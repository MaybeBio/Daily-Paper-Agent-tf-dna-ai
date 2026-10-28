# Identifying possible hub genes and biological mechanisms shared between bladder cancer and inflammatory bowel disease using machine learning and integrated bioinformatics


## Background
  Recent studies have shown that inflammatory bowel disease (IBD) is associated with bladder cancer (BC) incidence. But there is still a lack of understanding regarding its pathogenesis. Thus, this study aimed to identify potential hub genes and their important pathways and pathological mechanisms of interactions between IBD and BC using bioinformatics methods.


## Methods
  The data from Gene Expression Omnibus (GEO) and the cancer genome atlas (TCGA) were analyzed to screen common differentially expressed genes (DEGs) between IBD and BC. The “clusterProfiler” package was used to analyze GO term and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment in DEGs. After that, we conducted a weighted gene co-expression network analysis (WGCNA) on these DEGs to determine the vital modules and genes significantly related to BC. Protein–protein interaction (PPI) networks was used to identify hub genes. Further, the hub genes were used to develop a prognostic signature by Cox analysis. The validity of the ten hub DEGs was tested using three classification algorithms. Finally, we analyzed the microRNAs (miRNA)-mRNA, transcription factors (TFs)-mRNA regulatory network.


## Results
  Positive regulation of organelle fission, chromosomal region, tubulin binding, and cell cycle signaling pathway were the major enriched pathways for the common DEGs. PPI networks identified three hub proteins (AURKB, CDK1, and CCNA2) with high connectivity. Three machine-learning classification algorithms based on ten hub genes performed well for IBD and BC (accuracy > 0.80). The robust predictive model based on the ten hub genes could accurately classify BC cases with various clinical outcomes. Based on the gene-TFs and gene-miRNAs network construction, 9 TFs and 6 miRNAs were identified as potential critical TFs and miRNAs. There are 13 drugs that interact with the hub gene based on gene-drug interaction analysis.


## Conclusions
  This study explored common gene signatures and the potential pathogenesis of IBD and BC. We revealed that an unbalanced immune response, cell cycle pathway, and neutrophil infiltration might be the common pathogenesis of IBD and BC. Molecular mechanisms for the treatment of IBD and CC still require further investigation.


## Supplementary Information
  The online version contains supplementary material available at 10.1007/s00432-023-05266-0.