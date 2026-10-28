# RNA Binding Protein-Based Model for Prognostic Prediction of
Colorectal Cancer


## Background:
  Colorectal cancer (CRC) is a kind of gastrointestinal tumor with serious high morbidity and mortality. Several reports have implicated the disorder of RNA-binding proteins (RBPs) in plenty of tumors, associating it to tumorigenesis and disease progression. The study is intended to construct novel prognostic biomarkers associated with CRC patients.


## Methods:
  Data of gene expression was acquired from the TCGA database, prognosis-related genes were selected. Besides, we analyzed GO and KEGG pathways. Univariate and multivariate Cox analyses were performed to generate a prognostic-related gene signature, which was evaluated by the Kaplan-Meier (K-M) and the Receiver Operating Characteristic (ROC) curve. The independent prognostic factor was established by survival analysis. GSE38832 dataset was used to validate the signature. Finally, expression of 8 genes was further confirmed by qRT-PCR in SW480 and SW620 cell lines.


## Results:
  We obtained 224 differentially expressed RBPS in total, of which 78 were downregulated and 146 were upregulated. Univariate COX analysis was conducted in the TCGA cohort to select 13 RBPs with P < 0.005, stepwise multivariate COX regression analysis was used to construct an 8—RBP signature (TERT, PPARGC1A, BRCA1, CELF4, TDRD7, LUZP4, PNLDC1, ZC3H12C). Based on the model, systematic analysis illustrated that a high risk score was obviously connected to a poor prognosis. The prognostic value of the risk score was validated in GSE38832 dataset, indicating that the risk model was accurate and effective. The prognostic signature-based risk score was identified as an independent prognostic indicator for CRC. The expression results of qRT-PCR were consistent with the results of differential expression analysis.


## Conclusions:
  The eight-RBP signature can predict the survival of CRC patients and potentially act as CRC prognostic biomarker.


## Introduction
  Colorectal cancer (CRC) is the leading cause of cancer mortality and morbidity. Individuals with colorectal cancer generally have a survival rate of fewer than 5 years because of early metastasis. Even though the rapid development of treatments such as radiotherapy, surgery, targeted therapies and chemotherapy, the poor prognosis and high recurrence rate remain a concern. 1

  RNA binding proteins function in conjunction with several different RNA types, involving tRNAs, mRNAs, rRNAs, miRNAs, ncRNAs, snoRNAs and snRNAs. They either directly interact with RNA or act as a constituent of a ribonucleoprotein complex indirectly associated with RNA. Regulating the epithelial homeostasis, injury response and malignant transformation of intestinal epithelial cells by RNA binding protein (RBPS) is an emerging research hotspot. 2  At present, there are over 1500 experimentally validated RBP-coding genes, accounted for a large proportion of all protein-coding genes. 3  RBP is essential for regulating many basic cellular processes, including RNA splicing, modification, degradation, stability, localization, modification, translation, and transport. RBPs can bind a particular target RNA to form ribonucleoprotein (RNP) complexes and regulating gene expression after transcription. 4  RBP is crucial in post-transcriptional modulation that subsequently participates in several pathways, including apoptosis, differentiation, angiogenesis, proliferation and migration. 5  Recent evidence suggests that RBPs participate in the pathogenesis of cardiovascular disease as key regulators, such as HUR, SRSF1, MUR, and Quaking. 6,7

  Recent evidence about RBPs and colorectal cancer suggests about 30% of colorectal cancer patients over-express Lin28b. 8,9  Human colorectal cancers highly express IMP1, 10  which is linked to lymph node metastasis, poor prognosis, TNM stage, and tumor size. 11  Overexpression of MSI can activate mTORC1 complex with inhibition of PTEN to transform intestinal epithelial cells and form tumors. 12,13  Moreover, there is high HUR protein expression in colon cancer cell cytoplasm and nucleus 14  and is underexpressed in healthy colon cells. 15  By up-regulating the expression of zinc finger E-box binding homeobox 1 (ZEB1) mRNA, forkhead box K2 protein (FOXK2) endorses CRC cells migration. 16  In conclusion, RBP might play a crucial role in the regulation of cancer. Nevertheless, most roles of RBP have not been studied. A comprehensive analysis of RBPs will contribute to our understanding of their role in tumors.

  Here, we obtained the RNA-SEQ data and clinicopathological data from the TCGA database to identify prognosis-related RBPs. Survival-related RBPs were screened by univariate and multivariate COX regression, and their potential function and clinical significance were systematically explored. The study was designed and conducted in strict conformed to the Transparent Reporting of a Multivariable Prediction Model for Individual Prognosis or Diagnosis statement and the Reporting Recommendations for Tumor Marker Prognostic Studies. 17,18  The findings of the present study might be possibly beneficial in the development of prognosis biomarkers. The established signature could be regarded as a novel independent prognostic factor that has a pivotal role in predicting the prognostic of CRC patients.


## Materials and Methods

### Data Source and Preprocessing
  The source of gene expression profile and relevant clinical data were obtain from the Cancer Genome Atlas (TCGA) dataset. To ensure high-quality analyses, patients with missing or incomplete data or survival time less than 14 days were excluded. Limma package was used to analyze all the original information and genes that had an average count value < 1 were excluded, Wilcox test was utilized to test samples. Genes were identified for follow-up analyses which logFC > 0.5 and FDR < 0.05. “pheatmap” R package was used to visualize the various RBPs expression patterns.


### Kyoto Encyclopedia of Genes and Genomes (KEGG) and Gene Oncology (GO)
Analyses
  To determine the function of differently expressed RBPs, GO and KEGG analyses were completed. The org.Hs.eg.db (version 3.7.0) and clusterProfiler (version 3.10.1) 19  were used to carry out all the KEGG pathway and GO analyses.


### PPI Network Construction and Module Selection
  STRING website (http://string-db.org) was utilized for analyzing the protein-protein interaction (PPI) among the differently expressed RBPs. Cytoscape 3.7.0 software was used in network construction and visualization. After that, key modules with node counts > 5 and scores > 7 were chosen via MCODE (Molecular Complex Detection) plug-in in PPI network. P-values < 0.05 were treated as statistically significant.


### Assembly and Verification of the 8-RBP Signature
  The evaluation of key modules survival-associated genes was completed via Univariate Cox regression. Based on the aforementioned primary selected survival-related genes, the TCGA cohort was subjected to multivariate Cox for optimal model determination. A risk score for every patient was computed as the sum of each gene’s score as follows:

  β  refers to the coefficient value; Exp serves as the level of expressed genes. The CRC patients were grouped into low-risk and high-risk based on median risk score. Next, the difference in OS among the subgroups was determined by Kaplan-Meier (KM) and log-rank methods through the “survival” R package. Moreover, model predictive power was evaluated by calculating the AUC of 1-year, 3-year, and 5-year time-dependent ROC curve using “survivalROC” package. 20  Afterward, The GSE38832 dataset was used to further validate the prognostic value of the risk signature.


### Determination of the Independent Prognostic Capacity of the Multi-Gene
Signature
  The Univariate and multivariate Cox regressions were utilized to identify whether the risk score and the respective clinicopathological properties were independent prognostic aspects. P < 0.05 being considered meaningfully.


### Development of the Nomogram
  A nomogram was used to predict CRC prognosis. The nomogram was established by “rms” R package and included all feature genes that had a significant association with OS. After that, we plot Calibration to assess the difference in actual versus nomogram predicted OS.


### Cell Culture and qRT-PCR
  Human CRC cell lines with high metastatic potential (SW620) and low metastatic potential (SW480) were obtained from an American-type culture collection (Manassas, VA, USA). DMEM medium with 10% FBS (Invitrogen) in a humidified incubator at 37 °C and 5% CO2. Total RNA from cell lines was extracted by TRIzol reagent. cDNA was synthesized using cDNA Synthesis Kits (Toyobo, FSQ-301). qRT-PCR was carried out on the iQ5 Real-Time PCR Detection System (Bio-Rad, Hercules, CA, USA). Primer sequences were listed in Table 1. U6 was used as the internal reference. The qRT-PCR relative quantitative method was used to analyze the experimental results. Statistical analyses were performed with GraphPad Prism 8.0.1 software. The expression levels of 8 genes were analyzed by unpaired t-test, and P < 0.05 indicated that the difference was statistically significant.


## Results

### The RBPs Differential Expression in CRC
  Herein, a comprehensive investigation on significant functions and prognostic features of RBPs was undertaken. The study procedure was represented in Figure 1. Based on Wilcox test, we identified 469 and 41 tumor and normal colon tissue samples, respectively. Regarding RBPs, 78 were considerably upregulated, whereas 146 were downregulated (Figure 2).


### Differently Expressed RBPs GO and KEGG Pathway Enrichment
  To annotate mechanisms and function of screened RBPs, differently expressed RBPs were sorted into 2 sub-sets (the downregulated and upregulated groups) and then subjected to GO and KEGG pathway analyses. The outcomes demonstrated that the genes in the downregulated group were markedly enriched in the biological process (BP) and correlated with regulation of cellular amide metabolic process, regulation of translation, RNA splicing (Figure 3A). The upregulated genes were notably enhanced in terms of ncRNA production, nucleic acid phosphodiester bond hydrolysis, and ribosome biogenesis (Figure 3C). Regarding the analysis of cellular component (CC), there was abundance of downregulated RBPs in the cytoplasmic ribonucleoprotein granule, endolysosome membrane, and ribonucleoprotein granule (Figure 3A). However, elevated RBPs were predominant in the cytoplasmic ribonucleoprotein granule, nucleolar part, and the ribonucleoprotein granule (Figure 3C). The molecular function (MF) revealed downregulated RBPs were high in the catalytic activity, acting on RNA, mRNA 3′−UTR binding, endonuclease activity (Figure 3A). In contrast, the elevated RBPs were mostly high in catalytic activity, acting on RNA, nuclease activity, ribonuclease activity (Figure 3C).

  Overall, the KEGG pathways exhibited 6 effects from downregulated differently expressed RBPs (Figure 3B). These included enrichment in the Hepatitis C, TGF-beta signaling pathway, Progesterone−mediated oocyte maturation, Oocyte meiosis. The elevated differently expressed RBPs were associated with mRNA surveillance pathway, RNA transport, Ribosome biogenesis in eukaryotes (Figure 3D).


### Protein-Protein Interaction (PPI) System Assembly and the Key Modules
  The mutual interaction among the differently expressed RBPs in CRC was investigated thoroughly via the PPI linkages of the chosen genes. The linkages were constructed from the String database, using Cytoscape software to form the PPI network (Figure 4A). The co-expression network was performed to find the possible key modules via the MODE tool (Figure 4B). Module 1 contained 24 nodes and 254 edges (Figure 4C), and module 2 involved 8 nodes and 23 edges (Figure 4D). Module 3 included 5 nodes and 10 edges (Figure 4E). According to the GO and pathway evaluations, RBPs in the key module 1 were primarily enriched in rRNA processing, ribosome biogenesis, and rRNA metabolism. On the other hand, the module 2 RBPs were linked to RNA splicing, mRNA 3′-UTR AU-rich region binding, and mRNA 3′-UTR binding. Module 3 was highly enhanced in defensive reaction to virus, response to virus, and cellular response to exogenous dsRNA (Table 2).


### The Selection of Survival-Related Genes
  Overall, there were 13 survival-related RBPs confirmed from the TCGA cohort via univariate Cox regressions (Figure 5A). Whereafter, Multiple stepwise Cox regression analysis was utilized to test these candidate RBPs. 8 feature RBPs (BRCA1, TERT, TDRD7, PPARGC1A, LUZP4, CELF4, ZC3H12C, and PNLDC1) were discovered (Figure 5B, Table 3). Figure 5C shows the expression of these 8 RBPs among the tumor and normal samples.


### Construct the Predictive Model in the TCGA Cohort
  The predictive model was constructed with the 8 hub RBPs. Here, LUZP4, TERT, PNLDC1 and CELF4 served as high-risk RBPs (HR > 1). On the other hand, the remaining 4 (BRCA1, TDRD7, PPARGC1A and ZC3H12C) were confirmed to be low-risk RBPs (HR < 1). The formula below was applied in computing each patient’s risk score:

  In terms of the median risk score, CRC patients were separated into 2 subsets: the high and low-risk group. Furthermore, to comprehend possible impact on OS of the patient from risk score, Kaplan-Meier method was used to analyze the high and low-risk groups. The analysis revealed that the OS in low-risk was higher than in the high-risk group (Figure 6A). Furthermore, we analyzed ROC based on 1, 3, and 5 years to evaluate the specificity and sensitivity of prognostic signature (Figure 6B). The corresponding AUCs values for 1 year, 3 years and 5 years survival were 0.685, 0.687 and 0.708. The results suggested that the signature has high prognostic accuracy. The distributions of the risk scores, OS and OS status were shown in Figure 6C-E. From the graph, we can see that CRC mortality rises highly as the risk score increases. Besides, the expression levels of 8 RBPs were visualized in heatmaps. ZC3H12C, BRCA1, TDRD7 and PPARGC1A had a higher expression in the low-risk group than in the high-risk group, while TERT, CELF4, LUZP4 and PNLDC1 was highly expressed in the high-risk group.


### Validation of the Signature in the GSE38832 Dataset
  The GSE38832 GEO dataset was used to further validate the prognostic value of the risk signature. The outcomes from KM analysis in the GEO dataset (Figure 7A) showed survival of the low-risk patients was higher than the high-risk ones. Additionally, according to ROC values (Figure 7B), the corresponding values of AUC in the GEO dataset were 0.670,0.622 and 0.677 for 1 year, 3 years and 5 years survival. This indicated a good specificity and sensitivity of the prognostic model. The TCGA cohort exhibited equal risk score, survival period distribution and patients’ state (Figure 7C-E). Altogether, these outcomes provide important insights into the eight-RBP signatures, which have a high selectivity of high-risk CRC patients with severe prognoses. The result was consistent with the TCGA results, indicating that the risk model was accurate and effective.

  SW480 and SW620 have been shown to exhibit several phenotypic differences including metastatic potential. 21,22  Highly metastatic SW620 cell lines could be considered high-risk patients, while poorly metastatic SW480 cell lines act as low-risk patients. The expression levels of 8 genes as presented in Figure 8. Expression levels of genes are consistent with our results except for TERT.


### The Signature-Based Risk Score Acted as Independent Prognostic CRC
Parameter
  The univariate and multivariate Cox regression analyses were confirmed in the TCGA cohort to determine if the eight-RBP risk signature were independent prognostic factors. The results obtained from the univariate Cox model suggested that the risk score obtained from the signature was correlated to OS worsening (HR = 1.024, P < 0.001, 95% CI [1.013-1.035]) (Figure 9A). In the meantime, stage (HR = 2.597, P < 0.001, 95% CI [1.992-3.386]) was certified to be highly related to OS (Figure 9A). Afterward, the entire variables were analyzed via multivariate Cox regression. Further statistical tests revealed that the signature from the risk score maintained a reduced OS risk factor (HR = 1.021, P < 0.001, 95% CI [1.010-1.032]) (Figure 9B). In summary, the results indicate that a risk scored derived from signature could be regarded as an independent prognostic parameter in individuals with CRC.


### Generate a Nomogram
  Next, a nomogram incorporating the signatures was built to predict probable OS in 1 year, 3 years, and 5 years (Figure 9C). The calibration plot showed good agreement between nomogram prediction and actual observations. (Figure 9D-E). Together these results provide important insights into the risk score, which perfectly matches the projections and experimental outcomes.


## Discussion
  Colorectal cancer exhibits high malignancy and is highly associated with liver and lung metastasis, which have a strong impact on the survival prognosis. 23  Hence, discovering a highly sensitive and specific prognostic biomarker is important. Prior studies have noted the importance of RNA binding proteins, which is important for tumorigenicity and progression. 24 -26  However, very few RBPs have been deeply investigated, and some of them may be associated with genesis and development of carcinoma. 27

  Prior studies have noted that post-transcriptional regulation is important in RNA, especially in genetic expressions. Some reports have confirmed that RBPs are key regulators of post-transcription processes such as differentiation, apoptosis, migration, angiogenesis as well as cell proliferation. HuR protein is one of the hot spots now, which belongs to ELAV family of RBPs. HuR can identify and bind to target genes, thus stabilizes the target genes, suppresses the mRNA degradation, and regulates multifarious processes such as proliferation, tumor growth, transcription and translation, differentiation, apoptosis, angiogenesis and protein transport. 28  The insulin-like growth factor-2 mRNA binding proteins (IGF2BPs or IMPs) are preserved RBPs subsets. IMP1 plays a key role in cell proliferation and growth by combining and shielding several mRNAs. 29  It has previously been observed that over 80% of CRC overexpress IMP1, 10  a regulator of cell cycle migration and progression. 30  IMP1 is also linked to lymph node metastasis and invasion. 11,31,32  Additionally, protein synthesis occurs in ribonucleoprotein granule. The mutation of it affects translation and plays an important regulatory role in carcinogenesis. 33  The whole-genome sequence analysis of cancer cell confirmed ribonucleoprotein regulates gene mutation regulations in colorectal carcinomas, endometrial cancer, chronic lymphocytic leukemia (CLL), T-cell acute high-grade gliomas, and lymphoblastic leukemia (T-ALL) cancer cells. 34  -37  In brief, RBPs affect the development of several diseases by regulating transcription. Our results are consistent with previous studies. The enrichment analysis in this study confirms that RBPs dysregulation was highly connected with control of translation, such as RNA splicing, catalytic activity, ribonucleoprotein granule, cytoplasmic ribonucleoprotein granule, mRNA 3′−UTR binding and acting on RNA. The KEGG pathway results reflect that the abnormal expressed RBPs might take part in the mediation of carcinoma progression by controlling mRNA surveillance pathway, TGF−beta signaling pathway and RNA transport. All these results showed that most of the dysregulation RBPs link with RNA modification, and the processing and modification of RNA are connected with tumorigenesis.

  The current study selected the feature RBPs using univariate Cox and multiple Cox regression analysis. Cumulatively, 8 genes related to the survival in CRC patient was confirmed. This included TERT, BRCA1, TDRD7, LUZP4, PPARGC1A, CELF4, PNLDC1 and ZC3H12C. Among the RBPs genes, a small number of them are associated with colorectal cancer. The BRCA1 is mainly linked with hereditary breast cancer and meta-analysis confirmed that BRCA1 mutation carriers increase the risk of colorectal cancer. 38  TERT is involved in the early stages of colorectal cancer development, initially affecting the tumor’s stromal microenvironment by inducing COX-2 expression. 39  CUG binding protein 4 (CUBP4) or CELF4 has multiple functions, and the main function is related processes like splicing and translation. Previous research has shown that reduces CELF2 expression may be related to tumor promotion and development by regulating the transcription process. 40  PPARGC1A is a tumor inhibitor in ovarian and colorectal carcinomas, and it can also act as a negative prognostic marker for CRC. 41,42  Several RBPs are associated with other tumors, the relationship between most RBPs and CRC is still not clear. LUZP as a regulatory protein, mutation and Excessive expression of LUZP result in tumorigenesis. Solid tumors like pancreatic, breast and cervical carcinomas have exhibited abnormal expression of LUZP. 43 -45  ZC3H12A, a novel RNA-binding protein (RBP) called MCPIP1 or Regnase-1, links with immune homeostasis and post-transcriptional regulation. 46,47  Prior studies in lung carcinoma found that ZC3H12A activates macrophages. 48  PNLDC1, a PARN-like 3′-to-5′ exonuclease located at the membrane of the mitochondria in a mouse, is related to a mature piRNA development. 49  The TUDOR domain-containing proteins (TDRDs) play major roles in identifying methyl-lysine/arginine residue. The dysregulation of TDRD could initiate tumorigenesis. 50

  In this study, to predict the survival of CRC patients, a risk score formula based on the 8-gene signature was made. In CRC patients, high expression of LUZP4, TERT, PNLDC1 and CELF4 related to a more unfavorable clinical outcome, whereas high expression of TDRD7, BRCA1, ZC3H12C and PPARGC1A were connected with a good prognosis. One of the important findings in this study was that the 8-RBPs risk signature was constructed and demonstrated a robust prognostic prediction in CRC. The ROC analysis of the model demonstrated a higher precision for both the TCGA cohort (1-year AUC = 0.685; 3-year AUC = 0.687; 5-year AUC = 0.708) and GEO dataset (1-year AUC = 0.670; 3-year AUC = 0.622; 5-year AUC = 0.677). The results of cellular experience provide strong support for our finding. Expression levels of genes are consistent with ours except for TERT. This might be due to the differing behavior of cells in vitro or even to technical reasons. It should be validated in future large sample clinical studies. In conclusion, the above results suggest that the model has a significant prognostic value for CRC.

  In the present study, a novel prognosis predictive model of RBPs signature was unveiled, and the predictive capability of the model was effectively assessed. This signature could serve as promising biomarkers for supervising the development of colorectal cancer. The present study outlines important CRC pathogenesis and provides information on therapy and colorectal cancer prognosis.


## Acknowledgments
  The results of this study are derived from the TCGA and GEO databases. We are grateful to the authors whose data is used in this study.