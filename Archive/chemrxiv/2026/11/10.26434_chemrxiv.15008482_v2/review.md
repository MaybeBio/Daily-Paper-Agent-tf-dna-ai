## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary material were available for inspection
- **Shared manuscript claim summary** The authors introduce SO3LR-SF, a physics-based scoring framework built on four pretrained SO3LR machine-learned force fields, and report competitive accuracy against DLPNO-CCSD(T) references on PLA15, comparable ranking performance to semi-empirical and molecular dynamics-based methods on two ligand-binding benchmarks, fast per-complex scoring times, a trimming protocol, a restrained geometry optimization step, and a multi-level explainability framework including a predictive relationship between polar SASA ratio and electrostatic scoring performance
- **Visible evidence base** Abstract text only; no figures, tables, methods descriptions, or supplementary data were provided
- **Missing materials affecting confidence** Full methods, benchmark construction details, data splits, uncertainty estimates, statistical significance tests, computational details for reference calculations, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a potentially useful scoring framework with an attractive combination of speed, accuracy, and interpretability. However, the evidence base available for review is limited to the abstract, which prevents verification of the central claims. Several claims are stated without supporting statistical detail, and the relationship between the reported metrics and the underlying data distributions cannot be assessed. The work is likely of interest to the computational drug discovery community, but the case for its central conclusions is not fully established from the supplied material.
- **Who would be interested in the results, and why** Computational chemists and structural biologists working on structure-based drug design, particularly those developing or applying machine-learned force fields, scoring functions, and free-energy methods. The combination of speed, accuracy, and interpretability would appeal to practitioners seeking practical alternatives to expensive alchemical free-energy calculations.
- **Major strengths** The framework addresses a real need for fast and accurate protein-ligand binding affinity estimation. The reported accuracy on PLA15 against high-level quantum reference data is notable. The inclusion of explainability tools is a valuable addition. The claim that no experimental binding-affinity data are required for training is an important differentiator.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor
  - **Claim pointer** The abstract reports average Spearman correlations of around 0.50 on the FEP benchmark and around 0.59 on the Wang dataset, and states that these values match or surpass several comparator methods
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The abstract reports only point estimates of Spearman correlations without confidence intervals, standard errors, or statistical significance tests against comparator methods. The differences between SO3LR-SF (0.50) and GFN-FF (0.47) or MMGBSA (0.44) may not be statistically meaningful, particularly given the small number of targets (8 in each benchmark).
  - **Why it matters** Without uncertainty quantification, the reader cannot determine whether the reported performance differences are robust or within noise. This is critical for a claim of parity or superiority against established methods.
  - **Resolution test** Provide confidence intervals or bootstrap estimates for all reported correlations, and perform paired statistical tests (e.g., Wilcoxon signed-rank across targets) between SO3LR-SF and each comparator.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility and methodology
  - **Claim pointer** The abstract states that SO3LR-SF can be instantiated with any of four pretrained SO3LR models and combines an equivariant message-passing network with physically motivated terms
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The abstract does not describe how the physically motivated terms are parameterized, how they are combined with the neural network, or whether any fitting is performed on the benchmarks. The statement that no experimental binding-affinity data are used for training is ambiguous, as it does not clarify whether the physically motivated terms or any other components are optimized on the benchmark datasets.
  - **Why it matters** The scientific contribution depends on the clarity of the method. If any component is tuned on the test benchmarks, the reported performance could be optimistically biased. The reader cannot assess the method's generalizability without this information.
  - **Resolution test** Provide a full methods description, including parameterization of all terms, any fitting procedures, and explicit confirmation that no benchmark data were used in any training or tuning step.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Benchmark validity
  - **Claim pointer** The abstract reports relative interaction errors of 2.1-5.8% against DLPNO-CCSD(T) references on PLA15 (15 active-site models)
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The abstract does not specify how the DLPNO-CCSD(T) reference values were computed, what level of theory was used for the underlying structures, or whether the same structures were used for all methods. The comparison across methods is therefore difficult to interpret.
  - **Why it matters** The accuracy claim against high-level quantum reference data is the strongest evidence for the method's physical validity. Without details on the reference calculations and structural preparation, the claim cannot be independently assessed.
  - **Resolution test** Provide full computational details for the DLPNO-CCSD(T) calculations, including basis sets, truncation settings, and structure preparation protocols.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Predictive claim
  - **Claim pointer** The abstract states that the polar SASA ratio of the binding pocket is predictive of electrostatic scoring performance, with r = 0.74-0.81 across models
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** This is a potentially useful diagnostic, but the abstract does not report how this correlation was computed, over how many data points, or whether it was validated on held-out data. The range of r values across models is reported, but the significance of these correlations is not stated.
  - **Why it matters** If this relationship is robust, it could enable pre-scoring quality assessment. However, without validation details, it may be an overfit observation on a small number of targets.
  - **Resolution test** Report the number of data points, the statistical significance of the correlations, and any cross-validation or out-of-sample testing used to establish the predictive claim.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Runtime claim
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The abstract states that each complex is scored in 3 s to 47 s on 12 CPU cores, but does not specify which model or system size corresponds to which end of this range.
  - **Required correction** Provide a breakdown of runtime by model and system size, or state the range explicitly as a function of these variables.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Trimming protocol
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The 8 Å trimming protocol is stated to reduce runtime threefold without loss of accuracy, but the abstract does not specify which accuracy metric is used or over which benchmark this was tested.
  - **Required correction** Specify the accuracy metric and the benchmark used to support the "without loss of accuracy" claim.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "Physics-based" description
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The framework is described as "physics-based," but it combines a learned neural network with physically motivated terms. The term may be misleading without clarification of the relative contribution of each component.
  - **Required correction** Clarify the extent to which the model is physics-based versus learned, and consider using a more precise descriptor such as "hybrid physics-informed."
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Pretrained models
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The abstract refers to four pretrained SO3LR models but does not state where these models can be obtained or whether they are publicly available.
  - **Required correction** Provide availability information for the pretrained models, including any licenses or access restrictions.

## Technical failings that need to be addressed before the case is established
- R1-M1: Lack of uncertainty quantification and statistical significance testing for all reported performance metrics
- R1-M2: Insufficient methodological detail to assess potential benchmark overfitting or tuning
- R1-M3: Incomplete description of reference calculations and structural preparation for the PLA15 benchmark

## Assessment against Nature-style criteria
- **Originality** The combination of a pretrained equivariant neural network with explicit physical terms for a scoring function is a reasonable contribution, though the individual components are not novel. The explainability framework and the polar SASA diagnostic are potentially original elements.
- **Scientific importance** Accurate and fast binding affinity prediction is of high importance to drug discovery. If the claims are substantiated, the work could have practical impact. However, the importance is moderated by the lack of demonstrated advantage over existing methods beyond parity.
- **Interdisciplinary readership** The work bridges machine learning, physical chemistry, and drug design, and would be of interest to readers across these fields. The abstract is written in a way that is largely accessible to nonspecialists.
- **Technical soundness** Cannot be fully assessed from the abstract. The reported metrics are plausible, but the absence of statistical rigor and methodological detail prevents verification.
- **Readability for nonspecialists** The abstract is clearly written and the key claims are understandable. The use of acronyms (SO3LR, DLPNO-CCSD(T), MMGBSA) is standard for the field.

## Recommendation posture
Currently not established from the provided evidence. The abstract presents an interesting framework with promising results, but the lack of statistical rigor, methodological detail, and validation information prevents a supportive recommendation. The authors should provide the full manuscript with complete methods, uncertainty quantification, and benchmark details for a proper assessment.

## Risk / unsupported claims
- The claim that SO3LR-SF "requires no experimental binding-affinity data for training" is not verifiable from the abstract, as the training procedure for the physically motivated terms is not described.
- The claim that the 8 Å trimming protocol reduces runtime threefold "without loss of accuracy" is unsupported without specification of the accuracy metric and benchmark.
- The predictive relationship between polar SASA ratio and electrostatic scoring performance (r = 0.74-0.81) is reported without sample size, significance, or validation details.
- The parity or superiority claims against GFN-FF, MMGBSA, Glide, and molecular dynamics-based methods are not supported by statistical testing.
- The runtime range of 3 s to 47 s is reported without context regarding model or system size.