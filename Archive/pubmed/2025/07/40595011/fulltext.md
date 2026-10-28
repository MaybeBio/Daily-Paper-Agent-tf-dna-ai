# Integrating machine learning and bioinformatics approaches to identify novel diagnostic gene biomarkers for diabetic mice


## Abstract
  Diabetes is a complex metabolic disorder, and its pathogenesis involves the interplay of genetic, environmental factors, and lifestyle choices. With the rising prevalence and increasing associated chronic complications, identifying and understanding the molecular mechanisms of diabetes has become an important direction in bioinformatics research. The aim of this study is the identification of diagnostic genes associated with streptozotocin (STZ)-induced diabetic mice. GSE179717 and GSE179718 gene expression datasets were downloaded from the Gene Expression Omnibus (GEO) database. Differentially expressed genes (DEGs) were identified by screening diabetic mice and controls. A total of 45 overlapping genes were recognized as potential DEGs across the two datasets. Next, Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) analysis were performed on the overlapping genes. Protein-protein interaction (PPI) networks were constructed to identify hub genes in the DEGs. After the application of Least absolute shrinkage and selection operator (LASSO), Random Forest analysis, three genes (Scd1, Sirt1 and Hmgb1) were identified as diagnostic genes. Real-time quantitative polymerase chain reaction (RT-qPCR) was supplied to detect the expressions of diagnostic genes in aged diabetic mice. In conclusion, the results of this study suggest that focusing on these genes may provide new targets for the diagnosis and treatment of diabetes.


## Introduction
  Diabetes is one of the defining medical challenges of the 21st century1. Elderly diabetes is an increasingly severe public health issue, particularly globally, as the aging population intensifies and the number of elderly diabetic patients continues to rise2. Elderly diabetes patients not only face the physiological and psychological challenges experienced by traditional diabetes patients but also encounter more complex pathological conditions due to the various physiological changes associated with the aging process3. The incidence of diabetes in the elderly population continues to rise, and the risk of related complications, such as cardiovascular disease, kidney injury, and neuropathy, has significantly increased4–6. Therefore, it is particularly important to explore the pathogenesis of elderly diabetes and its associated factors in depth.

  In biomedical research, bioinformatics analysis provides powerful tools for understanding elderly diabetes. These technologies effectively integrate high-throughput genomic sequencing, transcriptomic analysis approaches to identify key genes, pathways, and biomarkers associated with elderly diabetes7,8. By systematically analyzing the gene expression patterns and metabolic characteristics of elderly patients, researchers can uncover specific biological mechanisms that influence the onset and progression of diabetes, such as decreased insulin sensitivity, activation of chronic low-grade inflammation, and7,9,10.

  Furthermore, elderly patients face increased difficulty in the individualized management of diabetes treatment due to the presence of multiple comorbidities and complex medication regimens. By integrating bioinformatics approaches, it is possible to not only identify potential biomarkers for the disease but also provide data support for the formulation of personalized treatment strategies, thereby optimizing clinical intervention outcomes. This interdisciplinary research approach not only enhances our understanding of elderly diabetes but also offers new directions for future therapies.

  In this study, gene expression profiles were downloaded from the Gene Expression Omnibus (GEO), and the relationship between the expression of differentially expressed genes (DEGs) and diabetes in mouse models was examined using machine learning and bioinformatics. Additionally, Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment analyses were performed to investigate the pathophysiological features of the DEGs. Furthermore, a protein-protein interaction (PPI) network was established using Cytoscape for selected hub genes related to diabetes. Receiver Operating Characteristic (ROC) analyses were conducted to confirm the sensitivity and specificity of these hub genes in diabetes models. To validate the results obtained from the analyses, an elderly diabetes mouse model was established, and diagnostic genes (Sirt1, SCD1 and HMGB1) were detected through RT-qPCR to verify the findings. In conclusion, novel and reliable biomarkers for screening, diagnosis, and prognosis, as well as potential therapeutic targets for elderly diabetes, are provided by our findings.


## Materials and methods

### Data sources
  Microarray expression data (GSE179717 and GSE179718) was downloaded from the Gene Expression Omnibus (GEO) database (https://www.ncbi.nlm.nih.gov/geo/), representing a GPL6246 Affymetrix Mouse Gene 1.0 ST Array. GSE179717 includes 13 visceral fat tissues from 7 control mice and 6 STZ-treated mice. GSE179718 includes 12 skeletal muscle tissues from 7 control mice and 5 STZ-treated mice. The flow diagram of the work was shown in Fig. 1.

  Fig. 1Workflow chart of the present study.


### Screening of DEGs
  GEO2R (http://www.ncbi.nlm.nih.gov/geo/geo2r/) was used to screen the DEGs between STZ-treated mice and control mice in GSE179717 and GSE179718 datasets. The adjusted P-value < 0.05 and |Log fold change (FC)|>0.5 were set as the threshold criterion for statistical significance. The volcano map of DEGs was plotted in R software. The Heatmap package in R software was utilized to visualize the top 50 DEGs. Next, Venn diagram was utilized to analyze the overlapping of DEGs in two datasets (GSE179717 and GSE179718).


### GO and KEGG analysis of DEGs
  To investigate the biological function of DEGs, DAVID (https://david-d.ncifcrf.gov/home.jsp) online tool was utilized to perform Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway analysis. The GO analysis annotates gene function at three levels: Biological process (BP), cellular component (CC), and molecular function (MF). The P-value < 0.05 was statistically significant.


### Protein-protein interaction network and identification of hub genes
  The Search Tool for the Retrieval of Interacting Genes/Proteins (STRING, http://string-db.org/) was used to construct the protein-protein interaction (PPI) network of the 45 DEGs11. The PPI network was subsequently visualized by Cytoscape software12. The Molecular Complex Detection (MCODE)13 was used to screen the significant modules of the PPI network and then Cytohubba14 was used to determine the top hub genes.


### Expression analysis of hub genes by GSE179717 and GSE179718 dataset
  To increase the biological significance of the hub genes, the expression of these hub genes in both GSE179717 and GSE179718 dataset were visualized by GraphPad software through constructing the violin plot. Then, the expression of DEGs in both datasets were merge. Receiver operating characteristic (ROC) curves were used to evaluate the diagnostic ability of hub genes in these two datasets. The construction of ROC curve and the calculation of the area under the ROC curve (AUC) were finished in MedCalc Statistical Software version 14.8.1 (MedCalc Software Ltd, Ostend, Belgium). The statistical significance was set as P < 0.05.


### Identifcation of diagnostic genes
  Machine learning is an algorithm that enables computer programs to learn from data or past experiences and then optimize their performance. Least absolute shrinkage and selection operator (LASSO) and Random Forest analysis were performed to screen the hub genes using the ‘glmnet’ and ‘randomForest’ package in R software. We chose lasso analysis that includes penalty parameters and cross-validation, as it is a more effective method for evaluating high-dimensional data compared to traditional regression analysis. Additionally, the Random Forest was employed to classify the hub genes. The optimal number of variables is determined by calculating the average error rate, while the optimal number of trees is identified by selecting the configuration with the lowest error rate. Once these parameters are established, a random forest model is constructed to determine the feature importance scores for each hub gene. Genes with a Mean Decrease Gini Index greater than 0.25 are selected. The intersection of the results from the LASSO analysis and the Random Forest identifies the diagnostic genes for diabetes.


### Animal experiments and sample collection
  Six-week-old male C57BL/6 mice were purchased from the Laboratory Animal Center, Xiamen University (Xiamen, China). All mice were housed at 25 ± 2 °C with 55 ± 10% humidity and a 12-h light/dark cycle. Mice were divided randomly into two groups, the STZ-treated group and the healthy control group. STZ-treated group mice were given a high-fat diet (60.3 kcal%) for 8 weeks. Following this, a continuous injection of STZ (30 mg/kg) was administered intraperitoneally for 7 days. After 72 h, mice with fasting blood glucose levels ≥ 16.7 mmol/L will continue to be fed a high-fat diet for up to 24 months to establish an aged type 2 diabetes mouse model. The healthy control group received an intraperitoneal injection with the same dose of citrate bufer. Afer 24 months of experiments, mice were anesthetized with isofurane and sacrifced. Then, the skeletal muscle tissues were immediately removed, frozen in liquid nitrogen, and stored at -80 °C for further studies. All animal care and experimental procedures were approved by the Animal Ethics Committee of Xiamen University (Animal Ethics Approval No.: XMULAC20220126). All experimental procedures were conducted in strict compliance with the relevant guidelines and regulations established by the Institutional Animal Care and Use Committee of Xiamen University, and were performed in accordance with the ARRIVE guidelines for reporting animal research.


### RNA extraction and quantitative RT-PCR
  According to the manufacturer’s instructions, total RNA was extracted from the gastrocnemius muscle tissue using the Animal Tissue/Cell RNA Quick Extraction Kit (Heruibio, HRQ0272, China). The cDNA synthesis was conducted using HRbio™ III 1st Strand cDNA Synthesis SuperMix for qPCR (Heruibio, HRF0182, China). Using GAPDH as a reference, we performed quantitative RT-PCR with HRbio™ qPCR SYBR Green Master Mix (Heruibio, HRF0052, China) in the ABI QuantStudio6 (Thermo Fisher Scientific, USA). The 2-∆∆Ct method was applied to calculate the relative expression level of mRNA. The primer pairs used for amplifcation were as follows: Scd1 F: 5’-CTCCCTCCGGAAATGAACGAG-3’, R: 5’-CCTGATAGGTGGGGTCGTGA-3’; Sirt1 F: 5’-ACCACCAAATCGTTACATATTCCA-3’, R: 5’-CCGTATCATCTTCCAAGCCATT-3’; Hmgb1 F: 5’-AAGGCTGACAAGGCTCGTT-3’, R: 5’-TGATTTTGGGGCGGTACTCA-3’; GAPDH F: 5’-TGGAAAGCTGTGGCGTGATG-3’, R: 5’-TACTTGGCAGGTTTCTCCAGG-3’.


### Statistical analysis
  All statistical analyses in this study were executed using R software. By default, a significance level of P ≤ 0.05 was regarded as statistically significant, and all P-values were evaluated using a two-tailed test.


## Results

### DEGs screening
  After screening with the threshold of an adjusted P-value < 0.05 and |logFC|>0.5, 331 DEGs (155 upregulated and 176 downregulated) were identified in the GSE179717 dataset, 578 DEGs (282 upregulated and 296 downregulated) were identified in GSE179718. The volcano map of DEGs is shown in Fig. 2A-B. The heatmap for the top 50 DEGs is displayed in Fig. 2C-D. In total, 45 DEGs were shared between these two datasets, as identified through venn diagram analyses (Fig. 2E).

  Fig. 2DEGs in the merged datasets. (A, B) The volcano map of DEGs in GSE179717 and GSE179718. (C, D) Heatmap of top 50 DEGs in GSE179717 and GSE179718. (E) Venn diagram of DEGs from GSE179717 and GSE179718.


### Functional enrichment analysis
  The 45 DEGs in middle overlapping section of venn diagram were used for GO and KEGG analysis with the DAVID (https://david-d.ncifcrf.gov/home.jsp) online tool. GO enrichment results indicated that the 45 DEGs were enriched in ‘fatty acid biosynthetic process’, ‘unsaturated fatty acid biosynthetic process’, ‘cellular response to insulin stimulus’, ‘lipid metabolic process’ and ‘positive regulation of cysteine-type endopeptidase activity involved in apoptotic process’ in BP terms (Fig. 3A). In terms of CC, ‘the terms integral component of endoplasmic reticulum membrane’, ‘cytosol’, ‘intracellular membrane-bounded organelle’, ‘cytoplasm’ and ‘nucleolus’ (Fig. 3A). The MF terms of the DEGs were ‘palmitoyl-CoA 9-desaturase activity’, ‘stearoyl-CoA 9-desaturase activity’, ‘DNA binding’, ‘oxidoreductase activity, acting on paired donors, with oxidation of a pair of donors resulting in the reduction of molecular oxygen to two molecules of water’ and ‘oxidoreductase activity’ (Fig. 3A). Moreover, KEGG analysis demonstrated that the 45DEGs was enriched in ‘AMPK signaling pathway’, ‘Alcoholic liver disease’, ‘Fatty acid metabolism’, ‘Biosynthesis of unsaturated fatty acids’ and ‘Terpenoid backbone biosynthesis’ (Fig. 3B).

  Fig. 3Gene ontology and KEGG enrichment analysis. (A) Biological process, Cellular component and Molecular function. (B) KEGG enrichment analysis.


### PPI network analysis and identifcation of hub genes
  45 DEGs were used to construct a PPI network using the STRING database. The combined score was > 0.4. Then 45 DEGs were visualized using Cytoscape3.7.2(Fig. 4A). As is shown in Fig. 5A, the PPI network comprised 18 nodes and 64 edges. Using the MCODE plug-in in Cytoscape, two module was determined. The first one module (score = 5.6) included 6 nodes and 28 edges (Fig. 4B). The second one module (score = 3.0) included 3 nodes and 6 edges (Fig. 4C). The top ten hub genes obtained by Degree, in the cytoHubba plug-in, are shown in Fig. 4D.

  Fig. 4PPI network and hub gene. (A) PPI network. (B, C) The most two significant modules. (D) The top 10 hub genes obtained by Degree.

  Fig. 5Violin diagrams for the expressions of top 10 hub genes in GSE179717. (A) Sirt1, (B) Scd1, (C) Fasn, (D) Lep, (E) Elovl6, (F) Dgat2, (G) Myc, (H) Nfkbia, (I) Scd2 and (J) Hmgb1. Each point represents a sample. There are 6 STZ-treated samples and 7 control samples.


### Expression analysis of hub genes by GSE179717 and GSE179718 dataset
  After overlapping with DEGs, the top 10 hub genes: Stearoyl-Coenzyme A desaturase 1 (Scd1), fatty acid synthase (Fasn), ELOVL family member 6, elongation of long chain fatty acids (Elovl6), diacylglycerol O-acyltransferase 2 (Dgat2), Leptin (Lep), stearoyl-Coenzyme A desaturase 2 (Scd2), sirtuin 1 (Sirt1), nuclear factor of kappa light polypeptide gene enhancer in B cells inhibitor, alpha (Nfkbia), myelocytomatosis oncogene (Myc) and high mobility group box 1 (Hmgb1) was selected. As illustrated in Figs. 5 and 6, the differences in expression levels of hub genes between the two datasets were statistically significant. Scd1, Sirt1, Myc, Nfkbia, and Hmgb1 exhibited elevated expression levels in STZ-treated mice. Conversely, Fasn, Elovl6, Dgat2, Lep, and Scd2 demonstrated higher expression in control mice. ROC curve analysis revealed that the 10 hub genes exhibited strong discriminative power between STZ-treated mice and control mice (Fig. 7).

  Fig. 6Violin diagrams for the expressions of top 10 hub genes in GSE179718. (A) Sirt1, (B) Scd1, (C) Fasn, (D) Lep, (E) Elovl6, (F) Dgat2, (G) Myc, (H) Nfkbia, (I) Scd2 and (J) Hmgb1. Each point represents a sample. There are 5 STZ-treated samples and 7 control samples.

  Fig. 7ROC curves of the hub genes in merged datasets (GSE179717 and GSE179718). (A) Sirt1, (B) Scd1, (C) Fasn, (D) Lep, (E) Elovl6, (F) Dgat2, (G) Myc, (H) Nfkbia, (I) Scd2 and (J) Hmgb1.


### Identifcation and validation of diagnostic genes
  We screened out diagnostic genes from 10 hub genes by LASSO analysis and Random Forest analysis. In the LASSO analysis, a total of five hub genes were selected (Fig. 8A-B). On the other hand, the Random Forest analysis identifed six hub genes with a relative importance greater than 0.25 (Fig. 8C-D). These diagnostic genes are listed in Table 1. By considering the results from both algorithms, three signature genes were ultimately determined: Scd1, Sirt1 and Hmgb1 (Fig. 8E). Base on the quantitative RT-qPCR experiment, the mRNA expression level of Scd1, Sirt1 and Hmgb1 were detected in the muscle tissue from STZ-treated mice and control mice. The results indicated that the expression levels of Scd1 and Hmgb1 were upregulated in the STZ-treated group compared to the control group (Fig. 9A-C), while the expression of Sirt1 were downregulated (Fig. 9B).

  Fig. 8Machine learning algorithms for identifying hub genes. (A) The LASSO plot illustrates how the coefficients for parameters decrease in size as the penalty parameter k increases. (B) The penalty plot of LASSO displays error bars representing the standard errors. (C) Confidence intervals for the error rate in the Random Forest model are presented. (D) The relative importance of genes is more than 0.5 in Random Forest. (E) The interaction of the LASSO and Random Forest algorithms for diagnostic genes.

  Table 1The diagnostic genes screened out through LASSO and random forest analysis.LASSO analysisRandom forest algorithmsScd1, Myc, Sirt1, Hmgb1, Dgat2Scd1, Sirt1, Nfkbia, Hmgb1, Fasn, Lep

  Fig. 9Validation of diagnostic genes. (A) Relative mRNA level of Sirt1 in controls vs. STZ group. (B) Relative mRNA level of Scd1 in controls versus STZ group. (C) Relative mRNA level of Hmgb1 in controls vs. STZ group. (**P < 0.01, ***P < 0.001, ****P < 0.0001).


## Discussion
  The present study leverages an integrative approach combining bioinformatics and machine learning to uncover novel diagnostic biomarkers for diabetes, particularly focusing on STZ-induced diabetic mice. The identification of DEGs across two datasets (GSE179717 and GSE179718) revealed a subset of 45 overlapping genes, which were further analyzed through GO and KEGG pathways. This enrichment analysis highlighted significant biological processes and pathways, such as fatty acid biosynthesis, insulin response, and AMPK signaling, underscoring their potential roles in diabetes pathogenesis.

  The construction of a PPI network and subsequent module analysis pinpointed key hub genes, including Scd1, Sirt1, Myc, Nfkbia, and Hmgb1, which showed elevated expression in STZ-treated mice. Conversely, genes like Fasn, Elovl6, Dgat2, Lep, and Scd2 were more highly expressed in control mice. This differential expression pattern suggests a complex interplay of metabolic and regulatory pathways in diabetes.

  Machine learning techniques, specifically LASSO and Random Forest analyses, were instrumental in narrowing down the list of hub genes to three diagnostic genes: Scd1, Sirt1, and Hmgb1. These genes not only exhibited significant differential expression but also demonstrated strong discriminative power between STZ-treated and control mice, as evidenced by ROC curve analysis. We found that the expression levels of these genes showed significant differences between healthy control mice and diabetic mice, which were further validated through RT-qPCR.

  Scd1(stearoyl-Coenzyme A desaturase 1), a key enzyme in fatty acid metabolism, has been previously implicated in insulin resistance and diabetes. SCD1 serves as a key regulator of fuel metabolism and may be a valuable therapeutic target for managing obesity and the progression of related metabolic disorders, such as type 2 diabetes and hepatic steatosis15. SCD1 catalyzes the production of monounsaturated fatty acids (MUFAs), primarily oleate and palmitoleate, which play a crucial role in regulating weight gain in response to high-carbohydrate diets.

  Sirt1 (Sirtuin 1) is an NAD + dependent deacetylase that belongs to the sirtuin family of silent information regulator proteins16. SIRT1 is involved in various biological processes within the cells, including DNA repair, cell cycle regulation, inflammatory responses, and metabolic regulation. Additionally, AMPK enhances SIRT1 activity by augmenting intracellular NAD + levels17. Intriguingly, SIRT1 has the capacity to indirectly stimulate the AMPK signaling cascade amidst chronic metabolic adjustments18. Conversely, AMPK can also directly facilitate the phosphorylation of SIRT1, consequently potentiating the enzymatic activity of the SIRT1 deacetylase19. As a result, AMPK emerges as a pivotal regulator of SIRT1 function. This finding aligns with the KEGG pathway analysis of DEGs.

  Hmgb1 (High Mobility Group Box 1) is a nuclear protein that has gained significant attention in the field of diabetes research due to its role in inflammation, apoptosis, and tissue repair20,21. The relationship between HMGB1 and diabetes is multifaceted, with evidence suggesting that HMGB1 may contribute to both the development and progression of diabetes. For example, HMGB1 has been implicated in the inflammatory response, which is a key feature of both type 1 and type 2 diabetes. It can activate immune cells and promote the release of pro-inflammatory cytokines, contributing to the autoimmune destruction of beta cells in type 1 diabetes and the inflammatory processes that lead to insulin resistance in type 2 diabetes22. HMGB1 can increase oxidative stress and endoplasmic reticulum (ER) stress response, which is a common pathway in the pathogenesis of diabetes23–26.

  The findings of this study provide a robust framework for understanding the molecular underpinnings of diabetes and offer potential biomarkers for early diagnosis and therapeutic targeting. Future studies could validate these biomarkers in human cohorts and explore their functional roles through experimental models. Additionally, the integration of multi-omics data could provide a more comprehensive understanding of the disease mechanisms, paving the way for personalized medicine approaches in diabetes management. Conclusively, Scd1, Sirt1 and Hmgb1 were determined to be potential biomarkers in diabetes.


## Acknowledgements
  The authors would like to thank the editor and reviewers for their valuable comments and acknowledge GEO database for providing their platform and contributors for uploading their meaningful datasets.