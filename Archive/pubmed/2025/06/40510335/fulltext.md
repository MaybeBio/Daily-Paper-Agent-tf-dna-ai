# Molecular mechanisms of deer antler in promoting osteogenic differentiation of human mesenchymal stem cells via JUN modulation


## Background
  Traditional Chinese medicine and food deer antler has been extensively used in bone regeneration, but its molecular mechanisms remain poorly understood. Preliminary investigations suggest deer antler contains bioactive compounds that influence osteogenic differentiation and immune microenvironments.


## Purpose
  To elucidate the molecular mechanisms of deer antler in promoting human mesenchymal stem cell (hMSC) osteogenic differentiation, focusing on JUN downregulation and immune microenvironment modulation using bioinformatics and molecular docking approaches.


## Methods
  Chemical components and targets were identified using the BATMAN-TCM database. Differentially expressed genes (DEGs) related to osteogenic differentiation were analyzed using Gene Expression Omnibus datasets. Gene Ontology (GO), KEGG enrichment, LASSO regression, and SVM-RFE were applied to identify key genes. A Protein-Protein Interaction (PPI) network was constructed to determine core genes. JUN expression was validated using independent datasets and ROC analysis. Immune cell infiltration was analyzed using CIBERSORT, examining JUN’s correlation with immune cells. Molecular docking explored JUN’s interaction with two active deer antler compounds.


## Results
  The study identified 62 bioactive compounds and 1051 potential targets. DEGs analysis revealed 282 genes associated with osteogenic differentiation. Cross-analysis identified 43 overlapping genes, enriched in “response to mechanical stimulus” and “rheumatoid arthritis” pathways. Machine learning approaches highlighted 7 critical genes, with JUN emerging as the core gene. JUN levels were significantly decreased during osteogenic differentiation, showing high diagnostic accuracy (AUCs: 0.977-1.000). Immune cell analysis revealed JUN correlations with neutrophils, monocytes, eosinophils, M2 macrophages, and resting CD4+ T cells. Molecular docking confirmed strong binding affinities of JUN with Retinol (-8.1 kcal/mol) and Progesterone (-6.0 kcal/mol).


## Conclusions
  The study provides a comprehensive molecular framework demonstrating JUN as a key molecule in hMSC osteogenic differentiation. Deer antler’s bioactive compounds, particularly Retinol and Progesterone, potentially exert therapeutic effects through targeted JUN modulation, offering novel insights into natural compound-mediated bone regenerative mechanisms.


## Introduction
  The restoration and healing of bones are essential for preserving skeletal health, especially in the context of fractures, osteoporosis, and other degenerative bone disorders (1, 2). Human mesenchymal stem cells (hMSCs) are crucial for this process, as their transformation into bone-forming cells is key to new bone tissue development (2, 3). Although our knowledge of the cellular and molecular basis of bone regeneration has grown, there is still a need for more effective treatments, especially in complex scenarios where there is a need to boost bone-forming capabilities and regulate the immune system (4, 5).

  Deer antler (Cornu Cervi Pantotrichum), a well-known traditional Chinese medicine and food, is widely utilized for its potential to improve bone health and facilitate repair (6, 7). This natural remedy is abundant in bioactive components such as growth factors, peptides, and minerals, which are thought to contribute to its healing properties by promoting the development of bone tissue and adjusting the immune response (6, 8, 9). However, the molecular mechanisms underlying these effects remain poorly understood, posing a challenge to the scientific validation and clinical application of deer antler (10).

  Recent advances in bioinformatics and high-throughput data analysis have provided valuable tools for investigating the complex interactions between traditional Chinese medicine and molecular targets (11). In particular, network pharmacology and machine learning techniques offer new opportunities to identify bioactive compounds, potential targets, and regulatory pathways associated with therapeutic effects (12). These computational approaches have revolutionized our understanding of traditional medicine mechanisms (13).

  This study aims to elucidate the molecular mechanisms by which deer antler promotes osteogenic differentiation in hMSC, focusing on its effects on the key regulatory gene and the immune microenvironment. Employing bioinformatics, machine learning algorithms, immunological profiling, and molecular docking techniques, this study investigates the mechanisms by which the bioactive constituents of deer antler engage with molecular signaling cascades to potentiate osteogenic processes. These findings are expected to provide a scientific foundation for the therapeutic use of deer antler in bone-related disorders and contribute to the modernization of traditional Chinese medicine practices.


## Materials and methods

### Identification of bioactive compounds and potential targets of deer antler
  The bioactive compounds of deer antler and their potential molecular targets were identified using the BATMAN-TCM database (14), a comprehensive platform for exploring traditional Chinese medicine and its pharmacological mechanisms. Potential targets were systematically extracted based on compound-target interactions with confidence score cutoff≥0.86 (LR=112.67) and adjusted p-value ≤ 0.05.


### Collection and preprocessing of gene expression datasets
  Gene expression profiles associated with osteogenic differentiation and stem cell proliferation were retrieved from the Gene Expression Omnibus (GEO) database (15). Five datasets (GSE80614, GSE100752, GSE12267, GSE28205 and GSE9451) were curated based on rigorous criteria pertinent to osteogenic differentiation and stem cell research. Subsequent data preprocessing encompassed normalization and batch effect correction, facilitated by the R packages limma (version 3.62.1) (16) and edgeR (v4.4.0) (17). Principal Component Analysis (PCA) was performed to visualize sample clusters and evaluate potential batch effects. The Combat algorithm (18) from the sva package (v3.54.0) (19) was applied to remove batch effects. Differentially expressed genes (DEGs) were identified using the criteria of |log2FoldChange| > 1 and adjusted p-value < 0.05. Data visualization was accomplished through hierarchical clustering heatmaps and volcano plots generated using the Complex Heatmap package in R (20). Detailed descriptions of datasets including sample size, cell source, induction conditions, and culture environments are summarized in  Supplementary Table S1 . To address dataset heterogeneity, the Combat algorithm from the sva package was used to perform batch correction. The efficacy of this correction was validated using PCA visualization.


### Functional enrichment analysis
  Gene Ontology (GO) (21) and Kyoto Encyclopedia of Genes and Genomes (KEGG) (22) pathway enrichment analyses were conducted using the ClusterProfiler package (v4.14.3) (23) in R. The intersection between DEGs and deer antler target genes was identified through Venn diagram analysis using the VennDiagram package (24). The resulting overlapping genes underwent further functional enrichment analysis to elucidate their roles in biological processes and molecular pathways.


### Machine learning for key gene identification
  Two complementary machine learning approaches were employed to identify key regulatory genes. Least Absolute Shrinkage and Selection Operator (LASSO) regression was implemented using the glmnet package (v4.1-8) (25), while Support Vector Machine Recursive Feature Elimination (SVM-RFE) was performed using the e1071 package (v1.7-16) (26). Genes identified by both methods with consistent selection frequencies > 80% were retained for subsequent analyses.


### Protein-protein interaction network analysis
  A PPI network was constructed using both STRING database (v11.5) (27) and GeneMANIA database (28) with an interaction confidence score threshold of 0.4. Core regulatory genes were determined based on the centrality metrics from both networks.


### Validation of gene expression and diagnostic performance
  Independent validation was performed using GEO datasets GSE18043 and GSE28074. These validation datasets underwent identical preprocessing procedures as the primary analysis. Receiver Operating Characteristic (ROC) curves were generated using the pROC package (v1.18.5) (29), with Area Under the Curve (AUC) values calculated to assess diagnostic accuracy.


### Immune infiltration analysis
  Immune microenvironment analysis was conducted using the Cell-type Identification By Estimating Relative Subsets Of RNA Transcripts (CIBERSORT) algorithm (30) with the LM22 signature matrix. Results were visualized using ggplot2 (v3.5.1) (31) for heatmaps and violin plots. Correlations between core regulatory gene expression and immune cell populations were assessed using Pearson correlation analysis, with significance threshold set at p < 0.05. All immune cell estimations were performed on batch-corrected gene expression data. Low-quality samples were excluded using LM22 matrix quality thresholds to ensure robust immune deconvolution.


### Molecular docking analysis
  Molecular interactions between core regulatory gene and deer antler bioactive compounds were investigated through molecular docking simulations. Three-dimensional structures of bioactive compounds were obtained from PubChem (32), while the core regulatory gene protein crystal structure was retrieved from the Protein Data Bank (33). Docking simulations were performed using AutoDock Vina (v1.5.6) (34), and molecular interactions were visualized using PyMOL (v3.1.0) (34).


### Statistical analysis
  All statistical analyses were performed in R (version 4.4.2) (35). Multiple testing corrections were implemented using the Benjamini-Hochberg method to control the false discovery rate (FDR). Statistical significance was set at p < 0.05 unless otherwise specified.


## Results

### Identification of bioactive compounds and potential targets in deer antler
  Analysis through the BATMAN-TCM database (14) identified 62 bioactive compounds and 1,051 potential molecular targets in deer antler.


### Identification of differentially expressed genes
  PCA visualization before and after batch correction confirmed the effectiveness of the correction ( Figure 1A ). Analysis of GEO datasets yielded 282 DEGs associated with osteogenic differentiation (|log2FoldChange| > 1, adjusted p < 0.05). Hierarchical clustering analysis revealed distinct expression patterns between osteogenic differentiation and control groups ( Figure 1B ). Volcano plot visualization highlighted 112 upregulated and 170 downregulated genes ( Figure 1C ).


### Overlapping genes and functional enrichment analysis
  Upon integrating the deer antler-associated targets (n=1,051) with DEGs (n=282), we identified 43 intersecting genes, as depicted in  Figure 2A . GO analysis revealed that the biological processes “response to mechanical stimulus” (GO:0009612, adjusted p-value=1.14E-07) and “muscle cell proliferation” (GO:0033002, adjusted p-value=1.99E-07) were significantly enriched, as illustrated in  Figures 2B, C . KEGG pathway analysis indicated a pronounced enrichment in immune-modulatory pathways, particularly “rheumatoid arthritis” (hsa05323) and “lipid and atherosclerosis” (hsa0541), with adjusted p-values less than 3E-6, as shown in  Figures 2D, E . These findings align with recent studies highlighting the mechano-immunological regulation of bone regeneration (36). Specifically, the enrichment of ‘rheumatoid arthritis’ pathway highlights the immunological basis of osteogenic modulation, given the role of T cells and monocytes in bone microenvironment remodeling and osteoclast activity.


### Machine learning and PPI identifies JUN as a core gene
  Advanced machine learning approaches identified key regulatory genes from the 43 overlapping candidates. LASSO regression identified 14 genes (λ=1) ( Figure 3A ), while SVM-RFE yielded 13 genes (10-fold cross-validation accuracy=0.824) ( Figure 3B ). Seven genes were consistently identified by both methods: JUN, EGR1, ADRA1B, RARRES1, APOD, RBP1, and CXCL12 ( Figure 3C ). Protein-protein interaction (PPI) network analysis revealed JUN as the hub gene ( Figures 3D, E ). The LASSO regression was tuned using 10-fold cross-validation to select λ=1. SVM-RFE was configured with a linear kernel and optimized with 10-fold CV to achieve 82.4% accuracy. These settings are provided in the supplementary code.


### Validation of JUN expression
  Independent validation using GEO datasets GSE18043 and GSE28074 confirmed significant downregulation of JUN in osteogenic differentiation compared to hMSC controls (adjusted p=3.7E-08) ( Figure 4A ). ROC analysis demonstrated JUN’s robust diagnostic potential, with AUC values of 0.977 (95% CI: 0.945–0.999) in the experimental dataset ( Figure 4B ) and 1.000 (95% CI: 1.000–1.000) in the validation dataset ( Figure 4C ).


### Immune infiltration analysis and JUN-immune cell correlations
  CIBERSORT analysis revealed significant alterations in immune cell proportions between osteogenic differentiation and control groups ( Figure 5A ). The relationships between different immune cell populations based on their infiltration levels are illustrated ( Figure 5B ). Significant differences in immune cell populations were observed, as presented in  Figure 5C : CD8+ T cells (p = 0.005), monocytes (p < 0.001), M2 macrophages (p = 0.013), neutrophils (p < 0.001), dendritic cells in both resting (p = 0.013) and activated states (p = 0.010).

  JUN expression showed significant correlations with specific immune cell populations ( Figure 5D ):

  Significant Positive Correlations

  Significant Negative Correlations


### Molecular docking confirms JUN-bioactive compound interactions
  Molecular docking simulations demonstrated strong interactions between the JUN protein and bioactive compounds derived from deer antlers. Specifically, retinol exhibited a binding energy of -8.1 kcal/mol ( Figure 6A ), while progesterone showed a binding energy of -6.0 kcal/mol ( Figure 6B ). These binding energy values indicate stable molecular interactions, suggesting that deer antler compounds may directly modulate JUN activity.


### Summary of key findings

## Discussion
  Bone regeneration represents a complex biological process orchestrated by intricate cellular signaling networks, immune system interactions, and environmental factors (37). This study presents a comprehensive investigation of deer antler’s molecular mechanisms in promoting human mesenchymal stem cell (hMSC) osteogenic differentiation. Our findings identify JUN as a pivotal regulatory molecule and demonstrate how deer antler’s bioactive compounds may facilitate bone regeneration through JUN-mediated pathways.


### JUN as a central regulator of osteogenic differentiation
  JUN, a key component of the activator protein-1 (AP-1) transcription factor family, orchestrates various cellular processes including proliferation, differentiation, and stress responses (38). Our analysis revealed significant downregulation of JUN during osteogenic differentiation, consistent with previous studies suggesting its role as a negative regulator of osteogenesis (39). The remarkable diagnostic performance of JUN (experimental AUC: 0.977; validation AUC: 1.000) establishes it as a robust biomarker for osteogenic differentiation. This downregulation appears to be a critical checkpoint in the osteogenic pathway, potentially facilitating the activation of pro-osteogenic transcriptional programs (40). However, the role of JUN was identified via bioinformatics analysis only. Functional validation such as gene knockdown or overexpression experiments are planned in follow-up studies to verify its causal role in osteogenesis.


### Immune modulation and JUN’s role in the osteogenic microenvironment
  The significant changes in immune cell composition suggest an active immune response during osteogenic differentiation. The increased proportion of CD8+ T cells, monocytes, and M2 macrophages aligns with previous findings showing their involvement in bone regeneration and remodeling (41). The presence of both resting and activated dendritic cells suggests ongoing immune surveillance and potential antigen presentation during the differentiation process (42).

  The correlation between CD4+ T cell subsets indicate coordinated T cell responses, while the M2 macrophage-neutrophil correlation suggests a potentially orchestrated innate immune response ( Figure 5B ). These findings provide new insights into the immune microenvironment during osteogenic differentiation and may have implications for bone tissue engineering and regenerative medicine (43).

  The transcription factor JUN plays crucial roles in immune response regulation through its differential association with various immune cell populations. Our correlation analysis reveals several significant relationships that align with and extend previous findings in the literature.

  The positive correlation between JUN expression and monocytes supports previous studies demonstrating JUN’s essential role in monocyte differentiation and function (38, 44). A striking negative correlation was observed between JUN and neutrophils, representing the strongest relationship in our study. This finding suggests JUN may act as a negative regulator of neutrophil activation states. This observation is consistent with work by Behre et al. (45). The strong negative correlation might indicate a regulatory mechanism where JUN helps maintain neutrophil homeostasis by preventing excessive activation. The negative correlation with M2 macrophages provides interesting insights into JUN’s potential role in macrophage polarization. This relationship suggests that JUN might influence the balance between M1 and M2 phenotypes (46). The observed correlations with resting memory CD4+ T cells and eosinophils suggest broader immunomodulatory roles for JUN. The negative correlation with memory CD4+ T cells might reflect JUN’s involvement in T cell quiescence, as supported by Riera-Sans et al. (47).

  Collectively, our results imply that the JUN protein serves as a central regulatory hub within the immune system, modulating the equilibrium among various immune cell subsets. The contrasting correlations observed with distinct myeloid cell types—positively associated with monocytes and negatively with neutrophils and M2 macrophages—suggest a potential role for JUN as a molecular determinant in the lineage commitment and functional specification of myeloid cells.


### Bioactive compounds in deer antler target JUN
  Utilizing the BATMAN-TCM database, our investigation revealed 62 bioactive compounds and 1,051 potential targets in deer antler. Molecular docking identified Retinol and progesterone as key interactors with the JUN transcription factor, with binding energies of -8.1 kcal/mol and -6.0 kcal/mol, respectively. Given Retinol’s established role in osteogenic differentiation and its stable interaction with JUN, it emerges as a promising candidate for bone health therapies (48). Progesterone boosts bone health via multiple mechanisms like regulating bone resorption and formation (49). Its significant binding affinity with JUN implies its role in bone regeneration. These molecular interactions establish a fundamental groundwork for the traditional function of deer antler in bone regeneration and its therapeutic uses.


### Functional enrichment and pathway analysis
  Functional enrichment analysis has identified a number of crucial biological processes and pathways that are significantly correlated with the bioactive components of deer antler. The prominent discoveries are as follows:

  These results align with current understandings of bone physiology, emphasizing mechanical and immunological pathways as the principal mediators of the therapeutic outcomes of deer antler.


### Implications for bone regeneration therapies
  The identification of JUN as a central regulator presents several therapeutic opportunities:


### Study limitations and future directions
  The study is subject to several limitations. Firstly, it depends on bioinformatics findings which call for experimental verification. Secondly, it only concentrates on particular compounds within the intricate composition of deer antlers. Thirdly, bulk RNA sequencing has limitations in analyzing immune cell heterogeneity. Future endeavors should prioritize in vitro and in vivo validations, investigate additional bioactive compounds, and employ single-cell RNA sequencing to achieve a more nuanced understanding of the immune microenvironment.


## Conclusion
  This study establishes JUN as a critical regulator in hMSC osteogenic differentiation and elucidates potential mechanisms through which deer antler bioactive compounds may promote bone regeneration. The findings provide a scientific foundation for the development of novel therapeutic strategies in bone regeneration.


## Data availability statement
  The original contributions presented in the study are included in the article/ Supplementary Material . Further inquiries can be directed to the corresponding author.


## Author contributions
  CY: Conceptualization, Formal analysis, Funding acquisition, Methodology, Writing – original draft. YW: Software, Writing – original draft. HH: Validation, Writing – original draft. XL: Formal analysis, Writing – original draft. JW: Formal analysis, Writing – original draft. CL: Investigation, Writing – review & editing. YS: Resources, Writing – original draft. DH: Data curation, Writing – review & editing. RT: Writing – review & editing. ZW: Visualization, Writing – review & editing. LJ: Supervision, Writing – review & editing. FL: Conceptualization, Project administration, Writing – review & editing.


## Conflict of interest
  The authors declare that the research was conducted in the absence of any commercial or financial relationships that could be construed as a potential conflict of interest.


## Correction note
  A correction has been made to this article. Details can be found at: 10.3389/fimmu.2025.1684846.


## Generative AI statement
  The author(s) declare that no Generative AI was used in the creation of this manuscript.


## Publisher’s note
  All claims expressed in this article are solely those of the authors and do not necessarily represent those of their affiliated organizations, or those of the publisher, the editors and the reviewers. Any product that may be evaluated in this article, or claim that may be made by its manufacturer, is not guaranteed or endorsed by the publisher.


## Supplementary material
  The Supplementary Material for this article can be found online at: https://www.frontiersin.org/articles/10.3389/fimmu.2025.1550249/full#supplementary-material