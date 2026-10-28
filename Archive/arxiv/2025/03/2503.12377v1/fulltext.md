## GCBLANE: A Graph-Enhanced Convolutional BiLSTM Attention Network for Improved Transcription Factor Binding Site Prediction

Identifying transcription factor binding sites (TFBS) is important for understanding gene regulation, as these sites allow transcription factors (TFs) to bind to DNA and modulate gene expression. Despite progress in high-throughput sequencing, accurately pinpointing TFBS remains challenging due to the vast amount of genomic data and complex binding patterns. To tackle this problem, we introduce GCBLANE, a graph-enhanced convolutional bidirectional Long Short-Term Memory attention network. This model’s structure combines convolutional, multi-head attention, and recurrent layers, augmented by a graph neural network, enabling the detection of crucial features for TFBS prediction. In an extensive evaluation of 690 datasets from ENCODE ChIP-seq experiments, GCBLANE exhibited exceptional performance, achieving an average AUC of 0.943. Further evaluation on 165 ENCODE ChIP-seq datasets yielded an average AUC of 0.9495, surpassing advanced models that utilise multimodal approaches, including DNA shape information. This results underscores GCBLANE’s effectiveness, compared to other sophisticated methods in comprehensive assessments. By integrating graph-based learning with traditional sequence analysis techniques, GCBLANE represents a major step forward in TFBS prediction.

K eywords Transcription Factor Binding Sites ⋅ \cdot Deep Learning ⋅ \cdot Multi-head attention ⋅ \cdot Graph Neural Networks


## 1 Introduction

Transcription Factor Binding Sites (TFBS) are specific DNA sequences that serve as anchoring points for transcription factors (TFs), which play an essential role in controlling gene expression [ 1 ] . Gene expression refers to the process through which genetic information is utilised to produce functional products, such as peptides or regulatory RNA molecules. Transcription factors (TFs) are proteins that interact with DNA to influence gene activity, either promoting or inhibiting gene expression. They play a key role in facilitating the conversion of DNA into mRNA, a critical step in regulating protein synthesis within the cell. [ 2 ] .

Transcription factors are vital due to their ability to connect TF mutations to specific diseases and their potential as therapeutic targets [ 3 ] . Most transcription factors comprise a DNA-Binding Domain (DBD) that interacts with specific DNA sequences near regulatory genes [ 4 ] . Precise identification of Transcription Factor Binding Sites (TFBS), which span 4 to 30 base pairs in length, is crucial. Motifs are brief nucleotide sequences that are fundamental to essential biological functions, including transcription and translation. They are typically recognized by specific proteins, such as transcription factors, which bind to them and influence gene expression. These sequences are crucial for regulating genetic processes and ensuring proper cellular function [ 5 ] . Modern sequencing technologies have generated extensive high-quality TFBS data, which is available through repositories like JASPAR [ 6 ] . Yet, the considerable time and resources required for thorough TFBS identification make it challenging to address all TFBS comprehensively, leading researchers to increasingly adopt computational approaches. As a result, researchers are increasingly turning to computational methods. Current TFBS prediction techniques face challenges in accuracy and efficiency due to the vast amount of data and complex binding patterns that often fail to capture all relevant TFBS characteristics from DNA sequences. To improve prediction accuracy and efficiency, we developed a Graph-enhanced Convolutional BiLSTM Attention Network (GCBLANE). This model combines convolutional layers, recurrent layers, and the attention mechanism with a graph neural network to enhance the extraction of key features for TFBS prediction, thereby improving the model’s performance on complex genomic data.


## 2 Literature Review

The rapid expansion of genomic data and improvements in processing capacity have made deep learning essential for identifying transcription factor binding sites (TFBS) [ 7 ] . This section examines various machine learning approaches used in TFBS prediction. DeepBind [ 8 ] , a notable deep-learning technique, employs convolutional neural networks (CNNs) and surpasses previous methods in performance. However, CNNs struggle to capture sequential dependencies. To overcome this limitation, DanQ [ 9 ] was created. This model unifies CNNs and RNNs, employing a convolutional layer to identify regulatory motifs and recurrent layers to recognise the relationships between these motifs, leading to enhanced performance compared to similar models. KEGRU [ 10 ] , another deep-learning approach, improves TFBS detection by integrating gated recurrent units (GRUs) with k-mer embedding.

Compared to approaches like gkSVM [ 11 ] and DeepBind, KEGRU exhibits superior effectiveness. Although machine-learning models have been effective in various tasks, deep-learning techniques often surpass them in performance but struggle with interpretability. To address this challenge, attention mechanisms have been integrated into deep-learning frameworks. TBiNet [ 12 ] , a model comprising a CNN layer, BiLSTM layer, and attention layer, utilises the attention component to concentrate on TF binding motifs, enabling it to surpass leading models such as DanQ and DeepSea. Similarly, DeepGRN [ 13 ] incorporated attention mechanisms into a CNN-RNN-based structure, demonstrating competitive performance among the top methods evaluated in the ENCODE-DREAM Challenge. By utilising self-attention mechanisms and residual blocks, the Self-Attention Residual Network (SAResNet) [ 14 ] enhances feature extraction efficiency. Additionally, the integration of transfer learning contributes to a quicker convergence during the training process. This model delivers better accuracy compared to other methods, especially when applied to smaller datasets. By integrating both bottom-up and top-down attention modules with residual blocks and a feed-forward network, MAResNet [ 15 ] achieved improved performance, resulting in an AUC of 0.927. MSDenseNet [ 16 ] excelled further, reaching an AUC of 0.933 through the application of fault-tolerant coding.

Recent advancements in TFBS prediction have led to the emergence of more sophisticated approaches. Notable among these are DeepSTF [ 17 ] , DSAC [ 18 ] , TBCA [ 19 ] , and MLSNet [ 20 ] which employ a multimodal strategy by incorporating DNA shape features into their predictive models. While MultiTF [ 21 ] combines graph and cross-attention networks for trimodal TFBS prediction, it also incorporates additional DNA shape and structural features. This integration of structural information with sequence data has shown promising results in improving the prediction accuracy. Another significant development is BERT-TFBS [ 22 ] , which utilises a pre-trained DNABERT-2 module. These developments emphasise the continuous need for innovations to improve model size and training efficiency. However, these approaches using language models also present computational challenges due to the high resource requirements of complex transformer-based architectures. Other existing methods rely on complex modalities, such as DNA shape, structural features, or DNA-breathing dynamics, which may increase computational overhead. While these models capture complex relationships, none have fully explored the combination of graph and sequential neural networks in a sequence-only context. Graph-based neural network approaches have shown promise in related areas of genomic research, particularly in predicting TF-target gene interactions. Notable examples include GraphTGI [ 23 ] and PPRTGI [ 24 ] , which leverage graph structures to capture complex relationships in genetic regulatory networks.

To address this gap, we introduce GCBLANE, which focuses on integrating graph and sequential neural networks, specifically for sequence-based TFBS prediction, offering a simpler and more computationally efficient approach without the need for additional modalities. No existing studies have explored the combination of graph and sequential neural networks for TFBS prediction in a sequence-only context, making GCBLANE a novel and efficient approach that does not rely on additional modalities. This unexplored avenue offers scope for developing more comprehensive and accurate models for TFBS prediction, potentially leading to breakthroughs in our understanding of gene-regulation mechanisms.


## 3 Methodology

To address the challenges in transcription factor binding site (TFBS) prediction, we propose GCBLANE, a Graph-Enhanced Convolutional BiLSTM Attention Network. This section details the key components of our methodology, including datasets, feature representation, model architecture, transfer learning, training procedure, and evaluation metrics.


## 3.1 Datasets

To evaluate the models, 690 ChIP-seq datasets and a subset of 165 ChIP-seq datasets were used. These datasets served as benchmarks for evaluating, validating and comparing predictive performance with various state-of-the-art models for TFBS prediction. The data were originally sourced from the ENCODE Dream Challenge. The 690 ChIP-seq datasets encompass approximately 25 million sequences, which spanned 91 human cell types and incorporated 161 DNA-binding proteins, including both general and sequence-specific types. Additionally, 165 ChIP-seq datasets cover 29 unique transcription factors (TFs) across 32 cell lines. All datasets were split into three portions: 70% for model training, 10% for model validation, and 20% for model testing purposes.

Negative samples were created utilising the ’fasta-dinucleotide-shuffle’ tool within MEME [ 25 ] . This tool shuffles the dinucleotide sequences from the positive samples while preserving their overall nucleotide composition. The negative samples are essential for training the model to distinguish between true binding sites and random sequences. To maintain dataset balance, the ratio of negative to positive samples was carefully controlled during data preparation. A ratio of 1:1 was maintained, where for every positive sample, a corresponding negative sample was generated. Maintaining this balance is essential for enabling the model to distinguish between positive and negative instances effectively, reducing bias, and enhancing the reliability of predictions. The positive samples are made up of DNA sequences, each 101 base pairs long, containing at least one TFBS present. The datasets can be found at https://github.com/projectultra/GCBLANE .


## 3.2 Feature Representation

Preprocessing is essential for processing DNA sequences in neural networks that require vector representations. Several encoding methods exist for this purpose. Label encoding assigns numerical values to nucleotides (e.g, A = 1, T = 2, C = 3, G = 4), but this approach may inadvertently create a hierarchy among nucleotides. An alternative method is k-mer encoding [ 26 ] , which divides a sequence into k-length sub-sequences.

In this study, a binary vector representation known as one-hot encoding, shown in Figure 1 , was utilised to encode individual nucleotides. The encoding assigned specific binary patterns to each nucleotide: adenine (A) was represented as [1 0 0 0], thymine (T) as [0 1 0 0], cytosine (C) as [0 0 1 0], and guanine (G) as [0 0 0 1]. Using the one-hot encoding method converts each nucleotide into a vector primarily consisting of zeros, with a single bit positioned to denote the particular nucleotide being encoded. This method effectively distinguishes the four nucleotides, allowing for clear and straightforward input representation in the model. Unlike label encoding, one-hot encoding ensures that all the motifs are equally weighted. However, this approach increases the dimensionality of the input space, which can affect the computational efficiency, particularly for large datasets.

For the graph module, a de Bruijn graph representation is employed to enhance feature extraction [ 27 ] . The de Bruijn graph shown in Figure 2 captures overlapping k-mers within a sequence, encoding structural relationships and dependencies in the genomic data. This allows the model to leverage additional contextual information beyond that captured by the sequential methods. By constructing a de Bruijn graph, graph neural networks (GNNs) can capture multi-hop relationships (i.e. relationships between distant k-mers) that extend beyond immediate neighbours. In essence, GNNs provide a global context, enabling the model to look at the DNA sequence not only as a string of letters but also as a network of relationships that can influence TFBS prediction.


## 3.3 Model Architecture

The GCBLANE Model Architecture shown in Figure 3 introduces a novel approach for transcription factor binding site prediction. To enhance the accuracy of TFBS predictions, the model incorporates a graph neural network module, which effectively represents spatial and sequential relationships in genomic data. It integrates a multi-head attention mechanism for feature extraction from sequential data, recurrent layers for capturing intermediate dependencies, and a convolutional network to address local dependencies.

GCBLANE begins with a convolutional neural network (CNN) [ 28 ] , comprising multiple convolution layers that apply filters to extract unique features from the data. A large number of filters was selected to ensure thorough feature extraction while reducing the chance of missing key information. The CNN layers use the PReLU activation function, an enhancement of Leaky ReLU. While Leaky ReLU allows a small gradient for negative inputs, PReLU allows the slope ( a a ) of the negative part to be a learnable parameter.

This adaptability optimises the slope during training, helping the model learn complex patterns more effectively and mitigating issues associated with fixed activation functions. To preserve critical information that might otherwise be lost, ’same’ padding and a stride of one are utilised. To condense the output and lower the computational costs max pooling layers are utilised. However, the pooling layers are avoided in the initial layers to mitigate potential information loss. By focusing on the most important features from the input data, max pooling creates a more streamlined representation that enhances the overall effectiveness of the neural network. Batch normalisation is incorporated to mitigate overfitting by normalising convolutional layer outputs, adjusting each batch’s mean and variance. This stabilizes learning, accelerates convergence, and acts as a regulariser, reducing sensitivity to initial weights and promoting robust feature learning. Spatial dropout, selectively drops entire channels instead of individual neurons. This method reduces dependency on particular patterns, encouraging the model to capture broader and more adaptable representations. Together, these techniques enhance the network’s ability to generalise to unseen data while maintaining a robust performance on the training set. The operations on sequence feature of for a given CNN block is as follows:

Where 𝐒 \mathbf{S} , 𝐖 M \mathbf{W}_{M} , and 𝐛 M \mathbf{b}_{M} denote the sequence features, weight matrix, and bias of the convolutional layer, respectively. PReLU ​ ( ⋅ ) \text{PReLU}(\cdot) denotes the parametric ReLU activation function. MaxPool ​ ( ⋅ ) \text{MaxPool}(\cdot) represents the maximum pooling operation. BN ​ ( ⋅ ) \text{BN}(\cdot) represents the Batch Normalization operation. Convolution ​ ( ⋅ ) \text{Convolution}(\cdot) represents the convolution operation.

The CNN output is passed into an attention network that uses a multi-head attention mechanism, similar to those found in transformer models [ 29 ] . This process derives query, key, and value representations from the CNN’s output, utilizing self-attention to process the same input across all three embeddings. The model also uses 8 attention heads. Each attention head operates separately on the input, enabling the model to capture diverse patterns and dependencies. This parallel attention strategy improves the model’s capacity to extract different relationships from the data.

The attention score is computed as:

where d k d_{k} is the dimensionality of the key vectors, and 𝐐 \mathbf{Q} , 𝐊 \mathbf{K} , and 𝐕 \mathbf{V} are the query, key, and value matrices, respectively.

The multi-head attention is defined as:

where:

Where 𝐖 𝐐 \mathbf{W_{Q}} , 𝐖 𝐊 \mathbf{W_{K}} , 𝐖 𝐕 \mathbf{W_{V}} , and 𝐖 𝐎 \mathbf{W_{O}} are learned parameters. The final output is the concatenation of outputs from all attention heads.

Furthermore, the model generates attention scores, which quantify the significance of different elements in relation to one another. These scores indicate how much focus the model places on specific features during the learning process, effectively highlighting the contributions of individual elements to the overall output. By leveraging multiple attention heads and attention scores, the model can adaptively weigh the importance of various inputs, improving its capability to extract meaningful patterns and enhance predictive accuracy.

After the attention network, the data are fed into a recurrent network that starts with a bidirectional layer, allowing the model to process the input sequence in both forward and backward directions. This dual processing enables the model to capture contextual information from both ends of the sequence. Following the bidirectional layer, a Long Short-Term Memory (LSTM) [ 30 ] layer is employed to model long-range dependencies within the sequence data. The LSTM’s architecture is particularly suited for retaining information over extended sequences, effectively addressing issues related to vanishing gradients and enabling the model to learn patterns that span across significant sequence steps. The output from the recurrent network is then channelled into a dense layer, which performs dimensionality reduction, condensing the information into a vector of size 64. This step facilitates the transition to the next stages of the model, ensuring that the essential features are retained while minimising computational complexity.

The BiLSTM layer processes the sequence bidirectionally as follows:

Forward Pass: From the beginning of the sequence ( t = 1 t=1 ) to the end of the sequence ( t = T t=T ):

Backward Pass: From the end of the sequence ( t = T t=T ) to the beginning of the sequence ( t = 1 t=1 ):

Combined Output: The final hidden state 𝐡 𝐭 \mathbf{h_{t}} at each position t t is the sum of forward and backward hidden states:

Following the BiLSTM, a unidirectional LSTM layer processes the combined output as follows:

where 𝐟 𝐭 \mathbf{f_{t}} is the forget gate, 𝐢 𝐭 \mathbf{i_{t}} is the input gate, 𝐜 𝐭 \mathbf{{c_{t}}} is the candidate cell state, 𝐨 𝐭 \mathbf{o_{t}} is the output gate, ⊙ \odot denotes the element-wise multiplication (Hadamard product).

GCBLANE incorporates a graph neural network (GNN) [ 31 ] module to further enhance its capabilities. This GNN module was used to integrate additional contextual information into the model by encoding spatial information and interactions between k-mers within the genomic data. The graph module processes the graph representation to model complex relationships and dependencies that are not captured by the sequential layers alone. Graph convolution operates on the adjacency matrix 𝐀 \mathbf{A} of the graph and the feature matrix 𝐗 \mathbf{X} , where the updated feature matrix 𝐗 ′ \mathbf{X^{\prime}} is computed as:

where 𝐀 ^ = 𝐀 + 𝐈 \hat{\mathbf{A}}=\mathbf{A}+\mathbf{I} is the adjacency matrix 𝐀 \mathbf{A} with added self-loops via the identity matrix 𝐈 \mathbf{I} , 𝐃 ^ \hat{\mathbf{D}} is the degree matrix of 𝐀 ^ \hat{\mathbf{A}} , 𝐗 \mathbf{X} is the input feature matrix, 𝐖 \mathbf{W} is the learnable weight matrix, and σ \sigma is the ReLU activation function.

Pooling layers reduce the graph size using MinCut clustering:

Cluster Assignment :

where 𝐒 \mathbf{S} is computed by an MLP with softmax output.

Coarsened Features and Adjacency :

The final stage of GCBLANE consists of a dense layer with two neural units, employing a softmax activation function to generate the predicted probabilities for the presence or absence of a TFBS.


## 3.4 Transfer Learning

Transfer learning has proven effective in prior state-of-the-art methods for transcription factor binding site (TFBS) prediction, enabling models to leverage generalizable features from broad datasets before adapting to specific tasks. In this work, we adopt a two-stage transfer learning strategy for GCBLANE to enhance its predictive performance across diverse datasets. This approach involves initial training on a global dataset followed by fine-tuning on each of the 690 individual ChIP-seq datasets, allowing the model to balance general pattern recognition with dataset-specific adaptation.

In the first stage, GCBLANE is pre-trained on this global dataset to capture broad, universal patterns critical for TFBS prediction, such as common motifs and sequential dependencies across TFs and cell lines. This pre-training phase leverages the model’s convolutional, recurrent, and graph neural network modules to learn a robust initial feature representation. By exposing the model to a diverse yet manageable subset of the data, it establishes a strong foundation of generalizable knowledge, reducing the risk of underfitting to the datasets during subsequent fine-tuning.

In the second stage, the pre-trained GCBLANE model is individually fine-tuned on each of the 690 specific ChIP-seq datasets. Fine-tuning adjusts the model’s weights to account for dataset-specific characteristics, such as unique TF binding preferences or cell-line-specific genomic contexts. For each dataset, the pre-trained model is initialized with the weights learned from the global dataset, and training proceeds with the dataset’s training split. This process refines the model’s ability to detect subtle, dataset-specific TFBS patterns while preserving the general features acquired during pre-training. The fine-tuning step employs a reduced learning rate (starting at 0.001 and decaying to 1 × 10 -6 ) to ensure stable convergence without disrupting the pre-learned representations excessively.

This transfer learning strategy offers several advantages. First, pre-training on the global dataset accelerates convergence during fine-tuning by providing a well-initialized starting point, reducing the number of epochs required for each dataset-specific model to achieve optimal performance. Second, it enhances generalization across the heterogeneous 690 datasets, as the global pre-training mitigates the impact of limited training samples in smaller datasets. Finally, by fine-tuning individually, GCBLANE adapts to the variability in TF binding behaviours and experimental conditions present in the ENCODE data, achieving superior performance compared to training from scratch on each dataset independently.

The effectiveness of this approach is evident in the results (Section 4), where GCBLANE demonstrates consistent improvements over baseline methods, particularly on small and medium-sized datasets. The transfer learning framework thus underscores GCBLANE’s scalability and adaptability, making it a practical solution for large-scale TFBS prediction tasks.


## 3.5 Training Procedure

To improve the predictive performance of the model, different hyperparameters were evaluated using a grid search during training, with a validation set used to assess their impact. All models used a batch size of 128, while the global model was trained with a learning rate of 0.001. Training spanned 10 epochs, with an early stopping mechanism applied. For each of 690 datasets the global model was fine-tuned with the learning rate starting at 0.001 and gradually decreased to as low as 1 × 10 − 6 1\times 10^{-6} using Keras built-in callback function. The fine-tuning was conducted over 50 epochs with early stopping to avoid overfitting. The GPU runtime on Google Colaboratory, specifically a T4 GPU, was used to conduct the training process. The Adam optimizer [ 32 ] was used, with categorical cross-entropy as the loss function.

The model was developed using TensorFlow [ 33 ] and Keras [ 34 ] , with the graph module implemented through Spektral [ 35 ] . All executions were performed in a Jupyter Notebook on Google Colaboratory, which provided access to high-performance computing resources, including GPUs and TPUs, to accelerate GCBLANE’s training. The full code is available on GitHub for reference and can be run in Colab for reproducibility.

Table 2 summarises the hyperparameter configurations. The choice of a learning rate of 0.001 was based on preliminary experiments that indicated this rate provided a good balance between convergence speed and stability. A lower learning rate could lead to slower training without significant performance gains, while a higher learning rate risked overshooting optimal parameter values. The batch size of 128 was selected based on its impact on model performance. This size provided a good trade-off between convergence speed and the stability of training. Smaller batch sizes were tested; however, they resulted in increased training time and did not converge during training, which negatively affected the overall performance of the model. Larger batch sizes led to overfitting on the training set, which compromised the model’s ability to generalise effectively.


## 3.6 Evaluation Metrics

Given that predicting transcription factor binding sites (TFBS) can be approached as a binary classification task, the model’s performance was evaluated using a variety of standard classification metrics. These metrics include accuracy, precision, recall, F1 score, ROC-AUC, and PR-AUC. Each of these metrics provides valuable insights into the model’s effectiveness. The terms used in these calculations are defined as follows: TP (True Positives) refers to the instances correctly identified as positive, FP (False Positives) indicates the instances incorrectly classified as positive, TN (True Negatives) denotes the instances correctly recognized as negative, and FN (False Negatives) represents the instances mistakenly classified as negative. The details of these metrics are outlined below.

The primary comparison metric chosen was the ROC-AUC, as it assesses the ability of the model to distinguish between positive and negative classes across all possible thresholds. It is particularly useful for comparing classifiers in the context of datasets which are imbalanced, as it reflects the trade-off between the true positive rate (sensitivity) and false positive rate. ROC-AUC allows for comparison with other TFBS predictors that have used this metric, providing a standardised measure of performance. Importantly, because the ROC-AUC does not depend on a specific prediction threshold, it offers a global measure of classification performance, ensuring a robust comparison across different models.

Although ROC-AUC is widely used, PR-AUC is more informative for imbalanced datasets, where the positive class (TFBS) is relatively sparse. By concentrating on precision (how many selected items are relevant) and recall (how many relevant items are selected), PR-AUC highlights the model’s ability to accurately identify positive instances. Because false positives might result in inaccurate biological interpretations, this metric is essential for TFBS prediction. PR-AUC helps to assess the model’s capability to maintain high precision across varying recall values, making it especially useful in cases where high recall is critical, such as binding site identification. Although PR-AUC has not always been reported in other papers, we include it to provide a more detailed evaluation of GCBLANE’s performance.

We evaluated our model against leading deep learning approaches, including those that exclusively use DNA sequences and others that combine DNA sequences with shape information. To ensure a fair comparison, we used identical benchmark datasets consisting of 690 and 165 ChIP-seq samples, maintaining consistent training and testing divisions.


## 4 Results


## 4.1 Global Performance

We evaluated GCBLANE’s effectiveness by examining its performance on the global dataset. The results, illustrated in Figure 4 , reveal that GCBLANE attained a remarkable accuracy of 0.8636 on the test set, demonstrating its strong predictive abilities. The similar performance of the model across the validation and training sets suggests suggests effective generalization and indicates that the model avoids overfitting.

To further evaluate GCBLANE’s performance, two key curves were analysed:

Receiver Operating Characteristic (ROC) Curve: Figure 6 shows the ROC curve, where GCBLANE achieved a high true-positive rate while maintaining a low false-positive rate. An area under the ROC curve (ROC-AUC) of 0.9396 reflects excellent discriminative ability.

Precision-Recall (PR) Curve: Shown in Figure 6 , GCBLANE maintained high precision across a range of recall values, indicating its ability to correctly identify positive samples without a significant drop in precision.

Additional insights were gained from the confusion matrix (Figure 7 ), which compares actual versus predicted classifications: True Positives: 44.46% of the test set, indicating strong identification of actual binding sites. True Negatives: 41.90%, showing accurate rejection of non-binding sites. False Positives: 8.10%, a relatively low rate of incorrect positive predictions. False Negatives: 5.54%, a minimal rate of missed binding sites. The high true-positive rate and low false-negative rate are particularly critical for TFBS prediction, as failing to detect true binding sites can significantly affect downstream biological analyses.


## 4.2 Ablation Experiments

To understand the contribution of each component within the GCBLANE, we conducted ablation experiments by comparing it with its variants: CBLANE: Excludes the graph convolutional (GCN) component from GCBLANE. GNN: Uses only a standard Graph Neural Network without a recurrent, or attention network.

The full model (GCBLANE), incorporating all components (CNN, attention, BiLSTM, and GNN), achieved the highest performance across all metrics, with an ROC-AUC of 0.9396 and PR-AUC of 0.9404. In contrast, CBLANE, a variant without the GNN module, exhibited a notable drop in performance. The ROC-AUC decreased to 0.8918 and the PR-AUC decreased to 0.8846, indicating that the GNN module plays a significant role in enhancing feature extraction, particularly in capturing structural dependencies that are not fully addressed by the sequential components alone.The GNN-only variant performed the worst, with an accuracy of 0.6776 and ROC-AUC of 0.7476. While the GNN captured some structural relationships within the data, the absence of convolutional, recurrent, and attention layers hindered the ability of the model to fully capture local motifs and sequential dependencies, which are critical for highly accurate TFBS prediction. By using de Bruijn representation, the GNN models relationships between features in a non-linear manner, capturing complex dependencies essential for biological sequences. This ability is crucial for identifying patterns that sequential models might overlook. Analysing the contributions of each component provides insights into how GCBLANE achieves superior performance. The findings suggest that a holistic approach, which combines graph-based representation learning with traditional sequence modelling, is crucial for improving TFBS prediction accuracy.


## 4.3 Overall Performance on 690 ChIP-seq Datasets

The violin plot in Figure 8 shows the kernel density distributions for each evaluation metric, providing insights into the variability and central tendencies of model performance across the 690 ChIP-seq datasets. Each violin plot has embedded box plots indicating median and interquartile ranges. Metrics such as ROC-AUC and PR-AUC exhibit tightly concentrated distributions, reflecting consistent performance across datasets. The model demonstrates consistently high performance across all evaluation metrics on the 690 ChIP-seq datasets, as shown in Figure 8 and Table 4. The model achieves an accuracy of 0.8796 with ROC-AUC and PR-AUC scores of 0.9433 and 0.9430, respectively, indicating excellent classification capability.


## 4.4 Comparison with other predictors

We evaluated GCBLANE’s effectiveness by comparing its results with those of other cutting-edge techniques across datasets of varying sizes as shown in Table 4, Table 5 and Table 6. The categorization of the 690 ChIP-seq datasets adheres to the same classification criteria employed by all other state-of-the-art methods:

Small Datasets: Fewer than 3000 training examples

Medium Datasets: Between 3000 and 30,000 training examples

Large Datasets: Greater than 30,000 training examples

GCBLANE exhibited superior performance, particularly on small and medium datasets, where it achieved the highest accuracy across all methods, indicating its robust predictive capabilities in scenarios with limited training data. On every dataset, we can observe that GCBLANE performs better than any other model, proving its exceptional performance.

Next, using the 165 datasets, we compare GCBLANE with other cutting-edge techniques that make use of multimodal techniques like DNA Shape.

The distribution of accuracy, ROC-AUC, and PR-AUC—three classification metrics—for GCBLANE and alternative methods is depicted in Figure 9 , 10 and 11 based on the testing sets of 165 ChIP-seq datasets. Across all three metrics, GCBLANE outperforms previous approaches, showing higher values in terms of its mean, median, quartiles, maximum, and minimum. This demonstrates GCBLANE’s exceptional performance compared to existing methods.

Sequence-based models like BERT-TFBS, DLBSS, DanQ, and DeepBind lag behind GCBLANE, with lower accuracy and AUC values, reflecting their limited ability to capture relevant features compared to GCBLANE’s approach. For instance, BERT-TFBS achieves an accuracy of 0.851 and a PR-AUC of 0.920, which is significantly below GCBLANE’s performance.

Even sequence-shape-based models, such as MLSNet, TBCA, and DSAC, also fall short of GCBLANE’s performance despite incorporating additional DNA shape information. MLSNet, for example, reaches an accuracy of 0.831, which is much lower than GCBLANE. These results suggest that the incorporation of shape information alone does not compensate for the enhanced feature extraction mechanisms utilized by GCBLANE.


## 4.5 Cell Lines and Transcription Factors Results

To comprehensively evaluate the performance of GCBLANE across various cell lines and transcription factors (TFs), we analysed the results of the 165 ChIP-seq datasets, partitioned by 32 cell lines and 29 TFs. Heat maps (Figures 12 and 13 ) illustrate the accuracy of GCBLANE compared to other models on these datasets, with a more intense red colour representing higher accuracy scores.

GCBLANE exhibits superior performance across most cell lines and TFs, further underscoring its robust generalization capabilities. Specifically, GCBLANE outperforms other models on key TFs, including CEBPB, CTCF, FOS, and JUN, achieving consistently high accuracy. Similarly, the model excels on cell lines such as Nha and Nhlf, where previous methodologies have struggled to deliver comparable results.

Additionally, a consistent trend is observed across all models when applied to different cell lines and TFs. Certain TFs and cell lines yield high accuracy across most models, while others exhibit uniformly lower performance. This trend highlights the influence of factors such as dataset size, the biological characteristics of specific TFs, and the unique properties of cell lines on transcription factor binding site prediction. GCBLANE’s ability to address these challenges effectively demonstrates its advantage over alternative approaches.

To summarise, the experimental outcomes showcase the exceptional effectiveness of the newly introduced GCBLANE when compared to all current benchmark models across the 165 ChIP-seq datasets. The research indicates that highly accurate predictions for TFBSs can be obtained without the need for multimodal approaches or the use of computationally demanding language models.


## 5 Conclusion

In this study, we created and applied GCBLANE, a cutting-edge deep learning model for DNA sequence Transcription Factor Binding Site (TFBS) prediction. GCBLANE integrates convolutional, multi-head attention, recurrent layers, and a graph neural network module, thereby significantly enhancing its predictive capabilities. The inclusion of the GNN module addressed the limitations of traditional sequential models by enabling the representation of complex spatial relationships in DNA sequences. This novel combination of sequential and graph-based learning provides GCBLANE with a unique advantage over the existing methods. When compared to previous state-of-the-art techniques, the model exhibits notable gains in computing efficiency and performance on small and medium-sized datasets. On 690 ChIP-seq datasets, GCBLANE performed better than any existing technique for TFBS prediction. Its exceptional performance over other top models, including those that use DNA shape characteristics, was further validated by experiments conducted on 165 ChIP-seq datasets. Even though GCBLANE performs well, there is room for development, particularly when dealing with huge datasets, where it hasn’t been able to outperform alternative techniques. One possible enhancement could be the incorporation of DNA shape profiles and structural information into the model.


## Acknowledgments

This research did not receive any specific grant from funding agencies in the public, commercial, or not-for-profit sectors.


## References