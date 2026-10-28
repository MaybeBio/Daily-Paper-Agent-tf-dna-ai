# PDA-Pred: Predicting the binding affinity of protein-DNA complexes using machine learning techniques and structural features


## Abstract
  Protein–DNA interactions play an important role in various biological processes such as gene expression, replication, and transcription. Understanding the important features that dictate the binding affinity of protein-DNA complexes and predicting their affinities is important for elucidating their recognition mechanisms. In this work, we have collected the experimental binding free energy (ΔG) for a set of 391 Protein-DNA complexes and derived several structure-based features such as interaction energy, contact potentials, volume and surface area of binding site residues, base step parameters of the DNA and contacts between different types of atoms. Our analysis on relationship between binding affinity and structural features revealed that the important factors mainly depend on the number of DNA strands as well as functional and structural classes of proteins. Specifically, binding site properties such as number of atom contacts between the DNA and protein, volume of protein binding sites and interaction-based features such as interaction energies and contact potentials are important to understand the binding affinity. Further, we developed multiple regression equations for predicting the binding affinity of protein-DNA complexes belonging to different structural and functional classes. Our method showed an average correlation and mean absolute error of 0.78 and 0.98 kcal/mol, respectively, between the experimental and predicted binding affinities on a jack-knife test. We have developed a webserver, PDA-PreD (Protein-DNA Binding affinity predictor), for predicting the affinity of protein-DNA complexes and it is freely available at https://web.iitm.ac.in/bioinfo2/pdapred/


## Introduction
  Protein-DNA interactions are essential components for all biological systems. These interactions control/regulate replication, repair, methylation, transcription and maintain the genome stability [1]. Numerous studies have been carried out to understand the structure–function relationship of protein-DNA complexes such as identification of DNA binding proteins, predicting the binding site residues, binding affinity of protein-DNA complexes and recognition mechanism of protein-nucleic acid complexes [2–7].

  The function of a protein-DNA complex is dictated by its binding affinity [8], which is quantitatively measured using dissociation constant (Kd) and binding free energy (ΔG). Understanding the affinity of protein-DNA interactions is important to study the effects on gene expressions, delineate the recognition mechanism based on interactions between protein and DNA and so on [9,10]. It has a broad spectrum of applications such as designing complexes with the desired affinities, developing prediction methods for the target sites, and quantitative simulation of gene regulation networks.

  Experimentally, binding affinities of protein-nucleic acid complexes are studied with electrophoretic mobility shift assay, filter binding assay, fluorescence spectroscopy, isothermal titration calorimetry, and surface plasmon resonance. These experimental data are compiled in ProNAB database, which contains more than 20,000 entries on binding affinities of protein-nucleic acid complexes and their mutants [11].

  Computationally, Protein-DNA binding affinities are studied through molecular dynamics simulations, statistical methods and machine learning techniques [12]. Barissi et al. [13] developed a physics-based machine learning method, DNAffinity, for predicting the binding affinity of transcription factors using the features derived from molecular dynamics stimulations. Rastogi et al. [10] proposed a method to quantify the sequence-affinity relationship by analyzing data from DNA sequencing experiments to comprehensively probe protein-DNA interactions. Yang et al. [14] developed a structure-based machine learning method, PredDBA, for predicting the binding affinity of protein-DNA complexes using a limited set of non-redundant complexes. Most of these methods are focused on a specific protein-DNA complex or a small set of data. In addition, the performance of available methods is not uniform in different structural and functional classes of protein-DNA complexes. On the other hand, the availability of protein-DNA binding affinity data in ProNAB database aid to develop reliable methods for binding affinity prediction. Understanding the binding affinity is also crucial for structure modeling of protein-DNA complexes [15].

  In this work, we constructed a non-redundant dataset for binding affinities of protein-DNA complexes with known three-dimensional structures. We classified the complexes based on their structural and functional classes, and derived features at three levels such as protein, DNA and protein-DNA interactions. These features are related with binding affinity using machine learning techniques. Our method showed a correlation and mean absolute error of 0.78 and 0.98 kcal/mol, in jack-knife test, respectively. The salient features of important structural parameters and performance of the method based on structural and functional classifications are discussed.


## Materials and methods

### Dataset
  We obtained the binding affinity of protein-DNA complexes from ProNAB database using the following criteria: (i) experimentally known binding affinity (ΔG), (ii) known 3D structure and (iii) non-redundant complex structures. ProNAB is a well-curated database with the highest number of protein-DNA binding affinity data. In some complexes, multiple binding affinity values were reported for the same protein-DNA complex, determined from different experimental methods or conditions such as pH, temperature, or buffer. In such cases, the affinity determined at physiological conditions (pH: 7; T: 298 K) was selected. The average ΔG was considered for the complexes where multiple data were reported in the literature. Using the above criteria, we obtained the binding affinity of 391 complexes. These complexes were grouped into different classes based on their structure (all-α: 113; all-β: 45; αβ: 181 and others: 36), function (Regulatory: 187 and others: 152) and percentage of binding site residues. The structural and functional classification were obtained from NDB [16].


### Development of features
  We derived a set of 117 features from protein-DNA complex structures. Features were grouped as (i) protein-based, (ii) DNA-based and (iii) interactions between protein and DNA.


### Protein-based features

### DNA-based features

### Features based on protein-DNA interactions

#### Interaction energy
  The interaction energy of protein-DNA complexes was calculated using the formula [21]  (1) Interactionenergy=∑[(Aijrij12−Bijrij6)+qiqjεrij]   Aij=εij*(Rij*)12,Bij=2εij*(Rij*)6,Rij*=(Ri*+Ri*),εij*=(εi*εj*)1/2

  The total interaction energy is calculated as the sum of van der Waals and electrostatic interaction energies. We also calculated the interaction energy contributed by the main chain and side chain atoms such as interaction energy due to main chain-main chain, main chain-side chain, side chain-main chain and side chain-side chain atoms of protein and DNA respectively.


#### Development of contact potentials
  We constructed a non-redundant dataset of 989 protein-DNA complexes with a sequence identity of ≤ 25% for developing atom–atom and amino acid residue-nucleotide contact potentials.


#### Atom propensity
  We computed the preference of the interacting atoms at the interface of a protein-DNA complex as described in Shanmugam et al. [22]. It is given by  (2) Propensity(i,j)=Nij/NPD(ni/np*nj/nd)  where, Nij is the number of contacts of type ‘i’ in protein and ‘j’ in DNA. ni and nj are total number of atoms of type i and j in protein and DNA, respectively. NPD, np and nd are the number of interacting atoms in the protein-DNA interface, number of atoms in proteins and number of atoms in DNA, respectively.


#### Residue propensity and contact potentials
  We have computed the propensity of amino acid-nucleotide contacts between protein and DNA using the equation [23]:  (3) Propensity(i,j)=Nij/∑NijTj/∑jTj  where Nij is the total number of contacts between base i and amino-acid residue j, and Tj is the total number of residue j in the whole data set. We have computed the propensities for the distance cut-off of 3.5 and 6 Å, which are widely used in the literature.

  The propensity has been converted into potentials using the equation [23]:  (4) Potential(i,j)=−RTln[propensity(i,j)]  where R is the gas constant and T is the temperature.


### Development of multiple regression models
  We have developed multiple regression equations to relate the binding affinity with different features developed from protein-DNA complexes. It is defined as,  (5) yi=β0+β1Xi1+β2Xi2+⋯+βpXip+ε  where, i is the number of observations, yi is the dependent variable (binding affinity), Xi are the structure-based parameters, β0, β1 … βp are regression coefficients and ε is the error term of the model.


### Procedure for feature selection
  We have carried out an exhaustive systematic search for all possible combinations of four features and selected the best combination based on correlation. Further, additional features were added until there was no increase in correlation (r) and the number of features reaches the square root of the number of data points. The selected features were used for the development of the final model. We have utilized the python machine learning package scikit-learn for constructing linear regression models [24]. A similar procedure was used to develop models for all the classes.


### Assessment of prediction performance
  The performance of the method was assessed using Pearson (r) and Spearman correlation coefficients, which explain the relationship between the experimental and predicted binding affinities, and mean absolute error (MAE) to examine the absolute difference between predicted and experimental affinity values using the SciPy package of python [25]. The model was further validated using a jack-knife test, where regression equations were developed using (n − 1) data points and used the same to predict the ΔG of the left-out complex, recursively.


## Results and discussion

### Analysis of binding affinity of protein-DNA complexes
  We have analyzed the binding affinity of 391 protein-DNA complexes and the distribution of ΔG values is shown in Fig. 1. We observed that ΔG ranges from −20 kcal/mol to −4 kcal/mol and 70% of the complexes have the ΔG of −11 to −7 kcal/mol. The complexes 1P47 (Zif268-DNA complex) and 4DTM (RB69 DNA Polymerase-DNA complex) have the highest and lowest affinities of −20.0 kcal/mol and −3.9 kcal/mol, respectively.

  Further analysis revealed that 67% of residues in Zif268 are interacting with DNA in 1P47 whereas only 20% are at the interface of 4DTM. In addition, 1P47 has twice the number of charged residues at the interface as well as more interface area compared to 4DTM. Fig. 2 shows the protein atoms, which are in contact with the DNA in both high (1P47) and low affinity (4DTM) complexes. Interestingly, 1p47 has more polar atoms and spanned with larger interface area compared to 4DTM, which has more non-polar residues and less interface area.

  We explored the binding affinities of protein-DNA complexes based on structural and functional classes and the results are presented in Supplementary Fig. S1. The analysis revealed that the range of ΔG for all-α, all-β and mixed class is −13.1 to −5.9 kcal/mol, −14.4 to −5.8 kcal/mol and −20.0 to −3.9 kcal/mol, respectively. Based on functional classification, the range is −20.0 to −4.7 kcal/mol for regulatory and −17.4 to −3.9 kcal/mol for other complexes.


### Atomic contact potentials
  We have computed the propensity of atomic contacts at the interface of protein-DNA complexes (Eqn. (2)).These propensity values were converted to contact potentials (Eqn. (4)) and the results are presented in Supplementary Table S1. We observed that N-O atom pairs are the most preferred ones with the lowest energy of −0.97 kcal/mol, which are involved in electrostatic interactions. Further, contacts between C and O atoms between protein and DNA, occur more frequently at the interface of the protein-DNA complexes and are energetically favorable with a contact potential of −0.28 kcal/mol. Interestingly, similar results are also reported for protein-carbohydrate complexes, with preferred CO contacts between proteins and carbohydrates [22].


### Amino acid-nucleotide contact potentials
  We have computed the preference of amino acid-nucleotide contacts between protein and DNA and the results obtained with a distance cutoff of 3.5 Å are presented in Supplementary Table S2. We observed that all the four bases (A, T, G, C) prefer to interact with the positive charged amino acids Arg (20–25%) and Lys (14–16%), along with higher preference for Arg compared to Lys, which is similar to the observations reported in [23]. Further, Cytosine and Adenine tend to prefer most of the polar and charged amino acids such as Arg, Lys, Tyr, Ser, Thr and Asn at the interface. In addition, Thymine occurred most frequently at the protein-DNA interface, which agrees well with the previous result reported by Meysman et al. [26]. In addition, Cys, Asp, Met are less favored at the interfaces of protein-DNA complexes.

  We calculated amino acid-base propensities from the number of contacts, and further obtained the contact potentials, and the results are presented in the Table 1. Overall, Thymine-Trp interaction is energetically favorable at the interface with −2.25 kcal/mol, showing the importance of π-π interactions [27]. Further, Trp-Thymine has the strongest interaction among other aromatic amino acids Phe and Tyr. Frequently occurring amino acids Arg and Lys have the interaction energy of −0.93 and −0.91 kcal/mol, respectively with Thymine.


### Relationship between structure-based features and the binding affinity
  We have related the parameters derived from structures of proteins, DNA and protein-DNA complexes (Materials and methods) with binding affinities to explore the relationship between them. Interestingly, although the direct correlation between each property and binding affinity is poor, we observed an increase in specific properties with different ranges of binding affinities.

  The features related to binding interface of protein-DNA complexes such as contact potentials and total number of polar residues directly relate with protein-DNA binding affinity. Fig. 3 shows the data obtained with specific parameters such as (i) contact potentials at 3.5 Å (Fig. 3a) and (ii) number of polar residues in the interface of protein-DNA complexes (Fig. 3b). We observed that the average contact potentials (3.5 Å) of the complexes decreases from −31.95 to −8.22 kcal/mol with the decrease in the affinity range of the complex from −20 to −16 kcal/mol and −8 to −4 kcal/mol (Fig. 3a). For the complexes with the binding affinity of −20 to −16 kcal/mol and −8 to −4 kcal/mol, the average number of polar residues are 82 and 43 (Fig. 3b), respectively. Inspection of results revealed that the average number of polar residues and contact potential decreases approximately two and four folds with the decrease in affinity in the range of −20 to −16 kcal/mol to −8 to −4 kcal/mol.


### Prediction of binding affinity

#### Single property correlation
  We related the binding affinity of 391 protein-DNA complexes with each feature derived from protein-DNA complexes and obtained a maximum correlation (r) of 0.21. Earlier studies showed that the classification of protein–protein/protein-nucleic acid complexes based on structure and function improved the correlation for understanding the relationship between sequence/structural features with binding affinity [14,28–30]. Hence, we classified the dataset based on functional and structural classes of proteins as well as number of binding site residues with the condition that sufficient number of data are present in each class. Table 2 shows the correlation between structural features and binding affinity of protein-DNA complexes belonging to of different classes.

  N: number of complexes; αβ includes α + β and α/β classes of proteins.

  The classification of protein-DNA complexes based on structure, function and percentage of binding site residues improved the correlation in the range of 0.35–0.75. In single-stranded DNA, we obtained a maximum correlation of 0.75 between energy due to side chain hydrogen bonds and binding affinity (Fig. 4). Interestingly, previous study showed that hydrogen bonds at the interface are the major contributors to protein–ssDNA binding affinity [31]. In addition, electrostatic interactions, which are favored by the highly negatively charged surface of DNA with positive charged amino acid residues also showed a correlation of 0.61 in the αβ-regulatory with high percentage of binding site residues. In all-β-regulatory complexes contact potentials showed the highest correlation of 0.58.


#### Multiple regression technique for predicting the binding affinity
  We have utilized multiple regression technique to combine the features for predicting the binding affinity and the results are presented in Table 3. The selected features and regression equations obtained for each class are presented in Supplementary Table S3 and Supplementary Table S4, respectively. We observed that the correlation lies in the range of 0.77 to 0.98 with MAE in the range of 0.16 to 1.27 kcal/mol in all the sub classes in the training set. Further, on evaluating the model with jack-knife test, we obtained a correlation in the range of 0.64 to 0.96 with MAE of 0.24 to 1.53 kcal/mol. Overall, our method could relate the binding affinity of 391 complexes with a correlation of 0.86 and MAE of 0.76 kcal/mol on training, and a correlation of 0.78 and MAE of 0.98 kcal/mol, in jack-knife test. The relationship between experimental and predicted binding affinities are shown in Fig. 5, and for all the individual classes of protein-DNA complexes are provided in Supplementary Fig. S2. Further, we have examined the performance using 10-fold cross validation and the results are presented in Supplementary Table S5. Our method showed an average correlation and MAE of 0.75 and 1.02 kcal/mol, respectively.


### Analysis of features important for binding affinity of protein-DNA complexes
  The features selected in each class of protein-DNA complexes to predict the binding affinity are presented in Supplementary Table S3. Further, we grouped these features based on interaction energy, structural features, percentage of secondary structures, accessible surface area and base step parameters, and the results are shown in Table 4 under different categories such as protein-based, DNA-based and interaction-based. We observed that interaction-based features are important in most of the models (except all-α-regulatory-high and αβ-regulatory-low). Single-stranded DNA class mainly depends on interaction-based features whereas DNA-based features are dominant in αβ-regulatory-low class.

  We observed that base step parameters and accessible surface area are important to predict the binding affinity in most of the classes of protein-DNA complexes. In addition, atomic contacts and contact potentials are identified in mixed class proteins (αβ). Interestingly, non-regulatory proteins belonging to mixed class is dominated with interaction energies. This analysis reveals the importance of specific features common to several classes of protein-DNA complexes. Detailed analysis of each class is provided in Supplementary information.


### Comparison of our method with PreDBA
  Yang et al. [14] developed a machine-based learning model, PreDBA, to predict the protein-DNA binding affinity, which was trained on 100 non-redundant complexes. To compare our predictions with PreDBA, we tested the model developed in Yang et al. [14] with our dataset. We excluded the redundant protein-DNA complexes that are used in their training dataset and obtained a test dataset of 225 complexes. PreDBA provides the binding affinity for each chain of the protein against each strand of DNA. Hence, protein-DNA complexes with more than one protein or DNA chain, we computed the affinity for all the possible combinations of DNA and protein pairs and considered the closest prediction to the experimental binding affinity to estimate the correlation/MAE. Fig. 6 shows the relationship between experimental and predicted binding affinities obtained with PreDBA (Fig. 6a) and in the present work (Fig. 6b).

  We observed that our method predicted with an average correlation of 0.76 and MAE of 0.98 kcal/mol, while average correlation of PreDBA was 0.32 with MAE of 1.86 kcal/mol. The improved performance in our method is mainly due to the classification of complexes and the availability of experimental affinity for a large number of protein-DNA complexes in ProNAB database [11]. Supplementary Table S6 shows the results for each class of protein-DNA complexes based on structure and function.


### Prediction on the web
  We have developed a web server, PDA-PreD, for predicting the binding affinity of protein–DNA complexes. It takes the protein–DNA complex structure in PDB format or the PDB ID as input. The output includes the predicted value of binding affinity ΔG and the dissociation constant (Kd) computed using the equation, ΔG = -RT ln(Kd). The web server is freely accessible at https://web.iitm.ac.in/bioinfo2/pdapred/.


### Case study with DNA Polymerase I -DNA complex
  We have explored the binding affinity of DNA Polymerase I-DNA complex (2HHU) using structural features identified in this work. It belongs to αβ non-regulatory class with binding site residues less than the average. It has the experimental binding affinity of −4.03 kcal/mol and our model predicted the affinity as −4.33 kcal/mol, which shows a good agreement. Fig. 7 shows the interactions between the sugar-phosphate backbone of the DNA and the protein. We analyzed the individual features used in the model to predict the binding affinity of the complex. Our analysis showed that it has high percentage of CO atom contacts with preferred atomic contact potentials, backbone hydrogen bond energy of −10.6 kcal/mol and favorable van der Waals and total interaction energies of −24.5 kcal/mol and −162.3 kcal/mol, respectively. The combination of these parameters could correctly predict the binding affinity of the complex with a deviation of 0.3 kcal/mol.


## Conclusions
  We have systematically analyzed the relationship between structural features of protein, DNA as well as interaction energy, and binding affinity of protein-DNA complexes. Our analysis showed that interaction energy, contact potential, number of interface atoms, ASA of protein and DNA, surface area and volume of the protein, and DNA base step parameters are important to understand the binding affinity. Further, classification of complexes based on structure, function and binding site residues are important to account the binding affinity. We have developed multiple regression-based methods for predicting the binding affinities of the protein-DNA complexes and our method showed an average correlation of 0.78 and MAE of 0.98 in a jack-knife test, which are better than other existing methods in the literature. We have developed a web server for predicting the binding affinity and it will be useful for large scale analysis and developing strategies for therapeutic targets.


## Supplementary Material

## Data availability
  Data will be made available on request.


## Acknowledgements
  We acknowledge the Indian Institute of Technology Madras and Purdue University for computational facilities. We thank all the members from Protein Bioinformatics Lab for providing valuable suggestions and Rahul Nikam for helping with the web server. Ms. Divya Sharma is acknowledged for critical reading of the manuscript. The work is partially supported by the Science and Engineering Research Board (SERB), Ministry of Science and Technology, Government of India to MMG (No. CRG/2020/000314) and Overseas Visiting Doctoral Fellowship program (OVDF 2022) to HK. DK acknowledges support from the National Institutes of Health (R01GM123055, R01GM133840, 3R01GM133840-02S1) and the National Science Foundation (DMS2151678, DBI2003635, CMMI1825941, DBI2146026, IIS2211598, and MCB1925643) of USA.