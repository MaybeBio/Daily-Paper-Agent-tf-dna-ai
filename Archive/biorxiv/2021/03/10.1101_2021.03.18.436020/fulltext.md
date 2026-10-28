## Abstract

Accurate prediction of protein-ligand binding affinity is important in that it can lower the overall cost of drug discovery in structure-based drug design. For more accurate prediction, many classical scoring functions and machine learning-based methods have been developed. However, these techniques tend to have limitations, mainly resulting from a lack of sufficient interactions energy terms to describe complex interactions between proteins and ligands. Recent deep-learning techniques show strong potential to solve this problem, but the search for more efficient and appropriate deep-learning architectures and methods to represent protein-ligand complexes continues. In this study, we proposed a deep-neural network for more accurate prediction of protein-ligand complex binding affinity. The proposed model has two important features, descriptor embeddings that contains embedded information about the local structures of a protein-ligand complex and an attention mechanism for highlighting important descriptors to binding affinity prediction. The proposed model showed better performance on most benchmark datasets than existing binding affinity prediction models. Moreover, we confirmed that an attention mechanism was able to capture binding sites in a protein-ligand complex and that it contributed to improvement in predictive performance. Our code is available at https://github.com/Blue1993/BAPA .

Author summary The initial step in drug discovery is to identify drug candidates for a target protein using a scoring function. Existing scoring functions, however, lack the ability to accurately predict the binding affinity of protein-ligand complexes. In this study, we proposed a deep learning-based approach to extract patterns from the local structures of protein-ligand complexes and to highlight the important local structures via an attention mechanism. The proposed model showed good performance for various benchmark datasets compared to existing models.


## Introduction

Structure-based drug design (SBDD) is a method widely used for identification of drug candidates. SBDD includes docking-pose evaluation and estimation of interaction strength between target proteins and small molecules (ligand) [ 1 ]. The strength of interactions, known as binding affinity, is generally calculated using various scoring functions. The stronger the interaction, the more the ligand affects the physiological function of the target proteins, so ligands that bind strongly to target protein are selected as drug candidates [ 2 ]. Since the predicted binding affinity of the ligand in a library can be used for virtual screening or used to lead optimization, accurate prediction of the binding affinity can reduce the cost of de novo drug design [ 3 ].

Mancy scoring functions have been proposed including force-filed-based [ 4 , 5 ], knowledge-based [ 6 , 7 ], and empirical scoring functions [ 8 , 9 ]. Empirical scoring functions are known to show the best prediction performance among the three categories of functions [ 10 ], and these empirical functions exploit descriptors of various protein-ligand interactions to calculate a binding affinity score. Those descriptors generally include hydrogen bond, desolvation, van der Waals (vdw), and hydrophobic effects. The coefficient of each descriptor is estimated based on the known binding affinity of protein-ligand complexes. A limitation of the empirical methods, however, is the poor correlation between the experimental and predicted affinity scores. One of the main reasons for this poor correlation is that empirical methods use few terms related to protein-ligand complexes for easy interpretation of results, resulting in failure to describe the true complexity of protein-ligand complexes [ 11 ].

Machine learning-based scoring functions [ 12 – 16 ] have been proposed to overcome the limitations of empirical scoring functions and to provide better prediction performance. Those methods exploit various statistical descriptors that are calculated from information about the chemical and physical structure of known protein-ligand complexes [ 17 ]. One representative machine learning-based method is RF-Score [ 12 ]. This method represents intermolecular interaction by count of atom pairs with nine heavy-atom type ( C , N , O , F , P , S , Cl , Br , and I ). RF-Score showed significant improvement compared to existing methods on the PDBbind [ 18 ] v2007 benchmark set. Moreover, RF-Score v3 [ 13 ], which has six additional features, achieved higher predictive accuracy than the original RF-Score model. Another machine learning-based method is structural interaction fingerprints (SIFt) [ 14 ], which represents intermolecular interactions with a fingerprint-like format. However, a limitation of SIFt is that the number of interaction types is insufficient to handle the complexity of protein-ligand complexes. To overcome this limitation, structural protein-ligand interaction fingerprints (SPLIF) [ 15 ] and protein-ligand extended connectivity (PLEC) fingerprints [ 16 ] have been proposed. Both of these methods are based on extended connectivity fingerprints (ECFP) [ 19 ].

Recent advances in deep learning in computer vision have led to the development of deep learning-based scoring functions [ 20 – 23 ]. Compared to traditional machine-learning methods, deep learning-based methods do not require domain knowledge for feature selection [ 24 ] and can identify hidden patterns using nonlinear transformation [ 25 ]. Representative methods using convolutional neural networks (CNN) are Pafnucy [ 20 ] and KDEEP [ 21 ]. In the two CNN-based methods, each channel is composed of chemical information extracted from a three-dimensional sub-grid for each protein-ligand complex. The problem is that chemical information includes several features such as atomic partial charges, which are calculated using empirical methods like AM1-BCC [ 26 ], and which can be incorrect [ 22 ].

Fingerprints based on interaction descriptors are an alternative to multidimensional channel representation. However, a limitation of this representation is that it is insufficient to consider the complexity of protein-ligand interaction. We defined descriptors based on RF-Score features for various patterns of interaction. The challenge in this situation, however, is that when diversity is considered, the dimension of fingerprints increases, so it becomes difficult for the predictive model to capture information that is highly related to binding affinity. In sequence-based binding affinity prediction studies, an attention mechanism was introduced to learn binding sites in the training process from training data [ 27 , 28 ]. We introduced an attention mechanism for capturing descriptors that are important in the prediction of affinity. Another, concern is the lack of distance information in descriptors used in this study. To supplement the descriptors, we used Vina terms, a quantitative numerical value of intermolecular interactions reflecting distance information. This idea was referred to in RF-Score v3.

In the current study, we proposed a deep learning-based model named BAPA (Binding Affinity Prediction with Attention) to improve the accuracy of protein-ligand binding affinity prediction. The proposed model has two important features. First, descriptor embeddings that contains embedded information about the local structures of a protein-ligand complex is learnable, which is means that it is constantly updated for more proper embedding of local structures. Second, we introduced an attention mechanism for highlighting important descriptors to binding affinity prediction. A descriptor vector represents information about the local structure of a protein-ligand complex. In the BAPA, a convolutional layer transforms those descriptor vectors to latent representation and an attention layer captures important descriptors related to binding affinity prediction from the latent representation. This process is shown in Fig 1 . When compared with existing methods on four benchmark datasets, BAPA generally show better prediction performance.


## Results


## Model performance evaluation metrics

The performance of binding affinity prediction models was evaluated via five metrics: mean absolute error (MAE), root mean square error (RMSE), Pearson’s correlation coefficient ( R p ), Spearman’s correlation coefficient ( R s ), and standard deviation in regression (SD). MAE and RMSE compute the average of errors between true and predicted affinity scores. Two correlation coefficients measure the linear correlation between true and predicted scores. The SD exhibits the average distance that the true affinities fall from the regression line.


## Selection of the optimal number of descriptors

CNN uses convolution operation to extract features from the input while considering the association of pixels close to the distance (spatial information). However, the order of each element of the descriptor vector d is randomly arranged. To arrange the adjacency of related descriptors, we assigned the priority of the descriptors using a random forest regressor trained using the training dataset. Each descriptor is sorted in descending order according to random forest priority.

The initial descriptor vector d is a very spare vector, with 9,333 descriptors as elements. The following experiment was conducted to select only the descriptors more essential for the prediction of binding affinity and to represent them in a compact vector form. Among the 9,333 descriptors, the top 500, 1,000, 1,500, 2,000, 2,500 and 3,000 descriptors were selected. After proposed prediction model was trained using the training dataset, and performance evaluation was conducted according to the number of descriptors using the validation dataset. As shown in Table 1 , the best performance was shown with the use of 2,500 descriptors, so 2,500 (= u ) was selected as the optimal number of descriptors.


## Evaluation of the prediction performance on CASF benchmark

We compared BAPA with four existing popular prediction models including RF-Score v3 [ 13 ], Pafnucy [ 20 ], PLEC-linear [ 16 ], and Onionnet [ 22 ]. All models were performance evaluated with the test datasets after training with the training dataset used in this study.

We first presented the results of the CASF-2013 [ 29 ] benchmark set containing 195 complexes in Table 2 . We confirmed that BAPA outperformed the four-baseline model with R p = 0.77 and R s = 0.77. Furthermore, when compared to the second-best model, BAPA reduced MAE and RMSE by 0.12 and 0.11, respectively.

Results of the CASF-2016 [ 30 ] benchmark set containing 285 complexes are shown in Table 3 . We confirmed that BAPA has the lowest MAE, RMSE, and SD and highest R p and R s compared to other models. Our conclusion for the CASF benchmark sets is that BAPA provided an overwhelming advantage in terms of errors.


## Evaluation of the prediction performance on additional test dataset

We performed additional evaluation of predictive performance using the benchmark set obtained from the external database (CSAR NRC-HiQ [ 31 ]). For CSAR NRC-HiQ set2 containing 49 protein-ligand complexes, BAPA showed the best performance with respect to linearity, but with respect to errors, BAPA demonstrated only the second-best performance. These results are shown in Table 4 .

Finally, we presented the results for CSAR NRC-HiQ set1 containing 55 complexes in Table 5 . BAPA had the lowest MAE and RMSE and the second-best performance R p , R s , and SD. Our conclusion regarding the CSAR NRC-HiQ set is that it is difficult to say that any specific model is superior, but considering all the metric results, BAPA is slightly superior compared to other models.


## Generalization performance evaluation based on similarity

In machine learning, generalization refers to the ability of a model to show good performance for new data, that is, data that has not been used for training. In the current study, we attempted to evaluate generalization by constructing complexes of non-overlapping training dataset and test datasets based on PDB ID. However, since the complex is a protein-ligand pair, it should be considered that the proteins of training dataset and homolog proteins or similar proteins may exist in the test datasets. (In the case of a ligand, a homolog ligand or a similar ligand may exist.) Therefore, we performed the following experiment with reference to Li et al., [ 32 ] to evaluate the performance of the model according to protein structure similarity or ligand structure similarity.

The structure similarity between the two proteins is calculated by TM-align [ 33 ] and is defined as the TM-score [ 34 ]. The TM-score has a value between 0 and 1, and higher TM-scores indicate similarity in structure of the two proteins. Since most proteins have multiple chains, the TM-score was measured by comparing all chain structures of each protein. The structure similarity between the two proteins was defined as the lowest TM-score value, since several values may be present depending on the chain structure. Finally, the protein structure similarity of each complex in the test dataset to the training dataset was defined as an average value. Each complex in the test dataset was classified into one of two equal bins, a low similarity bin, and a high similarity bin, according to its similarity with the training dataset.

BAPA showed the best performance regardless of protein structure similarity for three test datasets (CASF-2013, CSAR NRC-HiQ set2, CASF-2016). These results can be seen in Tables 6 – 7 and S1 Table. In particular, for the high similarity complexes of the CSAR NRC-HiQ set2 test dataset, BAPA showed overwhelmingly high performance compared to other models. The results of the CSAR NRC-HiQ set1 are shown in S2 Table. For the high similarity complexes of the CSAR NRC-HiQ set1 test dataset, RF-Score v3 showed better prediction performance than BAPA. However, BAPA showed better performance than RF-Score v3 for the low structure similarity complexes. Therefore, it may be concluded, that BAPA showed good generalization ability.

To evaluate the performance of the model according to the ligand structure similarity, the structure similarity between the two ligands was defined as the SMILES-based Tanimoto coefficient [ 35 ]. As with proteins, the ligand structure similarity of each complex of the test dataset to the training dataset was defined as an average value. According to this value, complexes were classified into one of two equal bins of either low similarity or high similarity. In the case of ligands, BAPA showed generally good generalization performance for three test datasets (CASF-2016, CASF-2013, CSAR NRC-HiQ set2). These results are presented in S3-S5 Tables. In the CSAR NRC-HiQ set1 test dataset, BAPA showed lower performance than RF-Score v3 for low similarity complexes (S6 Table). Our conclusion, based on the results of these experiments, is that BAPA shows an overwhelmingly good generalization performance for protein structure similarity but demonstrates limitations in generalization performance for ligand structure similarity. Data on protein structure similarity and ligand structure similarity of each complex used in this experiment are provide in S7-S8 Tables.


## Assessment of module importance via ablation test

BAPA, proposed in this paper, showed good performance in various benchmark sets by applying 1D convolution to input generated from protein-ligand interaction descriptors, adding Vina terms, and applying an attention layer. In this architecture, to analyze the module that most affects the performance of the model, the ablation test was performed assuming 4 cases. The results are shown in Table 8 . The descriptor vector is denoted as ‘D’, the attention layer as ‘A’, and Vina terms as ‘V’. In the table, (‘D + A’) means that the experiment was conducted by removing the layer corresponding to the Vina terms from BAPA’s architecture (‘D + V + A’). Similarly, (‘D + V’) means the experiment was performed after removing the attention layer.

The poorest performance was shown when descriptors were used alone, as expected. However, contrary to our expectations, the use of Vina terms (‘D + V’) showed better performance than the use of the attention layer (‘D + A’). In other words, we confirmed that Vina terms have greater influence on predictive performance improvement than the attention layer. However, the best performance was shown when both modules were used, allowing us to confirm that the two modules complement each other and contribute to the performance. Similar trends were shown for the remaining 3 test datasets, as shown in the S9-S11 Tables.


## Analysis of attention vector

BAPA generally showed good performance in test datasets, and we confirmed that the attention layer is an important module for improvement of prediction performance in the ablation test. The presumed explanation for these results was that BAPA identified descriptors that related to the regions of protein-ligand interactions, e.g., binding sites, from the data. To prove this, the attention vectors of the two complexes (PDB ID: 1EBY), (PDB ID: 3DD0) were calculated, and the attention weights corresponding to the top 10% for each complex were then extracted. This has the same meaning as extracting descriptors with the top 10% attention weights for each complex.

The 1EBY complex (HIV protease in complex with the inhibitor BEA369) has 38 binding sites-related interactions based on the sc-PDB database [ 36 ]. The inhibitor BEA369 is located in the center and is connected by a purple straight line (ligand bond) in Fig 2A . The green dash lines and the brick-red spoked arcs indicate hydrogen bonds and hydrophobic contacts between the two atoms, respectively. For example, (C48, Asp29-CB) connected by a green dash line indicates a hydrogen bond between the C48 atom of inhibitor BEA369 and the CB atom of aspartic acid, residue 29 of HIV protease. The brick-red spoked arc (C33, Val82-CG1) indicates the hydrophobic contact between the C33 atom of inhibitor BEA369 and the CG1 atom of valine, residue 82 of HIV protease. We confirmed that the extracted top 10% descriptors included all 38 binding sties, and these were highlighted in yellow. These results are presented in Fig 2A . The 3DD0 complex has 9 binding sites-related interactions based on the sc-PDB database. We confirmed that the extracted top 10% descriptors include all interactions except for the two interactions (S2, Val121-CG2) and (N1, Thr199-N). The first refers to the hydrophobic contact between the S2 atom of ethoxzolamide and the CG2 atom of valine, residue 121 of carbonic anhydrase 2, and the second refers to the hydrogen bond between the N1 atom of ethoxzolamide and the N atom of threonine, residue 199 of carbonic anhydrase 2. These results are presented in Fig 2B . We can see that BAPA’s attention layer can capture important regions for interactions. The figure was plotted using Ligplot + [ 37 ].


## Discussion

In this paper, we proposed BAPA, which could be used for virtual screening and lead optimization in SBDD. The input of convolutional layer was generated using descriptor information and a learnable embedding matrix. The descriptor is a data structure that contains information about the local structure of the protein-ligand complex, and the embedding matrix is a matrix that contains embedded information about the descriptors. The embedding matrix is constantly updated for more appropriate (proper) embedding of the local structure. In addition, the attention mechanism was used to improve the predictive power of the model. The attention model could identify important descriptors in the protein-ligand complex, which would be expected to help researchers design better compounds. BAPA and others existing scoring functions were tested for the CASF-2016 and CASF-2013 benchmark sets. We confirmed that BAPA showed the best performance on both benchmark sets. In addition, BAPA showed good generalization performance for proteins with low structure similarity, which means that more accurate prediction performance can be expected for unseen proteins.

BAPA showed improved predictive performance, but a limitation remains with respect to binding sites that the attention layer cannot capture. There are two main explanations for this limitation. First, we ordered the array of descriptors based on the contribution of random forest in consideration of the convolution operation. However, there may be no association between these sorted descriptors. Second, the architecture of recent neural network models has many layers for feature extraction from the input. For example, Resnet [ 38 ] has 15 layers through introduction of skip-connection. BAPA, has a relatively low layer architecture in comparison. In the future, we plan to conduct research to overcome the limitations of our model.


## Materials and Methods


## Building dataset and preprocessing

We collected the PDBbind [ 18 ] v2016 refined set consisting of 4,507 complexes. The PDBbind dataset consists of 3D structure data of protein-ligand complexes and corresponding binding affinities expressed with pK a (− logK d or − log K i ) values. We also collected the PDBbind v2018 general set (16,126 complexes), CASF-2016 dataset (285 complexes), and CASF-2013 dataset (195 complexes). The latter two datasets were used only as test datasets for model performance evaluation. Training and validation datasets were constructed using the PDBbind v2016 and v2018 datasets. The training dataset comprised 3,689 complexes obtained by removing complexes that overlap with CASF-2016 and CASF-2013 datasets from the refined set . The validation dataset for model parameter optimization was composed of 677 complexes obtained by removing complexes that overlap with the training, CASF-2016, and CASF-2013 datasets from the v2018 general set . Removing was processed based on the PDB ID.

Previous studies have suggested that performing training and test using data provided by a specific database tends to yield overly optimized results [ 39 – 41 ]. We collected CSAR NRC-HiQ set1 and CSAR NRC-HiQ set2 composed of 176 and 167 complexes, respectively, as external test datasets. For each dataset, we removed complexes that overlapped with the training, validation, CASF-2016, and CASF-2013 datasets. This resulted in 55 complexes for CSAR NRC-HiQ set1 dataset and 49 complexes for CSAR NRC-HiQ set2 dataset used as test datasets. A summary of each dataset is shown in Fig 1 , and PDB IDs for all complexes in each dataset are provided in S12 Table.

In the PDBbind database, the crystal structure data of proteins are provided in PDB file format. All water molecules and cofactors were removed from the crystal structure, and USCF Chimera [ 42 ] and Openbabel [ 43 ] were used for preprocessing.


## Definition of descriptor

BAPA’s input, a molecular complex, is represented as a 1D vector, which is calculated based on descriptor information obtained from the training dataset. To generate descriptors focused on the contacted protein and ligand atom pairs in the molecular complex, we used nine heavy atoms of the protein and ligand. Let L be a list of heavy atoms in ligands [ C L , N L , O L , F L , P L , S L , Cl L , Br L , I L ] where L [ i ] is the i -th atom type of the ligand (0 ≤ i ≤ 8). Likewise, let P be a list of heavy atoms in proteins [ C P , N P , O P , F P , P P , S P , Cl P , Br P , I P ] where P [ j ] is the j -th atom type of protein (0 ≤ j ≤ 8). For each i and j , a set of contacts X [ i ][ j ] is defined by: where L [ i ] l and P [ j ] k are the l -th atom of the i -th atom type in the ligand and the k -th atom of the j -th atom type of the protein, respectively. The distance between the protein atom and the ligand atom pair is calculated by Euclidean distance. We use 12 Å as d cutoff , based on previous studies [ 13 , 44 ]. For example, there are two atom pairs with the distance is less than 12 Å (in Fig 3 ), so X [2][2] = {( L [2] 4 , P [2] 2 )} = {( O L 4 ↔ O P 2 )} and X [2][0] = {( L [2] 1 , P [0] 21 )} = {( O L 1 ↔ C P 21 )}.

The elements of sets X [ i ][ j ] form an imaginary edge of which two nodes are ligand and protein atom types. A graph that is extended with one-step neighborhoods from the imaginary edge is defined as a descriptor. The edge between the extended one-step neighborhoods and the imaginary edge has one of five bond types (single, double, triple, amide, and aromatic). Following the previous example, ( O L 4 ↔ O P 2 ) is extended to ′ C L 6 − ( O L 4 ↔ O P 2 ) = C P 9 ′ and ( O L 1 ↔ C P 21 ) is extended to ′ C L 1 − ( O L 1 ↔ C P 21 ) = C P 20 − C P 16 ′. Because the order of the bonds (edges) is not considered, ′ C L 1 − ( O L 1 ↔ C P 21 ) = C P 20 − C P 16 ′ and ′ C L 1 − ( O L 1 ↔ C P 21 ) − C P 16 = C P 20 ′ are the same. Removal of the atom indexes yields two descriptors, ′ C L − ( O L ↔ O P ) = C P ′ and ′ C L − ( O L ↔ C P ) = C P − C P ′ in Fig 3 . In this way, u unique descriptors were calculated from the training dataset, and each protein-ligand complex was represented as a descriptor vector d having the frequencies of u unique descriptors as elements.


## Autodock Vina-based additional features

BAPA exploits Vina terms that reflect distance information of intermolecular interactions in a protein-ligand complex. We used five additional intermolecular Vina terms and one flexible Vina terms. Intermolecular Vina terms consist of three steric interactions ( gauss 1 , gauss 2 , repulsion ), hydrophobic , and hydrogen bond terms. The flexible term is the number of active rotatable bonds between the heavy atoms of ligand [ 45 ].


## Prediction model

The proposed model, BAPA, has three kinds of neural network layers (convolutional, attention, and dense) for binding affinity prediction. We designed the model to extract local structure patterns from descriptor vector d via the convolutional layer. The latent representation (encoded vector; e ) of the complex is calculated from the output of the convolutional layer and Vina terms via feedforward network. Based on this information, the attention layer calculates the descriptors important for affinity prediction and yields an encoded context vector z . Finally, the concatenation of an encoded vector e and an encoded context vector z is input to the feedforward network to predict the binding affinity. Every layer was activated with the exponential linear unit (ELU) function and the whole network was implemented by TensorFlow (1.12.0). The overall architecture is depicted in Fig 4 .

The model starts with the embedding matrix E ∈ ℝ u × h to transform each descriptor to the corresponding embedding vector E i ∈ ℝ h where u is the count of descriptors and h is the embedding size. An embedding matrix is initialized by the truncated standard normal distribution. To add local structure information to each descriptor embedding vector, an element of the corresponding descriptor vector (frequency of each descriptor) is multiplied by a weight. Then, the input of the convolutional layer is generated through a dense layer for each column of embedding matrix to which local structure information was added.

To find the pattern in the input, all convolutional layers applied one-dimensional (1D) convolution operation. For example, the first convolutional layer uses three filters, and the stride size of each filter is one, so a feature map with a size of (3 × N × 1) is generated. To extract various patterns of the descriptors, five different window sizes (2, 4, 6, 8, and 10) were used, so that five (3 × N × 1) feature maps were generated in the first convolutional layer. Each of these five feature maps passes through the max pooling layer and decreases in size. The depth of the convolutional layer is four and the convolution operation is the same fashion for all convolutional layers, except that the number of filters is six for the second and third convolutional layers, and nine for the fourth convolutional layer. Detailed parameters for the convolutional layers are provided in S13 Table. The results of the fourth convolutional layer are flattened and concatenated, resulting in a single vector of size 513. The single vector and Vina terms are merged into the encoded vector e , which is the latent vector of the complex in the feedforward network.

In machine translation, the attention mechanism is mainly designed to solve the problem of long-term dependencies when the input sequence is long. When a word is predicted using a decoder, an attention mechanism puts more focus on words that are more related. In this study, we designed the attention layer to focus on more relevant descriptors. The latent representation of the complex (encoded vector e ) is input as an attention layer to calculate the contribution of each descriptor to the affinity prediction.

Encoded vector e and each row of embedding matrix E i are calculated into query vector q , key vector k i , and value vector v i through a dense layer. Note that in this study the key vector k i and the value vector v i have the same value. The similarity between query vector q and key vector k i (0 ≤ i ≤ u ) is calculated using the inner product. The similarities are transformed into descriptor weights via softmax. The weighted sum of the value vector v i over the descriptor weight is used as the context vector c . The context vector c is input to one dense layer to generate the encoded context vector z , which is used to predict the binding affinity together with encoded vector e .

The encoded context vector z , which is an output of the attention layer, and the encoded vector e , are used to predict the binding affinity ( pK a ) through the feedforward network consisting of 512, 256, and 128 neurons.

In the proposed neural network model, the input flows to the output layer in a feedforward fashion. The mean squared error was used as a loss function to train the weights and biases. To prevent overfitting, we applied L2 regularization, so the norm of weights is added to the loss. The Adam optimizer was used for training the network (learning rate 0.005, batch size 256).


## Supporting information

S1 Table. Comparison results using the CASF-2016 dataset with TM-Score.

S2 Table. Comparison results using the CSAR-HiQ set1 dataset with TM-Score.

S3 Table. Comparison results using the CASF-2013 dataset with Tanimoto coefficient.

S4 Table. Comparison results using the CASF-2016 dataset with Tanimoto coefficient.

S5 Table. Comparison results using CSAR-HiQ set2 dataset with Tanimoto coefficient.

S6 Table. Comparison results using CSAR-HiQ set1 dataset with Tanimoto coefficient.

S7 Table. Protein structure similarity of the test dataset to the training dataset with TM-Score.

S8 Table. Ligand structure similarity of the test dataset to the training dataset with Tanimoto coefficient.

S9 Table. Ablation test results with CASF-2013 dataset.

S10 Table. Ablation test results with CSAR NRC-HiQ set2.

S11 Table. Ablation test results with CSAR NRC-HiQ set1.

S12 Table. PDB IDs list for all complexes in each dataset.

S13 Table. Parameters and architecture in convolutional layers.


## Author Contributions

Conceptualization : Sangmin Seo, Jaegyoon Ahn

Data curation : Sangmin Seo

Formal analysis : Sangmin Seo

Funding acquisition: Sanghyun Park, Jaegyoon Ahn

Investigation : Sangmin Seo

Methodology : Sangmin Seo, Jaegyoon Ahn

Project administration : Sanghyun Park, Jaegyoon Ahn

Resources : Sanghyun Park, Jaegyoon Ahn

Software : Sangmin Seo

Supervision : Sanghyun Park, Jaegyoon Ahn

Validation : Sangmin Seo, Jonghwan Choi

Visualization : Sangmin Seo, Jonghwan Choi

Writing – original draft : Sangmin Seo, Jonghwan Choi, Sanghyun Park, Jaegyoon Ahn

Writing – review & editing : Sangmin Seo, Jonghwan Choi, Sanghyun Park, Jaegyoon Ahn


## Footnotes

↵ * ssm6410{at}yonsei.ac.kr (SS); sanghyun{at}yonsei.ac.kr (SP); jgahn{at}inu.ac.kr (JA)