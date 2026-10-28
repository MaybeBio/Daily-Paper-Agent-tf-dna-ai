# Unveiling the role of EGR1 and hub senescence-related genes in type II alveolar epithelial cells senescence for obstructive sleep apnea


## Background
  Obstructive sleep apnea (OSA) is a prevalent respiratory condition that predominantly occurs during sleep and is marked by complete or partial obstruction of the upper airway. Aging represents a significant risk factor for OSA, and the biomolecular mechanisms linking aging to OSA remain incompletely elucidated.


## Methods
  This research integrates bioinformatics and machine learning methods. Furthermore, potential biomarkers were subjected to further screening and validation through machine learning algorithmsithms, providing molecular insights for the diagnosis and treatment of OSA. Finally, we validated the expression of the hub SRG Early growth response factor-1 (EGR1) by sc-RNA-seq analysis and explored the underlying mechanism of EGR1 in AT2 and mouse cellular senescence.


## Results
  Studies have identified differentially expressed genes and gene co-expression modules that are significantly associated with Obstructive Sleep Apnea (OSA). These modules are found to be closely linked to aging processes and immune responses, as evidenced by the integration of differential co-expression and differential expression analyses in cancer research. Functional enrichment analysis showed that these genes participate in various biological processes, such as inflammatory responses and immune cell signaling pathways. Furthermore, EGR1, a critical gene validated experimentally, has been shown to play a pivotal role in cellular senescence, immune regulation, and DNA damage response, as evidenced by its cellular localization and expression patterns under various physiological and pathological conditions.


## Conclusion
  Recent studies have highlighted the pivotal role of aging-related genes, particularly EGR1, in the development of obstructive sleep apnea (OSA). The evidence suggests that EGR1 may be a viable therapeutic target, as seen in its potential application in treating fibrotic kidney disease, as well as its involvement in tumor gene-radiation therapy. These discoveries offer a scientific foundation for the development of personalized treatment strategies targeted at specific patient groups, potentially enhancing diagnostic and therapeutic outcomes for OSA patients.


## Clinical trial number
  Not applicable.


## Supplementary Information
  The online version contains supplementary material available at 10.1186/s12896-025-01067-0.


## Introduction
  Obstructive sleep apnea (OSA) is a prevalent sleep-related respiratory disorder characterized by recurrent episodes of complete or partial upper airway obstruction during sleep, resulting in substantial decreases in blood oxygen saturation and frequent sleep disruptions [1]. The prevalence of OSA increases with advancing age and is higher among individuals with a higher body mass index. Patients with OSA experience a range of symptoms that accompanied by various neuropsychiatric manifestations, such as impaired concentration, memory deficits, and mood disturbances, which are associated with sleep fragmentation and intermittent hypoxemia [2]. Chronic, untreated OSA results in diminished neurocognitive performance and reduced overall life expectancy, highlighting the critical need for timely diagnosis and effective therapeutic interventions to mitigate these adverse outcomes [3].

  Aging is a critical risk factor for OSA [4, 5]. The interconnection between aging and OSA is particularly significant, especially as the global population structure shifts toward an aging demographic. Aging is a complex biological process characterized by a progressive decline in cellular and physiological functions, thereby increasing susceptibility to diseases [6, 7]. Biomarkers such as telomere attrition, inflammation, alterations in synthesis pathways, and hormonal dysregulation are central to the aging process. These factors not only contribute to typical aging phenotypes but also influence diverse pathophysiological pathways. With regard to sleep and respiratory functions, aging is associated with increased neck fat accumulation, decreased airway muscle tone, and alterations in lung and chest wall mechanics, all of which contribute to a higher prevalence of OSA in older individuals [8]. Furthermore, aging alters sleep architecture, diminishing deep sleep phases and increasing nocturnal awakenings—changes that may exacerbate the severity and clinical outcomes of OSA [9].

  The shared mechanisms between aging and obstructive sleep apnea (OSA) include systemic inflammation, oxidative stress, and endothelial dysfunction. Aging affects OSA by increasing susceptibility to the hypoxic challenges associated with OSA, due to a decline in physiological reserves linked to the aging process. Furthermore, aging influences the neural regulation of upper airway muscles and respiratory drive during sleep, which may exacerbate OSA severity or complicate the management of the condition in elderly patients [10]. Although the interactions between aging and OSA are increasingly recognized, the precise mechanisms by which aging contributes to the onset of OSA remain incompletely understood. The complex interplay of age-related degenerative changes plays a significant role in the development and progression of OSA, highlighting the need for further research to fully elucidate these mechanisms and inform the development of effective interventions [11, 12].

  Bioinformatics is a multidisciplinary and interdisciplinary field. Recently, advancements in high-throughput sequencing and the application of machine learning in medicine have opened new avenues for exploring the molecular mechanisms of various diseases [13, 14]. The Weighted gene co-expression network analysis (WGCNA) method was used to construct a gene co-expression network to identify hub OSA-related genes. Single-sample gene set enrichment analysis (ssGSEA) was used to assess differences in immune cell infiltration in OSA patients, and Gene set variation analysis (GSVA analysis) was used to compare functional and pathway differences between different OSA subtypes, further revealing the molecular heterogeneity of OSA. In the field of machine learning, we utilized algorithms such as Least Absolute Shrinkage and Selection Operator (LASSO) and Random Forest for feature selection and model building. Ultimately, key discoveries from bioinformatics analyses were validated in the laboratory through experimental validation steps. By applying these methods, this study comprehensively revealed the molecular mechanisms of aging-related OSA, providing potential biomarkers and therapeutic targets for the diagnosis and treatment of OSA.


## Materials and methods

### Data collection and preprocessing
  This study utilized the OSA gene expression profile database, including GSE135917 [15] GSE38792 [16], and GSE75097 [17]. The datasets GSE135917 and GSE38792 are based on the GPL6244 (Affymetrix Human Gene 1.0 ST Array), whereas GSE75097 uses the GPL10904 (Illumina HumanHT-12 V4.0 expression beadchip) platform, with the information shown in Fig. 1. Studies have shown that continuous positive airway pressure (CPAP) can alter the expression profiles of OSA patients [18, 19], even restoring them to their initial levels prior to treatment. Thus, to prevent the transcriptomes of patients treated with CPAP from affecting the characteristic changes closely associated with the onset and progression of OSA. To mitigate batch effects and maintain sample uniformity, the “remove Batch Effect” function from the limma package (version 3.48.3) was utilized. GSE75097 utilizes the GPL10904 (Illumina HumanHT-12 V4.0 expression beadchip) platform. During the analysis, the “neqc” function of the limma package was used for background correction and normalization.

  Fig. 1Flowchart of the comprehensive analysis of aging-related genes in OSA


### Differential gene expression analysis involves several critical steps to ensure accurate and reliable results
  These include data preprocessing to remove low-quality data and handle missing values, normalization to make different samples comparable, and statistical testing using methods like t-tests and ANOVA to identify significantly differentially expressed genes.

  To identify differentially DEGs between OSA patients and controls, this study utilized the R package “limma” [20] for analysis. The merged expression data, with |logFC| > 0.58 and FDR < 0.05 as thresholds, identified OSA-related differentially expressed genes (OSA-DEGs) and generated volcano plots and heat maps.The differential expression analysis results were displayed using the R packages “ComplexHeatmap” (version 2.8.0) and “ggplot2” [21] (version 3.3.5).


### Weighted gene co-expression network
  Weighted Gene Co-Expression Network Analysis (WGCNA) is a method used to reveal gene co-expression modules, explore the relationships between gene modules and external clinical traits, and identify key genes in diseases.The R package WGCNA [14] is used to construct a weighted co-expression network based on the training set, analyzing the top 25% of genes with the highest expression variance across all expression profiles.


### Functional enrichment analysis
  To investigate the potential biological functions of genes specific to OSA, we utilized the “clusterProfiler " [23]package (version 4.0.5) in R for Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) analysis.The threshold was set at an adjusted p-value (adj. p-value) < 0.05, applying the Benjamini-Hochberg correction. Enriched GO terms, including Biological Processes (BP), Cellular Components (CC), and Molecular Functions (MF), were visualized using dotplot diagrams.Additionally, enriched KEGG pathways were displayed using the “pathview” [22]package (version 1.32.0).


### Download and organization of aging-related genes
  Based on previous research [23], human aging-related genes (ARGs), including GenAge (307) and CellAge (279), were obtained from the Human Aging Genomic Resources (HAGR, https://genomics.senescence.info/) database [24]. After merging and deleting duplicate genes, 543 ARGs were obtained for subsequent analysis.


### Evaluation of immune infiltration in OSA patients
  Single-sample Gene Set Enrichment Analysis (ssGSEA) was used to assess the immune cell infiltration in lungs of OSA patients and healthy controls.


### Unsupervised clustering analysis and gene set variation analysis
  This study uses the “ConsensusClusterPlus“ [25] R package for unsupervised clustering analysis, employing the k-means method run 1000 times with the maximum number of subtypes set to k = 6.Optimal subtype numbers are established using cumulative distribution function curves, consensus matrices, and consensus clustering scores.The “GSVA” R package is employed to conduct Gene Set Variation Analysis (GSVA) and immune infiltration analysis, evaluating the differences in enriched functions and pathways across subtypes.Gene sets like c2.cp.kegg.v7.4 and go.bp.v7.5.1, from the “symbols” category of the MSigDB database, serve as input files. Functions and pathways with GSVA scores t > 2 are considered significantly enriched.


### Feature selection, modeling, and validation
  The Least Absolute Shrinkage and Selection Operator (LASSO) is a widely used machine learning method for feature selection, often used in predictive analytics. By applying a penalty to the variables in the regression model, coefficients of non-important variables can be reduced to zero, thus excluding them from the model. Random Forest is an ensemble learning algorithm with good robustness against noisy data, significantly enhancing the model’s predictive accuracy through the combined predictions of multiple decision trees.The aforementioned machine learning methods are implemented using the R packages “glmnet “ [26] (version 4.1-2) and “randomForest” (version 4.6–14).We randomly divided the merged samples into a training set (80%) and a validation set (20%), retaining features with non-zero coefficients in the LASSO algorithm to generate a Random Forest predictive feature signature. We evaluated the predictive performance of the signature using 10-fold cross-validation. The Receiver Operating Characteristic (ROC) curve was plotted and the Area Under the Curve (AUC) was calculated to assess predictive accuracy using the R package “pROC” (version 1.18.0).


### Using machine learning (ML) models to identify characteristic biomarkers
  Machine Learning (ML) is a branch of artificial intelligence focused on developing algorithms and models that enable computer systems to learn from data and make predictions or decisions without explicit programming.This process involves creating mathematical models that can improve accuracy by continually learning and adjusting.The study randomly divides the samples into a training set (70%) and a test set (30%). Subsequently, using six different machine learning models, namely AdaBoost, Decision Tree, KNN, LightGBM, Naïve Bayes, and XGBoost, with gene data as input variables. Through 10-fold cross-validation and grid search to identify the optimal hyperparameter set for each model.Calculating and comparing several metrics in the test set, including accuracy, F1 score, Matthews correlation coefficient (MCC), true positives, true negatives, false positives, and false negatives, to assess the performance of machine learning models. Additionally, calculating the Area Under the Curve (AUC) of the Receiver Operating Characteristic (ROC) curve to assess the ability of OSA-related differentially expressed genes (OSA-ARDEGs) in distinguishing between healthy controls and OSA patients. AdaBoost, DT, and KNN models implemented through the R package “caret”, LightGBM through the R packages “LightGBM” and “tidymodels”, XGBoost through the R package “XGBoost”. Finally, Naïve Bayes implemented through the R package “e1071”.Model interpretability analysis performed using the R package “DALEX”.


### Construction and evaluation of binary logistic regression (LR) model
  This study uses a binary logistic regression (LR) model to identify the correlation coefficients of OSA-ARDEGs. Calibration plots are generated using the RMS program.Decision Curve Analysis (DCA), Calibration Curve Analysis, and AUC values are used to evaluate the discriminative performance of the risk scores.The GSE75097 dataset from the GEO database serves as an external validation set, and an internal validation set is also used to evaluate the model’s generalization capacity and stability.


### Gene set enrichment analysis (GSEA)
  To delve deeper into the potential mechanisms of key genes EGR1 and GLB1 in OSA, this research carried out gene set enrichment analysis (GSEA) on critical OSA-related differentially expressed genes (OSA-ARDEGs). Pathway enrichment analysis of key genes is conducted using GSEA, identifying signaling pathways implicated in the development of OSA through GSEA.Sort according to the standardized enrichment score (NES), with a P-value < 0.05 and a corrected absolute enrichment score (| NES |) > 1 as the screening criteria.


### Gene set variation analysis (GSVA)
  GSVA is a non-parametric, unsupervised learning method.In contrast to GSEA, GSVA does not require predefined sample grouping but calculates enrichment scores for specific gene sets in each sample directly.The fundamental concept of GSVA is to transform gene expression data from an expression matrix of individual genes to one featured by gene sets.Annotation libraries are imported into R, gene sets are defined based on GO and KEGG database annotations, and GSVA analysis is conducted using the R package GSVA, based on gene expression profiles from transcriptome sequencing.


### Experimental verification

#### Cell culture
  The pulmonary epithelial cell line AT2,beas-2b, MRC-5were procured from Fudan University’s Zhongshan Hospital in Shanghai, China. For the experiments, we used Dulbecco’s modified Eagle medium (DMEM, HyClone, USA), which was combined with 10% fetal bovine serum (FBS) and 1% penicillin/streptomycin (HyClone, USA) as additives. The cells were cultivated in an incubator with a 5% CO2 concentration at a temperature of 37 °C in a humidified setting.


#### Extraction of total protein
  When AT2, BEAS-2B, and MRC-5 cells reached 80–90% confluence, they were collected for protein extraction. Cells were lysed using RIPA lysis buffer (Cell Signaling Technology, Jiangsu, China) on ice for 30 min. Afterward, cells were scraped using a cell scraper and transferred into a new centrifuge tube to obtain the total protein solution. The sample was sonicated for 10 s, followed by centrifugation at 12,000 rpm for 15 min at 4 °C. The supernatant was collected for further analysis.


#### WB assay
  Total protein was extracted from cells or tissues using RIPA lysis buffer (Cell Signaling Technology, Jiangsu, China). WB assays were performed according to the guidelines provided by Abcam (https://www.abcam.cn/protocols/general-western-blot-protocol-2,accessed on 10 September 2021) utilizing a Bio-Rad gel analysis system (Bio-Rad, Hercules, CA, USA).WB bands were quantified using the ImageJ software(NIH, Bethesda, MD, USA). Supplementary Table S1 contained the listed commercial antibodies.


#### Reverse transcription-quantitative polymerase chain reaction (RT-qPCR) of mRNA
  With the TRIzol reagent (Thermo Fisher Scientific, Waltham, MA, USA), total RNA was extracted according to the recommended procedure by Abcam (https://www.abcam.cn/protocols/rna-isolation-protocol-cells-in-culture, accessed on 10 September 2021). Reverse transcriptions were performed in the subsequent.

  procedures utilizing a Takara reverse kit (Takara, Kusatsu, Shiga, Japan). The Bimake SYBR Green qPCR master mix (Houston, TX, USA) was used for RT-qPCR on a Bio-Rad CFX connect real-time PCR detection system (Hercules, CA, USA). The Ct values of target genes were normalized to ACTB in the same sample, and gene expression analysis was performed using the 2-ΔΔCt method. Supplementary Table S1 contains the primers sequences for all genes.


#### Measurement of cell apoptosis
  Apoptosis of AT2 cells was analyzed by flow cytometry. AT2 cells were collected by digestion with trypsin without EDTA. Subsequently, cells were washed twice with PBS (1,000 rpm, 5 min of centrifugation), and 1 × 10⁵ to 5 × 10⁵ cells were collected. 5 µL of Annexin V-FITC reagent was added, followed by 5 µL of Propidium Iodide (PI). The mixture was gently mixed and incubated in the dark at room temperature for 5–15 min. After incubation, apoptosis was immediately analyzed using a flow cytometer (ACEA NovoCyte, USA) to determine the apoptosis rate.


#### SA β-galactosidase assay
  To assess cellular senescence, cells were first washed once with PBS and then fixed with 1 mL of SA β-galactosidase staining fixative at room temperature for 15 min. After fixation, cells were washed again with PBS and stained with the staining solution. The cells were then incubated overnight at 37 °C in a non-CO₂ incubator. Following staining, the cells were observed under an optical microscope (Olympus, CKX31, Japan). The number of senescent cells was calculated by randomly selecting stained fields and counting the number of senescent cells per 100 cells.


#### γ-H2AX assay
  The harvested HEI-OC1 cells were subjected to immunofluorescence staining. First, the culture medium was aspirated from the 6-well plate, and the cells were washed once with PBS. Next, rabbit monoclonal antibody against γ-H2AX was added, and the cells were incubated at room temperature for 1 h. Afterward, DAPI staining solution was added to stain the cell nuclei at room temperature for 5 min. Upon completion of staining, an appropriate amount of anti-fluorescence quenching mounting solution was added to the 6-well plate, and coverslips were placed to mount the cells. Finally, the cells were observed using a fluorescence microscope. γ-H2AX labeling was visualized as green fluorescence, while the cell nuclei were stained blue by DAPI.


#### Enzyme-linked immunosorbent assay (ELISA)
  Enzyme-linked immunosorbent assay (ELISA) was used to detect molecules in the supernatant of AT2 cells. After 48 h of transfection, the cell supernatant was collected and centrifuged to remove cell debris. The supernatant was then used for ELISA. The levels of IL-6, IL-17A, IL-1β, and TNF-α protein expression were measured using the following ELISA kits: IL-6 ELISA Kit (Byabscience Biotechnology, Nanjing, Jiangsu), IL-17A ELISA Kit (Byabscience Biotechnology, Nanjing, Jiangsu), IL-1β ELISA Kit (Byabscience Biotechnology, Nanjing, Jiangsu), and TNF-α ELISA Kit (Byabscience Biotechnology, Nanjing, Jiangsu).


#### Telomere length measurement
  Genomic DNA was extracted from AT2 cells, standardized, and measured using the Telomere Relative Length Detection Kit (Wing and Applied Biotechnology, Shanghai) according to the manufacturer’s instructions. The DNA purity was ensured to be between A260/A280 ≈ 1.8-2.0. Telomere length was measured following the original method described by Cawthon [27], which involves quantitative PCR using serially diluted standard DNA and a standard curve method [29]. Telomere relative length was detected using the SYBR Green signal channel. Finally, the relative fluorescence intensity of the sample was calculated to obtain the quantitative result of the telomere length.


#### Data analysis
  Statistical analysis was performed using R software (v4.2.3, https://www.r-project.org). Comparisons between two groups were made using the Wilcoxon rank-sum test, chi-square test, and Fisher’s exact test. Spearman correlation analysis was conducted using the R packages “ggpubr” and “stats.” A p-value of < 0.05 was considered statistically significant. For qPCR statistical analysis, data are presented as mean ± standard deviation from at least three independent experiments. The statistical significance of differences was assessed using an unpaired two-tailed Student’s t-test. (ns indicates no significance; * p < 0.05; ** p < 0.01; *** p < 0.001). A p-value of < 0.05 was considered statistically significant. Each experiment was repeated three times for statistical analysis.


## Results

### Differential expression analysis between controls and OSA patients
  Using |logFC| > 0.58 and FDR < 0.05 as selection criteria, we identified 94 DEDEGs between the control group and OSA patients.Volcano plots and heatmaps are shown in Fig. 2A and B.

  Fig. 2Volcano plots and heatmaps. (A) Volcano plot of differentially expressed genes (DEGs). Genes were filtered based on |logFC| >0.58 and FDR < 0.05. Downregulated genes in OSA are represented by green dots, while upregulated DEGs are highlighted in red. (B) Heatmap displaying the expression patterns of DEGs in healthy controls and OSA patients


### Identifying key modules in OSA
  The WGCNA analysis included 44 patients with OSA and 15 healthy controls. A scale-free co-expression network was built using a soft power parameter (β = 10), achieving a scale-free topology fit (R2 = 0.9), as illustrated in Fig. 3A. Hierarchical tree-based clustering detected 14 distinct modules, each comprising over 50 genes. These modules were then assessed for their linkages to OSA (Fig. 3C). Findings revealed that the green (r = 0.67, p = 6e − 9), magenta (r = 0.33, p = 0.01), and pink (r = 0.32, p = 0.01) modules displayed positive correlations with OSA. Conversely, the yellow (r = − 0.73, p = 3e − 11), red (r = − 0.44, p = 4e − 4), and tan (r = − 0.36, p = 0.005) modules showed inverse relationships. The green module, demonstrating the most significant linkage (r = 0.67) and harboring 334 genes, was prioritized for deeper investigation. A scatter plot (Fig. 3E) graphically represented the association between module connectivity and OSA-related trait relevance.

  Fig. 3WGCNA of differentially expressed genes. (A) Sample clustering dendrogram with clinical trait heatmap. (B) Determination of soft-thresholding power, with the red line indicating a scale-free topology fit (R² = 0.9). (C) Module-trait associations showing correlation coefficients (upper values) and statistical significance (lower values). (D) Gene module clustering dendrogram, with color-coded modules and grey representing unassigned genes. (E) Association of trait relevance with network connectivity in the green co-expression module


### Functional enrichment analysis of DEGs
  Cross-referencing 94 DEGs against the green module’s gene set yielded 21 OSA-associated DEDEGs (Fig. 4A). The biological roles of these overlapping genes were investigated via GO and KEGG pathway enrichment studies. GO analysis demonstrated marked enrichment in key biological pathways, including transcriptional regulation of microRNAs, control of neuronal apoptosis, and calcium signaling-mediated cellular responses. Cellular compartment evaluation underscored the relevance of distinct subcellular structures, such as lysosomal compartments and RNA polymerase II-containing transcriptional regulatory complexes (Fig. 4B). Molecular function analysis demonstrated significant interactions between RNA polymerase II transcription factors and SMAD protein binding. KEGG pathway enrichment revealed prominent involvement in immune-related signaling cascades, including IL-17 and TNF signaling pathways, along with rheumatoid arthritis pathogenesis (Fig. 4C 4D). Additionally, significant enrichment was observed in osteogenic differentiation pathways and infection-related mechanisms, particularly those associated with Kaposi’s sarcoma-associated herpesvirus and enteropathogenic Escherichia coli.

  Fig. 4Functional and molecular profiling of OSA-associated DEGs and pathway enrichment. (A) Venn diagram illustrating the overlap between co-expressed gene clusters and differentially expressed DEGs identified in OSA. (B) GO enrichment across BP, CC, and MF domains. A graphical bubble chart displays the five most enriched terms with statistical significance, where bubble diameter correlates with the quantity of overlapping genes (larger = greater enrichment), and a chromatic gradient indicates the degree of statistical confidence (darker shades = more stringent FDR-corrected p-values). (C) KEGG pathway analysis, with a bubble chart ranking the 20 most enriched pathways based on significance. (D) Network visualization of functional associations among enriched KEGG pathways


### Correlation between OSA-ARDEGs
  By cross-referencing 21 OSA-associated genes with genes linked to aging, we pinpointed 4 aging-associated OSA-linked genes (OSA-ARDEGs), as visualized in Fig. 5A. The relationships among OSA-ARDEGs were evaluated using Pearson correlation coefficients.High correlations were found between EGR1 and FOS (cor = 0.95), and JUN (cor = 0.93), as well as between JUN and FOS (cor = 0.95) (Fig. 5B). Figure 5C illustrates the chromosomal positions of the OSA-ARDEGs.

  Fig. 5Correlation analysis of OSA-ARDEGs. (A) Venn diagram depicting intersections of aging-associated genes and DEGs derived from the co-expression network. (B) Correlation matrix depicting the relationships among OSA-ARDEGs. (C) Chromosomal localization of the four identified OSA-ARDEGs


### Immune infiltration analysis
  To examine variations in the immunological landscape of OSA patients compared to healthy individuals, we evaluated the prevalence and functional activity of immune cell subsets across both cohorts (Fig. 6A). Differences in immune cell abundance between groups, along with interrelationships among 22 immune subtypes, are illustrated in Fig. 6B and C. Results revealed a marked rise in M1 macrophage levels among OSA subjects relative to controls. Conversely, OSA cases displayed decreased proportions of plasma cells, naïve CD4 + T lymphocytes and activated dendritic cells.

  Fig. 6Immune cell correlation analysis. (A) Heatmap visualization of 22 immune cell subtype distributions across OSA patients and healthy controls. (B) Correlation matrix of immune cell interactions, with blue and red gradients representing positive and negative associations, respectively, where color intensity reflects correlation strength. (C) Comparative box plot analysis of immune cell population distributions between OSA patients and controls, with statistical significance denoted as *p < 0.05 and **p < 0.01

  We then examined the relationships between infiltrative immune cells and four types of OSA-ARDEGs (Fig. 7). Immune infiltration analysis revealed that EGR1 exhibited notable associations with dendritic cell activation (r = 0.59) and regulatory T cell abundance (Tregs; r = − 0.44) (Fig. 7A), indicating a pivotal function in modulating these populations. FOS displayed strong linkages to dendritic cell activation (r = 0.66) and inversely correlated with M0 macrophage prevalence (r = − 0.53) (Fig. 7B), highlighting its potential regulatory influence on these immune subsets. GLB1 demonstrated inverse relationships with monocyte infiltration (r = − 0.65) and dendritic cell activation (r = − 0.49) (Fig. 7C), suggesting its role in suppressing these cellular responses. JUN exhibited connections with dendritic cell activation (r = 0.56) and a negative association with memory B cell frequency (r = − 0.4) (Fig. 7D), implying involvement in immune activation dynamics and memory regulation.

  Fig. 7Correlation of OSA-ARDEGs with immune cell infiltration. Association patterns between OSA-associated differentially expressed genes (EGR1 (A), FOS (B), GLB1 (C), JUN (D)) and infiltrating immune cell populations are shown. Dot size corresponds to correlation coefficient magnitude, while color intensity represents statistical significance levels


### Construction and validation of OSA-ARDEGs gene markers
  To enhance the diagnostic accuracy of hub OSA-ARDEGs in OSA, we employed three distinct ML algorithms—LASSO regression (Fig. 8A-B), SVM-RFE analysis (Fig. 8C-D), and Random Forest modeling (Fig. 8E-F)—for feature selection. Through integrative analysis of these algorithmic outputs, GLB1 and EGR1 emerged as robust candidates, defining two key OSA-linked hub genes (OSA-ARDEGs).

  Fig. 8Discovery of core OSA-linked aging-related genes via ML algorithms. (A) LASSO regression coefficient trajectories, with optimal λ parameter demarcated by dashed vertical lines. (B) Cross-validation error curves for LASSO model parameter optimization, with individual gene trajectories displayed. (C-D) SVM-RFE algorithm performance metrics showing maximum accuracy and minimum error thresholds for optimal gene selection. (E) Feature importance ranking of OSA-ARDEGs. (F) Random forest error rate as a function of tree number. (G) Composite Venn diagram depicting overlapping genes selected via LASSO, Random Forest, and SVM-RFE methodologies


### Validating characteristic biomarkers using ML models
  Multiple machine learning algorithms, including AdaBoost, Decision Tree, KNN, LightGBM, Naïve Bayes, and XGBoost, were employed for OSA characteristic gene identification. Model performance evaluation demonstrated recall rates exceeding 50% across all algorithms, as detailed in Table 1. The predictive performance of each model was further validated through ROC curve analysis, presented in Fig. 9. Specifically, AdaBoost excelled in all metrics, achieving 100% accuracy, recall, F1 score, and an AUC of 1.0, demonstrating its superiority in identifying characteristic genes in OSA.Among them, AdaBoost had the highest AUC (1.0), while LightGBM performed best in terms of accuracy (0.9), Kappa value (0.7443), and F1 score (0.9318). The importance plots of the four OSA-ARDEGs for different models are shown in Fig. 10. EGR1 and GLB1 emerged as predominant features across multiple models, with GLB1 specifically identified as a key feature in the Decision Tree algorithm.

  Fig. 9displays the performance assessment of six ML algorithms via ROC curve evaluation: (A) AdaBoost, (B) Decision Tree, (C) KNN, (D) LightGBM, (E) Naïve Bayes, and (F) XGBoost. Model efficacy was quantified by AUC metrics

  Fig. 10Predictive feature relevance visualizations in ML classifiers. (A) AdaBoost classifier; (B) Decision Tree model; (C) KNN algorithm; (D) LightGBM framework; (E) Naïve Bayes predictor; (F) XGBoost system

  Table 1Comparison of diagnostic effects of six different machine learning modelsML modelsTPTNFPFNAccuracyKappaPrecisionRecallF1-ScoreAUCAdaBoost4416001.01.01.01.01.01Decision Tree;4111530.866706450.93180.89130.91110.905KNN4110630.850.59210.93180.87230.90110.915LightGBM4113330.90.74430.93180.93180.93180.964Naïve Bayes33115110.73330.39090.75000.86840.80490.834XGBoost399750.80.46750.88640.84780.86670.9048


### Construction and evaluation of the LR model
  Feature relevance assessment revealed two top-ranking genes, mutually prioritized by both AdaBoost and LightGBM frameworks, which were designated as core OSA-ARDEGs. Using these key genes, EGR1 and GLB1, a logistic regression (LR) model was developed. Investigation demonstrated significantly lower EGR1 levels in OSA patients relative to control subjects, whereas GLB1 expression was elevated in OSA cases (Fig. 11A). Furthermore, a nomogram developed through LR analysis is shown in Fig. 11B.

  Fig. 11Assessing the Risk of OSA. (A) Comparative distribution analysis of Hub OSA-ARDEGs in OSA patients versus healthy controls. (B) Nomogram construction for OSA risk prediction in the training cohort, incorporating characteristic gene expression profiles. (C) Calibration curve analysis demonstrating the nomogram’s predictive accuracy in the training set. (D) Decision curve analysis evaluating the clinical utility of the nomogram in the training cohort

  The model’s robustness was assessed via 1000 bootstrap resampling cycles applied to the training dataset. Calibration assessment validated the high predictive performance of the LR algorithm, as illustrated in Fig. 11C. Decision curve analysis revealed superior clinical utility of the model-based approach for OSA patients, as evidenced by the consistent superiority of the model’s benefit curve (red line) over the default strategies (gray line) across threshold probabilities (Fig. 11D).

  The training set evaluation demonstrated robust diagnostic performance, with Hub OSA-ARDEGs achieving AUC values of 0.801 and 0.865 (Fig. 12A), while the logistic regression model attained an AUC of 0.865 in the validation cohort (Fig. 12B). External validation using the GSE75097 dataset yielded AUC values of 0.607 and 0.577 for Hub OSA-ARDEGs (Fig. 12C), with the LR model achieving an AUC of 0.667 (Fig. 12D). These findings confirm the superior diagnostic predictive capacity of the logistic regression model across both internal and external validation datasets.

  Fig. 12Diagnostic model validation. (A) ROC evaluation of core OSA-linked aging-related DEGs in the validation cohort. (B) ROC curve-based assessment of the model’s diagnostic capability within the testing dataset. (C) ROC curve assessment of Hub OSA-ARDEGs in the external validation cohort. (D) Model diagnostic performance verification in the validation set using ROC curve analysis


### Pathway enrichment analysis (GSEA) of hub OSA-ARDEGs
  Pathway enrichment analysis for GLB1 and EGR1 was performed using GSEA. The results reveal distinct biological processes associated with each gene. EGR1 exhibited marked enrichment in biological pathways associated with cardiomyocyte differentiation, interleukin-1-mediated signaling responses, and DNA-binding transcriptional activation mechanisms, as illustrated in Fig. 13A. These processes appear more prominently among the most differentially expressed genes, indicated by earlier peaks in the ranked list for EGR1 compared to GLB1. For GLB1, enrichment analysis highlights its involvement in chromosome segregation, mitochondrion organization, and nuclear chromosome segregation, shown in Fig. 13C.

  Fig. 13GSEA Results for Key Genes. GLB1 GSEA enrichment analysis in GO (A) and KEGG (B). EGR1 GSEA enrichment analysis in GO (C) and KEGG (D)

  Extended pathway enrichment profiling of EGR1-related networks revealed associations with cytokine receptor cross-talk, TCR signaling cascades, and olfactory signal transduction mechanisms (as shown in Fig. 13B). In contrast, GLB1 pathways are enriched in oxidative phosphorylation, ribosome function, and the response to Vibrio cholerae infection (Fig. 13D). Each gene’s unique enrichment profile underscores its potential regulatory mechanisms and interactions within cellular processes.


### GSVA for hub OSA-ARDEGs
  Gene Set Variation Analysis (GSVA) was applied to assess GLB1 and EGR1 differential activity, specifically probing their functional involvement across distinct biological pathways. EGR1 predominantly upregulates pathways associated with metabolic processes and immune response modulation. Key upregulated pathways include Hemoglobin Alpha Binding, Toll-like Receptor 4 Binding, and Interleukin-21 Production. Notably, EGR1 downregulates pathways related to granulocyte chemotaxis and extracellular matrix disassembly, indicating a lesser role in these functions (Fig. 14A). Additionally, EGR1 upregulates pathways crucial to cellular metabolism, such as Porphyrin and Chlorophyll Metabolism, Sulfur Metabolism, Glutathione Metabolism, and Folate Biosynthesis. Conversely, it downregulates pathways involved in specialized or stress responses, including the Renin-Angiotensin System and Complement and Coagulation Cascades (Fig. 14B).

  Fig. 14Functional enrichment analysis of key genes. (A-B) GSVA results showing GO and KEGG pathway enrichment patterns associated with EGR1 expression


### Selection of basal protein and verification of overexpression plasmid
  To further explore the potential mechanisms of cellular senescence, this study focused on EGR1. During preliminary screening to identify a suitable cellular system, EGR1 baseline expression was assessed across three human cell lines: AT2 alveolar epithelial cells (type II), BEAS-2B bronchial epithelial cells, and MRC-5 fetal lung fibroblasts. Comparative analysis of EGR1 basal expression across three cell types revealed significantly higher expression levels in AT2 cells (Fig. 15A), establishing them as the experimental model for subsequent investigations. To elucidate EGR1’s role in cellular senescence mechanisms, an EGR1 overexpression vector was developed, with successful transfection confirmed through Western blot analysis (Fig. 17B).

  Fig. 15Basal protein expression and overexpression verification. (A) Baseline EGR1 protein levels across AT2 alveolar epithelial cells (type II), BEAS-2B bronchial epithelial cells, and MRC-5 fetal lung fibroblasts (triplicate experiments). (B) Immunoblot validation of lysates post-transfection with the EGR1 overexpression construct (triplicate experiments). *** p < 0.001


### Selection of senescence-related genes
  After transfection with the EGR1 overexpression plasmid, to improve the accuracy of predicting downstream signaling pathways, candidate genes for 12 Hub OSA-ARDEGs were predicted using the GEO and HCA databases. These genes included: CIITA, NAIP, NOD1, NOD2, NLRC5, NLRP1, NLRP3, NLRP4, NLRP5, NLRP13, NLRP14, and NLRX1. The accuracy of the candidate genes was subsequently verified by qPCR, as shown in Fig. 16(A). Due to issues with the CIITA and NLRP13 primers, new primers were designed for a second qPCR experiment. Finally, the three most markedly dysregulated genes—CIITA, NAIP, and NLRX1—were prioritized for immunoblot validation (Fig. 18B). Data revealed markedly elevated expression levels of these genes in EGR1-overexpressing AT2 cells.

  Fig. 16Screening and verification of senescence-related genes. (A) Verification of the accuracy of 12 Hub OSA-ARDEGs candidate genes (CIITA, NAIP, NOD1, NOD2, NLRC5, NLRP1, NLRP3, NLRP4, NLRP5, NLRP13, NLRP14, NLRX1) by qPCR. (B) Selection of differentially expressed genes (CIITA, NAIP, NLRX1) for Western blot (WB) analysis (N = 3). (ns indicates no significance; ** p < 0.01; *** p < 0.001)


### Apoptosis detection
  Apoptosis analysis through flow cytometry revealed distinct cellular states between experimental groups. The negative control (NC) group exhibited predominant cell viability, with the majority of cells localized in the healthy quadrant (Q3-3) and minimal apoptotic populations (Q3-1 and Q3-2), indicating low basal apoptosis rates and active cell proliferation. In contrast, EGR1 overexpression significantly enhanced apoptotic cell proportions, as demonstrated in Fig. 17


### Cellular senescence and DNA damage
  To assess the impact of EGR1 overexpression on cellular senescence in AT2 cells, β-galactosidase activity levels were quantified in both non-modified control (NC) and EGR1-overexpressing cohorts. Relative to NC cells, EGR1-overexpressing AT2 cells exhibited markedly elevated senescence levels (Fig. 17B). Furthermore, qPCR analysis of telomere length revealed no significant difference in telomere length between the NC and EGR1 overexpressing AT2 cells (Fig. 17D), suggesting that EGR1 does not induce senescence through a telomere-dependent mechanism. To explore the involvement of EGR1 in modulating the DNA damage response (DDR), γ-H2AX immunofluorescence staining was utilized to identify DNA double-strand breaks (DSBs). In the negative control (NC) group, γ-H2AX foci were scarcely detectable after treatment. In contrast, cells overexpressing EGR1 exhibited sustained γ-H2AX signals (Fig. 17C). These results suggest that EGR1 promotes cellular senescence and DDR activation in AT2 cells via a mechanism independent of telomere regulation.

  Fig. 17EGR1 promotes cell apoptosis, senescence, and DNA damage. C (A) Annexin V-FITC flow cytometric analysis of apoptosis across experimental cohorts (triplicate experiments). (B) Senescence evaluation via SA-β-Gal staining. Blue chromogenic substrate denotes senescent cells (triplicate experiments). (C) Quantification of γ-H2AX foci in wild-type vs. EGR1-overexpressing AT2 cells. Immunofluorescence revealed elevated γ-H2AX in EGR1-overexpressing cells versus controls (nuclear counterstain: DAPI [blue]; γ-H2AX [green]) (triplicate experiments). (D) Telomere length assessment in non-modified controls (NC) and EGR1-overexpressing AT2 cells via qRT-PCR (triplicate experiments; ns: non-significant, *** p < 0.001)


### ELISA
  Pro-inflammatory cytokines, particularly TNF-α and IL-6, are central drivers of OSA progression. Cytokine quantification assays identified robust upregulation of inflammatory mediators (IL-6, IL-17A, IL-1β, TNF-α) in EGR1-overexpressing AT2 cells (Fig. 18). These findings suggest that EGR1 potentially drives OSA progression by regulating inflammatory signaling pathways.

  Fig. 18ELISA analysis. Secreted levels of IL-6, IL-17A, IL-1β, and TNF-αin cell culture supernatants from non-modified control (NC) and EGR1-overexpressing AT2 cells were assayed via ELISA. Data were analyzed via Student’s t-test (triplicates; *** p < 0.001)


## Discussion
  OSA is increasingly recognized as a critical health problem, particularly prevalent in aging populations. Aging is a major risk factor for the development of OSA; physiological changes such as reduced muscle tone, increased neck fat deposition, and changes in respiratory drive contribute to its pathogenesis [28, 29]. Understanding the shared genetic mechanisms between OSA and aging is essential for developing targeted interventions that can mitigate OSA’s impact on the health and quality of life of older adults [30]. Therefore, the aim of this study is to identify potential aging biomarkers in OSA, explore the roles and mechanisms of aging-related genes and immune infiltration in OSA tissues, thereby providing new directions and insights for the underlying mechanisms and early diagnosis of OSA.

  To explore the role of aging-related genes in OSA, we screened 543 aging-related differentially expressed genes (ARDEGs) and performed an intersect analysis with OSA-associated differentially expressed genes (ultimately identifying four key OSA-ARDEGs. Through single-sample gene set enrichment analysis (ssGSEA), we observed a significant elevation in M1 macrophages in OSA patients relative to healthy controls. Furthermore, the expression of plasma cells, naive CD4 T cells, monocytes, and activated dendritic cells was found to be downregulated in OSA patients. The increase in M1 macrophages, notably, may be intricately associated with the high expression of inflammatory factors and oxidative stress status in OSA patients.

  Subsequently, we evaluated the performance of six ML models to determine the most appropriate model for identifying OSA-related characteristic genes. EGR1 is a transcription factor involved in various biological processes including cell survival, proliferation, and differentiation. It plays a critical role in regulating the hematopoietic system, especially in aging hematopoietic stem cells, where its expression impacts immune functions and the production of bone marrow cells [31]. Thus, it is necessary to more comprehensively analyze the mechanisms of interaction between aging and these two characteristic biomarkers to ascertain their roles in OSA and cellular homeostasis.

  In this study, we utilized ML models to identify ARDEGs that can predict the progression of OSA. Our analysis indicates that these ARDEGs have a high diagnostic predictive capability, which hold a significant position in the trend of machine learning applications in clinical diagnostics. This study constructs an ARDEGs signature using ML methods, which exhibits good diagnostic accuracy in both cross-validation and external validation. These ARDEGs demonstrate a high diagnostic predictive capability for OSA. With the growing prominence of machine learning applications in clinical diagnostics. This research demonstrates the potential of ML models in identifying potential ARDEGs related to the progression of OSA.

  To validate the results of bioinformatics analysis, we selected the EGR1 gene for further investigation. EGR1 is a transcription factor with complex and diverse roles in cancer. In pancreatic and gastric cancer metastasis, EGR1 promotes tumor cell proliferation and migration, playing a critical role in the process [32, 33]. However, in certain studies on liver and breast cancer, EGR1 has been identified as a tumor suppressor, inhibiting tumor growth [34, 35]. Despite this, the role of EGR1 in obstructive sleep apnea (OSA) remains poorly understood.

  Apoptosis refers to the programmed cell death process triggered by internal or external signals under specific physiological or pathological conditions. Several studies have shown that OSA induces apoptosis in tissues such as the brain, heart, and kidneys through intermittent hypoxia, further exacerbating cognitive impairment, metabolic disorders, and organ dysfunction [36–38]. Based on this, we analyzed the apoptosis levels in AT2 cells. The results indicated that the occurrence of apoptosis provided further support for the hypothesis of the EGR1 pathway predicted by bioinformatics analysis.

  Aging can be understood from two perspectives: on one hand, telomerase dysfunction leading to telomere shortening is associated with the loss of cellular proliferative capacity, a process known as replicative senescence [39]. On the other hand, stress-induced premature senescence, which does not involve telomere shortening, is typically caused by external stressors such as oxidative stress, radiation, or hyperglycemia, and this process is reversible [40]. Chronic exposure to oxidative stress or other environmental pressures leads to DNA damage, which in turn induces cell cycle arrest, loss of proliferative capacity, and ultimately results in either replicative or stress-induced senescence [41]. During the aging process, the cell’s response to external damage signals not only affects its own function but may also trigger tissue-level degeneration, leading to a variety of age-related diseases [42].

  The first pathway involves changes in telomere length, suggesting that telomere shortening is closely associated with the aging process. The second pathway involves DNA damage and the subsequent increase in γ-H2AX levels, which is closely related to cellular senescence and stress responses. Based on the experimental results, it is proposed that EGR1 may induce senescence through stress signals (such as DNA damage), thereby contributing to the process of stress-induced premature senescence (SIPS).

  For decades, immune dysregulation in patients with OSA has been a topic of concern. Experimental evidence has shown that EGR1 activates the transcription of CIITA, NAIP, and NLRX1 in AT2 cells. CIITA (MHC Class II Transactivator) is a key transcriptional regulator of MHC-II genes, and as the founding member of the NLR (nucleotide-binding oligomerization domain-like receptor) protein family, it plays a crucial role in the adaptive immune system. Studies have indicated that CIITA influences immune responses in the tumor microenvironment by regulating the expression of MHC-II molecules [43]. NLRX1 is a mitochondrial-localized NLR that plays a multifaceted role in the immune system. It negatively regulates type I interferons and pro-inflammatory responses by modulating the NF-κB signaling pathway, thereby influencing cell death, autophagy, and proliferation [43]. NAIP (NLR Family Apoptosis Inhibitory Protein) is a core component of the NAIP/NLRC4 inflammasome and primarily initiates the inflammatory response by recognizing pathogenic factors such as bacterial flagellin. The NAIP/NLRC4 inflammasome plays an important role in host defense, particularly in immune responses against bacterial infections by recruiting and activating Caspase-1 [44, 45].

  Therefore, EGR1 may play an important role in OSA by modulating the expression of immune-related factors and subsequently regulating the functions of CIITA, NAIP, and NLRX1. Further studies suggest that EGR1 activation could lead to the upregulation of inflammatory cytokines such as IL-6, IL-17A, IL-1β, and TNF-α, which play critical roles in the immune response in OSA and promote the onset and progression of the disease. These findings further elucidate the role of EGR1 in immune responses and suggest that it may serve as a potential therapeutic target for OSA, in line with the bioinformatics analysis results.

  In recent years, there has been a growing interest in the role of aging in OSA. Aging significantly affects lung cell function, leading to reduced lung capacity and elasticity, thus exacerbating respiratory diseases such as OSA [46]. Research indicates that specific aging genes, such as those involved in cellular aging and mitochondrial function, may serve as biomarkers for OSA, suggesting that genetic susceptibility worsens with age due to cumulative genetic and environmental stress [32]. Furthermore, epigenetic modifications in these aging genes can lead to metabolic imbalances, further complicating the cellular environment and promoting the progression of OSA.


### Limitation of the study
  This study still has several limitations. First, although we have conducted both internal and external validations for the diagnostic model, its effectiveness requires further confirmation in additional datasets. In this research, we utilized all available OSA datasets. The role of EGR1 in OSA remains incompletely understood: while experimental results suggest that EGR1 may influence immune factors and DNA damage response in OSA, its specific mechanisms need to be further explored. The complex interactions between EGR1 and aging have not been fully examined either. Second, the external validation of the diagnostic model (AUC ~ 0.6) shows weak performance, raising concerns about its clinical utility. Furthermore, to further validate the robustness and reliability of the diagnostic method, it is recommended to include more external validation cohorts. Lastly, as new research on aging mechanisms continues to emerge, our model should be regularly updated to maintain its cutting-edge relevance and practical applicability.


## Conclusion
  This study provides a new line of evidence for putative shared genetic mechanisms between OSA and aging through identification of key genes, pathways, and cell types that may underlie both conditions. The results offer promise that these common genetic features might serve as molecular leads to develop biomarkers for early diagnosis, prognosis, and therapeutic targeting in both OSA and cells senescence [47]. Especially, the salient findings that emerge with the use of bioinformatics tools and machine learning algorithms include the two genes (EGR1, GLB1) that were consistently upregulated in both OSA and cells senescence, offering promising targets for further investigation. In our preliminary investigation of the mechanisms of aging-related genes in OSA, we found that EGR1 and GLB1 serve as critical biomarkers of cellular aging and immune response. EGR1 may influence the progression of OSA by regulating immune-related factors and stress-induced premature senescence (SIPS).


### Future directions
  Our findings further indicate that these genes are closely linked to immune-inflammatory processes, suggesting they may serve as novel diagnostic and therapeutic targets for OSA. These discoveries provide a scientific foundation for the development of new diagnostic tools and therapeutic strategies for OSA, although further experimental validation is needed to support these findings.


## Supplementary Information
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2


## Acknowledgements
  None.