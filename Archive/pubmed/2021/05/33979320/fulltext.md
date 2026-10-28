# Decreased HLF Expression Predicts Poor Survival in Lung Adenocarcinoma


## Background
  Lung adenocarcinoma (LUAD) is a type of non-small cell carcinoma. Its pathogenesis is being explored and there is no cure for the disease.


## Material/Methods
  The Gene Expression Omnibus (GEO) was searched to obtain data on expression of messenger RNA. GEO2R, an interactive web tool, was used to calculate the differentially expressed genes (DEGs) in LUAD. All the DEGs from different datasets were imported into VENNY 2.1 (https://bioinfogp.cnb.csic.es/tools/venny/index.html) to identify the intersection of the DEGs. An online analysis tool, the Database for Annotation, Visualization, and Integrated Discovery (DAVID), was used to help understand the biological meaning of DEG enrichment in LUAD. Cytoscape 3.7.2 was used to perform centrality analysis and visualize hub genes and related networks. Furthermore, the prognostic value of the hub genes was evaluated with the Kaplan-Meier plotter survival analysis tool.


## Results
  The GEO database was used to obtain RNA sequencing information for LUAD and normal tissue from the GSE118370, GSE136043, and GSE140797 datasets. A total of 376 DEGs were identified from GSE118370, 248 were identified from GSE136403, and 718 DEGs were identified from GSE140797. The 10 genes with the highest degrees of expression – the hub genes – were CAV1, TEK, SLIT2, RHOJ, DGSX, HLF, MEIS1, PTPRD, FOXF1, and ADRB2. In addition, Kaplan-Meier survival evaluation showed that CAV1, TEK, SLIT2, HLF, MEIS1, PTPRD, FOXF1, and ADRB2 were associated with favorable outcomes for LUAD.


## Conclusions
  CAV1, TEK, SLIT2, HLF, MEIS1, PTPRD, FOXF1, and ADRB2 are hub genes in the DEG interaction network for LUAD and are involved in the development of and prognosis for the disease. The mechanisms underlying these genes should be the subject of further studies.


## Background
  Non-small cell lung carcinoma (NSCLC) includes large cell carcinoma, squamous cell carcinoma (SCC), and adenocarcinoma [1]. Unlike squamous cell lung cancer, lung adenocarcinoma (LUAD) is more common in non-smokers and women [2]. The incidence of LUAD is lower than for SCC and undifferentiated cancer and patients diagnosed with it are younger [2]. In general, there are no obvious clinical symptoms in the early stage of the disease and it often is diagnosed on a chest X-ray. LUAD tends to spread through the bloodstream in early stages, whereas metastasis through the lymphatic system occurs much later [3].

  The pathogenesis of lung cancer is complex and involves multiple causes and genes [4]. Many studies are focusing on the pathological mechanism of LUAD [1,4]. However, the cause of lung cancer is still unclear, and there is no cure for it [2]. Exploring the process of LUAD at the gene and protein level can provide detailed and useful information for a comprehensive understanding of the disease.

  Based on big data, bioinformatics methods are an increasingly popular way of exploring the role of differentially expressed genes (DEGs) in disease [5]. Hub genes can be identified by analyzing the DEG interaction network. Bioinformatics has been used to identify some diseases, especially in oncology [6]. However, few studies have combined assessment of DEG interaction networks and survival analysis for LUAD. Therefore, the aim of the present study was to use bioinformatics methods to retrieve the DEGs for LUAD, analyze the interaction network of the DEGs, identify hub genes in LUAD, and perform a Kaplan-Meier survival analysis.


## Material and Methods

### Search of Gene Chip Data
  The Gene Expression Omnibus (GEO) is a gene expression database created and maintained by the National Center for Biotechnology Information of the National Library of Medicine in the United States. We searched this database for gene chip data that compared tissue from LUAD with normal tissue. The keywords used were “lung adenocarcinoma.” Matrix data on messenger RNA (mRNA) expression were downloaded for analysis.


### Identification of Differentially Expressed Genes
  GEO2R is online software used to analyze data from GEO. We imported the data into the tool and analyzed it with the default settings. The DEG information was provided by GEP2R, which sorted the DEGs with LogFC. P<0.05 and LogFC >2 were considered statistically significant. DEGs from different datasets were imported into Venn. Venn was used to identify DEGs that were common to the different datasets (http://bioinformatics.psb.ugent.be/webtools/Venn/).


### Gene Ontology and Kyoto Encyclopedia of Genes and Genomes Pathway Enrichment Analysis of Genes
  We used the Database for Annotation, Visualization and Integrated Discovery (DAVID) 6.8 to explore the biological roles of involved genes [7,8]. Gene ontology (GO) enrichment and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway analyses were performed with DAVID. DEGs were imported into DAVID with the setting “gene list” and “gene symbol,” and the associated GO and KEGG terms were obtained. The top 3 terms for biological process, cellular component, and molecular function, and the KEGG pathway with the highest P value were selected.


### Protein–Protein Interaction Network Analysis
  The Protein–Protein Interaction (PPI) network can be used to show the functional relationship between common DEGs. Upregulated and downregulated genes were imported into the Search Tool for the Retrieval of Interacting Genes (STRING) to establish the network. The file “string_interactions.tsv” was downloaded. Then the PPI network “string_interactions.tsv” was imported into Cytoscape software (version 3.7.2) and visualized [9]. Using the software Centiscape 2.2 in Cytoscape, the DEGs were ranked by degree centrality. That information for the top 10 DEGs in the network was visualized with ggplot2 [10]. The enrichment results for the top 10 DEGs and the GO and KEGG terms were visualized with GOplot [11].


### Kaplan-Meier Survival Analysis of Hub Genes
  All the hub genes were imported into the Kaplan-Meier plotter web tool (http://kmplot.com/analysis/) [12]. The Kaplan-Meier plotter can assess the effect of 54 000 genes on survival in 21 cancer types, helping us discover and validate survival biomarkers [13]. Kaplan-Meier survival analysis results for each hub gene were obtained with default settings: “lung adenocarcinoma,” “auto select best cutoff,” and “all the follow-up threshold.” P<0.01 was defined as a statistically significant difference.


### Cell Culture and Transfection
  The LUAD cell line A549 was purchased from the Shanghai Cell Bank. Dulbecco’s modified Eagle’s medium and 10% fetal bovine serum were used to culture all the cells at 37°C in 5% CO2. For transfection, the negative control small interfering RNA (siRNA) and HLF siRNA were designed by Suzhou GenePharma Biotechnology Co., Ltd. A549 cells were transfected with 100 nM NC siRNA or HLA siRNA using Lipofectamine® 3000.


### Quantitative Reverse Transcription Polymerase Chain Reaction
  Invitrogen TRIzol was used to extract the total RNA from the cells and tissues. Quantitative real-time reverse transcription polymerase chain reaction (qRT-PCR) was performed to determine the HLF mRNA level. The primers were designed by Shanghai Bio Tech, as follows:

  The 2−ΔΔCq approach was used to quantify the HLF mRNA level.


## Results

### Identification of DEGs
  Gene expression profiles from the GSE118370, GSE136043, and GSE140797 datasets were obtained from the GEO database. GSE118370 is a LUAD dataset; GSE136043 is an mRNA microarray from lung cancer not otherwise specified, and GSE140797 is 7 pairs of LUAD tissue and normal tissue. There were 6 LUAD and 6 normal specimens in GSE118370, 5 LUAD and 5 normal in GSE136043, and 7 LUAD and 7 normal specimens in GSE140797 (Table 1). Next, 245 upregulated and 686 downregulated DEGs were identified in GSE118370; 617 upregulated and 687 downregulated DEGs were identified in GSE136043; and 1073 upregulated and 1281 downregulated DEGs were identified in GSE140797. Finally, 35 common upregulated and 142 common downregulated DEGs were obtained from the 3 datasets (Figure 1).


### Gene Ontology and Kyoto Encyclopedia of Genes and Genomes Enrichment Analysis of DEGs
  For all the common DEGs, GO and KEGG analysis results showed that during biological processes, common DEGs were significantly enriched in cell adhesion, morphogenesis of a branching structure, and angiogenesis. In molecular function, common DEGs were significantly enriched in protein binding, lipid binding, transcriptional activator activity, and RNA polymerase II core promoter proximal region sequence-specific binding. In the cellular component, common DEGs were significantly enriched as an integral component of the plasma membrane, the membrane raft, and the plasma membrane. In the KEGG pathway, common DEGs were significantly enriched in extracellular matrix-receptor interaction, protein digestion and absorption, and axon guidance (Table 2).


### PPI Network Construction and Module Analysis
  The network of protein interactions was obtained using STRING and then the top 10 hub genes with high degrees of expression were identified using Cytoscape (Figure 2). Those hub genes were CAV1, TEK, SLIT2, RHOJ, DGSX, FOXF1, HLF, MEIS1, PTPRD, and ADRB2, all of which were downregulated in LUAD. The degree centrality information for the hub genes is shown in Figure 3 and Table 3. Results of GO and KEGG enrichment analysis of the hub genes are shown in Figure 4. GO and KEGG analysis is one of the most important parts of bioinformatics. It can help us systematically understand the ways in which DEGs, including hub genes, affect biological functions. In the present study, the results of GO and KEGG analysis revealed the function of DEGs in LUAD, as shown in Table 2.


### Kaplan-Meier Survival Analysis of hub Genes
  The relationship between hub genes and prognostic conditions was evaluated with the Kaplan-Meier plotter online analysis tool. CAV1, TEK, SLIT2, FOXF1, HLF, MEIS1, PTPRD, and ADRB2 were found to be associated with favorable overall survival (OS) in patients with LUAD (Figure 5). The probes for hub genes that we used are shown in Table 4. The schema for this study is shown in Figure 6.


### Inhibition of HLF Promotes A549 Cell Proliferation
  To determine the expression of HLF with the lowest log rank P value, qRT-PCR analysis was used to compare the HLF expression between LUAD and adjacent normal tissue. A significantly lower level of HLF mRNA was found in the LUAD (Supplementary Figure 1A). Next, to study the function of HLF in LUAD, HLF siRNA was used to knock down its expression in A549 cells. The qRT-PCR result indicated an acceptable knockdown efficiency (Supplementary Figure 1B). In addition, to explore the impact of HLF on the proliferation of A549 cells, a qRT-PCR assay was performed to determine the expression of Cyclin D1 and Cyclin D3. Compared with the siRNA-NC group, the expression of Cyclin D1/3 was significantly increased (Supplementary Figure 1C).


## Discussion
  LUAD is a malignant tumor that originates from bronchial mucosal glandular epithelium and which accounts for about 33% of all lung carcinomas [14]. Lung cancer may not cause any symptoms, especially in the early stages of the disease. Patients with LUAD may develop a cough and chest symptoms. In the late stage, the tumor can block off an airway and interfere with breathing. Current treatments for LUAD include targeted therapy, radiotherapy, immunotherapy, chemotherapy, and surgery, but there is no criterion standard for the disease. The mechanism of LUAD is still unclear and there is controversy about what causes the disease. DEG analysis based on bioinformatic methods can help us explore the pathogenesis of LUAD and find novel targeted treatments for it.

  CAV1 is an isoform in the caveolin family that participates in some cellular processes, such as cellular signaling and immune responses [15]. In fact, CAV1 has been proven to be involved in some cancers, but there is controversy about the role it plays [16]. It is upregulated in some cancers, such as those of the breast, pancreas, and prostate, but downregulated in ovarian and colorectal cancers [17–20]. In the present study, CAV1 was found to be downregulated in LUAD, and those data combined with the Kaplan-Meier survival analysis results indicate that it can inhibit LUAD. This result is consistent with some previous studies, which have shown that CAV1 can positively regulate lung cancer by promoting cell proliferation and decreasing cell apoptosis [15].

  TEK reportedly may have prognostic potential in head and neck SCCs treated with radiation or chemoradiation [21]. TEK was also proven to be associated with gliomas, other brain tumors, and breast cancer [22,23]. Some preliminary data show that TEK suppresses LUAD cell phenotypes by interacting with miR-19a-3p [24]. Taking those findings together with the results from our study, it can be concluded that TEK plays a positive role in the development of LUAD.

  As reported in some studies, SLIT2 may suppress lung cancer progression [25,26]. The underlying mechanism is unclear. We found that expression of SLIT2 is downregulated in LUAD and survival analysis shows that it is associated with favorable prognosis. Therefore, SLIT2 may have a tumor suppressor role in LUAD.

  The FOXF1 transcription factor regulates E-cadherin expression downstream of the P53 family members, modulating cancer cell migration and invasion [27]. In NSCLC, FOXF1 may inhibit cancer growth by inducing tumor suppressor and G1-phase cell-cycle arrest [28]. In LUAD in our study, downregulation of FOXF1 and positive survival results were observed. Therefore, we concluded that FOXF1 is a prognostic factor for LUAD [29].

  HLF is an alias for EPAS1. Low EPAS1 expression in cancer, including LUAD, has been reported [30]. In NSCLC, EPAS1 can promote peritoneal carcinomatosis by enhancing the mesothelial-mesenchymal transition [31]. In the present study, downregulation of EPAS1 was further confirmed and EPAS1 was associated with favorable prognosis for LUAD, indicating that it may be a promising biomarker and therapeutic target.

  MEIS1 may play a role in limiting the proliferation of NSCLC cells [32]. In fact, MEIS1 may mediate suppression of metastasis in many types of cancer, including LUAD [33]. Low expression of MEIS1 in LUAD was consistently observed in the present study, and its favorable effect on LUAD was verified by survival analysis.

  PTPRD was been proven to be a potential candidate tumor suppressor gene not only in lung cancer but also in some other cancers [34–36]. Deletion of PTPRD and CDKN2A cooperate to accelerate tumorigenesis [37]. Indeed, in LUAD, we found that expression of PTPRD is downregulated and high expression of it led to better survival results.

  The literature regarding the relationship between ADRB2 and LUAD is limited. ADRB2 reportedly plays an essential role in gastric cancer, promoting progression and metastasis [38]. However, a case-control study did not support a major independent role for ADRB2 polymorphisms in LUAD risk [39]. In our study, ADRB2 was downregulated in LUAD, and high expression of it was associated with longer survival time.

  In the present study, CAV1, TEK, SLIT2, FOXF1, HLF, MEIS1, PTPRD, and ADRB2 were found to be associated with favorable OS in patients with LUAD. Moreover, inhibition of HLF was found to promote A549 cell proliferation, indicating that these genes are involved in the pathological development of LUAD and that they can be used as predictors of prognosis in patients.

  There are some limitations of the present study. First, there was no in vitro or in vivo validation. Second, only 3 datasets were used. More data could provide more convincing evidence about our results. Nevertheless, we believe that this bioinformatics-based study provides some useful information for further research on LUAD.


## Conclusions
  In this bioinformatics-based study, CAV1, TEK, SLIT2, HLF, MEIS1, PTPRD, FOXF1, and ADRB2 were identified as hub genes in the DEG interaction network for LUAD. They were involved in pathological development of LUAD and associated with favorable OS. These genes can be used as predictors of prognosis in patients with LUAD. Furthermore, these findings can facilitate further investigation into the mechanism of LUAD.


## Supplementary Data