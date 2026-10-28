1[3]y1 #3

1[3]001#1#3 # ​ 1 ± # ​ 2 #1\pm#2


## A Multi-Label Temporal Convolutional Framework for Transcription Factor Binding Characterization


## Abstract

Transcription factors (TFs) regulate gene expression through complex and cooperative mechanisms. While many TFs act together, the logic underlying TFs binding and their interactions is not fully understood yet. Most current approaches for TF binding site prediction focus on individual TFs and binary classification tasks, without a full analysis of the possible interactions among various TFs. In this paper we investigate DNA TF binding site recognition as a multi-label classification problem, achieving reliable predictions for multiple TFs on DNA sequences retrieved in public repositories. Our deep learning models are based on Temporal Convolutional Networks (TCNs), which are able to predict multiple TF binding profiles, capturing correlations among TFs and their cooperative regulatory mechanisms. Our results suggest that multi-label learning leading to reliable predictive performances can reveal biologically meaningful motifs and co-binding patterns consistent with known TF interactions, while also suggesting novel relationships and cooperation among TFs.


## 1 Introduction

Transcription factors (TFs) rarely act alone, but they frequently operate through cooperative mechanisms, forming complexes such as homo/hetero dimers, where distinct combinations of TFs can elicit different regulatory effects [ 24 , 33 , 37 ] . In prokaryotes, individual TFs typically recognize relatively long DNA motifs, which are often sufficient to uniquely identify their target genes. In contrast, TFs in organisms with larger and more complex genomes bind shorter DNA sequences, which are insufficient to define unique genomic locations on their own. Moreover, the development and maintenance of multicellular organisms require the emergence of intricate molecular systems capable of implementing combinatorial regulatory logic [ 26 ] . To overcome these challenges, eukaryotic organisms have evolved mechanisms for cooperative DNA recognition involving multiple TFs, through direct and indirect protein-protein interactions [ 31 ] , indirect interactions mediated by chromatin architecture, or through co-binding to adjacent or partially overlapping DNA motifs [ 2 ] . Each interaction mechanism confers distinct regulatory properties to the resulting TF complex [ 26 ] .

A representative example of TF cooperation is the formation of functional heterodimers [ 37 ] . Several eukaryotic TFs are unable to bind DNA as monomers and instead require physical interaction with another TF, often a member of the same family, to form a functional dimer capable of recognizing specific DNA sequences.

A classical example of such a mechanism is the MYC/MAX heterodimer, which plays a central role in transcriptional regulation [ 3 , 1 ] . While homo/hetero dimerization represent common forms of TF cooperation, they are only a subset of a much broader spectrum of regulatory complexes, whose combinatorial logic and mechanisms of action remain largely unexplored [ 12 ] .

In this paper we plan to investigate the question of multiple TFs DNA-binding prediction as a multi-label classification problem via deep learning. This perspective will enable the simultaneous prediction of binding events for multiple TFs and provides an opportunity to explore correlations among TFs that reflects the cooperative or combinatorial regulatory mechanisms as in Fig. 1 , obtained via a costly procedure, but going beyond. Our techniques can indeed refine and guide investigation complementing expensive lab protocols .

To date, deep learning approaches for DNA-binding recognition have focused on binary classification tasks, where the goal is to predict whether a given genomic region is bound by a single TF [ 39 , 42 , 18 ] .

In the present work, we take advantage of novel deep learning architectures, especially designed for sequential data modelling as Temporal Convolutional Networks (TCNs) for multi-label modelling TF binding site predictions, see Figure 2 . TCNs exhibit a decisive advantage with respect to traditional recurrent architectures, such as Recurrent Neural Networks (RNNs), which have been widely applied to sequence modelling tasks, including biological sequence analysis. RNNs however suffer from well-known limitations, including vanishing and exploding gradients [ 21 ] , limited parallelizability, and difficulties in capturing long-range dependencies. Also, more recently, attention-based models, most notably Transformers [ 36 ] , have achieved state-of-the-art performance across a wide range of sequence and language modelling tasks [ 8 , 16 ] . Their ability to model global dependencies and their scalability have made them highly successful in many domains. Nevertheless, attention-based architectures [ 11 ] come with significant drawbacks, including substantial data requirements, high computational costs during training, and limited interpretability. These issues are particularly problematic in biological applications, where data are often noisy or scarce and model transparency is essential. Temporal Convolutional Networks (TCNs) are able to address the limitations of recurrent models by enabling parallel computation and stable gradient propagation [ 29 ] and are particularly suited for the biological data analysis, where they can outperform attention-based models. TCNs were first introduced as a generative audio model named WaveNet [ 35 ] and later appeared as an action segmentation model in Lea et al. [ 25 ] . The general architecture proposed by Bai et al. [ 6 ] , however differs from such architectures by being much simpler. In fact, the model proposed by Bai, besides the basic concept of temporal convolutions listed before, uses only depth, dilation and residual connections to build the effective history of the model. The effective history is defined as the ability of the networks to look into the past to make a prediction, or worded differently, it is the size of the context window. TCN have been successfully applied in several field of application, including classification of satellite image time series [ 29 ] , clinical length of stay and mortality prediction [ 7 ] and energy-related time series forecasting [ 23 ] .

Moreover, compared to attention-based approaches as Transformer based architectures [ 36 ] , TCNs typically require fewer data and offer a favorable trade-off between model capacity and efficiency. Moreover, their convolutional backbone is naturally well-suited for modelling biological sequences. Key properties such as tunable receptive fields allow TCN-based architectures to capture long-range dependencies while maintaining architectural simplicity, making them especially amenable to downstream explainability analyzes.

In the present study, we investigate whether deep learning models, as RNN and TCN, can learn correlations among TF labels solely from DNA sequence data, obtained from public repositories. In addition, we apply explainability methods to trained models to assess whether they can reveal biologically relevant sequence features and plausible interactions among TFs. Through this integrated biological and computational approach, we seek to gain new insights into the cooperative nature of transcriptional regulation.


## 2 Materials and Methods

We describe the datasets and the deep learning architectures we used in our analysis on Transcription Factor Binding Sites (TFBS). To start with, we describe separately the datasets we used for our multi-label TFBS recognition, that we created from raw ChIP-seq data for our study, and the one, not curated by us, that we used to benchmark our algorithms. Explicitly note that we used the formers to solve a multi-label classification problem while we used the latter to solve a binary classification problem, as it was created for that purpose (see [ 41 ] ).


## 2.1 Datasets for multi-label TFBS recognition

For the problem of multi-label TFBS recognition we constructed 3 datasets using publicly available ChIP-seq experiments provided by the ENCODE Consortium on the ENCODE portal [ 14 ] . In particular, we used all the ChIP-seq profiles available on the ENCODE portal matching the selection criteria we now describe. Starting from MYC, a well-characterized TF with known cooperative behaviour, we followed two different approaches to determine which other TFs to include in the dataset. The first approach yields the datasets we call D-5TF-3CLand D-7TF-4CL. We obtain them by selecting 5 and 7 additional TFs based on motif enrichment analysis (SEA) in MYC-bound regions and data availability across 3 and 4 cell lines, respectively, as depicted in Table 1 , where the Group 0 represents D-5TF-3CL, while the Group 1 represents D-7TF-4CL. The second approach, yields the dataset we call H-M-E2F, obtained by selected a hand-crafted set of TFs with putative interactions with MYC. More specifically we downloaded Chip-Seq targeting E2F1, E2F6, E2F8, MYC in K562 cell line from the ENCODE Regulation ’TF Clusters’ track. More specifically, the enrichment-driven approach resulted in the D-5TF-3CL and D-7TF-4CL datasets while the hand-curated selection of TFs resulted in the H-M-E2F dataset.

We collected ChIP-seq profiles for selected TFs from the ENCODE portal [ 14 ] . Peak intersections were then computed across selected profiles. For each overlapping region, we extracted a 1000 ​ b ​ p 1000bp sequence centred at the midpoint. Each sequence was encoded with one-hot encoding and labelled with the TFs corresponding to the intersecting peaks.

The datasets thus obtained are then a set of sequence features X X and a set of labels Y Y where:

represents the sequence vector of the i t ​ h i^{th} sample and

represents the label vector consisting of k k binary variables l i k l^{k}_{i} encoding the presence/absence of the k k TFs, as usual | X | |X| and | Y | |Y| denoting the numerosity of samples in the dataset X X with labels Y Y . It is worth noting that while in the binary classification setting we distinguish between bound (positive) and unbound (negative), in our main formalization there is no absolute negative or unbound label; in fact each sequence example is labelled with one or more TFs. We train our proposed deep-learning models to jointly learn the probability of the label vector y i y_{i} modelling each l i k l^{k}_{i} as individual binary predictions, therefore predicting binding specificities for all TFs simultaneously.


## 2.2 Dataset for binary TFBS recognition

To benchmark our algorithms we used the dataset curated by Zeng et al. [ 41 ] , which includes 165 ChIP-seq datasets selected by the authors of op. cit. ensuring diversity across cell lines. The source of this data is the ENCODE consortium, the same source of data we used to create our multi-label dataset. This curated dataset was provided to us by the authors of [ 41 ] and was already labeled by them. Each dataset was provided to us already split into train ( 80 % 80\% ) and test ( 20 % 20\% ) sets with positive and negative instances. During training and development we further spilt each train set to obtain a validation set consisting of 20 % 20\% the initial train set. DNA sequences are 101 bp long and labeled binarily to indicate Transcription Factor Binding Sites (TFBS) presence.


## 2.3 Deep Learning Architectures

We designed and evaluated several Deep Learning (DL) models to address the main goal of this work, namely TF binding prediction task as a multi-label problem. We implemented a Temporal Convolutional Network(TCN)-based model alongside a hybrid baseline model based upon Recurrent Neural Network(RNN) and Convolutional Neural Networks(CNN). The baseline model is almost identical to the TCN model except for the TCN blocks which are substituted by two layers of Bi-LSTM with hidden_dimention = 50 . A visual representation can be found in Figure 6 as well as additional architecture details in Table 2 . TCNs are convolutional architectures for sequence modelling [ 6 ] , which have demonstrated strong performance across different domains. TCNs’ convolutional backbone enables effective modelling of long-range dependencies, arguably granting them an advantage in comparison with RNNs. In addition, convolutional architectures are characterized by a strong inductive bias suitable for local pattern detection, making them particularly effective for biological sequence analysis. TCNs have two distinguishing features:

All the convolutions operations in the network are causal, there is no information flowing from future to past.

The architecture can take as input a sequence of arbitrary length and map it to an output sequence of the same length similarly to RNN.

We will now introduce briefly the main features of the TCN architecture proposed by Bai [ 6 ] which we used as the foundations to develop our temporal convolutional models.

Causal Convolutions. The classic convolution layer is rendered causal by appropriate use of padding. In fact, the convolution operation is allowed access only to past events by zero-padding asymmetrically the sequence at the start. The padding , thus, ensures that there is no information leakage from future elements of the sequences as show in Fig. 3 .

The choice of appropriate padding also ensures that the output size matches the input size of the sequence.

Dilated Convolutions. The effective history grows linearly with the depth of the network, making it challenging to achieve a good enough context window for longer sequences. The effective history of the network is dependant also on the convolutions’ receptive field; due to this reason dilated convolutions represent an ideal solution to this challenge. Dilated convolutions in fact, enable an exponentially larger receptive field compared to classic convolutions [ 38 ] , thus increasing the effective history of the network without increasing its depth. The use of dilated convolution in TCN has been first introduced in [ 35 ] .

More formally a dilated convolution is defined as:

Where d d represents the dilation factor and k k represents the kernel size. When d = 1 d=1 dilation convolution and regular convolution are equivalent.

Residual Connections. Residual blocks where first introduced by He et al. [ 20 ] . Residual connections works by adding an identity mapping parallel to the convolutional block and then summing it with the output. More formally, for a generic layer F F with input x x the output O O of the residual block can be defined as:

Where σ ( . ) \sigma(.) is the activation function of choice. It is worth noting that x x and F ⁡ ( x ) F(x) might not have the same dimensions, in which case a linear projection is added.

Residual blocks allow the layers to learn just the residual feature map while the previous one is carried by the identity connection. Empirical results show that convolutional layers perform much better by learning on the residual feature map, rather than on the whole feature map itself. This enables layers to learn modifications to the identity mapping instead of the full transformation. In addition, residual connections stabilize larger networks by allowing an easier propagation for a fine-tuned signal; in fact, the unmodified propagation requires just setting all the layer’s weights to 0, which is much simpler than learning the identity operation. Due to the dependence of the temporal convolution’s effective history on the depth of the network, residual connections represent an optimal architecture for TCNs, as it allows for deeper architectures.


## 2.4 Attribution Methods

To gain insight into the DNA patterns learned by the models, we applied several explainability techniques. Attribution scores that quantify the contribution of each nucleotide to the model’s output were computed using Integrated Gradients [ 34 ] , with di-nucleotide shuffled sequences as baselines. Attribution was performed separately for each target TF. Subsequently, we used TF-MoDISco [ 32 ] to identify and extract informative seqlets, short genomic sequences with high information content, from the attribution maps.


## 2.5 Implementation

We implemented our models with the pytorch [ 4 ] framework performing hyperparameter tuning using Tree of Parzen Estimators [ 9 ] provided by the hyperopt library [ 10 ] . In addition, we also employed MLFlow [ 40 ] , Pandas [ 27 ] , scikit-learn [ 28 ] and numpy [ 5 ] python libraries during the development of our models and training scripts. We trained all our models with the Adam optimizer with weight decay set to 0 in conjunction with a custom learning rate scheduler. The scheduler is composed of a linear warmup phase for the first 20% of training epochs followed by cosine annealing to mitigate overfitting. During training we also employed early stopping with a patient mechanism. The final hyperparameters can be found in Table 2 .


## 3 Results and discussion

We detail our results on TF binary classification, as sanity check and benchmarking and then as multi-label TF binding sites classification, the main goal of our work.


## 3.1 Binary classification as benchmarking

In order to assess the general capabilities of the TCN architecture on the classification of genetic sequences we also tested our model in the binary classification setting. To this end, we used the dataset described in Section 2.2 that has been widely used for DNA–TF binding site prediction [ 43 , 17 ] .

Overall, the TCN-based model adapted to binary classification achieved satisfactory performances detailed in Table 3 and Fig. 7 , comparable and in line with the state-of-the-art of TFBS binary classification [ 43 , 17 ] . The comparison is unfavorable for our model as we are comparing it with deep learning models specifically developed for binary classification, some of which are also trained with DNA shape data to further improve on the task and thus having access to more data modalities besides sequence features. It is important to note, as highlighted by Figure 8 , that while there is a moderate correlation between metrics and dataset size, namely a Pearson coefficient of 0.61 0.61 , 0.56 0.56 and 0.57 0.57 for accuracy, AP and AU-ROC respectively, the TCN-based model obtained outstanding results also on small datasets, achieving less than 0.7 0.7 AP only on a 13 small size datasets out of 165. These results confirm the suitability of our architecture for TFBS classification tasks in general, moreover the model exhibited robust performances also on several small-sized datasets, showing a satisfactory behaviour also while trained in a regime of data scarcity.


## 3.2 Multi-label classification results

We trained and tested our TCN-based model as well as the Bi-LSTM-based baseline on the three multi label dataset. We evaluated the performance of the trained models using both label-specific and summary metrics. In order to assess the label-specific metrics we used F1-score [ 13 ] , precision and recall [ 30 ] . As summary metrics we adopted Area Under the Receiving-Operator Curve (AUC or AU-ROC) [ 13 ] and Average Precision (AP) defined as:

where R n , P n R_{n},P_{n} are respectively precision and recall at the n t ​ h n^{th} decision threshold. AP does approximate the area under the Precision-Recall curve without using linear interpolation. It has been noted that estimating the area under the curve with linear interpolation results in an overly optimistic metric [ 15 , 19 ] , while AP is a more conservative approximation. In addition, it is important to note that, while it is a widespread and generally accepted metric, AU-ROC is not suited to compare performances across different datasets. This is due to the fact that the baseline value depends on the dataset composition, making comparison across differently skewed datasets rather challenging. This is particularly relevant in cases where the class imbalance is severe as it is in ours.

Overall, the TCN-based model outperformed the baseline on almost all metrics across all datasets and labels. The TCN-based model obtained a general significant gain over the RNN-based model both in terms of performance and stability as can be seen from the plot of F1 scores in Figure 9 . We will now discuss in details the performance of both models on each joint dataset.

The H-M-E2F dataset. The H-M-E2F datasets represents the less complex datasets in terms of number of labels and the smallest in terms of number of sequences. The TCN-based model demonstrated a clear and substantial gain over the baseline, achieving satisfactory performance in areas where the baseline model proved inadequate. In terms of AP and AUC, the TCN-model achieved a stable and considerable gain. On the labels specific metrics, the highest gain for F1 and recall was obtained on the most frequent class, namely MYC , this improvement is also reflected in the gain obtained in the samples average which shows the highest increase over the considered averaging methods as expected. The class with the highest precision improvement on the other hand is E2F1 . The performance on E2F8 , while showing a similar gain in magnitude compared to the other labels, remain underwhelming and significantly lower than performance obtained on the other labels.

The D-5TF-3CLdataset. The D-5TF-3CLdataset is the biggest dataset taken into consideration, both in terms of number of labels and training sequences. The TCN-based model achieved also on this dataset a substantial gain over the baseline model, achieving higher gains compared to H-M-E2F dataset. It is important to note, however, that the higher gains are largely due to the fact that the baseline performance is way lower compared to the one achieved on the H-M-E2F dataset. This is particularly evident by comparing the AP scores of the two models on the two datasets; the TCN-based model’s AP score are somewhat comparable while the baseline model clearly struggles more on D-5TF-3CL. Taking into consideration label specific metrics, it is particularly noteworthy that the highest gain for each metric has been obtained on the same label, USF2 . This is particularly interesting because USF2 is the least frequent class in D-5TF-3CL, this suggests that the TCN-based model’s gain are not just imputable to an improved overall capacity to leverage training data and that the TCN-based model is able to capture and learn label-specific features that the recurrent baseline cannot, even with fewer examples. This in turns suggests that USF2 label is characterized by different sequence features that a recurrent architecture cannot fully learn. It is also worth noting that the performance of the TCN-based model are more stable compared to the baseline as can bee seen from the metrics’ standard deviations.

The D-7TF-4CLdataset. The D-7TF-4CLdataset lies in a middle ground between H-M-E2F and D-5TF-3CLdataset, both in terms of labels and in terms of training samples. In fact, it is composed by one more label compared to H-M-E2F while being constituted by almost twice the samples. Broadly speaking both models follow the same trend observed for D-5TF-3CLwith the TCN-based model outperforming the baseline. The AP scores of both models are comparable with the ones achieved on the D-5TF-3CLdataset as well. As befeore, the highest gain has been achieved on the less frequent class, USF2, for both F1 and precision while the highest gain in terms of precision has been obtained on c-Myc.


## 3.3 Attributions

In order to understand what the models’ have been learning and to gain insight on the effectiveness of our trained TCN-based model, we applied explainability techniques. We derived attribution scores for the TCN-based model trained on the H-M-E2F dataset with Integrated Gradients and used TF - MoDISco [ 32 ] to identify the most informative seqlets.

The heat-map and sequence logos obtained, as in Figure 10 , clearly show that the model is capturing correctly at least part of the underlying biological mechanism. In fact, the box logos obtained from the attribution pipeline represent two well known motifs belonging to consensus sequences of the labels present in the training dataset, namely MYC and E2F6.

The nature of the proposed task at hand does not allow for a seamless integration of existing attribution pipelines, due to the multi-label nature of our task it would be preferable to modify and apply attribution methods accordingly. The proper development of a sound attribution pipeline devised specifically for multi-label data, however, is out of the scope of this study and will be considered in future works.


## 4 Conclusions

We address the question of multiple Transcription Factors (TF) DNA-binding recognition modelled via multiple labels, going beyond the binary, single-TF prediction paradigm. Our deep learning framework based on Temporal Convolutional Networks (TCNs) achieves an effective learning in settings characterized by limited and noisy biological data, with a significant predictive performance. Beyond the predictive accuracy, we applied explainable artificial intelligence methods to extract from our models biologically meaningful insights as sequence motifs. Our findings suggest that multi-label deep learning models for TFBS prediction can serve not just as a predictive tool, but also as an hypothesis-generating framework for studying transcriptional regulation. We plan to deepen our investigation in the future towards a more comprehensive understanding of gene regulatory networks and their underlying cooperative mechanisms. Furthermore, we plan to develop an attribution framework specifically tailored on multi-label setting to fully leverage all the information and insights learned by the trained models.


## 5 Data availability

All the experimental data used to construct our dataset is publicly available on ENCODE Consortium [ 14 ] . In order to construct the two data-driven datasets we downloaded all available Chip-Seq experiments for the TF and cell-lines listed in Table 1 . For the manually curated dataset we downloaded Chip-Seq targeting the already specified transcription factor from in K562 cell line from The dataset used to test the capability of our model in the binary setting is the dataset proposed by [ 41 ] . The full list of encode identifiers is available upon request.


## 6 Code availability

The code is fully available upon request to the authors.


## 7 Conflict of interest

All authors declare no conflict of interest.


## References