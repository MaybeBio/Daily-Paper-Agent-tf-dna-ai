# NR1I2 as a core biological target in chronic venous ulcer tissues treated with ultrasound therapy


## Abstract
  Ultrasound therapy is a method of applying ultrasonic energy to the stimulation produced by human body to change the function and tissue state of the body in order to achieve the purpose of treating diseases. Chronic venous ulcer is a common chronic skin ulcer. GSE222503 for ultrasound therapy of chronic venous ulcers was downloaded from gene expression omnibus database, which were used to identify differentially expressed genes. Weighted gene co-expression network analysis, functional enrichment analysis, gene set enrichment analysis, immune infiltration analysis and construction and analysis of protein–protein interaction network were performed. Draw gene expression heatmaps. Comparative toxicogenomics database analysis was performed. Two hundred thirty-five differentially expressed genes were obtained. According to gene ontology analysis, in biological process analysis, they were mainly enriched in positive regulation of cellular biosynthetic process, reproductive cell development, vasculogenesis, vascular morphogenesis, and inflammatory response. In cellular component analysis, they were mainly enriched in leading edge of growing cell, extracellular matrix binding organelle, F-actin capping protein complex. In molecular function analysis, they were mainly concentrated in receptor ligand activity, cytokine receptor binding. In Kyoto encyclopedia of genes and genomes analysis, they were mainly enriched in cytokine–cytokine receptor interaction, PI3K-Akt signaling pathway, HIF-1 signaling pathway, heme biosynthesis. In weighted gene co-expression network analysis, the soft threshold power was set to 9. Thirty modules were generated. PF4, NR1I2, TTC16, H3C12, KLRB1, CYP21A2 identified by 4 algorithms (MCC, EPC, closeness, stress). Heatmap of core gene expression showed that H3C12, KLRB1, PF4, NR1I2 were all underexpressed in samples of ultrasound-treated chronic venous ulcers and overexpressed in samples of untreated chronic venous ulcers. Comparative toxicogenomics database analysis showed that H3C12, KLRB1, PF4, NR1I2 are associated with thrombophlebitis, phlebitis, vascular malformations, metabolic syndrome, ulcers, and inflammation. In samples of chronic venous ulcer tissue treated with ultrasound, NR1I2 shows low expression, while in samples of chronic venous ulcer tissue without ultrasound treatment, it shows high expression. This finding suggests a potential role of NR1I2 in the process of ultrasound therapy for chronic venous ulcers, which may be related to the therapeutic effect of ultrasound therapy on chronic venous ulcers.


## 1. Introduction
  Ultrasound therapy is a treatment method used for chronic venous ulcers, involving the use of ultrasound energy to promote wound healing and tissue repair.[1] Chronic venous ulcers are common chronic skin ulcers that typically occur in areas of venous valve dysfunction or venous insufficiency in the lower limb venous system.[2] This type of ulcer is prevalent worldwide, especially among the elderly and individuals with venous diseases. Chronic venous ulcers are characterized by persistent nonhealing wounds, which may recur and are often accompanied by symptoms such as pain, swelling, and skin discoloration. The clinical manifestations of chronic venous ulcers include ulcer formation, edema, discoloration, and sclerosis of the skin surrounding the ulcer, as well as associated pain and discomfort. The pathological features of chronic venous ulcers mainly include venous insufficiency, venous valve dysfunction, skin and tissue damage, and chronic inflammatory responses. Chronic venous ulcers not only affect the quality of life of patients but may also lead to serious complications such as infection, bleeding, and even limb necrosis.[3,4] The mechanism of ultrasound therapy for chronic venous ulcers is not yet clear but may be related to the biological effects of ultrasound on tissues, including the promotion of vascular endothelial growth factor expression, increased tissue perfusion, promotion of wound healing processes, and modulation of inflammatory responses.[5] Therefore, in-depth research into the molecular mechanisms of ultrasound therapy for chronic venous ulcers is particularly important and can provide more effective guidance and methods for future treatment methods and clinical practice.

  The current development of bioinformatics technology is characterized by the increasing volume of data and continuously improving analysis methods. Its advantages lie in its ability to handle large-scale biological data and extract useful information to advance biomedical research, genomics, translational medicine, and other fields.[6] The application of bioinformatics technology covers various aspects such as genomics, proteomics, transcriptomics, metabolomics, providing researchers with comprehensive and in-depth opportunities to understand complex molecular mechanisms and biological processes within organisms.[7]

  NR1I2 is a member of the nuclear receptor superfamily.[8] Its main role in the human body is as a transcription factor, regulating the metabolism and excretion of various drugs, especially by influencing the activity of the cytochrome P450 enzyme system in the liver. NR1I2 plays an important role in drug metabolism, toxicity regulation, and the effects of endogenous chemicals, making it significant in the study of drug interactions, drug metabolism pathways, and predicting individual drug responses.[9] However, the relationship between NR1I2 and ultrasound therapy for chronic venous ulcers is currently unclear.

  Therefore, this study aims to use bioinformatics technology to explore the core genes between ultrasound-treated and untreated chronic venous ulcer tissues and conduct enrichment analysis and pathway analysis. Public datasets will be used to validate the significant role of NR1I2 in ultrasound therapy for chronic venous ulcers.


## 2. Methods

### 2.1. Dataset of ultrasound therapy for chronic venous ulcers
  In this study, the dataset GSE222503 for ultrasound therapy of chronic venous ulcers was downloaded from the gene expression omnibus database (http://www.ncbi.nlm.nih.gov/geo/) and generated on the platform GPL23934. GSE222503 includes 3 postoperative samples of chronic venous ulcers treated with ultrasound therapy and 4 samples of chronic venous ulcers untreated with ultrasound therapy, which were used to identify differentially expressed genes (DEGs) in ultrasound-treated chronic venous ulcers.


### 2.2. DEGs screening
  The R package “limma” was utilized for probe summarization and background correction of the gene expression matrix of GSE222503. The Benjamini-Hochberg method was applied to adjust the raw P-values, and fold change was calculated using the false discovery rate (FDR). The cutoff criteria for DEGs were set as P < .05 and fold change > 1.5. A volcano plot was generated to visualize the DEGs.


### 2.3. Weighted gene co-expression network analysis (WGCNA)
  Firstly, we calculated the median absolute deviation for each gene in the gene expression matrix of GSE222503 and removed the bottom 50% of genes with the smallest median absolute deviation. Then, we used the “goodSamplesGenes” function in the R package WGCNA to remove outlier genes and samples. Subsequently, WGCNA was employed to construct a scale-free co-expression network. Specifically, we calculated the Pearson correlation matrix and used the average linkage method for pairwise genes. Then, a soft-thresholding power (β) of 10 was selected to construct the weighted adjacency matrix and further transformed it into the topological overlap matrix. Module identification was performed using hierarchical clustering based on topological overlap matrix-based dissimilarity measures, with a minimum module size of 30 genes and a sensitivity of 3. To analyze modules further, we calculated module eigengenes and selected a cutting line for module dendrogram, and merged some modules. Additionally, modules with a distance <0.25 were merged. The gray module was considered to be a set of genes that could not be assigned to any module.


### 2.4. Functional enrichment analysis
  Gene ontology (GO) and Kyoto encyclopedia of genes and genomes (KEGG) analyses were performed to assess gene function and biological pathways. We input the differential gene list into the KEGG API (https://www.kegg.jp/kegg/rest/keggapi.html) to obtain the latest KEGG pathway gene annotations as background. Then, we used the R package clusterProfiler (version 3.14.3) for enrichment analysis, with the minimum gene set size set to 5 and the maximum gene set size set to 5000. The significance level was set as a P value of <.05 and a FDR of <0.25. Additionally, Metascape database was utilized for comprehensive gene list annotation and analysis, with visualization exports.


### 2.5. Gene set enrichment analysis
  For gene set enrichment analysis (GSEA), we obtained the GSEA software (version 3.0) from the GSEA website (DOI:10.1073/pnas.0506580102, http://software.broadinstitute.org/gsea/index.jsp) and downloaded the c2.cp.kegg.v7.4.symbols.gmt subset from the Molecular Signatures Database (DOI:10.1093/bioinformatics/btr260, http://www.gsea-msigdb.org/gsea/downloads.jsp). Samples were divided into 2 groups based on treatment and control, and the gene expression profiles were used to evaluate relevant pathways and molecular mechanisms. The significance level was set as a P value of <.05 and a FDR of <0.25, with 1000 permutations. Additionally, GO and KEGG analyses were conducted for the entire genome, as formulated by GSEA.


### 2.6. Immune infiltration analysis
  CIBERSORT (http://CIBERSORT.stanford.edu/) was employed for immune cell infiltration analysis, utilizing the LM22 gene file to define 22 immune cell subtypes. We used the CIBERSORT software package to analyze the gene expression matrix of GSE222503, and linear support vector regression was used to deconvolute the expression matrix of immune cell subtypes to estimate immune cell abundance. Samples with a confidence level P < .05 were selected.


### 2.7. Construction and analysis of protein–protein interaction (PPI) network
  The search tool for the retrieval of interacting genes (STRING) database (http://string-db.org/) was used to collect, score, and integrate all publicly available protein-protein interaction information sources, supplemented by predicted interactions. The differential gene list was input into the STRING database to construct the PPI network of predicted core genes (confidence > 0.4). The Cytoscape software was utilized for biological network analysis and two-dimensional visualization. Through Cytoscape, the PPI network derived from the STRING database was visualized, and core genes were predicted. Initially, the PPI network was imported into the Cytoscape software, and modules with the best correlations were identified using MCODE. Furthermore, 4 algorithms (MCC, EPC, closeness, stress) were employed to calculate the top ten genes with the best correlations, and the intersection was taken. The resulting core gene list was visualized and exported after visualization.


### 2.8. Gene expression heatmaps
  The R package heatmap was used to generate heatmaps of the core genes found in the PPI network, illustrating the expression levels in the samples of ultrasound-treated chronic venous ulcers and untreated chronic venous ulcers.


### 2.9. Comparative toxicogenomics database (CTD) analysis
  The CTD integrates a vast amount of data on interactions among chemicals, genes, phenotypes, and diseases, facilitating research on environmental exposure factors and potential mechanisms of action of drugs. We inputted the core genes into the CTD website to identify the most relevant diseases associated with the core genes and plotted radar charts of the expression differences for each gene using Excel.


### 2.10. miRNA analysis
  We used miRNA prediction websites to search for miRNA information on target genes. In our study, we utilized the online databases TargetScan (www.targetscan.org) and DIANA-TarBase (dianalab.e-ce.uth.gr) to screen for miRNAs regulating the core genes.


## 3. Results

### 3.1. Analysis of differentially expressed genes
  In this study, using predefined cutoff values, we identified DEGs from the ultrasound-treated chronic venous ulcers dataset GSE222503. Ultimately, a total of 235 DEGs were obtained (Fig. 1).


### 3.2. Functional enrichment analysis

#### 3.2.1. DEGs
  We conducted GO and KEGG analyses on these DEGs. According to the GO analysis results, in biological process analysis, they were mainly enriched in positive regulation of cellular biosynthetic process, reproductive cell development, vasculogenesis, vascular morphogenesis, and inflammatory response (Fig. 2A). In cellular component analysis, they were mainly enriched in leading edge of growing cell, extracellular matrix binding organelle, F-actin capping protein complex (Fig. 2B). In molecular function analysis, they were mainly concentrated in receptor ligand activity, cytokine receptor binding (Fig. 2C). In KEGG analysis, they were mainly enriched in cytokine–cytokine receptor interaction, PI3K-Akt signaling pathway, HIF-1 signaling pathway, heme biosynthesis (Fig. 2D).


#### 3.2.2. GSEA
  Additionally, we performed GSEA on the entire genome to identify potential enrichment items among non-differentially expressed genes and validate the results of differentially expressed genes. The intersection of enrichment items with GO and KEGG enrichment items and DEGs is shown in the figure. The enrichment results of the GSE222503 dataset showed that differentially expressed genes were mainly enriched in vasculogenesis, inflammatory response, reproductive cell development, F-actin capping protein complex, cytokine receptor binding, and cytokine–cytokine receptor interaction (Fig. 2E–H).


#### 3.2.3. Metascape enrichment analysis
  In the Metascape enrichment projects, GO enrichment projects include responses to mechanical stimulus, NF-kappaB-inducing kinase activation, and protein polyubiquitination (Fig. 3A). Additionally, we generated enrichment networks colored and P-value colored for visualization, representing the associations and confidence levels of each enrichment project (Fig. 3B and C).


### 3.3. Immune infiltration analysis
  We analyzed the matrix of immune cell proportions in the GSE222503 dataset using the CIBERSORT package. At a 95% confidence level, we obtained the proportion results of immune cells in the entire gene expression matrix. The results suggested that Monocytes accounted for a relatively high proportion in the samples (Fig. 4A). Furthermore, we conducted correlation analysis of infiltrating immune cells and obtained a co-expression pattern diagram of immune cell components. The results suggested a highly positive correlation between T cells regulatory (Tregs) and NK cells resting, which may affect the treatment process of chronic venous ulcers with ultrasound (Fig. 4B).


### 3.4. WGCNA
  The selection of the soft threshold power is an important step in WGCNA. Network topology analysis was performed to determine the soft threshold power. In the WGCNA, the soft threshold power was set to 9 (Fig. 5A). A hierarchical clustering tree of all genes was constructed, and interactions between important modules were generated and analyzed (Fig. 5B). A total of 30 modules were generated (Fig. 5C), and a heatmap of module-trait correlations and a scatter plot of the correlation between the GS and MM of the relevant hub genes were also generated (Fig. 5D and E).

  We calculated the correlation between the module eigenvectors and gene expression to obtain MM and identified hub genes in clinically significant modules based on the cutoff criterion (|MM| > 0.8). A Venn diagram was drawn based on WGCNA and DEGs to identify the intersection for subsequent construction and analysis of PPI (Fig. 5F).


### 3.5. Construction and analysis of PPI network
  The PPI network of DEGs was constructed by the STRING online database and analyzed by Cytoscape software, resulting in 6 core genes (PF4, NR1I2, TTC16, H3C12, KLRB1, CYP21A2) identified by 4 algorithms (MCC, EPC, closeness, stress) (Fig. 6A–F).


### 3.6. Heatmap of core gene expression levels
  We visualized the expression levels of core genes in the gene expression matrix of the GSE222503 dataset for ultrasound-treated chronic venous ulcers and untreated chronic venous ulcers and generated heatmaps (Fig. 7A). We found that core genes (H3C12, KLRB1, PF4, NR1I2) were all underexpressed in samples of ultrasound-treated chronic venous ulcers and overexpressed in samples of untreated chronic venous ulcers. This suggests that core genes (H3C12, KLRB1, PF4, NR1I2) may play a regulatory role in ultrasound treatment of chronic venous ulcers.


### 3.7. CTD analysis
  In this study, we input the hub gene list into the CTD website to search for diseases related to the core genes, enhancing our understanding of the association between genes and diseases. We found that the core genes (H3C12, KLRB1, PF4, NR1I2) are associated with thrombophlebitis, phlebitis, vascular malformations, metabolic syndrome, ulcers, and inflammation (Fig. 7B). Among them, the association between the NR1I2 gene and ultrasound treatment of chronic venous ulcers is stronger, suggesting that NR1I2 may be a target gene for ultrasound treatment of chronic venous ulcers.


### 3.8. miRNA prediction and functional annotation related to Hub genes
  In this study, we input the hub gene list into miRNA prediction websites to find relevant miRNA, enhancing our understanding of gene expression regulation (Table 1).

  On the TargetScan website, miRNA prediction revealed that hsa-miR-129-5p is associated with the PF4 gene, while hsa-miR-140-3p is associated with the NR1I2 gene.

  On the DIANA-TarBase website, miRNA prediction revealed that hsa-miR-340-5p, hsa-miR-20b-5p, and hsa-miR-29c-3p are associated with the H3C12 gene. Hsa-miR-335-5p is associated with the KLRB1 gene. Hsa-miR-129-2-3p and hsa-miR-27a-3p are associated with the PF4 gene. Hsa-let-7i-3p, hsa-miR-146a-5p, and hsa-miR-15a-5p are associated with the NR1I2 gene.


## 4. Discussion
  Chronic venous ulcers can lead to serious complications such as infection, bleeding, and even limb necrosis.[10] It is crucial to delve into the molecular mechanisms of ultrasound therapy for chronic venous ulcers for targeted drug research. The main finding of this study is that NR1I2 is downregulated in samples of chronic venous ulcer tissue treated with ultrasound compared to samples of chronic venous ulcer tissue without ultrasound treatment.

  The gene product of NR1I2 belongs to the nuclear receptor superfamily, whose members are transcription factors encoding proteins with ligand-binding and DNA-binding domains.[11] It is a transcriptional regulator of the cytochrome P450 gene CYP3A4 and forms a heterodimer with the 9-cis-retinoic acid receptor RXR at the response element of the CYP3A4 promoter. It is activated by a series of compounds inducing CYP3A4, including dexamethasone and rifampicin.[12] Several splice variants encoding different subtypes have been described, some of which use a non-AUG (CUG) translation initiation codon. Additional transcript variants exist, but they have not been fully characterized.[13] Current research indicates that NR1I2 plays a crucial role in drug metabolism and detoxification processes, and its expression levels in the liver are regulated by various exogenous compounds.[14,15] Recent studies have increasingly focused on the role of NR1I2 in drug interactions, drug metabolism pathways, and disease occurrence and development. Furthermore, some studies suggest that NR1I2 may play an important regulatory role in tumors,[16,17] liver diseases, metabolic disorders, providing potential targets for developing new therapeutic methods. However, despite some progress in NR1I2 research, its exact mechanism of action in various diseases still requires further in-depth research and validation.

  Research progress on ultrasound therapy for chronic venous ulcers suggests that ultrasound waves have potential effects in promoting wound healing and improving tissue repair.[18] Recent studies have shown that ultrasound therapy can increase skin blood flow, promote cell proliferation and collagen synthesis, reduce inflammation, and facilitate tissue regeneration.[19] Additionally, some studies have found that ultrasound therapy can improve the healing rate and treatment effectiveness of chronic venous ulcers, reducing patients’ pain and improving their quality of life.[20] Nevertheless, the exact mechanism of ultrasound therapy for chronic venous ulcers remains unclear and requires further basic scientific research and clinical trials for validation and improvement.

  In recent years, research on ultrasound therapy for chronic venous ulcers has continued to increase, involving various types of ultrasound therapy techniques, including low-intensity ultrasound, high-intensity focused ultrasound, and ultrasound microwave therapy. These studies explore the mechanisms by which ultrasound waves promote wound healing, including their effects on improving blood circulation, releasing growth factors, regulating inflammation and cell apoptosis, and influencing tissue repair and regeneration.[21] Moreover, some studies have investigated the combined use of ultrasound therapy with other treatment methods and compared the efficacy of ultrasound therapy in patients with different types and severities of chronic venous ulcers. Although most of the current research results are preliminary clinical observations and experimental studies, these studies provide a theoretical basis and clinical application prospects for ultrasound therapy for chronic venous ulcers, as well as direction and motivation for future in-depth research and clinical practice.

  Currently, there is no direct research on the relationship between NR1I2 and chronic venous ulcers. However, considering the important role of NR1I2 in drug metabolism[22] and detoxification processes, and the fact that the treatment of chronic venous ulcers often involves drug therapy, it can be speculated that NR1I2 may be associated with the treatment and recovery process of chronic venous ulcers. Specifically, NR1I2 may affect the response and effectiveness of drug therapy for chronic venous ulcer patients by regulating drug metabolism pathways and the expression of drug target sites. However, this aspect of research has not been deeply explored and requires more experiments and clinical studies to validate the exact mechanism of action of NR1I2 in chronic venous ulcers. We speculate that NR1I2 may be related to the efficacy and mechanism of ultrasound therapy. Specifically, NR1I2 may affect patients’ response and efficacy of ultrasound therapy by regulating drug metabolism pathways and the expression of drug target sites.[23] Additionally, NR1I2 may also be involved in regulating tissue repair and regeneration processes after ultrasound therapy.[24,25]

  The results of this study provide a deep understanding of the mechanism of ultrasound therapy for chronic venous ulcers and identify clues for potential therapeutic targets. The clinical application prospects of this study are vast. Firstly, by comprehensively understanding the molecular mechanism of ultrasound therapy for chronic venous ulcers, a foundation can be laid for the development of more effective treatment methods. This may include targeted therapy against NR1I2, such as the development of NR1I2 modulators or drugs targeting the NR1I2 signaling pathway. Secondly, by gaining a deeper understanding of the pathophysiology of chronic venous ulcers, improvements can be made in the diagnosis and treatment strategies for patients. For example, gene expression signatures can be used to aid in diagnosis, assess the severity of the condition, predict patient responses to specific treatment methods, and personalize treatment plans. Additionally, by integrating other clinical data and experimental research, the potential therapeutic targets and mechanisms identified in this study can be further validated, thus enhancing our understanding of ultrasound therapy for chronic venous ulcers. This has the potential to bring substantial advancements to clinical practice, improving patient treatment outcomes and quality of life.

  Although this study conducted rigorous bioinformatics analysis, there are still some shortcomings worth noting. First, the study may be limited by the selection of datasets and sample sizes, which may affect the reliability and generalizability of the results. Second, the selection of some analysis methods or parameters may influence the results, thus requiring more validation and robustness analysis. Furthermore, although this study proposed some research progress on ultrasound therapy for chronic venous ulcers, it lacks a review and discussion of existing research and prospects for future research directions, which is also a potential improvement point. Therefore, future research can further enhance and strengthen the credibility and impact of this study by increasing sample sizes, using multiple analysis methods for validation, and strengthening the interpretation and discussion of results.


## 5. Conclusion
  In summary, in samples of chronic venous ulcer tissue treated with ultrasound, NR1I2 shows low expression, while in samples of chronic venous ulcer tissue without ultrasound treatment, it shows high expression. This finding suggests a potential role of NR1I2 in the process of ultrasound therapy for chronic venous ulcers, which may be related to the therapeutic effect of ultrasound therapy on chronic venous ulcers. However, further research is needed to explore the specific mechanisms of action. These findings provide important clues for a deeper understanding of the mechanism of ultrasound therapy for chronic venous ulcers and lay the foundation for further research on NR1I2 and its potential clinical applications.


## Author contributions
  Conceptualization: Chuanyingzi Lu.

  Data curation: Chuanyingzi Lu, Xiaoshi Bao.

  Formal analysis: Chuanyingzi Lu, Jingli Zhang, Xiaoshi Bao.

  Methodology: Chuanyingzi Lu, Jingli Zhang, Yajing Zhang.

  Validation: Jingli Zhang, Yajing Zhang, Xiaoshi Bao.

  Visualization: Chuanyingzi Lu, Jingli Zhang, Yajing Zhang, Xiaoshi Bao.

  Writing – original draft: Chuanyingzi Lu, Xiaoshi Bao.

  Writing – review & editing: Chuanyingzi Lu.