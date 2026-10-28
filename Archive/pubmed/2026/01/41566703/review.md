## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose DeepDBPI, a deep learning-based predictor for DNA-binding proteins, using four novel feature descriptors (CC-PSSM, BP-PSSM, TRG-PSSM, FEGS) and wavelet denoising, with six recurrent architectures tested. The best model (BiGRU with denoised FEGS) reportedly achieves 92.13% accuracy, 93.07% sensitivity, 91.19% specificity, and 0.8427 MCC on an independent test set.
- **Visible evidence base** Abstract text only; dataset and code availability statement (Zenodo DOI)
- **Missing materials affecting confidence** Full manuscript, all figures and tables, dataset details, feature extraction implementation, model hyperparameters, training/validation splits, baseline comparisons, and statistical significance tests

## Reviewer
- **Overall assessment** The abstract presents a plausible computational pipeline for DNA-binding protein prediction, combining established feature types with wavelet denoising and recurrent architectures. However, the evidence provided is insufficient to evaluate the novelty, technical soundness, or generalizability of the claims. The reported performance metrics are promising but lack context regarding baseline comparisons, dataset composition, and reproducibility details. The abstract does not establish that the proposed descriptors or denoising strategy offer meaningful improvements over existing methods.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those developing sequence-based predictors for DNA-binding proteins. Researchers in machine learning applied to biological sequences may also find the feature engineering and denoising approach of interest, though the novelty relative to existing PSSM-based descriptors is not clear from the abstract.
- **Major strengths** The abstract clearly states the biological motivation and the practical need for computational DBP prediction. The use of multiple feature descriptors and a systematic comparison of six recurrent architectures suggests a thorough empirical approach. The inclusion of a public data and code repository is commendable for reproducibility.
- **Major Concerns** The abstract does not provide sufficient detail to assess the novelty of the proposed descriptors relative to existing PSSM-based methods. The performance metrics are reported without baseline comparisons or statistical significance testing. The choice of BiGRU over other architectures is stated but not justified mechanistically. The generalizability of the model to diverse protein families or organisms is not addressed. The abstract lacks information on dataset size, class balance, and potential biases in the independent test set.
- **Minor Comments** The abstract would benefit from specifying the number of proteins in the training and independent test sets. The term "novel descriptors" is used without clarifying what distinguishes them from prior PSSM-based encodings. The wavelet denoising step is mentioned but its contribution to performance is not quantified. The statement about "insights for drug discovery" is speculative and not supported by the presented results.
- **Technical failings that need to be addressed before the case is established** The abstract does not provide evidence that the proposed method outperforms existing DBP predictors. Without baseline comparisons, the reported accuracy and MCC values cannot be interpreted as improvements. The lack of dataset details and hyperparameter information prevents independent replication or assessment of overfitting risk.
- **Assessment against Nature-style criteria** Originality: Not established from the abstract; the descriptors appear to be variations of existing PSSM-based features, and the novelty claim is unsubstantiated. Scientific importance: Moderate, as DBP prediction is an active field, but the abstract does not demonstrate a significant advance over current state-of-the-art. Interdisciplinary readership: Limited; the abstract is written for a specialized bioinformatics audience and does not frame the work for broader biological or clinical relevance. Technical soundness: Cannot be fully assessed; the methodology is described at a high level, and key details on data, training, and evaluation are missing. Readability for nonspecialists: The abstract is dense with acronyms and technical terms, making it difficult for non-experts to follow the core contribution.
- **Recommendation posture** Currently not established from the provided evidence. The abstract reports promising results but lacks the comparative and methodological detail needed to support the claims of novelty and improved performance. A full manuscript with baselines, dataset characterization, and ablation studies would be required to assess the contribution.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The proposed DeepDBPI model achieved the best prediction performance with Bi-GRU using the denoised-based FEGS encoding method under 5-fold cross-validation, evaluated by ACC, SN, SP, and MCC.
- **Evidence pointer** Abstract, Results section
- **Concern** The abstract reports performance metrics for the BiGRU model with denoised FEGS but provides no comparison against existing DBP predictors or against the other five architectures tested. Without baselines, the reader cannot determine whether the reported 92.13% accuracy and 0.8427 MCC represent a meaningful improvement or are within the range of existing methods.
- **Why it matters** The central claim of the paper is that DeepDBPI enhances DBP prediction. This claim requires evidence that the method outperforms current state-of-the-art tools on the same benchmark datasets. The absence of comparative results makes the performance metrics uninterpretable in context.
- **Resolution test** Provide a table comparing DeepDBPI against at least three existing DBP predictors on the same independent test set, including statistical significance tests (e.g., McNemar's test) and confidence intervals for the reported metrics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Originality
- **Claim pointer** The proposed DeepDBPI model leverages the evolutionary and graphical-based properties of protein sequences using novel descriptors, namely covariance correlation-based position-specific scoring matrix (CC-PSSM), binary-profile-based (BP-PSSM), Trigram (TRG-PSSM), and feature encoding based on graphical and statistical (FEGS) methods.
- **Evidence pointer** Abstract, Method section
- **Concern** The abstract claims these descriptors are "novel" but does not explain how they differ from existing PSSM-based feature encodings, such as PSSM-composition, PSSM-autocorrelation, or PSSM-DCT, which are widely used in the field. The novelty claim is unverifiable without a description of the feature construction and a comparison to prior encodings.
- **Why it matters** The contribution of the paper hinges on the novelty of the feature descriptors. If these are minor variations of existing methods, the scientific advance is limited. The abstract must clearly articulate the conceptual or methodological innovation.
- **Resolution test** In the full manuscript, provide a formal definition of each descriptor, a comparison to at least two existing PSSM-based encodings on the same dataset, and an ablation study showing the incremental contribution of each descriptor to prediction performance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** All data, including the dataset, feature extraction techniques, and models, are available at: https://doi.org/10.5281/zenodo.17496063.
- **Evidence pointer** Abstract, Data Availability statement
- **Concern** While the data availability statement is commendable, the abstract does not specify the dataset size, the number of positive and negative samples, the source of the dataset (e.g., UniProt, PDB), or the criteria for constructing the independent test set. Without these details, the reader cannot assess potential biases, such as sequence redundancy or class imbalance, that could inflate the reported metrics.
- **Why it matters** Reproducibility and generalizability depend on a clear description of the data. If the independent test set shares high sequence identity with the training set, the reported performance may be optimistically biased. The abstract must provide basic dataset statistics.
- **Resolution test** In the full manuscript, report the number of proteins in training and test sets, the sequence identity threshold used to avoid redundancy, the class balance, and the source of the dataset. Additionally, provide a detailed description of the independent test set construction.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Method section
- **Evidence pointer** Abstract, Method section
- **Issue** The abstract lists six recurrent architectures (ResNet, LSTM, BiLSTM, RNN, BiRNN, BiGRU) but does not specify the input dimensionality, the number of layers, or the training procedure. This level of detail is insufficient for a reader to understand the model complexity or computational cost.
- **Required correction** Provide a brief description of the model architecture, including the number of layers, hidden units, and training epochs, or refer to a supplementary table in the full manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, Results section
- **Concern** The abstract states that the model achieved "the best prediction performance with Bi-GRU" but does not report the performance of the other five architectures. This makes it impossible to assess whether the choice of BiGRU is robust or dataset-specific.
- **Required correction** Include a summary of the performance of all six architectures, or state that the full comparison is provided in the main text or supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, Results section
- **Concern** The abstract claims the model provides "insights for drug discovery and other proteomic problems," but no evidence or discussion is provided to support this broader relevance. This statement appears speculative.
- **Required correction** Either remove the speculative claim or provide a brief explanation of how the method could be extended to other protein function prediction tasks, with references to prior work.

## Risk / unsupported claims
- The claim that the proposed descriptors are "novel" is unsupported without a formal definition and comparison to existing methods.
- The claim that DeepDBPI "enhances" DBP prediction is unsupported without baseline comparisons to existing predictors.
- The reported performance metrics (92.13% ACC, 0.8427 MCC) are uninterpretable without context on dataset composition, class balance, and test set construction.
- The statement about relevance to drug discovery is speculative and not supported by the presented results.
- The generalizability of the model to diverse protein families or organisms is not addressed and cannot be assessed from the abstract.