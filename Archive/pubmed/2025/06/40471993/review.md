## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) without figures, tables, or supplementary files
- **Assessment boundary** Scientific claims, methodological soundness, and interpretability of the deep learning approach as described in the provided text
- **Shared manuscript claim summary** The authors present TTIRI, a deep learning model based on DNABERT-2, to identify transcriptional infidelity regions at nucleotide resolution in an allopolyploid line derived from goldfish and common carp hybrids. They claim accurate prediction at sequence and subregion levels, and use interpretability analyses to link position-specific motifs, transcription factor families, and classes to transcriptional infidelity.
- **Visible evidence base** Text descriptions of model architecture, training data construction, evaluation metrics, and interpretability methods; references to figures and supplementary data not visible in the provided material
- **Missing materials affecting confidence** Figures 1-4, all supplementary files (including Supplementary Data 1-3 and Supplementary File sections), detailed numerical results, model performance tables, and code repository contents

## Reviewer
- **Overall assessment** The manuscript addresses an interesting and potentially important problem: applying deep learning to understand transcriptional infidelity in a unique allopolyploid vertebrate system. The two-layer prediction architecture and the interpretability framework are reasonable methodological choices. However, the provided text lacks critical quantitative details, validation against alternative approaches, and biological validation of the interpretability findings. The claims of "nucleotide resolution" prediction are not fully supported by the described subregion-level approach, which appears to operate at a coarser granularity. The manuscript would benefit from clearer presentation of performance metrics, baseline comparisons, and independent validation of the biological conclusions.
- **Who would be interested in the results, and why** Researchers studying transcriptional fidelity mechanisms, RNA editing, and transcriptional regulation in polyploid vertebrates. The deep learning community working on genomic sequence models may also find the application of DNABERT-2 to a new task of interest. The allopolyploid fish system is a unique model that could attract evolutionary biologists studying polyploidization consequences.
- **Major strengths** 1) The problem is novel and biologically significant, particularly in the context of allopolyploid vertebrates. 2) The two-layer prediction architecture (sequence-level plus subregion-level) is a thoughtful design that addresses different granularities of prediction. 3) The interpretability framework using transcription factor motifs is a valuable approach to move beyond black-box predictions. 4) The use of a pre-trained genomic language model (DNABERT-2) is appropriate and leverages recent advances in the field.
- **Major Concerns** See detailed items below.
- **Who would be interested in the results, and why** Researchers studying transcriptional fidelity mechanisms, RNA editing, and transcriptional regulation in polyploid vertebrates. The deep learning community working on genomic sequence models may also find the application of DNABERT-2 to a new task of interest. The allopolyploid fish system is a unique model that could attract evolutionary biologists studying polyploidization consequences.
- **Major strengths** 1) The problem is novel and biologically significant, particularly in the context of allopolyploid vertebrates. 2) The two-layer prediction architecture (sequence-level plus subregion-level) is a thoughtful design that addresses different granularities of prediction. 3) The interpretability framework using transcription factor motifs is a valuable approach to move beyond black-box predictions. 4) The use of a pre-trained genomic language model (DNABERT-2) is appropriate and leverages recent advances in the field.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The application of deep learning to transcriptional infidelity prediction is novel, though the underlying methods are largely borrowed from existing tools. Scientific importance: The biological questions are important, but the current evidence does not establish a clear mechanistic advance. Interdisciplinary readership: The work bridges deep learning and molecular biology, which could appeal to a broad audience if the claims are properly supported. Technical soundness: The described methods are generally reasonable, but critical validation details are missing. Readability for nonspecialists: The text is generally accessible, though some methodological sections assume familiarity with deep learning concepts.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the core claims require substantial additional evidence and clarification.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model "can accurately identify transcriptional infidelity sequences at the nucleotide resolution" and offers "subregional predictions for these infidelity-prone DNA sequences."
- **Evidence pointer** Results section "T TIRI model accurately predicts transcriptional infidelity regions"; Figure 2 (not visible)
- **Concern** The claim of "nucleotide resolution" is not supported by the described methodology. The model operates at two levels: sequence-level (200 nt windows) and subregion-level (approximately two subregions per sequence when token count is 20). Neither of these constitutes nucleotide resolution. The subregion-level prediction divides a 200 nt sequence into approximately two parts, meaning each subregion is roughly 100 nt. This is far from nucleotide resolution. The manuscript conflates the resolution of the input sequence (nucleotides) with the resolution of the prediction (subregion-level). This is a fundamental mischaracterization of the model's capability.
- **Why it matters** The central claim of the manuscript is that the model achieves nucleotide-resolution prediction. If this is not accurate, the contribution is significantly diminished, and the title itself is misleading. The distinction between sequence-level, subregion-level, and nucleotide-level prediction is critical for understanding the model's actual utility.
- **Resolution test** The authors must clarify the exact resolution of predictions. If the model predicts at subregion level, they should describe the average size of subregions in nucleotides and avoid claiming nucleotide resolution. Alternatively, if they have a mechanism for nucleotide-level prediction, they must describe it explicitly and provide performance metrics at that resolution.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model achieves "an AUROC of ~0.928 in sequence-level prediction and an AUPRC of ~0.937 in subregional-level prediction."
- **Evidence pointer** Results section "T TIRI model accurately predicts transcriptional infidelity regions"; Figure 2 (not visible)
- **Concern** The performance metrics are reported without any comparison to baseline methods, ablation studies, or statistical significance testing. The manuscript states that DNABERT-2 "has demonstrated superior performance over baseline machine learning models" in other contexts, but this does not establish that the specific fine-tuned model outperforms simpler approaches for this task. Without baselines such as k-mer frequency models, position-specific scoring matrices, or simpler neural architectures, the claimed accuracy cannot be evaluated. Additionally, the AUPRC value is reported for a highly imbalanced subregion-level task, but the baseline prevalence is not stated, making it impossible to interpret the AUPRC value meaningfully.
- **Why it matters** A deep learning model's value is determined by its performance relative to existing or simpler alternatives. Without baselines, the reader cannot assess whether the complexity of the model is justified. The AUPRC value is also uninterpretable without knowing the class imbalance ratio.
- **Resolution test** The authors should provide performance comparisons against at least one or two baseline methods (e.g., logistic regression on k-mer frequencies, a simple CNN). They should also report the class imbalance ratio for the subregion-level task and provide confidence intervals or statistical tests for the reported metrics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The interpretability analysis reveals "the distribution of position-specific transcription factor families and classes that influence transcriptional infidelity in this line."
- **Evidence pointer** Results section "Quantifying the contribution of position-specific motifs to predicting transcriptional infidelity"; Figure 3 (not visible)
- **Concern** The interpretability findings are presented as biologically meaningful, but there is no independent validation. The authors identify transcription factor families and classes with high importance scores, but they do not validate these predictions experimentally or through comparison with known regulatory mechanisms. For example, the claim that the HD-ZF factors family shows high importance in the -40 to -60 nt region is not supported by any orthogonal evidence. The manuscript also does not discuss whether these transcription factors are expressed in the relevant tissue or whether their binding sites are enriched in regions of transcriptional infidelity compared to control regions.
- **Why it matters** The biological conclusions are the primary contribution beyond the technical model. Without validation, the interpretability results remain speculative. The authors need to demonstrate that the identified transcription factors are biologically relevant to transcriptional infidelity in this system.
- **Resolution test** The authors should provide at least one form of validation: (a) comparison with known transcriptional infidelity-associated motifs from the literature, (b) experimental validation of at least one predicted transcription factor binding event, or (c) enrichment analysis showing that the identified motifs are significantly overrepresented in infidelity regions compared to matched control regions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The training data consists of 3,610,001 transcriptional infidelity sites from F1 generation kidney cells, with 118,702 sites exhibiting multiple types of infidelity.
- **Evidence pointer** Methods section "Source of transcriptional infidelity site data"
- **Concern** The description of the training data is insufficient. The manuscript does not specify how the positive and negative samples were balanced, how the 10,000 samples per class were selected (random sampling is mentioned, but the seed and reproducibility details are absent), or how the train/validation/test split was stratified. More critically, the manuscript does not describe the genomic distribution of the infidelity sites. If the sites are clustered in specific genomic regions, the model may be learning regional biases rather than sequence determinants. The manuscript also does not state whether the negative samples were matched for genomic context (e.g., same genes, similar expression levels).
- **Why it matters** Data construction directly affects model validity. If the positive and negative samples are not well-matched, the model may learn confounding features. The lack of detail prevents replication and assessment of potential biases.
- **Resolution test** The authors should provide a detailed description of the data construction process, including the genomic distribution of infidelity sites, the criteria for selecting negative samples, and the exact sampling procedure. They should also discuss potential confounding factors and how they were addressed.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model uses DNABERT-2 with a two-layer prediction architecture, and the subregion-level prediction is optimized using a weighted binary cross-entropy loss.
- **Evidence pointer** Methods section "Model architecture"
- **Concern** The manuscript does not provide sufficient details on the model training procedure. Key hyperparameters such as learning rate, batch size, number of epochs, optimizer choice, and early stopping criteria are not reported. The manuscript also does not describe how the subregion-level labels were generated from the infidelity site data. Specifically, if a 200 nt sequence contains multiple infidelity sites, how are the subregion labels assigned? The description of the pooling mechanism (max and average pooling with concatenation) is also unclear regarding how the final subregion predictions are derived and how the number of subregions is determined.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without training details and clear label construction, other researchers cannot replicate or build upon this work. The ambiguity in subregion label generation also raises questions about the validity of the subregion-level evaluation.
- **Resolution test** The authors should provide complete training hyperparameters, a clear description of how subregion labels were constructed from infidelity sites, and a detailed explanation of the pooling and prediction mechanism. Ideally, they should also release the training code and configuration files.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Title
- **Evidence pointer** Title
- **Issue** The title states "at nucleotide resolution" but the model operates at sequence and subregion levels. This is misleading.
- **Required correction** Revise the title to accurately reflect the resolution of predictions, such as "at subregion resolution" or remove the resolution claim.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Model evaluation"
- **Evidence pointer** Methods section "Model evaluation"
- **Issue** The choice of AUROC for sequence-level and AUPRC for subregion-level is not justified. The manuscript states AUROC is appropriate for balanced datasets, but does not explain why AUPRC is preferred for the subregion-level task beyond mentioning class imbalance.
- **Required correction** Provide a brief justification for the metric choices, including the class imbalance ratio for the subregion-level task.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Quantifying the contribution of position-specific motifs"
- **Evidence pointer** Results section "Quantifying the contribution of position-specific motifs"
- **Issue** The description of the three analytical approaches (top individual sites, cumulative importance scores, positive importance across all sites) is somewhat confusing. The distinction between these approaches and their respective figures is not entirely clear from the text.
- **Required correction** Clarify the methodology for each approach and explicitly state what each panel in Figure 3 represents.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address potential limitations of the study, such as the use of a single tissue type, the lack of independent validation, or the potential for confounding by genomic context.
- **Required correction** Add a limitations paragraph acknowledging these issues and discussing their potential impact on the conclusions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The manuscript states that data and code are available at a GitHub repository, but the repository contents are not described. It is unclear whether the training data, model weights, and evaluation scripts are included.
- **Required correction** Provide a brief description of the repository contents and ensure that all necessary data and code for replication are included.

## Risk / unsupported claims
- The claim of "nucleotide resolution" prediction is unsupported by the described methodology, which operates at sequence and subregion levels.
- The reported performance metrics (AUROC ~0.928, AUPRC ~0.937) cannot be evaluated without baseline comparisons and class imbalance information.
- The biological significance of the identified transcription factor families and classes is asserted without independent validation.
- The statement that elevated transcriptional infidelity "could lead to reduced proteostasis and affect various biological processes" is presented as established, but the cited evidence is not provided in the text.
- The claim that the model provides "new insights into the deeper determinants of transcriptional infidelity" is not supported by mechanistic or experimental evidence.