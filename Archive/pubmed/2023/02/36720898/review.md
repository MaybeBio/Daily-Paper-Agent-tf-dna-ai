## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims, and presentation quality
- **Shared manuscript claim summary** The authors propose an explainable artificial intelligence (XAI) approach using support vector machines (SVM) with DNA Duplex Stability (DDS) encoding to classify and annotate archaeal promoter regions. They claim the model identifies conserved promoter elements, particularly an AT-rich region around position -27, and can be applied to predict promoters in 135 unannotated archaeal genomes at an unprecedented scale.
- **Visible evidence base** Abstract, full methods, results tables (Tables 1-3), figures (Figures 1-5), supplementary references
- **Missing materials affecting confidence** Supplementary figures S1-S5, raw data files, code repository contents, complete prediction results for all 135 organisms, detailed hyperparameter settings, and statistical significance tests

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful application of SVM with DDS encoding for archaeal promoter prediction, combined with SHAP-based interpretability. The core idea of using physicochemical properties rather than sequence motifs alone is reasonable and may have value for organisms lacking canonical promoter elements. However, several methodological weaknesses and overstatements in the claims undermine the current version. The validation strategy is incomplete, the interpretability analysis is somewhat superficial, and the claim of "unprecedented scale" is not well supported. The work is of interest to the archaeal genomics and gene regulation community, but requires substantial revision to establish the case convincingly.
- **Who would be interested in the results, and why** Researchers studying archaeal gene regulation, promoter structure, and genome annotation. The approach may also interest computational biologists working on interpretable machine learning for genomics. The public resource of predicted promoters could be useful for comparative genomics studies.
- **Major strengths** 1) The use of DDS as a feature representation is physically motivated and may capture regulatory signals not visible in sequence motifs. 2) The application of SHAP to interpret the SVM decision process is a commendable step toward transparency. 3) The inclusion of multiple archaeal species with diverse genomic GC content strengthens the generalizability claim. 4) The public availability of code and predicted promoter datasets is a positive contribution.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** 
  - **Originality** Moderate. The combination of DDS encoding with SVM and SHAP for archaeal promoter prediction is somewhat novel, though individual components are established. The claim of being the first to use XAI in regulatory region annotation is plausible but not rigorously verified.
  - **Scientific importance** Moderate. Archaeal promoter annotation is an under-served area, and a reliable computational tool would be valuable. However, the practical impact depends on the accuracy and generalizability of the model, which are not fully established here.
  - **Interdisciplinary readership** Limited. The work is primarily of interest to archaeal microbiologists and computational genomics researchers. The presentation assumes familiarity with both machine learning and archaeal transcription, which may limit broader accessibility.
  - **Technical soundness** Weak to moderate. Several methodological issues need addressing, including the negative control design, the validation approach, and the statistical treatment of results. The interpretability analysis requires more rigorous linking to biological function.
  - **Readability for nonspecialists** Moderate. The manuscript is generally clear, but some sections (e.g., SHAP methodology) may be challenging for readers without machine learning background. The figures are informative but could be better annotated.
- **Recommendation posture** Currently not established from the provided evidence. The core concept has merit, but the technical concerns must be resolved before the claims can be accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors claim the SVM model achieves reliable classification of archaeal promoter sequences, with accuracy, precision, recall, and specificity around 84-85%.
- **Evidence pointer** Table 2, Figure 1
- **Concern** The negative control dataset consists of shuffled versions of the positive promoter sequences. This is a weak control because shuffled sequences preserve dinucleotide composition and may not represent true non-promoter genomic regions. The model's performance on this artificial negative set may not reflect its ability to distinguish promoters from actual non-promoter intergenic sequences. The authors should use real non-promoter sequences (e.g., coding regions, intergenic regions without promoter activity) as negative controls.
- **Why it matters** If the negative control is not representative, the reported performance metrics may be inflated, and the model may not generalize to real-world promoter prediction tasks. This directly affects the validity of the core claim.
- **Resolution test** Retrain and evaluate the model using real non-promoter sequences (e.g., coding sequences or intergenic regions) as negative controls. Report performance metrics on this more realistic task and compare with the shuffled-control results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors claim the model correctly labeled 2193 out of 2719 experimentally validated T. kodakarensis promoters, achieving 80.65% precision.
- **Evidence pointer** Figure 2
- **Concern** The external validation uses only one species (T. kodakarensis), which is also part of the training data. This creates a potential circularity issue. The model was trained on T. kodakarensis promoters, so its performance on T. kodakarensis promoters is not an independent test of generalizability. The authors should validate on species not represented in the training set.
- **Why it matters** The claim of generalizability to other archaea is not supported by the current validation. Without independent species validation, the model may be overfitted to the training species.
- **Resolution test** Validate the model on experimentally confirmed promoter sequences from archaeal species not included in the training set (e.g., from the Prokaryotic Promoter Database or other sources). Report performance on these independent species.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability
- **Claim pointer** The authors claim the SHAP analysis reveals that an AT-rich region around position -27 is the most conserved and discriminatory feature, and that positions -33, -10, and +3 are also important.
- **Evidence pointer** Figure 3
- **Concern** The SHAP analysis is performed on only 100 randomly selected promoters. This is a small sample for a model with 99 features, and the stability of SHAP values across different random subsets is not assessed. Additionally, the authors do not provide confidence intervals or statistical tests for the SHAP importance values. The biological interpretation linking SHAP importance to known TF binding sites is plausible but not rigorously demonstrated.
- **Why it matters** The interpretability claims are a key novelty of the work. If the SHAP analysis is not robust or statistically grounded, the biological conclusions drawn from it are weakened.
- **Resolution test** Perform SHAP analysis on multiple random subsets (e.g., 10 different subsets of 100 promoters) and report the variance in SHAP importance values. Provide statistical tests (e.g., permutation tests) to assess the significance of the identified important positions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors claim the model can be used to annotate promoters in 135 unannotated archaeal organisms, delivering "regulatory regions annotation of archaea in a scale never accomplished before."
- **Evidence pointer** Table 3, Figure 5
- **Concern** The prediction of promoters in 135 organisms is presented without any experimental validation or orthogonal evidence. The authors do not assess the false positive rate in these predictions, nor do they compare their predictions with any existing annotations or experimental data for these organisms. The claim of "unprecedented scale" is not substantiated with a comparison to prior efforts.
- **Why it matters** The practical utility of the tool depends on the reliability of predictions in new organisms. Without validation, the predicted promoter set may contain many false positives, undermining the resource's value.
- **Resolution test** Provide a more detailed analysis of the predicted promoters, including comparison with any available experimental data, assessment of false positive rates using known non-promoter regions, and comparison with existing promoter prediction tools or databases.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors claim the SVM with RBF kernel was selected as the best-performing algorithm based on accuracy, precision, recall, specificity, and AUC.
- **Evidence pointer** Table 2, Methods section
- **Concern** The hyperparameter selection for the SVM (C and gamma) is not described in detail. The authors state they used default parameters from sklearn, but no justification is provided for why these defaults are appropriate for this problem. Additionally, the performance comparison across algorithms (SVM, LDA, CART, KNN) lacks statistical significance testing. The differences in performance may not be statistically meaningful.
- **Why it matters** Without proper hyperparameter tuning and statistical comparison, the claim that SVM is the best algorithm is not well supported. This affects the reproducibility and robustness of the approach.
- **Resolution test** Provide a description of hyperparameter tuning (e.g., grid search with cross-validation) and report the optimal parameters. Perform statistical significance tests (e.g., paired t-test or Wilcoxon test) comparing SVM performance with other algorithms across cross-validation folds.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "an AT rich region around position -27 upstream (relative to the start TSS) is the most conserved in the analyzed organisms." This is somewhat ambiguous, as "conserved" could refer to sequence conservation or feature importance. Clarify whether this refers to sequence conservation or model importance.
- **Required correction** Rephrase to specify whether the AT-rich region is conserved in terms of sequence alignment or in terms of model feature importance.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The ROC curve in Figure 1A is described, but the figure itself is not visible in the manuscript text. The caption mentions "receive operator characteristic curve" which should be "receiver operating characteristic curve."
- **Required correction** Correct the typo in the figure caption and ensure the figure is properly referenced and displayed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods section
- **Evidence pointer** Methods, "Motif discovery"
- **Issue** The MEME motif discovery parameters are described, but the authors do not specify how the "TATA motif" was identified among the 10 motifs found per organism. The criterion for selecting the TATA motif (AT-rich around positions -24 to -32) is somewhat circular, as this is the expected location.
- **Required correction** Provide a more objective criterion for identifying the TATA motif, or acknowledge the potential bias in the selection process.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion states "we made use and extended to quantitative levels already proposed arguments that state the representation of genomic information with numerical features regarding the physicochemical processes within the cell might enlighten genomic annotation." This sentence is convoluted and difficult to parse.
- **Required correction** Simplify and clarify this sentence to improve readability.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Not provided
- **Issue** The manuscript mentions that predicted promoter sequences are available at a website, but there is no explicit data availability statement in the text.
- **Required correction** Add a clear data availability statement specifying where all data, code, and supplementary materials can be accessed.

## Risk / unsupported claims
- The claim that the model delivers "regulatory regions annotation of archaea in a scale never accomplished before" is unsupported without a comparison to prior annotation efforts.
- The claim that the AT-rich region around position -27 is "the most conserved" is not clearly defined and is not supported by statistical evidence.
- The claim that the model's decision pattern "matches the same process performed with experimentally validated regulatory sequences" (based on Figure 5D) is an overstatement, as the comparison is only visual and not statistically tested.
- The biological interpretation of SHAP values as indicating TF binding sites is plausible but not rigorously validated against experimental binding data.
- The performance of the model on the independent T. kodakarensis dataset is not an independent validation, as this species was included in training.