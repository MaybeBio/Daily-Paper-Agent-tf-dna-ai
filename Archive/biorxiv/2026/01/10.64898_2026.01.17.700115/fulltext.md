## Abstract

Predicting antibody-antigen binding affinity is critical for therapeutic development, but machine learning-based approaches to the problem are typically hampered by the small amount of available structural and affinity data. We introduce SE3Bind, an SE(3)-equivariant architecture trained on two related tasks: re-docking of an antibody structure to its matching antigen structure, and antibody-antigen binding free energy prediction. Both tasks encourage the model to learn an energy function formulated in terms of scalar and vector fields associated with each protein. Under a stringent training/validation split of the data based on antigen sequence similarity, SE3Bind demonstrates an ability to generalize to out-of-distribution examples and achieves a performance comparable to that of existing models evaluated under similar conditions.


## 1 Introduction

Antibodies represent one of the most important classes of therapeutics, with applications in oncology, autoimmunity, and infectious diseases [ 1 ]. Since antibody derive their efficacy from their high binding selectivity to antigens, detailed structural information, from either experimental or computational sources, is essential for guiding rational antibody engineering and affinity prediction [ 2 , 3 , 4 ].

Recent advances in computational protein structure prediction such as AlphaFold [ 5 ], AlphaFold-Multimer [ 6 ], AlphaFold3 [ 7 ], and ESMFold [ 8 ] have made it possible to rapidly and accurately model many protein complexes. Nevertheless, antibody structure prediction continues to pose challenges, largely due to the structural diversity of complementarity-determining regions (CDRs)— of the CDR-H3 loop in particular [ 9 ]. Antibody-specific structure prediction frameworks have been introduced, including DeepAb [ 10 ], ABlooper [ 11 ], Ig-Fold [ 12 ], BLAM [ 13 ], AntiFold [ 14 ] and Ibex [ 15 ]. While these specialized approaches have improved the reconstruction of flexible CDR loops, achieving accurate predictions of complete antibody–antigen complexes is still an open challenge.

Despite the importance of antibodies as therapeutics, the structural coverage of antibody–antigen complexes remains low and associated binding affinity data is scarce [ 16 ]. This scarcity makes it difficult to directly train machine learning models for Δ G prediction. Given the continual improvement of structure prediction methods, and in anticipation of the time at which even challenging antibody-antigen structures can be predicted, it is useful to investigate how accurately binding affinities can be predicted from the current limited number of known complex structures.

Here, we present SE3Bind, an SE(3)-equivariant convolutional neural network (CNN) for predicting binding free energy (Δ G ) from high-resolution antibody-antigen complex structures. SE3Bind builds upon our previous finding [ 17 ] that the energy function learned from tasks such as molecular docking, fact-of-interaction prediction, or binding affinity prediction is highly transferable. It leverages limited antibody-antigen structural and binding affinity data to learn meaningful protein representations through two related tasks: re-docking of proteins forming a complex and prediction of their binding affinity. The energy function itself is written in a form often encountered in the theory of molecular interactions: as a volume integral of the product of two molecular fields.


## 2 Datasets

Training data was extracted from PDB-bind (v.2020) [ 18 ], which includes 2846 antibody-antigen structures with binding affinity measurements, and from SKEMPI 2.0 [ 19 ], which includes 4348. Crystal structures with a resolution of 3.25 Å or better were selected, resulting in a total of 2975 unique Protein Data Bank (PDB) IDs. The SACS antibody database [ 20 ] (accessed June 2022) contains 1,584 entries with both heavy and light antibody chains in complex with at least one antigen chain. Antibody-antigen pairs were matched using the SACS chain-mapping list. For instances in which the PDB file contains multiple copies of the antibody-antigen complex, each copy was included as a separate complex example. From SKEMPI 2.0 only the wild-type binding affinity information was incorporated, so that no mutated structures had to be predicted. Additionally, when multiple Δ G values are reported for any given antibody-antigen pair, the median Δ G value was taken as the experimental ground truth (see Section 4.1 for details).

Total of 668 antibody-antigen PDB files with associated Δ G are selected. From this set, 492 PDB IDs remain after filtering for resolution and removing entries with missing an antigen partner. Only antibodies with both a heavy and a light chain forming a complex with an antigen were included in the dataset. Antibody-antigen complexes are kept in their original PDB orientations, provided they fit within a cubic box of 150-Å side. Additionally, both the antibody and antigen components individually had to fit within a cubic box of 100-Å side, resulting in the final training set of 443 examples representing 282 unique antibody-antigen complexes (because some examples are from the same PDB file) and 311 experimental Δ G values (because some examples have more than one reported Δ G measurement). (See Supporting Table A.1 for the list.)

The validation set was assembled by combining two datasets: BM5.5 [ 21 ] and SAbDab [ 22 ]. From SAbDab, only complexes with antigens labeled as “protein” were included, while all antibody categories from BM5.5 were incorporated, including singledomain antibody complexes. Both datasets were filtered to retain only crystal structures with resolutions of 3.25 Å or better.

To minimize data leakage, antibody–antigen complexes with similar epitope–paratope interfaces were constrained to the same set (training or validation) by grouping them according to the UniRef50 [ 23 ] cluster ID of the antigen. Not controlling for data leakage can lead to severe overestimation of the model’s performance [ 24 ]. The validation set examples were drawn from clusters absent from the training set, yielding a total of 15 antibody–antigen complexes. (See Supporting Table A.2 for the list.) All examples were processed using homology modeling package MODELLER [ 25 ] to generate any unresolved residues and to standardize the stereochemistry. The training set only includes homology models, while the validation set has both the crystal structures and their corresponding homology models.


## 3 Model architecture

The architecture of the model is presented in Figure 1 . It is primarily designed for the task of predicting Δ G , the binding free energy of an antibody-antigen pair, given the three-dimensional structure of its complex. This task will be called “Task 1”.

The model can be pre-trained on a conventional re-docking task, which consists of predicting ( t b , ω b ), the pose of the antigen relative to the antibody, given the three-dimensional structures of both fragments. ( t b and ω b are the translation and rotation that bring the antigen to its correct position relative to the antibody.) However, with the equivariant architecture used in this work, it was found that the docking task can be learned “zero-shot” by training on the simpler task of predicting t b , given the fragment structures presented in the correct orientation [ 17 ]. This simpler task will be called “Task 0”

For each fragment—either the receptor R , the ligand L , or the receptor-ligand complex RL —, volumetric features are computed using an SE(3)-equivariant convolutional neural network (CNN) [ 26 ]. Each atom of the fragment is initially represented by a Gaussian distribution with standard deviation σ = 2 Å and projected on a grid of 2 Å resolution [ 27 ]. Five input channels are created: one for the carbon atoms, one for the nitrogen atoms, one for the oxygen atoms, one for the sulfur atoms, and one for all non-hydrogen atoms combined (which represents the sum of all previous channels). In the rest of the discussion, “receptor” will denote the antibody fragment and “ligand” will denote the antigen fragment. Because of the voxel-based representation of the input, each fragment can be formed of any number of protein chains.

Following our recent work [ 28 , 17 ], the CNN module has four convolutional layers, each using a kernel size of 9 × 9 × 9. Given the 2 Å resolution of the grid, this represents a receptive field of 64 Å × 64 Å × 64 Å. The first layer maps the five input channels onto eight scalars, eight vectors, and four tensors (rank 2), the second layer maps these onto eight new scalars, eight new vectors and four new tensors, the third layer operates like the second layer, and the fourth layer maps these back to three scalars and two vectors. All convolutional layers except the last one are followed by a hyperbolic tangent (“tanh”) nonlinearity applied on the element-wise norm of each feature, which preserves SE(3) equivariance.

The convolutional kernels map between input and output fields that transform under 3D rotations, and are designed to preserve these transformation properties throughout the network. To build kernels that ensure SO(3) equivariance, we follow the procedure outlined by Weiler et al. [ 26 ]. Each kernel is parameterized as a linear combination of basis functions, formed as products of radial and angular functions. The radial profile is represented using a basis of “shell” functions φ n ( r ), where r is the distance to the center of the kernel and n = 1 to 7. Each shell has a radius r n and a thickness σ , whose values are chosen so as to uniformly cover the volume of the 9 × 9 × 9 kernel. The angular dependence is captured by spherical harmonics Y lm , where l ranges from 0 to l max = 2 and m ranges from − l to + l . This forms a basis for functions on the sphere and encodes the directional structure required for SO(3) equivariance.

Each kernel is precomputed and stacked into a 5D tensor of shape (9, 9, 9, K in , K out ), where K in and K out correspond to the total number of components of the input and output features, respectively. For SE3Bind, the input layer consists in 5 scalar fields (1 component each), which corresponds to K = 5 × 1 = 5, and the hidden layers consist in 8 scalar fields, 8 vector fields (3 components each) and 4 tensor fields (5 components each), which corresponds to a total of K = 8 × 1 + 8 × 3 + 4 × 5 = 52 components. For an output layer consisting in 3 scalars and 2 vectors, K = 3 × 1 + 2 × 3 = 9. The kernel is passed to a conventional 3D convolution routine ( torch.nn.functional.conv3d ).


## 3.1 Binding pose

For each fragment, the network generates five volumetric features: three scalars F 0 , F 1 , and F 2 , and two vectors F 3 and F 4 . The interaction energy E ( t , ω ) is computed from the spatial correlations between receptor features F i [ R ] and ligand features F i [ L ], with i = 1 to 4 [ 28 , 17 ]: Note that features “0” are not included in the expression of the interaction energy: They are used later on for the calculation of the binding free energy. Function corr( F i [ R ], F i [ L ], t , ω ) represents the spatial correlation of feature F i [ R ] with a rotated and translated version of feature F i [ L ]. (Since the features are generated from an SE(3)-equivariant network, transforming the ligand features amounts to computing the features from the rotated and translated ligand.) Correlations are computed using a three-dimensional fast Fourier transform [ 29 ], which enables all translations t to be evaluated at once. The “ a ” coefficients are treated as learnable parameters.

The special case a 2 = − a 1 = 1 and a 4 = − a 3 = 1 has an interesting physical interpretation, since it can be re-cast as defining the energy in terms of a “charge” feature on one fragment interacting with an “electrostatic potential” feature on the other, and of a “dipole” feature on one fragment interacting with an “electric field” feature on the other.

The binding pose can be predicted by finding the ligand translation and rotation that minimize E ( t , ω ). If the ground-truth rotation ω b is provided (as in Task 0), the binding pose can be predicted by finding the translation that minimizes E ( t , ω b ). If the ground-truth translation t b is provided as well (as in Task 1), the interaction energy simply corresponds to E ( t b , ω b ).


## 3.2 Binding free energy

A binding event corresponds to the formation of a receptor-ligand complex RL from a receptor R and a ligand L freely moving in solution. Formally, the binding free energy can be expressed as where Z ( N R , N L , N RL ) is the partition function of a solution of N R copies of the receptor, N L copies of the ligand, and N RL copies of the receptor-ligand complex. Assuming that the copies of all fragments behave independently, the partition function can be factorized as following: where z F is the partition function of a single copy of fragment F in solution. The binding free energy then becomes (For a fuller discussion of the theory of molecular affinities, see for instance Ref. [ 30 ].)

Partition function z RL can be defined as a sum over all poses belonging to the bound state B and product z R z L can be defined as its complement: ζ b is the partition function associated with the internal degrees of freedom in the bound state, defined in terms of feature “0” of the RL complex: and ζ u is the equivalent function in the unbound state, defined in terms of feature “0” of the receptor and feature “0” of the ligand: For simplicity, we assume that the bound state is dominated by a single conformation ( t b , ω b ) and we write We also assume that the unbound state is represented by a large number of microstates for which E ( t , ω ) = 0 and we write N 0 is related to the concentrations of R and L but is expected to be the same across all examples if the Δ G values are defined according to the standard state.

The binding free energy expression from Eq. (5) becomes with Coefficients “ a ” and N 0 are treated as learnable parameters, along with the weights of the SE(3)-CNN producing the protein features.


## 4 Model training and testing


## 4.1 Two-stage training

The architecture described above is trained in two stages:

The protein features are learned by training on Task 0, which consists in predicting the correct translation t b when the interacting fragments are presented in the correct orientation ω b . ℒ 0 , the loss function for Task 0, is defined as the cross-entropy loss between the Boltzmann probability distribution and the ground-truth probability, which is 1 for translation t b and 0 for all other translations. Because feature “0” has no influence on E (see Eq. 1 ), we also apply an L1 regularization loss that keeps it close to zero at all points in space.

The protein features are learned by jointly training on Task 0 and Task 1, which consists in predicting the correct binding affinity Δ G b when the fragments are presented in the correct pose ( t b , ω b ). Training aims to minimize the sum ℒ 0 + ℒ 1 with regularization weight of 10 −3 , where ℒ 1 is the L1 regression loss on the binding free energies.

For examples with multiple experimental Δ G values, the median value is used as ground truth, consistent with ℒ 1 being an L1 regression loss. For the SE3Bind models in which ℒ 1 is replaced with an L2 loss, the average is used as ground truth.

Each training example has two labels: the docking pose ( t b , ω b ) and the binding free energy Δ G b , and therefore the same dataset can be used for both Task 0 and Task 1. In stage 1, the model is trained for 200 epochs; in stage 2, all models are trained for 1000 epochs.


## 5 Results


## 5.1 Learned features

The features learned from task 0 represent scalar and vector fields that contribute to the protein-protein interaction energy in a way similar to how the electrostatic potential ϕ and the electric field E would— along with their conjugate quantities, the charge density q and the polarization density µ . Scalar feature F 0 , used only for the binding affinity prediction task, can describe any additional contribution to Δ G not directly related to an interaction but related to the energy difference between the bound state and the unbound state. It can in principle account for entropic contributions.

Although we do no expect a direct connection to physical properties ϕ and q , a visual inspection of the scalar features (see Figure 2 ) suggests that the model is capturing meaningful variations of these properties near the entire surface of the protein.


## 5.2 Performance on the validation set

Table 1 summarizes the performance of SE3Bind and its ablated versions. Performance is measured using the mean absolute error (MAE) on the binding affinity—which corresponds to L 1 , the L1 regression loss—and the Pearson correlation coefficient R between the experimental and predicted Δ G values. Two versions of the validation set are used: one with homology models prepared as for the training set and the other with crystal structures.

While F 0 can in principle provide an indirect contribution to the binding free energy, models in which F 0 is turned off ( F 0 = 0) do not show a marked decrease in accuracy. By contrast, models in which F 0 is constrained to be positive ( F 0 ≥ 0) seem to perform slightly worse on Δ G prediction, both during training and during validation (see Table 1 ).

Models trained using an L2 regression loss for L 1 (instead of an L1 loss) display stronger signs of overfitting, with significantly lower Δ G MAEs on the training set but higher Δ G MAEs on the validation set (see Table 1 ).

The final SE3Bind architecture (first line of Table 1 ) is selected based on the overall Δ G MAE and overall Δ G correlation (see Figure 3 ). SE3Bind achieves a Δ G correlation of 0.56 on the training dataset, which is not the highest but which displays less overfitting than that of models trained using an L2 regression loss. SE3Bind also yields more consistent performance for the “homology models” and “crystal structures” validation sets, with Δ G correlation coefficients of 0.26 and 0.24, respectively. Although some of the SE3Bind variants produce higher R values on the training set, this improvement does not transfer to the validation sets (see Supporting Figure A.1 for details).


## 5.3 Comparison with models from the literature

Table 2 compares the performance of SE3Bind with existing affinity prediction models from the literature. To focus the comparison, all models selected have been specifically evaluated on antibody-antigen affinity benchmarks such as SabDab [ 22 ], AB-Bind S645 [ 32 ], or mmCSM-AB/mCSM-AB2 [ 33 ], or on the antibody-antigen structures from BM5.5 [ 21 ]. The AB-Bind S645 dataset comprises 645 ΔΔ G measurements associated with single mutations across 29 distinct antibody–antigen complexes. It also includes 27 “non-binders”, assigned a binding affinity of −8 kcal/mol. The BM5.5 dataset [ 21 ] includes 33 antibody–antigen complexes with experimentally measured binding affinities. Some of the prediction models have also been evaluated on more general PPI affinity benchmarks such as SKEMPI [ 19 ], which Table 2 also reports.

As Table 2 shows, a model’s capacity to generalize can be greatly overestimated if data leakage from the training set to the validation set is not explicitly controlled for. For instance, the TopNetTree architecture [ 34 ] trained on SKEMPI 1131 displays a ΔΔ G correlation of 0.85 for a random K -fold split but a correlation of only 0.38 for a training/validation split by protein Evolutionary Classification of Domains (ECOD) classes [ 35 ], which prevents data leakage across structural homologs. A similar trend is observed for the Graphinity architecture [ 24 ], which displays a ΔΔ G correlation of 0.87 for a random K -fold split but a correlation of only 0.25 for a split by clusters possessing similar CDR loops.

SE3Bind model’s performance is in line with that trend. Data leakage is prevented by keeping in the same set (training or validation) any two antigens with sequence identity greater than 50%. This ensures that the antibody-antigen interface of any example in the validation set will be different from all interfaces from the training set, regardless of the antibody.

To compare the SE3Bind data split achieved using a 50% antigen sequence cutoff with the Graphinity data splits based on CDR loops sequence identity, we follow the approach of Hummer et al [ 24 ] and examine the length-matched CDR sequence identity between the SE3Bind training and validation sets. Specifically, each of the three CDR loops from both the heavy and light chains were extracted using CDR sequences from SAbDab [ 22 ] and sequence identity was measured using multiple sequence alignment tool Clustal Omega [ 36 ]. For the H3 loop on the heavy chain, which is the main determinant of binding specificity [ 37 ], the median sequence identity between training and validation sets is 20%, with three antibodies sharing 100% CDR sequence identity despite the antigens having no more than 50% sequence identity (see Supporting Figure A.2 ). Splitting the datasets by UniRef50 antigen clusters and verifying CDR sequence identities confirmed that the training and validation sets consisted of largely non-overlapping examples. Under these stringent dataset splits, the model achieved binding affinity prediction performance comparable to existing methods.

Table 2 is also consistent with the fact that binding affinity is generally more difficult to predict for antibody-antigen pairs than for generic protein-protein pairs. Regardless of the data splitting approach used, every model reported in Table 2 performs significantly worse when validated on antibodyantigen pairs.


## 6 Conclusion

We present SE3Bind, an SE(3)-equivariant model capable of learning a protein-protein interaction energy function formulated in term of spatial correlations between representations similar to “molecular interaction fields” [ 45 ]. The energy function is pre-trained on a simplified re-docking task, then jointly trained on the task of estimating binding free energies.

For antibody-antigen interactions, our work confirms, as Hummer et al have observed [ 24 ], that the current generation of models overfit the available antibody-antigen affinity data, of which there is still too little. The resulting low capacity for generalizing may even be masked by the choice of validation metrics. Biologically- or structurally-informed partitioning of data is therefore essential for drawing realistic conclusions about predictive performance.

While acquiring more experimental data will assuredly help, another avenue is to augment existing binding affinity data with synthetic structural data. In absence of experimentally-determined structures, any reliable prediction of the structure of the antibody-antigen pair can provide insights on the factors driving the binding affinity; so can any prediction of the conformational ensembles accessible to the bound and unbound antibody-antigen pair, generated by methods such as AFsample2 [ 46 ] or Boltz-2 [ 47 ]

The relative simplicity of the SE3Bind model suggests that, given enough data, more complex volumetric representations of each interaction partner could be learned, composed of much more than 3 scalar fields and 2 vector fields [ 28 ]. Such representations may provide a better description of the structural features responsible for binding affinity.


## Code and data availability

The code and data related to this work are available at https://github.com/lamoureux-lab/SE3Bind .


## Conflict of interest

G. L. is consultant for Genentech, Inc.


## Supporting information


## Acknowledgments

The authors acknowledge the Office of Advanced Research Computing (OARC) at Rutgers University for access to the Amarel cluster and related computing resources. This work is supported by National Science Foundation Award Number 2152059.


## Funder Information Declared


## Footnotes

↵ † a.sub{at}rutgers.edu

↵ ‡ sid.bl{at}rutgers.edu (now at Bristol Myers-Squibb)

↵ § guillaume.lamoureux{at}rutgers.edu

https://github.com/lamoureux-lab/SE3Bind