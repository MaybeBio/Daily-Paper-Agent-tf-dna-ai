## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusion sections. Figures and tables are referenced but not provided.
- **Assessment boundary** Assessment is limited to the claims, methods, and results as described in the provided text. No code, data, or supplementary materials were inspected.
- **Shared manuscript claim summary** The authors claim that existing benchmark data sets for DNA-binding protein prediction contain substantial flaws, including train/test overlap, duplicate sequences, and DNA sequences mislabeled as proteins. They introduce new, larger, cleaned data sets with non-overlapping splits, propose new evaluation tasks including species-holdout benchmarks, and show that a simple BLAST nearest neighbor model and a gradient boosting model with language model features outperform two published neural network models.
- **Visible evidence base** Text descriptions of data set construction, model implementations, and results. Figures 1 to 7 are referenced but not visible. No tables, code, or data files were provided.
- **Missing materials affecting confidence** Figures 1 to 7, Table 1, Table 2, Table 3, the GitHub repository, and any supplementary information. Without these, quantitative results and statistical comparisons cannot be independently verified.

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely problem in computational biology, namely the reliability of benchmark data sets for protein function prediction. The authors identify real and concerning flaws in widely used data sets, and their proposed new data sets and evaluation protocols are a valuable contribution. The finding that a simple nearest neighbor baseline outperforms more complex neural networks is an important cautionary result for the field. However, the manuscript as presented has several significant weaknesses. The most critical is the lack of visible figures and tables, which prevents verification of the central quantitative claims. Additionally, the evaluation of only two neural network baselines, both from the same lineage, limits the strength of the comparative claims. The perturbation analysis is thoughtful but the interpretation is somewhat speculative. The species-holdout analysis is a strong addition but the presentation is incomplete without the figures. Overall, the work is promising and the data sets are likely to be useful, but the evidence as presented is insufficient to fully establish the claims.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those developing machine learning models for DNA-binding protein identification. Researchers who use benchmark data sets for model evaluation will also be interested, as the identified flaws in existing data sets have broad implications. The finding that a BLAST nearest neighbor baseline is competitive with deep learning models is relevant to anyone developing or evaluating such models.
- **Major strengths** The identification of specific, concrete flaws in existing benchmark data sets is a significant and actionable contribution. The proposed new data sets are larger, cleaned, and split to avoid overlap, which addresses the main criticisms of prior work. The inclusion of species-holdout tasks is a realistic and valuable evaluation protocol. The perturbation analysis is a creative approach to understanding model behavior. The finding that a simple baseline outperforms neural networks is an important and sobering result.
- **Major Concerns** The absence of figures and tables is a major limitation. The comparative evaluation includes only two neural network baselines, both from the same methodological family, which limits the generality of the claim that the proposed models outperform "recently published" methods. The interpretation of the perturbation results, while interesting, is not fully justified. The species-holdout analysis is described but the results are not visible. The manuscript does not discuss potential limitations of the new data sets, such as biases in UniProt annotations or the choice of GO term for defining DNA-binding.
- **Minor Comments** The abstract is clear and well-structured. The introduction provides good context. The methods section is generally clear but some details are missing, such as the exact hyperparameters for the neural network models and the gradient boosting model. The conclusion is somewhat repetitive of the results. The GitHub link is provided but its contents are not described in detail.
- **Technical failings that need to be addressed before the case is established** The lack of visible figures and tables is the primary technical failing. Without these, the quantitative claims cannot be assessed. The comparative evaluation is also incomplete, as only two neural network baselines are considered. The manuscript should either include a broader set of baselines or temper the claims accordingly.
- **Assessment against Nature-style criteria** Originality: The identification of data set flaws and the proposal of new data sets and evaluation protocols is original and valuable. Scientific importance: The work addresses a fundamental issue in a widely studied problem and has the potential to improve the reliability of future model evaluations. Interdisciplinary readership: The topic is of interest to computational biologists, bioinformaticians, and machine learning researchers, but the presentation is somewhat specialized. Technical soundness: The methods are generally sound, but the lack of visible results prevents full assessment. Readability for nonspecialists: The manuscript is written for a specialist audience and may be challenging for nonspecialists, though the abstract is accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The core contributions, namely the new data sets and the identification of benchmark flaws, are valuable. However, the manuscript cannot be accepted in its current form because the central quantitative results are not visible and the comparative evaluation is limited.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that their new models outperform previously published models across all data sets, and that the nearest neighbor model performs "essentially as well as" the gradient boosting model.
- **Evidence pointer** Figures 1 to 3, Figure 5, Figure 7, location not provided
- **Concern** The manuscript references seven figures and three tables, but none of these are provided in the submitted material. The central quantitative claims of the paper, including the comparative performance of the models and the results of the species-holdout analysis, are entirely dependent on these missing figures. Without them, the claims cannot be verified or evaluated.
- **Why it matters** The primary contribution of the paper is the empirical demonstration that the proposed models and data sets are superior to existing ones. If the figures are not available, the evidence for this claim is absent, and the manuscript cannot be assessed on its merits.
- **Resolution test** Provide all figures and tables with clear captions and axis labels. Ensure that the results described in the text are fully consistent with the data shown.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evaluation
- **Claim pointer** The authors state that the gradient boosting model and the nearest neighbor model "substantially outperform recently published results" and that the neural network baselines are outperformed across all data sets.
- **Evidence pointer** Section 3, Section 4, location not provided
- **Concern** The comparative evaluation includes only two neural network baselines, both from the same lineage (Qu et al. 2017 and Hu et al. 2019). The claim of outperforming "recently published" methods is therefore based on a very narrow comparison. Many other methods for DNA-binding protein prediction have been published, and it is not clear how the proposed models compare to them.
- **Why it matters** The claim of superiority over existing methods is a key part of the paper's contribution. If the comparison is limited to two related baselines, the claim is not well supported and may not generalize.
- **Resolution test** Expand the comparative evaluation to include a broader set of published methods, or clearly state the limitations of the comparison and temper the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of results
- **Claim pointer** The authors interpret the perturbation analysis as showing that the models "learn to focus on DNA-binding regions" and that the gradient boosting model is "more sensitive to large disruptions of a protein's non-binding components."
- **Evidence pointer** Section 4.3, Figure 6, location not provided
- **Concern** The perturbation analysis is a useful diagnostic, but the interpretation is somewhat speculative. The authors do not provide a clear framework for what constitutes a "focus" on a region, and the differences between models could be due to other factors, such as the nature of the features or the model architecture. The claim that the gradient boosting model is "more sensitive" to non-binding region disruptions is not well supported without a more detailed analysis.
- **Why it matters** The interpretation of the perturbation results is used to draw conclusions about what the models have learned. If the interpretation is not well justified, these conclusions are weakened.
- **Resolution test** Provide a more rigorous analysis of the perturbation results, including statistical tests and a clearer definition of what constitutes a meaningful change in prediction. Consider alternative explanations for the observed patterns.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data set limitations
- **Claim pointer** The authors claim that their new data sets are "large, cleaned to ensure data quality, divided into non-overlapping training and test sets."
- **Evidence pointer** Section 2.1, Table 1, location not provided
- **Concern** The manuscript does not discuss potential limitations of the new data sets. For example, the reliance on UniProt annotations, which are often inferred electronically, may introduce biases. The choice of GO term 3677 and its children for defining DNA-binding may also be imperfect. The authors do not address these issues.
- **Why it matters** The quality and representativeness of the data sets are central to the paper's contribution. If the data sets have unacknowledged limitations, the conclusions drawn from them may be less robust.
- **Resolution test** Add a discussion of the potential limitations of the data sets, including the sources of annotation and the potential for bias. Consider providing additional analyses to address these concerns.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Metrics
- **Evidence pointer** Section 2.2, location not provided
- **Issue** The definitions of ROC AUC and AP are referenced but not fully written out. The text says "the definitions of ROC AUC and AP are" and then moves to the next section.
- **Required correction** Provide the full definitions of ROC AUC and AP, or refer to a standard reference.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 3, Algorithms and Implementation
- **Evidence pointer** Section 3, location not provided
- **Issue** The description of the neural network models is brief. The text states that the models from Qu et al. and Hu et al. were used, but does not provide details on how they were implemented, trained, or tuned.
- **Required correction** Provide more details on the implementation of the neural network models, including hyperparameters, training procedures, and any modifications made.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 4, Results and Discussion
- **Evidence pointer** Section 4, location not provided
- **Issue** The text states that "Figures 1 to 3 contain the results on the three tasks from the random train/test split" but does not describe the specific results in the text. The reader is left to interpret the figures without guidance.
- **Required correction** Provide a more detailed description of the results in the text, including specific numbers or trends, to guide the reader through the figures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 5, Conclusion
- **Evidence pointer** Section 5, location not provided
- **Issue** The conclusion states that the paper makes "four main contributions" but only three are clearly enumerated in the text. The fourth contribution is implied but not explicitly stated.
- **Required correction** Clearly enumerate all four contributions in the conclusion.

## Risk / unsupported claims

- The claim that the proposed models "substantially outperform recently published results" is not fully supported due to the limited number of baselines evaluated.
- The claim that the models "learn to focus on DNA-binding regions" is based on an interpretation of the perturbation analysis that is not fully justified.
- The claim that the new data sets are "carefully curated" is not fully supported without a detailed description of the curation process and its validation.
- The quantitative results presented in the text cannot be verified without the figures and tables.
- The claim that the nearest neighbor model's performance is "not entirely explained by the electronic annotation process" is based on a single analysis (Figure 5) that is not visible.