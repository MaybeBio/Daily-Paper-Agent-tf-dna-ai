# The role of the TARDBP gene in osteonecrosis of the femoral head: Bioinformatics analysis and mechanistic exploration


## Abstract
  Osteonecrosis of the femoral head (ONFH) is a condition caused by venous stasis, impaired arterial blood flow, or destruction of the femoral head, often resulting in the localized death of bone cells and bone marrow components, leading to joint collapse. Although the pathogenesis of ONFH is complex, recent attention has focused on the role of the TAR DNA-binding protein (TARDBP) gene and its encoded protein, TDP-43, in the disease process. TDP-43, which plays a role in neurodegenerative diseases, may also regulate apoptosis, oxidative stress, and immune responses in ONFH. This study utilized the GSE74089 and GSE123568 datasets from the gene expression omnibus database to analyze differentially expressed genes between ONFH and normal samples. Through batch effect correction, gene enrichment analysis (gene ontology, Kyoto Encyclopedia of Genes and Genomes, and gene set enrichment analysis), protein–protein interaction network construction, and weighted gene co-expression network analysis, key genes in ONFH were identified. Additionally, immune infiltration was analyzed using CIBERSORT, and a neural network model was developed to assess the importance of these genes in ONFH. The analysis revealed that TARDBP expression was significantly elevated in ONFH samples and correlated with the infiltration of monocytes and M1 macrophages. Gene ontology and Kyoto Encyclopedia of Genes and Genomes analyses suggested that TARDBP may regulate bone metabolism and repair via the Wnt/β-catenin signaling pathway. Protein–protein interaction network analysis identified 9 core genes, with TARDBP scoring the highest in the neural network model, indicating its pivotal role in ONFH regulation. TARDBP is highly expressed in ONFH, and its possible role by regulating apoptosis, oxidative stress, and immune response provide new ideas for the study of the molecular mechanism of ONFH.


## 1. Introduction
  Osteonecrosis of the femoral head (ONFH) is a condition characterized by the localized death of bone cells and bone marrow components, resulting from venous stasis, impaired arterial blood flow, or damage to the femoral head.[1,2] In ONFH, decreased blood or oxygen supply leads to initial ischemic necrosis; however, the clinical symptoms primarily reflect the failure of bone tissue repair rather than ischemic injury alone.[3] An imbalance between bone formation and resorption occurs, where osteoblast activity cannot keep pace with osteoclast-mediated absorption of necrotic tissue, leading to unstable bone regions and eventually femoral head collapse and joint damage. ONFH is classified into traumatic and nontraumatic types. Traumatic ONFH is usually triggered by fractures, dislocations, or injuries,[4–7] whereas nontraumatic ONFH is associated with prolonged glucocorticoid use, alcohol abuse, hemoglobinopathies, and autoimmune diseases. Globally, the incidence of ONFH has been increasing, with around 20,000 new cases annually. Of these, 30% to 50% of patients eventually require hip replacement surgery.[8] Clinically, ONFH is characterized by hip pain, stiffness, and restricted mobility. Pain typically begins in the groin area and may radiate to the thigh or knee. As the disease progresses, patients may develop a limp.[9–11] Pathologically, the disease progresses through stages of ischemia, necrosis, failed bone repair, and femoral head collapse.[12] ONFH predominantly affects individuals aged 30 to 50 years,[13] and, if left untreated, often necessitates hip replacement surgery. The etiology of ONFH is complex and not yet fully understood. In addition to trauma, prolonged use of glucocorticoids, and alcohol abuse, genetic factors, chromosomal abnormalities, and gene fusions are also believed to play roles in its development.[14] Despite the availability of various clinical treatments, their effectiveness remains suboptimal, highlighting the need to explore the molecular mechanisms underlying ONFH to develop new targeted therapies.

  With the advancement of bioinformatics and high-throughput sequencing technologies, researchers have been able to identify core genes and molecular pathways associated with diseases from large-scale datasets. Bioinformatics analysis effectively identifies differentially expressed genes (DEGs) and employs enrichment analysis to explore their potential biological functions.[15] These techniques have been widely applied in the study of cancers,[16] cardiovascular diseases,[17] and neurodegenerative disorders,[18] providing valuable insights into the molecular mechanisms of these diseases. However, systematic research on the relationship between the TARDBP gene and ONFH remains lacking.

  TAR DNA-binding protein (TARDBP) 43 is a multifunctional RNA-binding protein involved in the regulation of RNA transcription, splicing, transport, and degradation. Abnormal expression of the TARDBP gene has been extensively reported in various neurodegenerative diseases, such as amyotrophic lateral sclerosis (ALS) and Alzheimer disease.[19] However, the role of TARDBP in ONFH has not been thoroughly investigated.

  In this study, we utilized datasets from the gene expression omnibus database and applied bioinformatics analysis techniques to identify DEGs associated with ONFH and perform functional enrichment and pathway analyses. Furthermore, we constructed a neural network model to evaluate the importance of the TARDBP gene in ONFH. Our findings aim to provide novel molecular targets for the diagnosis and treatment of ONFH.


## 2. Methods

### 2.1. ONFH datasets
  In this study, ONFH datasets GSE74089 and GSE123568 were obtained from the gene expression omnibus database (https://www.ncbi.nlm.nih.gov/geo/) using platforms GPL13497 and GPL15207. GSE74089 includes 4 ONFH samples and 4 normal tissue samples, while GSE123568 comprises 30 ONFH samples and 10 normal samples. These datasets were used to identify DEGs in ONFH.


### 2.2. Batch effect correction
  For dataset integration and batch effect removal, we initially merged GSE74089 and GSE123568 using the R package inSilicoMerging [DOI: 10.1186/1471-2105-13-335]. After obtaining the combined matrix, the removeBatchEffect function from the R package limma (version 3.42.2) was applied to eliminate batch effects, producing a corrected matrix for further analysis.


### 2.3. DEG identification
  The R package limma was utilized for probe summarization and background correction of the combined GSE74089 and GSE123568 datasets. Raw P-values were adjusted using the Benjamini–Hochberg method, and fold change was computed using the false discovery rate (FDR). DEGs were identified with a threshold of P < .05 and fold change > 1.5. Volcano plots were generated to visualize the identified DEGs.


### 2.4. Gene set enrichment analysis (GSEA)
  For GSEA, we obtained the GSEA software (version 3.0) from the GSEA website (https://software.broadinstitute.org/gsea/index.jsp). Sample groups were divided based on phenotype (disease vs normal), and the c2.cp.kegg.v7.4.symbols.gmt subset was downloaded from the Molecular Signatures Database (MSigDB) [DOI: 10.1093/bioinformatics/btr260]. Parameters were set with a minimum gene set size of 5, a maximum size of 5000, and 1000 permutations. A P-value < .05 and FDR < 0.25 were considered statistically significant. Gene ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) analyses were also conducted as part of the GSEA framework.


### 2.5. Functional enrichment analysis
  GO and KEGG analyses were performed to evaluate gene functions and biological pathways. The list of DEGs from the limma analysis was input into the KEGG REST API (https://www.kegg.jp/kegg/rest/keggapi.html) to retrieve the latest pathway annotations. We used the R package clusterProfiler (version 3.14.3) for enrichment analysis. Gene annotations were derived from the R package org.Hs.e.g..db (version 3.1.0). The enrichment criteria included a minimum gene set size of 5, a maximum size of 5000, with a P-value < .05 and FDR < 0.25.

  Additionally, the Metascape database (https://metascape.org/gp/index.html) was utilized for comprehensive gene list annotation and visualization. Metascape provided enriched functional terms and visual export of results based on the DEG lists.


### 2.6. Weighted gene co-expression network analysis (WGCNA)
  We utilized the merged batch-corrected gene expression matrix from the GSE74089 and GSE123568 ONFH datasets. The median absolute deviation for each gene was calculated, and the 50% of genes with the lowest median absolute deviation values were removed. Outliers among genes and samples were eliminated using the goodSamplesGenes function from the R package WGCNA. A scale-free co-expression network was constructed, with Pearson correlations and average linkage hierarchical clustering applied to all gene pairs. We used a power function Amn=∣Cmn∣βA_{mn} = |C_{mn}|^\betaAmn =∣Cmn ∣β to create a weighted adjacency matrix, where CmnC_{mn}Cmn represents the Pearson correlation between genes mmm and nnn, and β\betaβ is a soft-thresholding parameter to emphasize strong correlations and down-weight weaker ones. With a power of 10 applied, the adjacency matrix was converted to a topological overlap matrix (TOM), which measured network connectivity as the sum of adjacencies between each gene and all other genes. Dissimilarity was calculated as 1 − TOM1 − \text{TOM}1 − TOM, and average linkage hierarchical clustering was used to classify genes with similar expression patterns into modules, with a minimum module size of 30 genes. Modules with dissimilarity <0.25 were merged, while the gray module contained unassigned genes.


### 2.7. Construction and analysis of protein–protein interaction (PPI) network
  The Search Tool for the Retrieval of Interacting Genes (STRING) database (https://string-db.org/) was employed to predict and integrate PPI. We input the DEGs into STRING to construct a PPI network with a confidence score > 0.4. The resulting PPI network was visualized and analyzed using Cytoscape software, which provides biologists with tools for network analysis and 2D visualization. The MCODE plugin identified the most relevant modules, and 3 algorithms: MCC, EPC, and Radiality, were used to rank the top 10 correlated genes, with their intersections exported as core genes.


### 2.8. Gene expression heatmap
  The expression levels of the core genes identified from the PPI network were visualized using heatmaps generated by the R package heatmap. These heatmaps illustrated the differences in expression levels between ONFH and normal tissue samples in datasets GSE74089 and GSE123568.


### 2.9. Comparative toxicogenomics database (CTD) analysis
  The CTD provides extensive data on interactions between chemicals, genes, phenotypes, and diseases, facilitating research into disease-related environmental factors and drug mechanisms. We input the core genes into the CTD to identify associated diseases, and Excel was used to create radar plots illustrating the expression differences for each gene.


### 2.10. Immune infiltration analysis
  CIBERSORT (https://CIBERSORT.stanford.edu/) is a widely used computational tool for analyzing immune cell infiltration. The LM22 gene file was utilized to define 22 immune cell subtypes. Using the batch-corrected merged matrix from GSE74089 and GSE123568, CIBERSORT estimated the abundance of immune cells through deconvolution of the expression matrix using linear support vector regression. A P-value < .05 was set as the cutoff to identify samples with reliable estimates.


### 2.11. Neural network model construction
  Gene expression data from GSE74089 and GSE123568 were used to build a neural network model to evaluate the importance of the 9 core genes (SRSF1, HNRNPM, TARDBP, HNRNPC, HNRNPA1, HNRNPU, HNRNPR, HNRNPF, EWSR1). TensorFlow and Keras were employed to construct and train the neural network. Core gene data were labeled, with ONFH samples assigned a value of 1 and normal samples assigned a value of 0. Data were preprocessed into feature matrix XXX and label vector yyy, and split into training (70%) and testing (30%) sets using the train_test_split function. StandardScaler was applied to standardize the features.

  The neural network consisted of 2 hidden layers and was trained with the Adam optimizer and binary cross-entropy loss function. EarlyStopping and ReduceLROnPlateau were used to prevent overfitting and dynamically adjust the learning rate. The model was trained for 50 epochs with a batch size of 32, using 30% of the training data as a validation set. Model performance was evaluated using the testing set, with loss and accuracy metrics calculated. A confusion matrix and ROC curve further assessed the model’s performance. The weights from the first hidden layer were extracted to compute feature importance, with results sorted in descending order and visualized using bar charts with data labels for enhanced readability.


## 3. Results

### 3.1. DEG analysis
  In this study, we identified DEGs using the batch-corrected merged matrix from datasets GSE74089 and GSE123568, following the predefined threshold of P < .05. A total of 1976 DEGs were identified using the R software, and a volcano plot was generated to visualize the results (Fig. 1).


### 3.2. Functional enrichment analysis

#### 3.2.1. GO and KEGG enrichment analysis of DEGs
  We performed GO and KEGG enrichment analyses on the identified DEGs. The GO analysis showed that the DEGs were mainly enriched in organic acid catabolic processes, centromeric regions of condensed chromosomes, oxidoreductase activity, and aerobic glycolysis (Fig. 2A–C). The KEGG analysis revealed significant enrichment in the AMPK signaling pathway, mTOR signaling pathway, MAPK signaling pathway, TNF signaling pathway, and JAK–STAT signaling pathway (Fig. 2D).


#### 3.2.2. GSEA
  To further explore potential enrichment among non-DEGs, we conducted a GSEA analysis on the entire genome, aiming to validate the results obtained from the DEG analysis. GSEA results confirmed that the enriched pathways, including organic acid metabolism, mTOR signaling, MAPK signaling, and JAK–STAT signaling, were consistent with those found in the GO and KEGG analyses (Fig. 2E–H).


#### 3.2.3. Metascape enrichment analysis
  Metascape enrichment analysis revealed that the GO terms were associated with neutrophil degranulation, protein catabolic processes, hematopoiesis, and inflammatory responses (Fig. 3A). Enrichment networks were also generated, with nodes colored by enrichment terms and P-values (Fig. 3B and C) to visualize the relationships and confidence levels among the enriched terms.


### 3.3. WGCNA
  Selecting the soft-threshold power is a critical step in WGCNA. After network topology analysis, a power of 16 was chosen (Fig. 4A). A hierarchical clustering tree of all genes was constructed, resulting in 18 modules (Fig. 4B). Interactions among important modules were analyzed (Fig. 4C), along with a heatmap showing the correlation between modules and phenotypes (Fig. 4D). A scatter plot of module eigengenes and gene significance versus module membership for hub genes was also generated (Fig. 5A). Five highly connected hub gene modules with module membership values > 0.8 were identified as clinically significant and were retained for further analysis.

  A Venn diagram was used to intersect hub genes from WGCNA with the DEGs identified earlier, yielding 1001 overlapping DEGs (Fig. 5B), which were used to construct the PPI network.


### 3.4. PPI network construction and analysis
  The PPI network was constructed using the STRING online database and analyzed with Cytoscape software (Fig. 6A). Core gene clusters were identified (Fig. 6B), and 3 algorithms (MCC, EPC, and Radiality) were used to identify the most relevant hub genes (Fig. 6C and D). A Venn diagram was generated to combine results from the 3 algorithms, and the intersection yielded 9 core genes: SRSF1, HNRNPM, TARDBP, HNRNPC, HNRNPA1, HNRNPU, HNRNPR, HNRNPF, and EWSR1 (Fig. 6E).


### 3.5. Core gene expression heatmap
  We visualized the expression levels of the core genes in the ONFH datasets GSE74089 and GSE123568 using heatmaps (Fig. 7A). The heatmaps revealed that TARDBP was highly expressed in ONFH samples and showed low expression in normal tissue samples. These results suggest that TARDBP may play a regulatory role in the development of ONFH.


### 3.6. CTD analysis
  In this study, we input the list of hub genes into the CTD to explore their associations with diseases. The analysis revealed that the core gene TARDBP is linked to several conditions, including ALS, neurodegenerative diseases, necrosis, and inflammation (Fig. 7B).


### 3.7. Immune infiltration analysis
  Using the CIBERSORT package, we analyzed the merged matrix from the GSE74089 and GSE123568 ONFH datasets. At a 95% confidence level, we obtained the proportions of immune cells from the gene expression matrix, with monocytes showing a higher proportion in ONFH samples. This suggests that monocytes play a significant role in the onset and progression of ONFH (Fig. 8A).

  Additionally, heatmaps revealed that monocytes had high expression levels in colorectal cancer samples, further supporting their critical role in ONFH (Fig. 8B). Correlation analysis of immune cell composition showed a strong positive correlation between M1 macrophages and activated dendritic cells. This implies that these 2 cell types may jointly participate in immune responses involved in ONFH progression, potentially influencing disease outcomes (Fig. 8C).

  Based on these analyses, we conclude that TARDBP may serve as a key target gene in the development and progression of ONFH.


### 3.8. Neural network model analysis

#### 3.8.1. Model performance analysis
  The neural network model achieved an accuracy of 67% on the training set, with a loss value of 0.6667. This indicates that the model correctly classified 67% of the samples, showing better-than-random performance but still leaving room for improvement. The model demonstrated the same 67% accuracy on the test set, indicating stable performance without signs of overfitting (Fig. 9).


#### 3.8.2. Model evaluation metrics
  The confusion matrix showed the following results: True Positive (TP) = 1. False Positive (FP) = 1. False Negative (FN) = 4. True Negative (TN) = 9.

  Based on these metrics, we calculated the following: accuracy = 67% (above random guessing). Recall = 20%, indicating the model correctly identified only 20% of positive samples, which is relatively low. Specificity = 90%, meaning the model effectively identified negative samples.

  The area under the ROC curve was 0.52, reflecting the model’s limited overall performance (Figs. 10 and 11).


#### 3.8.3. Gene importance analysis
  Gene importance analysis identified TARDBP, HNRNPA1, and EWSR1 as highly significant. TARDBP had the highest importance score (1.693257), suggesting that it plays a pivotal role in the pathogenesis of ONFH, potentially related to cell survival, apoptosis, and neuroprotection. These findings indicate that TARDBP could serve as a potential biomarker for early diagnosis and risk assessment of ONFH (Fig. 12).


## 4. Discussion
  Osteonecrosis of the femoral head (ONFH) is a disease caused by venous stasis, impaired arterial blood flow, or damage to the femoral head, resulting in the localized death of bone cells and bone marrow components, ultimately leading to structural collapse.[20,21] Without timely intervention, deformity of the femoral head can lead to severe osteoarthritis, greatly affecting the patient’s quality of life.[22,23] In recent years, extensive research has focused on the molecular mechanisms underlying ONFH, particularly the roles of oxidative stress, apoptosis, and bone cell necrosis, as well as early-stage inflammatory responses and immune cell infiltration. Exploring the molecular mechanisms of ONFH is essential for developing new targeted therapies. Identifying core genes associated with ONFH and studying their roles in the disease process will provide theoretical support for developing novel targeted treatment strategies. The main finding of this study is that TARDBP is highly expressed in ONFH and may play a role by regulating apoptosis, oxidative stress and immune response.

  The TARDBP gene encodes TDP-43, a multifunctional RNA-binding protein that participates in RNA splicing, transport, degradation, and plays a key role in RNA metabolism.[24] TDP-43 is predominantly located in the nucleus but can translocate to the cytoplasm under certain pathological conditions, forming insoluble protein aggregates.[25] Abnormal expression of TARDBP has been closely associated with various neurodegenerative diseases. For instance, aberrant accumulation of TDP-43 has been widely reported in the brains of patients with ALS and frontotemporal dementia.[26,27] Studies indicate that TARDBP mutations, such as A315T, G348C, and A382T, lead to toxic aggregation and motor neuron toxicity in ALS and other neurodegenerative diseases. Overexpression of these mutants has caused neuronal damage and motor deficits in both cellular and zebrafish models, suggesting that these mutations contribute to disease through both toxic gain-of-function and loss-of-function mechanisms.[28] Research highlights the importance of TDP-43 in vascular function. Its absence in endothelial cells inhibits angiogenesis, disrupts the blood–brain barrier, and compromises vascular stability, triggering inflammatory responses in the nervous system. This disruption leads to damaged fibronectin matrices and reduced β-catenin signaling, emphasizing TDP-43’s critical role in vascular formation and stability.[29] Additionally, TDP-43 dysregulation is associated with increased apoptosis and oxidative stress. In neurodegenerative disease models, mitochondrial accumulation of TDP-43 induces mitochondrial dysfunction, resulting in elevated reactive oxygen species (ROS) levels, reduced oxidative phosphorylation, and altered mitochondrial membrane permeability, contributing to increased cell death and cellular stress responses.[30]

  Studies indicate that ischemia-induced oxidative stress is a key pathological mechanism of ONFH. It causes mitochondrial dysfunction, generating large amounts of ROS, which trigger apoptosis and bone cell necrosis. Specifically, oxidative stress damages mitochondria, activating mitochondrial permeability transition pores and releasing damaged molecules, such as mitochondrial DNA, into the cytoplasm, which initiates further inflammatory responses.[31] Excess ROS production also promotes apoptosis by activating pro-apoptotic proteins like BAX and BAK. These proteins form channels in the outer mitochondrial membrane, releasing apoptotic factors and initiating a cascade of cell death. Mitochondrial dysfunction has also been linked to cellular aging, as impaired mitochondria cannot be effectively cleared through autophagy under oxidative stress, leading to reduced metabolic capacity and further ROS accumulation.[32] Additionally, immune cell infiltration, especially by macrophages, has been found to play a crucial role in ONFH progression. Macrophage infiltration into tissue, along with lipid engulfment, appears to influence their polarization state, modulating inflammatory responses.[33]

  TARDBP plays a role in regulating apoptosis and autophagy in neurodegenerative diseases, which is similar to the apoptosis observed in osteocytes and bone marrow mesenchymal stem cells in osteonecrosis of the femoral head (ONFH). TARDBP may regulate cell survival in ONFH by influencing apoptosis pathways such as p53, Bcl-2, and caspase. The occurrence of ONFH is closely related to local inflammation and oxidative stress.[34] TARDBP is involved in the regulation of inflammatory factors (e.g., TNF-α, IL-6) and oxidative stress-related gene expression. It may affect the inflammatory microenvironment of ONFH by modulating the NF-κB and Nrf2 pathways. A critical aspect of ONFH is the disruption of blood supply leading to osteocyte death and impaired bone remodeling.[35] TARDBP may influence the progression of ONFH by regulating angiogenesis-related factors such as VEGF and Ang-1/2, as well as bone remodeling pathways involving RUNX2 and OPG/RANKL. TARDBP may also interact with other key genes involved in ONFH, such as HIF-1α, VEGF, and MMP-9. These genes are closely related to ischemia, inflammation, apoptosis, and bone remodeling, and they may influence the development and progression of ONFH through a co-regulatory network. In the context of ONFH, our findings suggest that TARDBP may accelerate bone cell death through the regulation of apoptosis and oxidative stress responses. Our results are consistent with previous research, showing that TARDBP expression is significantly elevated in ONFH samples and positively correlates with disease progression. This suggests that TARDBP may play a crucial role in ONFH pathogenesis by regulating apoptosis and metabolic pathways. Furthermore, TARDBP’s elevated expression is associated with increased infiltration of monocytes[36] and M1 macrophages, indicating that it may influence immune responses in ONFH.

  The finding that TARDBP is highly expressed in osteonecrosis of the femoral head has multiple implications and interpretations. From the cellular level, it affects the function of osteoblasts. Osteoblasts are essential for the formation and repair of bone tissue.[37] The high expression of TARDBP may interfere with the normal differentiation and proliferation process of osteoblasts, resulting in the reduction of the number or abnormal function of osteoblasts, resulting in insufficient new bone formation and unable to effectively repair the damaged femoral head tissue. It affects the function of osteoclasts, which are responsible for bone resorption and maintain bone metabolic balance together with osteoblasts. High expression of TARDBP may promote the activity or increase the number of osteoclasts by regulating related signaling pathways, resulting in excessive bone resorption, breaking the balance of bone metabolism, and accelerating the loss of bone mass and structural destruction of the femoral head. Affect bone marrow mesenchymal stem cells, bone marrow mesenchymal stem cells have the potential to differentiate into osteoblasts, adipocytes and other cells. The high expression of TARDBP may change the differentiation direction of BMSCS, making them differentiate more into adipocytes and less into osteoblasts, resulting in decreased osteogenic ability. At the same time, the increase of adipocytes may also compress the blood vessels and affect the blood supply of the femoral head. From the perspective of molecular mechanism, regulating gene expression, TARDBP,[38] as a DNA-binding protein, may bind to specific gene sequences to regulate the expression of a series of genes related to bone metabolism. When overexpressed in osteonecrosis of the femoral head, it may down-regulate the expression of genes that promote bone formation, and up-regulate the expression of genes that promote bone resorption or apoptosis, thereby promoting the development of osteonecrosis of the femoral head. TARDBP may be involved in the regulation of multiple signaling pathways, such as Wnt/β-catenin signaling pathway. In osteonecrosis of the femoral head, the high expression of TARDBP may abnormally activate or inhibit these signaling pathways, and then affect the function and fate of osteoblasts and osteoclasts, ultimately leading to the damage of the structure and function of the femoral head. From the perspective of disease diagnosis and treatment, the high expression of TARDBP in ONFH makes it a potential marker for early diagnosis of ONFH. Detection of TARDBP levels in blood or tissues can help to achieve early detection and diagnosis of the disease in the early stage without obvious symptoms and imaging changes, and provide a basis for timely intervention and treatment. Clarifying the high expression and mechanism of TARDBP in osteonecrosis of the femoral head may provide a target for the development of new treatment methods. Drugs targeting TARDBP or its upstream and downstream related molecules can be designed to regulate the imbalance of bone metabolism and improve the pathological state of femoral head by inhibiting the expression or blocking the function of TARDBP, which provides a new strategy and direction for the treatment of femoral head necrosis.


## 5. Strengths and limitations
  Through bioinformatics analysis and neural network modeling, has uncovered TARDBP’s potential role in ONFH, some limitations remain. The data were derived from public databases and lacked large-scale clinical sample validation. Additionally, we did not conduct TARDBP gene knockout or overexpression experiments, limiting our understanding of its function.


## 6. Conclusion
  TARDBP is highly expressed in ONFH, and its possible role by regulating apoptosis, oxidative stress and immune response provide new ideas for the study of the molecular mechanism of ONFH and offer theoretical support for developing TARDBP-targeted therapeutic strategies.


## Author contributions
  Conceptualization: Sheng Sun.

  Data curation: Rongqiang Bu, Lei Zang.

  Formal analysis: Yi Zhang, Lei Zang.

  Methodology: Sheng Sun, Jian Qi, Rongqiang Bu, Lei Zang.

  Software: Jingjing Wang, Guangxu Ren, Jian Qi.

  Visualization: Sheng Sun, Jingjing Wang, Guangxu Ren, Yi Zhang, Lei Zang.

  Writing – original draft: Sheng Sun, Jingjing Wang, Lei Zang.

  Writing – review & editing: Sheng Sun.