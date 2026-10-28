# Exploration of the molecular linkage between endometriosis and Crohn disease by bioinformatics methods


## Background:
  Endometriosis (EMT) is a common disease in reproductive-age woman and Crohn disease (CD) is a chronic inflammatory disorder in gastrointestinal tract. Previous studies reported that patients with EMT had an increased risk of CD. However, the linkage between EMT and CD remains unclear. In this study, we aimed to investigate the potential molecular mechanism of EMT and CD.


## Methods:
  The microarray data of EMT and CD were downloaded from Gene Expression Omnibus. Common genes of EMT and CD were obtained to perform the Gene Ontology and Kyoto Encyclopedia of Gene Genomes enrichments. The protein-protein interaction network was constructed by Cytoscape software and the hub genes were identified by CytoHubba plug-in. Finally we predicted the transcription factors (TFs) of hub genes and constructed a TFs-hub genes regulation network.


## Results:
  A total of 50 common genes were identified. Kyoto Encyclopedia of Gene Genomes enrichment showed that the common genes mainly enriched in MAPK pathway, VEGF pathway, Wnt pathway, TGF-beta pathway, and Ras pathway. Fifteen hub genes were collected from the protein-protein interaction network, including FMOD, FRZB, CPE, SST, ISG15, EFEMP1, KDR, ADRA2A, FZD7, AQP1, IGFBP5, NAMPT, PLUA, FGF9, and FHL2. Among them, FGF9, FZD7, IGFBP5, KDR, and NAMPT were both validated in the other 2 datasets. Finally TFs-hub genes regulation network were constructed.


## Conclusion:
  Our findings firstly revealed the linkage between EMT and CD, including inflammation, angiogenesis, immune regulation, and cell behaviors, which may lead to the risk of CD in EMT. FGF9, FZD7, IGFBP5, KDR, and NAMPT may closely relate to the linkage.


## 1. Introduction
  Crohn disease (CD), a type of inflammatory bowel disease (IBD), is defined as a chronic inflammatory disease of gastrointestinal tract. The prevalence of CD has been increasing since the 20th century.[1] A systematic review reported that the prevalence rate in Europe ranged from 137.17 to 322 per 100,000, while in Asia, it varied from 1.2 to 53.1 per 100,000.[2] The cause and pathophysiology of CD are complex. Now it is believed to be the disturbed innate and adaptive immune response caused by multiple elements, including genetic susceptibility, environmental factors, and intestinal microflora.[3] Clinical presentations depend on the disease location and severity of inflammation. Most of CD patients experience intermittent abdominal pain, chronic diarrhea, and weight loss, profoundly impacting their quality of life.[4]

  Endometriosis (EMT) is a disease that endometrium-like tissue appears outside the uterus.[5] EMT affects 10% of reproductive-age woman, with approximately 200 million women worldwide potentially suffering from this disease.[6] EMT patients typically present chronic pain continually or intermittently until the menopause, dysmenorrhea, infertility, and abnormal menstruation. However, the etiology of EMT is largely unknown. Retrograde menstruation is the widely accepted theory, but increasing studies believe EMT is related with abnormal autoimmunity.[7] Immune escape and abnormal expression of immune cells have been identified.[8] Several studies have revealed that EMT is not solely linked to malignant tumors such as ovarian cancer, non-Hodgkin lymphoma, and breast cancer, but also some immune diseases like systemic lupus, rheumatoid arthritis, and IBD.[9,10] A nationwide cohort in Danish reported that patients with EMT had an elevated risk of developing IBD. The standardized incidence ratio of ulcerative colitis was 1.5 and that of CD was 1.6.[11] Although EMT patients have been observed to be more susceptible to CD, our understanding of the mechanism is very limited.

  With the quick development of gene microarray technology, this method is widely applied in the genomics research in various diseases, which enables researchers to comprehend gene expression and make a further analysis. For instance, Antonio et al[12] obtained intestinal tissue from IBD patients and utilized a high-throughput approach to identify a novel predictor classifier. Stefania et al[13] discovered 2 important genes (BMP4 and GREM1) that were specifically deregulated in the ectopic endometrium by genome wide profiling analysis. As a consequence, we can investigate the relationship between diseases by integrating and analyzing the biological data.

  Therefore, we used original microarray datasets from Gene Expression Omnibus (GEO) in order to reveal the molecular mechanism of CD and EMT. Common genes of CD and EMT were obtained, and analyzed by enrichment analysis and PPI network. Moreover, Transcription factors (TFs) of hub genes were predicted. The regulatory relationship between hub genes and TFs were displayed.


## 2. Materials and methods

### 2.1. Collection of CD and EMT related genes
  Key words “inflammatory bowel disease,” “Crohn’s disease,” “CD,” “endometriosis,” and “EMT” were put into GEO database (https://www.ncbi.nlm.nih.gov/geo/) to search CD and EMT gene expression profiles. Selected profiles should meet the following criteria. Firstly, the gene expression profiling should include 2 groups. One is case group and the other is control group. Secondly, each group should contain at least 5 samples. Thirdly, the sample for sequencing should be intestinal tissue or endometriosis tissue. According to the criteria, 2 datasets of CD (GSE36807 and GSE59071) and 2 datasets of EMT (GSE25628 and GSE7305) were collected.


### 2.2. Differential expression genes
  GSE36807 and GSE25628 were used for differential expression genes (DEGs) analysis by R soft. Raw data were read and preprocessed by R soft. Then “limma” package was performed for the data analysis. GSE36807 contained 13 CD and 7 control samples. P value < 0.05 and |log2 FC (fold change)| > 0.58 were set as the cutoff for DEGs.[14] GSE25628 contained 16 EMT and 6 control samples. P value < 0.05 and |log2 FC (fold change)| > 1 were set as the cutoff for DEGs.[15] Subsequently, we visualized the DEGs by a heatmap and a volcano map, respectively. Finally we overlapped the DEGs of CD and EMT in order to obtain common genes. A Venn diagram was constructed by R package “VennDiagram” to visualize the common genes.


### 2.3. GO and KEGG enrichment analysis of common genes
  Gene Ontology (GO) function enrichment consisted of biological process (BP), molecular function (MF), and cellular component (CC). Kyoto Encyclopedia of Gene Genomes (KEGG) was applied to explore metabolic pathways. GO and KEGG enrichment analysis were performed by R soft. R packages included “org.Hs.eg.db,” “clusterProfiler,” “enrichplot,” and “ggplot2.” P value < 0.05 was recognized as significant enrichment.[16] The first 10 enrichment results were displayed by a bubble diagram or a bar chart.


### 2.4. Construction of the protein-protein interaction network
  In order to explore the relationship between common genes, we searched these genes in the online website STRING (https://cn.string-db.org). All the common genes were put into STRING and we got the protein-protein interaction (PPI) network. The protein interaction data was analyzed by cytoscape_3.9.1 software. According to plug-in “Cytohubba,” we figured out hub genes.


### 2.5. GO and KEGG enrichment of hub genes
  GO function and KEGG pathway enrichment were analyzed by R soft. P value < 0.05 was considered as significant enrichment.[16] Subsequently we displayed the enrichment results by a bubble diagram or a bar chart.


### 2.6. Validation of hub genes expression
  To enhance accuracy, the hub genes obtained from the PPI network were validated with other datasets. The expression of these hub genes was validated in GSE59071 for CD and GSE7305 for EMT. GSE59071 contained 8 CD and 11 control samples. GSE7305 contained 10 EMT and 10 control samples. The expression of hub genes was visualized by a violin chart.


### 2.7. Prediction of transcription factors
  Transcriptional Regulatory Relationships Unraveled by Sentence-based Text mining (TRRUST) is a database that focuses on human and mouse transcriptional regulatory networks. We upload the hub genes to TRRUST and enrich the TFs. Subsequently, cytoscape_3.9.1 software was applied to construct the TFs-hub genes network. The flow chart is shown in Figure 1.


### 2.8. Ethical statement
  This study does not involve in any patient’s personal data, cell, or animal experiments, and does not require any ethical approval.


## 3. Results

### 3.1. DEGs of CD and EMT
  According to the inclusion criteria, GSE36807 dataset and GSE25628 dataset were selected for the DEGs analysis. Based on the cutoff criteria, there were 434 DEGs of CD, including 202 up-regulated genes and 232 down-regulated genes. There were 1782 DEGs of EMT, including 654 up-regulated genes and 1128 down-regulated genes. A volcano plot and a heatmap were constructed by R soft to visualize the distribution of DEGs (Fig. 2). Subsequently, we obtained 50 common genes by matching the DEGs of CD and EMT (Fig. 3, Supplement S1, http://links.lww.com/MD/M497).


### 3.2. GO and KEGG enrichment analysis of common genes
  We utilized R soft to perform the GO function and KEGG enrichment to gain a deeper understanding of the common genes. The top 10 enriched GO terms are displayed in Figure 4. In terms of BP, the results chiefly enriched in wound healing, peptide hormone processing, signaling receptor ligand precursor processing, macrophage chemotaxis, and response to antibiotic. In terms of CC, these genes mainly associated with collagen-containing extracellular matrix, high-density lipoprotein particle, plasma lipoprotein particle, lipoprotein particle, and protein-lipid complex. In terms of MF, these genes principally related with protein-cysteine S-palmitoyltransferase activity, protein-cysteine, S-acyltransferase activity, Wnt-protein binding, and frizzled binding. KEGG analysis enriched 5 pathways, including MAPK signaling pathway, VEGF signaling pathway, Wnt signaling pathway, TGF-beta signaling pathway, and Ras signaling pathway (Fig. 5).


### 3.3. Construction of PPI network and analysis
  All the common genes were put into the STRING database and we got a PPI network, including 49 nodes and 109 edges (Fig. 6). Subsequently, the PPI network was analyzed by CytoHubba plug-in to figure out the hub genes. Fifteen genes were collected, including IGFBP5, ISG15, KDR, FMOD, FRZB, SST, ADRA2A, PLAU, AQP1, EFEMP1, FHL2, FGF9, FZD7, NAMPT, and CPE (Fig. 7).

  GO analysis and KEGG enrichment were performed for the hub genes. In terms of the BP, the results mainly related with sensory organ morphogenesis, wound healing, postembryonic animal organ morphogenesis, regulation of smooth muscle cell migration and smooth muscle cell migration. In terms of CC, the results were associated with dopaminergic synapse, peptidase inhibitor complex, serine-type endopeptidase complex, serine-type peptidase complex, and protein complex involved in cell-matrix adhesion. In terms of MF, these genes enriched in Wnt-protein binding, receptor ligand activity, signaling receptor activator activity, transmembrane receptor protein tyrosine kinase activity, and transmembrane receptor protein kinase activity (Fig. 8). From the results of KEGG analysis, hub genes chiefly related with Wnt signaling pathway and Rap1 signaling pathway (Fig. 9A). Furthermore, we displayed the relationship between hub genes and pathways (Fig. 9B). According to the results, KDR, FGF9, FZD7, and FRZB closely related with these pathways.


### 3.4. Validation of hub genes expression
  Validation of hub genes was performed in GSE59071 for CD and GSE7305 for EMT. As for CD, the results showed 4 up-regulated (IGFBP5, KDR, NAMPT, and PLUA) and 3 down-regulated (FGF9, FZD7, and SST) genes (Fig. 10). As for EMT, The results showed 11 up-regulated (AQP1, CPE, EFEMP1, FHL2, FMOD, FRZB, FZD7, IGFBP5, ISG15, KDR, and NAMPT) and 1 down-regulated (FGF9) genes (Fig. 11). IGFBP5, FGF9, FZD7, KDR, and NAMPT exhibited differential expression in GSE59071 and GSE7305. Moreover, the expression of these 5 genes closely aligned with that of GSE36807 and GSE25628. We hypothesized that these genes may play an important role in the linkage between EMT and CD.


### 3.5. Prediction of TFs and analysis
  The TFs of hub genes were predicted by online website TRRUST version 2. All the hub genes were uploaded to the website and 4 TFs were obtained, including serum response factor (SRF), jun proto-oncogene (JUN), v-rel reticuloendotheliosis viral oncogene homolog A (RELA), and nuclear factor of kappa light polypeptide gene enhancer in B-cells 1 (NFKB1). According to the regulation of TFs and hub genes, TFs-hub genes network was constructed (Fig. 12). We found that every TF regulated 2 genes.


## 4. Discussion
  EMT is a common disease in childbearing age women. CD has a peak onset between 20 and 40 years old, followed by a small peak from 50 to 60 years old.[17] The epidemiology indicates that these 2 diseases share a similar onset age. There are more and more studies showing the correlation between EMT and CD. Previously a few cases reported the co-existence of EMT and CD.[18,19] Nowadays a cohort study has found the increased incidence of CD in patients with EMT, and a meta-analysis has further corroborated this observation.[11,20] However, the mechanism of the linkage between EMT and CD remains largely unknown. As a consequence, it is crucial to figure out the intricate relationship between EMT and CD in order to achieve early detection and diagnosis.

  Our study is the first to explore the relationship between CD and EMT at genetic level. In this study, we downloaded 2 dependent gene expression data of CD and EMT from GEO. Fifty common genes were obtained from matching DEGs of CD and EMT. The KEGG pathways analysis showed that the common genes mainly enriched in the MAPK signaling pathway, Wnt signaling pathway, VEGF signaling pathway, TGF-beta signaling pathway, and Ras signaling pathway. These pathways were chiefly related to inflammation, cell behavior, angiogenesis, and immunoregulation.

  The MAPK’s family members consisted of extracellular signal-regulated kinase (ERK), c-Jun N-terminal Kinase (JNK), and p38 mitogen-activated protein kinase (p38MAPK). MAPK signaling pathway involved in a wide variety of cellular activities, including inflammation, cell proliferation, differentiation, migration, senescence, and apoptosis.[21,22] EMT was regarded as a chronic inflammatory condition. A study showed that estrogen-induced reactive oxygen species and then activated MAPK signaling pathways, which played a crucial role in the inflammation.[23] Moreover, excessive production of estrogen in EMT profoundly disturbed the MAPK pathway, resulting in the stimulation of ectopic endometriotic cell proliferation.[23] Activation of MAPK signaling pathway was also confirmed in CD patients, which triggered intestinal inflammation by up-regulating pro-inflammation cytokines.[24]

  Wnt signaling pathway consisted of ligand protein Wnt and membrane protein receptors, which involved in cell specification, stem cell self-renewal and tissue patterning.[25] Studies showed that high expression of this pathway was observed in the tissue of CD or EMT. Abnormal cell behaviors like cell migration, invasion, and matrix metalloproteinase expression induced by Wnt signaling pathway may be the prerequisites to develop and maintained EMT.[26] In the intestine of IBD, Wnt pathway was found to be the regulator of inflammation and was considered as a feature of chronic IBD.[27] Moreover, continuous activation of Wnt pathway increased collagen-I expression in myofibroblasts and involved in intestinal fibrosis.[28]

  Ras was an important regulator of cell growth.[29] However, over activation of Ras signaling pathway increased cell proliferation and migration in EMT.[30] Similarly, a study found that Ras highly expressed in CD and contributed to intestinal fibrosis. Activated Ras pathway promoted extracellular matrix and myofibroblast formation in intestine.[31]

  VEGF signaling pathway played a leading role in angiogenesis, contributing to the progression of diseases and inflammation.[32,33] Angiogenesis promoted ectopic endometrium cell proliferation, migration, and invasion.[34] Among many pro-angiogenic factors, VEGF played an important role in the pathogenesis. Studies found that high expression of VEGF promoted the development of EMT.[35,36] VEGF was also highly expressed in IBD.[37] Angiogenesis significantly contributed to the recruitment of pro-inflammatory cells and led to the disruption of epithelial integrity, ultimately impacting the progression and severity of IBD.[38]

  TGF-beta was regarded as one of the most important cytokines in tissue. The TGF-beta signaling pathway played a critical role in cell development and homeostasis.[39] However, higher expression of TGF-beta was found in endometriotic tissue. Abnormal expression of TGF-beta enhanced the migration, adhesion to mesothelium and invasive ability of ectopic endometrial cells.[40,41] Moreover, TGF-beta regulated multiple immune activities to accelerate the progression of EMT.[42–44] Overexpression of TGF-beta1 protected ectopic tissue survival from immune clearance via reducing natural killer cell and macrophage numbers.[45] Similarly, dysregulated TGF-beta signaling in IBD led to systemic autoimmunity, abnormal intestinal microbial immune regulation, and barrier function impairment.[44]

  After conducting aforementioned analysis, we discovered several shared signaling pathways that involved in the progression of EMT and CD, thereby furnishing a pathophysiologic groundwork for the risk of CD in patients with EMT.

  Subsequently, we obtained 15 hub genes in PPI network by cytoHubba plug-in. These hub genes mainly enriched in Wnt signaling pathway and Rap1 signaling pathway. Rap1 belonged to Ras family. These results were consistent with the KEGG enrichment of common genes. Furthermore, these hub genes were validated in other datasets and 5 genes exhibited differential expression in EMT and CD. These genes were FGF9, FZD7, IGFBP5, KDR, and NAMPT, which may closely relate to the common pathology of EMT and CD.

  FGF9 belonged to the human fibroblast grow factor (FGF) and was a kind of secreted protein regulating embryonic development, cell proliferation, cell differentiation, and cell migration.[46,47] FGF9 was required for many organs development, like lung, heat, and digestive system.[46] However, FGF9 mutation was reported to be associated with colorectal, endometrial, and ovarian cancer, which indicated the importance of this gene in the intestinal and endometrial disease development.[48] High expression of FGF9, especially in the early stage, promoted endometriotic stromal cell proliferation and maintain endometriosis.[49,50] As for CD, there had been no research exploring the relationship between FGF9 and CD. However, a study found FGF9 regulated the small intestinal mesenchymal fibroblast proliferation and differentiation during the late stage embryogenesis.[51] We suspected that FGF9 may promote intestinal fibrosis in CD by accelerating mesenchymal fibroblast proliferation. Therefore, we believed that abnormal FGF9 expression may promote tissue proliferation to maintain EMT or CD.

  FZD7 was a receptor of Wnt protein and was one of the Frizzled family members.[52] A study found that up-regulation of FZD7 could promote cell proliferation, migration, and invasion in ectopic human endometrium by activating Wnt signaling pathway.[53] Similarly, our study showed that FZD7 was increased in EMT tissue. As for CD, FZD7 was decreased in our research. A study found that loss of FZD7 prevented intestinal stem cells from regenerating.[54] In addition, down-regulation of FZD7 in intestine interrupted differentiation procession of intestinal stem cells and thus the homeostasis of the intestinal epithelium.[55] Although no study has explored the role of FZD7 in CD, we hypothesized that it caused the disease by affecting the biological processes of intestinal stem cell.

  IGFBP5 belonged to the insulin-like growth factor binding proteins (IGFBPs) and was a kind of secreted protein released by a variety of different cells.[56] IGFBPs were associated with autoimmune diseases via its immunoregulation.[57] Peripheral blood mononuclear cells, including lymphocytes and monocytes, formed the major innate and adaptive immune systems. In a vivo study, IGFBP5 could recruit mononuclear cell infiltration and accelerate peripheral blood mononuclear cells migration.[58] Moreover, IGFBP5 induced the preferential migration of CD4 + T cells, which involved in the early phase of inflammation and fibrosis in a disease development.[59] Studies found that IGFBP5 was highly expressed in inflamed and fibrotic intestine tissue in CD patients. IGFBP5 stimulated smooth muscle, fibroblasts, and myofibroblasts to increase collagen synthesis and cell proliferation.[60] In addition, IGFBP5 also regulated smooth muscle proliferation via alpha-submit Gi 3.[61] Beside, IGFBP5 was found to dominate in the proliferation phase of endometrium.[62] Nowadays, increasing evidence proofed that EMT was an autoimmune disease.[63] We suspected IGFBP5 may affect the cell cycle of immune cells to trigger EMT.

  KDR, a receptor tyrosine kinase gene, encoded a receptor vascular endothelial cell growth factor (VEGF).[64] VEGF played an important role in angiogenesis, vascular development, vascular permeability, and embryonic hematopoiesis.[65] As mentioned before, angiogenesis contributed to the development of EMT and CD.

  NAMPT was recognized as a regulator of the intracellular nicotinamide adenine dinucleotide pool, in which NAMPT catalyzed rate-limiting step in the biosynthesis of nicotinamide adenine dinucleotide from nicotinamide (NAM).[66] NAMPT was elevated in inflammatory disorders and represented damage-associated molecular patterns-like actions.[67] A study showed that elevation of NAMPT reflected the activation and severity of CD.[68] In contrast, NAMPT exerted different effect on endometrial cells. NAMPT regulated by estrogen and progesterone in uterus, elevated cellular proliferation by increasing antioxidant enzymes.[69] This suggested that increased NAMPT may prompt ectopic endometrial cells survival.

  TFs are the DNA-proteins that recognize specific DNA sequence and regulate the transcription of chromatin. They form a complex system that governs the genome expression.[70] As a consequence, we predicted the TFs of hub genes, including JUN, NFKB1, RELA, and SRF, and established the TFs-genes network. Pro-inflammatory TNF was a main contributor to CD and was regulated by JUN. Increased expression of JUN was found in CD patients and stimulated macrophages to product TNF.[71] In addition, JUN interacted with the functional AP-1 transcription factor binding site to promote Metastasis-Associated in Colon Cancer 1 expression, which induced cell migration and metastasis in colorectal cancer.[72] A study reported that transcription factor JUN contributed to aromatase P450 (P450arom) expression. P450arom was a key enzyme for biosynthesis of estrogen which was an important element for the development of EMT.[73] NFKB1 was a vital transcription regulator of immune response and its polymorphism was associated with the risk of CD.[74] Additionally, NFKB1 polymorphism was also found to heighten susceptibility to EMT.[75] RELA, also known as nuclear factor KF-kappa-B p65 subunit, was strongly activated in IBD and played a central role in the persistent inflammation.[76] Similarly, RELA was increased in EMT and mediated cell proliferation, invasion and inflammation of endometrial stromal cells.[77] Transcription factor SRF was related with intestinal fibrosis. Increased SRF stimulated myofibroblasts to synthesize collagen and fibronectin, promoting intestinal fibrosis in CD.[78]

  However, there are also some limitations in our study. On one hand, only 4 TFs were predicted via a public database. On the other hand, our study revealed the potential mechanism between EMT and CD only by nonexperiment methods. Therefore, our further study will utilize RT-qPCR to analyze the mRNA expression of hub genes in EMT and CD samples. Furthermore, we will investigate whether alterations in these hub genes would impact the enriched signaling pathways, ultimately influencing the development of these diseases.


## 5. Conclusion
  In conclusion, our study uncovered a deep insight into the molecular mechanism between EMT and CD via bioinformatics analysis. Integrating multiple databases, we revealed the shared pathogenesis of EMT and CD, including inflammation, angiogenesis, immune regulation, cell behaviors, which may lead to the risk of CD in EMT. These genes (FGF9, FZD7, IGFBP5, KDR, and NAMPT) may closely relate to the common pathology of EMT and CD.


## Author contributions
  Conceptualization: Peizhu Su, Zhaotao Li, Liu Liu.

  Data curation: Yilin Wang.

  Formal analysis: Yilin Wang.

  Funding acquisition: Zhaotao Li.

  Methodology: Weijie Zhou, Yilin Wang.

  Software: Weijie Zhou.

  Supervision: Peizhu Su, Liu Liu.

  Validation: Weijie Zhou.

  Visualization: Weijie Zhou.

  Writing – original draft: Weijie Zhou.

  Writing – review & editing: Weijie Zhou, Peizhu Su, Zhaotao Li, Liu Liu.


## Supplementary Material