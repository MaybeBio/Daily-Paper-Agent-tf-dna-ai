## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusions) as provided
- **Assessment boundary** Scientific and technical evaluation of the reported method, experimental design, and claims; no assessment of code functionality or reproducibility beyond what is described
- **Shared manuscript claim summary** The authors propose iProtDNA-SMOTE, a graph neural network framework integrating ESM2 protein language model embeddings with GraphSMOTE-based oversampling and GraphSAGE-MLP classification, to predict protein-DNA binding residues from sequence-derived structural information. They report superior performance over existing methods on three independent test sets (TE46, TE129, TE181) using two training sets (TR646, TR573).
- **Visible evidence base** Abstract; Sections 1-4; Tables 1-4 referenced; Figures 1-2 referenced; equations for GraphSAGE aggregation, MLP computation, and focal loss described in text
- **Missing materials affecting confidence** Actual table data (Tables 1-4) not provided; figure contents not visible; no hyperparameter settings; no training details (epochs, learning rate, batch size); no ablation studies; no statistical significance testing; no runtime or computational cost analysis; no code or data availability verification

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely the prediction of protein-DNA binding sites from imbalanced sequence data. The integration of ESM2 embeddings with graph-based oversampling is a reasonable and potentially useful combination. However, the current manuscript has substantial gaps in methodological detail, experimental rigor, and validation depth that prevent full assessment of the claims. The reported performance improvements are modest and lack statistical validation. The writing contains numerous typographical and grammatical errors that impede readability. The work is potentially publishable after major revisions, but the case is not fully established from the provided evidence.

- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics working on protein-nucleic acid interaction prediction, particularly those developing deep learning methods for imbalanced biological datasets. The combination of protein language models with graph neural networks and oversampling strategies may be of interest to those exploring similar hybrid architectures. The public availability of code and datasets could benefit the community, though this could not be verified.

- **Major strengths** 
  1. The problem addressed is of practical importance, and the class imbalance issue is well-recognized in this domain.
  2. The combination of ESM2 embeddings with graph-based oversampling (GraphSMOTE) is a sensible and contemporary approach.
  3. Evaluation on multiple independent test sets from different sources provides some evidence of generalizability.
  4. The use of MCC as a primary metric for imbalanced data is appropriate.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model achieves superior performance over existing methods across all evaluated datasets.
- **Evidence pointer** Tables 2-4 (data not visible in provided material)
- **Concern** The actual numerical results are not visible in the provided material. The reported improvements are described as modest (e.g., 1.7% MCC improvement over CLAPE-DB on TE46), yet no statistical significance testing is reported. It is unclear whether these differences are meaningful or within the range of random variation. Additionally, no confidence intervals or variance estimates are provided.
- **Why it matters** Without statistical validation, the central claim of superiority over existing methods cannot be substantiated. Modest improvements on a single split of each dataset may not reflect genuine algorithmic advantage.
- **Resolution test** Provide full tables with all metrics, include statistical significance testing (e.g., paired tests across multiple runs or cross-validation folds), and report confidence intervals or standard deviations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The GraphSMOTE-based oversampling strategy effectively addresses class imbalance and enhances model generalization.
- **Evidence pointer** Section 2.2, Procedure III; Section 3
- **Concern** No ablation study is presented to isolate the contribution of the GraphSMOTE component. It is unclear whether the reported performance is due to the oversampling strategy, the ESM2 embeddings, the graph construction, or the specific classifier architecture. The claim that GraphSMOTE "enhances model's generalization and specificity" is not directly supported by any comparative experiment.
- **Why it matters** The novelty of the method rests substantially on the integration of GraphSMOTE with ESM2 features. Without ablations, the specific contribution of each component remains unknown, and the design choices cannot be justified.
- **Resolution test** Include ablation experiments removing or replacing each key component (e.g., no oversampling, random oversampling, SMOTE without graph structure, different backbone GNN) and report the resulting metrics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The model is fully described and reproducible from the manuscript.
- **Evidence pointer** Sections 2.2-2.4
- **Concern** Critical implementation details are missing. The number of GraphSAGE layers, hidden dimensions, dropout rates, learning rate, optimizer, training epochs, batch size, and the specific ESM2 variant used (the text mentions ESM2_t36_3B_UR50D but the abstract and introduction refer to "ESM2" generically) are not specified. The oversampling ratio for GraphSMOTE is not stated. The graph construction threshold is given (8 angstroms) but the source of 3D structures (AlphaFold3 predictions vs experimental structures) is not clarified for each dataset.
- **Why it matters** Reproducibility is a core requirement for computational biology methods. Without these details, other researchers cannot implement or fairly compare against the method.
- **Resolution test** Provide a complete hyperparameter table, training configuration, and clarify the structure source for each dataset. Consider releasing the full training configuration in the code repository.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The method outperforms existing state-of-the-art approaches including those using contrastive learning and pre-trained language models.
- **Evidence pointer** Section 3.1-3.2
- **Concern** The comparison is limited to a subset of existing methods. Several recent deep learning approaches for protein-DNA binding prediction (e.g., methods using different architectures or larger pre-trained models) are not included. The choice of baselines appears somewhat arbitrary, and the most recent state-of-the-art may not be represented.
- **Why it matters** The claim of outperforming "existing methods" requires comparison against the current best-performing approaches. An incomplete baseline set weakens the significance of the reported improvements.
- **Resolution test** Expand the comparison to include more recent and diverse baseline methods, or justify the exclusion of specific approaches.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The model demonstrates "high reliability and precision" for predicting protein-DNA binding sites.
- **Evidence pointer** Section 3; Abstract
- **Concern** The reported precision values are relatively low (e.g., 0.583 on TE46, 0.497 on TE129, 0.303 on TE181), indicating a substantial number of false positives. The recall values are also modest (0.363 on TE46). The claim of "high reliability" is not well supported by these absolute performance levels, even if they are improvements over baselines.
- **Why it matters** For practical applications, users need to know the expected error rates. Overstating reliability could mislead potential users of the method.
- **Resolution test** Moderate the language used to describe performance, and discuss the practical implications of the observed precision-recall tradeoff.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract and throughout
- **Evidence pointer** Abstract, Section 1
- **Issue** The abstract states the model "utilizes non-equilibrium graph neural networks" which is not a standard term and is not defined or used consistently in the main text. The term "unbalanced graph data" is also used imprecisely.
- **Required correction** Use standard terminology consistently. If "non-equilibrium" refers to the oversampling approach, clarify this. Otherwise, replace with standard terms such as "class-imbalanced graph data."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 2.2, Procedure II
- **Evidence pointer** "If the distance between the ∁α atoms of two residues is less than this threshold"
- **Issue** The symbol "∁α" appears to be a typographical error. The standard notation is "Cα" (alpha carbon).
- **Required correction** Correct the symbol to "Cα" throughout.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.4
- **Evidence pointer** Equations for GraphSAGE and MLP are referenced but not shown in the provided text
- **Issue** The equations are described in words but the actual mathematical formulations are not visible in the provided material. This makes it difficult to assess the technical correctness of the implementation.
- **Required correction** Ensure all equations are properly typeset and visible in the final manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 2.1
- **Evidence pointer** Dataset descriptions
- **Issue** The text states "five benchmark datasets" but then lists TR646, TE46, TR573, TE129, and TE181, which are five datasets total (two training, three testing). The phrasing is slightly confusing.
- **Required correction** Clarify that there are two training datasets and three independent test datasets.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Throughout
- **Evidence pointer** Multiple locations
- **Issue** Numerous typographical and grammatical errors are present, including "duo to" (should be "due to"), "Thes comparisons" (should be "These comparisons"), "through evaluation" (should be "thorough evaluation"), "capable of capture" (should be "capable of capturing"), and inconsistent use of "model's" vs "models".
- **Required correction** Thorough proofreading is needed throughout the manuscript.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.3
- **Evidence pointer** Description of ESM2_t36_3B_UR50D
- **Issue** The choice of this specific ESM2 variant (3B parameters) is not justified. Smaller or larger variants may offer different tradeoffs between performance and computational cost.
- **Required correction** Briefly justify the choice of model size or include a comparison with other ESM2 variants.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 2.4
- **Evidence pointer** Focal loss description
- **Issue** The focal loss parameters (alpha and gamma) are not specified. These are critical hyperparameters that significantly affect performance on imbalanced data.
- **Required correction** Report the values used for alpha and gamma, and ideally include a sensitivity analysis.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3
- **Evidence pointer** Comparison tables
- **Issue** The comparison tables are referenced but not visible in the provided material. It is unclear whether all baselines were evaluated under identical conditions (e.g., same cross-validation protocol, same feature representation).
- **Required correction** Ensure tables are complete and include a description of the evaluation protocol used for all methods.

## Risk / unsupported claims
- The claim of "superior predictive accuracy" and "unwavering capacity for generalization" is not fully supported without statistical significance testing and confidence intervals.
- The specific contribution of GraphSMOTE to the reported performance is unsubstantiated without ablation studies.
- The claim that the model "effectively addresses the class imbalance issue" is not directly demonstrated through comparison with alternative imbalance-handling strategies.
- The statement that ESM2 embeddings "comprehensively capture information from protein sequences" is an overstatement not directly tested in this work.
- The claim of "high reliability and precision" is not supported by the reported absolute metric values.
- The reproducibility of the method cannot be assessed from the provided material due to missing implementation details.
- The performance comparison may not reflect the true state of the art if recent methods are omitted.