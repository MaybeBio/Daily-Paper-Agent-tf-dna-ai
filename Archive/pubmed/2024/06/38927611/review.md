## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusions) as provided
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as stated in the provided text
- **Shared manuscript claim summary** The authors propose EC-PDH, a machine learning method combining empirical mode decomposition (EMD) features with CatBoost classification, to predict hot spots at protein-DNA interfaces. They report superior performance (AUC 0.847, MCC 0.543, F1 0.772) compared to existing methods.
- **Visible evidence base** Tables 1-6 (referenced), Figures 1-7 (referenced), performance metrics reported in text
- **Missing materials affecting confidence** Actual data tables, figures, detailed feature lists, hyperparameter settings, code availability, full dataset composition, statistical significance tests, and comparison methodology details

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful application of EMD-based feature extraction for protein-DNA hot spot prediction. However, several critical methodological gaps and reporting deficiencies prevent full evaluation of the claims. The core idea of applying EMD to extract novel features is interesting, but the evidence provided is insufficient to establish that EC-PDH genuinely outperforms existing methods or that the reported improvements are statistically robust.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein-DNA interaction prediction, machine learning practitioners applying signal processing techniques to biological sequence/structure data, and researchers developing hot spot prediction tools for drug discovery or protein engineering applications.
- **Major strengths** 1) Novel application of EMD to protein-DNA hot spot prediction, representing a creative cross-disciplinary approach. 2) Comprehensive feature engineering pipeline combining multiple feature types. 3) Use of SMOTE-Tomek to address class imbalance is methodologically appropriate. 4) Comparison with multiple existing methods and classifiers demonstrates thoroughness.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset composition), R1-M2 (comparison methodology), R1-M3 (statistical validation), R1-M4 (reproducibility)
- **Assessment against Nature-style criteria** **Originality**: Moderate. EMD application to this problem is novel, but the overall approach follows established hot spot prediction pipelines. **Scientific importance**: Moderate. Incremental improvement in prediction accuracy, but broader biological insight is limited. **Interdisciplinary readership**: Limited. Primarily relevant to computational biology specialists. **Technical soundness**: Currently insufficient due to missing methodological details and validation gaps. **Readability for nonspecialists**: Acceptable, though some technical sections could be clearer.
- **Recommendation posture** Currently not established from the provided evidence. Major methodological clarifications and additional validation are required before the claims can be assessed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and dataset composition
- **Claim pointer** The authors claim to have collected and screened 339 mutations from four protein thermodynamics databases, with 131 hot spots and 208 non-hot spots from 117 protein-DNA complexes.
- **Evidence pointer** Section 2.1, Table 1 (referenced)
- **Concern** The dataset construction process is insufficiently described. The authors state they added data from Nabe and ProNAB to their previous sxPDH dataset, but do not specify which databases were used, how mutations were curated, what filtering criteria were applied beyond sequence similarity and solvent accessibility, or how the final 117 complexes were selected from the initial 293. The threshold of ∆∆G≥1.0 kcal/mol for defining hot spots is cited from study [9], but no justification is provided for this choice. Additionally, the statement that "interface residues with a soluble surface area greater than 1 Å" were filtered is ambiguous, as this appears to be a distance threshold rather than an area measurement.
- **Why it matters** Dataset composition directly affects model generalizability and comparability with existing methods. Without clear inclusion/exclusion criteria, the reported performance cannot be properly contextualized or reproduced.
- **Resolution test** Provide a detailed flowchart of dataset construction, specify all source databases with accession numbers, state all filtering criteria with thresholds, and report the distribution of mutations across complexes and databases.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparison methodology
- **Claim pointer** The authors claim EC-PDH outperforms existing state-of-the-art methods (WTL-PDH, PrPDH, sxPDH, inpPDH) on the test set.
- **Evidence pointer** Section 3.5, Figure 5 (referenced)
- **Concern** The comparison with existing methods is inadequately described. It is unclear whether these methods were retrained on the same training set, whether their published models were used directly, or whether the same feature sets and hyperparameters were employed. The test set composition is not described in sufficient detail to determine whether it is identical across all compared methods. No statistical significance testing (e.g., DeLong test for AUC comparison, McNemar's test) is reported.
- **Why it matters** Fair comparison is essential to substantiate the claim of superior performance. Without controlled conditions and statistical validation, the reported improvements could be due to dataset differences, implementation details, or random variation.
- **Resolution test** Describe the exact comparison protocol, including whether methods were retrained, what hyperparameters were used, and whether the same train/test splits were applied. Report confidence intervals and p-values for performance differences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validation and overfitting
- **Claim pointer** The authors report AUC 0.847, MCC 0.543, F1 0.772 on the test set, and AUC 0.859-0.863 on the training set with cross-validation.
- **Evidence pointer** Sections 2.6, 3.1-3.4, Tables 3-5 (referenced)
- **Concern** The manuscript reports results from 50 runs of 10-fold cross-validation on the training set, but the variance across these runs is not reported. The test set contains only 58 samples (29 hot spots, 29 non-hot spots), which is very small for reliable performance estimation. The feature selection procedure (mRMR-SFS) is performed on the training set, but it is unclear whether this selection is nested within the cross-validation folds or performed on the full training set before cross-validation, which could lead to selection bias and optimistic performance estimates.
- **Why it matters** Small test sets and potential information leakage during feature selection can produce inflated performance estimates that do not generalize. The reported metrics lack uncertainty quantification.
- **Resolution test** Report mean and standard deviation across cross-validation runs, use nested cross-validation for feature selection, and provide confidence intervals for test set metrics. Consider external validation on an independent dataset.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and methodological detail
- **Claim pointer** The authors describe a complete pipeline including EMD feature extraction, SMOTE-Tomek balancing, mRMR-SFS feature selection, and CatBoost classification.
- **Evidence pointer** Sections 2.2-2.5, Tables 2, 4-5 (referenced)
- **Concern** Critical implementation details are missing. The EMD implementation (MATLAB toolbox, Python package, or custom code) is not specified. The number of IMFs used, stopping criteria for sifting, and how the first three IMFs were selected are not described. The SMOTE-Tomek parameters (k-neighbors, sampling strategy) are not provided. The CatBoost hyperparameters beyond those listed (iterations, learning rate, depth, random seed) are not given, and no hyperparameter tuning procedure is described. The feature selection procedure details, including the number of features evaluated at each step and the stopping criterion for SFS, are absent.
- **Why it matters** Reproducibility is a fundamental requirement for computational studies. Without these details, other researchers cannot replicate the method or verify the results.
- **Resolution test** Provide complete implementation details, including software versions, parameter values, and code availability. Consider depositing the code and data in a public repository.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Section 2.2.6, EMD feature description
- **Evidence pointer** Section 2.2.6
- **Issue** The description of EMD feature extraction is somewhat unclear. The sentence "we created four IMF functions for ASA, uASA, dASA and secondary structure features, respectively" is ambiguous, as it is unclear whether four separate EMD decompositions were performed or one combined decomposition. The notation in equation (4) uses both xi* and xi+m without clearly defining the conjugate operation for real-valued signals.
- **Required correction** Clarify the EMD procedure, define all notation precisely, and specify whether the features were extracted from each IMF separately or from the ensemble.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Dataset description
- **Evidence pointer** Section 2.1
- **Issue** The authors do not state whether the dataset is publicly available or how other researchers can access it. Given the small size of the dataset, this is particularly important for benchmarking purposes.
- **Required correction** State data availability and provide a link to the dataset or a clear description of how to obtain it.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1-7
- **Evidence pointer** Figures 1-7 (referenced)
- **Issue** The figures are referenced but not included in the provided text. It is not possible to assess their quality or informativeness.
- **Required correction** Ensure all figures are clearly labeled, include appropriate legends, and are referenced in the text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Related work coverage
- **Affected element** Introduction
- **Evidence pointer** Section 1
- **Issue** The introduction covers several existing methods but does not discuss recent deep learning approaches to hot spot prediction, which have become increasingly prominent in the field.
- **Required correction** Add discussion of recent deep learning methods and clarify the novelty of the proposed approach relative to these methods.

## Risk / unsupported claims
- The claim that EC-PDH "outperforms the existing state-of-the-art methods" is not supported by the provided evidence due to inadequate comparison methodology and lack of statistical testing.
- The claim that EMD features "contribute most to the identification of hot spot residues" is based on a single feature importance analysis without clear methodology or validation.
- The claim that the method "positively contributed to the advancement of research on protein-DNA interaction mechanisms" is overstated given the limited biological interpretation provided.
- The performance metrics reported for the test set (AUC 0.847, MCC 0.543, F1 0.772) cannot be fully evaluated without confidence intervals or error bars.
- The statement that "the combination of EMD features and wavelet features results in the best performance" is not supported by quantitative comparison data in the provided text.