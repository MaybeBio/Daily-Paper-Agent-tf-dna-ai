## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose EPDRNA, an ensemble classifier combining four machine learning algorithms with soft voting, to predict DNA and RNA binding sites in disease-related proteins. Features include PSSM, physicochemical properties, and amino acid type. The model reportedly achieves AUC values of 0.73 (DNA) and 0.71 (RNA) in 10-fold cross-validation, and recall/precision of 85%/25% (DNA) and 82%/27% (RNA) on independent test sets. A webserver is provided.
- **Visible evidence base** Abstract text only; no dataset details, feature engineering specifics, algorithm identities, cross-validation protocols, or independent test set descriptions are provided
- **Missing materials affecting confidence** Full manuscript, dataset composition and size, exact feature encoding, algorithm names and hyperparameters, independent test set construction, baseline comparisons, statistical significance tests, and webserver implementation details

## Reviewer
- **Overall assessment** The abstract presents a plausible but incompletely supported computational method for a niche but relevant problem. The reported performance metrics are modest and lack context from baselines or statistical validation. Several technical details essential for reproducibility and for assessing the claim of superiority over existing methods are absent. The work may be of interest to the protein bioinformatics community, but the current evidence does not establish the method's utility or novelty beyond what is stated.
- **Who would be interested in the results, and why** Researchers in protein function prediction, particularly those studying DNA and RNA binding proteins in disease contexts. The webserver may be useful for experimentalists seeking candidate binding residues. The ensemble approach may interest method developers in bioinformatics, though the modest performance and lack of comparative benchmarks limit broader appeal.
- **Major strengths** The problem is relevant and under-addressed for disease-related proteins. The ensemble strategy with soft voting is a reasonable approach. The provision of a freely accessible webserver enhances practical utility. The use of multiple feature types (PSSM, physicochemical properties, amino acid type) is standard and sensible.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The model achieves "the best AUC value of 0.73 at the DNA binding sites, and the best AUC value of 0.71 at the RNA binding sites in 10-fold cross validation in the training sets."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The AUC values are reported without any baseline comparison, confidence intervals, or statistical significance testing. It is unclear whether these values represent a meaningful improvement over simple sequence composition or existing predictors. The phrase "best AUC" implies multiple models were tested, but no details on the range or the selection procedure are given.
  - **Why it matters** Without baselines or error estimates, the reported AUC cannot be interpreted as evidence of model effectiveness. A model with AUC around 0.7 may be only marginally better than random for imbalanced binding site prediction, and the claim of a useful predictor is not established.
  - **Resolution test** Provide AUC values for at least one standard baseline (e.g., sequence composition only, or an existing predictor) on the same datasets, with confidence intervals or standard deviations from repeated cross-validation. Report the range of AUC across the four individual algorithms to justify the ensemble.
  
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "The EPDRNA achieved 85% recall rate and 25% precision on the protein-DNA interaction independent test set, and achieved 82% recall rate and 27% precision on the protein-RNA interaction independent test set."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The precision values are very low (25% and 27%), which means the majority of predicted binding sites are false positives. The abstract does not report the corresponding specificity, F1 score, or Matthews correlation coefficient, nor does it explain the threshold used to convert probabilities to binary predictions. The imbalance between recall and precision suggests the model may be biased toward predicting binding sites.
  - **Why it matters** Low precision undermines the practical utility of the webserver for experimentalists, as users would face many false leads. The lack of threshold details and additional metrics prevents assessment of whether the operating point is appropriate or whether the model is well-calibrated.
  - **Resolution test** Report precision-recall curves or F1 scores, specify the decision threshold, and provide specificity or MCC values. Justify the chosen operating point in terms of the intended use case.
  
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** "The dataset used in model was collated from UniProt and PDB database, and PSSM, physicochemical properties and amino acid type were used as features."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The dataset construction is described only in vague terms. No information is given on the number of proteins, the number of binding and non-binding residues, the criteria for selecting disease-related proteins, the redundancy reduction procedure, or the sequence identity threshold. The feature encoding is also unspecified (e.g., window size, normalization, PSSM generation method).
  - **Why it matters** Without these details, the results cannot be reproduced or compared with other methods. Dataset bias or leakage could inflate performance, and the absence of a clear data split protocol raises concerns about overfitting.
  - **Resolution test** Provide a detailed dataset description including counts, redundancy reduction, and train/test split criteria. Specify all feature encoding parameters and the PSSM generation tool.
  
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Originality
  - **Claim pointer** "At present, there are few methods for specifically identifying the binding sites of disease-related protein-DNA and protein-RNA."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not cite or compare with any existing methods for DNA or RNA binding site prediction, whether general or disease-specific. The claim of scarcity is unsubstantiated, and the novelty of the ensemble approach or the disease-specific focus is not demonstrated relative to prior work.
  - **Why it matters** For a methods paper, situating the work within the existing literature is essential to establish contribution. Without comparisons, readers cannot judge whether EPDRNA offers any advantage over established tools.
  - **Resolution test** Include a brief literature review and quantitative comparisons with at least two existing predictors on the same independent test sets.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Abstract wording
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The sentence "In this study, so we combined four machine learning algorithms" contains a grammatical error ("so" is redundant).
  - **Required correction** Revise to "In this study, we combined four machine learning algorithms."
  
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Model description
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract does not name the four machine learning algorithms used in the ensemble.
  - **Required correction** List the four algorithms explicitly in the abstract or methods.
  
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Webserver
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The webserver URL is provided, but no information is given on input format, output interpretation, or availability of the underlying model for local use.
  - **Required correction** Add a brief description of the webserver's functionality and data requirements.
  
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interdisciplinary readership
  - **Affected element** Abstract context
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract does not explain why disease-related proteins are a distinct challenge for binding site prediction, which would help non-specialists understand the motivation.
  - **Required correction** Add one sentence on the biological or structural differences of disease-related proteins that motivate a dedicated model.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of baselines and statistical validation), R1-M2 (incomplete performance metrics and threshold justification), R1-M3 (insufficient dataset and feature details for reproducibility)
- **Assessment against Nature-style criteria** 
  - Originality: The disease-specific focus is a minor differentiator, but the ensemble approach and features are standard. The claim of scarcity of existing methods is unverified. Originality is not clearly established.
  - Scientific importance: The problem is relevant to understanding disease mechanisms, but the modest performance and lack of demonstrated improvement over existing tools limit the potential impact.
  - Interdisciplinary readership: The work is primarily of interest to bioinformatics specialists. The abstract does not frame the findings in a way that would attract a broader biological or clinical audience.
  - Technical soundness: The reported metrics are incomplete and lack statistical context. The dataset and feature descriptions are insufficient for reproducibility. Technical soundness is not established from the abstract.
  - Readability for nonspecialists: The abstract is generally clear but lacks motivation for the disease-specific approach and omits key methodological details that would aid comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially useful tool, but the lack of baselines, incomplete performance reporting, and insufficient methodological detail prevent a positive assessment. The authors should address the major concerns, particularly R1-M1, R1-M2, and R1-M3, before the case for the model's utility can be made.

## Risk / unsupported claims
- The claim that "there are few methods for specifically identifying the binding sites of disease-related protein-DNA and protein-RNA" is unsupported without a literature survey.
- The reported AUC values (0.73 and 0.71) are presented as evidence of model quality but are uninterpretable without baselines or error estimates.
- The independent test set performance (recall 85%/82%, precision 25%/27%) is reported without context on dataset composition or threshold selection, making the practical utility unassessable.
- The statement that EPDRNA "achieved the best AUC value" implies model selection, but the selection process and the performance of individual algorithms are not described.
- The webserver's functionality and the model's generalizability to unseen disease-related proteins are not verifiable from the abstract.