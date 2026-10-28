## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, and supplementary sections) as provided.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and clarity of claims based solely on the supplied text. No external data, code, or supplementary files were accessed.
- **Shared manuscript claim summary** The authors propose a computational method for identifying DNA-binding proteins (DBPs) using six feature extraction methods, feature splicing, Z-score standardization, MRMD dimensionality reduction, and an XGBoost classifier. They report superior or comparable performance on benchmark datasets PDB1075, PDB186, PDB14189, and PDB2272, with accuracy of 78.26% (PDB2272) and 85.48% (PDB186), and MCC values of 0.5652 and 0.713, respectively.
- **Visible evidence base** Tables 1–5 (referenced but not fully shown in text), Figures 1–2 (referenced but not shown), equations 1–8, and textual descriptions of results. Dataset descriptions in Table 2 (referenced but not shown).
- **Missing materials affecting confidence** Actual tables and figures are not provided in the supplied text, preventing independent verification of numerical results, feature dimensions, and comparative performance. Code, hyperparameters, and detailed experimental settings are not described. The MRMD dimensionality reduction step lacks specific parameter choices and validation of the selected feature counts.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in bioinformatics, namely the computational identification of DNA-binding proteins, and applies a well-established machine learning algorithm (XGBoost) with a combination of standard feature extraction methods. The reported results are plausible and consistent with prior work in the field. However, the manuscript has several methodological gaps, including incomplete reporting of experimental details, lack of statistical validation, and insufficient discussion of limitations and generalizability. The novelty is incremental, as the approach largely combines existing techniques without introducing a new conceptual framework. The evidence presented is sufficient to support the main claims only if the missing details are clarified and additional validation is provided.
- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics, particularly those working on protein function prediction, DNA-protein interactions, and machine learning applications in genomics. The method could be of interest to those seeking simple, interpretable classifiers for DBP identification, though the incremental improvement over existing methods may limit broader appeal.
- **Major strengths** The manuscript is clearly written and follows a logical structure. The use of multiple feature extraction methods and a robust ensemble classifier (XGBoost) is methodologically reasonable. The authors compare their method against several existing approaches on benchmark datasets, which is commendable. The inclusion of MRMD for dimensionality reduction is a thoughtful step to address the curse of dimensionality.
- **Major Concerns** The following concerns are identified.
- **Minor Comments** The following comments are identified.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality: The approach is a combination of existing feature extraction methods and XGBoost, which has been applied in similar contexts. The novelty is limited, as no new algorithm or conceptual insight is introduced. Scientific importance: The problem of DBP identification is of moderate importance, but the incremental performance gains over existing methods do not constitute a major advance. Interdisciplinary readership: The work is primarily of interest to bioinformatics specialists; the methods and results are unlikely to attract a broad interdisciplinary audience. Technical soundness: The methodology is generally sound, but the lack of detailed experimental reporting and statistical validation weakens the technical rigor. Readability for nonspecialists: The manuscript is accessible to readers with a basic background in machine learning and protein sequence analysis, but the dense citation list and lack of explanatory context for some methods may hinder nonspecialists.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding experimental reproducibility, statistical validation, and clarification of the novelty claim.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors claim that their method achieves superior results on PDB186 and PDB2272, with specific accuracy and MCC values.
- **Evidence pointer** Tables 4 and 5, referenced in Sections "Independent Data Set of PDB186" and "Independent Data Set of PDB2272"; location not provided.
- **Concern** The manuscript does not provide the actual tables or figures, making it impossible to verify the reported numerical results. Additionally, the experimental setup is incompletely described: the train-test split for PDB1075 (30% random split) is mentioned, but the exact random seed, number of runs, and variance across runs are not reported. For the independent datasets, the training and testing protocols are described, but the hyperparameters of the XGBoost model (e.g., learning rate, max depth, number of estimators, subsampling ratios) are not specified. Without these details, the results cannot be reproduced or independently validated.
- **Why it matters** Reproducibility is a cornerstone of scientific research. The lack of detailed experimental parameters and raw results undermines the credibility of the reported performance and prevents other researchers from building upon or verifying the method.
- **Resolution test** The authors should provide the full tables and figures, specify all hyperparameters and random seeds, and report results over multiple runs (e.g., mean and standard deviation) to demonstrate robustness.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validation
- **Claim pointer** The authors claim that their method outperforms other methods on PDB186 and PDB2272 in terms of accuracy, MCC, and specificity.
- **Evidence pointer** Sections "Independent Data Set of PDB186" and "Independent Data Set of PDB2272"; location not provided.
- **Concern** The performance comparisons are presented as point estimates without any statistical significance testing. It is unclear whether the observed differences between the proposed method and the comparators are statistically significant or within the range of random variation. For example, the difference in MCC between the proposed method (0.713) and Adilina's work (0.670) on PDB186 may not be significant given the dataset size. No confidence intervals, p-values, or cross-validation results are provided.
- **Why it matters** Without statistical validation, the claim of "superior performance" is not rigorously supported. This is particularly important in machine learning applications where small differences in metrics can be due to chance.
- **Resolution test** The authors should perform statistical tests (e.g., McNemar's test for classifier comparison) or provide confidence intervals for the reported metrics. Alternatively, they could report results from multiple cross-validation folds to demonstrate consistency.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The authors state that MRMD is used for dimensionality reduction, and after this step, the dimensions of PDB14189 and PDB2272 are 379, and those of PDB1075 and PDB186 are 1460.
- **Evidence pointer** Section "Dimensionality Reduction by Max-Relevance-Max-Distance"; location not provided.
- **Concern** The MRMD method is described in general terms, but the specific implementation details are missing. The authors do not explain how the "most effective group" of features is selected, what criteria are used to determine the optimal number of features, or whether the dimensionality reduction is performed on the training set only (to avoid data leakage) or on the combined dataset. The choice of feature counts (379 and 1460) appears arbitrary without a clear justification or validation.
- **Why it matters** Dimensionality reduction can significantly impact model performance. If the feature selection is performed incorrectly (e.g., using test data), the reported results may be optimistically biased. The lack of clarity on this step undermines the methodological rigor.
- **Resolution test** The authors should describe the MRMD procedure in detail, including how the optimal feature subset is determined, and confirm that dimensionality reduction is applied only to the training data. They should also provide a rationale for the selected feature counts.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Novelty
- **Claim pointer** The authors claim that their method uses "fewer features and simpler recognition methods than other methods" while achieving satisfactory results.
- **Evidence pointer** Abstract and Section "Introduction"; location not provided.
- **Concern** The novelty of the proposed approach is not clearly articulated. The combination of six existing feature extraction methods with XGBoost is a straightforward integration of known techniques. The authors do not compare the number of features used in their method against those used in the comparator methods, nor do they demonstrate that their method is simpler in any meaningful way. The claim of "fewer features" is not substantiated with quantitative comparisons.
- **Why it matters** For a method to be publishable in a high-impact venue, it must offer a clear advance over the state of the art. The current manuscript does not convincingly demonstrate such an advance, either in terms of performance, efficiency, or interpretability.
- **Resolution test** The authors should provide a direct comparison of feature counts and model complexity against the comparator methods. They should also discuss what specific aspect of their approach is novel and why it matters for the field.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors evaluate their method on four benchmark datasets and report consistent performance improvements.
- **Evidence pointer** Sections "Performance Analysis", "Independent Data Set of PDB186", and "Independent Data Set of PDB2272"; location not provided.
- **Concern** The evaluation is limited to datasets derived from the Protein Data Bank, which may not represent the full diversity of DNA-binding proteins. The authors do not discuss potential biases in the datasets (e.g., sequence redundancy, class imbalance) or how their method might perform on more challenging, real-world datasets. The generalizability of the method to other organisms or protein families is not addressed.
- **Why it matters** A method that works well on benchmark datasets may not perform adequately in practical applications. The lack of discussion on generalizability limits the practical utility of the proposed approach.
- **Resolution test** The authors should discuss the limitations of their evaluation and, if possible, include additional experiments on more diverse datasets or provide a qualitative analysis of the types of proteins where the method succeeds or fails.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided.
- **Issue** The abstract states that "the decline in many life activities is closely related to DBPs," which is vague and potentially misleading. DNA-binding proteins are involved in many processes, but the phrase "decline in life activities" is not a standard scientific term.
- **Required correction** Rephrase to be more specific, such as "dysregulation of DNA-binding proteins is associated with various diseases and cellular dysfunctions."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section "Extracting Features"
- **Evidence pointer** Section "Extracting Features"; location not provided.
- **Issue** The text states that "the spliced features are represented by Z∗" but the notation is not consistently used in subsequent sections. In the standardization section, the notation changes to M∗, which may confuse readers.
- **Required correction** Use consistent notation throughout the manuscript, or clearly define the relationship between Z∗ and M∗.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Dimensionality Reduction by Max-Relevance-Max-Distance"
- **Evidence pointer** Section "Dimensionality Reduction by Max-Relevance-Max-Distance"; location not provided.
- **Issue** The authors mention that MRMD was developed by Zou et al. in 2015, but the citation is not provided in the reference list. Additionally, the URL for the MRMD software is given, but it is not clear if the software version used is the latest.
- **Required correction** Add the appropriate citation for the MRMD method and specify the version of the software used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language
- **Affected element** Section "Extreme Gradient Boosting Algorithm"
- **Evidence pointer** Section "Extreme Gradient Boosting Algorithm"; location not provided.
- **Issue** The sentence "It can optimize the objective function at the same time because the tree is prepriced" is unclear. The term "prepriced" is not standard and likely a typographical error.
- **Required correction** Revise to "It can optimize the objective function at the same time because the tree is pre-pruned" or similar.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Formatting
- **Affected element** Section "Experimental Results With PDB2272 and PDB186 as Test Set"
- **Evidence pointer** Section "Experimental Results With PDB2272 and PDB186 as Test Set"; location not provided.
- **Issue** The section title is grammatically awkward. It should be "Experimental Results with PDB2272 and PDB186 as Test Sets" or "Experimental Results Using PDB2272 and PDB186 as Test Sets."
- **Required correction** Revise the section title for grammatical correctness.

## Risk / unsupported claims
- The claim that the proposed method uses "fewer features and simpler recognition methods" is not supported by quantitative comparisons with other methods.
- The reported performance metrics (accuracy, MCC, specificity) cannot be independently verified because the tables and figures are not provided in the supplied text.
- The claim that the method "outperforms" other methods is not supported by statistical significance testing.
- The generalizability of the method beyond the four benchmark datasets is not demonstrated or discussed.
- The statement in the abstract that "the decline in many life activities is closely related to DBPs" is vague and not substantiated with specific evidence.