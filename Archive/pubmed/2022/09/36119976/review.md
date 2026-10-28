## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, web application, conclusions)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose two machine learning frameworks: (1) a PSSM-based deep CNN for identifying transcription factors (TFs) and (2) a reduced g-gap dipeptide composition (RGDC) with SVM for identifying TFs that prefer binding to methylated DNA (TFPMs). They report superior performance over prior methods on the same benchmark datasets.
- **Visible evidence base** Tables 1, 3, 4; Figures 1–6; equations 1–5; text descriptions of methods and results
- **Missing materials affecting confidence** Full dataset details, hyperparameter grids, code implementation, cross-validation fold compositions, statistical significance tests, and raw performance metrics per fold are not fully provided

## Reviewer
- **Overall assessment** The manuscript addresses a relevant biological problem with practical implications, and the proposed methods show promising performance gains over existing baselines. However, several methodological details are insufficiently described, and the evidence for the claimed superiority is not fully established due to missing statistical analyses and incomplete reporting of experimental setups. The work is potentially publishable after substantial revisions.
- **Who would be interested in the results, and why** Researchers in computational biology, bioinformatics, and epigenetics, particularly those working on transcription factor binding prediction, DNA methylation, and machine learning applications in genomics. The web server provides a practical tool for the community.
- **Major strengths** (1) The problem is biologically meaningful and timely. (2) The use of PSSM with CNN for TF classification is a reasonable extension of existing approaches. (3) The RGDC method is a novel combination of established techniques. (4) The authors compare against prior work on the same datasets, which facilitates direct benchmarking. (5) A user-friendly web server is provided.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - *Originality*: Moderate. The combination of PSSM/CNN and RGDC/SVM is somewhat novel, but each component is well-established. The conceptual advance is limited.  
  - *Scientific importance*: Moderate. The problem is relevant, but the incremental performance gains over existing methods may not constitute a major breakthrough.  
  - *Interdisciplinary readership*: Limited. The manuscript is primarily of interest to computational biologists; the biological insights are not deeply explored.  
  - *Technical soundness*: Weak to moderate. Several methodological details are missing, and the statistical robustness of the results is not demonstrated.  
  - *Readability for nonspecialists*: Moderate. The text is generally clear, but some sections assume familiarity with machine learning and bioinformatics terminology.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The authors claim that their methods achieve superior performance compared to prior studies (Table 4).  
- **Evidence pointer** Section "Results and Discussion", Table 4  
- **Concern** The manuscript does not provide sufficient details to reproduce the experiments. Specifically, the exact hyperparameter grids for SVM (γ and C), the CNN architecture parameters (e.g., number of epochs, batch size, learning rate schedule), and the data preprocessing steps (e.g., how PSSMs are generated, how sequences are truncated or padded) are not fully described. Additionally, the code is only referenced via a GitHub link, but no version or usage instructions are provided.  
- **Why it matters** Without full methodological transparency, the reported results cannot be independently verified, which undermines the credibility of the performance claims.  
- **Resolution test** Provide a complete description of all hyperparameters, data preprocessing steps, and training procedures. Include a detailed README for the code repository and, if possible, a Docker container or environment file to ensure reproducibility.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical validity  
- **Claim pointer** The authors state that their methods outperform those of Liu et al. and Li et al. on both classification problems.  
- **Evidence pointer** Section "Results and Discussion", Table 4  
- **Concern** The performance comparison is based on single-point estimates of metrics (e.g., accuracy, sensitivity, specificity, AUC) without any measure of variance or statistical significance testing. It is unclear whether the observed differences are statistically meaningful or could arise from random variation, especially given the small test set sizes (e.g., 106 positive and 106 negative for TF classification; 69 positive and 37 negative for TFPM classification).  
- **Why it matters** Claims of superiority require statistical support. Without confidence intervals or hypothesis tests, the reported improvements may be overstated.  
- **Resolution test** Report performance metrics with confidence intervals (e.g., bootstrap) or perform statistical significance tests (e.g., McNemar's test for paired comparisons) to demonstrate that the differences are unlikely to be due to chance.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological justification  
- **Claim pointer** The authors propose RGDC as an effective encoding scheme for TFPM classification, suggesting that the relationship between amino acid pairs separated by gaps may be related to DNA binding ability.  
- **Evidence pointer** Section "Reduced G-Gap DC", Section "Results and Discussion"  
- **Concern** The choice of the optimal grouping scheme (Op(8)) and gap size (3-gap) is based solely on cross-validation performance. However, the manuscript does not provide a biological rationale for why these specific parameters should be optimal, nor does it explore whether the results are sensitive to these choices. Additionally, the claim that RGDC captures information relevant to DNA binding is speculative and not supported by any mechanistic analysis.  
- **Why it matters** Without a clear justification or sensitivity analysis, the method may appear as a black-box optimization that could overfit the training data.  
- **Resolution test** Provide a sensitivity analysis showing how performance varies across different grouping schemes and gap sizes. Discuss potential biological interpretations of the optimal parameters, or temper the claims about biological relevance.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Data and benchmark integrity  
- **Claim pointer** The authors use the dataset from Liu et al. for training and testing.  
- **Evidence pointer** Section "Benchmark Dataset", Table 1  
- **Concern** The manuscript does not describe how the dataset was obtained, whether any preprocessing was applied (e.g., sequence redundancy reduction, filtering), or whether the training and test sets are truly independent. Additionally, the class imbalance in the TFPM dataset (270 positive vs. 146 negative in training; 69 positive vs. 37 negative in test) is not addressed in the modeling approach, which could bias the results.  
- **Why it matters** Dataset quality and balance directly affect model performance and generalizability. Without clarity on these points, the reported results may not be reliable.  
- **Resolution test** Describe the dataset acquisition and any preprocessing steps. Justify the choice of not addressing class imbalance, or apply appropriate techniques (e.g., class weights, oversampling) and report their impact.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Equation 1  
- **Evidence pointer** Section "Reduced G-Gap DC"  
- **Issue** The equation for calculating x_i^g is not fully defined. The notation for the summation index and the meaning of "N^2 g-gap dipeptide" is unclear.  
- **Required correction** Provide a clear definition of all variables in the equation, including the range of the summation and the exact meaning of "N^2 g-gap dipeptide."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Presentation  
- **Affected element** Figure 6  
- **Evidence pointer** Section "Results and Discussion"  
- **Issue** The figure is described as showing the best validation AUC for each combination of Op(.) and g-gap, but the exact values and the range of the color scale are not specified in the text.  
- **Required correction** Add a clear description of the figure, including the color scale, axis labels, and the specific values for the best-performing combination.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Web-based application  
- **Evidence pointer** Section "Web-Based Application"  
- **Issue** The manuscript states that a web server is available, but no details are provided on the implementation, user interface, or any limitations (e.g., maximum sequence length, runtime).  
- **Required correction** Provide a brief description of the web server's functionality, including input/output formats, any constraints, and a screenshot or usage example.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Language  
- **Affected element** Abstract and Introduction  
- **Evidence pointer** Abstract, Introduction  
- **Issue** Some sentences are awkwardly phrased, and there are minor grammatical errors (e.g., "TFs have ability to bind" should be "TFs have the ability to bind").  
- **Required correction** Perform a thorough language edit to improve clarity and grammatical correctness.

## Risk / unsupported claims
- The claim that RGDC captures information related to DNA binding ability is speculative and not supported by mechanistic or functional analyses.
- The claim of "superior performance" over prior methods is not statistically substantiated due to the lack of variance estimates or significance testing.
- The optimal parameters (Op(8), 3-gap) are presented without sensitivity analysis, so their robustness is unknown.
- The generalizability of the methods to other datasets or organisms is not demonstrated.