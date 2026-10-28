# The GFPT2/O-GlcNAcylation/c-Myc axis promotes bladder cancer progression


## Background
  Glucose metabolic reprogramming is a hallmark of bladder cancer. However, the exact relationship between glucose metabolism and the onset and progression of bladder cancer remains poorly understood.


## Methods
  We integrated a metabolic gene interaction perturbation network with machine learning algorithms to identify GFPT2 as a metabolic prognostic gene in bladder cancer. External validation was performed through survival analysis using clinical cohort data. GFPT2 expression levels was assessed by RT‒qPCR, Western blotting, and immunohistochemistry. To further explore the protumorigenic role of GFPT2, cell function experiments and animal studies were conducted. Coimmunoprecipitation and immunofluorescence techniques were used to investigate the interactions between the key downstream molecules, c-Myc and OGT, and GFPT2.


## Results
  GFPT2 expression was higher in bladder cancer tissues than in normal tissues, and high GFPT2 expression was closely associated with poor prognosis in bladder cancer patients. GFPT2 overexpression promoted the proliferation and migration of bladder cancer cells. Mechanistic studies revealed that GFPT2 regulated the O-GlcNAcylation of c-Myc, inhibited its ubiquitination-mediated degradation, and thereby enhanced c-Myc stability, which promoted the proliferation and migration of bladder cancer cells.


## Conclusion
  This study reveals a novel mechanism involving the GFPT2/O-GlcNAcylation/c-Myc signalling axis in the malignant progression of bladder cancer. These findings provide a theoretical basis for potential new therapeutic strategies targeting bladder cancer.


## Supplementary Information
  The online version contains supplementary material available at 10.1186/s12967-026-07811-0.


## Introduction
  Bladder cancer is the ninth most common malignant tumour worldwide. In 2022, approximately 614,000 new cases were diagnosed, and approximately 220,000 deaths were attributed to the disease [1]. Among the various subtypes of bladder cancer, muscle-invasive bladder cancer is particularly aggressive, and is characterised by a high propensity for metastasis and recurrence [2, 3]. Despite undergoing radical cystectomy, patients have a 5-year overall survival rate of only 66% [4]. The significant economic strain and clinical challenges posed by bladder cancer underscore the urgent need for the development of novel molecular markers to improve diagnosis, treatment, and prognosis.

  Metabolic reprogramming is a hallmark of tumour cells, including those of bladder cancer [5]. Glucose metabolism involves the glycolytic pathway, pentose phosphate pathway, and hexosamine biosynthesis pathway (HBP) [6]. The HBP, a crucial branch of glucose metabolism, significantly promotes the proliferation and metastasis of bladder cancer cells [7]. UDP-GlcNAc, the end product of the HBP, is a crucial substrate for O-GlcNAc glycosylation, which regulates signalling processes that are fundamental to tumour progression [8]. GFPT2, a key enzyme in the HBP, influences tumour cell proliferation, migration, and invasion by regulating HBP flux [9]. However, the precise mechanisms through which GFPT2-mediated O-GlcNAcylation affects bladder cancer progression remain poorly understood. This gap in knowledge underscores the importance of further research into the role of GFPT2 in metabolic reprogramming and its potential impact on bladder cancer.

  O-GlcNAcylation, a reversible posttranslational modification, has been linked to various aspects of cancer biology. Previous studies have shown that O-GlcNAcylation can upregulate the expression and stability of NUSAP1, thereby accelerating bladder cancer progression [10]. However, the detailed mechanisms through which O-GlcNAcylation modulates downstream targets to affect cell proliferation and metastasis remain incompletely elucidated.

  c-Myc is a widely studied oncogenic transcription factor that regulates tumour cell proliferation, invasion, angiogenesis, metabolism, and immune evasion [11]. Regarding bladder cancer, c-Myc acts as an oncogene that promotes malignant progression and enhances both tumour cell growth and invasion [12, 13]. Moreover, c-Myc is closely associated with glucose metabolism, and inhibition of the HBP pathway has been shown to reduce c-Myc expression, subsequently suppressing tumour cell growth [14]. Despite these findings, the role of c-Myc O-GlcNAcylation in bladder cancer progression remains unclear. We therefore hypothesise that GFPT2, the rate-limiting enzyme of the HBP, may regulate O-GlcNAcylation of c-Myc.

  This study identifies GFPT2 as a potential prognostic marker for bladder cancer. We show that GFPT2 enhances the malignant phenotype of bladder cancer by increasing cellular O-GlcNAcylation. We further elucidate the role of the GFPT2/O-GlcNAcylation/c-Myc axis in driving bladder cancer cell proliferation and migration. Notably, this report is the first to document GFPT2-mediated O-GlcNAcylation in bladder cancer, offering new insights for future targeted therapies.


## Methods

### Data sources
  To ensure data integrity and analytical accuracy, we included bladder urothelial carcinoma samples with multiomics profiles and complete clinical information. We used a bladder cancer cohort (n = 400) from the TCGA database (https://portal.gdc.cancer.gov) along with normal bladder tissue samples (n = 9) from the GTEx database (https://www.gtexportal.org/) to construct a metabolic perturbation network for bladder cancer. The TCGA cohort was used as the training set for the metabolic prognostic risk model, while two independent GEO datasets, GSE13507 (n = 165) and GSE32548 (n = 130) from the Gene Expression Omnibus (https://www.ncbi.nlm.nih.gov/geo/), served as the validation cohorts.


### Construction and identification of metabolic perturbation network subtypes
  To investigate the mechanisms underlying tumour heterogeneity within the metabolic perturbation network, we constructed a network reflecting mutual perturbations among metabolic genes [15, 16]. We first mapped candidate genes to a protein functional relationship network using metabolic pathway annotations, and then constructed a metabolic gene interaction perturbation network to identify bladder cancer metabolic subtypes (Supplementary Materials and Fig. 1A). Consensus clustering (ConsensusClusterPlus R package) was applied to the perturbation network, which comprised 763 metabolic genes and 1989 interactions, to identify metabolic subtypes. UMAP dimensionality reduction and visualisation were performed with the umap and ggplot2 packages. To characterise the differences among the metabolic subtypes, we conducted GSVA on the subtypes (Supplementary Fig. 1). Finally, we assessed the survival and prognosis of the subtypes using the Kaplan–Meier method and Cox regression analysis.

  Fig. 1Construction of metabolic perturbation network subtypes in bladder cancer. (A) Flowchart illustrating the construction of the gene interaction perturbation network. (B, C) Consensus clustering matrix heatmap and UMAP plot showing the optimal number of clusters (K = 6) for the TCGA bladder cancer cohort. (D) Kaplan‒Meier survival curves of overall survival for the six metabolic subtypes in the TCGA bladder cancer cohort. Subtype C3 had the most favourable prognosis, whereas subtype C6 had the poorest outcome. (E) Results of univariate analysis for the six bladder cancer subtypes. Univariate Cox proportional hazards regression analysis of the six metabolic subtypes revealed significant heterogeneity in survival outcomes. Subtype C3 was associated with the lowest risk of death, and subtype C6 was associated with the highest risk


### Construction of the prognostic model and selection of key genes
  Differentially expressed genes (DEGs) between the C3 and C6 subtypes were identified. These DEGs were then integrated with genes from the GSE13507, GSE32548, and TCGA bladder cancer cohorts, along with 599 metabolic genes from 24 KEGG differential metabolic pathways. From this integration, we extracted intersecting genes for machine-learning modelling (Supplementary data, Supplementary Fig. 2). A total of 92 algorithm combinations from 9 algorithms, including Lasso, Ridge, GBM, SuperPC, plsRcox, CoxBoost, stepwise Cox, elastic Net, and random survival forest (RSF), were used to construct a prognostic risk model, and the predictive ability was evaluated by the C-index. The StepCox[forward] + RSF combination emerged as the optimal model. We divided the patients in the TCGA cohort into high- and low-risk groups on the basis of the resulting risk scores. We evaluated survival prognosis with Kaplan–Meier analysis and assessed model performance using receiver operating characteristic (ROC) curves. Bidirectional stepwise Cox regression identified six top-ranked metabolism-related prognostic genes (MRPGs). We estimated the importance of each MRPG with the importance function in the RandomForest package and determined the optimal cut-off value for each MRPG with the survminer package, dividing samples into high- and low-expression groups. We evaluated the survival prognosis for each group by Kaplan–Meier analysis and selected the most important MRPG as the target gene.


### RNA extraction and quantitative real-time PCR
  Total RNA was extracted using RNAiso Plus (Takara, Japan). Subsequently, cDNA synthesis was subsequently conducted with a ToloScript RT EasyMix for qPCR kit (TOLOBIO, China). Quantitative real-time PCR (qRT‒PCR) was then performed on a 7500 Real-Time PCR System following the instructions of the SYBR qPCR Master Mix (TOLOBIO, China). The primer sequences employed in this study are detailed in the Supplementary Materials.


### Western blotting
  Protein extraction was followed by treatment of the samples with SDS‒PAGE sample buffer. The proteins were then separated by SDS‒PAGE electrophoresis. After electrophoresis, the proteins were transferred to a polyvinylidene fluoride (PVDF) membrane. The membrane was subsequently blocked at room temperature with 5% skim milk powder for 1 h Following blocking, the membrane was incubated overnight with the primary antibody, after which it was washed. The membrane was then incubated with the appropriate secondary antibody for 1 h, followed by additional washing steps. Chemiluminescence was used to develop the images, and the membrane was photographed for further analysis (details of the antibodies are provided in the Supplementary Materials).


### Bladder cancer cohort and immunohistochemistry
  Clinical data were collected from patients diagnosed with bladder urothelial carcinoma who underwent bladder tumour surgery between January 2014 and December 2021. Immunohistochemical analysis was conducted on 70 bladder urothelial carcinoma tissue samples with complete data and 30 paired adjacent normal tissue samples. Additionally, fresh tumour and adjacent tissue samples from 24 patients who underwent radical cystectomy between September 2023 and July 2025 were analysed for GFPT2 mRNA and protein expression levels using RT‒qPCR and Western blotting. Patient follow-up was conducted via outpatient visits or telephone contact. Overall survival time was defined as the duration from the date of surgery to either the date of death or the end of the follow-up period.

  This study adhered to the ethical principles of the Declaration of Helsinki and received approval from the Ethics Committee of Liuzhou Workers’ Hospital (No.: KY2024532). All participants signed informed consent forms and were clearly informed of the research purpose and their rights. Paraffin sections were baked, dewaxed, and hydrated, and antigen retrieval was performed in EDTA solution for 20 min. The sections were then incubated with 3% hydrogen peroxide at room temperature for 10 min to block endogenous peroxidase activity. Next, sections were incubated with the primary antibody overnight at 4°C, followed by incubation with the secondary antibody at room temperature. 3,3’-Diaminobenzidine was used for colour development, and haematoxylin was used for counterstaining; images were captured under a microscope.

  GFPT2 expression was independently evaluated by two senior pathologists, who scored the proportion of positive cells and staining intensity. The proportion scores were 4 (> 76%), 3 (51–75%), 2 (26–50%), 1 (1–25%), and 0 (0%). Staining intensity was scored as 3 (strongly positive), 2 (positive), 1 (weakly positive), or 0 (negative). The immunoreactivity score (IRS) was equal to the product of these two scores (range, 0–12). The samples were classified into high- and low-expression groups according to the optimal cut-off value.

  The Ki67 scoring criteria followed those of previous studies. High expression was defined as a proportion of positive cells > 15%, and low expression was defined as a proportion of positive cells ≤ 15% [17, 18].


### Cell lines and reagents
  T24, UM-UC-3, J82, 5637, and SV-HUC-1 cells were obtained from the Cell Bank of the Chinese Academy of Sciences. T24 cells were maintained in RPMI-1640 medium (Gibco, Shanghai, China), while UM-UC-3 cells were maintained in Dulbecco’s modified Eagle’s medium (DMEM) (Gibco, Shanghai, China). All media were supplemented with 10% foetal bovine serum (FBS, Procella, Wuhan, China) and 1% penicillin–streptomycin, and the cultures were kept in a humidified incubator at 37 °C with 5% CO₂. OSMI-1 (1681056-61-0; Proteintech, Wuhan, China) and 10,058-F4 (MCE; HY-12702; Shanghai, China) were used in this study.


### Immunofluorescence
  Cells from each treatment group were fixed with 4% paraformaldehyde, permeabilised with 0.3% Triton X-100, and washed with PBS. After blocking for 30 min at room temperature, the cells were incubated with the primary antibody overnight at 4 °C and then incubated with the secondary antibody for 1 h at room temperature. After counterstaining with DAPI, the samples were observed and imaged under a microscope.


### Cell counting Kit-8 (CCK-8), colony formation, wound healing and transwell migration assays

#### CCK-8 assay
  Cells were cultured in a 96-well plate, and reagents were added according to the instructions of the CCK-8 kit (Beyotime, Shanghai, China). The absorbance was measured using a microplate reader.


#### Colony formation assay
  Cells were seeded into 24-well plates at a density of 300 cells/well and cultured in growth medium for 2 weeks. After the culture period, the cells were stained with crystal violet and photographed, and the number of colonies formed was counted.


#### Wound healing assay
  Cells were seeded into 6-well plates at a density of 5 × 10⁵ cells per well and cultured until they reached 90–100% confluence. A sterile pipette tip was used to generate a straight-line scratch across the monolayer. The wells were gently rinsed with phosphate-buffered saline (PBS) to remove detached cells and debris. Fresh serum-free culture medium was then added to minimise the confounding effects of cell proliferation, and the cells were incubated for an additional 18 h. Images of the wound area were captured at 0 h and 18 h using an inverted phase-contrast microscope to assess cell migration.


#### Transwell migration
  Transfected cells were seeded into the upper chamber of a 24-well Transwell insert (Corning, USA), and the lower chamber was filled with medium containing 10% foetal bovine serum. After incubation, the cells were fixed with paraformaldehyde, stained with crystal violet, and observed under a microscope to record migration.


### Coimmunoprecipitation(Co-IP)assay
  After cell lysis, the target antibody was added and incubated overnight at 4 °C to form immune complexes. Washed protein A/G magnetic beads were then added, and the samples were incubated at 4 °C for 4–6 h. After the unbound components were removed by multiple washes, the immunoprecipitated proteins were heated with 50 µL 1× SDS–PAGE sample buffer at 95 °C for 5 min for immunoblot analysis.


### Animal studies
  Male BALB/C nude mice (Beijing Vital River Laboratory Animal Technology, China) were used to establish subcutaneous tumorigenesis and lung metastasis models. The Experimental Animal Ethics Committee of Guangxi Medical University approved the animal protocol (No.: 202408006).


#### Subcutaneous tumour xenograft model
  Bladder cancer cells (5 × 106) were injected into the left axilla of each mouse (n = 5). Once subcutaneous tumours formed, tumour size and body weight were measured every 3 days. The experiment ended when the tumour volume reached 1000 mm3 (volume = width2 × length × 0.52). Tumours were excised, photographed, fixed, and processed into paraffin sections for immunohistochemistry (IHC) analysis.


#### Lung metastasis model
  Bladder cancer cells (1 × 106) were injected into nude mice via the tail vein, and pulmonary metastatic foci were monitored using an in vivo imaging system. After euthanasia, we dissected and photographed the lungs, fixed them in 4% paraformaldehyde, and processed the tissues into paraffin sections for haematoxylin and eosin (HE) staining.


#### c-Myc inhibitor intervention model
  One week after the nude moice model was established, 10,058-F4 (20 mg/kg) was administered via the tail vein injection every two days for a total of five doses.


### Statistical analysis
  Data processing and statistical analyses were performed using R software (version 4.4.1), IBM SPSS Statistics 25, GraphPad Prism 10, and Zstats 1.0 (www.zstats.net). Categorical variables were compared using the chi-square test or Fisher’s exact test, as appropriate. For continuous variables, the log-rank test, Wilcoxon rank-sum test, or t test was applied depending on the data characteristics. Differences among multiple groups were assessed using one-way ANOVA. Survival analysis was conducted using the Kaplan–Meier method with the “survival” and “survminer” R packages. All statistical tests were two-sided, and a P value of less than 0.05 was considered to indicate statistical significance. P values are presented as follows: not significant (NS) for p > 0.05, *p < 0.05, **p < 0.01, ***p < 0.001, and ****p < 0.0001.


## Results

### Construction of bladder cancer metabolic perturbation network subtypes
  We constructed a bladder cancer metabolic perturbation network by integrating the initial background network, 948 metabolism-related genes from the MisgDB database, and gene data from TCGA bladder cancer samples and GTEx normal bladder tissue samples. This network included 763 metabolic genes and 1989 interactions (Fig. 1A). We then conducted a consensus clustering analysis on the perturbation network [19] and applied the UMAP dimensionality reduction algorithm to classify bladder cancer samples into six distinct subtypes (Fig. 1B, C). Kaplan-Meier survival analysis revealed significant differences in survival among the subtypes, with subtype C6 having the poorest prognosis and subtype C3 having the best prognosis (Fig. 1D). These findings were further validated by Cox proportional hazards regression analysis (Fig. 1E). GSVA revealed variations in metabolic pathway expression between the C6 and C3 subtypes, with C6 exhibiting higher metabolic activity (Supplementary Fig. 1), further supporting our conclusions. Overall, compared with the C6 subtype, the C3 subtype was associated with a more favourable clinical prognosis in terms of survival.


### Machine learning screening of MRPGs
  We applied machine learning algorithms to model 106 metabolic genes and evaluated each model’s predictive performance by calculating the C-index on the training and validation sets (Fig. 2A). The StepCox[forward] + RSF model achieved the highest mean C-index (0.742) and was selected as the best prognostic predictor. Using this model, we computed prognostic risk scores for samples in the TCGA bladder cancer cohort and divided the samples into high- and low-risk groups according to their scores. Kaplan–Meier survival analysis revealed a statistically significant difference in survival between the high- and low-risk groups (Fig. 2B–D), and ROC curves were used to assess the model’s predictive performance (Fig. 2E–G). Bidirectional stepwise Cox regression based on the StepCox[forward] + RSF model was used to screen six MRPGs, and heatmaps were constructed to illustrate their expression across subtypes and risk groups (Fig. 3A). Prognostic significance scoring revealed that GFPT2 had the highest score (Fig. 3B). Kaplan-Meier curves for the three cohorts revealed that high GFPT2 expression was associated with poor bladder cancer prognosis (Fig. 3C–E), indicating that GFPT2 may serve as a potential prognostic molecular marker for bladder cancer patients.

  Fig. 2Prognostic modelling of MRPGs in bladder cancer with machine learning algorithms. (A) Concordance indices for 92 combinations of machine learning algorithms. (B–D) Kaplan‒Meier survival curves comparing the high- and low-risk groups in the TCGA, GSE13507, and GSE32548 bladder cancer cohorts. Patients in the high-risk group had a significantly poorer prognosis. (E–G) ROC curves of the risk-score prognostic models for the TCGA, GSE13507, and GSE32548 bladder cancer cohorts

  Fig. 3Identification of MRPGs. (A) Heatmap showing the expression of six MRPGs. (B) Prognostic importance scores for the six MRPGs, with higher scores indicating a greater contribution to survival prediction. (C–E) Kaplan–Meier survival curves showing that high GFPT2 expression is significantly associated with poor overall survival in three independent cohorts: the TCGA (C), GSE13507 (D), and GSE32548 (E) cohorts


### GFPT2 is a prognostic molecular marker for bladder cancer
  To validate the findings of the previous study, we examined clinical tissue specimens. The results indicated that GFPT2 mRNA and protein expression were increased in bladder cancer tissues compared with those in adjacent normal tissues (Fig. 4A, B). Immunohistochemical analysis of cancerous and adjacent tissues from 70 bladder cancer patients revealed that GFPT2 protein expression was predominantly localised to the cytoplasm, whereas Ki67 protein expression was primarily localised to the nucleus. Both proteins were expressed at higher expression levels in bladder cancer tissues than in normal tissues (Fig. 4C, D). To elucidate the clinical prognostic value of GFPT2 expression, we analysed its correlation with clinicopathological features in a bladder cancer cohort (Supplementary Materials, Supplementary Table 1). Through Kaplan‒Meier survival analysis of a single-centre cohort, we confirmed that GFPT2 expression levels strongly correlated with poor prognosis in bladder cancer patients (Fig. 4E). These results indicate that GFPT2 expression can serve as a prognostic molecular marker for bladder cancer patients after surgery.

  Fig. 4GFPT2 expression is a prognostic molecular marker for bladder cancer. (A) RT‒qPCR analyzed GFPT2 mRNA expression in 24 paired bladder cancer and tissue samples. (B) Western blot analysis of GFPT2 protein expression in 4 paired bladder cancer and normal tissue samples. (C, D) IHC staining revealed significantly higher protein expression of GFPT2 and Ki-67 in bladder cancer tissues than in normal tissues. (E) Kaplan–Meier survival curves showing that high GFPT2 protein expression is associated with significantly worse overall survival in bladder cancer patients


### GFPT2 promotes the proliferation and migration of bladder cancer cells
  To clarify the role of GFPT2 in bladder cancer, we examined its effects on cell proliferation and migration. We first measured GFPT2 expression in the normal bladder urothelial cell line SV-HUC-1 and in several bladder cancer cell lines. GFPT2 expression was higher in the cancer cell lines than in SV-HUC-1 cells, and the RT‒qPCR and Western blotting results were consistent. Its expression was highest in UM-UC-3 cells and relatively lower in T24 cells (Fig. 5A, B). Therefore, we chose UM-UC-3 cells to establish a stable GFPT2 expression knockdown line and T24 cells to establish a stable GFPT2 overexpression line (Supplementary Fig. 4). CCK-8 and colony formation assays revealed that knockdown of GFPT2 expression significantly inhibited the proliferation of UM-UC-3 cells, whereas overexpression of GFPT2 significantly promoted the proliferation of T24 cells (Fig. 5C, D). Knockdown of GFPT2 expression in UM-UC-3 cells reduced the migration of bladder cancer cells, and the opposite trend was observed in T24 cells with GFPT2 overexpressing (Fig. 5E, F). We used UM-UC-3 cells stably expressing shGFPT2 or shNC to construct subcutaneous tumour xenograft and lung metastasis models in nude mice. These experiments revealed that knockdown of GFPT2 expression inhibited tumour growth and metastasis (Fig. 5G–J). Immunohistochemistry revealed decreased expression of GFPT2, OGT, and Ki67, suggesting that GFPT2 may affect bladder cancer cell proliferation by regulating O-GlcNAcylation (Fig. 5K).

  Fig. 5GFPT2 promotes bladder cancer cell proliferation and migration. (A, B) GFPT2 expression in normal bladder urothelial cell lines and bladder cancer cell lines. (C) A CCK-8 assay was used to assess the effect of GFPT2 on the proliferative activity of bladder cancer cells. (D) Effect of GFPT2 on the colony-forming ability of bladder cancer cells. (E, F) Wound-healing and Transwell migration assays were used to determine the effect of GFPT2 expression on bladder cancer cell migration. (G–I) Effect of GFPT2 on subcutaneous tumorigenesis in nude mice. (J) Effect of GFPT2 on lung metastasis model of bladder cancer in nude mice. (K) IHC was used to detect GFPT2, OGT, and Ki67 protein expression in subcutaneous tumours from nude mice


### GFPT2 regulates O-GlcNAcylation levels in bladder cancer cells
  GFPT2 is a key enzyme in the HBP that converts fructose-6-phosphate to GlcN-6-P, which is further processed to the HBP end product UDP-GlcNAc and thereby controls HBP flux [9]. UDP-GlcNAc serves as the essential substrate for O-GlcNAcylation and is used by OGT to carry out O-GlcNAc on proteins [20]. Previous studies have shown that GFPT2 modulates O-GlcNAcylation levels in tumour cells through the HBP [21, 22]. We therefore hypothesised that GFPT2 regulates O-GlcNAcylation in bladder cancer cells. To test this hypothesis, we observed that knocking down GFPT2 expression in the UM-UC-3 cells resulted in decreased OGT expression and reduced O-GlcNAcylation levels. Conversely, the overexpression of GFPT2 in T24 cells increased OGT expression and O-GlcNAcylation (Fig. 6A, B). To further assess the role of O-GlcNAcylation in GFPT2-driven phenotypes, we treated GFPT2-overexpressing bladder cancer cells with OSMI-1, an OGT inhibitor, and found that OSMI-1 markedly reversed the enhanced proliferation and migration induced by GFPT2 overexpression (Fig. 6C–E). These results suggest that GFPT2 promotes malignant progression in bladder cancer through the regulation of O-GlcNAcylation.

  Fig. 6GFPT2 regulates O-GlcNAcylation levels in bladder cancer cells. (A, B) GFPT2 increased O-GlcNAcylation in bladder cancer cells. (C) A colony formation assay was used to assess the effect of OSMI-1 on the proliferation of bladder cancer cells overexpressing GFPT2. (D, E) Wound-healing and Transwell migration assays were used to evaluate the effect of OSMI-1 on the migration of GFPT2-overexpressing bladder cancer cells


### GFPT2 regulates the O-GlcNAcylation of c-Myc
  Studies have shown that O-GlcNAcylation of c-Myc is associated with the malignant progression of tumour cells [23]. Therefore, we speculate that GFPT2 may influence bladder cancer cells by modulating c-Myc O-GlcNAcylation. To test this hypothesis, we initially examined the interaction between c-Myc and OGT in bladder cancer cells using Co-IP and immunofluorescence experiments (Fig. 7A, B). These results suggest that c-Myc is a downstream target of GFPT2. Subsequent IP experiments demonstrated that c-Myc underwent O-GlcNAc modification (Fig. 7C, D). We next assessed the effect of GFPT2 on c-Myc mRNA and protein expression. GFPT2 altered the protein expression of OGT and c-Myc but did not significantly affect c-Myc mRNA expression (Fig. 7E, F). These findings supports a role for GFPT2 in regulating c-Myc O-GlcNAcylation. Additionally, the OGT inhibitor OSMI-1 reversed the increase in c-Myc O-GlcNAcylation induced by GFPT2 overexpression in T24 cells (Fig. 7G).

  Fig. 7GFPT2 regulates the O-GlcNAcylation of c-Myc. (A) Co-IP results showing the interaction between c-Myc and OGT. (B) Immunofluorescence staining demonstrating the colocalisation of c-Myc and OGT. (C, D) O-GlcNAcylation of c-Myc was detected. (E) RT‒qPCR analysis of GFPT2, OGT, and c-Myc mRNA expression in bladder cancer cells after GFPT2 knockdown and overexpression. (F) Western blot analysis of GFPT2, OGT, and c-Myc protein levels in bladder cancer cells with GFPT2 knockdown or overexpression. (G) O-GlcNAcylation of c-Myc after OSMI-1 treatment


### O-GlcNAcylation of c-Myc increases its protein stability
  Previous studies have shown that GFPT2 regulates c-Myc protein expression and O-GlcNAcylation. O-GlcNAcylation affects protein stability, protein‒protein interactions, and subcellular localisation [24]. To explore the relationship between GFPT2 and c-Myc stability, we treated T24 bladder cancer cells overexpressing GFPT2 with cycloheximide (CHX). The results revealed that GFPT2 overexpression slowed c-Myc degradation (Fig. 8A). We also examined the degradation pathway of c-Myc by treating cells with MG-132 and bafilomycin A1 (BafA1). The results revealed that the c-Myc protein was degraded via the proteasome pathway rather than the lysosomal pathway (Fig. 8B). The overexpression of GFPT2 significantly increased the O-GlcNAcylation level of c-Myc while decreasing its ubiquitination level. Conversely, knocking down GFPT2 expression resulted in the opposite effect (Fig. 8C). The OGT inhibitor OSMI-1 effectively reversed the changes in O-GlcNAcylation and ubiquitination levels of c-Myc induced by GFPT2 overexpression in T24 cells (Fig. 8D). These findings suggest that GFPT2-mediated O-GlcNAcylation inhibits c-Myc ubiquitination, thereby increasing its protein stability. To determine whether GFPT2 exerts its procancer effects through c-Myc, we treated GFPT2-overexpressing T24 cells with the c-Myc inhibitor 10058-F4, which significantly reversed the proliferation and migration phenotypes induced by GFPT2 overexpression (Fig. 8E–G).

  Fig. 8GFPT2 regulates the O-GlcNAcylation of c-Myc and inhibits its ubiquitin-mediated degradation. (A) Western blot analysis showed that ectopic expression of GFPT2 significantly delayed c-Myc degradation in CHX-treated T24 bladder cancer cells, indicating an extended half-life of c-Myc. (B) Western blot analysis revealed that MG132 treatment effectively stabilized c-Myc protein expression in T24 bladder cancer cells, whereas BafA1 had no apparent effect. These results suggest that c-Myc is predominantly degraded through the proteasome-dependent pathway. (C) IP and Western blot analysis of c-Myc O-GlcNAcylation and ubiquitination. (D) Western blot analysis of c-Myc O-GlcNAcylation and ubiquitination after OSMI-1 treatment. (E–G) Colony formation, wound-healing, and Transwell migration assays in GFPT2-overexpressing bladder cancer cells treated with 10058-F4


### In vivo validation of the GFPT2/O-GlcNAcylation/c-Myc axis
  To confirm the role of the GFPT2/O-GlcNAcylation/c-Myc axis, we established subcutaneous tumour and lung metastasis models in nude mice. The results revealed that the c-Myc inhibitor 10058-F4 inhibited tumor progression (Fig. 9A–D). Immunohistochemical analysis of subcutaneous tumours revealed that GFPT2 overexpression increased OGT and c-Myc expression, whereas 10058-F4 treatment markedly reduced c-Myc expression (Fig. 9E). In the lung metastasis model, GFPT2 overexpression enhanced tumour cell migration, which was reversed by 10058-F4 treatment (Fig. 9F). These results validate the role of the GFPT2/O-GlcNAcylation/c-Myc axis in bladder cancer progression. Further investigations into specific inhibitors targeting this signalling axis are warranted.

  Fig. 9In vivo validation of the GFPT2/O-GlcNAcylation/c-Myc axis. (A) Subcutaneous tumour formation and treatment with 10058-F4. (B) Gross image of the tumour. (C, D) Tumour volume and weight measurements. (E) IHC analysis of GFPT2, OGT, c-Myc, and Ki67 expression in subcutaneous xenograft tumours from nude mice. (F) Assessment of lung metastases in a nude mouse experimental metastasis model


## Discussion
  Metabolic reprogramming related to bladder cancer has attracted significant attention in recent years. Through metabolic gene perturbation network analysis, we identified GFPT2 as an MRPG for bladder cancer. By integrating data from public databases, clinical cohorts, cell experiments, and animal studies, we confirmed the oncogenic role of GFPT2 and the potential of its expression as a prognostic marker. Our experiments also revealed that the GFPT2/O-GlcNAcylation/c-Myc axis promotes bladder cancer cell proliferation and migration (Fig. 10). These findings support the clinical application of GFPT2 expression as a prognostic marker for postsurgical bladder cancer patients.

  Fig. 10Molecular mechanism through which activation of the GFPT2/O-GlcNAcylation/c-Myc axis promotes the progression of bladder cancer (created with BioGDP.com [25])

  To date, a unified consensus on the molecular classification of bladder cancer has not been established. Recent studies have revealed multiple molecular subtypes of bladder cancer, highlighting its significant molecular heterogeneity and the complexity of its underlying mechanisms [26–28]. This diversity suggests that bladder cancer is not a single disease, but rather a collection of distinct molecular entities with unique biological behaviours and responses to treatment. Understanding these subtypes is crucial for improving diagnostic accuracy and tailoring therapeutic strategies to the individual molecular profiles of patients. In our study, we classified bladder cancer into six subtypes using the metabolic perturbation network classification algorithm. We found that the C3 subtype had the best prognosis, while the C6 subtype had the worst prognosis. GSVA revealed significant differences between the C3 and C6 subtypes in terms of pathways such as glucose metabolism, amino acid metabolism, and nucleotide metabolism. Notably, the C6 subtype was more active related to the glucose metabolism pathway, suggesting that tumor metabolism is closely linked to prognosis. GFPT2 expression is associated with poor prognosis in patients with various tumours [9, 29–31]. However, its relationship with the clinical prognosis of bladder cancer patients has not previously been reported. Our data show that GFPT2 expression is increased in bladder cancer tissues compared to normal tissues, and high GFPT2 expression is associated with poor postoperative outcomes. These findings suggest that GFPT2 expression may serve as a potential biomarker for predicting prognosis in bladder cancer patients.

  Studies have shown that O-GlcNAcylation promotes proliferation, angiogenesis, and metastasis in bladder cancer cells. OGT inhibition reduces tumour cell O-GlcNAc levels and suppresses the malignant phenotype of bladder cancer [7, 10]. However, the interplay between GFPT2 and the regulation of O-GlcNAcylation and OGT expression in bladder cancer remains incompletely understood. Our findings indicate that GFPT2 significantly promotes both the proliferation and migration of bladder cancer cells. Furthermore, we observed a strong correlation between GFPT2 and OGT expression and O-GlcNAcylation levels in these cells. The precise molecular mechanisms underlying the GFPT2-mediated regulation of O-GlcNAcylation in bladder cancer warrant further investigation to fully elucidate its potential as a therapeutic target.

  Previous studies have demonstrated that c-Myc stability is regulated by ubiquitination [32, 33]. However, the role of O-GlcNAcylation in modulating c-Myc degradation through the ubiquitin-mediated pathway in bladder cancer cells remains unclear. Both O-GlcNAcylation and ubiquitination are known to affect target proteins, with O-GlcNAcylation enhancing protein stability by inhibiting ubiquitin-dependent degradation [34]. Our results indicated that c-Myc was primarily degraded via the ubiquitin–proteasome pathway. Subsequent experiments demonstrated that the GFPT2-mediated O-GlcNAcylation of c-Myc inhibited its ubiquitination, thereby increasing c-Myc stability and promoting malignant progression of bladder cancer. These findings reveal that activation of the GFPT2/O-GlcNAcylation/c-Myc signalling axis may be associated with poor prognosis in patients with bladder cancer. Although the results of these experiments provided important evidence, future multicentre clinical cohort studies are needed to validate the clinical significance of these conclusions.

  Although this study successfully integrated multiple bladder cancer cohorts for external validation, the clinical cohort from a single centre remains relatively small. To strengthen the findings, we plan to expand the clinical sample size and incorporate multi-centre, real-world cohort studies, thereby providing further validation of GFPT2 expression as a potential prognostic biomarker for bladder cancer. Additionally, our study did not fully explore the roles of cell metabolism, epigenetic regulation, and phosphorylation in modulating O-GlcNAcylation in bladder cancer cells. These areas represent promising avenues for future research and will be the focus of our ongoing investigations. Although we identified a GFPT2/O-GlcNAcylation/c-Myc axis in bladder cancer, whether GFPT2-derived metabolites influence other oncogenic transcription factors or epigenetic regulators remains to be determined. Environmental and endocrine-metabolic factors, which have been associated with urogenital disorders via systemic inflammation and metabolic dysregulation [35–39], may also modulate this axis and merit further study.


## Conclusion
  This study identifies GFPT2 as a potential prognostic marker for bladder cancer patients after surgery and demonstrates its role in promoting malignant progression through the O-GlcNAcylation of c-Myc. We elucidated the mechanism by which the GFPT2/O-GlcNAcylation/c-Myc axis drives bladder cancer cell proliferation and migration. These findings offer a potential strategy for improving postoperative prognosis in bladder cancer patients.


## Supplementary Information
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2

  Supplementary Material 3


## Acknowledgements
  Not applicable.