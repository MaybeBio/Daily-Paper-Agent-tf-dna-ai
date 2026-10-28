# In Silico Molecular Docking and Simulation Studies of Protein HBx Involved in the Pathogenesis of Hepatitis B Virus-HBV


## Abstract
  Current drug discovery involves finding leading drug candidates for further development. New scientific approaches include molecular docking, ADMET studies, and molecular dynamic simulation to determine targets and lead compounds. Hepatitis B is a disease of concern that is a life-threatening liver infection. The protein considered for the study was HBx. The hepatitis B X-interacting protein crystal structure was obtained from the PDB database (PDB ID-3MSH). Twenty ligands were chosen from the PubChem database for further in silico studies. The present study focused on in silico molecular docking studies using iGEMDOCK. The triethylene glycol monoethyl ether derivative showed an optimum binding affinity with the molecular target HBx, with a high negative affinity binding energy of −59.02 kcal/mol. Lipinski’s rule of five, Veber, and Ghose were followed in subsequent ADMET studies. Molecular dynamic simulation was performed to confirm the docking studies and to analyze the stability of the structure. In these respects, the triethylene glycol monoethyl ether derivative may be a promising molecule to prepare future hepatitis B drug candidates. Substantial research effort to find a promising drug for hepatitis B is warranted in the future.


## 1. Introduction
  HBV, which belongs to the Hepadnaviridae group, has a small double-stranded circular-DNA genome that is relaxed and converted to covalently closed circular DNA (cccDNA) in the nuclei of infected hepatocytes [1]. Of the four mRNAs generated from cccDNA by the host RNA polymerase 2, the 0.7 kb mRNA encodes the HBV X protein [1]. It has fascinating properties because it is required for HBV infection in the human liver that expresses the 17-kD HBx protein [2]. However, the exact functions of HBx are not entirely understood in the virus lifecycle. An infected person spreads hepatitis B through blood, sperm, or other body fluids to someone who is not infected. The transmission can occur through sexual contact, needle sharing, syringe sharing, or from mother-to-baby [3]. Chronic hepatitis B virus infection, which accounts for 55% of liver cancer cases globally, has been linked to liver carcinogenesis [4]. In the ranking of the most common cancers worldwide, hepatocellular carcinoma (HCC) stands fifth, and liver cancer stands third. More than 80% of these cases are found in the eastern Pacific and sub-Saharan African regions where tumor incidence is highest [5]. Despite the uncertainty surrounding malignancy caused by HBV, previous research has established that the HBV X (HBx) protein plays a significant role in HCC development. To bridge the gap between previous and present research information, the importance of HBx as a potential drug target for treating HCC was investigated [6].

  Over 78,000 people die yearly from diseases of the liver that are both acute and chronic caused by the hepatitis B virus (HBV), and there are more than 255 million people infected chronically [7]. Cirrhosis and hepatocellular carcinoma are common complications associated with chronic hepatitis B in untreated adults. The two crucial antiviral therapies are nucleos(t)ide analogs (NAs) and pegylated interferon (IFN) α (PEG-IFN-α). A functional cure for HBV is rare despite the effectiveness of NAs. Hepatitis B is rarely eliminated, and drug resistance is a major concern during long-term treatment [8]. Despite the limited course of treatment and the possibility of maintaining a virologic response post drug withdrawal, PEG-IFN has not yet proved to be an effective treatment [9].

  Numerous signaling pathways affected by the HBV X protein (HBx) influence cell invasion and proliferation. Aside from its role in viral replication and chromosomal instability, HBx plays a role in oncogenesis. DNA methylation, angiogenesis, oncogenesis, oxidative stress, and migration are all factors that it regulates [10].


## 2. Materials and Methods

### 2.1. Target Protein Accession
  The high-resolution crystal structure of the target, hepatitis B X-interacting protein, (1.51 Å) was taken from the RCSB Protein Data Bank (PDB ID-3MSH). The three-dimensional structure of protein HBx was obtained from RCSB PDB (Figure 1). The experimental data was obtained by X-ray crystallography.


### 2.2. Sequence Retrieval
  The FASTA sequence of HBx protein with accession ID—3MSH_A of 99 amino acids was retrieved from NCBI.

  >pdb|3MSH|A Chain A, hepatitis B virus X-interacting protein

  MEATLEQHLEDTMKNPSIVGVLCTDSQGLNLGCRGTLSDEHAGVISVLAQQAAKLTSDPTDIPVVCLESD

  NGNIMIQKHDGITVAVHKMASLEHHHHHH


### 2.3. Preparation of Ligands
  From RCSB PDB, four unique ligands were identified, namely PG4, PO4, GOL, and IPA, from which PG4 was considered for further study since it is not commonly found in other proteins. A total of 20 ligands were selected using isomeric SMILES format from the PubChem database based on similar ligands in PDB and files were downloaded in 3D SDF format. The SMILES translator and structure file generator was used to convert the files into PDB format.2.4. for molecular docking analysis.

  Docking is a computer-aided prediction of the size and conformation of drug and enzyme/protein seeking to find the best match between two molecules. Simply defined, docking is an in silico method that is used to predict a protein’s (enzyme) reaction with ligands.

  Major steps involved in the docking process are:

  Target selection > ligand selection and preparation > docking > evaluating docking results.

  Large databases of potential drugs can be screened in silico to identify molecules with a high likelihood of binding to a target protein. Ligands are positioned correctly in a protein’s binding pocket during the docking process, and the affinity between the ligand and the protein is predicted.

  The molecular docking procedure generates multiple ligand conformations and orientations that fit against the target and selects appropriate matches. The less the binding free energy of a complex, the more stable it is. To perform docking analysis, iGEMDOCK was used [11]. It uses an empirical scoring function and generic evolutionary method for the molecular docking process. This tool identifies pharmacological interactions visually, and virtual screening is performed through a graphical user interface. The screening process evaluates pharmacological interactions without using any of the known active compounds [12].

  Compared to other docking simulation software, iGEMDOCK (version 2.1) displayed better overall results. GEMDOCK (Generic Evolutionary Method for Molecular DOCKing) is a tool for calculating the form and orientation of ligands in relation to the target protein. iGEMDOCK can be used both to prepare an interactive screening compound library and the target protein binding site [13]. A series of interaction profiles for protein-compound interactions are generated by iGEMDOCK, including electrostatic force (E), hydrogen-bonding (H), and van der Waal’s (V) interactions. As a final step, iGEMDOCK also allows individual screening compounds to be ranked and viewed according to their chemical activity and pharmacological interactions [12,14].


### 2.4. ADMET Studies
  The selected hit molecules will be validated with ADME/T studies to identify potential lead molecules against the pathogenic organism. By using ADME/T tools, it is possible to predict pharmacokinetic parameters, such as the bioavailability, metabolic half-life, and permeability of the ligands during the drug design process [15]. Analyzing ADME during the initial discovery phase can dramatically reduce the fraction of clinical trials affected by pharmacokinetic failures [16].

  Six physicochemical properties assessed for study were: lipophilicity, size, polarity, solubility, flexibility and saturation for the bioavailability radar. For a molecule to be considered drug-like, it has to be wholly within a physicochemical range on each axis which is depicted by the pink area in the radar graph [17].

  Lipinski proposed ADMET properties called the “rule of five”. A compound can be evaluated for oral absorption by the rule of five, the oldest and most well-known of all the rules used to measure drug-likeness [18].

  The Lipinski rule of five includes:the molecular weight of molecule (MW) ≤ 500,the octanol/water partition coefficient (iLOGP = A log P) ≤ 5,the number of hydrogen bond donors (HBDs) ≤ 5,the number of hydrogen bond acceptors (HBAs) ≤ 10.6, and,the topological polar surface area (TPSA) < 40 Å2.

  Apart from Lipinski’s rule, other rules that the compounds should adhere to are those of Ghose, Egan, Veber and Muegge. Each of these evaluate drug-like properties based on distinct parameters. A molecule can be orally bioactive/absorbable only if there is no violation of more than two of the rule of five conditions [19]. Some complex natural compounds that may not comply with this rule can be evaluated with several other drug-likeness rules equivalent to the rule of five [20].


### 2.5. Molecular Dynamics
  Molecular dynamics simulation was performed using Schrödinger. This powerful computational tool can predict material properties, design drugs and model biomolecules, and much more [21]. MD simulation is performed after docking to optimize the final structures, analyze the stability of different complexes, and account for solvent effects as a final filter in silico to guide chemical synthesis for hit optimization [22].

  It enables understand of structure and dynamics—analyzing the time-dependent behavior of a molecular system allows tracking of the motion of individual atoms at these scales [23]. The Schrödinger tool was used to analyze the parameters of MD trajectories, including: root mean square deviation (RMSD), root mean square fluctuation (RMSF), radius of gyration (RG), number of intermolecular hydrogen bonds, solvent accessible surface areas (SASA), and the B-factor [24].


## 3. Results and Discussion

### 3.1. Molecular Docking
  Twenty ligands from PubChem were considered for the docking process. PDB format of the drug was chosen for preparing the binding site. The virtual screening procedure of iGEMDOCK consisted of four main steps which were: setting population size = 200, generations = 70, number of solutions = 2, and default setting = standard docking.

  To evaluate binding affinities and to understand the possible interactions between ligands and proteins, molecular docking was performed. The energy contribution by van der Waal’s force, hydrogen bonding, and the electrostatic force is displayed in Table 1.

  The top six ligands with least binding energy were: 2-[2-(2-ethoxyethoxy) ethoxy] ethanol (−59.0259), 2-[2-[2-(2-ethoxyethoxy) ethoxy] ethoxy] ethanol (−55.8216), 2-[2-[2-(2-propoxyethoxy) ethoxy] ethoxy] ethanol (−53.6121), 2-[2-[2-[2-(2-hydroxyethoxy) ethoxy] ethoxy] ethoxy] ethanol (−52.5801), 2-[2-[2-(2-methoxyethoxy) ethoxy] ethoxy] ethanol (−52.1195), and 2-[2-(2-propoxyethoxy) ethoxy] ethanol (−51.3424). The best molecule showing the highest binding energy, 2-[2-(2-ethoxyethoxy) ethoxy] ethanol, was the most effective inhibitor.

  Amino acids contributing to the binding of the compound can be viewed in the interaction analysis depicted in Table 2. The amino acids which were involved in interaction with the protein were 9 (leucine), 10 (glutamine), 12 (threonine), 15 (asparagine) as depicted in Figure 2.


### 3.2. ADMET Studies
  The selected molecules had an acceptable oral toxicity (LD50), which means they would not elicit any untoward adverse effects in low concentrations. As a result of the analysis of all properties, the molecules in question were determined to be non-toxic, ensuring their safety. The predicted toxicity properties of the molecules, along with their prediction probability, bioavailability and drug-likeness, are shown in Table 3, Table 4 and Table 5.

  Considering CID_8190, after docking results, it was observed that the compound followed the rules of Lipinski, Ghose, Veber, Egan and Muegge with a bioavailability score of 0.55.

  The bioavailability radar has six axes which consist of six essential properties for oral bioavailability. The optimum values are depicted in the pink region. The red line of the compound under consideration was completely included in the pink area. This shows that the criteria of flexibility, lipophilicity, size and polar nature were fulfilled (Figure 3).

  According to the ADME and drug-like properties of the molecules shown above, the molecules are highly bioavailable in the gastrointestinal tract, but not permeable through the blood-brain barrier (BBB).

  The bioavailability radar considers six physicochemical properties of a drug to determine the molecule’s drug-likeness: saturation, polarity, flexibility, size, lipophilicity, and solubility [25].

  The molecules were shown to be bioavailable orally, of low toxicity, and to have a good absorption rate (Figure 4).


### 3.3. MD Simulation
  All the protein frames were initially aligned on the reference frame backbone, and the calculation of RMSD was based on Cα or side chain. Visualizing the RMSD of protein provides detailed information concerning structural conformations during the simulation. This parameter indicates simulation equilibration and its fluctuation around a thermal mean. Changes of the order of 1–3 Å are acceptable. If the protein undergoes a much more significant conformational change than 3 Å, it indicates that a large conformational change occurs during simulation. RMSD values should stabilize at around a fixed value or converge during simulation. An insight into the ligand’s stability relative to the binding pocket of the protein is provided by ligand RMSD.

  The graph in Figure 5 shows the protein RMSD evolution (indicated on the left Y-axis) and ligand RMSD (indicated on the right Y-axis). The plot shows that the compound hepatitis B X-interacting protein (PDB ID 3MSH) complex showed stabilization soon after beginning the simulation, i.e., 10 ns. Considering ligand RMSD, the fluctuation was observed after 30 ns of the trajectory curve. Throughout the simulation of 50 ns, no noteworthy conformational changes occurred in the protein structure. Variations were in the range of 1–3 Å, which can be considered to be non-significant.

  Protein-ligand interactions are divided into four types: hydrogen bonds, hydrophobic and ionic interactions, and water bridges. The graph displays the compound contacts studied during the 50 ns trajectory in bar chart format (Figure 6). The bar graph depicts hydrogen bonds, hydrophobic contacts, and water bridges visualized throughout the simulation period. The significant hydrogen bonds observed in the initial docked pose of the compound (Thr 36, Ser 38, Glu 68, His 41, Asp 70, Ser 69, Asn 71) did not change during the simulation. Hydrogen bonding with His 41 remained for more than 20% of the simulation time. Hydrophobic interaction was observed with residues Leu 37, Val 44, Ile 45, Leu 48, Leu 67, Ile 74, and Ile 76. Water bridged interactions were noticed with residues Thr 36, Ser 38, Glu 40, Glu 68, Ser 69, Asp 70, and Asn 71. Hence, the four important residues identified were: Ser 38, His 41, and Ser 69.


## 4. Conclusions
  With the advancement of technology, computer-aided drug design (CADD) has paved the way for lead identification and optimization in research and development. Using in silico tools, it is easier and more effective to limit the required number of molecules for further analysis by experiments. The study identified twenty compounds from which triethylene glycol monoethyl ether derivative was chosen based on docking score, binding energies, suitable ADMET, and simulation results. In conclusion, this research has highlighted the relevance of this compound as a potential treatment lead for hepatitis B, which could be used for developing more potent anti-HBV drugs.


## Acknowledgments
  The authors are thankful to Najran University, Najran, KSA; and KLE Technological University, BVB Campus, Hubballi, India, for constant support and encouragement.