## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusions, data availability) as provided by the author. Figures, tables, and supplementary materials referenced but not fully available for inspection.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and adequacy of evidence as presented in the supplied text. No independent verification of data or code was performed.
- **Shared manuscript claim summary** The authors propose GeSite, a structure-based nucleic acid-binding residue (NBS) prediction method combining a domain-adaptive protein language model (ESM-DBP and newly developed ESM-RBP) with an E(3)-equivariant graph neural network (EGNN). They claim superior or comparable performance to state-of-the-art (SOTA) methods on multiple benchmark datasets, robustness on low-structure-similarity and newly released proteins, and interpretability of predictions via GNNExplainer.
- **Visible evidence base** Abstract, Introduction, Methods (datasets, model architecture, training details), Results (ablation on language model, architecture comparison, SOTA comparison, structural similarity analysis, case studies, interpretability), Conclusions, Data availability statement. Tables 1-3 and Figures 1-7 are referenced but not fully visible in the provided text.
- **Missing materials affecting confidence** Full tables (especially Table 3 with SOTA comparisons), all figures, supplementary texts (S2, S3), and detailed hyperparameter settings. Statistical significance testing details are incomplete. The exact composition of the RNA-285_Test set and the structural similarity filtering procedure are described but not fully verifiable.

## Reviewer
- **Overall assessment** The manuscript presents a technically sound and potentially valuable contribution to the field of nucleic acid-binding residue prediction. The combination of domain-adaptive pretraining with an equivariant GNN is a reasonable and well-motivated design choice. The reported performance improvements, particularly on low-similarity proteins, are encouraging. However, the evidence as presented is incomplete in several key areas, including full performance tables, statistical rigor, and clarity of the interpretability analysis. The core claims are plausible but not fully established from the provided material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function annotation, protein-nucleic acid interaction prediction, and development of deep learning methods for structural biology. The domain-adaptive pretraining strategy may also interest researchers working on protein language models and transfer learning. The interpretability analysis could appeal to those studying model explainability in bioinformatics.
- **Major strengths** 1. The methodological combination of domain-adaptive PLMs with an equivariant GNN is novel and well-justified. 2. The use of a large, non-redundant RNA-binding protein dataset for domain-adaptive pretraining is a significant effort. 3. The evaluation includes multiple benchmark datasets and a newly constructed test set, addressing generalization. 4. The interpretability analysis is a valuable addition, providing insight into model behavior beyond raw performance metrics.
- **Major Concerns** 1. The full performance comparison table (Table 3) is not visible, preventing verification of the claimed SOTA improvements. 2. Statistical significance testing is only partially reported; the p-value calculation method is unclear and may not be appropriate. 3. The interpretability analysis, while interesting, lacks quantitative validation of whether the identified salient regions truly correspond to functional domains. 4. The construction of the RNA-285_Test set and the structural similarity filtering are described but not fully detailed, raising questions about potential biases.
- **Minor Comments** 1. The abstract claims "superior or comparable" performance, but the specific improvements are only given for AUC; other metrics should be summarized. 2. The introduction could better contextualize the limitations of existing methods, particularly regarding interpretability. 3. The methods section on EGNN implementation is brief; more details on hyperparameters and training convergence would be helpful. 4. The case study on African swine fever virus DNA ligase is interesting but would benefit from a more detailed biological interpretation.
- **Technical failings that need to be addressed before the case is established** 1. Full performance tables and figures must be provided for verification. 2. Statistical significance testing should be clarified and applied consistently across all comparisons. 3. The interpretability analysis needs quantitative support, such as enrichment analysis of salient residues against known functional domains. 4. The structural similarity filtering procedure should be described in sufficient detail to allow replication.
- **Assessment against Nature-style criteria** Originality: High. The combination of domain-adaptive pretraining with equivariant GNNs for NBS prediction is a novel contribution. Scientific importance: Moderate to high. Accurate NBS prediction is a relevant problem in functional genomics, and the method shows promise. Interdisciplinary readership: Moderate. The work will primarily interest computational biologists and bioinformaticians, with potential appeal to structural biologists. Technical soundness: Moderate. The approach is well-motivated, but the evidence is incomplete, particularly regarding statistical rigor and full performance reporting. Readability for nonspecialists: Good. The manuscript is generally well-written and accessible, though some technical details could be clarified.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the preliminary results are encouraging, but the manuscript requires substantial revisions to fully establish the claims, particularly regarding performance verification, statistical rigor, and interpretability validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that GeNet is "superior or comparable to state-of-the-art prediction methods" across multiple benchmark test sets, with specific AUC improvements of 0.75%, 0.22%, and 9.96% over the second-best method on DNA-129_Test, DNA-181_Test, and RNA-117_Test, respectively.
- **Evidence pointer** Table 3, location not provided
- **Concern** The full performance comparison table (Table 3) is not visible in the provided material. Without the complete table, it is impossible to verify the claimed improvements, assess the performance across all metrics (e.g., MCC, F1, precision, recall), or evaluate the consistency of the improvements across different datasets. The claim of "superior or comparable" is too vague without the full data.
- **Why it matters** The central claim of the manuscript is that GeSite outperforms existing methods. This claim cannot be evaluated without the complete performance data. The reader needs to see the full table to judge whether the improvements are consistent, meaningful, and not due to chance or dataset-specific artifacts.
- **Resolution test** Provide the full Table 3 with all metrics (AUC, MCC, F1, precision, recall, etc.) for all methods on all datasets. Include standard deviations or confidence intervals where applicable. Clearly indicate which differences are statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report p-values for the comparison between GeSite and control methods, stating that "the p-values against most methods are statistically significant, except that against ESM-NBR and CLAPE on DNA-129_Test are relatively high, which are 3.39e-02 and 7.85e-01, respectively."
- **Evidence pointer** Results section, "Comparison with state-of-the-art methods", location not provided
- **Concern** The method for calculating p-values is unclear. The authors state that "the probability of native NBS being predicted a positive sample is employed since the limited computational accuracy," which is not a standard approach for hypothesis testing. It is unclear what null hypothesis is being tested, how the p-value is computed, and whether multiple testing corrections were applied. A p-value of 7.85e-01 for CLAPE suggests no significant difference, yet the authors still claim superiority. The statistical framework needs to be clarified and justified.
- **Why it matters** Statistical significance is crucial for supporting the claim that GeSite is superior to existing methods. An unclear or inappropriate statistical test undermines the validity of the performance comparisons. The reader cannot assess whether the observed differences are meaningful or due to random variation.
- **Resolution test** Clearly describe the statistical test used, including the null hypothesis, the test statistic, and how the p-value is computed. Justify the choice of test and apply it consistently across all comparisons. Consider using standard tests such as the Wilcoxon signed-rank test or McNemar's test for paired comparisons. Report effect sizes and confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability validation
- **Claim pointer** The authors state that "interpretability analysis exposes the perception of the prediction model on various remote and close functional domains, which is the source of its discernment" and that the model "captures key information about nucleic acid-binding domains."
- **Evidence pointer** Results, "Interpretability and visualization", location not provided
- **Concern** The interpretability analysis using GNNExplainer identifies salient residues, but there is no quantitative validation that these residues are enriched for known functional domains or binding sites. The authors show examples (e.g., 5trd_A, 5ui5_V) where salient regions overlap with known domains, but this is anecdotal. A systematic enrichment analysis against a database of functional domains or known binding sites would strengthen the claim that the model learns biologically meaningful features.
- **Why it matters** The interpretability claim is a key differentiator of this work. Without quantitative validation, the claim that the model "perceives" functional domains remains speculative. The reader cannot determine whether the identified salient regions are truly informative or merely coincidental.
- **Resolution test** Perform a systematic enrichment analysis of salient residues against known nucleic acid-binding domains (e.g., from Pfam or InterPro) across all test proteins. Report enrichment statistics (e.g., hypergeometric test p-values) and show that the model's salient regions are significantly enriched for functional domains compared to random regions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Dataset construction and bias
- **Claim pointer** The authors constructed a new test set, RNA-285_Test, from newly released protein-RNA complexes, filtering by sequence identity (CD-HIT, threshold 0.4) and structural similarity (TM-score > 0.5).
- **Evidence pointer** Methods, "Benchmark datasets", location not provided
- **Concern** The description of the RNA-285_Test construction is brief. It is unclear how the "newly released" complexes were selected, whether they overlap with the training set in terms of protein families or folds, and whether the TM-score filtering was applied against the training set or against all existing structures. The threshold of 0.5 for TM-score is relatively high and may still allow significant structural similarity. The potential for bias in this new test set needs to be addressed.
- **Why it matters** The generalization claim relies heavily on the new test set. If the test set is not sufficiently distinct from the training set, the reported performance may be inflated. The reader needs to understand the construction process to assess the validity of the generalization claim.
- **Resolution test** Provide a detailed description of the RNA-285_Test construction, including the source of the complexes, the exact filtering steps, and the distribution of TM-scores against the training set. Show that the test set is structurally distinct from the training set and that the performance on this set is not due to training set leakage.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of claims
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that GeSite is "superior or comparable" to SOTA methods, but the specific improvements are only given for AUC. This is vague and does not give the reader a clear picture of the overall performance.
- **Required correction** Summarize the key performance metrics (e.g., MCC, F1) in the abstract, or state the range of improvements across all metrics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods, "Implement of E(3) Equivariant Graph Neural Network"
- **Evidence pointer** Methods, location not provided
- **Issue** The description of the EGNN architecture is brief. The equations are referenced but not fully explained. Hyperparameters such as learning rate, batch size, and number of epochs are given, but other details such as the number of hidden units, dropout rates, and optimization schedule are missing.
- **Required correction** Provide a more detailed description of the EGNN architecture, including all hyperparameters and training details, to allow replication.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation of results
- **Affected element** Results, "Performance of different network architectures"
- **Evidence pointer** Results, location not provided
- **Issue** The comparison of different network architectures is presented only through figures (Figures 3A and 3B). The text mentions AUC and MCC values but does not provide a table with the exact numbers. This makes it difficult to compare the architectures quantitatively.
- **Required correction** Include a table with the exact performance metrics (AUC, MCC, AP) for all architectures on both datasets.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability statement
- **Evidence pointer** Data Availability, location not provided
- **Issue** The statement mentions that weights and code are available, but it is unclear whether the training data (e.g., UniRBP40) and the new test set (RNA-285_Test) are also available. The statement says "DNA- and RNA-binding residues datasets are freely accessible," but it is not clear if this includes the newly constructed RNA-285_Test.
- **Required correction** Clarify which datasets are available and provide direct links to all data and code.

## Risk / unsupported claims
- The claim that GeSite is "superior or comparable" to SOTA methods cannot be fully verified without the complete Table 3.
- The claim that the model's interpretability analysis reveals perception of functional domains is not quantitatively validated.
- The claim of robustness on low-structure-similarity proteins is based on a filtering procedure that is not fully described, and the results are not fully presented.
- The p-value calculation method is unclear and may not be statistically valid.
- The performance comparison on the new RNA-285_Test set is not fully detailed, and the potential for bias is not addressed.