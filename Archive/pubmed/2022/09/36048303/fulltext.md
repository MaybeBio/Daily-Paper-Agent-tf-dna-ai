# Homology Modeling of Forkhead Box Protein C2: Identification of potential inhibitors using ligand and structure based virtual screening


## Abstract
  Overexpression of Forkhead box protein C2 (FOXC2) has been associated with different types of carcinomas. FOXC2 plays an important role in the initiation and maintenance of the epithelial-mesenchymal transition (EMT) process, which is essential for the development of higher-grade tumors with enhanced ability of metastasis. Thus, FOXC2 has become a therapeutic target for the development of anticancer drugs. MC-1-F2, the only identified experimental inhibitor of FOXC2, interacts with the full length of FOXC2. However, only the DNA binding domain (DBD) of FOXC2 has resolved crystal structure. In this work a three-dimensional (3D) structure of the full-length FOXC2 using homology modeling was developed and used for structure-based drug design (SBDD). The quality of this 3D model of full-length FOXC2 was evaluated using MolProbity, ERRAT, and ProSA modules. Molecular dynamics simulation was also carried out to verify its stability. Ligand-based drug design (LBDD) was carried out to identify similar analogs for MC-1-F2 against 15 million compounds from ChEMBL and ZINC databases. 792 molecules were retrieved from this similarity search. De novo structure-based drug design was performed against the full-length 3D structure of FOXC2 through homology modeling to identify novel inhibitors. Combination of LBDD and SBDD helped in gaining a better insight into the binding of MC-1-F2 and its analogues against the full length of the FOXC2. The binding free energy of the top hits were further investigated using molecular dynamics simulations and MM/GBSA calculations to result in eight promising hits as lead compounds targeting FOXC2.


## Introduction
  The epithelial-mesenchymal transition (EMT) is a biological process in which the epithelial cells undergo biochemical changes to become mesenchymal cells [1], [2]. EMT is essential for cancer metastasis through the generation of more invasive cells with higher migration capacity and increased resistance to apoptosis with stem cells like features [2], [3]. The generated cancer stem cells (CSCs) from the EMT process have the ability of self-renewal leading to the formation of secondary tumors [2], [4], [5]. Several transcription factors are activated to initiate the EMT process including zinc finger E-box binding homeobox 1 (ZEB1), Snail, Slug, Twist, Goosecoid, and Forkhead Box Protein C2 (FOXC2). [6]–[9]

  FOXC2 is a member of FOX family of transcription factors, that are characterized by the presence of conserved winged-helix (forkhead) DNA-binding domain (DBD). This conserved DBD consists of three α-helices, three β-sheets and two less conserved winged loops. The main region for DNA recognition among these secondary structures is located near the third helix H3. [10]–[15]. FOX family of transcription factors is divided into 19 subgroups, including the FOXC subgroup [16]. FOXC subfamily consists of two proteins: FOXC1 and FOXC2. Both proteins are involved in different developmental processes [17]. Mutations in FOXC2 gene were found to be associated with different genetic diseases such as Lymphoedema distichiasis syndrome (LDS) [18]. Overexpression of FOXC2 was found to be associated with breast and hepatocellular carcinoma through initiating and maintaining EMT [19]–[21].

  Indirect inhibition of FOXC2 resulted in attenuating the cancer metastasis by reversing the effects of EMT, making FOXC2 an appropriate drug target for the treatment of metastatic cancer [22]–[24]. This drives the work of Castaneda et al. to develop the first small molecule inhibiting FOXC2 [25]. One-bead-one-compound (OBOC) library of α-helix mimetics was utilized to find a proper inhibitor for the full-length structure of FOXC2. OBOC library was used because of the presence of H3 domain, in which an α helix is essential in the functional role of FOXC2. Screening of nearly 20,400 compounds of OBOC library was carried out followed by elimination of false positive to find the top 16 hits and further filtration of false positive [25]. The most probable hit identified was MC-1-F2 (Figure 1). MC-1-F2 is the first inhibitor of FOXC2 in vitro. MC-1-F2 was found to induce apoptosis and to stop colony forming in the cell lines with high expression of FOXC2. This implies that MC-1-F2 alters the EMT process and the metastasis of the cancer by definite binding to FOXC2 [25].

  The dissociation constant value (Kd) for the binding of MC-1-F2 to the DBD of FOXC2 was higher than 100μM, this indicates that the binding was very weak and not enough for the inhibitor to bind to the protein. This insinuates that other domains of the protein are involved in the effective binding of the inhibitor [25]. In other words, MC-1-F2 was found to bind to the full-length structure of FOXC2 not only the DBD. The binding between MC-1-F2 and FOXC2 involved both the main scaffold of MC-1-F2 as well as the side chains [25].

  MC-1-F2 violates the four rules of Lipinski’s rule of five, which decreases its probability to be an active drug because of the poor physicochemical properties. Therefore, in this work we applied both ligand-based drug design and structure-based drug design computational methods to develop novel compounds with improved physicochemical properties as potent inhibitors for FOXC2.


## Methodology

### Ligand-based drug design (LBDD)
  Multi-fingerprint browser based on city-block distance using daylight-type substructure fingerprint (sFP) was utilized to search for similar analogs to MC-1-F2 in more than 13 million structures of commercially available compounds in ZINC database and more than 2 million compounds in ChEMBL database [26]–[30]. sFP is a binary fingerprint represents the molecule in the form of 0 and 1 to indicate the absence and the presence of certain substructure, respectively [31], [32].

  sFP is used to calculate the city-block distance (CBD) through following equation to measure the similarity between molecules A and B, represented as two vectors in K dimensional space.

  This search resulted in retrieving nearly 1,000 compounds from the ZINC database and nearly 10,000 compounds from the ChEMBL database.

  Lipinski’s rule of five was applied on the retrieved similar analogs, followed by removal of compounds containing toxicity alerts as well as removal of pan-assay interference compounds (PAINS) using KNIME [33] to get a total of 5,414 compounds. This filtration was carried out to ensure that the molecules have desirable physicochemical properties as drug molecules.

  A molecular substructure miner, MoSS, using pair-wise maximum common substructure similarity (MCSS) metric, implemented in KNIME was used for the purpose of reliable similarity search [34]. MoSS focuses on finding the frequent substructures and the discriminative fragments in a database of molecules. Similarity search based on city-block distance implemented in the multi-fingerprint browser is fast, thus suitable to screen large databases. MoSS MCSS molecule similarity was applied as an additional similarity metric on the 5,414 compounds to ensure the close proximity of the retrieved compounds to MC-1-F2. This results in reduction of the 5,414 compounds to 792 compounds. Furthermore, these 792 compounds were clustered into five different groups based on K-Medioids using the values generated by MoSS MCSS molecule similarity [33]. Clustering of the molecules was carried out to identify common functional groups within the retrieved molecules similar to MC-1-F2.


### Homology modeling of the full-length structure of FOXC2
  The available crystal structures of FOXC2 in Protein Data Bank (PDB) only contain the DBD and not the full length of the protein. MC-1-F2, the only identified experimental inhibitor for FOXC2, interacts with other domains of FOXC2 in addition to the DBD. Thus, it is necessary to develop a three-dimensional (3D) structure of the full-length of FOXC2 using homology modeling. The target 3D structure of FOXC2 consists of 501 residues, this represented the full length of the FOXC2 protein including the N-terminal, C-terminal, and DBD.

  I-TASSER, Threading ASSEmbly Refinement, server was used to build 3D structures of full-length FOXC2 (UniprotKB Q99958) [35]–[37]. I-TASSER depends on enhanced Profile-Profile threading Alignment (PPA), where the target sequence is aligned with protein structures in the PDB whose pair-wise sequence identity with the target sequence is more than 70%. This alignment is carried out to search for similar protein folds depending on the sequence using PPA method. The identified folds are excised from the threading aligned regions. On the other hand, the unaligned parts of the sequence, representing the loops, are modeled using ab-initio modeling [38]. The final structure is an average of the coordinates of all the clustered structures generated by replica-exchange Monte Carlo simulations [39], which is carried out to explore the conformational space.

  The developed 3D model for the full-length of FOXC2 protein was associated with a Z-score of 3.93. Z-score measures the difference between the native raw fold of a protein and the average score of misfolded structures divided by the standard deviation. The normalized Z-score assess the quality of the model as well as the alignment [40]. 1VTN is a forkhead protein used as template sequence for the generation of the homology model of FOXC2.The normalized Z-score of 3.93, larger than 1, indicates a good alignment of FOXC2 protein sequence with the sequence of 1VTN protein.

  I-TASSER uses the confidence score (C-score) to evaluate the quality of the model.

  M is the multiplicity of the clustered structures; Mtot is the total number of the I-TASSER structure decoys; ⟨RMSD⟩ is the average root mean square deviation (RMSD); Z(i) is the highest Z-score of the templates used in the PPA threading and Z0(i) is a Z-score cutoff distinguishing between good and bad templates [35]–[37].

  The C-score, with range between −5 and 2, was 1.1 for the final model, suggesting high quality of the homology model. Furthermore, Molprobity, ERRAT, and ProSA modules [41]–[44] were employed to validate the quality of the model.


### Molecular dynamics simulations for the homology model of FOXC2
  Molecular dynamics (MD) simulation was carried out for the homology model. The protein was prepared for the MD simulation using CHARMM program package version 41b1 [45]. The protein was solvated in a cubic box using TIP3P water model. [46] Counter ions Cl− and Na+ were added to neutralize the charges and maintain ionic strength of the system. The model was minimized followed by heating from 0 K to 300 K. The prepared system was equilibrated for 10 ns as isothermal-isobaric ensemble (NPT) using OpenMM [47] running on GPU. A production 100 ns simulations was carried out as canonical ensemble (NVT). Electrostatic interactions were computed using Particle mesh Ewald (PME) [48] method. Hydrogen covalent bonds were constrained during the simulation using SHAKE method [48].

  Root-mean-square deviation (RMSD) was calculated using MdTraj package [49], where the first frame of the simulation was the reference structure. RMSD was used to evaluate the stability of the generated model and the convergence of the simulation, and calculated as  (3) RMSD=1N∑i=1N(Uri−riref)2  where N is the number of atoms, ri is the coordinate of atom i, riref is the coordinate of atom i in the reference structure, and U is the best-fit rotational matrix to align a given structure onto the reference structure.


### Identification of binding site of the full-length homology model of FOXC2
  The binding site of the full-length homology model of FOXC2 was determined using MakeReceptor module implemented in the OpenEye scientific package. [50]–[52] MakeReceptor module identifies the active site by determining the target mask and by generating negative image for the active site. Target mask is the subset of the protein suitable for docking, while negative image is the shape of the active site where ligands interact with the active site without clashes. [50]–[52] MC-1-F2 was docked against the three binding sites detected by the MakeReceptor module. The binding site associated with the highest score upon docking of MC-1-F2 was chosen to be the active site. The docking score of MC-1-F2 against the identified active site was based on four factors: shape complementarity of −13 kcal/mol, hydrogen bond component of −2 kcal/mol, protein desolvation of 6 kcal/mol, and ligand desolvation of 8 kcal/mol. Besides the shape complementarity component, the ligand desolvation attributes immensely to the final docking score due to the large size of MC-1-F2.

  Furthermore, the binding of MC-1-F2 against both the full length model generated by I-TASSER [35]–[37] and the crystal structure of DBD of FOXC2 (PDB ID: 6O3T) was investigated using BindScope server, a convolutional neural network to predict the binding probability of compounds. [53]–[55] This was performed to validate the generated model by I-TASSER [35]–[37]. The binding probability of MC-1-F2 to the 3D structure including the full-length of the protein (the generated homology model) is expected to be higher than the PDB structure of DBD only.


### Screening through molecular docking
  The 792 compounds obtained from the similarity search were screened using molecular docking against the identified active site of the full-length FOXC2 3D structure. Conformational search was carried out for these 792 compounds using OMEGA2 package [56] to determine the most probable conformation for each compound. OMEGA is a knowledge-based method efficient in producing bioactive conformations of the molecular structures with high-quality. OMEGA method takes into account the effect of ionization, tautomerism, and isomerism by generating different conformers for the same molecule based on energetic and geometric criteria. This is achieved by combining a library of fragments along the sigma bond. [56]

  FRED docking package provided by OpenEye Scientific Software Inc. was used to dock these compounds against the target active site [50], [51]. In FRED docking method, systematic examination is carried out for all the possible docking poses. The top hits are determined using Chemgauss4 scoring function, which depends on shape complementarity. [50], [51] The top 15 hits based on the docking score were further validated by calculating the binding probability using BindScope server. [53]–[55] BindScope server was employed as a further filtration step in the virtual screening process, as it was found to outperform the classical virtual screening methods that depends on simple docking scoring functions[57].


### De novo structure-based design based (SBDD) on the full-length model
  Complimentary to the above virtual screening studies to find potent inhibitors from the existing databases, de novo SBDD using LIGANN server [58]–[60] was performed based on the active site of the 3D structure of the full-length FOXC2 identified by MakeReceptor module. LIGANN is a generative neural network (GNN) produces ligands’ shapes complementary to the protein shape, represented as generative adversarial network. The ligand shape is decoded into SMILES strings representing the ligands generated from the design (SBDD). Using generative neural networks in the de novo structure-based design bypasses the challenges faced by the conventional structure-based compound design. This is achieved by including the 3D information of the compounds’ binding poses during the design process. This was found to top the Fragment-based Drug Design (FBDD) by 200% when the size of the linker was limited to 5 atoms. [58]–[60]

  Total of 79 new compounds were generated and screened through molecular docking using FRED [49], [50] against the identified active site of the full-length FOXC2. Similarly, the top 15 hits with respect to the docking score were further validated by calculating the binding probability using BindScope server. [53]–[55]


### MM/GBSA calculation
  The stability of the binding of the top ten hits to the developed full-length mode of FOXC2 was assessed using molecular dynamics (MD) simulations. Amber ff14SB forcefield implemented in Amber package was used for the protein [61]–[63]. The ligands were parameterized using General AMBER force field 2 (GAFF2) implemented in AnteChamber module [64], [65].

  The complexes of the top ten hits were solvated in a cubic water box using TIP3P water model, followed by neutralizing the system using Na+ and Cl− counter ions. The system was then minimized by steepest descent algorithm, then equilibrated for 50 picosecond (ps) as isothermal-isobaric ensemble (NPT) at 300K. 50 nanosecond (ns) simulations for the top ten hits were carried out in the form of canonical ensemble (NVT). Electrostatics interactions were accounted for using particle-mesh Ewald method, while the hydrogen bonds were estimated using SHAKE algorithm[66]. The stability of the binding was assessed using RMSD.

  The binding free energy of the protein-ligand complexes were calculated using Molecular Mechanics/Generalized Born Surface Area (MM/GBSA) algorithm implemented in AmberTools20 [67].


## Results

### Ligand-based drug design: Similarity search of MC-1-F2
  Similarity search for analogues to MC-1-F2 compound was performed against 15 million commercially available compounds in ChEMBL and ZINC databases using multi-fingerprint browser. [26]–[30] This search resulted in nearly 11, 000 compounds. Additional filtration step was employed utilizing MoSS MCSS molecule similarity implemented in KNIME to ensure the proximity of the similar analogues retrieved from the initial similarity search. [33] The output molecules from this similarity search were further filtered by removing the PAINS and the toxicity alerts and applying Lipinski’s rule of five. This extensive filtration resulted in 792 compounds.

  K-Medoids clustering based on MoSS MCSS molecule similarity was applied on the 792 compounds identified from the similarity searching resulted in five groups. Group 1 contained 209 molecules, group 2 contained 88 molecules, group 3 contained 75 molecules, group 4 contained 308 molecules, and group 5 contained 112 molecules. Each group is represented by a representative molecule illustrated in Figure 2. These five representative molecules constitute the cluster centers used in dividing the 792 molecules obtained from the similarity search into five groups using the K-Medoids clustering. Group 1 contained the largest number of molecules and was the most similar group to MC-1-F2 based on MoSS MCSS molecule similarity. 1,3,5-Triazine-2,4-diamine was found to be the common functional group in the representative structures of all five groups. The role of this functional group in the binding of MC-1-F2 and the similar analogues to FOXC2 protein should be further investigated.


### Quality of the generated 3D structure of the full-length FOXC2
  The developed full-length model of FOXC2, 501 residues, generated by I-TASSER [35]–[37] showed 70% pair-wise sequence identity to 1VTN target sequence. In addition, the Z-score of the developed model is 3.93 reflecting the good quality of the model.

  The quality of the developed model was assessed using MolProbity. [35] 85.4% of the residues lie within favorable area in the Ramachandran plot. Only 3.6% of the residues, 17 residues out of 501 residues, were identified to be outliers of the Ramachandran plot (Figure 3). Moreover, there was no residues forming unfavorable bonds or violating the acceptable tetrahedral geometry or the chiral volume of the protein structure. This supports that the developed structure of the full-length FOXC2 protein has good quality and should be suitable for the consequent SBDD studies.

  The homology model of the full-length of the protein was also validated using ERRAT server [36] to check the quality of the model by calculating the non-bonded interactions between different atom types. The model is considered acceptable if the overall quality is higher than 50%. In addition, the higher the overall quality score the more reliable the homology model. The overall quality of the first 300 residues (0–305) of the model is 81.8% (Figure 4a). While the overall quality of the last 200 residues (306–501) of the protein is 78.9% (Figure 4b). With the weighted average of the model’s quality surpasses 81.2%, the developed model of the full-length of FOXC2 protein is considered a good model. Moreover, less than 3% of the residues exceeded the 99% error value with respect to the non-bonded interaction. This further supports and validates the quality of the generated model.

  ProSA module [43], [44] was employed to evaluate the quality of the model by calculating the energy of the residues as well as the Z-score of the overall structure. PRoSA Z-score indicates the statistical significance of the model by comparing its score to the knowledge-based scores of proteins of similar size with the same folds. [43], [44] The quality of the protein folds was evaluated based on the energy of the amino acid residues. The lower the energy of the residues the better the model. The energy of the residues of the developed model was associated with energy ranging from −1 kcal/mol to 1 kcal/mol (Figure 5a). This indicates the low energy of the protein folds when compared to random conformers of similar size. Z-score measures the deviation of the total energy of the model with respect to 3D structures generated by X-ray and NMR with similar sizes. The model was associated with Z-score of −4.29 (Figure 5b). This reflects that the generated model of the full-length of FOXC2 is stable with low energy and has quality well comparable with proteins with similar sizes from PDB.


### Homology modeling and molecular dynamics simulations
  RMSD was calculated over the time-course of 100 ns molecular dynamics simulation to check the stability of the generated model as well as the convergence of the simulation. RMSD showed that the simulation was converged after the first 10 ns. High rise in the RMSD value from 0 nm to 1.15 nm was observed in the first 10 ns. However, the RMSD remains around 0.05 nm for the rest of the simulations (Figure 6), indicating the stability of the generated 3D model for the full-length FOXC2.

  Root mean square fluctuation (RMSF) was calculated for the full-length model of FOXC2 after the first 10 ns. The first frame was used as the reference structure. The fluctuations of the RMSF values are less than 0.1 nm for all the residues, except for the first ten residues that show high fluctuations of nearly 0.25 nm to 0.5 nm. This indicates the high flexibility of the N-terminal. RMSF shows that model is stable as indicated by the limited fluctuation profile of the residue over the time-course of the simulation (Figure 7).


### Identification of the generated model active site
  The interaction of MC-1-F2 was investigated with the three detected sites from MakeReceptor module. [50]–[52] The binding site associated with the highest score upon docking of MC-1-F2 was chosen to be the active site. The interaction of MC-1-F2 with FOXC2 involved not only the DBD of the protein, but also part of the C-terminal. This agrees with the experimental data that MC-1-F2 inhibitor binds to the full length of the protein. [25] The binding mode of MC-1-F2 upon docking involves important residues ASN 449, LEU 459, SER 476, TYR 481, THR 484, and TYR 488. This may be due to the fact that the C-terminal of the protein contained the extra detected secondary structures in the full-length FOXC2 compared to DBD, providing a stable binding site (Figure 8). Using BindScope server, the binding probability of MC-1-F2 to the full-length protein was compared to that of the DBD. This was implied to validate and ensure the better binding of MC-1-F2 to the identified active site compared to the DBD. it was found that the binding probability of MC-1-F2 against the full-length model was higher than the DBD (Table 1). This agrees with the experimental data that MC-1-F2 interacts with not only the DBD but the full length of FOXC2. [25]


### Screening using docking method against the determined active site (LBDD)
  Docking of the 792 compounds, obtained from similarity search for analogues to MC-1-F2 (LBDD), against the determined active site of the full-length FOXC2 using FRED. [50], [51] The docking scores of the top 15 molecules have range from −13 kcal/mol to −6 kcal/mol (Table S1). The docking scores of the similar analogues are higher than MC-1-F2. This may be attributed to the smaller size of the analogues compared to MC-1-F2.

  The top 15 molecules based on FRED docking scores contain the main scaffold of MC-1-F2 inhibitor, 1,3,5-Triazine-2,4-diamine functional group in particular. The top hits were further evaluated using BindScope server [53]–[55] to calculate the binding probability and to identify the most probable hits. The compounds with binding probability equal to or higher than 0.85 were selected. This additional filtration using binding probability resulted in choosing only 3 compounds from the top 15 hits. The selected 3 compounds are illustrated in Figure 9.


### De novo design of inhibitors against full-length FOXC2 (SBDD)
  Docking of the 79 molecules, obtained from de novo structure based design using LIGANN (SBDD) [58]–[60], against the detected active site of the full-length FOXC2 was carried out using FRED. [50], [51] Compounds generated from SBDD have higher docking scores compared to compounds generated from LBDD. The docking score of the top 15 hits generated from SBDD ranges from −17 kcal/mol to −11 kcal/mol (Table S2). The higher docking scores could be attributed to the smaller and the simpler compounds obtained from de novo SBDD compared to the compounds obtained from LBDD. The compounds with binding probability equal to or higher than 0.85 as evaluated using BindScope server [53]–[55] were selected. This additional filtration resulted in choosing 7 compounds from the top 15 hits. The selected 7 compounds, illustrated in Figure 9, were found to lack the 1,3,5-Triazine-2,4-diamine moiety which was an essential functional group in the hits from the similarity search.

  In summary, the top 10 hits obtained from this filtration included 3 compounds from the similarity search (LBDD) and 7 compounds from de novo structure-based design (SBDD). Some of the compounds, especially those obtained from LBDD were structurally similar to MC-1-F2 (Figure 1).

  Since the main problem with the experimentally identified inhibitor MC-1-F2 was the unfavorable physicochemical properties which resulted in difficulty purifying the compound using HPLC, the physicochemical properties of the top ten hits were inspected. The physicochemical properties of the compounds generated from the similarity search were found to have higher polar surface area (PSA) compared to those generated from de novo structure-based design (Table 2). The top ten hits, obtained from augmenting both LBDD and SBDD, have larger number of hydrogen bond acceptor moieties than hydrogen bond donor moieties. This was found to be also a feature in the experimentally identified inhibitor MC-1-F2. In addition, the top ten hits follow Veber’s rule [68] not only Lipinski’s rule of five, where the PSA for all the top ten hits is less than 140 Å2 unlike MC-1-F2 (Table 2). The physicochemical properties of the top ten hits are favorable compared to MC-1-F2, that could provide better bioavailability and higher chance of being an efficient drug, as well as easier synthesis process.

  The binding mode of the top ten hits were investigated in comparison to MC-1-F2. All the top ten hits and MC-1-F2 shared interactions with four specific residues, ASN449, LEU459, SER476 and THR484, in the identified active site (Figure 10).

  The stability of the identified binding mode was further evaluated using molecular dynamics simulations of the top ten hits. The low deviation of the RMSD values reflects the convergence of the simulations (Figure 11). The fluctuation of the RMSD values for each trajectory is less than 0.25 nm. This indicates the stability of the binding between the top ten hits and the identified active site of the developed full-length of FOXC2 (Figure 11).

  The binding free energies of the top ten hits targeting FOXC2 were calculated using MM/GBSA method. The binding affinities of all the identified ligands were found to be higher than the experimental inhibitor (MC-1-F2), except for compound 5 with slightly lower binding affinity (Figure 12). This implies that effectiveness of augmenting LBDD and SBDD in identifying new inhibitors for FOXC2 with better physicochemical properties.


## Discussion and Conclusion
  MC-1-F2 is the first identified inhibitor of FOXC2 protein, however the compound had unfavorable physiochemical properties. This resulted in difficulty purifying the drug during its synthesis. The two main computational drug design approaches: ligand-based drug design (LBDD) and structure-based drug design (SBDD) were applied to find new hits with desirable physicochemical properties. The top 8 hits identified from both LBDD and SBDD have favorable physicochemical properties following both Lipinski’s and Veber rules [68]. We anticipate that the favorable physicochemical properties will play important roles in our future efforts to examine the efficacy of small molecule inhibitors of FOXC2 in vivo as well as to perform clinical and translational research.

  Moreover, the top eight hits were found to share a common binding mode including four residues: ASN449, LEU459, SER476 and THR484. That is why more studies should be carried out investigating the role of these four residues and the C-terminal of FOXC2 protein in its role in the EMT process. The binding modes of MC-1-F2 and the top eight hits suggest that these could be allosteric compounds, and more studies should be carried out. In the previous study, it has been shown that MC-1-F2 retains FOXC2 in the cytoplasm resulting in the inhibition of FOXC2 nuclear localization, and the cytoplasm-retained FOXC2 becomes subjected to 26S-proteasome mediated degradation. [25] Examining the roles these four residues and the C-terminus of FOXC2 play in the FOXC2 protein-protein interactions associated with FOXC2 nuclear localization will lead us to mechanistic understanding of FOXC2 inhibitors.

  The developed model for the full length of FOXC2 with I-TASSER was found to be stable over the time-course of 100 ns simulations as indicated by the RMSD value that ranged from 1.15 nm to 1.20 nm after the first 10 ns. This reflected the stability of the model and the convergence of the simulations. This supported the use of the model as the basis for the SBDD.

  FOXC2 is a new interesting therapeutic target for the development of anticancer drugs by inhibiting its role in initiating and maintaining the EMT process. Augmenting both LBDD by carrying out similarity search for MC-1-F2 against both ZINC and ChEMBL databases and SBDD by carrying out homology modeling, molecular dynamics, de novo structure-based design, and MM/GBSA calculations helped in identifying new possible hits. Moreover, applying several filtration steps by carrying out docking using FRED and by using BindScope, a convolutional neural network approach, and binding free energy calculations ensured that the top eight hits obtained had the desirable physicochemical properties unlike the experimental inhibitor identified MC-1-F2.


## Supplementary Material

## Data and Software Availability

### Experimental Data
  The crystal structure of DBD of Forkhead Box Protein C2 (PDB ID: 6O3T)) can be obtained free of charge from the Protein Data Bank (https://www.rcsb.org/).

  The sequence of Forkhead Box Protein C2 (UniprotKB Q99958) can be obtained free of charge from Uniprot (https://www.uniprot.org)


### Packages
  Multi-fingerprint browser can be used free of charge from (http://dcb-reymond23.unibe.ch:8080/MCSS/)

  KNIME package can be downloaded free of charge from (https://www.knime.com/)

  OpenMM. Package can be downloaded free of charge from (https://openmm.org)

  I-TASSER server can be used free of charge from (https://zhanggroup.org/I-TASSER/)

  BindScope server can be used free of charge from (https://playmolecule.com/BindScope/)

  LIGANN server can be used free of charge from (https://playmolecule.com/LiGANN/)

  MakeReceptor module, Omega, and FRED can be obtained from OpenEye Scientific using (https://www.eyesopen.com)

  PyMOL 2.4.0 (can be obtained free of charge from (https://pymol.org/2/)

  Molprobiity can be used free of charge from (http://molprobity.biochem.duke.edu)

  ProSA module can be used free of charge from (https://prosa.services.came.sbg.ac.at/prosa.php)


## Acknowledgments
  Research reported in this paper was supported by the National Institute of General Medical Sciences of the National Institutes of Health under Award no. R15GM122013. Computational time was generously provided by Southern Methodist University’s Center for Research Computing. The authors would like to thank OpenEye Scientific Software Inc. for providing academic license of their computer-aided drug design programs.