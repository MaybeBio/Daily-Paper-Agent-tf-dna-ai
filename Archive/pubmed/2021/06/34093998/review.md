## Review setup
- **Input scope** Full manuscript text (main text, figures, tables, supplementary data references)
- **Assessment boundary** Scientific and technical evaluation of the manuscript as submitted; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors present PredTAD, a machine learning framework based on Gradient Boosting Machine (GBM), which predicts TAD boundaries in breast cancer cell lines using genomic and epigenomic features. The framework is further applied to identify TAD boundary alterations between normal and cancer cells, linking a specific boundary loss near the RET oncogene to its overexpression and potential clinical relevance.
- **Visible evidence base** Main text, Figures 1–7, Table 1, Supplementary Figures 1–3 (referenced but not provided in detail)
- **Missing materials affecting confidence** Supplementary figures and data files not provided; detailed hyperparameter tuning and feature selection procedures not fully described; no explicit description of cross-validation strategy for the main model; no information on class imbalance handling; no code or data availability verification possible from the manuscript alone

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely problem: predicting 3D chromatin organization features from readily available genomic and epigenomic data, and applying such predictions to understand cancer-related chromatin alterations. The use of GBM is reasonable, and the inclusion of a wide range of features is a strength. However, several technical aspects require clarification and strengthening before the claims can be fully supported. The link between predicted boundary alterations and oncogene dysregulation is suggestive but not rigorously established. The manuscript would benefit from more rigorous validation, clearer methodological details, and a more cautious interpretation of the biological implications.
- **Who would be interested in the results, and why** Researchers in computational genomics, chromatin biology, and cancer epigenetics would be interested. The framework offers a potentially cost-effective alternative to Hi-C for identifying TAD boundaries, and the application to breast cancer could inform studies on chromatin-mediated oncogene regulation. Clinically oriented researchers may also find the RET-related findings of interest, though the translational relevance is preliminary.
- **Major strengths** 
  1. The problem is well-motivated and clinically relevant.
  2. The use of a broad set of genomic and epigenomic features is a strength.
  3. The framework is potentially generalizable to other cell types and conditions.
  4. The identification of specific features (e.g., CTCF, SMC3, RAD21) aligns with known biology.
  5. The application to RET is a concrete example of how the framework could be used.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that PredTAD accurately predicts TAD boundaries using GBM with 10 kb bins and neighboring bin information.
  - **Evidence pointer** Methods section "PredTAD boundary prediction model"; Results section "PredTAD predicts TAD boundaries in breast cancer cell lines using epigenomic and genomic information"
  - **Concern** The description of the model training and evaluation is incomplete. The authors state that training and test sets were randomly selected at a 7:3 ratio per chromosome, but do not specify whether this was done per chromosome or genome-wide, how class imbalance was handled, or whether the reported AUCs are from a single split or cross-validation. The 5-fold cross-validation AUC is only mentioned for the chromosome-random-split and feature-selection experiments, not for the main model.
  - **Why it matters** Without a clear and rigorous evaluation protocol, the reported performance metrics cannot be properly interpreted or compared with other methods. This undermines the central claim of predictive accuracy.
  - **Resolution test** Provide a detailed description of the training/validation/test split, class imbalance handling, and whether the reported AUCs are from cross-validation or a single holdout set. Report confidence intervals or standard deviations for the AUCs.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that PredTAD outperforms HubPredictor, PGSA, and TAD-Lactuca in predicting TAD boundaries.
  - **Evidence pointer** Results section "Comparison to other models"; Figure 4
  - **Concern** The comparison with other methods is not described in sufficient detail. It is unclear whether the same training and test sets were used for all methods, whether hyperparameters were optimized for each method, and whether the comparison was fair in terms of feature sets and data preprocessing. The figure shows ROC curves but no statistical significance testing is reported.
  - **Why it matters** A fair and rigorous comparison is essential to support the claim of superiority. Without it, the conclusion that PredTAD is "better" is not well supported.
  - **Resolution test** Describe the exact experimental setup for the comparison, including data splits, hyperparameter tuning, and any preprocessing steps. Report statistical tests (e.g., DeLong test for ROC AUC differences) and confidence intervals.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance / Claim support
  - **Claim pointer** The authors claim that a predicted TAD boundary loss near RET leads to its overexpression and contributes to breast cancer.
  - **Evidence pointer** Results section "Loss of TAD boundary promotes RET oncogene expression and breast cancer"; Figure 7
  - **Concern** The causal link between the predicted boundary loss and RET overexpression is not established. The analysis is correlative: the boundary loss is predicted, and RET expression is higher in cancer cells. No functional validation (e.g., CRISPR perturbation, reporter assays) is provided. The Hi-C heatmap in Figure 7A is shown for MCF10A and MCF7, but the resolution and statistical support for the boundary loss are not described.
  - **Why it matters** The manuscript's broader claim that PredTAD can uncover structural changes that contribute to disease relies on this example. Without functional evidence, the claim remains speculative.
  - **Resolution test** Provide additional evidence linking the boundary loss to RET expression, such as CRISPR-mediated disruption of the boundary in MCF10A followed by RET expression analysis, or at minimum, a more detailed statistical analysis of the Hi-C data supporting the boundary loss.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that PredTAD can be trained on one cell line (GM12878) and applied to breast cancer cell lines with high accuracy.
  - **Evidence pointer** Results section "Application of PredTAD in predicting TAD boundaries in other cell lines"
  - **Concern** The cross-cell-line transferability experiment is described briefly. It is unclear which features were used, how the model was trained, and whether the test set was independent. The AUC of 0.7471 is reported without context or comparison to within-cell-line performance.
  - **Why it matters** Generalizability is a key selling point of the framework. The current evidence is insufficient to support the claim of transferability.
  - **Resolution test** Provide a detailed description of the transfer experiment, including feature selection, training data, and test data. Compare the cross-cell-line AUC with within-cell-line AUCs and discuss any performance drop.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Figure 1
  - **Evidence pointer** Results section "Epigenetic and genetic features in TAD boundaries"
  - **Issue** The figure legend is not provided in the manuscript text, making it difficult to interpret the figure.
  - **Required correction** Include a detailed figure legend for Figure 1, describing the data sources, normalization, and statistical tests used.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods section "Gene expression analysis"
  - **Evidence pointer** Methods section "Gene expression analysis"
  - **Issue** The differential expression analysis is described briefly. It is unclear how the 6271 differentially expressed genes were defined (e.g., fold change threshold, adjusted p-value) and whether batch effects were considered.
  - **Required correction** Provide the full criteria for defining differentially expressed genes and describe the statistical methods used.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Data availability section
  - **Evidence pointer** Data availability section
  - **Issue** The code repository is mentioned, but it is not clear whether the code is versioned, documented, and includes all necessary scripts to reproduce the results.
  - **Required correction** Provide a more detailed description of the code repository, including dependencies, usage instructions, and a link to a stable version (e.g., Zenodo DOI).
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Table 1
  - **Evidence pointer** Results section "Altered chromatin organization contributes to oncogenic pathway activation in breast cancer cells"
  - **Issue** The p-values in Table 1 are not adjusted for multiple testing, and the table is not referenced in the text with sufficient context.
  - **Required correction** Report adjusted p-values (e.g., Benjamini-Hochberg) and provide a brief description of the pathway analysis method in the text.
- **Technical failings that need to be addressed before the case is established** R1-M1 (model evaluation protocol), R1-M2 (fair comparison with other methods), R1-M3 (causal link between boundary loss and RET expression)
- **Assessment against Nature-style criteria** 
  - **Originality** The use of GBM with a broad feature set for TAD boundary prediction is not entirely novel, as similar approaches exist. However, the application to breast cancer-specific boundary alterations and the focus on oncogene dysregulation adds a new dimension.
  - **Scientific importance** The problem is important, and the potential to predict TAD boundaries without Hi-C is valuable. However, the biological claims are not fully supported, limiting the current impact.
  - **Interdisciplinary readership** The work bridges computational biology, epigenetics, and cancer biology, which could attract a broad audience. However, the technical details may be challenging for non-specialists.
  - **Technical soundness** The technical approach is reasonable but lacks rigor in evaluation and comparison. The causal claims are not supported by functional validation.
  - **Readability for nonspecialists** The manuscript is generally well-written, but some sections (e.g., feature engineering, model evaluation) could be clearer for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the evaluation protocol, comparison with other methods, and the causal link to RET require substantial strengthening. The manuscript is not currently established from the provided evidence.

## Risk / unsupported claims
- The claim that PredTAD "accurately predicts" TAD boundaries is not fully supported due to incomplete evaluation details.
- The claim that PredTAD outperforms other methods is not rigorously established.
- The claim that a TAD boundary loss near RET causes its overexpression is correlative and lacks functional validation.
- The claim that PredTAD can be applied to other cell lines with high accuracy is based on a single, briefly described experiment.
- The biological significance of the pathway analysis (Table 1) is limited by the lack of multiple testing correction and the absence of validation.