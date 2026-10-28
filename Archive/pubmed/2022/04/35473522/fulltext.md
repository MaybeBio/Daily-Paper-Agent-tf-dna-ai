# Identification of Key Diagnostic Markers and Immune Infiltration in Osteoarthritis


## Abstract
  Background: Osteoarthritis (OA) is a worldwide chronic disease of the articulating joints. An increasing body of data demonstrates the immune system's involvement in osteoarthritis. The molecular mechanisms of OA are still unclear. This study aimed to search for OA immune-related hub genes and determine appropriate diagnostic markers to help the detection and treatment of the disease.

  Methods: Gene expression data were downloaded from the GEO database. Firstly, we analyzed and identified the differentially expressed genes(DEGs)using R packages. Meanwhile, ssGSEA was used to determine the activation degree of immune-related genes (IRGs), and WGCNA analysis was applied to search for co-expressed gene modules associated with immune cells. Then, critical networks and hub genes were found in the PPI network. Gene Ontology (GO) annotation and Kyoto Encyclopedia of Gene and Genomes (KEGG) pathway enrichment analyzed the biological functions of genes. The ability of the hub genes to differentiate OA from controls was assessed by the area under the ROC curve. A miRNA and transcription factor (TF) regulatory network was constructed according to their relationship with hub genes. Finally, the validation of hub genes was carried out by qPCR.

  Results: In total, 353 DEGs were identified in OA patients compared with controls, including 222 upregulated and 131 downregulated genes. WGCNA successfully identified 34 main functional modules involved in the pathogenesis of OA. The most crucial functional module involved in OA included 89 genes. 19 immune-related genes were obtained by overlapping DEGs with the darkgrey module. The String database was constructed using the protein-protein interaction (PPI) network of 19 target genes, and 7 hub genes were identified by MCODE. ROC curve showed that 7 hub genes were potential biomarkers of OA. The expression levels of hub genes were validated by qPCR, and the results were consistent with those from bioinformatic analyses.

  Conclusion: Immune-related hub genes, including TYROBP, ITGAM, ITGB2, C1QC, MARCO, C1QB, and TLR8, may play critical roles in OA development. ITGAM had the highest correction on immune cells.


## INTRODUCTION
  Osteoarthritis (OA) is a highly prevalent, age-dependent joint disease, particularly among older people with multiple comorbid illnesses [1]. It is regarded as a multifactorial disease, with common risk factors including age, excess, mechanical loading, and metabolic syndrome [2]. Bone destruction, synovial hyperplasia, osteophyte formation and subchondral bone sclerosis are the main features of osteoarthritis, and the typical symptom is severe joint pain [3]. Specifically, knee osteoarthritis is a painful disease and substantially decreases the life quality of suffered patients [4]. Consequent to unprecedented global population aging, osteoarthritis remains a leading cause of disability, and the treatment often comes at a high cost [5], imposing an enormous economic burden worldwide. Unfortunately, few effective disease-modifying therapies are available due to the unknown etiology and pathological mechanisms. As a consequence, identifying new and effective treatments is vital to improve osteoarthritis outcomes and guide clinical management.

  Cumulating evidence supports the pathological roles of immune and inflammatory in the occurrence and development of osteoarthritis [6, 7]. Some studies proposed that altered gene expression in chondrocytes osteoarthritis progression by regulating immune responses [8, 9]. Pro-inflammatory cytokines play a central role in chondrocyte apoptosis and cartilage matrix proteolysis and thus may be implicated in the pathogenesis of osteoarthritis [10]. Previous studies showed that the extent of immune dysregulation significantly correlates with the severity of osteoarthritis, revealing an association between immunity response and clinical manifestations [11]. Therefore, exploring immune infiltration and related diagnostic gene markers in OA will provide a deeper understanding of the pathogenesis of osteoarthritis.

  In this study, with the aid of Gene Expression Omnibus (GEO) and bioinformatics, we aimed to describe the characteristics of infiltrating immune cells in osteoarthritis tissues, and comprehensive bioinformatics analyses were performed to explore underlying hub genes. Besides, we constructed a gene-TF-miRNA co-regulatory network according to the relationship among hub genes, TF, and miRNA by bioinformatics methods.


## MATERIALS AND METHODS

### Data Source
  The RNA expression datasets of OA were obtained from Gene Expression Omnibus (GEO) database (https://www.ncbi.nlm.nih.gov/geo/). The gene expression profiles of human knee osteoarthritis tissues were downloaded from GSE114007 (20 OA patients and 18 control individuals) and GSE143514 (5 OA patients and 3 control individuals) for training (Training Set), respectively. The gene expression profiles for validation (Validation Set) were downloaded from GSE98918 (12 OA patients and 12 control individuals).


### Acquirement of Differentially Expressed Genes (DEGs)
  Generally, all microarray data after normalization were analyzed by R software. After removing interbatch differences, R package “DESeq2” was used to identify differentially expressed mRNAs between OA and control samples with ∣log2FC| >1 and adj.P.Val < 0.05 as the threshold. The DEGs' heatmap cluster and volcano plots were created using the “heatmap” and “ggplots” packages via R software.


### Functional Annotation and Pathway Enrichment Analysis
  GO annotation and KEGG enrichment analysis were performed using the “clusterProfiler” package to reveal the functions of DEGs. The GO functions include biological processes, cellular components, and molecular functions. The KEGG pathway analysis was prone to describe gene function at the genomic and molecular levels and show the correlated genes. P < 0.05 was considered statistically significant.


### Infiltration of Immune Cells
  The GEO gene expression profile data were used to quantify the infiltration of immune cells in knee tissues by ssGSEA (Single-sample gene set enrichment analysis), and the infiltration of 28 immune cells was obtained. Each resulting ssGSEA score represents the degree to which the genes in a particular gene set are co-ordinately up or downregulated in each sample in the dataset. The ssGSEA ranked the genes by their absolute expression in a sample, and the enrichment score was calculated by an integration of the differences between the empirical cumulative distribution functions. Furthermore, we performed Spearman correlation analysis on infiltrating immune cells and gene expression by the “ggpubr” package.


### WGCNA
  The WGCNAR package was used for weighted gene co-expression network analysis on the GEO expression file. Firstly, samples were clustered to assess the presence of any outliers. Then, the automatic network construction function was used to get the co-expression network. The pickSoftThreshold was used to calculate the soft thresholding power β. Furthermore, hierarchical clustering and the dynamic tree cut function were used to detect different modules. Finally, the Pearson correlation coefficient between the sample vector of variables and the characteristic gene of the module was calculated to measure the degree of association between the clinical features and the modules. We then found out which module of immune cell genes was the most relevant in OA.


### Protein-protein Interaction (PPI) Network Construction
  Analysis of the functional interactions between proteins could provide essential insights into the progression of OA. We constructed the PPI network by STRING database (https://string-db.org/). A combined score of >0.4 was considered significant. Cytoscape performed the visualized PPI network. MCODE was used to screen the significant modules in the PPI network. The genes with the highest degree of connectivity in the module were considered hub genes. They were expected to exhibit higher biological significance than the other gene members of the module.


### Validation of Hub Genes
  The expression levels of hub genes were uesd to verify whether the hub genes were essential to OA. The “pROC” package was used to perform ROC curve analysis to evaluate the diagnostic value of hub genes for OA, and the area under the curve (AUC) was then computed. The higher the AUC value was, the better the ability of the gene to distinguish whether the sample was diseased or not. The genes with AUC > 0.7 were considered diagnostic genes of OA.


### Correlation Analysis between Hub Genes and Infiltrating Immune Cells
  The “ggpubr” package was used to perform Spearman correlation analysis on hub genes and infiltrating immune cells,and the “ggplot2” package was used to visualize the results.


### Multi-factor Regulation Network Construction
  We used NetworkAnalyst (https://www.networkanalyst.ca/) and miRNet databases (https://www.mirnet.ca/) to predict the TFs and miRNAs of hub genes. The data of hub genes and their TFs and miRNAs were integrated into a regulatory network and visualized using Cytoscape software.


### RT-PCR Validation of the Hub Genes
  To confirm the results of bioinformatics analysis, cartilage tissues of OA patients undergoing knee replacement and normal patients were collected for RT-PCR validation. The study protocol was approved by the Ethics Committee of The Affiliated Hospital of Qingdao University (approval number: QYFY WZLL 26788), and all patients signed the informed consent for tissue collection.

  Total RNA of cartilage tissue was extracted with TRIzol reagent (Invitrogen, USA). Those RNA samples were reverse transcribed to cDNA with the PrimeScript RT reagent Kit and subsequently amplified using the TB Green Premix Ex Taq II kit (TaKaRa, Japan). Primer sequences of mRNA were shown in Table 1. The primers of all mRNAs were purchased from ThermoFisher (USA). The gene expression was normalized for GAPDH levels and calculated using the 2−ΔΔCt method. P < 0.05 indicated a significant difference.


## RESULTS

### Identification of Differentially Expressed Genes (DEGs)
  First, the batch effect was removed from the gene expression matrix after merging the GSE114007 and GSE143514 datasets. Then we used the “DESeq2” package to extract a total of 353 DEGs (Supplementary File 1), including 222 downregulated genes and 131 upregulated genes, which were shown in volcano plots (Fig. 1A). The top 10 upregulated and downregulated DEGs in the visualized heatmap were sorted by the log2FC of DEGs (Fig. 1B).


### GO Annotation and KEGG Pathway Enrichment Analysis of the DEGs
  To obtain the functions of these 353 DEGs, GO annotation and KEGG enrichment analysis were conducted using the “clusterProfiler” package. For GO biological process, the DEGs were mainly enriched in regulating the immune effector process, T cell activation, and cell−cell adhesion. In the cellular component, the DEGs were mainly enriched in the collagen-containing extracellular matrix, endocytic vesicles, and the external side of the plasma membrane. The top three significantly enriched terms were receptor ligand activity, signaling receptor activator activity, and amide binding in the molecular function group (Fig. 2A). Besides, the top ten GO terms in each group are listed in Table 2. The result of the KEGG pathway enrichment analysis is shown in Fig. (2B). Leishmaniasis, Staphylococcus aureus infection, and Hematopoietic cell lineage were highly associated with OA. The above results indicated that the DEGs were mainly related to immune-related functions. Additionally, the top ten pathways are listed in Table 3.


### Immune Infiltration Analyses
  The difference in the infiltration of 28 immune cells between OA and control was investigated by ssGSEA. The scores of the infiltration of immune cells between OA patients and control were summarized by a heatmap (Fig. 3A). The boxplot showed that 12 immune cells had higher infiltration rates in OA samples (Fig. 3B, P < 0.05).


### Weighted Co-expression Network Construction and Identification of Key Modules
  Pearson’s correlation coefficient was used to cluster the samples. There was no outlier to remove (Fig. 4A). The soft threshold was set to 18 to construct a scale-free network (Fig. 4B). 34 modules were then identified based on average hierarchical clustering and dynamic tree clipping (Fig. 4C). The darkgrey module was highly related to 12 immune cells. Thus, this module, including 89 genes, was selected for further analysis (Fig. 4D).


### GO and KEGG Enrichment Analysis of Immune-related Genes
  Darkgrey module genes and DEGs were overlapped to obtain 19 immune-related genes (Fig. 5A). Then GO analysis and KEGG analysis of the immune-related genes were conducted. The results showed that the related genes were mainly associated with biological processes such as regulation of immune effector process, positive regulation of leukocyte activation, macrophage activation, and T cell activation. As for GO-CC, the genes were enriched in the external side of the plasma membrane, secretory granule membrane, and MHC protein complex. Meanwhile, regarding GO-MF, the genes were mainly enriched in peptide binding, complement binding, and pattern recognition receptor activity (Fig. 5B). Besides, the top ten GO terms in each group are listed in Table 2 . Finally, the KEGG analysis revealed that the genes were significantly involved in the phagosome, neutrophil extracellular trap formation, and complement and coagulation cascades (Fig. 5C). Additionally, the top ten pathways are listed in Table 3.


### PPI Network Construction and Module Analysis
  To further study the interaction of 19 immune-related genes, the PPI network was constructed using by STRING database. With the confidence >0.4 and hiding the disconnected nodes, a visualized PPI network was created by Cytoscape (Fig. 6A). 9 genes in the key module were selected as hub genes using the MCODE plugin (Fig. 6B).


### Hub Gene Validation
  A Receiver Operating Characteristic (ROC) curve was plotted, and the area under the curve (AUC) was calculated to evaluate the diagnostic value of hub genes. The AUCS of 7 hub genes, including TYROBP, ITGAM, ITGB2, C1QC, MARCO, C1QB, and TLR8, were all greater than 0.7 (Fig. 7A). Therefore, these hub genes have a higher diagnostic value as a biomarker.

  Furthermore, the expression levels of the 7 hub genes were examined in GSE98918. The AUC of 7 hub genes was also greater than 0.7 (Fig. 7B). It has been determined that these hub genes could be used as diagnostic markers of OA.


### Correlation Analysis between Hub Genes and Infiltrating Immune Cells
  Exploring the relationship between hub genes and immune cells indicated that ITGAM had the highest correction with immune cells. ITGAM was negatively correlated with Type 17 T helper cells and Eosinophils but positively correlated with other immune cells (Fig. 8).


### Multi-factor Regulation Network Construction
  Based on miRNet and NetworkAnalyst databases, the miRnas hub genes and TFs-hub gene networks were constructed with the help of Cytoscape software (Fig. 9). The network was composed of 7 hub genes, 25 miRNAs, and 36 TFs.

  The hub gene-TF-miRNA network consisted of 7 hub genes (pink ellipse nodes), 25 miRNAs (green rectangle nodes), and 36 TFs (blue diamond nodes).


### RT-PCR Validation of the Hub Genes
  Quantitative PCR (qPCR) analyses were performed and showed the relative expression levels of 7 hub genes, including TYROBP, ITGAM, ITGB2, C1QC, MARCO, C1QB and TLR8 (Fig. 10). The results were consistent with those from bioinformatic analyses.


## DISCUSSION
  Osteoarthritis (OA), especially knee OA, is a chronic disease of the articulating joints, followed by activation of the inflammatory response involving the interaction of cartilage, subchondral bone, and synovium [12], causing joint pain, stiffness, and functional disability in patients worldwide. Previous studies have identified immune cells as significant regulators in the metabolic activities of chondrocytes [12-14]. Therefore, finding immune-related hub genes and diagnostic gene markers to help detect and treat the disease. The present study was conducted to identify 353 DEGs and 19 immune-related genes. A total of 7 hub genes were identified based on the integrated analysis of the PPI network, and ITGAM was indicated to have the highest correction for immune cells. The following analysis also revealed a hub-gene-related TF-miRNA network.

  To understand the functions of 353 DEGs, GO annotation and KEGG enrichment analysis were conducted, and found that these genes were associated with immune-related processes. WGCNA revealed 19 immune-related genes, and following enrichment analysis showed that they were mainly associated with biological processes, such as the regulation of the immune effector process, positive regulation of leukocyte activation, macrophage activation, and T cell activation. It was reported that neutrophil elastase released by activated leukocytes could activate MMP-13, PAR2, and a series of cascade reactions, leading to severe cartilage destruction [15, 16]. It was proved that osteophyte formation was related to PAR2 [17, 18]. Suppression of PAR2 would inhibit the apoptosis and senescence of chondrocytes by activating autophagy [19]. Besides, increased macrophage infiltration in the synovium of OA could upregulate the production of anti-inflammatory cytokines such as IL-1 and TNF-α [20, 21]. M1 polarization was associated with the release of R-spondin-2 and the activation of β-catenin signaling, which could exacerbate the progression of osteoarthritis [22]. However, M2 macrophages could inhibit the hypertrophy and apoptosis of chondrocytes, protecting cartilage and promoting cartilage repair [23]. It was also revealed that activated T helper cells would induce osteoclast formation and promote the progression of osteoarthritis by inducing macrophage inflammatory protein-1γ [24]. These genes were also involved in molecular functions, for instance, complement binding and pattern recognition receptor activity. It was found that complement factors, produced and activated in OA joints, suggested an association between the complement alternative pathway components and joint inflammation, supporting the involvement of innate immunity in OA [25]. Besides, pattern recognition receptors could recognize the cellular debris released during chondrocyte degeneration and apoptosis, activating downstream signal pathways and triggering an intense inflammatory response [26, 27]. On the whole, GO annotation and KEGG enrichment analysis indicated a strong correlation between these genes and immune-related processes related to OA progression.

  A PPI network was constructed to further study the interaction of 19 immune-related genes. Then, 7 hub genes (TYROBP、ITGAM、ITGB2、C1QC、MARCO、C1QB、TLR8) were identified with AUC> 0.7, which were recognized as diagnostic biomarkers of OA. Exploring the relationship between hub genes and immune cells indicated that ITGAM had the highest correction with immune cells. ITGAM, a marker for total macrophages, was considered a risk factor for systemic lupus erythematosus and possibly a protective factor to rheumatoid arthritis [28]. Meanwhile, ITGAM has been reported to encode CD11b, prevent chondrocyte mineralization, and alleviate OA progression [29, 30]. Besides, TYROBP, together with OSCAR, was proved to regulate the immunoreceptor tyrosine-based activation motif (ITAM) signaling pathway, which was strongly associated with osteoclastogenesis [31]. A study suggested that ITGB2, one of the integrin family, was significantly increased in OA meniscal compared with the control group, consistent with our previous study [32]. Besides, ITGB2 was involved in the phosphate metabolic process, with the clinical observation that meniscal calcification was more severe in OA menisci [33]. It was revealed that C1QB and C1QC, encoding C1q, were increased under inflammatory stimuli relevant to OA, and binding of C1q to chondrocytes would lead to changes in collagen expression with a decrease in type II collagen [34]. MARCO, an M1 macrophage marker, was reported to be significantly associated with early synovitis and the process of including increased trafficking and migration of monocytes into the synovial membrane [35]. A previous study showed that TLR8 expressing M1 macrophages could exacerbate cartilage degeneration in response to a joint injury [36]. Furthermore, when overexpressing human TLR8 in mice, researchers found that huTLR8 would promote the exacerbation of arthritis, and the levels of huTLR8 were related to proinflammatory cytokines in mice joints [37]. As a whole, these hub genes are valuable for being recognized as diagnostic biomarkers of OA. It has also been observed that several studies reported some diagnostic biomarkers in osteoarthritis, which were different from the hub genes found or derived from the same gene family [38-40]. The possible reasons might be the differences in the resources of the datasets analyzed. In any event, further experimental work will be required to test the value of these markers. Finally, we constructed a gene-TF-miRNA co-regulatory network based on the relationship among hub genes, TF, and miRNA, which provides a resource for future mechanistic studies of OA.

  Nevertheless, there were several potential limitations to this study. First, the data were obtained mainly from the GEO database, and immune cell infiltration of OA was not validated experimentally. Second, although we performed quality control of the original data, larger samples should be analyzed to validate the results. Finally, further elucidation of related molecular and validation of mechanisms have to be done to provide new ideas for postponing the development of osteoarthritis [41, 42].


## CONCLUSION
  Overall, this study identified 19 immune-related genes and 7 hub genes, and a TF-miRNA network (7 hub genes, 25 miRNAs, and 36 TFs) was successfully built. ITGAM was found to be significantly related to immune cells in OA. Furthermore, the biological functions and pathways of the identified genes provide a more detailed molecular mechanism of immune infiltration in OA development. Related diagnostic gene markers in OA will help to facilitate our understanding of the mechanisms governing osteoarthritis.


## DISCLOSURE
  The authors declare that they have no competing interests. This research did not receive any specific grants from funding agencies in the public, commercial, or not-for-profit sectors.


## AUTHORS’ CONTRIBUTIONS
  MY Yan conceived the study design and performed the original manuscript drafting. HB Zhao and ZW Sun were responsible for writing and editing. JL Chen contributed to the acquisition of the data. Yi Zhang and JK Gao contributed to the analysis and interpretation of data. TB Yu was responsible for the conceptualization and supervision of the manuscript. All authors have read and approved the final manuscript.


## ETHICS APPROVAL AND CONSENT TO PARTICIPATE
  Not applicable.


## HUMAN AND ANIMAL RIGHTS
  No animals/humans were used for studies that are the basis of this research.


## CONSENT FOR PUBLICATION
  Not applicable.


## AVAILABILITY OF DATA AND MATERIALS
  The data supporting the findings of this study are available within the article.


## FUNDING
  None.


## CONFLICT OF INTEREST
  None.


## SUPPLEMENTARY MATERIAL

## ACKNOWLEDGEMENTS
  We thank Zhen Shang for his guidance in the bioinformatics analysis.