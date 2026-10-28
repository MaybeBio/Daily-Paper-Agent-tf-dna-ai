## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusion. Figures and tables are referenced but not fully visible in the provided material.
- **Assessment boundary** The review assesses the scientific claims, methodological soundness, and presentation quality of the manuscript as submitted. It does not assess the suitability for a specific journal but evaluates against general high-impact standards.
- **Shared manuscript claim summary** The authors present a novel computational method using limited-parameter LSTM and CNN models to predict DNA-binding residues in anti-DNA autoantibodies from primary amino acid sequences alone. They claim that analysis of LSTM hidden states can recover sub-sequences correlated with experimentally known binding sites, offering a tool for rational vaccine design and synthetic biology with minimal data and computational resources.
- **Visible evidence base** The provided material includes the full text of the manuscript, including methods descriptions, results tables (Tables 1 and 2), and figure captions (Figures 1-14). Specific numerical results for binding prediction accuracy and correlation coefficients are reported in the text.
- **Missing materials affecting confidence** The actual figures and tables are not fully visible, limiting the ability to visually inspect the data distributions, PCA plots, activation maps, and sequence alignments. The specific details of the dataset composition, including the exact sequences used and the criteria for manual selection, are not fully described. The code repository is referenced but not reviewed.

## Reviewer
- **Overall assessment** The manuscript addresses an interesting and potentially useful problem: predicting binding residues in anti-DNA autoantibodies from sequence alone using small neural networks. The idea of interpreting hidden states to localize functional regions is timely. However, the study has significant methodological weaknesses and the evidence presented does not fully support the strength of the claims. The dataset is very small, the validation is limited, and the statistical analyses are incomplete or inappropriately applied. The manuscript would benefit from a more rigorous experimental design, clearer reporting of methods, and a more cautious interpretation of the results.
- **Who would be interested in the results, and why** Researchers in computational biology, immunology, and protein engineering would be interested. Specifically, those working on antibody engineering, autoimmune disease mechanisms, and the application of deep learning to biological sequence analysis would find the approach relevant. The promise of a low-resource method for binding site prediction could appeal to labs without extensive computational infrastructure.
- **Major strengths**
    - The problem is relevant and under-served, with few computational studies focusing on anti-DNA autoantibodies.
    - The use of limited-parameter models is a practical consideration for real-world applications.
    - The idea of analyzing internal representations (hidden states) for interpretability is a valuable direction.
    - The authors provide a clear statement of their contribution and make their code available.
- **Major Concerns**
    - **R1-M1**: The dataset is extremely small (81 binding, 81 non-binding after downsampling) and the non-binding set is constructed by a subjective PCA-matching procedure. This raises serious concerns about generalizability and the potential for overfitting. The claim that the model can predict binding for "novel" sequences is not supported by any external validation.
    - **R1-M2**: The statistical analysis is flawed. The use of a one-sample t-test to claim statistical significance for accuracy values is inappropriate, as it does not account for the variance across different data splits or the non-independence of the samples. The correlation coefficients are reported with inconsistent notation (e.g., "r(798) .0627" vs "r(798) = .1870") and the degrees of freedom are not clearly justified.
    - **R1-M3**: The "knockout" and "insertion" tests, while creative, are not convincingly validated. The knockout test shows a high reversal rate, but the interpretation is confounded by the fact that the model may be using other features. The insertion test shows a very low reversal rate, which the authors dismiss, but this actually undermines the claim that the identified sites are necessary and sufficient for binding prediction.
    - **R1-M4**: The comparison between LSTM and CNN is not well-framed. The authors state that CNN outperforms LSTM on prediction, but LSTM is better for site recovery. This is an interesting observation, but the reasons for this difference are not explored, and the practical implications are unclear. The claim that "larger LSTM hidden states allow for a more accurate binding site interpretation" is not directly supported by the data presented.
    - **R1-M5**: The manuscript lacks a clear description of the hyperparameter tuning process. It is unclear how the model architectures (e.g., 300 hidden nodes, 200 epochs) were chosen, and whether the results are sensitive to these choices. This limits the reproducibility of the work.
- **Minor Comments**
    - **R1-m1**: The abstract mentions "limited neural networks" but the term is not formally defined. Clarify what "limited" means in this context (e.g., number of parameters, training data size).
    - **R1-m2**: The introduction could better contextualize the novelty of the approach. The statement "no computational studies have reported successful binding-site prediction from primary sequence alone" is strong and should be supported with a more thorough literature review.
    - **R1-m3**: The methods section for data augmentation is vague. The statement "Augmentation did not significantly increase model performance" is not quantified. Please provide the data.
    - **R1-m4**: The description of the CNN architecture is incomplete. The number of filters, strides, and padding for each convolutional layer are not specified.
    - **R1-m5**: The manuscript uses the term "operator-set thresholds" without explaining who the "operator" is or how these thresholds are set in practice.
    - **R1-m6**: The discussion of the "HVD region" is speculative. The claim that the model is focusing on this region because it is important for binding is not directly tested.
    - **R1-m7**: The conclusion states that the method "will further the rapidly developing field of applied deep learning," which is an overstatement given the limited scope of the study.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria**
    - **Originality**: The idea of using hidden state analysis for binding site prediction is not entirely new, but its application to anti-DNA autoantibodies is a novel contribution. However, the novelty is incremental rather than groundbreaking.
    - **Scientific importance**: The problem is important for understanding autoimmunity and for potential therapeutic applications. However, the current study does not provide a robust enough demonstration to have a significant impact.
    - **Interdisciplinary readership**: The work sits at the intersection of immunology, computational biology, and machine learning. It could appeal to a broad audience, but the technical presentation may be challenging for non-specialists.
    - **Technical soundness**: The technical soundness is currently weak due to the small dataset, inadequate statistical analysis, and lack of external validation. The methods are not described with sufficient detail for replication.
    - **Readability for nonspecialists**: The manuscript is generally readable, but the methods section is dense and assumes familiarity with deep learning concepts. The results section could be clearer with more explicit explanations of the figures.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has a promising idea but requires major revisions and additional experiments to support its claims. The authors need to address the concerns about dataset size, statistical rigor, and validation before the work can be considered for publication.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data and validation
- **Claim pointer** The authors claim the model can predict binding for "novel" sequences and that the method is useful for "rational vaccine design" and "synthetic biology."
- **Evidence pointer** Methods: Dataset section; Results: Tables 1 and 2
- **Concern** The dataset is very small (81 binding, 81 non-binding after downsampling) and the non-binding set is constructed by a subjective PCA-matching procedure. This raises serious concerns about generalizability and the potential for overfitting. The claim that the model can predict binding for "novel" sequences is not supported by any external validation.
- **Why it matters** A model trained on such a small, potentially biased dataset is unlikely to generalize to new, unseen antibodies. The lack of external validation means the reported accuracy and site recovery rates may be optimistically biased.
- **Resolution test** The authors should validate their model on an independent, larger dataset of anti-DNA antibodies with known binding sites. If such a dataset is not available, they should use cross-validation with multiple splits and report the variance. They should also clearly describe the PCA-matching procedure and justify its use.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical analysis
- **Claim pointer** The authors claim statistical significance for their accuracy and correlation results (e.g., "statistically significant at 87.81% by one sample t-test, t(99) = 90.9673, p .0001").
- **Evidence pointer** Results: Binding specificity section, Tables 1 and 2
- **Concern** The use of a one-sample t-test to claim statistical significance for accuracy values is inappropriate, as it does not account for the variance across different data splits or the non-independence of the samples. The correlation coefficients are reported with inconsistent notation (e.g., "r(798) .0627" vs "r(798) = .1870") and the degrees of freedom are not clearly justified.
- **Why it matters** Inappropriate statistical tests can lead to false confidence in the results. The reported p-values are not meaningful if the test is not correctly applied.
- **Resolution test** The authors should use appropriate statistical tests, such as a paired t-test or Wilcoxon signed-rank test, to compare model performance across multiple data splits. They should also clarify the degrees of freedom for their correlation analyses and use a consistent notation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of interpretability
- **Claim pointer** The authors claim that the "knockout" and "insertion" tests validate the identified binding sites.
- **Evidence pointer** Methods: Knockout test, Insertion test, Peak knockout test; Results: Binding-site analysis
- **Concern** The "knockout" and "insertion" tests, while creative, are not convincingly validated. The knockout test shows a high reversal rate, but the interpretation is confounded by the fact that the model may be using other features. The insertion test shows a very low reversal rate, which the authors dismiss, but this actually undermines the claim that the identified sites are necessary and sufficient for binding prediction.
- **Why it matters** The interpretability of the model is a key selling point of the paper. If the knockout and insertion tests do not provide clear evidence that the identified sites are functionally relevant, the main contribution of the work is weakened.
- **Resolution test** The authors should provide a more detailed analysis of the knockout and insertion tests, including the distribution of results across all models. They should also discuss the implications of the low insertion reversal rate and how it affects the interpretation of the identified sites.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model comparison and interpretation
- **Claim pointer** The authors claim that "larger LSTM hidden states allow for a more accurate binding site interpretation" and that CNN is better for prediction.
- **Evidence pointer** Results: Binding-site analysis, Table 3
- **Concern** The comparison between LSTM and CNN is not well-framed. The authors state that CNN outperforms LSTM on prediction, but LSTM is better for site recovery. This is an interesting observation, but the reasons for this difference are not explored, and the practical implications are unclear. The claim that "larger LSTM hidden states allow for a more accurate binding site interpretation" is not directly supported by the data presented.
- **Why it matters** Understanding why different architectures perform differently on prediction vs. interpretability is crucial for guiding future work. Without this analysis, the practical recommendations for when to use which model are unclear.
- **Resolution test** The authors should provide a more detailed analysis of the differences between LSTM and CNN hidden states. They should also discuss the trade-offs between prediction accuracy and interpretability and provide guidance on model selection.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors claim their method is "user friendly for researchers without extensive computational background knowledge and computing resources."
- **Evidence pointer** Methods: Binding prediction, Binding-site analysis
- **Concern** The manuscript lacks a clear description of the hyperparameter tuning process. It is unclear how the model architectures (e.g., 300 hidden nodes, 200 epochs) were chosen, and whether the results are sensitive to these choices. This limits the reproducibility of the work.
- **Why it matters** For a method to be useful to the community, it must be reproducible. Without a clear description of the hyperparameters and the tuning process, other researchers will not be able to apply the method effectively.
- **Resolution test** The authors should provide a detailed description of the hyperparameter search, including the range of values tested and the criteria for selection. They should also provide the code and configuration files in a way that allows others to reproduce the results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The term "limited neural networks" is not defined. It is unclear if this refers to the number of parameters, the amount of training data, or something else.
- **Required correction** Define "limited" in the context of the models used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Literature review
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The statement "no computational studies have reported successful binding-site prediction from primary sequence alone" is strong and should be supported with a more thorough literature review.
- **Required correction** Provide a more comprehensive review of existing methods for binding site prediction, including those that use sequence alone, and clarify the novelty of the current approach.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reporting
- **Affected element** Methods: Data augmentation
- **Evidence pointer** Methods: Data augmentation
- **Issue** The statement "Augmentation did not significantly increase model performance" is not quantified. Please provide the data.
- **Required correction** Report the performance with and without augmentation, including the relevant metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods: CNN prediction
- **Evidence pointer** Methods: CNN prediction
- **Issue** The description of the CNN architecture is incomplete. The number of filters, strides, and padding for each convolutional layer are not specified.
- **Required correction** Provide a complete description of the CNN architecture, including all hyperparameters.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods: Binding-site analysis
- **Evidence pointer** Methods: Binding-site analysis
- **Issue** The term "operator-set thresholds" is used without explanation. It is unclear who the "operator" is or how these thresholds are set in practice.
- **Required correction** Clarify the meaning of "operator-set thresholds" and describe how they are determined.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion: Binding site analysis
- **Evidence pointer** Discussion: Binding site analysis
- **Issue** The discussion of the "HVD region" is speculative. The claim that the model is focusing on this region because it is important for binding is not directly tested.
- **Required correction** Provide evidence to support the claim that the model is focusing on the HVD region, or temper the interpretation.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Overstatement
- **Affected element** Conclusion
- **Evidence pointer** Conclusion
- **Issue** The conclusion states that the method "will further the rapidly developing field of applied deep learning," which is an overstatement given the limited scope of the study.
- **Required correction** Soften the language to reflect the preliminary nature of the findings.

## Risk / unsupported claims
- The claim that the model can predict binding for "novel" sequences is unsupported due to the lack of external validation.
- The claim that the method is "user friendly for researchers without extensive computational background knowledge" is not fully supported, as the methods section is technical and the hyperparameter tuning process is not described.
- The claim that the "knockout" and "insertion" tests validate the identified binding sites is not fully supported, particularly given the low insertion reversal rate.
- The claim that "larger LSTM hidden states allow for a more accurate binding site interpretation" is not directly supported by the data presented.
- The statistical significance of the results is not reliably established due to the inappropriate use of statistical tests.