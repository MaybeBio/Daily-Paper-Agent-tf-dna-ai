## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, results, discussion, and supplementary figure/table references.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality. No assessment of code or data availability beyond stated URLs.
- **Shared manuscript claim summary** The authors train a supervised XGBoost model on CRISPRi enhancer perturbation data from Gasperini et al. (2019), integrating TF ChIP-seq and histone modification data, to predict functional enhancer-promoter (EP) pairs. They report improved performance over the Activity-by-Contact (ABC) model on genome-wide data, identify novel predictive features (e.g., enhancer/promoter density, relative contact strength), and highlight discrepancies between genome-wide and targeted experimental datasets. They also characterize atypical enhancers that function without strong direct contact.
- **Visible evidence base** Main text figures (Fig. 1–7), tables (Table 1–2), and references to supplementary materials (Supplementary Figs S1–S14, Tables S1–S10). No raw data or code were inspected.
- **Missing materials affecting confidence** Supplementary figures and tables were not provided for inspection. The Zenodo and GitHub links were not accessed. This limits verification of feature engineering details, full SHAP results, and hyperparameter settings.

## Reviewer
- **Overall assessment** This manuscript presents a useful and timely application of supervised machine learning to a large CRISPRi perturbation dataset, with the goal of learning enhancer-promoter specificity. The work is generally well-structured and the authors are appropriately cautious about the limitations of their approach. The main strengths are the integration of diverse genomic features and the careful analysis of why performance differs between genome-wide and targeted datasets. However, several technical and interpretational issues need to be addressed before the core claims are fully established. In particular, the handling of class imbalance, the potential for data leakage in feature construction, and the interpretation of SHAP values for correlated features require more rigorous treatment. The claim that the model "learns" biological principles, as opposed to experimental artifacts, needs stronger support.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and gene regulation. The work is relevant to those developing predictive models for enhancer-promoter interactions, those interpreting large-scale perturbation screens, and those interested in the limitations of current machine learning approaches in genomics. The findings on the importance of relative contact strength and the role of genomic density will be of interest to the broader chromatin biology community.
- **Major strengths**
  - Use of a large, genome-wide CRISPRi dataset, which is more comprehensive than many previous training sets.
  - Integration of multiple feature types (histone marks, TF binding, Hi-C, genomic context) in a single model.
  - Clear demonstration that performance varies substantially between genome-wide and targeted datasets, with a thoughtful discussion of why.
  - Identification of specific TF clusters and chromatin features that contribute to prediction, providing potential biological hypotheses.
  - The analysis of atypical enhancers with weak direct contact is a novel and interesting contribution.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the supervised model outperforms the ABC model on genome-wide data (Section 3.1, Fig. 1a–b).
- **Evidence pointer** Section 3.1, Fig. 1a–b, Table 1a–c
- **Concern** The comparison between the XGB model and the ABC model may be biased. The ABC model is an unsupervised ranking method, not a classifier trained on the same data. The authors state that the comparison is "expected" to be biased because ABC components are used as features (Discussion). However, the magnitude of this bias is not quantified. A fairer comparison would involve retraining ABC with a threshold optimized on the training set, or comparing against a logistic regression model using only ABC features. Without this, the claim of "improved performance" is not rigorously established.
- **Why it matters** The central claim of the manuscript is that integrating additional features improves prediction. If the baseline is not fairly calibrated, the improvement may be overstated, undermining the main conclusion.
- **Resolution test** Provide a comparison against a baseline model trained only on ABC score and distance, with the same cross-validation scheme and threshold selection. Report the difference in average precision and discuss whether the improvement is statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the density of the enhancers and promoters within the chromatin landscape is a factor modulating the detection of functional EPs" (Section 3.6).
- **Evidence pointer** Section 3.6, Fig. 5
- **Concern** The interpretation that density affects detection is confounded by the experimental design. In Gasperini et al. (2019), enhancers were selected based on certain features (e.g., presence of DHS, H3K27ac), and the number of candidate enhancers per gene varies. The observed relationship between density and false negatives could be an artifact of the selection criteria or the statistical power of the CRISPRi screen in dense regions, rather than a biological property of enhancer function. The authors acknowledge this possibility but do not provide a formal test to distinguish between these explanations.
- **Why it matters** The claim that density is a "factor modulating detection" is a key finding. If it is an artifact, the biological interpretation is incorrect.
- **Resolution test** Perform a permutation test where the density labels are shuffled, or stratify the analysis by the number of enhancers tested per gene. Alternatively, use a mixed-effects model with gene as a random effect to control for gene-level variability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "several TF peaks were identified that improved the prediction by identifying the negatives and reducing False Positives" (Abstract, Section 3.4).
- **Evidence pointer** Section 3.4, Fig. 3b, Fig. 4
- **Concern** The identification of TFs such as EMSY and HCFC1 as markers of "insensitive" genes is based on SHAP values. However, SHAP values for correlated features can be unreliable, and the authors note that they used NMF to address this. The specific claim that these TFs are causally involved in making genes insensitive to enhancers is not supported by the data, which is correlational. The authors do discuss this, but the language in the abstract and results could be interpreted as stronger than warranted.
- **Why it matters** Overinterpretation of correlational findings can mislead readers and future research directions.
- **Resolution test** Soften the language to clearly state that these are predictive features, not necessarily causal. Consider a validation experiment, such as knockdown of HCFC1 or EMSY followed by perturbation, to test causality, or explicitly state that such experiments are needed.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the overall MAP from the inner fold validations were around 0.27–0.31, and the outer fold average precision on the test folds ranged from 0.22 to 0.32" (Section 3.1).
- **Evidence pointer** Section 3.1, Table 1a
- **Concern** The average precision values are low in absolute terms, and the range across folds is wide. The authors do not report confidence intervals or statistical significance of the difference between models. Given the extreme class imbalance (positive rate <2%), a trivial classifier that predicts all negatives would achieve an average precision equal to the positive rate, which is approximately 0.018. The reported values are higher, but the improvement over a random baseline is not quantified.
- **Why it matters** Without a baseline comparison, the reader cannot assess whether the model is actually learning meaningful patterns or just exploiting the class imbalance.
- **Resolution test** Report the average precision of a dummy classifier (e.g., predicting the majority class) and a random classifier. Provide confidence intervals for the reported metrics, and test whether the difference between the full model and the reduced model is statistically significant using a paired test across folds.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The authors claim that "the results uncovered a discrepancy in the prediction of genome-wide data compared to data from targeted experiments" (Abstract).
- **Evidence pointer** Abstract, Section 3.1, Fig. 1e–h
- **Concern** The discrepancy is described, but the underlying reasons are not fully explored. The authors suggest differences in experimental design and positive rates, but do not provide a quantitative analysis of how these factors contribute. For example, a direct comparison of feature distributions between the two datasets could be informative.
- **Why it matters** Understanding the source of the discrepancy is important for interpreting the model's generalizability and for guiding future experimental designs.
- **Resolution test** Provide a detailed comparison of the feature distributions (e.g., Hi-C contact, H3K27ac, expression) between the Gasperini2019 and Fulco2019/Schraivel2020 datasets. Discuss how these differences might affect model performance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract uses terms like "EP relationships" and "perturbation studies" without defining them. A brief definition of enhancer-promoter interactions and the perturbation approach would improve accessibility.
- **Required correction** Add a brief explanation of what enhancer-promoter interactions are and what a perturbation study entails.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Section 2.2
- **Evidence pointer** Section 2.2
- **Issue** The threshold for calling a positive is "adjusted P-value < .1". This is a relatively lenient threshold, and the authors do not discuss the potential impact of this choice on the model's training and evaluation.
- **Required correction** Justify the choice of threshold or discuss its potential impact on the results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Section 2.3
- **Evidence pointer** Section 2.3
- **Issue** The authors state that they explored other algorithms but do not report the results. This is acceptable, but a brief mention of which algorithms were tried and why they were not used would be helpful.
- **Required correction** Add a sentence listing the other algorithms considered and the reason for choosing XGBoost.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, Section 3.4
- **Evidence pointer** Section 3.4
- **Issue** The discussion of NMF clusters (e.g., NMF1_TSS) is difficult to follow without a clear explanation of what NMF is and how the clusters are defined.
- **Required correction** Provide a brief explanation of NMF and how the clusters are derived, or refer the reader to the supplementary methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the "atypical enhancers" is interesting but speculative. The authors suggest a role for "trans-acting regulation" and "redundancy" but do not provide direct evidence.
- **Required correction** Clearly label these as hypotheses and suggest specific experiments to test them.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The feature "relative strength of the chromatin contact compared to other enhancers or other TSS nearby" is not clearly defined. It is unclear how this is calculated.
- **Required correction** Provide a precise definition of this feature, including the formula or algorithm used.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, Section 3.1
- **Evidence pointer** Section 3.1
- **Issue** The term "recall = 0.7" is used without explanation. Nonspecialist readers may not be familiar with this metric.
- **Required correction** Briefly define recall and explain why this value was chosen.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The definition of the Chromatin Interaction Network (ChIN) and the labels e0, e1, e2, e3, einf is clear, but the choice of distance thresholds is not justified.
- **Required correction** Explain why these specific distance categories were chosen and how they relate to biological concepts of enhancer-promoter communication.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Results, Section 3.5
- **Evidence pointer** Section 3.5
- **Issue** The list of TFs that predict positive EP pairs is presented, but the biological significance of these TFs is not discussed in detail. For example, the authors mention GATA1 and GATA2, which are known hematopoietic factors, but do not elaborate on why this is expected or interesting.
- **Required correction** Add a brief discussion of the biological relevance of the identified TFs.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, Section 3.7
- **Evidence pointer** Section 3.7
- **Issue** The authors state that "the pattern is replicated in the whole data" but do not show the corresponding figure or table.
- **Required correction** Reference the specific supplementary figure or table that supports this statement.

## Risk / unsupported claims
- The claim that the model "learns" biological principles of enhancer-promoter specificity is not fully supported. The model may be learning experimental artifacts or statistical properties of the dataset.
- The claim that "the density of the enhancers and promoters within the chromatin landscape is a factor modulating the detection of functional EPs" is confounded by experimental design and requires further analysis.
- The claim that "several TF peaks were identified that improved the prediction by identifying the negatives and reducing False Positives" is based on correlational SHAP analysis and should not be interpreted as causal.
- The comparison with the ABC model is potentially biased and needs to be re-evaluated with a fairer baseline.
- The generalizability of the model to other cell types is not demonstrated, and the authors acknowledge this limitation.