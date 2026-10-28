## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full manuscript, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose NoAS-DS, a neural architecture search method tailored for sequence-based classification tasks, specifically applied to transcription factor binding site (TFBS) and RNA-binding protein (RBP) prediction. The method combines convolutional and LSTM layers in a hybrid architecture search, reports high accuracy outperforming other models on TFBS and RBP datasets, and claims transfer learning capability to other DNA datasets of similar nature.
- **Visible evidence base** Abstract text only; no quantitative results, dataset descriptions, baseline comparisons, or implementation details are available
- **Missing materials affecting confidence** Full manuscript, experimental setup, dataset specifications, performance metrics, baseline model details, statistical significance tests, and any figures or tables

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially useful contribution to neural architecture search for DNA sequence classification. The motivation is clear, and the hybrid convolution-LSTM approach is a reasonable design choice. However, the abstract lacks quantitative evidence, detailed methodology, and rigorous comparison to existing methods. The claims of high accuracy and generalization are not substantiated with specific numbers or statistical analysis. The contribution's novelty relative to existing NAS methods for genomics is not clearly articulated. The case for the method's effectiveness is currently not established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in computational genomics, particularly those working on transcription factor binding site prediction, RNA-protein interaction modeling, and deep learning applications to DNA sequence analysis. The work may also interest the NAS community focused on non-image domains, as it addresses a gap in architecture search for sequence data.
- **Major strengths** The problem is well-motivated, addressing a real limitation of existing NAS methods that are predominantly designed for image classification. The hybrid convolution-LSTM architecture is a sensible choice for sequence-based tasks, as it combines local feature extraction with temporal dependency modeling. The proposed transfer learning aspect is a practical consideration that could enhance the method's utility.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: The hybrid NAS approach for DNA sequence classification is a reasonable incremental contribution, but the abstract does not clearly differentiate it from existing NAS methods for genomics. Scientific importance: The application to TFBS and RBP prediction is relevant, but the abstract does not demonstrate a significant advance over current state-of-the-art. Interdisciplinary readership: The work bridges machine learning and genomics, which could attract a broad audience, but the abstract is too technical and lacks context for nonspecialists. Technical soundness: The abstract provides insufficient detail to assess the methodology's rigor, including search strategy, hyperparameter selection, and evaluation protocols. Readability for nonspecialists: The abstract assumes familiarity with NAS, TFBS, and RBP terminology, and the writing is dense without clear explanations of key concepts.
- **Recommendation posture** Currently not established from the provided evidence. The abstract shows promise, but the lack of quantitative results and methodological detail prevents a supportive recommendation. The authors should provide a full manuscript with comprehensive experimental validation before the case can be assessed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims "high accuracy results on TFBS and RBP datasets which outperformed other models in TF-DNA binding prediction tasks."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract provides no quantitative performance metrics, such as accuracy, AUC, F1-score, or precision-recall values, to support the claim of high accuracy and outperformance. No specific dataset names, sizes, or train-test splits are mentioned. Without numerical results and a description of the comparison baselines, the claim cannot be evaluated.
- **Why it matters** The central contribution of the paper is the claimed performance improvement. Without concrete numbers and a clear description of the experimental setup, readers cannot assess whether the improvement is statistically significant or practically meaningful. This is essential for establishing the method's validity.
- **Resolution test** Provide a table or figure in the full manuscript with performance metrics (e.g., AUC, accuracy) for NoAS-DS and at least three baseline models on the TFBS and RBP datasets, including standard deviations and statistical significance tests (e.g., paired t-test or Wilcoxon test).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The abstract states that NoAS-DS "specifically combines Convolution and LSTM layers that helps in the process of automatic architecture building."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not describe the architecture search algorithm, including the search space, search strategy (e.g., reinforcement learning, evolutionary, or gradient-based), or the optimization objective. It is unclear how the convolution and LSTM layers are combined, how the search is conducted, and what constraints or heuristics are applied. The term "neural optimal architecture search" is not defined in terms of optimality criteria.
- **Why it matters** Reproducibility is a core requirement for scientific contributions. Without a detailed description of the search method, other researchers cannot replicate the approach or build upon it. The novelty of the hybrid combination also depends on how it differs from existing NAS methods that may already incorporate recurrent layers.
- **Resolution test** In the full manuscript, provide a formal description of the search space, the search algorithm, the optimization objective, and pseudocode or a flowchart. Include a comparison with at least one existing NAS method that uses recurrent layers to highlight the specific contribution.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalization claim
- **Claim pointer** The abstract claims that "The best architectures generated by the proposed model can be applied to other DNA datasets of similar nature using transfer learning technique that demonstrates its generalization capability."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not provide any evidence for the transfer learning claim. No experiments are described that apply the learned architectures to new datasets, and no metrics are reported to demonstrate successful transfer. The phrase "datasets of similar nature" is vague and does not specify what similarity criteria are used.
- **Why it matters** Generalization is a key selling point of the method, as it claims to reduce effort for new prediction tasks. Without empirical validation, this claim is speculative. If the transfer learning does not work as described, the practical utility of the method is significantly diminished.
- **Resolution test** In the full manuscript, include a dedicated section on transfer learning experiments, where architectures trained on one dataset (e.g., a TFBS dataset) are applied to at least two other DNA sequence datasets (e.g., different cell types or species). Report performance metrics and compare them to training from scratch or to a baseline architecture.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract title and terminology
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "NoAS-DS" is not expanded or explained. The abbreviation "DS" is ambiguous, and the title "Neural optimal architecture search" may overstate the optimality of the method, as no formal optimality guarantee is described.
- **Required correction** Expand the abbreviation in the abstract (e.g., "NoAS-DS (Neural optimal Architecture Search for DNA Signals)") and clarify the meaning of "optimal" in the context of the search method, or consider revising the title to avoid implying a formal optimality guarantee.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Related work
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract mentions that "Most of the architecture search methods are developed over the task of image classification" but does not cite or discuss any specific prior NAS methods for sequence or genomic data. This omission makes it difficult to assess the novelty of the proposed approach.
- **Required correction** In the full manuscript, include a brief review of existing NAS methods applied to DNA or sequence data, and explicitly state how NoAS-DS differs from them.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract structure
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract is dense and jumps between motivation, method, and results without clear transitions. Terms such as "DNA computing" and "TF-DNA binding prediction" are used without definition, which may hinder nonspecialist readers.
- **Required correction** Restructure the abstract to include a brief definition of key terms (e.g., "DNA computing" and "TF-DNA binding") and use clearer topic sentences to guide the reader through the motivation, method, and results.

## Risk / unsupported claims
- The claim of "high accuracy results" is unsupported due to the absence of quantitative metrics.
- The claim of outperforming other models is unsupported without baseline descriptions and statistical tests.
- The claim of transfer learning capability is unsupported without experimental evidence.
- The claim of "neural optimal architecture search" is not defined in terms of optimality criteria and is therefore not assessable.
- The generalizability of the method to "other DNA datasets of similar nature" is speculative without a clear definition of similarity or empirical demonstration.