# AMBP gene activation promotes cholangiocarcinoma progression through the WNT/β-catenin signaling pathway: Regulatory effect of polysaccharides from Auricularia auricula-judae


## Abstract
  Cholangiocarcinoma (CCA), an aggressive hepatobiliary malignancy with poor prognosis, involves abnormal molecular regulatory networks. This study explores α-1-microglobulin/bikunin precursor's (AMBP’s) role in CCA, its pro-carcinogenic mechanisms via the wingless/integrated (WNT) pathway, and Huaier polysaccharide’s targeted therapeutic potential. Using GSE132305, R software identified differentially expressed genes. Gene ontology/Kyoto encyclopedia of genes and genomes, gene set enrichment analysis, and Metascape analyzed enriched pathways, focusing on WNT. Weighted gene co-expression network analysis explored gene–phenotype correlations. STRING-based protein–protein interaction networks and algorithms (MCC, DMNC, and EPC) identified hub genes. TCGA enabled survival analysis and differential expression visualization. CIBERSORT analyzed immune infiltration (especially Tregs). TCMSP screened Huaier components, with molecular docking testing target binding. Reverse transcription quantitative polymerase chain reaction and Western blotting validated hub gene functions. Differentially expressed genes enriched in WNT, a key driver of CCA. Weighted gene co-expression network analysis and protein–protein interaction identified AMBP as a hub gene; its high expression linked to lower survival and elevated levels in CCA tissues. Increased Tregs in CCA correlated with immunosuppression and poor prognosis. Multi-omics confirmed AMBP promotes malignancy via WNT activation. Quercetin, Huaier main component, showed strong binding to AMBP via multiple interactions. AMBP overexpression in CCA cells activated WNT molecules (β-catenin, c-Myc, and Cyclin D1), enhancing tumor progression. Huaier targeted AMBP, reducing WNT activity and related proteins. High AMBP expression associates with CCA tumorigenesis, immunosuppression, and poor prognosis, acting via WNT. Huaier polysaccharide reverses CCA malignancy by inhibiting AMBP, reducing invasiveness/metastasis and improving prognosis.


## 1. Introduction
  Cholangiocarcinoma (CCA) is a highly aggressive malignancy originating from the biliary epithelium, with a globally rising incidence and an extremely poor prognosis, as evidenced by a 5-year survival rate of <30%.[1] Despite recent breakthroughs in targeted therapies and immunotherapies, critical challenges such as pronounced tumor heterogeneity, complex molecular mechanisms, and the scarcity of effective therapeutic targets remain central barriers to improving clinical outcomes.[2,3] In this context, unraveling the key molecular mechanisms driving CCA progression and developing novel targeted therapeutics have emerged as urgent scientific priorities.

  The aberrant activation of the canonical wingless/integrated (WNT)/β-catenin signaling pathway has been confirmed as a critical molecular hallmark of CCA.[4] Studies have demonstrated that in the microenvironment of chronic biliary inflammation, macrophages secrete WNT7b/WNT10a ligands, which activate β-catenin via Frizzled/low-density lipoprotein receptor-related protein receptors. This drives the transcription of downstream target genes such as c-Myc and Cyclin D1, thereby promoting tumor proliferation, epithelial–mesenchymal transition (EMT), and chemotherapy resistance.[5] The α-1-microglobulin/bikunin precursor (AMBP) gene has garnered attention due to its unique biological functions. This gene encodes a glycoprotein that undergoes proteolytic cleavage to generate α-1-microglobulin (A1M) and bikunin, which are involved in inflammatory regulation and protease inhibition, respectively.[6,7] Clinical studies reveal that AMBP exhibits dysregulated expression in multiple malignancies, including gastric cancer, hepatocellular carcinoma, and oral squamous cell carcinoma, with its expression levels strongly correlating with chemoresistance, lymph node metastasis, and other aggressive behaviors.[8–11]

  In recent years, natural bioactive polysaccharides have emerged as a research hotspot in anticancer drug development due to their multi-target regulatory properties. Among these, Huaier polysaccharide (Trametes robiniophila polysaccharide, TRP) (the active component of the traditional Chinese medicine Huaier, has demonstrated significant antitumor activity and clinical adjuvant therapeutic potential in various solid tumors).[12] Studies confirm that in pancreatic and ovarian cancer models, Huaier polysaccharide markedly downregulates β-catenin expression, blocks its nuclear translocation, and suppresses the WNT pathway-mediated EMT process.[13,14] Further investigations reveal that Huaier polysaccharide inhibits the WNT pathway by targeting the Twist1/FBP1 axis, a mechanism also shown to exert antitumor effects in CCA cells.[15] These multidimensional mechanisms of action position TRP as an ideal candidate drug for targeting the AMBP–WNT axis.

  This article integrates bioinformatics analysis, molecular docking, and experimental verification to systematically elucidate the mechanism of action of the AMBP gene in mediating the WNT signaling pathway in CCA, and evaluates the therapeutic potential of Huaier polysaccharide. The aim is to provide theoretical basis and candidate drugs for the precise treatment of CCA.


## 2. Methods

### 2.1. CCA dataset
  In this study, the CCA dataset GSE132305 profile was generated from the GPL13667 platform and downloaded from the GEO database (http://www.ncbi.nlm.nih.gov/geo/). GSE132305 includes 182 CCA samples and 38 normal samples. This dataset was used to identify differentially expressed genes (DEGs) in CCA.


### 2.2. Screening of DEGs
  The R package “limma” was used for probe summarization and background correction of the gene expression matrix from GSE132305. The Benjamini–Hochberg method was applied to adjust raw P-values. Fold change was calculated using the false discovery rate (FDR). The cutoff criteria for DEGs were set as P <.05 and fold change >1.5. A volcano plot was generated to identify DEGs.


### 2.3. Gene set enrichment analysis (GSEA) analysis
  For GSEA, we obtained the GSEA software (version 3.0) from the GSEA website (DOI: 10.1073/pnas.0506580102; http://software.broadinstitute.org/gsea/index.jsp). Samples were divided into 2 groups based on diseased and normal tissues. The c2.cp.kegg.v7.4.symbols.gmt subset was downloaded from the Molecular Signatures Database (DOI: 10.1093/bioinformatics/btr260; http://www.gsea-msigdb.org/gsea/downloads.jsp) to evaluate relevant pathways and molecular mechanisms. Based on gene expression profiles and phenotypic grouping, the minimum gene set size was set to 5, and the maximum to 5000, with 1000 permutations. A P value <.05 and an FDR <0.25 were considered statistically significant. Additionally, genome-wide gene ontology (GO) and Kyoto encyclopedia of genes and genomes (KEGG) analyses were performed, as implemented by GSEA.


### 2.4. Functional enrichment analysis
  GO analysis and KEGG analysis are computational methods used to evaluate gene functions and biological pathways. In this study, the DEG list identified by limma differential analysis was input into the KEGG REST API (https://www.kegg.jp/kegg/rest/keggapi.html) to obtain the latest KEGG Pathway gene annotations. Using these annotations as the background, genes were mapped to the background set, and enrichment analysis was performed using the R package clusterProfiler (version 3.14.3) to obtain results of gene set enrichment. Additionally, GO annotations of genes from the R package org.Hs.e.g..db (version 3.1.0) were used as the background. Genes were mapped to this background set, with the minimum gene set size set to 5 and the maximum to 5000. A P value <.05 and an FDR <0.25 were considered statistically significant criteria.

  Furthermore, the Metascape database provides comprehensive gene list annotation and analysis resources, with results visualized and exported. We used the Metascape database (http://metascape.org/gp/index.html) to perform functional enrichment analysis on the abovementioned DEG list and exported the results.


### 2.5. Weighted gene co-expression network analysis (WGCNA)
  First, using the gene expression matrix from the CCA dataset GSE132305, we calculated the median absolute deviation for each gene, excluding the top 50% of genes with the smallest median absolute deviation values. The goodSamplesGenes method from the R package WGCNA was used to remove outlier genes and samples. We further constructed a scale-free co-expression network using WGCNA. Specifically, Pearson correlation matrices and the average linkage method were first applied to all paired genes. A weighted adjacency matrix was then constructed using the power function Amn=∣Cmn∣β A_{mn} = |C_{mn}|^\beta Amn =∣Cmn ∣β (where Cmn C_{mn} Cmn represents the Pearson correlation between Gene m m m and Gene n n n, and Amn A_{mn} Amn represents the adjacency between Gene m m m and Gene n n n). Here, β \beta β is a soft-thresholding parameter that emphasizes strong correlations between genes while weakening the influence of weak and negative correlations. After selecting a power of 10, the adjacency matrix was converted to a topological overlap matrix (TOM), which measures the network connectivity of a gene (defined as the sum of its adjacencies with all other genes). This connectivity was used to calculate the network gene ratio and the corresponding dissimilarity (1-TOM). To classify genes with similar expression profiles into gene modules, average linkage hierarchical clustering was performed based on the TOM-based dissimilarity metric, with a minimum size (gene set) of 30 for the gene dendrogram. The sensitivity was set to 3. For further module analysis, we calculated the dissimilarity of module eigengenes, selected a cutting line for the module dendrogram, and merged some modules. Additionally, modules with a distance <0.25 were merged. Notably, the gray module was considered a collection of genes that could not be assigned to any other module.


### 2.6. Construction and analysis of protein–protein interaction (PPI) network
  The STRING database (http://string-db.org/) is designed to collect, score, and integrate all publicly available sources of PPI information, supplemented with computational predictions. In this study, the DEG list was input into the STRING database to construct a PPI network for predicting core genes (with a confidence score >0.4). Cytoscape software provides biologists with biological network analysis and 2D visualization capabilities. Using Cytoscape, we visualized the PPI network generated by the STRING database and predicted core genes. Specifically, we first imported the PPI network into Cytoscape, identified the most highly correlated modules using MCODE, and calculated the top 10 most correlated genes using 3 algorithms (MCC, DMNC, and EPC) respectively. The intersection of these gene lists was taken, and the core gene list was visualized and exported.


### 2.7. Survival analysis
  We obtained clinical survival data for CCA from TCGA and used the R package maxstat (version: 0.7-25; Max Planck Institute for Molecular Genetics, Berlin, Germany) to calculate the optimal cutoff value for the RiskScore of core genes. The minimum sample size per group was set to >25%, and the maximum to <75%. Based on this cutoff, patients were divided into high-risk and low-risk groups. The survfit function from the R package survival was further used to analyze prognostic differences between the 2 groups, and the log-rank test method was applied to evaluate the significance of prognostic differences between samples in different groups.


### 2.8. Gene expression heatmap
  Using the R package heatmap, we generated a heatmap of the expression levels of core genes identified in the PPI network within the CCA dataset GSE132305, visualizing the expression differences of core genes between CCA and normal tissue samples.


### 2.9. Comparative toxicogenomics database (CTD) analysis
  The CTD integrates extensive interaction data between chemicals, genes, functional phenotypes, and diseases, providing significant convenience for studying disease-related environmental exposure factors and potential mechanisms of drug action. We input the core genes into the CTD website to identify the most relevant diseases associated with the core genes and used Excel to plot expression difference radar charts for each gene.


### 2.10. Immune infiltration analysis
  CIBERSORT (http://CIBERSORT.stanford.edu/) is a widely used method for calculating immune cell infiltration, where the LM22 gene signature file is used to define 22 immune cell subsets. We applied an integrated bioinformatics approach, using the CIBERSORT tool to analyze the gene expression matrix of the CCA dataset GSE132305. Based on the principle of linear support vector regression, we deconvolved the expression matrix of immune cell subtypes to estimate immune cell abundances. Meanwhile, samples with sufficient confidence were selected using a confidence P <.05 as the cutoff criterion.


### 2.11. Collection of active ingredients and prediction of potential targets
  Using “Flos Sophorae” and “Fructus Sophorae” as search terms, relevant chemical components were retrieved from the TCMSP database (https://tcmsp-e.com/tcmsp.php). Compounds meeting the pharmacokinetic (absorption, distribution, metabolism, excretion) parameters were selected: oral bioavailability ≥30% and drug-likeness ≥0.18. Targets corresponding to these chemical components were extracted, and known targets not predicted in TCMSP were supplemented by reviewing relevant literature. These targets were standardized in the Uniprot protein database (https://www.uniprot.org).


### 2.12. Construction of “Active Component-Target Network” for TRP
  The “active component-target network” for TRP was primarily constructed and analyzed using Cytoscape 3.7.2 software (National Resource for Network Biology, University of California, San Diego). Relationships between the obtained active components and targets were imported to complete the network construction, where “nodes” represent drug molecules and corresponding genes, and “edges” represent the relationships between them. The “Network Analyze” plugin was used for network feature analysis to screen for more important active components.


### 2.13. Protein target molecular docking

#### 2.13.1. Preparation of target proteins and small molecule structures
  The crystal structure of the AMBP target protein (PDB ID: 4ES7) was obtained from the Protein Data Bank (https://www.rcsb.org/). Using PyMOL 2.1 software (Schrödinger, LLC, New York), irrelevant small molecules were removed from the protein. The protein was then imported into AutoDock Tools-1.5.6 to remove water molecules, add hydrogen atoms, and set atomic types, and finally saved as a pdbqt file.

  The structure of the compound (Quercetin) was retrieved from the PubChem database (https://pubchem.ncbi.nlm.nih.gov/). The downloaded compound underwent energy minimization using Chem3D and was converted to mol2 format. The small molecule compound was imported into AutoDock Tools-1.5.6 to add atomic charges, assign atomic types, and set all flexible bonds as rotatable by default, and was ultimately saved as a pdbqt file.


#### 2.13.2. Molecular docking
  The processed quercetin compound was used as the small molecule ligand, and 5 protein targets served as receptors. The center position of the Grid Box, determined based on the interaction between the small molecule and the target, was set with dimensions of 40 × 40 × 40. Finally, batch molecular docking was performed using AutoDock Vina. The docking results were analyzed, and visualization of the binding interactions between the compound and the protein was conducted using PyMOL 2.1. During the calculation, the Lamarckian genetic algorithm was employed for molecular docking, with the following parameters: a population size of 150, a maximum of 25 million energy evaluations, a maximum number of generations of 2000, a crossover rate of 0.8, a mutation rate of 0.02, and 200 independent docking runs. The final docking structures were evaluated based on binding free energy.


#### 2.13.3. Screening and analysis of docking results
  The interaction modes between the compound and target proteins were analyzed to characterize the interactions with protein residues, including hydrogen bonding, π–π interactions, and hydrophobic interactions. By referencing the docking scores of the compounds, we inferred whether the screened compounds possess potential biological activity.


### 2.14. Cell culture
  Human normal biliary epithelial cells were used as the normal group, and the CCA cell line HuCCT1 was used as the experimental group. Cells were seeded into cell culture dishes and cultured in DMEM (high-glucose medium) and RPMI-1640 medium supplemented with appropriate concentrations of fetal bovine serum or synthetic medium additives to provide essential growth factors and nutrients. Culture conditions: incubated in a 37 °C, 5% CO2 incubator. Medium was replaced regularly to maintain the cell growth environment.

  The AMBP gene was knocked down in CCA cells using RNA interference technology.

  AMBP siRNA sequences:

  Sense strand (SS): GGAAGUUUCUCUAUCACAAAU

  Antisense strand (AS): UUGUGAUAGAGAAACUUCCCA

  AMBP gene was overexpressed via plasmid transfection, and the AMBP overexpression sequence is as follows:

  >NM_001633.4:92-1150 Homo sapiens AMBP, mRNA

  ATGAGGAGCCTCGGGGCCCTGCTCTTGCTGCTGAGCGCCTGCCTGGCGGTGAGCGCTGGCCCTGTGCCAACGCCGCCCGACAACATCCAAGTGCAGGAAAACTTCAATATCTCTCGGATCTATGGGAAGTGGTACAACCTGGCCATCGGTTCCACCTGCCCCTGGCTGAAGAAGATCATGGACAGGATGACAGTGAGCACGCTGGTGCTGGGAGAGGGCGCTACAGAGGCGGAGATCAGCATGACCAGCACTCGTTGGCGGAAAGGTGTCTGTGAGGAGACGTCTGGAGCTTATGAGAAAACAGATACTGATGGGAAGTTTCTCTATCACAAATCCAAATGGAACATAAC

  CATGGAGTCCTATGTGGTCCACACCAACTATGATGAGTATGCCATTTTCCTGACCAAGAAATTCAGCCGCCATCATGGACCCACCATTACTGCCAAGCTCTACGGGCGGGCGCCGCAGCTGAGGGAAACTCTCCTGCAGGACTTCAGAGTGGTTGCCCAGGGTGTGGGCATCCCTGAGGACTCCATCTTCACCATGGCTGACCGAGGTGAATGTGTCCCTGGGGAGCAGGAACCAGAGCCCATCTTAATCCCGAGAGTCCGGAGGGCTGTGCTACCCCAAGAAGAGGAAGGATCAGGGGGTGGGCAACTGGTAACTGAAGTCACCAAGAAAGAAGATTCCTGCCAGCTGG

  GCTACTCGGCCGGTCCCTGCATGGGAATGACCAGCAGGTATTTCTATAATGGTACATCCATGGCCTGTGAGACTTTCCAGTACGGCGGCTGCATGGGCAACGGTAACAACTTCGTCACAGAAAAGGAGTGTCTGCAGACCTGCCGAACTGTGGCGGCCTGCAATCTCCCCATAGTCCGGGGCCCCTGCCGAGCCTTCATCCAGCTCTGGGCATTTGATGCTGTCAAGGGGAAGTGCGTCCTCTTCCCCTACGGGGGCTGCCAGGGCAACGGGAACAAGTTCTACTCAGAGAAGGAGTGCAGAGAGTACTGCGGTGTCCCTGGTGATGGTGATGAGGAGCTGCTGCGCTTC

  TCCAACTGA

  Knockdown and overexpression efficiencies were validated using Western blotting (WB) and reverse transcription quantitative polymerase chain reaction (RT-qPCR).

  Drug treatment group: after transfecting cells with the AMBP overexpression plasmid for 24 hours, Huaier polysaccharide-TRP was added. Cells were collected following 24 hours of drug treatment.


### 2.15. Real-time quantitative polymerase chain reaction
  RT-qPCR was used to detect the mRNA expression levels of the AMBP gene and key molecules in the WNT signaling pathway (β-catenin, c-Myc, and Cyclin D1) in the normal group, HuCCT1 group, HuCCT1-AMBP_KO group, HuCCT1-AMBP_OE group, and HuCCT1-AMBP_OE-TRP group.

  After removing the cell culture medium, cells were washed with phosphate-buffered saline, and total RNA was extracted by adding RNA extraction reagent (Servicebio, G3013, Wuhan) to the culture plate. An ultra-micro spectrophotometer (Nanodrop 2000, Thermo, Waltham) was used to measure the absorbance values at 260 nm and 280 nm to determine the concentration and purity of the RNA solution. A reaction system was prepared using a reverse transcription kit (Servicebio, G3331-50, Wuhan). After removing genomic DNA, RNA was reverse-transcribed into cDNA. Next, a real-time qPCR reaction system (Servicebio, G3326-01, Wuhan) was prepared, using 2× concentrated real-time qPCR MasterMix. At least 3 parallel wells were set for each sample to ensure data statistical validity. The reaction system included: 2× qPCR MasterMix, template cDNA, forward and reverse primers, ddH2O, etc. The prepared reaction solution was loaded into a real-time qPCR instrument, and amplification was performed with the following temperature cycles and data acquisition settings: initial denaturation at 95°C for 30 seconds, followed by 40 cycles consisting of denaturation at 95°C for 10 seconds and annealing/extension at 60°C for 30 seconds. All experimental data were collected using a StepOneTM real-time qPCR instrument. Finally, melting curve analysis was completed according to the instrument’s default settings. Relative mRNA expression was calculated using the 2−ΔΔCt method, with Ct values normalized to the reference gene glyceraldehyde-3-phosphate dehydrogenase.

  The primer sequences for target genes are as follows:

  AMBP: Forward primer (5′-AGCATGACCAGCACTCGTTG-3′); Reverse primer (5′-GCAGTAATGGTGGGTCCATGAT-3′)

  β-catenin: Forward primer (5′-TGGATACCTCCCAAGTCCTG-3′); Reverse primer (5′-CGAGTCATTGCATACTGTCCA-3′)

  c-Myc: Forward primer (5′-GCCTCAGAGTGCATCGAC-3′); Reverse primer (5′-TCCACAGAAACAACATCG-3′)

  CyclinD1: Forward primer (5′-TGCATGTTCGTGGCCTCTAA-3′); Reverse primer (5′-GAACTTCACATCTGTGGCAC-3′)

  Glyceraldehyde-3-phosphate dehydrogenase: Forward primer (5′-AACGGATTTGGTCGTATT-3′); Reverse primer (5′-GGAAGATGGTGATGGGATT-3′).


### 2.16. Western blot
  Western blotting was used to detect the expression levels of AMBP, key molecules in the WNT signaling pathway (β-catenin, p-GSK3β, c-Myc, and Cyclin D1), and apoptosis/metastasis-related molecules (Bax, Bcl2, E-cadherin, and N-cadherin) in the normal group, HuCCT1 group, HuCCT1-AMBP_KO group, HuCCT1-AMBP_OE group, and HuCCT1-AMBP_OE-TRP group.

  Total cellular protein was extracted using RIPA lysis buffer (with protease inhibitors added minutes before use). Protein concentration was determined using the BCA assay. Proteins were separated by SDS-PAGE under the following conditions: 90 V for approximately 30 minutes (stacking gel) and 130 V for approximately 60 minutes (separating gel). After electrophoresis, proteins were transferred from the gel to a polyvinylidene fluoride membrane. The polyvinylidene fluoride membrane was blocked in blocking buffer for 1 hour. The blocking buffer was removed, and primary antibodies (e.g., AMBP [Proteintech, 26716-1-AP, 1:5000, Wuhan], β-catenin [Proteintech, 51067-2-AP, 1:5000, Wuhan], p-GSK3β [Proteintech, 67558-1-Ig, 1:2000, Wuhan], and c-Myc [Proteintech, 67447-1-IG, 1:5000]) were added, followed by overnight incubation at 4 °C. The primary antibodies were removed, and the membrane was washed with TBST 3 times (5–10 minutes per wash). HRP-conjugated secondary antibodies (Solarbio, SE134/SE131, 1:1000) were added, and the membrane was incubated at room temperature for 1 hour. The secondary antibodies were removed, and the membrane was washed with TBST 3 times (5–10 minutes per wash). Finally, the membrane was developed using chemiluminescence. Gray value analysis was performed using ImageJ software (version 1.53t; National Institutes of Health, Bethesda), and all data were repeated 3 times for statistical processing.


## 3. Results

### 3.1. Analysis of DEGs
  Using the preset cutoff value (P < .05), we identified DEGs in the gene expression matrix of GSE132305. A total of 153 DEGs were finally identified using R software, and a volcano plot was generated (Fig. 1).


### 3.2. Functional enrichment analysis

#### 3.2.1. Functional enrichment analysis of DEGs
  GO and KEGG analyses were performed on these DEGs. According to GO analysis, they were primarily enriched in organic acid catabolic processes, condensed chromosome centromeric regions, and oxidoreductase activity (Fig. 2A–C).

  In KEGG analysis, they were mainly clustered in the WNT signaling pathway, PI3K-Akt signaling pathway, IL-17 signaling pathway, cGMP-PKG signaling pathway, and extracellular matrix–receptor interaction (Fig. 2D).


#### 3.2.2. GSEA analysis
  Additionally, genome-wide GSEA was conducted to identify potential enrichment terms among non-DEGs and validate the results from DEG analysis. The GSEA enrichment results were highly consistent with the GO and KEGG enrichment terms of DEGs, with these genes primarily enriched in the WNT signaling pathway (Fig. 2E–H). This further supported the GO and KEGG enrichment findings.


#### 3.2.3. Metascape enrichment analysis
  In Metascape enrichment terms, GO enrichment included the severe acute respiratory syndrome coronavirus 2 signaling network, cellular response to cytokines, extracellular matrix organization, adipocyte differentiation, muscle tissue development, vitamin D receptor pathway, Naba Lab's extracellular matrix regulators, cellular response to growth factors, blood vessel development, and regulation of systemic processes (Fig. 3A). We also generated enrichment networks colored by enrichment terms and P-values (Figs. 3B, C and 4), visually representing the associations and confidence of each enrichment term.


### 3.3. WGCNA analysis
  Selecting the soft-thresholding power is a critical step in WGCNA analysis. Network topology analysis was performed to determine the soft-thresholding power, which was set to 9 in this study (Fig. 5A). A hierarchical clustering tree of all genes was constructed, yielding 13 modules in total (Fig. 5B). Interactions between key modules were analyzed (Fig. 5C), and a heatmap of module–phenotype correlations (Fig. 5D) and a scatter plot of GS versus MM correlations for hub genes (Fig. 6A) were generated. We calculated the correlation between module eigengenes and gene expression to obtain MM values. Based on the cutoff criterion (|MM| > 0.6), 8 highly connected gene modules were identified as hub modules in the clinically significant modules, and genes within these modules were designated as hub genes.Figure 5.WGCNA analysis. (A) β = 9, 0.94. β = 9, 5.70. (B and C) The hierarchical clustering tree of all genes was constructed, and 13 important modules were generated. (D) The heat map of correlation between modules and phenotypes. WGCNA = weighted gene co-expression network analysis. Figure 6.(A) The scatter map of correlation between GS and MM of related hub genes. (B) The DEGs screened by WGCNA and DEGs was used to obtain venn map 71 intersection genes were obtained.DEGs = differentially expressed genes, WGCNA = weighted gene co-expression network analysis.

  Furthermore, a Venn diagram was plotted to intersect the hub genes identified by WGCNA with the DEGs, resulting in 71 overlapping DEGs (Fig. 6B). These overlapping DEGs were used for subsequent PPI network construction.


### 3.4. Construction and analysis of PPI network
  The PPI network was constructed using the STRING online database and analyzed with Cytoscape software (Fig. 7A). A core gene cluster was identified (Fig. 7B), and core genes within this cluster were recognized using 3 algorithms: MCC, DMNC, and EPC (Fig. 7C–E). A Venn diagram was plotted to obtain the union of these core genes (Fig. 7F), ultimately yielding 5 core genes: APOA2, AMBP, SERPINA1, FGA, and FGB.Figure 7.Construction and analysis of protein-protein interaction (PPI) networks. (A) Construct the PPI network of DEGs using STRING online database and utilize Cytoscape software for analysis. (B) CLUSTER was used to identify the central gene. (C) MCC was used to identify the central gene. (D) DMNC was used to identify the central gene. (E) EPC was used to identify the central gene. (F) Five core genes (APOA2, AMBP, SERPINA1, FGA, and FGB) were obtained by merging using Venn diagrams. AMBP = alpha(1)-microglobulin/bikunin precursor, DEGs = differentially expressed genes.


### 3.5. Survival analysis
  Using CCA survival data downloaded from TCGA, a prognostic score relationship plot was generated. It was observed that patient survival rates significantly decreased with increasing risk scores, with the low-risk group showing notably longer survival times and higher survival rates than the high-risk group (Fig. 8A). A heatmap visualizing the expression levels of core genes in the CCA survival data indicated that core genes (APOA2, AMBP, SERPINA1, and FGB) acted as protective factors, with their expression decreasing as risk scores increased (Fig. 8B). A box plot of core gene expression in CCA was also generated (Fig. 8C), where red represents cancer samples (T) and gray represents normal samples (N). Results showed that core genes (APOA2, AMBP, SERPINA1, and FGB) were significantly more highly expressed in CCA tissues than in normal tissues, suggesting these genes may play important roles in the disease.Figure 8.Survival analysis. (A) The impact of GSE132305 on the survival time and survival rate of cholangiocarcinoma patients. (B) The expression heatmap of core genes in GSE132305 for cholangiocarcinoma survival data. (C) Box plot of cholangiocarcinoma.


### 3.6. Core gene expression heatmap
  We visualized the expression levels of core genes in the GSE132305 CCA dataset matrix (Fig. 9A) and generated a heatmap. We found that the core gene AMBP was highly expressed in CCA samples and lowly expressed in normal samples, with significant differences. Based on this result, we speculate that AMBP may regulate CCA.Figure 9.(A) The heatmap depicting the expression levels of differentially expressed genes related to ferroptosis in the merged matrix of GSE132305 datasets. (B) CTD analysis. One core genes (AMBP) is closely related to the occurrence of liver damage, inflammation, necrosis. AMBP = alpha(1)-microglobulin/bikunin precursor, CTD = Comparative Toxicogenomics Database.


### 3.7. CTD analysis
  In this study, we input the core gene list into the CTD website to identify diseases associated with these core genes, enhancing our understanding of gene–disease associations. The core gene AMBP was found to be related to liver injury, inflammation, and necrosis (Fig. 9B), further supporting the link between core genes and CCA.


### 3.8. Immune infiltration analysis
  Using the CIBERSORT tool, we analyzed the data matrix of the GSE132305 CCA dataset. Under 95% confidence, we obtained the proportions of immune cells in the whole gene expression matrix. Regulatory T cells (Tregs) were found to be more abundant in CCA samples. This suggests that Tregs, which have immunosuppressive functions, may inhibit antitumor immune responses and promote immune escape in CCA (Fig. 10A). A heatmap of immune cell expression levels in the dataset was also generated, showing higher expression of Tregs in CCA samples, further supporting the findings in Figure 10A (Fig. 10B). Additionally, correlation analysis of infiltrating immune cells yielded a co-expression pattern plot of immune cell components. This analysis revealed a significant negative correlation between activated memory CD4+ T cells (T_cells_CD4_memory_activated) and naive B cells (B_cells_naive). This phenomenon may indicate that increased levels of activated memory CD4+ T cells could suppress naive B cell function, thereby affecting the immune microenvironment and disease progression in CCA (Fig. 10C).Figure 10.Immunoinfiltration analysis. (A) Whole gene expression matrix results in proportion of immune cells. (B) Heat map of immune cell expression in data set. (C) Map of co-expression patterns between immune cell components.


### 3.9. Active ingredients and therapeutic targets
  A total of 27 chemical components from Flos Sophorae and 21 from Fructus Sophorae were retrieved and extracted using the TCMSP database and existing literature reports. With the criteria “OB ≥ 30% and DL ≥ 0.18,” 6 active compounds were selected from Flos Sophorae and 6 from Fructus Sophorae. Targets corresponding to these active compounds were identified, duplicate entries were removed, and a total of 118 unique targets were obtained after merging. The active ingredients of each herb in the formula are shown in (Table 1).


### 3.10. Construction of the “Active Component-Disease-Target Network”
  An “active component-target network” was constructed, consisting of 130 nodes and 336 edges. The degree of individual targets (representing the number of connected targets) is shown in (Fig. 11).Figure 11.The main active component-target network diagram of the treatment of cholangiocarcinoma with Sophoraeavescentis polysaccharides (the degree is related to the size of the target).

  Network analysis revealed that quercetin had a degree of 75 and a betweenness of 0.30747, predicting it as the primary active component of Trametes robiniophila polysaccharide in treating CCA. The top 7 active ingredients are listed in (Table 2).


### 3.11. Docking results

#### 3.11.1. Screening results
  Molecular docking results are presented in Table 3, with visualizations shown in Fig. 12.Figure 12.The binding mode of AMBP with quercetin. (A) The 3D structure of complex. (B) The electrostatic surface of protein. (C) The 3D binding mode of complex. AMBP = alpha(1)-microglobulin/bikunin precursor. Figure 13.RT-qPCR detection of mRNA expression levels of the AMBP gene and WNT signaling pathway-related molecules (β-catenin, c-Myc, and Cyclin D1) in cells of each group. Data are presented as mean ± SD from 3 independent experiments. Statistical significance is indicated as: *P < .05, **P < .01, ***P < .001. AMBP = alpha(1)-microglobulin/bikunin precursor, RT-qPCR = reverse transcription quantitative polymerase chain reaction.


#### 3.11.2. Analysis of compound–protein interactions
  In this experiment, quercetin was docked with 4 target proteins. Docking results indicated strong binding interactions and high compatibility between multiple compounds and target proteins (binding energy < -6 kcal/mol). Complexes formed by the docked compounds and proteins were visualized using PyMOL 2.1 (one optimal conformation was selected for each protein), revealing the binding modes between compounds and proteins. Based on these modes, amino acid residues involved in the binding pockets of proteins were clearly identified.

  Quercetin exhibited good matching with the active site of the AMBP protein. The small molecule formed hydrophobic interactions with hydrophobic amino acids TRP-60, MET-37, and THR-38 in the protein pocket. Additionally, active groups of the compound formed hydrogen bonding interactions with ARG-59 and LYS-62, which are critical for stabilizing the small molecule within the protein pocket.

  Quercetin also formed multiple interactions (hydrogen bonding, hydrophobic, and van der Waals forces) with the TNF protein site. For example, it formed strong hydrophobic interactions with amino acids LEU-120, TYR-119, TYR-59, LEU-57, and TYR-151. The compound also formed strong hydrogen bonding interactions with SER-60 (characterized by short bond distances and strong binding), and notably, conjugation interactions with TYR-119. These interactions effectively promoted the formation of stable complexes between the small molecule and the protein.

  In summary, quercetin forms multiple interactions (hydrogen bonding, hydrophobic, and conjugation) with the protein target AMBP, which effectively promote the formation of stable complexes between the protein and small molecule, indicating a strong association with the target. We conclude that AMBP may serve as a key target gene, playing an important role in the development and treatment of CCA with TRP.


### 3.12. Real-time quantitative polymerase chain reaction
  Analysis of real-time quantitative polymerase chain reaction results showed that AMBP mRNA expression levels were significantly elevated in CCA cells. AMBP overexpression further activated the WNT pathway, upregulating the mRNA levels of key molecules (β-catenin, c-Myc, and Cyclin D1). Conversely, AMBP knockdown reversed the mRNA expression of these molecules. Additionally, TRP intervention significantly reduced AMBP mRNA expression in the HuCCT1-AMBP_OE group, accompanied by a marked decrease in β-catenin, c-Myc, and Cyclin D1 mRNA levels (Fig. 13).


### 3.13. Western blotting
  WB results revealed that in CCA cells, the expression of WNT signaling pathway-related molecules (β-catenin, p-GSK3β, c-Myc, and Cyclin D1) was significantly increased. AMBP overexpression further promoted activation of the WNT pathway, with β-catenin, c-Myc, p-GSK3β, and Cyclin D1 expression levels further significantly upregulated (Fig. 14). Moreover, AMBP overexpression increased the Bcl2/Bax ratio (antiapoptotic Bcl2↑, pro-apoptotic Bax↓), suppressed E-cadherin expression, and promoted N-cadherin expression, thereby inhibiting apoptosis and facilitating cancer cell invasion and metastasis (Fig. 15). However, AMBP knockdown reversed the expression of these proteins, inhibiting WNT pathway activation, promoting apoptosis, and impeding cancer cell invasion and metastasis.Figure 14.Western blotting detection of expression levels of AMBP and WNT signaling pathway-related molecules (β-catenin, p-GSK3β, c-Myc, and Cyclin D1) in cells of each group. GAPDH was used as the loading control. Representative blots from 3 independent experiments are shown. Statistical significance is indicated as: *P < .05, **P < .01, ***P < .001. AMBP = alpha(1)-microglobulin/bikunin precursor, GAPDH = glyceraldehyde-3-phosphate dehydrogenase. Figure 15.Western blotting detection of expression levels of molecules related to cell apoptosis and metastasis (Bcl, Bax, E-cadherin, and N-cadherin) in cells of each group. GAPDH was used as the loading control. Representative blots from 3 independent experiments are shown. Statistical significance is indicated as: *P < .05, **P < .01, ***P < .001. GAPDH = glyceraldehyde-3-phosphate dehydrogenase.

  In the HuCCT1-AMBP_OE-TRP group, Huaier polysaccharide significantly downregulated AMBP protein levels, accompanied by reduced expression of β-catenin, p-GSK3β, c-Myc, and Cyclin D1, thereby inhibiting WNT pathway activation (Fig. 14). Under Huaier polysaccharide treatment, the epithelial marker E-cadherin was significantly upregulated, while the mesenchymal marker N-cadherin was significantly downregulated, and the Bcl2/Bax ratio was reduced. These effects collectively inhibited cancer cell invasion and metastasis and induced cancer cell apoptosis (Fig. 15).

  In summary, Western blotting further confirmed the regulatory mechanism of the AMBP gene on the WNT signaling pathway, highlighting its critical role in this pathway. The experiments also demonstrated that Huaier polysaccharide can effectively target and reverse the abnormal activation of the WNT signaling pathway regulated by the AMBP gene.


## 4. Discussion
  This study systematically reveals the mechanism of the AMBP gene as a key regulatory factor in CCA and its potential for targeted therapy. Through multi-omics integrated analysis, we found that AMBP is significantly overexpressed in CCA, promoting tumor progression by activating the WNT signaling pathway while also being closely associated with the formation of an immunosuppressive tumor microenvironment.[16] Further research demonstrated that Huaier polysaccharides exhibit potential therapeutic value in targeting the AMBP gene to suppress CCA.[17]

  The AMBP gene, which encodes the glycoprotein precursor of α-1-microglobulin/bikunin, is cleaved into 2 functional proteins: A1M and Bikunin. A1M, a member of the lipocalin family, exhibits free radical scavenging, heme-binding, and anti-inflammatory functions.[15,18] Bikunin, a Kunitz-type protease inhibitor, regulates extracellular matrix remodeling and inflammatory responses.[15] In gastric and hepatocellular carcinomas, aberrant AMBP expression is significantly associated with tumor progression, chemotherapy resistance, and poor prognosis. For instance, elevated serum AMBP levels in gastric cancer patients correlate positively with lymph node metastasis and TNM stage progression, suggesting its role as a pro-tumorigenic factor in modulating the tumor microenvironment.[8] However, the role and molecular mechanisms of AMBP in CCA remain unclear.[19,20]

  In this study, RT-qPCR and Western blot confirmed that AMBP is highly expressed in CCA cells. Its overexpression promotes tumor proliferation by activating key molecules of the WNT pathway (β-catenin, c-Myc, and Cyclin D1).[15,21,22] This aligns with previous findings that aberrant WNT/β-catenin signaling is a hallmark of CCA, driving β-catenin nuclear translocation, upregulating c-Myc and Cyclin D1, and accelerating cell cycle progression.[4,23] Notably, AMBP overexpression also increases p-GSK3β (phosphorylated at Ser9), suggesting inhibition of GSK3β activity to stabilize β-catenin and enhance WNT signaling.[24–26]

  Additionally, AMBP overexpression resulted in an elevated Bcl2/Bax ratio, indicating that its antiapoptotic effect may be mediated by suppressing the mitochondrial apoptotic pathway, which aligns with reports of AMBP overexpression being associated with chemotherapy resistance in gastric cancer.[8] In terms of invasion and metastasis, AMBP overexpression significantly downregulated the epithelial marker E-cadherin and upregulated the mesenchymal marker N-cadherin, suggesting its role in promoting metastasis through EMT induction and matrix degradation.[25] The loss of E-cadherin is a critical event in CCA invasion and metastasis, and its expression level positively correlates with patient survival.[27,28] This study further confirmed that AMBP knockdown reverses these molecular changes and inhibits cancer cell invasion, providing a theoretical basis for targeting AMBP to intervene in metastasis.

  The intervention experiment of Huaier polysaccharide demonstrated that it can significantly downregulate the expression of AMBP mRNA and protein, and inhibit WNT pathway activity. This effect may be achieved through direct binding to AMBP or regulation of its transcription, though the specific mechanism requires further investigation. Additionally, Huaier polysaccharide restores E-cadherin expression and reverses the EMT process, consistent with its antimetastatic effects observed in liver and breast cancers.[29] Notably, Huaier polysaccharide also induces apoptosis by increasing the Bax/Bcl-2 ratio, highlighting its multi-target therapeutic properties.[30,31]The advantages of Huaier polysaccharide lie in its natural origin and low toxicity. For example, in gastric cancer, it enhances chemosensitivity to chemotherapeutic agents, while in CCA, its targeting of the AMBP–WNT axis may reduce side effects on normal tissues.[32,33]

  However, this study has limitations: the molecular mechanism by which AMBP regulates the WNT pathway requires further validation; the effects of Huaier polysaccharide on the AMBP-WNT axis have not been confirmed through functional experiments; and the immune microenvironment analysis needs additional experimental verification. Future research could involve constructing AMBP knockout mouse models, integrating single-cell sequencing technology to explore its regulatory network, and developing preclinical studies on nanoparticle-targeted delivery systems for Huaier polysaccharide to enhance therapeutic efficacy.

  In conclusion, this study systematically elucidates the central role of the AMBP–WNT signaling axis in CCA progression and reveals the therapeutic potential of Huaier polysaccharide in targeting this pathway, providing novel insights for precision treatment of CCA.


## 5. Conclusion
  The AMBP gene drives CCA proliferation, EMT, and metastasis by activating the WNT/β-catenin pathway, while Huaier polysaccharide reverses these malignant phenotypes through targeted suppression of AMBP expression. This discovery provides critical insights into the molecular mechanisms underlying CCA pathogenesis and offers a scientific foundation for the clinical application of Huaier polysaccharide.


## Author contributions
  Conceptualization: Chenrui Yang, Yajuan Liu.

  Data curation: Chenrui Yang, Yajuan Liu.

  Formal analysis: Chenrui Yang, Yajuan Liu.

  Investigation: Xiaoyong Wu, Yanliang Wang.

  Resources: Yanzhong Zhang, Yafan Yang.

  Software: Xiaoyong Wu, Yanliang Wang.

  Supervision: Yanzhong Zhang, Yafan Yang.

  Validation: Fangyuan Sun, Zhe Zhao.

  Visualization: Fangyuan Sun, Zhe Zhao.

  Writing – original draft: Chenrui Yang, Yajuan Liu.

  Writing – review & editing: Yanzhong Zhang, Yafan Yang.