# Bioinformatic identification of genes and mechanisms related to acute respiratory distress syndrome and sepsis: A bioinformatic study


## Abstract
  We hypothesized that acute respiratory distress syndrome (ARDS) and sepsis share hypoxia-related transcriptional signatures that reflect overlapping immunopathogenic mechanisms. This study aimed to identify shared hypoxia-related genes and associated regulatory features using bioinformatic analyses. Gene expression datasets GSE28750 and GSE76293 were analyzed separately after within-dataset normalization. Differentially expressed genes (DEGs) were defined using |logFC| > 1 and adjusted P < .05. Hypoxia-related genes were compiled from GeneCards, PubMed-curated studies, and molecular signatures database, harmonized by official gene symbols, and intersected with common DEGs from both datasets to identify hypoxia-related DEGs (HRDEGs). Gene ontology enrichment, gene set enrichment analysis, interaction network analysis, immune infiltration analysis, and protein-protein interaction analysis using STRING with a minimum interaction score of 0.400 were subsequently performed. Eleven HRDEGs were identified: capping actin protein, gelsolin-like, CKS2, CLU, FLVCR1, FUNDC1, HPSE, LCN2, MAPK14, PFKFB3, PLAC8, and TDRD9. Gene ontology enrichment suggested involvement in cellular iron ion homeostasis- and iron ion transport-related processes. Gene set enrichment analysisindicated enrichment of hypoxia- and inflammation-related pathways. Under the stricter STRING threshold (score ≥ 0.400), the protein-protein interaction network showed a limited but biologically plausible interaction pattern among the HRDEGs. Predicted miRNA, ribonucleic acid-binding protein, transcription factor, drug, and immune infiltration analyses further suggested that these genes may participate in inflammatory and immune regulatory processes relevant to ARDS and sepsis. This bioinformatic study identified shared hypoxia-associated genes in ARDS and sepsis and generated testable hypotheses regarding their possible regulatory and immunologic relevance. These findings should be interpreted as exploratory and warrant experimental validation in future studies.


## 1. Introduction
  Acute respiratory distress syndrome (ARDS) is a life-threateninglung illness characterized by intense inflammation and the buildup of fluid in the small air sacs of the lungs, resulting in severe respiratory failure.[1–3] This syndrome often occurs as a result of several underlying disorders, such as sepsis. Sepsis is a dangerous infection that can cause uncontrolled immune responses, leading to extensive inflammation and malfunction of multiple organs.[4,5] In the case of ARDS, sepsis can trigger an intensified immune response, which worsens lung damage and impairs the lungs’ ability to oxygenate.

  One common complication of ARDS and sepsis is hypoxia, which is the lack of oxygen to the body tissues. In ARDS, fluid-filled alveoli significantly impede gaseous exchange, leading to hypoxia.[6,7] Simultaneously, sepsis can cause hypoxia by reducing cardiac output and obstructing microcirculation, hindering the transport of oxygen to critical tissues.

  Hypoxia, ARDS, and sepsis all interact in complex ways.[8] Hypoxia can be precipitated by either sepsis or ARDS, while the latter can sometimes appear as a consequence of the former. Despite this, the variability in hypoxia severity between ARDS and sepsis patients (and its subsequent impact on clinical outcomes and therapeutic strategies) remains poorly elucidated.[9,10] While existing literature has extensively documented the individual effects of ARDS and sepsis on hypoxia, comprehensive investigations into how these conditions collectively influence hypoxia progression and intensity are scant. This lacuna underscores the need for more detailed studies to enhance our prognostic abilities and refine patient management for those afflicted with both ARDS and sepsis.

  In response to this need, our study employed bioinformatic analyses on ARDS and sepsis datasets to delineate their association with hypoxia. We hypothesized that ARDS and sepsis share a core set of hypoxia-related transcriptional signatures that may reflect overlapping immunopathogenic mechanisms. By integrating differential expression analysis, enrichment analysis, interaction network analysis, and immune infiltration profiling, we identified several genes linked to these pathologies and generated a framework for future mechanistic validation rather than definitive causal inference.


## 2. Materials and methods

### 2.1. Data download
  The Gene Expression Omnibus (GEO) database was queried to obtain the GSE28750 and GSE76293 gene expression profile datasets (Table 1). GSE28750 contains 41 samples, including sepsis, postsurgical sepsis, and matched healthy controls. To preserve a clinically cleaner sepsis-versus-control comparison and reduce the confounding influence of recent surgical trauma, only the 10 sepsis samples and 20 healthy controls were included in the present analysis, whereas the 11 postsurgical sepsis samples were not analyzed. GSE76293 contains 94 samples, including ARDS, matched healthy volunteers, and samples exposed to GM-CSF or a PI3K inhibitor. To evaluate the natural untreated ARDS transcriptional state, only 12 ARDS samples and 12 matched healthy volunteers samples were retained, while treatment-exposed samples were excluded from downstream analysis.

  Hypoxia-related genes were systematically identified using multiple sources to ensure broad but curated coverage. First, the GeneCards database was queried using the term “Hypoxia,” and protein-coding genes with a relevance score > 1.5 were retained as a moderate relevance threshold to reduce weakly annotated hits while preserving genes with established hypoxia associations.[11] Additional genes were obtained from recent PubMed-reported hypoxia studies and the BUFFA_HYPOXIA_METAGENE set from the molecular signatures database. Gene symbols from the 3 resources were harmonized to official gene symbols, and duplicate entries were removed, yielding 1337 unique hypoxia-related genes for downstream intersection analysis (Table 2). This study relied exclusively on public-domain de-identified datasets and therefore did not require separate ethics review or participant consent.


### 2.2. Differentially expressed genes (DEGs) analysis
  To pinpoint differential genes associated with sepsis and ARDS, normalization and differential expression analyses were conducted on datasets GSE28750 (Table 3) and GSE76293 (Table 4) using the limma package.[12] Each GEO series was processed independently with background correction and within-dataset normalization. Because the 2 datasets were not merged into a single expression matrix, cross-dataset batch correction methods such as ComBat were not applied. Sample quality was assessed using expression distribution plots and principal component analysis (PCA) within each dataset, and no additional outliers were removed beyond the predefined inclusion criteria described above. Using |logFC| > 1 and adjusted P < .05, DEGs were identified between the normal and sepsis groups in GSE28750 and between the ARDS and normal groups in GSE76293.

  In addition, genes that showed differential expression (Co-DEGs) in both datasets were located using a Venn diagram. To further investigate their possible functions in both situations, these Co-DEGs were subsequently intersected with the hypoxia-related genes that had been found. Visualization of DEGs was facilitated through the use of volcano plots and heatmaps to illustrate their expression patterns and significance levels.


### 2.3. Functional enrichment analysis
  Using the clusterProfiler tool in R, functional implications of the hypoxia-related DEGs (HRDEGs) were examined by gene ontology (GO) analysis.[13] With a false discovery rate (q-value) below 0.05 and an adjusted P value (P_adj) < .1, significant GO keywords were discovered. We corrected the P values using the Benjamini-Hochberg approach.


### 2.4. Gene set enrichment analysis (GSEA)
  For the purpose of evaluating enrichment within the c2.all.v2022.1.Hs.symbols.gmt gene set from molecular signatures database, GSEA was executed on all identified DEGs using the clusterProfiler package.[14] The analysis was performed with a 2023 seed, 1000 permutations, and gene set sizes ranging from 10 to 500 genes. Adjusted P values below .05 and false discovery rate values below 0.25 were considered statistically significant.[15]


### 2.5. Protein-protein interaction (PPI) network analysis
  The STRING database was used to generate PPI networks with a minimum required interaction score of 0.400, corresponding to medium confidence. The resulting network was visualized in Cytoscape (version 3.9.1) to explore interaction patterns among HRDEGs under a more stringent confidence threshold.[16,17]


### 2.6. Construction of interaction networks
  For constructing interaction networks involving miRNAs, ribonucleic acid (RNA)-binding protein (RBPs), transcription factor (TFs), and drugs, we employed multiple specialized databases. miRNA interactions were analyzed using the miRDB database, focusing on targets with a Target Score > 80 to establish the miRNA interaction network.[18] In addition, the abundant information on miRNA-ncRNA, miRNA-mRNA, and RBP interactions gleaned from cross-linking immunoprecipitation-seq and degradome sequencing was made use of by the encyclopedia of RNA interactomes platform.[19] This platform facilitated the identification of interactions with a high degree of confidence, setting thresholds of a clusterNum > 4 and clipExpNum > 4 for selecting significant mRNA-RBP pairs.[20]

  Through the utilization of the human transcription factor target database, the TFs that interact with hub genes were identified. Cytoscape was used to display the mRNA-TF and mRNA-drug interaction networks. Using the Comparative Toxicogenomics Database, we were able to anticipate drug and molecular compound interactions, with a particular emphasis on chemicals that demonstrate strong relevance to the genes that were identified.[21]


### 2.7. Immune infiltration analysis
  Immune cell composition in the context of sepsis and ARDS was quantified using the cell-type identification by estimating relative subsets of RNA transcripts algorithm, which allows detailed immune cell profiling from gene expression data. Immune infiltration was evaluated separately in GSE28750 and GSE76293 rather than after physical merging of the 2 datasets, thereby preserving the original series-specific expression structure.[22]


### 2.8. Statistical analysis
  Data processing and statistical analyses were performed using R software. Continuous variables were expressed as mean ± standard deviation. Two-group comparisons were performed using the Wilcoxon rank-sum test, and correlations were evaluated using Spearman rank correlation method. A 2-sided P < .05 was considered statistically significant.


## 3. Results

### 3.1. Data standardization in sepsis and ARDS studies
  The normalization process of GSE28750 and GSE76293 was performed using the limma package, as illustrated in the technology roadmap (Fig. 1). Detailed normalization results are shown in Figure 2A–2D. The final GSE28750 analytical set comprised 30 samples, including 20 healthy controls and 10 sepsis samples. The final GSE76293 analytical set comprised 24 samples, including 12 matched healthy volunteers and 12 ARDS samples.

  After within-dataset normalization, expression distributions became comparable across samples in each series, supporting downstream analysis while avoiding overstatement regarding cross-dataset batch correction. Because the 2 cohorts were analyzed independently rather than merged, the purpose of normalization was to reduce technical variation within each dataset rather than to eliminate inter-study batch effects.


### 3.2. Differential gene analysis between sepsis and ARDS
  PCA was used to reduce the dimensionality of the GSE28750 and GSE76293 expression matrices and to visualize variance between disease and control groups within each dataset. The PCA plots (Fig. 3A and 3B) demonstrated separation between case and control samples after normalization, supporting the analytical distinction of the comparison groups within each GEO series.

  Subsequently, limma was used to identify DEGs between disease and control groups in both datasets. In GSE28750, 826 of 21,655 genes met the predefined thresholds, including 447 upregulated and 379 downregulated genes in sepsis relative to controls (Fig. 3C). In GSE76293, 349 of 21,629 genes were differentially expressed, including 195 upregulated and 154 downregulated genes in ARDS relative to controls. Although the sepsis dataset yielded a relatively large number of DEGs for a modest sample size, downstream interpretation was restricted to genes that were reproducible across the independent ARDS dataset and that also overlapped with the curated hypoxia-related gene list, thereby reducing the likelihood of overinterpretation.

  To focus on the impact of hypoxia in these conditions, we intersected the DEGs from both datasets, identifying 173 common DEGs between the GSE28750 and GSE76293 datasets, depicted in a Venn diagram (Fig. 3E). Further refinement using the list of hypoxia-related genes resulted in the identification of 11 HRDEGs common to both sepsis and ARDS, namely capping actin protein, gelsolin-like (CAPG), CKS2, CLU, FLVCR1, FUNDC1, HPSE, LCN2, MAPK14, PFKFB3, PLAC8, and TDRD9. To delve further into these HRDEGs’ expression profiles, we used heatmaps to show how the illness and normal groups in the 2 datasets differed in gene expression (Figs. 3F–3H).


### 3.3. HRDEGs correlation analysis in sepsis and ARDS
  Correlation analyses of the 11 HRDEGs, namely CAPG, CKS2, CLU, FLVCR1, FUNDC1, HPSE, LCN2, MAPK14, PFKFB3, PLAC8, and TDRD9, were conducted within the GSE28750 and GSE76293 datasets using Spearman rank correlation coefficient. The results for GSE28750 are visualized in a heatmap (Fig. 4A), indicating that most HRDEGs correlations were statistically significant (P < .05). Similarly, correlations within the GSE76293 dataset also demonstrated statistical significance for most gene pairs, as shown in the corresponding heatmap (Fig. 4D).

  Further detailed analysis was represented through correlation scatter plots for gene pairs with consistent correlation trends. Specifically, the correlation between FLVCR1 and PLAC8, as well as PLAC8 and TDRD9 in the GSE28750 dataset, showed strong positive and negative relationships, respectively (Figs. 4B and 4C). In the GSE76293 dataset, similar patterns were observed, with FLVCR1 and PLAC8 showing a strong negative correlation (r = −0.784, P < .001, Fig. 4E), and PLAC8 and TDRD9 displaying a strong positive correlation (r = 0.790, P < .001, Fig. 4F).

  These correlations may reflect coordinated regulation among HRDEGs and provide hypotheses about gene modules that could influence ARDS and sepsis biology. Further functional validation is needed before these relationships can be interpreted mechanistically.


### 3.4. HRDEGs expression difference analysis
  The 11 HRDEGs’ expression levels were compared in the 2 datasets, analyzing the disease group and the control group separately. A comparison of the normal and sepsis groups in the GSE28750 dataset using the Wilcoxon rank-sum test showed statistically significant variations in expression across the 11 HRDEGs (Fig. 5A).

  The GSE76293 dataset, on the other hand, compared the normal and ARDS groups using the identical HRDEGs. Figure 5B shows that, in comparison to other HRDEGs, CKS2 and LCN2 had very significant expression changes, suggesting that these genes may play a role in the pathogenesis of ARDS.


### 3.5. HRDEGs functional enrichment analysis
  To further understand the 11 HRDEGs and the many biological processes, cellular components, and molecular functions they contribute to, we ran a GO analysis on each (Table 5). The study found that these genes are involved in many biological processes, including transport of iron coordination entities, differentiation of brown fat cells, transport of iron ions, homeostasis of iron ions in cells, and regulation of embryonic growth. Within the secretory granule lumen, the cytoplasmic vesicle lumen, and certain granules, HRDEGs were shown to be significantly more abundant in comparison to other cellular components. Some of the important molecular roles were binding macrolides, activating cyclin-dependent protein serine/threonine kinase, binding carbohydrate phosphate, and sugar phosphatase.

  To visually represent these findings, we employed bubble and network diagrams to illustrate the complex interactions and enriched categories based on GO analysis (Figs. S1A–S1D, Supplemental Digital Content 1). Additionally, we integrated the logFC from the differential expression analysis into the GO enrichment results to calculate a z-score for each gene, highlighting the relative importance of each gene within the enriched GO terms based on their expression changes. The integrated results were displayed in a circle graph for the GSE28750 dataset and in a chord graph for the GSE76293 dataset, providing a clear visualization of gene importance and interactions (Figs. S1E and S1F, Supplemental Digital Content 1).


### 3.6. GSEA enrichment analysis of GSE28750 and GSE76293 datasets
  GSEA was used to evaluate how gene expression influences the pathogenesis of sepsis and ARDS in the GSE28750 and GSE76293 datasets. The GSE28750 dataset revealed significant enrichment of DEGs in pathways linked to coronavirius disease 2019 (COVID-19) and hypoxia. Notably, the Blanco Melo pathway indicated upregulation in COVID-19 severe acute respiratory syndrome coronavirus 2 positive lung tissue, the Mense pathway highlighted hypoxia upregulation, the Gross pathway involved hypoxia regulation via HIF1A downregulation, and the Buffa Hypoxia Metagene showed marked involvement (Figs. S2B–S2E, Supplemental Digital Content 2).

  Similarly, in the GSE76293 dataset, significant enrichment was observed in pathways associated with COVID-19 and inflammatory responses. Key pathways included Blanco Melo for COVID-19 severe acute respiratory syndrome coronavirus 2 positive patient lung tissue, Manne for combined COVID-19 cohorts versus healthy donor platelets, and Nemeth for inflammatory response to lipopolysaccharide (Figs. S2G–S2J, Supplemental Digital Content 2).

  To illustrate the overlap and unique pathway contributions in sepsis and ARDS, we constructed a Venn diagram (Fig. S2K, Supplemental Digital Content 2). This revealed overlaps in general inflammatory and disease-specific pathways, with additional unique enrichments in lesser-known pathways such as Osman Bladder Cancer Down, Jison Sickle Cell Disease Down, and Lee Differentiating T Lymphocyte pathways. These results suggest shared and distinct molecular mechanisms underlying sepsis and ARDS, enhancing our understanding of their pathobiology and potential therapeutic targets.


### 3.7. Interaction network analysis of HRDEGs, mRNA-miRNA, mRNA-TF, and mRNA-drugs
  We conducted a multilevel interaction analysis to investigate regulatory features associated with HRDEGs in ARDS and sepsis. Using STRING with a minimum interaction score of 0.400, we obtained a more stringent PPI network for the 11 HRDEGs (Fig. S3A, Supplemental Digital Content 3). Under this threshold, only a subset of genes displayed medium-confidence protein associations, indicating that the updated network should be interpreted as a conservative representation of the most supported interactions rather than as evidence of a dense hub structure.

  In addition, miRNA interactions were predicted for the HRDEGs using the miRDB database. This analysis yielded an mRNA-miRNA interaction network consisting of 5 genes (CKS2, FLVCR1, MAPK14, PFKFB3, and TDRD9) and 49 miRNA molecules, forming 60 predicted interaction pairs (Fig. S3B, Supplemental Digital Content 3, Table S1, Supplemental Digital Content 4). RBP interactions were then explored using the encyclopedia of RNA interactomes database, revealing high-confidence connections involving 7 genes and 24 RBPs, as detailed in Table S2, Supplemental Digital Content 5 (Fig, S3C, Supplemental Digital Content 3).

  TF interactions were also analyzed using CHIPBase and human transcription factor target databases, resulting in a network involving 9 genes and 126 TFs, with CAPG showing the most extensive interactions (Fig. S3D, Supplemental Digital Content 3, Table S3, Supplemental Digital Content 6). Lastly, using the Comparative Toxicogenomics Database, we explored potential drugs targeting these genes, identifying 36 drugs or molecular compounds, with a significant focus on LCN2 (Fig. S3E, Supplemental Digital Content 3, Table S4, Supplemental Digital Content 7).

  Taken together, these interaction networks suggest that HRDEGs may participate in multilayered regulatory processes relevant to ARDS and sepsis. Because these networks are prediction-based and generated in silico, they should be viewed as hypothesis-generating resources for future mechanistic and therapeutic studies rather than as confirmatory evidence.


### 3.8. Immune infiltration analysis in sepsis and ARDS datasets
  After removing immune cell types with zero estimated proportions, we used the cell-type identification by estimating relative subsets of RNA transcripts method to assess the correlation between gene expression data from the GSE28750 sepsis dataset and 22 immune cell types. The analysis revealed intricate patterns of 19 immune cell types, illustrated in a heatmap (Fig. S4A, Supplemental Digital Content 8). Various immunological functions were shown by the significant correlations found between the expression of 5 HRDEGs and 6 different types of immune cells (Fig. S4B, Supplemental Digital Content 8).

  In the ARDS dataset (GSE76293), a similar approach revealed correlations between immune cell infiltration and HRDEG expression. After excluding cells with zero infiltration, we analyzed the presence of 17 different immune cell types across samples. This analysis highlighted how immune cells correlate with disease mechanisms in ARDS, depicted in a histogram for each sample type (Fig. S4C and S4D, Supplemental Digital Content 8). Notable findings include significant correlations of M0 macrophages with HPSE and MAPK14; naive CD4 T cells with MAPK14; and a strong interaction between gamma delta T cells and MAPK14, suggesting a crucial role in the immune response to ARDS. Additionally, gamma delta T cells exhibited a strong negative correlation with FLVCR1, emphasizing its unique immunological influence compared to other HRDEGs.

  These findings further illustrate the complex interplay between immune cell dynamics and HRDEG expression in ARDS. They provide candidate immune-associated processes for subsequent validation, but they do not by themselves establish causality or immediate therapeutic actionability.


## 4. Discussion
  ARDS is a serious syndrome characterized by acute respiratory failure and severe hypoxemia.[1] In the present study, hypoxia was used as a biologically plausible entry point to examine shared transcriptomic features between ARDS and sepsis. By analyzing 2 public datasets independently and then focusing on overlapping signals, we identified 11 HRDEGs that may represent convergent responses across these clinically related but distinct conditions.

  Several of the identified genes, including CAPG, CKS2, LCN2, MAPK14, and HPSE, have prior links to inflammatory regulation, neutrophil activity, macrophage biology, or cellular stress responses.[1,2,23] In our analysis, these genes were associated with immune cell infiltration patterns and with enrichment terms related to iron handling and inflammatory stress. These observations support the possibility that hypoxia-related transcriptional programs participate in the immunopathology of ARDS and sepsis, but they should be interpreted as associative rather than causal.

  The interaction analyses further extend this hypothesis-generating framework. The miRNA, RBP, TF, and drug networks were derived from public prediction and curation resources, and therefore they indicate putative rather than experimentally confirmed regulatory relationships. Likewise, the updated STRING network obtained under a score threshold of 0.400 intentionally favors specificity over density and should be read as highlighting the most supported interactions among HRDEGs. Together, these analyses provide a set of candidate regulatory axes for future validation.

  An important strength of the study is that candidate genes were not selected from a single dataset alone. Instead, differential expression was first established within each GEO series and then restricted to overlapping signals that also intersected with a curated hypoxia-related gene set. This design reduced the chance that a single-cohort artifact would dominate interpretation. Even so, the current findings are best positioned as a resource for follow-up studies rather than a basis for immediate translational claims.

  The therapeutic modulation of these HRDEGs remains a critical frontier. Given that hypoxia significantly shapes the immune microenvironment, strategies aimed at oxygen-sensing pathways or metabolic reprogramming may offer new avenues to overcome treatment resistance in ARDS and sepsis.[24] Furthermore, the intricate cross-talk between hypoxia and programmed cell death mechanisms (including pyroptosis and iron-mediated damage) suggests a shared molecular foundation that warrants deeper mechanistic exploration.[25] By refining the bioinformatic framework established in our preliminary research, this study identifies a consolidated set of regulatory axes that may serve as functional checkpoints.[26] These findings provide a prioritized list of candidate markers for future validation, ultimately aiming to improve precision diagnostics and clinical outcomes in critically ill patients.


### 4.1. Limitations
  This study has several limitations. First, the sample sizes were modest and the 2 GEO datasets were imbalanced in composition, which may have increased sampling variability. Second, the cohorts were derived from different studies with different clinical contexts, and although the datasets were intentionally analyzed separately, sample heterogeneity cannot be completely excluded. Third, the analyses were based on microarray data, which are constrained by probe coverage, platform-specific noise, and limited dynamic range compared with newer sequencing approaches. Fourth, the interaction networks and immune infiltration analyses were computational inferences from public resources and were not experimentally validated. Finally, the absence of granular clinical metadata prevented direct association of the identified signatures with severity, outcome, or treatment response.


## 5. Conclusions
  Through transcriptomic analysis, we identified shared hypoxia-related genes in ARDS and sepsis and characterized their associated enrichment patterns, predicted regulatory networks, and immune cell correlations. These findings refine the catalogue of candidate biomarkers and biological processes that may be relevant to both conditions. However, the present results are exploratory and should primarily be viewed as a foundation for future experimental validation and clinically annotated studies rather than as definitive therapeutic targets.


## Acknowledgments
  We thank the investigators who generated and deposited the GEO datasets used in this study.


## Author contributions
  Conceptualization: Rui Zhang, Yinghua Fu, Fang Long, Qiong Cheng.

  Data curation: Rui Zhang, Yinghua Fu.

  Formal analysis: Rui Zhang, Yinghua Fu, Fang Long.

  Methodology: Rui Zhang, Fang Long, Qiong Cheng.

  Visualization: Rui Zhang, Yinghua Fu.

  Supervision: Rui Zhang.

  Writing – original draft: Rui Zhang, Yinghua Fu, Fang Long.

  Writing – review & editing: Rui Zhang, Yinghua Fu, Fang Long, Qiong Cheng.


## N/A