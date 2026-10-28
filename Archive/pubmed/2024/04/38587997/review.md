## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose ESPDHot, a stacked ensemble machine learning method for predicting protein-DNA interaction hotspots, defined as interface residues whose mutation causes a binding free energy change (DeltaDeltaG) exceeding 2 kcal/mol. The method uses ADASYN oversampling to address class imbalance, introduces three new feature types (residue interface preference, residue fluctuation dynamics, coevolutionary features), employs Boruta with a Random Grouping strategy for feature selection, and builds a two-layer stacking classifier (SVM, XGBoost, ANN in layer one; Logistic Regression in layer two). The authors report superior performance over state-of-the-art predictors on an independent test set, with F1, MCC, and AUC of 0.571, 0.516, and 0.870, respectively.
- **Visible evidence base** Abstract text only; no quantitative comparisons, dataset descriptions, or methodological details beyond those summarized above
- **Missing materials affecting confidence** Full manuscript, dataset composition and source, feature definitions, hyperparameter settings, baseline predictor details, statistical significance tests, cross-validation procedures, and any figures or tables

## Reviewer
- **Overall assessment** The abstract presents a plausible machine learning pipeline for a biologically relevant prediction task. However, the evidence provided is insufficient to evaluate the novelty, technical soundness, or robustness of the claimed improvements. The reported performance metrics are modest in absolute terms, and without details on dataset splits, baseline comparisons, or statistical validation, the central claim of outperforming state-of-the-art predictors cannot be verified from the supplied material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein-DNA interaction prediction, protein engineering, and machine learning applications in structural biology. The method could also interest researchers developing feature engineering strategies for imbalanced biological datasets.
- **Major strengths** The problem is well-motivated and practically relevant. The use of a stacked ensemble architecture and the introduction of three new feature types suggest a thoughtful approach to improving prediction performance. The explicit handling of class imbalance via ADASYN is appropriate for the task.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** 
  - Originality: The abstract claims three new feature types, but their novelty relative to existing literature cannot be assessed without full methodological details. The stacked ensemble approach is not inherently novel.
  - Scientific importance: The task is important, but the modest performance metrics (F1 0.571, MCC 0.516) limit the potential impact. The abstract does not demonstrate a substantial advance over existing methods.
  - Interdisciplinary readership: The topic bridges machine learning and molecular biology, but the abstract is written for a specialist audience and does not convey broader significance.
  - Technical soundness: Cannot be evaluated from the abstract alone. Key details on data, feature construction, and validation are missing.
  - Readability for nonspecialists: The abstract is concise but assumes familiarity with machine learning and biophysical concepts. It is not accessible to a broad scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient information to support the central claims of novelty and superior performance. A full manuscript review would be required to assess technical soundness.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "ESPDHot outperforms the current state-of-the-art predictors, achieving superior performance on the independent test data set, with F1, MCC, and AUC reaching 0.571, 0.516, and 0.870, respectively."
- **Evidence pointer** Abstract, performance metrics section; location not provided
- **Concern** The claim of superior performance is based on a single set of metrics on an independent test set. No information is provided about the size of the test set, the identity of the state-of-the-art predictors compared, the statistical significance of the differences, or the variance of the performance estimates. The absolute values of F1 (0.571) and MCC (0.516) are moderate, and without context, it is unclear whether these represent a meaningful improvement.
- **Why it matters** A central claim of the work is that ESPDHot outperforms existing methods. Without statistical validation and detailed comparison, this claim cannot be substantiated. The reported metrics alone do not establish superiority, especially given the modest absolute values.
- **Resolution test** Provide the full comparison table with multiple baseline methods, report confidence intervals or standard deviations across multiple runs, and include statistical significance tests (e.g., paired bootstrap or McNemar's test) for the differences in F1, MCC, and AUC.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and data transparency
- **Claim pointer** "To tackle the imbalanced data set issue, the adaptive synthetic sampling (ADASYN), an oversampling technique, is adopted to synthetically generate new minority samples, thereby rectifying data imbalance."
- **Evidence pointer** Abstract, methodology description; location not provided
- **Concern** The abstract does not describe the dataset used for training and testing, including its source, size, class distribution, or how the independent test set was constructed. The definition of hotspots (DeltaDeltaG > 2 kcal/mol) is stated, but the source of DeltaDeltaG values and the criteria for selecting interface residues are not provided. Without this information, the reproducibility of the method and the validity of the evaluation are unclear.
- **Why it matters** Reproducibility is a fundamental requirement for computational methods. The lack of dataset details prevents readers from assessing whether the training and test sets are appropriate, whether there is potential data leakage, and whether the results can be generalized to other protein-DNA systems.
- **Resolution test** Specify the dataset source (e.g., a public database), the number of proteins and residues, the class distribution before and after ADASYN, and the procedure for splitting training and independent test sets. Provide details on how interface residues and DeltaDeltaG values were obtained.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and feature validity
- **Claim pointer** "Besides traditional features, we introduce three new characteristic types including residue interface preference proposed by us, residue fluctuation dynamics characteristics, and coevolutionary features."
- **Evidence pointer** Abstract, feature description; location not provided
- **Concern** The abstract claims three new feature types, but it does not explain how these features are computed, what makes them novel relative to existing descriptors in the literature, or how they contribute to the improved performance. The term "residue interface preference proposed by us" suggests a novel contribution, but no definition or rationale is given. Without this information, the novelty claim cannot be evaluated.
- **Why it matters** The introduction of new features is a key contribution of the work. If the features are not clearly defined or are similar to existing ones, the novelty of the method is diminished. Additionally, the contribution of each feature type to the final performance is not assessed, making it difficult to determine which aspects of the method drive the results.
- **Resolution test** Provide formal definitions and computational procedures for each new feature type. Compare them with existing features in the literature to demonstrate novelty. Include an ablation study showing the performance contribution of each feature type.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Method description
- **Evidence pointer** Abstract, methodology section; location not provided
- **Issue** The abstract states that the Random Grouping strategy was "previously developed" by the authors, but it does not explain what this strategy entails or how it is combined with Boruta for feature selection.
- **Required correction** Briefly describe the Random Grouping strategy and its role in the feature selection process, or provide a citation to the previous work.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Performance metrics
- **Evidence pointer** Abstract, performance metrics section; location not provided
- **Issue** The abstract reports F1, MCC, and AUC but does not provide other standard metrics such as sensitivity, specificity, or precision, which would give a more complete picture of the model's performance.
- **Required correction** Include additional performance metrics or refer to a table in the full manuscript where these are reported.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Contextualization
- **Affected element** Comparison with existing methods
- **Evidence pointer** Abstract, performance comparison statement; location not provided
- **Issue** The abstract claims superiority over state-of-the-art predictors but does not name any of these predictors or describe the comparison conditions.
- **Required correction** Name the baseline methods and briefly describe the evaluation protocol (e.g., same training data, same test set) to allow readers to contextualize the comparison.

## Risk / unsupported claims
- The claim that ESPDHot "outperforms the current state-of-the-art predictors" is unsupported without detailed comparison data and statistical testing.
- The novelty of the three new feature types is unverifiable from the abstract alone.
- The effectiveness of ADASYN in improving performance is asserted but not demonstrated with comparative results.
- The generalizability of the method to diverse protein-DNA systems is not addressed.
- The practical significance of the reported performance metrics (F1 0.571, MCC 0.516) is not discussed in the context of existing benchmarks.