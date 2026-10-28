# Characterization of PANoptosis-based markers for ischemic stroke and their appealing implications in improving prognosis and in glioma patients


## Objective
  Pyroptosis, apoptosis and necroptosis separately participate in the pathogenesis of ischemic stroke, but the implication of PANoptosis in this disease is still unexplored. This study conducted a comprehensive investigation on PANoptosis in ischemic stroke and glioma.


## Methods
  Four transcriptomic datasets of ischemic stroke: GSE16561, GSE58294, GSE22255, and GSE37587 were gathered. Consensus clustering analysis was implemented based upon PANoptosis genes. WGCNA was utilized for PANoptosis subtyping-related genes. Multiple well-established machine learning models were also built for feature gene selection. Moreover, survival and receiver operating characteristic (ROC) analysis was performed to evaluated the prognostic value of the feature genes in the glioma.


## Results
  Fifteen PANoptosis genes were aberrantly expressed in peripheral blood of ischemic stroke than that of controls. Based upon them, ischemic stroke was classified as two PANoptosis molecular subtypes, with heterogeneous molecular mechanisms, and immune cell infiltration. The PANoptosis molecular subtyping-related module genes were determined, and key genes were subsequently via distinct machine learning approaches. Among them, the SVM model had the lowest |residual|, and the AUC of 1 in diagnosing ischemic stroke. The feature genes in the SVM model were regarded as the key genes (comprising TMEM55A, CCPG1, CYP1B1, PJA2, MTPN, SCYL2, BAZ2B, and DPYD). Based upon them, the nomogram was established, which could accurately predict ischemic stroke risk. All of them were in relation to ischemic stroke-related signaling pathways, and immune cell infiltration. Transcription factors were predicted, which transcriptionally modulated them. Additionally, drugs that potentially targeted them were determined. Moreover, the expression and prognostic value of genes in glioma were evaluated in the The Human Protein Atlas (HPA) and The Cancer Genome Atlas database (TCGA). All genes showed a significant prognostic value except PJA2. The diagnostic and prognostic ROC analysis result indicated that BAZ2B can served as potential diagnostic and prognostic marker in glioma.


## Conclusion
  Altogether, this is the first study to characterize PANoptosis-based molecular subtypes, and diagnostic model for ischemic stroke, providing a promising avenue for patient risk prediction through a non-invasive method. Moreover, the BAZ2B genes could serve as predictive biomarkers in glioma, providing essential implications for patient prognosis.


## Supplementary Information
  The online version contains supplementary material available at 10.1007/s12672-025-03782-8.


## Introduction
  Stroke ranks among the major causes of death and disability globally [1]. In 2019, there were 7.6 million newly diagnosed cases of ischemic stroke, occupying ~ 62% of all stroke cases, and 3.3 million cases died from the disease [2]. Ischemic stroke can result in permanent brain injury when circulation is delayed [3]. Common causes of ischemic stroke can be subclassified as large vessel sclerosis, small vessel lesions, cardiogenic embolism, other causes (vascular or blood diseases), and unknown etiology [4]. Diagnosis of ischemic stroke primarily depends upon neuroimaging technology. Owing to the lack of early diagnostic indicators, currently, therapeutic regimens against acute ischemic stroke only cover intravenous thrombolysis and mechanical thrombectomy, both of which target reperfusion of clotted blood vessels [5–7]. Because of strict inclusion criteria, such treatments are suitable for only a small percentage of patients, and lots of patients have persistent neurological dysfunction though recanalization is successfully achieved [8]. Hence, novel biomarkers, and additional therapeutic regimens are required for combating ischemic stroke.

  PANoptosis is an inflammatory programmed cell death, which can be activated by components that are contemporaneously engaged from pyroptosis, apoptosis, and/or necroptosis [9]. PANoptosis shares basic features of each of the three programmed cell death forms but cannot be explained by any of them alone [10]. Numerous studies have proposed the roles of pyroptosis [11, 12], apoptosis [13, 14], and necroptosis [15, 16] separately in the pathogenesis of ischemic stroke. Nevertheless, the implication of PANoptosis as a whole in ischemic stroke is still indistinct. Hence, comprehending the mechanisms underlying PANoptosis can open an additional avenue for proposing a novel molecular classification, and a diagnostic model for ischemic stroke. This study presented a comprehensive analysis of the expression features of PANoptosis genes in peripheral blood and proposed two PANoptosis molecular subtypes in ischemic stroke patients. Each PANoptosis molecular subtype owned the unique molecular mechanisms, and immune cell infiltration features. In addition, we established a PANoptosis-based model for diagnosing ischemic stroke risk through well-established machine learning methods. Associations of the key genes in the diagnostic model with signaling pathways and immune cells were evaluated. Also, transcriptional factors and drugs that transcriptionally modulated and targeted the key genes were probed, respectively.


## Materials and methods

### Acquiring and preprocessing data
  The current study gathered four peripheral blood transcriptomic datasets of ischemic stroke: GSE16561 [17], GSE58294 [18], GSE22255 [19], and GSE37587 [20] from the Gene Expression Omnibus (https://www.ncbi.nlm.nih.gov/geo/). The GSE16561 dataset comprised microarray expression profiling on peripheral whole blood from 39 acute ischemic stroke cases and 24 healthy controls on the GPL6883 platform. The GSE58294 dataset was composed of microarray expression profiling on blood from 69 cardioembolic stroke cases and 23 healthy controls on the GPL570 platform. The GSE22255 dataset included microarray expression profiles on peripheral blood from 20 ischemic stroke cases and 20 control subjects on the GPL570 platform. The GSE37587 dataset contained microarray expression data on peripheral whole blood from 68 ischemic stroke cases on the GPL6883 platform. The GSE16561, and GSE58294 datasets were merged as the training set, and batch effects were corrected utilizing sva package (Supplementary Fig. 1A, B) [21]. Afterwards, the GSE22255, and GSE37587 datasets were integrated as the validation set (Supplementary Fig. 1C, D). PANoptosis genes were acquired from the previously published literature [22].


### Analysis of differentially expressed PANoptosis genes
  The expression of genes between stroke and controls was compared utilizing limma package [23]. Differentially expressed genes (DEGs) with adjusted p < 0.05 were selected. Intersection analysis on DEGs and PANoptosis genes was conducted. The genomic location of differentially expressed PANoptosis genes was mapped by executing Rcircos package [24].


### Functional enrichment analysis
  Enrichment of functions and signaling pathways was analyzed utilizing clusterProfiler package [25]. The analyses comprised Gene Ontology (GO) and the Kyoto Encyclopedia of Genes and Genomes (KEGG).


### Molecular subtyping analysis
  ConsensusClusterPlus package was adopted for consensus clustering analysis on ischemic stroke samples utilizing differentially expressed PANoptosis genes [26]. Consensus matrix was adopted for determining the optimal number of clusters.


### Gene set variation analysis (GSVA)
  Molecular processes and pathways were examined through GSVA method [27] based upon the gene sets of “c5.go.symbols” and “c2.cp.kegg.symbols” from the Molecular Signatures Database [28]. The GSVA enrichment score was estimated for each sample.


### Estimation of immune cell infiltration
  Through executing single sample gene set enrichment analysis (ssGSEA), the infiltration of 29 immune cell types was estimated in accordance with the expression profiling of markers genes.


### Weighted gene co-expression network analysis (WGCNA)
  WGCNA package was adopted for constructing a co-expression network [29]. The first 5000 genes with variance were determined for subsequent analysis. The soft-threshold β value was chosen via sft$powerEstimate function. The weighted adjacency matrix was converted to a topological overlap matrix (TOM) for estimating the network connectivity. Through hierarchical clustering method, clustering tree structure of the TOM was established. Genes with similar expression patterns were merged into one module based upon weighted correlation coefficients. Pearson correlation analysis on modules with molecular subtypes was executed, a model with the highest |correlation coefficient| was regarded as the PANoptosis subtype-related module. The module partitions and eigengenes were outputted. Gene significance across modules was computed, followed by correlation of module membership with gene significance on the module.


### Machine learning for selecting key genes
  Intersection analysis on the DEGs and the PANoptosis subtype-related module genes was executed. Subsequently, key genes were chosen via four machine learning approaches: generalized linear model (GLM), extreme gradient boosting (XGB), random forest (RF), and support vector machine (SVM) utilizing caret, xgboost, randomForest, and kernlab packages. DALEX package was utilized for explaining the residual distribution and feature importance of the machine learning models. Receiver operating characteristic (ROC) curves were plotted for appraising the diagnostic efficacy of the models and the chosen key genes via pROC package.


### Nomogram construction
  Nomogram was drawn for scoring each key gene by use of rms package. The probability of one patient developing ischemic stroke was eventually evaluated based upon the combined score. Calibration and decision curves were conducted for reflecting the accuracy of the nomogram.


### GSEA
  Potential molecular processes and pathways underlying the specified gene were assessed via GSEA based upon the “c2.cp.kegg.symbols” gene set from the Molecular Signatures Database [30].


### Transcription factor prediction
  Transcription factors of the key genes were screened in accordance with the miRNet 2.0 online database (https://www.mirnet.ca/) [31]. A transcription factor-gene interaction network was established via Cytoscape tool [32].


### Drug-gene interaction analysis
  Based upon the Drug-Gene Interaction Database (DGIdb, www.dgidb.org) [33], drugs that potentially target the key genes were selected, and a drug-gene interaction network was built via Cytoscape tool.


### Immunofluorescence staining
  The protein expression level and distribution of subcellular in the glioma cell U-215MG of the eight genes was analyzed in the HPA database (https://www.proteinatlas.org/).


### Statistical analysis
  All the analyses were executed utilizing R software (version 4.1.0). Continuous variables were compared utilizing Student’s t-test or Wilcoxon test. Pearson’s test was adopted for correlation analysis. Statistical significance was set at p < 0.05. Furthermore, survival analysis was performed using the “survival” R package, and diagnostic potential value was estimated using the “pROC” R package.


## Results

### Differentially expressed PANoptosis genes in peripheral blood of ischemic stroke
  The present study firstly determined 1446 DEGs in peripheral blood of ischemic stroke compared with that of controls (Fig. 1A; Supplementary Table 1). Among PANoptosis genes, fifteen presented the aberrant expression in ischemic stroke, composed of TNFSF10, PPP3R1, DFFB, CASP1, APAF1, CHUK, YWHAG, LY96, CYCS, CD14, HMGB2, MLKL, TFDP1, BNIP3L, and FASLG (Fig. 1B). Fig. 1C illustrates the genomic position of the differentially expressed PANoptosis genes. Among them, TNFSF10, PPP3R1, CASP1, APAF1, CHUK, YWHAG, LY96, CD14, HMGB2, MLKL, TFDP1, and BNIP3L displayed the notable up-regulation in peripheral blood of ischemic stroke, with the notable down-regulation of DFFB, CYCS, and FASLG (Fig. 1D, E). Thus, molecular processes and pathways underlying the differentially expressed PANoptosis genes were probed. They were observed to participate in regulating cysteine-type endopeptidase activity involved in apoptotic process (Fig. 1F) as well as PANoptosis pathways (apoptosis, necroptosis, etc.) (Fig. 1G). In addition, they presented the remarkable interactions at the transcriptional levels (Fig. 1H).

  Fig. 1Differentially expressed PANoptosis genes in peripheral blood of ischemic stroke. (A) Volcano diagram illustrating the DEGs in peripheral blood of ischemic stroke (IS) versus that of control subjects. (B) Venn chart of the shared DEGs and PANoptosis genes. (C) Circle map depicting the genomic position of the differentially expressed PANoptosis genes. (D) Heatmap of the transcriptional values of the differentially expressed PANoptosis genes in peripheral blood from ischemic stroke and controls. (E) Box plots of the differential expression of these genes in peripheral blood of ischemic stroke in comparison to that of controls. (F, G) GO and KEGG pathway enrichment results on the differentially expressed PANoptosis genes. (H) Heatmap illustrating the interactions between them. *p < 0.05; **p < 0.01; ***p < 0.001


### Classification of ischemic stroke into two PANoptosis molecule subtypes
  Based upon the peripheral blood expression of the differentially expressed PANoptosis genes, ischemic stroke samples were clearly clustered into two clusters via consensus clustering approach, termed as C1, and C2, respectively (Fig. 2A). For verifying the accuracy of this classification, PCA was executed in accordance with the transcription profiling of the differentially expressed PANoptosis genes. It was proven the clear separation between the C1 and C2 subtypes (Fig. 2B). The C2 subtype presented the higher expression of TNFSF10, PPP3R1, CASP1, APAF1, CHUK, YWHAG, LY96, CD14, HMGB2, MLKL, TFDP1, and BNIP3L as well as the lower expression of DFFB, CYCS, and FASLG in comparison to the C1 subtype (Fig. 2C, D).

  Fig. 2Classification of ischemic stroke into two PANoptosis molecule subtypes, and analysis their relevant molecular mechanisms and immune cell infiltration. (A) Consensus matrix when k = 2 in accordance with the peripheral blood expression of the differentially expressed PANoptosis genes. (B) PCA plots proving the distinction of the two subtypes at the transcriptional levels. (C) Heatmap of the expression of the differentially expressed PANoptosis genes in peripheral blood from the two subtypes. (D) Box plots illustrating the differential expression of these genes in the two subtypes. (E, F) Differential GO and KEGG terms between the C1 and C2 subtypes. (G) Heatmap illustrating the abundance of immune cell types in peripheral blood from ischemic stroke (IS) and control subjects. (H) Comparison of the infiltration levels of immune cells between ischemic stroke and control subjects. (I) Heatmap of the crosstalk between diverse immune cell populations. (J, K) The differential infiltration of diverse immune cell types in the two subtypes. *p < 0.05; **p < 0.01; ***p < 0.001


### PANoptosis molecule subtypes with distinct molecular mechanisms and immune cell infiltration
  Next, the heterogeneity in molecular functions and signaling pathways was probed in the two PANoptosis molecule subtypes. It was found that negative regulation of cell death was down-regulated in the C2 subtype versus the C1 subtype (Fig. 2E). In addition, immunity-related signaling pathways, e.g., primary immunodeficiency, allograft rejection, and graft versus host disease displayed the up-regulation in the C2 subtype compared with the C1 subtype (Fig. 2F). The infiltration of diverse immune cell populations was estimated in peripheral blood of ischemic stroke and controls. The alterations in most immune cell populations were investigated in ischemic stroke, such as the higher infiltration of activated dendritic cells, and natural killer T cells (Fig. 2G, H). The immune cell populations were extensively interacted (Fig. 2I). The heterogeneous immune cell infiltration was found in the two PANoptosis molecule subtypes, with the higher abundance of most immune cell populations in the C2 subtype (Fig. 2J, K).


### Identification of PANoptosis molecule subtyping-related genes
  WGCNA was adopted for constructing PANoptosis molecule subtyping-related modules (Fig. 3A). For meeting a scale-free co-expression network, an appropriate soft threshold value should be determined. It was observed that when soft threshold value was 14, scale-free topology R^2 was 0.83, and mean connectively tended to be low (Fig. 3B, C), indicating a scale-free co-expression network. Genes with similar expression patterns were merged into one module. Consequently, seven modules were built (Fig. 3D), including blue (N = 685), brown (N = 388), green (N = 213), red (N = 164), yellow (N = 217), turquoise (N = 799) and grey (N = 916) modules. Among them, the yellow module presented the strongest positive interaction with the PANoptosis molecule subtyping (r = 0.54 and p = 2e-11) (Fig. 3E). Afterwards, we compared gene significance for the PANoptosis molecule subtyping across the co-expression modules. As illustrated in Fig. 3F, the yellow module had the highest gene significance. In addition, module membership of the yellow module was strongly associated with gene significance of the PANoptosis molecule subtyping (Fig. 3G). Altogether, the yellow module was regarded as the PANoptosis molecule subtyping-related module. Biological significance of the yellow module genes was subsequently evaluated. They were remarkably correlated to protein modification process, and immune response (Fig. 3H-J). In addition, natural killer cell-mediated cytotoxicity, RNA degradation, B cell receptor signaling pathway, phagosome, etc. were notably enriched by the yellow module genes (Fig. 3K).

  Fig. 3Identification of PANoptosis molecule subtyping-related genes. (A) Dendrogram of ischemic stroke peripheral blood specimens (upper) and heatmap of the two PANoptosis molecule subtypes (lower). (B) Scale independence or mean connectivity under a gradient of soft threshold values. (C) Selection of the optimal threshold of soft connectivity. (D) Gene dendrogram and establishment of co-expression modules. (E) Heatmap illustrating the relationships of the merged modules with the PANoptosis molecule subtyping. (F) Comparison of gene significance across the modules. (G) Scatter diagram depicting the association of module membership of the yellow module with gene significance of the PANoptosis molecule subtyping. (H-J) Biological processes, cellular components, and molecule functions of the yellow module genes. (K) KEGG pathway enrichment results on the yellow module genes


### Multiple machine learning algorithms for selecting PANoptosis signature genes for ischemic stroke diagnosis
  After intersecting the DEGs and the yellow module genes, 53 differentially expressed PANoptosis molecule subtyping-related genes were determined (Fig. 4A; Supplementary Table 2). Four well-established machine learning approaches: GLM, XGB, RF, and SVM were employed for determining PANoptosis signature genes genes with strong diagnostic potential. The SVM model presented the lowest |residual|, followed by RF, XGB, and GLM (Fig. 4B, C). Additionally, the first ten important feature genes of each model were ranked in accordance with the root mean square error (Fig. 4D). The area under the ROC curve (AUC) values were 1, 0.960, 0.960, and 0.679 for the SVM, RF, XGB, and GLM models, respectively (Fig. 4E). Thus, the SVM model was chosen as the diagnostic model for ischemic stroke, and the first eight feature genes in the SVM model were chosen as the PANoptosis signature genes (TMEM55A, CCPG1, CYP1B1, PJA2, MTPN, SCYL2, BAZ2B, and DPYD). All the key genes displayed the remarkably higher expression in peripheral blood of ischemic stroke in comparison to that of controls (Fig. 4F). Moreover, their expression was notably higher in the C2 subtype versus the C1 subtype (Fig. 4G).

  Fig. 4Multiple machine learning algorithms for selecting PANoptosis signature genes for ischemic stroke diagnosis. (A) Venn chart of the shared DEGs and the yellow module genes. (B) Box plots showing the root mean square of residuals in four machine learning algorithms: GLM, XGB, RF, and SVM. (C) Reverse cumulative distribution of |residuals| in the four machine learning algorithms. (D) The feature importance constructed by the four machine learning algorithms. (E) ROC curves of the four machine learning models in diagnosing ischemic stroke. (F) Box plots depicting the differential expression of the key genes in peripheral blood from ischemic stroke (IS) and control subjects. (G) Box plots for the differential expression of the key genes in the two PANoptosis molecule subtypes. ***p < 0.001


### Evaluation of each PANoptosis signature genes in diagnosing ischemic stroke
  The diagnostic utility of each PANoptosis signature genes in ischemic stroke was assessed. In the training set, the AUC values were 0.78, 0.847, 0.764, 0.812, 0.826, 0.773, 0.828, and 0.805 for TMEM55A, CCPG1, CYP1B1, PJA2, MTPN, SCYL2, BAZ2B, and DPYD, respectively (Fig. 5A-H), indicative of the favorable diagnostic efficacy. The generalizability of the PANoptosis signature genes was proven in the validation set (Supplementary Fig. 2A-H).

  Fig. 5Evaluation of each PANoptosis signature genes in diagnosing ischemic stroke, and construction of a diagnostic nomogram. (A-H) ROC curves of the PANoptosis signature genes: TMEM55A, CCPG1, CYP1B1, PJA2, MTPN, SCYL2, BAZ2B, and DPYD in diagnosing ischemic stroke. (I) The nomogram comprising PANoptosis signature genes for ischemic stroke risk prediction. (J, K) Calibration and decision curves for evaluating the accuracy of the nomogram in predicting ischemic stroke risk


### Generation of a nomogram comprising the PANoptosis signature genes for ischemic stroke risk prediction
  A nomogram was built for predicting ischemic stroke risk, composed of the PANoptosis signature genes (TMEM55A, CCPG1, CYP1B1, PJA2, MTPN, SCYL2, BAZ2B, and DPYD) (Fig. 5I). Calibration curves demonstrated that the nomogram accurately predicted ischemic stroke risk (Fig. 5J). Decision curve showed that patients could clinically benefit from the nomogram (Fig. 5K).


### Signaling pathways underlying the PANoptosis signature genes
  GSEA results demonstrated that BAZ2B was negatively linked with oocyte meiosis, ubiquitin-mediated proteolysis, O-glycan biosynthesis, and P53, TGF-beta, mTOR, and NOD-like receptor signaling pathways (Fig. 6A). CCPG1 presented the negative associations with apoptosis, and mTOR, Toll-like receptor, P53, ERBB, chemokine, and JAK-STAT signaling pathways (Fig. 6B). CYP1B1 was negatively connected to leishmania infection, and Toll-like receptor, insulin, and NOD-like receptor signaling pathways (Fig. 6C). In Fig. 6D, DPYD displayed the negative associations with O-glycan biosynthesis, apoptosis, ubiquitin-mediated proteolysis, and P53, TGF-beta, Toll-like receptor signaling pathways. In addition, MTPN was positively linked with JAK-STAT, ERBB, TGF-beta, Wnt, P53, and mTOR signaling pathways (Fig. 6E). PJA2 displayed the negative relationships with ubiquitin-mediated proteolysis, oocyte meiosis, and P53, TGF-beta, T cell receptor, and Wnt signaling pathways (Fig. 6F). SCYL2 presented the negative connections to O-glycan biosynthesis, ubiquitin-mediated proteolysis, oocyte meiosis, and TGF-beta, P53, and mTOR signaling pathways (Fig. 6G). Moreover, TMEM55A was found to negatively associate with RIG-I, Toll-like receptor, P53, NOD-like receptor, and TGF-beta signaling pathways, and O-glycan biosynthesis (Fig. 6H).

  Fig. 6Signaling pathways underlying the PANoptosis signature genes. (A-H) GSEA for probing the signaling pathways related to BAZ2B, CCPG1, CYP1B1, DPYD, MTPN, PJA2, SCYL2, and TMEM55A


### Associations of the PANoptosis signature genes with immune cell infiltration
  We further probed the relationships of each PANoptosis signature gene with the infiltration of immune cell types in peripheral blood of ischemic stroke. The results demonstrated that BAZ2B, CCPG1, CYP1B1, DPYD, MTPN, PJA2, SCYL2, and TMEM55A were all remarkably linked with the abundance of most immune populations (Fig. 7A-H).

  Fig. 7Associations of the PANoptosis signature genes with immune cell infiltration in peripheral blood of ischemic stroke. (A-H) Correlation analyses on BAZ2B, CCPG1, CYP1B1, DPYD, MTPN, PJA2, SCYL2, and TMEM55A with the infiltration of immune cell populations


### Transcription factors of the PANoptosis signature genes
  Transcription factors of the PANoptosis signature genes were predicted, and a transcription factor-gene network was established, as shown in Supplementary Fig. 3, such as SIN3A, RAD21, and SOX13 for BAZ2B; CUX1, FOXA3, and KLF11 for CCPG1; CTBP1, SP3, and NFIC for CYP1B1; ETS1, TBX21, KLF6 for MTPN; FOXM1, ZNF83, and EED for PJA2; ZNF335, SMAD5, and ZNF589 for SCYL2; SAP30, PHF8, and KDM5B for TMEM55A.


### Drugs that potentially target the PANoptosis signature genes
  Drugs that potentially targeted the PANoptosis signature genes were predicted. As illustrated in Supplementary Fig. 4, chrysin, exemestane, chembl2347759, formestane, amodiaquine, acacetin, pinocembrin, 2’h,4 h-[2,8’-bichromen]-4-one, toremifene, medroxyprogesterone acetate, letrozole, isopropyl alcohol, doxorubicin, paclitaxel, anastrozole, risperidone, fadrozole, naringenin, alpha-naphthoflavone, fluorouracil, cyclophosphamide, spironolactone, epirubicin, rifampin, 2’h,4 h-[2,5’-bichromen]-4-one, beta-naphthoflavone, aminoglutethimide, and docetaxel potentially targeted CYP1B1. Gossypol, piroxicam, prostaglandin a2, chembl533226, oxytetracycline, chembl1588237, tyrphostin 23, mifepristone, chembl586000, chembl584248, slazinic acid, chembl546170, stilonium iodide, chembl235891, chembl339587, 3-o-methylquercetin, pyronin y, chembl602927, chembl1388703, doxorubicin hydrochloride, chembl1310138, chembl606167, chembl2002487, chembl602363, pentabromophenol, chembl602718, deferiprone, chembl84010, nitroxoline, and chembl591361 potentially targeted BAZ2B. Gimeracil, oxaliplatin, capecitabine, tegafur, eniluracil, fluorouracil, flucytosine, leucovorin, and irinotecan potentially targeted DPYD.


### Role of the PANoptosis molecule subtyping-related genes in glioma
  The glioma and ischemic stroke are the two leading causes of death worldwide. Despite their different physiological incidence, 10% of ischemic stroke patients develop brain cancer, especially glioma, in the post-ischemic phase [34]. Thus, we further estimated the prognostic value of the genes in glioma. The survival analysis result revealed that most of genes including CCPG1, CYP1B1, DPYD, MTPN, PIP4P2 and SCYL2 were risky genes (HR > 1, p-value < 0.05) that high expression of it was corresponding to a poor survival outcome, while BAZ2B was a protective genes (HR < 1, p-value < 0.05) (Fig. 8). ROC curve analysis result indicated that BAZ2B, SCYL2, DPYD, and MTPN have a good prognostic ability in the 1-year overall survival of glioma (Fig. 9A). The diagnostic ROC curve result revealed that BAZ2B, PJA2, PIP4P2 showed a good diagnostic value between normal and glioma patients (Fig. 9B). The expression level between normal and glioma of eight genes were further examined. As supplementary Fig. 5 showed most of genes have no significant difference between normal and glioma tissue, except PJA2 as the RNA level. To further verify the expression at the protein level, a quantitative analysis of tissue immunohistochemistry (IHC) from the HPA database was conducted on these genes. As Fig. 10 showed, most of genes including BAZ2B, CCPG1, CYP1B1, PJA2 presented a high level in tumor tissue compared to normal brain tissue, while DPYD showed an increase level in normal brain tissue. Moreover, the immunofluorescence staining data from the HPA database was also used to analyze the subcellular distribution of these three genes in the U-251MG glioma cell, and the result showed MTPN and PJA2 were in cytosol and intermediate filaments, respectively (Fig. 11).

  Fig. 8Survival analysis on BAZ2B, CCPG1, CYP1B1, DPYD, MTPN, TMEM55A (PIP4P2), PJA2, and SCYL2 in glioma

  Fig. 9ROC curve analysis of the eight genes in glioma. (A) Prognostic ROC curve analysis was performed to evaluated the prognostic value of PANoptosis molecule subtyping-related genes as 1-year overall survival in glioma patients. (B) ROC analysis was performed to evaluated the diagnostic value of PANoptosis molecule subtyping-related genes between normal and glioma tissue

  Fig. 10The protein expression level of eight genes was evaluated in HPA database

  Fig. 11Immunofluorescence revealed the localization of MTPN and PJA2 in the U-251MG glioma cell


## Discussion
  As the awareness of programmed cell death mechanisms increase, unique molecular features of different programmed cell death modality have been discovered [35]. Apoptosis is a broadly studied non-inflammatory programmed cell death triggered by caspase-3/7 downstream of caspase-8/9/10 [36]. Necroptosis is initiated by RIPK3-dependent MLKL oligomerization [36]. Moreover, pyroptosis is driven by the gasdermin family members (GSDMD, and GSDME) [37]. PANoptosis is a coordinated system in which any one of the three programmed cell death modes compensates for the other and can work together [38]. Nevertheless, research on PANoptosis in ischemic stroke remains lacking.

  Alterations in gene expression following ischemic stroke can be potentially applied as biomarkers for etiology of ischemic stroke and estimating patient outcomes [39]. We found that 15 PANoptosis genes were aberrantly expressed in peripheral blood of ischemic stroke, of which TNFSF10, PPP3R1, CASP1, APAF1, CHUK, YWHAG, LY96, CD14, HMGB2, MLKL, TFDP1, and BNIP3L were up-regulated, and DFFB, CYCS, and FASLG were down-regulated in ischemic stroke. These findings expanded our comprehending of the transcriptomic alterations of PANoptosis genes in peripheral blood following ischemic stroke. On the basis of these PANoptosis genes, ischemic stroke was classified as two PANoptosis molecular subtypes. Each PANoptosis subtype owned the unique PANoptosis gene expression, molecular mechanisms, and infiltration of immune cell types.

  Four machine learning models: SVM, RF, XGB, and GLM were constructed for diagnosing ischemic stroke. Among them, the SVM model had the AUC of 1. The feature genes in the SVM model (BAZ2B, CCPG1, CYP1B1, DPYD, MTPN, PJA2, SCYL2, and TMEM55A) were considered as the PANoptosis signature genes. The nomogram based upon them could accurately estimate the risk of ischemic stroke. Among them, CYP1B1 genetic variants (rs10916 and rs2855658) have been determined to correlate to increased risk of ischemic stroke in Chinese Han population who are ≥ 60 years old, smoking, or drinking [40].

  Pathology and treatment of ischemic stroke usually focus on the brain. Exploring inflammation, an essential secondary cell death mechanism in ischemic stroke, is largely relegated to the brain [41]. Thus, peripheral inflammation is an equally potent contributor to the initiation and development of ischemic stroke secondary cell death. The PANoptosis signature genes were all connected to the abundance of most immune cell populations, demonstrating the associations of the key genes with peripheral inflammation.

  To probe out the transcriptional regulation mechanisms of the PANoptosis signature genes, we inferred their potential upstream transcriptional factors that might contribute to the aberrant expression in peripheral blood of ischemic stroke. In addition, we predicted drugs that potentially targeted the PANoptosis signature genes. Nevertheless, experiments require to be implemented for proving the mechanisms of the transcriptional factor-gene interactions and the drug-gene interactions in ischemic stroke.

  The retrospective nature of the research restricts the establishment of causal relationships between the identified lncRNA features and clinical outcomes. Relying on Cancer Genome Atlas (TCGA) data may introduce selection bias as the represented patient demographics and healthcare systems may not fully represent a broader population of ccRCC patients. Additionally, while the statistical methods used are standard, they do not account for potential nonlinear relationships or interactions between lncRNAs, which could be revealed through more advanced analytical techniques.

  Despite the results being promising, there are still some limitations to this study. Firstly, all the data were retrieved from a public database and lack experiments to validate their functions and molecular mechanisms. Secondly, considering the small sample size of these datasets, there is still a need to validate the robustness of the results in large and multi-central cohorts. Thirdly, the model is overfitting and requires further expansion of samples to demonstrate its generalizability.


## Conclusion
  Collectively, the study proposed two diverse PANoptosis molecular subtypes for ischemic stroke, providing a novel insight into the associations of PANoptosis with molecular and immune characteristics. Additionally, the PANoptosis-related genes could effectively predict the prognosis of glioma patients. These findings provide a roadmap for patient risk stratification, and assist improve diagnosis and prognosis for ischemic stroke and glioma.


## Supplementary Information
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2

  Supplementary Material 3

  Supplementary Material 4

  Supplementary Material 5

  Supplementary Material 6

  Supplementary Material 7


## Acknowledgements
  We sincerely thank the Gene Expression Omnibus (GEO) and The Cancer Genome Atlas Program (TCGA) database for providing the raw data.