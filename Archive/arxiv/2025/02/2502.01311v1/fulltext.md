## TFBS-Finder: Deep Learning-based Model with DNABERT and Convolutional Networks to Predict Transcription Factor Binding Sites

Transcription factors are proteins that regulate the expression of genes by binding to specific genomic regions known as Transcription Factor Binding Sites (TFBSs), typically located in the promoter regions of those genes. Accurate prediction of these binding sites is essential for understanding the complex gene regulatory networks underlying various cellular functions. In this regard, many deep learning models have been developed for such prediction, but there is still scope of improvement. In this work, we have developed a deep learning model which uses pre-trained DNABERT, a Convolutional Neural Network (CNN) module, a Modified Convolutional Block Attention Module (MCBAM), a Multi-Scale Convolutions with Attention (MSCA) module and an output module. The pre-trained DNABERT is used for sequence embedding, thereby capturing the long-term dependencies in the DNA sequences while the CNN, MCBAM and MSCA modules are useful in extracting higher-order local features. TFBS-Finder is trained and tested on 165 ENCODE ChIP-seq datasets. We have also performed ablation studies as well as cross-cell line validations and comparisons with other models. The experimental results show the superiority of the proposed method in predicting TFBSs compared to the existing methodologies. The codes and the relevant datasets are publicly available at https://github.com/NimishaGhosh/TFBS-Finder/.


## I Introduction

Transcription factors (TFs) are proteins that play an important role in the regulation of genetic transcriptions by binding to DNA regulatory sequences known as Transcription Factor Binding Sites (TFBSs) (typically of size 4-30 bp) [ 1 , 2 , 3 ] . Accurate prediction of TFBSs provides crucial information on regulatory networks that control cellular functions [ 4 , 5 ] , as well as identifying disease-associated variants and regulatory regions, enabling early detection and targeted therapies [ 6 ] . Chromatin immunoprecipitation sequencing (ChIP-seq) [ 7 ] can be used to identify DNA fragments that interact with TFs. However, such method is costly, paving the way for more inexpensive but effective computational approaches to predict TFBSs.

In recent years, many researchers have proposed several machine learning and deep learning approaches to identify TFBSs which include Hidden Markov Models (HMM) [ 8 ] , Support Vector Machine (SVM) [ 9 ] , Random Forest (RF) [ 10 , 11 ] models etc. Although traditional machine learning algorithms provide competitive results, they are dependent on other methods for feature extraction and they also do not work well with large-scale datasets. To address these challenges, recently many deep learning algorithms have been proposed, which show immense potential in predicting TFBSs when working with huge amount of experimental data such as ChIP-seq. In this regard, DeepSEA [ 12 ] and DeepBind [ 13 ] which use convolutional neural networks (CNNs) showcase good performance for the prediction of TFBSs. However, CNNs fail to capture long term dependencies between different positions in a DNA sequence. To overcome this, DanQ [ 14 ] proposed by Quang et al. and DeepSite [ 15 ] proposed by Zhang et al., combine CNN and bidirectional long-short term memory (BiLSTM) to predict TFBSs. Other models such as DSAC [ 16 ] , D-SSCA [ 17 ] , DeepSTF [ 18 ] and SAResNet [ 19 ] use attention mechanisms for TFBS prediction.

The evolutionary deep learning model Bidirectional Encoder Representations from Transformers (BERT) [ 20 ] effectively learns contextual information in natural language processing. Since its proposal in [ 20 ] , it has also been used for pre-training human DNA and protein sequences giving birth to DNABERT [ 21 ] and ProteinBERT [ 22 ] respectively.

DNABERT is an effective pre-trained model for embedding DNA sequences and subsequently other deep learning models may be used for classifying TFBSs. In this regard, Ghosh et al. [ 23 ] have used DNABERT for embedding the DNA sequences, while CNN, BiLSTM and capsule network have been used as the subsequent prediction layers. On the other hand, BERT-TFBS [ 6 ] has DNABERT-2, a CNN module, a convolution block attention module (CBAM) and an output module for TFBS prediction on 165 ChIP-seq datasets. Both works have shown promising results in predicting TFBSs.

Taking cue from the literature, in this work we propose TFBS-Finder that utilises DNABERT, a CNN module, a modified convolution block attention module (MCBAM), a multi-scale convolutions with attention (MSCA) module and an output module to predict TFBSs. Similarly to [ 6 ] , we have trained and tested TFBS-Finder on 165 ChIP-Seq datasets, encompassing different cell-lines and TFs. The results show the superiority of TFBS-Finder when compared to the state-of-the-art predictors.

To summarise, the main contributions of the work are as follows:

We propose a novel DNABERT-based deep learning model (TFBS-Finder) for predicting TFBSs. The model utilises DNABERT for embedding while CNN, MCBAM, MSCA and output modules are used for subsequent prediction.

Ablation study is conducted to showcase the importance of each module of TFBS-Finder.

To show the generalisability and robustness of TFBS-Finder, cross-cell line validations are conducted to predict TFBSs.

All codes along with a sample dataset and a trained model are publicly available at https://github.com/NimishaGhosh/TFBS-Finder/..


## II Materials and Methods

In this section, data preparation is provided followed by a discussion on the pipeline of the work.


## II-A Data Preparation

In this work, we have considered the benchmark 165 ChIP-seq datasets from Enclyopedia of DNA elements (ENCODE) [ 24 ] , consisting of 29 different TFs from 32 cell lines. The dataset is taken from Zeng et al. [ 25 ] where each positive sequence in the dataset is a 101 bp DNA sequence length containing TFBSs while the negative samples are obtained by shuffling the positive sequences conserving dinucleotide frequencies. Detailed descriptions of the datasets used in this work are given in Supplementary Table S1.


## II-B Pipeline of the Work

The pipeline for the proposed work is given in Figure 1 . The proposed model consists of five modules encompassing a DNABERT module, a Convolutional Neural (CNN) module, a modified CBAM (MCBAM) module, a multi-scale convolutions with attention module (MSCA) and an output module.

DNABERT: DNABERT is pre-trained on DNA sequences to extract long-term dependencies within such sequences. Here, the sequences are divided into tokens of size k k .

CNN: DNABERT generates embeddings for k k -mer tokens in DNA sequences, which capture context-aware representations of the input. The CNN module is used for extracting high-order local features from such embeddings by utilising a convolutional layer.

MCBAM: This module applies spatial and channel attention mechanisms to selectively enhance important local features extracted by the previous module.

MSCA: This module further enhances the local features captured by the feature extraction module. This is achieved by introducing multi-scale convolutions with an attention mechanism. Here, the attention is a form of feature-wise attention which is applied in the context of convolutional feature extraction.

Output module: Using the relevant features captured by MCBAM and MSCA, this module uses such features and applies a series of convolutions, pooling and multi-layer perceptron to provide the final prediction of the presence or absence of TFBSs.

DNABERT is a pre-trained bidirectional encoder to enocode DNA sequences using k k -mer technique. Sequences are divided into tokens of size k k and provided as initial input to DNABERT. Token and positional embeddings are applied to such tokens to form the input matrix M M . This input matrix is then passed through N N sequential encoders to get the embedded matrix M 1 M_{1} . Each such encoder has multi-head self-attention, two layer of normalisations and a feed-forward network. The processing of the multi-head self attention mechanism on the input matrix for each encoder can be given as:

where

Here, all 𝒲 \mathcal{W} s are parameters learned during training of the model. Next, the residue connection M n \textbf{M}^{n} and the multihead attention Multihead( M n \textbf{M}^{n} ) is passed through layer normalisation (LN) and feed forward network (FFN) to obtain:

Finally, after passing through the N N sequential encoder layers, the embedding matrix M 1 M_{1} of size d × D d\times D is obtained where d d is the number of tokens while D D is the embedding dimension.

A single convolutional layer is used in this module to extract high-order local features from the embedded matrix M 1 M_{1} . This module consists of one convolutional block with convolutional operation C ​ o ​ n ​ v 1 Conv_{1} , batch normalisation (BN), Gaussian error linear unit (GELU) activation function and dropout operation. This operations can be given as:

Spatial and channel attention blocks [ 26 ] are used in this module to enhance important local features obtained from the previous module. As given in [ 26 ] , the order of the two submodules affects the overall performance and in their work they have considered Channel-Spatial module. However, in our work (as reported later in Table I ), spatial attention before channel attention provides a slightly better result. This placement of attention blocks has also shown better results in [ 27 ] . The detailed operations of MCBAM module is given in Figure 2 .

As shown in Figures 1 and 2 , spatial attention is applied to feature matrix M 2 M_{2} . In this regard, initially M 2 M_{2} is subjected to global maxpooling and global average pooling in order to extract the spatial features. Convolution operation C ​ o ​ n ​ v 2 Conv_{2} is then applied on such features and finally a sigmoid function is applied, resulting in spatial attention feature M S M_{S} . Subsequently, element-wise matrix multiplication is carried out between M 2 M_{2} and M S M_{S} to generate M 2 ′ M_{2}^{\prime} . The aforementioned operations can be expressed as:

Once M 2 ′ M_{2}^{\prime} is constructed, channel attention submodule is applied on M 2 ′ M_{2}^{\prime} where each of its channel is subjected to global maxpooling and global average pooling separately. The resultant features are then individually passed through two convolutional layers where the first layer has convolution operation C ​ o ​ n ​ v 3 , 1 Conv_{3,1} and a GELU activation function while the second layer consists of only a convolution operation C ​ o ​ n ​ v 3 , 2 Conv_{3,2} . The resultant feature channels are then added and passed through a sigmoid function to acquire the channel attention feature M C M_{C} . Element-wise matrix multiplication is then performed between M C M_{C} and M 2 ′ M_{2}^{\prime} resulting in the feature matrix M 3 M_{3} which is the final output of MCBAM module. These operations can be given as:

This module utilises multi-scale convolutions with attention to further enhance the local features captured by the feature extraction module. As shown in Figure 1 , three separate convolutions C ​ o ​ n ​ v 4 , 1 Conv_{4,1} , C ​ o ​ n ​ v 4 , 2 Conv_{4,2} and C ​ o ​ n ​ v 4 , 3 Conv_{4,3} are applied to each input channel of the feature matrix M 2 M_{2} . The results of such convolutions are concatenated along the channel dimension producing M 2 ′′ M_{2}^{\prime\prime} , thus retaining all multi-scale information across channels. Next, a point-wise convolution C ​ o ​ n ​ v 5 Conv_{5} is applied on M 2 ′′ M_{2}^{\prime\prime} , thereby combining and compressing the concatenated features into a unified representation, enabling the model to learn meaningful relationships between features from different scales. Subsequently, a batch normalisation and a sigmoid activation function are applied to capture attention weights. Finally, element-wise multiplication is performed between such attention weight matrix M 2 ′′′ M_{2}^{\prime\prime\prime} and M 2 M_{2} to get the final output. In this way, features that are deemed more relevant (with higher weights) are enhanced, while less relevant features are suppressed. Such operations can be summarised as:

Thus, M 4 M_{4} is the final matrix of the MSCA module.

The output block considers the feature matrices M 3 M_{3} and M 4 M_{4} respectively, obtained from MCBAM and MSCA modules. This has the effect of parallel attention [ 27 ] in the output module, thereby exploiting both MCBAM and MSCA modules. The matrices obtained from these modules are passed separately through convolutional operations C ​ o ​ n ​ v 6 Conv_{6} and the resultant matrices are combined via addition which are then passed in parallel through global maxpooling and average pooling separately. The resultant matrices M 5 M_{5} and M 6 M_{6} are then concatenated and passed through yet another convolution operation with GELU as the activation function along with batch normalisation and dropout operations, leading to the feature matrix M 7 M_{7} . Finally, the prediction is obtained by flattening M 7 M_{7} and subsequently applying multilayer perceptron which consists of a fully connected layer with dropout as well as another fully connected layer with softmax activation function. The output of this module is the prediction probability y ^ \hat{y} , which predicts if a given DNA sequence consists of TFBSs. All the aforementioned operations can be depicted as:


## II-C Model Training

For training purpose, cross-entropy loss function is used in this work [ 6 ] :

Here, y y are the actual values of the DNA sequences while y ^ \hat{y} are the predicted values of TFBS-Finder and η \eta represents the batch size of DNA sequences which is considered as 64 in this work. AdamW optimisation method is used in this work while ReduceLROnPlateau is used as the scheduler which automatically aids in reduction of learning rate when the value of area under the precision-recall curve plateaus. Moreover, to prevent overfitting, early stopping and dropout are also used in this work where the dropout values are set to 0.2 and 0.3. The training is performed for 15 epochs. All the hyperparameters are selected based on experiments. All such hyperparameter values are provided in Supplementary Tables S2 and S3.


## III Results and Discussions

This section discusses the different results as obtained in this work. Initially, the analysis is performed to check if TFBS-Finder is able to differentiate sequences containing TFBS from shuffled sequences. As TFBS-Finder model is made up of a combination of 5 modules, we have conducted ablation studies to evaluate the contribution of such modules. We have also investigated the ability of TFBS-Finder when trained on sequences coming from a given cell-line to recognise sequences of different cell-lines, observing substantial cross- cell line consistency. Subsequently, we have performed comparison studies with existing state-of-the-art predictors to show the superiority of TFBS-Finder.


## III-A Performance Metrics

The different metrics used in this work to showcase the prediction performance of TFBS-Finder are accuracy, PR-AUC and ROC-AUC. Accuracy represents the proportion of correctly predicted samples. However, accuracy can turn out to be a biased metric when the data is imbalanced. In this regard, PR-AUC and ROC-AUC are some other parameters to judge prediction performance. PR-AUC is the area under the precision-recall curve and represents the model’s overall performance. Its value lies between 0 and 1 where a higher value of PR-AUC depicts better prediction performance. For imbalance class distributions, PR-AUC is a better metric than Accuracy. Another metric which is equally suitable for evaluating predictor performance is ROC-AUC or Area Under the Receiver Operating Characteristic curve, which is a graphical representation of the performance of a binary classification model at various classification thresholds. In order to evaluate the performance of TFBS-Finder, all the three metrics have been used in this work. However, since early stopping is used in this work to avoid overfitting, PR-AUC is used as the early stopping criteria. If PR-AUC does not improve for 2 consecutive runs during validation, the model stops training. We have used different values of k k (3, 4, 5 and 6) and observed that with k k =5, we get the best results. Thus, all the following experiments are conducted with k k = 5.


## III-B Ablation Study

TFBS-Finder uses different important modules such as DNABERT, CNN, MCBAM and MSCA for predicting TFBSs. In order to showcase their individual contributions, experiments and ablation studies are performed on 165 ChIP-seq datasets with different variants to compare such variants.

DNABERT+Output (Variant 1): In this variant, only DNABERT+Output is considered. All other modules are removed.

DNABERT+CNN+Output (Variant 2): Only DNABERT with CNN and output modules are used in this variant.

DNABERT+CNN+MSCA+Output (Variant 3): In this variant, the MCBAM module is removed.

DNABERT+CNN+MCBAM+Output (Variant 4): In this variant, the MSCA module is removed.

DNABERT+CNN+CBAM+MSCA+Output (Variant 5): Here, the positions of spatial and channel attention modules are reversed (such position is similar to CBAM [ 26 ] ) that is, channel attention comes before spatial attention module in order to show the importance of their individual position in the MCBAM module.

As observed from the results in Table I in Variant 1, with accuracy, PR-AUC and ROC-AUC scores of 0.918, 0.954 and 0.955, DNABERT provides strong representations of both local motifs and global dependencies. It performs well because the self-attention mechanism is inherently capable of capturing the relationships between tokens at various scales. The addition of CNN in Variant 2 captures localized features or motifs in the DNA sequences that may complement the global representations from DNABERT, thereby providing an accuracy of 0.925 and PR-AUC and ROC-AUC of 0.957 and 0.956 respectively. In variant 3, MSCA introduces a mechanism to expand the receptive field of CNNs, which helps capture broader local context providing an accuracy, PR-AUC and ROC-AUC score of 0.900, 0.942 and 0.942 respectively. However, DNABERT already excels at capturing global context through self-attention, so adding only MSCA might create redundancy or disrupt DNABERT’s well-calibrated global representations. Spatial and channel attention mechanisms in Variant 4 focus on specific regions of feature maps and refines the features captured by the CNN module leading to scores of 0.909, 0.950 and 0.950 for all the parameters. Although these mechanisms can improve certain tasks, they might conflict with global attention of DNABERT by overemphasizing local features, leading to a loss of global context. Significant improvement (accuracy, PR-AUC and ROC-AUC values of 0.927, 0.961 and 0.961) is noticed for Variant 5 when MSCA is added to channel and spatial attention mechanisms. The proposed model TFBS-Finder shows the best performance across all variants in which an optimal balance is observed between local and global feature extraction. Here, CNN captures localised patterns while spatial and channel attention in MCBAM module refine these patterns by focusing on relevant regions and channels. The MSCA module also provides an additional mechanism to capture multi-scale features and broader local context using dilated convolutions. This increases the receptive field and allows the model to learn a diverse set of features at various scales. All these modules together achieve an accuracy, PR-AUC and ROC-AUC of 0.930, 0.961 and 0.961 respectively. The detailed results are provided in Supplementary Table S4.

(a) (b) (c)

Figure 3 shows the violin plots for the prediction performance of TFBS-Finder and the 5 variants. The median values of accuracy for the 5 variants and TFBS-Finder are respectively 0.913, 0.925, 0.902, 0.913, 0.927 and 0.928 while for PR-AUC (and ROC-AUC respectively), such values are 0.954, 0.956, 0.942, 0.950, 0.959 and 0.960 (0.953, 0.954, 0.941, 0.950, 0.959, 0.960). In terms of quartile values (lower and upper) TFBS-Finder also shows superior performance. Such values for lower (and upper) quartiles for TFBS-Finder in terms of accuracy, PR-AUC and ROC-AUC are respectively 0.911, 0.948, 0.948 (0.955, 0.978, 0.976). Among the variants, Variant 5 has the closest performance to TFBS-Finder. The lower (and upper) quartiles for Variant 5 for accuracy, PR-AUC and ROC-AUC are 0.907, 0.948, 0.947 (0.952, 0.978, 0.976). Considering all the metrics, it can be observed that although Variant 5 gives equally competent results, the experiments show that TFBS-Finder works slightly better for all the performance metrics.


## III-C Cross-cell line validation

Cross-cell line validation is performed in order to show the generalisability and robustness of TFBS-Finder to identify the binding sites of a particular TF, in this case CTCF, occurring in different cell lines. In this regard, we have considered four cell lines Gm12878, Helas3, Hepg2 and K562 which have many TFs in common (as shown in Figure 4 ) and also have a large number of CTCF sequences.

(a) (b) (c)

(d) (e) (f)

To prepare the training dataset for cross-cell validation, the training sequences bounded by CTCF are considered as positive while the rest of the sequences bounded by other TFs are considered as negative. This resulted in 71761 positive and 147870 negative sequences for Gm12878. Similarly, for Helas3, these statistics are 84901 and 166311 while for Hepg2 such numbers of positive and negative sequences are 35857 and 381333 and for K562, they are 82297 and 406752. As can be observed from the statistics, the number of negative sequences is quite high as compared to the positive sequences which is quite obvious given the fact that only the sequences bounded by CTCF forms the positive sequences while those bounded by the other TFs together constitute the negative sequences. As the motivation is to identify the binding sites of CTCF, to balance the dataset we have randomly selected a number of negative sequences equal to the number of positive ones while ensuring that the negative sequences have candidates from all the other TFs (71761, 84901, 35857 and 82297 for Gm12878, Helas3, Hepg2 and K562 respectively). The test dataset is also prepared in a similar manner, where the sequences bounded by CTCF are considered as positive and those bounded by other TFs are negative. For example, for CTCF pertaining to Gm12878 (for wgEncodeAwgTfbsBroadGm12878CtcfUniPk), the number of positive sequences in test set is 8644 indicating that there are 8644 such sequences in the dataset wgEncodeAwgTfbsBroadGm12878CtcfUniPk with TFBSs for CTCF while 37098 negative sequences constitute the other 15 TFs. For the other TFs, the number of positive sequences includes the binding sequences of CTCF in wgEncodeAwgTfbsBroadGm12878CtcfUniPk and wgEncodeAwgTfbsUtaGm12878CtcfUniPk, while the negative sequences are their own binding sites. This method of data preparation is also true for the other cell lines. Detailed statistics is provided in Supplementary Table S5.

Table II shows the average values over all the TFs of ROC-AUC scores for TFBS-Finder trained on the four cell lines Gm12878, Helas3, Hepg2 and K562 and then tested on the testing samples of these cell lines to predict the corresponding CTCF binding sites. The diagonal values indicate the traditional cell line prediction while the rest of the values show the cross-line validation results. It can be observed from the results that TFBS-Finder has a high score of more than 0.93 in all the cases, thereby showcasing the generalisability and robustness of the proposed model.

(a) (b)

(c) (d)

Figure 5 shows the distributions of the prediction performance of TFBS-Finder based on ROC-AUC when trained on Gm12878, Helas3, Hepg2 and K562 while tested for the related cell lines. For Hepg2, the traditional validation shows superior performance with the median value as 0.961. However, for the other cell-lines, cross-validations show slightly better performance. As shown in [ 6 ] , CTCF and YY1 show similarity in their binding regions, thereby often misclassifying sequences bound by YY1 as CTCF. This is also observed in all the figures of Figure 5 . Moreover, CoREST is also misclassified as CTCF for all the cell lines while MYC is misclassified in Helas3 and Hepg2 while HDAC is misclassified in Helas3. This show a probable interaction of CoREST, MYC and HDAC with CTCF. To summarise, the results of Table II and Figure 5 indicate that TFBS-Finder shows good performance for both cross-cell line and traditional validations. The detailed results are provided in the Supplementary Table S6.


## III-D Comparison with existing models

In this subsection, we present the results of the comparison of the prediction performance of TFBS-Finder with other existing models. In this regard, we have considered seven benchmark models which include BERT-TFBS [ 6 ] , DeepBind [ 13 ] , DanQ [ 14 ] , DLBSS [ 28 ] , CRPTS [ 29 ] , D-SSCA [ 17 ] and DSAC [ 16 ] . BERT-TFBS uses DNABERT-2 [ 30 ] as the encoding technique along with CNN and CBAM modules while DeepBind considers one-hot encoding along with CNN architecture. On the other hand, DanQ utilises CNN as well as Bi-LSTM architectures, DLBSS and CRPTS use a shared CNN and CNN with RNN architectures, respectively, while D-SSCA and DSAC use CNNs and attention mechanisms. The results of this comparison are based on 165 ChIP-seq datasets where the dataset is the same as considered in [ 6 ] .

Table III shows the comparison among TFBS-Finder and other existing predictors considering the average values of accuracy, PR-AUC and ROC-AUC over all cell lines and all TFs. As can be observed from the table, TFBS-Finder outperforms all other models. The best performance among the existing predictors is shown by BERT-TFBS. However, TFBS-Finder with accuracy, PR-AUC and ROC-AUC of 0.930, 0.961 and 0.961 respectively, outperforms BERT-TFBS by 7.9%, 4.1% and 4.2%. The detailed results are provided in the Supplementary Table S7.

(a) (b) (c)

Figure 6 reports the distributions of accuracy, PR-AUC and ROC-AUC scores of TFBS-Finder along with other state-of-the-predictors. TFBS-Finder shows the best performance amongst all the benchmark predictors in terms of median, lower and upper quartiles. TFBS-Finder has median values of 0.928, 0.960 and 0.960 for accuracy, PR-AUC and ROC-AUC which are 7.5%, 3.4% and 3.4% better than BERT-TFBS. The lower quartiles (and upper quartiles) values for accuracy, PR-AUC and ROC-AUC scores of TFBS-Finder are 0.911, 0.948 and 0.948 respectively (0.955, 0.978 and 0.976) which are better than BERT-TFBS by 10.3%, 5.5% and 5.8%(1.6%, 5% and 1.3%). The above results showcase the superiority of TFBS-Finder over other existing state-of-the-art predictors in predicting TFBSs on the 165 ChIP-seq datasets.


## IV Conclusion and Future Work

In this work, we propose TFBS-Finder which utilises DNABERT for global context while CNN, MCBAM and MSCA performs feature extraction and capture local contexts to predict TFBSs for DNA sequences. TFBS-Finder is trained and tested on 165 ChIP-seq datasets where the experimental studies show that TFBS-Finder outperforms the existing predictors in terms of average accuracy, PR-AUC and ROC-AUC. We have performed ablation studies to understand the importance of local and global contexts to identify TFBSs. Furthermore, cross-cell line validations are also performed to show the generalisability and robustness of TFBS-Finder. Although, the proposed model shows very inspiring results, as a future work, we would additionally like to incorporate DNA structure information along with DNA sequences to see the effect on the prediction capacity of TFBS-Finder.


## V Acknowledgment

This work has been carried out under SERB-SURE scheme (SUR/2022/002836), funded by Government of India. The authors show their gratitude to the Italian CINECA Consortium for graciously providing the required computational resources.


## References