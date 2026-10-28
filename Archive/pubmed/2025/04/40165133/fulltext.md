# Integrated bioinformatics and experiment validation reveal cuproptosis-related biomarkers and therapeutic targets in sepsis-induced myocardial dysfunction


## Background
  Sepsis-induced myocardial dysfunction (SIMD) is a serious sepsis complication with high mortality, yet current diagnostic and therapeutic approaches remain limited. The lack of early, specific biomarkers and effective treatments necessitates exploration of novel mechanisms. Recently, cuproptosis has been implicated in various diseases, but its role in SIMD is unclear. This study aimed to identify cuproptosis-related biomarkers and potential therapeutic agents, supported by animal model validation.


## Methods
  Four GEO datasets (GSE79962, GSE267388, GSE229925, GSE229298) were analyzed using Limma and WGCNA to identify overlapping genes from differentially expressed genes (DEGs), cuproptosis-related DEGs (DE-CRGs), and module-associated genes. Gene Set Enrichment Analysis (GSEA) and single-sample GSEA (ssGSEA) were performed to assess biological functions and immune cell infiltration, respectively. ceRNA and transcription factor networks were constructed to explore gene regulatory mechanisms, while consensus clustering was employed to define cuproptosis-related subtypes. Diagnostic genes were selected through SVM–RFE, LASSO, and random forest models. Additionally, potential gene-targeting agents were predicted using drug-gene interaction analysis. The findings were validated in SIMD animal models through qPCR and immunohistochemical analysis to confirm gene expression.


## Results
  PDHB and DLAT emerged as key cuproptosis-related biomarkers. GSEA indicated upregulation of oxidative phosphorylation and downregulation of chemokine signaling. ssGSEA revealed negative correlations with several immune cell types. A ceRNA network (51 nodes, 56 edges) was constructed. Machine learning identified PDHB, NDUFA9, and TIMMDC1 as diagnostic genes, with PDHB showing high accuracy (AUC = 0.995 in GSE79962; AUC = 0.960, 0.864, and 0.984 in external datasets). Using the DSigDB database, we predicted six drugs that exhibit significant binding activity with PDHB. qPCR and immunohistochemistry confirmed reduced PDHB and DLAT expression in SIMD animal models.


## Conclusion
  This study identifies PDHB and DLAT as cuproptosis-related biomarkers, addressing the diagnostic and therapeutic gaps in SIMD by unveiling novel molecular insights for early intervention and targeted treatment.


## Clinical trial number
  Not applicable.


## Supplementary Information
  The online version contains supplementary material available at 10.1186/s12879-025-10822-9.


## Introduction
  Sepsis-induced myocardial dysfunction (SIMD) is a severe consequence of sepsis that significantly impairs patient prognosis, with fatality rates reaching as high as 70 -90% in affected patients compared to only 20% in sepsis patients without cardiac dysfunction [1, 2]. Key features of SIMD include ventricular dilation, decreased ejection fraction, and diminished contractility [3]. Despite these well-recognized clinical manifestations, the underlying molecular mechanisms remain poorly understood, which has hindered the development of early diagnostic markers and effective, evidence-based therapies. Biomarkers, as a rapid and direct diagnostic tool, are critical for early identification and improving patient outcomes [4]. However, conventional diagnostic approaches often rely on traditional inflammatory or apoptotic markers, which lack specificity and sensitivity for SIMD.

  Copper, an essential trace element, is highly concentrated in the heart under normal physiological conditions [5, 6]. In patients with sepsis-induced myocardial dysfunction, increased serum copper levels have been positively correlated with impaired cardiac function [7]. The imbalance of copper ions in cardiomyocytes suggests an important, yet underexplored, role of copper-related cellular processes in SIMD. Cuproptosis, a recently defined mode of cell death triggered by the accumulation of Cu2+ ions [8], has been linked to the progression of cardiovascular diseases [9–11] and sepsis [12, 13]. Previous studies have focused predominantly on inflammatory responses and conventional apoptosis, the potential impact of cuproptosis in the pathogenesis of SIMD has not been adequately investigated [14, 15]. This gap in understanding motivates our study to explore the role of cuproptosis-related genes (CRGs) in SIMD.

  Recent advances in bioinformatics and machine learning provide powerful tools to integrate large-scale datasets and unravel complex disease mechanisms [16, 17]. These methods overcome limitations of traditional approaches by enabling the discovery of novel biomarkers and therapeutic targets through comprehensive data analysis and predictive modeling. In this study, we primarily analyzed the SIMD microarray dataset GSE79962 to identify cuproptosis-related feature genes. We further performed functional enrichment, immune infiltration, competing endogenous RNA (ceRNA), and transcription factor (TF) regulatory network analyses to elucidate the mechanisms underlying cuproptosis in SIMD. Unsupervised clustering was applied to reveal distinct cuproptosis-related subtypes, and three machine learning models (SVM–RFE, LASSO, and random forest) were constructed to select the most significant diagnostic markers. The diagnostic performance of these markers was validated using external datasets (GSE267388, GSE229925, and GSE229298). Moreover, we predicted potential therapeutic agents targeting the key diagnostic gene via molecular docking and verified the expression of feature genes in a SIMD animal model.

  In summary, our study explores a cuproptosis-focused approach to address diagnostic and therapeutic challenges in SIMD. By providing insights into the potential for early diagnosis and targeted treatment, this work offers a new perspective for further research into SIMD management. Figure 1 presents the study workflow (Fig. 1).

  Fig. 1The flowchart of this study. SIMD, sepsis-induced myocardial dysfunction; DE-CRGs, differentially expressed cuproptosis-related genes; DEGs, differentially expressed genes; GO, gene ontology; KEGG, kyoto encyclopedia of genes and genomes; WGCNA, weighted gene co-expression network analysis; ROC, receiver operating characteristic. GSEA, gene set enrichment analysis; ssGSEA, single-sample gene set enrichment analysis; ceRNA, competing endogenous RNA; GSVA, gene set variation analysis; Lasso, least absolute shrinkage and selection operator; SVM-RFE, support vector machine-recursive feature elimination; RF, radio frequency; DSigDB, drug signatures database


## Methods

### Data source
  The datasets used in this study were selected based on their relevance to SIMD, ensuring they contained gene expression profiles directly associated with SIMD. Additionally, they included a sufficient number of high-quality samples to ensure statistical reliability. All datasets are publicly available on the GEO database, supporting transparency and reproducibility. Specifically, the GSE79962 dataset, obtained from the GPL6244 platform, includes 51 left ventricular tissue samples, with 20 from sepsis patients and 11 from healthy controls, totaling 31 samples for analysis. The GSE267388 dataset, from the GPL28330 platform, includes 5 myocardial samples from SIMD mice and 5 control mice. The GSE229925 dataset, from GPL24247, includes 11 SIMD myocardial samples and 4 normal controls, while the GSE229298 dataset, also from GPL24247, contains 8 SIMD myocardial samples and 8 normal controls. All datasets were retrieved from the GEO database (https://www.ncbi.nlm.nih.gov/geo/).


### Statistical methods and data analyses

#### Differential expression gene analyses

##### Differential expression gene screening
  Examination of differential expression was performed utilizing the “limma” package within R software (version 4.4.1) [18]. The thresholds for identifying DEGs were set as adjusted p < 0.05 and log (fold change) > 0.5 or log (fold change) < -0.5, with the p-values being adjusted using the FDR method. Visualization of the results was carried out using the “ggplot2” and “heatmap” packages to generate the volcano plot and heatmap, respectively. The same approach was applied to analyze the differential expression of cuproptosis-related genes (CRGs) in SIMD patients and healthy controls. The list of CRGs was sourced from published studies [8].


##### Functional enrichment analysis
  Gene Ontology (GO) examination, which encompasses molecular function (MF), biological pathways (BP), and cellular components (CC), was undertaken to annotate the functions of genes. Additionally, Kyoto Encyclopedia of Genes and Genomes (KEGG) enrichment analysis serves as a valuable tool for investigating gene functions and associated high-level genomic information. Both analyses were carried out utilizing the R package “clusterProfiler”.


##### Weighted gene coexpression network analysis (WGCNA)
  We established a network of co-expressed DEGs by employing the R package “WGCNA”. Initially, the Pearson correlation coefficient (PCC) was calculated to construct a gene expression similarity matrix. Subsequently, Pearson correlation analysis was employed to generate an unsupervised gene expression matrix through the topological overlap measure (TOM). This matrix was then converted into a topological representation. Utilizing hierarchical clustering with average linkage, genes were grouped relying on their similar expression patterns, employing a 1-TOM criterion. A dynamic hearing algorithm was subsequently applied to mine gene comodules from the resulting clustering tree, where modules exhibiting a similarity of at least 75% were merged. Finally, to evaluate the credibility of the selected modules, we determined both module membership (MM) and gene significance (GS) for each gene within the target module, ensuring rigorous assessment. The same approach was used to build the modules with the greatest correlation to cuproptosis-related clusters.


##### Recognition of feature genes relying on receiver operating characteristic (ROC) curve and area under ROC curve (AUC) analysis
  The diagnostic significance of the intersecting genes among DEGs, DE-CRGs, and DiseaseWGCNA was evaluated through ROC curve and AUC analysis, employing the ‘pROC’ package in R. The same method was applied to determine the diagnostic worth of the intersection genes of LASSO, SVM and RF machine learning.


##### Gene set enrichment analysis (GSEA)
  GSEA is a technique founded on enrichment analysis, which ranks the genes in the gene concentration according to their differential expression, and calculates their related enrichment scores [19]. To investigate the influence of two feature genes on the processes involved in the development of SIMD, we employed this single-gene GSEA approach utilizing the “limma”, “org.Hs.eg.db”, “clusterProfiler” and “enrichplot” package.


##### Single-sample GSEA (ssGSEA)
  ssGSEA is relying on the improvement of GSEA method, and the gene expression data of each sample is normalized, and then the ssGSEA score corresponding to each gene set is calculated [20]. Specifically, we performed ssGSEA by R packages “GSVA” and “GSEABase” to assess the extent of infiltration of 28 distinct immune cell types within the GSE79962 dataset. The R package “limma” was then utilized to analyze and visualize the differentially expressed immune cells with the two feature genes in the SIMD group and the control group, respectively.


##### Competing endogenous RNA network and transcription factors search
  To identify potential messenger RNA, microRNA, and long noncoding RNA (mRNA-miRNA-lncRNA) interaction network involving the two feature genes, we initially queried MiRanda (http://www.microRNA.org), miRDB (https://mirdb.org/), and TargetScan (http://www.TargetScan.org/vert_71/) to locate miRNAs associated with PDHB and DLAT. The selection criteria stipulated that the miRNAs had to be predicted by all three databases. Subsequently, the corresponding lncRNAs for these miRNAs were identified using the SpongeScan website [21]. Furthermore, transcription factors (TFs) related to the PDHB and DLAT were predicted utilizing the TRRUST database (https://www.grnpedia.org/trrust/). Finally, we visualized these predictions with Cytoscape 3.10.2 (https://cytoscape.org/).


##### Genotyping analysis
  We employed the “ConsensusClusterPlus” package in R to exclude the control group from the GSE79962 dataset and then categorized SIMD patients into distinct molecular clusters according to the expression levels of CRGs. The highest count of fractals, k = 9, was ascertained through the analysis of the cumulative distribution function (CDF) curve, uniform clustering scores, and consensus matrix assessments. Subsequently, we utilized principal component analysis (PCA) to assess the significance of the clusters. Following this, the ‘limma’ and ‘pheatmap’ packages in R were employed to investigate the expression of DE-CRGs after clustering. Finally, we conducted gene set variation analysis (GSVA) employing the signature gene sets (c2.cp.kegg.symbols.gmt, c5.go.symbols.gmt) provided by the MSigDB database to evaluate the enrichment characteristics of the genes. Furthermore, the immune microenvironment of the clusters was calculated using the R package “CIBERSORT”.

  Identification of characteristic biomarkers through machine learning algorithms.


##### Model construction
  To find potential diagnostic biomarkers for SIMD, we selected 50 key genes common to “DiseaseWGCNA” and “ClusterWGCMA”. We used three machine learning models—LASSO regression, Random Forest (RF), and SVM-RFE—known for their effectiveness in feature selection and prediction accuracy with high-dimensional data.

  LASSO was used for variable selection and regularization to minimize overfitting and identify key predictors of SIMD [22]. The R package “glmnet” was used, with an initial λ = 1 and optimization of λ (lambda.min = 0.02020337) via 5-fold cross-validation. Important features were selected based on the optimal λ.

  RF was used to enhance model stability and accuracy by mitigating overfitting [23]. We utilized the “randomForest” R package with 500 trees and mtry set to 7 for feature selection. An optimal tree count of 23 minimized the error rate. Gene importance was ranked using the Gini index, and the top 10 genes were selected.

  SVM was used to handle high-dimensional data, with SVM-RFE iteratively removing less informative features [24]. Feature weights were determined using linear SVM, ranked by the squared mean-to-standard deviation ratio. To enhance robustness, k = 10 sub-sampling was used.

  To evaluate model robustness, we used cross-validation for LASSO and SVM, along with independent validation using datasets GSE267388, GSE229925, and GSE229298. Diagnostic accuracy of the selected genes was assessed via ROC curves and AUC analysis. Genes identified by all three methods were deemed the most reliable diagnostic biomarkers for SIMD.


##### Drug prediction and molecular docking
  Among the feature genes, NDUFA9, PDHB, and TIMMDC1, screened by the three machine learning models, PDHB was a differentially expressed cuproptosis-related gene in SIMD. Then, we used the Drug Signatures Database (DSigDB, http://dsigdb.tanlab.org/DSigDBv1.0/) to predict PDHB with P < 0.05 as the threshold and performed molecular docking for the significant drugs. The protein structure of PDHB was retrieved from the Protein Data Bank (PDB)(https://www.rcsb.org/), while the 3D or 2D structure of the drug was acquired from PubChem (https://pubchem.ncbi.nlm.nih.gov/). Finally, CB-Dock2 (https://cadd.labshare.cn/cb-dock2/index.php) was utilized to carry out molecular docking. A ΔG value of < -5 kcal/mol is considered indicative of potential binding activity [25].


#### Animal experiment validation

##### Animal grouping and modelling
  According to our team’s previous research [26], a group of male C57BL/6J mice, aged between six and eight weeks, were maintained in a meticulously controlled environment with a consistent 12-hour cycle of light and darkness, constant humidity and temperature, while also having unlimited access to food and water. Six mice were randomly grouped into two separate groups for this experiment. Specifically, the SIMD model mice (a total of 3) received an intravenous injection of lipopolysaccharide (LPS) at a dosage of 10 milligrams per kilogram of body weight for a time span of 12 h. Conversely, administered an identical volume of normal saline for comparison.


##### Echocardiography analysis of cardiac function
  After being administered LPS or saline, the mice were sedated with 1.0-1.5% isoflurane for 12 h. Echocardiography (30 MHz, VisualSonics Vevo 3100) was utilized to analyse changes in cardiac function. The internal diameter of the left ventricle (LV) was measured using two-dimensional (2D)-guided M-mode from the short-axis perspective at the location of the papillary muscles, averaging measurements over at least three consecutive heartbeats to ensure accuracy. Echocardiography results were utilized to assess cardiac function parameters, including ejection fraction (EF), fractional shortening (FS), left ventricular end-systolic diameter (LVESd), and left ventricular end-diastolic diameter (LVEDd).


##### Heart and serum sample collection and treatment
  Subsequently, the blood samples were processed by centrifugation at 3000 rpm for 20 min in a refrigerated environment maintained at 4 °C. The resulting serum was meticulously collected and frozen at -80 °C for further analysis. The mouse heart tissues were carefully harvested and washed with saline solution. These samples were later classified into two portions. One portion was promptly frozen at -80 °C for further qPCR, and the remaining portion was preserved with 4% paraformaldehyde for subsequent histopathological examinations and immunohistochemistry.


##### Haematoxylin and eosin (HE) staining
  The myocardial tissues from the mice were immersed in 4% paraformaldehyde, encapsulated in paraffin wax, and sliced into 4 μm sections. The sections were deparaffinized at 60 °C, followed by two incubations in xylene and dehydration with gradient dilutions of ethanol. Then, the sections were stained with Harris haematoxylin for 10 min and subsequently treated with 1% HCl in ethanol for 30 s. After 15 min of rinsing with tap water, the slices were stained with a 1% solution of iron red-stained eosin and treated with 90% ethanol. Next, the sections were subjected to a cleansing process in which they were immersed in 95% ethanol for one minute, followed by three consecutive rinses with xylene. Afterwards, the sections stained with H&E were incubated at room temperature for 20 min before being placed under a light microscope at a magnification of 400×. This allowed for the observation of any morphological alterations in the myocardium.


##### ELISA
  In compliance with the manufacturer’s guidelines, utilizing a series of specific ELISA kits for IL-1β (catalogue no: ELK1271), IL-6 (catalogue no: ELK1157), TNF-α (catalogue no: ELK1387), CKMB (catalogue no: ELK1286), and cTnT (catalogue no: ELK6207). The results are expressed in ng per mg of total protein.


##### Quantitative real-time PCR
  Cardiac tissue RNA extraction was carried out systematically with TRIzol reagent (ELKBiotechnology) in accordance with the manufacturer’s recommended procedure. Subsequently, using EntiLink 1st Strand cDNA Synthesis SuperMix (ELKBiotechnology, product code Eq. 031), reverse transcription of 2 micrograms of RNA samples was performed. The cDNA samples were then subjected to q-PCR analysis in a QuantStudio 6 Flex System (Life Technologies) using EnTurbo SYBR Green PCR SuperMix (ELK Biotechnology, Eq. 001). The internal control used for normalization was glyceraldehyde 3-phosphate dehydrogenase (GAPDH). The custom-designed and synthesized qPCR primers, as listed in Table 1, were procured from HY Cell Biotechnology (Wuhan, China). Relative gene expression levels were precisely calculated through the renowned 2−ΔΔCt approach.

  Table 1PCR primers for quantitative real-time PCRGenesForward (5’-3’)Reverse (5’-3’)PDHBGACCAGGTTATAAACTCAGCTGCGCATTACCACTGGGTTATTATCACDLATTCATCTGTATCACAGTTGAAAAGCGGAAGAACAATCTGCATATGAGTAGDLDTTGAATTTAGAGAAGATGATGGAGCTTTAAGGATAAAGCTCCTGTAGATGDBTCTGATCGACATTGAGACAGAAGCCCAACAACTTCACTCAGCTTAATATLIASGGATTAGATGTGTATGCACACAATGGAGCTTTCAGTGTGGCATAGACTTPDHA1GAACTTCTATGGAGGCAACGGCACAGTGCTGCCATATTGTAAGCDLSTTTGACATCAGTGTTGCAGTTGCGGTGAAGGTACCACCATCCATATNFE2L2GAGTCGCTTGCCCTGGATATCGGGAACAGCGGTAGTATCAGC


##### Immunohistochemistry
  After deparaffinization and dehydration, the tissue sections were subjected to an overnight incubation at 4 °C with PDHB and DLAT (Rabbit. No. 13426-1-AP, Proteintech, 1:500), following epitope retrieval, H2O2 treatment, and nonspecific antigen blocking. Next, the sections were incubated with secondary antibodies (Aspen. No. AS-1107, Servicebio, 1:200) at room temperature for two hours. Signal detection was conducted using an enhanced DAB staining kit (ZLI-9019, ZSGB-Bio). Images were acquired utilizing a light microscope (CX21, CX31, OLYMPUS). The staining intensity was evaluated with Image-Pro Plus version 6.0 (Media Cybernetics, Inc., Rockville, MD, USA).


## Results

### Differential expression analysis
  To elucidate differentially expressed genes, we obtained the SIMD-associated dataset GSE79962 from the GEO database. By applying stringent screening criteria of P-adjustment < 0.05 and absolute log fold-change (FC) > 0.5, a total of 442 DEGs were identified, with 227 genes upregulated and 215 genes downregulated (Additional file 1, Table S1). Comprehensive clustering analysis of these DEGs was performed, with results visually represented in a volcano plot (Fig. 2A). Furthermore, the dataset’s heatmap revealed distinct clustering patterns, underscoring an enhanced level of sample stratification and analytical confidence (Fig. 2B).

  Fig. 2Data preprocessing for differentially expressed genes (DEGs). A Volcano plot in GSE79962. B Heatmap of DEGs expression. Red represent up-regulation and blue represent down-regulation


### Enrichment analysis of functional pathways for DEGs associated with SIMD
  Enrichment analysis revealed that in the BP category, DEGs were significantly enriched in energy metabolism by oxidation of organic compounds, muscle tissue development, and purine nucleotide metabolism. In the CC category, genes were primarily associated with the mitochondrial inner membrane, mitochondrial protein complexes, and oxidoreductase complexes. In the MF category, enriched terms included quinone binding, haptoglobin binding, and RAGE receptor binding (Fig. 3A, B). KEGG pathway analysis identified key pathways such as oxidative phosphorylation, cellular senescence, HIF-1 signaling, adipocytokine signaling, ferroptosis, and glycolysis/gluconeogenesis. Additionally, diseases like Huntington’s disease, diabetic cardiomyopathy, and Alzheimer’s disease were significantly enriched (Fig. 3C, D). Detailed enrichment information on the oxidative phosphorylation is shown below (Fig. 3E). These findings highlight the critical roles of DEGs in mitochondrial function, energy metabolism, and cellular stress responses.

  Fig. 3Functional enrichment study based on DEGs. A, B GO analysis from three perspectives: biological processes, cellular composition, and molecular function. C, D KEGG pathway analysis. E Pathways of Oxidative phosphorylation


### Differential expression and correlation analysis of cuprotosis-related genes in SIMD
  Differential analysis identified eleven significantly dysregulated cuproptosis-related genes (DE-CRGs) between the SIMD and control groups, including NFE2L2, FDX1, LIAS, LIPT2, DLD, DLAT, PDHA1, PDHB, MTF1, DBT, and DLST. Among them, NFE2L2 and MTF1 were significantly upregulated in SIMD, while the remaining genes exhibited lower expression levels in the SIMD group compared to controls (Fig. 4A). The heatmap visualization of DE-CRGs (Fig. 4B) further confirmed this expression trend, which was consistent with the box plot results.

  To further explore potential regulatory interactions among these genes, we performed a correlation analysis (Fig. 4C, D). A strong positive correlation was observed between PDHB and DLD (R = 0.82, p = 1.4e-08) (Fig. 4E), suggesting potential co-regulation or functional interdependence in SIMD pathology. Conversely, a significant negative correlation was detected between DLAT and NFE2L2 (R=-0.73, p = 3e-06) (Fig. 4F), indicating possible opposing regulatory mechanisms. Given that NFE2L2 is a well-known transcription factor involved in oxidative stress response, its upregulation in SIMD may reflect a compensatory mechanism to counteract cellular damage [27], while the downregulation of DLAT, a key enzyme in pyruvate metabolism, may suggest metabolic dysfunction [28]. These findings imply that cuproptosis-related genes might be intricately involved in the pathophysiological processes of SIMD, potentially influencing oxidative stress and metabolic pathways.

  Fig. 4Differential expression and correlation analysis of CRGs in SIMD. A Box diagram and (B) heatmap of the 19 CRGs between between SIMD and normal samples. C Correlation coefficient network and (D) matrix diagram between the 11 DE-CRGs. E The Pearson correlation coefficient graph displayed the strongest positive and (F) the strongest negative correlation. *P < 0.05, **P < 0.01, ***P < 0.001


### Functional pathway enrichment analysis of DE-CRGs
  The GO annotation for the BP category indicated that DE-CRGs participate in processes such as acetyl-CoA metabolism, thioester metabolism, and the tricarboxylic acid cycle. The mitochondrial matrix and oxidoreductase complex were significantly enriched in the CC category. The oxidoreductase activity, iron-sulfur cluster binding and metal cluster binding were significantly enriched in the MF category (Fig. 5A, B). KEGG analysis showed their association with Lipoic acid metabolism, Citrate cycle (TCA cycle) and Carbon metabolism (Fig. 5C, D). Detailed enrichment information of the Lipoic acid metabolism is shown in the figure below (Fig. 5E). These results suggest that TCA cycle, energy metabolism and metal metabolism play a key role in cuproptosis, which is similar to the results of SIMD functional enrichment.

  Fig. 5Functional enrichment study based on DE-CRGs. A, B GO analysis from three perspectives: biological processes, cellular composition, and molecular function. C, D KEGG pathway analysis. E Pathways of lipoic acid metabolism


### Hub modules and genes identified by WGCNA in SIMD (disease WGCNA)
  A total of 19,975 genes across 31 samples were extracted from GSE79962 dataset for analysis. The heatmap suggested that clinical traits can be roughly divided into three modules, two of which are associated with SIMD (Fig. 6A). Subsequently, when the soft threshold was chosen at a scale independence of 0.9 (R2 = 0.9), a power of β = 9 was determined, and the mean connectivity was high (Fig. 6B). The minimum gene count per module was set at 100 using the dynamic tree cutting algorithm. Furthermore, cluster dendrogram (Fig. 6C) and network heatmap (Fig. 6D) were generated, and the data were analysed to correlate the modules with clinical traits. Seven distinct modules were identified (Fig. 6E), with the brown module (consisting of 792 genes) recognized as the central module for clinical trait associations. To highlight the hub genes, module membership (MM) and gene significance (GS) were correlated (Additional file 2, Table S2), resulting in the identification of 277 key genes with MM > 0.7 and GS > 0.5 (Fig. 6F).

  Fig. 6Key modules and genes identified by WGCNA in SIMD. A Sample dendrogram and trait heatmap. B Scale-free fit parameters of different soft-thresholding powers and the average connectivity. C Cluster dendrogram of different co-expression modules. D Network heatmap plot of 7 modules. E Heatmap of module-trait correlations. F Scatter plot of module membership and gene significance in the brown module


### Identifying the intersection feature genes
  By determining the intersection of the DEGs, DE-CRGs, and hub genes identified through DiseaseWGCNA, two overlapping genes (PDHB and DLAT) were identified (Fig. 7A). In SIMD, both PDHB and DLAT were lowly expressed (Fig. 7B, C). The diagnostic significance of the two genes was verified through ROC curve and AUC analysis (PDHB: 0.995, DLAT: 0.959) (Fig. 7D).

  Fig. 7Identifying the feature genes. A Venn diagram of DEGs, DE-CRGs and DiseaseWGCNA. B PDHB expression. C DLAT expression. D Quantification of ROC curves values of AUC for PDHB and DLAT


### Functional enrichment analysis and immune characteristics correlation analysis of two feature genes
  GSEA analysis was performed to achieve a comprehensive understanding of the pathways related to the two identified feature genes. In the GSEA analysis of PDHB, the up-regulated pathways were valine, leucine, and isoleucine degradation, oxidative phosphorylation, and Parkinson’s disease. The down-regulated pathways were chemokine signaling pathway, focal adhesion, and ECM receptor interaction (Fig. 8A). For DLAT, the pathways of Parkinson’s disease, oxidative phosphorylation, and Huntington’s disease were up-regulated, while the chemokine signaling pathway, NOD-like receptor signaling pathway, and cytokine receptor interaction were down-regulated (Fig. 8B). ssGSEA was used to analyze immune signatures associated with the two feature genes. The immune cells associated with PDHB were natural killer T cell, natural killer cell, memory B cell, macrophage, central memory CD4 T cell, type 1 T helper cell, plasmacytoid dendritic cell, and effector memory CD8 T cell. All of them were negatively correlated with PDHB (Fig. 8C). Type 1 T helper cell, natural killer T cell, natural killer cell, and central memory CD4 T cell had a significant negative association with DLAT (Fig. 8D). Integrated analysis revealed that the oxidative phosphorylation pathway exhibited marked upregulation in feature genes, whereas chemokine signaling demonstrated downregulation. Notably, significant negative correlations were observed between both genes and NK/NKT cells. These findings collectively suggest that cuproptosis may contribute to the pathological progression of SIMD through these pathways and cellular components.

  Fig. 8Gene set enrichment analysis (GSEA) and immune characteristics correlation analysis. The pathway related to two genes (A) PDHB and (B) DLAT. Correction between (C) PDHB and (D) DLAT


### Prediction of mRNA-miRNA-lncRNA ceRNA network and TF-miRNA-hub gene network for SIMD
  We further investigated the possible regulatory mechanism of these two genes in SIMD. Three online miRNA databases (miRanda, miRDB and TargetScan) were used to predict the miRNAs regulating PDHB and DLAT activity. The findings showed that PDHB and DLAT were targeted by a total of 54 miRNAs (Additional file 3, Table S3). Subsequently, we predicted 42 lncRNAs that bind to these miRNAs (Additional file 4, Table S4). Using Cytoscape software, we developed an mRNA-miRNA-lncRNA ceRNA network consisting of 51 nodes and 56 edges, representing intricate regulatory interactions (Fig. 9A). Furthermore, two transcription factors (TFs) were identified as targets for PDHB and DLAT (Fig. 9B).

  Fig. 9Characteristic gene regulatory network. A lncRNA-miRNA-mRNA ceRNA network. B mRNA-TF network


### Identification of cuproptosis-related clusters in SIMD patients
  To further explore the expression of CRGs in SIMD, we classified patients by analysing the expression profiles of 11 DE-CRGs. K = 2 optimally divided patients into C1 (high expr., n = 11) and C2 (low expr., n = 9) clusters (Fig. 10A). The cumulative distribution function (CDF) plot visualizes the consensus levels across each K value (Fig. 10B), while the delta area plot highlights the comparative variation in the area beneath the CDF curve (Fig. 10C). PCA revealed distinct cuproptosis transcription profiles between the two clusters (Fig. 10D).

  Fig. 10Identification of cuproptosis-related clusters in SIMD patients. A Consensus clustering analysis of 11 DE-CRGs at k = 2. B Consensus index of the cumulative distribution function (CDF). C Relative change in the area under the CDF delta curves for k = 2 by increasing the index from 2 to 9. D Principal component analysis (PCA)


### Cluster analysis
  Analysis of DE-CRGs across clusters revealed significant differences in eight genes, including NFE2L2, LIAS, DLD, DLAT, PDHA1, PDHB, DBT, and DLST. NFE2L2 was upregulated in C1, while the others were downregulated compared to C2 (Fig. 11A, B). GSVA identified distinct functional enrichments: C1 was associated with copper ion homeostasis, immune response, and inflammatory pathways, while C2 was enriched in metabolic processes, including the TCA cycle, oxidative phosphorylation, and fatty acid metabolism (Fig. 11C, D). KEGG analysis further highlighted the activation of NOD-like and TOLL-like receptor signaling in C1, whereas metabolic pathways dominated in C2. Immune cell infiltration analysis showed a significant increase in NKT cells, megakaryocytes, and MEPs in C1, while CD4 + Tem, hepatocytes, macrophages (M1), mesangial cells, and preadipocytes were upregulated in C2 (Fig. 11E). Collectively, these findings suggest that C1 is more closely linked to cuproptosis, while C2 is primarily driven by metabolism.

  Fig. 11Differential expression and enrichment analysis of clusters. The expression levels of the 11 DE-CRGs in the two clusters are shown in the box diagram (A) and (B) heatmap. C GSVA of GO terms between C1 and C2 clusters. D GSVA of KEGG terms between C1 and C2 clusters. E Box plot of immune cell infiltration. *P < 0.05, **P < 0.01, ***P < 0.001


### Hub modules and genes identified by WGCNA in clusters (Cluster WGCNA)
  Similarly, we conducted WGCNA analysis to examine correlations following the clustering analysis. The heatmap suggested that clinical traits can be roughly divided into six modules (Fig. 12A). When R2 = 0.9, a power of β = 9 was determined (Fig. 12B). Cluster dendrogram (Fig. 12C) and network heatmap (Fig. 12D) were generated, and ten distinct modules were identified (Fig. 12E), indicating that the genes represented in yellow are highly positively correlated within Cluster C2 (Fig. 12F) (Additional file 5, Table S5).

  Fig. 12Key modules and genes identified by WGCNA in Clusters. A Sample dendrogram and trait heatmap. B Scale-free fit parameters of different soft-thresholding powers and the average connectivity. C Cluster dendrogram of different co-expression modules. D Network heat map plot of 10 modules. E Heatmap of module-trait correlations. F Scatter plot of module membership and gene significance in the yellow module


### Construction and validation of the Lasso model, RF model, and SVM model
  We designed three algorithms aimed at identifying genes with diagnostic potential for SIMD from a total of 50 overlapping genes from DiseaseWGCNA and ClusterWGCNA (Fig. 13A). Lasso model results showed an association between the expression of four genes and the occurrence of SIMD (Fig. 13B) (Additional file 6, Table S6). Random forest analysis assessed how error rates varied with the number of classification trees, ultimately highlighting 10 genes with notable relative importance (Fig. 13C; Additional file 7, Table S7). Concurrently, the SVM-RFE method identified a subset of six genes, optimizing classification accuracy to 0.967 while minimizing the error rate to 0.033 (Fig. 13D) (Additional file 8, Table S8). The key genes screened by three machine learning methods intersected, and three diagnostic characteristic genes were obtained, among which PDHB was one of the DE-CRGs (Fig. 13E).

  Fig. 13Construction of three machine learning models. A Venn diagram of DiseaseWGCNA and ClusterWGCNA. B Regression coefficient path diagram and cross-validation curves in LASSO. C The identification of feature importance based on random forests. D The curve of change in the predicted true and error value of each gene in SVM-RFE. E Venn diagram of the there feature genes obtained from the LASSO, SVM-RFE, and RF


### Identification and validation of feature genes
  We explored ROC analysis to assess the diagnostic effectiveness of these three genes. This method allowed us to quantitatively evaluate their ability to differentiate between individuals with SIMD and healthy individuals. The main focus of our analysis was the AUC (Area Under the Curve) value, which acts as a comprehensive measure of the ROC curve’ s performance. Our detailed evaluation yielded intriguing results, as the examination of the diagnostic efficacy for all three genes indicated considerable predictive value. The AUC values of PDHB were 0.995 (GSE79962), 0.960 (GSE267388), 0.864 (GSE229925) and 0.984 (GSE229298) (Fig. 14A). The AUC values of NDUFA9 were 0.973 (GSE79962), 0.920 (GSE267388), 0.750 (GSE229925) and 0.680 (GSE229298) (Fig. 14B). The AUC values of TIMMDC1 were 0.982 (GSE79962), 0.920 (GSE267388), 0.750 (GSE229925) and 0.969 (GSE229298) (Fig. 14C).

  Fig. 14ROC curves and area under the curve of (A) PDHB, (B) NDUFA9 and (C) TIMMDC1 in GSE79962 and three external datasets


### Prediction of candidate drugs
  Based on the above studies, we discovered the potential of PDHB as a diagnostic molecular marker and a therapeutic target for SIMD. We then consulted the DSigDB database to pinpoint drugs with potential efficacy in targeting PDHB. Based on the P value < 0.05, a total of seven drugs including FERRIC AMMONIUM CITRATE, oxidopamine, Imatinib, Cube root extract, deferoxamine, SARIN and vinblastine (Table 2) (Fig. 15A). We further used molecular docking to study the binding between PDHB and 7 drugs (Fig. 15B, C, D, E, F, G, H). Molecular docking verification confirmed that except for SARIN, the other six drugs had low binding energy to PDHB (Table 3).

  Table 2The potential drugs of PDHB were identified using DSigDBTermP-valueCombined ScoreGenesFERRIC AMMONIUM CITRATE0.001272459133525.5449PDHBoxidopamine0.001985036124555.5316PDHBImatinib0.005700616104439.6051PDHBCube root extract0.010077874101200.0793PDHBdeferoxamine0.01058685890072.39007PDHBSARIN0.0117575288554.31179PDHBvinblastine0.01353896388371.92302PDHB

  Fig. 15Prediction of the top 7 candidate drugs for SIMD based on PDHB. A The netplot of PDHB with 7 drugs. Molecular docking between PDHB and (B) FERRIC AMMONIUM CITRATE, (C) oxidopamine, (D) Imatinib, (E) Cube root extract, (F) deferoxamine, (G) SARIN and (H) vinblastine

  Table 3Binding energy of PDHB to seven candidate drugsDrugsFERRIC AMMONIUM CITRATEoxidopamineImatinibCube root extractdeferoxamineSARINvinblastineBinding energy (kcal/mol)-7.0-6.2-10.1-10.1-6.7-4.8-9.0


### Experimental validation
  To further validate the transcriptomics analysis findings, we established a SIMD animal model. Echocardiography revealed decreased heart function after LPS injection (Fig. 16A, B, E, F). HE staining revealed a disrupted myocardium, swollen/broken fibres, and inflammatory cell infiltration after LPS treatment (Fig. 16C, D). ELISA demonstrated elevated serum markers of myocardial damage, CKMB and cTnT, and the inflammatory factors IL-6, TNF-α, and IL-1β (Fig. 16G, H, I, J, K). Based on the above results, the SIMD mouse model was successfully established.

  Subsequent q-PCR revealed that the expression of 8 DE-CRGs significantly differed between the SIMD mice and controls (Fig. 17A, B, C, D, E, F, G, H). Then, we conducted IHC staining and found that the levels of PDHB (Fig. 18A, B) and DLAT (Fig. 18C, D) were significantly lower in the SIMD mice tissue samples than in the control samples.

  Fig. 16Construction of SIMD mouse model. A, B Representative echocardiographic images. C, D Representative images showing HE-stained sections of heart tissues. Scale bar: 50 mm. Echocardiographic data comparing left ventricle (E) ejection fraction (EF) and (F) fractional shortening (FS). ELISA results for (G) CKMB, (H) cTnT, (I) IL-6, (J) TNF-α, and (K) IL-1β in heart tissues. *P < 0.05, **P < 0.01

  Fig. 17The mRNA differential expression of (A) PDHB, (B) DLAT, (C) DLD, (D) DBT, (E) LIAS, (F) PDHA1, (G) DLST, (H) NFE2L2 was analyzed by PCR in SIMD mouse and controls. **P < 0.01, ***P < 0.001

  Fig. 18Immunohistochemical staining analysis of two feature genes. A Quantitative immunohistochemical profiling of PDHB expression. B Immunohistochemical staining for PDHB. C Quantitative immunohistochemical profiling of DLAT expression. D Immunohistochemical staining for DLAT. ***P < 0.001


## Discussion

### Summary of our work
  In this study, we applied bioinformatics methods using the GEO database to identify key copper toxicity-related genes, PDHB and DLAT, which are significantly associated with sepsis-induced myocardial dysfunction (SIMD). Machine learning techniques further validated PDHB as a diagnostic gene for SIMD. Our animal experiments confirmed that PDHB and DLAT are differentially expressed in SIMD mouse models compared to controls.


### Cuproptosis and its role in SIMD
  Recent studies have focused on the role of metal ions in cell death, particularly cuproptosis, which is driven by excessive copper accumulation in cells, leading to mitochondrial dysfunction. Unlike ferroptosis, cuproptosis results from copper toxicity that disrupts mitochondrial function [29]. Our study explored the involvement of cuproptosis-related genes (CRGs) in SIMD and identified 11 differentially expressed CRGs and highlighted PDHB and DLAT as feature genes. These genes, along with PDHA1, are components of the pyruvate dehydrogenase (PDH) complex, which is vital for cellular energy metabolism. PDHB catalyzes the conversion of pyruvate into acetyl-CoA [30], while DLAT transfers acetyl groups to acetyl-CoA, crucial for efficient cellular energy production [31].


### Impact of PDHB and DLAT on energy metabolism and heart function
  RNA sequencing of tissue samples from 95 human subjects revealed that PDHB and DLAT are highly expressed in heart tissue [32], where their downregulation leads to reduced PDH activity, ATP production, and accumulation of pyruvate and lactate. These changes are associated with cardiomyopathies [33], and heart failure [34]. In SIMD, oxidative phosphorylation pathways were upregulated, while chemokine signaling was downregulated. Disruption of mitochondrial function occurs when elevated copper levels bind to lipoylated DLAT, leading to impaired oxidative phosphorylation and mitochondrial dysfunction [35], which impairs the TCA cycle and inhibits oxidative phosphorylation, ultimately leading to mitochondrial dysfunction. Chemokines, a small class of cytokines, primarily regulate cell migration and localization, particularly in immune response and inflammation [36]. Immune cell infiltration analysis indicated a negative correlation between PDHB and DLAT expression and NK/NKT cells, suggesting their role in regulating immune responses in SIMD.


### Machine learning for diagnostic biomarkers and drug discovery
  We classified SIMD into two subtypes based on CRG expression: Cluster C1, which shows a stronger correlation with cuproptosis. Using machine learning techniques such as LASSO, RF, and SVM-RFE, we identified three potential diagnostic biomarkers: NDUFA9, PDHB, and TIMMDC1. NDUFA9 stabilizes complex I in the mitochondrial respiratory chain [37, 38], and TIMMDC1 is implicated in mitochondrial complex I deficiency [39]. ROC and AUC analyses confirmed PDHB as a reliable diagnostic biomarker for SIMD. Moreover, using PDHB as a target, we identified several potential therapeutic drugs. Deferoxamine, an iron chelator, has previously been shown to alleviate CLP-induced septic shock in rats by reducing oxidative stress, curbing neutrophil infiltration, and preventing mitochondrial dysfunction [40]. Furthermore, deferoxamine’s analog, deferoxone, has potent antioxidant properties and can suppress both ferroptosis and cuproptosis, which are implicated in various free radical-related diseases [41]. Other potential drugs identified include FERRIC AMMONIUM CITRATE F, which induces ferroptosis in cardiomyocytes [42, 43], and Imatinib and Vinblastine, common chemotherapy agents with known anticancer effects [44, 45].


### Animal model validation and future implications
  Additionally, we constructed an animal model of SIMD and confirmed the expression of DE-CRGs through q-PCR and immunohistochemical analysis. Consistent with the genomic data, the expression of PDHB and DLAT was significantly downregulated in the myocardial tissue of SIMD mice, further validating their role in SIMD. These genes could be used in early diagnostic panels for SIMD, allowing clinicians to detect myocardial dysfunction before it progresses to heart failure. Furthermore, their roles in mitochondrial dysfunction and energy metabolism suggest that they could serve as therapeutic targets for improving cardiac function in septic patients. For instance, modulating the expression or activity of PDHB and DLAT could restore mitochondrial function and enhance cardiac energy production, providing a novel approach for treating SIMD. Moreover, the combination of PDHB and DLAT as diagnostic biomarkers may help stratify patients based on the severity of myocardial dysfunction, thereby facilitating the development of more targeted and personalized treatment strategies.


### Limitation in our study
  Despite the promising results, several limitations must be addressed. Translating findings from animal models to human studies requires validation in human myocardial tissue from SIMD patients. Species-specific metabolic and immune differences need careful consideration. Multi-center clinical cohorts could help assess the reliability of PDHB and DLAT as biomarkers across different populations. Further mechanistic studies are needed to fully understand the roles of these genes and explore potential therapeutic interventions targeting cuproptosis and mitochondrial dysfunction in SIMD.


## Conclusion
  In conclusion, our study identifies PDHB and DLAT as critical cuproptosis-related genes involved in SIMD. These genes may serve as diagnostic biomarkers and therapeutic targets for SIMD, providing valuable insights into its molecular mechanisms and paving the way for more targeted diagnostic and therapeutic strategies.


## Electronic supplementary material
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2

  Supplementary Material 3

  Supplementary Material 4

  Supplementary Material 5

  Supplementary Material 6

  Supplementary Material 7

  Supplementary Material 8


## Acknowledgements
  Not applicable.