# Identification of New Drug Target in Staphylococcus lugdunensis by Subtractive Genomics Analysis and Their Inhibitors through Molecular Docking and Molecular Dynamic Simulation Studies


## Abstract
  Staphylococcus lugdunensis is a coagulase-negative, Gram-positive, and human pathogenic bacteria. S. lugdunensis is the causative agent of diseases, such as native and prosthetic valve endocarditis, meningitis, septic arthritis, skin abscesses, brain abscess, breast abscesses, spondylodiscitis, post-surgical wound infections, bacteremia, and peritonitis. S. lugdunensis displays resistance to beta-lactam antibiotics due to the production of beta-lactamases. This study aimed to identify potential novel essential, human non-homologous, and non-gut flora drug targets in the S. lugdunensis strain N920143, and to evaluate the potential inhibitors of drug targets. The method was concerned with a homology search between the host and the pathogen proteome. Various tools, including the DEG (database of essential genes) for the essentiality of proteins, the KEGG for pathways analysis, CELLO V.2.5 for cellular localization prediction, and the drug bank database for predicting the druggability potential of proteins, were used. Furthermore, a similarity search with gut flora proteins was performed. A DNA-binding response-regulator protein was identified as a novel drug target against the N920143 strain of S. lugdunensis. The three-dimensional structure of the drug target was modelled and validated with the help of online tools. Furthermore, ten thousand drug-like compounds were retrieved from the ZINC15 database. The molecular docking approach for the DNA-binding response-regulator protein identified ZINC000020192004 and ZINC000020530348 as the most favorable compounds to interact with the active site residues of the drug target. These two compounds were subjected to an MD simulation study. Our analysis revealed that the identified compounds revealed more stable behavior when bound to the drug target DNA-binding response-regulator protein than the apostate.


## 1. Introduction
  Staphylococcus lugdunensis is a coagulase-negative and Gram-positive staphylococci first identified in 1988 [1]. S. lugdunensis is usually present on human and other mammals’ skin [2]. Meningitis, septic arthritis, skin abscesses, brain abscess, breast abscesses, peritonitis, spondylodiscitis, and wound infections are different diseases associated with Staphylococcus lugdunensis [3]. S. lugdunensis is the causative agent of bacteremia in some patients [4]. Most virulent factors of Staphylococcus lugdunensis are identical to staphylococcus aureus [5]. Both bacteria share approximately 70% of the genome [6]. For S. lugdunensis identification, the ornithine decarboxylase test is mainly used [7]. The clinical properties, infection, and biochemical features of S. lugdunensis are identical to S. aureus [8]. Genome sequencing flaunts the genes encoded for virulency, such as hemolysin, adhesions, and toxins [9]. Biofilm production is an essential factor contributing to the pathogenicity of Staphylococcus. Due to the presence of the ica gene, S. lugdunensis has the ability of biofilm formation [10]. The pathogen becomes methicillin-resistant when SCC mec or staphylococcal cassette chromosome, a movable genetic element, is transferred to different staphylococcal species [11]. S. lugdunensis displays predominant resistance to beta-lactam antibiotics because of the production of beta-lactamase enzymes. A total of 73.3% of S. lugdunensis isolates were resistant to ampicillin, and 46.6% to cloxacillin and oxacillin. Resistance to beta-non-lactam antibiotics was lower than beta-lactam antibiotics at 53% for azithromycin and 46.6% for amikacin [12]. Yen and his coworkers stated that S. lugdunensis showed 87% resistance to penicillin and 20% to oxacillin [13].

  Subtractive genome analysis plays a vital role in drug target identification. Drug targets must be necessary for pathogen survival. In three types of cases, subtractive genomics can be widely used: firstly, for pathogens with no virulent factor identified; secondly, for pathogens resistant to drugs; and thirdly, for pathogens for which no powerful drugs are available. There is a need to develop new drugs and cure diseases as the available drugs for treating diseases caused by different pathogens exhibit side effects, and drug-resistant strains increase daily. A unique therapeutic target in the pathogen is predicted using subtractive genome analysis because the target should only be present in the pathogen, preventing drug interactions within human proteins. Experimental approaches are costly, time-consuming, and provide infrequent results. The subtractive genomics approach is highly effective, quick, and inexpensive, so computational approaches are usually preferred over experimental approaches [14,15]. Drug and vaccine targets can be predicted [16]. Many researchers have utilized the subtractive genomics approach for drug target prediction in Bacillus anthracis [17], Burkholderia pseudomalleii [18], and Staphylococcus aureus [19]. This study aims to identify new, non-homologous, essential, and non-gut flora therapeutic targets in S. lugdunensis strain N920143 using subtractive genomics. Additionally, it aims to uncover novel drug target inhibitors and construct a homology model of computationally predicted drug targets.


## 2. Materials and Methods

### 2.1. Pathogen Complete Protein Sequences Retrieval
  The complete protein sequences of Staphylococcus lugdunensis strain N920143 were downloaded from the NCBI (The National Center for Biotechnology Information; Available online: https://www.ncbi.nlm.nih.gov/ (accessed on 22 May 2022) database [20]. Proteins in the FASTA (Fast Alignment Sequence Test for Application; Available online: https://www.ebi.ac.uk/Tools/sss/fasta/ (accessed on 22 May 2022) were selected for further analysis.


### 2.2. Duplicate Proteins Identification
  Proteins possessing ≥ 60% similarity were counted as duplicates. Proteins with amino acid sequences < 100 and duplicates were excluded because they were potentially not essential for the survival of pathogens [21]. The CD-hit program; Available online: http://weizhong-lab.ucsd.edu/cdhit_suite/ (accessed on 8 August 2022) was used to identify duplicate proteins [22].


### 2.3. Non-Paralogs Proteins Identification
  The non-paralog set of proteins was submitted to the NCBI BLASTp (Basic Local Alignment Search Tool; Available online: https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE=Proteins; (accessed on 8 August 2022), in contrast to homo-sapiens proteins, which used a 10−4 E value (expected value) [23]. Only non-homologous proteins were used for further analysis, while human homologous proteins were removed.


### 2.4. Essential Proteins Identification
  Key cellular functions of microbes are maintained by vital genes and are therefore considered vital for pathogen survival. Non-homologous protein sequences were submitted to the BLASTp against DEG (differentially expressed genes; Available online: https://tubic.org/deg/public/index.php; (accessed on 8 August 2022) using the anticipated E value of 10−5 to predict the pathogen genes involved [24]. The DEG database was used to identify essential genes of the S. lugdunensis.


### 2.5. Analysis of Standard and Unique Pathways
  Using the KAAS (KEGG Automatic Annotation Server) at the KEGG (Kyoto Encyclopedia of Genes and Genomes) [25], metabolic pathways of S. lugdunensis strain N920143 were analyzed. Metabolic pathways of pathogens and humans were identified and compared manually. Pathways that appeared only in the pathogen genome were considered unique to S. lugdunensis. In contrast, pathways that appeared in both pathogens and humans were considered common pathways, according to the KEGG database [26].


### 2.6. Proteins Localization Prediction
  Identifying the subcellular location of proteins is vital for effective drug target identification. Extracellular cell wall, cytoplasmic, and membrane proteins were differentiated by CELLO V.2.5 (Available online: http://cello.life.nctu.edu.tw/; (accessed on 8 August 2022). Extracellular or membrane proteins could be possible vaccine targets, while cytoplasmic proteins are considered potential drug targets.


### 2.7. Virulent Proteins Identification
  PAIDB v2.0 (Available online: http://www.paidb.re.kr; (accessed on 8 August 2022) was used for the identification of virulent proteins. The PAIDB gives essential information about predicted pathogenicity in the prokaryotic genome [27].


### 2.8. Drug Ability Potential of Short-Listed Proteins
  The drug bank database (Available online: https://go.drugbank.com/; (accessed on 8 August 2022) was accessed to evaluate the druggability potential of all the selected protein sequences of S. lugdunensis strain N920143. FDA-approved drug targets for drug IDs are present in drug bank databases [28].


### 2.9. Gut Metagenome Screening
  Gut microbiota is constituted of beneficial bacteria that inhabit the human digestive tract. In the human intestine, almost a hundred trillion microbes exist [29]. Between gut flora and humans, a mutualistic and symbiotic relationship exists [30]. Functions such as inhibiting pathogen growth, enhancing the immune system, and producing energy by fermenting undigested carbohydrates are performed by beneficial microbes in the host [31]. The human microbiome project database (Available online: https://hmpdacc.org/; (accessed on 8 August 2022) was used, and proteins resembling gut flora were excluded [32].


### 2.10. 3D Structure Prediction
  As the crystal structure of the drug target was not available in the PDB database (Available online: http://www.rcsb.org/pdb/; (accessed on 8 August 2022), homology modeling was performed. The Phyre2 server can develop a highly confident 3D structure: the Phyre2 online server was used in this study to build 3D structures of the drug target. Sequences of the target protein were taken in FASTA format from the NCBI, and submitted as input files to the Phyre2 server. The 3D structure was developed automatically and finally downloaded in PDB format.


### 2.11. Model Validation
  The 3D structures developed via the Phyre2 server were validated by Procheck (Available online: https://www.ebi.ac.uk; (accessed on 8 August 2022) and ProSA web (Available online: https://prosa.services.came.sbg.ac.at; (accessed on 8 August 2022) servers. The Procheck server was used for Ramachandran plot analysis [33]. ProSA web is an online server that performs statistical analysis of protein structures [34].


### 2.12. Molecular Docking
  In MOE (Molecular Operating Environment, 2016; Available online: https://www.chemcomp.com/Products.htm; (accessed on 8 August 2022) software, the study of molecular docking was performed to find the hits that interact strongly with the predicted drug target. A default value of 0.05 was used for energy minimization, and the model was protonated. The active site of the predicted drug target protein was identified using the site finder option in MOE. Different parameters like Refinement, Rigid Receptor, Rescoring, London dG, Placement, and Triangle Matcher functions in the MOE dock options, were used [24]. A total of 10,000 drug-like compounds retrieved from the ZINC15 database (Available online: https://zinc15.docking.org/; (accessed on 8 August 2022) were docked with the active site of the drug target.


### 2.13. MD Simulation Study
  The effect of the top two hits on the structure and stability of the identified drug target proteins was investigated using molecular dynamics simulation. The Amber 20 software (Available online: https://ambermd.org/; (accessed on 8 August 2022) was used to investigate the dynamics of the drug target in the presence and absence of ligands. Cleaning each structure was the first step for MD simulation. After that, a cubic simulation cell with a periodic boundary condition was built. The (AMBER14) force field was used for the protein. Then, a cubic box of TIP3 water with a box dimension of 12 Ao of protein was used. The counter ions (Na+ and Cl) were added to neutralize the systems [35,36]. Energy minimization was performed on the systems in 5000 stages, using 2500 steepest-descent steps and 2500 conjugate gradient steps. The systems were gently heated from 0 to 325 Kelvin. The Langevin dynamics approach (1 atm pressure and 310 K temperature) was used as a Langevin thermostat [37]. The MD simulation was run for 100 nanoseconds at a constant temperature of 325 K. Origin software was used for data visualization and analysis.


### 2.14. Post MD Analysis
  The conformational changes during simulations were analyzed in this study. The CPPTRAJ module of AMBER 20 was used to investigate the root-mean-square deviation (RMSD), root-mean-square fluctuation (RMSF), and radius of gyration (RoG).


## 3. Results and Discussion
  A new drug target in the S. lugdunensis genome was identified by performing subtractive genomics. Figure 1 describes the systematic workflow, and Table 1 describes the relative number of proteins obtained from each step. By subtractive genome analysis, a DNA-binding response-regulator protein was found as a novel drug target in S. lugdunensis bacteria. Due to the lack of its 3D structure in the protein databank database (PDB), homology modeling was performed to predict new inhibitors against computationally predicted drug-target-protein molecular docking.


### 3.1. Retrieval of Pathogen Proteome and Removal of Duplicates
  Among all the available strains of S. lugdunensis, N920143 was selected as this strain was human pathogenic. From the NCBI database, a total of 2240 proteins of S. lugdunensis strain N90143 were downloaded. All the protein sequences obtained from the NCBI database were submitted to the CD-hit tool, with an identity value of 60%, to remove duplicate proteins and sequences with fewer than 100 amino acids [21,22]. The total number of proteins of N920143 were minimized to 2102 after running the CD-hit tool.


### 3.2. Pathogen Essential and Non-Homologous Genes Identification
  Non-duplicate proteins were submitted to the NCBI BLASTp (Available online: https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE=Proteins; (accessed on 8 August 2022) against human proteome using a 10−4 E value [38]. A total of 980 proteins were found as non-homologous in the N920143 strain. The basic standard for potent drug targets is that drug target proteins are crucial for pathogen survival, but must be absent in the human host so that human and pathogen proteins do not cross-bind and to avoid the side effects of drugs [15]. Complete protein sequences of the N920143 strain were submitted to the BLASTp instead of a DEG (database of essential genes) to determine the pathogen’s essential genes, using expected values 10−5. In the N920143 strain, 670 essential proteins were found in the database of essential genes.


### 3.3. Pathways Analysis
  The KEGG database was used to analyze the pathogen and host metabolic pathways through the KAAS server [39]. Common pathways were not considered, and only the pathogen’s unique pathways were preferred. In the N920143 strain of S. lugdunensis, 21 unique pathways were found. Unique pathways, along with pathway IDs, are presented in Table 2. In these unique pathways, five proteins were involved (Table 3). A single protein could be involved in more than one pathway. Proteins that are not homologous to humans and take part in multiple pathways can be a more potent drug target [26].


### 3.4. Prediction of Protein Subcellular Localization
  According to CELLO V.2.5, 70% of the proteins were present in the cytoplasm and 30% were present in the membrane.


### 3.5. Druggability of Selected Proteins
  For the druggable potentiality identification, all the essential and non-homologous proteins were blasted with a drug bank database, containing FDA-approved drug targets. Five proteins revealed similarities with FDA-approved drugs in the drug bank database. Table 4 delineates proteins possessing druggable potency, along with drug bank IDs.


### 3.6. Screening of Short-Listed Proteins with Gut Flora
  Along with pathogenic bacteria, the beneficial bacteria in human gut flora can also be targeted by most antibiotics [40], so we tended to exclude those proteins of S. lugdunensis that displayed homology with gut flora proteins to avoid the side effects of drugs. Regarding this concept, the human microbiome project database was used to evaluate those proteins that showed similarities with regular gut flora proteins. Of the human non-homologous, virulent, and essential proteins that were compared with gut flora proteins, 11 out of 12 displayed similarities with gut flora. Only one DNA-binding response-regulator protein did not display any similarity with gut flora; therefore, this was selected as a novel drug target in S. lugdunensis.


### 3.7. Homology Modeling and Model Validation
  The crystal structure of the target protein was not found in the PDB database; homology modeling was performed via the Phyre2 server. Figure 2 shows the 3D structures of the drug target DNA-binding response regulator. The 3D structure was further validated by the Ramachandran plot and the ProSA web server. The quality of the model was predicated on the Z-score plot of the ProSA web server. The Z-score of the excellent quality model lies within the range of native protein structures, while the erroneous structure has a Z-score outside this range [33]. The Z-score of the target DNA-binding response-regulator protein is −3.63, as in Figure 3. Ramachandran plot analysis was performed by the Procheck server [17]. According to the Ramachandran plot, 94.7% of residues are in the most favored region, 5.3% in the additional allowed region, 0% in the generously allowed, and 0% in the disallowed region as seen in Figure 4. The Ramachandran plot quantified that the quality of the model is good if >90 % of residues are in the most favored regions.


### 3.8. Molecular Docking Study
  Ten thousand compounds of zinc database were docked against the receptor active site of the DNA-binding response regulator. Among the top 100 compounds, two hits yielded a favorable interaction with the DNA-binding response-regulator protein (Figure 5). Compounds ZINC000020192004 and ZINC000020530348, with docking scores of −16.231 and −14.187, were found as novel and potent inhibitors against the predicted drug target protein. Docking scores of these potent inhibitors are shown in Table 5.


### 3.9. MD Simulation
  The RMSD parameter determined the complex stability. The complex is more stable when the average RMSD value is low [41,42] (Figure 6). The RMSD plots for ZINC000020192004 and ZINC000020530348 in complex with drug target and unbound (apo-enzyme) are shown in Figure 7. The two complexes converged at around 5 ns and remained stable during the simulation, with overall average values of 1.6 and 1.5. The apo-enzyme average RMSD is 1.6A.

  The average RoG values of 16.2, 16.1, and 16.01 were observed for ZINC000020192004 and ZINC000020530348, and the apo-enzyme. The RMSF measures how the residues fluctuate when bound to a drug [43]. An increase in the RMSF value indicates an increase in the flexibility of the alpha-carbon atoms. Compared to the two predicted hits, the more flexible regions were found in the apo-enzyme. High residual fluctuations were recorded at residues 20–40 and 60–80, as shown in Figure 8.

  The RoG parameter was used to evaluate the structural compactness of proteins when bound to molecules [44]. A lower RoG value indicates more stability, while a higher RoG value indicates an unstable system [45]. The RoG plot results correlate with its RMSD plot, indicating that molecule binding did not affect the structural stability of the DNA-binding response-regulator protein [46]. In the case of the ligand-bound complexes, a lower RoG value was revealed; meanwhile, for the apoenzyme, a slightly higher RoG value was indicated, as is displayed in Figure 9.


## 4. Conclusions
  In the present study, we utilized the art of computational biology to identify novel therapeutic targets in S. lugdunensis proteome. Through subtractive proteomic analysis, novel drug targets involved in unique metabolic pathways were identified by using comparative sequence analysis and different biological updated databases. The prioritized therapeutic targets, including 4-hydroxtetrahydrodipicolinate reductase, signal peptidase, DNA-binding response regulator, and genome polyprotein, are critical to the pathogen’s survival. The drug target predicted in the present study was promising to be essential to the pathogen survival and did not share homology with the human gut microbiota. The three-dimensional structure of the DNA-binding response regulator-protein was subjected to molecular docking studies, and it evaluated ZINC000020192004 and ZINC000020530348 as lead compounds. These compounds showed striking interactions with the DNA-binding response regulator. Furthermore, the results of the MD simulation analysis demonstrated that the two hits, ZINC000020192004 and ZINC000020530348, remained stable with the active site residues of the DNA-binding response-regulator protein. Further in vitro study is needed to validate these drug targets and the lead compounds.


## Acknowledgments
  The authors extend their appreciation to the Deanship of Scientific Research at King Khalid University for funding this work through the Large Groups Project under grant number (RGP.2/70/43).