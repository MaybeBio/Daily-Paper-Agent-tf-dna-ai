## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose a sequence-to-sequence deep learning model for predicting protein-DNA binding residues. The model accepts entire protein sequences of variable length and employs two modules, a Transformer Encoder Block for global feature extraction and a Feature Extracting Block for local feature extraction, in a hierarchical manner. The authors report that comparisons on two benchmark datasets, PDNA-543 and PDNA-41, demonstrate the effectiveness of their method.
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or dataset descriptions are provided beyond dataset names
- **Missing materials affecting confidence** Full manuscript, all figures and tables, model architecture details, hyperparameter settings, training and evaluation protocols, baseline method descriptions, and any statistical significance tests

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially useful contribution to the field of protein-DNA binding residue prediction. The proposed seq2seq architecture with hierarchical feature extraction is a reasonable design choice given the limitations of sliding window approaches. However, the abstract provides no quantitative evidence, no comparison details, and no methodological specifics that would allow an independent assessment of the claims. The core assertion of effectiveness is unsupported by the visible material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function annotation, protein-DNA interaction prediction, and deep learning applications in genomics. Researchers developing sequence-based prediction tools for other biomolecular interactions may also find the hierarchical feature extraction approach relevant.
- **Major strengths** The motivation is clearly stated and addresses a real limitation of existing two-step sliding window methods. The proposed architecture is conceptually sound, combining global and local feature extraction in a single end-to-end model. The use of a seq2seq framework to handle variable-length sequences is an appropriate design choice.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: The hierarchical combination of Transformer and local feature extraction blocks is a reasonable incremental contribution, but the abstract does not establish novelty relative to existing deep learning methods for this task. Scientific importance: Protein-DNA binding prediction is a relevant problem, but the abstract does not demonstrate a meaningful advance over the state of the art. Interdisciplinary readership: The work is primarily of interest to computational biology specialists; the abstract does not frame the findings for a broader audience. Technical soundness: Cannot be assessed from the abstract alone; no architectural details, training procedures, or evaluation metrics are provided. Readability for nonspecialists: The abstract is generally clear, though the module names are introduced without functional explanation.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient quantitative or methodological detail to support the claim of effectiveness. A full manuscript with detailed results and comparisons would be required for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that comparison results on PDNA-543 and PDNA-41 prove the effectiveness of their method in identifying protein-DNA binding residues.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that comparison results prove effectiveness but provides no numerical results, no performance metrics, no baseline methods, and no statistical analysis. No values for sensitivity, specificity, precision, recall, F1-score, Matthews correlation coefficient, or area under the ROC curve are reported.
- **Why it matters** A claim of effectiveness in a prediction task requires quantitative evidence with appropriate evaluation metrics and comparison against existing methods. Without any numbers, the claim cannot be verified or contextualized relative to prior work.
- **Resolution test** Provide performance metrics for the proposed method and all baselines on both datasets, including confidence intervals or statistical significance tests where applicable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors describe a seq2seq model with two modules, Transformer Encoder Block and Feature Extracting Block, for hierarchical feature extraction.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract provides no details on the architecture, such as the number of layers, hidden dimensions, attention heads, activation functions, or how the Feature Extracting Block is implemented. No information is given on training data, loss function, optimization algorithm, learning rate, or regularization strategies.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without architectural and training details, other researchers cannot implement or validate the proposed approach, and reviewers cannot assess whether the design choices are sound.
- **Resolution test** Provide a complete description of the model architecture, training procedure, and hyperparameters in the full manuscript.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative rigor
- **Claim pointer** The authors state that most current state-of-the-art methods are two-step approaches with sliding windows and that their method improves efficiency and ease of use.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not identify which state-of-the-art methods were compared, what their reported performance is, or how the comparison was conducted. The claim of improved efficiency and ease of use is not supported by any runtime measurements or usability analysis.
- **Why it matters** Demonstrating an advance requires a fair and comprehensive comparison with existing methods, including both performance and practical considerations. Without this, the claimed advantage cannot be established.
- **Resolution test** List all baseline methods, their sources, and their performance on the same datasets. Provide runtime or computational cost comparisons if efficiency is claimed.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Module descriptions
- **Evidence pointer** Abstract, location not provided
- **Issue** The names "Transformer Encoder Block" and "Feature Extracting Block" are introduced without explaining what each block does functionally beyond the general statement of global and local feature extraction.
- **Required correction** Provide a brief functional description of each block in the abstract or ensure the full manuscript clearly defines their roles.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Dataset context
- **Affected element** Benchmark datasets
- **Evidence pointer** Abstract, location not provided
- **Issue** The datasets PDNA-543 and PDNA-41 are named but not described. Readers unfamiliar with these benchmarks will not know their size, composition, or how they were constructed.
- **Required correction** Add a sentence describing the datasets, including the number of proteins, the number of binding and non-binding residues, and any relevant construction criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Effectiveness"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "effectiveness" is used without specifying which metric defines it. Different metrics can lead to different conclusions about model quality.
- **Required correction** Specify the primary evaluation metric or metrics used to determine effectiveness.

## Risk / unsupported claims
- The claim that the proposed method is effective on PDNA-543 and PDNA-41 is unsupported by any quantitative data in the visible material.
- The claim that the method improves efficiency and ease of use relative to existing two-step approaches is unsupported by any measurements or analysis.
- The claim that the hierarchical feature extraction approach improves recognition capability is not verifiable without architectural details and ablation studies.
- The general statement that most current state-of-the-art methods are two-step sliding window approaches is presented without citations or a systematic survey.