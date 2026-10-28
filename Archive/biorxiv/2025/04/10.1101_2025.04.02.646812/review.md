## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and supplementary figure references
- **Assessment boundary** Scientific content, methodological rigor, validation strength, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present CREsted, a Python software package for end-to-end modeling, interpretation, and design of cell type-specific enhancers from scATAC-seq data. They demonstrate its utility across multiple biological systems (mouse cortex, human PBMC, cancer cell lines, zebrafish development), validate predicted TFBS against ChIP-seq and in vivo data, and show that CREsted models can outperform large pre-trained models like Borzoi on cell type-specific tasks.
- **Visible evidence base** Results sections describing model performance metrics (correlations, precision/recall), in vivo validation of synthetic enhancers in zebrafish, comparisons against gR eLU and Borzoi models, and methodological descriptions in the Methods section
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; detailed benchmark results tables; exact hyperparameter configurations; code execution outputs; statistical test details for some comparisons; full details of the in vivo validation results

## Reviewer
- **Overall assessment** This manuscript describes a timely and potentially valuable software package for enhancer modeling from scATAC-seq data. The breadth of applications across species and tissues is impressive, and the in vivo validation of designed enhancers in zebrafish is a strong contribution. However, the manuscript currently reads more as a software demonstration with multiple case studies rather than a focused scientific advance. Several key claims, particularly regarding superiority over existing methods and the biological insights derived, require stronger quantitative support and clearer presentation. The package itself appears well-designed and addresses a genuine need in the field, but the manuscript would benefit from sharper hypotheses and more rigorous benchmarking to establish its distinct contribution.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those developing or applying deep learning models to enhancer function. Researchers studying cell type-specific gene regulation in development and disease, especially in the contexts of brain, immune cells, and cancer. The zebrafish enhancer design component will interest researchers using zebrafish as a model system for enhancer validation. The software package itself will be of practical use to the broader genomics community seeking accessible tools for enhancer modeling.

- **Major strengths**
  1. Comprehensive software package addressing the full pipeline from data preprocessing to enhancer design, integrated into the scverse ecosystem
  2. Demonstration across multiple diverse biological systems and species, showing versatility
  3. In vivo validation of designed synthetic enhancers in zebrafish, providing functional evidence
  4. Comparison with existing methods (gReLU, Borzoi) and demonstration of competitive or superior performance
  5. Novel peak-scaling normalization approach that addresses a real technical challenge
  6. Open-source availability with documentation and reproducibility resources

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that CREsted models outperform large pre-trained models like Borzoi on cell type-specific chromatin accessibility predictions
- **Evidence pointer** Results section "CREsted-trained models outperform large, pre-trained models on cell type-specific chromatin accessibility predictions", Figures 5b, 5c, S12, S13
- **Concern** The comparison between CREsted-trained models and Borzoi may not be entirely fair or complete. The base Borzoi model was pre-trained on a different data distribution and for different tasks, and the comparison uses only a subset of Borzoi's output classes (19 mouse cortex classes). The manuscript does not clearly state whether the base Borzoi model was evaluated on the same test sets with identical preprocessing, nor whether the performance metrics account for the different training data volumes. Additionally, the claim of "outperforming" is based on mean correlation values, but the statistical significance of these differences is not fully reported for all comparisons.
- **Why it matters** The central claim of the paper's benchmarking section is that CREsted provides superior performance to existing large models. If this comparison is not rigorously controlled, the conclusion may be overstated and could mislead users in model selection.
- **Resolution test** Provide a detailed comparison table with per-class correlation values, confidence intervals, and statistical tests for all model comparisons. Clearly describe the evaluation protocol, including whether identical preprocessing, test sets, and class subsets were used. Consider evaluating on additional independent datasets to strengthen generalizability claims.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The claim that CREsted enables "scrutinization of the enhancer logic" and provides biological insights into cell type-specific regulation
- **Evidence pointer** Results sections on mouse cortex and PBMC models, Figures 2f-g, 3a-d, S3, S5-S9
- **Concern** While the authors demonstrate that CREsted can identify known TFBS and motifs, the biological novelty of the insights derived is not clearly established. The identified motifs largely recapitulate known regulators (e.g., TBR1, NFI for deep layer neurons; SPI1, IRF for microglia). The manuscript would be strengthened by demonstrating that CREsted can uncover previously unknown regulatory mechanisms or provide quantitative predictions that lead to testable hypotheses beyond what is already known. The in silico mutation analysis of the SstChodl enhancer is interesting but represents a single example.
- **Why it matters** The scientific impact of the work depends on whether CREsted enables new biological discoveries, not just recapitulation of known biology. Without clear evidence of novel insights, the contribution may be seen as primarily technical.
- **Resolution test** Provide at least one or two examples where CREsted predictions led to previously unknown regulatory mechanisms or novel candidate regulators that were subsequently validated. Alternatively, demonstrate systematic discovery of new enhancer grammar rules that go beyond known motif combinations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that the peak-scaling normalization improves cross-cell type comparability of chromatin accessibility
- **Evidence pointer** Methods section "CREsted workflow", Figure S1
- **Concern** The peak-scaling normalization approach relies on the assumption that housekeeping gene promoters should have equal accessibility across cell types. While the authors provide some evidence supporting this (Figure S1), the assumption may not hold universally, particularly for genes with cell type-specific functions or in pathological states. The manuscript does not thoroughly discuss the limitations of this assumption or provide sensitivity analyses.
- **Why it matters** The normalization is a key component of the preprocessing pipeline and could affect all downstream analyses. If the assumption is violated in certain contexts, it could introduce systematic biases.
- **Resolution test** Provide additional validation of the normalization approach across more diverse cell types and conditions, including cases where housekeeping gene expression may vary. Discuss potential limitations and provide guidance on when the default normalization may not be appropriate.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The claim that CREsted is "user-friendly" and accessible to non-specialist users
- **Evidence pointer** Throughout the manuscript, particularly the Introduction and Discussion
- **Concern** While the package is well-documented and integrated into scverse, the manuscript assumes significant familiarity with deep learning concepts, scATAC-seq analysis, and enhancer biology. The description of the modeling approaches, particularly the transfer learning from Borzoi and the various loss functions, may be challenging for experimental biologists who could benefit from the tool. The manuscript does not provide sufficient context for readers unfamiliar with sequence-to-function models.
- **Why it matters** The stated goal of making enhancer modeling accessible to a broader community is undermined if the manuscript and documentation are not accessible to that community.
- **Resolution test** Revise sections of the manuscript to provide more background on deep learning approaches for regulatory genomics. Consider adding a "quick start" example or case study that walks through a complete analysis from raw data to biological interpretation in a way that is accessible to non-specialists.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and technical, making it difficult for readers outside the immediate field to understand the key contributions. The phrase "modeling genomic and synthetic cell type-specific enhancers" is vague.
- **Required correction** Consider revising the abstract to more clearly state the problem being addressed, the key innovation of CREsted, and the main findings in accessible language.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Methods section "CREsted workflow"
- **Issue** The description of the model training procedures, while detailed, lacks some specific hyperparameter values and configuration details that would be needed for exact reproduction.
- **Required correction** Provide a table or supplementary file with all hyperparameters, training configurations, and environment specifications.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section on mouse cortex model
- **Evidence pointer** Figure 2b-d
- **Issue** The performance metrics (correlations) are reported as averages across cell types, but the variability across cell types is not clearly shown. Some cell types may have much lower performance than others.
- **Required correction** Show per-cell-type performance metrics in a supplementary figure or table, and discuss any cell types where performance is notably lower.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section on cancer cell lines
- **Evidence pointer** Figure 4
- **Issue** The comparison between cell lines and patient biopsies is interesting but the analysis appears somewhat preliminary. The identification of "potential MES-like biopsy topics" relies on correlation analysis without clear thresholds or statistical significance testing.
- **Required correction** Provide more rigorous statistical analysis of the similarity between cell line and biopsy enhancer codes, including confidence intervals and appropriate significance tests.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the limitations of the study is somewhat brief and does not address several potential concerns, such as the generalizability of the models to other species or tissues, the impact of batch effects, or the interpretability of the deep learning models.
- **Required correction** Expand the discussion of limitations and future directions, addressing the concerns above.

## Risk / unsupported claims
- The claim that CREsted "outperforms" Borzoi is not fully supported by the presented evidence, as the comparison may not be entirely fair and statistical significance is not fully reported.
- The claim that CREsted enables "scrutinization of the enhancer code" at "nucleotide-level resolution" is supported for specific examples but the generalizability of this capability is not systematically demonstrated.
- The biological novelty of the insights derived from the mouse cortex and PBMC models is not clearly established, as many identified motifs correspond to known regulators.
- The in vivo validation of designed enhancers in zebrafish is presented as a key result, but the details of this validation (number of enhancers tested, quantitative readouts, statistical analysis) are not fully described in the provided text.
- The claim that the peak-scaling normalization is broadly applicable relies on assumptions about housekeeping gene accessibility that may not hold universally.
- The comparison of CREsted with gReLU is presented, but the specific differences in model architecture, training data, and evaluation protocol are not fully described, making it difficult to interpret the performance differences.