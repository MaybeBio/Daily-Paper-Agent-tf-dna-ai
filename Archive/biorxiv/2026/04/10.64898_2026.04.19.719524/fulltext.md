## Abstract

Drug-target interaction prediction is significant in the hit identification phase of drug discovery, enabling the identification of potential drug candidates for downstream optimization. Traditional computational methods have some drawbacks in their ability to represent 3D structural data for both molecules and target proteins, which is required for the intricate protein-ligand interactions that regulate binding affinity. In this approach, we propose a graph transformer-based model (GTStrDTI) that combines an intragraph attention mechanism with cross-modal attention to enrich the representation of both the drug molecule and target protein. This approach comprehensively models both intramolecular structural features and intermolecular interactions, thereby enhancing binding affinity prediction performance. A thorough evaluation on benchmark datasets such as KIBA, DAVIS, and BindingDB_Kd shows that our approach surpasses the state-of-the-art methods under challenging target cold-start settings. Our analysis found that augmenting graph-based 3D structural protein target (C-alpha contact graphs from PDB with threshold distance of 5Å) and incorporating molecule adjacency information, boosts predictive performance, thus contributing towards narrowing the gap between computational and experimental research.


## 1. INTRODUCTION

High-affinity binding between small molecules or peptides and their receptor proteins constitutes a fundamental selection criterion in the drug discovery process. Binding affinity can be measured experimentally [ 1 ] using techniques such as surface plasmon resonance, isothermal titration calorimetry, and radioligand binding assays. These methods are reliable but come with limitations: they are slow and expensive, especially when screening thousands of compounds at once. Consequently, the development of accurate computational models for binding affinity prediction [ 2 ] has become imperative to accelerate the drug discovery pipeline and reduce resource expenditure and time. Accurately predicting drug-target binding affinity offers critical insight into the pharmacological mechanisms. A systematic study of protein-ligand interaction is quite helpful in the hit identification phase. This is also beneficial in optimizing hit compounds, designing drugs, and identifying off-target effects.

Traditional methods for predicting drug target interactions can be categorized into three major categories: (i) ligand-based, (ii) structure-based and (iii) chemogenomic-based. Ligand-based focuses on quantitative structure-activity relationship (QSAR) models [ 3 ], which are governed by similarity principles, by using known bioactive molecules to infer potential interactions. It has limitations where the information about active ligand and sites is limited. Structure-based methods, such as molecular docking [ 4 ] and free energy perturbation (FEP) [ 5 ], leverage physics-based methods to simulate interactions at the atomic level. Being highly accurate, these methods, however, demand high computational resources and execution time. These methods are highly sensitive to force field and ligand parameters. The above-mentioned methods limit their ability in the virtual screening task. Chemogenomic [ 6 ] approaches represent a paradigm shift by employing machine learning algorithms to model drug-target relationships in a data-driven manner. These methods typically encompass three sequential stages:

data preprocessing and featurization of ligand molecular and protein structural data,

training predictive models using diverse learning algorithms, and

trained models used for affinity prediction on unseen drug-target pairs.

Our (GTStrDTI) method adopts a chemogenomic framework that leverages graph-based representations with a transformer [ 7 ] architecture for binding affinity prediction. This deep learning-based approach offers computational speed several orders of magnitude greater than physics-based simulations. However, its predictive performanceis critically dependent on the quality of molecular featurization and the architectural design of the underlying model. Despite these dependencies, the scalability and speed of machine learning methods position them as highly promising tools for large-scale virtual screening for hit identification.


## 2. RELATED WORK

Predicting how strongly a drug molecule binds to its target protein is one of the hardest problems in computational chemistry. Solving it could dramatically speed up the drug discovery process, from early screening to refining promising drug candidates. Molecular docking and virtual screening workflow employ a scoring function to rank candidate ligand poses within binding sites. Glide [ 8 ] and AutoDock Vina [ 9 ] are being extensively used as scoring functions. Simulation-based approaches such as free energy perturbation have also shown remarkable success in finding good binders. Their sensitivity to ligand parametrization and force field selection, combined with substantial computational demands, constrains their applicability to large compound libraries.

Machine learning has offered a faster and more practical alternative to traditional methods. One early example, RF-Score [ 10 ], took a straightforward approach; it examined how different types of atoms in the protein and drug molecules are arranged near the binding site, then used a random forest model to predict binding strength. Several methods that followed worked along similar lines with comparable results.

ID-Score [ 11 ], for instance, went a step further by pulling together 50 different descriptors that capture various aspects of how a drug interacts with its target, such as electrostatic forces, how well the two molecules fit each other’s shape, and how solvation affects the interaction. These descriptors were then fed into a Support Vector Machine to make predictions. In other studies, researchers combined descriptors from a popular docking tool called AutoDock Vina with random forest models, and managed to enhance accuracy even further. SFCscore (RF) [ 12 ] employed this strategy with the original AutoDock Vina descriptors and also shows similar results.

Deep learning techniques [ 13 ] are widely used in drug-target affinity (DTA) prediction. 1D CNNs are utilized in DeepDTA[ 14 ] to encode molecule SMILES and target protein sequence, followed by feature addition and classification modules. Graph Convolutional Networks (GCNs) are utilized in iEdgeDTA [ 15 ], where a 1D graph of protein sequence with edge attentive graph convolution of drug embeddings. Introduction of 3D convolutional neural networks (3D-CNNs) by KDEEP [ 16 ] outperformed alternative machine learning methods and classical scoring functions across multiple diverse datasets. To model drug-target interaction in a comprehensive manner, graph neural network (GNN) based architectures have been designed. GraphDTA [ 17 ] pioneered the application of GNNs for learning drug structural representations, integrating them with CNN-based protein sequence encoding. GraphPrint [ 18 ] constructs graph representations of protein three-dimensional structures using amino acid residue spatial coordinates, combining these with drug molecular graphs and traditional descriptors in a joint learning framework for DTA prediction. The generative AI model OmegaFold is used in DTA-GTOmega [ 19 ] for 3D structure generation of the target protein, and the graph encodes descriptor information. T-ALPHA [ 20 ] presents a hierarchical transformer-based model that enhances binding affinity prediction through integration of multimodal feature representation. AttentionMGT-DTA [ 21 ] introduces a multimodal attention-based architecture for DTA prediction, representing drugs as molecular graphs and targets as binding pocket graphs, incorporating dual attention mechanisms to facilitate information integration and interaction between protein modalities and drug-target pairs.

GTStrDTI methodology aims to mitigate the limitations of earlier studies by integrating advanced 3D structural information of both the target protein and the ligand through graph-based transformer networks since previous studies have been deficient in capturing the necessary features and architectures to realistically represent these interactions. By applying this approach, more sophisticated representations can be leveraged to achieve more accurate binding affinity predictions.


## 3. MATERIALS AND METHODS


## 3.1 Graph construction

Drug SMILES ( Simplified Molecular Input Line Entry System ) are encoded into graph [ 22 ] features, which is shown in Figure 1 , using RDKit [ 23 ]. Drug is represented by G d ( X d , E d , E xd ), where (n denotes the number of atoms, f are feature dimensions) represent the node features as listed in Table 1 , (b denotes the number of edges) represent the adjacency matrix, and (m denotes the number of edge dimensions)

We encoded structural features into a graph representation by utilizing the C α [ 24 ] centroid atomic centroids of each residue. Pairwise threshold distances of 5Å is applied to detect the edges. The protein graph is represented as G t ( X t , E t ), where (n denotes the number of residues, f are feature dimensions) represent the node features, as illustrated in Table 2 , (b denotes the number of edges) represent the adjacency matrix.


## 3.2 Model

Figure 2 illustrates an advanced dual-stream transformer architecture that processes both drug and protein information as graph structures, representing a significant advancement in computational drug discovery. Our architecture processes drug and protein representations via parallel transformer pathways that share block configurations. It ensures symmetric feature extraction from both molecular entities prior to cross-modal integration via an attention mechanism.

The core innovation in our approach is the use of a dual transformer block, which takes a normalized graph representation as an input. Each transformer block has 4 essential modules arranged in a distinctive order:

This specialized graph transformer layer extends traditional transformer attention mechanisms to graph structures. It computes attention weights between connected nodes, allowing the model to focus on chemically or structurally relevant regions. For drugs, this captures important pharmacophores [ 25 ] and reactive groups. For proteins, it identifies key binding residues and structural motifs.

This component performs self-attention within each graph, enabling long-range dependencies and global context understanding. In molecular graphs, this allows atoms to attend to distant but chemically relevant atoms. In protein graphs, this captures allosteric effects and long-range structural constraints that influence binding.

Self-Attention Graph pooling provides a learnable method for aggregating node-level information into graph-level representations. Unlike traditional pooling methods that may lose important structural information, SAG [ 26 ] pooling maintains attention-weighted importance scores, preserving critical molecular or protein features while creating fixed-size representations suitable for downstream processing.

The combination of graph-specific normalization with ELU [ 27 ] ensures stable training dynamics while maintaining the expressiveness necessary for complex molecular and protein feature learning. ELU activation helps mitigate vanishing gradients common in deep graph networks.

The node features of both the drug and target graphs are subjected to Layer Normalization [ 28 ], which enhances training stability and accelerates the convergence of the neural network.

Now, normalized graphs , and are passed to the graph transformer module, which applies the attention mechanism.

In this formulation, and represent the feature vectors of node i at the p th layer within the protein and drug graphs, respectively. The parameter x specifies the dimensionality allocated to each attention head in the hidden representation, while the matrices W correspond to trainable weights. Additionally, captures the edge features between nodes i and j at layer p in the drug graph G d , and α ij is the attention weight showing how strongly node i attends to node j . After two layers of message aggregation, the updated node representations are obtained and denoted as H t ,( p ) ∈ R n × v and H d ,( p ) ∈ R a × v , where m denotes the p th Graph Encoder module. The dimension v corresponds to the product of the hidden layer size and the x number of attention heads. The outputs generated by each successive pair of Graph Transformer layers are subjected to the ELU activation function. Subsequently, SAG pooling and global pooling operations are employed to aggregate the node-level latent representations, yielding a compact one-dimensional global feature vector.

Here, the number of target residues is denoted by n, while the number of atoms in the drug molecule is denoted by a.

The architecture’s most sophisticated component is the Co-Attention [ 29 ] Layer, which facilitates interaction between processed drug and protein representations. This cross-modal attention mechanism allows the model to identify complementary features between drug and protein graphs, essentially learning which molecular features are most relevant for binding to specific protein regions. The co-attention mechanism computes attention weights between drug nodes and protein nodes, creating a rich interaction matrix that captures potential binding modes, steric complementarity, and electrostatic interactions. This approach goes beyond simple feature concatenation by learning dynamic, context-dependent interactions between molecular entities. After M serial Graph Encoder modules G t and G d are stacked to obtain R t ∈ R M × V and R d ∈ R M × V , which are fed into the co-attention module to obtain pairwise interaction importance.

Here, and are the normalized forms of R t and R d . B T , W k , and W q are learnable matrices.

Following the co-attention integration, the architecture adopts a Rescale Tensor Factorization [ 30 ] module, which is designed to efficiently process the high-dimensional interaction tensors generated by the attention mechanism. This factorization approach reduces computational complexity while preserving essential interaction information necessary for accurate binding affinity prediction. The final representation ( R td ) of protein-drug interaction is passed to fully connected layers.

The final Output Layer transforms the factorized representations into binding predictions, typically regression values for binding affinity ( K i ).


## 4. EXPERIMENTS AND RESULTS


## 4.1 Dataset

The datasets in this work are curated for AI-driven virtual screening and binding affinity prediction tasks, including the KIBA dataset [ 31 ], Davis dataset [ 32 ], and BindingDB_ K d [ 33 ]. Each dataset integrates chemical and biological information necessary for ligand-based, structure-based, and hybrid QSAR (Quantitative Structure-Activity Relationship) modelling. We explored a range of open-source and proprietary datasets to understand their structure, quality, and suitability for predictive modeling, particularly for estimating binding affinities. This exploration is foundational to building robust QSAR models and screening millions of compounds in silico to discover potential hits for a given biological target. We have taken standard open-source datasets made available through institutional collaborations and licensed sources for training and validation purposes. The availability of diverse chemical and biological information in datasets made them substantial for our approach. The key fields included in the datasets are summarized below:

It is a textual notation (encoding) used to represent chemical molecules in a linear string. The string “CC(=O)OCC” is a SMILES notation of ethyl acetate. In cheminformatics, it is predominantly used to represent molecules, compute descriptors, and encode input to various networks.

A unique identifier assigned to each molecule in the dataset, often derived from internal database IDs or external sources (e.g., BindingDB ID, PubChem CID). Helps in tracking, referencing, or mapping molecular data across different sources. E.g. “BDB123456” or “CID2244”

A unique 4-character alphanumeric code representing the 3D structure of a protein or protein-ligand complex in the Protein Data Bank. Enables access to detailed 3D structural information for docking and structure-based QSAR models. E.g., “1A2B” or “6LU7” (COVID-19 main protease). Affinity Value (Binding Affinity)

Quantitative measurement [ 34 ] of how strongly a ligand binds to its target protein, usually expressed in IC 50 , K i , or K d units (typically in nanomolar, nM) used to rank compounds during virtual screening. It is the target variable for the model. Lower values indicate stronger affinity.

Remove Incomplete or Invalid Entries: SMILES, Protein Sequence, and Affinity Value. Standardize and validate SMILES, filter out invalid SMILES strings using RDKit (E.g.: molecules that cannot be parsed). Remove duplicates based on canonical SMILES.

Remove outlier: Remove outlier data based on affinity values and protein sequence length.

Standardize Affinity values: Convert Affinity Values to a Common Scale. Ensure all affinity values are in the same unit (E.g.: nM) and convert them into log pK d . Validate PDB IDs.

Target structure verification: Ensured PDB IDs are correctly formatted (4-character codes). We also removed any structures that were invalid or missing.

Distribution plots of atom length, target sequence length, and datasets across all settings are provided in the Supplementary Information (SI) which is shown in Figures S1 – S3 , while the unique protein targets and drugs are summarized in Table 3 . The Distribution of ligand atom length, target protein sequence length, and transformed activity values (p K d ) indicates that the dataset includes small, medium, and large ligands interacting with protein targets of varying sequence lengths. The detailed Distribution is presented in Table 4 .


## 4.2 Experimental Settings

The proportions of drug types in the training, validation, and test sets were set to 70%, 10%, and 20%, respectively, consistent with previously published studies to enable fair comparison. The detailed Distribution of the split datasets is provided in Table S1 of the Supplementary Material. Table 5 presents the experimental configuration used for model training.

In traditional evaluation methods, overlapping between training and testing data can lead to data leakage, resulting in models that perform exceptionally well during testing but poorly in real-world applications. The cold-start [ 35 ] setting, by strictly separating training and testing data, mitigates the risk of data leakage and overfitting. Furthermore, this setting can simulate real-world scenarios where new drugs or targets are encountered. By excluding these new drugs or targets during model training, we can assess the model’s generalization capability on unseen data, ensuring its effectiveness beyond just the training. Testing statistics are shown in Supplementary Information (SI) Table S1 .

The training, validation, and test sets have only overlapped targets, but no overlapping drugs. For example, each test’s drug is new to the training and validation sets. The proportions of drug types in training, validation, and test sets are set to 70%, 10%, and 20%, respectively.

The training, validation, and test sets have only overlapped drugs, but no overlapping targets. For example, each test’s target is new to the training and validation sets. The proportions of target types in training, validation, and test sets are set to 70%, 10%, and 20%, respectively.

The training, validation, and test sets have no overlap for both drugs and targets. For example, each test’s drug and target are both new to the training and validation sets. The proportions of drug and target types in training, test, and validation sets are set to 70%, 20%, and 10%, respectively.


## 4.3 Evaluation Metrics

We assessed the performance of the DTA prediction models using commonly used regression metrics, including Mean Squared Error (MSE), Root Mean Square Error (RMSE), Spearman rank correlation coefficient (ρ), Pearson correlation coefficient (r), and the concordance index [ 36 ] (CI). Lower RMSE and MSE values indicate smaller deviations between predicted and observed DTA values, whereas higher values for the remaining metrics indicate stronger agreement between model predictions and ground-truth DTA/DTI outcomes.

Root Mean Squared Error (RMSE) evaluates the average magnitude of prediction errors, giving higher importance to larger errors, and is expressed in the same units as the target variable.

Where n= number of observations, y i = actual value, ŷ i = predicted value

MSE quantifies prediction error as the mean of the squared deviation between actual and predicted values. It is the foundation of RMSE.

Where n= number of observations, y i = actual value, ŷ i = predicted value

Provides a quantitative measure of the linear association between two continuous variables. It is the parametric test assuming normal distributions. Values range from −1 to +1. r = 1 represents perfect positive linear relationship, r = −1 perfect negative linear relationship and r = 0 shows no linear relationship.

Where n = number of observations, x i , y i = individual data points, means of x and y

It represents monotonic correlation based on the ranks of data values rather than the raw values. It measures a monotonic relationship. Values range from −1 to +1. p = 1 represents perfect positive linear relationship, p = −1 perfect negative linear relationship and p = 0 shows no linear relationship. It is useful for non-normal distributions when we want to assess a monotonic rather than a linear relationship.

Where n = number of observations, d i = difference between ranks of paired observations

Concordance Index (CI) measures how well a predictive model preserves the correct ranking of outcomes. It calculates the proportion of all valid sample pairs for which the predicted values are ordered correctly, giving full credit for correct order (1), half credit for ties (0.5), and no credit for incorrect order (0). CI ranges from 0 to 1, with higher values indicating better ranking performance.


## 4.4 Results

We compare the proposed method with existing mainstream DTA prediction models across three benchmarks: drug cold-start, target cold-start, and drug-target cold-start settings. Scatter plots for all settings are in Supplementary Information (SI) Figures S4 - S6 . We have achieved a significant improvement over our previous counterpart in target cold start testing, highlighted in Table 6 . The target cold-start setting evaluates a model’s ability to predict interactions for previously unseen protein targets. Most therapeutic proteins have limited or no experimental interaction data. A model that performs well only on targets it has already seen is not useful for novel target exploration. It also reduces overestimation of performance. Warm-start or random splits can inflate accuracy because the model indirectly sees similar versions of the same protein in training.


## 4.5 Case Studies

We validate the practical readiness of approach through extensive case studies spanning diseases across four major therapeutic categories: respiratory, cardiovascular, infectious, and neurological disorders. These diseases are chosen so that the holistic efficacy of the model can be tested across different types of protein targets and verify the generalizability of the model. Results are shown in Table 7 , which involves the comparison of predicted binding affinity of inhibitors for the unseen crystal structure of HIV-1 Protease (PDB ID: 1JKH, 6DH3, 3S56, 2AQU, 8FN7, 4MBS, 2ZD1, 1MUI, 2B60, 6PUW), where average standard deviation between experimental and predicted binding affinity values is found to be 1.29 Kcal/mol. Comparison results that can be referenced from table were also performed on crystal structures of Human VMAT2 associated with Huntington’s disease (PDB IDs: 8T6A, 8JTA, 3WS9, 3JSI, 5W5V, 4PH9) target protein with inhibitors, shows standard deviation in binding affinity values against experimental results is 0.97 Kcal/mol. We have compared inhibitor binding affinity for crystal structures of Non-Small Cell Lung Cancer (NSCLC) (PDB IDs: 7JXM, 2XP2, 4XV2, 7JUR) correspond to experimental data, results show a standard deviation of 0.87 kcal/mol. Unseen crystal structure of a congenital heart disease-associated protein (PDB IDs: 7DDH, 2H42, 2C6N) target with its some inhibitor was selected for comparison and results show a standard deviation of 0.73 kcal/mol.

As emphasized in the Table 7 , the 3D crystal structure of the SARS coronavirus main protease (PDB IDs: 7BV2, 7EO8, 9LUF) target taken with inhibitors to infer the prediction results and the deviation from experimental results, corresponds to a standard deviation of 0.94 kcal/mol, showed strong alignment and correlation, indicating the robustness of the proposed approach for varied molecule target pairs.


## 5. CONCLUSION

We presented a framework for predicting drug target binding affinity that integrates 3D structural, physicochemical, electronic, and bond properties of both drug molecules and protein targets. It can operate without the need for highly computational pretrained models for feature extraction or prediction. This approach is flexible in processing artificially generated and experimentally determined protein targets. We have demonstrated our model’s capability to enhance drug candidate selection during virtual screening, thereby accelerating the drug discovery pipeline by reducing both time and cost requirements. Through the integration of 3D protein structural information, our model successfully addresses the challenging target cold-start scenario across the DAVIS, KIBA, and BDB datasets, outperforming existing methods that depend exclusively on conventional protein representations or pretrained models. Given the recent advances in accurate computational protein structure prediction and the expanding availability of 3D protein structure databases, incorporating structural information represents a promising new paradigm for drug-target affinity prediction and related applications in drug discovery and multimodal learning. This research improves our understanding of drug target interaction. It provides practical benefits by helping make the drug development process more efficient and cost-effective. These evaluation studies demonstratethe model’s utility in computational drug discovery.

However, the approach has some limitations. Notably, our work does not include an ablation study, making it difficult to evaluate each component’s contribution. Additionally, limited explainability of deep learning is one of the hindrances in trusted adoption of the technique. With further improvements in features representation by considering secondary structure, torsion Angle and dynamics features, it could become even more accurate in its predictions. On the architecture side, adapting to optimize graph pooling, sparse attention and tweaking the positional encoding can further enable researchers to identify promising drug candidates with improved computational efficiency.


## FUNDING

This research received no specific grant from any funding agency in the public, commercial, or not-for-profit sectors.


## DECLARATIONS

The authors declare that they have no competing interests.


## Supplementary Information


## ACKNOWLEDGEMENTS

The authors would like to express their sincere gratitude to all individuals who contributed their time, expertise, and support during the course of this research.