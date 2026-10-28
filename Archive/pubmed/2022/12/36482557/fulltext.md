# Network-based pharmacology and molecular docking exploring the “Bupleuri Radix-Scutellariae Radix” mechanism of action in the viral hepatitis B treatment


## Abstract
  Viral hepatitis B is caused by the hepatitis B virus, which is characterized by liver lesions. Bupleuri Radix and Scutellariae Radix are the main traditional medicine pairs with remarkable efficacy in hepatitis B. However, their molecular mechanisms are incompletely understood. The main active components of Bupleuri Radix and Scutellariae Radix, as well as therapeutic targets for the treatment of hepatitis B, were identified through network pharmacology techniques. We identified viral hepatitis B targets using the GeneCards, online mendelian inheritance in man, and therapeutic target databases. We discovered the active components of Bupleuri Radix and Scutellariae Radix as well as therapeutic targets using the encyclopedia of traditional Chinese medicine, HERB, traditional Chinese medicine systems pharmacology database, and a bioinformatics analysis tool for molecular mechanism of traditional Chinese medicine databases. VENNY obtained the intersections. Cytoscape and STRING were used to create the “active ingredient-potential target” network and protein interaction network. The DAVID database was used to enrich GO and KEGG pathways. The results were confirmed using the molecular docking method. There were 1827 viral hepatitis B targets, and 37 active ingredients for Bupleuri and Scutellariae Radix, with the main components being quercetin, wogonin, baicalein, and kaempferol. Tumor necrosis factor (TNF), mitogen-activated protein kinase 3 (MAPK3), interleukin-6 (IL-6), vascular endothelial growth factor A, cysteinyl aspartate specific proteinase 3, transcription factor AP-1 (JUN), RAC-alpha serine/threonine-protein kinase, and cellular tumor antigen p53 are among the 78 common targets of Bupleuri Radix and Scutellariae Radix intervention in viral hepatitis B. KEGG enrichment resulted in 107 pathways, including cancer, hepatitis B, and TNF signaling pathways. According to the molecular docking technique, quercetin, wogonin, baicalein, and kaempferol had strong binding activities with TNF, MAPK3, and IL-6. In this study, we initially identified various molecular targets and multiple pathways involved in hepatitis B treatment with Bupleuri Radix and Scutellariae Radix.


## 1. Introduction
  Viral hepatitis B is characterized by discomfort, gastrointestinal symptoms, yellow urine, hepatomegaly, and abnormal liver function, which is caused by the hepatitis B virus (HBV) infection.[1] According to epidemiological studies, approximately 257 million people worldwide have chronic hepatitis B virus infection, and approximately 900,000 people die each year from HBV-related diseases.[2] Current hepatitis B treatment strategies include antiviral drugs (e.g., entecavir, propofol tenofovir fumarate tablets) and immune intervention (e.g., pegylated interferon-alpha), both of which have limitations such as immune tolerance, high cost, and side effects.[3,4] As a result, hepatitis B treatment requires a more secure and effective strategy.

  Traditional Chinese medicine (TCM) has been used to treat hepatitis for over 2000 years, and Xiaochaihu Decoction has played an important role in inhibiting viral replication, controlling liver inflammation, and resisting liver fibrosis, of which “Bupleuri Radix (BR, Chai Hu in Chinese)-Scutellariae Radix (SR, Huang, Qin in Chinese)” is particularly effective.[5,6] Experimental studies have shown that Bupleuri Radix and Scutellariae Radix can treat hepatitis B by repairing liver cell damage, reducing the liver inflammatory response and cell necrosis, and inhibiting liver fibrosis.[7,8] The combination use of them can enhance the curative effect.[9]

  The specific chemicals and mechanism of action of “Bupleuri Radix-Scutellariae Radix” in the treatment of hepatitis B remain unknown due to the complexity of their components and the limitations of existing research methods. Network pharmacology is a novel approach based on systems biology and multidirectional pharmacology that uses the holistic and systematic nature of interactions between herbal small molecules, host targets, and diseases as the starting point for systematically analyzing drug mechanisms of action and has unique advantages for predicting the biological processes involved in TCM treatment of disease.[10,11]

  Here, we used network pharmacology to identify the active ingredients of “Bupleuri Radix-Scutellariae Radix” and to predict the relevant target genes and key pathways associated with the hepatitis B treatment. We validated the major components by molecular docking. Our study provided new ideas and targets for the treatment of hepatitis B. Figure 1 depicts the specific process of the network pharmacology approach.


## 2. Materials and methods

### 2.1. Building a library of hepatitis B-related genes
  “Hepatitis B” was entered as a searching term in the therapeutic target database (http://db.idrblab.net/ttd/), GeneCards (https://www.genecards.org/), and online mendelian inheritance in man (https://omim.org/) for hepatitis B related genes, with the GeneCards filter set to score ≥ 20. Duplicate entries are removed after integrating the results with Excel.


### 2.2. Screening ingredients and targets of Bupleuri Radix and Scutellariae Radix
  “Bupleuri Radix” and “Scutellariae Radix” were used separately as keywords to search the traditional Chinese medicine systems pharmacology database [traditional Chinese medicine systems pharmacology database (TCMSP), https://tcmspw.com/tcmsp.php], the bioinformatics analysis tool for traditional Chinese medicine’s molecular mechanism [a bioinformatics analysis tool for molecular mechanism of traditional Chinese medicine (BATMAN-TCM), http://bionet.ncpsb.org.cn/bat-man-tcm/index.php/Home/Index/index], the encyclopedia of traditional Chinese medicine (the encyclopedia of traditional Chinese medicine, http://www.tcmip.cn/ETCM/index.php/ Home /Index/), and HERB (http://herb.ac.cn/) database. The screening criteria for the TCMSP database were drug-like (DL) ≥ 0.18 and oral bioavailability (OB) greater than 30%. The screening criteria for the BATMAN-TCM database were score ≥ 20 and P < .5. After retrieving the information from the above databases, the data were combined together, duplicates were removed to obtain the final data. TCMSP developed a computerized targeting technique that predicted these active ingredient potential protein targets. The proteins’ informative targets were also normalized using the Uniprot protein database.


### 2.3. Construction of the “active ingredient-potential target” network
  VENNY mapping was used to reveal common targets for Bupleuri Radix, Scutellariae Radix, and Hepatitis B. The active ingredients and predicted targets are loaded into Cytoscape 3.7.1 to build the “active ingredient-potential target” network, The target’s active ingredients were analyzed using the network topology parameters.


### 2.4. Building protein–protein interaction (PPI) network
  To build up the PPI network, the common targets of the ingredients and disease were loaded onto STRING to generate the node-node data file string interactions.tsv, which were then imported into Cytoscape for visual analysis.


### 2.5. Target functions and pathways enrichment analysis
  The GO function and the KEGG pathway enrichment analysis were done using DAVID software. The top P-value data were selected and were presented in the form of bar graphs and bubble plots using online bioinformatic tools.


### 2.6. Molecular docking
  Firstly, Bupleuri Radix and Scutellariae Radix components 3D structures in mol2 format of the selected molecules were downloaded from the TCMSP database. The protein 3D structures were downloaded from the RCSB database. The ligand and receptor were prepared by AutodockTools 1.5.6 and saved as pdbqt files. For the semi-flexible docking, the Autodock vina 1.1.2 were used, the parameter exhaustiveness was set to 20 and all other parameters were set to default values. The highest affinity’s docking conformation was chosen as the optimal result.


## 3. Results

### 3.1. Collection of hepatitis B-related targets
  Using therapeutic target database, online Mendelian inheritance in man, and GeneCards databases, 18, 964, and 854 targets related to hepatitis B were collected. After combining the data and removing duplicate targets, 1827 targets remained as hepatitis B targets.


### 3.2. Bupleuri Radix and Scutellariae Radix’s active ingredients and targets acquisition
  Using the databases TCMSP, ETCM, BATMAN-TCM, and HERB, Bupleuri Radix and Scutellariae Radix’s active ingredients and corresponding protein targets were retrieved. We set the selection conditions of TCMSP as OB ≥ 30% and DL ≥ 0.18. The selection criteria for BATMAN-TCM were score ≥ 20 and P < .5. By creating Venn diagrams for 1827 disease targets and 130 drug targets, 78 overlapping targets were obtained (Fig. 2). In the end, 37 active ingredients were identified, 12 from Bupleuri Radix and 26 from Scutellariae Radix, with Stigmasterol being common to both (Table 1). The OB values of the components identified from Bupleuri Radix ranged from 30 to 57 and the DL values from 0.2 to 0.76, while the OB values of the components identified from Scutellariae Radix ranged from 30 to 104 and the DL values from 0.2 to 0.86.


### 3.3. “Active Ingredient-potential target” network
  The selected Bupleuri Radix and Scutellariae Radix’s targets and active ingredients were loaded into Cytoscape (version 3.7.1) for analysis. The results were shown in Figure 3, where red hexagons represent active ingredients, green triangles represent potential targets, and gray lines represent correlations. As can be seen from the figure, quercetin (BR11) was emerged as the most interacting ingredient and interacted with 69 targets, followed by wogonin (SR2, 52 targets), kaempferol (BR4, 34 targets), and baicalin (SR4, 33 targets). Based on the magnitude of the degree value and correlation, the top ranked active ingredients from the figure include quercetin, wogonin, baicalein, and kaempferol. These 4 ingredients could be Bupleuri Radix and Scutellariae Radix’s main active ingredients in the treatment of hepatitis B.


### 3.4. PPI network
  To create PPI map, the selected 78 common targets were loaded to STRING. The result were imported into Cytoscape, as shown in Figure 4, the red triangle represents the core target, the green hexagon represents the non-core target, and the gray line represents the correlation between the targets. The larger the node, the stronger the interaction, so the 8 targets with the strongest interactions were selected and placed in the inner circle with red markers. Therefore, it is presumed that the main nodes of Bupleuri Radix and Scutellariae Radix for the treatment of hepatitis B were tumor necrosis factor (TNF), mitogen-activated protein kinase 3 (MAPK3), interleukin-6 (IL-6), vascular endothelial growth factor A, cysteinyl aspartate specific proteinase 3, JUN, RAC-alpha serine/threonine-protein kinase, and cellular tumor antigen p53. The information of the 8 core targets were listed in Table 2.


### 3.5. GO function and KEGG pathway enrichment analysis
  GO function enrichment was executed based on P < .01, and the 15 results with the top P-value in biological process (BP), cell component (CC), and molecular function (MF) were selected and displayed in Figure 5. X-axis represents GO function classification and y-axis represents the number of enriched genes. Three different colors on the x-axis represent 3 GO functions, green represents biological process, red represents cellular component and blue represents molecular function. In the biological process, positive regulation transcription from RNA polymerase II promoter, positive regulation of DNA transcription’s template nucleus, and negation regulation of apoptotic process were among the top enriched processes. The nucleus, cytosol, and cytoplasm were the major cellular compartments for ingredients to work on. Protein binding was the major molecular function of these ingredients.

  KEGG pathway analysis to obtain the relevant pathway of Bupleuri Radix and Scutellariae Radix against hepatitis B, and the 20 pathways with the lowest p-values were selected for the bubble chart display (Fig. 6). The size of the bubble area represents the number of enriched genes and the color of the bubble represents the significance of the enrichment. The figure showed that 38 genes were enriched in pathway in cancer, 27 genes in hepatitis B and 22 genes in the TNF signaling pathway, all of which had P < .01. These pathways might be the major pathways involved in the treatment of hepatitis B.


### 3.6. Molecular docking
  To predict potential targets proteins of the top selected ingredients, the target proteins TNF, MAPK3, and IL-6 were docked with quercetin, wogonin, baicalein, and kaempferol. Table 3 showed that binding energies of the four ingredients with IL-6 were between –5.6 and –6.3 kcal·mol − 1 indicating a moderate binding activity. The binding energy with TNF and MAPK3 were less than –8.9 kcal·mol − 1, indicating stronger binding activity.

  Figure 7 showed predicted docking conformation between quercetin and TNF, the quercetin predicted to form a hydrogen bond with TNF residue TYR119 with a bond length of 1.9 Å, with residue TYR151 with a bond length of 2.7 and 3.5 Å, and with residue LEU157 with a bond length of 2.2 Å. The docking structure of quercetin and MAPK3 predicted that quercetin formed hydrogen bond with residue GLN122 with a bond length of 1.9 Å, with residue ASP123 with a bond length of 2.4 Å, with residue MET125 with a bond length of 3.2 Å, and with residue ASN171 with a bond length of 2.0 Å.


## 4. Discussion
  Hepatitis B is a viral disease that primarily affects the liver. Patients who have had HBV for more than six months may develop varying degrees of inflammatory necrosis or fibrosis in the liver, cirrhosis and, eventually, liver cancer can develop in severe cases.[12] Bupleuri Radix and Scutellariae Radix are two of the most common hepatitis B drug combinations. We thoroughly investigated the underlying mechanisms in the study using a network pharmacology approach.

  The “active ingredients-potential targets” revealed that the main active ingredients of Bupleuri Radix and Scutellariae Radix for hepatitis B treatment were quercetin, baicalein, baicalin, and kaempferol. To support this prediction, previous studies demonstrated that quercetin significantly inhibited the expression of hepatitis B surface antigen, hepatitis B e antigen, and HBV DNA, as well as decreased the expression of TNF-), interleukin-6, and other inflammatory markers levels; reduced liver damage and prevent liver fibrosis, and play an important role in the prevention and treatment of liver cancer.[13–15] Several studied also showed that baicalein, baicalin, and kaempferol have anti-HBV, anti-inflammatory, anti-liver fibrosis, and anti-cancer properties, which are consistent with the findings of the current study, in which the main active ingredients act on hepatitis B.[16–18] In summary, the active ingredients in Bupleuri Radix and Scutellariae Radix can inhibit HBV replication, reduce inflammation, protect the liver from the development of hepatocellular carcinoma.

  TNF and IL-6 are the main targets in the regulation of hepatitis B, according to the result of PPI network. Hepatitis B disease is caused by an induced immune response that produces a variety of cytokines and thus impairs hepatocyte function, rather than by HBV directly destroying liver cell structure.[19] TNF-α and IL-6 are produced as mediators of inflammation by activated macrophages, T cells, and fibroblasts, respectively, and contribute to hepatocyte degeneration and necrosis, resulting in impaired liver function, leading to cirrhosis and liver fibrosis.[20] Bekçibaş et al[21] discovered that elevated levels of cytokines such as serum TNF-α and IL-6 in patients with chronic hepatitis B were positively correlated with disease severity and HBV-DNA load, suggesting that these cytokines may be involved in the process leading to liver injury.[22,23] Beringer et al[24] went on to show that neutralizing IL-17 and TNF-α reduced liver inflammation and thus prevented fibrosis, and that the mechanism may be related to their interaction to induce IL-6 and IL-8 production. Second, TNF-α and IL-6 are mediators of HBV replication and expression. On the one hand, TNF-α and IL-6 have been shown in studies[25,26] to inhibit HBV replication by activating nuclear factor kappa-B to disrupt the formation or stability of the viral capsid; Chen et al[27] discovered that IL-6 can effectively inhibit HBV replication and prevent HBV covalently closed circular DNA (cccDNA) accumulation. Some studies,[28] on the other hand, have shown a risk of hepatitis B virus reactivation in HBV patients treated with TNF-α inhibitors; Qiao et al[29] reported that IL-6 increased the activity of the HBV enhancer (Enh1), which has a promotional effect on HBx expression and HBV replication; and Xia et al[30] discovered that IL-6 can enhance intrahepatic HBV replication. In conclusion, TNF-α and IL-6 play critical roles in the host’s inflammatory response and viral clearance.

  According to the PPI results, MAPK3 is an important target for hepatitis B treatment. MAPK3 is a mitogen-activated protein kinase that is linked to HBV transmission and infection. It is also known as extracellular signal-regulated kinase 1 (ERK1). Yang et al[31] discovered that ERK1/2 mediates trophoblast differentiation and can promote HBV transmission. Fang et al[32] found that serum ERK1/2 protein levels fluctuate with HBV infection in chronic hepatitis B patients. ERK1 and ERK2 levels in the blood can be used as novel biomarkers for chronic HBV infection. Dai et al[33] showed that activation of the ERK1/2 pathway in HepG2.2.15 cells downregulated hepatocyte nuclear factor 4α (HNF4α) and HNF1α to inhibit HBV replication; Bai et al[34] further demonstrated that activation of the ERK pathway inhibited HBV core promoter activity. Collectively, the MAPK3 target plays a unique role in achieving inhibition of HBV virus replication.

  KEGG analysis revealed significant enrichment in cancer, hepatitis B, and TNF signaling pathways, all of which are involved in hepatitis B pathogenesis. The receptor signaling routes, which include TNFR1 and TNFR2, and downstream signaling pathways, which include nuclear factor kappa-B, MAPK, and the Phosphatidylinositol 3-kinase (PI3K)/AKT (protein kinase B) signaling pathway, are the 2 types of TNF signaling pathways (Fig. 8).[35] TNF-α is activated and forms homotrimers before binding to TNFR1 and TNFR2 receptors, causing trimerization of the receptors. TNF receptors bind to ligands and mediate the binding of bridging proteins like TRADD or TRAF, which then initiate the transduction of downstream signaling pathways that produce inflammatory mediators like inflammatory factors (IL-6, TNF-α), JUN, and so on, leading to liver inflammation, fibrosis, and even the development of hepatocellular carcinoma.[36]

  Molecular docking revealed that quercetin and baicalein had good binding capabilities with TNF, MAPK3, and IL-6, implying that Bupleuri Radix and Scutellariae Radix exerted anti-hepatitis B effects by modulating the TNF signaling pathway.


## 5. Conclusion
  In conclusion, Bupleuri and Scutellariae Radix have multi-components and multi-targets including TNF, MAPK3, and IL-6. These targets can inhibit HBV replication, control chronic inflammation in the liver via the TNF signaling pathway. Although the network pharmacology method can effectively remedy the defects of complex components and single target in Chinese medicine research, it still faces some challenges in practical application: Network pharmacology is based on database and analysis software, and the reliability of the results is closely related to the perfection of the database. The drug exerts its efficacy based on potent substances, and the database does not incorporate the dose screening criteria of the ingredients, and some active ingredients screened out have low contents in the original herbs. The basic pharmacological effects and mechanisms of Bupleuri Radix and Scutellariae Radix in the treatment of hepatitis B were first established in this study. Subsequent biological experiments are required to validate the active ingredients and core targets in order to clarify the mechanisms of the hepatitis B treatment.


## Author contributions
  Conceptualization: Piao Long.

  Data collection: Piao Long, Yu Xia, Yuying Yang.

  Data curation: Piao Long, Yu Xia, Yuying Yang.

  Funding acquisition: Jianzhong Cao.

  Investigation: Yu Xia.

  Software: Piao Long.

  Supervision: Jianzhong Cao.

  Writing – original draft: Piao Long.

  Writing – review & editing: Jianzhong Cao.