# Identification and verification of feature biomarkers associated with CD14
+ monocytes in type 1 diabetes


## Aims/Introduction
  Monocytes contribute to the immune dysregulation of pancreatic islets in Type 1 diabetes mellitus (T1D). This study aims to identify the feature genes of CD14+ monocytes in T1D, which might offer a new perspective on immune dysregulation and potential therapeutic targets in T1D.


## Materials and Methods
  Two CD14+ monocyte‐related datasets were integrated for DEGs and WGCNA analysis. LASSO and SVM‐RFE machine learning algorithms were applied for further screening of feature genes. Subsequent nomogram model and single‐gene GSEA analysis were performed. The experiments in vitro and in vivo were conducted for the verification and functional investigation of the feature gene.


## Results
  Eleven up‐regulated and five down‐regulated DEGs in T1D samples were identified in the integrated dataset. WGCNA analysis obtained 13 gene co‐expression modules in which the yellow module had a significantly positive correlation with the T1D phenotype, and the magenta module had a negative correlation. Thirteen intersecting genes between DEGs and WGCNA gene modules were subjected to LASSO and SVM‐RFE machine learning, and the feature gene ID1 was eventually screened out and verified. In terms of the T1D diagnostic model, the calibration curve and ROC curve displayed high predictive accuracy and effectiveness. Single‐gene GSEA analysis revealed that high ID1 was associated with the IL1/IL1R/JNK signaling pathway gene set. The increased ID1 was verified in high glucose‐treated THP‐1 cells and T1D subjects, and the deficiency of ID1 impaired the expression of the inflammatory cytokine IL6.


## Conclusions
  We had identified ID1 as the feature gene of CD14+ monocytes, which exhibited the ability for diagnosis and prediction of T1D.


## INTRODUCTION
  Type 1 diabetes (T1D), also known as insulin‐dependent diabetes, is caused by the destruction of pancreatic beta cells 1 ,  2 . T1D mostly occurs in childhood and adolescence, with an increasing incidence in recent years. Epidemiological studies suggest that T1D affects more than 200 000 youth in the United States 3  and more than half a million children aged 0–14 years worldwide 4 . T1D commonly accompanies a series of chronic complications, including diabetic nephropathy, diabetic neuropathy, and cerebral macrovascular disease 5 ,  6 . In view of the increasing prevalence worldwide, T1D has gradually become a great threat to adolescent health.

  T1D is a multifactorial disease involving genetic and environmental factors 7 ,  8 . Multiple genes contribute to the susceptibility to T1D, among which human leukocyte antigen HLA is considered a vital susceptibility gene. HLA alleles, particularly HLA‐DQB1 and HLA‐DRB1, account for up to 50% of the genetic heritability of T1D 9 . Meanwhile, environmental factors, such as exposure to toxic chemicals, are associated with the development of T1D. As well, the infection of rubella or hepatitis virus is reported to increase the risk of T1D 10 .

  Besides, T1D is considered an autoimmune disease, characterized by the inflammation of pancreatic islets 11 ,  12 . Islet inflammation involves the infiltration of autoreactive T cells and a local inflammatory response, leading to the destruction of insulin‐producing β cells 13 . Inflammatory cells, mainly including lymphocytes, plasmocytes, and monocytes, play an essential role in triggering the inflammatory response in pancreatic islets 14 . Several studies have focused their attention on peripheral blood mononuclear cells (PBMCs) in T1D patients. A bioinformatics study displays the dynamic molecular networks of IL‐17, nuclear factor‐κB and tumor necrosis factor signaling pathways in PBMCs in T1D individuals 15 ,  16 . CD14+ monocytes are a crucial component of PBMCs, which are closely associated with the pathogenesis of type 1 diabetes 17 . CD14+ monocytes could highly express MHC class II and costimulatory molecules to present pancreatic autoantigens to T cells, activating autoreactive T cells and driving β‐cell destruction 18 . Additionally, CD14+ monocytes could infiltrate pancreatic islets and other tissues under hyperglycemic conditions and differentiate into M1‐type pro‐inflammatory macrophages, further amplifying local inflammation and leading to the damage of pancreatic islets and other tissues 19 . Clinical studies showed that T1D patients exhibit an increased proportion of CD14+ monocytes in peripheral blood, along with a more pronounced pro‐inflammatory phenotype 20 . Despite these findings regarding CD14+ monocytes in T1D, there is little research reporting the molecular mechanism of CD14+ monocytes in T1D.

  In this paper, two GEO datasets were integrated to explore the DEGs in CD14+ monocytes of T1D. We employed WGCNA analysis and two machine learning algorithms to screen the feature genes and construct a risk prediction model for diagnosing T1D. Collectively, these observations would strengthen the potential role of CD14+ monocytes in the development of T1D and provide potential drug targets and clinical diagnostic markers.


## MATERIAL AND METHODS

### Data source and data processing
  The datasets GSE154609, GSE164338, and GSE33440 were obtained from the NCBI Gene Expression Omnibus (GEO) database (https://www.ncbi.nlm.nih.gov/geo/; Table 1). Microarray analysis of the three datasets was performed on CD14+ monocytes isolated from peripheral blood mononuclear cells obtained from patients with type 1 diabetes and healthy nondiabetic control subjects. Among them, the GSE154609 dataset contained 12 control samples and 12 T1D samples; the GSE164338 dataset contained 5 control samples and 5 T1D samples; and the GSE33440 dataset contained 6 control samples and 16 T1D samples.

  To combine the expression data of the GSE154609 and GSE164338 datasets, we performed the de‐batching effect using the R package ‘Combat’ in the ‘sva’. The de‐batching effect was assessed by the boxplot and the Principal component analysis (PCA). After the de‐batching, the integrated dataset included 17 healthy control samples and 17 T1D samples. The dataset GSE33440 was set as the validated dataset. A workflow of our study was displayed in Figure 1.


### Identification of differentially expressed genes (DEGs) and functional enrichment
  The differential gene analysis between the T1D and control group was performed by using the R package ‘limma’ in the integrated dataset. Due to the fewer differentially expressed genes, we set the thresholds for differential genes at the |log2FoldChange (FC)| > 0.5 and adj.P.Val < 0.05. The DEGs were visualized using Volcano plots and heat maps which were generated by the R packages ‘ggplot2’ and ‘heat maps’ respectively. Gene enrichment analysis including the GO functional and KEGG pathway analysis was performed using the R package ‘clusterProfiler’ package, with the threshold for enrichment significance as adjusted P‐value <0.05.


### WGCNA analysis
  WGCNA is a weighted correlation network analysis to construct a gene co‐expression network 21 . We performed the WGCNA method using the R package ‘WGCNA’ to analyze the genes from 17 T1D patients and 17 control samples in the integrated dataset. The soft threshold power was calculated based on the criteria of approximating scale‐free topology of the network. Here, we selected a power of β = 4 to construct a scale‐free network. Through the use of dynamic tree cutting, different gene modules were acquired, with the criterion of the minimum module size set to 30 genes and the minimum height for merging modules at 0.25. Additionally, the correlation between gene modules and the T1D phenotype was further analyzed.


### Screening biomarkers by machine learning models
  The intersecting genes between DEGs and WGCNA module genes were obtained using the online analysis site (https://www.bioinformatics.com.cn/static/others/jvenn).

  Two machine learning algorithms, least absolute shrinkage and selection operator (LASSO) and support vector machine–recursive feature elimination (SVM‐RFE) models, were constructed for further screening of biomarkers. The intersecting genes were regarded as independent variables, and the occurrence of T1D was served as a dependent variable. Ultimately, the intersecting genes between LASSO and SVM‐RFE analysis were identified as potential feature biomarkers.


### Nomogram model construction and validation
  The screening feature genes were applied to construct a nomogram model using the R package ‘RMS’, which assessed the influence degree of different predictors on the clinical diagnosis of T1D. Risk score was calculated according to the coefcients in this diagnostic model. The calibration curve was product to evaluate the accuracy and precision of the predictive model. DCA (Decision Curve Analysis) curve and CIC (Clinical Impact Curve) curve were to evaluate clinical predictive models in practical clinical decision making. Receiver Operating Characteristic (ROC) curve was performed using the R package ‘pROC’, for evaluating the sensitivity and specificity of the diagnostic model.


### PPI network and gene correlation analysis
  The screening feature genes were applied to construct a Protein–Protein interaction (PPI) network by the gene mania database (http://genemania.org). Gene correlation analysis was generated using the R package ‘Performance Analytics’, P < 0.05 was set as the threshold for gene significant correlation.


### Single‐gene GSEA
  Single‐gene GSEA was conducted using the R package ‘clusterProfiler’ and “GseaVis.” Briefly, the samples in integrated dataset were divided into “High” group and “Low” group according to the single‐gene expression median. All genes were analyzed for differential expression between the two groups, and sorted in order of the logFC values. Gene set of “C2” were selected for GSEA analysis to detect the KEGG pathway enrichment. The criterion of significant enriched gene sets was set as |NES| > 1, NOM P‐value <0.05, FDR q‐value <0.25.


### Gene knockdown experimentin vitro
  Human mononuclear macrophage cell lines THP‐1, purchased from the Chinese Academy of Sciences Cell Bank, were used for the validation and functional investigation of ID1. THP‐1 cells were cultured in RPMI‐1640 media supplemented with 10% fetal bovine serum. For high glucose treatment, THP‐1 cells were cultured with 25 mM glucose for 24 h. To knock down the expression of ID1, the specific siRNAs of ID1 were designed and transfected into THP‐1 cells. After 24 h, the transfected cells were collected for further experiments.


### Quantitative real‐time PCR (qPCR)
  Treated cells were collected in TRIzol reagent (Invitrogen), and total RNA was extracted according to the manufacturer's protocol. The cDNA was generated using the First Strand cDNA Synthesis Kit (TaKaRa). Real‐time PCR analysis was performed with SsoFastTM EvaGreen R Supermix (Invitrogen) by the Bio‐Rad iQ5 Real‐Time PCR System. Beta‐actin was used as an internal control. The relative difference was expressed as the fold change calculated by the 2−ΔΔCT method. A primer list for qPCR was provided in Table S1.


### Peripheral blood mononuclear cells (PBMCs) and CD14
+ monocyte isolation
  PBMCs were isolated from the blood samples of 9 type 1 diabetes patients and 9 control subjects, respectively, with the approval of the ethical committee of the Central Hospital of Wuhan. Briefly, the blood samples were diluted with phosphate buffer and dropwise added into Ficoll–Hypaque solution. After centrifuging, PBMCs were isolated and subjected to qPCR to detect the expression of ID1. CD14+ monocytes were isolated by incubating PBMCs with anti‐human CD14 magnetic beads for cell sorting. The purified CD14+ cells were cultured in vitro in medium supplemented with 20 ng/mL M‐CSF. After 7 days, CD14+ monocytes were treated with high glucose to detect the expression of ID1.


### Statistical analysis
  All data processing and analysis were performed with R (version 4.3.2) and R Bioconductor packages. Statistical significance was evaluated with the Mann‐Whitney test for two‐group comparisons. Gene correlation coefficients were estimated via Pearson correlation analysis. Differences were considered statistically significant at P < 0.05.


## RESULTS

### Gene expression of CD14
+ monocytes in type 1 diabetes
  To explore the gene expression feature of CD14+ monocytes in type 1 diabetes, GSE154609 and GSE164338 datasets were integrated, and the batch effect was removed. The boxplot and PCA analysis showed a robust de‐batching effect (Figure 2a,b). After de‐batching, an integrated dataset was generated, which included 17 healthy control samples and 17 T1D samples. Gene differential expression analysis was performed in the integrated dataset, and 102 DEGs were finally screened when screened with P < 0.05 (Figure S1). Among them, 70 genes were up‐regulated in T1D samples, and 32 genes were down‐regulated, which were mainly enriched in the response to cAMP, chemokine‐mediated signaling pathway, response to chemokine, and cellular response to chemokine (Figure S1).

  To ensure the robustness of the identified DEGs, we had used FDR (False Discovery Rate) to screen for differentially expressed genes and ultimately identified 16 significant genes, including 11 up‐regulated and 5 down‐regulated genes (Figure 2c,d).


### WGCNA co‐expression gene network construction
  To identify the co‐expression network in the CD14+ monocytes of T1D patients, the integrated dataset including 17 healthy control samples and 17 T1D samples was applied to WGCNA analysis. The soft‐thresholding power β = 4 was selected to construct a scale‐free network (Figure 3a). A topological overlap matrix (TOM), representing gene connectivity, was generated by the adjacency matrix. Gene cluster analysis acquired 13 gene co‐expression module eigengenes (Figure 3b). Subsequent correlation analysis was carried out to assess the most relevant gene modules with the T1D phenotype. The results showed that the yellow module had a significant positive correlation with the T1D phenotype, whereas the magenta module had a negative correlation (Figure 3c). The correlations between module membership and gene significance in the yellow and magenta modules were exhibited in Figure 3d,e. Additionally, we also performed the correlation analysis on modules unrelated to T1D. Among them, the red and tan modules, as well as the brown and green modules, showed significant correlations (Figure S2A). We further conducted functional enrichment analysis on the gene sets from these two module pairs. The results revealed that the genes in the brown and green modules were mainly enriched in immunoglobulin production, the production of molecular mediators of the immune response, immune response‐regulating cell surface receptor signaling pathway, immune response‐activating cell surface receptor signaling pathway, antigen receptor‐mediated signaling pathway, and lymphocyte mediated immunity (Figure S2B). The genes in the red and tan modules were mainly enriched in the Cajal body (Figure S2C).


### The feature gene screening by two machine learning algorithms
  To screen the feature genes in the CD14+ monocytes of T1D patients, we obtained the intersecting genes between 16 DEGs and 589 yellow and magenta module genes. Eventually, 13 intersecting genes were screened out (Figure 4a).

  For further feature gene screening, 13 intersecting genes were applied to two machine learning algorithms. After adjusting for multicollinearity effects, 8 feature genes were ultimately subjected to machine learning algorithms. The intersecting genes were regarded as independent variables, and the occurrence of T1D was served as a dependent variable. LASSO algorithms identified 5 feature genes out of 8 genes (Figure 4b,c), and SVM‐RFE algorithms identified 7 genes (Figure 4d). By the intersection between the two machine learning algorithms, 4 most important genes were eventually screened for feature genes (Figure 4e), including ID1 (the inhibitor of DNA binding 1), MIR500B (microRNA 500b), LOC100506844, and LOC100288846.


### Gene enrichment analysis
  To ensure the credibility of the hub genes, the dataset GSE33440 was used for verifying the differential expressions of the above five genes. Because of the different sequencing platforms in these datasets, MIR500B, LOC100506844, and LOC100288846 were not detected in GSE33440. Consistently, the expression of ID1 in the integrated data and GSE33440 were significantly elevated (Figure 5a,b), suggesting the importance of ID1.

  Further investigation on the potential function of ID1 was performed. Protein–protein interaction network of ID1 was constructed and shown (Figure 5c). Additionally, ID1 highly‐related genes were extracted based on gene correlation analysis and analyzed for GO enrichment (Figure 5d). As shown in the results, ID1 was mostly involved in “integrated stress response signaling,” “cellular response to calcium ion,” and “cellular response to interleukin−1” (Figure 5d), with the related genes including JUN, CCL3, CCL3L3, and IL1B (Figure 5d).

  Besides, all samples in the integrated dataset were divided into “high‐expression” and “low‐expression” groups according to feature genes' median and applied to single‐gene GSEA analysis. “C2” gene sets representing KEGG pathways were selected in GSEA analysis. As shown in Figure 5, the gene sets of “KEGG_MEDICUS_REFERENCE_IL1_IL1R_JNK_SIGNALING_PATHWAY” and “KEGG_MEDICUS_REFERENCE_TRANSLATION_INITIATION” were activated in the ID1 high‐expression group (Figure 5e,f), but the gene sets of “KEGG_MEDICUS_REFERENCE_TCR_PLCG_ITPR_SIGNALING_PATHWAY” were repressed (Figure 5e,f).


### Gene correlation analysis
  Considering the results of gene enrichment, we speculated that ID1 was associated with inflammation‐related genes, such as CCL3, CCL3L3, and IL1B. Among these genes, CCL3 and CCL3L3 were significantly elevated in the integrated data, and IL1B had a slight increasing trend (Figure 6a). The correlations between ID1 and these inflammatory genes were assessed by using Pearson correlation coefficients (Figure 6b). The results showed that these genes had significant correlation with each other (Figure 6b); the pairwise correlation was shown in Figure 6c–e.


### Construction and validation of the nomogram model
  Based on the feature gene, a nomogram model was subsequently constructed for the T1D risk diagnosis (Figure 7a). The calibration curve revealed the high predictive accuracy of the risk model (Figure 7b). DCA curve and CIC curve showed the robust effect of clinical predictive models in practical clinical decision making (Figure 7c,d). Meanwhile, the ROC curve manifested that the predictive model had considerable diagnostic performance, with the AUC value of 0.924 (Figure 7e). For internal validation, the ROC curves in GSE154609 and GSE164338 respectively showed the good sensitivity and specificity of ID1, with the AUC values of 0.938 and 0.72 (Figure S3). Consistently, the ROC curve of ID1 in the external validation dataset GSE33440 also displayed the robust predictive efficacy (Figure 7f).


### Validation of the expression of ID1 in vitro and in vivo
  To validate the expression of ID1in T1D, we introduced the in vitro cell model in which human monocyte cell lines were treated with high glucose to mimic the hyperglycemia in T1D. The results showed that high glucose treatment could increase the expression level of ID1in THP‐1 cells (Figure 8a). Additionally, the PBMCs from 9 T1D and 9 healthy subjects were isolated and detected for ID1 expression. We found that ID1 was significantly enhanced in T1D patients compared with the control group (Figure 8b). To further validate our findings, we isolated CD14+ monocytes from PBMCs and subjected them to high glucose stimulation. The results demonstrated that high glucose could induce ID1 expression in CD14+ monocytes (Figure 8c), indicating the potential role of ID1 in T1D.


### ID1 regulated the expression of the inflammatory cytokine IL6 in THP‐1 cells
  To determine whether ID1 was involved in the inflammatory reaction in T1D, we knocked down ID1 through transfecting the specific siRNAs. The significantly decreased ID1 was shown in ID1 siRNA‐transfected cells in Figure 9a, indicating a robust knockdown efficiency. Furthermore, the deficiency of ID1 could impair the expression of the inflammatory cytokine IL6 induced by high glucose (Figure 9b), suggesting the important role of ID1 in regulating the hyperglycemia‐induced inflammatory response. To elucidate the molecular mechanism of ID1 regulating the inflammatory response in T1D, we further detected the inflammation‐related signaling pathways. The results demonstrated that high glucose stimulation activated the expression of p‐ERK (Figure 9c). However, the knockdown of ID1 significantly suppressed the p‐ERK level (Figure 9c), suggesting that ID1 might regulate the inflammatory response by modulating the ERK signaling pathways.


## DISCUSSION
  T1D is a chronic autoimmune disease, characterized by T‐cell‐mediated destruction of pancreatic β cells 10 . The pathogenesis of T1D is related to immune system over‐activation caused by genetic factors and environmental factors. Monocytes infiltrate into the pancreatic β cells and differentiate to macrophages, which polarize to the M1 inflammatory phenotype and serve to present antigens and perform immune surveillance 22 . However, few studies have been reported to involve monocytes/macrophages in T1D. Here, we focused on the gene expressions of CD14+ monocytes isolated from PBMCs of T1D. By merging two GEO datasets, we acquired an integrated dataset that contained 17 CD14+ monocyte samples from healthy controls and 17 samples from T1D subjects.

  For analyzing biomarker genes in CD14+ monocytes of T1D, gene differential expression analysis was performed in the integrated dataset. However, a few genes were screened out when the thresholds for differential genes were set as |log2FoldChange (FC)| > 0.5 and adj.P.Val < 0.5, suggesting that the gene changes in CD14+ monocytes of T1D were slight; more attention should be focused on the slightly changed genes which might serve as co‐expression regulatory networks. In the present WGCNA analysis, we produced 13 gene modules in which the yellow and magenta modules had significant positive correlations with T1D phenotype. By intersecting the genes between DEGs and WGCNA gene modules, 13 hub genes were screened eventually, which might play a significant role in T1D pathogenesis. In the period of bioinformatic big data, multiple machine learning algorithms are developed for the discovery of feature biomarker genes 23 ,  24 . Here, we introduced LASSO and SVM‐RFE machine learning algorithms to screen the feature genes in CD14+ monocytes. Eventually, ID1 was screened out and verified, suggesting the potential vital role of ID1 in the development of T1D.

  ID1 is the inhibitor of DNA binding, which has no DNA binding activity and can inhibit the DNA binding and transcriptional activation ability of basic HLH proteins by forming heterodimers 25 . ID1 participates in cell growth, senescence, and differentiation, and is reported to be a potential biomarker of multiple cancers 25 ,  26 . High expression of ID1 in monocytes is strongly associated with phenotypic and functional MDSC markers in advanced melanoma 27 . However, few studies have linked ID1 to diabetes. A meta‐analysis of PBMC transcription profiles discovered that ID1 was differentially and significantly expressed in type 1, type 2, and gestational diabetes 28 , indicating the potential role of ID1 in the development of T1D. Consistent with these observations, we identified ID1 as a critical feature gene of CD14+ monocyte in T1D. The experiments in cell lines and in T1D subjects verified the increase of ID1 in T1D. Based on the feature gene, a nomogram diagnostic model of T1D was established and validated. The calibration curve and ROC curve indicated the diagnostic model had high predictive accuracy and efficacy, suggesting that ID1 might be a critical feature gene of monocyte for T1D diagnosis.

  A possible mechanism of ID1 involved in T1D was the inflammatory response. The gene enrichment analysis displayed that ID1 was highly associated with the cellular response to IL‐1, in which the disturbance of the signaling pathway and overproduction of pro‐inflammatory cytokines could mediate autoinflammatory diseases 29 ,  30 . The genes in the IL‐1 signaling pathway, including CCL3, CCL3L3, and IL1B, were significantly linked to ID1 expression. Gene correlation analysis showed the significant relationship between ID1 and the expressions of these genes, suggesting that ID1 might be involved in the inflammatory response in T1D. Previous studies had linked ID1 to the inflammatory reaction. In tubular epithelial cells, ID1 overexpression enhanced the phosphorylations of IκBα and p65 NF‐κB, promoting the NF‐κB signaling pathway 31 . Mice with ID1 deficiency developed significantly reduced renal infiltration of T cells and macrophages 31 . Another study also found that ID1 deficiency in vivo could ameliorate airway inflammation in an animal model of asthma, shown by the decreased CCL11, CCL24, and Muc5ac expressions and inflammatory cell infiltration 32 . ID1 also participated in the inflammatory regulation of immune cells. The overexpression of ID1 induced the expression of IL‐9 in Th9 cells 33 . Here, we found ID1 was associated with the inflammatory response of monocytes triggered by hyperglycemia. The deficiency of ID1 could significantly impair the high glucose‐induced IL6, suggesting the important role of ID1 in the inflammatory disorder in T1D. The phosphorylation of ERK (extracellular signal‐regulated kinase) is a key molecule in the MAPK (mitogen‐activated protein kinase) signaling pathway, which plays a critical role in inflammatory responses by regulating the expression of inflammation‐related genes and cellular functions. In this study, we found that ID1 modulated the inflammatory response via the ERK signaling pathway in the mononuclear macrophage cell line. Knockdown of ID1 could suppress the high glucose‐induced phosphorylations of ERK. These observations strengthened the evidence of ID1 regulating the inflammatory response in T1D.

  However, this study has several limitations. First, larger independent validation cohorts including diverse populations across different regions, ages, and disease stages are necessary to confirm the biomarker's sensitivity and specificity. Second, the molecular mechanisms underlying ID1's role in T1D require further investigation, along with the development and validation of animal disease models. Finally, translating ID1 from basic research to clinical applications demands more standardized protocols, including the development of assay kits and clinical application scenarios.

  Collectively, we integrated two datasets of CD14+ monocyte in T1D to screen feature genes by machine learning algorithms. We eventually identified ID1 as the feature gene and constructed a robust diagnostic prediction model for T1D risk. Despite more clinical samples and experiments still being necessary for the validation of the diagnostic model, our findings provide a potential drug target and clinical diagnostic marker of T1D.


## DISCLOSURE
  The authors declare no conflicts of interest.

  Approval of the research protocol: This study was approved by the ethics committee of The Central Hospital of Wuhan, and the study protocol conforms to the provisions of the Declaration of Helsinki.

  Informed consent: The patients/participants provided their written informed consent to participate in this study.

  Registry and the registration no. of the study/trial: N/A.

  Animal studies: N/A.


## Supporting information

## ACKNOWLEDGMENTS
  The study was supported by grants from the National Natural Science Foundation of China (82200922, 81500634), the Health Commission Foundation of Hubei Province in China (WJ2019H359), and the Wuhan Municipal Health Commission Foundation (WX19Q12).