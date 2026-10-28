# Roles of NOC3L and DDX17 in acquired immunodeficiency complicated with viral myocarditis and osteoporosis


## Abstract
  Acquired immunodeficiency syndrome is a systemic infectious disease caused by human immunodeficiency virus infection, which could attack the bones and heart. However, the relationship between Nuclear Complex Associated 3 Homolog (NOC3L) and DEAD box helicase 17 (DDX17) and acquired immunodeficiency complicated with viral myocarditis and osteoporosis is unclear. The acquired immune deficiency dataset GSE140713, GSE147162 and the osteoporosis dataset (GSE230665), and viral myocarditis dataset (GSE150392) configuration files were generated from gene expression omnibus. The differentially expressed genes (DEGs) were screened and performed weighted gene co-expression network analysis. Construction and analysis of protein–protein interaction network. Functional enrichment analysis, gene set enrichment analysis, immune infiltration analysis, gene expression heatmap, and comparative toxicogenomics database analysis were performed. TargetScan screens miRNAs of DEGs. Thousand three hundred thirty-five DEGs were identified. According to gene ontology, they are mainly concentrated in the regulation of RNA biosynthesis, cytoplasmic ribosome, and the DNA binding transcription factor activity. In Kyoto Encyclopedia of Genes and Genomes analysis, they are mainly concentrated in TGF-β signal pathway, Notch signaling pathway, cAMP signaling pathway, and Apelin signaling pathway. Gene set enrichment analysis shows that DEGs are mainly enriched in cytoplasmic ribosome, transcriptional regulator activity, DNA binding transcription factor activity, TGF-β signal pathway, and Notch signal pathway. In the enrichment project of Metascape, tyrosine kinase receptor signaling, growth regulation, and enzyme-linked receptor protein signaling pathways can be seen in the gene ontology enrichment project. Four core genes (NOC3L, WDR46, SDAD1, and DDX17) were obtained. Core genes (NOC3L, WDR46, SDAD1, and DDX17) were low expressed in both acquired immunodeficiency and osteoporosis samples. Comparative toxicogenomics database analysis showed that core genes (NOC3L, WDR46, SDAD1, and DDX17) were associated with inflammation necrosis. The expressions of NOC3L and DDX17 are low in acquired immunodeficiency combined with viral myocarditis and osteoporosis.


## 1. Introduction
  Acquired immune deficiency combined with osteoporosis refers to a disease state where both acquired immune deficiency and osteoporosis coexist. Acquired immune deficiency refers to the dysfunction of the immune system acquired at a certain stage of life. Osteoporosis is a bone system disease. These 2 conditions can simultaneously affect a person’s health status and interact with each other. The global number of people infected with human immunodeficiency virus (HIV)/acquired immunodeficiency syndrome (AIDS) in 2020 was approximately 38 million. The infection rate of HIV/AIDS is relatively high in sub Saharan Africa, accounting for over half of the global number of infections. HIV is mainly transmitted through the following channels: sexual transmission, mother to child transmission, blood transfusion, or blood product transmission.[1,2] More than 200 million people worldwide suffer from osteoporosis. People over 50 years old have a higher risk of osteoporosis. Women have a higher risk of osteoporosis than men. Bad living habits are related to the occurrence of osteoporosis. Family history will also increase the risk of individual disease. Incidence rate in Europe and North America is relatively high.[3,4] Patients with acquired immune deficiency and osteoporosis typically exhibit accelerated progression of osteoporosis, with fragile and fragile bones that are more prone to fractures. The pathogenesis of acquired immune deficiency combined with osteoporosis involves multiple factors, including functional damage to the immune system, increased inflammatory response, hormone imbalance, abnormal function of bone cells, and side effects of drug treatment. Some common clinical manifestations of acquired immune deficiency include increased susceptibility to infection, enlarged lymph nodes, weight loss, recurrent oral ulcers, Candida infections, skin lesions, malignant tumors, etc.[5] The clinical manifestations of osteoporosis include increased risk of fractures, decreased height, spinal deformation, bone pain, posture changes, and bone vulnerability.[6,7] The pathological features of acquired immune deficiency mainly involve abnormalities and destruction of the immune system. Acquired immune deficiency leads to abnormal immune system function, mainly due to damage to T lymphocyte function. Lymph tissue of AIDS patients, especially lymph nodes, spleen and tonsils, may have pathological changes. HIV infection triggers a chronic inflammatory response throughout the body, leading to damage to multiple tissues and organs. Impaired immune system makes AIDS patients susceptible to Candida and other fungi. Acquired immune deficiency makes AIDS patients more prone to malignant tumors.[8] Viral myocarditis refers to localized or diffuse acute or chronic inflammatory lesions of the myocardium caused by viral infection. Multiple viruses can cause myocarditis, among which enteroviruses and upper respiratory tract infection viruses are the most common. When HIV infected individuals come into contact with these viruses, their immune system is compromised, making them more susceptible to developing myocarditis. The pathological characteristics of osteoporosis mainly involve structural and metabolic abnormalities in bone tissue, leading to decreased bone density and structural destruction of bone. Bone density refers to the ratio of mineral content and bone mass in bone tissue. The decrease in bone formation process is due to a decrease in the function or quantity of bone forming cells. Osteoporosis leads to abnormal changes in bone microstructure. In osteoporosis, changes in the composition and structure of bone matrix result in a decrease in the quality and mechanical properties of bone tissue. Osteoporosis leads to bone destruction, leading to enlargement of the bone marrow cavity.[9] Acquired immunodeficiency combined with viral myocarditis and osteoporosis poses risks of increased fracture risk, pain and functional limitations, altered body posture, and decreased height, seriously affecting mental health. The etiology of acquired immunodeficiency combined with viral myocarditis and osteoporosis is unclear.

  Bioinformatics is an interdisciplinary field involving computer science, mathematics, biology, and statistics. Its development has greatly aided biological research and accelerated interpretation and understanding of biomolecules such as genomes, proteins, and metabolomes. The advantages of bioinformatics technology are mainly reflected in its efficiency, accuracy, visualization and repeatability, which makes the interpretation of biological information more efficient and accurate. Related studies have shown that MKI67 is a potential oncogene of oral squamous cell carcinoma by high-throughput technology,[10] CEACAM1 can be used as a target of oral cancer.[11]

  However, the relationship between Nuclear Complex Associated 3 Homolog (NOC3L), DEAD box helicase 17 (DDX17), and acquired immune deficiency combined with viral myocarditis and osteoporosis is currently unclear. This article intends to use the bioinformatics technology to explore core genes between acquired immune deficiency combined with viral myocarditis and osteoporosis and normal tissues. Validate significant role of NOC3L and DDX17 in the combination of acquired immunodeficiency, viral myocarditis, and osteoporosis using a public dataset.


## 2. Methods

### 2.1. Acquired immunodeficiency combined with viral myocarditis and osteoporosis dataset
  In this study, the acquired immune deficiency dataset GSE140713, GSE147162, and the osteoporosis dataset GSE230665 configuration files were generated from gene expression omnibus of GPL6480, GPL21185, and GPL10332. GSE140713 includes 50 acquired immunodeficiency and 7 normal tissue samples, GSE147162 includes 2 acquired immunodeficiency and 2 normal tissue samples. GSE230665 includes 12 osteoporosis and 3 normal tissue samples. Viral myocarditis dataset (GSE150392) is downloaded.


### 2.2. De batch processing
  For merging and de batching of multiple datasets, R software package was used to merge datasets. R software package in Silico Merging was used to merge the datasets and obtain merge matrix. We use the remove Batch Effect function of R software package limma to remove batch effects and ultimately obtain matrix after removing batch effects.


### 2.3. Screening of differentially expressed genes (DEGs)
  We first performed a log2 transformation on the de batch merge matrix as well as the gene expression matrix. And calculated logarithmic ratio of the adjusted t-statistic, adjusted f-statistic, and differential expression by adjusting the standard error to a common value through empirical Bayesian adjustment. We obtained significance of differences for each gene and created a volcanic map. Afterwards, the differential genes of the de batch merge matrix.


### 2.4. Weighted Gene Co-expression Network Analysis (WGCNA)
  We used de batch merge matrices of dataset to calculate median absolute deviation of each gene. We also used R software package WGCNA’s good Samples Genes method to remove the outliers and samples, further constructed a scale-free co-expression network using WGCNA.

  Average linkage hierarchical clustering was performed using TOM-based differential measures to classify genes with similar expression profiles into gene modules. The heterogeneity of the module signature genes was calculated, the cut lines of the module tree view were selected, and some modules were merged.


### 2.5. Construction and analysis of protein–protein interaction (PPI) network
  This study inputted a list of DEGs into Search Tool for the Retrieval of Interacting Genes database and constructed a PPI network for predicting core genes. The core genes were visualized and predicted using Cytoscape software. Firstly, we import PPI network into Cytoscape software and use MCODE to find modules with the best correlation. We also use 4 algorithms (MCC, MNC, DMNC, and Betweenness) to calculate the best correlation and take the intersection.


### 2.6. Functional enrichment analysis
  Gene ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) analysis are computational methods for evaluating gene functions and biological pathways. This study inputted the list of DEGs screened from Wayne diagram into KEGG rest API. We obtained the latest KEGG pathway gene annotation as a background and mapped the genes to the background set. We used R software package cluster Profiler for enrichment analysis to obtain results of gene set enrichment. Genes were mapped to the background set using the GO annotation of genes in the R software package as the background. Metascape database can provide comprehensive gene list annotations and analysis resources with visual export. We used Metascape Database for functional enrichment analysis and export of the list of DEGs mentioned above.


### 2.7. Gene set enrichment analysis (GSEA)
  The website obtained GSEA software, which divided disease samples from 2 datasets based on acquired immunodeficiency, osteoporosis, and normal tissue into 2 groups. The samples were collected from Molecular Signatures Database. Based on the gene expression profiles and phenotypic grouping, minimum gene set was set to 5, the maximum gene set was set to 5000. A thousand resamplings were conducted, and P value < .05, FDR < 0.25 were considered statistically significant. GO and KEGG analyses were conducted on entire genome.


### 2.8. Immune infiltration analysis
  CIBERSORT is a very commonly used method for calculating immune cell infiltration. We applied integrated bioinformatics methods and analyzed osteoporosis dataset GSE230665 using the CIBERSORT software package.

  The expression matrix of immune cell subtypes was deconvolved using principle of linear support vector regression to estimate the abundance of immune cells. At the same time, we used a confidence level of P < .05 as the truncation criterion to screen samples with sufficient confidence.


### 2.9. Gene expression heatmap
  R packet heatmap was used to generate heatmaps of expression levels of core genes in PPI network, respectively, to visualize expression differences of core genes between samples of acquired immunodeficiency, osteoporosis, and normal tissue.


### 2.10. Comparative toxicogenomics database (CTD) analysis
  The CTD integrates a large amount of data on chemical substances, genes, and interactions between diseases. The core genes were entered into CTD to find the diseases most associated with core genes. Excel was used to draw radar maps of differences in expression of each gene.


### 2.11. The miRNA
  TargetScan is an online database for prediction and analysis of miRNAs and target genes. TargetScan screened miRNAs that regulated central DEGs.


## 3. Result

### 3.1. DEGs analysis
  Based on the set cutoff values, we identified DEGs using gene expression matrices of acquired immunodeficiency dataset (Fig. 1A) and the osteoporosis dataset (Fig. 1B), and then used the Wayne plot to intersect the DEGs, resulting in a total of 1335 DEGs (Fig. 1C).


### 3.2. Functional enrichment analysis

#### 3.2.1. DEGs
  We conducted GO and KEGG analysis on DEGs. According to GO analysis, they are mainly concentrated in regulation of RNA biosynthesis, cytoplasmic ribosome, and DNA binding transcription factor activity. In KEGG analysis, they are mainly concentrated in TGF-β signal pathway, Notch signaling pathway, cAMP signaling pathway, and Apelin signaling pathway (Fig. 2A–D).


#### 3.2.2. GSEA
  We conducted GSEA on entire genome, aiming to identify potential enrichment terms in non-DEGs and verify the results of DEGs. The enrichment results of acquired immunodeficiency dataset (Fig. 3A–D) and osteoporosis dataset (Fig. 3E–H) show that DEGs are mainly enriched in cytoplasmic ribosome, transcriptional regulator activity, DNA binding transcription factor activity, TGF-β signal pathway, Notch signal pathway.


#### 3.2.3. Metascape enrichment analysis
  In the enrichment project of Metascape, tyrosine kinase receptor signaling, growth regulation, and enzyme-linked receptor protein signaling pathways can be seen in GO enrichment project (Fig. 4A). At the same time, an enrichment network with enrichment terms and p-values is output (Fig. 4B and C), visualizing correlation and confidence of each enrichment project.


### 3.3. WGCNA
  The selection of soft threshold power is an important step in WGCNA. The soft threshold power in WGCNA is set to 9, which is the lowest power for scale-free topology fitting index of 0.9 (Fig. 5A and B). Hierarchical clustering trees of all genes were constructed, 27 modules were generated (Fig. 5C), the interactions between modules were analyzed (Fig. 5D). A heat map of module phenotype correlation (Fig. 6A). A scatter map of GS and MM correlation of relevant hub genes (Fig. 6B–E) were also generated.


### 3.4. Construction and analysis of PPI network
  The PPI network of DEGs was constructed using Search Tool for the Retrieval of Interacting Genes online database and analyzed by Cytoscape (Fig. 7A) to obtain core gene cluster (Fig. 7B), and then uses a variety of algorithms to identify the central gene and make a Venn diagram to obtain the union (Fig. 7C). We use the 4 algorithms of MCC, MNC, DMNC, and Betweenness to obtain the core gene (Fig. 7D–G), and finally we get 4 core genes (NOC3L, WDR46, SDAD1, and DDX17).


### 3.5. Immune infiltration analysis
  CIBERSORT software package was used to analyze gene expression matrix of osteoporosis. The proportion of immune cells in entire gene expression matrix (Fig. 8A), the expression heatmap of immune cells in dataset (Fig. 8B) were obtained. Correlation analysis was also performed on infiltrating immune cells, resulting in a co-expression pattern between the immune cell components (Fig. 8C).


### 3.6. Core gene expression heatmap
  We visualized the expression levels of core genes in acquired immunodeficiency dataset (Fig. 9A), the osteoporosis dataset (Fig. 9B), and generated heat maps, respectively. We found that core genes (NOC3L, WDR46, SDAD1, and DDX17) were low expressed in both acquired immunodeficiency and osteoporosis samples, and high expressed in normal samples, It is speculated that core genes (NOC3L, WDR46, SDAD1, and DDX17) may have regulatory effects on acquired immune deficiency and osteoporosis.


### 3.7. CTD analysis
  A list of core genes was entered into the CTD to search for diseases associated with core genes, improving the knowledge of gene–disease associations. Core genes (NOC3L, WDR46, SDAD1, and DDX17) were associated with inflammation, necrosis, weight loss, and edema (Fig. 10). And the NOC3L and DDX17 were significantly related with the HIV, viral myocarditis, and osteoporosis (Fig. 11).


### 3.8. Prediction and functional annotation of miRNAs related to hub genes
  A list of hub genes were input into target scan to find relevant miRNAs and improve the understanding of gene expression regulation (Table 1). The miRNA associated with the NOC3L is hsa-miR-758-3p. The miRNAs associated with the SDAD1 are hsa-miR-30b-5p, hsa-miR-30a-5p, and hsa-miR-30d-5p. The miRNAs associated with the DDX17 gene are hsa-miR-449a, hsa-miR-34c-5p, and hsa-miR-449b-5p.


## 4. Discussion
  The harm of acquired immune deficiency combined with viral myocarditis and osteoporosis is mainly reflected in multiple aspects. Patients with acquired immunodeficiency combined with viral myocarditis and osteoporosis have fragile and fragile bones, making them prone to fractures. HIV infection leads to a decrease in the number of CD4+ T cells, which disrupts the normal functions of cellular and humoral immunity, leading to immune deficiency in the body.[12–14] Some drugs or chemotherapy drugs are used to suppress the function of the immune system, such as immunosuppressants used after organ transplantation. These drugs suppress the immune response, reduce the activity and function of immune cells, and thus increase the body’s susceptibility to infection. Abnormal regulation of the immune system may also lead to acquired immune deficiency. Imbalance in immune regulation in autoimmune diseases can lead to the immune system attacking normal tissues while weakening its ability to respond to infections.[15,16] Infection with certain pathogens can also lead to acquired immune deficiency. Long term chronic infection can activate the immune system, leading to depletion and functional damage of immune cells, ultimately leading to immune deficiency.[17,18] Some genetic mutations may lead to dysfunction or defects in the immune system, increasing the risk of infection. The molecular mechanism of osteoporosis involves multiple complex biological processes and regulatory factors. The occurrence of osteoporosis is closely related to imbalance of bone remodeling. In osteoporosis, process of bone resorption is relatively enhanced, while the process of bone formation is relatively weakened.[19–21] Hormones play an important regulatory role in occurrence of osteoporosis. After menopause, women’s estrogen levels decrease, leading to increased bone resorption and reduced bone formation, thereby accelerating the loss of bone density. Decreased testosterone levels in males are also associated with osteoporosis.[22–24] Abnormal bone cell function in osteoporosis is an important factor leading to imbalanced bone remodeling. During the process of bone resorption, the activity of bone resorption cells increases, leading to bone destruction. During the process of bone formation, the number and function of osteoblasts decrease, leading to a decrease in bone formation ability. Factors such as malnutrition, vitamin D deficiency, and insufficient calcium intake may also affect the occurrence of osteoporosis.[25] Inflammatory factors and immune cells can directly or indirectly affect bone cell function and bone remodeling processes. Deeply exploring the molecular mechanism of acquired immunodeficiency combined with osteoporosis is crucial for study of targeted drugs. The main result of this study is that NOC3L and DDX17 are low expressed in acquired immunodeficiency combined with osteoporosis. The higher NOC3L and DDX17, the better the prognosis.

  NOC3L is a gene that encodes the NOC3 protein. The NOC3L protein is mainly located in the nucleolar region of the nucleus and participates in various nuclear processes and nucleolar functions. Its localization in the nucleus is closely related to its function in the nucleolus. NOC3L participates in the formation and assembly of nucleoli, regulating their structure and function. The nucleolus is a special subcellular structure in the nucleus, which is related to the biosynthesis of ribosome and the processing of nucleic acid. NOC3L is involved in the processing and modification of rRNA (ribosomal RNA) in the process of ribosome biosynthesis. It, together with other nucleolar proteins, constitutes a complex of ribosome biosynthesis and regulates the processing and maturation of rRNA. NOC3L is related to transcription factors and RNA polymerase, and participates in the process of transcriptional regulation. It may interact with other proteins to regulate the transcription and expression of regulator gene.[26]

  DDX17, also known as RNA helicase A is an ATP dependent RNA helicase that plays an important role in multiple nucleic acid related processes. As an RNA helicase, DDX17 plays a role in unwinding and resolution of nucleic acids. It can bind RNA molecules and unravel their double stranded structure through ATPase activity, promoting the structural transformation of RNA and the unraveling of RNA–RNA or RNA–DNA interactions. DDX17 is involved in the process of gene expression regulation. It forms complexes with transcription factors, RNA polymerase and other auxiliary proteins to regulate the transcription initiation and extension of regulator gene. DDX17 promotes the formation of transcriptional complexes or unravels transcriptional inhibition by unraveling DNA–RNA complexes or RNA secondary structures. DDX17 plays an important role in mRNA processing and transportation. It participates in mRNA processing processes such as splicing, capping, and polyadenylation, regulating mRNA stability, and post transcriptional modifications. In addition, DDX17 is also associated with processes such as mRNA transport, nucleocytoplasmic transport, and local transport. DDX17 regulates the replication and infectivity of viruses by interacting with viral RNA or viral protein.[27,28] Some studies have shown that depletion of DDX17 reduces HIV-1 infectivity 5-fold, and extracellular (supernatant) CA-p24 decreases to a similar extent without affecting intracellular HIV-1Gag levels.[29,30] Further studies have shown that knockdown of MiR-9-5p can promote osteogenic differentiation of BMSCS under high glucose treatment by targeting DDX17.[31] Therefore, it is hypothesized that NOC3L and DDX17 may play a role in regulation of gene transcription and expression during the inflammatory response of acquired immunodeficiency and in osteoporosis.

  DDX17 is an RNA helicase that plays an important role in regulating gene expression and RNA metabolism within cells. Although DDX17 plays an important role in biological processes, there is currently no direct evidence linking it to viral myocarditis. In summary, there is currently no direct evidence to suggest a clear link between NOC3L and DDX17 and viral myocarditis. The pathogenesis of viral myocarditis involves multiple viruses and complex biological processes, and although NOC3L and DDX17 each play important roles in biological processes, they are not necessarily directly related to viral myocarditis.

  Although this article has conducted rigorous bioinformatics analysis, there are still some shortcomings. This study did not conduct animal experiments on gene overexpression or knockout to further validate its function.


## 5. Conclusion
  The present study found that the low expression of NOC3L and DDX17 in acquired immunodeficiency combined with viral myocarditis and osteoporosis may be associated with the disease process, and future studies should further explore their possibilities as potential therapeutic targets. NOC3L and DDX17 may play a role in the occurrence and development of acquired immunodeficiency combined with viral myocarditis and osteoporosis through cellular regulation and other pathways, which provides a certain direction for the study of its mechanism and develops therapeutic strategies based on these genes.


## Author contributions
  Conceptualization: Liping Xiao, Xin Li.

  Data curation: Liping Xiao, Jing-Jing Wang, Chang-Song Zhao.

  Formal analysis: Jing-Jing Wang.

  Methodology: Liping Xiao, Xin Li, Xue-Min Quan, Chang-Song Zhao.

  Visualization: Xin Li, Xue-Min Quan.

  Writing – original draft: Liping Xiao, Xin Li, Jing-Jing Wang, Xue-Min Quan, Chang-Song Zhao.

  Writing – review & editing: Liping Xiao, Xin Li.