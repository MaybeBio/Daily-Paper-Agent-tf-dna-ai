# Role of Macrophage‐Related Genes GAS7 and ZEB2 in Acute Myocardial Infarction Pathogenesis


## Background
  Acute myocardial infarction (AMI) involves complex immune responses and cellular interaction mechanisms. Although the pathogenesis of AMI is now preliminarily understood, there is still a lack of biomarkers that can accurately and rapidly diagnose its disease characteristics.


## Methods
  This study analyzed single‐cell RNA sequencing (scRNA‐seq) and bulk RNA‐seq data related to AMI from the Gene Expression Omnibus (GEO) database. Data preprocessing and clustering were performed using Seurat, and cell–cell communication was analyzed using CellChat. Functional enrichment was performed using clusterProfiler. Key transcription factors were identified using SCENIC, and module‐specific genes associated with macrophages in AMI were identified using high‐dimensional weighted gene coexpression network analysis (hdWGCNA). These were combined with WGCNA to identify genes associated with AMI. Molecular docking was then used to predict potential targeted drugs for AMI. In addition, an oxygen–glucose deprivation (OGD)–induced AC16 cardiomyocyte model combined with quantitative real‐time polymerase chain reaction (qRT–PCR) was used to validate the expression patterns of the key regulators and biomarkers.


## Results
  This study identified six cell types in AMI, including adipocytes, cardiomyocytes, endothelial cells, fibroblasts, macrophages, and smooth muscle cells. CellChat showed that cell–cell communication intensity was generally enhanced in AMI. hdWGCNA identified the M5 and M8 modules as significantly associated with macrophages. SCENIC analysis found that FOS and ETV6 were important regulatory factors of macrophages. WGCNA screened the brown module as significantly associated with AMI, enriched in immune and inflammatory response pathways. The final integration of all analysis results identified GAS7 and ZEB2 as potential biomarkers for AMI, and receiver operating characteristic (ROC) curves validated the good diagnostic performance of the two genes for AMI. Furthermore, qRT–PCR in an OGD‐induced AC16 cardiomyocyte model confirmed the upregulation of FOS, ETV6, GAS7, and ZEB2, consistent with the transcriptomic findings. Molecular docking indicated that GAS7 has a good binding affinity with sulforaphane.


## Conclusion
  This study revealed the cellular communication characteristics in the pathogenesis of AMI and identified GAS7 and ZEB2 as potential biomarkers for AMI based on macrophage characteristics. It also elucidated their targeted therapeutic drugs, providing new insights into the mechanism and treatment of AMI.


## 1. Introduction
  Acute myocardial infarction (AMI) is a life‐threatening condition caused by acute obstruction of the coronary arteries, leading to insufficient blood supply to the corresponding myocardial region and resulting in myocardial necrosis [1, 2]. Although current clinical diagnosis primarily relies on electrocardiogram changes and myocardial injury markers (such as troponin) testing, these methods still have significant limitations in terms of early diagnostic sensitivity and prognostic assessment, particularly in patients with atypical symptoms, where the diagnostic efficacy of existing biomarkers is often insufficient [3–5]. Additionally, traditional biomarkers struggle to fully reflect the complex pathophysiological processes of AMI, including key components such as inflammatory responses, oxidative stress, and myocardial remodeling [6, 7]. Therefore, identifying novel biomarkers with higher sensitivity and specificity holds significant clinical importance for achieving early, precise diagnosis and personalized treatment of AMI.

  Macrophages are key effector cells of the innate immune system, and resident cardiac macrophages are responsible for the efficient clearance and degradation of apoptotic myocardial cells, playing a crucial role in inflammatory regulation and tissue repair following AMI [8]. Studies have shown that tissue‐resident cardiac macrophages can be divided into the CCR2‐subpopulation derived from embryos and the CCR2+ subpopulation derived from the adult hematopoietic lineage [9]. Among these, the CCR2‐subpopulation primarily promotes coronary artery development, cardiac regeneration, and facilitates signal transmission within the atria and ventricles [10]. CCR2+ subpopulation macrophages primarily originate from monocytes. Related studies have revealed that these macrophages can promote monocyte recruitment, release of monocyte chemotactic protein (MCP), and cell mobilization through a MYD88‐dependent mechanism [11]. Studies have shown that macrophages rapidly infiltrate the infarct area after myocardial ischemia and participate in different stages of pathophysiological processes through phenotypic polarization. Among them, proinflammatory M1 macrophages exacerbate early myocardial damage, whereas anti‐inflammatory M2 macrophages promote late tissue repair, and the dynamic balance between the two directly affects the process of myocardial remodeling [12]. From a regulatory mechanism perspective, macrophages stimulated by proinflammatory signals such as lipopolysaccharides and interferons typically exhibit enhanced phagocytic activity and antigen presentation functions. They can induce a proinflammatory microenvironment through proinflammatory cytokines like IL‐12 and IL‐23, as well as chemokines such as CXCL9 and CXCL10, thereby affecting AMI repair [13]. In contrast, M2 macrophages selectively produce anti‐inflammatory cytokines such as IL‐10, which stimulate fibroblast‐mediated extracellular matrix production and cell proliferation, thereby promoting myocardial tissue remodeling and repair [14]. Therefore, using macrophage‐related characteristics as a starting point not only reveals the key molecular mechanisms of AMI but also provides a unique perspective for developing molecular targets with both diagnostic value and therapeutic potential.

  This study analyzed the single‐cell atlas of AMI and clarified the pivotal role of macrophages in AMI pathogenesis. By integrating weighted gene coexpression network analysis (WGCNA) with other computational approaches, we identified macrophage‐ and AMI‐related key genes as potential diagnostic biomarkers, and their dysregulated expression was further validated in an oxygen–glucose deprivation (OGD)–induced AC16 cardiomyocyte model. Subsequent molecular docking suggested candidate therapeutic agents targeting these biomarkers, providing a preliminary basis and important reference for the development of new diagnostic and therapeutic strategies for AMI.


## 2. Materials and Methods

### 2.1. Data Acquisition
  The single‐cell multiomics dataset GSE270788 and the bulk microarray dataset GSE66360 were obtained from the Gene Expression Omnibus (GEO) database (http://www.ncbi.nlm.nih.gov/geo). We obtained cardiac tissue samples from five AMI cases and seven healthy controls in the GSE270788 dataset. Additionally, we obtained samples from the GSE66360 dataset, which includes 50 healthy controls and 49 MI cases. Both datasets are publicly available, and no specific permission was required for their use in this study.


### 2.2. Single‐Cell Data Analysis
  For the GSE270788 dataset, we used the Seurat package [15] to read the scRNA‐seq data, retaining cells with a mitochondrial gene proportion < 7.5% and a gene count between 200 and 3000, resulting in a total of 28,619 cells. We then standardized the data using the ScaleData function, performed principal component analysis (PCA) dimensionality reduction, and used the harmony package to remove batch effects between different samples. After dimensionality reduction using the first 20 principal components via uniform manifold approximation and projection (UMAP), we clustered the cell subpopulations using the FindNeighbors and FindClusters functions (resolution = 0.2). Cell types were determined based on the expression of known marker genes from the CellMarker database.


### 2.3. Cell Communication
  This study used the CellChat package [16] to explore ligand–receptor pairs in cell subpopulation interactions, using bubble plots to display the likelihood and significance of ligand–receptor interactions between cell subpopulations.


### 2.4. Enrichment Analysis
  This study used the FindMarkers function to identify differentially expressed genes between different cell subpopulations and used the gseGO function of the clusterProfiler package [17, 18] to perform biological process enrichment analysis on gene sets sorted by logFC.


### 2.5. Transcription Factor Analysis
  In this study, the human RcisTarget database was downloaded from the website (https://resources.aertslab.org/cistarget/) for the construction of the transcription factor regulatory network. The network was constructed using the R package SCENIC [19]. A regulon is a set of target genes regulated by the same TF, and the AUCell algorithm [19] was used to evaluate transcription factor activity.


### 2.6. High‐Dimensional Weighted Gene Coexpression Network Analysis (hdWGCNA)
  In this study, AMI sample cell clusters were selected from scRNA data, and only genes expressed in ≥ 5% of cells were retained to create an initial WGCNA object. Subsequently, the KNN algorithm with k = 25 was used to aggregate cells, integrating up to 20 neighboring cells into a single metacell to reduce the sparsity of the single‐cell expression matrix. The optimal soft threshold power was automatically selected using pickSoftThreshold(), and a weighted coexpression network was constructed based on this. Module feature relationship analysis identified modules significantly associated with macrophages, and key genes in important modules were identified based on their intramodule connectivity. The Top 15 genes were considered to be module feature genes associated with macrophages.


### 2.7. WGCNA Identifies AMI‐Related Genes
  The GSE66360 dataset was used in WGCNA [20] to identify gene modules associated with AMI. First, the samples were clustered to identify coexpression modules. The study demonstrated that the coexpression network conforms to a scale‐free network, where the logarithm of the degree k of a node (log(k)) is negatively correlated with the logarithm of the probability of the node′s occurrence (log(P(k))), with a correlation coefficient exceeding 0.85. To ensure the network is scale‐free, the soft threshold β is determined using the pickSoftThreshold() function. Next, the expression matrix is converted into an adjacency matrix, which is then converted into a topological matrix. Based on topological overlap matrix (TOM), genes are clustered using average‐linkage hierarchical clustering.


### 2.8. Molecular Docking
  In this study, the intersection of SCENIC analysis results, macrophage‐related module characteristic genes, and AMI‐related genes was obtained to identify potential biomarkers for AMI in this study. The receiver operating characteristic (ROC) curve and area under the curve (AUC) analysis were performed using the R package pROC to evaluate the diagnostic performance of each biomarker for the disease. Three‐dimensional structures of drug molecules were downloaded from the PubChem website (https://pubchem.ncbi.nlm.nih.gov/) as ligands, and the three‐dimensional structures of targeted drugs were minimized using the ChemBioOffice software. Receptor protein crystal structures were obtained from the Uniprot database (https://www.uniprot.org/), and 3D structure files of target proteins were downloaded from the PBD database (https://www.rcsb.org/). Water molecules and ligands were removed using Pymol software [21], and molecular docking was performed using AutoDockTools software. The screening criteria were as folows: binding energy < −5 kcal/mol.


### 2.9. Cell Culture and OGD Treatment
  Human cardiomyocytes AC16 were used in this study. Cells were maintained in Dulbecco′s modified Eagle′s medium (DMEM) with high glucose supplemented with 10% fetal bovine serum (FBS) and 1% penicillin–streptomycin under standard culture conditions (37°C, 5% CO2, saturated humidity) in a humidified incubator. Cells were passaged at 70%–80% confluence using Trypsin–EDTA and were routinely tested to be mycoplasma‐free.

  For establishment of the OGD–reoxygenation model, AC16 cells were seeded in appropriate culture plates and grown to approximately 70%–80% confluence. After the removal of the complete medium, cells were gently rinsed two to three times with glucose‐free phosphate‐buffered saline (PBS) to thoroughly eliminate residual high‐glucose medium. Prewarmed glucose‐free DMEM was then added, and the cells were transferred to a hypoxic incubator (37°C, 1% O2, 5% CO2, 94% N2) for 2–6 h to induce OGD [22, 23]. At the end of hypoxic incubation, the glucose‐free medium was discarded and replaced with high‐glucose DMEM containing 10% FBS, and the cells were returned to a normoxic incubator (37°C, 5% CO2) for 24 h to mimic reperfusion injury. Control cells were maintained in high‐glucose DMEM with 10% FBS under standard normoxic conditions throughout the same period.


### 2.10. Quantitative Real‐Time PCR (qRT–PCR)
  Total RNA was extracted from cultured cells using TRIzol reagent (15596026CN; Invitrogen, Carlsbad, California, United States) in accordance with the manufacturer′s protocol. RNA yield and quality were assessed with a NanoDrop spectrophotometer (Thermo Fisher Scientific, United States). Complementary DNA (cDNA) was generated from total RNA using a reverse transcription kit (D7178S, Beyotime, Shanghai, China). Quantitative PCR was subsequently performed on an Applied Biosystems real‐time PCR platform (Applied Biosystems, Foster City, California, United States) using SYBR Green qPCR Mix (D7260, Beyotime, China).

  The amplification conditions were as follows: an initial denaturation at 95°C for 10 min, followed by 30 cycles of 95°C for 15 s, 60°C for 30 s and 72°C for 1 min, and a final extension at 72°Cfor 5 min. Relative mRNA expression levels were calculated using the 2−Δ ΔCt method, with GAPDH serving as the endogenous control. Primer sequences are listed in Table 1. All samples were run in technical triplicates, and no‐template controls were included in each assay to monitor specificity and exclude contamination.


### 2.11. Statistical Analysis
  All statistical analyses were conducted using R software (Version 4.2.0). Differences in continuous variables between two groups were assessed with the Wilcoxon rank‐sum test. All cellular experiments were performed in at least three independent biological replicates. qRT–PCR data were analyzed using two‐way analysis of variance (ANOVA) to evaluate the effects of treatment (control vs. OGD) and gene expression levels. When a significant interaction or main effect was detected, Bonferroni′s multiple comparisons test was applied to adjust for multiple testing. Data are presented as mean ± standard deviation (SD). A two‐sided p value < 0.05 was considered to indicate statistical significance.


## 3. Results

### 3.1. AMI Single‐Cell Atlas
  After cell filtering, standardization, dimensionality reduction, and clustering, we identified a total of eight clusters. Through cell annotation using the cellmarkar2.0 website, we ultimately obtained six cell types: adipocyte, cardiomyocyte, endothelial cell, fibroblast, macrophage, and smooth muscle cell (Figure 1A–C). By comparing the differences in cell proportions between AMI and donor samples, we found that compared with healthy controls, AMI had a lower proportion of cardiomyocytes and higher proportions of macrophages, fibroblasts, and adipocytes (Figure 1D).


### 3.2. Analysis of Cell–Cell Communication in AMI Cell Subpopulations
  To further elucidate the cell–cell communication relationships in AMI, we analyzed single‐cell transcriptomic data using CellChat and systematically compared it with a healthy control group. The results showed that the number and intensity of cell–cell communication in the AMI group were significantly higher than those in the control group (Figure 2A–B). Further analysis at the cellular type level revealed that communication intensity between fibroblasts, cardiomyocytes, and macrophages was significantly enhanced in the AMI group, particularly in terms of signal flow toward endothelial cells, whereas such communication was weaker in the healthy control group (Figure 2C–F). At the signaling pathway level, the relative information flow in pathways related to SEMA3, ANGPTL, and ADIPONECTIN was significantly higher in the AMI group than in the healthy control group (Figure 2G). Key ligand–receptor pair analysis further revealed highly active intercellular communication events in AMI, including enhanced axes such as SEMA3C − PLXND1, SEMA3C − (NRP1 + PLXNA4), and NAMPT − (ITGA5 + ITGB1) (Figure 2H–I).


### 3.3. Functional Enrichment of Cell Subpopulations in AMI
  We performed GSEA on macrophages, cardiomyocytes, endothelial cells, and fibroblasts in AMI. In macrophages, multiple pathways related to stress and metabolism were significantly activated in the AMI group, including response to nutrients, response to corticosteroids, and regulation of hormone levels. Some developmental pathways related to cardiac muscle morphogenesis, such as cardiac muscle tissue morphogenesis and ventricular cardiac muscle tissue development, were suppressed in AMI (Figure 3A). In cardiomyocytes, mitochondrial metabolic pathways such as aerobic respiration, oxidative phosphorylation, and cellular respiration were inhibited in AMI, whereas developmental pathways such as blood vessel development and cell morphogenesis were activated in AMI (Figure 3B). In endothelial cells, energy metabolism‐related pathways were inhibited, whereas the response to fibroblast growth factor was activated in AMI (Figure 3C). In fibroblasts, pathways related to mitochondrial metabolism and respiration were inhibited in AMI, whereas pathways such as response to cAMP, axon guidance, and collagen fibril organization were activated in AMI (Figure 3D).


### 3.4. Gene Screening of Modules Related to Macrophages in AMI
  This study focused on macrophage subpopulations in AMI as the analysis subject. The pickSoftThreshold() function was used to automatically screen for the optimal soft threshold power β = 6, and a weighted gene coexpression network was constructed based on this (Figure 4A,B). By calculating the module feature vector (ME) and gene internal connectivity, the data were ultimately divided into 10 coexpression modules, and the hub genes of each module were identified (Figure 4C).

  Subsequently, we calculated the expression levels of genes within each module in different cell types. We found that genes in Modules M5 and M8 exhibited higher expression proportions and levels in macrophages (Figure 5A,B). Therefore, we selected these two modules as key modules and extracted the hub gene networks within them (Figure 5C).


### 3.5. Identification of Key Transcription Factors in Macrophages
  This study identified two highly significant regulatory factors in macrophages: FOS and ETV6, both of which showed significantly higher regulatory activity in AMI patients than in the control group (Figure 6A). Further enrichment analysis of the target gene sets for the two regulons revealed that these downstream genes were significantly enriched in processes such as regulation of hemopoiesis, cellular response to transforming growth factor, membrane invagination, and regulation of fibroblast proliferation (Figure 6B). Finally, this study constructed a regulatory network diagram linking the key regulatory factors to their target genes (Figure 6C).


### 3.6. WGCNA Identification of Genes Associated With AMI
  In this study, WGCNA was performed on GSE66360 to screen for AMI‐associated genes. Appropriate parameters were determined through soft threshold screening, with the scale‐free topological fitting index reaching stability at a soft threshold of 16 (Figure 7A). Based on this, hierarchical clustering was performed on the genes, and a clustering dendrogram was generated (Figure 7B). Among these, the brown module showed the strongest positive correlation with AMI (Figure 7C). The number of genes in each module is shown in Figure 7D. According to the screening criteria (MM > 0.8 and GS > 0.2), 133 genes with high connectivity were identified as hub genes (Figure 7E). Gene enrichment analysis of the brown module revealed significant enrichment in immune regulation–related pathways such as neutrophil degranulation, immune response–regulating signaling pathways, and inflammatory response (Figure 7F).


### 3.7. Identification of Key Biomarkers Associated With AMI and Molecular Docking
  In this study, genes screened by WGCNA, SCENIC analysis, and hdWGCNA were intersected to obtain GAS7 and ZEB2 as potential biomarkers for AMI (Figure 8A). In the GSE66360 dataset, ROC analysis validated the good diagnostic performance of the two genes in AMI, with AUC values of 0.78 and 0.83, respectively (Figure 8B). GAS7 and ZEB2 were both significantly overexpressed in the AMI group (Figure 8C).

  In the subsequent analysis, we predicted the potential drug–protein interaction networks for GAS7 and ZEB2, identified sulforaphane as a target compound, and performed molecular docking analysis using the crystal structures 2lx7 of GAS7 and 2da7 of ZEB2 (Table 2). The results showed that the binding energy between GAS7 and sulforaphane was −7.41 kcal/mol, indicating good binding stability (Figure 8D).


### 3.8. Validation of FOS, ETV6, GAS7, and ZEB2 Expression in an OGD‐Induced Injury Model
  To experimentally validate the expression patterns of the key regulators and biomarkers identified by integrative bioinformatics analyses, we established an OGD model in vitro. qRT–PCR showed that the mRNA levels of FOS, ETV6, GAS7, and ZEB2 were all significantly upregulated in OGD‐treated AC16 compared with the control group (Figure 9). These results are consistent with the transcriptomic findings and further support the involvement of these genes in ischemic myocardial injury.


## 4. Discussion
  The pathogenesis of AMI is complex, involving inflammatory responses, immune cell infiltrations, and interactions between various cell types [24–26]. In recent years, research has increasingly recognized the important role of the immune system, particularly innate immune cells, such as macrophages, in the treatment of AMI. Macrophages not only participate in the clearance and repair of necrotic myocardium but also influence tissue remodeling and functional recovery in the late stages of myocardial injury through cytokine secretion and regulation of cellular communication [27–29]. However, the molecular mechanisms underlying AMI remain unclear, and there is a lack of stable and effective diagnostic biomarkers and treatment strategies [30]. Here, we integrate single‐cell transcriptomic data with conventional transcriptomic data for the first time to systematically analyze the cellular communication networks and transcriptional regulatory mechanisms of AMI from a macrophage perspective. By innovatively combining multilevel bioinformatics methods such as hdWGCNA, SCENIC, and WGCNA, we have identified GAS7 and ZEB2 as novel diagnostic biomarkers for AMI closely associated with macrophages. These findings provide new candidate biomarkers for the early diagnosis of AMI and are expected to advance the development of precision diagnostics and personalized treatment strategies for AMI.

  This study identified two highly significant regulatory factors in macrophages: FOS and ETV6, both of which exhibited significantly higher regulatory activity in AMI patients compared with the control group. Upregulation of FOS plays a crucial role in myocardial lesions and may be involved in the pathogenesis of AMI, as demonstrated by a related study where metoprolol inhibition of FOS expression in rats showed positive therapeutic effects on AMI rats [31]. Additionally, FOS in macrophages is associated with tissue repair and inflammatory progression following myocardial infarction. For example, the synergistic effect of Lgr4 in inflammatory phenotype macrophages on AP‐1 activation is achieved through the transactivation of FOS, thereby influencing tissue repair and exacerbating inflammatory progression [32]. ETV6 encodes a transcription repressor factor of the E26 transformation‐specific family. Recent reports indicate that variants in ETV6 are responsible for hereditary thrombocytopenia and hematological malignancies, as ETV6 functions as a cytoskeletal regulatory gene in platelet production, leading to alterations in platelet size, shape, and function, as well as changes in circulating progenitor cell levels, which have adverse effects on cardiovascular disease [33]. ETV6 in macrophages is associated with NF‐κB pathway activation and the expression of IL‐1β, IL‐6, and TNF‐α, playing a role in the atherosclerosis process by promoting plaque formation, local inflammation, and thrombosis [34]. As such, both regulatory factors are closely associated with macrophage phenotype regulation, consistent with the findings of this study, which indicate that the target genes of these two regulatory factors are significantly enriched in pathways related to cellular phenotype regulation, such as the cellular response to transforming growth factor, thereby influencing AMI.

  This study further screened candidate genes using WGCNA and ultimately identified GAS7 and ZEB2 as potential biomarkers in AMI. Notably, the upregulation of FOS, ETV6, GAS7, and ZEB2 was further validated by qRT–PCR in an OGD‐induced AC16 cardiomyocyte model, which mirrored the dysregulation patterns identified in public AMI datasets and provided experimental support for our integrative bioinformatics findings. A study found that GAS7 was significantly upregulated in M1 polarization of macrophages, accompanied by activation of the NF‐κB pathway in cells, whereas knockdown of GAS7 reduced M1 polarization and expression of M1 marker genes [35]. This indicates that GAS7 is closely associated with the proinflammatory phenotype of macrophages, and proinflammatory macrophages have adverse effects on both early myocardial injury and subsequent tissue repair in AMI [36]. Myocardial cells stimulate angiogenesis in a ZEB2‐dependent manner following ischemic injury. Specifically, myocardial cells in the infarcted heart induce the expression of TMSB4 and PTMA by expressing ZEB2, thereby enhancing endothelial cell migration to stimulate angiogenesis and prevent heart failure [37]. Thus, the genes screened based on macrophage characteristics in this study are associated with cardiovascular disease regulation or cardiomyocyte phenotype and may have potential diagnostic value for AMI.

  This study further predicted the potential drug–protein interaction network of GAS7 and ZEB2, identifying sulforaphane as a target compound, with GAS7 exhibiting good binding stability with sulforaphane. Sulforaphane is the most common antioxidant component in cruciferous plants [38, 39]. Previous studies have shown that this compound can delay the progression of inflammation‐induced liver fibrosis by regulating intracellular oxidative stress levels, involving the JAK/STAT3 pathway [40]. In the regulation of cardiovascular‐related diseases, sulforaphane inhibits myocardial cell apoptosis and oxidative stress in myocardial cells, thereby alleviating myocardial damage [41]. An animal experiment validated sulforaphane′s excellent cardiac protective effects, demonstrating that long‐term low‐dose sulforaphane treatment of fibroblasts enhances the release of F‐EXO exosomes targeting cardiomyocytes, thereby effectively preventing the onset of heart failure. This opens a new avenue for the large‐scale production of cardiac protective exosomes using fibroblasts for clinical applications [42]. This also validates the efficacy of sulforaphane as a potential therapeutic agent for AMI.

  This study also has certain limitations. First, the study data were primarily derived from public databases, with a relatively limited sample size and a lack of external independent validation cohorts. In the future, it will be necessary to collect clinical samples from AMI patients across multiple centers and with a large sample size to validate the robustness and universality of GAS7 and ZEB2 as diagnostic biomarkers through prospective cohort studies. Second, the specific molecular mechanisms by which GAS7 and ZEB2 regulate macrophage function and AMI progression have been inferred solely through bioinformatics predictions, with a lack of direct evidence at the tissue level or in animal models. Future studies should establish macrophage‐specific GAS7/ZEB2 knockout mice or utilize lentivirus‐mediated gene overexpression/silencing techniques, combined with AMI animal models and experimental methods such as immunohistochemistry and Western blotting, to elucidate the signaling pathways involved in macrophage polarization, cytokine secretion, and myocardial repair. Third, molecular docking suggests that sulforaphane binds well to GAS7; however, its therapeutic efficacy as a targeted treatment has not yet been validated at the cellular or animal level. Therefore, future studies should validate the direct binding between the two using surface plasmon resonance (SPR) or cell‐based thermal shift analysis (CETSA), and evaluate the effects of sulforaphane administration on GAS7 expression, macrophage phenotype, and cardiac function parameters in OGD‐induced cardiomyocytes or AMI animal models to clarify its clinical translation potential as a drug candidate. Through these targeted studies, it is anticipated that the preliminary findings of this research can be advanced toward clinical diagnostic and therapeutic applications.


## 5. Conclusion
  In summary, this study utilized single‐cell transcriptomics to identify various cell subpopulations in AMI, elucidated the crucial role of macrophages, and combined WGCNA and other analytical methods to identify key genes associated with macrophages as potential biomarkers. Further molecular docking simulations revealed potential therapeutic drugs for AMI, providing guidance for the development of novel treatment strategies for AMI.


## N/A

## Author Contributions
  All authors contributed to this present work. Zhenfang Liu designed the study. Jia Song and Lingling Li acquired the data. Li Yang interpreted the data. Ziyin Fan drafted the manuscript. Genyuan Xie revised the manuscript.


## Funding
  The study was supported by Hunan Provincial Natural Science Foundation of China (2023JJ50220).


## Disclosure
  All authors read and approved the manuscript.


## Ethics Statement
  Ethical approval was not required for this study because it involved no animal or human experiments.


## Consent
  The authors have nothing to report.


## Conflicts of Interest
  The authors declare no conflicts of interest.


## Data Availability Statement
  The datasets generated and/or analyzed during the current study are available in the [GSE66360] repository [https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE66360] and [GSE270788] repository [https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE270788].


## Acknowledgments
  The authors have nothing to report.