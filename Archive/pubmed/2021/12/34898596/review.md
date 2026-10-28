## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present CoRE-ATAC, a deep learning framework that integrates DNA sequence and ATAC-seq chromatin accessibility data to classify cis-regulatory elements (promoters, enhancers, insulators, other) in both bulk and single-cell ATAC-seq datasets. The model is trained on four cell types and evaluated on held-out cell types, demonstrating generalizability, concordance with orthogonal functional assays (MPRA, STARR-seq, CAGE), and utility for single-nucleus ATAC-seq data.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Materials and Methods sections as provided
- **Missing materials affecting confidence** Figures and supporting information (S1-S21 Figs) are referenced but not provided; specific numerical results for some comparisons are not fully detailed; code availability is stated but not verified

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially useful computational tool for functional annotation of ATAC-seq peaks. The integration of sequence and accessibility data with a deep learning architecture is a reasonable approach, and the evaluation across multiple cell types and assays is commendable. However, several technical aspects require clarification and additional validation to fully establish the method's utility and robustness, particularly regarding the novelty of the architecture, the handling of single-cell data sparsity, and the interpretation of the MPRA concordance analysis.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and epigenomics who work with ATAC-seq data and seek functional annotation of open chromatin regions. The tool's ability to work with both bulk and single-cell data, and its potential for personalizing predictions using genotype information, would be of interest to those studying disease-associated regulatory variation.
- **Major strengths**
  1. The manuscript addresses a clear and important need: functional interpretation of ATAC-seq peaks, which are abundant but functionally ambiguous.
  2. The model architecture integrates multiple data modalities (sequence, cut sites, read pileups) in a novel way, and the inclusion of genotype information is a forward-looking feature.
  3. The evaluation strategy is thorough, including held-out cell types, comparisons with alternative methods, and validation against multiple orthogonal experimental datasets (CAGE, STARR-seq, MPRA).
  4. The demonstration of applicability to single-nucleus ATAC-seq data is a significant contribution, as this is a rapidly growing data type.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that CoRE-ATAC's novel data encoders integrate DNA sequence with ATAC-seq cut sites and read pileups to achieve superior performance.
  - **Evidence pointer** Results section, Figures 2D and S7
  - **Concern** The comparison with alternative methods (DeepSEA, LS-GKM) is limited to enhancer versus "other" classification. The manuscript does not report comparisons for promoter or insulator classification, nor does it provide statistical significance testing for the observed performance differences. Furthermore, the hyperparameter tuning procedure is described as a sequential one-at-a-time approach, which may not find a globally optimal configuration and could bias the comparison against other methods.
  - **Why it matters** The central claim of the paper is that CoRE-ATAC provides improved functional classification. Without a comprehensive and statistically rigorous comparison, it is unclear whether the observed improvements are robust or specific to the chosen evaluation setup.
  - **Resolution test** Provide performance comparisons for all four classes (promoter, enhancer, insulator, other) with statistical significance tests (e.g., bootstrapped confidence intervals or DeLong test for AUC). Describe the hyperparameter search in more detail, or use a more systematic approach such as random search or Bayesian optimization.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that CoRE-ATAC can predict individual-level variability in cis-RE activity, including genetically modulated gain/loss of enhancer activity confirmed by MPRA.
  - **Evidence pointer** Results section, Figures 4C, 4D, and S15
  - **Concern** The MPRA concordance analysis identifies 237 loci with predicted gain/loss of enhancer activity based on genotype. However, the manuscript does not report the total number of loci tested, the false discovery rate, or the effect sizes. The example in Figure 4D shows a single locus, and the statement that "the direction of effect coincides" is not quantified. It is unclear how many of the 237 predictions were confirmed by MPRA and whether this is significantly better than chance.
  - **Why it matters** This is a key validation of the model's ability to capture genotype-dependent regulatory effects, which is a unique and important feature. Without rigorous statistical assessment, the claim of concordance is not fully supported.
  - **Resolution test** Report the total number of loci with genotype information, the number of significant MPRA hits, and a confusion matrix or enrichment statistic (e.g., odds ratio with confidence intervals) for the concordance between predicted and observed direction of effect. Provide a permutation-based null model to assess significance.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The claim that CoRE-ATAC effectively infers cis-RE function from aggregate single-nucleus ATAC-seq data.
  - **Evidence pointer** Results section, Figures 5C, 5D, and S16
  - **Concern** The performance on snATAC-seq data is lower (mean micro-average precision = 0.68, F1 = 0.41) compared to bulk data. The manuscript attributes this to differences in data processing but does not investigate the sources of error. For example, it is unclear whether the model's performance varies by cell type or by the number of cells per cluster. The comparison with ChromHMM annotations from "closest reference" cell types is also potentially problematic, as mismatches in cell type identity could lead to underestimated performance.
  - **Why it matters** The applicability to single-cell data is a major selling point of the manuscript. A more detailed error analysis would help users understand the limitations and potentially guide improvements.
  - **Resolution test** Provide per-cell-type performance metrics and analyze whether performance correlates with cluster size or data quality. Discuss the potential impact of using "closest reference" ChromHMM annotations and consider sensitivity analyses with alternative reference mappings.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and reproducibility
  - **Affected element** Methods section, ATAC-seq data encoders
  - **Evidence pointer** Materials and Methods, "ATAC-seq data encoders"
  - **Issue** The description of the 10x600 matrix is brief. It is unclear how the "10" rows are defined and how the cut sites and read pileups are normalized across samples with different sequencing depths.
  - **Required correction** Provide a more detailed description of the matrix construction, including the specific data tracks, normalization procedures, and how genotype information is incorporated.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Clarity and reproducibility
  - **Affected element** Methods section, Ground truth selection
  - **Evidence pointer** Materials and Methods, "Ground truth selection& model training"
  - **Issue** The process of converting 15-state and 18-state ChromHMM models to the four classes is described, but the specific mapping rules are not fully detailed. The statement "based on emission probability correlations" is vague.
  - **Required correction** Provide a table or explicit list of which ChromHMM states map to which of the four classes (promoter, enhancer, insulator, other).
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, SNP enrichment analysis
  - **Evidence pointer** Results section, "Predicting disease-relevant enhancers from single nuclei ATAC-seq data"
  - **Issue** The SNP enrichment analysis using GREGOR is described qualitatively. The manuscript states that enhancers are "enriched" for relevant diseases but does not report enrichment p-values or effect sizes.
  - **Required correction** Report the GREGOR enrichment p-values and odds ratios for the key disease-cell type pairs mentioned (e.g., B cells and Systemic Lupus, islets and Type 2 Diabetes).
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The Discussion would benefit from a more explicit statement of the method's limitations, particularly regarding the reliance on ChromHMM as ground truth, which is itself a computational prediction.
  - **Required correction** Add a paragraph explicitly discussing the limitations of using ChromHMM states as ground truth and the potential impact of errors in these annotations on model training and evaluation.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking concerns. The lack of comprehensive and statistically rigorous comparisons with alternative methods, and the insufficiently quantified MPRA concordance analysis, prevent the manuscript from fully establishing its claims of improved performance and genotype-aware prediction.
- **Assessment against Nature-style criteria**
  - **Originality** The integration of sequence and accessibility data with a deep learning architecture, particularly the inclusion of genotype information, is a novel contribution. However, the overall concept of using machine learning for regulatory element classification is not entirely new, and the manuscript should more clearly differentiate itself from prior work beyond PEAS.
  - **Scientific importance** The ability to functionally annotate ATAC-seq peaks, especially from single-cell data, is of high importance to the genomics community. The potential for personalized predictions is also significant.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and epigenomics researchers. The manuscript is written in a way that is accessible to this audience, but may be less accessible to a broader biological audience without a computational background.
  - **Technical soundness** The overall approach is sound, but the evaluation has gaps as detailed in the major concerns. The lack of statistical rigor in key comparisons and validations is a weakness.
  - **Readability for nonspecialists** The manuscript is generally well-written and the figures (as described) appear to be informative. However, the methods section is dense and may be challenging for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially valuable tool, but the blocking concerns regarding the rigor of the performance comparison and the MPRA validation must be addressed before the claims can be fully accepted.

## Risk / unsupported claims
- The claim that CoRE-ATAC is the "best performing model" for enhancer prediction is not fully supported due to the limited comparison and lack of statistical testing.
- The claim of concordance with MPRA is not quantified and may be based on a subset of loci without appropriate multiple testing correction.
- The claim that the model can be used to study cis-regulatory elements in rare cells without sorting is supported by the snATAC-seq analysis, but the lower performance on this data type and the lack of per-cell-type analysis limit the strength of this claim.
- The statement that CoRE-ATAC "increases the functional resolution" of ATAC-seq maps is a reasonable interpretation but is not directly measured in the manuscript.