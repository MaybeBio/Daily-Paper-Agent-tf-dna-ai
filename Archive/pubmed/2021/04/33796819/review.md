## Review setup
- **Input scope** Full manuscript text including abstract, results, methods, and supplementary figure legends
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided text
- **Shared manuscript claim summary** The authors present AgentBind, a transfer learning framework using CNN architectures (DeepSEA, DanQ) with Grad-CAM interpretation to predict whether specific TF motif instances are bound, and to identify sequence context features most predictive of binding across 38 TFs in GM12878 cells
- **Visible evidence base** Main text figures (Figs 1-4), Extended Data Figs 1-5, Supplementary Tables 1-11, and Online Methods
- **Missing materials affecting confidence** Actual figure images, supplementary tables, and code were not provided; only text descriptions of results

## Reviewer

- **Overall assessment** The manuscript presents a well-structured framework for TF binding prediction with interpretability, addressing an important gap in understanding sequence context features beyond core motifs. The transfer learning approach and systematic comparison of training data choices are valuable contributions. However, several technical concerns regarding the interpretation methodology, control experiments, and generalizability claims need to be addressed before the conclusions are fully established.

- **Who would be interested in the results, and why** Computational biologists developing deep learning methods for regulatory genomics, experimental biologists studying TF binding mechanisms, and researchers interested in variant prioritization for non-coding disease-associated variants. The framework's flexibility and interpretability features would appeal to those seeking to move beyond black-box predictions.

- **Major strengths**
  1. Systematic evaluation of training data choices (baseline, GC-controlled, DNaseI-controlled) and their impact on learned features
  2. Rigorous benchmarking against non-deep-learning methods (KSM, IMPACT)
  3. Comprehensive interpretation analysis using multiple techniques with a well-designed simulation experiment
  4. Cross-cell-type validation for STAT3 demonstrating generalizability
  5. Practical utility demonstrated through variant prioritization analyses

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of interpretation method
- **Claim pointer** "Grad-CAM better pinpoints specific important bases" and subsequent use of Grad-CAM scores for all downstream analyses
- **Evidence pointer** Results section "Identifying the context-specific determinants of TF binding", Figure 2a, Supplementary Table 11
- **Concern** The choice of Grad-CAM over other interpretation methods is based on a simulation experiment, but the simulation setup may not reflect real biological complexity. The simulation uses only GATA1 and TAL1 motifs with simple background nucleotide frequencies, which may not capture the complexity of real TF binding contexts. The reported performance differences between methods appear modest, and the selection of the first convolutional layer for Grad-CAM requires justification. The authors do not demonstrate that Grad-CAM's superiority holds across different model architectures or more complex motif combinations.
- **Why it matters** All downstream biological interpretations (5-mer enrichment, variant prioritization) depend on the reliability of Grad-CAM scores. If the interpretation method is not optimal or its limitations are not characterized, the biological conclusions drawn from these scores may be unreliable.
- **Resolution test** Provide additional validation of Grad-CAM performance using more realistic simulated data with multiple interacting motifs, varying motif strengths, and realistic background models. Compare Grad-CAM against other methods (e.g., DeepLIFT, integrated gradients) on real biological data where ground truth is partially known (e.g., known co-binding events from ChIP-seq).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and control conditions
- **Claim pointer** "We find that the choice of training data heavily influences classification accuracy and the relative importance of features such as open chromatin"
- **Evidence pointer** Results section "Predicting binding status of TF motif occurrences", Figure 1b, Supplementary Tables 3-7
- **Concern** The comparison between baseline, GC-controlled, and DNaseI-controlled models is confounded by sample size differences. The DNaseI-controlled models have greatly reduced sample sizes (mean decrease 50%), which the authors acknowledge may drive performance differences. However, they do not adequately control for this confound. The claim that DNaseI-controlled models "better capture features specific to each TF" is based on comparisons where both the feature distribution and sample size change simultaneously.
- **Why it matters** The central conclusion that different training data choices reveal different biological features depends on isolating the effect of training data composition from sample size effects. Without proper controls, the observed differences could be artifacts of statistical power rather than genuine biological differences.
- **Resolution test** Perform additional experiments with matched sample sizes across conditions (e.g., downsampling baseline and GC-controlled models to match DNaseI-controlled sample sizes). Alternatively, use bootstrap resampling to estimate confidence intervals for performance metrics and feature importance scores across different sample sizes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and external validation
- **Claim pointer** "Our framework enables novel insights into features predictive of TF binding and is likely to inform future deep learning applications to interpret non-coding genetic variants"
- **Evidence pointer** Results sections on cross-cell-type comparison and variant prioritization, Figure 4, Extended Data Fig 5
- **Concern** The cross-cell-type analysis is limited to a single TF (STAT3) and three cell types. The variant prioritization analyses are correlative and do not demonstrate causal relationships. The MPRA comparison uses a small number of variants (116 true positives, 226 true negatives) and the effect sizes are modest. The claim that Grad-CAM scores "may be helpful in prioritizing variants" is not strongly supported by the presented evidence.
- **Why it matters** The broader applicability of the framework to other TFs, cell types, and variant prioritization tasks is a key selling point. Without stronger external validation, the generalizability claims remain speculative.
- **Resolution test** Extend cross-cell-type analysis to additional TFs and cell types. For variant prioritization, use independent datasets with experimentally validated functional variants and compare against existing variant prioritization tools. Provide effect size estimates and confidence intervals for the MPRA comparison.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation and validation
- **Claim pointer** "Top 5-mers capture known co-binding relationships" and "DNaseI-controlled models identify 5-mers that represent cooperative relationships between TFs"
- **Evidence pointer** Results section "Grad-CAM scores give insight into features of TF binding", Figure 3a-c, Extended Data Figs 3-4
- **Concern** The biological interpretations of enriched 5-mers are based on manual inspection and matching to known motifs. This approach is subjective and may miss novel or unexpected patterns. The authors do not provide quantitative validation that the identified 5-mers are functionally relevant (e.g., through mutagenesis experiments or comparison with independent functional data). The distinction between "co-binding" and "cooperative relationships" is not clearly defined or validated.
- **Why it matters** The biological insights are a major contribution of the paper. If the interpretations are not rigorously validated, the conclusions about TF binding mechanisms may be premature or incorrect.
- **Resolution test** Provide systematic motif enrichment analysis using established tools (e.g., HOMER, MEME) with appropriate multiple testing correction. Validate a subset of predicted co-binding relationships using independent experimental data (e.g., ChIP-seq co-occupancy, protein-protein interaction databases). For novel 5-mers, provide additional evidence of functional relevance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Model training details
- **Evidence pointer** Online Methods "CNN model architecture and training"
- **Issue** The description of the transfer learning process lacks specific details on hyperparameter selection, learning rates, early stopping criteria, and the number of epochs for fine-tuning. The authors state that "pre-training noticeably improves the performance" but do not provide a systematic analysis of how different pre-training strategies affect results.
- **Required correction** Provide complete hyperparameter settings and training details in the Online Methods or Supplementary Information. Include a sensitivity analysis of key hyperparameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Performance comparisons
- **Evidence pointer** Results section "Predicting binding status of TF motif occurrences", Supplementary Tables 3-4
- **Concern** Performance metrics are reported as averages across TFs without confidence intervals or measures of variance. The authors do not report whether performance differences between models (e.g., baseline vs. GC-controlled) are statistically significant.
- **Required correction** Report standard deviations or confidence intervals for all performance metrics. Perform appropriate statistical tests (e.g., paired Wilcoxon test) for model comparisons and report effect sizes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data and code availability
- **Evidence pointer** Data and Code Availability sections
- **Issue** While code is available on GitHub, the authors do not provide a detailed description of the computational environment, dependencies, or expected runtime. The data availability statement mentions variant annotation scores but does not specify the format or provide a data dictionary.
- **Required correction** Provide a detailed README with installation instructions, dependency versions, and example commands. Include a data dictionary for all output files.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Discussion of limitations
- **Evidence pointer** Discussion section
- **Issue** The authors acknowledge limitations but do not discuss the potential impact of using a single reference genome (hg19) or the effects of genetic variation on model performance. The discussion of PWMs limitations is brief and does not address how this might affect the interpretation of results.
- **Required correction** Expand the discussion of limitations to include the potential effects of reference genome choice, population diversity, and PWM limitations on the generalizability of findings.

- **Technical failings that need to be addressed before the case is established**
  1. Confounded experimental design in training data comparisons (R1-M2)
  2. Insufficient validation of interpretation method choice (R1-M1)
  3. Lack of statistical rigor in performance comparisons (R1-m2)
  4. Incomplete reporting of training details for reproducibility (R1-m1)

- **Assessment against Nature-style criteria**
  - **Originality** The framework combines existing components (transfer learning, CNN architectures, Grad-CAM) in a novel application for TF binding prediction with interpretability. The systematic comparison of training data choices is a useful contribution, though the individual components are not novel.
  - **Scientific importance** Understanding sequence context features that determine TF binding is an important question in regulatory genomics. The framework has potential utility for variant prioritization, which is clinically relevant. However, the biological insights are largely confirmatory of known relationships rather than providing major new discoveries.
  - **Interdisciplinary readership** The work bridges machine learning and molecular biology, with potential interest for computational biologists, geneticists, and researchers studying gene regulation. The methods are described at an appropriate level for a technical audience, though some biological background is assumed.
  - **Technical soundness** The deep learning methodology is generally sound, but the experimental design confounds and lack of statistical rigor in some comparisons weaken the technical foundation. The interpretation methodology requires additional validation.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible, with clear explanations of the framework and results. However, some sections (particularly the interpretation methods comparison) may be challenging for readers without deep learning expertise.

- **Recommendation posture** Supportive if technical concerns are resolved. The framework is potentially valuable, but the confounded experimental design, insufficient validation of interpretation methods, and lack of statistical rigor need to be addressed. The biological insights, while interesting, are largely confirmatory and would benefit from stronger validation. The authors should also strengthen the external validation to support generalizability claims.