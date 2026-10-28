# Treatment of non-small cell lung cancer using chem-bioinformatics-driven engineering of exosomal cargo-vehicle for telmisartan and pioglitazone targeted-delivery


## Abstract
  The activation of the PPARG transcription factor is linked to reduced non-small cell lung cancer (NSCLC) growth. Bioinformatics, cheminformatics, and molecular docking/dynamics studies assessing pioglitazone and telmisartan as repurposed PPARG agonists for treating NSCLC with a targeted delivery system was done. Bioinformatics confirmed that the expression of the PPARG gene can predict outcomes in lung adenocarcinoma and is related to immune cells present in the tumor. Cheminformatics data showed that pioglitazone and telmisartan have a strong attraction to the PPARG receptor, with good efficiency as ligands. Both drugs were found to be lipophilic, suggesting compatibility with a targeted delivery formulation that may include albumin. Further cheminformatics predictions highlighted systemic toxicity values and the need for targeted delivery to minimize toxic side effects. Molecular docking and dynamics simulations showed that the telmisartan-MyoVc cargo domain complex was strong and stable during an 18 ns simulation period. Bioinformatics and cheminformatics data support pioglitazone and telmisartan as promising repurposed drugs for LUAC, highlighting their lipophilicity and compatibility with exosomal components like albumin. Cheminformatics also pointed out potential off-target effects and hepatotoxicity, emphasizing the importance of exosomal targeted delivery. Molecular docking and MD simulations confirmed the affinity and stability of drug-exosomal vehicle complexes. The proposed engineering of exosomal cargo for targeted delivery of these drugs to lung cells could enhance NSCLC treatment and address drug resistance while minimizing systemic toxicity.


## Introduction

### Problem statement
  The creation of an effective system/formula for treating lung cancer is critical, especially given the annual increase in new cancer cases.


### Literature review
  Cancer-related fatality impedes progress toward Sustainable Development Goal (SDG) #3 of “Better Health.”

  As the field of drug delivery systems (DDS) has evolved, nanotechnology (NT) has made significant contributions to the development of smart nanocarriers1,2 such as synthetic lipid-based nanocarriers that provide a unique platform for drug encapsulation3,4. Furthermore, natural cell-derived carrier systems have sparked substantial interest5.

  The lncRNADisease database6 and the Kyoto Encyclopedia of Genes and Genomes (KEGG) database7 include these types of lung cancer: lung adenocarcinoma (LUAD), lung cancer that has spread to the brain, lung squamous cell carcinoma, pulmonary adenocarcinoma, non-small cell lung cancer (NSCLC), and small cell lung cancer (SCLC). Genetic changes in the lung and related pathways (Fig. 1) from KEGG include Ras or ErbB, MAPK (mitogen-activated protein kinase), calcium, and PI3K-AKT signaling pathways, which are linked to oncogenes or tumor suppressor genes.

  Interestingly, both in vitro8–10 and in vivo11 studies have shown that activating peroxisome proliferator-activated receptor gamma (PPARG) slows down the growth of NSCLC lung cancer cells and/or might help stop the spread of developed NSCLC12. KEGG data on lung cancer genetic pathways that matched the results of earlier experimental studies, which demonstrated MAPK’s regulatory capability over PPARG activity13, 14‚15 providing proof-of-concept for the direction of our research.

  Repositioning diverse pharmaceuticals with distinct modes of action is a strategic approach to mitigate or postpone cancer treatment resistance15. Selective PPARG activators have been previously investigated for their roles as antidiabetic agents or insulin sensitizers and their involvement in lipid metabolism16,17. The efficacy of thiazolidinediones (TZDs), a category of oral PPARG activators that mitigate tumor growth progression in the liver18 and in NSCLC xenograft animal models11,19,20, has been established for decades. BioGRID4.421 and the integrated repository portal for tumor-immune system interactions (TISIDB)22 consistently identified pioglitazone as a distinctive interactor of PPARG, classified as a member of TZDs with the most extensive safety margin. Telmisartan, an angiotensin II receptor type 1 (AT1) antagonist, utilized in hypertension management, was identified as a partial PPARG agonist23–25. Moreover, recent studies have demonstrated the anticancer properties of telmisartan against many cancer types, including NSCLC26–28. Unexpectedly, the PI3K/AKT signaling pathway28 contributed to the anticancer efficacy of telmisartan against NSCLC with PPARG activation, aligning with the lung oncogenes depicted in Fig. 1.

  Fig. 1Lung genetic alterations and related pathways retrieved from KEGG, where Ras or ErbB, MAPK, calcium, and PI3K-AKT signaling pathways comprising either oncogenic or tumor suppressor genetic alteration signaling pathways give rise to atypical hyperplasia, then primary and metastatic adenocarcinoma.

  The use of exosomes, as a regenerative-biological cell therapy, shows promise for treatment of various non-communicable diseases (NCDs)29. We will use exosomes to transport natural or manufactured anticancer drugs, to tumor cells as safe and non-immunogenic way30–32. It would be more appropriate to utilize exosomes, which are naturally occurring extracellular vesicles (ECVs) in the blood or tissues, instead of drug-encapsulated nano-scaffolds made of blended FDA-approved polymers like polyethylene glycol (PEG) or polylactic-co-glycolic acid (PLGA).

  Online databases Vesiclepedia and Exocarta33 show that exosomes, which are a type of extracellular vesicle (ECV), contain parts of cell membranes, such as transmembrane proteins, surface markers, albumin, growth factors and their receptors, proteoglycan receptors, cytokines, heterotrimeric G proteins, heat shock protein 90 (HSP90), and non-muscle myosin34. This non-muscle myosin probably works with cytoskeletal actin in target organs, along with adhesion molecules and proteins from the extracellular matrix.


### Aim and objectives
  Per, we emphasize pioglitazone and telmisartan as distinctive ligands for the NSCLC repressor PPARG in the current in-silico targeted delivery investigation; therefore, we will use chem-bio-informatics35 to find out how well the chosen drugs work for treating lung cancer when delivered by exosome cargo, before testing them in the lab.

  Second, to establish the drug’s affinity for the carrier protein, we will run the test drugs through a stiff molecular docking process in the exosome cargo domain, using albumin as a protein component of the target exosome. In addition, we will run a molecular dynamics simulation on the drug-cargo combination to see how stable it is when interacting with the protein in the drug delivery system.


## Materials and methods

### Bioinformatics databases

#### Biological information
  Transcriptome data and clinical information for LUAD were gathered from The Cancer Genome Atlas (TCGA) using the Genomic Data Commons download tool.


#### Lung cell type enriched transcriptome
  The Human Protein Atlas36 shows that the lung-specific proteome has 195 raised genes, 17 enriched genes, and 42 group-enriched genes. The Human Protein Atlas gave us the results acquired from the following links:

  https://genemania.org/search/homo-sapiens/pparg.

  http://stitch.embl.de/cgi/network.pl?%20taskId=KpczawHjZzrz.

  https://thebiogrid.org/111464/summary/homo-sapiens/pparg.html.


#### Systematic data base-mining and enrichment-analyses of PPARG gene expression profile and prognostic role in lung adenocarcinoma (LUAD)

##### UALCAN data base mining
  The open-access platform UALCAN (http://ualcan.path.uab.edu/) is based on level 3 RNA-seq and pathological files from the TCGA database37 and was used to examine the relative transcriptional levels of the PPARG gene between tumor and non-cancerous tissues, as well as the correlation of PPARG gene mRNA levels with pathological features.


##### Differential expression of PPARG gene in LUAD and normal tissues
  We are looking at how much PPARG is expressed in normal tissues compared to tumor tissues using data from the GTEx Portal38,39 Release V8, which can be found at this link: https://exphewas.ca/v1/gene/ENSG00000132170?analysis_subset=BOTH#cardio-endpoints-results-section.

  https://www.gtexportal.org/home/gene/ENSG00000132170.

  http://ualcan.path.uab.edu/cgi- bin/TCGAExResultNew2.pl? genenam = PPARG&ctype = LUAD.

  The expression of the PPARG gene in LUAD is shown according to the type of tumor, its stage, whether it has spread to lymph nodes, and the mutation status of the TP53 protein. https://ualcan.path.uab.edu/cgi- bin/TCGAExResultNew2.pl? genenam = PPARG&ctype = LUAD.

  The TP53 mutation status was determined using whole exome sequencing data from TCGA, which was obtained via Mutation Annotation Format (MAF) files generated by VarScan2 on the Genomic Data Commons portal. The samples with and without the TP53 mutation were matched to RNA-seq data.


##### GEPIA database mining
  GEPIA, an interactive website (http://gepia.cancer-pku.cn/) Using data from the Cancer Genome Atlas and the TCGA database, “expression level analyses”40 were conducted to study the prognostic values and survival related to PPARG gene expression in lung cancer and nearby normal tissue samples. The gene expression patterns of the PPARG-correlated genes are also extracted and rated alongside PPARG. We acquired the data results from the following link: https://ualcan.path.uab.edu/cgi-bin/TCGAExHeatMap5KK.pl?%20cantype=LUAD&correlFile=PPARG%23%23QlWdS8a2H.


##### ImmuCellAI analysis
  The Immune Cell Abundance Identifier (ImmuCellAI) program, http://bioinfo.life.hust.edu.cn/ImmuCellAI, calculates the abundance of 24 immune cells from gene expression datasets obtained by RNA-Seq and microarray data41.

  The 24 immune cells are divided into 18 T-cell subtypes and six other types: B cells, natural killer (NK) cells, monocyte cells, macrophage cells, neutrophil cells, and dendritic cells. The 24 immune cells are divided into two layers: innate immunity, which includes DC, B cells, monocytes, macrophages, NK, neutrophils, CD4 T, CD8 T, NKT, and Tgd. Layer 2 of adaptive immunity includes CD4 naive, CD8 naive, Tc, Tex, Tr1, nTreg, iTreg, Th1, Th2, Th17, Tfh, Tcm, Tem, and MAIT.

  We obtained the expression data for the 24 immune infiltrating cells corresponding to LUAD samples from the ImmuneCellAI website. The revised database includes an R package for retrieving heatmap and pairwise correlation matrix visualizations. The database application is called Tumor Immune Estimation Resource (TIMER 2.0).

  https://cistrome.shinyapps.io/timer/ is a web server that brings together resources for studying immune cell abundance and gene expression in LUAD42. We validated the ImmuneCellAI data using the TIMER 2.0 database and found it to be supportive.

  The GEPIA database, http://gepia.cancer-pku.cn/, provides correlation curves between PPARG expression levels and immune infiltration of tumor-infiltrating lymphocytes, CD8 + T cells, CD4 + T cells, macrophages, neutrophils, and dendritic cells in LUAC.


#### PPARG protein-protein interaction and functional network
  The Protein-Protein Interaction (PPI) network was constructed using GeneMANIA version 3.6.0 http://www.genemania.org/43 Utilizing a massive collection of functional association data to predict PPARG gene function and discover additional genes connected to PPARG, BioGRID4.4 database https://thebiogrid.org/ and STITCH version: 5.0 http://stitch.embl.de/ Protein and genetic relationships, pathways, co-expression, co-localization, and protein-domain similarity are all association data used to draw the rank showing important interacting molecules. The data obtained from GeneMANIA and STITCH for the PPARG network of predicted functional partners met the results obtained from BioGRID4.4 https://thebiogrid.org/111464/summary/homo-sapiens/pparg.html (Accessed April 20th, 2024).

  The data could be visualized through these links:

  GeneMANIA network: https://genemania.org/search/homo-sapiens/pparg.

  STITCH network: http://stitch.embl.de/cgi/network.pl?%20taskId=KpczawHjZzrz.

  BioGRID4.4 network: https://thebiogrid.org/111464/summary/homo-sapiens/pparg.html (Accessed April 20th, 2024).


### Molecular docking
  Polar hydrogens were added to the resulting PDB files44, and docking was carried out using the Molecular Operating Environment (MOE) version 2014.0901 software (Chemical Computing Group Inc., Quebec, Montreal, Canada).

  https://www.chemcomp.com/Research-Citing_MOE.htm.

  We treated the protein to remove repeated chains and water molecules. The MOE QuickPrep methodology was used to refine the structure, 3D protonation, and partial charge calculation using an RMSD gradient of 0.1 kcal/mol and the AMBER10:EHT field.

  In this study, we employed rigid docking to calculate the binding affinity scores (KJ/mol) of pioglitazone and telmisartan to albumin and extracellular exosomes, which serve as carrier proteins for targeted lung medicine administration.

  For the MyoVc carrier protein, we used the SiteFinder | 3D server’s site finder tool45 to find the largest pocket with 57 amino acids, verifying that the tested drugs fit well.

  We used the MOE Dock protocol and its descriptors to establish the optimum postures and binding score values for the drugs under investigation. We ran molecular docking with the MOE default settings, using the triangle matcher as the placement method and London dG as the primary scoring function. We added another refinement step by integrating the stiff docking approach with the GBVI/WSA dG affinity score algorithm46. Furthermore, the test compound’s first docking pose was the best, with the highest binding energy value. The best pose was finally chosen, photographed, and exported as a JPEG.


### MD simulation of telmisartan in cargo binding domain from human MyoVc
  A molecular dynamics simulation of telmisartan was performed for 18 ns, demonstrating the drug’s stability within the cargo-binding region of the human carrier protein MyoVc (PDB code: 4L8T), which is crucial for the exosome’s cargo. Molecular dynamic simulations employed Molecular Mechanics with Generalized Born and Surface Area solvation method (MM/GBSA) to calculate the free energy of ligand binding to proteins (Godschalk et al., 2013).

  The initial PDB files for the optimal pose of the telmisartan compound in complex with the protein were prepared for the run. MD simulations were conducted for 19 nanoseconds at 310 K, equivalent to body temperature, utilizing Nanoscale Molecular Dynamics (NAMD 2.14 Release - Aug 2020) software https://www.ks.uiuc.edu/Research/namd/, which is founded on the Charm + + programming model. The pH was kept at a standard physiological level of 7. We employed the all-hydrogen AMBER99SB force field to accurately represent molecular interactions. The geometry of telmisartan was optimized through quantum mechanics (QM) calculations using Gaussian 16 software https://gaussian.com/gaussian16/, and the Schrödinger equation was solved for the molecule47. The input consists of the coordinates, net charge, and total spin. The outcome comprises the total energy and the wave function, which serve as the basis for calculating all measurable properties of the system.

  The final charges for Telmisartan were assigned to the compound utilizing Antechamber, and the force field parameters adhered to GAFF2 standards48. The general AMBER force field is utilized for rational drug design, as detailed on the official website, ensuring precise modeling of molecular forces. The complex was located centrally within a traditional three-point water model, the TIP3P water cube, with dimensions that provided a minimum 14 Å water buffer surrounding the complex. To replicate physiological conditions, the complex was neutralized and adjusted to a 150 mM ionic concentration of sodium and chloride ions, accomplished by replacing water molecules with the highest electrostatic potential at their oxygen atoms with these ions. The current MD protocol commenced with an initial depreciation of the fully solvated and ionized systems, succeeded by a gradual temperature increase to the target level. We imposed substantial constraints on the protein backbones and bound telmisartan to avoid unrealistic modifications during the initial simulation phases. Following heating, the systems experienced a 1 ns equilibration under periodic boundary conditions, during which energy restraints were gradually lifted. The simulations continued for an additional 17 ns, recording atomic coordinates at intervals of 0.1 picosecond for comprehensive analysis. This experimental method for molecular dynamics provided a controlled simulation environment, essential for accurately investigating the dynamics and stability of the human myosin cargo binding domain and telmisartan complex.


## Results and discussion

### Bioinformatics studies
  This study is part of a bigger project in our group that uses natural products that have been changed into new uses, like prodigiosin, camptothecin, and hinokitiol, to target different types of cancer49–51. The project also uses man-made small-molecule drugs that target signaling pathways in diseases like cancer52,53.

  Two drugs called pioglitazone and telmisartan54 are known to trigger PPARG. This study investigated whether they could help cure lung cancer by using exosomes. Exosomes that cells release could be used to deliver drugs for the focused treatment of certain diseases55,56.

  Before doing any experiments in cells or living things, we used computer analysis, bioinformatics, cheminformatics, molecular modeling, and simulation to guess how the two PPARG agonist drugs would react and interact with their target molecules in lung cancer, as well as with proteins and drug cargo. This assumption was very important before making the drug-exosomal cargo for the lungs. It made sure that it was only taken up by lung cancer cells so that the drug could be given in a controlled and long-term way to create an “effective, personalized, and targeted” (EPT) treatment.


#### Lung cell type enriched transcriptome
  The Human Protein Atlas indicates that the lung has the most group-enriched gene expression similarity to lymphoid tissue, with the PPARG gene being one of the enriched genes expressed in the lung. Table 1 presents the number of genes within each specificity group for the lung cell types.

  Table 1Number of genes in each specificity category in the lung cell types.Lung cell typeNumber of enriched genesTotal number enrichedVery highHighModerateRespiratory ciliated cells5915337681Alveolar cells type 1434148132Alveolar cells type 220122221363Mitotic cells1112616153NK-cells3133955B-cells41611Endothelial cells098897Smooth muscle cells14133663Fibroblasts2864164256Macrophages451105160Neutrophils615247160Mast cells104317T-cells6295489Plasma cells166154185All cell types10614938682422


#### Systematic database mining and enrichment-analyses of PPARG gene expression profile and the prognostic role in lung adenocarcinoma (LUAD)
  Utilizing the UALCAN database37 associated with the GTEx database gateway, we examined the expression levels of the PPARG gene in normal and lung cancer cells, revealing that it is expressed at elevated levels in normal tissues relative to malignant tissues (Fig. 2).

  Figure 2 illustrates PPARG gene expression based on sample type, using TCGA samples to compare primary lung tumors (n = 515) with 59 normal samples, as analyzed by UALCAN, and indicates statistical significance (A). The median gene-level TPM is 19.5 for the lung (green line pointing to 8 o’clock) for 578 samples. (B) The violin plot and (C) the box plot illustrates that the PPARG gene is expressed at higher levels in lung-normal tissue from 59 cases compared to tumor tissue from 515 cases.

  Fig. 2PPARG gene expression based on sample type, from TCGA samples, comparing primary lung tumor (n = 515) to 59 normal samples, by UALCAN, showing statistical significance (A) median gene-level TPM is 19.5 for the lung (green line pointing to 8 o’clock) for 578 samples. (B) violin plot and (C) box plot showing the higher expression of the PPARG gene in lung-normal tissue for 59 cases compared to tumor tissue for 515 cases.

  PPARG gene expression plots (Fig. 3) based on tumor histology (Fig. 3A), tumor stage (Fig. 3B), nodal metastasis (Fig. 3C), and tissue TP53 mutation status (Fig. 3D) verified the significantly higher levels of gene expression in normal lung cells and tissues compared to the different histological features of LUAC and the lung tumor tissues at stages 1–4, respectively. PPARG gene expression was consistently higher in normal cases than in LUAC cases, regardless of whether they had absent or positive lymph nodal metastases and whether their TP53 status was non-mutated or mutated. The data presented in this phase of bioinformatics also demonstrates the role of PPARG gene activation in lung tissue protection against LUAC proliferation and metastases.

  Figure 3. is using TCGA samples, we assessed the transcript/million of the PPARG gene in LUAD according to histological subtypes (A), individual cancer stages (B), nodal metastasis (C), and TP53 mutation status (D). [NOS: Lung Adenocarcinoma—Not Otherwise Specified; Mixed: Lung adenocarcinoma Mixed subtype with transparent cells: lung The condition is known as clear cell adenocarcinoma. LBC Nonmucinous: Lung Bronchioloalveolar Carcinoma. A solid pattern in the lung is a defining feature of non-mucinous adenocarcinoma. Acinar: Lung. Acinar adenocarcinoma, LBC-mucinous: lung bronchoalveolar carcinoma. Mucinous (colloid) Carcinoma Papillary: Lung papillary adenocarcinoma. Mucinous: Lung Mucinous adenocarcinoma. Micropapillary: Lung micropapillary adenocarcinoma. Signet Ring: Lung. Signet Ring Adenocarcinoma. N0: No regional lymph node metastasis; N1: Metastases in 1 to 3 axillary lymph nodes; N2: Metastases in 4 to 9 axillary lymph nodes; N3: Metastases in 10 or more axillary lymph nodes; nodal metastasis is not available for one sample. NX: Eleven samples failed to detect cancer in the neighbouring LN.

  Fig. 3PPARG gene Expression in transcript/million in LUAD based on histological subtypes (A), individual cancer stages (B), nodal metastasis (C), and TP53 mutation status (D), from TCGA samples. [NOS: Lung Adenocarcinoma-Not Otherwise Specified, Mixed: Lung Adenocarcinoma Mixed subtype, Clear Cell: Lung Clear Cell Adenocarcinoma, LBC-Non mucinous: Lung Bronchioloalveolar Carcinoma Non-mucinous, Solid Pattern Predominant: Lung Solid Pattern Predominant Adenocarcinoma, Acinar: Lung Acinar Adenocarcinoma, LBC-Mucinous: Lung Bronchioloalveolar Carcinoma Mucinous, Mucinous: Mucinous (Colloid) Carcinoma, Papillary: Lung Papillary Adenocarcinoma, Mucinous: Lung Mucinous Adenocarcinoma, Micropapillary: Lung Micropapillary Adenocarcinoma, Signet Ring: Lung Signet Ring Adenocarcinoma. N0: No regional lymph node metastasis, N1: Metastases in 1 to 3 axillary lymph nodes, N2: Metastases in 4 to 9 axillary lymph nodes, N3: Metastases in 10 or more axillary lymph nodes, nodal metastasis is not available for 1 sample, NX: cancer in nearby LN cannot be measured in 11 samples.].

  The heatmap of PPARG gene expression in LUAC and other related genes revealed that PPARG is the most important gene associated with LUAC’s poor prognosis, particularly when compared to normal tissue (Fig. 4) from the GEPIA database.

  Fig. 4Heatmap of the expression pattern of PPARG and other input genes in LUAD is positively correlated to the PPARG gene.

  Additionally, ImmuneCellAI41 is used to gather expression data from 24 types of immune infiltrating (TIF) cells in LUAD samples to find and categorize the TIF cell subtype that has strong links to LUAC.

  The new database includes an R tool for retrieving the pairwise correlation matrix (Fig. 5A) and heatmap (Fig. 5B) visualizations. Furthermore, examining the immune infiltration cell abundance in 576 ImmuneCellAI samples (Fig. 5B) revealed high levels of expression of macrophages, NK, DC, and other T-cell subtypes, which is corroborated by results from the TIMER 2.0 database program42. Additionally, the pairwise correlation matrix showed a strong connection between T-cell subtypes, macrophages, and DCs (Fig. 5A).

  Fig. 5Different immune infiltrating cell expression levels in LUAD samples retrieved from ImmuneCellAI. (A) Pairwise correlation values matrix for exploring the immune infiltration cells abundance in 576 samples, and (B) Heatmap presentation of the immune infiltrating cell expression levels in LUAC.

  Accordingly, we studied the correlation of the PPARG gene expression level to the tumor-infiltrating lymphocytes, CD8+, CD4+, macrophages, neutrophils, and dendritic cells in LUAC as an excellent sign for cancer disease prognosis57. Surprisingly, the gene expression was negatively correlated to B cells and positively correlated to CD8 + and CD4 + subtypes of T-lymphocytes in terms of the partial correlation values (Spearman’s rho) obtained from the GEPIA database (Fig. 6).

  Fig. 6Correlation values of PPARG gene expression level (expressed as log2 TPM) with the tumor immune infiltration cells level in LUAD.

  To better understand how the PPARG gene functions in LUAD, we examined critical genes that interact with it via gene-protein linkages and gene-gene links, as well as creating and analyzing a PPI network.

  Therefore, drugs such as pioglitazone and telmisartan can stimulate the PPARG protein, potentially aiding in the destruction of cancer cells58 either by affecting genes or through pathways related to PPARG that were identified via computer analysis (Fig. 7).Fig. 7(A) The GeneMANIA presentation of PPARG’s protein-protein interaction (PPI) network shows networks for physical interactions between genes as pink lines, co-expression as violet lines, predictions as yellow lines, common route pathways as light blue lines, and genetic interactions as green lines. Additionally, shared protein domains were considered when examining these protein relationships. (B) The STITCH presentation of PPARG predicted functional partners’ networks.


### Cheminformatics studies of the repurposed Pioglitazone and Telmisartan

#### In-silico measurement of physicochemical properties and Tox2159
  We used the Admetlab 2.0 online tool to assess the physicochemical features of pioglitazone and telmisartan, such as logP (lipophilicity) and TPSA (topological polar surface area). We also investigated how well the drugs bind to plasma proteins, their ability to cause breathing problems, their effects on mitochondrial membrane potential, aromatase enzyme activity, aryl hydrocarbon receptor activity, human liver toxicity, and liver injury caused by drugs used to treat the same drugs.

  According to the results in Table 2, pioglitazone (logP = 3.01) and telmisartan (logP = 6.249) are both effective in mixing with fats, but telmisartan performs better. The TPSA values for pioglitazone (68.290 Å²) and telmisartan (72.940 Å²) indicate that these drugs can mix with lipids, but not adequately enough to pass through the blood-brain barrier, keeping them safe from possible side effects in the central nervous system. The TPSA values of pioglitazone (68.290 Å²) and telmisartan (72.940 Å²) revealed that these test drugs are lipophilic but not adequate to penetrate the blood-brain barrier (BBB), making them safe regarding any potential central nervous system (CNS) side effects62,63. These findings also demonstrated that telmisartan and pioglitazone may be employed efficiently in targeted delivery systems based on various fat-loving materials, such as albumin and lung exosomes (Lung-Exo), without producing any physical problems.

  Based on computer estimates of how dangerous compounds are from the Tox21 Data Challenge, which is part of the NIH and FDA’s “Toxicology in the 21 st Century” initiative, we determined that pioglitazone, like telmisartan, affects SR-MMP activity (Table 2). Notably, investigations have demonstrated that pioglitazone causes mitochondrial damage, supporting the predictions (Table 2). Interestingly, experimental evidence64 reveals that pioglitazone’s mitochondrial toxicity fits expectations (Table 2). The test compounds demonstrated activity on NR-Aromatase and NR-AhR, both of which are part of the TOX21 pathway. The projected results (Table 2) indicated that pioglitazone and telmisartan had the potential to cause hepatotoxicity and drug-induced liver damage. Some experimental research65,66 demonstrated pioglitazone’s ability to generate hepatic energy alterations, which validated the data given in Table 2.

  Table 2The predicted physicochemical property and TOX21 of Pioglitazone and Telmisartan.ParameterPioglitazoneTelmisartanComment LogP (W/O) 3.0216.249Optimum TPSA (Å 2 ) 68.29072.940Lipophilic PPB 97.171%98.951%Strong binder Respiratory Toxicity ----Non-toxic SR-MMP ++++Active NR-Aromatase +++++Active NR-AhR ++Active H-HT +++++Hepatotoxic DILI ++++++Hepatotoxic[LogP: partition coefficient, o/w: octanol/water, TPSA: topological polar surface area, PPB: Plasma Protein Binding, SR-MMP: Mitochondrial Membrane Potential, NR-AhR: nuclear receptor-aryl hydrocarbon receptor, H-HT: human hepatotoxicity, DILI: drug-induced liver injury.].


#### Pioglitazone and Telmisartan biological targets of the highest corresponding probabilities
  Using the Swiss Target Predictor67,68, we discovered that pioglitazone and telmisartan are likely to interact with various biological targets, including receptors, enzymes, and transporter proteins (Table 3). Both drugs were shown to influence the liver bile salt export pump, the kidney enzyme carbonic anhydrase II (CA2), and the lung angiotensin-converting enzyme (ACE). The interactions match the known harmful effects of pioglitazone65,66 and telmisartan69 along with the expected information from Admetlab 2.060,61 about liver toxicity and damage (Table 2). The predictor determined that both drugs target the type-1 angiotensin II receptor (AGTR1) (Table 3). The findings imply that pioglitazone should be investigated for its potential as an AGTR1 binder, which could shed light on the structural properties that allow both telmisartan and pioglitazone to have the pharmacological effects of PPARG agonists and possibly AGTR1 antagonists.

  Table 3Predicted Pioglitazone and Telmisartan biological targets of the highest probability.DrugTargetCommon NameCHEMBL ID Pioglitazone PPARGPeroxisome proliferator-activated receptor gammaCHEMBL235MAOBMonoamine oxidase BCHEMBL2039CA2Carbonic anhydrase IICHEMBL205AGTR1Type-1 angiotensin II receptorCHEMBL227PPARAPeroxisome proliferator-activated receptor alphaCHEMBL239ABCB11Bile salt export pumpCHEMBL6020 Telmisartan ACEAngiotensin-converting enzymeCHEMBL1808AGTR1Type-1 angiotensin II receptorCHEMBL227PPARGPeroxisome proliferator-activated receptor gammaCHEMBL235AGTR2Angiotensin II receptorCHEMBL4607GLRA1Glycine receptor subunit alpha 1CHEMBL5845


#### Prediction of Pioglitazone-PPARG, Telmisartan-PPARG nuclear receptor affinity and ligand efficiency
  The Zinc20 database70,71 provided numerical values for how well pioglitazone (pKi = 7.06) and telmisartan (pKi = 5.82) bind to their targets, supporting earlier findings that classify pioglitazone as a PPARG agonist and telmisartan as a partial agonist23. Additionally, the ligand efficiency values from the database show the binding strengths of pioglitazone (0.41) and telmisartan (0.21).

  Table 4Predicted Pioglitazone and Telmisartan binding affinity and ligand efficiency.DrugGene NameClasspKi (L.E.) Pioglitazone PPARG (agonist)Transcription factor/NR7.06 (0.40) Telmisartan 5.82 (0.21)

  The cheminformatics data in this study for pioglitazone and telmisartan highlights the need to create these helpful drugs in lung-derived extracellular vesicles (Lung-Exo) or inhalable exosomes for targeted delivery to lung cells, to reduce the known side effects of the repurposed drugs, and to enhance their effectiveness.


### Affinity and stability studies of pioglitazone and telmisartan into the protein carrier vehicle used for lung-targeted delivery
  Molecular docking and dynamics (MD) simulations are used to evaluate how well the repurposed drugs stick to their carrier vehicles and to check if the complex remains stable as it travels from where it is given to where it works.


#### Molecular docking studies of pioglitazone and telmisartan into the carrier vehicle used for lung-targeted delivery
  Albumin has been selected as a universal carrier for hydrophobic pharmaceuticals. The diverse human cargos act as vesicles that associate with the canonical non-muscle Myosin V (MyoV) carrier, specifically its paralog VC (MyoVC) or Myo5C, which is involved in cell membrane trafficking and the intracellular transport of cargos, including exosomes, according to KEGG.

  To evaluate the binding affinity scores of pioglitazone and telmisartan to human serum albumin and extracellular exosome carrier protein for targeted pulmonary drug delivery, the albumin protein carrier was sourced from the RCSB Protein Data Bank (RCSB PDB) under PDB code 1HK1, which represents human serum albumin (HSA) complexed with thyroxine (3,3’,5,5’-tetraiodo-l-thyronine)72. The cargo binding domain from human MyoVC was obtained from the Peptide Atlas73 with PDB code 4L8T, which does not contain a crystallized ligand74.

  We identified the optimal location within the cargo-binding domain of the transporter protein to accommodate the tested pharmaceuticals, enabling an assessment of their compatibility following docking simulations. We selected the pocket with the highest amino acid content and largest dimensions to ensure compatibility with the shape of the target medicines for docking. The pocket selected exhibited the highest amino acid count and largest dimensions, thereby ensuring compatibility with the contoured surface of the target medicines for docking. Conversely, we incorporated these two medications directly into the albumin carrier to facilitate the targeted delivery of thyroxine (T4) within the body.

  The docking results demonstrated that both pioglitazone and telmisartan exhibit strong binding to MyoVc and albumin carriers (Fig. 8), indicating that their interactions with the amino acids at the binding sites of these proteins contribute to the observed high-affinity scores. The findings demonstrate that both drugs effectively treat lung cancer, necessitating reduced doses and less frequent administration. Additionally, the human MyoVc cargo-binding domain transporter can deliver telmisartan to lung tissues for cancer therapy. Our findings indicate that pioglitazone exhibits weaker binding and attraction at the albumin site, suggesting it is less stable compared to telmisartan.

  Figure 9 presents 2D-style docking solutions for pioglitazone, telmisartan, and T4 within the cargo domain of MyoVc (PDB entry 4L8T) vesicles (exosomes) in the upper panel and albumin (PDB entry 1HK1) in the middle panel, alongside albumin complexed with T4 (the original ligand) in the lower panel. The three-letter and digit protein sequence code denotes amino acid residues, whereas the green and blue dotted lines classify contact forces following the figure’s descriptive scheme.

  Fig. 8Affinity in complex with Cargo domain of MyoVc (pdb entry 4L8T) vesicles (exosomes) (upper panel) and in complex with albumin (pdb entry 1HK1) (middle panel) compared to albumin carrying T4 (the original ligand) (lower figure). Blue and green dotted arrows and green dots present hydrophobic interactions and hydrogen bonding forces.


#### MD simulation of telmisartan in complex with cargo binding domain from human MyoVc
  We ran molecular dynamics simulations of the telmisartan-human MyoVc cargo-binding domain complex to study how the protein behaves and changes at the atomic level for 18 nanoseconds. The intricate system reached equilibrium within 1 ns, demonstrating stable atomic fluctuations within 17 ns of the simulation’s duration. This verifies that the simulation time was adequate for the aims of the present investigation, designated as a “TDDS study75”.

  Solvation and Equilibration of the Complex

  Figure 9 presents a comprehensive structural analysis of the protein-ligand complex, showcasing the solvated human MyoVc cargo binding domain in conjunction with the Telmisartan complex, along with the equilibrated states of the protein-ligand complex collected at different phases of the simulation. The subsequent perspective of the complex illustrates various approaches to examining the simulated conditions of the protein-ligand complex (MyoVc-telmisartan).

  Fig. 9Human MyoVc Cargo Binding Domain and Telmisartan Solvated (upper panel) complex top and side views and equilibrated complex (lower panel) shown in a carton view or with a white surface view with Telmisartan in blue within the pink binding pocket.

  Root-Mean Square Deviations (RMSD)

  An essential component of our research entailed examining the stability and conformational alterations of the complex, protein, and ligand separately. Figure 10 displays the RMSD values for the complex, protein, and ligand, respectively. These graphs illustrate three separate stages in the execution of molecular dynamics simulations.

  The initial phase, lasting 2 ns, includes 50,000 steps of energy minimization. A 0.5 ns duration of incremental heating elevates the system to ambient temperature. We then utilized a 1 ns equilibration phase to steady the system. The concluding step of our simulation method was a prolonged (17 ns) duration of production molecular dynamics simulations, during which the most notable dynamic characteristics of the complex were observed and assessed.

  The RMSD analysis of MD simulations for the protein transporter complex (Fig. 10A), apoprotein (Fig. 10B), and ligand (Fig. 10C) showed that telmisartan can likely stay attached to the human MyoVc cargo-binding domain at the specific pocket shown in Fig. 8.

  Fig. 10The RMSD graph for the human (A) MyoVc Cargo Binding Domain and Telmisartan complex, (B) MyoVc Cargo Binding Domain protein only, and (C) Telmisartan.

  Beta Factor Analysis of Protein Backbone Atoms

  To demonstrate the flexibility of the protein backbone atoms and the interactions of telmisartan with the human MyoVc cargo-binding domain within the binding site76, we assessed the beta factor of the protein complex throughout molecular dynamics simulations concerning the positions of the protein residues77. The highest beta factor values, illustrated in the beta factor plot (Fig. 11), were observed at residue numbers 155–180 (auth: 1450–1475), indicating concordance with the contact force established with His 155 (auth: His 1450), as represented by the extracted docking solution of Telmisartan (Fig. 8). Additionally, various protein residue numbers exhibited significant changes in atomic motion during the simulation compared to the initial atomic trajectories at 30–40 (auth: 1325–1335), 105–115 (auth: 1400–1410), and 300–345 (auth: 1595–1640). The graphical representation of the beta factor for the protein complex (Fig. 11) confirmed the flexibility of the protein transporter’s active site in the presence of telmisartan and its atomic interactions. Previous research has investigated the anti-lung cancer effects of TZDs in clinical settings; however, the most effective PPARG agonist, rosiglitazone, exhibits specific undesirable effects, unlike pioglitazone. The side effects of the partial PPARG agonist, telmisartan, are infrequent; however, its gene expression profiles confer superior anti-tumor benefits. In the present study, telmisartan was recognized as an appropriate candidate for the “Beta Factor Analysis” of the human MyoVc cargo binding domain protein during molecular dynamics simulations, which elucidated the stability and flexibility of the MyoVc protein-drug complex and its interaction dynamics with telmisartan.

  Fig. 11The average atomic fluctuations (Beta Factor) of the Human MyoVc Cargo Binding Domain protein during the molecular dynamic simulations.


## Conclusion
  The activation of the PPARG transcription factor is linked to reduced NSCLC growth. Research indicates that pioglitazone and telmisartan are potential therapies for NSCLC due to their PPARG-agonistic properties. There is a critical need for new targeted drug delivery formulations for these drugs to minimize systemic toxicity. The study suggests using extracellular vesicles from lung tissue for targeted drug delivery to pulmonary cancer cells. Bioinformatics and cheminformatics data support pioglitazone and telmisartan as promising repurposed drugs for LUAC, highlighting their lipophilicity and compatibility with exosomal components like albumin. Cheminformatics also pointed out potential off-target effects and hepatotoxicity, emphasizing the importance of exosomal targeted delivery. Molecular docking and MD simulations confirmed the affinity and stability of drug-exosomal vehicle complexes. The proposed engineering of exosomal cargo for targeted delivery of these drugs to lung cells could enhance NSCLC treatment and address drug resistance while minimizing systemic toxicity. Finally, the study’s computational technique saves the researchers time and money when building formulations containing biological components for targeted drug delivery.

  Nonetheless, experimental validation is on the way as the sustainability of the current manuscript, to emphasize the success of the suggested formulation based on computational work (a limitation).

  Recommendation. Repurposing PPARG-agonist drugs with or without co-supplementary vitamins with tumor-modulatory effects and positive impact on various disease metabolic/inflammatory pathways as vitamin D78 would be crucial point to study as well.


## Acknowledgements
  PROTAC Scientific, Drug Discovery Pro LLC as well as the Molecular Operating Environment (MOE) software (Chemical Computing Group Inc., Quebec, Montreal, Canada).