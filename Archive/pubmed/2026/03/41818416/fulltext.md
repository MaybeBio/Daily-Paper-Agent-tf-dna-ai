# Epigenetic Alterations Beyond CpG Islands in Periodontitis: In Silico Study of DNA Methylation Data


## Objectives
  To classify differentially methylated CpG sites in periodontitis based on methylation shift direction and location relative to CpG islands.


## Material and Methods
  We integrated DNA methylation data from 65 gingival samples (31 periodontitis, 34 healthy) from three GEO datasets. Preprocessing included normalization using R pipelines. Differential DNA methylation analysis was performed with the limma package. CpG sites (adjusted p < 0.05) were further evaluated using an exploratory threshold‐crossing framework based on group‐mean β‐values (cutoff = 0.5) identifying Control low → Periodontitis high and Control high → Periodontitis low shifts, annotated with Illumina 450k references. Top 20 CpG‐associated genes were selected by absolute logFC. Gene Ontology (GO) enrichment was conducted using clusterProfiler.


## Results
  We identified 164,400 differentially methylated CpG sites, including CpGs exhibiting Control low → Periodontitis high and Control high → Periodontitis low shifts, and mapped to gene features. Nearly half of methylation alterations (47.77%) were in OpenSea regions, with additional signals in CpG islands and promoter‐proximal regions. GO enrichment analysis revealed that differentially methylated genes in periodontitis were associated with epithelial and organ morphogenesis, including epithelial tube morphogenesis, epithelial cell proliferation, and cell fate commitment. Enriched cellular components were membrane‐ and vesicle‐associated structures, while molecular functions were transmembrane transporter activity, ion channel activity, and DNA‐binding transcription factor–related functions. These findings suggest that DNA methylation alterations in periodontitis are linked to epigenetic regulation of epithelial structure and tissue remodeling, with implications for immune‐related cellular processes.

  Among the top 20 genes exhibiting β‐threshold–based directionality changes, 13 were significantly enriched in GO terms: 8 in the Control low → Periodontitis high group (DGKA, CHMP6, RUNX2, CDKL1, SLC6A3, CFTR, HLA‐C, LRIG1), 5 in the Control high → Periodontitis low group (AP2A2, PARD3, PADI2, FOXK1, RGS1).


## Conclusions
  This study provides an exploratory, direction‐aware summary framework of DNA methylation in periodontitis, highlighting functional changes beyond CpG islands and identifying candidate genes for further functional validation.


## Introduction
  Periodontitis is a common chronic inflammatory disease characterized by progressive destruction of the periodontal ligament and alveolar bone, ultimately leading to tooth loss (Kinane et al. 2017). It arises from dysbiosis of the oral microbiome and an exaggerated or dysregulated host immune response (Bartold and Van Dyke 2013). While conventional research has highlighted the contributions of microbial, environmental, and genetic factors, increasing attention has turned toward epigenetic regulation, particularly DNA methylation, as a key mechanism modulating host responses in periodontitis pathogenesis (Barros et al. 2018).

  Several previous epigenome‐wide association studies (EWAS) have examined gingival tissue, peripheral blood, and immune cells in the context of periodontitis (reviewed in Cho et al. 2021; reviewed in Suzuki and Yamada 2022; Zhao et al. 2023). However, most of these studies focused on identifying differences in methylation levels between healthy and diseased tissues, without clarifying whether CpG sites exhibit a threshold‐crossing shift between low and high methylation states (β cutoff = 0.5) at the group level. To our knowledge, no previous study has systematically investigated this “directionality of change” in DNA methylation during the onset of periodontitis, particularly focusing on CpG sites that exhibit a threshold‐crossing shift between low and high methylation states at the group level. Furthermore, previous studies have used inconsistent criteria for defining hypermethylation, often based on arbitrary thresholds derived from β‐values, with no standardized evaluation method established to date.

  To address this limitation, we adopted the classification approach described by Alholle et al. (2015) where CpG sites with methylation levels ≥ 50% are defined as hypermethylated, and those with < 50% as hypomethylated. Based on this definition, we first determined the hypermethylation or hypomethylation status for each CpG site in both healthy and periodontitis tissues (Alholle et al. 2015). To clearly distinguish between methylation state and direction of change, we hereafter refer to CpG sites with β ≥ 0.5 and β < 0.5 as “high‐methylation” and “low‐methylation” states, respectively. We then focused specifically on CpG sites that cross this threshold between groups (Control low → Periodontitis high or Control high → Periodontitis low) as an exploratory, group‐level summary of methylation directionality.

  Another notable feature of our approach is the spatial genomic annotation of each CpG site. We classified CpGs by their relation to CpG islands (Island, Shore, Shelf, OpenSea), as well as to gene structural elements (TSS200, TSS1500, 5′ UTR, 1stExon, Gene body, 3′ UTR) (Jones 2012). This spatial stratification enabled us to map methylation changes not only to promoter‐proximal regions but also to distal regulatory elements and intragenic regions, which are increasingly recognized as important for transcriptional fine‐tuning. There remains a lack of integrated approaches that simultaneously consider the spatial relationship of CpG regions and gene structural domains in large‐scale DNA methylation studies of inflammatory conditions. This analytical gap is particularly evident in the context of chronic inflammatory diseases such as periodontitis, where no previous studies have applied such classification systematically. Our study addresses this need by providing a genome‐wide cross‐tabulation framework that captures both spatial and structural dimensions of methylation change.

  Furthermore, we separately analyzed hypermethylated and hypomethylated CpG sites and linked them to associated genes. From these, we conducted GO enrichment analysis on the genes, providing a comprehensive landscape of the functional pathways potentially regulated by differential DNA methylation in periodontitis.

  This study provides a systematic and spatially contextualized epigenetic profile of periodontitis, offering new insights into its regulatory architecture and biological implications.


## Materials and Methods

### Data Collection and Integration
  Publicly available DNA methylation datasets were obtained from the Gene Expression Omnibus (GEO) under the accession numbers GSE53849, GSE59932, and GSE59939 (De Souza et al. 2014; Planello et al. 2016). GSE59932 and GSE59939 represent sub‐series of the same study (SuperSeries GSE59962) and therefore share a common primary publication (Planello et al. 2016). These datasets included a total of 34 healthy control samples and 31 periodontitis samples, all analyzed using the Illumina HumanMethylation450 BeadChip platform. Because all datasets used the same array platform and were derived from gingival tissue collected under comparable protocols from the same institution (Piracicaba Dental School, University of Campinas, UNICAMP, Brazil), platform‐ and site‐related heterogeneity was minimized, supporting integrated analysis. The sample distribution was as follows: GSE53849 included 11 control and 12 periodontitis samples; GSE59932 included 12 control and 10 periodontitis samples; and GSE59939 included 11 control and 9 periodontitis samples. Raw methylation data (β‐values) were downloaded and processed using R (version 4.3.0). All subsequent preprocessing harmonization, statistical analyses, and downstream data generation reported in this study were conducted using R (version 4.5.0) to ensure reproducibility and consistency across datasets.

  GSE53849 included samples from 12 chronic periodontitis patients and 11 age‐ and gender‐matched healthy controls, with mean ages of 50.63 and 50.42 years, respectively (De Souza et al. 2014). Chronic periodontitis was diagnosed based on clinical attachment loss (CAL ≥ 5 mm) and bleeding on probing in at least one site. Control samples were obtained from non‐inflamed gingival areas in patients undergoing surgery for non‐periodontal reasons, showing no signs of inflammation or CAL > 3.5 mm. Biopsies (~2 × 2 mm) included junctional epithelium and soft connective tissue. Exclusion criteria included smoking, systemic diseases affecting periodontal health, recent use of antibiotics or anti‐inflammatory drugs, pregnancy, and lactation.

  GSE59932 and GSE59939 included biopsies from a total of 19 chronic periodontitis patients and 23 healthy controls (Planello et al. 2016). Age information was not reported for these datasets. Participants met similar exclusion criteria, including the absence of smoking, systemic disease, recent medication, pregnancy, lactation, and alcohol use. Samples were taken from a single tooth and included junctional epithelium and connective tissue. Control tissues were collected during aesthetic procedures or third molar extractions, and showed no clinical signs of periodontitis.

  Ethnicity was not explicitly reported in the original studies.


### Data Preprocessing and Cleaning
  The three datasets were merged into a unified CpG‐by‐sample matrix using common probe IDs. Quality control and preprocessing were conducted using the minfi, wateRmelon, and data.table packages in R. CpG sites with more than 80% missing β‐values across samples were removed, resulting in a final set of 484,331 CpG sites retained for downstream analyses, while no samples were excluded. Sample metadata was aligned and integrated with the beta matrix to ensure consistent labeling across samples. All preprocessing steps were applied uniformly to all samples using a single, reproducible analytical pipeline.


### Differential Methylation Analysis and Data Transformation
  Differential methylation results comparing periodontitis and healthy control groups were obtained using the limma‐based analyses of publicly available GEO data. After quality control and probe filtering as described in Section 2.2, these differential methylation result tables derived from publicly available GEO data were used as input for all downstream analyses.

  β‐values were logit‐transformed to M‐values prior to statistical modeling, as M‐values provide improved statistical properties for differential methylation analysis.

  A design matrix representing disease status (periodontitis vs. control) was constructed, and linear models were fitted for each CpG site using the lmFit() function. Empirical Bayes moderation was applied using the eBayes() function to stabilize variance estimates across CpG sites in this high‐dimensional dataset.

  Significantly differentially methylated CpG sites were defined as those with an adjusted p‐value < 0.05 based on the Benjamini–Hochberg false discovery rate (FDR), a threshold widely used in high‐dimensional genomic analyses employing limma and empirical Bayes methods (Ritchie et al. 2015; Phipson et al. 2016).

  The resulting differential methylation statistics, including log fold change (logFC), moderated t‐statistics, raw p‐values, adjusted p‐values, and B‐statistics (the log‐odds of differential methylation as defined in the limma framework), were obtained for all 484,331 CpG sites and are provided in Supplementary File 1, together with the corresponding R script and README to ensure full reproducibility. These files represent the finalized outputs of the limma‐based analysis used throughout the manuscript.


### CpG Annotation and Gene Mapping
  Significant CpG sites were annotated to genes using the IlluminaHumanMethylation450kanno.ilmn12.hg19 annotation package in R (version ≥ 4.3.0). Annotations included gene symbols, genomic coordinates, and CpG island context. The mapping was performed by merging CpG probe IDs with the official annotation data provided in the Bioconductor package. In cases where a probe mapped to multiple genes, all associated mappings were retained to preserve biological interpretation. The resulting annotated dataset is provided in Supplementary File 2. This annotation represents the finalized mapping used for all downstream analyses and tables reported in this study. The accompanying R script and instructions used for the annotation are included in Supplementary File 2, while the Illumina 450K annotation reference table together with its export script and README are provided in Supplementary File 3.


### Differential Methylation Visualization Using a Volcano Plot
  Differential methylation results obtained as described in Section 2.3 were visualized using a volcano plot.

  The volcano plot was generated using the ggplot2 package (version 3.4.4) in R. LogFC values derived from the limma analysis were plotted on the x‐axis, and −log10‐transformed Benjamini–Hochberg adjusted p‐values were plotted on the y‐axis.

  All 484,331 CpG sites analyzed were included in the plot, regardless of statistical significance. A dashed horizontal line corresponding to −log10(0.05), which is approximately 1.301 was added to illustrate the conventional adjusted p‐value threshold. Vertical logFC threshold lines were intentionally omitted to emphasize statistical significance rather than effect size cutoffs. The resulting volcano plot is shown in Figure 1. The R script and README used to generate Figure 1 (Volcano Plot) are provided in Supplementary_Figure_1_VolcanoPlot_script.R and Supplementary_Figure_1_VolcanoPlot_README.txt.


### Hierarchical Clustering and Heatmap Visualization
  β‐Values for all samples were compiled from three GEO datasets (GSE53849, GSE59932, and GSE59939) to construct a CpG‐by‐sample methylation matrix. From the full set of 484,331 CpG sites, a subset of 164,400 significantly differentially methylated CpGs (adjusted p < 0.05) was selected. A fixed random seed was set to ensure reproducibility, and 10,000 CpGs were randomly sampled from this significant subset to visualize global methylation patterns. β‐values were transformed to Z‐scores across samples to enable clustering. Hierarchical clustering of both CpGs and samples was performed using Euclidean distance and complete linkage. Sample group annotations (Control vs. Periodontitis) were added to the column side of the heatmap and color‐coded (blue for Control, red for Periodontitis). The heatmap was generated using the pheatmap package (version 1.0.12) and is shown in Figure 2. The Z‐score matrix and sample metadata used to generate this heatmap are provided in Supplementary File 4 and Supplementary File 5, respectively. The R script and README used to generate Figure 2 are provided in Supplementary_Figure_2_Heatmap_script.R and Supplementary_Figure_2_Heatmap_README.txt.


### Sample Clustering and Dimensionality Reduction
  Unsupervised hierarchical clustering and dimensionality reduction analyses were conducted using 10,000 randomly sampled differentially methylated CpG sites. Z‐score normalization was applied across samples for each CpG site. Hierarchical clustering was performed using Euclidean distance and complete linkage. The dendrogram was visualized using the dendextend package (version 1.19.0), with sample labels colored by group. Principal component analysis (PCA) was conducted using the prcomp() function (stats package). Data were Z‐score normalized per CpG site prior to PCA; therefore, additional scaling was not applied. The first two principal components were visualized in a scatter plot, with sample groups indicated by color. The same Z‐score matrix and sample metadata described in Section 2.6 (Supplementary Files 4 and 5) were also used in this analysis. The R script and README used to generate Figure 3 (Hierarchical Clustering and PCA) are provided in Supplementary_Figure_3_Hierarchical clustering and PCA_script.R and Supplementary_Figure_3_Hierarchical clustering and PCA_README.txt.


### Directionality Classification and Cross‐Tabulation Analysis
  Group‐wise average β‐values were calculated separately for control and periodontitis samples for each CpG site. CpG sites were assigned a “high‐methylation” state (β ≥ 0.5) or “low‐methylation” state (β < 0.5) based on group‐wise mean β‐values, following the thresholding concept used by Alholle et al. (2015).

  For clarity, these thresholds are hereafter referred to as high‐methylation (β ≥ 0.5) and low‐methylation (β < 0.5) states, respectively, to distinguish methylation state from direction of change.

  When used in the context of directionality, the terms “Control low → Periodontitis high” and “Control high → Periodontitis low” refer specifically to threshold‐crossing changes between groups, namely Control low (β < 0.5) → Periodontitis high (β ≥ 0.5) and Control high (β ≥ 0.5) → Periodontitis low (β < 0.5), respectively, rather than simply higher or lower methylation levels in the disease group.

  This classification scheme was applied as an exploratory framework to summarize group‐level methylation trends and was not intended to replace continuous differential methylation analysis based on linear modeling. The fixed β‐value threshold (β ≥ 0.5 for high methylation and β < 0.5 for low methylation) was adopted following the approach described by Alholle et al. (2015).

  From CpG sites classified into either “Control low → Periodontitis high” or “Control high → Periodontitis low” categories, the top 20 genes with the largest absolute log fold change (logFC) were extracted (Table 1). Genomic spatial annotations relative to CpG islands (Relation_to_Island) and gene structural regions (UCSC_RefGene_Group) were assigned using Illumina HumanMethylation450K annotation data. CpG sites lacking annotation were categorized as “unknown.”

  Stratified cross‐tabulations integrating methylation directionality, CpG island–defined regions, and gene structural regions were generated for CpG sites mapped to these top 20 genes and summarized in Table 2.

  For CpG island–defined regions, Relation_to_Island categories were ordered as follows: CpG islands, north and south shores (≤ 2 kb flanking CpG islands), north and south shelves (~2–4 kb outside shores), and OpenSea regions (> 6 kb from CpG islands), according to established definitions (Shen et al. 2013). Unknown spatial relationships were grouped as “unknown.”

  For gene structural annotation, UCSC_RefGene_Group categories were ordered by proximity to the transcription start site: TSS200 (within 200 bp of the transcription start site), TSS1500 (200–1500 bp upstream), 5′ untranslated region (5′ UTR), first exon (1stExon), gene body (exons and introns), and 3′ untranslated region (3′ UTR). Unknown annotations were grouped as “unknown.”

  This consistent ordering facilitated interpretation of spatial methylation patterns across genomic regions and enabled systematic comparison between CpG island–proximal and distal methylation changes. All annotated CpG data, group‐wise average β‐values, and scripts used to generate Tables 1 and 2 are provided in Supplementary File 6.


### Gene Ontology Enrichment Analysis
  To investigate the biological implications of differential DNA methylation in periodontitis, Gene Ontology (GO) enrichment analysis was performed using the R package clusterProfiler (v4.6.2). A total of 164,400 significantly differentially methylated CpG sites (adjusted p < 0.05) were identified, and 19,605 annotated gene symbols (SYMBOL) were extracted from these CpGs. These gene symbols were converted to Entrez Gene IDs using the org.Hs.eg.db annotation package. GO enrichment analysis was then conducted with enrichGO() across three ontologies: Biological Process (BP), Cellular Component (CC), and Molecular Function (MF). The parameters used included: pvalueCutoff = 0.05, qvalueCutoff = 0.2, and pAdjustMethod = “BH” (Benjamini–Hochberg method). The top 20 significantly enriched GO terms were selected from each category and visualized. Furthermore, for each enriched GO term, Table 3 lists the gene symbols that were both among the top 20 differentially methylated genes and enriched in that GO term. The full dataset of enriched GO terms, along with the R script and README used to reproduce Table 3, is provided in Supplementary File 7: Table 3 Generation Script and README.


### Statistical Analysis
  Earlier preprocessing and annotation reference generation steps were performed using R (version 4.3.0). All downstream statistical analyses, data integration, visualization, and interpretation were conducted using R (version 4.5.0) (Core Team R 2024), consistent with the scripts and README files provided in the Figshare repository. All downstream analyses, figures, and supplementary files reported in this manuscript, as were generated using this platform and corresponding scripts to ensure full reproducibility. Differential methylation analysis was performed using linear models with empirical Bayes moderation implemented in the limma package. CpG sites with an adjusted p‐value < 0.05 based on the Benjamini–Hochberg FDR were considered statistically significant. Unsupervised analyses, including hierarchical clustering and PCA, were applied to evaluate global methylation patterns. Directionality classification based on group‐wise average β‐values (≥ 0.5 as high‐methylation and < 0.5 as low‐methylation) was used solely as an exploratory approach to summarize group‐level methylation trends and was not intended to replace continuous differential methylation analysis.

  GO enrichment analysis was performed using the clusterProfiler package with multiple‐testing correction applied to enriched terms.


## Results

### Global Methylation Differences Visualized by Volcano Plot
  Volcano plot of all 484,331 CpG sites revealed a dense cluster of non‐significant sites around the origin and a smaller number of significantly differentially methylated CpG sites (adjusted p < 0.05) extending toward both tails.

  The detection of many significant CpG sites reflects the genome‐wide scope and high sensitivity of the Illumina HumanMethylation450 BeadChip combined with the use of empirical Bayes–moderated linear models.

  The majority of CpG sites did not exceed the threshold for significance, but a subset exhibited strong differential methylation. Vertical logFC threshold lines were intentionally omitted to focus on statistical significance (Figure 1).


### Hierarchical Clustering Reveals Distinct Methylation Patterns
  The heatmap of the 65 samples using the 10,000 randomly sampled significantly differentially methylated CpG sites showed distinct clustering patterns among control and periodontitis samples (Figure 2).

  Samples within each group tended to cluster together, indicating group‐specific methylation profiles. This result suggests that periodontitis is associated with widespread changes in DNA methylation at these CpG loci.


### Unsupervised Clustering and Ordination Separate Periodontitis and Control Samples
  Hierarchical clustering of the 65 samples based on the 10,000 randomly sampled significantly differentially methylated CpG sites effectively grouped the samples by clinical status. Periodontitis and control samples formed distinct clusters, indicating consistent group‐level methylation differences (Figure 3A).

  PCA further supported this separation, with the first two principal components, PC1 (31.6%) and PC2 (11.6%), accounting for a substantial proportion of variance and revealing distinct group distributions (Figure 3B).


### Differential Methylation Analysis
  A total of 164,400 significantly differentially methylated CpG sites were analyzed. Among these, methylation status changes between control and periodontitis groups were categorized into threshold‐crossing Control low → Periodontitis high and Control high → Periodontitis low groups based on group‐specific β‐values. The top 20 genes with the largest methylation changes were identified from these CpG sites (Table 1).

  Cross‐tabulation of CpG sites by spatial relation to CpG islands and gene structural annotation revealed distinct distribution patterns. Most CpG sites with methylation changes were enriched in TSS200 and TSS1500 regions within or near CpG islands. In particular, gene body (Body) regions also contained substantial CpG sites with methylation changes associated with periodontitis, especially in OpenSea regions distant from CpG islands.

  This comprehensive classification table (Table 2) integrates methylation changes, genomic context, and top gene associations, providing a detailed landscape of epigenetic alterations in periodontitis.


### GO Enrichment Analysis in Periodontitis‐Associated Differentially Methylated Genes
  GO enrichment analysis of the 19,605 genes associated with significantly differentially methylated CpG sites revealed distinct functional signatures (Table 3). In the BP category, the top enriched terms included epithelial and organ morphogenesis such as epithelial tube morphogenesis, epithelial cell proliferation, cell fate commitment, and embryonic organ development. In the CC category, enriched terms were predominantly localized to membrane‐ and vesicle‐related cellular components, including external side of plasma membrane, synaptic membrane, and clathrin‐coated vesicle. The MF category showed enrichment in transmembrane transporter activity, ion channel activity, and DNA‐binding transcription factor–related functions. These results indicate that DNA methylation alterations in periodontitis are linked to epigenetic regulation of epithelial structure, tissue remodeling, and membrane‐associated signaling, with additional implications for cell–cell communication and immune‐related cellular processes.

  Furthermore, the CpG sites corresponding to both the top 20 genes and the enriched GO terms are presented in Table 3. Among the genes showing Control low → Periodontitis high threshold‐crossing shifts, eight genes, including diacylglycerol kinase alpha (DGKA), charged multivesicular body protein 6 (CHMP6), RUNX family transcription factor 2 (RUNX2), cyclin dependent kinase like 1 (CDKL1), solute carrier family 6 member 3 (SLC6A3), CF transmembrane conductance regulator (CFTR), major histocompatibility complex, class I, C (HLA‐C), and leucine rich repeats and immunoglobulin like domains 1 (LRIG1), were found to be associated with enriched biological functions. In contrast, five genes, including adaptor related protein complex 2 subunit alpha 2 (AP2A2), par‐3 family cell polarity regulator (PARD3), peptidyl arginine deiminase 2 (PADI2), forkhead box K1 (FOXK1), and regulator of G protein signaling 1 (RGS1), were identified in the Control high → Periodontitis low threshold‐crossing group.

  In the Control low → Periodontitis high group, DGKA was associated with BP such as regulation of body fluid levels and wound healing. CHMP6 was also linked to the BP term wound healing. RUNX2 showed enrichment in several BP terms including epithelial cell proliferation, cell fate commitment, lymphocyte differentiation, and embryonic organ development, as well as MF terms such as DNA‐binding transcription activator activity, RNA polymerase II‐specific, and DNA‐binding transcription factor binding. CDKL1 was related to MF terms including protein serine/threonine kinase activity and protein serine kinase activity. SLC6A3 was associated with multiple BP terms such as sensory system development, visual system development, eye development, regulation of body fluid levels, camera‐type eye development, and gland development. It was also enriched in CC terms like synaptic membrane and postsynaptic membrane, and MF terms including metal ion transmembrane transporter activity, solute:monoatomic cation symporter activity, monoatomic anion transmembrane transporter activity, and inorganic anion transmembrane transporter activity. CFTR was linked to BP terms such as regulation of membrane potential and regulation of body fluid levels, CC terms including endocytic vesicle, apical part of cell, apical plasma membrane, and clathrin‐coated vesicle, as well as MF terms like gated channel activity, monoatomic anion transmembrane transporter activity, monoatomic ion channel activity, ligand‐gated monoatomic ion channel activity, and inorganic anion transmembrane transporter activity. HLA‐C was associated with CC terms endocytic vesicle and external side of plasma membrane, while LRIG1 was linked to the BP term embryonic organ development.

  In the Control high → Periodontitis low group, AP2A2 was associated with the CC terms endocytic vesicle and clathrin‐coated vesicle. PARD3 was linked to apical part of cell and apical plasma membrane. PADI2 was related to the MF term DNA‐binding transcription factor binding, and FOXK1 was enriched in the MF term DNA‐binding transcription repressor activity. RGS1 showed associations with CC terms such as neuron‐to‐neuron synapse, postsynaptic specialization, asymmetric synapse, postsynaptic density, and clathrin‐coated vesicle, and was also linked to the MF term calmodulin binding.


## Discussion
  In this study, we performed an integrated epigenome‐wide DNA methylation analysis using three publicly available datasets to characterize the epigenetic landscape of periodontitis. The results revealed widespread methylation changes predominantly associated with epithelial structure, tissue remodeling, and membrane‐associated regulatory processes, with additional involvement of immune‐related pathways. All datasets were generated using the same Illumina HumanMethylation450 BeadChip platform and derived from gingival tissue samples collected at the same institution under comparable clinical and experimental protocols. These shared characteristics minimized platform‐ and site‐related heterogeneity and supported the validity of the integrated analysis. Although explicit batch‐effect correction was not applied, hierarchical clustering and PCA consistently separated control and periodontitis samples, suggesting that disease‐associated signals outweighed potential inter‐dataset variability.

  The relatively large number of significant CpG sites identified should be interpreted in the context of epigenome‐wide association study design. The Illumina HumanMethylation450 BeadChip interrogates over 450,000 CpG sites, and empirical Bayes–moderated linear models implemented in limma are designed to provide stable inference in high‐dimensional settings with limited sample sizes (Ritchie et al. 2015; Phipson et al. 2016). Consistent with this, previous EWAS have shown that disease‐associated DNA methylation changes, particularly in immune‐mediated and chronic inflammatory conditions, can be distributed across many loci with modest effect sizes (Rakyan et al. 2011). Accordingly, the present analysis was primarily exploratory, and downstream biological interpretation focused on top‐ranked CpG‐associated genes with the largest absolute methylation differences.

  Directionality classification based on a fixed β‐value threshold was applied as a complementary, exploratory framework to summarize group‐level methylation trends. However, this approach simplifies continuous methylation data and should therefore be interpreted with caution. Importantly, continuous differential methylation analysis using limma with empirical Bayes moderation was performed independently, and the direction‐based classification was not intended to replace linear modeling–based inference. Similar threshold‐based strategies have been employed in previous epigenetic studies to facilitate interpretation of disease‐associated methylation patterns (Alholle et al. 2015).

  Integration of CpG island context with gene structural annotation revealed that a substantial proportion of differentially methylated CpG sites were located outside promoter‐associated CpG islands, particularly within gene body regions in OpenSea domains. Gene body methylation in such regions has been reported to modulate transcriptional fidelity, alternative splicing, and regulatory precision rather than directly suppressing gene expression (Jones 2012). This distribution contrasts with classical cancer epigenetic models that emphasize promoter CpG island hypermethylation (Esteller 2008; Jones and Baylin 2002).

  GO enrichment analysis identified pathways related to epithelial function, tissue remodeling, and developmental processes, with additional links to immune‐related regulation. Notably, several enriched BP terms, such as lymphocyte differentiation, link these developmental pathways to immune‐related processes, highlighting the interplay between epithelial regulation and immune responses in chronic periodontal inflammation.

  Hereafter, the terms “hypermethylated” and “hypomethylated” genes are used only to denote genes harboring CpG sites that crossed the β = 0.5 threshold between groups (Control low → Periodontitis high or Control high → Periodontitis low), as defined in the Section Material and Methods, 2, and do not refer to absolute methylation states.

  Among hypermethylated genes, RUNX2 showed gene body methylation in OpenSea regions and was enriched in GO terms related to cell fate commitment, epithelial proliferation, and immune‐related processes. RUNX2 is a key transcription factor in osteogenesis and tissue regeneration (Kim and Adachi 2021; Komori 2017), and its altered methylation may contribute to impaired bone regeneration and epithelial repair in periodontitis, as suggested by previous experimental studies (An et al. 2015; Korinfskaya et al. 2021).

  Other hypermethylated genes, including CFTR, HLA‐C, and LRIG1, were associated with epithelial barrier function and immune modulation. CFTR plays a central role in epithelial ion transport and barrier integrity and has been shown to be expressed in gingival tissues under inflammatory conditions (Ajonuma et al. 2010). Altered methylation of CFTR has also been reported in other chronic inflammatory diseases (Gaia‐Oltean et al. 2021), supporting its potential involvement in epithelial dysfunction during periodontitis.

  Gene body and shore methylation have been reported to modulate transcriptional precision and regulatory control rather than acting as simple on–off switches (Jones 2012). Against this background, hypermethylated genes such as HLA‐C (Schaefer et al. 2008) and LRIG1 (Ta et al. 2024), which are involved in antigen presentation and immune checkpoint regulation, respectively, may reflect epigenetic modulation of immune activity in chronically inflamed periodontal tissues.

  Among genes showing Control high → Periodontitis low shifts, RGS1 and PADI2 were enriched in immune‐related pathways. RGS1 has been implicated in immune cell migration and inflammatory signaling and has been reported as a disease‐associated gene in periodontitis and other inflammatory conditions (Zhang et al. 2022; Cheng et al. 2025). PADI2 has been shown to be upregulated in periodontal tissues and to participate in inflammation‐associated epigenetic regulation through protein citrullination (Clancy et al. 2017; Engström et al. 2018). The observed hypomethylation of these genes may therefore reflect enhanced immune activation in periodontal inflammation.

  Importantly, functional interpretations in this study should be considered with caution. DNA methylation changes do not necessarily translate directly into corresponding changes in gene expression, particularly in the absence of matched transcriptomic data. Functional implications were inferred based on genomic location, GO enrichment, and previously reported biological roles of the identified genes. These interpretations are therefore hypothesis‐generating rather than definitive. Future studies integrating DNA methylation with gene expression or other multi‐omics data will be necessary to validate the regulatory consequences of the methylation changes observed here.

  A limitation of this study is the lack of harmonized, sample‐level demographic and clinical covariates across the public datasets, including age, sex, and quantitative measures of disease severity or inflammation. Although age and sex were reported for GSE53849, these variables were not consistently available for GSE59932 and GSE59939, and clinical indices (e.g., CAL, probing depth, and bleeding on probing) were not provided in a unified format across studies. Accordingly, covariate‐adjusted modeling could not be applied uniformly in the integrated analysis and should be addressed in future studies with standardized metadata. Therefore, the threshold‐based categorization was applied for interpretability and hypothesis generation, and is not intended to replace continuous differential methylation analysis based on linear modeling.


## Conclusions
  In conclusion, our comprehensive epigenome‐wide DNA methylation analysis revealed that periodontitis is associated with widespread, yet selective, methylation changes within the genomic regions interrogated by the Illumina HumanMethylation450 BeadChip, with a substantial proportion of significant sites observed in OpenSea regions and TSS‐proximal regions (TSS200 and TSS1500). This distribution pattern contrasts with the classical cancer epigenetic model where promoter CpG island hypermethylation is prevalent. Notably, the study identified multiple genes, such as RUNX2, DGKA, CFTR, RGS1, PADI2, and FOXK1, whose methylation status and GO enrichment suggest potential roles in tissue remodeling, immune regulation, and epithelial barrier function during periodontal inflammation.

  These findings highlight the distinct epigenetic landscape of chronic inflammatory diseases like periodontitis and emphasize the importance of gene body and non‐CpG island methylation as regulatory mechanisms beyond traditional promoter silencing. Our results provide a valuable basis for future multi‐omics studies aiming to integrate DNA methylation with gene expression to further elucidate functional implications in periodontal disease pathogenesis. These findings not only provide new insights into the epigenetic landscape of periodontitis but also suggest that specific differentially methylated genes, such as RUNX2, PADI2, and RGS1, may serve as candidates for biomarker development, to be confirmed by future functional and clinical validation.


## Author Contributions
  Koki Yoshida: data extraction, processing, formal analyses, data interpretation, draft writing and critical revision of the manuscript. Gowri Sivaramakrishnan: data extraction and processing. Farah Asa'ad: conceptualization, manuscript editing and critical revision of the manuscript.


## Funding
  The authors received no specific funding for this work.


## Ethics Statement
  The authors have nothing to report.


## Consent
  The authors have nothing to report.


## Conflicts of Interest
  The authors declare no conflicts of interest.


## Data Availability Statement
  The DNA methylation datasets analyzed in the current study are publicly available in the Gene Expression Omnibus (GEO) under accession numbers GSE53849, GSE59932, and GSE59939.

  All processed data, annotation results, R scripts, and supplementary datasets used to generate Figures 1–3 and Tables 1–3 are available on Figshare at: https://doi.org/10.6084/m9.figshare.29429705.

  The Figshare repository is publicly accessible and contains all supplementary datasets associated with this study.


## Acknowledgments
  The authors have nothing to report.