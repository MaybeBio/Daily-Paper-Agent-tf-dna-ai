# Identification of core genes shared by ischemic stroke and myocardial infarction using an integrated approach


## Background:
  Both ischemic stroke (IS) and myocardial infarction (MI) are caused by vascular occlusion that results in ischemia. While there may be similarities in their mechanisms, the potential relationship between these 2 diseases has not been comprehensively analyzed. Therefore, this study explored the commonalities in the pathogenesis of IS and MI.


## Methods:
  Datasets for IS (GSE58294, GSE16561) and MI (GSE60993, GSE61144) were downloaded from the Gene Expression Omnibus database. Transcriptome data from each of the 4 datasets were analyzed using bioinformatics, and the differentially expressed genes (DEGs) shared between IS and MI were identified and subsequently visualized using a Venn diagram. A protein–protein interaction (PPI) network was constructed using the Interacting Gene Retrieval Tool database, and identification of key core genes was performed using CytoHubba. Gene Ontology (GO) term annotation and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment analysis of the shared DEGs were conducted using prediction and network analysis methods, and the functions of the hub genes were determined using Metascape.


## Results:
  The analysis revealed 116 and 1321 DEGs in the IS and MI datasets, respectively. Of the 75 DEGs shared between IS and MI, 56 were upregulated and 19 were downregulated. Furthermore, 15 core genes – S100a12, Hp, Clec4d, Cd163, Mmp9, Ormdl3, Il2rb, Orm1, Irak3, Tlr5, Lrg1, Clec4e, Clec5a, Mcemp1, and Ly96 – were identified. GO enrichment analysis of the DEGs showed that they were mainly involved in the biological functions of neutrophil degranulation, neutrophil activation during immune response, and cytokine secretion. KEGG analysis showed enrichment in pathways pertaining to Salmonella infection, Legionellosis, and inflammatory bowel disease. Finally, the core gene–transcription factor, gene–microRNA, and small-molecule relationships were predicted.


## Conclusion:
  These core genes may provide a novel theoretical basis for the diagnosis and treatment of IS and MI.


## 1. Introduction
  Each year, approximately 15 million people worldwide experience a stroke. With a rapidly aging population, the morbidity and mortality rates associated with stroke (ischemic stroke [IS]) are increasing annually.[1] As one of the most devastating neurological disorders, IS causes a combination of physical, behavioral, cognitive, and psychological impairments.[2] The most common treatment for IS is intravenous thrombolysis using recombinant tissue plasminogen activators (rTPAs). The main disadvantage of this treatment plan is that the window for effective treatment is only 3 hours.[3] Myocardial infarction (MI), a disease characterized by high mobility and mortality, is a global health and economic challenge.[4] Acute MI (AMI) is the main cause of disability and death worldwide, and one of its serious complications is IS. Complex IS can cause considerable pain and financial burden to patients.[5] The pathophysiological mechanisms and risk factors of cardiovascular and cerebrovascular diseases, such as age, hypertension, and diabetes, share similarities.[6] However, the relationship between the mechanisms of these 2 diseases remains unclear. Moreover, identifying new biomarkers is necessary to improve the diagnosis and treatment of both IS and MI.[5]

  Bioinformatics analysis has been widely used to discover novel biomarkers of neurological and cardiovascular diseases.[7] Specifically, high-throughput gene sequencing technology can be used to reveal the mechanisms of disease occurrence and development at various molecular levels, providing direction for laboratory and clinical research.[8] In this study, using bioinformatics methods, we screened common differentially expressed genes (DEGs) in both diseases and analyzed their functions and pathways. A gene network map was constructed, and core genes were identified.


## 2. Methods
  As all the data were obtained from online databases, written informed consent from patients had already been obtained. Moreover, our study was based on open-source data; thus, there are no relevant ethical issues.

  A workflow diagram of this study is shown in Figure 1.


### 2.1. Data collection and analysis
  Using the keywords “MI,” “IS,” and “Homo sapiens,” we searched the NCBI Gene Expression Omnibus (GEO) database (https://www.ncbi.nlm.nih.gov/geo/) and obtained 4 target datasets, namely GSE58294, GSE16561, GSE60993, and GSE61144, after screening. The gene expression files of all 4 datasets were downloaded. Among them, the GSE58294 data was from the GPL570 sequencing platform and contained 69 patients with cardioembolic stroke and 23 healthy controls; the GSE16561 dataset was derived from the GPL6883 sequencing platform and contained 39 patients with IS and 24 healthy controls; the GSE60993 dataset was derived from the GPL6884 sequencing platform and contained 17 patients with MI and 16 healthy participants; and the GSE61144 dataset was derived from the GPL6106 sequencing platform and contained 7 patients with ST-elevation MI (STEMI) and 17 healthy controls. In addition, the gene expression matrix and associated annotation files were downloaded for each array dataset. Probe IDs were converted to gene names using the corresponding annotation files, and if multiple probes were mapped to the same symbol, they were averaged. Using Perl v5.30.0 software, the 2 IS datasets, GSE58294 and GSE116561, and the 2 MI datasets, GSE60993 and GSE61144, were overlaid to screen for shared genes.


### 2.2. Screening of DEGs
  The “limma” and “pheatmap” packages in R packages were used to filter and remove genes with missing values and vacancies according to the screening conditions |logFC| > 0.58 and adj.P.Val.Filter ≤ .05. Next, the unique and shared sections of the datasets of the 2 diseases were analyzed and visualized using the “ggplot2” and “VennDiagram” packages.


### 2.3. Gene ontology (GO) and Kyoto Encyclopedia of genes and genomes (KEGG) pathway enrichment analyses
  To explore the cellular pathways affected by the identified DEGs and GO characteristics of these genes the identified DEGs, the online software DAVID (https://david.ncifcrf.gov/) was used to perform KEGG pathway enrichment and GO analyses of key genes.


### 2.4. Protein–protein interaction (PPI) network construction and analysis
  Studying the interaction network among proteins helps to identify core regulatory genes. The online software STRING (https://string-db.org/) was used to build a PPI network diagram with the medium confidence set to 0.4. Using the CytoHubba plug-in in Cytoscape (http://cytoscape.org/), the key nodes in the PPI network were determined according tofollowing the Degree algorithm, and from these key nodes, the core genes were deduced. The biological pathway of each core gene was identified using the gene function online annotation analysis tool Metascape (http://metascape.org).


### 2.5. Hub gene verification and construction of transcription factor (TF)–gene interaction and TF–microRNA (miRNA) regulatory networks
  The shared DEGs were imported into the NetworkAnalyst (https://www.networkanalyst.ca) website to obtain the relationships between miRNAs and genes according to the TarBase v8.0 database and between TFs and genes through the ENCODE and JASPAR background databases.


### 2.6. Small-molecule identification
  The Connectivity Map (CMAP) database (https://clue.io/) contains extensive information on molecular interference and gene expression. The DEGs were matched to genes involved in small-molecule interference to identify small molecules. These probes were mapped to the database to obtain relevant active small molecules, and enrichment values were calculated. Values close to −1 indicated that the small molecules could mimic the state of those in normal cells.


## 3. Results

### 3.1. Identification of DEGs
  A total of 116 and 1321 DEGs from patients with IS and MI, respectively, were identified (Fig. 2). The 75 common DEGs between the 2 diseases are shown in a Venn diagram (Fig. 3), of which 56 and 19 were upregulated and downregulated, respectively.


### 3.2. KEGG pathway and GO term enrichment analyses of DEGs
  To further explore the biological processes and pathway enrichment of the 75 shared DEGs, KEGG pathway and GO term enrichment analyses were performed, the results of which are summarized in Figure 4A–D and presented in full in Table 1.


### 3.3. Construction and analysis of the PPI network
  Further analysis of the relationships among the proteins encoded by the shared DEGs using the PPI network revealed 39 nodes and 39 connections in total, and those with a standard confidence score > 0.4 are shown in Figure 5A. A map of the top 15 hub proteins is shown in Figure 5B. The score of each protein indicates the strength of the relationship between the gene and the PPI network, with higher scores indicating stronger connectivity. The biological pathways of each core gene are shown in Figure 6A and B.


### 3.4. Hub gene verification and TF–gene and miRNA–gene regulatory networks
  In TarBase, we observed that the highest interaction rate, reaching 69 degrees, belonged to the gene ORMDL3, with which the miRNA hsa-mir-27a-3p had a significant interaction of up to 9 degrees (Fig. 7). The interaction rate between the gene CD163 and TFs was the highest, reaching 11 degrees. Furthermore, the relationship between the TF FOXC1 and the genes was 10 degrees (Fig. 8).


### 3.5. Active small molecules associated with key genes
  The top 10 small molecules that significantly corresponded to key gene expression changes are shown in Table 2. Small molecules with enrichment close to −1 are important in the 2 diseases.


## 4. Discussion
  Both IS and MI are influenced by environmental and genetic factors. Different mechanisms have been reported between the 2 diseases,[9] but there are similarities in risk factors and physiology between the 2 diseases. Herein, the GEO database was used to analyze datasets of patients with IS and MI, explore the commonalities between the 2 diseases, and 75 shared DEGs and 15 key core DEGs were identified. Three aspects of GO, specifically biological processes (BP), molecular functions (MF), and cellular components (CC), were analyzed for each DEG, demonstrating that BP involved in both disorders primarily included neutrophil degranulation, neutrophil activation involved in the immune response, and cytokine secretion. Furthermore, CCs primarily involved were specific granules, tertiary granules, and specific granule membranes. Finally, the enriched MF were mainly serine-type peptidase activity, serine hydrolase activity, and pattern recognition receptor activity. KEGG analysis revealed that DEGs were mainly implicated in Salmonella infections, Legionellosis, and inflammatory bowel disease.

  To better understand the common genes between IS and MI, PPIs were investigated. According to the Degree algorithm, the top 15 genes were S100a12, Hp, Clec4d, Cd163, Mmp9, Ormdl3, Il2rb, Orm1, Irak3, Tlr5, Lrg1, Clec4e, Clec5a, Mcemp1, and Ly96. These were subsequently referred to as key genes. Metascape functional analysis of these hub genes showed that they were mainly enriched in response to bacteria, positive regulation of cytokine production, and inflammatory responses. These results were generally consistent with the DEG analysis results.

  Atherosclerosis is an inflammatory disease characterized by the accumulation of macrophages in blood vessel walls. Approximately half of all IS cases of IS are caused by arterial-to-arterial embolism in the aorta and precranial arteries or by intracranial atherosclerotic plaques, both of which impair vascular function, and can lead to arterial occlusion and tissue ischemia.[10] The rupture of atherosclerotic plaques in coronary arteries can lead to AMI.[11] Atherosclerosis plays an important role in the pathological mechanisms underlying IS and MI occurrence and development.

  S100A12 encodes a calcium-binding protein involved in inflammation and atherosclerosis progression. Serum S100A12 can predict future cardiovascular events and may serve as a potential biomarker for coronary heart disease treatment and disease progression. Moreover, the S100 protein family is a potential target for the prevention and treatment of atherosclerosis.[12] Notably, S100A12 can be used to rapidly identify patients with STEMI more accurately than using other cardiac biomarkers, especially within the first 2 hours after symptom onset. Indeed, peak plasma S100A12 levels are also a strong predictor of the 1-year outcomes of patients after STEMI.[13]

  CD163 encodes a membrane receptor expressed by cells of the macrophage lineage. Recent studies performed on patients with atherosclerosis have shown that CD163 expression is increased at sites of inflammation, indicating the presence of intraplaque hemorrhage or asymptomatic plaques.[14] In atherosclerosis, CD163-expressing macrophages have been identified as a protective mechanism against the deleterious effects of tumor necrosis factor (TNF)-like weak inducer of apoptosis (TWEAK) on atherosclerotic plaque formation and progression.[15]

  MMP9 encodes matrix metalloproteinase-9, which is a potential candidate diagnostic biomarker in patients with AMI.[16] Moreover, higher serum MMP9 levels during the acute phase of IS are associated with an increased risk of death and severe disability. In addition, serum MMP9 may be an important prognostic factor in IS.[17]

  CLEC4D encodes a C-type lectin receptor 4D. Related studies have reported that pharmacological and genetic inhibition of protein kinase 2 (HIPK2) can improve TAC-induced cardiac function and inhibit cardiac hypertrophy and fibrosis. In vitro studies have shown that HIPK2 inhibition prevents cardiomyocyte hypertrophic growth and neonatal rat cardiac fibroblast (NRCF) proliferation and differentiation. At a mechanistic level, early growth response 3 (EGR3) and CLEC4D are novel targets of HIPK2, regulated by ERK1/2-CREB, that mediate the protective function of HIPK2 inhibition in cardiomyocytes. HIPK2 inhibition prevents pathological cardiac remodeling by reducing ERK3/4-CREB-inhibited EGR1 and CLEC2D in cardiomyocytes and inhibiting Smad3 phosphorylation in cardiac fibroblasts.[18] Neuroinflammation and immune responses are the key players in IS pathophysiology. CLEC4D and CD163 are both immune biomarkers of IS. CLEC4D strongly correlated with the proportion of neutrophils (R = 0.72), providing a basis for further research on reperfusion injury. Immuno-neuroprotective therapies offer potential targets.[19] The prediction of these target genes may provide new directions for the treatment of IS and MI.

  CLEC4E encodes bacterial C-type lectin domain family 4 member E.[20] AMI primarily occurs due to coronary atherosclerotic plaque rupture and subsequent thrombosis in STEMI. Gene-by-gene analysis of platelet gene expression led to the identification of 5 DEGs: FKBP5, S100P, SAMSN1, CLEC4E, and S100A12. Early signals of impending AMI may be detected by platelet gene expression profiling of these genes.[21]

  The functions related to each key gene were primarily neutrophil degranulation and activation involved in the immune response, further supporting the widely accepted role of the inflammatory response in these 2 diseases. Neutrophils mediate inflammation, tissue destruction, and immunopathology of the central nervous system. Neutrophils release key mediators, including matrix metalloproteinases that degrade the brain extracellular matrix (ECM), tumor necrosis factor (TNF)-α that may drive inflammation, reactive oxygen species that drive necrosis, and neutral granulocyte extracellular traps that interact with platelets to form thrombi, which in turn that may lead to IS.[22]

  miRNAs regulate gene expression by blocking mRNA translation, thereby playing important roles in numerous diseases.[23] For example, Shen et al (2023) found that miR-27a-3p attenuates ischemia-reperfusion (I/R) injury by targeting FOXO1.[24]

  Interactions between proteins and DNA are mediated by TFs. This interaction underlies transcriptional regulation.[25,26] FOXC1 transcriptionally activates ELAVL1, which may promote ferroptosis during myocardial ischemia-reperfusion (I/R) by regulating autophagy, leading to myocardial injury. Inhibition of ELAVL1-mediated autophagic ferroptosis provides a new perspective for the treatment of myocardial I/R injury.[27] Neuroinflammation is a key factor in stroke progression, and controlling overactive neuroinflammation remains a long-term challenge. MDL-811 not only improved disease behavior in mice with lipopolysaccharide-induced neuroinflammation but also promoted long-term functional recovery and significantly reduced brain damage in mice with IS. Importantly, MDL-811 also exhibits a strong anti-inflammatory effect on human monocytes isolated from patients with IS, while Foxc1, a key gene induced by MDL-811 stimulation, is required for the anti-inflammatory effect of MDL-811.[28]

  Ten small-molecule candidates with overlapping gene expression between IS and MI were identified using the CMAP database. NU-1025 is a poly-ADP ribose polymerase (PARP) inhibitor, and studies have demonstrated that NU-1025 shows neuroprotective activity and potential in the treatment of IS.[29] Severe DNA damage from vascular inflammation leads to the hyperactivation of PARP1. This leads to NAD+ and ATP depletion in endothelial cells, downregulation of atherosclerosis protective SIRT1, necrotic cell death, and ultimately atherosclerotic plaque destruction. Inhibition of PARP reduces endothelial cell adhesion to P-selectin and ICAM-1 molecules, inflammatory cells, pro-death caspase-3, and c-Jun N-terminal kinase (JNK) activation and upregulates pro-survival extracellular signal-regulated kinases and AKT. This reduces vascular cell apoptosis and necrosis and limits atherosclerosis and plaque destruction.[30] Geldanamycin (GA) is an HSP90 inhibitor that reduces the protein of mixed lineage kinase (MLK) and activates AKT, MLK3, and, subsequently, JNK, which is involved in neuronal cell death in ischemic brain injury.[31] Heat shock protein 90 (HSP90) in RIPC-isolated exosomes (RIPC-Exos) was found to be important in mediating cardioprotection during I/R, while treatment with the HSP90 inhibitor GA significantly reversed the cardioprotection of RIPC-Exos, as well as activated complement components, JNK signaling, and inflammation.[32] The small molecules used in these studies may serve as a valuable basis for developing therapeutic drugs for IS and MI.

  However, it is worth noting that this study comes from the analysis of public database data and requires further in-depth research in the future. This study discovered a common core gene in the occurrence of IS and MI, which may provide a theoretical basis for the diagnosis and treatment of these 2 diseases.


## 5. Conclusion
  In summary, 15 key shared core DEGs in patients with IS and MI were identified in this study using bioinformatics. Analysis of the biological functions and pathways of key core DEGs and examination of associated miRNAs, TFs, and active small molecules may provide a basis for the future prevention, diagnosis, and treatment of IS and MI.


## Author contributions
  Data curation: Min Wang.

  Resources: Guangming Wang.

  Software: Min Wang, Yuan Gao, Huaqiu Chen.

  Validation: Yuan Gao, Huaqiu Chen.

  Writing – original draft: Min Wang, Yuan Gao.

  Writing – review & editing: Jianjie Cheng, Guangming Wang.