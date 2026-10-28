## ABSTRACT

In the traditional scoring functions for protein–ligand binding affinity prediction, the energies of the electrostatic and van der Waals interactions were evaluated (or restricted) by the mathematical expressions of and , respectively. In comparison, the power exponents of distance-based variables as adopted in the present study are not restricted as those in traditional energy terms for atomic interactions. The distance-based variables were integrated using linear regression and artificial neural network to predict the protein–ligand binding affinity or binding energy. The training of the linear, neural network and mixed models was based on the newest data in PDBbind, i.e ., PDBbind (v.2024). Estimated according to Pearson’s correlation coefficient ( R ), the best performances of the linear models are 0.700 < R ≤ 0.800 with the high-quality affinity data, and those of the neural network-based mixed models are 0.800 ≤ R < 0.900 with the same data. The predictive powers of the best models developed in this study are superior to the sophisticated linear and machine learning-based scoring functions developed before. The results suggest that the distance-based variables with appropriate power exponents may have the ability to improve the prediction of protein–ligand binding affinity with high accuracy.

HIGHLIGHTS

By using the newest data in PDBbind (v.2024) to train the linear, neural network and mixed models, the quantitative distance–energy relationships are further explored and improved to predict the binding affinity of protein–ligand complexes.

The power exponents of distance in the traditional energy terms are expanded to characterize the distance–energy relationships accurately at atom level for protein–ligand interactions.

The best models are superior to the sophisticated machine learning-based scoring functions developed before.


## 1. INTRODUCTION

The protein–ligand binding affinity refers to the binding strength between the ligand molecule (such as a drug molecule) and the target protein (such as a receptor protein). This parameter is crucial not only in characterizing the protein–ligand binding interactions, but it is also a key parameter in rational drug design [ 1 ]. Experimental determination of the protein–ligand binding affinity usually is labor intensive and time consuming. In theory, computational prediction of the protein–ligand binding affinity is a viable option for saving experimental time and cost [ 2 , 3 ]. In the literature, the methods for computing the protein–ligand binding affinity/energy can be roughly categorized into two classes: the molecular dynamics simulation-based methods and the scoring functions [ 4 ]. The former is relatively rigorous which requires extensive computational resource and time; the latter is usually viewed less rigorous but is more suited for computing the binding affinities for a large number of protein–ligand complexes in a high throughput fashion. The scoring functions are usually trained based on the known experimental structures and binding affinities [ 3 ]. At present, the performances of the scoring functions with explicit formations are almost always not as good compared to those without explicit formations such as the machine learning-based methods [ 3 , 5 - 8 ].

In this work, the performances of distance-based models for protein–ligand binding affinity prediction were further explored using the artificial neural network. The power exponents of distance-based variables in the traditional energy terms were expanded as adopted in the previous work [ 9 ]. For examples, the energies of the electrostatic and van der Waals interactions were estimated (or restricted) using the mathematical expressions of and , respectively. Here, r is the distance of the interacting atom pair, and a, b, c are the corresponding parameters. Additionally, a large number of more reliable experimental structures from PDBbind (v.2024) [ 10 , 11 ] were employed to generate the models. The performances of the best models presented in this work are better than those of the sophisticated methods developed earlier.


## 2. MATERIALS AND METHODS


## 2.1. Datasets

The protein–ligand binding affinity data used in this work were filtered from PDBbind (v.2024) [ 10 , 11 ]. The original experimental structures of these complexes are downloaded from Protein Data Bank ( https://www.rcsb.org/ ) [ 12 ]. The protein–ligand complexes were filtered by five criteria: 1) there is a definite experimental binding affinity, i.e ., inhibition constant ( K i ) or dissociation constant ( K d ); 2) The number of atoms for the ligand molecule is ≤150, and the number of its heavy atoms is ≤70; 3) no clashes between the heavy atoms, i.e ., the distance between any two heavy atoms > 1 Å; 4) protein–peptide interactions are not considered; 5) no unusual or unrecognized atom types (such as Cd, Cu, As, Y, Yb, Ru, Pt, V, Si, Be, Al, Rb, Pr, Mo, Cs, Te, Sr, Re, In, Ga, Eu and Du) in the binding pockets. After filtering, there are 13733 protein–ligand complexes. They were divided into four sets based on the data quality defined by PDBbind v.2024 [ 10 , 11 ]. SET -1 (6999 complexes) is from PDBbind v.2024 general set, SET -2 (5215 complexes) from PDBbind v.2024 refined set with high-quality data, SET -3 (1234 complexes) from PDBbind v.2024 refined+ set composed of high-quality data and complexes with metal-containing proteins and their ligands, and SET -4 (285 complexes) is the Core Set (CASF-2016) [ 3 ].


## 2.2. Atom types and interacting pairs

The atom types in the experimental structures were assigned using Open Babel 2.4.1 [ 13 ]. There are 36 heavy atom types for receptors and ligands in the binding pockets ( Supplementary Table S1 ). The water molecules were excluded and the multiple ligands of the same type in the experimental structure were adopted. As defined in the previous work [ 9 ], an interacting atom pair is composed of two atoms with distance > 1 Å and ≤ 10 Å. The two atoms are from the ligand and the receptor, respectively. In considering the different surrounding environments of atoms in the ligand and the receptor, the pair composed of atom type 1 from the ligand and atom type 2 from the receptor is different from that composed of atom type 2 from the ligand and atom type 1 from the receptor (here atom type 1 is not the same with atom type 2). In total, there are 859 kinds of atom type pairs.


## 2.3. Affinity predictive models

The distance-based pre-linear models were trained using the least-square method [ 14 ]. The mathematical expression of the pre-linear models is shown as follows:

Here, K is the inhibition constant ( K i ) or dissociation constant ( K d ); a i and b are the coefficients and the constant term, respectively; N l is the number of ligands with same type in the experimental structure; d ij is the distance of the j th interacting atom pair for the i th kind of atom type pair; m is equal to 859, which is the total number of atom type pairs; k is the power exponent, different power exponent corresponds to different pre-linear model.

The training set was composed of 8000 protein–ligand complexes which were stochastically selected from the whole set (13733 complexes). All the 859 atom type pairs were included in the training set. The random selection was repeated 10000 times. So, there were 10000 training sets to train the pre-linear models. One representative pre-linear model for each power exponent was selected from all 180000 linear models.

The mathematical formation of the linear models based on the pre-linear models is expressed as follows:

Here, K is the inhibition constant ( K i ) or dissociation constant ( K d ); a i and b are the coefficients and the constant term, respectively; prelm i is the predicted value using the i th pre-linear model, n is the maximum power exponent of the distance-based variables in the adopted pre-linear models.

The training set was generated in the same way as the pre-linear models. The random selection was repeated 100 times. So, there were 100 training sets to train the linear models. All the combinations (2 18 -1) of the 18 representative pre-linear models with different power exponents were employed to generate the linear models. Finally, there were 26214300 ((2 18 -1)*100) linear models, and one representative linear model was selected according to the performances in the four sets.

In order to further explore the affinity predictive power of distance-based variables, the back propagation neural network [ 15 , 16 ] was used to train affinity predictive models. The distance-based variables were same as those in the pre-linear models. One or two hidden layers were employed in the neural network architecture, and the number of nodes at each hidden layer was set to 5, 10, 15 or 20. As such, there were 20 (4 + 4 □ 4) neural network architectures. For each neural network architecture, 10 models were trained to find the best network parameters. The training set was the one used for the representative pre-linear models. For every power exponent, 18 representative neural network models were selected from the 200 models.

The formation of the mixed models based on the representative neural network models using the distance-based variable with same power exponent was as follows:

Here, K is the inhibition constant ( K i ) or dissociation constant ( K d ); a i and b are the coefficients and the constant term, respectively; nnm i is the predicted value using the i th neural network model, n is the maximum power exponent of the distance-based variables in the adopted neural network models.

The training sets were same with those for the mixed models based on the representative pre-linear models. For each power exponent, one representative mixed model based on the 18 representative neural network models was selected according to the performances in the four sets.

The final mixed models with different power exponents were trained based on the 18 representative mixed models based on neural network models. The formation of the final mixed models was as follows:

Here, K is the inhibition constant ( K i ) or dissociation constant ( K d ); a i and b are the coefficients and the constant term, respectively; mm i is the predicted value using the i th mixed model, n is the maximum power exponent of the distance-based variables in the adopted mixed models.

The training sets were same with those for the mixed models based on the representative pre-linear models. One representative final mixed model based on the mixed models was selected according to the performances in the four sets.


## 2.4. Metrics for evaluating the performance of the affinity predictive models

The scoring power of a scoring function is usually evaluated using Pearson’s correlation coefficient ( R ) which is computed as follows [ 3 ]:

Here, n is the total number of protein–ligand complexes in a set, x i (or y i ) is the values of the experimental (or predicted) binding affinity of the i th protein–ligand complex, (or ) is the average of the experimental (or predicted) values of the binding affinities.

The ranking power is frequently estimated using Spearman’s rank correlation coefficient ( ρ ) which is calculated as follows [ 3 , 17 ]:

Here, n is the total number of protein–ligand complexes for a given protein target and binding pocket, rx i (or ry i ) is the rank based on the values of the experimental (or predicted) binding affinity of the i th complex, (or ) is the average rank based on the values of the experimental (or predicted) binding affinities. In SET -4 (CASF-2016), there are 57 protein targets, and 5 ligands bind to the same binding pocket in each target [ 3 ]. The average Spearman’s rank correlation coefficient ( ρ ) for the 57 targets was employed to evaluate the ranking power of a scoring function.


## 3. RESULTS AND DISCUSSION

The flowchart of this work is shown in Fig. 1 . The steps include: 1 ) filtering the data from PDBbind v.2024 [ 10 , 11 ]; 2 ) assigning the atom types in the experimental structures using Open Babel 2.4.1 [ 13 ]; 3 ) calculating the distance-based variables; 4 ) training the pre-linear and neural network models based on the distance-based variables; 5 ) training the linear models based the pre-linear models as well as the mixed based on the neural network models using the distance-based variables with same power exponents; 6 ) training the final mixed models with different power exponents based on the mixed models.

Among the 13733 protein–ligand complexes, approximately 40% of them have multiple ligand molecules of the same type bound to different sites of the same protein structures ( Fig. 2A, 2B ). Most of the complexes have ≤5 ligand molecules of the same type bound to the same structures ( Fig. 2B ).


## 3.1. Performances of untrained models in affinity prediction

The untrained models use the presupposed mathematical expressions for the distance-based variables without training. The distance-based variables were derived from the experimental structures of the protein–ligand complexes. The simplest presupposed formations are the negative sum of distance-based variables, i.e ., for one specific ligand in the binding pocket and for multiple ligands of the same type ( d ij is the distance of the j th interacting atom pair for the i th kind of atom type pair, k is the power exponent, N l is the ligand number). The presupposed mathematical expressions are based on the formations of electrostatic and van der Waals energies (expressed as and ) [ 18 ].

When the power exponent ( k ) was equal to 1, the R (Pearson’s correlation coefficient) values for and are 0.457 vs . 0.461 in ALL (13733 complexes), 0.385 vs . 0.390 in SET -1 (6999 complexes), 0.591 vs . 0.594 in SET -2 (5215 complexes), 0.285 vs . 0.276 in SET -3 (1234 complexes), and 0.637 vs . 0.647 in SET -4 (285 complexes) ( Fig. 2C ). Overall, the results when considering multiple ligands of the same type is slightly better than those when only considering one specific ligand in the binding pocket, even though the advantage is very small.

The performance of the untrained models, i.e ., ( k = 1, 2, …, 18), are shown in Fig. 2D . When the power exponent ( k ) is ≤ 11, the R values decrease in all the sets with the power exponent increasing; the changes of the R values are not very apparent after the power exponent ( k ) is > 11. Especially, the performances in SET -2 and SET -4 are better than those in SET -1 and ALL when k ≤ 5. The reason is that the affinity data quality in SET -2 and SET -4 from PDBbind (v.2024) refined set better than those in SET -1 from the general set and ALL. The affinity data in SET -3 are from PDBbind (v.2024) refined+ set which composed of the complexes with metal-containing proteins and their ligands. The special protein–ligand interactions involving metal ions make the Pearson’s correlation coefficients ( R ) between the distance-based variables and the experimental affinities lower than those in other sets when k ≤ 5 ( Fig. 2D ).


## 3.2. Performances of the representative pre-linear and linear models in affinity prediction

Based on their performances, 18 representative pre-linear models were selected from all the 180,000 related models. The best representative pre-linear models are those with the power exponent ( k ) ≤ 3 ( Fig. 3A ). Overall, when k ≥ 4, the R values decrease with the power exponent increasing. After training, the performances of the pre-linear models in SET -2, SET -3 and SET -4 with high-quality affinity data are better than those in SET -1 with low-quality affinity data and those in ALL with both low-quality and high-quality affinity data ( Fig. 3A ). Comparing with the negative sum of the distance-based variables, the performances are improved using linear regression. The R values of the negative sum of the distance-based variables ( k = 1) and the pre-linear model 2 ( k = 2) are 0.461 vs . 0.615 in ALL, 0.390 vs . 0.558 in SET -1, 0.594 vs . 0.675 in SET -2, 0.276 vs . 0.659 in SET -3 and 0.647 vs . 0.746 in SET -4.

Furthermore, one representative linear model was selected from a large number of models trained based on the predicted values of the 18 representative pre-linear models. The R values of the pre-linear model 2 ( k = 2) and linear model are 0.615 vs . 0.653 in ALL, 0.558 vs . 0.613 in SET -1, 0.675 vs . 0.690 in SET -2, 0.659 vs . 0.701 in SET -3 and 0.746 vs . 0.739 in SET -4 ( Fig. 3B ). After integrating the predicted values of the representative pre-linear models, the overall performances are further improved.


## 3.3. Performances of the representative neural network and mixed models in affinity prediction

The performances of the distance-based variables were further investigated using artificial neural network. For each power exponent, there are 18 representative neural network models. The mean performances of these models are shown in Fig. 4A . The best performances of the models are achieved when the power exponent ( k ) ≤ 5. The R values decrease with the power exponent increasing when k > 5. The R values of the representative neural network model k 3-1 (3 is the power exponent, 1 is the model No.) are 0.704 in ALL, 0.675 in SET -1, 0.732 in SET -2, 0.726 in SET -3 and 0.800 in SET -4. The results are better than those of the pre-linear and linear models.

Then, the mixed models were trained using linear regression based on the predicted values of the representative neural network models. For each power exponent, one representative mixed model was selected from a large number of models. Overall, the performance of the mixed model ( Fig. 4B ) is better than those of the neural network models for each power exponent ( Fig. 4A ). The best mixed models are those with the power exponent ( k ) ≤ 5 ( Fig. 4B ). When k > 5, the R values decrease with the power exponent increasing. The decreasing of the R values in SET -3 are slower than those in other sets ( Fig. 2D , Fig. 3A , Fig. 4A, 4B ). The reason may be that the strengths of the metal-involving interactions decay more slowly with the power exponent increasing.

Finally, new mixed models (named as final mixed models) were trained using linear regression based on the predicted values of the 18 representative mixed models. One final mixed model was selected from a large number of models. As shown in Fig. 4C , the R values of the representative neural network model k 3-1, the mixed model ( k = 3) and the final mixed model are 0.704 vs . 0.790 vs . 0.818 in ALL, 0.675 vs . 0.772 vs . 0.803 in SET -1, 0.732 vs . 0.804 vs . 0.826 in SET -2, 0.726 vs . 0.821 vs . 0.858 in SET -3 and 0.800 vs . 0.858 vs . 0.893 in SET -4. The results are better than those of the pre-linear and linear models. The performances are improved at every stage and the related training are effective.


## 3.4. Comparison with other scoring functions for protein□ligand binding affinity prediction

The scoring power and ranking power of the linear model, neural network model k 3-1, mixed model 3 ( k = 3), final mixed model are compared with those of the previous scoring functions in SET -4 (CASF-2016) [ 3 ]. The previous scoring functions include X-Score [ 5 ], APBScore [ 4 ], AA-Score [ 19 ], Δ Lin_F9 XGB [ 8 ] and 8 linear models in our recent work [ 9 ]. The performances of APBScore, AA-Score, Δ Lin_F9 XGB are from the corresponding original works [ 4 , 8 , 19 ].

As shown in Fig. 5A, 5B , the scoring power of all the linear models are R > 0.63 and < 0.76 in CASF-2016; the ranking power of all the linear models are mean ρ > 0.57 and < 0.64 in CASF-2016. The performances of the machine learning-based scoring functions (Δ Lin_F9 XGB [ 8 ], neural network model k 3-1, mixed model 3 ( k = 3), final mixed model) are better than those of the linear models. The R and mean ρ values of Δ Lin_F9 XGB [ 8 ] and the final mixed model in CASF-2016 are 0.845 vs . 0.893 and 0.704 vs . 0.800, respectively.


## 3.5. Summary of the predictive powers of distance-based models for protein□ligand binding affinity prediction

In summary, the R (Pearson’s correlation coefficient) values of the untrained model (negative sum of the distance-based variables ( k = 1)), the pre-linear model 2 ( k = 2), the linear model, the neural network model k 3-1, the mixed model ( k = 3), and the final mixed model ( Table 1 ) are 0.461 → 0.615 → 0.653 → 0.704 → 0.790 → 0.818 in ALL; 0.390 → 0.558 → 0.613 → 0.675 → 0.772 → 0.803 in SET -1; 0.594 → 0.675→ 0.690 → 0.732 → 0.804 → 0.826 in SET -2; 0.276 → 0.659 → 0.701 → 0.726 → 0.821 → 0.858 in SET -3; 0.647 → 0.746 → 0.739 → 0.800 → 0.858 → 0.893 in SET -4. The ρ (Spearman’s rank correlation coefficient) values of these models in SET -4 (CASF-2016) ( Table 1 ) are 0.605 ± 0.423 → 0.577 ± 0.363 → 0.586 ± 0.359 → 0.668 ± 0.326 → 0.754 ± 0.256 → 0.800 ± 0.229.

According to the results of the pre-linear and linear models in the previous [ 9 ] and present works, it is expected that the R values in the set with high-quality affinity data would be > 0.700 if the pre-linear and linear models are trained using the same high-quality affinity data. There are 5500 complexes in the set composed of SET -2 and SET -4 with high-quality affinity data. These complexes involve 651 kinds of atom type pairs. Supplementary pre-linear and linear models were trained based on the high-quality affinity data. The training set composed of 3500 complexes was stochastically selected from SET -2 and SET -4. The R values of the supplementary linear model are 0.731 in SET -2, 0.802 in SET -4, and the ρ value is 0.677 ± 0.327 in SET -4 (CASF-2016) ( Supplementary Table S2 ). The performance of the supplementary linear model is comparable to or even better than those of some machine learning-based methods such as Δ vina RF 20 [ 6 ] ( R = 0.732 and ρ = 0.626 in CASF-2016) and Δ vina XGB [ 7 ] ( R = 0.796 and ρ = 0.647 in CASF-2016).

According to the results, the R values of the linear models based on the distance-based variables range from 0.700 to 0.800 in the set with high-quality affinity data; those of the neural network-based mixed models range from 0.800 to 0.900. Although there are no explicit formations for the neural network models, the high performances reflect that there may exist mathematical expressions which can predict the protein–ligand binding affinity with a high accuracy. It is hoped that the effective mathematical expressions will be figured out in the future. Lastly, the distance-based scoring functions will be applied in the binding pose selection for structural prediction of protein–ligand complex in a large set composed of experimental structures.


## 4. CONCLUSION

The nonbonded atom interactions are mostly related to distance such as electrostatic, van der Waals and hydrogen bonding interactions in the traditional force field. In this work, the predictive power of the distance-based variables in protein–ligand binding affinity were further explored and improved using linear regression and artificial neural network. The power exponents of distance were expanded to incorporate the existing multibody interactions implicitly into the scoring functions. The best models are superior to the sophisticated methods developed before. The findings of this work demonstrate the values of further exploring distance-based variables for improving the accuracy of protein–ligand binding affinity prediction.


## DATA AVAILABILITY STATEMENT

Supplementary File 1: the 859 kinds of atom type pairs; Supplementary File 2: the negative sums of the distance-based variables; Supplementary File 2: the negative sums of the distance-based variables; Supplementary File 3: the coefficients of the representative pre-linear models, linear model, mixed models and final mixed model; Supplementary File 4: the predicted values of all the representative models in the results section; Supplementary File 5: the performances of all the representative models in the results section.


## CONFLICT OF INTEREST

The authors declare that they have no conflict of interest.


## AUTHOR CONTRIBUTIONS

Conceptualization, Y.X.Y.; Research design: Y.X.Y.; Methodology, Y.X.Y.; Formal analysis, Y.X.Y., B.T.Z.; Investigation, Y.X.Y., B.T.Z.; Resources, B.T.Z.; Data curation, Y.X.Y.; Writing—original draft preparation, Y.X.Y., B.T.Z.; Writing—review and editing, Y.X.Y., B.T.Z.; Visualization, Y.X.Y.; Supervision, B.T.Z.; Project administration, B.T.Z.; Funding acquisition, B.T.Z.


## ACKNOWLEDGEMENTS

This work is supported by research grants from Shenzhen Key Laboratory of Steroid Drug Discovery and Development (No. ZDSYS20190902093417963) and Shenzhen Peacock Plan (No. KQTD2016053117035204).


## Funder Information Declared


## Footnotes

FOOTNOTES

1 Funding Support: This work was supported, in part, by research grants from Shenzhen Peacock Plan (No. KQTD2016053117035204), Shenzhen Key Laboratory of Steroid Drug Discovery and Development Research (No. ZDSYS20190902093417963), 2022 Stable Funding Support Program for Shenzhen Institutions of High Learning, and Longgang District Science and Technology Bureau’s Key Laboratory Program.