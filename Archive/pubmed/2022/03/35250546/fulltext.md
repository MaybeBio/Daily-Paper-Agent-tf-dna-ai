# Is Immune Suppression Involved in the Ischemic Stroke? A Study Based on Computational Biology


## Objective
  To identify the genetic mechanisms of immunosuppression-related genes implicated in ischemic stroke.


## Background
  A better understanding of immune-related genes (IGs) involved in the pathophysiology of ischemic stroke may help identify drug targets beneficial for immunomodulatory approaches and reducing stroke-induced immunosuppression complications.


## Methods
  Two datasets related to ischemic stroke were downloaded from the GEO database. Immunosuppression-associated genes were obtained from three databases (i.e., DisGeNET, HisgAtlas, and Drugbank). The CIBERSORT algorithm was used to calculate the mean proportions of 22 immune-infiltrating cells in the stroke samples. Differential gene expression analysis was performed to identify the differentially expressed genes (DEGs) involved in stroke. Immunosuppression-related crosstalk genes were identified as the overlapping genes between ischemic stroke-DEGs and IGs. Feature selection was performed using the Boruta algorithm and a classifier model was constructed to evaluate the prediction accuracy of the obtained immunosuppression-related crosstalk genes. Functional enrichment analysis, gene-transcriptional factor and gene-drug interaction networks were constructed.


## Results
  Twenty two immune cell subsets were identified in stroke, where resting CD4 T memory cells were significantly downregulated while M0 macrophages were significantly upregulated. By overlapping the 54 crosstalk genes obtained by feature selection with ischemic stroke-related genes obtained from the DisGenet database, 17 potentially most valuable immunosuppression-related crosstalk genes were obtained, ARG1, CD36, FCN1, GRN, IL7R, JAK2, MAFB, MMP9, PTEN, STAT3, STAT5A, THBS1, TLR2, TLR4, TLR7, TNFSF10, and VASP. Regulatory transcriptional factors targeting key immunosuppression-related crosstalk genes in stroke included STAT3, SPI1, CEPBD, SP1, TP53, NFIL3, STAT1, HIF1A, and JUN. In addition, signaling pathways enriched by the crosstalk genes, including PD-L1 expression and PD-1 checkpoint pathway, NF-kappa B signaling, IL-17 signaling, TNF signaling, and NOD-like receptor signaling, were also identified.


## Conclusion
  Putative crosstalk genes that link immunosuppression and ischemic stroke were identified using bioinformatics analysis and machine learning approaches. These may be regarded as potential therapeutic targets for ischemic stroke.


## Introduction
  Ischemic stroke is the second most common cause of mortality worldwide and imposes a tremendous healthcare burden owing to significant disability. Aging populations are likely to further compound the gravity of the burden imposed by stroke (Katan and Luft, 2018). The prevention and clinical management of stroke assume critical importance. As currently widely applied modalities are limited in their clinical efficacy, a need for the advent of novel approaches is recognized. Molecular mechanisms involved in the pathophysiology of stroke resulting from cerebral ischemia and consequent brain tissue damage, involve immune activation, which leads to a host of both neuroprotective and neuro-toxic effects (Iadecola and Anrather, 2011; Iadecola et al., 2020). Further, stroke is frequently followed by post-stroke infection, which results from systemic immunosuppression that occurs after stroke and is associated with a worse prognosis (Shi et al., 2018). This occurs as a bi-directional brain-immune system interaction, when catecholamines and glucocorticoids are produced by an activated HPA-axis in attempts to limit local inflammation, which leads to natural killer T-cell (NKT) and T-cell activation, alongside reactive oxygen species production (Shim and Wong, 2016). Immune-modulatory approaches involving T-cell transfer, natural killer T-cell (NKT) activators and interferon-gamma (IFN-γ) have shown benefit in reducing post-stroke immunosuppression (Wong et al., 2011; Liu et al., 2017). Immunomodulatory approaches that target multiple elements of the immune system are now recognized as the most promising directions in stroke and its complication management (Fu et al., 2015). Several established drugs such as Azithromycin and Metformin have shown neuroprotective action in stroke via modulation of innate immune responses (Amantea and Giacinto, 2016) and the repurposing of such drugs may offer therapeutic potential, thus underscoring the importance of uncovering immunosuppression mechanisms in stroke.

  However, at present, the immune mechanisms implicated in stroke and stroke-associated systemic immunosuppression are still poorly understood. A comprehensive understanding of the immune mechanisms relevant to stroke has the potential to identify target genes and functional pathways, which can direct therapeutic interventions including drug development and repurposing. Integrated bioinformatics analysis of gene expression or transcriptomic datasets associated with disease can leverage higher scales of data to generate valuable insights. Gene expression data can also enable in silico identification of heterogeneous cell populations within a sample, including immune activate cell subsets (Newman et al., 2015). Furthermore, the application of machine learning-based feature selection algorithms can highlight potentially the most important genes linked to a disease or condition (Kursa, 2014). Therefore, in the current study, we aimed to utilize bioinformatics tools combined with feature selection to perform comprehensive secondary analysis of multiple transcriptomic datasets in stroke to reveal key immunosuppression related genes implicated in its pathogenesis. This approach could help highlight genes and pathways of high value for clinical and therapeutic translation for managing stroke and related immunosuppression.


## Materials and Methods

### Gene Expression Datasets in Stroke and Immunosuppression-Related Gene Data
  Two gene-expression microarray datasets pertaining to ischemic stroke were identified and downloaded from the NCBI Gene Expression Omnibus (GEO) database,1 GSE16561 and GSE22255. GSE16561 included peripheral blood samples from 39 stroke patients and 24 controls in a total of 63 samples analyzed using the “Illumina HumanRef-8 v3.0 Expression BeadChip” array (Barr et al., 2010) and GSE22255 included peripheral blood mononuclear cells from 20 stroke patients and 20 controls in a total of 40 samples analyzed using the “Affymetrix Human Genome U133 Plus 2.0” array (Krug et al., 2012).

  Next, immunosuppression-related genes were downloaded from DisGenet2 and HisgAtlas.3 In addition, drugs related to immunosuppressive agents were sourced from Drugbank.4 Here, 311 immunosuppressive drugs were identified and the relevant immunosuppressive related genes were downloaded. The immunosuppression-related genes obtained from these three databases (DisGeNET, HisgAtlas, and Drugbank) were merged to obtain a total of 1,332 genes, and the expression profiles of these specific immunosuppression-related genes in the GSE16561 and GSE22255 datasets were extracted.


### Analysis of Immune-Cell Subsets Enriched in Stroke
  The expression levels of immunosuppression-related genes in stroke were normalized and the “CIBERSORT” deconvolution algorithm (Newman et al., 2019) in the R statistical environment was applied to predict the infiltrating immune cell subsets that are highly related to stroke. The expression matrix of immunosuppression-related genes in stoke was used as the input, with 1,000 permutations and quantile normalization. A heatmap was then constructed to display immune cell subsets in each sample.


### Differential Gene Expression Analysis and Functional Enrichment Analysis
  The downloaded GSE16561 and GSE22255 gene expression datasets were subjected to preprocessing and filtration. Differential gene expression was performed using the R package “limma” with a P-value < 0.05 and logFC change > 0.58 set as thresholds to determine differentially expressed genes (DEGs) and volcano plots were plotted to display the results. Gene ontology (GO) functional profiles of the significant differentially expressed genes from these two data sets were clustered based on similarity using the “compareCluster_go” function of the “clusterProfiler” R package (Yu et al., 2012). Among these, pathways with P-value < 0.05 were considered as significantly enriched.


### Protein-Protein Interaction Network
  Protein-protein interaction (PPI) data was downloaded from multiple databases including PBIND (currently offline), BioGRID),5 MINT,6 HPRD,7 IntAct8 and OPHID9 and were integrated and the PPI relationship pairs of the immunosuppression-related DEGs were extracted from the integrated PPI data. A PPI network was constructed using Cytoscape and topological properties were analyzed using the “networkanalyzer” tool (Gustavsen et al., 2019). Gene nodes with the highest degree (indicating network connectivity) were considered to be of high functional importance in stroke and the top 30 genes were thus annotated as important stroke-related genes.


### Identification of Immunosuppression-Related Crosstalk Genes and Protein-Protein Interaction Network
  Immunosuppression-related genes were downloaded from the InnateDB10 database and intersecting DEGs in the GSE16561 and GSE22255 datasets were identified among these, merged with the earlier identified immunosuppression-related DEGs, and labeled as immunosuppression-related crosstalk genes. PPI relationship pairs for these genes were extracted and a crosstalk gene PPI network was constructed using Cytoscape.


### Feature Selection of Most Important Immunosuppression-Related Crosstalk Genes
  The immunosuppression-related crosstalk genes were considered as stroke-related features and the Boruta algorithm was applied using the R package “Boruta” (Kursa and Rudnicki, 2010) to select the most representative features. Boruta algorithm is a supervised classification feature selection method that is based on random forest and identifies all relevant features for classification task. The central concept in this algorithm is the iterative comparison of the actual predictor variables to generated shadow variables using random forest, thus sequentially identifying the variables relevant to classification. In the first step, the gene expression profiles of these crosstalk genes in the GSE16561 dataset were extracted. In the second step, the Boruta algorithm was applied to group features based on the category of each sample, with a p-value < 0.01 and the default maximum run at 100 times. The outcome grouped the crosstalk gene features into three categories: tentative temporary/pending features (not enough to accept or reject), confirmed features, and rejected features. For the tentative features, the “TentativeRoughFix” function was applied. Assuming that the Boruta algorithm might have preference errors, a traditional recursive feature elimination algorithm (RFE) was also applied to perform feature screening on the extracted immune gene expression values and the outcomes were compared.


### Classifier Models Based on Crosstalk Immunosuppression-Related Crosstalk Genes
  First of all, considering that the expression values in the GSE16561 and GSE22255 data sets were of different magnitudes and the GSE16561 data was normalized but GSE22255 was not, the GSE22255 data was normalized so that the two datasets were consistent. Next, the crosstalk genes obtained using the Boruta algorithm were verified using the two standardized data sets, and the “k nearest neighbor” method was applied to fill in missing (NA) values. The Decision tree, AdaBoost, and SVM algorithms were used to build classifier models. Here, randomly selected samples from the GSE16561 and GSE22255 datasets were used as a training set. Randomly selected 70% samples from the GSE16561 series were set as a test set and the crosstalk gene expression data from the GSE22255 data set was used as the verification set. To predict the accuracy of the classifier models, the test set data was input into the trained classifier for verification, and the receiver operating curves (ROC) curves of the prediction results were plotted using the “pROC” R package. Next, 1,159 genes related to ischemic stroke were downloaded from the “DisGenet” database. The crosstalk immunosuppression-related genes obtained were intersected with these to identify the potentially most valuable classifier genes and the accuracy of the selected genes was examined.


### Pathway Analysis of the Immunosuppression-Related Crosstalk Genes
  The crosstalk genes were subjected to KEGG pathway analysis and the top 30 enriched pathways were represented as key pathways of interest.


### Crosstalk Gene-Transcription Factor Network Analysis
  Transcription factors (TF) and target gene pairs were downloaded from the TRRUST11 and ORTI12 databases and the data were pooled. The TF-target gene relationship pairs of the crosstalk genes were extracted the TF-crosstalk gene network was plotted in Cytoscape. The topological properties of the top 10 genes ranked by outdegree were analyzed to gain insights into the transcriptional regulation of immunosuppression-related genes in stroke pathogenesis.


### Biological Pathways Analysis Enriched by the Transcription Regulatory Crosstalk Genes
  The TF-target gene relationship pairs were extracted from the transcriptional regulatory network, and these genes were divided into two gene sets, genes that were up-regulated and those that were down-regulated. The “enrichGO()” function of the “clusterprofiler” R package was applied to separately analyze biological pathways enriched in these two gene sets, with a p-value < 0.05. The top 30 enriched biological pathways were reported as those being most significant pathways.


### Crosstalk Gene- Drug Target Network Analysis
  To identify drugs that may be potentially relevant to stroke by immune modulation, gene-drug interaction pair data was downloaded from the DIGDB database.13 Drugs related to the most significant crosstalk genes identified earlier to construct a gene-drug network.


## Results

### Immune-Cell Subsets Enriched in Stroke
  The derived cellular component subsets in the samples are displayed as heatmaps and volcano plots (Figure 1) and significant differences were noted in the immune cell components between the stroke and normal samples. As samples were not labeled correctly, filtering was applied. Thereafter, GSE16561 retained 48 samples while GSE22255 retained 24 samples. Two subtypes of immune cells, resting CD4 memory T cells and M0 Macrophages were significantly different between the cases and controls. CD4 memory T cells were significantly down-regulated in stroke whereas M0 Macrophages were noted as significantly up-regulated.


### Differentially Expressed Genes and Functional Enrichment Analysis
  Among the DEGs determined in the two datasets, 147 DEGs were shared (Figure 2). The top 10 most highly significantly enriched pathways are depicted in Figure 3. Nodes representing regulatory pathways that control cell growth and division were found overlapping amongst the results from the two datasets. Other sets of functional pathways enriched in the DEGs varied between the two datasets, plausibly owing to sample heterogeneity.


### Protein-Protein Interaction Network in Stroke
  The PPI network of integrated DEGs of the two datasets is represented in Figure 4. The network consisted of 1,460 PPI pairs and 821 nodes. The gene nodes with topmost degree ranks in the PPI network included GRB2, MAPK1, TP53, FYN, PXN and Table 1 presents the top 10 gene nodes in the network.


### Immunosuppression-Related Crosstalk Genes
  The PPI network of these immunosuppression-related crosstalk genes comprising of 213 PPI pairs and 140 nodes is depicted in Figure 5. There are 213 international pairs and 140 nodes in the network.


### Feature Selection From Immunosuppression-Related Crosstalk Genes
  Using the Boruta algorithm, 54 immune-related crosstalk gene features were selected as representative features (Figure 6A). 98 feature genes were selected by the RFE algorithm (Figure 6B), which included all 54 genes selected using the Boruta algorithm, validating its good performance.


### Classifier Models Based on Immunosuppression-Related Crosstalk Genes
  The ROC curves pertaining to the dataset used to evaluate the classifier models are represented in Figure 7. The SVM classifier showed the best performance. The AUC values for the test set and validation set were 0.974 and 0.958, respectively, indicating the excellent performance of the classifier model to predict stroke patients and normal samples (Table 2). Among the 54 crosstalk immune-related genes, 17 genes were noted in the DisGenet database including, “ARG1” “CD36” “FCN1” “GRN” “IL7R” “JAK2” “MAFB” “MMP9” “PTEN” “STAT3” “STAT5A” “THBS1” “TLR2” “TLR4” “TLR7” “TNFSF10” “VASP.”

  Among the 54 crosstalk immune-related genes, 17 genes were noted in the DisGenet database including, “ARG1” “CD36” “FCN1” “GRN” “IL7R” “JAK2” “MAFB” “MMP9” “PTEN” “STAT3” “STAT5A” “THBS1” “TLR2” “TLR4” “TLR7” “TNFSF10” “VASP.” Another classifier model was constructed using these 17 genes and the ROC curves were plotted (Figure 8).


### Pathway Analysis of the Immunosuppression-Related Crosstalk Genes
  The top 30 KEGG pathways enriched in the immune-related crosstalk genes are represented in a barplot and dotplot (Figure 9). NOD-like receptor signaling pathway showed the highest significance and gene ratio values. TNF-signaling, Measles, Tuberculosis, C-type leptin receptor signaling and osteoclast differentiation were among the topmost enriched pathways.


### Immunosuppression-Related Crosstalk Gene-Transcription Factor Network Analysis
  The TF-target gene network consisted of 146 nodes and 208 TF-target gene pairs (Figure 10). The topological properties of top 10 genes in the network ranked by outdegree is presented in Table 3. STAT3, SPI1, CEBPD, STAT5A, and SP1 were ranked the highest in this network.


### Biological Pathways Analysis Enriched by the Transcription Regulatory Immunosuppression-Related Crosstalk Genes
  The up-regulated crosstalk immunosuppression-related genes were mainly enriched in biological pathways related to cell growth and proliferation, and energy metabolism, while the down-regulated genes were mainly enriched in positive cell apoptosis. The biological pathways related to cell differentiation and migration indicated that up- and down-regulated genes function together to promote the occurrence and development of stroke (Figure 11A). Expression levels of 10 key genes screened in the transcriptional regulatory network showed that the STAT3 gene and HIF1A gene showed similar transcriptional regulatory relationship in both the datasets, whereas TP53 as a transcription factor and its target gene JUN did not consistency in the expression pattern (Figure 11B) suggesting immune type heterogeneity in stroke.


### Drugs Targeted by Immunosuppression-Related Crosstalk Genes
  Drugs related to the 17 immunosuppression-related cross talk genes were screened and 11 genes were found to have target drugs. A gene-drug network is presented in Figure 12. The maximum numbers of drug targets were noted for the PTEN gene, followed by the JAK2 gene.


## Discussion
  The current study provides insights into the immune landscape of stroke via a comprehensive bioinformatic analysis of key immunosuppression-related genes underpinning the pathogenesis of stroke. Using a machine learning approach, a small number of 17 potentially most relevant immunosuppression-related crosstalk gene features were identified, which showed high performance accuracy in classifying stroke from healthy samples suggesting their potential value in molecular diagnosis and as biological targets.

  The initial findings showed that CD4 memory T cells were significantly downregulated while M0 Macrophages were upregulated in stroke. CD4 T cell infiltration has been implicated in stroke-associated neuroinflammation (Yilmaz et al., 2006; Gu et al., 2013) and CD4 cell deficit has shown beneficial effects by reducing infarction. The seemingly contrasting finding from our study may be accounted for by the temporal sequence of T cell infiltration in ischemic stroke, whereby animal models of stroke have shown that the peak of T cell infiltration appears after 3–5 days in transient ischemia, while other report CD4 T cells showed a rise beginning from 7 to 30 days after stroke (Gelderblom et al., 2009; Shichita et al., 2009; Stubbe et al., 2012). The samples used in the present study included blood collected within 24 h of symptom onset (Barr et al., 2010) and whereas the exact duration was not specified in one dataset (Krug et al., 2012), therefore, the temporal variation in immune cell infiltration could not be assessed. Macrophages and microglia play key roles in mediating tissue injury during the acute phase of ischemic stroke (Mabuchi et al., 2000; Hu et al., 2012). Infiltration of blood monocytes through a breached blood-brain barrier is an important early event in the neuroinflammation of post-stroke brain tissue (Mo et al., 2013). C-C chemokine receptor 2 (CCR2) + Mo/MΦ have been found to spread through the brain tissue in the early phase of stroke and have been implicated in both early stage inflammation and later functional recovery (Garcia-Bonilla et al., 2016; Fang et al., 2018; Pedragosa et al., 2020).

  The PPI network of DEGs in stroke indicated that the top genes of relevance were GRB2, MAPK1, TP53, FYN, and PXN. The involvement of these genes in stroke pathology is largely supported by experimental data. GRB2 encodes for a protein that binds the epidermal growth factor receptor leading to downstream mitogen-activated protein kinase (MAPK) signaling and is implicated in the development of atherosclerotic lesions (Proctor et al., 2007). GRB2 has been implicated in neuronal autophagy in stroke neuropathology via the suppression of the Akt/mTOR pathway (Luo et al., 2020). p38 mitogen-activated protein kinase (MAPK) signaling is a key mediator of inflammation, being a critical mediator of cell responses to cytokines and MAPK signaling has been widely implicated in the pathogenesis of stroke (Sun and Nan, 2016), although the specific upstream and downstream mechanisms remain unclarified, and different brain tissue types are marked by varying MAPK signaling patterns after ischemic stroke (Sawe et al., 2008). Animal data have shown that inhibition of p38 MAPKα starting in the early period after stroke led to improvement in motor and somatosensory function (Alam et al., 2020), whereas others have reported that MAPK-1 signaling plays an endogenous protective role in stroke and its inhibition accelerated stroke-induced injury via its anti-apoptotic and anti-inflammatory actions (Liu et al., 2014). MAPK inhibitors are emerging as promising anti-inflammatory agents for acute stages of brain inflammation (Kaminska et al., 2009) including cerebrovascular disorders (Ansar et al., 2013).

  TP53 polymorphism has been found associated with the prognosis of post-stroke functional recovery (Gomez-Sanchez et al., 2011) and neuroprotection after ischemia (Ramos-Araque et al., 2018). Furthermore, methylation of TP53 promoter has been associated with ischemic stroke (Wei et al., 2019). A recent bioinformatic study investigating ischemic stroke-related targets for the herbal medication Calculus Bovis reported MAPK1 and TP53 among the top target genes (Liu et al., 2021).

  FYN is a type of Src Family Kinase (SFK) gene, that code for a non-receptor protein tyrosine kinase and SFK inhibitors have shown protective action against ischemic stroke in animals (Takenaga et al., 2009). FYN is shown to interact with NMDAR during the ischemic response (Takagi et al., 1999) and phosphorylation of several proteins, which is implicated in cell death in stroke via reactive oxygen species generation and calcium flux (Knox and Jiang, 2015). In a rabbit, increased expression of FYN gene after ischemic stroke has been documented, and the authors suggested that GP6 induced activation of FYN initiated phosphorylation events eventually accelerating platelet adhesion (Gu et al., 2021).

  Paxillin or PXN is implicated in oligodendrocyte differentiation (Yamauchi et al., 2006). Downregulation of PXN in response to treatment of ischemic stroke with two Chinese medicine derived bioactive compounds has been documented (Liu et al., 2012). Similar downregulation of PXN by Diphenyleneiodonium for the treatment of stroke has been also documented (Nagel et al., 2012) although experimental evidence describing functional pathways of PXN involvement in stroke pathology is scarce. In a concordant finding, a bioinformatics analysis of inflammation associated competing endogenous RNA network in ischemic stroke has reported FYN and PXN among the most significantly enriched modules from the hub genes (Zhang et al., 2020).

  The SVM classifier showed excellent AUC values for discrimination of ischemic stroke and pathway analysis of the immunosuppression-related crosstalk genes showed TNF-signaling among the topmost enriched pathways. TNF-signaling plays pleiotropic and multiple roles in ischemic stroke, including acute inflammation and cell death during the early stages and tissue repair during the later recovery phase (Sairanen et al., 2001). The disease-related KEGG pathways enriched in the 17 key immunosuppression-related crosstalk genes including Measles and Tuberculosis pathways and osteoclast differentiation have been similarly reported as top pathways implicated in stroke (Diao and Liu, 2017). Leptin receptors are expressed by astrocytes (Schwartz and Baskin, 2013) and treatment with Leptin has shown improvements in post-stroke edema and functional recovery (Busch et al., 2010). In the transcriptional regulatory network of the immunosuppression-related crosstalk genes, STAT3 and SPI1 showed very high degrees. Activation of the JAK/STAT3 pathway in stroke is well-documented (Planas et al., 1996; Choi et al., 2003; Satriotomo et al., 2006) and its inhibition is found to significantly reduce the inflammatory process (Wu et al., 2018). In agreement with our findings, transcriptomic analysis of astrocytes has shown Stat3, Sp1, and Spi1 as the most significant transcription factors in stroke (Rakers et al., 2018).

  Along with STAT3, HIF1A showed a consistent transcriptional regulatory relationship in both datasets. HIF1A or hypoxia-inducible factor 1, is implicated in cellular adaptation to hypoxia and its inhibition was found to increase mortality and infarct volume size, while its downstream genes were found to increase ischemia-induced blood-brain barrier permeability on one hand, but also induce neuroprotection on the other hand (Yan et al., 2011). HIF1A has been considered an important target for the management of stroke (Pan et al., 2021). Analysis of drug targets for the immunosuppression-related crosstalk genes showed PTEN and JAK2 as the most prominent targets. PTEN or Phosphatase and tensin homolog deleted on chromosome 10 inhibitor drugs administration after stroke is found to confer neuroprotection via improvement of axonal growth and activation of the Akt/mTOR activation (Mao et al., 2013). Small molecule PTEN inhibitors currently under investigation include BPV that has shown protective effects in experimental stroke (Mao et al., 2013) and SF1670 (Li et al., 2011). JAK2 is a part of the Janus Kinase family and are implicated in cytokine and growth factor-related signaling and JAK targeting has been proposed as a strategy for the management of multiple immune and inflammatory diseases (Schwartz et al., 2017).

  The findings of the present study must be considered in light of its limitations. The included microarray datasets were of small sample size and RNA-seq datasets were not included. Large sampled transcriptome datasets with detailed metadata including time after stroke are essential to decipher the molecular events in the immune cascade following stroke. Additionally, experimental in vitro and in vivo investigations to verify the identified relevant immunosuppression-related genes in stroke were not conducted. In addition, the functional pathways involved remain to be investigated in future targeted studies. Therefore, future studies are necessary to confirm the involvement of the highlighted immune crosstalk genes and their related mechanistic pathways in ischemic stroke, in order to facilitate the clinical translation of these findings. At the same time, the strength of the current study includes the application of multiple bioinformatics and machine learning approaches to identify the most relevant immunosuppression-related genes in stroke.


## Conclusion
  The present bioinformatic study utilized a comprehensive approach to analyze immunosuppression-related genes implicated in stroke and identified key immunosuppression-related genes, transcriptional regulatory factors and signaling pathways implicated in the molecular pathogenesis of ischemic stroke. The most prominent molecular mechanisms included 17 immunosuppression-related key crosstalk genes including ARG1, CD36, FCN1, GRN, IL7R, JAK2, MAFB, MMP9, PTEN, STAT3, STAT5A, THBS1, TLR2, TLR4, TLR7, TNFSF10, and VASP, transcription factors targeting STAT3, SPI1, CEPBD, SP1, TP53, NFIL3, STAT1, HIF1A, and JUN, and, enriched signaling pathways, PD-L1 expression and PD-1 checkpoint pathway, NF-kappa B signaling, IL-17 signaling, TNF signaling, and NOD-like receptor signaling.


## Data Availability Statement
  The original contributions presented in the study are included in the article/Supplementary Material, further inquiries can be directed to the corresponding author/s.


## Author Contributions
  XW: conceptualization, funding acquisition, methodology, formal analysis, and writing—original draft. QW, KW, and QN: methodology, formal analysis, and writing—original draft. HL and ZS: formal analysis, methodology and writing—review and editing. YX: project administration, supervision, and writing—review and editing. All authors contributed to the article and approved the submitted version.


## Conflict of Interest
  The authors declare that the research was conducted in the absence of any commercial or financial relationships that could be construed as a potential conflict of interest.


## Publisher’s Note
  All claims expressed in this article are solely those of the authors and do not necessarily represent those of their affiliated organizations, or those of the publisher, the editors and the reviewers. Any product that may be evaluated in this article, or claim that may be made by its manufacturer, is not guaranteed or endorsed by the publisher.


## Funding
  This present study was funded by the China Postdoctoral Science Foundation (2020M681398), the Shandong Medical and Health Technology Development Fund (2018WS147 and 202103070325), and the Natural Science Foundation of Shandong Province (ZR2020MH141 and ZR2021MH0025).


## Supplementary Material
  The Supplementary Material for this article can be found online at: https://www.frontiersin.org/articles/10.3389/fnagi.2022.830494/full#supplementary-material