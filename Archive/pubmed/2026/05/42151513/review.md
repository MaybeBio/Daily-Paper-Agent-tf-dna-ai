## Review setup
- **Input scope** Full manuscript text (abstract, introduction, related work, methodology, results, discussion, conclusion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific soundness, methodological rigor, reproducibility, and validity of claims based solely on the provided text
- **Shared manuscript claim summary** The authors propose an explainable AI framework integrating machine learning (MNB, LR, RF) and deep learning (CNN, CNN-Attention, CNN-BiLSTM) models for multi-species DNA functional group classification across Human, Chimpanzee, Dog, and Combined datasets. They report that Logistic Regression achieved the highest MCC and F1-scores across all datasets, and that a multi-level XAI analysis (Feature Importance, Saliency Maps, Integrated Gradients, GradientSHAP, Attention Heatmaps) identified consensus motifs, evaluated stability via Jaccard similarity, and assessed fidelity via masking experiments.
- **Visible evidence base** Text descriptions of methods and results, including performance tables (Tables 2-7), motif analysis tables (Tables 9-11), fidelity analysis (Table 12), and figure descriptions (Figures 1-11)
- **Missing materials affecting confidence** Actual figures, full tables with all data, dataset details, code availability, hyperparameter values, model architecture specifics, statistical test details, and supplementary information

## Reviewer
- **Overall assessment** The manuscript addresses a relevant topic in genomic machine learning, but the current evidence base is insufficient to establish the claimed contributions. The primary finding that Logistic Regression outperforms deep learning models is plausible but lacks critical context, including dataset characteristics, baseline comparisons, and rigorous statistical validation. The XAI analysis, while comprehensive in scope, is described at a level that prevents assessment of its validity or biological significance. The manuscript requires substantial revisions to clarify methodology, provide complete results, and temper claims that currently exceed the evidence presented.

- **Who would be interested in the results, and why** Researchers in computational genomics and bioinformatics, particularly those working on DNA sequence classification and model interpretability. The comparison of classical ML versus deep learning approaches for k-mer based classification, and the integration of multiple XAI techniques, may interest practitioners seeking practical guidance on model selection and interpretation in genomic tasks. The multi-species aspect could appeal to those studying cross-species regulatory elements.

- **Major strengths**
  - The integration of multiple XAI techniques (five methods) within a single framework is a systematic approach to interpretability.
  - The use of multiple performance metrics (MCC, F1, AUC) appropriate for imbalanced classification is methodologically sound.
  - The inclusion of stability (Jaccard similarity) and fidelity (masking) analyses goes beyond typical XAI applications.
  - The comparison across multiple species and a combined dataset addresses a gap in multi-species genomic classification.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript claims a "controlled hyperparameter tuning strategy" and "robustness evaluation" but provides no specific hyperparameter values, search ranges, or selection criteria.
- **Evidence pointer** Section "Performance of the machine learning models", Tables 2-3; Section "Deep learning models used"
- **Concern** The hyperparameter configurations listed in Table 2 are described only as "Config 1/2/3" with minimal parameter values (e.g., alpha, C, tree counts). For deep learning models, no learning rates, batch sizes, embedding dimensions, or layer counts are provided beyond vague descriptions. The claim of "controlled" tuning is unverifiable without the full search space, selection methodology, or final chosen parameters for each model-dataset combination.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without complete hyperparameter details, other researchers cannot replicate the experiments or assess whether the reported performance differences reflect genuine model capabilities or artifacts of suboptimal tuning for some models.
- **Resolution test** Provide a complete table of all hyperparameters tested, the selection criterion (e.g., validation performance), and the final chosen configuration for each model and dataset. Include code or a repository link.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** The manuscript states that "Logistic Regression consistently achieved the highest MCC and F1-scores across all evaluated datasets" and reports p-values from McNemar's test.
- **Evidence pointer** Section "Performance of the machine learning models", Table 4; Section "Performance of the deep learning models", Table 7
- **Concern** The p-values reported in Tables 4 and 7 are presented without context. It is unclear which comparisons are being tested (e.g., LR vs MNB, LR vs RF, LR vs each DL model), whether multiple testing corrections were applied, and what the null hypothesis is. The p-values for some comparisons (e.g., 4.44 x 10^-65) are implausibly small given the reported performance differences, suggesting possible methodological issues. Additionally, the manuscript does not report confidence intervals or effect sizes, which are essential for interpreting the practical significance of performance differences.
- **Why it matters** The central claim of LR superiority rests on statistical comparisons. If the testing methodology is flawed or incomplete, the conclusion may not be supported. The lack of multiple testing correction is particularly concerning given the large number of pairwise comparisons implied.
- **Resolution test** Clearly state the null hypothesis for each comparison, report all pairwise p-values, apply and disclose multiple testing corrections (e.g., Bonferroni, FDR), and include confidence intervals for the primary metrics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data and preprocessing transparency
- **Claim pointer** The manuscript describes using "three publicly available DNA sequence datasets from Kaggle" and constructing a "Combined dataset" by merging all three sources.
- **Evidence pointer** Section "Datasets used", Table 1
- **Concern** No dataset identifiers, accession numbers, or URLs are provided. The preprocessing steps are described only at a high level (k-mer segmentation, count vectorization, integer encoding), with no details on sequence length filtering, handling of ambiguous bases, class balance adjustments, or train-test split verification. The claim that the Combined dataset "integrates sequences from all three species" is ambiguous regarding whether sequences are pooled with species as a feature or treated as a single homogeneous set.
- **Why it matters** Dataset provenance and preprocessing directly affect model performance and generalizability. Without this information, readers cannot assess potential data leakage, class imbalance issues, or whether the Combined dataset is meaningfully different from the individual species datasets.
- **Resolution test** Provide dataset names, sources, and access links. Describe all preprocessing steps in detail, including any filtering, normalization, or augmentation. Clarify the construction of the Combined dataset and report class distributions for all datasets.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** XAI validity
- **Claim pointer** The manuscript claims that the XAI analysis "identified consensus motifs, cross-dataset and cross-model motif patterns, and evaluated model stability based on motif overlap and Jaccard similarity, as well as model fidelity based on performance drops after masking model-identified motifs."
- **Evidence pointer** Section "Explainability based motif analysis", Tables 9-12, Figures 10-11
- **Concern** The XAI analysis is described at a level that prevents assessment of its validity. No details are provided on how motifs were defined, how top-k motifs were selected, how consensus was determined across models or XAI methods, or how statistical significance of motif enrichment was assessed. The fidelity analysis (Table 12) reports performance drops but does not specify the masking procedure (e.g., whether all occurrences of a motif were masked, how partial overlaps were handled). The biological interpretation of motifs relies on "Tomtom tool against the JASPAR2020 CNE database," but the specific parameters, significance thresholds, and results of these comparisons are not reported.
- **Why it matters** The XAI component is a core contribution of the manuscript. Without methodological detail, the biological claims (e.g., "motifs correspond to conserved transmembrane and cytoplasmic elements") are unsupported. The validity of the stability and fidelity metrics depends entirely on the rigor of the underlying procedures.
- **Resolution test** Provide a detailed description of the motif extraction and consensus procedure, including thresholds and statistical tests. Report the full results of the Tomtom comparisons, including p-values and the specific database version. Describe the masking procedure in detail and justify the choice of metrics.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmarking and comparative claims
- **Claim pointer** The manuscript claims that "the novelty of our framework lies not only in integrating ML and DL models, but in introducing a structured, multi-level explainability pipeline" and compares with prior studies in Table 8.
- **Evidence pointer** Section "Benchmarking against prior studies", Table 8
- **Concern** The comparison with prior studies is superficial. Table 8 lists previous works with their reported accuracies but does not provide a direct, controlled comparison using the same evaluation protocol. The claim of novelty is not substantiated by a systematic review of existing XAI frameworks in genomics. The manuscript does not discuss how the proposed framework differs from or improves upon existing explainable AI approaches in this domain beyond listing techniques.
- **Why it matters** The scientific contribution of the manuscript depends on demonstrating a clear advance over existing methods. Without a rigorous comparative analysis, the novelty claim is not established. The lack of a systematic literature review weakens the contextualization of the work.
- **Resolution test** Conduct a systematic comparison with existing methods using identical evaluation protocols, including statistical testing. Provide a more comprehensive review of prior XAI frameworks in genomics and clearly articulate the specific novel contributions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract states "The functional groups represent gene families, including transcription factors and kinases," but the methodology section lists seven functional groups (GPCRs, Tyrosine kinase, Tyrosine phosphatase, Synthetase, Synthase, Ion channel, Transcription factor). The abstract is incomplete and does not accurately represent the full scope of the classification task.
- **Required correction** Update the abstract to list all seven functional groups or use a more general description that encompasses all classes.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methodology, "Preprocessing steps"
- **Evidence pointer** Section "Preprocessing steps"
- **Issue** The text contains an incomplete sentence: "ensuring that raw DNA sequences are transformed into structured representations suitable for The processed sequences were then segmented into k-mers". This appears to be a typographical error or missing text.
- **Required correction** Complete the sentence and ensure all preprocessing steps are described in full.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Tables 4 and 7
- **Evidence pointer** Tables 4 and 7
- **Issue** The p-values are reported in scientific notation (e.g., 4.44 x 10^-65) without indicating the test statistic or degrees of freedom. Some p-values are identical across different comparisons (e.g., 1.62 x 10^-93 appears twice), which is suspicious and may indicate a reporting error.
- **Required correction** Report the test statistic, degrees of freedom, and exact p-values. Verify that all reported values are correct and unique where appropriate.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1-11
- **Evidence pointer** Figure descriptions in text
- **Issue** The figures are described but not provided in the manuscript text. Given the importance of figures for understanding the framework architecture (Figure 1), model performance (Figures 7-8), and motif analysis (Figures 10-11), their absence limits the reader's ability to interpret the results.
- **Required correction** Ensure all figures are included in the final submission with appropriate resolution and captions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The term "functional group" is used to describe both gene families (e.g., GPCRs, kinases) and chemical functional groups, which may cause confusion. The manuscript should clarify the terminology early in the text.
- **Required correction** Define "functional group" in the context of this manuscript and use consistent terminology throughout.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section "Deep learning models used"
- **Evidence pointer** Section "Deep learning models used"
- **Issue** The manuscript states that "All deep learning models were trained using the Adam optimizer with categorical cross-entropy loss" but does not specify the number of training epochs, batch size, learning rate schedule, or early stopping criteria beyond "patience = 5" and "maximum limit of 30 epochs."
- **Required correction** Provide complete training details, including the final learning rate, batch size, and any data augmentation or regularization techniques.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Consensus motifs analysis"
- **Evidence pointer** Section "Consensus motifs analysis"
- **Issue** The text states that "motifs such as ctgtgg, tgctgt, and ggaggc corresponded to conserved transmembrane and cytoplasmic elements, including CWxP-related residues and glycine-rich hinge regions." However, the connection between specific 6-mer DNA sequences and protein-level motifs (e.g., CWxP) is not explained. DNA k-mers do not directly correspond to amino acid motifs without considering codon usage and reading frames.
- **Required correction** Clarify the relationship between DNA k-mers and protein motifs, or revise the interpretation to avoid overclaiming biological significance.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Stability analysis of motifs"
- **Evidence pointer** Table 11
- **Issue** The stability analysis reports Jaccard indices and overlap percentages for ML and DL model pairs, but the text does not explain how these metrics should be interpreted. For example, a Jaccard index of 0.25 is described as "higher consistency" without context for what constitutes acceptable or meaningful stability.
- **Required correction** Provide interpretation guidelines for the stability metrics and discuss the implications of the observed values.

## Risk / unsupported claims
- The claim that "Logistic Regression consistently achieved the highest MCC and F1-scores across all evaluated datasets" is not fully supported without complete results for all models and datasets, including standard deviations and statistical tests.
- The claim that identified motifs "represent biologically plausible sequence signatures aligned with known structural, catalytic, or regulatory features" is unsupported without detailed enrichment analysis results and statistical significance testing.
- The claim that "the novelty of our framework lies not only in integrating ML and DL models, but in introducing a structured, multi-level explainability pipeline" is not substantiated by a systematic comparison with existing XAI frameworks.
- The statement that "classical models showed stronger generalization across species" is not supported by cross-validation or external validation results.
- The claim that "deep learning architectures captured longer motif dependencies" is not demonstrated with specific evidence or analysis.
- The biological interpretations of specific motifs (e.g., "CWxP-related residues," "GxGxxG P-loop") are not verifiable without detailed sequence analysis and comparison to known databases.
- The performance comparison with prior studies in Table 8 is not a controlled comparison and does not account for differences in data splits, preprocessing, or evaluation protocols.