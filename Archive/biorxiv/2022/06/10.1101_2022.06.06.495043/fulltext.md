## Abstract

Illuminating interactions between proteins and small drug molecules is a longstanding challenge in the field of drug discovery. Despite the importance of understanding these interactions, most previous works are limited by hand-designed scoring functions and insufficient conformation sampling. The recently-proposed graph neural network-based methods provides alternatives to predict protein-ligand complex conformation in a one-shot manner. However, these methods neglect the geometric constraints of the complex structure and weaken the role of local functional regions. As a result, they might produce unreasonable conformations for challenging targets and generalize poorly to novel proteins. In this paper, we propose Trigonometry-Aware Neural networKs for binding structure prediction, TANKBind, that builds trigonometry constraint as a vigorous inductive bias into the model and explicitly attends to all possible binding sites for each protein by segmenting the whole protein into functional blocks. We construct novel contrastive losses with local region negative sampling to jointly optimize the binding interaction and affinity. Extensive experiments show substantial performance gains in comparison to state-of-the-art physics-based and deep learning-based methods on commonly-used benchmark datasets for both binding structure and affinity predictions with variant settings.


## 1 Introduction

Proteins are the workhorses of human bodies. They have a wide range of interaction partners, small molecules, other proteins, and DNA/RNA, for example. In this paper, we focus on drug-like small molecules as the interaction partners for proteins. The words ligands, drugs, small molecules and compounds are used interchangeably throughout the paper. Small molecules activate or inhibit activities of target proteins through mostly non-covalent interactions. In 2021, FDA approved 60 new drugs, among which 36 were small molecules Kinch et al. [2022] . Understanding the mechanism-of-actions and off-target effects of drug molecules typically requires analyzing the structures of the related protein-ligand complexes Boopathi et al. [2021] , Xie et al. [2011] , but solving the complex structure experimentally is a an extremely challenging task. Despite tremendous effort spent on this topic over the last 50 years, only about 19,000 protein-ligand complex structures have been solved experimentally using X-ray, Cryo-EM or NMR Liu et al. [2015] . On the other hand, the estimated chemical space of drug is 10 60 and estimated number of unique proteins in human body is at least 20, 000, making the number of possible protein-ligand complex far exceeding the number of experimentally solved structures Reymond et al. [2010] , Ponomarenko et al. [2016] .

On the computational side, molecular docking is a commonly-used method for predicting the protein-ligand complex structures the corresponding binding affinities Trott and Olson [2010] , Friesner et al. [2004] , Ackloo et al. [2022] , Gentile et al. [2022] . Generally, the docking process involves three main stages: (1) locating favorable binding sites given a protein target; (2) sampling the ligand conformation as well as its position and orientation within these sites; (3) scoring and ranking the conformations of the complex using physics-inspired empirical energy functions to refine the structures and assess protein-ligand binding affinity. Due to its good interpretability and usability, docking has been integrated in drug development process for a long time and a number of successful cases have been reported Anderson [2003] . However, most open-source docking packages use atomlevel pairwise scoring functions, limiting the capacity to model the many-body effects. Moreover, they need to sample a large range of possible ligand poses and protein side-chain conformations, which leads to relatively high computational cost Trott and Olson [2010] , Jain [2006] .

To overcome these challenges, we propose a two-stage deep learning framework to neuralize the molecular docking process and predict the binding structures with better accuracy and lower computational cost. In the first stage, we segment the whole protein into functional blocks and predict their interactions with the ligand, creating an protein-ligand interaction energy landscape using a novel trigonometry-aware architecture. The trigonometry module has enough model capacity to capture many-body effects. In the second stage, we prioritize the crystallized binding structures by constrastively ensuring a weaker binding affinity for non-native interactions. In particular, our model improves the drug-protein binding structure predictions with a combination of (i) a novel trigonometry-aware architecture that jointly infuses trigonometry constraints and excluded-volume effects as inductive biases, (ii) a new divide-and-conquer strategy that constructs the protein-ligand local functional binding pairs in a contrastive manner. By doing so, we create a funnel-shape energy landscape for the inter-molecular interaction, removing the need of extensive sampling Jumper et al. [2021] , Jain [2006] , Chen et al. [2020a] , Onuchic et al. [1997] .

Our novel method is well-motivated by leveraging prior knowledge from physics and biology. Physically, the inter-molecular trigonometry module, inspired by the intra-molecular Evoformer module used in AlphaFold2 Jumper et al. [2021] , ensures that our energy landscape disfavors configurations of protein-ligand complexes that are prohibited by laws of nature, for instance, no two atoms could overlap and the distances between atoms have to satisfy triangle inequality theorem in euclidean geometry. More details on these constraints is shown in section 3.3 . Biologically, the functional regions of proteins tend to be more conserved and closely associated with binding De Juan et al. [2013] , Glaser et al. [2003] , allowing the model to learn critical information and generalize better to unseen proteins.

We evaluate our algorithm against several state-of-the-art deep learning and physics-based docking methods on task of binding structure prediction under multiple settings. Compared with baselines, our model increase the fraction of predictions with ligand root-mean-square deviation (RMSD) less than 5Å by 16% in re-docking setting, 22% in self-docking setting, and 42% in the more difficult new-protein setting. Our model is also capable of predicting binding affinities, achieving better correlations with experimentally-measured values than sequence-based, structure-based and even complex-based methods. We also show that TankBind has the potential to discover novel mechanism-of-actions of drug molecules by identifying unseen protein binding sites.


## 2 Related Work


## Geometric Deep Learning for drug discovery

There has been a surge of interest in integrating geometric priors for representation learning in the domain of drug discovery Jumper et al. [2021] , Baek et al. [2021] , Jing et al. [2021] , Ganea et al. [2021] , Jin et al. [2021] , Ingraham et al. [2019] , AlQuraishi [2019] , Schütt et al. [2017] , Somnath et al. [2021] . Recent researches have incorporated geometric information and symmetry properties of the input signals to improve the spatial perception of the learned representations. These works have been shown great potential in various applications like protein structure modeling Jumper et al. [2021] , Baek et al. [2021] , Jing et al. [2021] , Ganea et al. [2021] , molecular low-energy generation prediction Shi et al. [2021] , Xu et al. [2022] , Méndez-Lucio et al. [2021] , property/function prediction Schütt et al. [2017] , Somnath et al. [2021] and molecule design Jin et al. [2021] , Ingraham et al. [2019] . Among which, AlphaFold 2 achieved outstanding performance in protein structure prediction Jumper et al. [2021] , representing the state-of-the-art geometry-aware method. Our work is inspired from this groundbreaking work, adapting it from the intra-molecular structure prediction to the field of predicting the inter-molecular binding structure and binding affinity.


## Drug-protein Interaction (DPI) prediction

The goal of DPI prediction is to illustrate the binding structure and binding affinity between protein and ligand. Apart from docking-based approaches Trott and Olson [2010] , Friesner et al. [2004] , prior machine learning-based works either use complex-free models to predict the binding affinity directly from protein-ligand pairs Wang and Dokholyan [2021] , Li et al. [2020] , Tsubaki et al. [2019] , Gao et al. [2018] , Karimi et al. [2019] , Zheng et al. [2020] or make predictions through complex structure that has been previously obtained by experimental or docking approaches Jiménez et al. [2018] , Lim et al. [2019] , Morrone et al. [2020] . The former ones are less interpretable while the latter requires data involved in vast experimental costs and labour. More recently, EquiBind Stärk et al. [2022] takes a new approach by directly predicting the key points on both the protein and the compound, and aligning their key points through the ingeniously designed optimal transport loss. However, this method may generate compound structures clashing with the protein structures and currently lacks the capability to predict the binding affinity, limiting its use in drug discovery. In contrast, our approach has a trigonometry module imposing geometry constraints and a state-of-the-art binding affinity prediction capability.


## 3 TankBind Model


## 3.1 Overview of TankBind model

The general protocol of our model is shown in figure 1 . The encoding of protein and compound is described in section 3.2 . The rationale and implementation of trigonometry module is detailed in section 3.3 . The design of loss functions for training is described in section 3.4 . The generation of atom coordinates from predicted inter-molecular distance map is introduced in section 3.5 .


## 3.2 Structural encoders of protein and drug

Our model input is the separate structures of a protein and a drug compound, both encoded as graphs. Indices i, k always operate on the residue dimension, j, k′ always on the compound dimension. n is the number of protein nodes and m is the number of compound nodes.

The protein is represented as a proximity 3D graph following Jing et al. [2020] . We denote the protein graph as , where each node corresponds to an amino acid, and has feature with both scalar and vector features. Each node also has a position equal to the Cartesian coordinate of C α i . An edge exists if is among the 30 nearest neighbors of . Each edge also encodes both the scalar and the vector features. We then apply the geometric vector perceptrons (GVP) Jing et al. [2020 , 2021] to embed the protein and arrive at feature after graph propagation, where n is the number of nodes and s is the embedding size.

To implicitly model side-chain flexibility, we choose a residue-level representation ignoring the finer details of protein structure, separating our method from other methods that use all-atoms or surface vertexes representation Jiang et al. [2021] , Gainza et al. [2020] . Also, as shown by Jumper et al. [2021 , 2018] , residue-level embedding is enough to infer the side-chain conformation.

Motivated by protein co-evolution De Juan et al. [2013] and divide-and-conquer theory, the protein graph, , is further divided into subgraphs . Each subgraph includes all the and inside the functional block. The subgraph is denoted as , where x o is the center of the functional block predicted by a widely-used ligand-agnostic method, P2rank (published in 2018) Krivák and Hoksza [2018] . Justification for the size of radius and use of P2rank is described in appendix 11.

The drug compound is represented as a graph using TorchDrug toolkit Zhu et al. [2022] . The compound graph is denoted as where each node corresponds to a heavy atom (non-hydrogen atom), and has feature and each edge , has feature . We use Graph Isomorphism Network (GIN) Xu et al. [2018] to embed the compound and arrive at feature after graph propagation, where m is the number of heavy atoms and s is the embedding size.


## 3.3 Details of trigonometry module

The compound feature, h c , and the protein block feature, h p , are used to form the initial interaction embedding . The interaction embedding will be further updated with pair distance map of protein nodes, and pair distance map of compound nodes, .

The rationale for including both the pair distance map of the protein nodes and the pair distance map of the compound nodes in updating the protein-compound interaction embedding is explained with two simplified examples. As shown in the upper part of figure 2 , if a protein node A is in close proximity with compound node B, then compound node C will not be in contact with node A due to the large distance constraint between node B and C. Distance constraint between compound nodes B and D could also force a node D to be in close contact with protein node A.

To build this observation of trigonometry constraints into our model, we design the following module to update the interaction embedding, in layer ℓ , ∀( i, j ): where is the linear embedding of encoded pair distance between protein nodes. , n is the number of nodes in protein block, s is the embedding size. is the linear embedding of encoded pair distance between compound nodes. , m is the number of compound nodes. and are the same gated linear transformations of but with non-shared parameters, is a layernorm function followed by a linear transformation.

Another type of physical constraint need to be take into consideration is the excluded-volume (Van Der Waals) and saturation effect. As shown in the upper figure 2 , if protein node A forms a strong interaction, hydrogen bonding for example, with compound node B, then node D is unlikely to form the same type of interaction with node A because node A has limited number of hydrogen donors or acceptors. To account for these effects, we designed a self-attention module to modulate the interaction between a protein node and all compound nodes by taking the whole interaction between this protein node and all compound nodes into consideration. , where are linear transformation of is number of attention heads. Function g h is the standard g with reshaping the embedding into heads at the end, Φ is a linear transformation.

Lastly, a non-linear transition module is added to transit the interaction embedding to the next layer through multilayer perceptron, . The whole trigonometry module is composed of three consecutive parts, the trigonometry update, the self-attention modulation, and the non-linear transition module. Layernorm is applied on every input and a 25% dropout is applied to the trigonometry update and self-attention modulation during training. The final outputs, drug-protein binding affinity, , and inter-molecular distance map, , are predicted directly based on the last layer embedding , where L is the number of module stacks.


## 3.4 Design of binding interaction and affinity loss functions

Many previous works model the interaction between compound and protein by only preserving the interaction region, residues that far away are ignored Townshend et al. [2020] , Méndez-Lucio et al. [2021] . On the positive side, the computation and memory demand for characterize the interaction between protein and the drug compound is greatly reduced by focusing on regional interaction. But the fact of not binding to alternative binding sites is also a valuable information. By the nature of crystallization, if a protein-compound complex could be successfully crystallized, other possible binding sites on this protein definitely bind less strongly than the native binding site to the compound, therefore, those other binding sites could be used as high-valued decoys. Based on this observation, we designed a max-margin constrastive affinity loss, equation 4 , following the idea of Hadsell et al. [2006] . Such that the compound’s predicted affinity, , to the decoys is less than the experimentally measured affinity, a , by a margin value, ϵ . where is the predicted affinity to block ζ , and indicator function when block ζ encloses the native ligand, and otherwise. We, therefore, take full use of information stored in the whole protein instead of only the native binding region. We also include a mean squared erorr (MSE) loss for native interaction distance map, . The overall training objective of TankBind is: .


## 3.5 Generation of drug coordinates based on predicted inter-molecular distance map

The Cartesian coordinates, , of the heavy atoms of a drug compound could be deduced analytically based on the predicted inter-molecular distance matrix, , the coordinates of protein nodes, , and the pair distance matrix of compound nodes, , Masters et al. [2022] , Hoffmann and Noé [2019] . But since predicted distance matrix contains noise, we take a numerical approach Masters et al. [2022] , Zsoldos et al. [2007] . By minimizing the total loss, , which consists of two parts, the interaction loss and the compound configuration loss, we could derive the coordinates of the docked drug coordinates, . where n is the number of protein nodes, and m is number of compound nodes, and are the Cartesian coordinates of protein nodes. All inter-molecular distances are clamped to have an upper bound of 10Å to focus on the direct interaction. In self-docking setting, when the compound configuration is unknown, we add a local atomic structures (LAS) mask to the configuration loss to allow for compound flexibility while enforcing basic geometric constraint, where when compound atom j and k′ are connected by connected by a bond, or 2-hop away, or in the same ring structure, and otherwise Stärk et al. [2022] , Trott and Olson [2010] . For every test protein-ligand pair, TankBind predicts the binding affinity of the ligand to all segmented functional blocks and chooses the one with strongest affinity to generate the binding structures.


## 4 Evaluation


## 4.1 Protein-ligand binding structure prediction

We used publicly available PDBbind v2020 dataset Liu et al. [2015] which has the structures of 19443 protein-ligand complexes along with their experimentally measured binding affinity. PDBbind is a database curated based on the Protein Data Bank (PDB) Burley et al. [2021] . We followed the same time split as defined in EquiBind paper Stärk et al. [2022] in which the training and validation data are the protein-ligand complex structures deposited before 2019 and the test set is the structures deposited after 2019. After removing a few structures that unable to process using RDKit from the training set, we had 17787 structures for training, 968 for validation and 363 for testing Landrum et al. [2013] . We also reduced the possibility of encountering equally valid binding sites by removing chains that have no atom within 10Å from any atom of the ligand following the protocol described in Stärk et al. [2022] .

We compared TankBind with the most widely-used docking method AutoDock VinaTrott and Olson [2010] and the recent proposed geometry-based DL method EquiBind Stärk et al. [2022] . We also included four popular docking methods QVina-W, GINA McNutt et al. [2021] , SMINA Koes et al. [2013] and GLIDE Friesner et al. [2004] as listed in Stärk et al. [2022] .

We follow prior work Stärk et al. [2022] and use ligand root-mean-square deviation (RMSD) of atomic positions and centroid distance to compare predicted binding structures with ground-truths. The Ligand RMSD calculates the normalized Frobenius norm of the two corresponding matrices of ligand coordinates. The centroid distance is defined as the the distance between the averaged 3D coordinates of the predicted and ground-truth bound ligand atoms, indicating the model capability of identifying correct binding region. Hydrogens are not involved in the calculation.

We start with a real-world blind self-docking experiment, in which the ligand conformation is not fixed, and the result of re-docking experiment, in which the native ligand conformation is given, is reported in Appendix A. As shown in the table 1 , TankBind achieves state-of-the-art performance, outperforming geometry DL-based model EquiBind. This advantage is particularly evident in the top 25% and top 50% ligand RMSD, which allows our method to predict 22% more qualified (below Threshold 5Å) binding poses than EquiBind. This results are also consistent in the metrics of centroid distance, demonstrating that our method also has a clear advantage in the identification of binding region. Even though GLIDE (commercial) and Autodock Vina are established docking software with more than a decade of continuous development, our model remarkably frequently outperforms them. At the same time, we are orders of magnitude faster than them, and on the same level as EquiBind (Appendix 7). In addition, we explore the possible of TankBind-R, where we randomly segment the protein, TankBind-P, where we only doing the summation over protein nodes in equation 1 , and TankBind-C, where we only sum over compound nodes. The performance reduction on the these variants supports our view that trigonometry message passing between proteins and ligand and segmentation choice are critical to the prediction of binding structures.

We next focus on the new protein setting, in which the tested proteins have not been observed in the training set. Table 2 shows that Tankbind leads to larger improvements over EquiBind and docking methods with regard to ligand-RMSD and centriod distance.This is in line with our expectation that TankBind has better generalization ability due to the physical-inspired trigonometry module and explicit consideration of conservative functional blocks. In this setting, as shown in Figure 3 and table 2 , for fractions smaller than 2Å, 5Å and 15Å, the performance between EquiBind and other docking method are comparable, while TankBind is always better by a large margin, further confirming the effectiveness of our method and indicating that the proposed strategy has practical values for the virtual screening of new proteins.


## 4.2 Protein-ligand binding affinity prediction

TankBind is also capable of predicting protein-ligand binding affinity because of the constrastive affinity loss function. Since we segmented the whole protein into protein blocks, the predicted binding affinity of ligand to the whole protein is equal to the binding affinity to the one protein block that predicted to bind strongest with the ligand. To demonstrate the ability, we compared TankBind with the state-of-the-art binding affinity prediction models.

We split the dataset into training, test and validation splits based on the same time split described earlier. The experimentally measured affinity data in PDBbind dataset has three different names, depending on the exact experiment setups, 50% inhibiting concentration (IC50), inhibition constant ( i ), and dissociation constant ( K D ), all converted to the unit of molar concentration. Similar to previous methods Somnath et al. [2021] , Townshend et al. [2020] , we predict negative log-transformed binding affinity.

We compare TankBind against two state-of-the-art sequence-based methods, TransformerCPI Chen et al. [2020b] and MONN Li et al. [2020] , two complex-based methods, IGN Jiang et al. [2021] and PIGNet Moon et al. [2022] both requiring prior knowledge of the inter-molecular structure to predict affinity, and two structure-based methods, HOLOPTOT Somnath et al. [2021] and STAMPDPI Wang et al. [2022] . For evaluating various methods, we use four metrics – root mean squared error (RMSE), Pearson correlation coefficient, Spearman correlation coefficient and mean absolute error (MAE). We also include the mean and standard deviation across 3 experimental runs in appendix 8.

As shown in Table 3 , our model obtains the best performance in PDBbind test set, consistently outperforms SOTA binding affinity prediction methods. Note that even without the prior interaction information, TankBind also achieves better result than complex-based methods (PIGNET and IGN), proving that the predicted binding structural information provided considerable gain to the affinity prediction task.


## 4.3 Ablation study

We conducted ablation studies to investigate factors that influence the performance of proposed TankBind framework. As shown in Table 4 , the original version of TankBind with the trigonometry message passing between protein and ligand shows the best performance among all architectures. Replacing the P2rank with a randomly split of blocks performed the worst, which verifies our hypothesis that functional block segmentation can improve generalization. Simple architecture substitutions for protein (TAPE) Rao et al. [2019] and molecular representation (GAT) Veličković et al. [2017] decrease slightly the model performance. Replacing the intra-trigonometry module with the uni-modal variants (TankBind-P and TankBind-C) both caused noticeable decreases in performances.


## 4.4 Case studies

As a representative case, in PDB 6K1S, a seen protein binds to a new drug compound at a site that has not been observed before. This protein has three co-crystallized complex structures in the training set, PDB 4X60, 4X61, 4X63. As shown in the left of figure 4 , our method, shown in red, aligns well with the true ligand, shown in green, despite our method has never seen any compound locates at this site before. While other two methods, EquiBind in cyan, Vina in orange identify an incorrect site for this compound. Packages Kalign, Biopython, and Smith-Waterman library are used to systematically analyze the results Lassmann [2020] , Cock et al. [2009] , Li et al. [2020] , Zhao et al. [2013] (see Appendix 12).

We picked two representative examples with both compound and protein are unseen, one, PDB 6QRG, in the right of figure 4 and another, PDB 6KQI, in appendix 6. Both PDB 6QRG and PDB 6KQI have max protein similarity below 0.8 (6QRG 0.78, 6KQI 0.57), and max compound similarity below 0.4 (6QRG 0.36, 6KQI 0.27).


## 5 Conclusion

In this work, we propose a novel binding structure and affinity prediction model, TankBind, that builds trigonometry constraints into the model and explicitly attends to all possible binding sites by segmenting the whole protein into functional blocks. We observe significant improvements on task of binding structure prediction over existing deep learning methods: a 22% increase in the fraction of prediction below 5Å in ligand RMSD, and a 42% increase when the proteins have not been observed in the training set. Moreover, we demonstrate that the model is able to predict affinity and outperform SOTA methods on PDBbind. This work opens a new direction for modelling the inter-molecular interaction between protein and drug molecule. Numerous directions for further exploration include incorporating a ligand conformer generation module, enhancing the dataset with AlphaFold-predicted structure and public available SAR data, integrating the segmentation of functional block in an end-to-end manner, and combining the model with protein backbone dynamics modeling to handle larger scale conformation changes induced by drug-protein interactions.


## 5.1 Blind re-docking new receptors

We also benchmark on the new receptors test set in which the proteins have not been seen in the training set, shown in table 5 and figure 5 .


## 5.2 Pseudo code for the trigonometry module and an illustrative figure for trigonometry updating

The pseudo code for the whole trigonometry module is listed below. The whole module contains three sub-module: TrigonometryUpdating, TriangleSelfAttention , and Transition .

The TrigonometryModule function for updating z ij .

The TrigonometryUpdating function.

The TriangleSelfAttention function.

The Tranistion function.

Figure 6 shows the embeddings used to update a single interaction embedding, z ij between a protein node i and a ligand node j .


## 5.3 Visualization of the gate functions and the self-attention map

To show the motivation behind the employment of the gate functions and self-attention, we have visualization them using an example, PDB 6HD6. Figure7 shows the output of the gate function at the last stacked layer for the native protein block with the compound FYH. Its resemblance to the inter-molecular distance map indicates the gate function is able to modulate the interaction based on the predicted distance.

Figure8 shows the output of the self-attention map (3rd head) at the last stacked layer averaged over all protein nodes for the native protein block with compound FYH. The output resembles the compound intra-molecular distance map. This indicates that the self-attention module is aware of the compound conformation and is able to update the interaction embedding based on this.


## 6 Another example of TankBind finding the correct binding site when both the protein and the ligand are unseen

A protein is unseen when the max protein sequence similarity (normalized Smith-Waterman alignment score) to the training set is less than 0.8. A compound is unseen when max compound similarity (Tanimoto Similarity of Morgan fingerprints) to the training set is less than 0.5. Figure 9 shows that, for PDB 6KQI, we correctly locate the true binding site on the protein, while the other two methods fail to do so under the same re-docking setting.


## 7 Runtime details of different methods

The averaged runtime is shown in table 6 . Baseline numbers are taken from EquiBind paper. The TankBind model has 1.8M parameters, comparable to EquiBind and GNINA, having 1.4M and 0.4M parameters respectively.


## 8 Repeated runs of protein-ligand binding affinity prediction

Table 7 provides more details than the figure in main text, including the mean and standard deviation of various methods across 3 experimental runs. Our model outperforms other models. For PIGNet and STAMP-DPI, we were unable to re-train the model, so we directly used the save-model provided by official repository for prediction.


## 9 Additional ablation studies

Our ablation studies compose of mainly two categories. The first one is mainly associated with the framework of model, and the second one is associated with the training protocol. On the model side, TankBind-P is only doing the first summation over protein nodes inside the bracket of the equation 1 , TankBind-C is only doing the second summation. We also included the results when the whole trigonometry module is only applied once, (single stack), and is completely removed, (no trig). For protein embedding, we tested using the pre-trained model TAPE to embed the protein instead of the GVP, and, for compound embedding, using GAT in place of GIN. On the side of training protocol, we tried replacing P2Rank binding sites with randomly selected binding sites, “TankBind-R”, removing the random shift added to the center of protein block, “no random”, and only training on the protein block contains the native ligand, “native only”.


## 10 Example of the existence of equally valid binding sites that confuses the result

PDBbind curated the raw PDB file by only preserving a single ligand. In a few cases, when two or more identical chains are crystallized together, there are more than one valid binding site for the ligand. Here, we show an example with PDB 6MO9 in figure 10 .


## 11 Details about protein segmentation

Protein graph is segmented for two main reasons: computational memory efficiency and biological functional generalization. One the computational side, since the size of proteins has a large variation, ranging from a few dozen amino acids to more than 3000 amino acids, the memory consumption to represent the protein and the interaction between protein and ligand could easily exceed the capacity of a typical GPU. On the biological side, large protein typically have multiple domains. Each protein domain, typically of size 200 amino acids, folds and interacts with ligand independently from the rest. Also, protein domains, as the building blocks of proteins, are more evolutionary conserved which means that a model explicitly learning on a domain level could generalize better to new domains. Each block is a sphere of radius 20Å typically includes about 200 amino acids, in line with the size of a protein domain. Block of radius 20Å is large enough to enclose the drug molecules, which is usually less than 15Å long, and small enough to be memory efficient.

We tried two ways of segmenting the whole protein. First approach is random segmentation; We randomly select an protein node, and use this node as the block center. But this approach is not efficient, since the binding site on protein has certain characteristic, more hydrophobic for instance. In second approach, we used a ligand-agnostic method, P2rank v2.3 (trained model was released on 2018) Krivák and Hoksza [2018] to identify possible ligand binding sites, and use the centers of those potential binding sites as the block centers. For some small proteins, no binding site is identified, we therefore add an extra protein block located at the center of the whole protein. During training, we also add an extra protein block centering at the centroid of the co-crystallized ligand.

Despite P2rank assigns a score to each predicted binding site on the protein, the scores are fixed regardless of the interacting ligand because of the ligand-agnostic nature of P2rank. If we simply use the center of most probable binding site predicted by P2rank as the center of interaction block, this interaction block encloses the ligand for 73% of the test set. Our method, being a ligand-dependent method, improve the rate to 90%.


## 12 Systematically analysis of the PDBbind dataset

In order to examine whether our model has the capability to place the compound to a unseen binding site, we aligned all the training protein-ligand complex structure with the same protein, defined by having the same UniProt ID , to the test set protein. Kalign is used to align the protein sequences first, and Superimposer function within package BioPython is used to align the structures. After the alignment, we computed centroid distance between aligned compounds and centroid of the test set compound. We found three cases in total having the centroid of all aligned training set compounds at least 10Å away from the centroid of test set ligand. They are PDB 6HMY, 6MO9 and 6K1S. With a visual examination of these PDBs along with aligned training set PDBs, we found that the, for PDB 6HMY and 6MO9, the apparently unseen binding site are caused by the process of crystallization and multimeric nature of certain proteins. For PDB 6MO9, the single chain protein having two identical binding sites due to packing during crystallization. For PDB 6HMY, the protein is a pentamer which means there are actually 5 identical binding sites for the complete protein complex. But in PDB 6K1S, we found a genuine unseen site. We found three training set PDBs having the same protein: 4X60, 4X61, 4X63. In order to remove the possibility that a close homolog exists, we computed the normalized Smith-Waterman alignment score, and found no homolog with score above 0.8 for PDB 6K1S other than the three PDBs with identical protein mentioned beforehand. Compound similarity is computed based on the Tanimoto Similarity of their Morgan fingerprint using RDKit.


## 13 Hyper-parameters

The embedding sizes of the embedding of protein blocks and compound embedding are 128. The channel sizes of distance embedding are also 128. The trigonometry module is stacked 5 times. Transition module is a multilayer perceptron, where the hidden channel size is four times the input channel size. Dropout rate is set to 25%. layernorm is applied after each transition.


## 14 Training details

During training, data is augmented in two ways. First the protein blocks that do not bind to the specific compound are used as decoys. The constrastive loss function is designed to ensure the compound binds weaker to those decoys than the native protein block. The margin, ϵ in constrastive loss is set to 1, corresponding to 1 order of magnitude in binding concentration. A protein block encloses the ligand when it covers more than 90% of the native interaction. Second, the model will see a slightly different protein block for every training data because the center of block will have a random shift of −5Å to 5Å, drawn from the uniform distribution, in all three axes. In bind re-docking, the native conformation is given as input, while in bind self-docking setting, the local atomic structures (LAS) mask, as defined in section 3.5 is applied to the compound node pair-distance map. The compound node pair distance map is based on the native conformation during training and based on the conformation generated by RDKit during testing. Our model include the models in ablation studies are trained for 200 epochs, after which no performance gain was observed. The model with the lowest validation loss was chosen as the best model. Each epoch has 20,000 randomly sampled block-ligand pairs. The total training process takes about 50 hours on a single NVIDIA RTX 3090 GPU. We use Adam optimizer with a constant learning rate of 0.0001.


## 15 Implementation details of baselines for drug-protein binding structure prediction


## Vina

AutoDock Vina v1.2.3 is downloaded from https://github.com/ccsb-scripps/AutoDock-Vina . We follow the tutorial listed in https://autodock-vina.readthedocs.io/en/latest/docking_basic.html and use the center of ligand as the box center. The box size is set to 100Å and exhuastiveness is set to 32.


## EquiBind

EquiBind is downloaded from https://github.com/HannesStark/EquiBind . We follow the instruction and use saved model as listed in the GitHub. Our result slightly differs from the reported value. It could be due to a version change made by the developer, since its still an active repository. In the setting of “new receptors”, following the same procedure, We got 142 “new receptors” PDBs while EquiBind got 144 (exact list not provided). We estimated that the 142 version and 144 version will affect the reported value by less than 2%. The result for other baselines are copied directly from the EquiBind paper for ease of comparison.


## 16 Implementation details of baselines for binding affinity prediction


## TransformerCPI

We downloaded the code from the official repository https://github.com/lifanchen-simm/transformerCPI . we changed from the default classification task to regression task and switched to the PDBbind2020 dataset with time split, word2vec model is also retrained to extract sequence features based on the new dataset.


## MONN

We downloaded the code from the official repository https://github.com/lishuya17/MONN . The authors did not use a separate validation set, but instead used a clustering-based crossvalidation strategy. We switched the data split mode to time split and repeated the original authors’ data preprocessing steps on PDBbind2020 dataset.


## PIGNet

We downloaded the code and best save-model (best performance on CASF2016 bench-mark) from their official repository https://github.com/ACE-KAIST/PIGNet . Due to the lacking of pre-processing scripts for data augmentation, we were unable to re-train the model using PDB-bind2020. Instead, we used the best save-model presented by the authors. The result could be improved with additional data augmentation on the whole dataset instead of the PDBbind2019 refined set currently used for training.


## IGN

We downloaded the code from their official repository https://github.com/zjujdj/InteractionGraphNet/tree/master . The authors used PDBbind V2016 as an experimental dataset. We switched the data split mode to time split and repeated the data pre-processing protocol used by the authors on PDBBind2020.


## HOLOPROT

We downloaded the code from their official repository https://github.com/vsomnath/holoprot . The authors used PDBbind2019 refined set as an experimental dataset split by ligand scaffold and protein sequence. We followed the original authors’ data pre-processing on PDBbind2020 and calculated the multi-scale representation of proteins. The model was retrained on this new dataset with the default setting.


## STAMP-DPI

We downloaded the code from their official repository https://github.com/biomed-AI/STAMP-DPI . The authors used PDBbind2016 general set as training set. We followed the original data pre-processing and performed on the split PDBbind 2020 test set. We were unable to extract all features required for training due to time constraints. The released model was employed to evaluate on the test set without re-training.


## Acknowledgments and Disclosure of Funding

We thank Prof. Peter Wolynes, Prof.Yuedong Yang, Dr. Nicholas P Schafer, Dr.Leilei Shi, Dr. Jiahui Tong, for their helpful discussions; Penglei Wang for his support in binding affinity experiments; Meihui Song for her support in figure drawing. We thank the Guangzhou National Supercomputer Center for providing computational source.


## Footnotes

Accepted to NeurIPS2022