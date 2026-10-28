# Weighted Correlation Network Analysis of Cancer Stem Cell-Related
Prognostic Biomarkers in Esophageal Squamous Cell Carcinoma


## Abstract
  Background: The role of cancer stem cells in esophageal squamous cell carcinoma (ESCC) remains unclear. Methods: The mRNA stemness index (mRNAsi) of 179 ESCC patients (GSE53625) was calculated using a machine learning algorithm based on their mRNA expression. Stemness-related genes were identified by weighted correlation network analysis (WGCNA) and LASSO regression, whose associations with mutation status, immune cell infiltrations, and potential compounds were also analyzed. The role of these genes in proliferation and their expressions was assessed in ESCC cell lines and 112 samples from our center. Results: The ESCC samples had significantly higher mRNAsi than the normal tissues. Patients with high mRNAsi exhibited higher worse OS. Seven stemness-related genes were identified by WGCNA and LASSO regression, based on which a risk-predicted score model was constructed. Among them, CST1, CILP, PITX2, F2RL2, and RIOX1 were favorable for OS, which were adverse for DPP4 and ZFHX4 in the GSE53625 dataset. However, RIOX1 was unfavorable for OS in patients from our center. In vitro assays showed that CST1, CILP, PITX2, F2RL2, and RIOX1 were pro-proliferated, which were opposite for DDP4 and ZFHX4. In addition, SMARCA4, NOTCH3, DNAH5, and KALRN were more mutated in the low-score group. The low-score group had significantly more memory B cells, monocytes, activated NK cells, and Tregs and less macrophages M2, resting mast cells, and resting dendritic cells. Conclusions: Seven stemness-related genes are significantly related to the prognosis, gene mutations, and immune cell infiltration of ESCC. Some potential anticancer compounds may be favorable for OS.


## Introduction
  Esophageal squamous cell carcinoma (ESCC) occupied over 90% of all esophageal cancer cases, which exhibited a high incidence in East Asia and the Middle East. Due to exceptional tumor location, most ESCCs were found with dysphagia, which dramatically affects patient life quality. Unfortunately, the 5-year survival rate of esophageal cancer is <20% worldwide. 1  Thus, it is imperative to discover specific biomarkers to predict the prognosis and progress of ESCC.

  Cancer stem cells (CSCs) also remain the capacity for self-renewal and differentiation, which are involved in tumor progress, relapse, and treatment resistance. 2  First identified in breast cancer and leukemia, CSCs are now detected in various malignancies, including lung cancer, brain tumor, and intestinal tumor.2,3

  The mRNA expression based-stemness index (mRNAsi) was first introduced by Malta et al 4  to assess the differentiation of cancer cells. Lian et al 5  reported that a higher mRNAsi was significantly unfavorable for OS in medulloblastoma patients. Weighted correlation network analysis (WGCNA) has been widely used to explore the highly correlated genes and their associations with specific parameters in high-throughput data with the advantages of improved integration and exactitude. 6

  In this research, we calculated the mRNAsi and identified the most relevant key genes with WGCNA and LASSO regression using profiles from the GEO database and TCGA database, based on which a risk-predicted score model was constructed and validated in ESCC patients from our center. Gene mutations and immune cell infiltrations in low- and high-score groups were also analyzed. Potential compounds targeting the score model were searched in the Connectivity Map database.


## Patients and Methods

### Ethics Approval
  The Ethics Committee of Zhongshan Hospital, Fudan University has approved this research (Approval No. B2022-180R). Written informed consent was obtained from all patients.


### Data Collection and Calculation of mRNAsi
  The mRNA-expression profiles and corresponding clinical information of 179 ESCC patients were obtained from the GSE53625 and 98 ESCC patients from the TCGA database.

  The mRNAsi of each sample was calculated using the “TCGAbiolinks” R package.4,7,8 The associations of mRNAsi with clinical information were assessed by the Wilcoxon rank-sum test owing to nonnormal distribution.


### Weighted Correlation Network Analysis and LASSO Regression
  Weighted correlation network analysis was performed to screen coexpression modules and estimate their relevance to mRNAsi and other clinical parameters using the “WGCNA” R package. GO and KEGG pathway enrichment analysis was applied for genes within the most relevant modules to mRNAsi using the “clusterProfiler” R package.

  The LASSO regression was utilized to screen ideal prognosis-related key genes within the most relevant to mRNAsi to mRNAsi by the “glmnet” R package. 9  The 1 − standard error (SE) criteria were applied to select the optimal model parameter λ as previously reported. 10


### Construction and Validation of a Risk-Predicted Score Model
  Univariate Cox regression was utilized to evaluate the prognostic value of key genes, based on which a risk-predicted score model was constructed. The risk score was the sum of the Cox regression coefficient (β) multiplied by the corresponding gene expression. Patients were divided into low- and high-score groups according to the optimal cut-off score calculated using the “survminer” R package. 11

  The accuracy of the risk-score model was validated with 98 ESCC patients from the TCGA database. Immunofluorescence was used to estimate the expressions of the key genes in 112 ESCC samples from our center. Briefly, paraffin-embedded slides are deparaffinized and rehydrated. After antigen repair, the slides went through a block of endogenous peroxidase activity and nonspecific antigens and incubation with primary antibodies: anti-CST1 (Abcam, ab124281), anti-PITX2 (Affinity Biosciences LTD, DF13574), anti-RIOX1 (Abcam, ab194292), anti-CILP (Abcam, ab192881), anti-F2RL2 (Affinity Biosciences Ltd, DF15686), and anti-DPP4 (Affinity Biosciences Ltd, DF12387), anti-ZFHX4 (Affinity Biosciences Ltd, DF10016), horseradish peroxidase-conjugated secondary antibody, and Opal tyramide signal amplification (TSA) Fuorochromes (Opal 2-Color Manual IHC Kit, G1226, Servicebio Co., Ltd) for 10 min at room temperature. After the second run, the slides were stained with DAPI. The imageJ software was used to analyze the fluorescence intensity. 12  The effects of their expressions on prognosis were assessed by Cox regression.


### Cell Culture and siRNA Transfection
  KYSE150 (ESCC cell lines) were cultured with RPMI-1640 medium (KeyGEN BioTECH), supplemented with 10% fetal bovine serum (Every Green) and 100 IU/mL penicillin/streptomycin (Beyotime) in a humidified 5% CO2 atmosphere at 37 °C.

  Two different siRNAs were transfected into ESCC cells to knock down gene expressions with Lipo8000 transfect reagent (Beyotime) and Opti-MEM (Thermo Fisher Scientific) according to the manufacturer's protocol (Table S2).


### RNA Extraction and Quantitative Real-Time Polymerase Chain Reaction
  Total RNA was obtained with RNAiso Plus (Takara Bio, 9108) according to the manufacturer's protocol. RT reagent Kit (Takara Bio, RR047A) was used to synthesize the cDNA template. A quantitative real- time-polymerase chain reaction was performed using TB Green (Takara Biomedical Technology, RR820A) in QuantStudio5 (Thermo Fisher Scientific) according to the manufacturer's protocol. Primer sequences are listed in Table S2.


### Cell Proliferation Assays
  Briefly, 2000 cells/well were inoculated in blank 96-well plates. After incubation for 24, 48, 72, 96, and 120 h, cell proliferation was measured by CCK-8 (Beyotime).


### Characteristics of Mutations and Immune Cell Infiltration
  Various mutations and correlations between different gene mutations were analyzed with the “maftools” R package.13,14 The relative abundance of the 22 immune cell subpopulations was assessed by the CIBERSORT method. 15


### Potential Anticancer Compounds
  The potential activated or inhibited compounds were screened in the Connectivity Map (CMap) database. 16


### Statistical Analysis
  All statistical analyses were performed with SPSS (version 24; IBM). All tests were two-sided and P < .05 was considered significant.


## Results

### Calculation of mRNAsi and Weighted Correlation Network Analysis of Most
Relevant Module
  Based on the mRNA expression, we calculated the mRNAsi of 179 pairs of samples from ESCC patients in the GSE53625 dataset. Obviously, the ESCC samples had significantly higher mRNAsi than the normal tissues (P < .01) (Figure 1A). No significant association of mRNAsi with age, sex, and stage was observed. However, poorly differentiated cases and smokers had a higher mRNAsi (Figure S1A). The OS was also significantly worse in the patients with high mRNAsi (P < .01) (Figure 1B).

  Of the 21 gene modules generated by WGCNA, the pink module was the most relevant to the mRNAsi with a correlation coefficient of −0.73 (P < .01) (Figure 1C). Figure S2A also revealed that genes in the pink module were apparently related to the mRNAsi. GO and KEGG pathway enrichment analysis showed that extracellular matrix constituent and structure organization, PI3K-Akt signaling pathway, Rap1 signaling pathway, Rap1 signaling pathway, and calcium signaling pathway were enriched in the pink module (Figure 1D).


### Construction and Validation of a Risk-Predicted Score Model
  With the LASSO regression, 7 prognosis-related key genes among genes in the pink module were identified, based on which a risk-predicted score model was constructed with their Cox regression coefficient (Figure 2A-C). Risk score = (0.42 × expression level of CST1) + (0.44 × expression level of PITX2) + (0.50 × expression level of F2RL2) + (0.54 × expression level of CILP) + (0.55 × expression level of RIOX1) + (1.64 × expression level of ZFHX4) + (2.03 × expression level of DPP4). No significant association of risk scores with age, smoke, and stage was observed. However, poorly differentiated (P < .01) and male cases (P = .06) showed significantly lower risk scores (Figure S1B). Subsequently, 179 patients were divided into high- and low-score groups according to the optimal cut-off score calculated by the “survminer” R package. The low-score group exhibited a significantly worse OS (P = .04), which was also observed in the 98 ESCC patients from the TCGA database (P = .03) (Figure 2D).

  Besides, the expressions of the 7 key genes were also measured by immunofluorescence in 112 ESCC patients from our center (Table S1). CST1, PITX2, RIOX1, F2RL2, ZFHX4, and DPP4 were up-regulated in the ESCC samples. Conversely, CILP was down-regulated in the ESCC samples (Figure 3). In addition, high expressions of CST1 (P = .048), PITX2 (P = .035), CILP (P = .035), and F2RL2 (P = .037) were favorable for survival, which were adverse for DPP4 (P = .022), RIOX1 (P = .032), and ZFHX4 (P = .017) (Figure 4A).

  Through down-regulating the CST1, CILP, PITX2, F2RL2, and RIOX1 expressions with siRNAs, we observed that the proliferation of KYSE150 cells was inhibited, which was the opposite for DDP4 and ZFHX4 (Figure S2B).


### Genetic Variations and Immune Cell Infiltration
  The P53, NOTCH, and RKT-RAS pathways were the most common mutated pathways in ESCC (Figure 4B). Interestingly, COL6A5 was likely to comutate with TTN, ZNF750, and MUC17 (P < .05, respectively). Cooccurrence of APOB and CSMD3, HYDIN, and MUC4 was also observed (P < .05, respectively) (Figure 4C).

  Missense mutation and SNP were the most frequent in both low- and high-score groups. More specifically, TP53, TTN, CSMD3, FLG, EYS, and PIK3CA were less mutated in the low-score group. However, SMARCA4, NOTCH3, DNAH5, and KALRN were more mutated in the low-score group (Figure 4D).

  The CIBERSORT algorithm showed that the low-score group had significantly more memory B cells, monocytes, activated NK cells, and Tregs and less macrophages M2, resting mast cells, and resting dendritic cells (P < .05, respectively) (Figure 5A).


### Screening of Potential Targeted Compounds
  Three hundred top differentially expressed genes between low- and high-score groups were queried in the CMap database. Finally, 44 compounds were identified, which were related to 36 mechanisms of action (MoA). Among them, PDGFR receptor inhibitor, VEGFR inhibitor, KIT inhibitor, potassium channel activator, and FLT3 inhibitor were shared frequently (Figure 5B).


## Discussion
  Despite great progress in examination techniques and therapy, most ESCC patients reach an advanced stage, and lose the chance for radical surgery. Moreover, quite a few patients have recurrent or metastatic ESCC. A comprehensive understanding of the molecular heterogeneity of ESCC could improve personalized therapies.

  It has been reported that basal cells are the progenitor cells of the esophageal squamous epithelium.17,18 Stimulated by interleukin-1β (IL-1β)/interleukin-6 (IL-6), the basal cells can be transformed, accounting for ESCC. 19  Many research studies have proven the existence of CSCs in ESCC.20–23 Besides, many cell surface markers of CSCs in ESCC have been discovered including CD271, CD44, CD90, CD133, and CXCR4, which were unfavorable for prognosis and able to predict and evaluate therapy response.24–32 We also observed that low differentiated grades meant poor OS for ESCC patients.

  Secretory cystatin SN encoding by CST1 belongs to the type 2 cystatin superfamily, which specifically inhibits the proteolytic activity of cysteine proteases. 33  Choi et al 34  reported that CST1 was up-regulated in gastric cancer and contributed to cancer cell proliferation, which was also observed in colorectal cancer. 35  Similar to their findings, ESCC exhibited upregulation of CST1 and facilitation of cell proliferation in our study. PITX2 belongs to the bicoid/paired-like homeobox gene family with vital roles in embryonic development. 36  It has been reported that the expression of PITX2 was increased in ovarian cancer and colorectal cancer.37,38 It promoted the invasion of ovarian cancer. However, Hirose et al 38  revealed its inhibition of cell growth and invasion in colorectal cancer. We exhibited its overexpression and facilitation of cell proliferation in ESCC, which need further research to solve the contradiction. F2RL2, also known as PAR3, is a polarity protein, which regulates apical/basal polarity and spindle orientation and is essential for stem cell maintenance. 39  Zhou et al 40  reported that loss of Par3 promoted prostatic tumorigenesis. Nevertheless, Dadras et al 41  showed that Par3 participated in homeostatic redox control and limited invasiveness of glioblastoma.

  CILP is also a secreted protein, which is mainly from articular cartilage chondrocytes. 42  Its role in malignancy is rarely reported. We found that it was down-regulated in ESCC. Interestingly, its high expression in ESCC was related to worse OS and promotion of ESCC cells, which need larger sample size research studies to claim its effect. RIOX1 is one of the JMJD histone demethylases and regulates target genes in embryonic stem cells.43,44 Sinha et al 45  demonstrated that RIOX1 was highly expressed in prostate cancer and promoted cancer cell survival. It has been reported that ZFHX4 was overexpressed in ESCC and facilitated cancer migration and invasion, 46  which was similar to our results. DPP4 is a type II transmembrane protein, whose soluble form can be easily detected in serum or plasma. There are research studies that it was down-regulated in melanoma, nonsmall cell lung cancer, and renal cell carcinoma,47–49 up-regulated in thyroid cancer, ovarian cancer, and ESCC.50–52 Goscinski et al 53  revealed that high expression of DPP4 correlated with better survival in ESCC patients, which was also observed in our study.

  Many research studies have reported that NOTCH3 was differentially expressed between malignant and corresponding normal tissues, which was an important prognostic factor. 54  Liu et al 55  found that NOTCH3 was up-regulated in ovarian epithelial cancer than in normal tissues and in an ovarian benign tumor, which meant a shorter OS. However, Zhou et al 56  reported that NOTCH3 was down-regulated in small cell lung cancer. In addition, NOTCH3 mutations were closely associated with Cerebral Autosomal Dominant Arteriopathy with Subcortical Infarcts and Leukoencephalopathy (CADASIL) and Pulmonary Hypertension. 57  Sawada et al 58  demonstrated that NOTCH3 was frequently mutated (7.6%) in ESCC. In our study, NOTCH3 mutation was related to the poor OS of ESCC patients. Mangalaparthi et al 59  reported that DNAH5 was frequently mutated (21%) in ESCC, which meant poor survival and was consistent with our study. KARLN was mutated in a variety of malignancies, including melanoma, glioblastoma multiforme, lung cancer, and colorectal cancer. 60  Grønhøj et al 61  reported that KALRN was frequently mutated (28%) in human papillomavirus positive (HPV+) oropharyngeal squamous cell carcinomas.

  Dasatinib is an oral tyrosine kinase inhibitor and has been widely used in CML and Philadelphia chromosome-positive acute lymphoblastic leukemia. 62  Additionally, several clinical trials of dasatinib as monotherapy or combined therapy with other drugs have exhibited promising antitumor effects in solid tumors, including breast cancer, nonsmall cell lung cancer, melanoma, and colorectal cancer. 63  Sorafenib is an oral multikinase inhibitor and was first approved for the treatment of renal cell cancer. Xiang et al 64  demonstrated that stemness contributed to sorafenib resistance. Several clinical trials with dasatinib in nonsmall cell lung cancer and prostate cancer also showed an anticancer effect. 65  The association of these compounds with ESCC stemness and prognosis requires further study.

  Inevitably, there are some limitations to this research. First, this study is retrospective. Second, because of the limited sample size, the power calculation was not done for its estimation. Third, the effect of key genes on ESCC was only explored with one cell line. More experiments need to be done to validate it, including proliferation, colony formation, migration, and animal experiments.


## Conclusion
  In conclusion, high mRNAsi signified a poor OS in ESCC patients. Seven stemness-related genes were identified to be significantly associated with OS by WGCNA and LASSO regression, which were validated in 112 ESCC patients from our center and in vitro experiments. Two groups with different expression patterns exhibited distinct mutation characteristics and immune cell infiltration. The potential mechanisms between stemness and tumor immunity and drug sensitivity still need further studies.


## Supplemental Material

## Acknowledgments
  We would like to thank International Science Editing Co. for the language editing service.