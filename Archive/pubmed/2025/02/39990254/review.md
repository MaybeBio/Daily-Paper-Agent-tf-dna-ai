## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion)
- **Assessment boundary** Scientific claims, methodology, dataset construction, evaluation approach, and reproducibility as presented in the provided text
- **Shared manuscript claim summary** The authors present hierarchical and multi-class machine learning models using ESM2 protein language model embeddings to predict nucleic acid binding protein types (SSB, DSB, RBP, non-NABP) for any given protein, reporting up to 95% accuracy per hierarchical stage and 85% overall multi-class accuracy, with improved SSB prediction compared to prior work
- **Visible evidence base** Tables 1 and 2, Figures 1-4, hyperparameter file link, dataset availability link
- **Missing materials affecting confidence** Full tables and figures not provided; hyperparameter details not visible; dataset composition and redundancy removal details only partially described; no comparison with state-of-the-art methods beyond those listed; no external validation on independent benchmarks

## Reviewer
- **Overall assessment** The manuscript addresses a practically important problem, namely predicting nucleic acid binding protein types for proteins of unknown function, and the use of ESM2 embeddings with classical machine learning classifiers is a reasonable and potentially effective approach. The reported accuracy improvements over prior work are notable, particularly for SSB prediction. However, the evidence base as provided is incomplete, and several methodological details and validation aspects require clarification before the claims can be fully assessed. The work is incremental in nature, building directly on the authors' prior publications, and the novelty is limited to the application of ESM2 features to this specific problem with an expanded dataset. The manuscript is clearly written and accessible to a bioinformatics audience, though some technical details are missing.

- **Who would be interested in the results, and why** Researchers working on protein function prediction, particularly those focused on nucleic acid binding proteins, would find this work relevant. The improved SSB prediction is of specific interest given the under-explored nature of this class. Practitioners developing machine learning approaches for protein annotation may also benefit from the comparison of ESM2 features with traditional sequence-based features. The availability of code and datasets supports reproducibility and potential adoption.

- **Major strengths**
  - Addresses a practical gap: prediction of NABP types for proteins without known function, rather than assuming known binding status
  - Explicit inclusion and evaluation of SSBs, an under-studied class
  - Use of ESM2 embeddings, a modern and powerful feature representation
  - Systematic comparison of five classical machine learning classifiers
  - Multiple evaluation metrics and 100 independent train/test splits to assess stability
  - Code and data availability

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim high prediction accuracy up to 95% for each stage in the hierarchical approach and 85% overall for the multi-class approach
- **Evidence pointer** Tables 1 and 2, Figures 1-4, location not provided
- **Concern** The full results tables and figures are not included in the provided material, so the reported accuracy values cannot be independently verified. Additionally, the dataset sizes used for each classification stage are not clearly stated, particularly the number of positive and negative samples in each training and testing set. The class imbalance, especially for the small SSB set (347 sequences), could significantly affect the reported metrics, and the manuscript does not discuss how imbalance was handled beyond random subsampling in the hierarchical approach.
- **Why it matters** Without full results and clear dataset descriptions, the reader cannot assess whether the reported accuracies are robust, whether they are driven by class imbalance, or whether they generalize. The SSB set is particularly small, and the claim of improved SSB prediction requires careful examination of the evaluation setup.
- **Resolution test** Provide full tables and figures with all metrics, standard deviations, and dataset sizes for each classification stage. Clarify how class imbalance was addressed and report performance stratified by class. Include confusion matrices or per-class precision and recall for the multi-class model.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that the models can be used to accurately predict single-stranded DBPs, which is underexplored
- **Evidence pointer** Section 3.1, Figure 3B, location not provided
- **Concern** The claim of accurate SSB prediction is based on the hierarchical approach where SSB prediction depends on correct classification at two prior stages (non-NABP/NABP and DBP/RBP). The reported SSB accuracy of 79.04% for the hierarchical approach is a product of three stage accuracies, and the multi-class approach reports 90.28% for SSBs. However, the manuscript does not provide a direct comparison of SSB prediction performance against existing SSB-specific predictors or against the authors' prior SSB/DSB and SSB/RBP classifiers. The practical utility of the approach for identifying novel SSBs from uncharacterized proteins is asserted but not demonstrated with case studies or external validation.
- **Why it matters** The claim of accurate SSB prediction is a key contribution of the work. Without external validation or comparison to existing methods, the reader cannot determine whether the approach offers genuine improvement over the state of the art or whether the reported accuracy translates to real-world performance on diverse protein sequences.
- **Resolution test** Provide external validation on an independent benchmark dataset of SSBs and non-SSBs. Compare SSB prediction performance against existing SSB predictors and the authors' prior classifiers. Include case studies or examples of novel SSB predictions with experimental support if available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that combining ESM2 features with machine learning methods achieves a 13% overall accuracy improvement over their previous non-ESM2 approach (85% versus 72%)
- **Evidence pointer** Section 4, Discussion, location not provided
- **Concern** The comparison with the previous approach (Wu and Guo 2024) is not presented in a controlled manner. It is unclear whether the same datasets, train/test splits, and evaluation protocols were used. The improvement could be due to the ESM2 features, the updated datasets, or differences in model selection and hyperparameter tuning. The manuscript does not report results using the previous PSSM-based features on the current datasets, which would isolate the contribution of ESM2.
- **Why it matters** The claimed improvement is a central result of the paper. Without a controlled comparison, the reader cannot attribute the improvement to the ESM2 features specifically, which is the stated novelty of the work.
- **Resolution test** Perform an ablation study using the same datasets and protocols with PSSM-based features and with ESM2 features. Report the accuracy difference and discuss the contribution of each component.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that the datasets and code are available at a Figshare link and a GitHub link for hyperparameters
- **Evidence pointer** Data availability section, Section 2.3, location not provided
- **Concern** The manuscript states that datasets and code are available, but the provided links are not accessible in the review material. The hyperparameter file link is mentioned but not shown. The dataset construction details, including the exact redundancy removal procedure, sequence sources, and the criteria for defining SSB, DSB, RBP, and non-NABP, are not fully described. The random subsampling percentages (79% non-NABP, 81% RBP, 8.3% DSB, 6.2% RBP, 2.7% non-NABP) are stated but the rationale for these specific proportions is not explained.
- **Why it matters** Reproducibility is a core requirement for computational biology papers. Without full dataset descriptions and accessible code, other researchers cannot replicate the results or apply the method to their own data.
- **Resolution test** Ensure all links are functional and provide a detailed description of dataset construction, including sequence sources, filtering criteria, and the rationale for subsampling proportions. Provide the hyperparameter file as supplementary material.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.4, Evaluation metrics
- **Evidence pointer** Equations 1-6, location not provided
- **Issue** The equations for the evaluation metrics are referenced but not shown in the provided text. The definitions of accuracy, sensitivity, specificity, MCC, and F1 are standard, but the notation is not fully explained.
- **Required correction** Include the equations or provide clear verbal definitions of each metric in the text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 3.2, Multi-class approach
- **Evidence pointer** Figure 4, location not provided
- **Issue** The discussion of the multi-class approach results is brief and does not explain why SSB has the best prediction accuracy across all models. The reader is left to speculate on the reasons for this pattern.
- **Required correction** Add a brief discussion of potential reasons for the observed performance pattern, such as sequence features or dataset composition.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.1, Datasets
- **Evidence pointer** Section 2.1, location not provided
- **Issue** The manuscript states that datasets were used from a recent study but does not describe the original sources of the sequences or the criteria for functional annotation. The reader cannot assess potential biases in the dataset.
- **Required correction** Provide a brief description of the sequence sources and annotation criteria, or reference the original study with sufficient detail.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.2, Features from ESM2
- **Evidence pointer** Section 2.2, location not provided
- **Issue** The manuscript states that per-sequence representations are obtained by averaging per-residue representations. This is a common approach, but the authors do not discuss whether alternative pooling methods (e.g., attention-based pooling) were considered or whether the averaging approach is optimal for this task.
- **Required correction** Briefly justify the averaging approach or note that alternative pooling methods were not explored.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.1, Hierarchical approach
- **Evidence pointer** Table 2, location not provided
- **Issue** The comparison with published predictors in Table 2 is mentioned but the specific methods and their performance values are not described in the text. The reader cannot assess the fairness of the comparison.
- **Required correction** Briefly describe the compared methods and the conditions of the comparison in the text.

## Risk / unsupported claims
- The claim of 13% overall accuracy improvement over the previous approach is not supported by a controlled comparison in the provided material
- The claim of accurate SSB prediction is not validated on external benchmarks or compared to existing SSB-specific predictors
- The reported accuracy values cannot be independently verified without full tables and figures
- The practical utility of the models for predicting novel SSBs from uncharacterized proteins is asserted but not demonstrated with case studies
- The statement that protein language model features alone dramatically increase performance is based on prior work and not directly demonstrated in this manuscript

## Assessment against Nature-style criteria
- **Originality** Limited. The approach combines existing ESM2 embeddings with classical classifiers for a problem the authors have previously addressed. The novelty lies primarily in the application of ESM2 to the specific task of NABP type prediction with explicit SSB inclusion, which is incremental rather than transformative.
- **Scientific importance** Moderate. Improved prediction of NABP types, particularly SSBs, has practical value for functional annotation of uncharacterized proteins. However, the impact is limited by the lack of external validation and the incremental nature of the improvement.
- **Interdisciplinary readership** Limited. The work is primarily of interest to computational biologists and bioinformaticians working on protein function prediction. The methods and results are unlikely to attract a broader readership.
- **Technical soundness** Partially assessable. The methodology is generally sound, but the missing results tables and figures, unclear dataset descriptions, and lack of controlled comparisons prevent full assessment. The use of 100 independent train/test splits is a strength.
- **Readability for nonspecialists** Acceptable. The manuscript is clearly written and the hierarchical and multi-class approaches are explained in an accessible manner. However, some technical details, such as the ESM2 feature extraction process, may be challenging for readers unfamiliar with protein language models.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a relevant problem and the approach is reasonable, but the incomplete evidence base, lack of controlled comparisons, and missing external validation prevent a full assessment of the claims. The authors should provide complete results, clarify dataset construction, perform ablation studies to isolate the contribution of ESM2 features, and validate the models on independent benchmarks. If these concerns are addressed, the work could be considered for publication in a specialized bioinformatics journal, though the incremental novelty may limit its appeal for a high-impact venue.