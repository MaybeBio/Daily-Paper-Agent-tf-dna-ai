## Review setup
- **Input scope** Full manuscript text including abstract, results, methods, and supplementary information description
- **Assessment boundary** Technical and scientific evaluation of the prediction method, feature engineering, experimental design, and reported performance claims
- **Shared manuscript claim summary** The authors propose inpPDH, a support vector machine-based predictor for DNA-binding hot spot residues, which integrates traditional features with newly defined interfacial neighbor properties (INPs) and uses a two-step feature selection strategy to achieve improved prediction performance over existing methods
- **Visible evidence base** Benchmark dataset of 64 protein-DNA complexes (88 hot spots, 126 non-hot spots), training set of 40 complexes (62 hot spots, 88 non-hot spots), test set of 24 complexes (26 hot spots, 38 non-hot spots); performance metrics including SEN, SPE, PRE, F1, MCC, ACC, AUC; ROC curves; correlation heat maps; feature ablation analysis
- **Missing materials affecting confidence** Supplementary file with detailed per-method prediction results (Additional file 1) not provided; web server availability not independently verified; no confidence intervals or variance estimates for performance metrics; no external validation on independent datasets beyond the single test set

## Reviewer
- **Overall assessment** The manuscript presents a reasonable incremental contribution to the field of DNA-binding hot spot prediction. The introduction of interfacial neighbor properties is conceptually interesting and the two-step feature selection strategy is methodologically sound. However, the evaluation is limited to a single small benchmark dataset, and the comparison with existing methods relies on web server submissions without clear evidence of identical input conditions. The reported improvements, while statistically significant in terms of p-values, need stronger validation to establish generalizability. The work is suitable for a specialized bioinformatics audience but does not represent a major conceptual advance.

- **Who would be interested in the results, and why** Researchers working on protein-DNA interaction prediction, computational mutagenesis, and hot spot identification would find this work relevant. Practitioners developing machine learning-based predictors for biological interfaces may benefit from the feature engineering approach and the two-step feature selection methodology. The web server provides a practical tool for experimental biologists studying protein-DNA binding mechanisms.

- **Major strengths**  
  1. The concept of interfacial neighbor properties is a novel contribution that extends beyond single-residue features, potentially capturing cooperative effects in hot spot determination.  
  2. The two-step feature selection strategy combining SVM-RFE with correlation-based redundancy removal is methodologically rigorous and well motivated.  
  3. The feature ablation analysis (Table 1) provides useful insight into the relative importance of individual features.  
  4. The authors provide a freely accessible web server, enhancing the practical utility of the method.

- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Experimental validation  
  - **Claim pointer** The authors claim that inpPDH "yields significantly better prediction accuracy than those previously published methods in the literature" based on comparisons with SAMPDI, PremPDI, and mCSM-NA.  
  - **Evidence pointer** Table 2, Results and discussion section "Comparison with other methods"  
  - **Concern** The comparison with existing methods is performed by submitting the test set to web servers of these methods. This introduces potential inconsistencies: (a) the input formats and preprocessing steps may differ across servers, (b) the authors do not report whether the same structural models or input files were used for all methods, and (c) web server implementations may not reflect the optimal configuration of each method. Additionally, the p-values reported are based on AUC differences across ten randomly selected balanced subsets, but the methodology for generating these subsets and the statistical test used are not fully described.  
  - **Why it matters** The central claim of improved performance over existing methods is the primary contribution of this work. If the comparison is not rigorously controlled, the claim of superiority cannot be reliably established.  
  - **Resolution test** The authors should provide a detailed description of the input preparation for each method, confirm identical input structures and residue definitions, and describe the statistical test used for p-value calculation. Ideally, they should also perform a matched comparison using the same cross-validation folds for all methods.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Generalizability  
  - **Claim pointer** The authors state that "the results on the benchmark dataset show that this proposed method yields significantly better prediction accuracy" and conclude that inpPDH is an "accurate improved prediction model."  
  - **Evidence pointer** Dataset description in Materials and methods section "Data sets"; performance results in Table 2  
  - **Concern** The entire evaluation is based on a single dataset of 64 complexes, which is relatively small and may not be representative of the diversity of protein-DNA interactions. The dataset is derived from dbAMEPNI and SAMPDI, and the authors do not discuss potential biases in this dataset (e.g., overrepresentation of certain protein families or binding modes). No external validation on independent datasets is performed. The test set contains only 26 hot spots, which limits the statistical power of the reported sensitivity and precision estimates.  
  - **Why it matters** A prediction method must demonstrate generalizability beyond the training distribution to be practically useful. Without external validation, the reported performance may reflect dataset-specific overfitting or favorable dataset characteristics.  
  - **Resolution test** The authors should validate inpPDH on at least one independent dataset of protein-DNA complexes with experimentally verified hot spots. If such datasets are not available, they should discuss the limitations and provide a more thorough analysis of dataset composition and potential biases.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Methodological clarity  
  - **Claim pointer** The authors state that "we defined two kinds of interfacial neighborhood properties (INPs) based on the ASA and CASA features" and that these properties "have an important strength for identifying hot spot residues."  
  - **Evidence pointer** Materials and methods section "Interfacial neighborhood properties"; Table 1  
  - **Concern** The definition of INP1 and INP2 is provided in equations 1 and 2, but the biological or physicochemical rationale for these specific formulations is not adequately explained. Why is the ratio of monomer ASA to the average neighbor ASA a meaningful descriptor of hot spot propensity? The choice of a 6.5 Å cutoff for neighbor definition is cited from reference [12], but the sensitivity of results to this parameter is not explored. Furthermore, the feature ablation analysis shows that removing INP1-sASA causes a drop in AUC from 0.839 to 0.777, but the authors do not discuss whether this drop is statistically significant or whether it could be due to chance given the small dataset.  
  - **Why it matters** The novelty of this work rests substantially on the INP features. If the formulation is not well justified or the contribution is not robustly demonstrated, the incremental value over existing methods is diminished.  
  - **Resolution test** The authors should provide a clearer biological rationale for the INP formulations, perform a sensitivity analysis on the neighbor distance cutoff, and report confidence intervals or significance tests for the feature ablation results.

- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Dataset description  
  - **Evidence pointer** Materials and methods section "Data sets"  
  - **Issue** The authors state that the dataset is the same as used in their previous work PrPDH, but they do not provide a detailed description of the dataset composition, including the list of complexes, the criteria for defining hot spots versus non-hot spots, or the source of experimental binding free energy data.  
  - **Required correction** Provide a supplementary table listing all complexes in the dataset, their PDB identifiers, the number of hot spots and non-hot spots per complex, and the criteria used to classify residues as hot spots.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Statistical reporting  
  - **Affected element** Performance metrics  
  - **Evidence pointer** Table 2  
  - **Issue** The performance metrics (SEN, SPE, PRE, F1, MCC, ACC, AUC) are reported as point estimates without confidence intervals or variance measures. Given the small test set (26 hot spots, 38 non-hot spots), these estimates are likely to have substantial uncertainty.  
  - **Required correction** Report confidence intervals for the key metrics, or at minimum provide the number of true positives, false positives, true negatives, and false negatives to allow readers to compute confidence intervals.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Clarity of writing  
  - **Affected element** Results and discussion section "Evaluation of two-step feature selection method"  
  - **Evidence pointer** Figure 1 description  
  - **Issue** The text describing Figure 1 is incomplete. The sentence "the AUC score has been increased with 0.018 and 0.074, respectively" is awkwardly phrased and the LaTeX markup is visible in the text.  
  - **Required correction** Rewrite the sentence for clarity, for example: "the AUC score increased by 0.018 compared to the one-step feature selection and by 0.074 compared to the model without feature selection."

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Resource availability  
  - **Affected element** Web server  
  - **Evidence pointer** Conclusions section  
  - **Issue** The web server URL is provided, but there is no description of the server's implementation, input requirements, or output format. It is unclear whether the server accepts user-uploaded structures or only provides predictions for precomputed examples.  
  - **Required correction** Add a brief description of the web server's functionality, including input format requirements, expected runtime, and output interpretation.

- **Technical failings that need to be addressed before the case is established**  
  - R1-M1: Uncontrolled comparison with existing methods via web servers  
  - R1-M2: Lack of external validation on independent datasets  
  - R1-M3: Insufficient justification and robustness analysis of the INP features

## Risk / unsupported claims
- The claim that inpDH "yields significantly better prediction accuracy than those previously published methods" is not fully supported due to uncontrolled comparison conditions (R1-M1).
- The claim that the two INP features "make an obvious improvement on prediction model" is based on a single ablation analysis without statistical significance testing (R1-M3).
- The generalizability of the method to diverse protein-DNA complexes is not established given the single small dataset (R1-M2).
- The statement that "the combination of interfacial neighbor features and traditional features may support the creation of a discriminative feature set" is speculative and not directly tested against alternative feature combinations.
- The performance of the web server is not independently verifiable from the provided materials.