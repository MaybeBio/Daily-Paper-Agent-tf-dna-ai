# Study on differentially expressed genes and pattern recognition receptors in osteoporosis based on bioinformatics analysis


## Supplementary Information
  The online version contains supplementary material available at 10.1038/s41598-025-16891-9.


## Introduction
  Osteoporosis is a common skeletal disorder characterized by reduced bone mass and deterioration of bone microarchitecture, leading to increased bone fragility and susceptibility to fractures1. In the United States alone, approximately 54 million adults aged 50 years and older suffer from osteoporosis or are at risk due to low bone mass2. This disease primarily affects postmenopausal women, but men also face significant risks as they age3. Available treatment options include bisphosphonates, selective estrogen receptor modulators, and hormone replacement therapy. While these drugs are effective to some extent, they are limited by side effects and poor patient compliance4. For instance, long-term use of bisphosphonates may lead to osteonecrosis of the jaw, and selective estrogen receptor modulators may pose risks such as thrombosis. These limitations highlight the need for improved diagnostic tools and the discovery of additional therapeutic targets to enhance osteoporosis management. Therefore, in-depth research into the pathogenesis of osteoporosis and the identification of novel molecular targets remain of great clinical and social significance. Pattern recognition receptors (PRRs) are crucial elements of the innate immune system, responsible for triggering immune responses by detecting pathogen-associated molecular patterns (PAMPs) and damage-associated molecular patterns (DAMPs). Studies have shown that PRRs and pattern recognition receptor-related genes (PRR-related genes) play important roles in various diseases, including inflammatory and autoimmune diseases5. For example, Toll-like receptors (TLRs), a type of PRR, have been implicated in the pathogenesis of rheumatoid arthritis and systemic lupus erythematosus, where their activation leads to chronic inflammation and tissue damage6,7. Given the role of inflammation in bone remodeling and osteoporosis, PRR-related genes may also be involved in the pathogenesis of this disease. However, the specific mechanisms of these genes in osteoporosis remain largely unexplored. The interaction between genes and environment, particularly the relationship between long-term medication use and genetic variations, remains pivotal for a comprehensive elucidation.

  This study intends to comprehensively understand the role of PRR-related genes in osteoporosis through the integration of various bioinformatics analyses. The results may contribute to a better understanding of immune-related molecular mechanisms and support future studies exploring potential diagnostic indicators or therapeutic strategies for osteoporosis.


## Materials and methods

### Data acquisition
  The osteoporosis datasets GSE74298 and GSE568159 were downloaded from the GEO database10 (https://www.ncbi.nlm.nih.gov/geo/) using the R package GEOquery (version 2.66.0)11. Both datasets consist of human blood samples collected from postmenopausal women, and were generated using the GPL96 platform. Specifically, GSE7429 contains 10 osteoporosis samples and 10 control samples, while GSE56815 includes 20 osteoporosis samples and 20 control samples (Table 1).

  Table 1Datasets information list.GSE7429GSE56815PlatformGPL96GPL96SpeciesHomo sapiensHomo sapiensTissueBloodBloodSamples in Disease group1020Samples in Control group1020ReferenceIn vivo genome-wide expression study on human circulating B cells suggests a novel ESR1 and MAPK3 network for postmenopausal osteoporosisA novel approach for correction of crosstalk effects in pathway analysis and its application in osteoporosis research

  PRR-related genes were retrieved from the GeneCards database (https://www.genecards.org/)12which provides comprehensive information on human genes. Using “Pattern Recognition Receptors” as the search keyword and filtering for protein-coding genes with a Relevance Score > 15, we obtained a total of 1,052 PRR-related genes. The complete gene list is provided in the supplementary file (PRRRGs.csv). To integrate the datasets and correct for batch effects, the sva package13 was used on the GSE7429 and GSE56815 datasets, resulting in a combined dataset comprising 30 osteoporosis samples and 30 control samples. The integrated data were then normalized and annotated using the limma package14. To assess the effectiveness of batch effect removal, principal component analysis (PCA)15 was performed on the expression matrices before and after correction.


### Identification of PRR-related DEGs in osteoporosis
  Differential expression analysis was performed on the integrated GSE7429 and GSE56815 dataset using the limma package (version 3.54.2). Genes with an absolute log fold change (|logFC|) > 0 and a p-value < 0.05 were considered differentially expressed genes (DEGs), where logFC > 0 indicated upregulated genes and logFC < 0 indicated downregulated genes. The results were visualized using volcano plots generated with the ggplot2 package (version 3.4.4).

  To identify PRR-related DEGs associated with osteoporosis, the DEGs from the integrated dataset were intersected with the PRR-related gene set, and the overlapping genes were visualized using Venn diagrams. Heatmaps of PRR-related DEGs were generated using the pheatmap package.


### GO and KEGG enrichment analysis
  Gene Ontology (GO)16 and Kyoto Encyclopedia of Genes and Genomes (KEGG)17–19 enrichment analyses were performed on the PRR-related DEGs using the clusterProfiler package (version 4.4.4)20. GO terms and KEGG pathways with a p-value < 0.05 and false discovery rate (FDR, q-value) < 0.25 were considered significantly enriched.


### PPI network construction and hub gene identification
  A protein-protein interaction (PPI) network was constructed using the STRING database (https://string-db.org/)21with a minimum required interaction score set to 0.900 (highest confidence). Genes located in densely connected regions of the network—suggestive of molecular complexes with specific biological functions—were selected for further analysis. Hub genes were identified using the CytoHubba plugin22 in Cytoscape23based on five algorithms: Maximal Clique Centrality (MCC), Maximum Neighborhood Component (MNC), Degree, Edge Percolated Component (EPC), and Closeness24. The top 10 genes ranked by each algorithm were intersected to define the final set of hub genes. The results were visualized using Venn diagrams.

  Regulatory networks of miRNAs and transcription factors (TFs) associated with the hub genes were also constructed. miRNA data were obtained from the ENCORI database25and the mRNA–miRNA regulatory network was visualized using Cytoscape23.

  Similarly, TF data were retrieved from the ChIPBase database (http://rna.sysu.edu.cn/chipbase/)26, and the mRNA–TF regulatory network was visualized using Cytoscape.


### Construction of regulatory network
  MicroRNAs (miRNAs) play important regulatory roles in biological development and evolution. They can regulate multiple target genes, and conversely, a single gene can be regulated by multiple miRNAs. To explore the relationship between hub genes and miRNAs, relevant miRNA data were retrieved from the ENCORI database25. The mRNA–miRNA regulatory network was visualized using Cytoscape23.

  Transcription factors (TFs) regulate gene expression by interacting with genes at the transcriptional level. Using the ChIPBase database26 (http://rna.sysu.edu.cn/chipbase/), we analyzed TFs potentially regulating the hub genes, and constructed the corresponding mRNA–TF regulatory network, which was also visualized using Cytoscape.


### Validation of hub gene expression and ROC curve analysis
  To further examine the expression differences of hub genes between osteoporosis and control samples in the integrated GEO dataset, comparative expression plots were generated. The diagnostic potential of these hub genes was evaluated using receiver operating characteristic (ROC) curve analysis with the pROC package. The area under the curve (AUC) was calculated to assess diagnostic performance. AUC values ranging from 0.5 to 1.0 indicate varying degrees of diagnostic accuracy, with higher AUC values reflecting better discriminatory ability.


### Gene set enrichment analysis (GSEA)
  Gene set enrichment analysis (GSEA)27 evaluates whether predefined sets of genes show statistically significant, concordant differences between two biological states by examining their distribution within a ranked gene list correlated with phenotype.

  In this study, the integrated GEO dataset was first ranked based on log fold change (logFC) values. GSEA was then performed using the clusterProfiler package (version 4.4.4)20 on all genes from the two groups in the integrated dataset.

  The analysis was conducted with the following parameters: seed = 2022, 1,000 permutations, and gene set size limits set to a minimum of 10 genes and a maximum of 500 genes. The “h.all.v7.5.1.symbols.gmt” [Hallmark] gene set was obtained from the Molecular Signatures Database (MSigDB)28. Gene sets with a p-value < 0.05 and false discovery rate (FDR, q-value) < 0.25 were considered significantly enriched.


### Immune infiltration analysis
  To explore the relationship between osteoporosis and immune cell infiltration, single-sample gene set enrichment analysis (ssGSEA)22 was applied to the integrated GEO dataset. ssGSEA quantifies the relative abundance of immune cell types in individual samples. A variety of human immune cell subtypes were annotated, including activated CD8 + T cells, activated dendritic cells, gamma delta T cells, natural killer (NK) cells, and regulatory T cells. The enrichment scores calculated by ssGSEA reflect the relative levels of immune cell infiltration and were used to generate an immune infiltration matrix.

  Subsequently, the ggplot2 package (version 3.4.4) was used to generate comparative plots illustrating differences in immune cell infiltration between osteoporosis and control groups. Immune cell types with statistically significant differences between groups were selected for further analysis.

  Spearman correlation analysis was then performed to evaluate the relationships between different immune cell types, and the results were visualized accordingly. In addition, Spearman analysis was used to assess the correlations between hub gene expression and immune cell infiltration, and the results were visualized as bubble plots using ggplot2, providing insights into the interactions between key genes and the immune microenvironment.


### Statistical analysis
  All data processing and statistical analyses were conducted using R software (version 4.2.2). For comparisons between two groups, independent Student’s t-tests were used for normally distributed variables, while Mann–Whitney U tests were applied to non-normally distributed variables. For comparisons involving three or more groups, the Kruskal–Wallis test was employed.

  Spearman correlation analysis was used to calculate correlation coefficients between variables. Unless otherwise specified, a p-value < 0.05 was considered statistically significant.


## Results

### Technical roadmap
  An overview of the study’s analytical workflow is illustrated in Fig. 1. This roadmap outlines the key methodological steps, including data acquisition, preprocessing, differential expression analysis, functional enrichment analysis, protein–protein interaction (PPI) network construction, hub gene identification, regulatory network construction, validation of hub gene expression, gene set enrichment analysis (GSEA), and immune infiltration analysis.


### Dataset integration
  The sva package in R was initially used to correct batch effects between the osteoporosis datasets GSE7429 and GSE56815, resulting in an integrated GEO dataset. To evaluate the effectiveness of batch effect correction, boxplots (Figs. 2a,b) were generated to compare gene expression distributions before and after correction. In addition, principal component analysis (PCA) plots (Figs. 2c,d) were used to assess changes in sample clustering and low-dimensional variance structure.

  Both the boxplot and PCA analyses demonstrated that batch effects were effectively mitigated in the integrated dataset.


### Differentially expressed pattern recognition receptor-related genes in osteoporosis
  The integrated GEO dataset was divided into osteoporosis and control groups. To identify differentially expressed genes (DEGs) between the two groups, differential expression analysis was conducted using the limma package in R. A total of 1,347 DEGs met the screening criteria of |logFC| > 0 and p-value < 0.05, of which 742 genes were upregulated (logFC > 0) and 605 genes were downregulated (logFC < 0). These results are presented in the volcano plot in Fig. 3a.

  To identify PRR-related DEGs, the list of DEGs was intersected with pattern recognition receptor-related genes obtained from the GeneCards database. A Venn diagram (Fig. 3b) was used to visualize the intersection, resulting in a total of 98 PRR-related DEGs. These included genes such as ADRB1, FLT3, IL1R2, ITCH, PIK3CG, ADA, FRS2, WNT1, RIPK2, GPR182, ADRA1A, HTR3A, ROR2, P2RX2, BMP4, ITGA3, MTNR1A, HTR4, SST, GRIN2A, TNFSF11, TP63, F2, ANGPT1, ORC3, NR2E3, GNAQ, RET, TYRO3, RARG, GH1, CXCR4, NOTCH3, BTK, NPY, EPHA4, GIPR, CDK2, PTEN, EPHB1, CD86, ADIPOR1, NR6A1, IRAK4, ACE, SAG, CD320, MDM2, IGF1R, SRP19, ADRB2, PGLYRP1, HGF, ESR1, OPTN, TNFRSF10C, GHR, BAX, TNFRSF8, CCND1, HTR7, PTGER2, GRIN2B, OXTR, IL5RA, RPS27A, PPARG, PTGIR, BDKRB1, APP, NFKBIA, VEGFC, AKT1, BCL2L1, ITPR1, CCR1, CXADR, NCOR1, LPAR1, AGTR2, TAS2R16, TNFRSF14, ITGAV, NCOA2, MYD88, TNFRSF9, TICAM1, SMAD7, PPARA, SYK, MECP2, PTGER4, NLRP3, NRG1, FFAR2, TAC1, TRPV4, and ITPR2.

  The expression patterns of these 98 PRR-related DEGs were further evaluated between osteoporosis and control groups. The results were visualized using a heatmap generated with the pheatmap package (Fig. 3c).


### Gene ontology (GO) and pathway (KEGG) enrichment analysis
  GO and KEGG enrichment analyses were performed to investigate the biological significance of the 98 PRR-related DEGs. The detailed results are provided in the supplementary materials, highlighting significant enrichment across multiple functional categories.

  In the biological process (BP) category, key enriched terms included positive regulation of the mitogen-activated protein kinase (MAPK) cascade, calcium ion homeostasis, leukocyte migration, regulation of the inflammatory response, and peptidyl-tyrosine phosphorylation.

  In the cellular component (CC) category, significantly enriched terms included the external side of the plasma membrane, transcription regulator complex, neuronal cell body, actin-based cell projection, and endocytic vesicle.

  For molecular function (MF), enriched terms included protein serine/threonine/tyrosine kinase activity, signaling receptor activator activity, peptide binding, amide binding, and receptor–ligand activity.

  KEGG pathway enrichment analysis revealed significant involvement in pathways such as neuroactive ligand–receptor interaction, PI3K–Akt signaling pathway, calcium signaling pathway, cAMP signaling pathway, and cytokine–cytokine receptor interaction.

  The results of GO and KEGG enrichment analyses were visualized using a bubble chart (Fig. 4a). In addition, network diagrams (Figs. 4b–d) were constructed to illustrate the relationships among enriched BP, MF, and KEGG terms, where node size represents the number of genes associated with each term.


### Construction of protein-protein interaction network and hub gene screening
  Protein–protein interaction (PPI) analysis was first conducted using the STRING database to construct a network of the 98 PRR-related DEGs (Fig. 5a). The resulting network contained 55 genes with interaction evidence, including ACE, ADRA1A, ADRB1, ADRB2, AGTR2, AKT1, BAX, BCL2L1, BDKRB1, BTK, CCND1, CCR1, CD86, CDK2, CXCR4, ESR1, F2, FRS2, GH1, GHR, GNAQ, GRIN2A, GRIN2B, HGF, IGF1R, IRAK4, ITGA3, ITGAV, ITPR1, ITPR2, LPAR1, MDM2, MECP2, MYD88, NCOA2, NCOR1, NFKBIA, NPY, OXTR, PIK3CG, PPARA, PPARG, PTEN, PTGER2, PTGER4, RET, RPS27A, SAG, SST, SYK, TAC1, TICAM1, TNFRSF9, and TP63.

  To identify hub genes, five topological algorithms—Maximal Clique Centrality (MCC), Maximum Neighborhood Component (MNC), Degree, Edge Percolated Component (EPC), and Closeness—were applied using the CytoHubba plugin in Cytoscape. The top 10 genes ranked by each algorithm were extracted and used to construct corresponding sub-networks: MCC (Fig. 5b), MNC (Fig. 5c), Degree (Fig. 5d), EPC (Fig. 5e), and Closeness (Fig. 5f). Node color gradients (from red to yellow) represent decreasing scores.

  A Venn diagram (Fig. 5g) was then used to identify genes that were shared across all five algorithms, resulting in the identification of six hub genes: MDM2, AKT1, ESR1, NCOR1, CCND1, and NCOA2.

  To further explore post-transcriptional regulation, miRNAs targeting the hub genes were retrieved from the ENCORI database and used to construct the mRNA–miRNA regulatory network, visualized in Cytoscape (Fig. 6a). This network includes four hub genes and 22 miRNAs; detailed information is provided in Table 2.

  Table 2mRNA-miRNA interaction network nodes.miRNAmRNAmiRNAmRNAhsa-miR-15b-5pCCND1hsa-miR-192-5pESR1hsa-miR-186-5pCCND1hsa-miR-7-5pESR1hsa-miR-532-5pCCND1hsa-miR-106b-5pESR1hsa-miR-660-5pCCND1hsa-miR-130b-3pESR1hsa-miR-502-3pCCND1hsa-miR-590-5pESR1hsa-miR-17-5pESR1hsa-miR-301b-3pESR1hsa-miR-18a-5pESR1hsa-miR-1276ESR1hsa-miR-19a-3pESR1hsa-miR-18a-5pNCOA2hsa-miR-19b-3pESR1hsa-miR-27a-3pNCOA2hsa-miR-20a-5pESR1hsa-miR-365a-3pNCOR1hsa-miR-92a-3pESR1hsa-miR-365b-3pNCOR1hsa-miR-93-5pESR1

  Subsequently, transcription factors (TFs) associated with the hub genes were retrieved from the ChIPBase database to construct the mRNA–TF regulatory network. This network was visualized using Cytoscape software (Fig. 6b) and includes five hub genes and 28 TFs. Detailed information is provided in Table 3.

  The construction process and interrelationship analyses support the biological plausibility of the proposed TF–miRNA–hub gene synergistic regulatory network, providing a valuable basis for future mechanistic studies.

  Table 3mRNA-TF interaction network nodes.mRNATFmRNATFAKT1FOSL2MDM2FOXA2AKT1FOXA1MDM2HNF4AAKT1FOXA2MDM2JUNAKT1GABPAMDM2MAZAKT1JUNMDM2STAT3AKT1MAXMDM2TBPAKT1MYCMDM2TCF12AKT1NRF1MDM2TP53AKT1SPI1NCOA2FOXA1AKT1USF1NCOA2FOXA2AKT1USF2NCOA2RAD21AKT1CTCFNCOA2YY1AKT1EGR1NCOR1CTCFAKT1ELF1NCOR1ERGAKT1EP300NCOR1GABPAAKT1ERGNCOR1NRF1ESR1FOXA1NCOR1POLR2AESR1HOXB13NCOR1RAD21MDM2ELF1NCOR1YY1MDM2ERGNCOR1CEBPAMDM2FOXA1NCOR1CEBPBTF Transcription factors.


### Expression analysis of hub genes
  Differential expression analysis was performed on the six identified hub genes between osteoporosis and control samples in the integrated GEO dataset. The results, visualized using box plots (Fig. 7a), revealed significant differences in the expression levels of all six hub genes between the two groups.

  To further evaluate their diagnostic potential, ROC curve analysis was conducted using the pROC package in R, based on the expression values of the hub genes. The ROC curves (Figs. 7b–g) indicated that ESR1 showed moderate discriminatory power in distinguishing osteoporosis from control samples (0.7 < AUC < 0.9). In contrast, the remaining hub genes (AKT1, CCND1, MDM2, NCOA2, and NCOR1) exhibited lower diagnostic accuracy (0.5 < AUC < 0.7).


### Gene set enrichment analysis (GSEA) of disease and control groups in the combined datasets
  To investigate the functional impact of gene expression on osteoporosis, GSEA was performed on the combined GEO dataset. This analysis assessed the association between global gene expression profiles and hallmark biological processes, cellular components, and molecular functions. The overall GSEA results are presented in Fig. 8a, with detailed enrichment statistics provided in Table 4.

  The results revealed significant enrichment in several key biological pathways, including the unfolded protein response (Fig. 8b), KRAS signaling up (Fig. 8c), fatty acid metabolism (Fig. 8d), TNF-alpha signaling via NF-κB (Fig. 8e), UV response down (Fig. 8f), and mitotic spindle (Fig. 8g).

  Table 4Results of GSEA for combined datasets.IDsetSizeenrichmentScoreNESpvalueqvaluerankHALLMARK_MITOTIC_SPINDLE1800.5021322.2148460.0034130.00304758HALLMARK_UV_RESPONSE_DN142-0.5243-2.065670.0014810.003043381HALLMARK_TNFA_SIGNALING_VIA_NFKB1980.3696471.6435720.0034970.003041981HALLMARK_FATTY_ACID_METABOLISM146-0.33691-1.338510.0431650.0297692057HALLMARK_KRAS_SIGNALING_UP197-0.31242-1.283250.0490880.0313551406HALLMARK_UNFOLDED_PROTEIN_RESPONSE1100.4266041.7329480.0031750.003042042GSEA Gene Set Enrichment Analysis.


### Immune infiltration analysis
  Immune cell infiltration differences between the osteoporosis and control groups were systematically evaluated using single-sample Gene Set Enrichment Analysis (ssGSEA). The results revealed significant differences in the infiltration abundance of several immune cell types, notably activated dendritic cells, central memory CD4 + T cells, and mast cells, suggesting potential roles for these cells in the development and progression of osteoporosis.

  Immune cell infiltration comparison: Based on the expression matrix from the integrated GEO dataset, ssGSEA was used to estimate the relative abundance of 28 immune cell types in osteoporosis and control samples. The group comparison plot (Fig. 9a) shows that activated dendritic cells, central memory CD4 + T cells, and mast cells exhibited significantly different infiltration levels between the two groups (p < 0.05), indicating their involvement in the osteoporosis-associated immune response.

  Immune cell correlation analysis: Correlation analysis among the three significantly altered immune cell types was visualized using a correlation heatmap (Fig. 9b). This highlights the complex interactions among immune cells and provides insight into immune regulation in osteoporosis.

  Correlation between hub genes and immune cells: A correlation bubble plot (Fig. 9c) was used to assess relationships between hub genes and immune cell infiltration levels. Notably, ESR1 showed the strongest positive correlation with activated dendritic cells (r = 0.365, p < 0.05), providing potential biological evidence for its immunological relevance in osteoporosis.


## Discussion
  Osteoporosis, a common bone disorder characterized by reduced bone density and increased fracture risk, affects 10–30% of women and 10% of men over 40 in developed Asia-Pacific economies29. By 2050, over half of global osteoporotic fractures are projected to occur in Asia30. Despite advances, osteoporosis remains underdiagnosed and undertreated, necessitating improved diagnostic and therapeutic strategies31. Current treatments, primarily pharmacological, often have side effects, highlighting the need for new biomarkers and therapeutic targets32.

  This study utilized bioinformatics approaches to identify biomarkers associated with osteoporosis, with a particular focus on PRR-related genes, which play a critical role in bone metabolism and the pathophysiology of osteoporosis33,34. By analyzing PRRRG expression and its correlation with immune cell infiltration, this work provides a solid foundation for future experimental research.

  Batch effect correction ensured consistent expression distributions across datasets (Figs. 2A-D), thereby enhancing the reliability of subsequent analyses. Differential expression analysis identified 1,347 DEGs, of which 98 PRR-related DEGs were associated with key pathways, including neuroactive ligand-receptor interaction, PI3K-Akt signaling, calcium signaling, cAMP signaling, and cytokine-cytokine receptor interaction.

  Despite the involvement of these pathways in various physiological and pathological processes, they exhibit specific regulatory roles in osteoporosis. For example, the MAPK signaling pathway is crucial for osteoblast differentiation and bone remodeling, where its dysregulation—whether through overactivation or inhibition—can lead to bone loss or reduced bone density. Similarly, the PI3K-Akt pathway is closely associated with osteoblast and osteoclast proliferation and apoptosis, influencing bone mineralization and trabecular architecture integrity35. Additionally, the cAMP signaling pathway impacts bone homeostasis by modulating the expression of genes related to bone formation.

  The differentially expressed genes identified in this study, such as MDM2, AKT1, and ESR1, are key nodes within these pathways. They likely affect bone quality and fracture risk by regulating immune cell infiltration, cytokine secretion, and the activity of osteoblasts and osteoclasts within bone tissue36. These findings contribute to a deeper understanding of the molecular features involved in osteoporosis and may serve as a valuable reference for future studies aiming to explore diagnostic markers or therapeutic targets in a more targeted and validated context.

  Our protein-protein interaction (PPI) network analysis identified six hub genes (MDM2, AKT1, ESR1, NCOR1, CCND1, NCOA2) that play pivotal roles in the regulatory networks of osteoporosis.

  Firstly, the role of MDM2 in osteoporosis has been validated in independent studies. MDM2 promotes osteoblast differentiation by regulating the p53 signaling pathway, highlighting its potential role in osteoporosis37. AKT1 also plays a critical regulatory role in the pathological process of osteoporosis. CircFam190a enhances the stability of AKT1 to promote osteoclast differentiation and function, thereby playing an important role in osteoporosis35.

  Secondly, ESR1, as an estrogen receptor, has been supported by independent studies for its protective role in osteoporosis36. The negative regulatory effect of NCOR1 in osteoporosis has also been confirmed38. This study found that with aging, the expression of NCOR1 is influenced by the tryptophan metabolite kynurenine, which in turn suppresses osteoblast bioenergetics and function. In the case of CCND1, miR-23b-3p inhibits osteoblast proliferation and differentiation by targeting CCND1, promoting the progression of osteoporosis, and further emphasizing the important role of CCND1 in bone formation39.

  Finally, the role of NCOA2 in osteoporosis has also been supported by literature40. This study compared the differentiation potential of dental-derived mesenchymal stem cells (DMSC) and bone marrow-derived mesenchymal stem cells (BMSC), and found that NCOA2 regulates adipogenesis in the secretome of BMSCs, which is closely related to the imbalance of bone/fat metabolism in osteoporosis.

  Furthermore, the construction of mRNA-miRNA and mRNA-transcription factor regulatory networks revealed complex interactions that control gene expression in the context of osteoporosis. The identification of specific miRNAs and transcription factors linked to hub genes emphasizes the multifaceted regulation of gene expression in this disease41. These findings not only enhance our understanding of the regulatory mechanisms involved in osteoporosis but also open avenues for innovative therapeutic strategies that could leverage miRNA or transcription factor modulation to correct dysregulated pathways.

  Previous studies have demonstrated that immune dysfunction plays a pivotal role in the development and progression of osteoporosis42. Pro-inflammatory cytokines such as TNF-α, IL-6, and IL-17 have been shown to promote osteoclast differentiation and bone resorption while inhibiting osteoblast activity43. Moreover, T and B lymphocytes are involved in regulating bone remodeling, particularly in estrogen-deficient or chronically inflamed environments44,45. These findings underscore the critical role of the immune system in maintaining bone homeostasis and its disruption in osteoporosis.

  Compared to these previous studies, which primarily focused on individual cytokines or specific immune cell subsets, our study provides a broader, systems-level perspective by integrating pattern recognition receptor (PRR)-related gene expression analysis with immune cell infiltration profiling and multi-layer regulatory network construction. This approach allowed us to identify hub genes and immunological features that may serve as novel indicators of osteoporosis risk or progression.

  Our study suggests that immune cells may play a role in osteoporosis. We noted a significant increase in activated dendritic cells, central memory CD4 T cells, and mast cells in osteoporosis samples. These findings are consistent with previous research that highlights the immune system’s involvement in bone metabolism. Dendritic cells, key antigen-presenting cells, have been implicated in modulating osteoclast differentiation and activity, thereby contributing to bone resorption and osteoporosis46. Similarly, central memory CD4 T cells, essential for sustaining immune memory, may influence chronic inflammatory responses that exacerbate bone loss47. Additionally, mast cells, which play roles in allergic reactions and inflammation, participate in bone remodeling by releasing cytokines and other mediators that affect both osteoclast and osteoblast activity48.

  The identification of ESR1 as a hub gene with a significant positive correlation with activated dendritic cells highlights the intricate relationship between the immune system and bone health. The identification of ESR1 as a hub gene with a strong positive correlation with activated dendritic cells further underscores the interplay between the immune system and bone health. ESR1 encodes the estrogen receptor, which is pivotal in maintaining bone density, particularly post-menopause when estrogen levels decline49. The association between ESR1 and immune cells suggests that estrogen signaling may influence immune responses impacting bone remodeling. This is supported by evidence indicating that estrogen deficiency increases pro-inflammatory cytokine production, promoting osteoclastogenesis and bone resorption50.

  This study has several limitations that should be considered. First, the lack of experimental validation limits the ability to substantiate the findings, while the relatively small sample size may restrict the generalizability of the conclusions. Additionally, the absence of clinical validation means that the practical relevance of the discoveries remains unconfirmed. Although efforts were made to minimize batch effects during the integration of multiple datasets, residual data biases may still exist.

  Second, although enrichment analysis revealed several biological pathways associated with osteoporosis, it is important to note that biological processes are often intertwined. Thus, a simple pathway analysis may not provide sufficient targeted information. In complex biological networks, the interaction between different pathways and molecular mechanisms may have led to the omission of key details and specific mechanisms. Future studies should focus on more targeted assessments, such as in-depth analyses of specific genes, cell types, or signaling pathways, to reveal more precise osteoporosis-related mechanisms and strengthen support for potential therapeutic targets.

  Moreover, while this study laid the groundwork for understanding the potential link between immune cells and osteoporosis through bioinformatics analysis, we acknowledge the need for experimental validation to clarify the specific mechanisms of action. The conclusions drawn here are primarily based on bioinformatics analyses and lack direct wet-lab support. We plan to conduct related experiments in the future, such as in vivo and in vitro studies on immune cells related to osteoporosis, to further explore the mechanisms of their interactions.

  Lastly, although bioinformatics methods were used to identify potential osteoporosis-related targets (e.g., ESR1) and validate their potential roles, we recognize that further wet-lab validation (such as Western blot, immunohistochemistry, etc.) will provide more comprehensive evidence to substantiate these biomarkers. Due to time and resource limitations, these experiments were not included in the current study. In the future, we plan to deepen our research through large-scale wet-lab experiments to validate our findings.


## Conclusion
  In this study, we successfully identified PRR-related DEGs in osteoporosis through comprehensive bioinformatics analysis and elucidated their biological functions. The results indicate that PRR-related DEGs are significantly enriched in various biological processes, cellular components, molecular functions, and signaling pathways. We constructed PPI and regulatory networks to highlight key hub genes with potential diagnostic value, further validated by ROC curve analysis. Additionally, GSEA and immune infiltration analysis offered insights into the possible molecular mechanisms and immune landscape of osteoporosis. These findings suggest a possible involvement of immune cells in osteoporosis and may inform future research directions.

  Fig. 1Technology roadmap.

  Fig. 2Data integration and batch effect correction of the combined GEO datasets. (a) Box plot of the combined GEO dataset before batch effect correction. (b) Box plot of the combined GEO dataset after batch effect correction. (c) Principal component analysis (PCA) plot before batch effect correction. (d) PCA plot after batch effect correction. In panels a and b, blue represents dataset GSE56815, and orange represents GSE7429.

  Fig. 3Differential expression analysis of PRR-related genes between osteoporosis and control samples. (a) Volcano plot of differentially expressed genes (DEGs) between osteoporosis and control groups in the combined GEO dataset. (b)Venn diagram showing the overlap between DEGs and PRR-related genes. (c)Heatmap of the expression profiles of PRR-related DEGs across the combined GEO dataset. PPI, protein–protein interaction; DEGs, differentially expressed genes; PRR, pattern recognition receptor.

  Fig. 4GO and KEGG enrichment analysis of PRR-related DEGs.(a) Bubble plot showing Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) enrichment results for PRR-related DEGs. Terms from the biological process (BP), molecular function (MF), and KEGG pathways are shown on the x-axis. Bubble size reflects the number of enriched genes, and bubble color indicates the p-value (orange = lower p-value; blue = higher p-value).(b–d) Network diagrams of enriched terms: (b) BP, (c) MF, and (d) KEGG. Orange nodes represent GO/KEGG terms, blue nodes represent genes, and edges indicate gene-term associations.Enrichment significance was defined as p-value < 0.05 and FDR (q-value) < 0.25.GO, Gene Ontology; KEGG, Kyoto Encyclopedia of Genes and Genomes; BP, Biological Process; MF, Molecular Function.

  Fig. 5Protein–protein interaction (PPI) network and hub gene identification.(a) PPI network of PRR-related DEGs constructed using the STRING database. (b–f) PPI subnetworks of the top 10 genes ranked by five different algorithms in the CytoHubba plugin: (b) Maximal Clique Centrality (MCC), (c) Maximum Neighborhood Component (MNC), (d) Degree, (e) Edge Percolated Component (EPC), and (f) Closeness. (g) Venn diagram showing the overlap of the top 10 genes identified by all five algorithms.PPI, protein–protein interaction; DEGs, differentially expressed genes; PRR, pattern recognition receptor.

  Fig. 6Regulatory networks of hub genes. (a) mRNA–miRNA regulatory network of hub genes. (b) mRNA–transcription factor (TF) regulatory network of hub genes. In both networks, orange nodes represent mRNAs. In panel (a), blue nodes represent miRNAs; in panel (b), blue nodes represent transcription factors (TFs).TF, transcription factor; miRNA, microRNA; mRNA, messenger RNA.

  Fig. 7Expression analysis of Hub Genes. (a) Box plots comparing expression levels of six hub genes between osteoporosis and control groups in the integrated GEO dataset. (b–g) Receiver operating characteristic (ROC) curves of hub genes: (b) AKT1, (c) CCND1, (d) ESR1, (e) MDM2, (f) NCOA2, and (g) NCOR1. Statistical significance: p < 0.05 (*), p < 0.01 (**).

  Fig. 8Gene set enrichment analysis (GSEA) between osteoporosis and control groups in the integrated GEO dataset. (a) Overview enrichment plot showing gene set enrichment results for six hallmark biological pathways. (b–g) Individual enrichment plots for significantly enriched gene sets: (b) HALLMARK_UNFOLDED_PROTEIN_RESPONSE, (c) HALLMARK_KRAS_SIGNALING_UP, (d) HALLMARK_FATTY_ACID_METABOLISM, (e) HALLMARK_TNFA_SIGNALING_VIA_NFKB, (f) HALLMARK_UV_RESPONSE_DN, and (g) HALLMARK_MITOTIC_SPINDLE. GSEA was performed using a significance threshold of p < 0.05 and false discovery rate (FDR, q-value) < 0.25.

  Fig. 9Immune infiltration analysis based on ssGSEA in the integrated GEO dataset. (a) Box plots comparing immune cell infiltration levels between osteoporosis and control groups. (b) Correlation heatmap showing pairwise relationships among immune cell infiltration scores. (c) Bubble plot illustrating correlations between hub gene expression and immune cell infiltration. Statistical significance: ns, p ≥ 0.05; p < 0.05 (*); p < 0.01 (**); p < 0.001 (***). Color scheme: orange = osteoporosis group; blue = control group. ssGSEA, single-sample gene set enrichment analysis.


## Supplementary Information
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2

  Supplementary Material 3

  Supplementary Material 4

  Supplementary Material 5