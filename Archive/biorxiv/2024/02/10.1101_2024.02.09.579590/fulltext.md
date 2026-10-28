## Abstract

Background A protein is a large complex macromolecule that has a crucial role in performing most of the work in cells and tissues. It is made up of one or more long chains of amino acid residues. Another important biomolecule, after DNA and protein, is carbohydrate. Carbohydrates interact with proteins to run various biological processes. Several biochemical experiments exist to learn the protein-carbohydrate interactions, but they are expensive, time-consuming, and challenging. Therefore, developing computational techniques for effectively predicting protein-carbohydrate binding interactions from protein primary sequence has given rise to a prominent new field of research.

Result In this study, we propose StackCBEmbed , an ensemble machine learning model to effectively classify protein-carbohydrate binding interactions at residue level. StackCBEmbed combines traditional sequence-based features along with features derived from a pre-trained transformer-based protein language model. To the best of our knowledge, ours is the first attempt to apply protein language model in predicting protein-carbohydrate binding interactions. StackCBEmbed achieved sensitivity and balanced accuracy scores of 0.730, 0.776 and 0.666, 0.742 in two separate independent test sets. This performance is superior compared to the earlier prediction models benchmarked in the same datasets.

Conclusion We thus hope that StackCBEmbed will discover novel protein-carbohydrate interactions and help advance the related fields of research. StackCBEmbed is freely available as Python scripts at https://github.com/nafiislam/StackCBEmbed .


## 1. Introduction

Nucleic acids, proteins, carbohydrates, and lipids are important biomolecules for any organism. Among these, carbohydrates come right after DNA and proteins in terms of importance [ 1 ]. Carbohydrates interact with protein molecules to facilitate various biological processes, such as cellular adhesion, cellular recognition, protein folding, ligand recognition, and so on [ 2 , 3 , 4 ]. Moreover, they provide protection of human cells against pathogens [ 5 ] as well as play an important role as biomarkers or drug targets [ 6 , 7 , 8 , 9 ]. In order to identify protein-carbohydrate interactions, several experimental techniques have been developed. These include X-ray crystallography, nuclear magnetic resonance (NMR) spectroscopy study, molecular modeling, dual polarization interferometry, and so on. However, weak binding affinity and the synthetic complexity of individual carbohydrates have made these techniques more expensive, time-consuming, and challenging [ 10 ]. Therefore, developing a computational technique for effectively predicting protein-carbohydrate binding sites has become an urgent necessity. The computational approaches concentrate on locating the sites of proteins that bind to carbohydrates.

Several computational methods can be found in the literature that leverages structural features to locate protein-carbohydrate binding sites. Taroni et al. [ 11 ] first proposed a method that used known protein structure to predict protein-sugar binding sites. They utilized six different attributes of each site, such as solvation potential, residue propensity, hydrophobicity, planarity, protrusion and relative accessible surface area. Through a feature selection process, three of these attributes (residue propensity, protrusion, and relative accessible surface area) were finally selected. These three parameters were then used to calculate the probability of a surface patch being a carbohydrate-binding site. This method provided 65% accuracy for 40 protein-carbohydrate sequences.

A method called COTRAN, proposed by Sujatha and Balaji [ 12 ], is able to predict galactose-binding sites from known galactose-binding proteins. Galactose-binding proteins are a special class of proteins, and galactose-binding sites vary across different protein-galactose complexes. No common features are known to be shared by these proteins to specifically bind to their targets. This study assumed that common rules exist for how they recognize galactose. As a result, the study examines 18 protein-galactose 3D structures from 7 different families to identify a unique pattern for galactose binding sites. Each family has similar binding sites, but these sites differ between families.

Another method called InCa-SiteFinder was proposed by Kulharia et al. [ 13 ] to predict inositol and carbohydrate binding sites on the protein surface. This method utilizes amino acid propensities and van der Waals interaction energy between protein and a probe. In order to predict glucose binding sites, Nassif et al. [ 14 ] utilized several chemical and residue-based features such as charges, hydrophobicity and hydrogen bonding with support vector machine (SVM) as the classifier. Tsai et al. [ 15 ] fed probability distributions of interacting atoms in protein surfaces to neural networks and SVMs to predict the binding sites. An energy-based approach was proposed in [ 16 ] to identify the protein-carbohydrate binding sites and the residues that have significant roles in binding. This method distinguished 3.3% of residues as binding sites in protein-carbohydrate complexes. In this study, the dominance of Tryptophan (TRP) to communicate with carbohydrates through aromatic-aromatic interactions had also been observed by performing the binding propensity analysis.

Shanmugam et al. proposed a method to identify and study the residues, which are involved in both folding and binding of protein-carbohydrate complexes [ 17 ]. They identified the stabilizing residues by means of hydrophobicity, long-range interactions, and conservations. The binding site residues were identified using a distance cutoff of 3.5Å between any heavy atoms in protein and ligand. The residues that were common in stabilizing and binding, are termed key residues. The study found that most of the key residues are present in β -strands. All- α, α + β , and α/β structural classes have more key residues than the other protein classes. Nevertheless, the structure-based methods discussed thus far rely on protein structures that are not always available, thereby rendering those ineffective as well as highlighting the importance of sequence-based approaches.

Malik and Ahmed [ 6 ] proposed the first sequence-based computational technique in which evolutionary features from the Position Specific Scoring Matrix (PSSM) were used to train a neural network that achieved 87% sensitivity and 23% specificity in a test set of 40 protein-carbohydrate complexes. Pai et al. [ 18 ] and Agarwal et al. [ 19 ] proposed similar PSSM-based methods to predict mannose-binding sites. Another method, SPRTNT-CBH was proposed in [ 10 ] where PSSM features along with other predicted structural features (referred to as sequence-derived structural information) were employed to train an SVM classifier. The classifier achieved 22.3% sensitivity and 98.8% specificity on an independent test set of 50 protein-carbohydrate complexes. Both of the methods mentioned above have issues with imbalanced prediction results, either having high sensitivity and low specificity, or vice versa.

To address these concerns, StackCBPred [ 20 ] employed a stacking ensemble classifier to enhance the prediction accuracy in terms of sensitivity (56.5%) and specificity (79.7%). This classifier was trained using a balanced training dataset and incorporated various evolutionary features as well as sequence-based predicted structural features. This model managed to somewhat mitigate the prediction bias observed in previous methods. Canner et al. [ 21 ] built two deep learning models, CAPSIF:V and CAPSIF:G, that use structures to predict carbohydrate-protein binding sites. Bibekar et al. introduced PeSTo-Carbs, a geometric transformer model, that predicts carbohydrate-protein binding sites using PDB input. They had proposed two models: PS-G and PS-S. However, there is still potential for further improvement in prediction performance. By incorporating more relevant features and exploring various other machine learning (ML) and deep learning (DL) architectures, the prediction performance could potentially be enhanced further.

In this study, we have introduced a stacking ensemble prediction model named StackCBEmbed. This model seamlessly integrates features directly extracted from protein sequences with attributes derived from a pre-trained transformer-based protein language model. An increasingly successful trend in various protein attribute prediction problems has been the utilization of recently developed protein language models [ 23 , 24 ]. These pre-trained models enable the generation of informative features for individual proteins, as well as the residues therein, offering enhanced predictive power while being computationally less intensive compared to evolutionary and other features that necessitate time-consuming database searches. To the best of our knowledge, ours is the first work to incorporate protein embedding features from a language model in the context of protein-carbohydrate binding sites prediction. Our method showed a significant improvement in terms of several prediction metrics, outperforming the state-of-the-art carbohydrate binding site prediction methods. The key contributions of our work can be summarized as follows.

We propose StackCBEmbed, a stacking ensemble prediction model for protein-carbohydrate binding sites. The architecture of the ensemble is determined through an objective approach, searching from a set of base predictors.

We have investigated features from a transformer-based protein language model (ProtT5-XL-U50) alongside conventional sequence-based and evolutionary features. Our results demonstrate the superiority of the embeddings extracted from the protein language model compared to the other features.

As the training dataset is heavily imbalanced, we have applied an ensemble random undersampling approach for data balancing.

In addition to using independent test sets from the literature, we have also prepared an independent test set, named TS46.

StackCBEmbed outperforms state-of-the-art methods for predicting protein-carbohydrate binding sites in terms of sensitivity and balanced accuracy scores, demonstrating a notable improvement across a number of prediction metrics.


## 2. Materials and Methods


## 2.1. Dataset

Zhao et al. [ 25 ] extracted 604 protein-carbohydrate complex structures from PROCARB database [ 26 ]. After removing glycoproteins, they selected only those proteins with more than five carbohydrate-binding residues (i.e., residues that have one or more heavy atoms that are within 4.5 Å of any heavy atom of carbohydrates). They further removed the redundant proteins using BLAST-CLUST [ 27 ] with a sequence identity cutoff of 30%. They thus obtained 113 protein-carbohydrate complexes. Taherzadeh et al. [ 10 ] used the Glyco3d database ( http://glyco3d.cermav.cnrs.fr/home.php ) to obtain more than 1000 three-dimensional structures of protein-carbohydrate complexes. After combining these two sets, they removed low-resolution structures ( > 3 Å) and homologous proteins (30% sequence identity cut-off). They thus obtained 152 protein-carbohydrate complexes. Out of these, 50 proteins were randomly chosen and separated for the independent test set (TS50), and the remaining set (102 proteins), labeled as TR102, was used for model training in their study. Gattani et al. [ 20 ] discarded 2 sequences from TR102, and 1 sequence from TS50, as those contained non-standard amino acids. They referred to the updated sets as the benchmark dataset and TS49, respectively. In our study we have used the benchmark dataset for training our prediction model and TS49 for independent testing. However, we had to leave out two more sequences (IDs: 2c3hB and 2vngB) from the benchmark dataset due to a discrepancy in the number of residues in the FASTA files vs. the PSSM files that we generated thereof.

Gattani et al. created a second independent test set from PROCARB as follows. From the PROCARB604 dataset, the proteins whose IDs matched the protein IDs that were present in the benchmark or TS49 dataset were removed. Redundant proteins with a sequence identity cutoff of 30% were then removed. They thus obtained a set of 88 sequences, which was named TS88. Like them, we too have used this as a second independent test set in our study.

The benchmark dataset contains 98 sequences with 1014 binding residues and 25705 non-binding residues. We randomly selected 30% of these residues to create a validation set, consisting of 275 binding residues and 7741 non-binding residues. The remaining portion was designated as the training set.

Additionally, in this work, we developed a third independent dataset from UniProt ( https://www.uniprot.org/ to further demonstrate the efficacy of our proposed method. To create this dataset, we used the advanced search option of UniProt with the following query:

(ft_binding_exp:”CHEBI:16646”) AND (reviewed:true) NOT (ft_carbohyd:n-linked) NOT (ft_carbohyd:o-linked) NOT (ft_carbohyd:c-linked)

Our search resulted in 122 proteins. After removing the proteins with no positive sites, 115 proteins remained. We then used BLAST-CLUST [ 27 ] with 30% sequence identity, which reduced the dataset to 80 proteins. We further filtered the dataset to include only the proteins that possessed more than five carbohydrate-binding residues and enforced 30% sequence identity cutoff with the benchmark dataset using BLAST-CLUST. The final count of proteins was 46, with 472 positive sites and 18820 negative sites. We named this dataset TS46.

The binding and non-binding residue distributions of the datasets used in our study are listed in Table 1 , from which it is evident that all the datasets are highly imbalanced.


## 2.2. Feature Extraction

Feature extraction is a very important step in the prediction pipeline. In this study, we utilized two types of features: the traditional sequence-based features and the embeddings derived from pre-trained transformer-based protein language models. These features are described below. Notably, after featurization, Yeo–Johnson transformation [ 28 ] was applied, followed by standardization, using PowerTransformer from scikit-learn python package.

Position specific scoring matrix (PSSM) expresses the evolution-derived information in protein sequences. Evolutionarily conserved residues have occupied a prominent place in several biological analyses [ 29 , 30 , 31 , 32 , 33 , 34 ] and they have considerably important functional roles in binding. We generated PSSM using PSI-BLAST [ 35 ] with E-value = 0.001, with 5 iterations. The PSSM is a L × 20 dimensional matrix ( L is the length of the protein sequence) which can be represented by : Here, P i,j indicates the score of the amino acid at position i being changed to amino acid j during the evolutionary process. For each residue, we thus get a 20-dimensional feature vector.

Monogram (MG) [ 36 , 37 ] feature for a residue is extracted from PSSM by summing up the scores for that residue along the protein sequence’s length. Thus, it results in a feature vector of length 1 for each residue and is location invariant. where, 1 < = m < = 20 and L is the length of the sequence.

Di-peptide composition (DPC) [ 38 ] can also be computed from PSSM to capture the partial sequence-order information. As there are 20 × 20 combinations of the dipeptides, this feature can be represented as a 20 × 20 matrix DPC [ i, j ], 1 ≤ i, j ≤ 20, which can later be flattened into a 400-dimensional vector. For the residue at position k , 1 ≤ k ≤ L, DPC [ i, j ] is calculated as follows. Note that for the first and last residues, the indices k − 1 and k + 1 respectively are out of range, therefore the corresponding P values are assumed to be 0. In other words, for the terminal residues, only one of the two terms in the sum has a contribution.

In order to predict the structural and functional features of proteins, as well as the sequence-structure-function relationship, the knowledge of solvent exposure is important. Accessible Surface Area (ASA) [ 39 ] measures the solvent accessibility of a biomolecule and can play a crucial role in predicting binding sites. Here SPIDER3 program [ 40 , 41 , 42 ] was used to predict ASA probabilities at the residue level directly from each of the protein sequences.

ASA has several drawbacks, however. For example, it is quite difficult to determine to what extent a residue is buried, and also, it is impossible to differentiate between the partially buried residue and the deeply buried residue through ASA. In order to solve these issues, HSE had been introduced [ 43 ]. HSE separates a residue’s sphere into two half-spheres: HSE-up and HSE-down. This measure has several interesting properties in the characterization of the residue’s spatial neighborhood, and it does not rely on a full-atom model. Thus, it is very convenient to apply this measure in protein structure modeling and prediction analysis. HSE-up and HSE-down were also extracted using the SPIDER3 program.

The torsion angles Phi ( ϕ ) and Psi ( ψ ) determine the shape of the protein backbone structure. The predicted values of these two angles have been used as features, as they have crucial roles in analyzing protein-carbohydrate interactions. Here, too, we have used SPIDER3 for the predicted torsion angles.

For each of the 20 standard amino acids, we utilized seven different physicochemical properties, as utilized in [ 44 ]: steric parameter, polarizability, normalized Van der Waals volume, hydrophobicity, isoelectric point, helix probability, and sheet probability.

From the latest Natural Language Processing (NLP) research [ 24 ], transformer models were trained on large protein corpora, and these are known as protein language models. The output from the last layer of these models can be used as features in various prediction problems. In our study, we have used ESM2 [ 45 ] and six of the models from [ 24 ]: ProtBert, ProtBert-BFD, ProtT5-XL-BFD, ProtT5-XL-U50, ProtAlbert, and ProtXLNet. ESM2 is a transformer-based protein language model that is trained over millions of diverse natural proteins across evolution using masked language modeling. Here we have used the esm2 t33 650M UR50D model. ProtBert and ProtBert-BFD are BERT-based models [ 46 ] trained on UniRef100 and BFD-100 corpora, respectively. The ProtAlbert model was acquired from the Albert model [ 47 ] while ProtXLNet was acquired from the XLNet model [ 48 ]. Both were trained on the UniRef100 corpora. On the other hand, ProtT5-XL-BFD was obtained from the T5 model [ 49 ] trained on BFD corpora. It was then fine-tuned on the UniRef50 dataset to create the ProtT5-XL-U50 model. Upon comparative analysis of the embeddings for our problem (see Results section), we decided to go with the ProtT5-XL-U50 embedding, which is a 1024-dimensional vector.


## 2.3. Performance Evaluation Criteria

We have used several well-established metrics [ 50 , 51 ] to objectively measure the performance of our prediction model. These are sensitivity (SN), specificity (SP), accuracy (Acc), balanced accuracy (BACC), Precision (Prec), F1-score (F1), and Matthew’s Correlation Coefficient (MCC). These can be mathematically defined as follows: Here, TP, FP, TN, and FN stand for True Positive, False Positive, True Negative, and False Negative, respectively. Additionally, we also assessed the area under receiver operating characteristic curve (AUROC or AUC in short) [ 52 ] and area under precision-recall curve (auPR in short) [ 53 ].


## 2.4. Feature selection

Using the aforementioned feature descriptors, we used incremental feature selection (IFS) to obtain the optimal combination of features. We took a phased approach to IFS (Algorithm 1), where at each phase, we try to augment the current set of features with one additional feature group. Among all the groups, the augmentation that yields the best performance is chosen, and the feature set is updated. The updated feature set is used in the next phas,e and the process repeats. Thus, while the search space of feature group combinations is exponential, only a limited set of combinations is explored in a greedy manner. Finally, of all the combinations explored, the one with the best performance is chosen. To measure the performance of each combination, we trained a classification model with those features using Extreme Gradient Boosting (XGB) from the scikit-learn package in Python [ 54 ], with default parameters. The benchmark dataset, balanced using random undersampling, was used. We used XGB since it has been very successful in numerous ML challenges in Kaggle ( https://www.kaggle.com/ ).


## 2.5. Framework of proposed method

In order to improve the prediction performance, we implemented a stacking ensemble model [ 55 ] using two stages of learners, known as base learners and meta learners respectively. In the first step, multiple base learners were trained using the balanced training dataset. Each trained model was used to make predictions on the validation set. In the next step, the validation set was used to train the meta learner. In this case, however, the feature vector was augmented by concatenating the predictions earlier made by the base learners. These predictions thus form yet another feature descriptor for the meta learner, which we refer to as base learner predictions (BLP) .

We experimented with ten machine learning algorithms: Naive Bayes (NB), K -nearest Neighbor (KNN), Logistic Regression (LR), Partial Least Square Regression (PLS), Support Vector Machine (SVM), Multi-layer Perceptron (MLP), Decision Tree (DT), Random Forest (RF), Extra Tree (ET) and Extreme Gradient Boosting (XGB). The xgboost Python library was used for XGB, while the scikit-learn library was used for the remaining learners. For all the learners, the class discriminating threshold was set at the default value, which is 0.5.

We analyzed the mutual information (MI) [ 56 ] between the residue-wise prediction probabilities and the target variable for each of these learners. As SVM had the highest MI, it was added in


## Incremental Feature Selection

both the base and meta layers. Subsequently, more predictors were added to the base layer in a phased approach as follows. At each phase, we tried to augment the current set of predictors with another predictor and calculated the MI between average prediction probabilities and labels. The predictor for which the average MI became the highest in the phase was added. It is possible that the MI may decrease in a phase from an earlier phase. Nevertheless, the updated set of predictors is used in the next phase, and the process repeats. Finally, the set of predictors that resulted in the highest MI across all the phases is chosen. Accordingly, four classifiers, SVM, MLP, ET, and PLS were selected as the base learners (see Results Section).


## 2.6. Imbalanced data handling

The datasets used in this study were significantly imbalanced. Therefore, it was necessary to balance the training dataset. We applied an ensemble random undersampling approach, inspired by [ 57 ], as follows. We prepared 10 subsampled datasets, each of which contained all positive samples. As to the negative samples, four of these datasets contained 0.2% of the negative samples, randomly selected, three datasets contained 2%, and the remaining three datasets contained randomly selected 20% of the negative samples. Using each of these 10 subsampled datasets, we trained separate SVM, MLP, ET, and PLS models. The validation set was featurized using selected feature descriptors, then augmented with the output of the base layer models, which we have referred to as the BLP descriptor. It was then used to train the SVM model in the meta layer. Data balancing in the meta layer was done using random undersampling.


## 2.7. Hyperparameter tuning

We tuned the hyperparameters of the base and meta layer classifiers to optimize prediction performance. We only tuned the crucial hyperparameters. The rest were set at their default values. We used GridSearchCV from the scikit-learn package in Python to grid search the hyperparameter space. We selected the values of each selected parameter of each classifier that had balanced performance across all performance metrics. After tuning the base classifiers, we applied the same process to the meta layer classifier on the validation dataset.


## 3. Results


## 3.1. Embedding from T5 model outperforms other embeddings

The 10-fold CV results averaged across all 10 predictors trained on protein embeddings from the seven different pre-trained language models are shown in Table 2 . ProtT5-XL-U50 embedding wins with respect to all metrics but sensitivity. However, the difference between it and ESM2 in the sensitivity metric is negligible. The ESM2 came out second best in terms of the other metrics. Therefore we selected the ProtT5-XL-U50 embedding for our model.


## 3.2. Embedding from language model wins over traditional feature descriptors

We wanted to examine how each feature descriptor influences the prediction of protein-carbohydrate binding sites. For each feature descriptor, we trained ten ML algorithms as stated before - NB, KNN, LR, PLS, SVM, MLP, DT, RF, ET, and XGB. The averages across these classifiers were used to compare the predictive ability of the descriptors. As observed from Table 3 , the embedding from ProtT5-XL-U50 exhibited the highest average scores across all performance metrics, indicating its effectiveness in predicting protein-carbohydrate binding sites. DPC is the best descriptor among the traditional descriptors, followed by PSSM.


## 3.3. Protein embedding along with PSSM constitutes the optimal feature descriptor

We had seven traditional feature descriptors and one embedding feature descriptor (ProtT5-XL-U50) at our disposal. As described earlier, to identify the optimal subset of features from this set, we employed incremental feature selection (Algorithm 1). Supplementary Table S1 shows the results of adding different feature groups. Based on the F1-score, we find the combination of ProtT5-XL-U50 embedding and PSSM to be the optimal feature descriptor.


## 3.4. SVM, MLP, ET, and PLS constitute the base layer of StackCBEmbed

Table 4 reports the highest MI obtained in each phase and the corresponding learner combination. When multiple combinations in a phase resulted in very close MI values, all combinations were considered for exploration in the next phase. For example, in phase 3, {SVM, MLP, RF} and {SVM, MLT, ET} produced very close MI values. So we expanded the search in phase 4 based on both these combinations. Based on the overall results, SVM, MLP, ET, and PLS were selected as the base learners. The results from the full search for base layer learners is available in Supplementary file .


## 3.5. SVM is chosen as the Meta layer classifier

As SVM had the highest MI score ( Table 4 ), it was also chosen as the meta layer classifier. Since the meta layer will be trained on the validation set, we further evaluated all the classifiers using 10-fold CV, and the results are shown in Table 5 . SVM has the most balanced performance. Therefore, our choice of SVM for the meta layer has been well-justified.

Figure 1 captures the overall training process of StackCBEmbed. The workflow for predicting the binding sites in a query protein is demonstrated in Figure 2 .


## 3.6. Hyperparameter tuning

The hyperparameters for the base layer classifiers (SVM, MLP, ET, PLS) and the meta layer classifier (SVM) were tuned using GridSearchCV . The parameters we tuned, alongside their final values, are given in Table 6 . (See Supplementary file for the full grid search results).


## 3.7. Stacking ensemble significantly improves prediction performance

The best 5 feature combinations from Supplementary Table S1, with respect to F1-score, are highlighted in Table 7 . In addition, FC-6 is the augmentation of FC-1 with the predictions obtained from the base layer predictors. In our stacking ensemble model, FC-6 is what the SVM learner in the meta layer learns on.

To examine the efficacy of stacking, we checked the performance of six SVM models trained using the validation set. Each model was trained using one of the six feature combinations mentioned in Table 7 . The 10-fold CV performance comparison is shown in Figure 3 . The FC-6 feature combination, which represents stacking, clearly outperforms the other combinations with respect to most of the performance metrics. Additionally, we used the t-distributed stochastic neighbor embedding (t-SNE) [ 58 ] to compare the feature space distribution of the feature combinations of Table 7 on the balanced validation dataset. As can be observed from Figure 4 , the feature space of FC-6 produces a better separation between red and blue spots. This explains the superior predictive ability of the stacking ensemble compared to the other baseline models.


## 3.8. StackCBEmbed outperforms state-of-the-art methods

We have used two independent test sets from the literature, TS49 and TS88, to compare the performance of StackCBEmbed with state-of-the-art (SOTA) methods, such as SPRINT-CBH, Stack-CBPred, PS-G, PS-S, CAPSIF:G, and CAPSIF:V. The SPRINT-CBH and StackCBPred servers were inaccessible, preventing us from reporting some of the metrics. Nevertheless, the trained model of StackCBPred was available in its GitHub repository, enabling us to replicate the results. We have presented both the published values as well as the reproduced values of performance metrics in Tables 8 and 9 . For PS-G, PS-S, CAPSIF:G, and CAPSIF:V, we used the scripts provided in their respective GitHub repositories and produced their results on the TS49 and TS88 independent test sets.

While StackCBEmbed uses only two feature descriptors, PSSM and embedding, PSSM is expensive to compute. Therefore, we created two other models, one using PSSM only, and the other one only using the embedding. We wanted to check how well the model performs in case the PSSM for a query protein cannot be provided. From the results in Tables 8 and 9 , we can see that when only PSSM is used, the model produces poor results in both datasets. However, when it uses embedding only, the results are quite good. In both datasets, it beats SOTA methods in terms of sensitivity and balanced accuracy. When both feature descriptors are combined, the results are further improved.

With SN scores of 73.6% and 66.6% and SP scores of 82.1% and 81.8%, StackCBEmbed achieved the highest BACC scores of 77.6% and 74.2% on TS49 and TS88 sets, respectively. It represents the model’s robust and consistent performance across both positive and negative class samples. This balance is significant in highly imbalanced datasets, and this makes StackCBEmbed a reliable and generalizable predictor. The model delivers AUC scores of 0.832 and 0.788 on TS49 and TS88 sets, respectively, which underlines its strong discriminating capability, even outperforming most predictors in this metric. StackCBEmbed is the most suitable predictor as it shows a balanced and consistent performance across both classes rather than just over-optimizing one class and neglecting the other one.

The Receiver Characteristic curve (ROC) represents the true positive rate (TPR) and false positive rate (FPR) values at several classification thresholds. Figure 5 shows the ROC curves (in independent test sets) for different flavors of StackCBEmbed. It also plots the same for other SOTA methods. From the curves in both datasets, it is clear that PSSM alone cannot give enough predictive capability to StackCBEmbed. However, when the embedding feature is added, its performance improves drastically. When embedding alone is used, the performance is very close to the regular StackCBEmbed. From the plots, we can see that StackCBEmbed beat other SOTA methods except PS-G. However, the performance of PS-G might be an overestimation for the reason described below.

The performance results of CAPSIF:G and CAPSIF:V predictors indicate significant overestimation due to substantial redundancy between the test sets used here and the training sets of these models. With 30% sequence similarity cutoff using BLAST-CLUST, we found that there were 18 redundant protein sequences in the TS49 set and 27 redundant protein sequences in the TS88 set for CAPSIF:G and CAPSIF:V. CAPSIF:V obtained SN scores of 38.5% and 29.0%, BACC scores of 67.9% and 62.6%, AUC scores of 71.5% and 65.1%, and auPR scores of 24.9% and 10.3% in non-redundant TS49 and TS88 sets (after removing the redundant protein sequences), respectively. CAPSIF:G achieved SN scores of 24.4% and 18.7%, BACC scores of 61.4% and 57.9%, AUC scores of 75.4% and 66.2%, and auPR scores of 21.1% and 7.4% in non-redundant TS49 and TS88 sets (removing the redundant protein sequences), respectively. These results highlight how crucial it is to make sure that the training and test sets do not have any redundancy to avoid overestimation. However, the training datasets for PS-G, and PS-S models were not properly provided in the respective GitHub repositories. We could not sort this out by contacting the authors either. As such, we could not measure the redundancy between their training sets, and TS88 and TS49; and the results for these models in Tables 8 and 9 are likely overestimations.

As both the test sets are heavily imbalanced, we also produced performance results after balancing the datasets. We kept all the positive samples and randomly undersampled the negative ones to make the dataset balanced. We did it 20 times and reported our results in mean ± stdev format in Tables 10 and 11 . Not surprisingly, StackCBEmbed outperformed SOTA methods in SN, BACC, F1, and MCC metrics.


## 3.9. StackCBEmbed performed well on TS46 test set

We have tested the different variations of StackCBEmbed on a third independent test set, TS46. The performance results are shown in Tables 12 and 13 . It performed significantly well on this test set as well. This is a further testament to the generalizability of StackCBEmbed in unseen data.


## 4. Discussion and Conclusion

In this study, we have proposed a novel prediction model for protein-carbohydrate binding sites. Named StackCBEmbed, the predictor is a stacking ensemble model trained using 98 protein sequences (≤ 30% pairwise sequence identity), comprising 1014 binding and 25705 non-binding residues. 70% of this data (training set) was used to train the base layer, while the remaining 30% (validation set) was used to train the meta layer. From a variety of traditional sequence-based features, and embedding from recently trained protein language models, the optimal feature vector was prepared using incremental feature selection. In the final model, a combination of PSSM (20 features) and embedding features (1024 features) were used. Therefore each residue was represented as a 1024 + 20 = 1044 dimensional feature vector. As the training data is heavily imbalanced, for improved learning, 10 different subsamples was prepared, each with a different ratio of positive and negative samples. The base layer of the model used SVM, MLP, ET, and PLS learners. As the meta layer, an SVM classifier was trained on the validation set, augmented with the prediction probabilities from the base layer models, and balanced using random undersampling. Results in two independent test sets indicate that StackCBEmbed outperforms SOTA methods in terms of BACC and SN metrics even when only the embedding features are used. The results further improve if PSSM features are added. This is an important observation because PSSM cannot be computed for proteins with not enough homologs in the database. Also, for proteins with enough homologs, the process to compute PSSM is time-consuming. Therefore, a researcher can choose to avoid using PSSM and still get good prediction results using StackCBEmbed.

We also looked at another SOTA method stemming out of the work by Malik et al. [ 6 ]. This publication is quite old and uses a dataset of 40 protein-carbohydrate complexes only. Neither a prediction server nor a standalone downloadable version was available for this method. Therefore we opted to exclude this approach from our benchmarking. More recent methods, such as, LMNG-lypred [ 59 ] and PUStackNGly [ 60 ] were also reviewed. But these models are primarily designed for predicting N-linked glycosylation sites. Our work, on the other hand, focuses on identifying non-specific carbohydrate binding sites, rendering these methods out of scope for comparative analysis.

Prediction models in different problems in bioinformatics are dominated by deep learning methods in the modern era. Accordingly, we started our exploration with several deep learning architectures alongside the traditional ML algorithms. Specifically, we investigated CNN, RNN, LSTM and Transformer models that are well-suited for sequence data. However, these did not yield promising results in this prediction problem (See Supplementary Tables S2 and S3). This might have been due to the small size of the dataset and significant imbalance therein. In fact, many recent studies [ 61 , 62 , 63 , 64 , 65 ] have used traditional machine learning models to surpass the performance of deep learning (DL) based methods. DL models do not perform well under small datasets as they tend to have millions (or even billions) of parameters to learn, resulting in overfitting [ 66 ]. DL models are expensive during inference as well. Therefore, the contribution of traditional ML in the field of bioinformatics is still very pertinent.

In our study, we explored and analyzed sequence-derived structural features. We could not generate predicted PDBs from AlphaFold [ 67 ] due to its high computational demands and resource-intensive nature. For instance, generating a predicted PDB file for the protein sequence ID 1F31A, having a sequence length of 1280 residues, took 3.72 hours with 16 GB of memory and 15 GB of VRAM. Although this limited our ability to incorporate AlphaFold-generated predicted PDBs in our model, we acknowledge the potential of using structural features from predicted PDBs to predict protein-carbohydrate binding sites and leave it as future work.

While StackCBEmbed outperformed SOTA methods in BACC and SN metrics in both the independent test sets, analysis of F1 and auPR scores revealed room for improvement. In particular, the tool needs to improve its precision. These findings highlight the importance of further research and development in this domain. StackCBEmbed achieved a balanced accuracy and sensitivity of 77.6% and 73%, respectively, in the TS49 test set. In the case of TS88, these values were 74.2% and 66.6%, respectively. Thus StackCBEmbed brings in significant improvements in protein-carbohydrate binding site prediction. The model is freely available as an easy to use python script at https://github.com/nafiislam/StackCBEmbed . We hope that research related to protein-carbohydrate binding sites will immensely benefit from the efficacy of this novel, easy-to-use predictor.


## Declarations


## Ethics approval and consent to participate

Not applicable


## Consent for publication

Not applicable


## Availability of data and materials

The StackCBEmbed model, associated data and scripts to reproduce the experimental results are available publicly at https://github.com/nafiislam/StackCBEmbed .


## Competing interests

The authors declare that they have no competing interests


## Funding

MSR is partially supported by Basic Research Grant administered by BUET. MMIN is supported by the RISE Student Research Grant [No. S2024-01-004], administered by RISE, BUET.


## Authors’ contributions

MSR and QFN conceived the research. TNI did preliminary explorations. MSR, QFN, and MMIN set up the experiments. MMIN and QFN conducted rigorous explorations to finalize the prediction model. MMIN validated all the experiments. MSR, QFN, and MMIN analyzed all the results. MMIN improved the code and wrote scripts to reproduce each experiment result. All authors reviewed and approved the manuscript.


## Supplementary Material

This supplementary section provides additional tables.


## Acknowledgements

Not applicable


## Footnotes

First, we have improved the manuscript's organization and readability. The large Table 4, which disrupted the flow of the main text, has been moved to the Supplementary Material section. This allows readers to focus on the key methodological and result-oriented discussions in the main body while still having access to detailed information. Second, we have strengthened the justification for our choice of protein language model embeddings. A more comprehensive comparative analysis of different embeddings has been included in Section 3.1. In addition to the previously evaluated models, we have now incorporated ESM2 into the benchmarking. The results confirm that ProtT5-XL-U50 remains the most effective embedding model for the protein carbohydrate binding site prediction task considered in this study. Third, we have expanded the experimental evaluation by adding additional baseline models. To address concerns regarding residue-level contextual modeling, we implemented and evaluated CNN, RNN, LSTM, and Transformer-based architectures using protein language model embeddings. These results are now reported in the Supplementary Material, and their limitations are discussed in the Discussion section, particularly in relation to dataset size and class imbalance. Fourth, we have significantly extended the comparison with state-of-the-art methods. In addition to SPRINT-CBH and StackCBPred, we now include comparisons with several recently proposed approaches, namely PS-G, PS-S, CAPSIF:G, and CAPSIF:V. Section 3.8 has been updated accordingly to provide a more comprehensive and up-to-date performance evaluation. Fifth, we have clarified the novelty and contribution of this work by emphasizing the methodological innovation of combining stacking ensemble learning with protein language model embeddings for carbohydrate binding site prediction. We also highlight the preparation of a novel independent test dataset to assess generalizability, which will be useful for future benchmarking studies. Finally, we have expanded the Discussion section to address structure-based analysis. While structural information and AlphaFold-generated models can enhance interpretability, we explain why this work focuses on sequence-based prediction and outline structure-based extensions as future work. Overall, these revisions improve the clarity, robustness, and relevance of the manuscript while addressing all major reviewer concerns.