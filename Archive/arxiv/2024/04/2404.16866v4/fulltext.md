## Annotation-guided Protein Design with Multi-Level Domain Alignment DOI: XXXXXXX.XXXXXXX Conference: Make sure to enter the correct conference title from your rights confirmation emai; June 03–05, 2018; Woodstock, NY ISBN: 978-1-4503-XXXX-X/18/06 CCS: Applied computing Computational biology

The core challenge of de novo protein design lies in creating proteins with specific functions or properties, guided by certain conditions. Current models explore to generate protein using structural and evolutionary guidance, which only provide indirect conditions concerning functions and properties. However, textual annotations of proteins, especially the annotations for protein domains, which directly describe the protein’s high-level functionalities, properties, and their correlation with target amino acid sequences, remain unexplored in the context of protein design tasks. In this paper, we propose P rotein- A nnotation A lignment G eneration (PAAG), a multi-modality protein design framework that integrates the textual annotations extracted from protein database for controllable generation in sequence space. Specifically, within a multi-level alignment module, PAAG can explicitly generate proteins containing specific domains conditioned on the corresponding domain annotations, and can even design novel proteins with flexible combinations of different kinds of annotations. Our experimental results underscore the superiority of the aligned protein representations from PAAG over 7 prediction tasks. Furthermore, PAAG demonstrates a significant increase in generation success rate (24.7% vs 4.7% in zinc finger, and 54.3% vs 22.0% in the immunoglobulin domain) in comparison to the existing model. We anticipate that PAAG will broaden the horizons of protein design by leveraging the knowledge from between textual annotation and proteins.


## 1. Introduction

Protein design ( Marshall et al. 2019 ) is a crucial task for its immense potential on drug discovery ( Sliwoski et al. 2014 ; Wu et al. 2024 ) , enzyme engineering ( Sterner et al. 2008 ) , immunongineering ( Swartz et al. 2012 ) and so on. The generation of proteins with specific properties, behaviors, or functions, such as optimizing the binding affinity to given molecules ( Houk et al. 2003 ; Zhao et al. 2023 ) or incorporating a particular ion-binding site ( Regan 1995 ) , is known as de novo protein design. This process presents a significant challenge due to the vast space of protein sequences and the complexity of protein functions. Recently, machine learning models have shown profound potential for protein design. The existing studies mostly rely on the structural ( Watson et al. 2023 ) or evolutionary information ( Alamdari et al. 2023a ) as the guidance to design proteins. However, in many cases, these conditions can only offer indirect guidance towards the desired protein design targets to their inherent ambiguity. For example, the same protein sequence segment can be either act as receptors to regulate synaptic function ( Stathakis et al. 1997 ) or helpers to locate target proteins to specific subcellular locations ( Mohandas et al. 1995 ) .

In addition to the structural and evolutionary information, the current protein dataset, such as Swiss-Prot ( Bairoch and Apweiler 2000 ) and UniProtKB ( Consortium 2022 ) , contains rich textual annotations derived from wet laboratory experiments and literature. Figure 1 illustrates an example of the textual annotations on the zinc-finger protein. Generally, these annotations can be categorized into property annotation and domain annotation . Property annotation represents a piece of text that depicts the global property of proteins, such as protein names, number of amino acids, subcellular localization ( Almagro Armenteros et al. 2017 ) and thermostability ( Dallago et al. 2021 ) . Conversely, domain annotation pertains to the knowledge derived from the local domain ( Drenth et al. 1968 ) of proteins, which is a subregion of amino acid sequence that is self-stabilizing and represents certain structural and functional aspects of the protein. These annotations provide both coarse and fine-grained information regarding protein’s functions, properties, and interactions, thereby encompassing knowledge with the potential to guide the generation and design of novel proteins.

For instance, as one of crucial functional domains of DNA/RNA binding proteins ( Cassandri et al. 2017 ) , the zinc-finger domain naturally has many variants, such as C2H2 type, CCHC type and Zinc ribbon type. These variants exhibit significant differences in both structural and evolutionary features among them which is hard covered by structural and evolutionary conditions. On the contrary, the “zinc-finger” annotation from the protein database inherently provides a more effective means of describing the high-level knowledge span across both sequences and structures. Hence, we aim to investigate the following question: Is it possible to leverage such textual annotations to guide the delicate controllable protein design?

Recently, several primary attempts have been made to leverage such textual annotations to guide the protein generation. Examples include training an individual protein caption model to guide the diffusion generation process ( Ingraham et al. 2023 ) , and incorporating the an overall text description through a global language-to-protein alignment model ( Liu et al. 2023b ) . However, current models cannot flexibly combine the different conditions and lack of the capability for fine-grained control, such as specifying the generation of particular domains.

To fill these gaps, in this paper, we introduce a novel framework, P rotein- A nnotation A lignment G eneration(PAAG), that enables annotation-guided protein design by aligning protein sequences with their textual annotations. Specifically, we first consider both property and domain annotations in proteins and design a multi-level alignment module to align the representations of sequences and annotations extracted from the existing encoders in both global and local level. For the generation task, PAAG utilizes an autoregressive decoder to generate protein sequences guided by the aligned representation of textual annotations. Additionally, PAAG employs an end-to-end training pipeline that joint training of alignment and generation tasks without freezing the parameters in sequence and text encoders. This joint training enhances the understanding of the complex and flexible annotation condition, resulting in improved guided generation. Figure 1 demonstrates an example of annotation-guided generation. In experiments, we first investigate the quality of protein representations from PAAG by seven predictive downstream tasks. PAAG surpasses state-of-the-art baseline with an average relative improvement of 1.5%. Subsequently, three protein generation tasks are conducted to assess the capabilities of PAAG. In the case of unconditional generation, PAAG produces sequences exhibiting the highest degree of novelty while maintaining the distribution of natural proteins. For the two conditional protein design tasks, PAAG demonstrates a nearly threefold increase in generation success rate (24.7% vs 4.7% in zinc finger, and 54.3% vs 22.0% in the immunoglobulin domain) 1 1 1 This is the success rate with quality threshold e = 1 e=1 , i.e., SR 1 \text{SR}_{1} . in comparison to the existing model. Our contributions are summarized as follows:

We propose the first annotation-guided protein design paradigm, integrating local and global annotation information. Our proposed framework PAAG is the first approach that can generate proteins containing specific domains, guided by their corresponding annotations with high success rate.

PAAG features a multi-level alignment module for handling annotation and protein data alignment at various granularities. Joint training of alignment and generation tasks allows the model to produce improved protein representations, consequently boosting performance in predictive and generative tasks.

Comprehensive experiments on 7 predictive and 3 generative tasks showcase PAAG’s superiority compared to the existing methods. Notably, PAAG is not only capable of generating proteins that include a single annotation, but it also successfully generates proteins adhering to the flexible conditions of multiple annotation combinations.


## 2. Preliminaries


## 2.1. Protein and Its Textual Annotations

The primary structure of a protein can be represented as an amino acid sequence S = ( s 1 , s 2 , ⋯ , s n ) S=(s_{1},s_{2},\cdots,s_{n}) , where s i s_{i} is the i i -th amino acids chosen from 20 different amino acids which are represented as 20 characters. Given a protein S S , the annotation-sequence pair set 𝒟 S = { ( T k , S i : j k ) } k = 1 K S \mathcal{D}_{S}=\{(T_{k},S^{k}_{i:j})\}_{k=1}^{K_{S}} is constructed by extracting the correspondence between textual annotations and protein domains & properties from protein database, such as UniProtKB ( Consortium 2022 ) , where T k T_{k} is the textual annotations of the k k -th domain S k i : j S^{k}_{i:j} of the protein and K S K_{S} is the number of annotation-domain pairs of the protein S S . For the property annotation, the corresponding domain is the entire sequence, i.e, S 1 : | S | S_{1:|S|} . This annotation-domain pair set 𝒟 S \mathcal{D}_{S} provides comprehensive knowledge about the protein S S and, therefore, plays an important role in training the protein generation model.


## 2.2. Encoders for Proteins and Annotations

We adopt a protein encoder (PE) to generate both the protein and its domain representations based on the amino acid sequence as 𝒛 S = f PE ​ ( S ) \bm{z}_{S}=f_{\text{PE}}(S) , where f PE f_{\text{PE}} is the protein encoder and 𝒛 S \bm{z}_{S} is the embedding of S S . For textual annotations, we generate their representations using the pre-trained language model f LM f_{\text{LM}} as 𝒛 𝒜 S = f LM ​ ( G ⁡ ( 𝒜 S ) ) \bm{z}_{\mathcal{A}_{S}}=f_{\text{LM}}(G(\mathcal{A}_{S})) , where 𝒜 S ⊆ { T k | ( T k , S i : j k ) ∈ 𝒟 S } \mathcal{A}_{S}\subseteq\{T_{k}|(T_{k},S_{i:j}^{k})\in\mathcal{D}_{S}\} is a subset of the annotations in the annotation-domain pair set for a protein S S , G ⁡ ( ) G() is a template function which converts a set of annotations to a textual description, the details of G ⁡ ( ) G() can be found in Appendix A.2 , and 𝒛 𝒜 \bm{z}_{\mathcal{A}} is the embedding of the annotation set. Note that the annotation subset can cover all annotations in 𝒟 S \mathcal{D}_{S} or just one. If 𝒜 S \mathcal{A}_{S} covers only one annotation T 0 T_{0} , we can skip the template function and directly generate the embedding of T 0 T_{0} using f LM f_{\text{LM}} .

We employ transformer-based protein encoder and text encoder as our base model and initialize them with pre-trained models. Specifically, we employ SciBERT ( Beltagy et al. 2019 ) , which is pre-trained on computer science and biological datasets, to initialize the text encoder f LM f_{\text{LM}} . The pre-trained protein encoder, ProtBERT ( Elnaggar et al. 2021 ) , is used to initialize the protein encoder f PE f_{\text{PE}} .


## 3. Methodology

In this section, we propose a novel framework, P rotein- A nnotation A lignment G eneration(PAAG), which enables the flexible annotations-guided protein design. Figure 2 illustrates the overall framework of PAAG. In the following, we present the details of each component of PAAG.


## 3.1. Multi-level Protein and Annotation Alignment

We will first employ template function G G to translate these annotations as textual descriptions and then utilize a language model to extract the representation of the annotation set 𝒛 𝒜 = f LM ​ ( G ⁡ ( 𝒜 ) ) \bm{z}_{\mathcal{A}}=f_{\text{LM}}(G(\mathcal{A})) . Then the protein sequence is generated using a decoder f D f_{D} based on this representation as S = f D ​ ( 𝒛 𝒜 ) S=f_{\text{D}}(\bm{z}_{\mathcal{A}}) .

To better integrate the information between proteins and annotations, we aim to align the multi-level representations of proteins and annotations. Specifically, we conduct local alignment and global alignment by performing contrastive learning at domain level and protein level, respectively.

We measure the alignment score using the cosine similarity between the embeddings of protein and the annotation set, which is defined as

where Proj a ​ ( 𝒛 ) = 𝑾 a ​ 𝒛 + 𝒃 \text{Proj}_{a}(\bm{z})=\bm{W}_{a}\bm{z}+\bm{b} projects the input 𝒛 \bm{z} into a latent space with dimension h h . 𝑾 a ∈ ℝ h × | 𝒛 | \bm{W}_{a}\in\mathbb{R}^{h\times|\bm{z}|} and 𝒃 ∈ ℝ h \bm{b}\in\mathbb{R}^{h} are trainable parameters. During alignment, we encourage the matched (positive) pairs to have representations with higher similarity s s than unmatched (negative) pairs. We next will explain in detail how to construct the positive and negative pairs in our multi-level framework.

Given a protein S S , and its annotation-domain pairs set 𝒟 S \mathcal{D}_{S} , in domain-level, we aim to align the representation of the domain S k i : j S^{k}_{i:j} and its corresponding annotation T k T_{k} and use all annotation-domain pairs in 𝒟 S \mathcal{D}_{S} as positive pair. To construct the negative pairs, we randomly sample the sub-regions outside the domain S k i : j S^{k}_{i:j} , i.e. S k 1 : i − 1 ∪ S k j + 1 : l S^{k}_{1:i-1}\cup S^{k}_{j+1:l} , as the negative samples S k − i : j S^{k-}_{i:j} of the domain.

Annotation-Domain Contrastive(ADC) Loss: In designing this loss, since our objective is on identifying functional regions within proteins, we consider amino acid sequences from the same protein as negative samples. Specifically, we adopt InfoNCE loss as the ADC loss to align the representations of local annotation 𝒛 T \bm{z}_{T} and functional domain 𝒛 S i : j \bm{z}_{S_{i:j}} as

where K S K_{S} is the number of functional domains for the protein S S , N N is the number of negative samples, and τ \tau is a learnable temperature parameter.

The local alignment enables PAAG to explicitly learn the relation between the functional domain and its annotation. Therefore, we can use the model to controllably generate the specific functional domain given annotations.

To enable global alignment, we utilize template function G ⁡ ( ⋅ ) G(\cdot) to construct protein-level textual description and form the positive protein-description pairs as { ( G ⁡ ( 𝒜 S ) , S ) } \{(G(\mathcal{A}_{S}),S)\} . Since multiple annotations and the entire protein will be more complex, to enlarge the number of negative samples for global alignment, we follow the setting of MOCO ( He et al. 2020 ) to construct momentum encoders f m f_{m} as:

where the encoder f f can be either protein encoder f PE f_{\text{PE}} or text encoder f LM f_{\text{LM}} , and m m is the momentum hyperparameter. We follow implementation details in ( Li et al. 2021 ) and ( Li et al. 2022 ) to construct the momentum encoders for both encoders. The momentum encoders extract consistent features to increase the number of negative samples, and the dynamic dictionaries will store these features.

Annotation-Protein Contrastive (APC) Loss is designed to align the representations of global properties 𝒛 𝒜 \bm{z}_{\mathcal{A}} with protein 𝒛 S \bm{z}_{S} . Specifically, for each protein sequence and annotation set, we calculate the softmax-normalized sequence-to-annotation and annotation-to-sequence similarity as:

where τ \tau is a learnable temperature parameter, A m A_{m} and S m S_{m} indicate their representations will be extracted by respective momentum encoders.

Denote y → a2s ​ ( A ) \vec{y}^{\mathrm{~a2s}}(A) and y → s2a ​ ( S ) \vec{y}^{\mathrm{~s2a}}(S) as the ground-truth one-hot similarity, where negative pairs have a probability of 0 and the positive pair has a probability of 1. The annotation-protein contrastive loss is defined as the cross-entropy H \mathrm{H} between p → \vec{p} and y → \vec{y} :

Through APC loss, PAAG aligns the representations of two modalities, improving the quality of aligned representation, which is crucial for downstream tasks such as classification and regression.

Annotation-Protein Matching (APM) Loss . Inspired by ( Li et al. 2022 ) , we introduce a multi-modal encoder f ME f_{\text{ME}} , which integrates the representation of annotations and protein as 𝒛 S , 𝒜 M = f ME ​ ( S , G ⁡ ( 𝒜 ) ) \bm{z}_{S,\mathcal{A}}^{M}=f_{\text{ME}}(S,G(\mathcal{A})) , to identify whether the given pairs of protein description G ⁡ ( 𝒜 ) G(\mathcal{A}) and protein S S are matched or not. Specially, the multimodal encoder f ME f_{\text{ME}} is transformer-based and shares the parameters of self-attention and feed-forward layers with f PE f_{\text{PE}} and has additional cross-attention layers between self-attention layers and feed-forward layers to integrate the text information. The cross-attention layers share the same cross-attention parameters as the decoder.

Annotation-Protein Matching (APM) Loss aims to facilitate the learning of multimodal representations. Additionally, we use the hard negative strategy, where we first select the most similar negative pairs and then use these most challenging negative pairs to optimize the model through in the training of the model with the APM loss, enabling the encoder to learn informative representations. To construct the APM loss, we extract the multi-modal representation as 𝒛 S , 𝒜 M = f ME ​ ( S , G ⁡ ( 𝒜 ) ) \bm{z}_{S,\mathcal{A}}^{M}=f_{\text{ME}}(S,G(\mathcal{A})) and use a classifier to classify its probability of being positive or negative, which is denoted by p → APM ​ ( 𝒜 , S ) \vec{p}^{\textrm{APM}}(\mathcal{A},S) . And we compute the cross-entropy between the ground-truth label y → APM ​ ( A , S ) \vec{y}^{\textrm{APM}}(A,S) indicating the protein-description pair being positive or negative to obtain the APM loss as

APM loss trains the cross-attention layers for integrating two modalities. These cross-attention will be shared with protein decoder, which helps protein decoder interpret textual information. In Sec. 4.7 , we demonstrate the importance of APM loss.


## 3.2. Conditional Protein Decoding

Protein Decoder. Our ultimate goal is generating functional proteins conditioned on a set of annotations 𝒜 = { T k } k = 1 K \mathcal{A}=\{T_{k}\}_{k=1}^{K} . We adopt an auto-regressive protein decoder f D f_{\text{D}} that can receive the condition from the language model. Specifically, the decoder will first process the protein sequence through causal attention layers to enable auto-regressive generation, then integrate the information from annotations via cross-attention layers followed by feed-forward layers. Note that the causal attention layers are initialized using the same weights as the self-attention layers in the protein encoder and the feed-forward layers share the same parameters as the protein encoder. Here, the parameter-sharing mechanism enables higher training efficiency ( Li et al. 2023 ) . The cross-attention layers are randomly initialized and trained from scratch.

Protein Modeling (PM) Loss . To guide the learning of the model, we estimate the PM loss as

where l l is the length of the protein S S and p ⁡ ( S i | S < i ; 𝒜 ) p(S_{i}|S_{<i};\mathcal{A}) is the predicted probability of the i i -th amino acid given all previous amino acids and the annotation set.


## 3.3. Training Objectives

In the training of PAAG, we optimize four objective functions. These functions are designed to align the representations between annotations and protein sequences, integrate the two modalities, and reconstruct the protein sequence. In contrast to ProteinDT ( Liu et al. 2023a ) , which splits the training process into three separate stages, PAAG jointly optimizes these four objective functions in an end-to-end manner. The overall pretraining objective of PAAG is :


## 3.4. Annotation-guided Protein Design

After obtaining the model F F of PAAG, we can use F F to design the proteins with given textual annotations. In the following, we given the definition of annotation-guided protein design.

Given an annotation set 𝒜 = { T k } k = 1 K \mathcal{A}=\{T_{k}\}_{k=1}^{K} with K K annotations, a generative model F F can leverage the information from { T k } k = 1 K \{T_{k}\}_{k=1}^{K} to generate the protein S S which satisfies the condition described in { T k } k = 1 K \{T_{k}\}_{k=1}^{K} . Quantitatively, this task aims to maximize the following objective function:

where M T ​ ( ⋅ ) \mathrm{M}_{T}(\cdot) is metric function for the annotation T T .

In this paper, we mainly focus on two type of metrics, functional-domain metric and global-property metric .

Functional-domain metric : for the annotation describing a certain functional domain, M T ​ ( ) \mathrm{M}_{T}() will invoke a profile hidden Markov models from Pfam ( Mistry et al. 2021 ) to search for the optimal match within protein S S regarding to the domain described by annotation T T and assign an e-value s s to this match. Given an e-value threshold e e , we have:

where 𝟙 S ​ ( cond ) \mathds{1}_{S}(\text{cond}) outputs 1 1 when cond = True \text{cond}=\text{True} , otherwise, outputs 0 0 .

Global-property metric : for the annotations describing protein’s global properties, M T ​ ( ) \mathrm{M}_{T}() employ a pre-defined oracle to determine if the given S S has the property described by the annotation T T and output a score s s in the range of [ 0 , 1 ] [0,1] . Here, 0 denotes the absence of the property, while 1 signifies its presence.


## 4. Experiment

In this section, we extensively evaluate PAAG from two aspects: (1). quality of aligned protein representation for the predictive tasks; (2) evaluation on the unconditional sequence generation and protein design with textual annotations.


## 4.1. Construction of ProtAnnotation Dataset

To enable multi-level alignment, we build the ProtAnnotation dataset with annotation-sequence pair set for protein design task. Specifically, we select the proteins with “Domain” entry in UniProtKB ( Consortium 2022 ) to build ProtAnnotation dataset.

However, since the biases within our training dataset will significantly impact the performance of PAAG, we limit our selection to protein-annotation pairs from a refined subset of UniProtKB, namely Swiss-Prot. Each entry in Swiss-Prot has been manually reviewed and supplemented with detailed information with protein function, structure, and interactions. Ultimately, the ProtAnnotation consists of 129,727 proteins. Moreover, in our alignment, we incorporate temperature ( Wu et al. 2018 ) to control the similarity scores of distribution between positive and negative pairs. An appropriate temperature can soften these scores, making the model less sensitive to noisy samples. This adaptability allows the learning process to focus more on meaningful correlations and reduce the impact of irrelevant variations, ultimately enhancing the PAAG’s robustness.

The domain annotations are extracted by these “Domain” entries including the domain description and start & end index of this domain. Additionally, we select four properties as the property annotations, that is, “protein_name”, “organism_name”, “length” and “SIMLARITY”. The textual description is assembled by the template function G G , which can accept any subset of annotation as input. More details, including the data examples are deferred in Appendix A.2 .


## 4.2. Quality of Aligned Representation

We first conduct multiple experiments on predictive tasks, to evaluate the quality of protein representation produced by PAAG.

Settings: To make a fair comparison with ProtST, we use the same proteins in dataset ProtDescribe ( Xu et al. 2023 ) to first pretrain PAAG, followed by full-model fine-tuning on various downstream tasks. For the full-model fine-tuning, we add a task head for each task and fine-tune the model for 100 epochs. We use the validation set to select the model and report the results on random seed 0, adhering to the same settings as in ProtST ( Xu et al. 2023 ) . More details are deferred in Appendix A.6 .

Benchmark Tasks: We adopt 7 downstream tasks within two task types as the benchmark task.

Protein Localization Prediction aims to forecast the subcellular locations of proteins. Derived from DeepLoc ( Almagro Armenteros et al. 2017 ) , we focus on two similar tasks. The subcellular localization prediction ( Abbr. as , Sub) encompasses 10 location categories and binary localization prediction ( Abbr. as , Bin) that includes 2 location categories, soluble and membrane-bound. The splits of data follow the original split in DeepLoc.

Fitness Landscape Prediction is primarily focused on the prediction of the effects of residue mutations on the fitness of proteins. We evaluate our models on β \beta -lactamase ( Abbr. , β \beta -lac) landscape from PEER ( Xu et al. 2022 ) , the AAV and Thermostability ( Abbr. , Thermo) landscapes from FLIP ( Dallago et al. 2021 ) , and the Fluorescence ( Abbr. , Flu) and Stability ( Abbr. , Sta) landscapes from TAPE ( Rao et al. 2019 ) . The splits of data follow the splitting setting of ProtST ( Xu et al. 2023 )

Baselines: We adopt two types of baseline. The first type is the models trained from scratch, including CNN ( Shanehsazzadeh et al. 2020 ) , ResNet ( Rao et al. 2019 ) , LSTM ( Rao et al. 2019 ) , Transformer ( Rao et al. 2019 ) . The second type is the pre-trained models with full model tuning, including OntoProtein ( Zhang et al. 2022 ) , ProtBert ( Elnaggar et al. 2021 ) and ESM2 ( Lin et al. 2023 ) . For the ProtST and PAAG, we train two variants with different initialization weights from ProtBert and ESM2 to verify the enhancement of text knowledge on protein representations from different protein encoders. We utilize distinct subscripts to denote the initialized parameters, such as PAAG ProtBert \text{PAAG}_{\text{ProtBert}} and PAAG ESM2 \text{PAAG}_{\text{ESM2}} .

Results: Table 1 reports the results of all models on seven baselines. As illustrated in Table 1 , PAAG achieves superior performance in comparison to the baselines on all 7 tasks. These results highlight the robust generalization capabilities of PAAG for downstream tasks. Specifically, PAAG outperforms the vanilla pretrained models, ProtBert and ESM2, in all cases, indicating that PAAG can further enhance the quality of protein representation by incorporating the knowledge from textual annotations. According to the results in Table 1 , multi-modal training has a positive influence on the performance of downstream tasks in both ProtST and PAAG. Additionally, the performance improvement of PAAG surpasses that of ProtST in 10 out of 14 cases, further validating the effectiveness of PAAG in augmenting the quality of protein representation.


## 4.3. Unconditional Protein Generation

To verify the learning effect of the decoder, we compare the ability of different models in unconditional generation task. A good decoder is able to generate protein sequences that conform to the distribution of the training set while simultaneously exhibiting adequate novelty.

Setting: In unconditional generation task, we only specify the length of generated proteins and conditions. We sample the same length from natural proteins, to ensue a fair comparisons across different models.

Baselines: We compare PAAG with 3 representative protein design models, i.e. , ProGen ( Madani et al. 2023 ) , Chroma ( Ingraham et al. 2023 ) and ProteinDT ( Liu et al. 2023b ) . Furthermore, we introduce two naive baselines: Random Uniform {}_{\text{Uniform}} and Random Empirical {}_{\text{Empirical}} . Random Uniform {}_{\text{Uniform}} generates protein sequence by randomly selecting amino acids based on a uniform distribution, while Random Empirical {}_{\text{Empirical}} adheres to the empirical amino acid distribution in the training dataset. Additionally, we report the results of the sequence set sampled from natural proteins, denoted as Natural, to serve as a reference. The details of baselines are in Appendix A.5 .

Evaluation metrics: To evaluate the quality of generated protein sequences, we employ three metrics: Distinct-n, Diversity and Novelty. Suppose 𝒮 \mathcal{S} is the protein sequence set.

Distinct-n ( Li et al. 2016 ) is a classical metric in natural language processing that measures textual diversity of generated text by counting distinct n-grams. We use normalized Distinct-n to assess the fraction of repetitive sequence motifs in sequences from 𝒮 \mathcal{S} , which exhibits the biological importance ( Andrade et al. 2000 ) . A higher Distinct-n suggests fewer repetitive amino acid segments. We set n = 2 n=2 here.

Diversity measures the dissimilarity of sequences in 𝒮 \mathcal{S} . We employ Mmseq2 ( Steinegger and Söding 2017 ) to compute the dissimilarity between each pair of sequences, and utilize the mean of these dissimilarities as Diversity. A higher Diversity signifies a greater diversity in 𝒮 \mathcal{S} .

Novelty measures the novelty of sequences in 𝒮 \mathcal{S} compared to a reference set. We take UniprotKB ( Consortium 2022 ) as the reference set. For each sequences in 𝒮 \mathcal{S} , we employ Mmseq2 ( Steinegger and Söding 2017 ) to return the dissimilarity score of the most similar sequence in UniprotKB. Novelty is defined as the mean of dissimilarity score for all sequences in 𝒮 \mathcal{S} . A higher Novelty indicates the generated sequences exhibit substantial novelty comparing with the reference set.

Results: Table 2 shows the results of unconditional generation under three metrics. From Table 2 , we can observe that:

PAAG achieves the highest novelty, indicating PAAG captures the intrinsic relationship between amino acids, rather than merely memorizing protein sequences in the training set.

PAAG exhibits the closest Distince-n score compared with natural proteins, which proves that proteins generated by PAAG possess similar amino acid distribution as natural proteins.

Since Random Empirical {}_{\text{Empirical}} generates protein sequence following the empirical amino acid distribution in the natural proteins, it is reasonable to obtain the closest diversity to natural proteins. Compared with other learning-based model, PAAG still maintains the closest diversity to natural proteins proving PAAG has the similar distribution at protein level.

ProGen and Chroma have considerably lower Distince-n score in comparison to PAAG and natural proteins, implying an abundance of repetitions within generated protein sequence. While ProteinDT has higher Distince-n score, it also fails to capture the intrinsic amino acid distrbution in natrual proteins.

In a summary, PAAG is capable of generating high-quality protein sequences, aided by the the multi-level alignment process.


## 4.4. Protein Design with Domain Annotations

In this section, we evaluate the performance of PAAG in generating proteins under the given domain annotations.

Settings: We utilize two biologically significant domains, zinc-finger domain ( Klug and Rhodes 1987 ) and immunoglobulin domain ( Brummendorf 1995 ) , as the target domain annotation to generate the proteins respectively. For each case, we generate N = 300 N=300 protein sequences given the length of the proteins and the annotation set containing the domain annotations of “zinc-finger” or “immunoglobulin domain”. For all models, the protein sequences are generated with the same length sampled from natural proteins that have corresponding domain in UniprotKB. To further evaluate the generalization ability of PAAG, we further test our model on generating proteins with EGF-like domain. The details can be found in Appendix A.7.1 .

Based on ( 11 ), we further define a metric: success rate SR e = M T , e ​ ( S ) N \text{SR}_{e}=\frac{M_{T,e}(S)}{N} to measure the generation quality with the proportion of proteins that successfully identify the specific domain with the quality threshold e e .

Model training: We train PAAG on ProtAnnotation for total 100 epochs, employing a learning rate of 3e-5 and incorporating a warm-up phase with a batch size of 32. Additionally, we extract a subset of ProtAnnotation which only contains proteins with “zinc-finger” and “immunoglobulin domain”. This subset is subsequently utilized to fine-tune the model over 5 epochs, adopting a learning rate of 1e-5 and maintaining the batch size at 32. We denote this fine-tuned version as PAAG ft \text{PAAG}_{\text{ft}} , and the PAAG without fine-tuning is denoted as PAAG. The generalization ability of PAAG ft \text{PAAG}_{\text{ft}} is also evaluated in A.4 . More details are deferred to Appendix A.7.2 .

Baselines: We adopt ProtenDT ( Liu et al. 2023b ) , Chroma ( Ingraham et al. 2023 ) and ProGen ( Madani et al. 2023 ) as the baselines due to their public availability of model weights and their capacity to accept text and keywords as conditional inputs for protein generation. ProGen utilizes keywords as its condition tags. Here, we take the keywords correspond to zinc-finger (“KW-0863”) and immunoglobulin domain (“KW-0393”) in Uniport to generate functional proteins. Chroma adopts ProCap to understand the textual conditions to guide its diffusion process. We give the same text prompts to Chroma to enable its controllable generation. We also include two trivial baselines Random Uniform {}_{\text{Uniform}} and Random Empirical {}_{\text{Empirical}} as the blank references.

Results: In Figure 3 (a) and (b), we plot the curves depicting the variation in success rate SR e \text{SR}_{e} for different models in two protein design tasks as the quality threshold e e varies from 0.001 to 100. Additionally, in Figure 3 (c) and (d), we employ violin plots to illustrate the distribution of e-value e e for generated sequences matched in Pfam. Due to Pfam’s limitations, e-values exceeding 100 are adjusted to the maximum e-value score among all method results for the current task. We also show the distribution of e-values calculated on natural proteins with domains as a reference. From Figure 3 , we can observe that:

PAAG achieves significantly higher success rates SR 1 \text{SR}_{1} across all tasks by a large margin, e.g. , 51 % 51\% versus 22 % 22\% in immunoglobulin domain task with quality threshold e = 1 e=1 . Furthermore, the fine-tuned P ​ A ​ A ​ G f ​ t PAAG_{ft} can further improve the success rates (54.3% on SR 1 \text{SR}_{1} ) consistently, indicating the finetuning process can help to further improve the quality.

ProGen and ProteinDT outperform other baseline methods. This may be due to they memorizing proteins with zinc and lg domain in the training data and output them when using keywords or textual prompts.

Chroma’s performance is not good, resembles the unconditioned results. This may be because Chroma’s training text primarily focuses on structural descriptions, making it less sensitive to the domain annotations.

Visualizations: We provide the visualization of generated proteins, folded by Omegafold ( Wu et al. 2022 ) , in Figure 4 . The figure 4 highlights generated domains in red and provides textual descriptions and e-value e e for each sequence. We observe the generated sequences accurately produce target domains as specified in the annotation set. Interestingly, in scenarios such as two zinc finger cases, when the prompt specifies the presence of multiple zinc finger domains, PAAG generates multiple functional domains in response. However, PAAG fails to capture the precise numbers of these domains, which can be a direction for future improvement.

Prompt : We further investigate the relationship between the number of domains in prompts and the proteins generated by PAAG. By varying only the domain count in prompts, we generate 900 proteins with ‘Small (1-3)’, ‘Median (4-6)’, and ‘Large (7-9)’ number of domains. Figure 5 shows that increasing domain numbers in prompts leads to a corresponding rise in generated domains across different e-values, indicating that PAAG can discern and generate the specified number of domains from text prompts through multi-level alignment. Given these observations, another interesting question is whether multiple domains in prompt will increase success rates. To this end, we re-evaluate PAAG using prompts specified only one domain (PAAG single domain {}_{\text{single domain}} ). The results are in Table 8 in Appendix. We can find while multiple domains improve success rates, PAAG single domain {}_{\text{single domain}} also outperforms the baselines, confirming the importance of multi-level alignment.


## 4.5. Protein Design with Property Annotations

In this section, we explore the potential of PAAG to generate proteins with certain properties guided by property annotations.

Settings: We employ the subcellular location of proteins as an example property. An additional dataset, termed ProtLocation, is generated by extracting subcellular location labels, encompassing Bin (2-class) task as delineated in Section 4.2 , from Deeploc ( Almagro Armenteros et al. 2017 ) . These labels are then incorporated into annotation-sequence pairs derived from Uniprot. ProtLocation includes 10100 10100 proteins for training, while a separate set of 2434 2434 test proteins is reserved for constructing the annotation set for generation. More details can be found in Appendix A.6.3 .

Evaluation protocol: For the generated sequences, we employ the official server provided by Deeploc ( Almagro Armenteros et al. 2017 ) as the pre-defined oracle to construct the Global-property metric M T ​ ( ) \mathrm{M}_{T}() for predicting binary location label. A generation is deemed successful if the predicted label aligns with the input annotation label.

Results: As shown in Table 3 , PAAG achieves overall 74.78 % 74.78\% success rate, indicting PAAG captures the difference between soluble and membrane-bound, and can generate properties given corresponding property annotations. We next will move to more challenging setting, generating proteins with both domain and property annotations.


## 4.6. Case study: Joint Generation with Domain and Property Annotations

In this part, we explore the potential of PAAG in generating proteins guided by the flexible combination of different annotations. Specifically, we generate the zinc-finger proteins in membrane-bound and soluble by the model in Section 4.5 following the same protocol in Section 4.4 . Despite this challenging setting, the joint success rate SR 1 \text{SR}_{1} of generating proteins with zinc-finger and corrected property is SR 1 = 10.17 % \text{SR}_{1}=10.17\% , However, given the current success rates of other models in generating zinc-finger proteins have approached zero, the task of producing such proteins with specific domain and property annotations remains unattainable by existing models. Zinc-finger domains are naturally occurring soluble proteins involved in DNA editing. Our generation of zinc-finger proteins anchored to the membrane underscores the efficacy of PAAG in producing novel, non-existent proteins. We showcase four examples of the generated results in Figure 6 . As shown in Figure 6 , PAAG can successfully generate proteins guided by both domain and property annotations, demonstrating its potential in complex protein design tasks.


## 4.7. Ablation Study

To ascertain the contribution of each component towards the generation of the functional proteins, the ablation study reports the SR 1 \text{SR}_{1} of zinc-finger and immunoglobulin domains in the absence of each alignment loss, as presented in Table 4 . We observe that ℒ A ​ D ​ C \mathcal{L}_{ADC} is the key to the high SuccessRate of PAAG. The SuccessRate decreases to 0 % 0\% without ℒ A ​ D ​ C \mathcal{L}_{ADC} , underscoring the importance of incorporating domain range into the learning framework. Furthermore, ℒ A ​ P ​ C \mathcal{L}_{APC} and ℒ A ​ P ​ M \mathcal{L}_{APM} also enhance the SuccessRate of generating high-quality immunoglobulin domains by 4.33 % 4.33\% and 3.33 % 3.33\% , respectively. Moreover, ℒ A ​ P ​ C \mathcal{L}_{APC} and ℒ A ​ P ​ M \mathcal{L}_{APM} are more important to zinc-finger domain, by improving the SR 1 \text{SR}_{1} by 12 % 12\% and 9.67 % 9.67\% .


## 5. Related Work

Moltimodal Representation Learning. By harnessing the potential of extensive image-text pair data, the Contrastive Language-Image Pretraining (CLIP) model, as proposed by Radford et al. ( Radford et al. 2021 ) , employs contrastive learning to align the representations between image and text modalities.Following by CLIP, many image-text pertaining model are proposed, such as BILP ( Li et al. 2022 ) , BLIP-2 ( Li et al. 2023 ) , InstructBLIP ( Dai et al. 2023 ) and ClipCap ( Mokady et al. 2021 ) . Beyond the image-text pretraining, several studies introduce the more modalities, such as videos ( Xu et al. 2021 ) , audios ( Tang et al. 2023 ) and even molecules ( Liu et al. 2022 ; Zhang et al. 2024 ) into a unified representation. Specifically, for multimodal learning on protein sequences, OntoProtein ( Zhang et al. 2022 ) first learns protein representations by combining them with textual descriptions in a knowledge graph. ProtST ( Xu et al. 2023 ) constructs a large-scale dataset containing aligned pairs of protein sequences and property descriptions, and pretrain a protein-biotext model to improve performance on downstream predictive task and enables zero-shot retrieval.

Protein Generation Model. With huge success of language models ( Devlin et al. 2019 ) , several studies ( Elnaggar et al. 2021 ; Shin et al. 2021 ; Ferruz et al. 2022 ; Rives et al. 2019 ) treat protein sequences consisting chains of amino acids as a type of “languages” and pretrain models on millions of protein sequences. Upon the pretrained model, they generate the protein sequences in an autoregressive manner. In addition to the autoregressive model, Evodiff ( Alamdari et al. 2023b ) extracts the evolutionary information from protein sequences and proposes an evolution-guided diffusion model to generate protein sequences. Given the significance of structural information for protein function, a group of methods ( Hsu et al. 2022 ; Ingraham et al. 2019 ; Tan et al. 2022 ; Jing et al. 2020 ) , known as inverse folding, utilize the structure as a conditional input, allowing for the generation of amino acid sequences. Some studies ( Shi et al. 2022 ; Watson et al. 2023 ) integrate both sequential and structural information and propose a co-design model that accepts sequences and structures as conditions. Recently, ProteinDT ( Liu et al. 2023b ) first proposes a text-sequence alignment framework, enabling its capabilities for text-guided protein generation and editing. Chroma ( Ingraham et al. 2023 ) trains a protein caption model ProCap and utilize it as a classifier guidance to generate proteins via a diffusion model.

Although ProteinDT ( Liu et al. 2023b ) and ProtST ( Xu et al. 2023 ) similarly align the protein and textual representations, the multi-level alignment framework enables PAAG to capture the both local and global properties of the protein. Furthermore, the momentum encoders and an additional matching loss assist PAAG to more effectively align the protein-level annotation with the proteins.


## 6. Conclusion

This paper presents PAAG, a multi-modality framework that first incorporates the rich annotation information derived from protein database, achieving the superior performance in various applications, such as representation learning and annotation-guided protein design. Crucially, we demonstrate that it is possible to use the flexible combinations of various kinds of textual annotations to guide the protein design process. We hope that PAAG will expand the possibilities of protein design and establish a robust foundation for future advancements in protein-related applications. Future research directions include functional protein editing, co-design of protein sequence-structure within alignment frameworks, and exploring the potential of larger protein dataset with lower annotation quality.


## References


## Appendix A Experimental settings


## A.1. General settings

Backbone Models of PAAG: We use ProtBert-BFD ( Elnaggar et al. 2021 ) to initialize our protein encoder and SciBert ( Beltagy et al. 2019 ) for the text encoder. Due to limited training data, we opt for a lighter decoder initialized by DistilProtBert ( Geffen et al. 2022 ) . Exploring a decoder with more parameters is a future direction.

Training Configurations: We train PAAG on ProtAnnotation, using the AdamW optimizer (with a learning rate of 3e-5 and zero weight decay) for 100 epochs. Our generation experiments are conducted on 16 NVIDIA Tesla A100-SX4-40GB GPUs.


## A.2. ProtAnnotation and template function G ⁡ ( ⋅ ) G(\cdot)

Table 5 depicts additional statistics of ProtAnnotation. We demonstrate several example data samples in ProtAnnotation as well as the corresponding textual description generated by the template function G ⁡ ( ⋅ ) G(\cdot) .

The explanation of four property annotations:

protein_name : The protein name is a naming method used to describe the function, characteristics, or origin of a protein. These names usually contain information about the protein’s structure, function, substrate specificity, and biological process.

organism_name : Organism names are used to identify and classify different species of living organisms, including bacteria, fungi, plants, and animals. These names usually consist of the genus and species of the organism, and sometimes include additional information such as strain or cultivar.

length : The number of amino acids in the protein sequence.

SIMILARITY : In the context of biology and protein classification, “similarity” refers to the shared characteristics or features among different proteins. This can include similar structures, functions, or evolutionary origins. Proteins with high similarity are often grouped into the same family or subfamily.


## A.3. Biological background of zinc-finger and immunoglobulin domain

We here introduce zinc-finger and immunoglobulin domains, highlighting their biological significance and functions in biology.

Zinc-finger: Zinc finger ( Klug and Rhodes 1987 ) domains are compact protein motifs known for binding DNA, RNA, proteins, and lipids, with binding characteristics influenced by amino acid sequence, linker structure, and number of fingers. Despite appearing in various protein families, they maintain stable structures and are crucial in processes like gene transcription and mRNA trafficking.

Immunoglobulin domain: Immunoglobulin (Ig) domains play a key role in protein-protein interactions, especially within the immune system, where they help recognize, bind, and neutralize antigens. These domains have a conserved structure found in a variety of proteins, including antibodies and cell adhesion molecules.

Examples of Zinc-finger and Ig domains are shown in Figure 7 .


## A.4. The evaluation metric for the unconditional generation

In the computation of the Distinct-n metric, we assign a value of n n to 2 2 . For the Novelty metric, the default parameters of Mmseq2 are employed with an exception for the e-value threshold, which is designated as 100 100 . In the case of the Diversity metric, the default parameters of Mmseq2 are again utilized, but with alterations to the e-value threshold and sensitivity, set to 1000000 1000000 and 15 15 respectively. During the application of Mmseq2 for the calculation of Novelty and Diversity metrics, the dissimilarity for unmatched sequences is assumed to be 1.0 1.0 .


## A.5. More details of baselines

ProGen ( Madani et al. 2023 ) represents each protein property as keyword tags, which are prepended to amino acid sequences during training to enable auto-regressive reconstruction. This allows ProGen to generate protein sequences from keyword tags. For controllable generation, ProGen translates desired properties into keyword tags to guide sequence generation.

Chroma ( Ingraham et al. 2023 ) is a protein design model focusing on generating protein backbones. It uses classifier guidance and ProCap, a protein-to-text model, for text-guided designs. With a sequence sampling model, Chroma can generate both structure and sequence based on specified conditions.

ProteinDT ( Liu et al. 2023b ) is a text-guided protein design model that aligns protein and text representations, then uses aligned text representations to design protein sequences via autoregressive and diffusion models. For fair comparison, we use autoregressive ProteinDT as our baseline. In unconditional generation, due to the lack of a specific template in ProteinDT, we randomly sample prompts from its dataset to evaluate the quality of generated proteins. In conditional experiments, ProteinDT receives the same prompts as PAAG.

In unconditional generation, PAAG accepts only the protein sequence length l l and the order k k of protein generated, using the template: ”protein number k, contains l amino acids.” For generating proteins with functional domains, we randomly sample organism names, lengths, and similarities from natural proteins with the corresponding domains. Generative hyper-parameters are specified in A.6 . Using property annotations, we apply the template function G ⁡ ( ) G() to describe test data from the Deeploc ( Almagro Armenteros et al. 2017 ) dataset, enabling PAAG to generate proteins with specified properties.


## A.6. Training configurations

In downstream prediction tasks, PAAG uses embeddings in the aligned space by employing both the protein encoder and the projector head for more informative aligned features. Hyperparameters for predictive tasks using PAAG-ProtBert and PAAG-ESM-2 are detailed in Table 9 and Table 10 .

While training PAAG with ProtAnnotation, we incorporate momentum contrast ( He et al. 2020 ) with a queue size of 16,384 and momentum of 0.995. The learnable temperature in contrastive learning is set to 0.07, and our latent space is aligned to 256 dimensions with a linear layer. Following ( Li et al. 2022 ) , we initialize learnable alpha at 0.4 for soft labeling. When fine-tuning on datasets with only zinc-finger and immunoglobulin domains, we maintain these hyperparameters but reduce the queue size to 4,096 due to less training data. Additionally, weight decay for AdamW is set at 0.05.

In our generative task, we use nucleus sampling in the decoder, sampling amino acids based on probability rather than always selecting the highest probability ones. The Top-p hyperparameter is set to 0.9, meaning the decoder considers the top 90% probability mass. We also set the decoder’s repetition penalty to 1.2.

Due to limited training data, we fine-tune the models from Section 4.4 for 100 epochs. We retain the ProtAnnotation training hyperparameters but lower the learning rate to 1e-5 without warm-up.

For binary localization properties, soluble and membrane-bound, we set template function G ⁡ ( ) G() as “is soluble” or “is membrane-bound”.


## A.7. Additional experimental results

We here generates 300 300 functional proteins with EGF-like domain for ProGen, ProteinDT and PAAG. The results are in Table 11 .

To ensure fine-tuned PAAG isn’t just memorizing the training set, we evaluate distinct-2, diversity, and novelty for unconditionally generated sequences. Table 8 shows that, even after fine-tuning, PAAG produces proteins with higher novelty than Chroma and ProGen, indicating it doesn’t overfit, thanks to label smoothing. Additionally, fine-tuned PAAG’s diversity is closest to natural proteins, suggesting it captures similar amino acid distributions.