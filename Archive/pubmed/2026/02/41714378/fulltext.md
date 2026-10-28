# Machine learning-driven discovery of STAT1 and TRIM22 as immune biomarkers for lupus nephritis: translational insights into diagnosis and pathogenesis


## Supplementary Information
  The online version contains supplementary material available at 10.1038/s41598-026-41028-x.


## Introduction
  Systemic lupus erythematosus (SLE) is a complex autoimmune disease characterized by its multisystem involvement, posing significant challenges in clinical diagnosis and treatment1. The hallmark of SLE is an aberrant immune response targeting the body’s own tissues, leading to damage in organs such as the skin, joints, kidneys, and heart2. Among these, lupus nephritis (LN) stands out as one of the most common and severe manifestations of SLE3. Approximately 40–60% of SLE patients develop LN, and the disease’s prevalence and prognosis are closely linked, making LN a major contributor to morbidity, mortality, and the progression to end-stage renal disease4,5. While immunosuppressants and glucocorticoids have shown some success in controlling disease activity, the long-term prognosis for LN remains unsatisfactory, necessitating further research to improve diagnostic and therapeutic strategies6.

  The pathogenesis of LN is multifactorial, involving immune complex deposition, autoantibody production, and immune dysregulation7. Dysregulated B and T cell responses, along with an imbalance in both innate and adaptive immunity, are key drivers of renal damage in LN8. Moreover, there is substantial immune cell infiltration in the kidneys of LN patients, particularly the accumulation of T cells, B cells, and macrophages, which exacerbate structural kidney damage by releasing pro-inflammatory cytokines and promoting tissue inflammation9–11.

  Currently, the diagnosis of LN heavily relies on renal biopsy, a method that is invasive and impractical for repeated sampling12. Although recent studies have explored non-invasive diagnostic approaches through the detection of serum and urinary biomarkers, none have yet been validated with sufficient sensitivity and specificity for clinical use13,14. Additionally, existing treatment regimens are limited by the severe side effects of long-term immunosuppressant and glucocorticoid use, with some patients experiencing resistance or relapse15. Therefore, novel diagnostic and therapeutic strategies, particularly those based on molecular mechanisms of immune regulation, are urgently needed.

  In recent years, advances in bioinformatics and high-throughput sequencing technologies have facilitated a deeper understanding of the molecular mechanisms underlying LN16. By integrating gene expression profiles and multi-omics data, researchers have identified differentially expressed genes (DEGs) closely associated with LN pathogenesis, particularly immune-related key genes17. These immune-related genes (IRGs) hold promise for early diagnosis and personalized therapy in LN18.

  The aim of this study is to use bioinformatics approaches to identify differentially expressed IRGs in LN patients by leveraging multi-omics data and to apply machine learning techniques to screen for potential key genes. By further analyzing the relationship between these genes and immune cell infiltration in LN, we hope to elucidate their potential applications in LN diagnosis and treatment.


## Materials and methods

### Data acquisition
  The research flow diagram is presented in Fig. 1. Three datasets related to LN, including clinical characteristics and gene expression profiles, were obtained from the Gene Expression Omnibus (GEO) database (http://www.ncbi.nlm.nih.gov/geo/). The GSE72326 dataset consisted of 20 normal and 24 LN blood samples. The GSE99967 dataset included 29 LN and 17 normal blood samples19. These two datasets were combined after batch correction using the “sva” package to generate the training set20. The GSE81622 dataset, comprising 25 normal and 15 LN blood samples, was utilized for validation21. A total of 2,483 IRGs were retrieved from the ImmPort database (https://www.immport.org/home)22 and included in Supplementary Table 1.

  Fig. 1The flow diagram of the research design.


### Differential expression and WGCNA
  Differentially expressed genes (DEGs) between LN and control samples were identified using the “limma” R package with the criteria |Log2FC| > 0.585 and FDR < 0.05. Weighted gene co-expression network analysis (WGCNA) was performed using the “WGCNA” package23. Sample clustering was conducted via hierarchical clustering, excluding outliers with clustering height > 70. The optimal soft-thresholding power was chosen to achieve scale-free topology. Modules were identified using the dynamic tree-cutting algorithm (minimum module size = 50) and merged if correlation > 0.25. Modules significantly associated with LN (|correlation| >0.4, p < 0.05) were defined as key modules.


### Identification of Immune-Related DEGs
  Immune-related DEGs (IR-DEGs) were defined as the intersection of DEGs, key module genes, and IRGs. Venn diagrams were used for visualization.


### Machine learning for biomarker identification
  Five machine learning algorithms—LASSO (glmnet)24, Random Forest (randomForest)25, Support Vector Machine (SVM, e1071)26, Extreme Gradient Boosting (XGBoost, xgboost)27, and Boruta (Boruta)28—were applied to identify signature genes. Genes consistently selected across all methods were considered potential diagnostic biomarkers.


### Diagnostic performance evaluation
  Receiver operating characteristic (ROC) curves were generated using the “pROC” package to evaluate the diagnostic performance of candidate biomarkers29. Biomarkers with high AUC values in both the training and validation sets were considered key LN diagnostic genes. A diagnostic nomogram based on these biomarkers was constructed using the “rms” package and assessed by calibration plots and ROC curves30.

  To ensure the generalizability of the diagnostic tool and address potential overfitting, a leave-dataset-out validation was conducted as a sensitivity analysis. This step specifically focused on the simplified two-gene signature (STAT1 and TRIM22), which was prioritized due to its superior consistency across multiple machine learning algorithms. The cross-validation involved training the model on one cohort and testing it on an independent cohort to verify the stability of the diagnostic signature across different datasets.


### Gene set enrichment and immune infiltration analysis
  Gene set enrichment analysis (GSEA) was conducted with the “clusterProfiler” package to identify immune-related KEGG pathways associated with key biomarkers (p.adjust < 0.05). Principal component analysis (PCA) was applied to visualize clustering of samples. Immune cell infiltration was evaluated using single-sample GSEA (ssGSEA) via the “GSVA” package based on a predefined immune cell marker gene set. Heatmaps and boxplots were generated with “pheatmap” and “ggpubr”. Spearman correlation analyses between candidate biomarkers (CD40LG, RETN, TRIM22, STAT1) and immune cell types were performed using the “psych” package with FDR correction.


### Construction of tf-gene regulatory network
  Transcription factors (TFs) associated with CD40LG, RETN, TRIM22, and STAT1 were predicted using the NetworkAnalyst platform. Experimentally validated TF binding profiles from the JASPAR database were used to construct TF-gene interactions, which were visualized using Cytoscape (version 3.10.2).


### Clinical characteristics and sample collection
  A total of 13 patients with LN and 10 age- and sex-matched healthy controls (HCs) were recruited from Longyan First Hospital (Fujian, China) under ethical approval (No. LYREC2024-k172-01) with written informed consent. LN diagnosis was established according to the International Society of Nephrology/Renal Pathology Society (ISN/RPS) criteria. Patients with malignancy, active infection, or other autoimmune diseases (e.g., rheumatoid arthritis or systemic sclerosis) were excluded. Clinical and laboratory data, including age, sex, renal SLEDAI, serum creatinine, eGFR, 24-hour urine protein, hematuria, urinary casts, urine white blood cell count, anti-dsDNA, complement C3/C4 levels, ongoing treatment, and renal biopsy classification, were obtained from electronic medical records at the time of sampling.

  Peripheral blood samples were collected from all participants into EDTA tubes, immediately mixed with TRIzol®-like reagent (CWBIO, CW0580S, China) at a 1:3 (v/v) ratio, flash-frozen in liquid nitrogen, and stored at − 80 °C until RNA extraction.


### RNA Extraction and qRT-PCR
  Total RNA was extracted from PBMCs using TRIzol-chloroform combined with UltraPure RNA column purification (CWBIO, CW0581M, China). RNA purity and integrity were assessed with a NanoPhotometer NP80 (Implen, Germany; OD260/280: 1.8–2.2) and 1% agarose gel electrophoresis. Genomic DNA was removed using 4×gDNA Wiper Mix (HiScript II, Vazyme, R223-01, China). cDNA synthesis was performed using HiScript II SuperMix in a 20 µL reaction at 50 °C for 15 min, followed by heat inactivation at 85 °C for 5 s. qRT-PCR was performed on a CFX Connect™ system (Bio-Rad, USA) using SYBR Master Mix (CWBIO, CW3360M, China) with the following cycling conditions: 95 °C for 30 s, 40 cycles of 95 °C for 10 s, 58 °C for 30 s, 72 °C for 30 s, and a melt curve from 65 to 95 °C at 0.5 °C increments. To ensure analytical specificity, particularly for the 317 bp STAT1 amplicon, PCR products were strictly verified by the presence of a single peak in melt curve analysis and visualized via agarose gel electrophoresis to rule out non-specific amplification. β-actin was used as an internal control, and relative expression was calculated using the 2−ΔΔCt method (primers in Table 1).

  Table 1Primer sequences used for qRT-PCR.Primer nameSequence (5′–3′)Product size (bp)Annealing temperature (°C)β-actin FTGGCACCCAGCACAATGAA18658.0β-actin RCTAAGTCATAGTCCGCCTAGAAGCACD40LG FGAGCAACAACTTGGTAACCCT13458.0CD40LG RGGCTGGCTATAAATGGAGCTTGRETN FCTGTTGGTGTCTAGCAAGACC10458.0RETN RCCAATGCTGCTTATTGCCCTAAATRIM22 FCTGTCCTGTGTGTCAGACCAG10258.0TRIM22 RTGTGGGCTCATCTTGACCTCTSTAT1 FGTTTCATTTGCCACCATCCG31758.0STAT1 RCACATAACCTTGTCCTTCACATTTC


### Statistical analyses
  All statistical analyses were performed using R software (version 4.3.1) and GraphPad Prism 9.0 (GraphPad Software, USA). For bioinformatics data, differential expression was analyzed using empirical Bayes statistics (moderated t-tests) within the ‘limma’ package. For clinical validation data, given the relatively small sample size, continuous variables were compared using the non-parametric Mann-Whitney U test (Wilcoxon rank-sum test) to avoid assumptions of normality. Categorical variables were compared using Fisher’s exact test. Multiple group comparisons were assessed using the Kruskal–Wallis test. Associations between variables were evaluated using Spearman correlation analysis. ROC curves were generated to evaluate the diagnostic performance of candidate genes, and the AUC was calculated using logistic regression models. All statistical tests were two-tailed, and a P value < 0.05 was considered statistically significant.


## Results

### Identification of differentially expressed genes in LN
  According to PCA results, the merged data set (training set) has eliminated the batch effect (Supplementary Fig. 1 A, B). As shown in Figs. 2A, B, we obtained the 320 DEGs between normal and LN groups, including 61 down-regulated and 259 up-regulated genes (Supplementary Table 2).

  Fig. 2Identification of differentially expressed genes in LN. (A) Volcano plot of DEGs between LN and normal controls. (B) Heatmap showing the TOP50 DEGs.


### Identification of key module genes and IR-DEGs in LN
  To identify genes associated with LN, WGCNA was performed. Hierarchical clustering of samples identified one outlier, which was removed before network construction (Supplementary Fig. 2A–B). Several modules were significantly correlated with disease status (Fig. 3A–C). Integrative analysis combining DEGs, key module genes from WGCNA, and IRG from the ImmPort database identified a set of 53 IR-DEGs (Fig. 3D–E), which may represent promising candidates for further diagnostic and therapeutic investigation in LN.

  Fig. 3Identification of key module genes and IR-DEGs in LN. (A) Scale-free topology fit and mean connectivity for different soft-thresholding powers. (B) Hierarchical clustering dendrogram of genes. (C) Module–trait relationships. (D) Scatterplots of gene significance versus module membership. (E) Venn diagram showing the intersection of DEGs, WGCNA module genes, and immune-related genes.


### Construction and evaluation of the IR-DEGs signature for LN
  To further identify key immune-related genes in LN, multiple feature selection methods were applied to the 53 IR-DEGs. First, the Boruta algorithm was used to assess feature importance, confirming several key predictors, including CD40LG, RETN, TRIM22, and STAT1 (Fig. 4A–B). Next, SVM-RFE analysis was performed to select an optimal subset of genes (Fig. 4C), and LASSO regression provided a coefficient profile with cross-validation to identify candidate biomarkers associated with LN immune response (Fig. 4D–E). Additionally, Random Forest and XGBoost analyses ranked genes based on importance (Fig. 4F–G). By integrating results from all five methods, four characteristic hub genes—CD40LG, RETN, TRIM22, and STAT1—were identified as robust candidates for diagnostic and therapeutic exploration in LN (Fig. 4H).

  Fig. 4Screening immune-related biomarkers of LN. (A) Z-score variation during Boruta feature selection. (B) Boruta feature selection plot. (C) SVM-RFE analysis. (D) LASSO regression coefficient profiles. (E) Cross-validation of the LASSO model using 10-fold cross-validation. The dotted vertical lines represent the optimal λ value (minimum criteria) and the 1-standard error criteria. (F) Random Forest feature importance ranking. (G) XGBoost feature importance ranking. (H) Venn diagram showing overlapping genes identified by multiple machine learning methods.


### Diagnostic validation and predictive modeling of Hub IR-DEGs in LN
  The diagnostic potential of the four hub IR-DEGs—STAT1, RETN, CD40LG, and TRIM22—was first evaluated individually in the training cohort. Each gene demonstrated good discrimination between LN patients and healthy controls (Fig. 5A), and these findings were confirmed in an independent validation cohort (Fig. 5B). Comparative expression analysis showed consistent upregulation of these genes in LN across cohorts (Figs. 5C–D).

  Based on the training data, we initially constructed a preliminary four-gene nomogram (Supplementary Fig. 3) which showed high theoretical discrimination. However, to ensure the robustness of the diagnostic model for clinical application, we prioritized experimental validation to determine the final diagnostic panel.

  Fig. 5Diagnostic performance and expression validation of hub IR-DEGs in LN. (A, B) ROC curves of CD40LG, RETN, TRIM22, and STAT1 in the training and independent validation cohorts. (C, D) Expression patterns of these four genes in the training and validation cohorts. Statistical comparisons were performed using the Mann-Whitney U test (Wilcoxon rank-sum test). ns, not significant; * P < 0.05; ** P < 0.01; *** P < 0.001; **** P < 0.0001.


### Functional enrichment analysis of biomarkers in LN
  Single-gene GSEA indicated that the four hub biomarkers were significantly associated with immune-related and inflammatory pathways, including antigen presentation, complement and coagulation cascades, NK cell-mediated cytotoxicity, T cell receptor signaling, and graft-versus-host and autoimmune responses (Fig. 6A–D). These results suggest that these genes play pivotal roles in immune regulation and inflammatory processes in LN.

  Fig. 6Functional enrichment analysis of LN-associated biomarkers.


### The Role of CD40LG, RETN, TRIM22, and STAT1 in the LN immune microenvironment
  PCA of CD40LG, RETN, TRIM22, and STAT1 expression profiles revealed three distinct clusters (Cluster 1–3), accounting for 79.7% of total variance (Dim1: 56.2%, Dim2: 23.5%), suggesting notable heterogeneity in LN pathogenesis (Fig. 7A). Immune deconvolution showed significant differences in the abundance of 17 out of 28 immune cell subsets across clusters (Fig. 7B–C). Cluster 1 was enriched in innate immune signatures, including neutrophils and macrophages, whereas Clusters 2 and 3 displayed adaptive immune-dominant profiles, with higher levels of effector memory CD8 + T cells and T follicular helper cells (Fig. 7C).

  Correlation analysis highlighted gene-specific immune interactions (Fig. 7D–E). CD40LG positively correlated with T follicular helper cells and effector memory CD8 + T cells, but negatively with neutrophils and macrophages. RETN was associated with activated dendritic cells and mast cells, TRIM22 with activated CD4 + T cells, and STAT1 showed mild correlation with natural killer (NK) cells. A Spearman correlation heatmap further visualized the strength and direction of these associations (Fig. 7E).

  Fig. 7Immune infiltration analysis of CD40LG, RETN, TRIM22, and STAT1 in LN. (A) PCA plot showing three clusters based on gene expression profiles. (B) Relative proportions of immune cell infiltration in LN samples. (C) Abundance of 28 immune cell types across clusters. (D) Correlation analysis between the four biomarkers and immune cell types. (E) Spearman correlation heatmap visualizing associations between biomarkers and immune cells. (Kruskal-Wallis test for panel C; Spearman correlation for panels D and E). ns, not significant; *P < 0.05, ** P < 0.01, *** P < 0.001.


### Transcription factor-gene regulatory network analysis in LN
  A transcription factor (TF)–gene regulatory network was constructed for the four hub genes (CD40LG, STAT1, RETN, and TRIM22) to explore potential upstream regulators (Fig. 8). Several TFs were predicted to interact with each hub gene, forming distinct regulatory connections. These predicted interactions suggest potential transcriptional regulation of the hub genes in LN. All results are based on computational prediction and require experimental validation.

  Fig. 8TF-gene regulatory network of four immune-related genes in LN.


### Clinical characteristics
  The baseline characteristics of the study cohort are summarized in Table 2. The LN group included 12 females and 1 male (mean age 38.7 ± 12.2 years), and the HC group comprised 9 females and 1 male (mean age 34.6 ± 11.4 years). There were no statistically significant differences in age or sex distribution between the two groups (P > 0.05). In LN patients, the mean renal SLEDAI was 7.69 ± 5.76. Laboratory values showed a mean serum creatinine of 66.2 ± 20.8 µmol/L and eGFR of 104.8 ± 23.3 mL/min/1.73 m². Clinical features included proteinuria > 0.5 g/24 h in 69.2% of patients, hematuria in 53.8%, urinary casts in 23.1%, and urine WBC > 5/HPF in 38.5%. Anti-dsDNA antibodies were positive in 61.5% of patients, and mean complement levels were C3 0.90 ± 0.17 g/L and C4 0.178 ± 0.041 g/L.

  Regarding treatment, all patients were receiving glucocorticoids (100%), and 53.8% were on immunosuppressants (primarily mycophenolate mofetil), while 23.1% were treated with biologics (belimumab). Renal biopsy revealed ISN/RPS classes III, IV, V, and mixed types.

  Table 2Baseline characteristics of LN patients and healthy controls.VariableLN (n = 13)HC (n = 10)DemographicsAge (years, mean ± SD)38.7 ± 12.234.6 ± 11.49/1 (90%/10%)Sex (female/male)12/1 (92.3%/7.7%) Clinical and Laboratory Data Renal SLEDAI7.69 ± 5.76——Serum creatinine (µmol/L)66.2 ± 20.8eGFR (mL/min/1.73 m²)104.8 ± 23.3——24 h urine protein > 0.5 g/24 h (positive)9 (69.2%)Hematuria (RBC > 5/HPF)7 (53.8%)——Urinary casts/cellular casts (positive)3 (23.1%)Urine WBC > 5/HPF (positive)5 (38.5%)—Anti-dsDNA (positive)8 (61.5%)C3 (g/L)0.90 ± 0.17—C4 (g/L)0.178 ± 0.041— Main treatment at sampling  Glucocorticoids 13 (100.0%)— Immunosuppressants Mycophenolate mofetil7 (53.8%)—Cyclophosphamide3 (23.1%)—Tacrolimus2 (15.4%)— Biologics Belimumab3 (23.1%)—Renal biopsy (ISN/RPS classification)III, IV, V, mixed types—Note: Continuous variables are expressed as mean ± standard deviation (SD), and categorical variables are expressed as frequency (percentage). There were no statistically significant differences in age (P = 0.456, Mann-Whitney U test) and sex distribution (P > 0.999, Fisher’s exact test) between the LN and HC groups.


### Validation of hub gene expression levels in LN
  qRT-PCR analysis was performed on peripheral blood samples from 13 LN patients and 10 healthy controls to validate the expression of candidate hub genes. STAT1 and TRIM22 were significantly upregulated in LN patients compared to controls (P = 0.0002 and P = 0.0003, respectively), while RETN and CD40LG showed no significant differences (P = 0.784 and P = 0.784, respectively) (Fig. 9A-D, Supplementary Table 3).

  To investigate whether clinical variables influenced STAT1 and TRIM22 expression, univariable linear regression and Spearman correlation analyses were performed, including eGFR, serological markers (C3, C4, anti-dsDNA), and disease activity indices (renal SLEDAI, 24-hour proteinuria, log-transformed). No significant associations were observed (all P > 0.05, see Supplementary Tables 4 and Supplementary Fig. 4). This lack of correlation suggests that clinical severity scores did not independently drive gene expression in this cohort, potentially due to the stabilizing effects of concurrent medication. These results indicate that STAT1 and TRIM22 serve as promising biomarkers for disease identification (diagnosis) even under treatment, whereas their utility for monitoring disease fluctuation appears limited in this context. Regarding RETN and CD40LG, their clinical relevance in peripheral blood warrants further investigation.

  Fig. 9Validation of hub gene expression levels in LN. (A–D) qRT-PCR analysis of STAT1, TRIM22, RETN, and CD40LG in peripheral blood from LN patients and healthy controls. Data are presented as median (IQR). Statistical comparisons between groups were performed using the Mann-Whitney U test. *** P < 0.001; ns, not significant.


### Construction and Clinical Validation of the Diagnostic Nomogram and Two-Gene Model
  To translate the identified hub genes into a clinically applicable diagnostic tool, we prioritized genes validated by qRT-PCR experiments. Based on these validation results, only STAT1 and TRIM22 showed significant upregulation in our clinical samples; therefore, these two experimentally confirmed genes were selected to construct the diagnostic model.

  Accordingly, we developed a diagnostic model based on the expression levels of STAT1 and TRIM22. A nomogram was first established using the training set to visualize the predicted probability of LN risk (Fig. 10A). ROC curve analysis in the training set demonstrated that the combined model based on STAT1 and TRIM22 exhibited high diagnostic accuracy (Fig. 10B).

  To verify the robustness and generalizability of the two-gene signature, we performed a “leave-dataset-out” cross-validation. The model was trained on one GEO cohort and tested on an independent GEO cohort, confirming stable diagnostic performance under cross-dataset conditions (Fig. 10C-D).

  Finally, the diagnostic efficacy of the signature was validated using the independent clinical qRT-PCR cohort. ROC curve analysis demonstrated strong diagnostic potential for STAT1 and TRIM22 individually, with AUCs of 0.923 and 0.915, respectively (Fig. 10E). Furthermore, a combined analysis integrating STAT1 and TRIM22 improved diagnostic performance to an AUC of 0.931 (Fig. 10F). These results suggest that a multi-gene panel provides superior sensitivity and specificity for LN detection compared to single biomarkers.

  Fig. 10Construction and validation of the diagnostic model for LN. (A) Diagnostic nomogram established in the training set based on STAT1 and TRIM22. (B) ROC curve analysis of the diagnostic performance of STAT1 and TRIM22 in the training set. (C–D) ROC curves of the two-gene model under leave-dataset-out cross-validation between independent GEO cohorts. (E) ROC curves of STAT1 and TRIM22 in the clinical validation cohort. (F) ROC curve of the combined model integrating STAT1 and TRIM22 in the clinical validation cohort. The nomogram was constructed using multivariate logistic regression analysis. Diagnostic performance was evaluated using ROC analysis and AUC calculations.


## Discussion

### Research innovation and key findings
  Integrating multi-cohort transcriptomics with machine learning, we identified STAT1 and TRIM22 as potential diagnostic biomarkers for LN based on peripheral blood mRNA expression. Upon validation in our clinical cohort, a notable observation was the divergence between their diagnostic accuracy and monitoring utility in peripheral blood: while both genes effectively distinguished LN patients from healthy controls, they did not correlate with disease activity indices (Fig.S4). Rather than a simple lack of relevance, we hypothesize that this discrepancy may reflect a ‘therapeutic decoupling’ of the interferon signature. As documented by Landolt-Marticorena et al., molecular interferon signatures—which are fundamentally orchestrated by the STAT1 pathway—often remain persistently elevated and relatively stable over time, even when clinical symptoms exhibit marked improvement under treatment31–33. This persistence suggests that STAT1 and TRIM22 represent a constitutive molecular imprint of LN that remains detectable despite the suppressive effects of glucocorticoids and immunosuppressants on clinical scores. Thus, these biomarkers may be more reliable for identifying the intrinsic autoimmune pathology rather than monitoring transient clinical fluctuations in treated populations.

  Conversely, CD40LG and RETN were excluded from the final model as they did not reach statistical significance in our validation. This may be attributed to their biological characteristics and detection limitations. Specifically, CD40LG is transiently expressed in activated CD4⁺ T cells, and its signal may be diluted in whole-blood samples by non-expressing cell populations34–36. Similarly, while RETN protein levels are elevated in LN serum, its peripheral mRNA abundance is predominantly macrophage-derived and may be limited by tissue-specific expression or post-transcriptional regulation37. While integrated multi-cohort analyses could capture these variable signals, they were likely below the detection threshold in our smaller, steroid-treated cohort.


### STAT1 in LN pathogenesis
  STAT1 is a central mediator of type I and II interferon signaling in the JAK–STAT pathway and plays a key role in autoimmune immune dysregulation32. Transcriptomic and single-cell studies have consistently identified STAT1-centered inflammatory signatures in SLE and related autoimmune diseases33. In LN renal biopsies, STAT1 and its downstream chemokine CXCL10 are markedly upregulated and pharmacologically modulated38.

  In this study, STAT1 was significantly upregulated in LN peripheral blood and positively correlated with renal NK cell infiltration (Fig. 8D), suggesting interferon-driven amplification of renal inflammation. This finding aligns with animal studies showing sustained glomerular STAT1 activation promotes renal injury39,40. Moreover, STAT1 cooperates with RELA to enhance CXCL10 transcription, facilitating monocyte recruitment and exacerbating renal inflammation41–44. Together, these data highlight the STAT1–CXCL10 axis as a central pathway in LN pathogenesis.


### Immunoregulatory role of TRIM22 in LN
  TRIM22 is an interferon-inducible E3 ubiquitin ligase involved in innate immune and inflammatory regulation45. We observed significant upregulation of TRIM22 in LN peripheral blood, with positive correlations to CD4⁺ T-cell activation (Fig. 8D). Experimental studies indicate that TRIM22 enhances NF-κB signaling and that its suppression alleviates renal inflammation in lupus-prone mice via inhibition of the NF-κB/NLRP3 axis46.

  Consistently, GSEA showed that high STAT1 and TRIM22 expression was associated with enrichment of NOD-like receptor and T-cell receptor signaling pathways, both of which converge on NF-κB activation47–49. NF-κB is a central regulator of pro-inflammatory cytokines, including TNF-α, IL-6, and MCP-150,51. These findings suggest that STAT1 and TRIM22 may cooperatively amplify NF-κB-mediated inflammatory responses, promoting immune cell infiltration and renal injury in LN.


### Clinical implications
  Current LN management relies on glucocorticoids and broad immunosuppression, with limited precision and substantial adverse effects52. While biologics such as belimumab improve outcomes in some patients, overall efficacy remains variable53. Traditional serological markers, including anti-dsDNA antibodies, show only moderate diagnostic performance for LN, with reported AUCs generally ranging from 0.6 to 0.854,55.

  In contrast, the diagnostic model based on STAT1 and TRIM22 demonstrated favorable accuracy in distinguishing LN patients from healthy controls within our validation cohort. We acknowledge that distinguishing LN from healthy individuals does not fully reflect the complex differential diagnosis faced by clinicians (e.g., distinguishing LN from other nephropathies). However, the robustness of this two-gene signature in treated patients suggests a specific utility: it may serve as a complementary, non-invasive tool to confirm the presence of an underlying interferon-driven autoimmune pathology when biopsy is contraindicated or inconclusive, rather than a standalone replacement for renal biopsy, pending further large-scale validation.


## Limitations
  Several limitations warrant mention. First, regarding the clinical cohort, the sample size was relatively small, and the majority of patients were receiving immunosuppressive therapy at the time of sampling. We acknowledge this as a potential confounding factor, as these medications may influence gene expression profiles. While this treatment background provides a potential explanation for the observed ‘therapeutic decoupling’ effect, it may limit the generalizability of our findings to treatment-naive populations. Furthermore, our study primarily compared LN patients with healthy controls. To fully address the clinical diagnostic dilemma, future large-scale studies including disease controls (e.g., patients with non-lupus glomerular diseases or SLE without nephritis) are necessary to rigorously validate the specificity of STAT1 and TRIM22 in a broader differential diagnosis context. Second, regarding experimental verification, since samples were not stored in a manner that preserved protein content, it was not possible to assess the protein-level consistency of STAT1 and TRIM22. We also note the methodological consideration regarding the 317 bp STAT1 amplicon; however, specificity was verified via melt curve analysis and agarose gel electrophoresis. Finally, the proposed mechanistic links are inferred primarily from bioinformatic analyses; future studies incorporating in vitro or in vivo interventions are warranted to experimentally validate these pathways.


## Conclusion
  In conclusion, we identified and characterized the immune-related hub genes STAT1 and TRIM22 in LN using transcriptomic data and machine learning. Both genes were significantly upregulated in peripheral blood and correlated with immune cell infiltration and inflammatory pathways. These biomarkers show promise as non-invasive molecular signatures for identifying underlying disease status. Building upon the insights and limitations of this exploratory study, further large-scale research is warranted to confirm their clinical utility and experimentally validate the proposed pathogenic mechanisms in LN.


## Supplementary Information
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2

  Supplementary Material 3

  Supplementary Material 4

  Supplementary Material 5

  Supplementary Material 6

  Supplementary Material 7

  Supplementary Material 8

  Supplementary Material 9

  Supplementary Material 10


## Acknowledgements
  The authors thank all participants of the study. ChatGPT (OpenAI) was used solely to assist with language refinement and formatting during manuscript preparation. All intellectual content, data analysis, and interpretation were conducted independently by the authors.