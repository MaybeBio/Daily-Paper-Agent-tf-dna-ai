## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and significance of the proposed CELLetter framework for ligand-receptor interaction prediction and cell-cell communication inference
- **Shared manuscript claim summary** The authors present CELLetter, a deep learning framework that uses the ProstT5 protein language model for feature embedding, a dual-stream architecture (MLP with residual connections and a CNN-based Mixture-of-Experts module) for feature extraction, a gating mechanism for feature fusion, and absolute difference/element-wise product operations for feature interaction, to predict ligand-receptor interactions and quantify cell-cell communication by integrating L-R co-expression with downstream transcription factor activity
- **Visible evidence base** Text descriptions of model architecture, equations (1)-(19), dataset descriptions (four L-R datasets, two spatial transcriptomics datasets, one scRNA-seq dataset), performance comparisons against four L-R classification baselines and ten CCC inference baselines, ablation study results, and spatial validation metrics
- **Missing materials affecting confidence** All figures and tables (including numerical results), supplementary materials, code implementation details, hyperparameter settings, training procedures, and detailed statistical test descriptions

## Reviewer

- **Overall assessment** The manuscript presents a technically sophisticated approach to a relevant problem in cell-cell communication inference. The combination of a protein language model with a dual-stream architecture and downstream TF activity integration is conceptually interesting. However, the current text lacks sufficient quantitative detail to fully evaluate the claimed performance improvements. The validation strategy, while comprehensive in scope, requires closer examination of the actual numerical results and statistical rigor. The biological application to HNSCC provides a useful case study but needs stronger evidence for the novelty of the MIF-CD44 finding beyond what is already established in the literature.

- **Who would be interested in the results, and why** Computational biologists developing methods for cell-cell communication inference from single-cell and spatial transcriptomics data would be the primary audience. Researchers studying tumor microenvironments, particularly those interested in ligand-receptor interactions in HNSCC, would find the application relevant. The methodological components (protein language model embeddings, MoE architectures, gating mechanisms) may also interest researchers in deep learning applications to biological sequence analysis.

- **Major strengths**
  1. The integration of a protein language model (ProstT5) for L-R feature representation is a modern and potentially powerful approach that leverages recent advances in protein representation learning
  2. The dual-stream architecture with separate global and local feature processing is well-motivated and addresses complementary aspects of protein function
  3. The incorporation of downstream TF activity into CCC scoring represents a meaningful advance over purely co-expression-based methods
  4. The validation strategy is multi-faceted, including classification benchmarks, spatial transcriptomics validation, and a real biological application
  5. The manuscript is generally well-written and the methodological logic is clearly presented

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "CELLetter demonstrated superior L-R classification performance" and "CELLetter attained the highest precision, recall, accuracy, and F1 score on every dataset"
- **Evidence pointer** Figures 4-6, location not provided
- **Concern** The manuscript claims superior performance across all metrics and datasets but provides no numerical values in the text. The reader cannot assess the magnitude of improvement, statistical significance, or practical relevance of the performance gains. Without actual numbers, confidence intervals, or statistical tests, the central claim of superiority cannot be evaluated.
- **Why it matters** The primary contribution of this work is the claimed performance improvement of the proposed method. Without quantitative evidence, the scientific case for CELLetter over existing methods is not established.
- **Resolution test** Provide numerical results for all metrics across all datasets, including standard deviations or confidence intervals, and appropriate statistical significance tests (e.g., paired tests across cross-validation folds).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The model is described as trainable end-to-end with a cross-entropy loss, but implementation details are incomplete
- **Evidence pointer** Section "Experimental settings", location not provided
- **Concern** The manuscript lacks critical implementation details: training/validation/test split procedures, hyperparameter values (learning rate, batch size, number of epochs, early stopping criteria), optimization algorithm, regularization strategies, and computational resource requirements. The ProstT5 embedding procedure (sequence length handling, truncation, padding) is not specified. The MoE module configuration (number of experts, expert capacity, routing mechanism) is described only at a high level.
- **Why it matters** Reproducibility is a fundamental requirement for computational methods. Without these details, other researchers cannot implement or fairly compare against CELLetter.
- **Resolution test** Provide complete implementation details, either in the main text or supplementary materials, sufficient for independent reimplementation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** "CELLetter's predicted L-R pairs exhibited significant spatial relevance compared with other baselines" and the spatial validation using three metrics
- **Evidence pointer** Section "Ligand-receptor validation", Figures 9, location not provided
- **Concern** The spatial validation methodology requires clarification. The manuscript states five random sampling rounds of 100 interactions were performed, but does not specify: (1) how the 100 interactions were sampled, (2) whether the same interactions were evaluated across all methods, (3) what statistical tests were used to compare methods, (4) how the expression threshold (20th percentile) was determined, and (5) whether results were consistent across sampling rounds. The claim of "significant" spatial relevance needs explicit statistical support.
- **Why it matters** The spatial validation is a key differentiator of this work, claiming biological plausibility beyond computational benchmarks. Without rigorous statistical methodology, these claims are not verifiable.
- **Resolution test** Describe the complete sampling and statistical testing procedure, report results for all sampling rounds, and provide effect sizes with confidence intervals.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological novelty
- **Claim pointer** "ligand macrophage migration inhibitory factor (MIF) and receptor CD44 were predicted as a central signaling axis within HNSCC tumor microenvironment, suggesting their potentials as therapeutic targets"
- **Evidence pointer** Section "Top 3 ligand-receptor pair analysis", Tables 6-7, Figure 11, location not provided
- **Concern** The MIF-CD44 axis in HNSCC is already well-documented in the literature. The manuscript cites references [80, 81, 90] supporting this, but does not clearly articulate what new biological insight CELLetter provides beyond confirming known interactions. The molecular docking validation (Table 7) shows all 20 predicted interactions have binding energies below -6 kcal/mol, but no comparison is made to docking results for known non-interacting pairs or to the performance of other prediction methods on the same docking task.
- **Why it matters** The biological application is presented as a demonstration of the method's utility. If it only confirms known biology without generating testable new hypotheses, the added value over existing methods is diminished.
- **Resolution test** Clearly articulate novel predictions made by CELLetter that are not in existing databases, and provide validation for at least one novel prediction beyond computational docking.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparative fairness
- **Claim pointer** "benchmarking it against 4 state-of-the-art L-R classification models, 6 L-R validation tools, 10 CCC inference methods"
- **Evidence pointer** Sections "Performance comparison" and "Comparison of CELLetter and 10 baselines", location not provided
- **Concern** The manuscript does not describe how baseline methods were configured. Were they used with default parameters? Were they retrained on the same data? For CCC inference baselines, the comparison appears to be based on ranking agreement rather than direct performance metrics, but this is not clearly explained. The choice of baselines and the fairness of comparison cannot be assessed.
- **Why it matters** Unfair or unclear baseline comparisons undermine the validity of claimed improvements.
- **Resolution test** Describe baseline configurations, parameter tuning procedures, and the exact comparison protocol for each baseline category.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states "11 evaluation metrics" but the main text describes six classification metrics plus three spatial metrics. The discrepancy is confusing.
- **Required correction** Clarify the total count of evaluation metrics and list them explicitly in the abstract or main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Equation (12)
- **Evidence pointer** Section "Transcription factor activity computation", location not provided
- **Issue** The global TF activity score is described as aggregating "logarithmic AUCell values across all TFs and all cells," but the equation itself is not shown in the text provided. The relationship between this global score and the per-cell AUCell values needs clearer mathematical exposition.
- **Required correction** Present the full equation and explain the biological rationale for aggregating across all TFs rather than focusing on pathway-specific TFs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Ablation study
- **Evidence pointer** Table 3, location not provided
- **Issue** The ablation results are described with percentage ranges (e.g., "decreased by 0.2%-8.0%") but no statistical significance testing is mentioned. It is unclear whether these differences are meaningful given the variance across cross-validation folds.
- **Required correction** Report standard deviations and perform appropriate statistical tests for ablation comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Section "Discussion", location not provided
- **Issue** The discussion does not address potential limitations of the approach, such as the reliance on known protein sequences, the handling of isoforms, or the computational cost of ProstT5 embeddings for large-scale screens.
- **Required correction** Add a limitations paragraph addressing these and other relevant constraints.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Section "Data availability", location not provided
- **Issue** The statement that data are from public domains is insufficient. Specific accession numbers for all datasets used in training and evaluation should be listed.
- **Required correction** Provide complete accession numbers and versions for all datasets.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 10 description
- **Evidence pointer** Section "Cell-to-cell communication inference results", location not provided
- **Issue** The description of Figure 10D is confusing: "the width of the outer ribbon to represent the total outgoing signal strength per cell population, and the thickness of the inner chords to represent the strength of individual communication events." This conflates two different visual encodings.
- **Required correction** Clarify the visual encoding scheme and ensure the description matches the actual figure.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Reference to Peng et al. [34]
- **Evidence pointer** Section "Data", location not provided
- **Issue** The manuscript states datasets were "compiled by Peng et al. [34]" but does not describe how these datasets were originally constructed, what positive and negative examples were used, or how class balance was handled.
- **Required correction** Provide a brief description of dataset construction and class balance in the main text.

## Risk / unsupported claims

1. "CELLetter demonstrated superior L-R classification performance" - unsupported without numerical results
2. "CELLetter's predicted L-R pairs exhibited significant spatial relevance" - unsupported without statistical test results
3. "MIF and CD44 were predicted as a central signaling axis" - the novelty of this finding is questionable given existing literature
4. "CELLetter provides a more comprehensive assessment of cellular communication potentials" - comparative claim not substantiated with quantitative evidence
5. The claim that the model "can effectively capture both short- and long-range dependencies" is asserted but not directly validated
6. The statement that the 99.99% probability threshold "minimizes error" is not supported by sensitivity analysis
7. The molecular docking results are presented as validation but no comparison to negative controls or alternative methods is provided
8. The claim that CELLetter "precisely decoded downstream cellular signaling events" is not directly validated against known signaling pathway activities