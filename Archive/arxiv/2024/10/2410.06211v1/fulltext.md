## A mechanistically interpretable neural network for regulatory genomics

Deep neural networks excel in mapping genomic DNA sequences to associated readouts (e.g., protein–DNA binding). Beyond prediction, the goal of these networks is to reveal to scientists the underlying motifs (and their syntax) which drive genome regulation. Traditional methods that extract motifs from convolutional filters suffer from the uninterpretable dispersion of information across filters and layers. Other methods which rely on importance scores can be unstable and unreliable. Instead, we designed a novel mechanistically interpretable architecture for regulatory genomics, where motifs and their syntax are directly encoded and readable from the learned weights and activations. We provide theoretical and empirical evidence of our architecture’s full expressivity, while still being highly interpretable. Through several experiments, we show that our architecture excels in de novo motif discovery and motif instance calling, is robust to variable sequence contexts, and enables fully interpretable generation of novel functional sequences.


## 1 Introduction

Transcription factors (TFs) are proteins that regulate gene activity by recognizing and binding to specific short DNA sequence patterns—or “motifs”—in the genome ( Lambert et al. 2018 ; Siggers & Gordân 2014 ) . High-throughput experiments measure regulatory activity—such as protein–DNA binding or associated readouts—across the genome ( Consortium 2012 ) . In general, the regulatory function of a DNA sequence is defined by the combination of motifs in that sequence. Understanding the motifs (and their syntax) which regulate the genome is thus crucial for many scientific and medical tasks, such as disease diagnosis and design of novel therapies (e.g., with CRISPR). Extracting motifs and syntax from these experiments, however, is challenging. Motifs and their configurations have a soft syntax (i.e., density, spacing, orientation, and co-binders), which induces a particular function such as TF binding, and these syntactical rules are dependent on surrounding context and cell type.

Thus, accurately predicting genome regulation from DNA sequence requires expressive models to capture the complexities of motifs and their syntax. In particular, deep neural networks (DNNs) have achieved state-of-the-art performance in mapping DNA sequences to TF binding and associated readouts ( Kelley et al. 2016 ; Žiga Avsec et al. 2021b ; Linder et al. 2023 ) . These models take a DNA sequence as an input, and predict a label measured by a biological experiment (e.g., a binary label denoting if a TF bound to that sequence). The common goal of these genomic DNNs is to ultimately identify the fundamental code (i.e., motifs and their syntax) underpinning genome regulation ( Novakovsky et al. 2022a ) . Notably, recent work has shown that motif discovery from these DNNs has far surpassed the ability of traditional statistical methods ( Tseng 2022 ) .

There are two main classes of methods that extract motifs from a trained DNN. As these DNNs are almost universally convolution-based in early layers ( Novakovsky et al. 2022a ) , a very common approach is to extract a motif from each first-layer filter ( Kelley et al. 2016 ) . This method, however, suffers from the critical limitation that information (including motifs) tends to be distributed or dispersed across filters and layers, thus there is no guarantee that any single filter will learn a biologically meaningful motif (Figure 2 a). The second class of methods relies on importance scores, which attempt to measure the contribution of individual DNA bases to the output prediction, with the assumption that bases in motifs have elevated importance. By integrating throughout the whole DNN, importance scores bypass the problem of distributed information. Unfortunately, importance scores are known to be highly unstable and unreliable approximations of a model’s decision making ( Ghorbani et al. 2017 ; Alvarez-Melis & Jaakkola 2018 ) , and in genomic DNNs, importance scores typically only show noisy and fragile motif instances (Supplementary Figure S1 ) ( Tseng et al. 2020 ) . In practice, to improve robustness, motif discovery via importance scores requires complex pipelines composed of many computationally expensive steps, which tend to be delicate and require constant human intervention ( Novakovsky et al. 2022a ; Shrikumar et al. 2018 ) .

In this work, we propose a new method of recovering motifs from a DNN, based on mechanistic interpretability . Mechanistic interpretability (MI) has recently emerged as a key research direction to explain complex models ( Bereska & Gavves 2024 ) . Our method, Analysis of Regulatory Genomics via Mechanistically Interpretable Neural Networks (ARGMINN) , enables motifs and their syntax to be directly readable from the network architecture, without compromising expressivity or relying on complex post hoc pipelines. In Section 3 , we formally describe the ARGMINN architecture, including several novel architectural contributions including: 1) a regularizer designed to ensure that the first layer’s convolutional-filter weights directly encode a non-redundant set of relevant motifs; and 2) a modified attention mechanism which reveals motif instances and their syntax in any query sequence with a single forward pass.

In Section 4 , we show experimental results which demonstrate ARGMINN’s interpretability and its main contributions to regulatory genomics, including: 1) superior motif discovery and motif-instance/syntax analysis compared to existing approaches; 2) robustness against natural or adversarial sequence modifications; and 3) the novel ability to perform fully interpretable sequence generation. In Section 5 , we provide theoretical results on ARGMINN’s expressivity, showing that it can learn any motifs and syntax, whereas previous MI architectures cannot.


## 2 Related Work

Practically all prevalent genomic DNN architectures have convolutional filters as the first layer ( Kelley et al. 2016 ; Žiga Avsec et al. 2021b ; Linder et al. 2023 ) . To recover motifs, most works directly visualize the filter weights or average subsequences which highly activate each filter ( Alipanahi et al. 2015 ; Kelley et al. 2016 ) . Although this has shown some limited success, these methods assume that each filter learns one motif, and each motif is learned by one filter. This is generally not true because—without special constraints—motifs are typically learned in a distributed fashion, where each motif is learned across many filters and layers (Figure 2 a).

As a result, more sophisticated post hoc pipelines were developed to extract motifs from trained DNNs. These pipelines integrate over the entire DNN to compute importance scores across the dataset (e.g., via integrated gradients or DeepLIFTShap ( Sundararajan et al. 2017 ; Shrikumar et al. 2017 ) ), resulting in an importance score at each position for each sequence. These scores are then segmented into high-importance regions as putative motif instances. Due to the noisiness of importance scores, however, these instances must be clustered into clean motifs by tools like MoDISco ( Shrikumar et al. 2018 ) . Each step of this pipeline is computationally expensive, and for most datasets, the time required to recover motifs is typically over an order of magnitude longer than the time needed to train the model. Furthermore, these pipelines heavily rely on importance scores from a black-box model, which can be extremely fragile, as importance scores frequently fail to reveal a model’s true decision-making process ( Ghorbani et al. 2017 ; Kindermans et al. 2017 ; Alvarez-Melis & Jaakkola 2018 ; Tseng et al. 2020 ) .

Within the field of explainable AI, there has been some burgeoning work exploring MI, where the patterns and rules learned by a DNN are reflected in its physical computation ( Bereska & Gavves 2024 ) . In particular, our work is a type of intrinsic MI, where the DNN’s architecture (e.g., weights and activations) directly encode learning ( Liu et al. 2023 ; Barbiero et al. 2023 ; Kasioumis et al. 2021 ) . This is typically done by increasing sparsity, modularity, and the proportion of monosemantic neurons (i.e., neurons which learn a single concept). DNNs may also improve their intrinsic MI by learning logical rules in a more structured way ( Riegel et al. 2020 ; Friedman et al. 2023 ) .

Despite these promising works, constructing intrinsically MI architectures for very general problems remains difficult. However, focusing on more constrained predictive tasks (e.g., motif discovery) makes MI more feasible, allowing us to restrict computation and the solution space. ARGMINN uses similar principles as other intrinsic MI works (e.g., sparsity, modularity, monosemanticity, and explicit logic), but in a biologically grounded manner, making it both highly interpretable and expressive.

Recently, the ExplaiNN architecture also aimed to interpretably learn motifs from DNA sequences ( Novakovsky et al. 2022b ) . ExplaiNN consists of a set of single-filter convolutional networks. Each network ideally learns a distinct motif, and outputs a scalar summarizing binding strength over the input. The final output is a learned linear combination of these scalars. In later sections, we will show that ARGMINN surpasses ExplaiNN in both interpretability and expressivity.

Our work also relates to concept bottleneck models (CBMs) ( Koh et al. 2020 ; Ghorbani et al. 2019 ; Kim et al. 2017 ) , which force decisions to be based on interpretable concepts from an intermediate layer. While CBMs can provide meaningful explanations, they require pre-defined concepts and concept-labeled inputs, which are labor-intensive to obtain. In our work, ARGMINN can be viewed as a type of CBM, but the concepts are motifs, and the concepts are learned entirely from the data , thus overcoming the typical limitations of CBMs. Furthermore, ARGMINN elucidates syntax between motifs—rules relating to positioning between concepts—in addition to the motifs themselves.


## 3 ARGMINN Architecture

We propose a mechanistically interpretable DNN architecture designed to 1) accurately predict regulatory function (e.g., protein binding) from DNA sequence; 2) reveal crucial motifs responsible for function across the dataset; and 3) reveal motif instances and their syntax in any given query sequence. Importantly, 2) and 3) are directly encoded in the model’s weights and activations.

Our architecture consists of two modules trained end to end (Figure 1 a). The motif-scanner module is a single convolutional layer which identifies motifs from the input sequence. We developed a novel regularizer for the filters so that the filter weights directly encode non-redundant motifs, thereby accomplishing goal 2) above. The convolutional activations are passed to the second module—the syntax builder —consisting of several layers of modified attention that assemble the syntax and logic between motifs to produce a final prediction. The syntax builder is designed such that the activations and attention scores immediately reveal motif instances and syntax, thus achieving goal 3).


## 3.1 Module 1: Motif Scanners

The “motif scanners” are a set of n f n_{f} convolutional filters of width w w , which are scanned across the input sequence to produce a set of activations (Figure 1 b). Thus, a filter’s activation is maximized when it scans over a one-hot-encoded sequence that exactly matches the encoded motif (motifs are learned de novo ). The activations are then thresholded by a ReLU function. The additive bias parameter of the filters and the ReLU allow the network to selectively cut off weak matches, thereby producing more sparse activations. For a 1-hot encoded DNA sequence S ∈ { 0 , 1 } ℓ × 4 S\in\{0,1\}^{\ell\times 4} , the convolutional weights W ∈ ℝ n f × w × 4 W\in\mathbb{R}^{n_{f}\times w\times 4} (and bias b ∈ ℝ n f b\in\mathbb{R}^{n_{f}} ) yield activations A ∈ ℝ + ( ℓ − w + 1 ) × n f A\in\mathbb{R}_{+}^{(\ell-w+1)\times n_{f}} :

Importantly, the filters are regularized so that each filter learns one distinct motif, and each motif is learned by one filter. This allows motifs to be directly read from the filter weights after training. We propose a novel secondary objective which penalizes different filters from activating on overlapping sequences. This is combined with a simple L1-penalty on the filter weights themselves to induce sparse filters that directly reveal distinct, non-redundant motifs.

At each position i i in sequence S S , each filter aggregates values S ⁡ [ i , i + w ] S[i,i+w] . Let a = argmax ​ { A i } ∈ { 0 , … , n f − 1 } a=\text{argmax}\{A_{i}\}\in\{0,\ldots,n_{f}-1\} be the index of the maximally activated filter at i i . For all other filters b ≠ a b\neq a , if filters a a and b b both achieve non-zero activation in the same neighborhood of S S , then they should not both have non-zero weights in the overlapping region (i.e., they should not be attending to the same part of the sequence). In other words, every position of S S is “protected”: at most one filter can activate while attending to any position. If another filter is activated nearby, then its weights should not be attending to the protected part of the sequence. Our filter-overlap regularization then can be defined as the following loss function:

At each position i i , we compare the filter weights of the maximally activated filter W a W_{a} with the weights of all other filters ( W b W_{b} ), at every possible overlapping window j j . We penalize the L1 norm of the overlapping weights, multiplied by the activation of filter b b (i.e., if W b W_{b} is not activated, there is no penalty). Importantly, this is a soft regularization which the model can choose to ignore if needed for performance. This regularization helps prevent: 1) two filters learning the same motif (or the same part of the same motif); and 2) two filters learning a motif in an interleaved fashion. However, our regularization still allows for a long motif to be learned by two filters, split somewhere down the middle (or similarly, two half-sites directly next to each other, each learned by one filter).

In practice, this loss is computed efficiently by caching all possible windows of weight sums (for each value of j j ) once, and at each i i scaling the window products with the activation of W b W_{b} .


## 3.2 Module 2: Syntax Builder

After the motif-scanner module, positional encodings P P are concatenated to the activations A A . The second module of ARGMINN is the syntax builder, which consists of n L n_{L} layers of a custom attention mechanism that learns syntax between motifs (Figure 1 c). In contrast to typical attention, our modified attention layer has an explicit “memory stream” m l m_{l} which is updated after each layer (inspired by Friedman et al. 2023 ). Each layer derives a single query from m l m_{l} , resulting in a linear vector of attention scores rather than a quadratic matrix (this improves both interpretability and efficiency). Importantly, every layer derives key and value vectors directly from the original “tokens” (i.e., A | P A\|P ). Each attention layer can be described as follows:

where m 0 m_{0} is initialized as a vector of ones, and d q l d_{q_{l}} is the dimension of the query vector. We also include n h n_{h} attention heads, but do not show the reshaping operations above for clarity.

Each layer can attend to multiple motifs (due to the multiple attention heads), and successive layers allow the model to capture interactions between motifs (e.g., with k k layers, the model can reason about k k th-order interactions between motifs). All together, our final loss function becomes:


## 4 Experimental Results

In this section, we show experimental results demonstrating ARGMINN’s advantages in motif discovery, motif instance calling, robustness, and interpretable generation.


## 4.1 Improved motif discovery

To extract motifs from ARGMINN, we applied the procedure from Kelley et al. 2016 to the first-layer convolutional filters. Specifically, we obtained a motif from each filter by averaging test-set subsequences which highly activate the filter (filters which were never activated in the test set were dropped) (Supplementary Methods C.4 ).

Over several simulated and real-world experimental datasets (Supplementary Methods C.1 ), we compared the motifs discovered by ARGMINN to those identified by several other methods: interpreting the filters of a standard CNN, ExplaiNN ( Novakovsky et al. 2022b ) , and importance-score clustering via DeepLIFTShap and MoDISco ( Shrikumar et al. 2018 ) . We systematically matched each discovered motif to the closest known relevant motif. For simulated datasets, we matched to ground-truth motifs; for experimental datasets, we matched to the closest relevant human motif. ARGMINN identified known, biologically relevant motifs , and compared to other methods, it generally missed the fewest relevant motifs and discovered the fewest redundant motifs (Figure 2 a–b, Supplementary Figures S2 – S5 , Supplementary Table S1 ). For example, ARGMINN trained on FOXA2 in HepG2 (a pioneer factor) revealed factors in the FOX, HNF4, and CEBP families, all known to co-localize or co-bind with FOXA ( Seachrist et al. 2021 ; Geusz et al. 2021 ; Liu et al. 2020 ) . Notably, in the experimental datasets, the singular most similar motif (an extremely strict requirement) to an ARGMINN filter is typically a known relevant motif (e.g., on this FOXA dataset, ARGMINN identified 4 motifs whose top match was a relevant motif, whereas the traditional CNN only identified 2, with much weaker similarities). Additionally, ARGMINN’s motifs were generally most similar to the ground truth (Figure 2 c, Supplementary Table S2 ), thus highlighting their quality . ARGMINN was also the method which consistently identified the fewest extraneous motifs—patterns which do not match any biologically relevant motif (Figure 2 d, Supplementary Table S3 ).

In contrast, other methods significantly underperformed compared to ARGMINN. Even when the standard CNN or ExplaiNN encoded motifs in their filters, ARGMINN’s filters were far more similar to the true motifs. ARGMINN also outperformed MoDISco ( Shrikumar et al. 2018 ) , which—despite recovering many relevant motifs—consistently identified less-accurate motifs than ARGMINN (Figure 2 c). Due to the unreliability and noisiness of the importance scores themselves, as well as the frailty of clustering, MoDISco also found many redundancies and extraneous motifs (Figure 2 b, 2 d).


## 4.2 Improved motif instance calling and syntax discovery

With previous DNN-based methods, identifying motif syntax required first learning motifs (e.g., via MoDISco) and then scanning sequences to “call” motif instances. Not only is this computationally expensive, but instance calling by sequence scanning tends to be highly inaccurate (e.g., due to partial hits or missing context which the DNN would have considered).

Instead, ARGMINN reveals motif instances by tracing attention scores from a single forward pass on any sequence (Figure 3 a). Since every attention layer derives keys/values directly from the motif-scanner activations, high attention scores directly point to the precise motif instances which the network deemed important for prediction. Specifically, for any input query sequence, we examine the attention scores across all layers/heads on the forward pass. For each high score (e.g., > 0.9 >0.9 ), we identify the corresponding sequence position. We then check the motif activations at that position, and call a motif instance if a motif/filter has high activation (Supplementary Methods C.4 ). For example, trained on an experimental dataset of REST binding, ARGMINN directly recovered the unique binding syntax—including spacing preferences—of the two halves of the REST motif in both directions/orientations ( Tang et al. 2021 ) (Figure 3 b).

We then quantitatively evaluated motif instances identified by ARGMINN versus a traditional pipeline. Namely, using FIMO ( Bailey et al. 2015 ) , we called instances of MoDISco-discovered motifs ( Shrikumar et al. 2018 ) in test sequences. For each method, we ranked instances by confidence and computed the number of ground-truth instances recovered by the top- k k called instances. For experimental datasets, we used independently derived binding footprints as ground truth ( Vierstra et al. 2020 ) . In general, ARGMINN’s motif instances were far more accurate than those found by the baseline (Figure 3 c, Supplementary Figure S6 , Supplementary Table S4 ). To gain further intuition, we also compared to motif instances found by using FIMO to scan for ARGMINN-discovered motifs. ARGMINN identified more accurate motif instances than FIMO, even when FIMO was given the same set of ARGMINN motifs. This comparison also shows the direct benefit of using ARGMINN to perform motif instance calling, compared to the traditional method of sequence scanning.

Finally, to further demonstrate that ARGMINN’s attention scores match underlying biological signal, we show that the positions of high attention scores in experimental test-set sequences closely track the measured biological strength of protein binding along the sequence (Supplementary Figure S7 ).


## 4.3 QTL prioritization

Next, we evaluated ARGMINN’s ability to classify and prioritize a set of causal DNase-sensitivity quantitative trait loci (dsQTLs) from a background set of non-causal dsQTLs. dsQTLs are mutations which change the DNase accessibility of a sequence. A predictive model which makes decisions based on biological signals (and not spurious correlates) should predict a larger change for causal dsQTLs compared to non-causal dsQTLs, which are merely correlated with the causal changes. On a held-out chromosome, we found that compared to other architectures, ARGMINN was capable of classifying/prioritizing the causal dsQTLs much more accurately (Figure 4 a). In particular, these causal dsQTLs tended to overlap specific motif instances which ARGMINN used for its prediction of accessibility (Figure 4 b). This further shows that ARGMINN makes biologically meaningful predictions on sequence changes, based on interpretable motif biology rather than spurious signals.


## 4.4 Robustness of ARGMINN

Because ARGMINN makes decisions based on biologically meaningful motifs, it is more robust to background variations. On several simulated datasets, we trained ARGMINN (along with a standard CNN and ExplaiNN) with a 50% GC background. We then computed predictive performance on test sequences with GC content ranging from 5% to 95%, thus simulating natural variation in background composition. ARGMINN’s performance suffered the least, with a higher and tighter distribution of performance in general (Supplementary Figure S8 a).

Furthermore, because traditional CNNs learn filters which do not accurately represent motifs, they are prone to adversarial attacks (Supplementary Methods C.4 ). On our SPI1 dataset, we trained a CNN to achieve 88% accuracy. We then easily constructed many sequences containing short substrings which highly activate its filters, but without any instances of the SPI1 motif. On this set of sequences, the standard CNN’s accuracy dropped to 55% . Reflexively, we also easily designed sequences containing the SPI1 motif, but we inserted substrings into the background which strongly deactivate the filters, leading the CNN’s accuracy to drop to 48% . In contrast, because ARGMINN encodes meaningful biological motifs in each filter, it remains robust against such an attack (i.e., one cannot easily identify highly-activating or anti-activating sequences which trick the model into giving the wrong prediction).

Finally, we used Ledidi ( Schreiber et al. 2020 ) to generate sequences which would bind to SPI1. Ledidi is a gradient-based sequence-design method, which optimizes input sequences to maximize the probability of a positive prediction from a given model. Applying Ledidi on the ARGMINN architecture generated sequences with the strongest instances of the true SPI1 motif (Supplementary Figure S8 b). The true binding strength of ARGMINN’s Ledidi-generated instances was significantly higher than those generated from the standard CNN ( p = 8.95 × 10 − 18 p=8.95\times 10^{-18} ) and ExplaiNN ( p = 5.53 × 10 − 146 p=5.53\times 10^{-146} ). This is likely due to the fact that ARGMINN is explicitly trained to focus on the relevant motifs, whereas the other models often focus on spurious, non-motif sequence patterns, resulting in ARGMINN’s being a more robust oracle for optimization.


## 4.5 Interpretable design of novel functional sequences

Upon training, ARGMINN reveals the functional motifs and the syntatical rules for combining them which produce a prediction of binding or accessibility. As such, ARGMINN can be used for interpretable generation of novel functional sequences . In contrast with sequence generation using traditional methods (e.g., gradient-based tools like Ledidi, or directed evolution) or non-interpretable generative models (e.g., diffusion models or autoencoders), we may start with ARGMINN interpretations and sample motif configurations to insert into non-functional backgrounds. This yields a generated sequence for which we have a complete understanding on the reason why it is biologically active (e.g., it is active because it has the FOXA motif and TEAD motif 50 bp apart) (Figure 5 a).

To demonstrate this ability, we trained ARGMINN to predict DNA accessibility in the HepG2 cell type from experimental data. On the test set, we then extracted the functional motifs and the syntactical rules and grammars between them. We sampled motifs and their configurations entirely from ARGMINN’s discovered biology, and inserted them into non-functional sequence backgrounds (Supplementary Methods C.4 ). Using the same model as a predictor of accessibility, we found that the newly generated sequences were predicted to be significantly more accessible than the shuffled non-functional backgrounds ( p = 1.78 × 10 − 32 p=1.78\times 10^{-32} ). Furthermore, these generated sequences were predicted to be just as accessible as natural sequences identified to be highly accessible by the original biological experiment ( p = 0.75 p=0.75 ) (Supplementary Figure S9 c). We then repeated our in silico validation with a completely independently trained model, Borzoi ( Linder et al. 2023 ) . Using the output head of Borzoi which predicts DNA accessibility in HepG2, we passed the same sequences through Borzoi to predict accessibility and confirmed the same trends: the generated sequences were far more accessible than the non-functional backgrounds, and were similar in accessibility to natural sequences identified by the experiment (Figure 5 b). We found that this trend was also upheld by two additional independent oracles (Supplementary Figure S9 a–b).


## 5 Theoretical results

For a MI architecture, ARGMINN is highly interpretable, yet uniquely retains high expressivity. Here, we show that ARGMINN is capable of learning any possible configuration of motifs—including positional and syntactic constraints—as long as the constraints are definable in first-order logic.

Every configuration of motifs/subsequences which is definable by a sentence in first-order logic (with positional variables) is recognizable by an ARGMINN classifier.

Furthermore, ARGMINN is more expressive than previous interpretable architectures for regulatory genomics, such as ExplaiNN ( Novakovsky et al. 2022b ) , which learns an output label from a linear combination of motif strengths:

There exists a configuration of first-order-logic-expressable motifs/subsequences which is not recognizable by any ExplaiNN classifier.

We formally prove Theorem 1 and Corollary 1.1 in Appendix A . Here, we briefly sketch the proof of Theorem 1 . Intuitively, ARGMINN’s motif-scanner module outputs motif binding strengths by encoding each motif’s position-weight matrix ( Benos et al. 2002 ) in a different filter. With expressive positional encodings, the syntax-builder module learns syntax/interactions between motif instances. Each attention head learns one syntactical “rule” (i.e., possible motif combinations), which is built up in complexity over layers (i.e., combinations of k k motifs are learned by the k k th layer).


## 5.1 Experimental follow-up to theoretical results

To empirically reinforce our theoretical results, we consider the REST binding motif, which consists of two halves which must bind together (with variable spacings) (Figure 3 b). Notably, both halves need to bind in the same orientation and order (half sites cannot be mixed/matched). On a simulated REST dataset which explicitly tests these complex requirements, ARGMINN achieved 90.9% test-set accuracy, whereas ExplaiNN only achieved 73.4% . This demonstrates that ARGMINN is sufficiently expressive to capture complex grammars and syntax between motifs, which previous architectures could not.


## 6 Discussion

We illustrated ARGMINN’s unique ability to reveal genome-regulatory motifs and their syntax directly from its weights and activations—an advantage which is entirely absent from traditional (non-MI) DNNs. We then compared the predictive performance of ARGMINN to standard CNNs and ExplaiNN (Supplementary Table S5 ). It is generally well known that more interpretable models may suffer slightly in predictive performance ( Dosilovic et al. 2018 ; Arrieta et al. 2020 ) . This is expected, as these models tend to base decisions on human-interpretable concepts (e.g., crucial motifs), instead of spurious signals which can be informative, but are not useful for understanding regulatory genomics (e.g., GC content, exceptionally rare motifs, etc.). Our empirical results fall in line with these expectations. On simulated datasets where we ensured that the only informative signals are motifs, ARGMINN achieved superior performance compared to the baselines. On experimental datasets with many more spurious signals, ARGMINN achieved competitive performance, but did not outperform its non-MI counterparts.

Additionally, to further show the benefit of our filter regularizer, we applied our regularization to a standard CNN. As a result, the CNN’s filters also encoded relevant and non-redundant motifs (Supplementary Figure S10 ). This shows that our filter-overlap regularizer can be readily applied to standard genomic DNNs to achieve more interpretable first-layer filters in general. Importantly, however, without the other architectural novelties of ARGMINN (Equation 3 ), such a DNN would still not reap benefits such as motif-instance and syntax discovery.

Finally, we explored the robustness of ARGMINN to the loss weights (which are hyperparameters) for our regularizers. We found that over many orders of magnitude, ARGMINN’s predictive performance and interpretability both remained robust to the loss weights (Supplementary Figure S11 ). This is partially due to the design of these regularizers, which are aimed to synergize with predictive performance and the learning of biological motifs, rather than compete with other losses.

Mechanistic interpretability is still a nascent field, and our research pioneers an architecture that enables direct interpretation with minimal post hoc analysis. To our knowledge, ARGMINN is the most MI (yet still fully expressive) architecture for genome regulation—a field where understanding a model’s learned decision rules is equally as critical as its accuracy ( Eraslan et al. 2019 ; Rudin 2019 ) —and is one of the few intrinsically MI architectures of its complexity in general. We showed that ARGMINN is expressive enough to accurately predict genome regulation, yet is uniquely constrained so the weights and activations directly encode the decision process in a human-interpretable way . Further work in this area can yield major benefits for scientific AI and explainable AI.


## References


## Appendix A Supplementary Proofs


## A.1 Proof of Theorem 1

In this section, we prove that every configuration of motifs (which is definable by a first-order-logical sentence with position-indexed variables) is recognizable by an ARGMINN classifier. We will first show that ARGMINN’s motif-scanner module is sufficiently expressive to characterize motif-based protein binding, and then subsequently that the syntax-builder module can recognize arbitrary logical syntax between these binding sites.

Biophysical assumptions

We begin with our biophysical assumptions which justify our modeling of motif biology by first-order logic (with position-indexed variables).

For binary biological readouts of interest (e.g., protein-binding measured by ChIP-seq, DNA accessibility measured by DNase-seq, etc.), the readout is fully characterized by the binding of proteins, which recognize motifs in the sequence ( Stormo & Fields 1998 ; Lemon & Tjian 2000 ) .

The free concentration of any particular protein is constant across training and testing conditions.

For a given potential binding site (e.g., a motif instance in a DNA sequence), the strength and likelihood of binding of a specific protein (these quantities are related through statistical mechanics) can be sufficiently summarized by a single scalar value (related to the K d K_{d} , or dissociation constant). Through statistical mechanics, the fraction/probability of binding is [ TF ] K d + [ TF ] \frac{[\text{TF}]}{K_{d}+[\text{TF}]} ( Stormo & Fields 1998 ) .

The K d K_{d} value (or a monotonic function of it) can be computed as an independently additive function of individual positions of the binding site. An example of this is the PWM (position weight matrix), which has been shown to be a good approximation of binding mechanics ( Benos et al. 2002 ; Pan & Phan 2008 ) .

Input sequences are a finite length ℓ \ell .

Given real-valued variables b m , p b_{m,p} representing the binding strength of motif m m at position p p in a sequence, the binary biological readout (e.g., binding of a particular protein of interest or accessibility) of the sequence as a whole can be expressed as the following disjunction of statements:

σ := ⋁ i = 1 n ϕ i \sigma:=\bigvee\limits_{i=1}^{n}\phi_{i} ,

where ϕ i \phi_{i} is a statement denoting a single possible configuration of motifs that induces a positive biological readout.

Each ϕ i \phi_{i} has the following form:

ϕ i := ( b m i , 1 , p i , 1 ≥ t i , 1 ) ∧ ⋯ ∧ ( b m i , d , p i , d ≥ t i , d ) \phi_{i}:=(b_{m_{i,1},p_{i,1}}\geq t_{i,1})\land\cdots\land(b_{m_{i,d},p_{i,d}}\geq t_{i,d}) .

That is, ϕ i \phi_{i} defines whether or not a specific configuration of d ≥ 1 d\geq 1 binding motifs m i , 1 , … , m i , d m_{i,1},…,m_{i,d} exist with sufficient strength at positions p i , 1 , … , p i , d p_{i,1},…,p_{i,d} . Note that with finite sequences, all possible statements about combinations of motifs (expressable in first-order logic) can be written in this form, by the Disjunctive Normal Form Theorem.

Below, we proceed with our proof by constructing an instantiation of the ARGMINN architecture where the particular instantiation implements/recognizes a sentence σ \sigma .

Motif-scanner module

Given the above biophysical assumptions, the motif-scanner module’s convolutional filters are sufficiently expressive to capture the binding strengths/likelihoods of each position for each potential binding motif.

We simply design this module to have n f n_{f} filters equal to the number of unique motifs m m in σ \sigma , with width w w equal to the maximum width of any motif. We set the multiplicative weights of each filter with the PWM of each motif, so that this module precisely implements the PWM-scanning procedure that is common in the field of regulatory genomics ( Benos et al. 2002 ) . For this proof, we set the bias to be 0. Note that if the convolutional filters W W are all PWMs, then the multiplicative weights are all non-negative, and so the pre-ReLU activation will also be non-negative.

Thus, the motif-scanner module outputs a set of binding strengths for each position of the sequence, for each possible motif. In other words, this module outputs b m , p b_{m,p} for each relevant motif m m , at each position p p . This constitutes the motif activations A A of the model.

Syntax-builder module

Now we design an instantiation of the syntax-builder module which captures the logic in σ \sigma . In particular, our model will produce a pre-sigmoid output which is positive if and only if σ \sigma is true.

The input to the syntax-builder module is the concatenation of motif activations A A (which is the matrix of binding strengths b m , p b_{m,p} ) and the positional encodings P P : A | P A\|P . For ease of proof, let the positional encodings P P be a one-hot-encoded vector of size ℓ \ell , denoting position. We will use the notation [ A ∥ P ] p [A\|P]_{p} to denote the column vector at position p p , which is an ( n f + ℓ ) (n_{f}+\ell) -dimensional vector where the first n f n_{f} entries contain the binding strengths/activations of each motif at position p p , and the latter ℓ \ell entries contain a one-hot encoding of position p p .

Recall that within σ \sigma , n n is the number of statements in disjunction. Let d m ​ a ​ x d_{max} be the maximum length of any of the ϕ i \phi_{i} s. For simplicity of our proof and construction, we pad every ϕ i \phi_{i} to have exactly d m ​ a ​ x d_{max} clauses by adding “dummy motif clauses”. For example, let us pad with the clause ( b 0 , 0 ≥ 0 ) (b_{0,0}\geq 0) . This simply checks that some arbitrary motif (index 0) at some arbitrary position (position 0) has non-negative activation, which will always be true since the convolutional weights in the motif-scanner module are PWMs.

We let the memory vector m l m_{l} be of dimension n ⁡ ( n f + ℓ ) n(n_{f}+\ell) . Additionally, we define the dimension of the query/key/value vectors be n f + ℓ n_{f}+\ell .

Our proof (like many other similar proofs) relies on the universal approximation theorem of feed-forward networks (FFNs). We also leverage Lemma 19 from ( Chiang et al. 2023 ) , which shows that in an FFN, residual connections can effectively be ignored (which simplifies the construction of our network).

We proceed with induction on d m ​ a ​ x d_{max} , where our syntax-builder module has d m ​ a ​ x d_{max} attention layers, with n n heads for each layer (one head for every ϕ i \phi_{i} ).

Base case: d m ​ a ​ x = 1 d_{max}=1

Consider d m ​ a ​ x = 1 d_{max}=1 . In this case, each ϕ i \phi_{i} can be written as ϕ i := b m i , p i ≥ t i \phi_{i}:=b_{m_{i},p_{i}}\geq t_{i} . That is, ϕ i \phi_{i} is true if and only if motif m i m_{i} at position p i p_{i} is strong enough.

Now we instantiate a single-attention-layer syntax-builder module with n n attention heads. We repeat the following for each head independently:

For each head i i , we learn to recognize ϕ i \phi_{i} . Recall that the memory vector m 0 m_{0} is initialized to be all 1s.

We define the weight matrices W Q , 1 , W K , 1 , W V , 1 W_{Q,1},W_{K,1},W_{V,1} separately for each attention head in this proof, knowing that the final weight matrices for the attention layer as a whole are obtained by a simple concatenatation operation over the heads. Let W Q , 1 W_{Q,1} map m 0 m_{0} to a single vector where the first n f n_{f} entries is a one-hot encoding where the 1 is in the position of motif m i m_{i} , and the latter ℓ \ell entries is filled with a very negative constant − C -C ( C >> 0 C>>0 ), except for the position p i p_{i} (indexed from within these latter ℓ \ell entries), which has a 1. Let W K , 1 = W V , 1 = I n f + ℓ W_{K,1}=W_{V,1}=I_{n_{f}+\ell} , the identity matrix of appropriate size:

where the 1 is at index m i m_{i} in the left block, and the 1 is at index p i p_{i} within the right block.

Next, we take the dot product of every key vector with the query vector. For the key vector [ A ∥ P ] p i [A\|P]_{p_{i}} (originating from position p i p_{i} ), the dot product will be b m i , p i + 1 b_{m_{i},p_{i}}+1 (the first n f n_{f} entries contribute the binding strength b m i , p i b_{m_{i},p_{i}} , and the latter ℓ \ell entries contribute the 1). For any other position p ≠ p i p\neq p_{i} , the dot product will be b m i , p − C b_{m_{i},p}-C .

We select C C to be a large-enough magnitude such that after the softmax, the attention score at position p i p_{i} will be approximately 1, and all other positions will effectively be 0. Thus, the final vector being passed to the feed-forward network (FFN) is equivalent to the value vector corresponding to position p i p_{i} (which is equivalent to the motif activations/positional encoding at position p i p_{i} ):

With all attention heads together, we obtain a concatenated vector of size n ⁡ ( n f + ℓ ) n(n_{f}+\ell) , where every contiguous i i th block of n f + ℓ n_{f}+\ell entries corresponds to ϕ i \phi_{i} , and contains the vector [ A ∥ P ] p i [A\|P]_{p_{i}} .

We then design our FFN to map from this vector to our final memory stream m 1 m_{1} . In particular, this FFN will produce an output vector of the same size, where every contiguous i i th block of n f + ℓ n_{f}+\ell entries contains all − 1 n f + ℓ -\frac{1}{n_{f}+\ell} if b m i , p i < t i b_{m_{i},p_{i}}<t_{i} , and all n n f + ℓ \frac{n}{n_{f}+\ell} otherwise. We invoke Lemma 19 from Chiang et al. 2023 and the Universal Approximation Theorem to perform this step.

Our final linear projection layer (which takes m 1 m_{1} and maps to an output prediction y ^ \hat{y} ) has weights of all 1 and bias of 0.

Together, this ensures that the output y ^ > 0 \hat{y}>0 if and only if there exists an i i such that b m i , p i > t i b_{m_{i},p_{i}}>t_{i} (i.e., ϕ i \phi_{i} is true).

Base case: d m ​ a ​ x = 2 d_{max}=2

We proceed with a similar structure as with the above base case. In the first layer, we define W Q , 1 , W K , 1 , W V , 1 W_{Q,1},W_{K,1},W_{V,1} identically as above. However, after the first attention layer, we design the FFN differently so that m 1 m_{1} contains information about the next motif within ϕ i \phi_{i} to search for.

In particular, each ϕ i \phi_{i} is of the form ϕ i := ( b m i , 1 , p i , 1 ≥ t i , 1 ) ∧ ( b m i , 2 , p i , 2 ≥ t i , 2 ) \phi_{i}:=(b_{m_{i,1},p_{i,1}}\geq t_{i,1})\land(b_{m_{i,2},p_{i,2}}\geq t_{i,2}) . In the first attention layer, we define the weight matrices W Q , 1 , W K , 1 , W V , 1 W_{Q,1},W_{K,1},W_{V,1} as above, so that the vector passed to the FFN is a concatenation of [ A ∥ P ] p i , 1 [A\|P]_{p_{i,1}} for all i i .

Here, we design the FFN so that it will produce m 1 m_{1} , where every contiguous i i th block of n f + ℓ n_{f}+\ell entries contains all 1s if b m i , 1 , p i , 1 ≥ t i , 1 b_{m_{i,1},p_{i,1}}\geq t_{i,1} , and all 0s otherwise.

Next, the second attention layer will identify the second motif in each ϕ i \phi_{i} . Again, we consider each attention head i i separately.

In this second layer, W Q , 2 W_{Q,2} produces a query vector for each head which is similar to that in the previous base case: a vector of n f + ℓ n_{f}+\ell entries where the first n f n_{f} is all 0 except for the position of m i , 2 m_{i,2} , and the latter ℓ \ell entries are all − C -C except for the position p i , 2 p_{i,2} (however, note that if the first motif m i , 1 m_{i,1} was not found at position p i , 1 p_{i,1} , then the i i th block of m 1 m_{1} will be all 0s, and so the query vector will be also all 0s). Again, we let W K , 2 = W V , 2 = I n f + ℓ W_{K,2}=W_{V,2}=I_{n_{f}+\ell} :

where the 1 is at index m i , 2 m_{i,2} in the left block, and the 1 is at index p i , 2 p_{i,2} within the right block. If the first motif m i , 1 m_{i,1} was not found, then this vector will be all 0s.

We then follow the same construction as with the previous base case, where the second FFN produces the final memory stream m 2 m_{2} based on comparing each b m i , 2 , p i , 2 b_{m_{i,2},p_{i,2}} to t i , 2 t_{i,2} : every contiguous i i th block of n f + ℓ n_{f}+\ell entries contains all − 1 n f + ℓ -\frac{1}{n_{f}+\ell} if b m i , 2 , p i , 2 < t i , 2 b_{m_{i,2},p_{i,2}}<t_{i,2} , and all n n f + ℓ \frac{n}{n_{f}+\ell} otherwise. If, however, the first motif m i , 1 m_{i,1} was not found, then the FFN will always output − 1 n f + ℓ -\frac{1}{n_{f}+\ell} for that block (in this case, the query vector is all 0s, and the latter ℓ \ell entries of the i i th block in the input to the FFN will be a smeared fraction rather than a one-hot encoding). The final projection layer will be the same as with the first base case, leading to the desired outcome.

Inductive case

We complete our inductive proof for a general d m ​ a ​ x d_{max} , as the construction of the architecture with d m ​ a ​ x d_{max} layers is a straightforward extension from the base cases.

We assume that in the first d m ​ a ​ x − 1 d_{max}-1 layers, the memory stream m d m ​ a ​ x − 1 m_{d_{max}-1} is structured as contiguous blocks of n f + ℓ n_{f}+\ell entries, where the i i th block is such that it contains all 1s if and only if b m i , j , p i , j ≥ t i , j b_{m_{i,j},p_{i,j}}\geq t_{i,j} for all j < d m ​ a ​ x j<d_{max} and all 0s otherwise. We then structure our final d m ​ a ​ x d_{max} th layer of the attention mechanism similarly to the second layer in the base case of d m ​ a ​ x = 2 d_{max}=2 .


## A.2 Proof of Corollary 1.1

Here, we prove that there exists a configuration of motifs specified by first-order logic, which is not recognizable by ExplaiNN.

Consider a dataset of sequences defined by the presence of distinct motifs A , B , C , D A,B,C,D . Every sequence has exactly two instances of such motifs. A positive sequence is defined by having both A A and B B , or both C C and D D . A negative sequence is defined by any other combination: A ​ C AC , B ​ D BD , A ​ D AD , or B ​ C BC . This constructed example is a realistic one, as it is the binding rule seen in transcription factors with two half sites (e.g., REST ( Tang et al. 2021 ) ), or co-factor binding where the motifs and transcription factors are unidirectional (e.g., JUND and TEAD).

Within ExplaiNN, each CNN “unit” learns the presence of one such motif, and returns a scalar score. Let there be four CNN units, one for each motif. For each input sequence, we obtain four such scores: s A , s B , s C , s D s_{A},s_{B},s_{C},s_{D} .

Each CNN unit consists of a single convolutional filter whose activation is maximized by the motif it learns. For simplicity, we assume that given a convolutional filter that learns substring X X , the distribution of activations of that filter on background sequences is identical to the distribution of activations on non- X X motifs. This could be realized, for example, by motifs whose composition is base/letter-wise distributed identically to the background (e.g., uniform). Thus, for a convolutional filter which recognizes X X , the distribution of its activations is identical across all non- X X substrings. Given sufficiently long sequences, the CNN unit for some motif X X will output a scalar score as follows: if X X is in the sequence, s X = p X s_{X}=p_{X} , a score for “positives”; if X X is not present, s X = n X ≠ p X s_{X}=n_{X}\neq p_{X} , a score for “negatives”.

Given these CNN units, suppose it is possible to distinguish positive and negative sequences with a linear combination, as in ExplaiNN. The output of the model is w A ​ s A + w B ​ s B + w C ​ s C + w D ​ s D + β w_{A}s_{A}+w_{B}s_{B}+w_{C}s_{C}+w_{D}s_{D}+\beta for scalar weights w A , … , w D w_{A},\ldots,w_{D} and bias β \beta .

For the classifier to be sufficiently expressive, we require that positive examples have a final output that is at least some threshold τ \tau , and negative examples to have an output that is strictly less than τ \tau .

Thus, we have the following inequalities (one for each possible pair of motifs):

Adding inequalities of the same type:

This is a contradiction, as this requires w A ​ ( p A + n A ) + ⋯ + w D ​ ( p D + n D ) w_{A}(p_{A}+n_{A})+\cdots+w_{D}(p_{D}+n_{D}) to be both at least 2 ​ ( τ − β ) 2(\tau-\beta) and strictly less than 2 ​ ( τ − β ) 2(\tau-\beta) .

Thus, ExplaiNN is not sufficiently expressive to capture every configuration of motifs expressable in first-order logic (e.g., exclusive disjunctions).


## Appendix B Supplementary Figures and Tables

Number of times each relevant motif was discovered by each method. A value of 0 means the motif was not discovered at all. Values greater than 1 indicate redundancy.

Similarity of closest motif discovered by each method to each relevant motif. If a method did not discover a motif, it is given a similarity of 0.

Number of extraneous motifs (i.e., those which do not match any known relevant motif) found by each method for each dataset.

Precision and recall values for motif instances discovered by ARGMINN (A) and by FIMO. We initialize FIMO either with motifs discovered by ARGMINN (F/AM), or with motifs discovered by MoDISco (F/MM).

Model performance comparing ARGMINN (A), a standard CNN (SC), and ExplaiNN (E). All models were given the same number and size of convolutional filters, and the overall complexity/capacity of the models were kept as similar as possible for comparison.


## Appendix C Supplementary Methods

All of the code used to generate the results and figures in this paper is available here:

https://github.com/Genentech/ARGMINN


## C.1 Training data

For our simulated datasets, we downloaded motif PFMs (position frequency matrices) from JASPAR ( Fornes et al. 2020 ) , and trimmed off low-information-content flanks. When training and testing, we randomly generated 500 bp sequences on the fly. Motif instances were sampled from the PFMs, and inserted into a randomly sampled background (from a uniform distribution of A, C, G, and T). Motifs (or combinations of them) were randomly inserted in the central 100 bp of the background. Our simulations contained motif configurations as follows:

SPI1: all positive sequences have a single instance of the SPI1 motif

TAL/GATA: 37.5% of positive sequences have a single instance of TAL1, 37.5% have a single instance of GATA1, and 25% of sequences have both (either 7, 8, or 9 bp apart)

E2F6: 10% of positive sequences have a single instance of E2F6, and 90% have both E2F6 and MAX, between 30 and 60 bp apart; 50% of negative sequences have only the MAX motif, and the other 50% are random background

JUND: 25% of positive sequences have the JUND TRE motif, 25% have the JUND CRE motif, and 50% have the JUND TRE motif followed by the TEAD4 motif with a spacing of 6 bp in between

REST: all positive sequences have both the left- and right-half motifs, with a spacing of 2, 6, 7, 8, 9, 10, or 11 bp apart; 25% of negative sequences have only the left-half motif, 25% have only the right-half motif, and 50% are random background

SPI1/CTCF: all positive sequences have a single instance of the SPI1 motif; 50% of negative sequences have SPI1 followed by the CTCF motif (either 30, 40, or 50 bp apart), and 50% are random background

When generating simulated sequences, we scanned the random backgrounds for spurious matches and filtered out such instances. Note that this is a crucial step for simulated datasets, as for short motifs such as GATA (6 bp), we would expect over 12% of random backgrounds to contain a perfect match by chance. This is an issue which is much rarer in real datasets, but for our simulations, we scanned the PFMs (and their reverse complements) across our generated backgrounds (for positive and negative sequences), and ensured that no PFM which was used in the simulation attained a match score of over 0.9.

For our experimental datasets, we downloaded the IDR peaks from ENCODE ( Consortium 2012 ) for the following experiments:

Our positive dataset consisted of random 500 bp sequences drawn from the genome, where at least half of the 500 bp overlaps a peak (if the peak is less than 500 bp), or at least half of the peak overlaps the 500 bp (if the peak is over 500 bp). Our negative dataset consisted of randomly sampled intervals from the genome. If a randomly selected negative sample overlapped a peak by more than half (or vice versa , it was relabeled as positive for the batch).

Note that when training, we automatically used reverse-complement augmentation so that every batch contained sequences along with their reverse complements.


## C.2 Model architectures

Our ARGMINN architecture consists of two modules: motif scanners and a syntax builder. The motif scanners consist of a single convolutional layer of n f n_{f} filters, each of w w bp in width (typical values are n f = 8 n_{f}=8 , w = 10 w=10 ), which scan across a one-hot-encoded DNA sequence. The result is passed to a ReLU, and the output constitutes the “motif activations”.

The motif activations are concatenated with a positional encoding of dimension d = 16 d=16 . Our positional encoding is defined as follows:

where i i is the position along the sequence, and j ∈ { 0 , … , d 2 − 1 } j\in\{0,\ldots,\frac{d}{2}-1\} .

Let A | P A\|P be the motif activations and positional encodings concatenated together. This is passed to two consecutive memory-stream-based attention layers. The l l th attention layer starts with a memory stream m l − 1 m_{l-1} of dimension 128 ( m 0 m_{0} is a vector of all 1s), and A | P A\|P . In each layer, m l − 1 m_{l-1} is passed through a linear layer to obtain a single query q l q_{l} of dimension equal to the dimension of each input token in A | P A\|P . Two separate linear layers also convert each token in A | P A\|P into a set of key vectors and value vectors (of the same dimension as the input token). The query, keys, and values are reshaped to obtain 4 attention heads. We then compute the attention scores by multiplying the query against all keys, and normalizing by d q l \sqrt{d_{q_{l}}} , where d q l d_{q_{l}} is the dimension of the query/key/value vectors. We then perform dropout on the attention scores with dropout rate 0.1, and softmax the scores for each attention head. These attention scores are used to weight the value vectors in a weighted sum, which is then reshaped to reincorporate the heads. This is passed through another linear layer which retains the same dimension, followed by dropout and layer normalization. This is then fed to a 2-layer MLP with ReLU and dropout in between the two linear layers, mapping the result to the same dimension as m l − 1 m_{l-1} . After a final dropout and layer norm, this is added to m l − 1 m_{l-1} to obtain m l m_{l} .

After all attention layers, the final m l m_{l} is passed to a single linear layer which maps it to a scalar prediction which is passed to a sigmoid activation function (for binary prediction).

Our standard CNN follows an architecture which is common in the literature for single-task predictions. We apply 3 successive convolutional layers to the input sequence, each with n f n_{f} filters. The filters of the first layer have width w w . The next two convolutional layers have filters of width 5. After each layer we apply ReLU and batch normalization. We then perform max pooling with a filter size of 40 and a stride of 40. This is passed to two linear layers of 10 and 5 hidden dimensions each. After each linear layer, we apply ReLU and batch normalization. Finally, a final linear layer maps the result to a sigmoid-activated output.

Our ExplaiNN implementation follows the description in Novakovsky et al. 2022b . As with the other architectures, we use the same number and width of first-layer convolutional filters.

Depending on the complexity of the dataset’s syntax, we selected the ARGMINN architectural hyperparameters accordingly. Note that these values were not tuned at all, and were chosen at the outset based on domain knowledge and never modified. We also ensured that for each dataset, we always used the same number and length of first-layer convolutional filters ( n f n_{f} and w w , respectively) in other architectures for a fair comparison.


## C.3 Training schedules

We trained all of our models and performed all analyses on a single Nvidia A100.

When training, we used a batch size of 128 with an equal number of positives and negatives (this includes the reverse-complement augmentation). For our simulated datasets, each training epoch consisted of 100 batches, and each validation and test epoch consisted of 10 batches. For our experimental datasets, we reserved chr8 and chr10 for validation, and chr1 for test (all other autosomes along with chrX were used for training).

We trained all of our models for 40 epochs (regardless of architecture), and noted that the loss had converged in all cases. We used a learning rate of 0.001.

For ARGMINN, we weighted the secondary losses as follows:

λ o \lambda_{o} : 0 for the first 10 epochs, increasing from 10 0.5 10^{0.5} to 10 4 10^{4} evenly in logarithmic space over the next 20 epochs, and stable at 10 4 10^{4} for the last 10 epochs

λ l \lambda_{l} : 0 for the first 10 epochs, increasing from 10 − 4 10^{-4} to 10 − 3 10^{-3} evenly in logarithmic space over the next 20 epochs, and stable at 10 − 3 10^{-3} for the last 10 epochs

For all of our models (ARGMINN, standard CNN, ExplaiNN), we trained 3 random initializations and selected the one with the best test accuracy for downstream analyses.


## C.4 Analyses

Extracting motifs from convolutional filters

To extract motif PFMs from convolutional filters, we adopted a procedure based on that described in Kelley et al. 2016 . Specifically, we passed the test set through the model and computed the average of all sub-sequences (pooling together all possible sub-sequences in the test set) which activated that filter to at least 50% of the maximum activation achieved over all such windows.

Computing importance scores

We computed importance scores using DeepLIFTShap, integrated gradients, or in silico mutagenesis ( Shrikumar et al. 2017 ; Sundararajan et al. 2017 ) .

For DeepLIFTShap and integrated gradients, we used PyTorch Captum. For DeepLIFTShap, we used a reference of 10 baselines consisting of dinucleotide-shuffled sequences, as recommended in Shrikumar et al. 2017 . We also recovered the hypothetical importance scores at each position, as recommended for MoDISco ( Shrikumar et al. 2018 ) . For integrated gradients, we used a baseline of all 0s.

To obtain in silico mutagenesis scores, we computed the importance of a base by first computing the difference between the output prediction of the original sequence versus every possible mutation that made at that position. We mean normalized over the base dimension to obtain a set of hypothetical importance scores. The actual importance score for a position was simply the hypothetical importance score (after mean normalization) for the base actually present in the sequence at the position.

Discovering motifs with MoDISco

In general, we discovered motifs using MoDISco from the standard CNN.

We computed importance scores over the entire positive-labeled dataset using the DeepLIFTShap algorithm as described above. We then ran MoDISco-lite v2.2.0 ( Shrikumar et al. 2018 ) using a maximum of 10000 seqlets and default parameters, as recommended by the authors.

Evaluating discovered motifs

To compute matches to known motifs, we used TOMTOM ( Bailey et al. 2015 ) to compute the q-value similarity between a PFM to known motifs (across all possible alignments). We reported the − log 10 ⁡ ( q ) -\log_{10}(q) value as similarity. For simulated datasets, we reported the closest match (i.e., highest similarity) to any motif in the dataset. For experimental datasets, we reported the closest match to any relevant motif in the JASPAR human-motif database ( Fornes et al. 2020 ) .

Note that to ensure a fair comparison, the lengths of the motifs were kept the same in each dataset. For ARGMINN, the standard CNN, and ExplaiNN, all models are trained with the same first-layer filter sizes. MoDISco by default outputs longer patterns, so we trimmed MoDISco-discovered motifs to the same size as the filters used by other methods (maximizing the total information content in the post-trimmed window; we used a uniform background for computing information content).

For our analyses on motif accuracy/similarity, redundancy, and number of extraneous motifs, we needed to match each motif discovered by each method to the closest relevant motif (or none at all). To do this, we first needed to identify the set of possible relevant motifs for each dataset (i.e., the set of motifs which would be considered biologically “accurate” for the task). For simulated datasets, the set of relevant motifs was simply the PFMs used to create the simulation. For experimental datasets, the set of relevant motifs was defined by first running TOMTOM against all known human motifs and pooling together the top matches (by motif family) over all methods and architectures (e.g., ARGMINN, MoDISco, etc.). We used a q-value cut off of 0.5. After pooling together all the top TOMTOM matches over all methods, we extracted a set of relevant motifs or motif families by checking for supporting literature. Any motif/family with supporting literature was kept as a relevant motif.

Finally, once the set of relevant motifs for each dataset was determined, we matched each motif (discovered by each method) to the closest relevant motif using TOMTOM. Discovered motifs which did not match any relevant motif (using the default TOMTOM threshold) were considered extraneous.

To compute redundancy, we counted the number of times each relevant motif was matched to by a method’s discovered motifs. We kept track of forward and reverse-complement orientations. As long as one orientation was discovered, we considered that motif to had been found; we computed redundancy as the maximum number of times a relevant motif was matched to (maximum over orientations). For reverse-complement symmetric motifs/families, we did not consider orientations separately, and computed redundancy accordingly.

To compute motif accuracy, we computed the similarity (measured by the TOMTOM q-value) of the closest motif discovered by each method to each relevant motif.

Tracing back motif instances and syntax

To trace back motif instances for a particular input sequence in ARGMINN, we performed a forward pass and retained the motif activations and attention scores. Over all layers and all attention heads, we examined the positions in the sequence which had an attention score of at least 0.9. We then called a motif hit if the activation for a filter at that position was at least the average activation (for that filter) over the test set.

In our analyses, we called motif instances over the test set.

To identify syntax, we separated the input sequences by which motif instances were called, and computed the distribution of the spacings between the motif instances.

In order to rank motif instances from ARGMINN, we ranked by maxmimum attention score over all heads/layers at that position. To break any ties, we used the highest motif-filter activation score at that position.

Scanning for motif instances with FIMO

Before running FIMO on MoDISco or ARGMINN motifs, we trimmed and filtered the motifs for high-information-content regions. Specifically, we cut off flanks with information content lower than 0.2. We then required that after trimming, the motif was at least 5 bp and had an average information content of 1.0. We used a uniform background for computing information content.

To scan for motif instances using FIMO, we started with PFMs and ran FIMO v5.0.5 ( Bailey et al. 2015 ) on test-set sequences and their reverse complements. We used the default FIMO parameters.

To rank FIMO hits, we used the q-value from FIMO. We also collapsed overlapping FIMO hits before analyzing, keeping the most significant q-value between overlapping hits for ranking purposes.

Evaluating motif instances

To evaluate our motif instances, we compared called motif instances to ground-truth instances. We computed the precision as the fraction of called instances which overlap ground-truth instances, and the recall as the fraction of ground-truth instances which overlap called instances. We also computed recall curves in a top- k k fashion, where we ranked the called instances (described above) and for each top k k called instances, we computed the recall relative to ground-truth instances.

For simulated datasets, the ground-truth motif instances are completely known, as they are defined at the time of sequence generation.

For experimental datasets, we obtained “ground-truth” motif instances from Vierstra et al. 2020 , an independently collected set of DNA-binding footprints in various cell types. For each cell type of interest (e.g., HepG2), we simply pooled together the footprints of all experiments from that cell type and used those as a set of ground-truth motif instances.

Due to computational efficiency, we also limited the set of called motif instances for experimental datasets to the top 10000 hits.

Evaluating QTL prioritization

We downloaded causal and non-causal QTLs in the GM12878 cell type from Lee et al. 2015 . We limited the set of dsQTLs to only those in the test set of our models (i.e., on chr1). We then took our models trained on GM12878 DNase accessibility, and for each putative QTL (causal or non-causal), we computed the absolute difference in the output prediction, and treated that as a score to compute precision and auROC.

Computing GC-content robustness

To test the robustness of our models against changes in GC content, we examined our models trained on simulated datasets (which allow us to modify the background GC content freely while keeping the motifs the same). Without retraining or fine-tuning, we evaluated the models’ predictive performance on background GC content of 5%, 10%, 15%, …, 90%, 95%.

Generating sequences using Ledidi

To generate novel sequences using Ledidi, we took our models (ARGMINN, standard CNN, ExplaiNN) trained on our simulated SPI1 dataset. For each model, we fitted Ledidi 32 times, and for each fitted instance, we generated 32 sequences. This yielded 1024 Ledidi-generated SPI1 sequences for each model. We used τ = 5 , λ = 5000 \tau=5,\lambda=5000 for Ledidi.

To evaluate the quality of the generated sequences, we scanned the true PFM across each sequence (note that these models were all trained on sequences which contain motifs sampled from this exact PFM), and computed the top match score (as a cross-correlation score) for each sequence.

We computed significance of the difference in distributions (between different models used with Ledidi) of top SPI1 match scores using a one-sided Mann-Whitney U test.

Generating adversarial examples

We generated adversarial examples in a standard CNN in two ways.

First, we generated sequences which had no motifs present, but were still predicted to have a positive label by the CNN. To do this, we built up random sequences by taking highly-activating sequences from random filters and adding them to the sequence. We took the most highly-activating sequence for each filter and randomly strung together a random ordering of such sequences to obtain a 500 bp example. We verified that no part of these sequences matched any motif (or reverse complement) in the dataset, using the same criteria as the data loader as described above.

Next, we generated sequences which had motifs, but were still predicted to be negative by the CNN. To do this, we first sampled a motif configuration from the normal simulation. Under normal circumstances, such a configuration would endow a positive label in the dataset. We then surrounded either side of this configuration with sequences that are least activating for a random ordering of filters. We randomly strung together a random ordering of such sequences to pad out a 500 bp example.

Interpretable sequence design

To design novel sequences intrepretably using ARGMINN, we started with our ARGMINN model trained on HepG2 DNase accessibility. We extracted motifs from the filters as described above. Prior to designing, we trimmed and filtered the motifs. Specifically, we first cut off flanks with information content lower than 0.2. We then required that after trimming, the motif was at least 5 bp and had an average information content of 0.8. We used a uniform background for computing information content.

We then extracted the motif syntax as described above, again only using the test set. This procedure takes each input sequence and assigns it a motif pattern (e.g., “CTCF - TEAD” or “FOXA” or “CTCF - FOXA - FOXA”). The motif pattern denotes which motifs were identified by ARGMINN in that sequence (in order) (e.g., CTCF followed by TEAD). Over the entire test set, we labeled each sequence with its motif pattern. For each pattern which has more than one motif, ARGMINN then gives a set of spacings that were identified over all sequences with that pattern.

We took the top 20 patterns (by number of sequences which have that pattern, requiring at least 5 sequences with that pattern). For each of the top 20 patterns, we generated 100 novel sequences with that pattern. To construct a novel sequence for a pattern, we started with an original 500 bp test sequence which falls under that pattern (sampled randomly). We then dinucleotide-shuffled the central 300 bp to destroy any functional motifs. We then inserted the motifs of that pattern (sampling from the ARGMINN-learned PFM(s)), at spacings sampled from the empirical distribution for that pattern (for single-motif patterns, the motif was simply placed in the center).

To validate our generated sequences in silico , we used several independently trained models as oracles:

Interpretations from ARGMINN itself were used to generate these sequences, but we also used ARGMINN as a predictive oracle, as it predicts accessibility from DNA sequence.

We used Borzoi ( Linder et al. 2023 ) as a predictive oracle. Specifically, we used output task 1510 (trained on ENCFF577SOF), which also measured HepG2 DNase accessibility. Whereas we designed 500 bp sequences, Borzoi predicts entire signal-profile tracks from an extremely large context (524000 bp inputs). To evaluate our 500 bp sequences, we took the original coordinate from which the sequence arose, and padded it with the appropriate genomic context on either side to from the full 524 kb input. To produce a scalar prediction, we summed the center of the (binned) profile prediction corresponding to the central 500 bp input.

We fine-tuned Enformer ( Žiga Avsec et al. 2021a ) on HepG2 DNA accessibility measured by massively parallel reporter assays (MPRAs). We downloaded the MPRA data from Gosai et al. 2023 , and verified that the predictive performance was on-par with the performance recorded in Gosai et al. 2023 . The fine-tuning was performed using the gReLU software package.

We fine-tuned Enformer using gReLU, using binary labels of HepG2 DNase accessibility from a different ENCODE expriment (ENCSR291GJU) from the one ARGMINN was trained on.

We computed significance of the difference in predicted accessibility (e.g. generated vs. background, or generated vs. natural) using a one-sided Wilcoxon test.

Expressivity requirement for REST binding

In order to demonstrate the expressivity and interpretability of ARGMINN compared to ExplaiNN, we constructed a simulated REST dataset which explicitly tests the requirements of the unique binding syntax of REST. In this dataset, positive sequences always had the left and right motifs (in that order) with 10 bp in between. Negative sequences were structured as follows: 10% have only the left motif; 10% have only the right motif; 50% have both the left and right motifs but in improper order or orientation (e.g., the reverse-complement of left and right in that order, or the left with the reverse of the right, etc.), with each configuration having a 10 bp spacer and being selected uniformly at random; 30% have two left or two right motifs, of all sorts of configurations (e.g., forward or reverse), each having a 10 bp spacer and being selected uniformly at random; 10% are uniform background.

Filter regularization on standard CNN

We applied our filter regularization to a standard CNN architecture, using the same loss weights and annealing schedule as described above. We assigned identities to these motifs also using the procedure with TOMTOM as described above.

ARGMINN loss-weight robustness

To evaluate the robustness of ARGMINN to the weights of the filter-overlap loss and the filter-L1 loss, we trained ARGMINN on the simulated SPI1 dataset 100 times, each time with a randomly selected loss weight. The filter-overlap loss weight was randomly selected between λ o ∈ [ 10 1 , 10 8 ] \lambda_{o}\in[10^{1},10^{8}] and the filter-L1 loss weight was randomly selected between λ l ∈ [ 10 − 5 , 10 0 ] \lambda_{l}\in[10^{-5},10^{0}] , where sampling was done uniformly on a logarithmic scale. We trained each model to completion as described above.

To evaluate the motif interpretability of each model, we extracted motifs from each ARGMINN model as described above. For each model, we then we computed the average similarity of all the discovered motifs to the true SPI1 PFM (similarity was computed as the − log ⁡ ( q ) -\log(q) score from TOMTOM). If a discovered motif was not similar enough to the true PFM to pass TOMTOM’s thresholds, it was given a − log ⁡ ( q ) -\log(q) value of 0 by default.