## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present ZFP-CanPred, a deep learning model using protein language model representations from the structural neighbourhood of mutated sites to predict cancer-associated driver mutations in zinc-finger proteins. They report an accuracy of 0.72, F1-score of 0.79, and AUC of 0.74 on an independent test set, and claim superior performance over 11 existing tools on a curated dataset of 331 mutations.
- **Visible evidence base** Abstract text only; no methodological details, dataset descriptions, or performance breakdowns are provided
- **Missing materials affecting confidence** Full methods, dataset composition and curation criteria, definition of structural neighbourhood, PLM architecture and training details, baseline tool versions and parameters, statistical significance testing, calibration analysis, and code validation

## Reviewer
- **Overall assessment** The abstract describes a potentially useful application of protein language models to a clinically relevant problem in cancer genomics. The reported performance metrics are modest and the comparative claim against 11 tools is difficult to evaluate without details on dataset overlap, baseline configurations, and statistical testing. The work may be of interest to computational biologists and cancer genomics researchers, but the current evidence base is insufficient to establish the model's superiority or general utility.
- **Who would be interested in the results, and why** Computational biologists developing variant effect prediction tools, cancer genomics researchers studying transcription factor mutations, and clinicians or translational scientists interested in driver mutation identification for targeted therapy. The focus on zinc-finger proteins addresses a specific family with broad regulatory importance, which may attract researchers working on gene regulation and oncogenic mechanisms.
- **Major strengths** The problem is well motivated given the biological importance of zinc-finger proteins in cancer. The use of structural neighbourhood information combined with protein language model representations is a reasonable and potentially novel approach. The authors provide open access to source code, which supports reproducibility and community use.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient detail to assess whether the reported performance is robust, whether the comparison against 11 tools is fair, or whether the model generalizes beyond the specific dataset used. Statistical significance of performance differences is not reported. The definition and implementation of "structural neighbourhood" are not described.
- **Assessment against Nature-style criteria** Originality is moderate; the combination of PLMs with structural context for ZNF-specific prediction is somewhat novel but builds on established variant effect prediction approaches. Scientific importance is relevant but not transformative, as the performance gains are modest. Interdisciplinary readership is plausible given the intersection of machine learning, structural biology, and cancer genomics. Technical soundness cannot be fully assessed from the abstract alone, but the lack of statistical testing and methodological detail is a concern. Readability for nonspecialists is adequate, though terms like "structural neighbourhood" and "PLM representations" would benefit from brief clarification.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a reasonable proof-of-concept, but the claims of superiority and practical utility require full methodological transparency and rigorous comparative analysis.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "ZFP-CanPred, achieved a superior performance with an accuracy of 0.72, F1-score of 0.79, and area under the Receiver Operating Characteristics (ROC) Curve (AUC) of 0.74, on an independent test set."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The reported performance metrics are modest, and no confidence intervals, standard deviations, or statistical significance tests are provided. It is unclear whether the independent test set is representative of the broader mutation space in zinc-finger proteins, and whether the model's performance is stable across different data splits.
- **Why it matters** Without statistical rigor, the reported accuracy and AUC cannot be distinguished from chance variation or dataset-specific artifacts. This undermines the reliability of the model for downstream applications in cancer genomics.
- **Resolution test** Provide confidence intervals or bootstrapped estimates for all metrics, report performance across multiple cross-validation folds, and include a statistical comparison against a null model or random baseline.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative validity
- **Claim pointer** "In a comparative analysis against 11 existing prediction tools using a curated dataset of 331 mutations, ZFP-CanPred demonstrated the highest AU-ROC of 0.74, outperforming both generic and cancer-specific methods."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The comparison against 11 tools is not described in sufficient detail. It is unclear whether the same dataset was used for all tools, whether default parameters were applied, whether the tools were retrained or used as pretrained models, and whether the 331 mutations overlap with the training data of any of the baselines.
- **Why it matters** An unfair or inconsistent comparison can inflate the apparent superiority of ZFP-CanPred. The claim of "highest AU-ROC" is only meaningful if all methods are evaluated under identical conditions with appropriate controls.
- **Resolution test** Describe the exact evaluation protocol for each baseline, including version, parameters, and any retraining. Report per-tool performance on the same independent test set and provide a statistical test for differences in AUC (e.g., DeLong test).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and methodological clarity
- **Claim pointer** "The representations derived from protein language models (PLMs) from the structural neighbourhood of mutated sites were utilized to train ZFP-CanPred"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not define what constitutes a "structural neighbourhood," how it is computed, which PLM is used, how representations are aggregated, or how the model architecture is designed. Without these details, the method cannot be reproduced or independently validated.
- **Why it matters** Reproducibility is a core requirement for computational tools. The absence of methodological detail prevents other researchers from building on or benchmarking the approach, and limits the scientific contribution.
- **Resolution test** Provide a detailed methods section describing the structural neighbourhood definition, PLM choice and version, feature extraction and aggregation, model architecture, training procedure, and hyperparameters. Include code and data availability statements that allow full replication.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Dataset description
- **Affected element** "curated dataset of 331 mutations"
- **Evidence pointer** Abstract only; location not provided
- **Issue** The origin, curation criteria, and class balance of the 331-mutation dataset are not described. It is unclear whether this dataset is independent of the training set and how neutral versus cancer-causing mutations were defined.
- **Required correction** Specify the source databases, inclusion and exclusion criteria, and the proportion of positive and negative examples. Clarify whether this dataset was used only for benchmarking or also for training.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Performance interpretation
- **Affected element** "balanced performance across specificity and sensitivity"
- **Evidence pointer** Abstract only; location not provided
- **Issue** The abstract does not report sensitivity and specificity values, so the claim of balance cannot be verified. A balanced performance is only meaningful if both metrics are reported and compared against baselines.
- **Required correction** Report sensitivity, specificity, precision, and F1-score for ZFP-CanPred and for the best-performing baseline tools.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** "predicting cancer-associated driver mutations in ZNFs"
- **Evidence pointer** Abstract only; location not provided
- **Issue** The model is trained and evaluated on zinc-finger protein mutations, but it is unclear whether the model would generalize to other transcription factor families or to non-cancer contexts. The abstract does not discuss potential limitations in this regard.
- **Required correction** Add a discussion of model scope and potential transferability, or explicitly state that the model is intended for ZNF-specific use only.

## Risk / unsupported claims
- The claim of "superior performance" over 11 tools is unsupported without detailed comparative methodology and statistical testing.
- The claim of "balanced performance across specificity and sensitivity" is unverifiable from the abstract alone.
- The general utility of the model for cancer driver mutation prediction is not established beyond the specific dataset and protein family.
- The novelty of the approach relative to existing PLM-based variant effect predictors is not clearly articulated.
- The reproducibility of the method is not assessable from the abstract due to missing methodological details.