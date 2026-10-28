# Bioinformatics Analysis of mRNAs and miRNAs for Identifying Potential Biomarkers in Lung Adenosquamous Carcinoma


## Background
  Lung adenosquamous carcinoma (LASC) is a special type of lung cancer. LASC is a malignant tumor with strong aggressiveness and a poor prognosis. Previous studies have revealed that microRNAs (miRNAs) are widely involved in the development of tumors by targeting mRNA. This study is aimed at identifying the key mRNAs and miRNAs of LASC and constructing miRNA-mRNA networks for deeply comprehending the latent molecular mechanisms.


## Methods
  mRNA dataset (GSE51852) and miRNA dataset (GSE51853) were extracted and downloaded from the Gene Expression Omnibus (GEO) database. Differentially expressed genes (DEGs) and differentially expressed miRNAs (DEMs) were picked out by the GEO2R web tool. Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) functional enrichment analyses were conducted in the DAVID database. The protein-protein interaction (PPI) network was performed and analyzed by using the STRING database and Cytoscape software, respectively. TransmiR v2.0 was applied to predict potential transcription factors of miRNAs. The target genes of DEMs were predicted in the miRWalk database.


## Results
  In comparison to normal tissues, a total of 1458 DEGs (511 upregulated and 947 downregulated) and 13 DEMs (5 upregulated and 8 downregulated) were screened out in LASC tissues. The PPI network of the DEGs displayed five key modules and seventeen hub genes. Six target genes of the DEMs were predicted, and five essential miRNA-mRNA regulatory pairs were established. Ensuingly, CENPF, one of the target genes, was also the hub genes of GSE51852, which was obtained from MCODE and cytoHubba and regulated by hsa-miR-205.


## Conclusions
  We constructed the miRNA-mRNA regulatory pairs, which are helpful to study the potential regulatory mechanisms and find out promising diagnosis biomarkers and therapeutic targets for LASC.


## 1. Introduction
  Lung cancer is the main cause of cancer-related death worldwide [1]. Lung adenosquamous carcinoma (LASC) is a rare subtype of non-small-cell lung cancer (NSCLC), accounting for 0.4-4% of all patients [2]. According to the fifth edition of the World Health Organization Classification of Lung Tumors, LASC is defined as a mixed-type tumor, consisting of adenocarcinoma and squamous cell carcinoma, with each component having at least 10% of the tumor cells [3]. At present, patients with LASC have a poor prognosis and limited treatment options, which is a clinical challenge for doctors. Therefore, in-depth study of accurate biomarkers for diagnosis and effective treatment targets is particularly important.

  Noncoding RNAs are genes with no coding ability, accounting for 98% of the human genome and including microRNA (miRNA), long noncoding RNA (lncRNA), and circular RNA(circRNA) [4]. MicroRNAs (miRNAs) are 19-24-nucleotide- (nt-) long noncoding, single-stranded, small RNAs, which bind to target mRNAs to regulate gene expression [5]. It is reported that miRNAs are involved in various physiological processes including cell proliferation, differentiation, apoptosis, tissue invasion and migration, and angiogenesis [6–8]. Li et al. found that miR-202-3p inhibits the proliferation, migration, and invasion of lung adenocarcinoma cells through lowering of the matrix metalloproteinase-1 (MMP-1) [9]. miR-24-3p promotes lung cancer cell migration and proliferation by regulating the sex determining region Y-box 7 (SOX7) [10].

  The miRNA-mRNA network is a novel model for displaying gene expression regulation between coding and noncoding RNAs. The integration and analysis of differentially expressed genes (DEGs) and differentially expressed miRNAs (DEMs) based on microarray data are helpful to dig out diagnostic biomarkers and therapeutic targets. A study reported that a crucial miRNA-mRNA network involved neck squamous cell carcinoma to explore the underlying regulatory mechanisms [11]. Another study revealed that candidate miRNA-mRNA regulatory networks could be used to predict radioresistance in nasopharyngeal carcinoma [12].

  In the present study, we used bioinformatics tools to analyze microarray datasets from the Gene Expression Omnibus (GEO) database for identifying DEGs and DEMs and constructing miRNA–mRNA regulatory networks associated with LASC.


## 2. Materials and Methods

### 2.1. Microarray Datasets
  Gene chip data about LASC was extracted from the Gene Expression Omnibus (GEO, http://www.ncbi.nlm.nih.gov/geo) database [13]. Then, two gene expression datasets (GSE51852 and GSE51853) were collected and downloaded from GEO, with the following keywords: “Lung Adenosquamous Carcinoma” and “Homo sapiens.” The detailed information of each dataset is generalized in Table 1.


### 2.2. Identification of DEGs and DEMs
  DEMs and DEGs were selected by GEO2R which is an interactive web tool that can identify differentially expressed genes across experimental conditions, with the same criteria. Adjusted P value < 0.01 and ∣log FC | >2 acted as the screening threshold for DEGs and DEMs between lung adenosquamous carcinoma and normal tissue.


### 2.3. GO and KEGG Pathway Enrichment Analyses of DEGs
  Gene Ontology (GO, http://www.geneontology.org/) is a widely used bioinformatics tool to perform enrichment analysis on gene sets, which includes a biological process (BP), cellular component (CC), and molecular function (MF). The Kyoto Encyclopedia of Genes and Genomes (KEGG, http://www.genome.jp/kegg/) is a database used to study the enrichment pathways of selected genes aimed at better understanding the functions of genes. DAVID (https://david.ncifcrf.gov/) is a universally used online database that was oftentimes applied to perform GO and KEGG pathway analyses.


### 2.4. Protein-Protein Interaction (PPI) Network and Module Study
  The PPI network of the DEGs was constructed and visualized using the STRING (https://string-db.org) database. The confidence > 0.9 and removal of disconnected nodes were set to identify the crucial PPIs. Then, Cytoscape software (version 3.7.2) was applied to analyze the PPI network. The Molecular Complex Detection (MCODE) plugin was used to find out key gene modules in the PPI network by using the cutoff criteria (MCODE score > 5) with the default parameters (degree cutoff = 2, node score cutoff = 0.2, K − core = 2, and max depth = 100). At the same time, the cytoHubba plugin was utilized to check out the hub genes, which are the top 20 genes in the degree rank. Finally, we pooled the overlapping genes between the MCODE and cytoHubba results to get consistent predictions to identify more specific key genes.


### 2.5. Identification of Potential Transcription Factors of DEMs
  The TransmiR v2.0 database (http://www.cuilab.cn/transmir) is a public database that can identify the enriched transcription factors (TFs) of miRNAs [14]. DEMs were uploaded to TransmiR for analysis, and the TFs that may regulate the DEMs were predicted (overlapping with DEGs).


### 2.6. miRNA Target Gene Prediction
  miRWalk (http://mirwalk.umm.uni-heidelberg.de/) is a comprehensive miRNA target gene database, which contains miRNA target gene information of multiple species [15]. In this study, the target genes of DEMs were predicted in the miRWalk database. The overlapping genes between predicted target genes of DEMs and DEGs by using the jvenn online tool (http://www.bioinformatics.com.cn/static/others/jvenn/example.html) [16]. Then, the miRNA-target gene regulatory network was constructed and visualized in the Cytoscape software.


### 2.7. Construction of miRNA–mRNA Regulatory Network
  The target gene of miRNA is indirectly contributing to understanding the biological functions and enriched pathways of miRNAs. The overlapping genes between predictive targeted genes of DEMs and DEGs served as remarkably differentially expressed target genes. Then, miRNA-mRNA regulatory pairs related to LASC were established by using the Cytoscape software to display the networking between miRNA and mRNA.


## 3. Results

### 3.1. Identification of DEGs and DEMs
  The data of the GEO dataset has been effectively normalized to assure its accuracy. GSE51852 and GSE51853 datasets were gained from GEO and analyzed by the GEO2R web tool. A total of 1458 DEGs (511 upregulated and 947 downregulated) and 13 DEMs (5 upregulated and 8 downregulated) were screened out between LASC tissues and normal tissues. The volcano map is designed to directly display all the genes studied in the data set. Red dots indicate meaningfully upregulated genes, and blue dots indicate meaningfully downregulated genes (Figures 1(a) and 1(b)). The cluster heat map can visually reflect the expression of genetic differences. We plotted a heat map on the basis of the expression levels of DEGs and DEMs in a free online platform (http://www.bioinformatics.com.cn) for data analysis and visualization (Figures 1(c) and 1(d)).


### 3.2. GO and KEGG Pathway Enrichment Analyses of DEGs
  GO and KEGG analyses were accomplished in the DAVID database to have a better understanding of the DEG functions. GO enrichment analysis showed that the 1458 DEGs were mapped to 442 GO terms. With the P value < 0.05 and fold enrichment > 2 being used as the screening criteria, the DEGs were significantly enriched in cell adhesion, inflammatory response, extracellular matrix organization, etc., in the category of biological processes. The cellular component enrichment analysis included proteinaceous extracellular matrix, extracellular matrix, and focal adhesion, while, for molecular functions, the DEGs were enriched in heparin binding, integrin binding, histone binding, metalloendopeptidase activity, and so on (Figures 2(a)–2(c)). The signal cascade of the identified genes can be obtained through the KEGG pathway analysis. The result showed that the 1458 DEGs were mapped to 36 KEGG terms. Then, the screening criteria were the same as those of the GO analysis. Finally, the KEGG pathways of the DEGs were mainly enriched in the p53 signaling pathway, TNF signaling pathway, ECM-receptor interaction, cell adhesion molecules (CAMs), etc. (Figure 2(d)).


### 3.3. PPI Network of DEGs and Hub Gene Confirmation
  The PPI network of 1458 DEGs was constructed and visualized using the STRING database. The disconnected nodes were removed, and the remaining DEGs together constituted a complex multicenter interaction network map, which contained 1366 nodes and 1145edges. From the 1366 nodes, the top 20 DEGs with the highest node degree were selected by using the NetworkAnalyzer tool of the Cytoscape software (Figure 3). The top 10 genes were CDK1, CENPA, CREBBP, BUB1, CCNB2, NDC80, MAPK3, BUB1B, ASPM, and TTK. The key clusters of DEGs were obtained through the MCODE plugin, with 29 key modules and a false degree cutoff = 2. Five significant key modules were dug out, including 75 key genes with the MCODE score ≥ 5 (Figure 4). The cytoHubba plugin was then used to search for hub genes in the PPI network of the DEGs. In total, the top 20 genes ranked by degree were identified as hub genes. At last, we summarized the overlapping genes between the MCODE and cytoHubba results (Figure 5(a)). 17 hub genes belonging to the GSE51852 were screened. In addition, we also used the DAVID online tool to analyze the GO annotations and KEGG pathway analysis of these genes, as shown in Figures 5(b) and 5(c).


### 3.4. Potential TFs of DEMs
  In this study, 13 DEMs were identified in GSE51853, of which 5 were upregulated and 8 downregulated. The current study demonstrated that transcription factors were essential factors to miRNA. The potential TFs of the DEMs were predicted by using the TransmiR v2.0 database. The overlapping genes between TFs and DEGs are shown in Table 2.


### 3.5. miRNA-Target Gene Regulatory Network
  104 target genes of the 13 DEMs were predicted in the miRWalk database. Among them, ZEB2, ROCK2, DCBLD2, and SATB2 were targeted by two miRNAs. Essential miRNA-target genes were predicted based on the expression profiles. There were 6 overlapping and significantly differentially expressed genes between DEGs and the predicted target genes, which explicated the complex correlations between miRNAs and targets (Figure 6(a)). As shown in Figure 6(b), 6 crucial miRNA-mRNA pairs were constructed, having an important effect on LASC. In addition, the target gene CENPF was one of the 17 hub genes of GSE51852 and was regulated by hsa-miR-205. The expression of the miR-205 and CENPF was higher in LASC tissue than in lung normal tissue (Figure 7).


## 4. Discussion
  Lung adenosquamous carcinoma is an extremely rare subtype tumor and more aggressive than adenocarcinoma and squamous cell carcinoma and has a worse prognosis [17]. The main histological subtype of adenocarcinoma may be a freestanding prognostic factor for LASC [18]. Most patients are diagnosed with lymph node metastasis, vascular infiltration, and involvement of the parietal layer of the pleura, so it is usually found at an advanced stage [19]. The pathogenesis of LASC is unclear at the molecular level. Thus, there is a pressing need to find more effective biomarkers for diagnosis and treatment. Microchip technology can be used to study the transcription and epigenetic changes of LASC genes and is an effective method to identify disease markers. In addition, miRNAs affect the occurrence and development of tumors by regulating gene expression [20–22]. Our study uses bioinformatics methods to study LASC DEGs and DEMs and explore the molecular pathological mechanism by constructing the miRNA-target gene regulatory network.

  In the present study, 1458 DEGs were identified from the GSE51852 and performed bioinformatics analysis. KEGG and GO enrichment analyses showed that the remarkable genes were enriched in different signaling pathways, such as “p53 signaling pathway,” “TNF signaling pathway,” “cell adhesion molecules (CAMs),” and “ECM-receptor interaction.” p53 is a tumor suppressor gene that is related to rapid tumor progression and resistance to antitumor treatments [23]. A recent study has shown that p53 may be an effective biomarker and is associated with postoperative recurrence for LASC patients [24]. The abnormal expression of p53 causes the activation of relevant signaling pathways in LASC. Tumor necrosis factor (TNF) is a highly pleiotropic cytokine that plays a key role in promoting or eliminating tumors.

  TNF, interacting with NF-κB, JNK, etc., can promote immune monitoring to destroy tumors or induce chronic inflammation and angiogenesis to result in tumor growth and metastasis [25].

  miRNAs are small, highly conserved, tissue-specific, and noncoding RNAs, which are composed of 20–24 nucleotides. miRNAs mainly regulate gene expression through posttranscriptional regulation of mRNA [26]. In our study, 13 DEMs were identified from the GSE51853 dataset. Previous studies have shown that miRNA expression can be regulated by transcription factors. Hereafter, we predicted the potential transcription factors (TFs) of these 13 DEMs through the TransmiR v2.0 database. The results revealed that ATOH8 and KLF2 are significant TFs. ATOH8, also called Math6/Hath6, is a major helix-loop-helix (bHLH) protein involved in neurological, endocrine, and cardiovascular growth [27]. Some researchers have reported that ATOH8 may be master regulators in lung adenocarcinoma [28], breast cancer [29], hepatocellular carcinoma [30], and colorectal cancer [31] to promote or inhibit tumor progression. KLF2 is a member of the KLF protein family and a transcriptional activator [32]. In comparison to adjacent normal tissues, the KLF2 expression levels were decreased in non-small-cell lung cancer, acting as a tumor suppressor function and a poor prognostic biomarker [33, 34]. Exosomal miR-25-3p promoted colorectal cancer vascular permeability and angiogenesis by targeting KLF2 [35]. miR-106b possesses an important role in cholangiocarcinoma tumor biology by repressing KLF2 [36]. In total, ATOH8 and KLF2 may be related to LASC, which needs further study.

  In this study, we used the miRWalk database to predict the target genes of these 13 DEMs and obtained 104 different target genes. Then, we got 6 overlapping target genes (CCND3, RUNX2, CENPF, SIK2, KIAA1109, NFAT5) between targets and DEGs and regulated by 5 DEMs (hsa-miR-138, hsa-miR-205, hsa-miR-218, hsa-miR-363, hsa-miR-31). We found that CENPF appertained to the 17 hub genes which is regulated by hsa-miR-205. CENPF (Centromere Protein F) is a protein coding gene and is part of the centromere-centromere complex [37]. CENPF expressions have been certified to be related to the prognosis and progression of various cancers, such as bladder, breast, and lung cancers [38–40]. Compared with noncancerous lung tissue, the expression of CENPF mRNA in LASC tissue was increased in GSE51852, which was similar to recent research [41, 42]. According to some researches, hsa-miR-205 is identified as an oncogenic miRNA and related to the progression of many cancers, especially lung squamous cell carcinoma (LUSC). miR-205 had a high diagnostic accuracy rate in discriminating lung squamous cell carcinoma from lung adenocarcinoma (LUAD) and small cell lung carcinoma (SCLC), and target genes of miR-205 were downregulated or upregulated in LUSC [43, 44]. In the LASC, the expression of miR-205 lay between LUAD and LUSC, which is consistent with the research that LASC is a transition state between classic LUAD and LUSC [45]. In addition, hsa-miR-205 is regarded as one of the basic regulators of the epithelial-mesenchymal transition (EMT). The Dai et al. [46] study indicated that hsa-miR-205 reversed EMT and inhibited the growth and invasion of gliomas by targeting HOXD9. The hsa-miR-205-CENPF regulatory pairs participated in the miRNA-gene regulatory network, suggesting that miR-205 may affect the pathogenesis of LASC through targeting CENPF and EMT.

  Our research has some limitations. First, the sample size of each dataset was insufficient, which could not meet the requirements of bioinformatics analysis. Second, all data in our research was extracted from one dataset, which might cause bias. Therefore, more research is needed to verify our results via larger sample sizes. Third, the miRNA-mRNA pairs were only originated from predictions in the public databases. Therefore, we will validate these analysis results in in vivo and in vitro experiments.

  In conclusion, based on the GEO database and bioinformatics analysis, we firstly found that one potential miRNA-mRNA regulatory pair (hsa-miR-205-CENPF) in LASC helps us to understand the molecular mechanism of this tumor, which may be promising biomarkers for the diagnosis and treatment of LASC patients.


## Data Availability
  The data presented in this study are available in the article materials and methods.


## Conflicts of Interest
  The authors declare that they have no conflicts of interest.


## Acknowledgments
  This study was supported by grants from the Natural Science Foundation of Guizhou Province ([2018]5623), Guizhou Provincial Respiratory Critical Disease Clinical Research and Prevention and Treatment Talent Base Project ([2020]8), Science and Technology Fund Project of the Health Commission of Guizhou Province (gzwjkj2020-1-054), Science and Technology Bureau Project of Zunyi City (Zunshi kehe[2019]72), and Master Degree Research Start-Up Fund of Affiliated Hospital of Zunyi Medical University ([2016]31).