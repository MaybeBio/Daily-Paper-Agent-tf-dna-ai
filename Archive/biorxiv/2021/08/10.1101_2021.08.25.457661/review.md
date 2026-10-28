## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure descriptions
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors propose GraphSite, a sequence-based predictor of protein-DNA binding residues that uses AlphaFold2-predicted structures and a graph transformer with k-nearest masking, and report substantial improvements over existing sequence-based and structure-based methods on independent test sets
- **Visible evidence base** Abstract, Sections 1-4, Tables 1 and 3 (referenced), Figures 2-6 (referenced), Supplementary Tables S1-S5 and Figures S1-S4 (referenced but not provided in full)
- **Missing materials affecting confidence** Full tables and figures not provided; exact numerical results for all metrics in Tables 2 and 3 not visible; supplementary materials not available for inspection; details of baseline method implementations and hyperparameter grids not fully specified

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially impactful application of AlphaFold2-predicted structures to the problem of DNA-binding site prediction. The core idea of using predicted structures with a graph transformer is novel and well-motivated. However, the evidence provided is insufficient to fully evaluate the claims. Key methodological details, complete numerical results, and statistical rigor are not fully visible. The claim of outperforming structure-based methods that use native structures is strong and requires careful scrutiny, particularly regarding potential data leakage, baseline fairness, and the impact of structure prediction quality.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function annotation, specifically DNA-binding site prediction. Researchers interested in leveraging AlphaFold2 predictions for downstream functional inference. Methodologists developing graph-based deep learning approaches for protein structure representation. The work may also interest experimental biologists seeking computational prioritization of DNA-binding residues for mutagenesis or functional studies.
- **Major strengths** The problem is well-defined and practically important. The use of AlphaFold2-predicted structures is timely and addresses a key limitation of sequence-based methods. The graph transformer architecture with k-nearest masking is a sensible and potentially powerful approach. The authors provide datasets, predicted structures, source code, and a web server, which is commendable for reproducibility. The inclusion of an independent test set (Test_181) with a time cutoff designed to avoid template leakage is a thoughtful design choice.
- **Major Concerns**
- **Minor Comments**
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is high; the combination of AlphaFold2 structures with graph transformers for binding site prediction is novel. Scientific importance is potentially high, given the broad utility of accurate binding site prediction. Interdisciplinary readership is plausible, spanning structural biology, machine learning, and genomics. Technical soundness cannot be fully assessed from the provided material; several methodological details and complete results are missing. Readability for nonspecialists is generally good, though some technical sections assume familiarity with deep learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the preliminary results are suggestive, but the current evidence base is insufficient to establish the claims with confidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that GraphSite "substantially improves over the latest sequence-based and structure-based methods" and specifically surpasses the state-of-the-art structure-based method by 16.4% in AUPR and 11.2% in MCC on Test_181.
- **Evidence pointer** Section 3.3, Table 3 (not fully visible)
- **Concern** The full numerical results for all methods on both Test_129 and Test_181 are not provided in the visible text. Only selected metrics (AUPR, MCC) are mentioned for the comparison with the best structure-based method. Without the complete table, it is impossible to verify the claimed improvements, assess variance, or evaluate performance across all metrics (e.g., F1, recall, precision, AUC).
- **Why it matters** The central claim of the paper rests on these comparative results. Incomplete reporting prevents independent verification and undermines confidence in the conclusions.
- **Resolution test** Provide the full Table 3 with all metrics, standard deviations, and statistical significance tests for all methods on both test sets. Include the exact p-values for the comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors state that GraphSite outperforms structure-based methods that use native protein structures, and that this is partly due to the high quality of AlphaFold2-predicted structures.
- **Evidence pointer** Section 3.3, Section 3.4, Figure 4
- **Concern** The comparison with structure-based methods may be unfair if those methods were not retrained or re-optimized on the same training data or if their input features differ substantially. Additionally, the claim that AlphaFold2 structure quality is crucial is supported only by a correlation analysis (Figure 4), which does not establish causation. The authors do not report results using native structures for a model retrained on native structures, which would be a more direct test of the impact of structure quality.
- **Why it matters** If the comparison is not fair, the claimed superiority may be an artifact of experimental setup rather than a genuine methodological advance. The causal link between structure quality and performance is not established.
- **Resolution test** Clarify whether all baseline methods were retrained on the same training set with the same cross-validation protocol. Report results for GraphSite trained and tested on native structures. Provide a more rigorous analysis of the relationship between structure quality and performance, e.g., by stratifying results by GDT bins and testing for a monotonic trend.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The methods section describes the use of AlphaFold2 with specific genetic databases and a "single representation" feature, but the exact implementation details are incomplete.
- **Evidence pointer** Section 2.2, Section 2.4
- **Concern** The description of the AlphaFold2 implementation is incomplete. The authors state they downloaded model parameters and databases but do not specify the exact version of AlphaFold2, the number of recycles, or the precise settings used for structure prediction. The "single representation" feature is mentioned but not fully defined in terms of its dimensionality and how it is derived. The graph transformer architecture is described, but key hyperparameters (e.g., number of layers, hidden dimensions, dropout) are only partially specified, and the grid search ranges are not provided.
- **Why it matters** Reproducibility is a core requirement for scientific publication. Without complete implementation details, other researchers cannot replicate the method or verify the results.
- **Resolution test** Provide a complete description of the AlphaFold2 settings, the exact definition of the "single representation" feature, and the full hyperparameter grid and final chosen values. Consider releasing the training and inference code in a documented form.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that GraphSite's performance is significantly better than other methods, and that the performance gap widens with increasing non-local contacts.
- **Evidence pointer** Section 3.1, Section 3.3, Figure 3
- **Concern** The statistical significance of the performance differences is not fully reported. The authors mention significance tests in Section 2.5 but do not provide the results of these tests in the visible text. The analysis in Figure 3, showing performance as a function of non-local contacts, does not include confidence intervals or statistical tests for the trend.
- **Why it matters** Without proper statistical testing, the observed differences could be due to chance, especially given the relatively small test sets. The claim of a widening gap with non-local contacts requires statistical support.
- **Resolution test** Report the p-values for all pairwise comparisons between GraphSite and each baseline method on both test sets. For Figure 3, provide confidence intervals and a statistical test for the trend (e.g., a test for interaction between method and contact bin).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Equation (1)
- **Evidence pointer** Section 2.2
- **Issue** The normalization equation is referenced but not shown in the visible text. The description of the feature normalization is incomplete.
- **Required correction** Include the explicit equation and describe the min and max values used for normalization.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.1, Table 1
- **Evidence pointer** Section 2.1
- **Issue** The details of the dataset construction, including the number of positive and negative residues, are not visible. The description of the data augmentation procedure is brief.
- **Required correction** Provide the full Table 1 with residue counts and clarify the augmentation procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.1, Figure 2
- **Evidence pointer** Section 3.1
- **Issue** The precision-recall curves and ROC curves are referenced but not shown. The text mentions "Figure 2 and Supplementary Figure S1" but does not describe the key visual patterns.
- **Required correction** Include the figures or provide a more detailed description of the curves in the text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.4, Figure 4
- **Evidence pointer** Section 3.4
- **Issue** The correlation between GDT and AUPR is described, but the strength of the correlation (e.g., Pearson or Spearman coefficient) is not reported.
- **Required correction** Report the correlation coefficient and its significance.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Section 4, Discussion
- **Evidence pointer** Section 4
- **Issue** The phrase "simultaneously solves the limitations of the current sequence-based and structure-based methods" is somewhat overstated, as the method still depends on the quality of predicted structures and does not address all limitations of either class.
- **Required correction** Soften the claim to "addresses key limitations" or similar.

## Risk / unsupported claims
- The claim that GraphSuite is "the first" to use AlphaFold2-predicted structures for binding site prediction is not verifiable from the provided text and may be difficult to substantiate.
- The claim that the performance improvement over BiLSTM is "likely due to its better capability in capturing long-range contact information" is presented as a hypothesis but not directly tested.
- The statement that the combined feature groups are "nonredundant" is based on ablation results that are not fully visible.
- The claim that the method is "practical and much more powerful" for situations where only sequences are available is supported by the Test_181 results, but the full comparison is not visible.
- The assertion that the performance drop when using native structures is due to training on predicted structures is plausible but not rigorously demonstrated.