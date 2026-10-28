## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific and technical evaluation of the manuscript content only; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors propose DRBP-EDP, a two-stage deep learning pipeline that uses ESM-2 embeddings and a dual-path neural network (Transformer-CNN and BiLSTM-Attention) to first classify proteins as nucleic acid-binding proteins (NABPs) versus non-NABPs, and then classify NABPs as DNA-binding proteins (DBPs) or RNA-binding proteins (RBPs). They report strong performance (90.03% accuracy in stage 1, 89.56% in stage 2) and claim superiority over 13 existing predictors on temporal and cross-species validation sets.
- **Visible evidence base** Abstract, Introduction, Materials and Methods (Datasets, Data partitioning, Data augmentation, Overall architecture, ESM-2, Transformer-CNN, BiLSTM-attention, Hyperparameter configuration, Loss function, Evaluation metrics), Results (Evaluation results at different classification stages, Ablation study, Comparative performance of model architectures, Comparative performance with other predictors, Impact of sequence redundancy thresholds, Application), Discussion, Conclusion
- **Missing materials affecting confidence** Figures 1-6 and Tables 1-5 are referenced but not provided; detailed results of statistical significance tests are not reported; exact dataset construction filtering criteria are only partially described; comparison predictor versions and hyperparameters are not specified; confidence intervals or variance measures for reported metrics are absent

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in protein function prediction, namely the discrimination of DNA-binding and RNA-binding proteins, which is complicated by the sequence and structural similarity of these two classes. The use of ESM-2 as a feature extractor is timely and the dual-path architecture is a reasonable design choice. However, the manuscript as presented has several significant gaps that prevent full evaluation of the claims. The most critical issues are the absence of the actual figures and tables, which are essential for assessing the validity of the reported results, and the lack of statistical rigor in comparing against baseline methods. The claim of "unprecedented performance" is not adequately supported without proper statistical testing and without demonstrating that the comparison is fair in terms of training data, hyperparameter tuning, and evaluation protocol. The dataset construction methodology is described at a high level but lacks the detail needed to assess potential biases, particularly regarding sequence redundancy and annotation quality. The manuscript would benefit from a clearer articulation of the novelty relative to existing ESM-based approaches and a more thorough analysis of failure cases.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those developing deep learning methods for nucleic acid-binding protein classification. The manuscript may also be of interest to researchers applying protein language models to downstream prediction tasks, as it demonstrates a specific application of ESM-2. The availability of both executable and web-based tools could be useful for experimental biologists seeking to annotate novel proteins.

- **Major Strengths**
  1. The problem is well-motivated and practically relevant, with clear applications in agriculture and medicine.
  2. The use of ESM-2, a state-of-the-art protein language model, is appropriate and current.
  3. The two-stage classification design is logical and addresses the hierarchical nature of the problem.
  4. The inclusion of temporal validation (TEST236) and cross-species evaluation is a good practice for assessing generalization.
  5. The authors provide both code and a web server, which enhances the utility of the work.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence integrity
- **Claim pointer** The authors report specific performance metrics (e.g., 90.03% accuracy in stage 1, 89.56% in stage 2, MCC of 80.18% and 78.51% respectively) and claim superiority over 13 predictors.
- **Evidence pointer** Results section, "Evaluation results at different classification stages" and "Comparative performance analysis of DRBP-EDP with other predictors"; Tables 3-5 and Figures 3-4 are referenced but not provided
- **Concern** The core results are presented without the accompanying figures and tables, which are essential for verification. The reported numbers cannot be independently checked, and the claim of superiority over 13 predictors is made without showing the full comparison table or providing statistical significance tests. Without these materials, the validity of the performance claims cannot be assessed.
- **Resolution test** Provide all figures and tables with full numerical data. Include confidence intervals or standard deviations for all reported metrics. Perform and report statistical significance tests (e.g., McNemar's test or DeLong's test for AUC comparison) against all baseline methods.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology completeness
- **Claim pointer** The authors state that a "refined approach to dataset construction is designed, resulting in the creation of high-quality protein classification datasets."
- **Evidence pointer** Materials and Methods, "Datasets" section; Figures 1A and 2A are referenced but not provided
- **Concern** The dataset construction process is described only at a high level. Key details are missing: the exact filtering criteria beyond the 0.4 similarity threshold, how annotation quality was verified, how the DBP and RBP labels were assigned (e.g., based on experimental evidence codes, GO annotations, or literature curation), and how potential conflicts (proteins annotated as both DBP and RBP) were resolved. The claim of "high-quality" datasets cannot be evaluated without this information.
- **Resolution test** Provide a detailed step-by-step description of the dataset construction pipeline, including all filtering thresholds, annotation sources, and conflict resolution strategies. Include a flowchart or pseudocode. Report the number of sequences removed at each step and the final annotation distribution.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative validity
- **Claim pointer** The authors claim that DRBP-EDP "demonstrated unprecedented performance" and outperformed 13 predictors on TEST236 and cross-species datasets.
- **Evidence pointer** Results section, "Comparative performance analysis of DRBP-EDP with other predictors"; Tables 4-5 are referenced but not provided
- **Concern** The comparison against 13 predictors is not described in sufficient detail. It is unclear whether the baseline methods were retrained on the same training data, whether their hyperparameters were optimized to the same extent, and whether the same evaluation protocol was used. If the baselines were not retrained and tuned under identical conditions, the comparison is potentially unfair. Additionally, the choice of baselines and their versions (e.g., web server versions vs. local implementations) is not specified.
- **Resolution test** Describe the exact protocol for baseline comparison, including whether each baseline was retrained, how hyperparameters were selected, and the version of each tool used. Provide the full comparison table with all metrics for all methods. Consider reporting results with and without retraining baselines to demonstrate robustness.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The authors state that "the combination of ESM-2 with the dual-path neural network offers certain advantages in handling complex protein classification tasks" based on ablation studies.
- **Evidence pointer** Results section, "Ablation study"; Table 3 is referenced but not provided
- **Concern** The ablation study is described only in terms of which components were removed, but the results are not shown. It is unclear whether the improvements are statistically significant and whether the ablation was performed on both stages. The claim that the dual-path design is beneficial needs to be supported by showing the performance of each variant across all metrics and ideally across multiple random seeds.
- **Resolution test** Provide the full ablation table with all metrics for each variant. Report results from multiple random seeds with mean and standard deviation. Perform statistical testing to confirm that differences are significant.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and analysis
- **Claim pointer** The authors state that "Fig. 3C depicted the prediction performance of each protein sequence in the test set in the form of a scatter plot" and discuss the impact of sequence redundancy thresholds.
- **Evidence pointer** Results section, "Evaluation results at different classification stages" and "Impact of sequence redundancy thresholds on overfitting and predictive performance"; Figures 3C and 5 are referenced but not provided
- **Concern** The analysis of prediction performance at the individual sequence level and the discussion of redundancy thresholds would benefit from more detailed interpretation. The scatter plot is mentioned but not shown, and the discussion of the redundancy threshold results is largely descriptive without providing mechanistic insight into why NR70 is optimal. The claim that "appropriate redundancy management enables optimal feature learning" is speculative without further analysis.
- **Resolution test** Provide the scatter plot and discuss specific examples of correct and incorrect predictions. For the redundancy analysis, provide a more detailed interpretation of why the optimal threshold exists, potentially including analysis of sequence features or embedding properties at different thresholds.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "90.03% accuracy in the first stage" and "89.56% accuracy in the second stage" but does not mention the corresponding MCC values or other metrics. This gives an incomplete picture of performance.
- **Required correction** Include MCC values in the abstract for both stages, or state that full metrics are reported in the main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Hyperparameter configuration
- **Evidence pointer** Materials and Methods, "Hyperparameter configuration" section; Table 2 is referenced but not provided
- **Concern** The hyperparameter table is not shown. The description mentions Optuna optimization but does not specify the search space, the number of trials, or the final values for key hyperparameters such as learning rate, batch size, number of layers, hidden dimensions, etc.
- **Required correction** Provide the full hyperparameter table and describe the Optuna search space and optimization process.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Results section, "Evaluation results at different classification stages"
- **Issue** The results are reported as averages from five-fold cross-validation, but no variance measures (e.g., standard deviation) are provided.
- **Required correction** Report standard deviations or confidence intervals for all metrics across the five folds.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion section is very brief and does not adequately contextualize the results, discuss limitations, or compare with the most recent state-of-the-art methods in depth.
- **Required correction** Expand the Discussion to include a critical assessment of the method's limitations, a more thorough comparison with recent approaches, and potential directions for future work.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Data augmentation
- **Evidence pointer** Materials and Methods, "Data augmentation" section
- **Issue** The data augmentation section lists methods but does not describe them in detail. The text ends with "introducing protein sequence variants through multiple methods:" followed by a list that is not fully described in the provided text.
- **Required correction** Provide a complete description of each data augmentation method, including any parameters or thresholds used.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Application
- **Evidence pointer** Results section, "Application"
- **Issue** The application section is very brief and does not describe the user interface, input/output formats, or any usage examples.
- **Required correction** Provide a more detailed description of the web server and executable, including screenshots or usage examples.

## Risk / unsupported claims
- The claim of "unprecedented performance" is not supported without statistical significance testing and full comparison data.
- The claim that the dataset is "high-quality" cannot be evaluated without detailed dataset construction information.
- The claim that "appropriate redundancy management enables optimal feature learning" is speculative and not directly supported by the presented analysis.
- The reported performance metrics (90.03% and 89.56% accuracy) cannot be verified without the corresponding figures and tables.
- The claim that DRBP-EDP outperforms 13 predictors cannot be assessed without the full comparison table and details of the comparison protocol.
- The statement that "the combination of ESM-2 with the dual-path neural network offers certain advantages" is not fully supported without the ablation results table.