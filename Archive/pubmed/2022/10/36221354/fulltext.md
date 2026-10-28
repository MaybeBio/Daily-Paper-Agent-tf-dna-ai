# Exploration of hub genes involved in PCOS using biological informatics methods


## Methods:
  Gene expression data of PCOS and non-PCOS subjects were collected from gene expression omnibus (GEO) database. GEO2R were used to calculating P value and logFC. The screening threshold of DEGs was P < .05 and | FC | ≥ 1.2. GO annotation and Kyoto encyclopedia of genes and genomes (KEGG) signaling pathway enrichment analysis was performed by using DAVID (2021 Update). The protein-protein interaction (PPI) network of DEGs was constructed by using the STRING database, and the hub genes were recognized through Hubba plugin of Cytoscape software.


## Results:
  PCOS and non-PCOS subjects shared a total of 174 DGEs, including 14 upregulated and 160 downregulated genes. The GO biological processes enriched by DEGs mainly involved actin cytoskeleton organization, positive regulation of NF-κB signaling pathway, and positive regulation of canonical Wnt signaling pathway. The DEGs were significantly enriched in cytoplasm, nucleus and cytosol. Their molecular functions mainly focused on protein binding, calmodulin binding and glycerol-3-phosphate dehydrogenase activity. The PI3K/Akt signaling pathway and glycosaminoglycan biosynthesis were highlighted as critical pathways enriched by DEGs. 10 hub genes were screened from the constructed PPI network, of which EGF, FN1 and TLR4 were mainly enriched in the PI3K/Akt signaling pathway.


## Conclusion:
  In this study, a total of 174 DEGs and 10 hub genes were identified as new candidate targets for insulin resistance (IR) in PCOS individuals, which may provide a new direction for developing novel treatment strategies for PCOS.


## 1. Introduction
  Polycystic ovary syndrome (PCOS), one of the most common endocrine disorders, is affecting up to 5% to 10% of women worldwide.[1] PCOS is an enigmatic endocrine disorder caused by hormonal imbalances and usually presents reproductive, metabolic and psychological syndromes.[2] According to the Rotterdam ESHRE/ASRM Consensus, the diagnostic criteria of PCOS are hyperandrogenism, ovulation disorder, polycystic ovaries (detected by ultrasonography) and the exclusion of other endocrinopathies.[3] The current understanding of the multisystemic features of this syndrome is increasing.[4,5] PCOS not only increases the risk of pregnancy-related disorders such as miscarriage, gestational diabetes, preterm birth and preeclampsia,[6–8] but also causes a range of other health problems, including chronic inflammation, insulin resistance (IR), glucose intolerance, metabolic syndrome and hypertension.[9] Patients with PCOS often exhibit type 2 diabetes mellitus (T2DM), obesity and other metabolic disorders.[10] PCOS is no longer simply considered an ovarian disease.[11] Skeletal muscle IR has been reported in >60% of patients with PCOS and 10% of women with PCOS may develop T2DM by the age of 40 years.[12] However, the molecule mechanism of IR in PCOS remains unclear and is worthy of further study. In this study, microarray data of PCOS and non-PCOS subjects were analyzed by using bioinformatics methods, which helped to explore critical differentially expressed genes (DEGs) underlying the pathogenesis of IR in PCOS.

  We present the following article in accordance with the MDAR reporting checklist.


## 2. Materials and methods

### 2.1. Sources of microarray data
  Microarray data of PCOS and non-PCOS subjects were obtained from the gene expression omnibus (GEO, https://www.ncbi.nlm.nih.gov/geo/) database by setting keywords as: “Syndrome, Polycystic Ovary” OR “Stein-Leventhal Syndrome” OR “Stein Leventhal Syndrome” OR “Syndrome, Stein-Leventhal” OR “Sclerocystic Ovarian Degeneration” OR “Ovarian Degeneration, Sclerocystic” OR “Sclerocystic Ovary Syndrome” OR “polycystic ovarian syndrome” OR “Ovarian Syndrome, Polycystic” OR “Polycystic Ovary Syndrome 1” OR “Sclerocystic Ovaries” OR “Ovary, Sclerocystic” OR “Sclerocystic Ovary” OR “PCOS” OR “polycystic ovarian syndrome”. GSE6798 (including 13 muscle samples from healthy control subjects and 16 muscle samples from PCOS patients) and GSE8157 (including 13 muscle samples from healthy control subjects and 10 muscle samples from PCOS patients) were downloaded for further analysis. Both datasets were based on GPL570 [HG-U133_PLus_2] Affymetrix Human Genome U133 Plus 2.0 Array chip. In addition, the PCOS patients meet the elevated free testosterone levels (>0.035 nmol/L) and hyperinsulinemia (>85 pmol/L); and the CON subjects meet regular menses, normal glucose tolerance, and no family history of diabetes. The study was conducted in accordance with the Declaration of Helsinki (as revised in 2013).


### 2.2. Data processing and DEGs screening
  GEO2R was used to calculate the logFC (log2foldchange) and P value of each gene. DEGs were identified according to the cutoff of P < .05 and |FC| ≥1.2 (|logFC|≥0.3). The DEGs with P < .05 and FC ≥ 1.2 (logFC ≥ 0.3) were considered to be up-regulated genes, while the DEGs with P < .05 and FC ≤ 1.2 (logFC ≤ 0.3) were considered to be down-regulated genes.

  Common upregulated and downregulated genes between the two datasets were identified and defined as Co-differentially expressed genes (Co-DEGs). The Co-DEGs in the two datasets were displayed by Venn, and the volcano plots and heatmaps were drawn by using R-related visualization capabilities.


### 2.3. Functional enrichment analysis of DEGs
  Database for annotation, visualization, and integrated discovery (DAVID) (2021 Update) was used for gene ontology (GO) annotation and Kyoto encyclopedia of genes and genomes (KEGG) pathway enrichment analysis. GO annotation is composed of biological processes (BP), cellular components (CC) and molecular functions (MF), and it is a good tool which can help to predict the main protein functions of DEGs. KEGG signaling pathway enrichment analysis is capable to classify all kinds of DEGs to specific pathways with system path. The DEGs were uploaded to DAVID (2021 Update) for GO annotation and KEGG signaling pathway analysis, then the top 10 GO annotation results were selected for bubble chart plotting.


### 2.4. Construction of protein-protein interaction (PPI) network between DEGs and HUB gene identification
  The PPI network of DEGs was constructed with the criterion of “confidence >0.7” based on the STRING (Search Tool for the Retrieval of Interacting Genes/Proteins, https://string-db.org/) database. The algorithm of the Hubba plugin of Cytoscape v3.9.1 was used for the top 10 hub genes analysis in the constructed PPI network.


## 3. Results

### 3.1. Differentially expressed genes (DEGs)
  GSE6798 contained 794 differentially expressed genes, including 433 down-regulated genes and 361 up-regulated genes. GSE8157 contained 3380 differentially expressed genes, including 304 down-regulated genes and 3076 up-regulated genes. GSE6798 and GSE8157 shared 174 Co-DEGs, including 14 up-regulated genes and 160 down-regulated genes (Table 1, Fig. 1). Volcano plots and heatmaps of DEGs were shown in Figure 2.


### 3.2. Functional analysis of DEGs
  GO annotation and KEGG signaling pathway enrichment analysis were performed on the screened DEGs using DAVID (2021 Update) online tool. The GO annotation includes BP, CC, and MF, and the corresponding bubble chart was shown in Figure 3. The Top 10 BP enriched by DEGs mainly included actin cytoskeleton organization, sensory perception of sound, positive regulation of I-kappaB kinase/NF-kappaB signaling, negative regulation of epithelial cell proliferation, positive regulation of neuron differentiation, positive regulation of canonical Wnt signaling pathway, small GTPase mediated signal transduction, neuron projection development, peptidyl-tyrosine phosphorylation and positive regulation of mitotic cell cycle. CC results showed that these genes were mainly involved in cytoplasm, nucleus, cytosol, nucleoplasm, perinuclear region of cytoplasm, centrosome, neuron projection, growth cone, sarcolemma and Z disc. Their MF mainly focus on protein binding, actin binding, calmodulin binding, protein C-terminus binding, guanyl-nucleotide exchange factor activity, transcription coactivator activity, GDP binding, translation elongation factor activity, ribonucleoprotein complex binding and protein phosphatase regulator activity (Table 2).

  In total, 7 KEGG signaling pathways were enriched by DEGs, including PI3K-Akt signaling pathway, Focal adhesion, Gap junction, Propanoate metabolism, Glioma, Glycosaminoglycan biosynthesis and beta-Alanine metabolism. Corresponding detailed data were shown in Figure 3 D and Table 3. Interestingly, PI3K/Akt pathway is commonly correlated with insulin resistance, a major pathogenic factor for IR (Fig. 4).


### 3.3. Core network of PCOS
  Based on the DEGs between PCOS and non-PCOS subjects, the PPI network of PCOS was constructed using the STRING database, which was displayed in Figure 5A. The constructed network of PCOS is comprised of 148 nodes and 215 interaction edges. The degree of connectivity of each gene was calculated using the Hubba plugin of Cytoscape V3.9.1. Accordingly, Top10 genes with the highest degree were obtained, which included EGF, PRKCA, FN1, TLR4, IFIH1, GAPDHS, GRM1, ATP2B2, NEFL, LMNB1. To further construct the core network of PCOS, these hub genes and their neighbors were extracted and reconnected. Finally, we obtained a core network of PCOS comprised of 57 nodes and 103 edges (Fig. 5B).


## 4. Discussion
  PCOS is defined as a highly complicated endocrine disease in women, whereas the etiology and physiopathology have not been elucidated sufficiently.[13,14] Currently, IR in PCOS patients is a hot topic in the field of endocrinology and IR appears to be the fundamental key factor within the pathophysiology of PCOS.[15] Numerous studies have confirmed that high fasting glucose and increased serum insulin are commonly found in PCOS patients.[16,17] Impaired insulin responsiveness has been observed in skeletal muscle and myotubes of PCOS women.[18] The skeletal muscle accounts for the largest portion of insulin-mediated whole-body glucose disposal,[19] and thus, skeletal muscle IR is crucial for whole-body IR and PCOS. However, the research on the molecular level of IR in PCOS is lacking. In the present study, bioinformatics methods were used for analyzing the gene expression microarray data extracted from PCOS and non- PCOS skeletal muscle tissue. Ultimately, we detected a total of 174 co-DEGs by analyzing the gene expression microarray data from GSE6798 and GSE8157 for further study.

  The GO analysis results revealed that the genes with significant differences in expression were mainly involved in positive regulation of NF-κB signaling pathway, positive regulation of canonical Wnt signaling pathway and protein binding. It has been pointed out that the activated NF-κB signaling pathway might be one of the important factors in the pathogenesis of IR in PCOS.[20,21] Conversely, IR can also disrupt ovarian and uterine glucocorticoid receptor activation by regulating the NF-κB signaling pathway and then lead to PCOS.[22] Zhao, Y et al demonstrated that the expression of WNT5a in PCOS patients was significantly elevated, and the up-regulated expression of WNT5a in PCOS increases inflammation and oxidative stress predominantly via the PI3K/Akt/NF-κB signaling pathway.[23] In addition, previous studies have shown that the activation of WNT2/β-Catenin signaling pathway, was tightly associated with insulin resistance and estrogen deficiency, two hallmarks of PCOS.[24] The Wnt signaling pathway is believed to be a significant contributor to the regulation of ovarian steroidogenesis, which could be one of the pathways modulated by gonadotropin signaling,[25] and the cyclical changes of the endometrium are controlled by estrogen and progesterone via modulating the Wnt/β-catenin signaling pathway.[26] Cytokine synthesis and increased endometrial inflammation in PCOS patients are coupled to the NFκB signaling pathway.[27] The Wnt signal pathway might be involved in the apoptosis of granulosa cells and the progression of PCOS.[28,29]

  Our KEGG enrichment analysis results suggested that many of EDGs were associated with the PI3K/Akt signaling pathway and glycosaminoglycan (GAG) biosynthesis, what is worth mentioning is that the PI3K/Akt signaling pathway was shown as the most enriched pathway. The PI3K/Akt signaling pathway is necessary for insulin stimulation of glucose transport,[30,31] the impaired PI3K/Akt signaling pathway has been implicated in the development of IR.[32] In turn, IR would exacerbate the PI3K/Akt signaling pathway, forming a vicious cycle.[33] Thus, the PI3K/Akt signaling pathway may act as a molecular link between PCOS and IR.

  The PPI network of the hub genes further revealed that EGF, FN1, and TLR4 all participate in the PI3K/Akt signaling pathway, and they were shown to be significantly decreased in the skeletal muscle of PCOS patients. This is consistent with previous animal studies. Evidence has shown that mRNA expression of EGF was reduced in PCOS rats.[34,35] The decrease of EGF and consequent inhibition of its downstream PI3K/Akt signaling pathway might be a feasible mechanism for IR induced by PCOS. The hub gene fibronectin (FN1), an integral component of mammalian extracellular matrices (ECM), is an essential glycoprotein that has numerous biological functions.[36] FN1 not only regulates adhesion, motility, growth and development[37] but also is related to metabolic syndrome (MetS) and IR.[38,39] In line with previous studies, the downregulation of FN1 seems to be related to PCOS[40] and FN1 may regulate IR by affecting the PI3K/Akt signaling pathway.[41] TLR4 is also a considerable hub gene, the downregulation of this gene can reduce the sensitivity of the insulin pathway by inhibiting the PI3K/AKT metabolic axis.[42,43] Glycosaminoglycans are long unbranched and complex polysaccharides that are also an essential component of ECM. It is by now generally accepted that GAG plays an important role in cell adhesion, migration, survival, and apoptosis.[44] Research has shown that GAG is increased in skeletal muscle of insulin-resistant mice,[45] indicating it may play a key role in the pathophysiology of PCOS.

  Although the genes we explored might be promising targets for PCOS which can help to provide new directions for the pathogenesis and its molecule mechanism of PCOS, it is also essential to conduct deeper and more extensive research for more accurate relevant clinical treatment.


## 5. Conclusion
  In this study, a total of 174 DEGs and 10 hub genes were identified as new candidate targets for IR in PCOS individuals, and we indicated that the down-regulation of the PI3K/Akt signaling pathway may act as the underlying molecular basis of IR in PCOS, which may provide a new direction for developing novel treatment strategies for PCOS.


## Author contributions
  Fei Zhou performed the data analysis and wrote this manuscript. Tiantian Cheng sorted out the data. Fei Zhou conceived and designed the experiments. Yuling Xing revised the manuscript. Linlin Yang and Huijuan Ma performed project coordination and supervised the project. All authors have seen and approved the final manuscript.

  Conceptualization: Fei Zhou.

  Data curation: Tiantian Cheng.

  Methodology: Linlin Yang.

  Supervision: Huijuan Ma.

  Writing – original draft: Fei Zhou.

  Writing – review & editing: Yuling Xing.