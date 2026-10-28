## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials & Methods, Results, Conclusions) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided text
- **Shared manuscript claim summary** The authors propose PDBP-Fusion, a deep learning method combining CNN and Bi-LSTM, to predict DNA-binding proteins from primary sequences using one-hot encoding, achieving superior performance over existing methods on benchmark and independent datasets
- **Visible evidence base** Text descriptions of datasets (PDB14189, PDB2272), model architecture, experimental procedures, and reported performance metrics in Tables 3-8 (tables not visible)
- **Missing materials affecting confidence** All figures (Figs. 1-9), all tables (Tables 2-8), supplementary code, web server accessibility, and detailed hyperparameter configurations

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in bioinformatics, namely the prediction of DNA-binding proteins from sequence data. The proposed architecture combining CNN and Bi-LSTM is not conceptually novel, as similar hybrid architectures have been widely applied in sequence analysis. The main claimed contribution is the use of one-hot encoding instead of word embedding, which is a relatively incremental modification. The reported performance improvements are substantial, but the absence of visible tables and figures prevents verification of these claims. Several methodological ambiguities and potential issues with dataset leakage and evaluation protocol need clarification. The manuscript is technically sound in its general approach but lacks sufficient detail for full reproducibility and does not demonstrate a clear advance over existing state-of-the-art methods beyond incremental metric improvements.
- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics working on protein function prediction, particularly those developing deep learning methods for sequence-based classification tasks. The work may also be of interest to those studying DNA-protein interactions and genome annotation. The claim of improved efficiency via one-hot encoding could appeal to practitioners seeking simpler preprocessing pipelines.
- **Major strengths** The problem is well-motivated and practically relevant. The use of a hybrid CNN-BiLSTM architecture is reasonable for capturing both local motifs and long-range dependencies. The authors evaluate on both a benchmark dataset and an independent test set, which is good practice. The provision of a web server and code is commendable for usability. The comparison against multiple existing methods, including traditional machine learning and deep learning approaches, is thorough in scope.
- **Major Concerns** 
  - R1-M1: Dataset leakage and redundancy
  - R1-M2: Evaluation protocol and statistical significance
  - R1-M3: Comparison fairness and baseline implementation
  - R1-M4: Reproducibility and methodological detail
  - R1-M5: Claim of superiority and generalizability
- **Minor Comments** 
  - R1-m1: Typographical and language issues
  - R1-m2: Inconsistent terminology
  - R1-m3: Missing figure/table references
  - R1-m4: Web server accessibility
  - R1-m5: Clarity of contribution statement
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: Low to moderate. Hybrid CNN-LSTM architectures for sequence classification are well established. The specific application to DBP prediction with one-hot encoding is incremental.
  - Scientific importance: Moderate. DBP prediction is a useful task, but the methodological advance is limited and does not open new biological or computational directions.
  - Interdisciplinary readership: Limited. The work is primarily of interest to bioinformatics specialists; the methodological novelty is unlikely to attract a broader scientific audience.
  - Technical soundness: Questionable based on provided evidence. Several methodological details are missing, and the evaluation protocol raises concerns about data leakage and statistical validity.
  - Readability for nonspecialists: Acceptable. The manuscript is generally clear, though some sections assume familiarity with deep learning terminology.
- **Recommendation posture** Currently not established from the provided evidence. Major concerns regarding dataset handling, evaluation rigor, and reproducibility must be resolved before the claims of superior performance can be accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data integrity and experimental validity
- **Claim pointer** The authors claim that PDBP-Fusion achieves superior performance on the PDB14189 benchmark dataset and PDB2272 independent dataset, implying that the model generalizes well to unseen data.
- **Evidence pointer** Section "Datasets", Section "Performance comparison on the benchmark dataset", Section "Performance comparison on the independent test datasets"
- **Concern** The PDB14189 dataset is described as containing 7,129 DBPs and 7,060 non-DBPs. The authors state that the PDB2272 dataset was filtered to remove sequences with more than 25% similarity. However, no such redundancy filtering is described for the PDB14189 training dataset. If the training set contains sequences highly similar to those in the test set, the reported performance may be inflated due to homology-based leakage. Additionally, the authors do not specify how the train/test splits were constructed during 5-fold cross-validation, nor whether sequence-level redundancy was controlled across folds.
- **Why it matters** If sequence redundancy is not controlled, the model may simply memorize near-duplicate sequences rather than learn generalizable features. This would invalidate the claim of superior generalization and make the reported performance metrics unreliable.
- **Resolution test** The authors must clarify whether redundancy filtering was applied to PDB14189, describe the exact procedure for constructing cross-validation folds, and provide evidence that no significant sequence similarity exists between training and test partitions. Ideally, they should report performance on a strictly non-redundant test set.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and evaluation methodology
- **Claim pointer** The authors report performance metrics (accuracy, precision, sensitivity, specificity, MCC, AUC) for PDBP-Fusion and compare them against other methods, claiming improvements of at least 9.1% in MCC.
- **Evidence pointer** Section "Model construction and evaluation", Section "Performance comparison on the benchmark dataset", Section "Performance comparison on the independent test datasets"
- **Concern** The evaluation protocol is described as 5-fold cross-validation repeated five times, with the average used as the final performance. However, the authors do not report variance or confidence intervals for any of the metrics. Given that deep learning models are known to exhibit variability across runs, the absence of standard deviation or statistical significance testing (e.g., paired t-test or Wilcoxon test) makes it impossible to determine whether the reported improvements over baselines are statistically meaningful. Furthermore, the comparison with methods like DNABP and MsDBP relies on previously published results, but the authors do not specify whether these were re-implemented under identical conditions or taken from the original publications, which may involve different data splits or preprocessing.
- **Why it matters** Without statistical significance testing and variance reporting, the claim of "superior performance" is not substantiated. The observed differences could be within the range of random variation, especially given the small number of repeated runs.
- **Resolution test** The authors should report mean and standard deviation for all metrics across the five repeated runs, perform appropriate statistical tests comparing PDBP-Fusion against each baseline, and clarify whether baseline results were reproduced under identical experimental conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Fairness of comparison and baseline validity
- **Claim pointer** The authors claim that PDBP-Fusion outperforms existing methods including DNABP, MsDBP, and StackDPPred on the same benchmark dataset.
- **Evidence pointer** Section "Performance comparison on the benchmark dataset", Section "Performance comparison on the independent test datasets"
- **Concern** The comparison with StackDPPred is described as using one-hot encoding and exploring SVM, KNN, LogReg, and RDF as base classifiers. However, the authors do not provide details on how these classifiers were optimized, what hyperparameter tuning was performed, or whether the same data splits were used. For DNABP and MsDBP, the authors rely on published results, but it is unclear whether those methods were evaluated on the exact same dataset version and with the same preprocessing. Additionally, the authors do not compare against more recent deep learning methods for DBP prediction, which limits the relevance of the claimed improvements.
- **Why it matters** An unfair or incomplete comparison undermines the central claim of the manuscript. If baselines are not optimally configured or evaluated under different conditions, the reported improvements may be artifacts of experimental setup rather than genuine methodological advances.
- **Resolution test** The authors should provide full details of baseline implementations, including hyperparameter optimization procedures, and ensure that all methods are evaluated on identical data splits and preprocessing pipelines. They should also include comparisons with more recent state-of-the-art deep learning methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and methodological transparency
- **Claim pointer** The authors state that the entire procedure was implemented based on the Keras framework and that complete code is provided via a web server.
- **Evidence pointer** Section "Experimental parameter configuration", Section "Web server for PDBP-Fusion"
- **Concern** The manuscript provides a high-level description of the model architecture but lacks critical details for reproduction. Specifically, the number of CNN layers, filter sizes, stride, pooling sizes, number of Bi-LSTM units, number of dense layers, dropout rates (beyond the range tested), batch size, learning rate, optimizer choice, and early stopping criteria are not fully specified. Table 2 is referenced but not visible. The web server URL is provided, but its accessibility and functionality cannot be verified from the manuscript. Additionally, the authors do not specify the random seed used for initialization, which is essential for reproducibility in deep learning experiments.
- **Why it matters** Reproducibility is a fundamental requirement for scientific validity. Without complete architectural and training details, other researchers cannot replicate the experiments or build upon the method. The claim of providing code is insufficient if the code is not accessible or documented.
- **Resolution test** The authors must provide a complete specification of the model architecture and training procedure, either in the manuscript or as supplementary material. The web server and code should be verified to be accessible and functional, with clear documentation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and scope of claims
- **Claim pointer** The authors conclude that "the fusion approach, combining local features and long-term dependencies, will be necessary for sequence-based tasks in genomics" and that PDBP-Fusion "showed remarkably higher generalization ability compared with existing methods."
- **Evidence pointer** Section "Conclusions"
- **Concern** The claim of general necessity for fusion approaches in genomics is overly broad and not supported by the experiments, which only address the specific task of DBP prediction. The claim of "remarkably higher generalization ability" is based on performance on a single independent dataset (PDB2272), which may not be representative of diverse genomic contexts. The authors do not discuss potential limitations of their approach, such as performance on proteins with unusual sequence composition or the impact of dataset bias.
- **Why it matters** Overstated conclusions can mislead readers and overstate the significance of the work. A more measured interpretation of the results, acknowledging limitations, would strengthen the manuscript's credibility.
- **Resolution test** The authors should temper their conclusions to reflect the specific scope of their experiments, discuss potential limitations, and avoid making broad claims about general applicability without additional evidence.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Language and presentation
- **Affected element** Abstract, Introduction, Conclusions
- **Evidence pointer** Location not provided
- **Issue** The manuscript contains several typographical and grammatical errors, such as "In this his study" in the Conclusions section. These errors detract from the professional presentation of the work.
- **Required correction** The manuscript should be carefully proofread and edited for language quality.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Location not provided
- **Issue** The terms "local features" and "long-term dependencies" are used throughout, but the manuscript does not clearly define what constitutes "local" versus "long-term" in the context of the sequence lengths used. The distinction between these feature types is central to the method's rationale.
- **Required correction** Provide explicit definitions of local and long-term features in the context of the model architecture and sequence lengths.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure and table referencing
- **Affected element** Results section
- **Evidence pointer** Location not provided
- **Issue** The manuscript references Figures 1-9 and Tables 2-8, but these are not visible in the provided text. The reader cannot verify the claims made in the text without access to these visual elements.
- **Required correction** Ensure all figures and tables are included and properly referenced in the final submission.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Web server accessibility
- **Affected element** Section "Web server for PDBP-Fusion"
- **Evidence pointer** Location not provided
- **Issue** The web server URL is provided, but there is no information about its uptime, maintenance status, or user instructions beyond a general statement.
- **Required correction** Provide a brief description of the web server interface and usage instructions, and confirm its accessibility.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Contribution clarity
- **Affected element** Introduction
- **Evidence pointer** Location not provided
- **Issue** The Introduction lists "contributions of this research" but the list is not explicitly enumerated or summarized. The reader is left to infer the contributions from the subsequent text.
- **Required correction** Clearly enumerate the specific contributions of the work in a dedicated paragraph or list.

## Risk / unsupported claims
- The claim of "at least 9.1% improvement in MCC" over other methods cannot be verified without access to Tables 7 and 8 and the underlying data.
- The claim of "remarkably higher generalization ability" is based on a single independent dataset and lacks statistical support.
- The assertion that one-hot encoding is "more efficient" than word embedding is not quantitatively supported by any runtime or complexity analysis.
- The claim that the fusion approach "will be necessary for sequence-based tasks in genomics" is speculative and not supported by the experimental scope.
- The performance metrics reported in the text (e.g., 86.45% sensitivity, 79.13% specificity, 82.81% accuracy, 0.661 MCC) cannot be independently verified without the corresponding tables and raw predictions.
- The statement that the model "can predict DBPs from sequences accurately and effectively" is a general claim that requires more rigorous evaluation across diverse datasets and conditions.