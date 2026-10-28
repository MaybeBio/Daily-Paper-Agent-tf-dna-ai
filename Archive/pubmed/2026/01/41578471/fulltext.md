# An integrated machine learning framework for developing a transcriptomic analysis and machine learning-based diagnostic model of gout based on sleep disorder-related genes


## Abstract
  Gout, often comorbid with sleep disorders (SDs), is prevalent in inflammatory arthritis. This comorbidity is notable in patients with impaired renal function requiring blood purification, with unclear underlying mechanisms. This study integrated transcriptomic analysis and machine learning to identify shared genetic markers and develop a diagnostic model for gout based on SD-related genes. Transcriptomic datasets from the Gene Expression Omnibus, including those of gout and SD patients, were systematically analyzed to develop the model. Differentially expressed genes (DEGs) associated with both conditions were identified and analyzed. Functional enrichment and immune infiltration analyses were performed using R packages. Immune infiltration analysis was conducted using single-sample gene set enrichment analysis. A gout diagnostic model was trained on the shared DEGs via machine learning methods. Eight shared DEGs were identified. Key pathways and molecular functions included DNA-binding protein serine/threonine kinase activity, arrhythmogenic right ventricular cardiomyopathy, and the Janus kinase/signal transducer and activator of transcription signaling pathway. Immune infiltration analysis revealed distinct immune cell infiltration profiles in gout and SD patients compared with healthy controls. A robust 8-gene diagnostic signature (APBA2, KLF13, FAM117A, IL6R, CCND3, WASF2, PROSC, and TAF1) was constructed. This study established a novel molecular framework linking gout pathogenesis with sleep disruption, thereby providing potential biomarkers for the early diagnosis and precision treatment of gout.


## 1. Introduction
  Gout is a chronic inflammatory arthritis characterized by hyperuricemia[1] and monosodium urate crystal deposition,[2] affecting approximately 1% to 6.8% of the global population, with a rising prevalence due to dietary and lifestyle changes.[3] It is characterized by recurrent acute attacks of severe joint pain, typically in the 1st metatarsophalangeal joint, and can lead to chronic joint damage, kidney dysfunction, and cardiovascular complications.[4] While traditionally viewed as a metabolic disorder, emerging evidence highlights its bidirectional relationship with sleep disorders (SDs), including insomnia, obstructive sleep apnea (OSA), and restless legs syndrome (RLS).[5] Participants with gout are also more likely to report suffering from RLS, insomnia, and worry about their sleep.[5] Physician-diagnosed gout patients reported frequent SDs and daytime sleepiness.[6] Conversely, chronic sleep deprivation increased serum uric acid levels through impaired renal excretion and enhanced purine biosynthesis.[7] Despite this clinical correlation, the molecular mechanisms linking gout pathogenesis and sleep regulation remain poorly understood.

  Gout arises from hyperuricemia, in which uric acid levels exceed the solubility threshold, leading to monosodium urate crystal formation.[8] The condition is classified into primary (genetic defects in purine metabolism or renal excretion)[9] and secondary (medications, malignancies, or renal disease) forms.[10] In primary gout, many cases involve renal under-excretion of uric acid.[11] Epidemiological studies have shown that only 29.9% of patients with gout, and none of those with tophaceous gout, were adequately treated.[12] Risk factors include obesity, hypertension, diabetes, and alcohol consumption, underscoring their association with metabolic syndrome.[13]

  SDs encompass a spectrum of conditions that affect sleep quality and duration, including insomnia, OSA, and RLS.[14] Insomnia, characterized by difficulty in initiating or maintaining sleep, affects many adults worldwide. With its extensive global burden, this pathological state is intricately linked to both somatic and neuropsychiatric manifestations, including cognitive impairment, anxiety disorders, chronic fatigue, diminished attention span, and memory dysfunction.[15] OSA, marked by repetitive apnea/hypopnea episodes during sleep, is linked to endothelial dysfunction, systemic inflammation, and metabolic derangements.[16] RLS is a sensorimotor disorder that causes the urge to move limbs at rest and is associated with caffeine and smoking.[17] These disorders disrupt circadian rhythms, compromise immune functions, and exacerbate inflammation.[18]

  While clinical and genetic evidence support an association between gout and SDs, integrative transcriptomic analyses are lacking.[19] Previous studies have focused on either condition in isolation, limiting insights into shared molecular mechanisms. Machine learning approaches offer a powerful framework for identifying complex gene-gene interactions and constructing predictive models.[20,21] This study addresses these gaps by: identifying differentially expressed genes (DEGs) associated with both gout and SDs; exploring functional pathways and immune cell infiltration; and developing a machine learning-based diagnostic model based on SD-related genes. It aimed to uncover novel biomarkers and therapeutic targets for the precise management of gout.


## 2. Methods

### 2.1. Data collection
  Transcriptomic datasets were retrieved from the Gene Expression Omnibus (GEO, https://www.ncbi.nlm.nih.gov/geo/) using “SDs” and “gout” as search terms. Four eligible datasets (GSE208668, GSE98582, GSE160170, and GSE178825) were selected based on sample size and disease specificity. Platform details and sample characteristics were presented in Table 1.


### 2.2. Ethics committee approval of the study
  This study used publicly available transcriptomic data from the GEO database, which has obtained ethical approval and informed consent from participants as specified in the original studies. The Institutional Review Board of People’s Hospital of Linquan County waived the need for additional ethical review due to the secondary use of de-identified public data.


### 2.3. Batch effect removal and identification of DEGs
  To ensure data integrity before downstream analysis, a 2-step preprocessing pipeline was implemented. First, transcriptomic datasets from SD cohorts (GSE208668 and GSE98582) were integrated using the ComBat algorithm from the sva R package (v3.5.0) to mitigate batch effects arising from technical variability.[22] Principal component analysis (PCA) was used to evaluate normalization efficacy, showing reduced inter-batch variance after correction. A similar workflow was applied to gout datasets (GSE160170 and GSE178825), with batch effect mitigation confirmed via PCA. Differential gene expression analysis was subsequently performed using the limma package,[23] with statistical thresholds set at |log2 fold change| > 0.25 and false discovery rate (FDR) < 0.05. Volcano plots were generated in R (v4.4.2) to visualize significant DEGs, and Venn diagram intersections were computed to identify overlapping genes between the SD and gout datasets.


### 2.4. Enrichment analysis of shared genes
  Functional annotation of the shared gene set was conducted to characterize biological processes and molecular mechanisms. Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment analyses were performed to identify overrepresented biological processes, cellular components, and signaling pathways. Additionally, Disease Ontology (DO) enrichment analysis was performed to explore disease-specific associations. These analyses were conducted using the org.Hs.eg.db (v3.19.1) annotation package, ggplot2 (v3.5.2) for visualization, and clusterProfiler (v4.12.6) or enrichplot (v1.24.4) for statistical computations in R software (v4.4.2). Enrichment significance was determined using a stringent threshold of P < .05, with FDR correction applied where appropriate.


### 2.5. Immune cell infiltration
  To characterize the immune microenvironment, single-sample gene set enrichment analysis (ssGSEA) was used to estimate the relative abundance of 23 immune cell subsets in each sample.[24] This approach leverages gene expression signatures to infer cellular composition and provides a comprehensive assessment of adaptive and innate immune responses. The analyzed cell types included: adaptive immunity: activated B cells, activated CD4+ T cells, activated CD8+ T cells, regulatory T cells, T follicular helper cells (Tfh cells), and type 1/2/17 T helper cells; innate immunity: activated dendritic cells, eosinophils, gamma delta T cells, macrophages, mast cells, monocytes, natural killer cells (CD56bright/CD56dim subsets), natural killer T cells, neutrophils, and plasmacytoid dendritic cells; immature populations: immature B cells and immature dendritic cells; and myeloid-derived suppressor cells.


### 2.6. Machine learning algorithms
  A comprehensive machine learning pipeline was developed to construct a diagnostic model for gout. Eight supervised learning algorithms were selected based on their performance in high-dimensional genomic data analysis: support vector machine, generalized linear model boosting, ridge regression, partial least squares regression for generalized linear models, stepwise GLM, linear discriminant analysis, extreme gradient boosting, and Naive Bayes. The algorithms systematically integrate distinct model configurations to explore their predictive performance.

  The integrated datasets (GSE160170 and GSE178825) were subjected to feature selection and hyperparameter tuning using a 10-fold cross-validation strategy. Performance metrics, including the area under the receiver operating characteristic curve, were computed for each model iteration. The optimal model was defined as the one achieving the highest mean area under the receiver operating characteristic curve across both training and validation subsets, consistent with established best practices in bioinformatics.[25]

  To ensure clinical utility, calibration curves were generated to evaluate agreement between predicted probabilities and observed outcomes. This process is critical for assessing model reliability in real-world settings, as it quantifies systematic bias in probability estimates.


### 2.7. Statistical analysis
  R software (v4.4.2) was utilized for statistical analyses. In 2-group comparisons, continuous variables were analyzed with the Student t test, and categorical data were evaluated using the Pearson chi-squared test. For comparing continuous variables across multiple groups, 1-way analysis of variance was employed, followed by the Benjamini–Hochberg procedure to manage the FDR during multiple testing correction. A P-value of <.05 was defined as statistically significant.


## 3. Results

### 3.1. Data processing and identification of differentially expressed associated genes with SD and gout
  Transcriptomic datasets from patients with SDs and healthy controls were retrieved from the GEO database (Fig. 1). Raw data underwent batch effect correction using the ComBat algorithm implemented in the sva (v3.52.0) R package, followed by integration and normalization to generate a processed dataset consisting of 128 SD cases and 97 controls (Fig. 2A and B). Similarly, gout and control datasets were batch-corrected and combined, yielding a validation cohort of 11 patients with gout and 9 controls (Fig. 3A and B). PCA confirmed the successful mitigation of technical variability after correction.

  Differential gene expression analysis identified 480 DEGs in the SD cohort (370 upregulated and 110 downregulated; Fig. 2C and D) and 264 DEGs in the gout cohort (50 upregulated and 214 downregulated; Fig. 3C and D). These DEGs were identified using stringent filtering criteria: |log2FC| > 0.25 and FDR < 0.05. Venn diagram intersection revealed 8 overlapping genes (Fig. 4A) that were prioritized for downstream functional analysis.


### 3.2. Functional enrichment of the pathogenic genes involved in SD-related gout
  Functional annotation of the shared gene set was conducted via GO, KEGG, and DO enrichment analyses to uncover underlying molecular mechanisms. GO biological processes are primarily involved in cell cycle regulation, particularly G1/S phase transition, positive regulation of protein kinase activity, and cell cycle checkpoint control. Cellular component analysis revealed enrichment in transferase complexes involved in phosphorus-containing group transfer, as well as scavenger receptor class A and mixed lineage leukemia 1 histone methyltransferase complexes. Molecular function annotations highlighted interactions with the Arp2/3 actin nucleation complex, cyclin-dependent kinase activity, and promoter-specific DNA binding (Fig. 4B).

  DO analysis revealed significant associations with arrhythmogenic right ventricular cardiomyopathy, proliferative diabetic retinopathy, and cervical carcinoma, suggesting potential shared pathogenic mechanisms (Fig. 4C). KEGG pathway enrichment analysis revealed activation of Janus kinase/signal transducer and activator of transcription (JAK/STAT) and PI3K-Akt signaling cascades, which are critical for inflammation and cell survival, alongside basal transcription factor networks essential for gene expression regulation (Fig. 4D). These findings indicate that the shared genes converge on pathways linking cell cycle progression, inflammatory signaling, and transcriptional regulation, providing mechanistic insights into the comorbidity between gout and SDs.


### 3.3. Immune cell infiltration analysis in SD and gout
  ssGSEA was used to characterize the immune cell landscape in SD and gout cohorts. This computational approach utilized gene expression signatures to estimate the relative abundance of 23 immune cell subsets, providing a comprehensive assessment of adaptive and innate immunity.

  In the SD cohort (Fig. 5A), ssGSEA revealed significant alterations in both adaptive and innate immune compartments. Specifically, immature B cells showed elevated infiltration (P < .05), whereas macrophages, natural killer T cells, natural killer cells, and regulatory T cells exhibited reduced abundance compared to healthy controls. These findings suggest a dysregulated B-cell maturation process and an immunosuppressive microenvironment in SD.

  The gout cohort (Fig. 5B) showed distinct immune profiles, with marked increases in Tfh cells and type 2 T helper (Th2) cells. Tfh cells play a critical role in germinal center reactions and antibody production, whereas Th2 cells mediate allergic and antiparasitic responses. These observations align with the chronic inflammatory phenotype of gout and highlight the potential for Th2-driven immune deviations.


### 3.4. Identification of shared DEGs with diagnostic value and developing a diagnostic model for SD-related gout via machine learning
  In the discovery cohort, which consisted of datasets GSE160170 and GSE178825, comprehensive analyses were performed (Fig. 6A–D). Multiple machine learning algorithms were initially considered to construct the most effective diagnostic model. After a series of evaluations and comparisons, the Naive Bayes algorithm emerged as the best-performing approach.

  The Naive Bayes algorithm is a well-known probabilistic classifier in machine learning. The algorithm was employed to sift through a large number of genes in the dataset. Through its unique probabilistic calculation and feature selection mechanisms, it successfully identified 8 key genes: APBA2, KLF13, FAM117A, IL6R, CCND3, WASF2, PROSC, and TAF1.

  Calibration curves were generated to assess the calibration of the diagnostic models. As shown in Figure 6E, across both cohorts, the calibration curves closely followed the ideal diagonal line. This close approximation indicates that the probabilities predicted by the model align closely with actual clinical outcomes observed in patients. Such an agreement strongly indicates the model’s robust calibration, which is essential for a reliable diagnostic tool.

  In addition to calibration analyses, a nomogram was constructed using the 8 identified genes. A nomogram is a graphical tool that simplifies the complex prediction process of a model. It exhibited improved diagnostic performance, as shown in Figure 6F. This suggests that when incorporated into the nomogram, these 8 genes provide more accurate and clinically useful diagnostic information.


## 4. Discussion
  This study is the 1st integrative analysis of transcriptomic data from patients with gout and SD, uncovering 8 shared DEGs and constructing a robust diagnostic model. The identified genes – APBA2, KLF13, FAM117A, IL6R, CCND3, WASF2, PROSC, and TAF1 – are enriched in pathways that link inflammation, kinase activity regulation, and cell cycle control. These findings provide novel insights into the molecular basis of comorbidity between SD and gout and suggest bidirectional interactions between immune dysregulation and sleep disruption.

  Sleep deprivation disrupts circadian rhythms,[26] leading to downregulation of these transporters and subsequent hyperuricemia.[27] Notably, our identified gene PROSC, involved in mitochondrial metabolism,[28] has been linked to circadian rhythm stability in murine models.[29] PROSC dysfunction may impair mitochondrial adenosine triphosphate production,[30] altering both sleep-wake cycles and purine breakdown – creating a bidirectional loop where sleep disruption exacerbates hyperuricemia, and vice versa. This aligns with recent findings that circadian misalignment in gout patients correlates with poor urate control.[31]

  SDs often involve neuroinflammation, which may synergize with peripheral inflammation in gout through the neuronal-immune axis.[32] Our shared DEG KLF13, a transcription factor, is highly expressed in hypothalamic neurons and regulates pro-inflammatory cytokine production.[33] In sleep-deprived rodents, KLF13 upregulation in the hypothalamus triggers microglial activation, amplifying systemic inflammation. In gout, KLF13-mediated cytokine release may enhance crystal phagocytosis by macrophages, worsening joint inflammation. This suggests KLF13 acts as a molecular switch integrating central (neuroinflammatory) and peripheral (joint) pathological processes, a mechanism supported by studies showing hypothalamic-pituitary-adrenal axis dysregulation in comorbid gout patients.[34]

  Moreover, IL6R, encoding the interleukin-6 receptor, plays a central role in inflammatory signaling. Modulation of IL-6 levels is associated with both the pathogenesis of gout[35] and sleep fragmentation,[36] corroborating its role in disease comorbidity. These shared DEGs converge on the JAK/STAT signaling pathway and are key regulators of inflammation.[37] The JAK/STAT signaling pathway is also related to both the treatment of gout[38] and chronic OSA previously reported by other studies.[39] JAK/STAT signaling pathway activation induced by sleep deprivation promotes inflammation and tissue atrophy in skeletal muscles,[40] while traditional Chinese medicine modulates this pathway to reduce hyperuricemia and inflammation during gout treatment.[38] This dual role highlights JAK/STAT as a critical molecular hub linking sleep disruption with pathological processes in both skeletal muscle and metabolic disorders, such as gout.

  Additionally, the enrichment of transferase complexes involved in phosphorus-containing group transfer and histone methyltransferase complexes underscores the importance of epigenetic modifications and metabolic signaling in gout pathophysiology.[41] Notably, the involvement of cyclin-dependent kinases points to potential cross-talk between cell proliferation and inflammation, offering a mechanistic explanation for the chronic inflammatory state observed in gout patients.[42] DO enrichment analysis identified significant associations between shared gene sets and conditions. Although these diseases appear unrelated at 1st glance, they share common pathological features, including chronic inflammation, oxidative stress, and impaired tissue repair mechanisms. These findings suggest that SD-related gout may involve the systemic dysregulation of inflammatory[43] and metabolic pathways,[44] contributing to its association with other complex diseases. This observation underscores the importance of considering gout not merely as a localized joint disorder, but as part of a broader network of interconnected pathological states.

  ssGSEA revealed significant alterations in both the adaptive and innate immune compartments. Collectively, these observations suggest that the immune cell landscapes in SD and gout are distinctly different, potentially reflecting disease-specific mechanisms. The dysregulated B cell maturation observed in SD may exacerbate inflammatory processes when coupled with the Th2-driven immune response characteristic of gout, thereby contributing to the complexity of managing these comorbid conditions. Future research should aim to further dissect these immune profiles and their interactions, as well as explore how modulating specific immune cell populations could mitigate symptoms and improve outcomes in patients with both gout and SDs. Incorporating longitudinal studies and experimental validations is essential to confirm these hypotheses and translate our findings into clinically actionable insights.

  The integration of machine learning with functional enrichment analysis provides a robust framework for identifying diagnostic biomarkers and therapeutic targets for SD-related gout. This research will enable medical professionals and researchers to leverage machine learning approaches in advancing the diagnostic and therapeutic processes of SD-related gout by identifying the opportunities and challenges.[45] Future studies should focus on validating these findings in larger patient cohorts and experimental models to confirm the causal relationships between SD-related genes and gout pathogenesis. Longitudinal studies are needed to elucidate the temporal dynamics of these molecular interactions and their impact on disease progression. Furthermore, incorporating multi-omics data – including transcriptomics, proteomics, and metabolomics – could enhance understanding of the complex interplay among genetic predisposition, environmental factors, and disease manifestation.


## 5. Limitations
  This study presents significant findings regarding the molecular mechanisms linking SD-related genes to gout; however, it has several limitations.

  First, while our integrated machine learning framework provided robust predictions and insights into potential gout diagnostic biomarkers based on SD-related genes, the model’s performance and reliability depend heavily on input data quality and quantity. Limited or biased datasets may reduce generalizability to broader populations. Although effective for high-dimensional data, Naive Bayes algorithms may overemphasize noisy features in small datasets, further limiting external validity. Additionally, the lack of external validation in independent, multiethnic populations hinders clinical translation; incorporating multiethnic datasets and stricter regularization could improve model stability.

  Second, functional enrichment analyses identified key pathways and biological processes, but these methods are inherently hypothesis-generating. Experimental validation is thus needed to confirm the causal relationships suggested by our computational approach.

  Third, as both gout and SDs are multifactorial, other unmeasured factors – including environmental influences, lifestyle choices, and genetic variability – likely contribute to pathogenesis but were not captured in this study.

  Fourth, heterogeneity in the GEO datasets, particularly in sample types, introduces bias. Gout datasets (GSE160170, GSE178825) focused on peripheral blood mononuclear cells, while the SD dataset GSE98582 used whole blood (containing erythrocytes, platelets, etc). Gene expression profiles differ substantially between these sample types, potentially skewing DEG identification. Persistent batch effects – despite ComBat correction – due to differing microarray platforms also impair cross-dataset comparability. Future studies should prioritize uniform sample collection and multi-platform validation to mitigate this.

  Finally, several critical gaps remain: longitudinal studies are needed to clarify the temporal dynamics between SDs and gout development, as well as the long-term efficacy and safety of targeting identified pathways therapeutically; our analysis omitted clinical variables influencing gene expression, such as medication use, disease severity, and comorbidities; and confounders like obesity – linked to both conditions via purine metabolism and circadian rhythms – were unaccounted for due to unavailable BMI data. Integrating electronic health record data with transcriptomics in future studies would help disentangle these factors.


## 6. Conclusion
  This study provides a novel molecular framework for understanding gout-SD comorbidities and presents a diagnostic tool with potential clinical utility. The identified genes and pathways highlight inflammation and circadian dysregulation as central mechanisms. While further validation is needed, these findings lay the groundwork for precision medicine approaches to managing gout among patients with SD.


## Acknowledgments
  The authors gratefully acknowledge Gene Expression Omnibus (GEO; https://www.ncbi.nlm.nih.gov/geo/) for providing the publicly available datasets used in this study.


## Author contributions
  Conceptualization: Wenhua Yang.

  Formal analysis: Wenhua Yang, Fangfang Lu.

  Methodology: Wenhua Yang, Fan Yang, Fangfang Lu.

  Resources: Fangfang Lu.

  Writing – original draft: Wenhua Yang, Fan Yang, Fangfang Lu.

  Writing – review & editing: Wenhua Yang, Fan Yang, Fangfang Lu.

  Validation: Fangfang Lu.