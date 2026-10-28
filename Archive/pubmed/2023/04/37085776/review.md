## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) for a BMC Bioinformatics article.
- **Assessment boundary** Technical and scientific evaluation of the proposed PSGRN method, its validation, and its claims relative to the state of the art in GRN inference.
- **Shared manuscript claim summary** The authors propose a supervised deep learning framework (PSGRN) based on a pseudo-Siamese network with GRU and DenseNet modules to infer gene regulatory networks from time-series gene expression data. They claim superior performance over existing methods (GENIE3, GRNBoost2, NODE, CNNC, DGRNS) on two maize datasets, as well as robustness to noise and incomplete data.
- **Visible evidence base** Main text including Figures 1-7, Tables 1-3, and references to supplementary material (Additional file 1). No code or full supplementary material was provided for review.
- **Missing materials affecting confidence** Supplementary material (Additional file 1) containing model architecture details and GRU structure; code repository (https://github.com/cirila9/PSGRN) referenced but not accessible in this review; full experimental details such as hyperparameter settings, training epochs, and statistical significance tests.

## Reviewer
- **Overall assessment** The manuscript presents a plausible and potentially useful deep learning architecture for GRN inference, combining GRU and DenseNet in a pseudo-Siamese framework. The motivation is clear and the problem is relevant. However, the evaluation is limited in several important ways: the comparison with state-of-the-art methods is incomplete (missing key baselines like PIDC, SCODE, ARACNe mentioned in the text), the robustness analysis is superficial, and the biological validation is anecdotal. The technical novelty over existing supervised methods like CNNC and DGRNS is incremental rather than fundamental. The claims of "outperforming state-of-the-art" are not fully supported by the evidence presented, particularly given the lack of statistical testing and the narrow evaluation on only two datasets derived from the same source.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, particularly those interested in deep learning approaches for time-series expression data. Researchers studying maize genomics and gene regulation during seed development may also find the application relevant. The method could be of interest to those seeking alternatives to existing supervised GRN inference tools.
- **Major strengths**
  1. The pseudo-Siamese architecture with separate GRU branches for TF and target gene time series is a reasonable design choice that allows asymmetric feature extraction.
  2. The use of both temporal (GRU) and spatial (DenseNet) feature learning is well motivated and addresses limitations of prior methods that treat expression data as static.
  3. The construction of two real maize datasets with different scales (500 vs 1000 top regulatory relationships) provides some evidence of generalizability.
  4. The discussion of why sigmoid is preferred over softmax for GRN inference is thoughtful and biologically motivated.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Evaluation completeness
  - **Claim pointer** "PSGRN outperforms state-of-the-art methods" (Abstract, Results)
  - **Evidence pointer** Figure 4, Table 2
  - **Concern** The comparison with existing methods is incomplete and potentially unfair. The authors state that CNNC and DGRNS "significantly outperform other methods, such as PIDC, SCODE, and ARACNe" but do not include these methods in the comparison. More critically, the comparison omits several widely used and recent GRN inference methods (e.g., GRNBoost2 is included, but methods like SCENIC, LEAP, or deep learning approaches such as DeepSEM or GNN-based methods are absent). The evaluation is also limited to AUPR, without reporting AUROC, F1, precision-recall curves, or other metrics that would provide a more complete picture. No statistical significance testing (e.g., paired tests across multiple runs) is reported.
  - **Why it matters** The central claim of the paper is that PSGRN is superior to existing methods. Without a comprehensive and statistically rigorous comparison, this claim is not established. The omission of key baselines and the lack of significance testing undermine confidence in the reported performance differences.
  - **Resolution test** The authors should include a broader set of baseline methods (at minimum PIDC, SCODE, ARACNe, and ideally more recent deep learning approaches), report multiple evaluation metrics, and perform statistical significance testing (e.g., bootstrap or repeated runs with different seeds) to demonstrate that performance differences are robust.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility / Technical soundness
  - **Claim pointer** "PSGRN is a supervised framework... applied to time-series expression datasets" (Methods)
  - **Evidence pointer** Section "Model training and datasets partition", Figure 2
  - **Concern** Critical implementation details are missing. The manuscript does not specify: (1) the exact architecture of the GRU (number of layers, hidden dimensions beyond the stated 128), (2) the DenseNet configuration (growth rate, number of dense blocks, compression factor), (3) the training procedure (optimizer, learning rate, batch size, number of epochs, early stopping criteria), (4) how the threshold for classification is determined, and (5) how the train/validation/test split is performed (the text says 3:1:1 but does not specify whether this is at the gene-pair level or some other unit). The code repository is mentioned but not accessible for verification.
  - **Why it matters** Reproducibility is a fundamental requirement for computational methods. Without these details, other researchers cannot implement or fairly compare against PSGRN. The lack of architectural and training details also makes it difficult to assess whether the reported performance is due to the proposed architecture or to specific implementation choices.
  - **Resolution test** The authors should provide a complete description of the model architecture and training procedure in the main text or supplementary material, and ensure the code repository is publicly accessible with clear documentation.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance / Biological validation
  - **Claim pointer** "PSGRN can effectively identify genes in the network... suggesting their definite involvement in the maize gene regulatory network" (Section "Network analysis")
  - **Evidence pointer** Figure 7, Section "Network analysis"
  - **Concern** The biological validation is weak. The analysis of the top 15 TFs using STRING is descriptive and does not provide quantitative evidence that the predicted interactions are biologically meaningful. The authors mention that GRMZM2G145041 and GRMZM2G119823 are "presumed" to play roles in DNA methylation and genomic imprinting, but no experimental validation or comparison with known regulatory interactions (beyond the training labels) is provided. The claim that these findings "provide further evidence for the accuracy and applicability of our model" is overstated.
  - **Why it matters** For a GRN inference method, biological validity is a key measure of usefulness. The current analysis does not demonstrate that PSGRN identifies novel, verifiable regulatory interactions beyond what is already known. Without such validation, the practical utility of the method remains unclear.
  - **Resolution test** The authors should provide quantitative biological validation, such as enrichment analysis of predicted targets for known biological processes, comparison with independent ChIP-seq or perturbation data, or experimental validation of a subset of novel predictions.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Robustness
  - **Claim pointer** "PSGRN still lack prior knowledge... Inducing more domain-specific knowledge of PSGRN may help predict the network more accurately" (Discussion)
  - **Evidence pointer** Section "Robustness validation", Table 3
  - **Concern** The robustness analysis is limited. The noise injection method is unusual: it duplicates time series from randomly selected gene pairs and mixes them with other genes' time series. This does not simulate realistic biological or technical noise (e.g., dropout events common in scRNA-seq, batch effects, or measurement errors). The incomplete data analysis uses only 70% subsampling, which is a mild perturbation. No sensitivity analysis is performed on key hyperparameters (e.g., tl=32, hidden dimension 128, network depth).
  - **Why it matters** The authors claim robustness and generalization, but the evidence is insufficient. Real scRNA-seq data are noisy and sparse, and the robustness of the method under realistic conditions is not demonstrated. Sensitivity to hyperparameters is also important for practical use.
  - **Resolution test** The authors should test robustness under more realistic noise models (e.g., adding Gaussian noise, simulating dropout, subsampling time points) and perform a sensitivity analysis on key hyperparameters.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity / Readability
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract, Introduction
  - **Issue** The abstract and introduction contain some vague and overly broad statements, such as "inferring large-scale information from GRNs remains a formidable challenge" and "PSGRN significantly improve inference accuracy, robustness, and generalization ability." These claims are not quantified or contextualized.
  - **Required correction** Provide specific quantitative claims (e.g., "PSGRN achieves an AUPR of 0.655, a 15% improvement over the best baseline") and clarify what "large-scale" means in this context.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness / Clarity
  - **Affected element** Section "Relatedness measurement"
  - **Evidence pointer** Section "Relatedness measurement"
  - **Issue** The justification for using sigmoid over softmax is confusing. The text states that softmax is "only applicable to dichotomous issues," which is incorrect; softmax is typically used for multi-class classification, while sigmoid is used for binary classification. The argument that "it is impossible to prove that two genes are completely unrelated" is not a standard justification for choosing sigmoid over softmax.
  - **Required correction** Clarify the technical reasoning. If the goal is to output a probability of interaction for each pair independently, sigmoid is appropriate. The current explanation is misleading.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Section "Spatial feature learning"
  - **Evidence pointer** Section "Spatial feature learning"
  - **Issue** The description of DenseNet is overly detailed for a general bioinformatics audience and does not clearly explain why DenseNet is specifically suited for this GRN inference task beyond generic benefits like "alleviating gradient vanishing."
  - **Required correction** Briefly explain the key advantage of DenseNet for this specific problem, such as feature reuse for capturing local correlations in the concatenated feature matrix.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Section "Network analysis"
  - **Evidence pointer** Section "Network analysis"
  - **Issue** The threshold for defining positive/negative predictions is set as the 10000th most significant coefficient, but the rationale for this choice is not explained. The resulting confusion matrix (6914 TP, 38108 TN, 3308 FP, 2776 FN) is presented without derived metrics like precision, recall, or F1-score.
  - **Required correction** Justify the threshold choice and report standard classification metrics.
- **Technical failings that need to be addressed before the case is established**
  1. Incomplete baseline comparison (R1-M1)
  2. Insufficient implementation details for reproducibility (R1-M2)
  3. Weak biological validation (R1-M3)
  4. Limited robustness analysis (R1-M4)
- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The combination of GRU and DenseNet in a pseudo-Siamese architecture for GRN inference is somewhat novel, but it builds heavily on existing supervised methods like CNNC and DGRNS. The core idea of using deep learning to classify TF-target pairs is not new.
  - **Scientific importance** Moderate. GRN inference is an important problem, and improved methods are valuable. However, the incremental improvement over existing methods and the limited evaluation on only two datasets from a single organism reduce the potential impact.
  - **Interdisciplinary readership** Limited. The paper is primarily of interest to computational biologists and bioinformaticians. The biological validation is too weak to attract a broader biology audience, and the technical novelty is not sufficient to attract a general machine learning audience.
  - **Technical soundness** Questionable. The evaluation is incomplete, the robustness analysis is superficial, and key implementation details are missing. The claims of superiority are not statistically supported.
  - **Readability for nonspecialists** Acceptable but improvable. The paper is generally well-structured, but some sections (e.g., DenseNet description) are overly technical, while others (e.g., sigmoid vs. softmax justification) are confusing.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant problem and presents a reasonable architecture, but the claims of state-of-the-art performance and robustness are not adequately supported. Major revisions are required to address the concerns above before the case for the method's utility can be made.

## Risk / unsupported claims
- "PSGRN outperforms state-of-the-art methods" - Not fully supported due to incomplete baseline comparison and lack of statistical testing.
- "PSGRN significantly improve inference accuracy, robustness, and generalization ability" - Robustness and generalization claims are based on limited experiments (only two datasets, one noise condition, one subsampling level).
- "PSGRN can effectively identify genes in the network... suggesting their definite involvement in the maize gene regulatory network" - Biological significance is asserted without quantitative validation.
- "The results show the model's robustness and generalization" - Generalization to other organisms or data types is not demonstrated.
- "PSGRN runs slower than other models except for DGRNS but achieves the best results" - The trade-off between runtime and performance is not discussed in terms of practical implications.