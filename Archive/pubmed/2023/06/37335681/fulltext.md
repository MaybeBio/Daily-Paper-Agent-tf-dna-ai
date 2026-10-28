# Comprehensive analysis of femoral head necrosis based on machine learning and bioinformatics analysis


## Abstract
  Osteonecrosis of the femoral head (ONFH) is a kind of disabling disease, given that the molecular mechanism of ONFH has not been elucidated, it is of significance to use bioinformatics analysis to understand the disease mechanism of ONFH and discover biomarkers. Gene set for ONFH GSE74089 was downloaded in the Gene Expression Omnibus, and “limma” package in R software was used to identify differentially expressed genes related to oxidative stress. Gene Ontology and Kyoto Encyclopedia of Genes and Genomes pathway enrichment analyze were performed for functional analysis. We constructed a protein interaction network and identified potential transcription factors and therapeutic drugs for the hub genes, and delineated the TF-hub genes network. Least absolute shrinkage and selection operator regression, support vector machine and cytoHubba were used to screen feature genes and key genes, which were validated by Receiver operating characteristic. CIBERSORT was used to explored the immune microenvironment. Subsequently, we identified the function of key genes using Gene set variation analysis and their relationship with each type of immune cell. Finally, molecular docking validated the binding association between molecules and validated genes. We detected 144 differentially expressed oxidative stress-related genes, and enrichment analysis showed that they were enriched in reactive oxygen species and AGE-RAGE signaling pathway. Protein-protein interaction and TF-hub genes network were conducted. Further exploration suggested that APOD and TMEM161A were feature genes, while TNF, NOS3 and CASP3 were key genes. Receiver operating characteristic analysis showed that APOD, CASP3, NOS3, and TNF have strong diagnostic ability. The key genes were enriched in oxidative phosphorylation. CIBERSORT analysis showed that 17 types immune cells were differentially relocated, and most of which were also closely related to key genes. In addition, genistein maybe potential therapeutic compound. In all, we identified that TNF, NOS3, and CASP3 played key roles on ONFH, and APOD, CASP3, NOS3, and TNF could serve as diagnostic biomarkers.


## 1. Introduction
  Osteonecrosis of the femoral head (ONFH) is a disease characterized by necrosis of bone marrow and bone cells and often leading to the collapse of the femoral head and subsequent arthritis of the hip. Among which, nontraumatic osteonecrosis of the femoral head is highly associated with steroids and alcohol abuse and usually affects adults under 50 years of age.[1] In China, there are an estimated 8.12 million cases of NONFH among people aged 15 years and older, and the total cost of treatment is supposed to be at least $64 billion, placing a huge financial burden on the healthcare system.[2] Although total hip arthroplasty is the most effective treatment for patients with end-stage ONFH, the failure rate is still high in young or active patients due to prosthesis loosening and excessive wear. As a result, the outcome of total hip arthroplasty is often not satisfied.[3] Therefore, it is of great significance to explore biomarkers for the diagnosis and treatment in the early stage of ONFH.

  Many studies have found that several inflammatory factors or enzymes in the degenerative cartilage of ONFH patients are significantly changed and are involved in the pathological process of ONFH.[4–6] Articular cartilage has no blood supply and they rely on abundant and active mitochondria for energy production.[7] However, excessive and abnormal mechanical load, proinflammatory cytokines and chemokines can stimulate mitochondria to produce excessive reactive oxygen species (ROS),[8,9] which could promote the production of matrix degrading enzymes and disrupt cartilage homeostasis.[10] Researchers found that matrix metal oproteinase expression and chondrocyte apoptosis can be effectively reduced by maintaining mitochondrial membrane potential and reducing ROS production.[11,12] However, the mechanisms that induce ROS production remain largely unknown and require further investigation.

  Previous studies have found that ONFH is associated with inflammation, oxidative stress and the immune response,[13,14] however, they did not further explore the specific role of hub genes and their relationship with the immune system. In this study, we identified key genes associated with oxidative stress in cartilage tissue by machine learning, an emerging method that was used for feature extraction,[15] with the aim of exploring the mechanisms of disease development and screening out the potential diagnostic and therapeutic targets for ONFH (Fig. 1).


## 2. Method and material

### 2.1. Microarray data profile
  We selected the GSE74089 dataset on GPL13497 platform for the analysis of ONFH cartilage, which included 4 ONFH patient cartilage samples and 4 normal cartilage samples. The GSE123568 dataset on GPL15207 platform was selected as the external validation dataset, which included 30 ONFH patient serum samples and 10 normal samples.


### 2.2. Data processing and identification of differentially expressed genes (DEGs) and differentially expressed genes related to oxidative stress (OS-DEGs)
  The GSE74089 dataset was analyzed using the “Limma” package in R software, and the unpaired Student t test was used to calculate P values. |log2FC| > 1 and adjusted P value < .05 was used as the threshold to select DEGs. Gene sets related to oxidative stress were obtained in AmiGO (http://geneontology.org/), and the overlapping genes of 2 gene sets were considered as differentially expressed genes related to oxidative stress.


### 2.3. Gene ontology (GO) And Kyoto encyclopedia of genes and genomes (KEGG) analysis
  The KEGG pathway enrichment analysis and GO functional analysis were used to annotate differentially expressed IRGs from biological processes, molecular functions, and cellular components. Database for Annotation, Visualization, and Integrated Discovery was used to analyze the biological functions of the differential genes online. The threshold was set to a corrected P value < .05, and the results were visualized using the “ggplot” package in R software.


### 2.4. Protein-protein interaction network analysis
  The protein-protein interaction network was constructed using the Search Tool for the Retrieval of Interaction Gene/Proteins database (version 11.5, https://string-db.org/). The network was visualized by Cytoscape (version 3.9.1, https://cytoscape.org/). And then, MCODE and cytoHubba were then applied to screen out key modules and hub genes. Furthermore, we predicted transcription factors for the hub genes in Metascape and constructed TF-hub genes network.


### 2.5. Least absolute shrinkage and selection operator (LASSO) regression and support vector machine analysis
  Diagnostic markers of ONFH were screened using the minimum absolute contraction LASSO regression and support vector machine recursive feature elimination (SVM-RFE). The LASSO regression algorithm was performed using the “glmnet” package, and the SVM-RFE was performed using the “caret” package. Venn diagram was used to visualize the key genes obtained from 3 screening methods. Receiver operating characteristic analysis was performed to evaluate the diagnostic performance of the feature genes.


### 2.6. Immune cells infiltration analysis
  CIBERSORT algorithm was used to analyze the gene expression matrix to obtain the immune cell infiltration matrix. We used the “ggplot2” package to create box maps of immune cell infiltration in ONFH tissue and normal tissue. Spearman correlation analysis was performed to explore the relationship between selected diagnostic markers and infiltrating immune cells.


### 2.7. Gene set variation analysis
  The “gene set variation analysis (GSVA)” package in R software was used to explore the pathways closely related to the key genes. Terms with FDR <0.25 and P values < .05 were considered statistically significant pathways.


### 2.8. Drug prediction and molecular docking
  Key genes were uploaded to the Traditional Chinese Medicine Systems Pharmacology Database and Analysis Platform database to obtain a list of potential molecules, and the list intersection was considered as potential therapeutic molecules. We downloaded the 3D deconstruction of compounds from PubChem database. And the 3D structure of key genes were acquired from the Worldwide Protein Data Bank database. The Auto Dock tool software facilitates receptor and ligand processing. PyMOL was used to visualize molecular docking results.


### 2.9. Statistical analysis
  R (version 4.2.0) was used for statistical analysis. Student T and Wilcoxon test were used to estimate the differences in variables between groups, and P values < .05 were considered statistically significant. Spearman correlation tests were used to estimate the relationship between variables.


### 2.10. Ethics statement
  This study was conducted using public database data, so ethical and consent permission is unnecessary.


## 3. Results

### 3.1. Identification of OS-DEGs
  The results of principal component analysis (PCA) showed that there were differences in gene expression between ONFH patients and normal controls (see Figure S1 A, Supplemental Digital Content, http://links.lww.com/MD/J98, which depicted the principal component analysis of GSE74089). A total of 5653 differentially expressed genes were identified, of which 3823 were upregulated and 1830 were downregulated (Fig. 2A). The relative expression levels of these genes were displayed in a heatmap (Fig. 2B). By taking the intersection of the DEGs and oxidative stress-related gene set, we screened 144 oxidative stress-related DEGs (Fig. 2C), of which 110 were upregulated and 34 were downregulated (Fig. 2D).


### 3.2. Enrichment analysis of OS-DEGs
  To assess the function of DEGs, GO and KEGG enrichment analysis was conducted. As shown in Figure 3A–C, DEGs were mainly enriched in oxidative stress, peroxidase activity and neuronal cell body. KEGG pathway analysis showed that DEGs were mainly enriched in chemical carcinogenesis-reactive oxygen species, AGE-RAGE signaling pathway in diabetic complications, Longevity regulating pathway and MAPK signaling pathway (Fig. 3D).


### 3.3. PPI network
  We constructed a protein-protein interaction network of 133 nodes and 579 edges using the Search Tool for the Retrieval of Interaction Gene/Proteins database, then identified 10 hub genes using cytoHubba, including TNF, CASP3, INS, JUN, HIF1A, NOS3, SOD2, SOD1, FOXO3, and PPARGC1A (Fig. 4A). Furthermore, we screened out 2 key modules through MCODE (Fig. 4B and C), which were determined to be involved in cellular response to oxidative stress and in positive regulation of nitric oxide biosynthetic process and positive regulation of ERK1 and ERK2 cascade (Fig. 4D and E). To explore the regulation of hub gene expression, we identified the upstream transcription factors of hub genes, including RELA, ATF2, NFKB1, JUN, SP1, SIRT1, EGR1, and TP53 (Fig. 4F and G).


### 3.4. Identification of key genes and feature genes
  LASSO regression analysis screened out 5 disease-related genes, including KLF2, APOD, PDGFD, COL1A1, and TMEM161A (Fig. 5A and B). SVM-RFE algorithm screened out 15 disease-related genes, including TMEM161A, NOS3, MICB, GATA4, CYP2E1, TNF, AQP1, CASP3, AREG, APOD, IL18BP, PLK3, AIFM1, NDUFA12, and HAO1 (Fig. 5C). Considering of the 3 sets of genes, we determined that APOD and TMEM161A might be diagnostic indicators, and CASP3, TNF and NOS3 are key genes for disease development (Fig. 5D).

  We selected the GSE123568 as the external test dataset, and 2 discrete samples were removed after PCA analysis (see Figure S1 B and C, Supplemental Digital Content, http://links.lww.com/MD/J98, which depicted the principal component analysis of GSE123568). We performed Receiver operating characteristic analysis (Fig. 5E–I) to evaluate the diagnostic accuracy of genes, and the results showed that APOD, TNF, CASP3, and NOS3 had good diagnostic efficacy (AUC > 0.7), especially TNF, with an AUC of 0.89 (95% CI = 0.7963–0.9748).


### 3.5. Immune microenvironments
  CIBERSORT algorithm was used to analyze the immune cell infiltration of each samples (Fig. 6A), and PCA showed that there were significant differences in immune cell composition between the 2 groups (Fig. 6B).The box diagram of immune cell infiltration showed that, compared to normal tissue, ONFH cartilage has higher proportion of plasma cells, macrophages M0, macrophages M1, activated memory CD4 T cells, resting memory CD4 T cells, follicular helper T cells, CD8 T cells, naïve CD4 T cells, but lower proportion of resting NK cells, activated dendritic cells, neutrophils, memory B cells, activated NK cells, naïve B cells, and macrophages M2 (Fig. 6C).

  Subsequently, we investigated the correlation between the key genes and immune cells (Fig. 6D). The results (see Table S1, Supplemental Digital Content, http://links.lww.com/MD/J99, which displayed the correlation between key genes and immune cells) showed that TNF was positively correlated with NK cells resting (cor = 0.92, P = .001) and negatively correlated with T cells CD4 memory activated (cor = −0.94, P < .001). CASP3 was positively correlated with T cells CD4 memory activated (cor = 0.94, P < .001), and negatively correlated with NK cells resting (cor = −0.9, P = .002). NOS3 is positively correlated with Macrophages M2 (cor = 0.91, P = .002) and negatively correlated with Macrophages M0 (cor = −0.91, P = .002), M1 (cor = −0.91, P = .002).


### 3.6. Significant pathways of key genes
  GSVA analysis was performed to further reveal the potential function of key genes. The results indicated that CASP3 was enriched in cytokine-cytokine receptor interaction and oxidative phosphorylation. And NOS3 was enriched in cell adhesion molecules, Hippo signaling pathway and oxidative phosphorylation, while TNF was enriched in oxidative phosphorylation, cytokine-cytokine receptor interaction and reactive oxygen species (Fig. 7A–C).


### 3.7. Drug prediction and molecular docking
  We used the Traditional Chinese Medicine Systems Pharmacology Database and Analysis Platform database to search for molecules related to key genes and finally obtained 7 potential therapeutic molecules, including 17-beta-estradiol, quercetin, resveratrol, genistein, daidzein, ursolic acid, and puerarin, which were underwent molecular docking for further evaluation (Table 1). Binding energy ≤ −4.25 kcal/mol was set as the standard, and binding energy < −5 kcal/mol indicating a stable compound is formed.[16] Molecular docking analysis (Fig. 8A–E) showed that NOS3 could bind well with genistein and ursolic acid, whereas TNF could bind well with genistein, daidzein and 17-beta-estradiol. However, CASP3 showed in affinity for docking with all molecules.


## 4. Discussion
  Previous studies have found that articular cartilage degrades in the early stages of ONFH, even before any significant imaging changes occur in the femoral head or hip joint.[17] Cartilage degeneration and labral tears on the femoral head surface exacerbate hip instability and accelerate the development of ONFH.[18] Therefore, the detection of pathogenesis in cartilage may well be helpful for the early diagnosis of ONFH, while early treatment may also hinder the development of ONFH. Also, the key genes predicted in this study are also expected to become the therapeutic targets for the disease.

  In this study, we screened out the differentially expressed genes related to oxidative stress and found that they were mainly enriched in the cellular stress response to reactive oxygen species and hypoxia, which was also consistent with the pathological process of ONFH.[19,20] In addition, APOD and TMEM161A, 2 characteristic genes of ONFH, were screened by machine learning and LASSO regression, and verified by external datasets. Surprisingly, we found that APOD had good diagnostic ability with an AUC of 0.75 and could serve as a diagnostic biomarker of ONFH. Of note, we found that 3 key genes also had excellent diagnostic performance, especially TNF, which had an AUC of 0.89.

  We combined MCC algorithm and support vector machine to determine 3 key genes, including TNF, CASP3, and NOS3. Subsequent GSVA results showed that key genes were involved in the process of oxidative phosphorylation, indicating that oxidative stress plays an essential role in the development of ONFH. Many studies proposed that the down-regulation of oxidative phosphorylation could lead to the reduction of ATP production and the release of fragmented mitochondrial DNA, and ultimately lead to mitochondrial dysfunction and the excessive production of reactive oxygen species.[21–23] TNF-α, as a systemic proinflammatory factor, can stimulate the expression of cytokines and matrix degrading enzymes, such as MMP-13, ADAMTS-4, and ADAMTS-7, causing the depletion of aggregcan and collagen in cartilage.[4,24] Caspase-3 specifically cleaved GSDME in the linker and released GSDME-N fragment to penetrate the membrane pore, which subsequently converts apoptosis to pyroptosis.[25] Studies have reported that the polymorphisms in NOS3 are significantly correlated with the risk of ONFH.[26] Although NOS3 deficiency leads to reduced bone formation and impaired osteoblast function,[27] most experimental results suggest that nitric oxide is deleterious to cartilage and may lead to the loss of extracellular matrix.[28,29]

  Functional enrichment analysis showed that OS-DEGs were mainly involved in AGE-RAGE signaling pathway, mitophagy and MAPK signaling pathway. Stimulation of IL-1β induces the accumulation of ROS and activates the MAPK pathway.[30] Many studies have depicted that p38 MAPK pathway not only triggers the degradation of articular cartilage mediated by aggrecanase and matrix metal oproteinase, but also plays a role in the apoptosis of chondrocytes.[31,32] Excessive production of ROS may induce mitophagy to remove damaged mitochondria,[33] which can negatively regulate oxidative damage and ROS production. Also, the interaction of HMGB1 with RAGE downregulates the expression of PPAR γ,[34] which subsequently impairs the ability of antioxidant systems, thereby, significantly exacerbated oxidative stress.[35]

  We also performed immune cell infiltration analysis and found an increased proportion of CD4 + T cells, CD8 + T cells, M0 macrophages, and M1 macrophages. Macrophages are important participants in the host inflammatory response. Polarized M1 macrophages can produce a large amount of proinflammatory cytokines, nitric oxide and reactive oxygen species,[36] and downregulates the expression of ACAN and COL2 to inhibit chondrogenesis, differentiation and cartilage repair. It has been reported that the imbalance of T cell subsets may be involved in the development of ONFH. The increased proportion of CD4 + T cells can produce proinflammatory cytokines and even induce receptor activator of nuclear factor kappa-b ligand-mediated osteoclast generation.[37] In addition, infiltration of CD8 + T cells may promote angiogenesis and cartilage destruction by maintaining VEGF and TIMP1 levels.[38]

  Through molecular docking analysis, we found that genistein could stably bind with TNF and NOS3, and could be a potential molecule for the treatment of ONFH. Genistein has strong anti-inflammatory and antioxidant effects, and can reduce oxidative stress by regulating Nrf2 signal to increase the expression of antioxidant enzymes.[39] Genistein was found to reduce TNF levels in a dose-dependent manner, which is consistent with our results, and interestingly, genistein also reduced the expression of caspase-3, thus achieving a protective effect on knee cartilage.[40,41] However, the therapeutic efficacy of genistein in ONFH still needs further experimental verification.

  This research has some limitations. First, the sample size in this data set is insufficient, therefore biological experiments to further validation are needed. Second, We applied machine learning to screen for signature genes and used a data set of ONFH patients serum but not cartilage tissue for validation, which may have biased the results somewhat. Therefore, data sets with sufficient sample sizes and experimental validation are required to explore the pathogenesis of ONFH.


## Author contributions
  Conceptualization: Zheng Chen.

  Methodology: Yuankang Jiang.

  Software: Suwen Wu.

  Writing – original draft: Zheng Chen, Meng Dang.

  Writing – review & editing: Meng Dang.


## Supplementary Material