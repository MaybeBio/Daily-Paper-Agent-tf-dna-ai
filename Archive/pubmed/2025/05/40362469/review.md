## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, conclusions) as provided
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors propose TFProtBert, a two-layer machine learning framework using ProtBert embeddings and SVM/LGBM classifiers, to predict transcription factors (TFs) and transcription factors preferring methylated DNA (TFPMs), claiming superior performance over existing methods on balanced and imbalanced datasets
- **Visible evidence base** Performance tables (Tables 1-4), dataset descriptions (Table 5), baseline model comparisons (Figures 2-3), t-SNE visualization (Figure 4), supplementary tables referenced (S1-S3)
- **Missing materials affecting confidence** Full supplementary tables (S1-S3) not provided; detailed hyperparameter configurations not shown; exact train/test split methodology for imbalanced dataset not fully specified; code and data availability stated but not verifiable from this material

## Reviewer
- **Overall assessment** The manuscript presents a straightforward application of ProtBert embeddings combined with classical machine learning classifiers for TF and TFPM prediction. The two-layer architecture is logical, and the performance improvements over existing methods are reported. However, several methodological concerns regarding dataset construction, evaluation rigor, and comparison fairness limit the strength of the claims. The work is incremental in nature, building on established embedding techniques without introducing novel architectural or conceptual advances.
- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics focused on transcription factor prediction, protein function annotation, and applications of protein language models. The work may also interest those developing machine learning pipelines for imbalanced biological datasets.
- **Major strengths** Clear two-layer prediction framework addressing a relevant biological problem; systematic comparison across 45 baseline models; inclusion of imbalanced dataset testing for robustness; use of established protein language model (ProtBert) with transfer learning; performance metrics reported comprehensively (ACC, Sn, Sp, MCC, AUC)
- **Major Concerns** See detailed items below
- **Minor Comments** See detailed items below
- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset leakage risk), R1-M2 (comparison fairness), R1-M3 (imbalanced dataset evaluation)
- **Assessment against Nature-style criteria** Originality: Low to moderate. The application of ProtBert to TF prediction is not conceptually novel, and the two-layer architecture is a straightforward combination of existing components. Scientific importance: Moderate. TF prediction is a relevant problem, but the incremental improvement over existing methods does not represent a major advance. Interdisciplinary readership: Limited. The work is primarily of interest to computational biologists and machine learning practitioners in bioinformatics. Technical soundness: Moderate. The methodology is generally sound but has concerns regarding dataset construction and evaluation rigor. Readability for nonspecialists: Adequate. The manuscript is generally clear, though some methodological details require domain expertise.
- **Recommendation posture** Currently not established from the provided evidence. The core claims of superior performance require addressing the methodological concerns, particularly regarding dataset leakage, comparison fairness, and imbalanced dataset evaluation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data integrity and evaluation validity
- **Claim pointer** The authors claim the proposed model "consistently outperformed state-of-the-art approaches" on TF and TFPM prediction tasks
- **Evidence pointer** Section 2.4, Table 2; Section 2.5, Table 3; Section 3.1, Table 5
- **Concern** The TF dataset is derived from Liu et al. (2020), and the same source is used for both training and independent testing. The manuscript does not clarify whether the independent test set shares sequence similarity with the training set. If sequences are highly similar or redundant, the reported performance may reflect memorization rather than generalization. Additionally, the TFPM dataset construction is not fully described, and the negative set composition for this task is unclear.
- **Why it matters** If the independent test set is not truly independent, the reported performance metrics are inflated and the generalization claims are unsupported. This is a fundamental issue that affects the validity of all reported results.
- **Resolution test** Provide a detailed description of how the independent test sets were constructed, including sequence identity thresholds between training and test sets. Perform a sequence similarity-based analysis (e.g., CD-HIT clustering at various thresholds) to demonstrate that test sequences are not near-duplicates of training sequences. If redundancy exists, re-evaluate with a strictly non-redundant test set.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparison fairness and reproducibility
- **Claim pointer** The authors state that "the performance results of the approved procedures were taken straight out of the original papers that accompanied each technique" (Section 2.4)
- **Evidence pointer** Section 2.4, Table 2; Section 2.5, Table 3
- **Concern** Comparing the proposed method against results taken directly from original papers is methodologically problematic. The original papers may have used different training/test splits, different evaluation protocols, or different versions of the datasets. This makes the comparison unfair and potentially misleading. For the TFPM comparison, the authors used the Li_RNN web server, but it is unclear whether the same evaluation protocol was applied.
- **Why it matters** Unfair comparisons undermine the central claim of superiority over existing methods. Without consistent evaluation conditions, the reported improvements cannot be attributed to the proposed method's merits.
- **Resolution test** Re-implement the existing methods (TFPred, PSSM+CNN, Capsule_TF, Li_RNN) using the same training and test splits as the proposed method, or use the authors' provided code if available. Report performance under identical evaluation conditions. If re-implementation is not feasible, clearly state the limitations of the comparison and avoid strong claims of superiority.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Imbalanced dataset evaluation
- **Claim pointer** The authors claim the proposed method demonstrates "robustness and generalization ability" on the imbalanced dataset (Section 2.6)
- **Evidence pointer** Section 2.6, Table 4
- **Concern** The imbalanced dataset contains 416 positive and 6444 negative sequences, a ratio of approximately 1:15. The manuscript reports recall and MCC but does not report precision, F1-score, or area under the precision-recall curve (AUPRC), which are more appropriate metrics for imbalanced classification. The reported MCC of 0.908 on the independent set appears surprisingly high given the extreme imbalance, and the authors do not explain how this was achieved or whether class weights or sampling strategies were used.
- **Why it matters** For imbalanced datasets, accuracy and MCC can be misleading. Without appropriate metrics and a clear description of the handling of class imbalance, the claimed robustness is not adequately supported.
- **Resolution test** Report precision, F1-score, and AUPRC for the imbalanced dataset. Describe any class weighting, oversampling, or undersampling strategies used. Provide a confusion matrix to enable assessment of the false positive and false negative rates. If no imbalance handling was used, explain how the high MCC was achieved.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Section 3.1, Table 5
- **Evidence pointer** Section 3.1, Table 5
- **Issue** The description of the TFPM dataset is incomplete. The manuscript states the training set includes 146 positive and 146 negative samples, and the independent set includes 69 positive and 37 negative samples, but the source and selection criteria for these samples are not fully described.
- **Required correction** Provide a detailed description of how the TFPM dataset was constructed, including the source database, selection criteria, and any filtering steps applied.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 3.3, Supplementary Table S3
- **Evidence pointer** Section 3.3, Supplementary Table S3
- **Issue** The hyperparameter tuning details are referenced to Supplementary Table S3, but the specific ranges and final selected values for each model are not described in the main text.
- **Required correction** Summarize the key hyperparameter ranges and final selected values for the main models in the main text or provide a more detailed description in the supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 2.1-2.6, Tables 1-4
- **Evidence pointer** Section 2.1-2.6, Tables 1-4
- **Issue** The manuscript reports performance metrics without confidence intervals or statistical significance testing. It is unclear whether the observed differences between models are statistically significant.
- **Required correction** Report confidence intervals for the main performance metrics or perform statistical significance testing (e.g., McNemar's test for classifier comparison) to support claims of superiority.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 2.7, Figure 4
- **Evidence pointer** Section 2.7, Figure 4
- **Issue** The t-SNE visualization is described qualitatively, but the figure itself is not provided in the manuscript text. The claim that the 1024-D feature vector shows "two separate clusters" is not verifiable from the provided material.
- **Required correction** Include the t-SNE figure in the main text or supplementary materials, and provide a quantitative measure of cluster separation (e.g., silhouette score) to support the qualitative claim.

## Risk / unsupported claims
- The claim of "consistently outperformed state-of-the-art approaches" (Abstract, Section 2.4) is not fully supported due to the unfair comparison methodology described in R1-M2
- The claim of "robustness and generalization ability" on the imbalanced dataset (Section 2.6) is not fully supported due to incomplete evaluation metrics and unclear handling of class imbalance as described in R1-M3
- The claim that the 1024-D feature vector provides "high degree of discrimination" (Section 2.7) is not verifiable without the actual t-SNE figure and quantitative measures
- The statement that the proposed method "has achieved the intended goals comprehensively" (Section 4) is an overstatement given the methodological concerns identified
- The generalizability of the model to diverse transcription factor collections is acknowledged as limited by the authors (Section 4), which tempers the broader applicability claims