## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2025)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No external data or supplementary files were assessed.
- **Shared manuscript claim summary** The authors present single-cell chromatin accessibility (scATACseq) and transcriptomic (scRNAseq) profiles of healthy adult mouse vascular tissue from three vascular sites (ascending aorta/aortic root, brachiocephalic/carotid, descending thoracic aorta). They report cell type- and vascular site-specific epigenomic and transcriptomic patterns, identify developmental transcription factor signatures (e.g., Tbx20, Hand2, Gata4, Hox family), demonstrate functional retention of site-specific TGFβ responses in cultured primary adventitial fibroblasts, and integrate human aortic dimension GWAS data with ChromBPNet models to predict variant effects in a cell type- and site-specific manner.
- **Visible evidence base** Main text, figures referenced (Fig 1–8, Fig S1–S6), tables referenced (Table S1–S25), Methods section.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S25) were not provided. Figure panels referenced in the text were not viewable. Specific numerical values for enrichment statistics, effect sizes, and quality control metrics were not fully reported in the text. Details of the ChromBPNet training hyperparameters and cross-validation performance metrics were not fully described.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question: whether vascular site-specific disease susceptibility is reflected in cell type-specific epigenomic and transcriptomic programs. The study design is comprehensive, combining scATACseq, scRNAseq, integrative analysis, functional validation in primary cells, and GWAS integration with deep learning. The data presented support the central claim that vascular cells retain site-specific epigenomic memory related to developmental origin. However, several technical and analytical concerns need to be addressed to fully establish the case, particularly regarding the statistical robustness of the differential analyses, the interpretation of the ChromBPNet results, and the strength of the GWAS enrichment claims.
- **Who would be interested in the results, and why** Vascular biologists, cardiovascular geneticists, and researchers studying gene regulation and epigenomics. The atlas of vascular site-specific regulatory elements will be a valuable resource. The demonstration of developmental memory in adult vascular cells and its link to disease risk loci has implications for understanding atherosclerosis, aneurysm, and potential therapeutic targeting.
- **Major strengths**
  1. Comprehensive multi-omic single-cell dataset across three clinically relevant vascular sites.
  2. Integration of chromatin accessibility, transcriptomics, and gene regulatory network inference.
  3. Functional validation of site-specific TGFβ responses in primary fibroblasts, strengthening the biological relevance of the epigenomic findings.
  4. Novel application of ChromBPNet to predict variant effects in a cell type- and vascular site-specific manner, linking epigenomics to human GWAS.
  5. Clear writing and logical flow from descriptive atlas to mechanistic and translational insights.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor and reproducibility
  - **Claim pointer** The authors claim thousands of differentially accessible peaks and differentially expressed genes between vascular sites within cell types (e.g., 4,805 peaks for SMC ascending vs descending; 1,342 DE genes in fibroblasts).
  - **Evidence pointer** Results sections "Epigenomic patterns of vascular SMCs..." and "Fibroblast cell subset analysis..."; Figures 2A, 3A; Tables S1, S8, S20.
  - **Concern** The manuscript does not report key statistical parameters for these differential analyses. What was the exact model used (e.g., negative binomial, MAST, Wilcoxon)? How were confounding factors such as sequencing depth, capture efficiency, and biological variability between the two pooled biological replicates (two sets of 8 mice) handled? Were the two replicates treated as independent samples or pooled? The lack of detail on the number of biological replicates per site and the statistical model precludes assessment of the robustness of the claimed effect sizes and p-values. For scATACseq, the use of "FindMarker" with number of peaks as a latent variable is mentioned, but the significance threshold and multiple testing correction method are not stated.
  - **Why it matters** The central claim of site-specific epigenomic and transcriptomic differences rests entirely on these differential analyses. Without clear statistical methodology and demonstration of reproducibility across biological replicates, the findings could be driven by technical artifacts or insufficient power.
  - **Resolution test** Provide a detailed description of the statistical models used for both scRNAseq and scATACseq differential analyses, including the formula, covariates, and multiple testing correction. Report the number of biological replicates per site and show that the differential signals are consistent across replicates (e.g., via split-replicate analysis or showing effect sizes with confidence intervals). For key claims, provide effect size distributions and volcano plots.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional validation and causal inference
  - **Claim pointer** The authors state that "differential chromatin accessibility appears to 'prime' vascular site-specific gene regulatory networks in disease relevant mechanisms" and that the TGFβ response in fibroblasts is dependent on vascular site, implicating "functional epigenomic memory."
  - **Evidence pointer** Results section "Primary adventitial fibroblast response to TGFβ..."; Figure 6.
  - **Concern** The in vitro fibroblast experiment is a key functional validation. However, the manuscript does not report the passage number of the fibroblasts used, the purity of the fibroblast cultures (contamination with other cell types such as endothelial or SMC), or the number of biological replicates for the RNAseq experiment (n=3 per condition is mentioned, but are these from independent mice or technical replicates from pooled cells?). The claim of "epigenomic memory" is inferred from retained transcriptomic differences after 3 passages, but no direct measurement of chromatin state (e.g., ATACseq or histone marks) is performed on the cultured cells. The link between the observed transcriptomic differences and the specific epigenomic differences identified in the primary tissue is correlative.
  - **Why it matters** The functional experiment is crucial to move beyond descriptive epigenomics. If the culture system is not well-defined or the link to chromatin state is not directly tested, the claim of "epigenomic memory" is overstated.
  - **Resolution test** Provide details on fibroblast culture characterization (purity, passage). Clarify the replication structure of the RNAseq experiment. To strengthen the "memory" claim, perform ATACseq or targeted chromatin analysis on the cultured fibroblasts to directly demonstrate retention of site-specific chromatin accessibility. Alternatively, temper the claim to "retained transcriptomic differences" and discuss the potential mechanisms.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** GWAS integration and variant effect prediction
  - **Claim pointer** The authors claim that aortic dimension GWAS genes are enriched in differentially expressed genes between vascular sites, and that ChromBPNet predicts variant effects in a cell type- and vascular site-specific manner, highlighting specific loci (e.g., ANGPT1, COL6A3).
  - **Evidence pointer** Results sections "Aortic dimension GWAS identifies genes..." and "ChromBPnet predicts..."; Figure 7, 8.
  - **Concern** The enrichment analysis for GWAS genes in DE gene lists appears to be based on the nearest gene to each GWAS locus. This is a simplistic approach that can be misleading. How were the random gene sets generated for comparison? Were they matched for gene size, expression level, or other confounders? For the ChromBPNet analysis, the manuscript states that models were trained on mouse data and applied to human variants. The "genome-agnostic" claim is interesting, but the validation of this cross-species application is not described. How were the 9 models (3 cell types x 3 sites) validated? What is the performance (e.g., AUROC) on held-out chromosomes? The p-values for variant effects are derived from empirical null distributions, but the manuscript does not report how many of the 27,556 variants achieved significant p-values, nor the false discovery rate.
  - **Why it matters** The translational relevance of the study hinges on the link between mouse epigenomics and human disease genetics. If the GWAS enrichment is not robust or the ChromBPNet cross-species predictions are not validated, the conclusions about site-specific variant effects are not supported.
  - **Resolution test** Provide a more rigorous GWAS enrichment analysis, e.g., using LD-based gene mapping or a stratified LD score regression approach. For ChromBPNet, report model performance metrics (e.g., AUROC, AUPRC) on test chromosomes for each of the 9 models. Describe the validation of cross-species application, perhaps by comparing predictions to human vascular cell ATACseq data if available. Report the number of significant variants and the FDR threshold used.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of developmental origin
  - **Claim pointer** The authors attribute site-specific epigenomic differences to developmental origin (secondary heart field, neural crest, somitic mesoderm).
  - **Evidence pointer** Abstract, Introduction, Discussion.
  - **Concern** While the correlation between developmental origin and site-specific patterns is plausible, the manuscript does not directly test this hypothesis. The observed differences could also be due to other factors such as hemodynamic forces, local paracrine signaling, or differences in cell maturation. The authors mention that culturing fibroblasts removes hemodynamic effects, but this does not exclude other environmental influences. The claim of a "developmental 'memory'" is an interpretation, not a demonstrated mechanism.
  - **Why it matters** The developmental memory hypothesis is a major conceptual framework of the paper. Overstating this link without direct evidence (e.g., lineage tracing, chromatin analysis of embryonic precursors) could mislead the field.
  - **Resolution test** Soften the language to "consistent with" developmental origin. Discuss alternative explanations. If possible, perform a more direct test, such as comparing the identified site-specific signatures to published data from embryonic vascular progenitors.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness of methods
  - **Affected element** Methods, "Analysis of Single-Cell Sequencing Data"
  - **Evidence pointer** Methods section.
  - **Issue** The methods for scRNAseq and scATACseq analysis are described at a high level. Specific parameters for clustering (e.g., number of principal components, resolution), marker gene identification, and data normalization are not fully detailed.
  - **Required correction** Provide a more detailed description of the computational pipeline, including software versions, parameters, and thresholds. Consider including a supplementary methods file or a table of key parameters.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Figure quality and data presentation
  - **Affected element** Figures 1–8
  - **Evidence pointer** Figure legends and text.
  - **Issue** The text references many figures and supplementary tables, but the figures themselves were not available for review. The legends are not provided in the text. It is difficult to assess the quality of the data presentation.
  - **Required correction** Ensure that all figures are clearly labeled, with comprehensive legends that allow the reader to understand the data without referring to the main text. Consider including key data points (e.g., effect sizes, p-values) directly on the figures.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology and consistency
  - **Affected element** Abstract, Results, Discussion
  - **Evidence pointer** Throughout.
  - **Issue** The terms "epigenomic memory," "priming," and "developmental memory" are used somewhat interchangeably. The distinction between these concepts should be clarified.
  - **Required correction** Define these terms clearly in the introduction or discussion and use them consistently throughout the manuscript.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Limitations and future directions
  - **Affected element** Limitations section
  - **Evidence pointer** Limitations section.
  - **Issue** The limitations section is brief and does not discuss the potential for cell-type heterogeneity within the dissected vascular sites (e.g., presence of adventitial vs. medial fibroblasts), the use of only male mice, or the lack of validation in human tissue.
  - **Required correction** Expand the limitations section to address these points and discuss how they might affect the interpretation of the results.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of detailed statistical methodology for differential analyses.
  - R1-M2: Insufficient detail on the functional validation experiment and overinterpretation of "epigenomic memory."
  - R1-M3: Inadequate description of GWAS enrichment and ChromBPNet validation.
- **Assessment against Nature-style criteria**
  - **Originality** High. The study provides a novel single-cell atlas of vascular site-specific epigenomic and transcriptomic programs and links them to developmental origin and disease risk. The application of ChromBPNet to predict variant effects in a site-specific manner is innovative.
  - **Scientific importance** High. The findings have significant implications for understanding the molecular basis of vascular site-specific disease susceptibility, which is a long-standing clinical observation. The identification of site-specific regulatory elements and potential master regulators (e.g., Meox1) could inform future therapeutic strategies.
  - **Interdisciplinary readership** Moderate to high. The work will appeal to cardiovascular researchers, epigenomicists, computational biologists, and geneticists. The integration of multiple techniques (single-cell omics, GWAS, deep learning) broadens its appeal.
  - **Technical soundness** Currently not fully established. The core descriptive analyses appear sound, but the lack of statistical detail and validation for key claims (especially the functional and GWAS integration parts) prevents a full assessment.
  - **Readability for nonspecialists** Good. The manuscript is well-written and the logical flow is clear. The abstract and introduction effectively set the stage. However, the results section is dense and may be challenging for readers not familiar with single-cell genomics and deep learning.
- **Recommendation posture** Supportive if technical concerns are resolved. The study addresses a fundamental question in vascular biology and presents a valuable resource. However, the major concerns regarding statistical rigor, functional validation, and GWAS integration must be adequately addressed before the claims are fully established. The authors should provide the missing methodological details and, where possible, strengthen the evidence for the "epigenomic memory" and site-specific variant effect hypotheses.

## Risk / unsupported claims
- The claim of "epigenetic 'priming'" for fibroblast activation is inferred from correlative data and requires direct experimental evidence.
- The statement that "site-specific enhancers govern complex genetic drivers of disease risk" is a strong conclusion that is not directly tested. The data show association, not causation.
- The enrichment of GWAS genes in DE gene lists is based on a "nearest gene" approach, which is a weak proxy for causal gene mapping. The claim of enrichment is therefore not robustly supported.
- The cross-species application of ChromBPNet (mouse training, human variant prediction) is a key claim, but the validation of this approach is not described, making the predictions unverifiable from the provided text.