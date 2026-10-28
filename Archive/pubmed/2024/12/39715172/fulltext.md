# Unveiling the intricate interplay: Exploring biological bridges between renal ischemia-reperfusion injury and T cell-mediated immune rejection in kidney transplantation


## Abstract
  Although the link between ischemia-reperfusion injury (IRI) and T cell-mediated rejection (TCMR) in kidney transplantation (KT) is well known, the mechanism remains unclear. We investigated essential genes and biological processes involved in interactions between IRI and TCMR. Methods: Renal IRI and TCMR datasets were obtained from the Gene Expression Omnibus database. IRI and TCMR co-expression networks were built using weighted gene co-expression network analysis, and essential modules were identified to acquire shared genes and conduct functional enrichment analysis. Shared genes were used for TCMR consensus clustering, differentially expressed genes (DEGs) were identified, and gene set enrichment analysis (GSEA) was conducted. Three machine learning algorithms screened for hub genes, which underwent miRNA prediction and transcription factor analysis. Hub gene expression was verified, and survival analysis was performed using Kaplan–Meier curves. Results: IRI and TCMR shared 84 genes. Functional enrichment analysis revealed that inflammation played a significant role. Based on shared genes, TCMR was divided into two clusters. GSEA revealed that graft rejection-related pathways varied between the two clusters. TCMR hub genes, guanylate-binding protein 1 (GBP1) and CD69, showed increased expression. Decreased survival rates were found in patients who had undergone KT and had high GBP1 and CD69 levels. Conclusions: The study demonstrates that renal IRI has a potential role in renal TCMR and the pathogenic pathways are potentially inflammation-related.


## Introduction
  Kidney transplantation (KT) is the primary therapeutic choice for patients with end-stage kidney disease to improve survival and quality of life. However, improving graft tolerance and extending graft survival remain the major challenges in KT. Acute T cell-mediated rejection (TCMR) is a severe clinical concern during the early phase of KT. TCMR is less concerning than antibody-mediated immune rejection because it is curable and uncommon six years post-transplantation [1]. However, Ho et al. discovered a significant prevalence of persistent TCMR in grafts [2]. Meanwhile, Mizera et al. suggested that chronic active TCMR is a contributor to KT graft loss [3], and TCMR was shown to be associated with kidney graft fibrosis [4]. In addition, graft loss has been linked to TCMR in young patients who have undergone KT [1]. According to Rampersad et al., the first occurrence of TCMR is related to a higher risk of all-cause graft loss [5]. Moreover, a prospective study showed that the combination of delayed graft function and TCMR significantly contributed to graft loss [6]. Therefore, investigating the mechanisms of TCMR is critical.

  Ischemia-reperfusion injury (IRI) is an unavoidable and harmful condition caused by graft acquisition, preservation, and blood supply recovery during KT. Renal IRI is closely linked to a decline in graft survival and the emergence of acute rejection (AR) [7]. Significant advances have been made in understanding the pathogenic mechanisms of IRI. Excessive reactive oxygen species cause oxidative phosphorylation in renal IRI. IRI also activates the complement system in the kidneys [8]. Several mechanisms of cellular demise, encompassing ferroptosis, pyroptosis, and necroptosis, participate in the pathogenesis of IRI. Furthermore, neutrophil recruitment is an important inflammatory mechanism in acute kidney injury (AKI) caused by IRI [9].

  The potential mechanisms underlying IRI and TCMR are related to the stimulation of T cell migration, production of inflammatory molecules such as damage-associated molecular patterns, and tumor necrosis factor (TNF) [7]. However, further research into the precise mechanisms is required to advance efforts to increase graft survival in patients undergoing KT. Exploring the probable mechanisms of IRI and TCMR will grant a better understanding of the incidence of KT rejection and guide research in KT therapy and prevention. Thus, we used a bioinformatics approach to explore the potential mechanisms and hub genes involved in IRI and TCMR. The flowchart of the research is shown in Fig 1.


## Methods

### Dataset acquisition
  Renal IRI and TCMR datasets were collected from the Gene Expression Omnibus database; the details of these datasets are shown in Table 1.


### Weighted Correlation Network Analysis (WGCNA)
  WGCNA is a systems biology approach for elucidating gene connection patterns. To exclude outlier data, the expression matrix was first checked for missing values before clustering genes with comparable gene expression patterns. Second, a soft threshold β was chosen based on scale-free network requirements, and the adjacency matrix was turned into a topological overlap matrix for hierarchical clustering. A dynamic shearing method was used to identify modules, and comparable modules were clustered and merged. The minimum number of genes in the module was set to 50, and modules with an Eigen factor greater than 0.75 were merged. Finally, the disease correlation, module membership, and gene significance of each module were calculated, and the key modules with the highest correlations were chosen for further analysis [10].


### Identification of Differentially Expressed Genes (DEGs)
  The R software (4.2.2) "limma" package was used to identify different subtypes of TCMR DEGs. Genes with adjusted p-values < 0.05 and a log fold change (logFC) > 0.5 were identified as DEGs.


### Functional analysis of shared genes
  The protein-protein interaction (PPI) network was built using the STRING (v11.5) database platform. Gene ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment analysis were performed for shared genes. GO analysis provides information on biological processes, molecular functions, and cellular components of genes. KEGG pathway enrichment analysis provides insights into the associated pathways in which the shared genes are involved. Gene set enrichment analysis (GSEA) was used to analyze the different potential biological mechanisms between the two TCMR clusters. An adjusted-p < 0.05 was considered significant.


### Consensus clustering
  The "ConcensusClusterPlus" package was used to perform consensus clustering. The number of clusters was set between 2 and 6, and the process was repeated 50 times to extract 80% of the total sample using clusterAlg = "hc" and distance = "pearson" [11].


### Screening of hub genes
  The least absolute shrinkage and selection operator (LASSO), support vector machine recursive feature elimination (SVM-RFE), and random forest analysis were performed to identify hub genes. LASSO is a regression analysis method that permits variable screening while fitting a generalized linear model. SVM-RFE is a supervised learning model that can be used to analyze data in classification and regression analysis. Random forest is an integrated learning method that produces predictions without considerable bias by training with numerous decision trees. The LASSO regression analysis was carried out using the "glmnet" package in R software (4.2.2). Random forest analysis was performed using the "randomForest" package. SVM-RFE analysis was performed with the "e1071" package.


### Regulation mechanism prediction
  Regulatory miRNAs of hub genes were predicted using TarBase v8.0, and transcription factors (TFs) were predicted using the ENCODE database on the NetworkAnalyst platform. Co-expression networks of mRNAs with predicted TFs and miRNAs were constructed using the Cytoscape software (v3.9.1).


### Validation of hub genes
  In the GSE129166 dataset, the expression of hub genes was confirmed by the Student’s t-test. The groups were divided into high- and low-expression groups according to the median expression of hub genes in the GSE21374 dataset. The "survival" package was used to investigate survival differences between the high- and low-expression hub genes. Significance was set at p < 0.05.


## Results

### Screening of renal IRI and TCMR Co-expression modules
  In the GSE43974, GSM1075318, GSM1075418, and GSM1075263 datasets were poorly clustered, and the outlier samples were removed. To construct the scale-free network, the scale-free fit index was set at 0.9, and the soft threshold β was 3. Among 21 identified models, module black had the highest correlation with IRI and was the most relevant module (r = 0.81, p = 2e-93), with a total of 739 genes (Fig 2A and 2B).

  In the GSE36059, GSM880323, GSM880570, GSM880576, GSM880265, GSM880280, GSM880242, GSM880298, GSM880362, and GSM880394 datasets were poorly clustered, and the outlier samples were removed. To construct the scale-free network, the scale-free fit index was set at 0.9, and the soft threshold β was 7. Among 19 identified modules, module black had the highest correlation with TCMR and was the most relevant module (r = 0.47, p = 7e-18), with a total of 1,494 genes (Fig 2C and 2D).


### Functional characteristics of shared genes
  In the IRI- and TCMR-related modules, 84 shared genes were used to build the PPI network (Fig 3A and 3B). GO analysis showed that these genes were involved in the viral response, inflammatory response regulation, cell-cell adhesion regulation, and cytokine-mediated signaling pathways, among others (Fig 3C). KEGG analysis suggested the shared genes were involved in the TNF signaling pathway, lipid- and atherosclerosis-related pathway, nucleotide oligomerization domain (NOD)-like receptor signaling pathway, interleukin (IL)-17 signaling pathway, and advanced glycation end products (AGE)-receptors for the AGE signaling pathway in diabetic complications (Fig 3D).


### Consensus clustering
  In the present study, TCMR was clustered based on gene sharing. Ultimately, k = 2 had the optimal number of clusters, and the TCMR samples were divided into two clusters, C1 (n = 15) and C2 (n = 20) (Fig 4A and 4B). Between clusters C1 and C2, 782 DEGs were identified, of which 743 genes were upregulated and 39 genes were downregulated (Fig 4C and 4D). GSEA revealed differences in the gene set expression of the graft rejection-related pathways between the two clusters (Fig 4E and 4F). Furthermore, the expression of AR markers was elevated in cluster C2, compared with that in C1 (Fig 5).


### Machine learning to screen hub genes
  Random forest analysis was performed on shared genes, and the top 15 most important genes were selected (Fig 6A and 6B). The model with nine genes had the lowest error rate and the highest accuracy, according to SVM-RFE analysis (Fig 6C and 6D). LASSO regression model analysis screened 13 genes (Fig 6E). Finally, the intersection of the hub genes screened by the three machine learning methods was used to obtain two genes, CD69 and guanylate-binding protein 1 (GBP1) (Fig 6F).


### Regulation mechanism prediction
  Regulatory miRNAs common to GBP1 and CD69 included hsa-mir-26a-5p, hsa-mir-128-3p, and hsa-mir-10b-5p, whereas common TFs included CCAAT/enhancer binding protein gamma (C/EBPG) (Fig 7A and 7B).


### Validation of hub genes
  The expression of the hub genes GBP1 and CD69 was verified in the GSE129166 dataset. The expression levels of GBP1 and CD69 were elevated in the TCMR group (Fig 8A and 8B). Based on the median GBP1 and CD69 expression, the KT samples in the GSE21374 dataset were classified into high- and low-expression groups. Patients who had undergone KT and had high GBP1 and CD69 expression levels experienced lower survival rates (Fig 8C and 8D).


## Discussion
  GBP1 is a GTPase primarily induced by interferon-γ (IFN-γ) and involved in processes such as infection and inflammation. Wang et al. found that GBP1 knockdown inhibited Bacillus Calmette-Guerin-induced apoptosis in macrophages [12]. In addition, GBP1 protects against dengue virus [13]. Pyroptosis is a significant mechanism of renal IRI [14], and GBP1 is a key protein involved in inflammatory pyroptosis [15]. C/EBP homologous protein/caspase-11 can induce renal tubular pyroptosis [16]. In renal tubular epithelial cells (TECs), Tisp40 can also induce gasdermin D-mediated pyroptosis, and the potential mechanism is related to nuclear factor-κB signaling [17]. In terms of KT, Chauveau et al. showed that GBP1 contributes to the diagnosis of antibody-mediated immune rejection [18]. In cardiac transplantation, CD69 has been shown to help with the identification of rejection [19]. CD69 is a marker of tissue-resident memory T cells. Recipient tissue-resident memory T cells are involved in allograft immune responses in KT and are associated with the secretion of TNF-α and IFN-γ [20]. Renal IRI can lead to the long-term infiltration of activated and effector memory T lymphocytes [21]. The continuous exposure of resident memory T cells to antigens leads to allograft rejection [22]. CD69 expression in peripheral blood CD3+ and CD8+ T cells is correlated with AR in patients who have undergone KT [23]. Conversely, it has been suggested that CD69 does not play a role in rejection recognition in KT [24]. Further research is needed to determine whether CD69 and GBP1 expression can be considered markers for KT rejection.

  Furthermore, TCMR could be divided into two subgroups based on genes shared by IRI and TCMR, allowing a comparison of the expression of 18 AR markers between the two subgroups [25]. The serum levels of CXCL10, which is widely expressed in chronic allograft nephropathy tissues, help predict graft loss [26]. Ischemia promotes AR by inducing CXCR3 expression, which is associated with inflammatory cell recruitment [27]. Expression levels of granzyme B and Fas ligand were elevated in both the tissue and peripheral blood of patients with AR rejection [28]. The levels of AR markers were higher in the C2 subgroup than in the C1 subgroup. These results suggest that IRI potentially impacts TCMR, and genes shared between IRI and TCMR are important in TCMR.

  The inflammatory response plays a significant role in renal IRI and TCMR. Patients with TCMR and glomerulonephritis have poor graft survival [29]. TNF-α induces renal tubular apoptosis in patients with renal IRI, resulting in renal atrophy [30]. Furthermore, TNF-α gene silencing dramatically reduces IRI damage in the liver and kidneys [31]. In KT, TNF-α can target the protein kinase B signaling pathway to induce the epithelial mesenchymal transition in renal TECs, leading to interstitial fibrosis [32]. IL-17 can enhance neutrophil recruitment in kidney IRI [33], and in patients with KT TCMR, increased IL-17 expression has been associated with poorer treatment outcomes [34]. Moreover, during heart transplantation, hyperlipidemia can enhance rejection by increasing IL-17 expression [35]. Activation of the NOD-like receptor protein 3 (NLRP3) inflammasome promotes caspase 1-mediated IL-18 and IL-1β production and is a promising therapeutic target for organ IRI [36]. NLRP3 activation in IRI is associated with mitochondrial reactive oxygen species [37]. In terms of regulatory miRNAs, miR-26a-5p has been shown to protect against brain and myocardial IRI [38] and alleviate sepsis-induced AKI via IL-6 [39]. miR-128-3p targets neuropilin-1 and promotes inflammatory responses in sepsis-induced AKI [40]. However, Xie et al. found that the downregulation of miR-128-3p expression in an IRI-AKI model reversed the reduction in apoptosis caused by LINC00963 knockdown [41]. miR-25-3p inhibits IRI-induced apoptosis in renal TECs [42]. miR-27a, whose target is Toll-like receptor 4, inhibits inflammatory responses in renal IRI [43]. Taken together with our results, these pathways provide promising therapeutic targets for the treatment of IRI and TCMR in KT.

  The present study had some shortcomings. First, further experimental investigations on the precise molecular pathways implicated by the hub genes (GBP1 and CD69) are required. Second, the clinical data were insufficient to determine the relationship between the hub genes, renal function, and pathological damage. Finally, clinical studies with larger sample sizes are warranted.