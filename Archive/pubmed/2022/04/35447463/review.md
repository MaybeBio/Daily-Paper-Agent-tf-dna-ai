## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose Target-DBPPred, a computational method for predicting DNA-binding proteins (DBPs) using a novel feature descriptor EDF-PSSM-DWT combined with multiple evolutionary feature descriptors, feature selection via sequential forward selection (SFS), and classification with Light eXtreme Gradient Boosting (LiXGB). They report accuracy improvements of 6.69% (training) and 15.07% (testing) over existing predictors.
- **Visible evidence base** Abstract text only; no quantitative performance metrics beyond the two accuracy improvement percentages; no dataset descriptions, benchmark comparisons, or statistical validation details
- **Missing materials affecting confidence** Full manuscript, all figures and tables, dataset specifications, baseline method details, hyperparameter settings, cross-validation protocols, and code or data availability statements

## Reviewer
- **Overall assessment** The abstract presents a plausible methodological pipeline for DBP prediction, combining established feature extraction techniques with a relatively recent boosting variant. However, the evidence provided is insufficient to evaluate the technical soundness, reproducibility, or generalizability of the claimed improvements. The reported accuracy gains lack context regarding baselines, datasets, and statistical significance.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those developing machine learning models for DNA-binding protein identification. Researchers in drug discovery and disease mechanism studies may also find relevance given the stated associations with human diseases.
- **Major strengths** The proposed feature descriptor EDF-PSSM-DWT integrates evolutionary information with signal processing, which is a reasonable approach for capturing sequence patterns. The use of multiple feature descriptors and classifier comparison reflects a systematic methodology. The reported performance gains, if reproducible, would represent a meaningful advancement in this prediction task.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset and baseline transparency), R1-M2 (statistical validation), R1-M3 (reproducibility)
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The combination of EDF-PSSM with DWT is novel, but the overall approach follows established patterns in the field.  
  - Scientific importance: Moderate. DBP prediction is a relevant problem, but the abstract does not demonstrate a transformative advance.  
  - Interdisciplinary readership: Limited. The work is primarily of interest to computational biology specialists.  
  - Technical soundness: Not assessable from the abstract alone. Critical details on data, validation, and implementation are absent.  
  - Readability for nonspecialists: Acceptable. The abstract is understandable, though technical terms are used without explanation.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if technical concerns are resolved with full manuscript data.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The claim that LiXGB with EDF-PSSM-DWT achieved 6.69% and 15.07% higher accuracy on training and testing datasets, respectively, compared to existing predictors.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not specify which datasets were used, what the baseline predictors were, or how the training and testing splits were constructed. Without this information, the reported accuracy improvements cannot be contextualized or verified.  
- **Why it matters** Accuracy improvements are only meaningful relative to well-defined baselines and datasets. If the baselines are weak or the datasets are non-standard, the claimed gains may not reflect genuine methodological advancement.  
- **Resolution test** Provide dataset names, sizes, and sources; list all baseline methods with their performance; describe the train-test split protocol (e.g., cross-validation, independent test set).

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The claim of improved performance over existing predictors.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No statistical significance tests, confidence intervals, or variance measures are reported. The observed accuracy differences could be within random variation, especially if evaluated on a single split.  
- **Why it matters** Without statistical validation, the robustness of the claimed improvement is unknown. A single favorable split can produce misleading results.  
- **Resolution test** Report statistical tests (e.g., paired t-test, Wilcoxon signed-rank test) across multiple cross-validation folds or independent runs, and provide confidence intervals for all performance metrics.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The proposed method Target-DBPPred and its feature descriptor EDF-PSSM-DWT.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No details are provided on hyperparameter settings for LiXGB, Adaboost, XGB, and ERT, nor on the implementation of SFS. The abstract does not mention code availability or data availability.  
- **Why it matters** Reproducibility is a core requirement for computational methods. Without implementation details and access to code or data, other researchers cannot validate or build upon the work.  
- **Resolution test** Provide full hyperparameter specifications, software versions, and a public repository with code and data, or a detailed description sufficient for independent reimplementation.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Feature descriptor description  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abbreviation EDF-PSSM-DWT is introduced but the components are not fully explained. The term "Evolutionary difference formula" is unclear without further context.  
- **Required correction** Provide a brief explanation of what the evolutionary difference formula computes and how it differs from standard PSSM encoding.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Performance metrics  
- **Evidence pointer** Abstract, location not provided  
- **Issue** Only accuracy is mentioned. Other standard metrics such as sensitivity, specificity, Matthews correlation coefficient, and area under the ROC curve are not reported.  
- **Required correction** Report a full set of performance metrics to allow comprehensive comparison with existing methods.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Related work  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract states that "several methods have been reported" but does not name any specific prior methods or their performance levels.  
- **Required correction** Cite and briefly describe the most relevant prior methods and their reported performance to establish the baseline context.

## Risk / unsupported claims
- The claim of 6.69% and 15.07% accuracy improvements is unsupported without dataset and baseline details.
- The general claim that "the obtained results verify the improved performance of our proposed predictor over the existing predictors" is not verifiable from the abstract alone.
- The biological relevance claims (association with asthma, cancer, AIDS) are stated without supporting references or data, though these are likely background context rather than novel findings.