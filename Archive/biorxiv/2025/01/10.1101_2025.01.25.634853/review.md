## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and data availability statements.
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and results as presented. No assessment of code functionality or data reproducibility beyond what is described in the text.
- **Shared manuscript claim summary** The authors present Camformer, a residual convolutional neural network that ranked 4th in the Random Promoter DREAM Challenge 2022, trained on 6.7 million random yeast promoter sequences. They report accurate prediction of gene expression (r² = 0.914 ± 0.003, ρ = 0.962 ± 0.002), systematic exploration of 270 model variants to identify factors contributing to performance, and use of explainable AI (Grad-CAM and in silico mutagenesis) to uncover cis-regulatory logic, including a specific interaction between IME1 and UME6 motifs.
- **Visible evidence base** Abstract, main text sections 1-5, figure references (Figures 1-8, S2-S13), and data/code availability statements. No supplementary methods or figures were provided for direct inspection.
- **Missing materials affecting confidence** Supplementary Methods (Sections 1.1.1, 1.2, 1.2.1, 1.3), all supplementary figures (S2-S13), and the full grid search results. These are referenced extensively and are essential for evaluating methodological details and result robustness.

## Reviewer
- **Overall assessment** This manuscript presents a competent and thorough analysis of a competitive deep learning model for promoter-to-expression prediction in yeast. The work is technically sound in its core claims, and the systematic grid search over 270 model variants is a valuable contribution. The use of explainable AI to derive biological insights, particularly the IME1-UME6 interaction, is a strength. However, the manuscript's reliance on supplementary materials for critical methodological details and the limited novelty of the biological findings temper the overall impact. The claims regarding state-of-the-art performance and biological discovery are largely supported by the provided evidence, but several technical and presentational issues need to be addressed.
- **Who would be interested in the results, and why** Researchers in computational genomics, regulatory genomics, and deep learning applied to biology. The work is directly relevant to those developing predictive models for gene regulation and those using interpretability methods to extract biological knowledge from such models. The systematic comparison of model design choices will be of practical interest to practitioners in the field.
- **Major strengths** 1) The use of a large-scale GPRA dataset (6.7 million promoters) for training and evaluation is a significant strength, enabling robust model assessment. 2) The systematic grid search over 270 model variants is a rigorous approach to understanding the factors that contribute to model performance, going beyond a single model presentation. 3) The application of two complementary interpretability methods (Grad-CAM and ISM) to derive cis-regulatory insights, including a specific and testable interaction between IME1 and UME6, demonstrates the utility of the model for biological discovery. 4) The baseline-normalised improvement metric provides a fairer comparison against prior work than raw performance differences.
- **Major Concerns** The following concerns are detailed below.
- **Minor Comments** The following comments are detailed below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (supplementary material dependency), R1-M2 (baseline comparison clarity), R1-M3 (biological validation).
- **Assessment against Nature-style criteria** **Originality:** Moderate. The application of a residual CNN to this specific dataset is not entirely novel, but the systematic analysis of model design and the focus on interpretability for biological discovery provide a degree of originality. **Scientific importance:** Moderate to high. The work addresses a fundamental question in regulatory genomics and provides a robust predictive model. The biological insights, while interesting, are limited in scope and require further validation. **Interdisciplinary readership:** Moderate. The work will appeal to computational biologists and machine learning researchers, but the biological findings may not be of sufficient breadth to attract a wider audience. **Technical soundness:** Generally sound, but the heavy reliance on supplementary materials for critical details prevents full assessment. The evaluation methodology is appropriate, and the use of multiple metrics is commendable. **Readability for nonspecialists:** The abstract and introduction are accessible, but the methods and results sections assume significant familiarity with deep learning and genomics. The manuscript is not written for a general scientific audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core claims appear well-supported, but the manuscript's dependence on supplementary materials and the need for clearer baseline comparisons and biological validation must be addressed before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness and reproducibility
- **Claim pointer** The manuscript claims a systematic grid search over 270 model variants and describes the model architecture and training procedures.
- **Evidence pointer** Sections 3.1, 3.2, and references to Supplementary Methods 1.1.1, 1.2, and 1.2.1.
- **Concern** The manuscript relies heavily on supplementary materials for essential methodological details, including the full description of the grid search, the architecture of Camformer-Small and Camformer-Mini, and the specifics of the Grad-CAM and ISM implementations. These materials were not provided for review, making it impossible to fully assess the validity and reproducibility of the methods.
- **Why it matters** The core claims of the paper, including the systematic comparison of model variants and the interpretability analysis, depend on these methodological details. Without them, the technical soundness of the work cannot be fully verified, and the reproducibility of the results is in question.
- **Resolution test** The authors must provide the supplementary methods and figures for review. The grid search methodology, model architectures, and interpretability procedures must be described in sufficient detail to be independently reproduced.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance and clarity of claims
- **Claim pointer** The manuscript claims that Camformer provides a "substantial improvement" over previous state of the art, specifically the benchmark model by Vaishnav et al. (2022).
- **Evidence pointer** Section 4.1, Figures 3, 4, S5, S6.
- **Concern** The comparison to the benchmark model is presented using a "baseline-normalised improvement" metric, but the raw performance differences and the statistical significance of these differences across all categories are not fully reported. The claim of "substantial improvement" is not consistently quantified, and the comparison to other top-performing models like LegNet is only briefly mentioned.
- **Why it matters** A clear and quantitative demonstration of improvement over existing methods is essential to establish the scientific importance of the model. The current presentation makes it difficult to assess the magnitude and significance of the claimed improvements.
- **Resolution test** The authors should provide a table or figure showing raw r² and ρ values for Camformer, the benchmark model, and other relevant models across all test categories, along with confidence intervals or statistical tests for the differences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance and biological validity
- **Claim pointer** The manuscript claims that the model captures cis-regulatory logic, specifically an interaction between IME1 and UME6 motifs, and that this can be used to study gene regulation.
- **Evidence pointer** Section 4.4, Figures 8e-h.
- **Concern** The biological findings, while interesting, are based solely on in silico analysis. The claim that the model captures a "switch" involving IME1 and UME6 is supported by model predictions and motif analysis, but there is no experimental validation of this interaction. The novelty of this finding is also not fully contextualised against existing knowledge of IME1 and UME6 biology.
- **Why it matters** The biological insights are a key part of the paper's contribution. Without experimental validation or a clear demonstration of novelty, the significance of these findings is limited.
- **Resolution test** The authors should either provide experimental validation of the IME1-UME6 interaction or clearly state that the findings are predictive and require experimental follow-up. They should also discuss the novelty of this interaction in the context of existing literature.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Section 1
- **Issue** The abstract and introduction use technical terms such as "residual convolutional neural network," "Grad-CAM," and "in silico mutagenesis" without sufficient explanation for a general scientific audience.
- **Required correction** Briefly define these terms in the abstract or introduction to improve accessibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.1
- **Evidence pointer** Section 4.1, Figure 3
- **Issue** The manuscript reports that "more than half" of the 10 retrained models exceeded the previously reported performance. This is a vague statement. The exact number and the range of performance across the 10 models should be reported.
- **Required correction** Report the exact number of models that exceeded the previous performance and provide the mean and standard deviation or range for r² and ρ across the 10 retrained models.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.3
- **Evidence pointer** Section 4.3, Figure S13
- **Issue** The manuscript states that there is "high concordance between ISM and Grad-CAM motifs" but does not provide a quantitative measure of this concordance.
- **Required correction** Provide a quantitative metric, such as the fraction of overlapping motifs or a correlation coefficient, to support this claim.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity of claims
- **Affected element** Section 4.4
- **Evidence pointer** Section 4.4, Figure 8d
- **Issue** The correlation between motif score and expression is described as "high" for ABF1 and "low" for UME6, but the actual correlation coefficients are not reported.
- **Required correction** Report the correlation coefficients and their significance for the examples mentioned.

## Risk / unsupported claims
- The claim that the model captures a "switch" involving IME1 and UME6 is based solely on in silico analysis and is not experimentally validated. This is a predictive finding that requires experimental follow-up.
- The claim of "substantial improvement" over previous state of the art is not fully quantified with raw performance values and statistical tests across all categories.
- The statement that "none of the 270 model variants outperformed the original model" is made without presenting the full results of the grid search, which are relegated to supplementary materials and a GitHub repository. This claim is not fully verifiable from the provided text.
- The generalisation of the model's performance to other yeast growth conditions (complex and defined media) is based on re-training and evaluation, but the comparison to other models on these datasets is not fully detailed.