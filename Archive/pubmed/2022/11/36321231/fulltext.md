# Molecular Mechanisms of Notopterygii rhizoma Et Radix for Treating Arrhythmia Based on Network Pharmacology


## Objective
  To explore the possible mechanism for treating NRR in arrhythmia using network pharmacology and molecular docking in this study.


## Methods
  Active compounds and targets for NRR were retrieved from the Traditional Chinese Medicine Systems Pharmacology (TCMSP) Database and Analysis Platform, SymMap, and the Encyclopedia of Traditional Chinese Medicine (ETCM) databases. Arrhythmia-related genes were acquired from the Comparative Toxicogenomics Database (CTD) and the GeneCards database. Overlapping targets of NRR associated with arrhythmia were acquired and displayed via a Venn diagram. DAVID was applied for GO and KEGG pathway analyses. Cytoscape software and its plug-in were used for PPI network construction, module division and hub nodes screening. AutoDock Vina and qRT-PCR were carried out for validation.


## Results
  In total, 21 active compounds and 57 targets were obtained. Of these, coumarin was the predominant category which contained 15 components and 31 targets. There were 5 key targets for NRR in treating arrhythmia. These targets are involved in the apoptotic process, extrinsic apoptotic signaling pathway in the absence of ligand, and endopeptidase activity involved in the apoptotic process by cytochrome c. The main pathways were the p53 signaling pathway, Hepatitis B and apoptosis. The molecular docking and qRT-PCR displayed good effects on hub node regulation in NRR treatment.


## Conclusion
  NRR plays an important role in anti-apoptotic mechanisms that modulate the p53 signaling pathway, which may provide insight for future research and clinical applications focusing on arrhythmia therapy.


## INTRODUCTION
  Ventricular arrhythmias are a major cause of morbidity and mortality in patients with heart disease [1]. It can manifest as asymptomatic premature ventricular contractions (PVCs) or non-sustained ventricular tachycardia (VT), and its symptoms include arrhythmia, or continuous ventricular tachycardia, ranging from patients presenting with mild symptoms to complete hemodynamics collapse [2, 3]. Medications, catheter ablation, or an embedded cardioverter-defibrillator can be used to treat arrhythmias. Unfortunately, many patients are prone to recurrence after surgery, and their symptoms persist [3]. Complementary and alternative therapies have unique advantages and potential in treating arrhythmias [4]. Different from the past model of “single-gene, single-target and single-drug,” the characteristic of the “multi-component, multi-target and multi-pathway” of traditional Chinese medicine has promoted the transformation of the drug discovery paradigm [5, 6]. Notopterygii rhizoma et Radix (NRR) is an important constituent of traditional Chinese medicine [7]. It is derived from the dried roots and rhizomes of Notopterygium incisum Ting ex H. T. Chang (N. incisum) and Notopterygium franchetii H. de Boiss. (N. franchetii), belonging to the Apiaceae family [8]. Many experiments have shown that NRR can help prevent arrhythmia [9-11]; however, its mechanisms are still unclear.

  Currently, the main approaches of drug design include pharmacophore linking strategy [12], structure-based and ligand-based [13, 14], and fragment-based [15] drug discovery. In addition, molecular databases [16] (such as Protein Data Bank database, KEGG database, Comparative Toxicogenomics database, PubChem Bioassay database, etc.) and computer-aided [17, 18] (such as artificial intelligence) methods can be used for pharmacological studies. The related studies of Chinese herbs and formulas are increasing [19, 20]. In this study, we combined systems biology, network pharmacology, molecular docking, and experimental validation to elucidate the possible mechanism of action of the drugs. The flowchart of this research is shown in (Fig. 1).


## MATERIALS AND METHODS

### Screening of Active Ingredients
  The Traditional Chinese Medicine Systems Pharmacology (TCMSP, https://tcmspw.com/index.php) Database and Analysis Platform, SymMap (http://www.symmap.org/), and the Encyclopedia of Traditional Chinese Medicine (ETCM, http://www.tcmip.cn/ETCM/index.php/Home/Index/) databases were searched to collate information regarding each of the chemical compounds within NRR [21-23]. The effective compounds were filtered based on their pharmacokinetic properties, including oral bioavailability (OB) ≥30% and drug-likeness (DL) index ≥0.18. Furthermore, the two/three-dimensional (2/3D) structures, canonical smiles and PubChem ID of the active compounds were acquired using the PubChem (https://pubchem.ncbi.nlm.nih.gov/) database. The resulting data was standardized using the Universal Protein Database (UniProt, https://www.uniprot.org/). The Protein Data Bank identification (PDB ID) was acquired from the database of PDB (https://www.rcsb.org/).


### Identification of Arrhythmia-associated Targets and Collection of Putative Target Proteins
  The Comparative Toxicogenomics Database (CTD, http://ctdbase.org/) [24] and GeneCards (https://www.gene cards.org/) [25] databases were applied to identify potential targets relating to arrhythmia, including ventricular premature beat (VPB), VT and ventricular fibrillation (Vf). Arrhythmia-associated genes were screened using scores >50% of CTD and 30% of GeneCards as cutoffs, respectively. The candidate targets for NRR and arrhythmia were further used and pooled to enable Venn analysis, which was used to obtain the targets for NRR-achieved anti-arrhythmia.


### Construction of Protein-Protein Interaction (PPI) Network and Topological Analysis
  The merged targets of NRR and arrhythmia were used to construct a PPI network via search tools for recurring instances of neighboring genes (STRING) database (v11.5) (https://www.string-db.org/). These used active interaction sources from text mining, experiments, databases, co-expression, neighborhood and gene fusion, and the raw data were saved in a tab-separated values (TSV) format. The Analyze Network tool of Cytoscape 3.8.2 was used to calculate the topological parameter [26]. The plugin MCODE (molecular complex detection) was used for module division; CytoHubba was applied to detect the core targets based on the maximal clique centrality (MCC) algorithm.


### GO and KEGG Enrichment
  The GO (Gene Ontology) and KEGG (Kyoto Encyclopedia of Genes and Genomes) enrichment analysis of overlapping target and core targets were carried out through the Database for Annotation, Visualization and Integrated Discovery (DAVID) v6.8 (https://david.abcc.ncifcrf.gov/) [27-28]. The following settings were applied: background and species = Homo sapiens, expression analysis systematic explorer = 0.01 and count = 2. P < 0.05 indicated a statistically significant difference in the annotation categories.


### Molecular Docking
  Small molecule ligand 2D structures of key active compounds were obtained from the PubChem database (https://pubchem.ncbi.nlm.nih.gov) and saved in an SDF format. These were then converted into 3D structures and optimized using the ChemBio3D Draw module in Chem Bio Office2010 software. Crystal structures of the five core receptors were downloaded from the PDB. The filter criteria were set as follows: (1) the protein structure is obtained by X-crystal diffraction; (2) preferential selection of protein structures reported in the literature of molecular docking; (3) the organism comes from Homo sapiens. The protein visualization software Pymol (v2.0) was used to remove ligand and water motifs. The AutoDockTools (v1.5.6) software was applied to process proteins, including adding nonpolar hydrogen, calculating the Gasteiger charge, assigning the AD4 type, and setting all the flexible bonds of small molecule ligands to be rotatable. Then the docking box was modulated based on the original ligand coordinates. Furthermore, the receptor protein was set as rigid docking, the genetic algorithm was selected, and the maximum number of evals was set as the medium. The docking results were acquired by running autogrid4 and autodock4, revealing the binding energies. The partial diagrams of molecular docking were then produced using the Pymol.


### Experimental Validation

#### Experimental Model and Drug Treatment
  NRR granular was purchased from the Granule Dispensing Department of Dongzhimen Hospital, Beijing University of Chinese Medicine. Calcium chloride was purchased from Sino Animal(Beijing)Science and Technology Development Co. Ltd (Beijing, China).

  The experimental procedures used in this study were approved by the Animal Welfare Ethics Committee of Sino Animal (Beijing) Science and Technology Development Co. Ltd. and were per the U.S. National Institutes of Health (NIH) guidelines (Publications No. 8023). Eighteen 8-week-old SD male rats were obtained from SPF (Beijing) Biotechnology Co., Ltd. [experimental animal license No. SYXK (Beijing), 2020-00 51]. The rats were placed in polycarbonate cages under a 12-h light/dark cycle, in an air-conditioned room, under a constant temperature (25 ± 1 °C) and humidity (50 ± 10%), with an SPF grade. The 18 mice were randomly divided into three groups: sham (deionized water), vehicle (deionized water) and NRR (NRR granule,19.08 mg/100g, 0.5ml/100g). Following a 14-day gavage period, on the 14th day, the rats were anesthetized for 30 minutes via intragastric administration. Anesthesia was induced via inhalation of 4% isoflurane and maintained with 2% isoflurane, and then linked electrocardiograph (ECG) leads were positioned. The IV lead electrocardiogram output was recorded using the PowerLab biological signal processing system. Once the electrocardiogram had stabilized, the sham rats were each injected with saline (0.9% NaCl, 1.5ml/min/kg) through the tail vein. The vehicle and NRR rats were injected with a calcium chloride solution (1.5ml/min/kg, concentration 35mg/ml) via the tail vein. The electrocardiogram output was recorded for 10 min, and arrhythmia was observed. The left cardiac myocardium (left ventricle) was frozen for analysis.


#### Quantitative Real-time PCR
  Five rats from each group were used for qRT-PCR experiments. Total RNA was extracted from the left cardiac myocardium using TRIzol (Tiangen Biochemical Technology, Beijing, Co., Ltd) and reverse transcribed into cDNA using a reverse transcription system kit (Takara, Shanghai, China) per the manufacturer’s protocol. qRT-PCR was performed on an ABI 7500 Real-Time PCR System (Applied Biosystems, Foster City, USA) using the SYBR Green PCR Kit to determine mRNA expression levels. The relative expression levels of CASP3 (primers: GCGGTATTGAGACAGACAGTGGA and ACGAGTGAGGATGTGCATGAATT), CASP8 (primers: TTTCTGTTTTGGATGAGGTGAC and ATGTTGCTGAGTTTGGGTATGT), CASP9 (primers: GCGACATGATCGAGGATATTC and CAGGTGGTCTA GGGGTGTAAC), BAX (primers: GGTGGTTGCCCTTT TCTACTTTGC and GCTCCCGGAGGAAGTCCAGTG), CDK2 (primers: CCCTGTCCGTACTTACACTCAT and CTTGGGGAAACTTGGCTTATA) were analyzed using the comparative CT method for relative quantitation and the 2-DDCt method, which involved the levels against β-actin expression. The relative expression data was presented as a percentage change compared to the matched controls. All of the quantitative data, obtained from at least three independent experiments, were presented as the mean ± standard error of the mean. SPSS statistical software version 27.0 (IBM Corp., Armonk, NY, USA) was used for statistical analysis. Student’s t-test was used to compare two groups, whereas a one-way analysis of variance was used to compare all three groups. P values lower than 0.05 were considered statistically significant.


## RESULTS

### Active Compounds and Target Genes Detection
  185, 235 and 58 components were obtained from the TCMSP, SymMap and ETCM databases, respectively. After their pharmacokinetic properties were screened and duplications removed, 21 active components remained. These were divided into five categories: 15 coumarins (e.g., Cnidilin, Ammidin, Phellopterin, etc.), 1 flavonoid (Diosmetin), 1 nitrogen-containing compound (Isoindigo), 2 triterpenoids (beta-sitosterol and Sitosterol) and 2 others (Fig. 2). The details of the 21 compounds are presented in Table S1. The targets were predicted using the UniProt database. This analysis identified 159 putative targets, including 105 in coumarin, 10 in flavonoid, 3 in nitrogen-containing compounds, 40 in triterpenoids and 1 in ‘others.’ A compound-target network was constructed, as shown in (Fig. 3). Eventually, 57 targets for NRR against arrhythmia were obtained.


### Putative NRR Target Proteins in Arrhythmia
  In total, 96342 and 5584 arrhythmia-associated genes were acquired from the CTD and GeneCards databases. Following prioritized inference and relevance scores, 452 and 97 genes were identified (Tables S3 & S4). Once data from the two databases had been integrated, 265 targets remained and were considered the key putative arrhythmia-associated proteins. As shown in the Venn diagram, a total of 19 overlapping genes for NRR and arrhythmia were obtained (Fig. 4A), including CDK2, BAX, CASP3, and others, which were taken as the key targets for treating arrhythmia with NRR.


### PPI Construction and Hub Genes Identification
  A function-associated protein network of the interactions between NRR and arrhythmia was constructed, which included 19 nodes and 40 edges (Fig. 4B). The topological parameters were analyzed based on Analyze Network (Table S5). Only one module was divided through MCODE, considered the core module (Fig. 4C). Furthermore, core proteins were identified via CytoHubba, including CASP3 (caspase 3), CASP8 (caspase 8), CASP9 (caspase 9), CDK2 (cell division protein kinase 2) and BAX (an apoptosis regulator BAX). These core targets all belonged to the core module (Fig. 4D).


### Biological Function of NRR Targeting for Arrhythmia
  In order to gain further insights into the mechanisms underlying the effect of NRR effects on arrhythmia at a systematic level, GO, and KEGG pathway analyses were carried out. There were 141 GO terms and 31 KEGG pathways enriched from the 19 overlapping targets (Tables S6 & S8), and 33 GO terms and 16 KEGG pathways enriched from 5 core targets (Tables S7 & S9). The GO-biological processes were mainly related to drug response, lipopolysaccharide and estradiol responses, the extrinsic apoptotic signaling pathway in the absence of ligands, and the apoptotic process. Fifteen pathways were consistently enriched in the overlapping and core targets. The top 3 pathways enriched by the five core targets were the p53 signaling pathway hepatitis B and apoptosis. A drug-compound-targets-pathways network was also built based on the KEGG enrichment analysis (Fig. 5).


### Molecular Docking
  It is possible to predict the affinity between the two counterparts by calculating the binding energy. Ten active NRR compounds exhibiting good pharmacokinetic properties were molecularly docked with five core receptors, including CASP3 (PDBID: 1NME), CASP8 (PDBID: 2K7Z), CASP9 (PDBID: 3V3K), BAX (PDBID: 2LR1), and CDK2 (PDBID: 2R3J). A binding energy of less than 0 indicates that two molecules combine spontaneously-the lower the binding energy, the stronger the affinity of the compounds to the targets. A total of 50 ligand-receptor combinations were computed. Most NRR components could bind well with the key receptors, and 44 combinations had affinities of < -7kcal/mol, accounting for 88% of the combinations. CDK2 and C9 had the strongest binding energy, at -9.7 kcal/mol. The molecular binding results are shown in (Fig. 6). p53 signaling pathway was exhibited in (Fig. 7).


### Experimental Validation of the NRR Targets for Treating Arrhythmia
  The ECG of the sham, vehicle and NRR-treated groups are shown in (Fig. 8). CASP3, CASP8, CASP9, BAX and CDK2 mRNA expression levels were all consistently altered in individual samples between the sham, vehicle and NRR groups. Expression levels of CASP3, CASP8, CASP9, BAX and CDK2 were upregulated following arrhythmia, whereas CASP3, CASP8, CASP9, BAX and CDK2 were downregulated following a 14 days NRR treatment regime.


## DISCUSSION
  In this study, a network pharmacology analysis was conducted on the active components of NRR in relation to arrhythmia disease targets. The ingredients contained in NRR mainly included coumarin, flavonoids, nitrogen-containing compounds, and triterpenoids, among which coumarin was the primary category. The results showed the detection of ultra-high performance liquid chromatography coupled with triple quadrupole mass spectrometry (UHPLC–MS/MS) [29]. Previous studies also verified that the aqueous solution of NRR exerts an anti-arrhythmic effect [30, 31]. The Biological processes of the NRR proteins associated with arrhythmia were involved in various apoptotic processes, such as endopeptidase activity involved in the apoptotic process by cytochrome c and in the extrinsic apoptotic signaling pathway when ligands are absent. Moreover, the p53 signaling pathway may be closely associated with mechanisms of action of the NRR proteins when it is used to treat arrhythmia.

  In order to further investigate the mechanisms, module division was conducted to find the core genes using MCC in our work. CASP3, CASP8, CASP9, BAX and CDK2 were identified from the module involved in p53 signaling. In addition, molecular docking results also exhibited that these genes had good binding properties with the core target genes. Clinical studies have shown that BAX expression was increased in cardiovascular patients, including those with arrhythmia [32], and patients with caspase3 variants were susceptible to atrial fibrillation (AF) [33]. Experimental research has shown that the expression of BAX was associated with AF [34], and the disturbance balance of Bcl-2/BAX expressions may be related to the development and maintenance of AF and plays a major role in structural remodeling of the atrium [35, 36]. Myocardial apoptosis can cause electrical and structural cardiac remodeling [37], and many important apoptotic factors, such as the expression of CASP8, CASP9, and BAX in the present experiments, are altered in many cardiovascular diseases (including ischaemia/ reperfusion [38], AF [33] and ventricular fibrillation (Vf) [37]). Oxidative stress can cause apoptosis, leading to cardiac and vascular abnormalities in different types of cardiovascular disease, and its mechanism may be related to the dysregulation of the Akt/p53 signaling pathway [39]. Another experimental study indicated that pioglitazone inhibited age-related arrhythmogenic atrial remodeling and AF perpetuation by enhancing antioxidant capacity and inhibiting the mitochondrial apoptotic signaling pathway [40]. Additional studies in animal models of ventricular fibrillation have manifested that mitochondrial damage leads to activation of the mitochondrial apoptotic pathway, characterized by the release of cytochrome c into the cytoplasm, reduction of the level of CASP9, activation of CASP3 and was in line with a significant decrease in left ventricular function [41]. In summary, our findings offer new insights into future NRR research and its applications for treating arrhythmia. However, apoptosis is a complicated process multiple targets regulate that. Although our results were verified by qRT-PCR, differing components and doses needed to be assessed in future studies to understand the processes in more detail.


## CONCLUSION
  Here, we applied systematic pharmacology to investigate the potential mechanisms underlying the effects of NRR on arrhythmia. The analysis of modules and core nodes helped to locate the possible major functional genes. Our data has shown that NRR, especially in main components (coumarin and triterpenoids), plays an anti-apoptotic role via multiple apoptotic factors/pathways. The targets were mainly aimed at the downstream of the p53 signaling pathways, which may prove to be its mechanism against arrhythmia. Moreover, our research was previously published as a preprint at Research Square [42].


## SUPPLEMENTARY MATERIALS

## AUTHORS’ CONTRIBUTIONS
  Hongxu Liu and Juju Shang contributed to the conception or design of the work. Wen long Xing revised the manuscript; Yupei Tan is responsible for data collection, and Penglu Wei drafted the manuscript. The final contribution was read and approved by all the authors.


## ETHICS APPROVAL AND CONSENT TO PARTICIPATE
  The Animal Welfare Ethics Committee of Sino Animal (Beijing) Science and Technology Development Co.Ltd reviewed and approved the animal study. (Publications No. 8023).


## HUMAN AND ANIMAL RIGHTS
  No animals were used. Animal experimentation was per the U.S. National Institutes of Health (NIH) guidelines.


## CONSENT FOR PUBLICATION
  Not applicable.


## AVAILABILITY OF DATA AND MATERIALS
  The datasets used and/or analysed during the current study are available from the corresponding author [JS and HL] upon reasonable request.


## FUNDING
  This work was supported by Grants from the National Natural Science Foundation of China (No. 81273741) and the China Postdoctoral Science Foundation (No.2021M702311).


## CONFLICT OF INTEREST
  The authors confirm that this article content has no conflict of interest.


## ACKNOWLEDGEMENTS
  Declared none.