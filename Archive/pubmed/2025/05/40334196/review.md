## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Technical and scientific evaluation of the CBR-KAN model for transcription factor binding site prediction, based solely on the supplied manuscript text
- **Shared manuscript claim summary** The authors propose CBR-KAN, a hybrid deep neural network integrating CNN, BiLSTM, KAN, and residual connections, and claim it outperforms existing methods (DeepBind, DanQ, DeepD2V, DeepSEA) across 50 ChIP-seq benchmark datasets for transcription factor binding site prediction
- **Visible evidence base** Tables 1-5 (referenced but not shown), Figures 1-6 (referenced but not shown), statistical test results (p-values reported in text), dataset descriptions
- **Missing materials affecting confidence** All tables and figures are referenced but not provided; no hyperparameter details, training curves, or code availability; no detailed dataset accession numbers; no baseline model implementation details

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational genomics and proposes a reasonable architectural combination. However, the current evidence base is insufficient to fully evaluate the claims. The core results are presented only as references to tables and figures that are not included in the supplied material. The statistical analysis is limited to a single test (T-test) without correction for multiple comparisons. The novelty of applying KAN to TFBS prediction is incremental, and the comparison with state-of-the-art methods lacks critical details on implementation fairness. The writing is generally clear but contains some redundancy and imprecise statements.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, specifically those developing deep learning methods for transcription factor binding site prediction. The work may also interest researchers exploring KAN architectures in biological sequence analysis. The practical implications for drug design and development are mentioned but not substantiated.

- **Major strengths** 
  1. The problem is well-motivated and practically relevant
  2. The architectural design is reasonable and combines established components (CNN, BiLSTM) with a newer one (KAN)
  3. The evaluation across 50 datasets is comprehensive in scope
  4. The authors acknowledge limitations regarding interpretability and generalization

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Testing on 50 common ChIP-seq benchmark datasets shows that CBR-KAN outperforms other state-of-the-art methods such as DeepBind, DanQ, DeepD2V, and DeepSEA in predicting TF binding sites"
- **Evidence pointer** Tables 1-5, Figures 3-6 (all referenced but not provided)
- **Concern** The central claim of superior performance is supported only by references to tables and figures that are not included in the supplied material. Without the actual numerical results, the claim cannot be verified or evaluated. The text provides some specific values (e.g., F1-score 0.855, MCC 0.799, ROC AUC 0.954 on GM12878BATF), but these are isolated and lack context such as confidence intervals or variance across datasets.
- **Why it matters** The primary contribution of this work is empirical. Without access to the actual results, the scientific case is not established. Reviewers and readers cannot assess whether the improvements are meaningful, consistent, or statistically robust.
- **Resolution test** Provide all tables and figures with complete numerical results, including per-dataset performance, means, standard deviations, and statistical significance tests with appropriate multiple comparison corrections.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** "The promising results on multiple key performance indicators demonstrate the potential of CBR-KAN in bioinformatics applications"
- **Evidence pointer** Methods section, Results section (location not provided)
- **Concern** The manuscript lacks critical methodological details needed to assess the validity of the comparison. Specifically: (1) How were baseline models (DeepBind, DanQ, DeepD2V, DeepSEA) implemented and trained? Were their hyperparameters optimized? (2) What was the train/validation/test split protocol across the 50 datasets? (3) How was the early stopping criterion (5000 batches without improvement) determined? (4) What was the total training time and computational cost? (5) Were the baseline models retrained on the same data or were pre-trained models used?
- **Why it matters** Fair comparison with state-of-the-art methods is essential for establishing the claimed improvements. Without these details, the reported performance differences could be attributed to implementation artifacts, hyperparameter choices, or evaluation protocol differences rather than architectural advantages.
- **Resolution test** Provide complete implementation details for all models, including architecture specifications, hyperparameter search procedures, training protocols, and evaluation methodology. Describe how the comparison was made fair across methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical validity
- **Claim pointer** "The results showed that the p values between the results of CBR-KAN and those of 'DeepBind', 'DanQ', 'DeepD2V', and 'DeepSEA' were 1.012 × 10⁻⁷, 5.4054 × 10⁻⁵, 0.0422, and 0.0398 respectively, all of which were significant"
- **Evidence pointer** Results section, T-test description (location not provided)
- **Concern** The statistical analysis is limited to pairwise T-tests without correction for multiple comparisons. With 50 datasets and 4 baseline comparisons, the family-wise error rate is inflated. Additionally, the text does not specify whether these are paired or unpaired tests, whether the data met normality assumptions, or whether the tests were performed on per-dataset metrics or pooled predictions.
- **Why it matters** The claim of statistical significance is central to the paper's conclusions. Inappropriate statistical testing can lead to false positive claims of superiority, undermining the reliability of the findings.
- **Resolution test** Apply appropriate multiple comparison corrections (e.g., Bonferroni, Holm, or FDR). Specify the exact test used, its assumptions, and whether they were verified. Consider reporting effect sizes and confidence intervals in addition to p-values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and contribution
- **Claim pointer** "This study proposes a hybrid deep neural network based on KAN, named CBR-KAN, which is an advanced model for predicting transcription factor binding sites (TFBS) in DNA sequences"
- **Evidence pointer** Introduction, Methods, Discussion
- **Concern** The novelty of this work is presented as the introduction of KAN to TFBS prediction. However, the manuscript does not clearly articulate what specific advantages KAN provides over MLP in this context beyond general claims of "improved robustness and feature extraction." The authors do not provide analysis of what the KAN layers learn, how they differ from MLP in this application, or why spline-based activations are particularly suited for DNA sequence data. The contribution appears incremental rather than transformative.
- **Why it matters** For a journal with broad readership, the significance of the contribution must be clearly established. If KAN is simply swapped for MLP without demonstrated mechanistic advantages, the contribution may be viewed as a minor architectural variation rather than a meaningful advance.
- **Resolution test** Provide analysis of KAN layer behavior (e.g., learned spline functions, comparison with MLP representations), ablation studies isolating KAN's specific contribution, and discussion of why KAN is particularly suited for TFBS prediction.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability claims
- **Claim pointer** "We sourced data from three additional cell lines available on GEO: GSM1873040 (LNCaP), GSM2437758 (MCF-7), and GSM2067524 (A549). Subsequently, we applied our model to these datasets, and the outcomes are presented in Table 5"
- **Evidence pointer** Results section, Table 5 (referenced but not provided)
- **Concern** The claim of cross-cell-line generalizability is based on only three additional cell lines, and the manuscript does not specify how these were selected, whether they represent diverse chromatin contexts, or how the model was adapted (if at all) to these new datasets. The reported improvements (e.g., "2.4% relative improvement in MCC") are modest and may not be practically significant.
- **Why it matters** Generalizability is a key claim in the discussion. Limited external validation with modest improvements does not strongly support the assertion of "exceptional robustness and cross-cell-line generalizability."
- **Resolution test** Provide details on the selection criteria for additional cell lines, the full results for all three cell lines, and a more nuanced discussion of the practical significance of the observed improvements.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and precision
- **Affected element** Methods, Dataset description
- **Evidence pointer** "Dataset and processing" section
- **Issue** The description of negative sample generation is incomplete. The text states "Negative samples are generated by matching the repeat fraction, length, and GC content of the positive samples" but does not specify the source of negative sequences, the ratio of positive to negative samples, or the exact matching algorithm.
- **Required correction** Provide complete details on negative sample generation, including source, ratio, and matching criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Model implementation
- **Evidence pointer** "Model building" section
- **Issue** The manuscript does not provide information on the embedding dimension, the number of LSTM layers, dropout rates, or the specific KAN architecture (number of layers, grid size, spline order). These details are essential for reproducibility.
- **Required correction** Provide a complete specification of all model hyperparameters, either in the text or as a supplementary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results section
- **Evidence pointer** "Results" section
- **Issue** The text contains a sentence fragment: "For the experimental results in Table 1, we conduct the following analysis:" followed by no analysis. This appears to be an incomplete section.
- **Required correction** Complete the analysis or remove the placeholder text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language and clarity
- **Affected element** Introduction
- **Evidence pointer** "Introduction" section
- **Issue** The sentence "Recent advances in next-generation sequencing have led to the development of Chromatin Immunoprecipitation Sequencing (ChIP-Seq) has been developed to identify protein-DNA binding sites" contains a grammatical error and redundancy.
- **Required correction** Revise to "Recent advances in next-generation sequencing have led to the development of Chromatin Immunoprecipitation Sequencing (ChIP-Seq) for identifying protein-DNA binding sites."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** "Discussion" section
- **Issue** The discussion of limitations is brief and does not address potential overfitting, the choice of evaluation metrics, or the computational cost of the proposed model compared to baselines.
- **Required correction** Expand the limitations section to address these points.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Methods, Dataset description
- **Evidence pointer** "Dataset and processing" section
- **Issue** The text states "following the method of Deng et al. [20]" but does not specify which aspects of the method were followed or whether any modifications were made.
- **Required correction** Clarify the specific aspects of the Deng et al. method that were adopted and any deviations.

## Risk / unsupported claims
- The central claim of superior performance over state-of-the-art methods is unsupported in the supplied material because all tables and figures are referenced but not provided
- The claim of "exceptional robustness and cross-cell-line generalizability" is weakly supported by only three additional cell lines with modest improvements
- The claim that KAN "significantly improves" prediction accuracy is not substantiated with mechanistic analysis or clear evidence of KAN-specific contributions
- The statement that the model has "high reliability and effectiveness" is an overstatement given the limited evidence provided
- The claim that the approach has implications for "drug design and development" is mentioned but not elaborated or supported
- The assertion that KAN provides "increased interpretability" is not demonstrated with any analysis of learned features or model behavior