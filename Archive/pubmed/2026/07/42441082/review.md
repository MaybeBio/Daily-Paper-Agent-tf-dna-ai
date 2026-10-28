## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present caRBP-Pred, a deep learning framework combining protein language model (ProtT5-XL) embeddings with a CNN-BiLSTM architecture, for the prediction of chromatin-associated RNA-binding proteins (caRBPs) in mice. They report competitive performance over baseline models, identify 41 high-confidence caRBP candidates in the mouse proteome, and provide motif analysis suggesting electrostatic and phase-separation mechanisms for chromatin recruitment.
- **Visible evidence base** Main text, Tables 1-6 (referenced), Figures 1-4 (referenced), Supplementary Figures S1-S3 and Tables S1-S5 (referenced)
- **Missing materials affecting confidence** Figures and tables are referenced but not provided in the submitted text. Supplementary materials are referenced but not included. Dataset construction details from the original source [14] are not fully described. Code availability is stated but not verified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant gap in the field by developing a specialized predictor for chromatin-associated RNA-binding proteins, a functional subset distinct from generic DNA/RNA-binding proteins. The integration of a protein language model with a CNN-BiLSTM architecture is a reasonable methodological choice, and the reported performance improvements over baseline models are encouraging. However, the manuscript has several significant limitations that affect the strength of the claims. The evaluation is based on a single dataset from one source, the external validation is limited in scope, and the biological validation of predicted candidates relies on database annotations rather than experimental confirmation. The motif analysis provides some mechanistic insight but is largely speculative. The technical soundness is generally adequate, but the lack of detailed hyperparameter reporting, the modest performance metrics on imbalanced data, and the absence of comparison with more recent state-of-the-art methods weaken the case. The manuscript would benefit from more rigorous benchmarking, additional validation datasets, and clearer presentation of the model's practical utility.

- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics working on protein function prediction, particularly those focused on RNA-binding proteins and chromatin biology. The paper may also interest experimental biologists studying transcriptional regulation and chromatin organization who could use the tool for candidate prioritization. The methodological approach of combining pLMs with hybrid neural architectures may appeal to machine learning practitioners in the protein domain.

- **Major strengths** 
  1. Addresses a specific and under-served prediction task (caRBPs) rather than generic RBPs, filling a clear gap in the literature.
  2. The integration of ProtT5-XL embeddings with CNN-BiLSTM is a sensible and modern approach that leverages both evolutionary information and local sequence patterns.
  3. The authors provide a practical inference pipeline with a conservative threshold for high-confidence predictions, which is useful for real-world screening applications.
  4. The motif analysis provides biologically interpretable results that connect predictions to potential mechanisms (electrostatic interactions, phase separation).
  5. The manuscript is generally well-written and the methodology is described with sufficient detail for reproduction.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and representativeness
- **Claim pointer** The authors claim that caRBP-Pred is a reliable predictor for caRBPs based on training and evaluation on a dataset derived from a single source [14].
- **Evidence pointer** Section "Dataset construction and preprocessing", Section "External validation on the TEST474 dataset"
- **Concern** The entire model is trained and evaluated on data from a single study [14], which limits the generalizability of the findings. The dataset of 349 caRBPs and 1,445 non-caRBPs is relatively small, and the positive class is heavily imbalanced. The external validation on TEST474 includes only 8 DNA/RNA-binding proteins, which is a very small sample for assessing the model's ability to distinguish caRBPs from other nucleic acid-binding proteins. The authors do not demonstrate performance on independent datasets from different experimental sources or organisms.
- **Why it matters** A predictor trained on a single dataset may overfit to dataset-specific biases and may not generalize to other experimental conditions, cell types, or organisms. The small external validation set, particularly for the most relevant comparison group (DNA/RNA-binding proteins), does not provide sufficient statistical power to support the claim of reliable discrimination.
- **Resolution test** The authors should validate caRBP-Pred on additional independent datasets from different sources, ideally including data from other organisms or experimental methods. They should also expand the external validation to include a larger set of DNA/RNA-binding proteins. If additional datasets are not available, the limitations should be explicitly acknowledged and the claims moderated accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Performance metrics and benchmarking
- **Claim pointer** The authors claim that pLM-CNN-BiLSTM "significantly improved performance" over baseline models, with AUC = 0.83, AP = 0.58, F1 = 0.52, and MCC = 0.41 for full-length protein sequences.
- **Evidence pointer** Section "The pre-trained pLM substantially enhances caRBP prediction for full-length sequences", Tables 4-5
- **Concern** The reported performance metrics, while improved over baselines, are still modest in absolute terms. An AUC of 0.83 and AP of 0.58 indicate substantial misclassification rates. The authors do not report confidence intervals or statistical significance testing for the differences between models, despite mentioning "statistical significance testing" in the Methods. The comparison with existing DRBP predictors is indirect and limited, as the authors acknowledge that source code was not available and they used web servers with potentially different evaluation protocols. No comparison with more recent deep learning methods for protein function prediction is provided.
- **Why it matters** The claim of "competitive predictive performance" requires rigorous benchmarking against state-of-the-art methods under identical conditions. Without statistical significance testing and direct comparisons, it is unclear whether the observed improvements are meaningful or within the range of random variation. The modest absolute performance also raises questions about the practical utility of the tool for high-throughput screening.
- **Resolution test** The authors should provide confidence intervals for all reported metrics, perform statistical significance testing (e.g., DeLong test for AUC, bootstrap for AP/F1/MCC), and include direct comparisons with more recent and relevant methods under identical training and evaluation protocols. If direct comparison is not possible, this should be clearly stated as a limitation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation and interpretability
- **Claim pointer** The authors claim that "enriched motifs in chromatin-contact peptides reveal electrostatic and phase-separation mechanisms for chromatin recruitment" and that predicted candidates are "biologically plausible."
- **Evidence pointer** Section "Results", Section "Discussion", Figure S2
- **Concern** The biological validation of predicted candidates relies entirely on database annotations (COMPARTMENTS, InterProScan) rather than experimental evidence. The motif analysis is based on a small number of positive peptides (n = 822, reduced to 45 after redundancy removal at 40% similarity), which limits the statistical power of motif discovery. The connection between the identified motifs and specific mechanisms (electrostatic interactions, phase separation) is speculative and not directly tested. The claim that 61% of candidates show chromatin-related localization is based on database annotations that may be incomplete or biased.
- **Why it matters** The biological relevance of the predictions is a key selling point of the manuscript. Without experimental validation or at least stronger computational evidence (e.g., structural modeling, evolutionary conservation analysis), the mechanistic claims remain speculative. The small number of unique peptides after redundancy filtering raises concerns about the robustness of the motif analysis.
- **Resolution test** The authors should either provide experimental validation for a subset of predicted candidates (e.g., chromatin immunoprecipitation, immunofluorescence) or substantially moderate the mechanistic claims. They should also report the motif analysis on the full set of peptides before redundancy filtering and provide statistical significance for motif enrichment.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity and reproducibility
- **Claim pointer** The authors state that the model uses "hybrid Dice-focal loss function" and that "the optimal model was selected through extensive architecture comparison."
- **Evidence pointer** Section "Model training parameters", Section "Model architecture and ablation study"
- **Concern** The manuscript lacks sufficient detail on several methodological aspects. The hyperparameter search space is not described, the final hyperparameter values are not reported, and the criteria for "optimal model" selection are vague. The handling of class imbalance beyond the loss function is not described. The threshold of 0.7 for high-confidence predictions is arbitrary and not justified. The computational resources required for training and inference are not reported.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without detailed hyperparameter reporting and clear model selection criteria, other researchers cannot replicate or build upon this work. The arbitrary threshold also affects the comparability of results across studies.
- **Resolution test** The authors should provide a complete description of the hyperparameter search, final hyperparameters, model selection criteria, and computational requirements. They should also justify the choice of threshold or provide a sensitivity analysis showing how performance varies with threshold.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Presentation and clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction do not clearly distinguish caRBPs from other chromatin-associated proteins or from RBPs that bind chromatin indirectly through RNA. The definition of caRBPs could be more precise.
- **Required correction** Provide a clear operational definition of caRBPs early in the manuscript, including how they differ from general RBPs and chromatin-binding proteins.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data description
- **Affected element** Dataset construction
- **Evidence pointer** Section "Dataset construction and preprocessing"
- **Issue** The source of the negative set (non-caRBPs) is not described in detail. It is unclear whether these are experimentally verified non-caRBPs or simply proteins not annotated as caRBPs.
- **Required correction** Clarify the criteria for inclusion in the negative set and discuss potential label noise.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evaluation methodology
- **Affected element** Cross-validation
- **Evidence pointer** Section "Dataset construction and preprocessing"
- **Issue** The use of "stratified group K-fold cross-validation" is mentioned, but the stratification variable is not specified. It is unclear whether stratification is based on the class label or some other property.
- **Required correction** Specify the stratification variable and explain why it was chosen.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** External validation
- **Affected element** TEST474 evaluation
- **Evidence pointer** Section "External validation on the TEST474 dataset"
- **Issue** The TEST474 dataset is described as having three groups, but the criteria for group assignment are not fully described. The small number of DNA/RNA-binding proteins (n = 8) is a concern.
- **Required correction** Provide more detail on the TEST474 dataset composition and discuss the limitations of the small sample size.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Motif analysis
- **Evidence pointer** Section "Results"
- **Issue** The motif analysis is presented as supporting electrostatic and phase-separation mechanisms, but the connection between the specific motifs and these mechanisms is not well-developed.
- **Required correction** Provide additional context or references to support the mechanistic interpretation of the identified motifs.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Discussion
- **Evidence pointer** Section "Discussion"
- **Issue** The Discussion section is somewhat repetitive of the Results and does not fully address the limitations of the study.
- **Required correction** Streamline the Discussion and add a more comprehensive limitations paragraph.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data
- **Evidence pointer** Section "Data Availability"
- **Issue** The GitHub repository is mentioned, but it is not clear whether the training data, evaluation scripts, and trained model weights are all included.
- **Required correction** Specify exactly what is included in the repository and provide a version/commit identifier.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** References
- **Affected element** Reference list
- **Evidence pointer** Not applicable
- **Issue** The reference list is not provided in the submitted text, so it is not possible to assess the currency and completeness of the literature review.
- **Required correction** Ensure that the reference list includes recent work on pLMs for protein function prediction and on caRBPs specifically.

## Risk / unsupported claims
- The claim that caRBP-Pred is "the first computational tool specifically designed for protein-level caRBP prediction" cannot be fully verified without a comprehensive literature search, but it appears plausible based on the cited literature.
- The claim that enriched motifs "reveal electrostatic and phase-separation mechanisms" is not directly supported by experimental evidence and should be considered speculative.
- The claim that 61% of predicted candidates show chromatin-related localization is based on database annotations and may be subject to annotation bias.
- The claim of "competitive predictive performance" is not fully supported due to the lack of direct comparisons with state-of-the-art methods and the absence of statistical significance testing.
- The performance of the model on the external TEST474 dataset, particularly for the DNA/RNA-binding group (n = 8), is based on a very small sample and should be interpreted with caution.
- The biological plausibility of the 5 predicted candidates from the "RNA-binding only" group is argued based on domain analysis but is not experimentally validated.