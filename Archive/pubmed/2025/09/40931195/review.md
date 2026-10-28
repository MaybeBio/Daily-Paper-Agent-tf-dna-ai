## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and support for claims; not editorial or formatting issues
- **Shared manuscript claim summary** The authors performed single-cell ATAC-seq and RNA-seq on mouse vascular tissue from three sites (ascending aorta/aortic root, brachiocephalic/carotid artery, descending thoracic aorta) and report that chromatin accessibility and gene expression are vascular site-specific within cell types, reflect developmental origin, and relate to disease risk loci. They further trained ChromBPNet models per cell type and vascular site to predict variant effects on chromatin accessibility, identifying site-specific effects and enriched TF motifs.
- **Visible evidence base** Main text figures 1-8, supplementary figures S1-S7, datasets EV1-EV25, methods section
- **Missing materials affecting confidence** Raw sequencing data files, complete analysis code, detailed quality control metrics, full list of differentially accessible peaks and genes, complete GWAS variant scoring results, and validation datasets were not provided in the manuscript text

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive single-cell epigenomic and transcriptomic atlas of three vascular sites in the mouse aorta, with a novel application of ChromBPNet to predict variant effects in a cell type and vascular site-specific manner. The dataset is substantial and the integration of scATAC-seq, scRNA-seq, GRN inference, and deep learning-based variant effect prediction is ambitious and potentially valuable. The observation that vascular site-specific chromatin accessibility reflects developmental origin and relates to disease risk is conceptually interesting. However, several technical concerns regarding data processing, statistical rigor, and the interpretation of the ChromBPNet results need to be addressed before the conclusions are fully supported.
- **Who would be interested in the results, and why** Vascular biologists, cardiovascular geneticists, and researchers studying gene regulation and epigenomics. The single-cell atlas of vascular cells across sites will be a useful resource. The application of ChromBPNet to predict variant effects in a cell type and site-specific manner is of interest to those studying the functional interpretation of GWAS variants. The developmental memory concept is relevant to developmental biologists.
- **Major strengths** 1) A large, multi-omic single-cell dataset from three vascular sites, providing a valuable resource. 2) The demonstration of vascular site-specific chromatin accessibility and gene expression within cell types is a significant finding. 3) The novel application of ChromBPNet to predict variant effects in a site-specific manner is a methodological advance. 4) The integration of GWAS data with single-cell epigenomics provides a framework for understanding disease risk.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "we predicted variant effects across cell type and vascular site of origin, revealing genomic regions enriched for specific TF motif footprints—including MEF2A, SMAD3, and HAND2."
  - **Evidence pointer** Figure 8, Methods section "ChromBPNet"
  - **Concern** The ChromBPNet models were trained on mouse ATAC-seq data but applied to human GWAS variants. The manuscript does not adequately address how cross-species differences in genome sequence and regulatory architecture affect the validity of these predictions. The models are trained on mouse reference genome (mm10) and the variant scoring is performed on human variants. The authors state this is a "genome-agnostic" approach, but this is not clearly explained or validated. The lack of a clear description of how the human variants are mapped to the mouse genome and how the models are applied to human sequences is a major gap.
  - **Why it matters** The central claim of the paper, that GWAS variants have vascular site-specific effects on chromatin accessibility, rests on the validity of these cross-species predictions. If the models are not correctly applied or validated, the conclusions about variant effects and TF motif enrichment are not supported.
  - **Resolution test** The authors should provide a detailed description of how the human variants are processed and scored with the mouse-trained models. They should also provide validation, such as showing that the models can predict known eQTL effects or that the predicted variant effects correlate with independent functional assays. A clear explanation of the "genome-agnostic" nature of the model is required.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor
  - **Claim pointer** The authors state that "we identified 469 high scoring aorta diameter LD-expanded GWAS variants across all of the vascular site datasets" and that "84 of 115 loci (73%)... to have either lead SNPs or SNPs in LD with the lead variant to be predicted to have vascular site-specific effect in SMCs."
  - **Evidence pointer** Figure 8B-H, Methods section "Predicting variant effects using ChromBPNet models"
  - **Concern** The criteria for "high scoring" and "vascular site-specific effect" are not clearly defined. The authors use a "top 1% of deviant SNPs" based on linear regression residuals, but the statistical significance of this deviation is not rigorously established. The empirical P values for the variant effect scores are mentioned, but the threshold for significance is not stated. The comparison of variant effects between cell types and vascular sites appears to be based on visual inspection of scatter plots rather than formal statistical testing.
  - **Why it matters** Without clear statistical thresholds and formal tests for differences between conditions, the claims of site-specific variant effects are not quantitatively supported. The reader cannot assess the robustness of the findings.
  - **Resolution test** The authors should define the criteria for "high scoring" variants and "vascular site-specific effect" with specific statistical thresholds. They should perform formal statistical tests to compare variant effect scores between cell types and vascular sites, accounting for multiple testing. The empirical P value thresholds should be stated.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "we discovered key regulatory enhancers to not only be cell type, but vascular site-specific" and that "epigenomic patterns of vascular SMCs are cell type and vascular site-specific."
  - **Evidence pointer** Figures 1-3, Methods section "scATACseq"
  - **Concern** The analysis of differentially accessible peaks between vascular sites within a cell type is performed on pooled cells from multiple mice (two sets of 8 mice). The manuscript does not describe how biological variability between mice is accounted for in the differential accessibility analysis. The use of a single pooled sample per site (or two pooled samples) may lead to false positives due to inter-individual variation.
  - **Why it matters** The core finding of site-specific epigenomic differences could be confounded by biological variation between animals. The lack of replication at the level of individual mice undermines the statistical confidence in the identified differentially accessible peaks.
  - **Resolution test** The authors should describe how biological replicates are handled in the analysis. If cells are pooled, they should acknowledge this limitation and ideally validate key findings with an independent method, such as bulk ATAC-seq on individual mice, or use a mixed-effects model that accounts for the mouse of origin.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors state that "This work supports a paradigm that cell type and vascular site-specific enhancers govern complex genetic drivers of disease risk."
  - **Evidence pointer** Figures 7-8, Discussion
  - **Concern** The link between the identified site-specific enhancers and disease risk is largely correlative. The GWAS enrichment analysis shows that disease-associated genes are differentially expressed, but the manuscript does not demonstrate a causal link between specific enhancers, variants, and disease. The ChromBPNet predictions are not experimentally validated.
  - **Why it matters** The paradigm claim is strong and would require functional evidence, such as CRISPR-based perturbation of specific enhancers or validation of variant effects in relevant cell types, to be fully supported.
  - **Resolution test** The authors should temper the strength of the claim or provide additional evidence, such as demonstrating that a specific variant alters enhancer activity in a reporter assay in a site-specific manner, or that deletion of a specific enhancer affects gene expression in a relevant cell type.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction and Discussion
  - **Evidence pointer** Introduction, Discussion
  - **Issue** The manuscript uses a lot of jargon and assumes a high level of familiarity with single-cell genomics and GWAS analysis. The significance of the findings could be made more accessible to a broader audience.
  - **Required correction** Consider adding a brief explanation of key concepts such as "chromatin accessibility," "enhancers," and "GWAS" for readers who may not be specialists in these areas.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "Mice and microdissections"
  - **Evidence pointer** Methods section
  - **Issue** The manuscript states that "two sets of 8 mice (16 mice total) were used to obtain two single-cell suspensions for each vascular tissue." It is unclear if these two sets are true biological replicates or if they were processed in separate batches. The potential for batch effects is not discussed.
  - **Required correction** Clarify the experimental design and discuss how batch effects were addressed, if at all.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Figure 8J
  - **Evidence pointer** Figure 8J
  - **Issue** The GTEx eQTL data for rs11677932 is shown as a boxplot, but the number of samples and the tissue type are not clearly indicated in the figure legend.
  - **Required correction** Provide more detail in the figure legend about the GTEx data, including the tissue type and sample size.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "scRNAseq"
  - **Evidence pointer** Methods section
  - **Issue** The methods for scRNA-seq data analysis are described briefly. The parameters used for clustering, normalization, and batch correction are not fully detailed.
  - **Required correction** Provide more specific details on the parameters used in Seurat, such as the number of principal components, resolution, and the specific functions used for batch correction.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Figure 2A
  - **Evidence pointer** Figure 2A
  - **Issue** The volcano plot in Figure 2A shows differentially accessible peaks, but the thresholds for significance (fold change and adjusted P value) are not stated in the figure legend.
  - **Required correction** Add the thresholds used to define differentially accessible peaks to the figure legend.

## Technical failings that need to be addressed before the case is established
- R1-M1: Cross-species application of ChromBPNet models is not adequately described or validated.
- R1-M2: Statistical criteria for defining "high scoring" and "site-specific" variant effects are not clearly defined.
- R1-M3: Biological replication in the differential accessibility analysis is not adequately addressed.

## Risk / unsupported claims
- The claim that "genetic variants that influence aortic dimension appear to regulate chromatin accessibility in not only a cell type, but also a vascular site-specific mechanism" is not fully supported due to the lack of validation of the cross-species ChromBPNet predictions and the absence of formal statistical tests for site-specific effects.
- The claim of an epigenetic "priming" for fibroblast activation based on the discrepancy between chromatin accessibility and RNA expression for Meox1 is speculative and not directly tested.
- The statement that "this work supports a paradigm that cell type and vascular site-specific enhancers govern complex genetic drivers of disease risk" is a strong conclusion that is not fully supported by the correlative data presented.

## Assessment against Nature-style criteria
- **Originality** The work is original in its combination of single-cell multi-omics with deep learning-based variant effect prediction across vascular sites. The concept of a "developmental memory" in adult vascular cells is not entirely new but is applied here in a novel context.
- **Scientific importance** The findings are potentially important for understanding vascular site-specific disease susceptibility and for interpreting GWAS loci. The resource generated will be valuable to the community. However, the lack of functional validation limits the immediate impact.
- **Interdisciplinary readership** The work will appeal to a specialized audience of vascular biologists, epigenomicists, and computational biologists. The methods and findings may be less accessible to a broader readership.
- **Technical soundness** The single-cell data generation and initial processing appear sound, but the statistical rigor of the differential analysis and the cross-species application of ChromBPNet are significant concerns. The lack of validation experiments weakens the technical soundness of the main claims.
- **Readability for nonspecialists** The manuscript is dense and uses specialized terminology, making it difficult for nonspecialists to follow. The main concepts and significance could be explained more clearly.

## Recommendation posture
**Currently not established from the provided evidence.** The manuscript presents a valuable dataset and an interesting conceptual framework, but the major claims regarding vascular site-specific variant effects are not fully supported due to concerns about the cross-species application of ChromBPNet, the lack of clear statistical thresholds, and the absence of functional validation. The authors should address these technical concerns and provide additional evidence to support their conclusions.