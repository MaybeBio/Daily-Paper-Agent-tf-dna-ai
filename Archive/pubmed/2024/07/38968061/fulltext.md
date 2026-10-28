# Integrating network pharmacology and Mendelian randomization to explore potential targets of matrine against ovarian cancer


## BACKGROUND:
  Matrine has been reported inhibitory effects on ovarian cancer (OC) cell progression, development, and apoptosis. However, the molecular targets of matrine against OC and the underlying mechanisms of action remain elusive.


## OBJECTIVE:
  This study endeavors to unveil the potential targets of matrine against OC and to explore the intricate relationships between these targets and the pathogenesis of OC.


## METHODS:
  The effects of matrine on the OC cells (A2780 and AKOV3) viability, apoptosis, migration, and invasion was investigated through CCK-8, flow cytometry, wound healing, and Transwell analyses, respectively. Next, Matrine-related targets, OC-related genes, and ribonucleic acid (RNA) sequence data were harnessed from publicly available databases. Differentially expressed analyses, protein-protein interaction (PPI) network, and Venn diagram were involved to unravel the core targets of matrine against OC. Leveraging the GEPIA database, we further validated the expression levels of these core targets between OC cases and controls. Mendelian randomization (MR) study was implemented to delve into potential causal associations between core targets and OC. The AutoDock software was used for molecular docking, and its results were further validated using RT-qPCR in OC cell lines.


## RESULTS:
  Matrine reduced the cell viability, migration, invasion and increased the cell apoptosis of A2780 and AKOV3 cells (P< 0.01). A PPI network with 578 interactions among 105 candidate targets was developed. Finally, six core targets (TP53, CCND1, STAT3, LI1B, VEGFA, and CCL2) were derived, among which five core targets (TP53, CCND1, LI1B, VEGFA, and CCL2) differential expressed in OC and control samples were further picked for MR analysis. The results revealed that CCND1 and TP53 were risk factors for OC. Molecular docking analysis demonstrated that matrine had good potential to bind to TP53, CCND1, and IL1B. Moreover, matrine reduced the expression of CCND1 and IL1B while elevating P53 expression in OC cell lines.


## CONCLUSIONS:
  We identified six matrine-related targets against OC, offering novel insights into the molecular mechanisms underlying the therapeutic effects of matrine against OC. These findings provide valuable guidance for developing more efficient and targeted therapeutic approaches for treating OC.


## Introduction
  Ovarian cancer (OC) is the most devastating malignancy among female reproductive carcinomas, tragically ranking as the fifth leading cause of cancer-related deaths among women worldwide [1]. Shockingly, merely a quarter of women with OC receive an early diagnosis at Stage I/II, and a staggering majority (75%) are confronted with the challenges of advanced stages (Stage III/IV) at the time of diagnosis [2]. A clinical investigation unequivocally underscores the pivotal role of metastasis in determining unfavorable survival outcomes for OC patients [3]. Despite the aggressive implementation of frontline treatments, such as surgical interventions and adjuvant chemotherapy, the 10-year survival rates for women diagnosed with OC at Stage III and Stage IV remain a mere 21% and less than 5%, respectively [4]. Consequently, the pressing need to explore more therapeutic agents and their precise targets for combating OC becomes ever more imminent.

  Matrine (C15H24N2O) is an intriguing alkaloid extracted from the Sophora family, which has been shown to have potential therapeutic effects on human diseases associated with epithelial cells [5, 6]. Previous study has demonstrated that matrine modulates various biological activities, such as apoptosis, oxidative stress, inflammation, fibrosis, and the immune response [7]. Notably, a published study has underscored the role of matrine role in promoting OC cell apoptosis by modulating the ERK/JNK signaling pathway [8]. Additionally, the efficacy of matrine in suppressing OC cell progression and development has been attributed to its inhibition of phosphorylation signaling pathways [9]. However, despite these findings, the specific targets through which matrine exerts its effects on OC remain unclear, warranting further investigation.

  Mendelian randomization (MR) is a rapidly advancing field grounded in Mendel’s law of inheritance. MR utilizes single nucleotide polymorphisms (SNPs) as instrumental variables (IVs) to uncover causal relationships between modifiable exposures and clinically important outcomes [10]. By utilizing genetic variants as instrumental variables, MR provides a robust approach to estimating the causal associations between exposures and their impacts on outcomes, lending valuable insights into the realm of causality in epidemiological research. MR can be employed to investigate the causal links between particular risk factors and tumor risk [11, 12, 13]. However, exploring the causal relationships using MR between matrine-related core targets and OC risk has not been reported.

  The primary objective of this study is to identify potential targets of matrine in OC and to investigate their associations with the disease. To achieve this, we conducted a comprehensive analysis, including differential expression analysis and protein-protein interaction (PPI) network analysis, to uncover the core targets of matrine against OC. Remarkably, six core genes were identified: TP53, STAT3, CCND1, VEGFA, IL1B, and CCL2. Furthermore, the causal associations between core targets and OC were investigated using an MR study. Finally, molecular docking analysis was performed to investigate the molecular docking site and binding energy, and the results were further validated in vitro. The pictorial representation of the methodology is shown in Supplementary Fig. 1.

  Figure 1.Effects of matrine on OC cell lines A2780 and SKOV3 cells. (A) CCK-8 assay CCK-8 detected the cell viability of A2780 and SKOV3 cells. (B) Flow cytometry detected cell apoptosis. (C) Wound healing detected cell migration. (E) Transwell assay detected cell invasion (scale bar = 50 μm). ** P < 0.01.


## Materials and methods

### Cells culture and treatment
  OC cell lines A2780 (#CL-0013, Procell, Wuhan, China) and SKOV3 cells (#CL-0215, Procell) were cultured in RPMI-1640 medium (Gibco, CA, USA) at 37∘C with 5% CO2. Matrine purchased from Wuhan Zhongbiao Science & Technology CO. (Wuhan, China) was diluted into 2 mg/mL and then used to treat cells for 24 h.


### Cells counting kit 8 (CCK-8) analysis for cell viability
  SKOV3 and A2780 cells were inoculated in a 96-well plate (100 μL/cell). After being treated with matrine for 24 h, 10 μL CCK-8 solution (Beyotime, Shanghai, China) was added into each well and incubated with cells for 2 h. Absorbance at 450 nm was determined with a microplate reader (Wuxi Hiwell Diatek, Jiangsu, China).


### Flow cytometry for cell apoptosis
  Flow cytometry was performed to assess the cell apoptosis in SKOV3 and A2780 cells. After culture for 24 h, cells were gathered and suspended in 195 μL FITC binding buffer (Beyotime). Then cells were stained with Annexin V-FITC (5 μL) and propidium iodide (10 μL) at 25∘C for 15 min and 10 min, respectively.


### Cell migration and invasion
  Would healing was used to assess of cell migration. SKOV3 and A2780 cells were lated in 6-well plates (5 × 105 cells/well). Then a sterilized pipette was used for scratches and cells were incubated in serum-free DMEM for 24 h.

  Transwell were employed to assess cell invasion. SKOV3 and A2780 cells were seeded into upper chamber, and DMEM containing 10% FBS was added to the lower chamber. After 24 h incubation, cells were washed with PBS, fixed with methanol, and stained with 0.1% crystal violet.


### Data acquisition and preprocessing
  The GeneCards (www.genecards.org) [14], Herbal Ingredients’ Targets Platform (HIT; http://hit2.badd-cao.net) [15], SwissTargetPrediction (www.swisstargetprediction.ch) [16], and SuperPred (http://prediction. charite.de/index.php) [17] databases were adopted to explore and predict the possible matrine-related targets. OC-related genes were downloaded from GeneCards and DisGeNET (http://www.disgenet.org) [18] online platforms. The GSE66957 containing mRNA profile information of 57 OC cases and 12 controls and GSE26712 including mRNA profile information of 185 OC cases and 10 controls were searched from the Gene Expression Omnibus (GEO, http://www.ncbi.nlm.nih.gov/geo/) database.


### Identification of potential matrine-related targets against OC
  The limma package was implemented to obtain differentially expressed genes (DEGs) in OC with detecting conditions of P< 0.05 and |logFoldChange(FC)|> 1 in the GSE66957 cohort. Subsequently, the VennDiagram package was performed to select intersecting genes by overlapping OC-related genes, matrine-related targets, and DEGs.


### PPI network development and core targets selection
  Search Tool for the Retrieval of Interacting Genes (STRING; https://string-db.org) [19] platform was adopted to explore the molecular interactions of intersecting genes with score_cutoff > 0.4 and size_cutoff < 10 as the filtering conditions. Subsequently, the PPI network was visualized using Cytoscape software. Furthermore, the cytoHubba plugin was applied to get the core targets in the PPI network, and the candidate core targets were finally detected by intersecting the results of Maximal Clique Centrality (MCC), Edge Percolated Component (EPC), Maximum Neighborhood Component (MNC), and Degree algorithms using VennDiagram. The core targets were input into the online website GEPIA (http://gepia.cancer-pku.cn/detail.php) to validate their expression levels with |log2FC|⩾ 1 and P⩾ 0.01 as the cutoff values. The differential expression of these core targets was further validated in the dataset GSE26712.


### Mendelian randomization (MR)
  TwoSampleMR package in R software (Version 4.2.2) was employed to conduct MR analysis. The exposure-related drug-targeting instrumental variables were harmonized with the outcome datasets. Four statistical methods, including inverse variance weighting (IVW), weighted mode, weighted median, and simple mode, were applied to explore potential causal relationships between core targets and OC. P< 0.05 was considered statistical significance. The extract_instruments function was applied to obtain SNPs independently affecting the core targets and analyzed the causal relationship between the obtained SNPs and OC based on genome-wide association studies (GWAS, https://gwas.mrcieu.ac.uk/datasets/). The heterogeneity test was performed by MR Egger and IVW methods.


### Molecular docking
  The three-dimensional (3D) protein structure of the core targets was obtained from the RCSB Protein Data Bank (RCSB) using the website http://www.pdb.org/. To isolate the modified and ligand components and eliminate water molecules, the Pymol software was utilized. Additionally, the 3D structure of matrine was acquired from PubChem, hydrogen atoms were added, and charges were calculated. Subsequently, Autodock (Version 4.2.6) software was employed to perform docking simulations with the core targets. A stable connection site was determined based on a threshold of limited binding energy ⩽-5.0 kcal⋅mol - 1 [20].


### Quantitative real-time PCR (qRT-PCR)
  Total RNA was isolated using Trizol (Invitrogen, CA, USA). Reverse transcription utilized the cDNA Reverse Transcription Kit (TIANGEN, Beijing, China) to synthesize cDNA. Quantitative PCR was conducted using SYBR Green PCR Master Mix (Lifeint, Xiamen, China) on the StepOnePlus Real-Time PCR System (Bio-rad, CA, USA). Specific primers designed for CCND1, IL1B, p53, and GAPDH (internal control) were used in a 20 μL reaction volume. The cycling conditions included an initial denaturation of 95∘C for 3 min, followed by 40 cycles of 95∘C, 12 s and 62∘C, 40 s, with subsequent melt curve analysis. Expression levels were calculated using the 2 - ΔΔCT method and normalized to GAPDH. Primer sequences were as follows: GAPDH: forward, 5’-3’-GAA GGT GAA GGT CGG AGT CA, reverse, 5’-3’-GAC AAG CTT CCC GTT CTC AG; CCND1: forward, 5’-3’-TCC TAC TAC CGC CTC ACA, reverse, 5’-3’-ACC TCC TCC TCC TCC TCT; IL1B: forward, 5’-3’-GCT CGC CAG TGA AAT GAT GG, reverse, 5’-3’-AAC ACG CAG GAC AGG TAC AG; P53: forward, 5’-3’-CCT GAG GTT GGC TCT GAC TG, reverse, 5’-3’-CTT CTT TGG CTG GGG AGA GG.


### Statistical analysis
  Statistical analysis of the RT-qPCR data was performed using GraphPad Prism software 8.0. After confirming that the data met the assumptions of normality and equal variance, we employed Student’s t-test to compare the means between the two groups. Each set of experiments was conducted in triplicate, and results were expressed as mean ± standard deviation. P< 0.05 was considered statistically significant.


## Results

### Effects of martrine in cell viability, apoptosis, migration, and invasion in vitro
  To investigate the effects of matrine on OC, A2780 and AKOV3 cells were cultured. Significantly, matrine reduced the cell viability, migration, invasion and increased the cell apoptosis of A2780 and AKOV3 cells (P< 0.01, Fig. 1A–D), indicating the therapy effectiveness in OC.


### Potential targets of matrine against OC
  To further investigate the targets of matrine on OC, network pharmacology and mendelian randomization were conducted. Totally 635 possible matrine targets and 5,513 OC-related genes were obtained from the online websites after removing duplicates (Fig. 2A–B, Supplementary Table 1). A total of 8,001 DEGs were detected from the GSE66957 cohort, which comprised 4,990 up-regulated genes and 3011 down-regulated genes (Fig. 2C–D, Supplementary Table 2). Finally, 105 potential targets of matrine against OC were confirmed by overlapping 635 possible targets of matrine, 5,513 OC-related genes, and 8,001 DEGs (Fig. 2E, Supplementary Table 3).

  Figure 2.Identification of potential targets of matrine against OC. (A) The possible targets of matrine are from HIT, SwissTargetPrediction, SuperPred, and GeneCards databases, respectively. (B) OC-related genes were obtained from the GeneCards and DisGeNET online websites, respectively. (C) Volcanic map of DEGs in GSE66957 cohort. (D) Heat map of the expression levels of DEGs between OC cases and controls from GSE66957 cohort. Blue represents down-regulation, and red represents up-regulation. (E) Venn diagram shows 105 interacting genes among OC-related genes, targets of matrine, and DEGs. OC: ovarian cancer; DEGs: differentially expressed genes.

  Figure 3.Screening of hub targets. (A) PPI network of 105 intersecting genes. (B) Four core modules (Degree, EPC, MCC, and MNC) in the PPI network. (C) Venn diagram shows the six hub targets among four core modules. PPI: protein-protein interaction.


### Identification of core targets
  The PPI network including 578 interactions among 105 potential targets of matrine was developed and shown in Fig. 3A. In addition, four core modules in the PPI network consisted of genes with the top 10 scores calculated by MCC, MNC, EPC, and Degree algorithms exhibited in Fig. 3B. By intersecting the four core modules, six core targets, consisting of TP53, STAT3, CCND1, VEGFA, IL1B, and CCL2, were further obtained (Fig. 3C). Moreover, the expression levels of six core targets were verified in the GEPIA database, and the results suggested that the expression of TP53, CCND1, VEGFA, IL1B, and CCL2 was remarkably higher in the OC samples than in the control group, whereas there was no significant difference in STAT3 (Fig. 4). Moreover, validation of the core targets differential expression in the GSE26712 dataset further revealed that TP53, CCND1, VEGFA, IL1B, and CCL2 levels were elevated in OC samples (Fig. 5).

  Figure 4.Box plots show the expression levels of CCL2, CCND1, IL1B, STAT3, TP53, and VEGFA between OC cases and controls based on the GEPIA database. Red indicates OC samples, while blue indicates normal samples. OC: ovarian cancer. * P < 0.05.

  Figure 5.Box plots show the expression levels of CCL2, CCND1, IL1B, STAT3, TP53, and VEGFA between OC cases and controls in validation dataset GSE26712. Red indicates OC samples, while blue indicates normal samples. OC: ovarian cancer. *P< 0.05, **P < 0.01, *** P< 0.001, *****  P< 0.0001.


### Evaluating the potential association between core targets and OC
  The SNP characteristics of CCND1, IL1B, TP53, VEGFA, and OC were meticulously presented in Supplementary Table 4, providing comprehensive insights into their genetic attributes. The causal correlations between the levels of core targets (CCND1, IL1B, TP53, and VEGFA) and the risk of OC were evaluated and shown in Fig. 6A–D, the results demonstrated that VEGFA and IL1B were protective factors for OC, while CCND1 and TP53 were risk factors for OC. The funnel plot exhibited a roughly symmetrical causal effect (Fig. 6E–H). Supplementary Table 5 demonstrated that CCND1 (Weighted median, β= 0.084, P= 0.021), IL1B (Weighted median, β=-0.146, P= 0.002; IVW, β=-0.088, P= 0.002; Weighted mode, β=-0.198, P= 0.001), TP53 (Weighted median, β= 0.129, P= 0.036), and VEGFA (Weight median, β=-0.146, P= 0.02; IVW, β=-0.146, P= 0.002; Weighted mode, β=-0.198, P= 0.001) were associated with the risk of OC. MR heterogeneity and multiple validity tests of exposure factors and OC were shown in Supplementary Table 6.


### Matrine-targets docking analysis
  To gain deeper insights into the molecular interactions, four genes (CCND1, IL1B, TP53, and VEGFA) detected by MR analysis were subjected to molecular docking as protein receptors interacting with matrine (CID: 91466). Based on the selection criteria of binding energy less than -5.0 kcal/mol and the ability to form hydrogen bonds between the receptor and ligand [20], the final docking results were obtained (Table 1). The results demonstrated that the binding energy scores of matrine target CCND1, IL1B, and TP53 were -5.918, -5.953, and -5.968 kcal⋅mol - 1, respectively (Fig. 7A–C). These findings indicated that the three identified genes do indeed bind stably to matrine.

  Table 1Results of molecular dockingGeneNameUniprotIDPDB IDCompoundPubchemIDBind energy (kcal/mol)TP53P046376ggcMatrineCID: 91466-5.968CCND1P243852w96-5.918IL1BP015845r8e-5.953

  Figure 6.Mendelian randomization study results. (A-D) Scatter plot showing the causal effect of CCND1, IL1B, TP53, and VEGFA on the risk of OC. (E-H) Funnel plots show overall heterogeneity of MR estimates of the effect of CCND1, IL1B, TP53, and VEGFA on OC. OC: ovarian cancer.

  Figure 7.Molecular docking site. (A) CCND1-matrine. (B) IL1B-matrine. (C) TP53-matrine. (D) RT-qPCR detected the mRNA expression of CCND1, IL1B, and P53. OC cell line A2780 and SKOV3 cells were treated with matrine. * P < 0.05, **P < 0.01.


### Validation of molecular docking in vitro
  We then validated the effect of matrine on levels of target genes CCND1, IL1B, and TP53 in OC cell lines A2780 and SKOV3.The expression levels of CCND1 and IL1B were decreased while P53 expression was increased in the marine-treated cells compared to control cells (P< 0.05, Fig. 7D). These results further indicated that matrine may treat OC by regulating the CCND1, IL1B, and TP53.


## Discussion
  OC is the second leading cause of gynecologic cancer deaths in women, with approximately 239,000 new cases reported annually (3.6% of cancer-related cases), resulting in approximately 152,000 deaths (4.3% of cancer-related deaths) annually worldwide [21]. Despite notable progress in medical research, patients with OC still face a formidable prognosis, with an approximate five-year survival rate of 59.6% after diagnosis in Asian countries [22]. Studies have demonstrated that matrine has anti-inflammatory properties [23] and inhibits progression and apoptosis in OC cells [8, 9]. Therefore, the present study applied network pharmacology, MR, and molecular docking analyses to explore the mechanism of matrine against OC, thus providing reference ideas and strategies for future OC prevention and treatment.

  Firstly, we verified the effects of matrine on the OC in vitro, suggesting that matrine decreased the cell viability, migration, invasion and increased cell apoptosis in OC cell line A2780 and SKOV3. This result is coincidence with the previous publications [8, 24, 25, 26]. Next, we detected six core matrine-related targets (TP53, CCND1, VEGFA, IL1B, CCL2, and STAT3), in which five genes (TP53, CCND1, VEGFA, IL1B, and CCL2) were remarkable differenttially expressed between OC and normal samples. Subsequent MR analyses provided valuable insights, suggesting that VEGFA and IL1B were protective factors for OC, whereas CCND1 and TP53 were risk factors for OC.

  CCND1 is a pivotal cell cycle regulatory protein frequently upregulated in human tumors and is associated with poor prognosis [27, 28, 29, 30]. MR analyses have shown a positive correlation between CCND1 and OC risk. Mechanistically, this may be due to CCND1 contributing to enhanced cell proliferation and division by forming a functional complex with cell cycle protein-dependent kinases (CDKs), effectively promoting the transition from the G1 to the S phase of the cell cycle [30].

  The TP53 protein functions as a crucial DNA-binding transcription factor, exerting its influence on hundreds of different promoter elements in the genome and thereby orchestrating the expression of numerous genes [31]. Playing a pivotal role in key cellular processes that regulate cell proliferation and preserve genomic integrity and stability [32], TP53 serves as a guardian of the genome. In human cancers, TP53 gene undergoes alterations in all but 5 residues of its 393 amino acids, making it truly exceptional among all cancer-associated genes [33]. Loss of heterozygosity at the TP53 motif is a common occurrence in OC [34, 35]. Considering these findings, TP53 emerges as a compelling candidate and potential risk factor in the context of OC.

  VEGFA serves as a pivotal controller in angiogenesis, acting as a specific mitogen for endothelial cells, an initiator of angiogenesis, and a mediator that enhances vascular permeability [36]. The significant role of VEGFA in promoting angiogenesis and its common upregulation in human cancers has led to the development of therapies targeting VEGF and VEGF receptors [37]. The role of VEGFA in promoting tumorigenesis and cancer cell survival in cancer remains contentious, likely attributed to its tissue-specific effects [38, 39, 40, 41]. A meta-analysis suggested that the VEGF + 936C > T polymorphism may be a protective factor against OC among whites [42], this is consistent with our MR results.

  We employed molecular docking analysis to investigate the therapeutic potential of matrine against OC. The results demonstrated promising binding interactions with three pivotal targets: TP53, CCND1, and IL1B. Furthermore, in vitro experiments revealed that matrine reduced expression levels of CCND1 and IL1B whereas increased the TP53 expression in OC cells. Thess indicate that matrine may exert its effects through targeted interactions with these critical proteins, shedding light on its molecular mechanisms of action in the context of OC treatment.

  Despite the valuable insights obtained from our research, it is important to acknowledge several limitations that warrant consideration. Primarily, the sample size utilized in this investigation was relatively small, and the reliance on a single dataset may introduce inherent biases that could impact the generalizability of our results. Moreover, this investigation only employed bioinformatics approaches and further in vitro and in vivo experiments are needed to validate our results. Next, the potential synergistic effects of matrine in combination with existing chemotherapeutic or targeted therapies needed to be explored. Finally, how matrine modulates the targets and potential pathways needed to be deeply delved.


## Conclusions
  Altogether, this study identified six pivotal matrine-related core targets (TP53, CCND1, STAT3, IL1B, VEGFA, and CCL2) against OC. MR analysis suggested intriguing insights into the potential roles of CCND1 and TP53 as risk factors in OC. Molecular docking analysis demonstrated that matrine had good potential to bind to TP53, CCND1, and IL1B. These findings collectively advance our understanding of the mechanism of action of matrine in OC and provide valuable insights into the potential efficacy of matrine.


## Funding
  The authors report no funding.


## Data availability statement
  The data that support the findings of this study are available from the GEO (https://www.ncbi.nlm.nih. gov/geo/) database.


## Ethical considerations
  This study do not involve human and animal studies and is exempt from Institutional Review Board approval.


## Supplementary Material

## Conflict of interest
  The authors declare that they have no conflict of interest.


## Acknowledgments
  The authors have no acknowledgments.