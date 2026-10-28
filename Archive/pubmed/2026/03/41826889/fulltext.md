# Ferroptosis-related gene BACH1 is associated with preeclampsia and shows potential as a biomarker


## Background
  Preeclampsia (PE) is a pregnancy-specific syndrome with unclear pathogenesis. Emerging evidence suggests that ferroptosis-related molecular pathways may be associated with oxidative stress and placental dysfunction observed in PE. In this study, we developed a PE classification model based on ferroptosis-related genes using machine learning and identified potential biomarkers.


## Methods
  We downloaded bulk and single-cell transcriptomic data of PE and normal placental tissues from the Gene Expression Omnibus (GEO) database. Ferroptosis-related genes were identified using weighted gene co-expression network analysis (WGCNA), differential expression analysis, and LASSO regression. Based on these genes, we developed a machine learning model to predict PE. Key marker genes were further selected using the random forest algorithm and validated in single-cell transcriptomic data.


## Results
  A total of 27 ferroptosis-related genes associated with PE were identified by overlapping 1,434 differentially expressed genes (DEGs) in PE, 268 known ferroptosis-related genes, and 1,151 PE-related genes. LASSO regression further selected 11 key genes with potential predictive value. Among them, BACH1 was significantly upregulated in PE and showed the strongest predictive performance as a single gene in the blood sample dataset (GSE48424). The machine learning classification model based on the selected genes exhibited strong discriminative performance, with the random forest classifier achieving an AUC of 0.87 in the test dataset (GSE75010). In the independent validation datasets (GSE149437, GSE25906, and GSE48424), the AUC values were 0.7, 0.78, and 0.81. Validation using the single-cell dataset GSE173193 confirmed that BACH1 was predominantly expressed in neutrophils from PE patients.


## Conclusions
  This study established a transcriptomic classification model for preeclampsia based on ferroptosis-related genes and identified BACH1 as a ferroptosis-related gene associated with preeclampsia, with potential as a blood-based biomarker pending prospective validation.


## Supplementary Information
  The online version contains supplementary material available at 10.1186/s12884-026-08884-x.


## Background
  Preeclampsia (PE) is a pregnancy-specific multisystem disorder that typically develops after 20 weeks of gestation and is characterized by new-onset hypertension accompanied by proteinuria or signs of organ dysfunction [1, 2]. In severe cases, PE may progress to eclampsia, HELLP syndrome, placental abruption, or even intrauterine fetal death [3]. Affecting approximately 3%–8% of pregnancies worldwide, PE remains a major contributor to maternal mortality and adverse perinatal outcome [4, 5]. Despite extensive research, the precise etiology of PE is still not fully understood. It is widely accepted that the condition is associated with abnormal placental development, insufficient spiral artery remodeling, endothelial dysfunction, an exaggerated inflammatory response, and immune maladaptation [6–8]. Oxidative stress and trophoblast apoptosis have been frequently reported in PE [9, 10], but these mechanisms alone do not completely explain its complex pathophysiology.

  In recent years, ferroptosis, a newly identified form of regulated cell death, has garnered growing attention [11]. Unlike apoptosis, necrosis, or necroptosis, ferroptosis is characterized by the iron-dependent accumulation of lipid peroxides, depletion of intracellular glutathione (GSH), inactivation of glutathione peroxidase 4 (GPX4), and oxidation of membrane phospholipids enriched in polyunsaturated fatty acids [12–14]. Ferroptosis is tightly regulated by iron metabolism, lipid peroxidation pathways, and redox homeostasis. It has been implicated in various diseases, including neurodegenerative disorders, cancer, metabolic diseases, and ischemia-reperfusion injury [15, 16].

  Compelling evidence suggests a potential involvement of ferroptosis in the pathogenesis of PE [17, 18]. Placental tissues from PE patients exhibit elevated levels of lipid peroxidation products such as 4-hydroxynonenal (4-HNE), phosphatidylethanolamine, and malondialdehyde (MDA), along with decreased GSH levels and downregulated GPX4 expression [19–21]. Furthermore, pharmacological inhibition of ferroptosis using agents such as ferrostatin-1 (Fer-1) or liproxstatin-1 has been shown to alleviate PE-like phenotypes in vitro, improving trophoblast proliferation, migration, and invasion [17, 22]. These findings highlight the potential of ferroptosis-related markers as novel targets for the diagnosis and treatment of PE.

  This study aims to identify ferroptosis-related genes that are strongly associated with PE, construct a PE classification model using machine learning algorithms, and screen for potential biomarker genes suitable for early screening of PE, thereby providing new insights into the diagnosis and treatment of this condition.


## Methods

### Data source
  The datasets used in this study were obtained from the Gene Expression Omnibus (GEO) database. The GSE75010 [23] and GSE25906 [24] datasets consisted of placental tissue samples, including transcriptomic data from patients with PE and normal pregnancies. The GSE48424 [25] and GSE149437 [26] dataset comprised peripheral blood samples, providing gene expression profiles of PE patients and healthy pregnant women. In addition, the single-cell transcriptomic dataset GSE173193 [27] was downloaded to further validate the expression patterns of key genes across distinct placental cell populations. In all datasets, the diagnosis of preeclampsia followed the clinical criteria defined in the original studies, and detailed information on sample size and dataset characteristics is summarized in Supplementary Table 1.


### Differentially expressed gene (DEG) analysis
  The identification of DEGs was performed using placental tissue samples from the GSE75010 dataset, which was selected due to its relatively well-annotated placental transcriptomic profiles and sufficient sample size. Transcriptomic profiles from normal pregnancies and PE patients were compared using the Limma R package, with the thresholds set at P < 0.05 and |logFC| > 0.5 to screen for DEGs associated with PE.


### Enrichment analysis
  To investigate the potential biological roles of DEGs, KEGG pathway analysis, Gene Ontology (GO) functional annotation, and Gene Set Enrichment Analysis (GSEA) were performed [28]. KEGG and GO enrichment analyses were conducted using the clusterProfiler R package, with GO analysis covering the three categories of biological process (BP), cellular component (CC), and molecular function (MF). GSEA was performed using the hallmark gene sets from the Molecular Signatures Database (MSigDB). Gene sets with P < 0.05 were considered significantly enriched.


### Weighted gene co-expression network analysis (WGCNA)
  The GSE75010 dataset containing placental tissue samples was used to perform WGCNA to identify gene modules significantly associated with PE. Pearson’s correlation coefficients were calculated among samples based on gene expression profiles, and a soft-thresholding power was selected to ensure the scale-free topology of the network. A weighted adjacency matrix was then constructed and transformed into a topological overlap matrix. Genes were hierarchically clustered into distinct modules, and module eigengenes (MEs) were correlated with clinical phenotypes (normal pregnancy vs. PE). Modules showing the strongest correlations with preeclampsia status were selected for downstream intersection analysis with differentially expressed genes and ferroptosis-related gene sets.


### LASSO regression analysis
  Among the candidate ferroptosis-related genes (Supplementary Table 2), least absolute shrinkage and selection operator (LASSO) regression was applied for feature selection. This analysis identified 11 key genes with potential discriminative relevance, which were subsequently used for model construction and functional validation.


### Machine learning model development
  Based on the selected ferroptosis-related genes, four machine learning algorithms were employed to construct classification models: Random Forest (RF), Logistic Regression (LR), Support Vector Machine (SVM), and Extreme Gradient Boosting (XGBoost). Model training and testing were performed on the GSE75010 dataset using 5-fold cross-validation to ensure robustness. Independent validation was conducted using GSE25906 (tissue samples) and GSE48424 (blood samples). Model performance was evaluated by calculating the area under the receiver operating characteristic curve (AUC), which was used to compare the discriminative power of each algorithm in predicting PE. In addition, precision–recall (PR) analysis was performed, and the area under the precision–recall curve (AUPRC) was calculated.

  For PR analysis, 95% confidence intervals of AUPRC were estimated using bootstrap resampling with 1,000 iterations.


### Single-cell transcriptomic analysis
  Single-cell data were processed following the standard workflow of the Seurat R package, including quality control, normalization, dimensionality reduction, clustering, and visualization. Cell type annotation was performed with reference to the CellMarker database and previously reported placenta-specific marker genes to ensure accurate classification [27, 29].


## Results

### Clinical characteristics and DEGs
  Patients with PE are generally characterized by elevated blood pressure and restricted placental and fetal growth. In this study, we first compared the clinical features between PE and normal pregnancies. The results showed that systolic and diastolic blood pressure were significantly increased in the PE group, while neonatal birth weight and placental weight z-scores were markedly decreased (Fig. 1).

  Fig. 1Available clinical characteristics of PE (n = 80) and normal (n = 77) pregnancies in the GSE75010 dataset. A Maximum diastolic blood pressure; B Maximum systolic blood pressure; C Newborn weight z-score; D Placental weight z-score. Boxplots represent the median and interquartile range, with each point corresponding to one sample Statistical significance was assessed using the Wilcoxon rank-sum test

  We further performed transcriptomic analyses to identify molecular alterations. Differential expression analysis using the GSE75010 and GSE25906 datasets identified a large number of DEGs, with 820 genes downregulated and 614 genes upregulated (Fig. 2A). The heatmap illustrated that ferroptosis-related genes exhibited distinct expression patterns between groups (Fig. 2B). Notably, exploratory subtype-stratified analyses suggested heterogeneity among preeclampsia samples, with a subset—more frequently observed in preterm PE—showing higher expression levels of several ferroptosis-related genes, including BACH1, PLIN2, and ARRDC3 (Figure S1). Functional enrichment revealed that these DEGs were predominantly associated with HIF-1 signaling, PI3K-Akt signaling, and extracellular matrix organization (Fig. 2C–D). In addition, GSEA demonstrated that hallmark pathways such as hypoxia and glycolysis were significantly activated in PE (Fig. 3).

  Fig. 2Identification and enrichment of DEGs. A Volcano plot showing upregulated and downregulated genes between preeclampsia (PE; n = 103) and normal pregnancy groups (n = 114), identified by differential expression analysis using the limma package across the GSE75010 and GSE25906 datasets, with thresholds of P < 0.05 and |log₂fold change| > 0.5. B Heatmap displaying the expression pattern of ferroptosis-related genes in PE and normal groups. C Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment analysis of DEGs. Enrichment results were considered significant at adjusted P < 0.05. D Gene Ontology (GO) enrichment analysis of DEGs, including biological process (BP), cellular component (CC), and molecular function (MF) categories. Enrichment results were considered significant at adjusted P < 0.05

  Fig. 3Gene set enrichment analysis (GSEA) of preeclampsia-associated transcriptomic alterations using the Hallmark gene sets from the Molecular Signatures Database (MSigDB). A GSEA enrichment results showing upregulated and downregulated pathways significantly associated with PE. Pathways with a false discovery rate (FDR) < 0.05 were considered significantly enriched. B Ridge plot of normalized enrichment scores (NES) summarizing the enrichment patterns of Hallmark pathways. C Enrichment score curves for selected Hallmark pathways, illustrating their distribution across the ranked gene list


### WGCNA identifies PE-associated modules
  To further investigate gene modules associated with PE, weighted gene co-expression network analysis (WGCNA) was performed using the GSE75010 dataset. A scale-free network was constructed by selecting an appropriate soft-thresholding power (Fig. 4A). Sample clustering revealed that PE and normal groups could be clearly distinguished based on their expression profiles (Fig. 4B). Module–trait correlation analysis demonstrated that several modules were significantly associated with the PE phenotype (Fig. 4C–D). Notably, the yellow and midnightblue modules showed the strongest positive correlations with the PE phenotype (P < 0.01) and were therefore selected for downstream analyses (Supplementary Table 3).

  Fig. 4Weighted gene co-expression network analysis (WGCNA) of the GSE75010 placental transcriptomic dataset. A Soft-thresholding power selection showing the scale-free topology fit. B Sample dendrogram showing hierarchical clustering of PE (n = 80) and normal (n = 77) placental samples. C Gene module clustering tree showing the division of different gene modules. D Module–trait correlation heatmap showing the Pearson correlation between module eigengenes and PE status (binary trait)


### Identification of key ferroptosis-related genes
  To further identify ferroptosis-related genes closely associated with PE, we integrated DEGs, genes from the PE-associated WGCNA modules (yellow and midnightblue), and a curated ferroptosis-related gene set. The intersection yielded 27 candidate genes and known ferroptosis-related gene sets. The intersection yielded 27 candidate genes (Fig. 5A and Supplementary Table 4). Subsequently, feature selection was performed using LASSO regression and the random forest algorithm (Fig. 5B–D), resulting in 11 key genes, including BACH1, PLIN2, TXNRD1, RGS4, and DUSP1, among others. Expression profiling revealed significant differences between PE and normal pregnancies for these key genes (Fig. 6). Notably, BACH1, PLIN2, and TXNRD1 were markedly upregulated in PE patients, indicating their association with preeclampsia-related transcriptional alterations. To further assess robustness, we evaluated BACH1 in an independent peripheral blood dataset (GSE149437), which yielded consistent results (Figure S2).

  Fig. 5Identification of ferroptosis-related candidate genes. A Venn diagram showing the intersection of DEGs, WGCNA module genes, and ferroptosis-related genes. B LASSO regression analysis for feature selection of key genes. C LASSO regression analysis for feature selection of key genes. LASSO coefficient profiles showing the selection of key genes at the optimal regularization parameter (λ). D Important genes ranked by Random Forest feature importance, with BACH1 showing the highest importance

  Fig. 6Expression of key genes in PE and normal groups. Expression levels of selected key genes in PE (n = 80) and normal pregnancies (n = 77) from the GSE75010 dataset. Differences between groups were assessed using the Wilcoxon rank-sum test. Data are presented as boxplots showing the median and interquartile range


### Classification performance of key genes
  To evaluate the diagnostic discrimination ability of key genes between PE cases and controls, single-gene validation was performed using the blood transcriptomic dataset GSE48424, and their discriminative performance was assessed by ROC curve analysis (Fig. 7). Several genes demonstrated moderate classification ability, with BACH1 achieving the highest AUC (0.77), indicating its potential utility for distinguishing PE cases from controls in retrospective blood transcriptomic data. In addition to AUROC, precision–recall analysis was performed to further assess classification performance. BACH1 achieved an AUPRC of 0.75 (95% CI: 0.52–0.93) in GSE48424 and 0.85 (95% CI: 0.75–0.95) in GSE149437, supporting its discriminative ability in independent blood datasets (Figure S3).

  Fig. 7ROC curves of single-gene classification performance in GSE48424. A ROC curve for BACH1, with an AUC of 0.77, indicating its potential utility in distinguishing preeclampsia cases from controls in peripheral blood samples. B-F ROC curves for other key genes, with AUC values ranging from 0.63 to 0.74

  Building upon these findings, four machine learning models were constructed using the selected ferroptosis-related key genes: Random Forest (RF), Logistic Regression (LR), Support Vector Machine (SVM), and Extreme Gradient Boosting (XGBoost) (Fig. 8). In the training dataset GSE75010, all four models showed good discriminative performance, with the RF model achieving the highest AUC (0.87). In the independent validation datasets GSE25906 and GSE48424, the RF model maintained strong performance (AUC = 0.78 and 0.81, respectively), suggesting relatively stable performance across the evaluated datasets. In contrast, the performance of LR, SVM, and XGBoost models fluctuated more noticeably in the validation cohorts.

  Fig. 8Machine learning model performance. ROC curves showing the classification performance of four machine learning models based on ferroptosis-related key genes. A ROC curve for Random Forest (RF). B ROC curve for Logistic Regression (LR). C ROC curve for Support Vector Machine (SVM). D ROC curve for XGBoost. Models were trained on the GSE75010 dataset using 5-fold cross-validation and evaluated in independent validation datasets (GSE25906 and GSE48424)


### BACH1 expression and clinical features
  To further evaluate the clinical significance of the key gene, we analyzed the correlation between BACH1 expression and clinical parameters (Fig. 9). The results demonstrated that BACH1 expression was significantly positively correlated with maximum systolic blood pressure (R = 0.56, P < 0.001) and maximum diastolic blood pressure (R = 0.53, P < 0.001). In addition, BACH1 expression was positively associated with neonatal birth weight z-score (R = 0.46, P < 0.001) and placental weight z-score (R = 0.39, P < 0.001). These findings indicate that BACH1 expression is correlated with several clinical parameters in the analyzed dataset. However, the observed positive correlations with neonatal birth weight and placental weight z-scores should be interpreted with caution, as these analyses were not adjusted for gestational age or preeclampsia subtype and may be influenced by cohort heterogeneity.

  Fig. 9Correlation between BACH1 expression and clinical features in the GSE75010 dataset. Scatter plots showing correlations between BACH1 expression and clinical parameters in placental samples. A Maximum diastolic blood pressure, B Maximum systolic blood pressure, C Newborn weight z-score, D Placental weight z-score. Correlations were assessed using Spearman’s rank correlation. R and P values are shown


### Single-cell analysis reveals neutrophil-specific expression of BACH1
  To further validate the expression characteristics of BACH1 across different cell types, we analyzed the GSE173193 single-cell transcriptomic dataset. UMAP visualization revealed the distribution of major placental cell populations, including villous cytotrophoblasts (VCTs), extravillous trophoblasts (EVTs), syncytiotrophoblasts (SCTs), neutrophils, macrophages, monocytes, T/NK cells, and erythroid progenitors (Fig. 10A–B).The results demonstrated that BACH1 expression was predominantly enriched in neutrophils and was markedly higher in PE patients compared with normal pregnancies (Fig. 10C). This finding not only validates the cell type–specific distribution of BACH1 at the single-cell level but also provides supportive transcriptomic evidence for further investigation of BACH1 as a blood-associated candidate marker in PE.

  Fig. 10Single-cell transcriptomic validation of BACH1 expression in the GSE173193 dataset. A UMAP plot showing clustering of placental cell populations. B UMAP plots for different cell populations showing BACH1 expression in neutrophils and other cell types. C Expression of BACH1 in neutrophils, with significantly higher expression in PE samples compared to normal pregnancies


## Discussion
  In this study, we systematically identified and validated ferroptosis-related key genes across multiple transcriptomic datasets associated with PE by integrating placental and peripheral blood transcriptomic datasets with WGCNA, LASSO regression, and multiple machine learning approaches. Among these genes, BACH1 was consistently upregulated in both placental tissues and blood samples and exhibited robust performance in retrospective single-gene discrimination and multi-model classification. Single-cell transcriptomic analysis further revealed that BACH1 was specifically enriched in neutrophils in placental single-cell datasets. Importantly, the enrichment of BACH1 in neutrophils raises the possibility that elevated BACH1 expression observed in bulk placental and peripheral blood transcriptomic data may partly reflect changes in immune cell composition, such as increased neutrophil abundance in preeclampsia, rather than solely cell-intrinsic upregulation. Alternatively, BACH1 upregulation may represent a compensatory redox-regulatory response within trophoblasts or immune cells under oxidative stress conditions, or a combination of both mechanisms. Previous studies have demonstrated that neutrophil activation contributes to the development of PE [30]. This provides transcriptomic evidence supporting an association between ferroptosis-related gene expression and PE and suggests BACH1 as a candidate blood-based biomarker associated with preeclampsia. Given the retrospective nature of the datasets analyzed, its role in early prediction remains to be validated in prospective early-pregnancy cohorts.

  Previous studies have highlighted placental hypoxia, impaired trophoblast invasion, and metabolic reprogramming as key pathological features of PE, particularly early-onset PE [31, 32]. Our DEG and enrichment analyses demonstrated significant involvement of HIF-1 signaling, PI3K-Akt signaling, and extracellular matrix-related pathways, along with hallmark pathways such as hypoxia, glycolysis, and oxidative phosphorylation, which are highly consistent with these pathological processes [33–35]. Compared with earlier research that mainly emphasized oxidative stress and apoptosis, our findings underscore a potential association between ferroptosis-related transcriptional programs and preeclampsia, supporting further investigation of ferroptosis in PE pathogenesis.

  Notably, BACH1, a transcription factor, is closely linked to oxidative stress regulation, iron metabolism, and lipid peroxidation [36]. It has been reported to be upregulated in various oxidative stress-related diseases [37]. Our study demonstrated elevated BACH1 expression in both placental and blood samples from PE patients, suggesting its potential involvement in PE-associated molecular processes in association with ferroptosis-related pathways. Together, these observations support the hypothesis that BACH1 may be linked to ferroptosis-related processes in PE; However, direct experimental validation of ferroptosis activity will be required in future studies. Furthermore, the predictive performance of BACH1 in blood datasets and its neutrophil-specific expression provide supportive evidence for its potential utility as a non-invasive blood biomarker. This finding is of practical relevance, as blood-based biomarkers are convenient, repeatable, and widely applicable, and may facilitate biomarker prioritization and risk stratification in future preeclampsia studies.

  However, the observed positive correlations between BACH1 expression and neonatal birth weight or placental weight z-scores appear counterintuitive, as preeclampsia is commonly associated with fetal growth restriction. This unexpected directionality may reflect heterogeneity among preeclampsia cases, including differences between early- and late-onset disease, as well as potential confounding by gestational age at sampling. Due to the retrospective nature of the analyzed public datasets and the limited availability of detailed clinical metadata, these correlation analyses were not adjusted for gestational age or PE subtype. Therefore, these findings should be interpreted with caution and should not be viewed as direct indicators of disease severity or maternal–fetal outcomes. Future studies with well-annotated prospective cohorts will be required to clarify the clinical significance of these associations.

  Nevertheless, several limitations should be acknowledged. First, although multiple public datasets were integrated and validated at the single-cell level, prospective validation in clinical cohorts is still lacking. Second, the performance of machine learning models may be influenced by dataset size and heterogeneity, necessitating further evaluation in larger, multicenter cohorts. In addition, early- and late-onset PE cases were analyzed together due to incomplete clinical annotations, and potential confounding by gestational age and PE subtype could not be fully controlled. Finally, the precise molecular mechanisms by which BACH1 contributes to PE remain to be elucidated through in vitro and in vivo functional studies.


## Conclusions
  By integrating placental and peripheral blood transcriptomic datasets with weighted co-expression analysis, machine learning modeling, and single-cell validation, this study systematically identified ferroptosis-related key genes associated with PE. Our findings demonstrated that BACH1 was consistently upregulated in both tissues and blood samples, exhibited consistent discriminative performance in retrospective datasets, and showed neutrophil-specific expression at the single-cell level. These results highlight the potential role of ferroptosis in PE pathogenesis and suggest that BACH1 may represent a promising non-invasive blood-associated candidate marker for preeclampsia, pending validation in prospective early-pregnancy cohorts.


## Supplementary Information
  Supplementary Material 1.

  Supplementary Material 2.


## Acknowledgements
  The authors thank the staff and participants of this study for their important contributions.