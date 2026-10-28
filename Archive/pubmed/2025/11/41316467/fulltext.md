# Exploring the impact of endocrine-disrupting chemicals on erectile dysfunction through network toxicology and machine learning


## Background
  Erectile dysfunction (ED) is a common male sexual disorder with a multifactorial etiology. The exposure to endocrine-disrupting chemicals (EDCs) has been increasingly linked to reproductive health disorders in both men and women. EDCs can interfere with hormonal signaling and physiological homeostasis, but their specific roles and mechanisms in contributing to ED remain inadequately elucidated.


## Methods
  Network toxicology and enrichment analysis were used to identify potential targets and signaling pathways involved in ED induced by EDCs. Single-cell sequencing was conducted to analyze the expression profiles of these targets in corpus cavernosum tissue. Key regulatory molecules were identified through protein–protein interaction (PPI) network analysis. Core targets were selected using three machine learning algorithms to evaluate the association between EDCs and ED. Molecular docking simulations were further employed to verify the binding affinity between EDCs and target proteins, elucidating potential mechanisms of action.


## Results
  A total of 186 potential targets were identified. Single-cell sequencing revealed their expression characteristics. PPI analysis identified key regulatory molecules, and machine learning approaches pinpointed two core targets: CTNNB1 and HIF1A. Molecular docking confirmed that most EDCs exhibit stable binding to CTNNB1 and HIF1A, suggesting the involvement of associated signaling pathways in the development of ED.


## Conclusions
  This study systematically characterizes the molecular pathways through which EDCs contribute to ED, with CTNNB1 and HIF1A emerging as central players. The identification of these core targets provides a theoretical foundation for developing targeted interventions against environment-related ED and underscores the importance of mitigating EDC exposure in public health strategies.


## Supplementary Information
  The online version contains supplementary material available at 10.1186/s40360-025-01033-8.


## Introduction
  The global incidence of reproductive system diseases has been steadily increasing, constituting a substantial public health concern. Among female reproductive disorders, uterine fibroids, polycystic ovary syndrome (PCOS), and cervical cancer display distinct epidemiological profiles. Epidemiological data indicate that uterine fibroids affect more than 80% of women of African descent and approximately 70% of White women, with 30%–40% of affected individuals presenting with clinical manifestations such as pelvic pain, abnormal uterine bleeding, infertility, early miscarriage, and obstetric complications [1, 2]. PCOS, a major contributor to infertility, affects an estimated 4%–21% of women globally and exerts significant effects on cardiovascular, neurological, and endocrine–metabolic systems [3]. Cervical cancer continues to be a leading cause of gynecological mortality worldwide, with a disproportionately high burden in low- and middle-income countries [4]. In contrast, among male reproductive disorders, prostate cancer ranks as the second most frequently diagnosed malignancy in men globally, following lung cancer [5]. Although the overall incidence of testicular cancer remains relatively low, it represents the most common solid malignancy among men aged 15–40 years, with 90%–95% of cases identified as germ cell tumors [6]. Erectile dysfunction (ED) is a prevalent sexual disorder among men, particularly those aged 40 to 70 years [7]. Emerging evidence suggests that vascular, neurogenic, and metabolic factors are significantly associated with its pathogenesis [8–10]. Current treatment strategies primarily involve phosphodiesterase type 5 inhibitors (PDE5i), surgical interventions and Traditional Chinese medicine [11, 12].

  Endocrine-disrupting chemicals (EDCs) are exogenous compounds commonly found in food, water sources, and derivatives of fossil fuels [13–15]. These chemicals can disturb endocrine homeostasis by interfering with hormone synthesis, secretion, transport, and immune system regulation [16, 17]. Increasing evidence suggests that exposure to EDCs is significantly associated with various pathological conditions, including reproductive developmental abnormalities, metabolic disorders, and neurological diseases [18–20]. Moreover, several studies have reported a potential association between EDCs exposure and ED [21, 22]. In the study, we investigated 10 representative EDCs, encompassing volatile organic compound metabolites (mVOCs), disinfection by-products (DBPs), antifungal and antibacterial agents, plasticizers, and organophosphate esters (OPEs) [23–28]. These substances may interfere with normal physiological functions by disrupting hormone metabolism, signal transduction pathways, mitochondrial activity, and vascular function [27–30]. Such disruptions are closely linked to the underlying pathophysiological mechanisms of ED [31–35].

  Network toxicology combines bioinformatics, systems biology, and chemoinformatics to construct a systematic framework for investigating how chemical substances interact with biomolecular networks and influence cellular functions. This interdisciplinary approach facilitates the identification of potential mechanisms involved in disease pathogenesis [36]. In this context, molecular docking, which relies on atomic-level simulations, elucidates the binding interactions between small-molecule ligands and target proteins, thereby offering insights into the molecular pathways through which chemical compounds may contribute to disease onset.

  The integration of genomics and machine learning has facilitated the incorporation of gene expression data into disease diagnostic models, enhancing our understanding of disease mechanisms and advancing the development of diagnostic and therapeutic strategies [37, 38]. These models not only offer practical approaches for disease diagnosis but also provide a robust scientific basis for designing effective treatment plans.

  In this study, we integrated network toxicology, machine learning, and molecular docking to systematically investigate the interaction networks between EDCs and key proteins implicated in erectile dysfunction. This approach aimed to elucidate the molecular mechanisms underlying the pathological effects of these compounds and to establish a theoretical framework for the prevention and treatment of erectile dysfunction.


## Materials and methods

### Collection and prediction of target proteins for EDCs
  Ten EDCs were selected based on previously published literature [23–28], which are N-Acetyl-S-(2-hydroxypropyl)-L-cysteine (2HPMA), N-Acetyl-S-(4-hydroxy-2-butenyl)-L-cysteine (MHBMA3), Phenylglyoxylic acid (PGA), Dichloroacetic acid (DCAA), Trichloroacetic acid (TCAA), 2-ethylhexyl diphenyl phosphate (EHDPP), Tris(2-biphenylyl) phosphate (TBPP), Climbazole (CBZ), Di(2-ethylhexyl) phthalate (DEHP) and Triclosan (TCS). Their chemical structures and corresponding SMILES were retrieved from the PubChem database (https://pubchem.ncbi.nlm.nih.gov/) [39]. Target prediction was performed using the SMILES codes via SwissTargetPrediction (http://www.swisstargetprediction.ch/) and the Similarity Ensemble Approach (SEA) (https://sea.bkslab.org/), with the target organism specified as Homo sapiens [40]. The resulting predicted targets provided a basis for subsequent network analyses and molecular docking studies, thereby facilitating the identification of key protein interactions potentially involved in endocrine disruption and ED. The organism of these proteins was set to Homo sapiens.


### Prediction of target proteins for erectile dysfunction
  Target genes associated with ED were retrieved from the GeneCards (https://www.genecards.org/) and OMIM (https://www.omim.org/) databases. In the GeneCards database, genes ranked within the top 50% by relevance score were selected as candidate targets. The gene sets from both databases were then integrated, and overlapping genes shared between EDCs and ED were identified through intersection analysis. These shared genes were regarded as potential molecular targets through which EDCs may contribute to the development of ED. The organism of these proteins was set to Homo sapiens.


### Enrichment analysis
  To elucidate the biological functions and signaling pathways associated with EDCs target genes related to ED, functional enrichment analysis was conducted. Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway analyses were performed using the R package ‘clusterProfiler’ [41]. The enrichment results were visualized using the R packages ‘ggsankey’, ‘ggplot2’, and ‘ComplexHeatmap’, which generated Sankey diagrams and bar plots [42].


### Construction of protein-protein interaction networks and identification of key targets
  A protein–protein interaction (PPI) network was constructed using the STRING database (https://cn.string-db.org/) (the search type was based on Multiple Proteins by Names / Identifiers) to analyze the interactions between target genes associated with ED and those corresponding to ten EDCs, with the minimum required interaction score set to 0.6 and the organism restricted to Homo sapiens. The resulting interaction data of full STRING network were exported and visualized using Cytoscape software [43]. Subsequently, the MCODE and cytoHubba plugins were employed for clustering analysis and identification of key target genes [44, 45].

  MCODE assigns weights to vertices based on local neighborhood density and performs outward traversal from locally dense proteins to effectively identify highly interconnected regions within molecular interaction networks. In this study, clusters were derived from the PPI network using the default parameters (Degree Cutoff = 2, Cluster Finding: Haircut, Node Score Cutoff = 2, K-Core = 0.2, and Max.Depth = 100). The cluster with the highest score was subsequently selected to identify the key genes.

  CytoHubba ranks nodes within a network according to their topological characteristics and provides multiple topological analysis algorithms. In this study, the EPC, MCC and MNC algorithms were employed [46]. The EPC algorithm evaluates edge percolation, reflecting the contribution of nodes to maintaining network connectivity. MCC is highly effective in predicting essential proteins, as it captures the significance of both densely and sparsely connected nodes and exhibits strong adaptability to the heterogeneity of biological networks. MNC considers the size of a node’s neighborhood, facilitating the identification of locally dense clusters within the network. The top 15 genes ranked by each algorithm were regarded as key genes [47]. The score of the three cytohubba algorithms are supplied in Supplementary Table 2.


### Single-cell RNA sequencing data curation
  The single-cell dataset GSE206528 was retrieved from the Gene Expression Omnibus (GEO) database (https://www.ncbi.nlm.nih.gov/geo/) and analyzed using the Seurat package (version 5.1.0) [48]. The analysis was performed using five ED samples (including 3 non-diabetic patients and 2 diabetic patients). Cells were filtered based on the following criteria: gene expression count between 800 and 7,000, total UMI count below 30,000, and mitochondrial gene content less than 10%. Data normalization and identification of the top 2,000 highly variable genes were carried out using the NormalizeData and FindVariableFeatures functions. Following preprocessing, dimensionality reduction was performed using principal component analysis (PCA), followed by cell clustering on a K-nearest neighbor (KNN) graph with the Louvain algorithm. t-distributed stochastic neighbor embedding (t-SNE) analysis was conducted using 20 principal components and a resolution of 0.8, resulting in 21 clusters. Cell types were annotated based on the expression of canonical marker genes: Schwann cells (S100B, MPZ), T cells (CD3D, CD3E), macrophages (CD163, CD68), fibroblasts (LUM, COL1A1, PDGFRA), endothelial cells (VWF, PECAM1, ENG), and smooth muscle cells (ACTA2, MYH11).


### Core target gene score based on single-cell clusters
  We employed four gene set scoring algorithms—AUCell, UCell, AddModuleScore, and ssGSEA—to analyze the expression profiles of target genes in single-cell data from ED samples [49–52]. The scores generated by each algorithm were calculated and averaged to obtain a composite activity score for each individual cell. Subsequently, the AUC scores were projected onto a t-SNE plot using the R package ggpubr, facilitating the identification of clusters with high gene activity. The distribution of composite scores across different cell types was visualized using violin plots.


### Bulk transcriptome data curation and batch effect removal
  We retrieved the ED datasets GSE2457 and GSE31247 from GEO database (https://www.ncbi.nlm.nih.gov/geo). The GSE2457 dataset includes corpus cavernosum tissues from five normal rats and five diabetic rats, while the GSE31247 dataset contains corpus cavernosum tissues from three sham-operated rats and three cavernous nerve injury rats. Both datasets were log2-transformed before further analysis. Data integration and batch effect correction were performed using the R package ‘sva’, with the effectiveness of the correction verified through PCA.


### Machine learning identify core targets
  The core target genes were identified by intersecting the key target genes obtained from the MCODE and cytoHubba plugins. Using these core target genes and the integrated ED expression matrix, three machine learning algorithms—least absolute shrinkage and selection operator (LASSO), support vector machine (SVM), and random forest (RF). LASSO regression was conducted using the R package “glmnet”. Following tenfold cross-validation, genes with nonzero coefficients were identified as core genes. The SVM model was implemented with the R package “kernlab”, and after tenfold cross-validation, the “svmRadial” kernel was applied to screen key genes. The RF model was developed using the R package “randomForest”, where gene importance was computed and ranked, and the top five genes were selected as the most significant candidates. Genes selected by all three algorithms were then designated as the core target genes.


### Molecular docking
  We employed molecular docking to explore the potential binding interactions between ten EDCs and core target genes. The 3D molecular structures of the EDCs (sdf files) were retrieved from the PubChem database, while the protein structures of the core target genes were predicted using the AlphaFold server (https://alphafoldserver.com/). The amino acid sequences of the proteins were obtained from the UniProt database and submitted to the AlphaFold server. The entity type was specified as Protein, and the predicted structures were downloaded in CIF format for subsequent analysis. Molecular docking was performed using the CB-DOCK2 online platform (https://cadd.labshare.cn/cb-dock2/php/blinddock.php). The docking results were generated by selecting the Auto Blind Docking option. The conformation exhibiting the lowest binding energy selected as the optimal result. A binding energy threshold of -5 kJ/mol was set to indicate stable interactions, whereas values below − 7 kJ/mol were considered indicative of strong binding affinity. Finally, a binding energy heatmap illustrating the interactions between the target genes and pollutants was generated for visualization using the online platform (https://www.bioinformatics.com.cn/) [53].


### Cell lines and cell culture
  The HUVEC (CL-0143) cell line was obtained from Procell Life Science & Technology Co., Ltd. (Wuhan, China). It was authenticated by short tandem repeat (STR) profiling and confirmed to be free of mycoplasma contamination. HUVEC cells were cultured in HUVEC-specific medium (Procell, Cat# CP-0122, China) supplemented with 1% keratinocyte growth supplement (KGS) and 1% penicillin-streptomycin (P/S). TBPP (Cat#132-28-5) was purchased from Leyan / Shanghai Haohong Scientific Co.,Ltd.


### RNA extraction and quantitative Real-Time polymerase chain reaction (RT-qPCR)
  HUVEC cells treated with DMSO control or varying concentrations of ATBC (0 nM, 10 nM, 50 nM, 100 nM) for 48 h. The total RNA was extracted from cells using the Cell Total RNA Isolation Kit (FOREGENE, Chengdu, China) and reverse-transcribed into cDNA using the ReverTra Ace qPCR RT Kit (TOYOBO, Shanghai, China). After the culture medium was completely removed, Buffer cRL1 was added to lyse the cells. The resulting lysate was mixed with Buffer cRL2 at a volume ratio of 1:1.6, then passed through a DNA-Cleaning Column by centrifugation to eliminate genomic DNA. The clarified supernatant was transferred to an RNA-Only Column in multiple batches. The column was washed sequentially with 500 µL of Buffer RW1 and two rounds of 700 µL Buffer RW2 to remove residual contaminants. RNA was then eluted with 60 µL of RNase-free ddH₂O preheated to 65 °C. All steps were carried out at ambient temperature.

  RT-qPCR was performed with SYBR Green qPCR Master Mix (TOYOBO, Shanghai, China). GAPDH was used as the internal reference gene. RT-qPCR analysis of CTSS expression was conducted using the following gene-specific primers: for the CTNNB1, the forward primer is CGTGACAGGGAAGACATCA and the reverse primer is GTAGTCCATAGTGAAGGCGAA; for the HIF1A, the forward primer is GCATCTCCATCTCCACCC and the reverse primer is ACTCCTTTTCCTGCTCTGTTT; for the GAPDH, the forward primer is TCAAGAAGGTGGTGAAGCAG and the reverse primer is AAGGTGGAGGAGTGGGTGT. Relative mRNA expression levels were calculated using the 2^−ΔΔCT method. All samples were analyzed in triplicate.


### Statistical analysis
  Statistical analyses were conducted using R (version 4.4.1) and RStudio (version 2023.12.1 + 402). Unless otherwise indicated, statistical significance was defined as P < 0.05, with significance levels categorized as follows: *P < 0.05, **P < 0.01, ***P < 0.001, and ****P < 0.0001.


## Results

### Chemical information and toxicity predictions of ten EDCs
  The flowchart of this study is provided in Fig. 1. The chemical properties of the ten EDCs, including their chemical formulas, molecular weights, SMILES notations, and PubChem CIDs, are presented in Supplementary Table 1.

  Fig. 1The flowchart of the study


### Target genes of EDCs
  After integrating and eliminating duplicate data from multiple databases, we identified 549 target genes associated with ten EDCs. A total of 1,514 target genes were identified through screening of the GeneCards and OMIM databases, with 186 genes overlapping with those associated with EDCs (Fig. 2A). Subsequently, a PPI network for these potential genes involved in ED was constructed using the STRING database (Fig. 2B). Ultimately, 186 genes were identified as potential targets related to EDC-induced ED and we constructed a network diagram that illustrates the relationships between these chemicals and their target genes. Further research will evaluate the potential of these genes as therapeutic targets or biomarkers for assessing the risks of ED associated with EDCs exposure.

  Fig. 2Identification and network analysis of potential target genes associated with EDC-induced erectile dysfunction. A. Venn diagram showing the overlap between ED-related target genes and those associated with EDCs. B. Compound-target gene network of EDCs inducing ED


### Enrichment analysis of target genes
  To elucidate the biological processes and signaling pathways associated with the target genes, we conducted GO functional analysis and KEGG enrichment analysis. The KEGG analysis identified key pathways, including the “HIF-1 signaling pathway” “Apoptosis” and “Insulin resistance” all of which play critical roles (Fig. 3A). The GO analysis revealed that the most significantly affected biological processes (BP) included “response to steroid hormone” “endocrine process” and “endothelial cell proliferation” The major cellular components (CC) involved were the “protein kinase complex”, “G protein-coupled receptor complex” and “protein kinase complex”. Regarding molecular function (MF), the most significant functions were “nuclear receptor binding” “hormone binding” and “insulin receptor binding” (Fig. 3B).

  Fig. 3The associations between EDCs and ED. A. Sankey plot shows KEGG enrichment analysis of the potential target genes. B. GO enrichment analysis of the potential target genes shown in bar plot. The horizontal axis represents the number of enriched genes count and the color indicates –log10(p.adjust)


### Enrichment scoring of risk targets in the single-cell dataset
  Following quality control of the single-cell data, we extracted 39,421 cells from the ED single-cell dataset (GSE206528), which includes data from five ED samples (Fig. 4A). Based on gene expression profiles, these cells were classified into 21 distinct clusters (Fig. 4B). Using cell-specific markers for annotation, we identified six distinct cell types: T cells, Schwann cells, macrophages, fibroblasts, endothelial cells, and smooth muscle cells (Fig. 4C). A dot plot was used to visualize the marker genes associated with each cell type (Fig. 4D). A bar plot illustrates the proportion of each cell type in each ED sample (Fig. 4E).

  Fig. 4Cell type determination and scoring in single-cell sequencing. A. t-SNE plot showing the distribution of ED samples. B. t-SNE plot displaying the distribution of cell clusters. C. Subgroup annotation on t-SNE coordinates. D. Analysis of cell composition profiles. E. Marker gene characteristics for various cell subtypes. F. t-SNE heatmap showing scores from four single-cell scoring algorithms, with higher brightness indicating higher scores. G. t-SNE heatmap and violin plot illustrating the mean scores from the four single-cell scoring algorithms

  Subsequently, four single-cell scoring algorithms—AUCell, UCell, AddModuleScore, and ssGSEA—were employed to evaluate the activity of target genes (Fig. 4F). The final score was derived from the average of the scores obtained from all four methods, with fibroblasts exhibiting the highest score, followed by endothelial cells. Among the immune cells, macrophages displayed the highest score (Fig. 4G). These results suggest that EDCs may contribute to the development of ED by targeting the aforementioned cell types.


### Core targets identification
  We utilized the MCODE plugin to identify gene clusters and selected Cluster 1, which comprised 34 genes, as the target cluster (Fig. 5A). Subsequently, the cytoHubba plugin was applied to identify the top 15 target genes using the MNC, MCC, and EPC algorithms (Fig. 5B and D). The results of MCODE and cytoHubba are shown in Supplementary Table 2. By intersecting the gene sets identified by these four methods, we ultimately identified 12 key target genes (Fig. 5E).

  Fig. 5Identification of key target genes. A. Multiple gene clusters were identified using the MCODE plugin; the target genes from the highest-scoring cluster were selected as key targets. B-D. Fifteen target genes identified by the EPC, MCC, and MNC algorithms, respectively. E. Venn diagram showing the 12 overlapping genes identified by all four algorithms

  We integrated the GSE2457 and GSE31247 datasets and performed batch effect correction. The results before and after correction are shown by PCA plots (Fig. 6A and B). To identify core target genes, we employed three machine learning algorithms. The LASSO regression algorithm was applied to eliminate redundant genes, identifying Ctnnb1 and Hif1a as core targets (Fig. 6C and D). The SVM algorithm evaluated model accuracy across varying gene counts and achieved the highest accuracy using Ctnnb1 and Hif1a (Fig. 6E). The RF algorithm assessed the importance of genes and selected the top five as core candidates (Fig. 6F). By intersecting the results of all three algorithms, Ctnnb1 and Hif1a were identified as shared core target genes (Fig. 6G).

  Fig. 6Identification of core target genes using machine learning algorithms. A–B. PCA plots before and after batch effect correction of the merged GSE2457 and GSE31247 datasets. C-D. LASSO regression for feature selection. These pictures detail the coefficient paths across regularization parameters (C) and highlight the optimal λ via cross-validation (D). E. Feature importance scores obtained from SVM for core target gene selection, with higher scores indicating greater feature importance. F. Random Forest (RF) analysis for core target gene selection. The left side displays feature importance scores, while the right side shows feature selection stability across runs. G. Venn diagram showing the intersection of core target genes identified by the three algorithms


### Molecular docking
  We conducted molecular docking analyses of CTNNB1 and HIF1A with ten EDCs. The results indicated that both target proteins formed stable interactions with most of the tested compounds (Supplementary Table 3). Notably, the strongest binding affinities were observed with TBPP for both CTNNB1 and HIF1A (Fig. 7).

  Fig. 7Molecular docking between core targets and ten EDCs

  Table 1The types of bonds between TBPP and core proteins. Each type lists the participating amino acid residues and their positions within the protein sequenceLigandProteinHydrophobic bondHydrogen bondIonic bondCation–πTBPPCTNNB1VAL511GLY512ARG469ARG515ARG474ARG612VAL613LEU781PRO714GLU568/571LYS508HIF1AVAL536LYS118GLU234LYS118LYS190\LYS118GLU234ILE235ASN232PRO226/228TYR119

  Then we discuss the binding sites of TBPP with CTNNB1 and HIF1A exhibit multiple types of interactions, suggesting a relatively stable complex formation (Table 1). Hydrophobic interactions are predominant, involving CTNNB1 residues VAL511, VAL613, LEU781, PRO714, and the carbon atoms of GLU568/571 and LYS508, as well as HIF1A residues VAL536, LYS118, GLU234, ILE235, ASN232, PRO226/228 and TYR119. Close contacts between the carbon atoms of the protein and the ligand facilitate the insertion of the ligand into the hydrophobic pocket of the protein. The formation of hydrogen bonds (HIF1A: LYS118, GLU234; CTNNB1: GLY512) contributes additional directionality and specificity to the interaction. Furthermore, ionic interactions between the negatively charged atoms of TBPP and the positively charged residues (ARG469 and ARG515 in CTNNB1; LYS118 and LYS190 in HIF1A) enhance the overall stability of the complexes. In addition, cation–π interactions are observed between the aromatic rings of TBPP and ARG474 and ARG612 of CTNNB1. Collectively, these interactions enable TBPP to achieve effective binding with CTNNB1 and HIF1A, thereby supporting its potential biological activity.

  Fig. 8The mRNA expression of proteins in HUVEC with different concentrations of TBPP. A. CTNNB1 expression in HUVEC with different concentrations of TBPP. B. HIF1A expression in HUVEC with different concentrations of TBPP

  Subsequently, HUVEC cells were treated with different concentrations of TBPP (0 nM, 10 nM, 50 nM, 100 nM) and the expression levels of CTNNB1 and HIF1A were quantified in each group using RT-qPCR. The results showed that CTNNB1 and HIF1A expression levels were significantly elevated in TBPP-treated cells compared with the control group, exhibiting a clear concentration-dependent trend (Fig. 8A-B). These findings suggest that TBPP may modulate HUVEC function through the regulation of CTNNB1 and HIF1A.


## Discussion
  The pathogenesis of ED is multifactorial, involving vascular abnormalities, endocrine imbalances, and neural damage [11]. Emerging evidence suggests that EDCs may contribute significantly to the onset and progression of ED by influencing key pathophysiological mechanisms, including metabolic dysregulation, aberrant neurodevelopment, and vascular remodeling [54–56]. Consequently, elucidating the molecular targets through which EDCs exert their effects on ED has become an area of considerable scientific interest.

  In the present study, we employed a systematic approach to integrate data from multiple sources, including the GeneCards, OMIM, SwissTargetPrediction, and SEA databases. Through network analysis, we identified 186 potential molecular targets associated with EDC-induced ED. Subsequently, we constructed a PPI network utilizing the STRING database and visualized it using the Cytoscape platform. This integrative strategy enabled a comprehensive exploration of the molecular mechanisms potentially underlying EDC-induced ED.

  Based on the 186 potential targets, KEGG and GO enrichment analyses were conducted to elucidate the physiological processes and signaling pathways potentially involved. Among these, the HIF-1 signaling pathway was identified as playing a central role in metabolic reprogramming by upregulating enzymes associated with glycolysis and glucose transport—alterations that have been implicated in the development of ED [11, 57–59]. Moreover, erectile function is tightly regulated by androgen levels, and androgen deficiency has been shown to impair this function by disrupting mitochondrial activity and promoting eNOS methylation [60, 61]. Insulin resistance, a hallmark of diabetes, may also represent a critical mechanism through which EDCs contribute to ED pathogenesis [62]. Single-cell analysis revealed that target genes were highly expressed in fibroblasts, endothelial cells, and macrophages. Given that ED is frequently accompanied by penile fibrosis and endothelial dysfunction, these findings suggest that EDCs may exert their effects primarily through these cell populations [63, 64]. In addition, previous studies have demonstrated that nerve injury, together with macrophage recruitment, can directly compromise erectile function. Macrophages may also promote arterial plaque formation, leading to endothelial dysfunction and atherosclerosis—vascular alterations that further exacerbate the progression of ED [65].

  We subsequently utilized the PPI network and machine learning approaches to identify core targets from the pool of potential candidates, ultimately selecting CTNNB1 and HIF1A. HIF1A serves as a key regulatory factor mediating cellular adaptation and survival under hypoxic conditions. Activation of HIF1A by branched-chain amino acids enhances glycolysis, which may lead to vascular dysfunction [66]. Previous studies have shown that HIF1A expression is markedly elevated in ED models, and that suppression of HIF1A alleviates hypoxia-related signaling pathways and restores erectile function [67, 68]. CTNNB1 (β-catenin), a pivotal component of the canonical Wnt signaling pathway, functions as a central regulator of tissue fibrosis [69, 70]. Under hypoxic conditions, elevated CTNNB1 expression disrupts the phenotype and gap junction communication of corpus cavernosum smooth muscle cells, thereby contributing to the development of ED [71]. Moreover, CTNNB1 has been reported to directly induce fibrosis of the tunica albuginea, further exacerbating the progression of ED [72].

  Molecular docking analysis demonstrated that all ten EDCs could form stable interactions with the core targets CTNNB1 and HIF1A, with TBPP exhibiting the highest binding affinity. These results indicate that EDCs may contribute to the development and progression of ED by modulating the HIF signaling pathway or the Wnt/β-catenin signaling pathway. Considering the stable binding of TBPP to proteins, we experimentally verified by RT-qPCR that TBPP may influence HUVEC function by targeting HIF1A and CTNNB1, or by modulating related signaling pathways.

  However, this study has several limitations that need to be addressed. The data are primarily derived from sequencing results in large international databases, and the absence of validation using real-world clinical data is a significant concern. Moreover, the mechanisms by which EDCs affect ED targets remain unclear and require further exploration through experimental studies. Future research should focus on in-depth mechanistic investigations to elucidate the specific pathways through which EDCs contribute to the development of ED. Additionally, prospective real-world studies are crucial to enhance the reliability and generalizability of the findings.


## Conclusion
  This study elucidates the potential mechanisms linking exposure to EDCs with the onset of ED, providing valuable insights for environmental health research and public health policymaking. By integrating network toxicology, single-cell sequencing, PPI network analysis, machine learning, and molecular docking, we systematically characterized the molecular pathways through which EDCs may contribute to ED. The findings highlight the urgent need to reassess the health risks associated with EDC exposure and offer a theoretical foundation for developing effective strategies for ED prevention and treatment. Collectively, this research promotes further investigation in the field and provides new perspectives and practical guidance for the global prevention and management of ED.


## Supplementary Information
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2

  Supplementary Material 3

  Supplementary Material 4

  Supplementary Material 5

  Supplementary Material 6


## Acknowledgements
  We thank Mingjie Chen (Shanghai NewCore Biotechnology Co., Ltd.) for providing data analysis and visualization support.