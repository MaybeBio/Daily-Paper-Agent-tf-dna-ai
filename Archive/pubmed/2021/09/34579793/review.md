## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and supplementary figure legends
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors propose that transfer learning for transcription factor binding prediction is improved when the pre-training step incorporates biologically relevant transcription factors, such as those sharing binding modes or cofactor relationships with the target factor, and they demonstrate this using a large matrix of binding events across accessible genomic regions
- **Visible evidence base** Main text figures 1-9, supplementary figures S1-S11, supplementary tables S1-S6, methods section
- **Missing materials affecting confidence** Actual model performance values for all individual transcription factors are not fully reported in the main text; code availability is not stated; exact hyperparameter choices for fine-tuning are not fully specified; statistical test details for some comparisons are incomplete

## Reviewer
- **Overall assessment** This manuscript presents a systematic evaluation of transfer learning strategies for transcription factor binding prediction, with a focus on the biological relevance of pre-training data. The authors construct a large, carefully curated matrix of binding events and demonstrate that transfer learning improves performance, particularly for transcription factors with limited data. The key novel contribution is the finding that pre-training with biologically related transcription factors, such as those sharing binding modes or cofactors, yields greater improvements than pre-training with randomly selected factors. The interpretability analyses using DeepLIFT and TF-MoDISco provide mechanistic insight into how transfer learning refines convolutional filters. The work is technically sound overall, though several concerns regarding statistical rigor, baseline comparisons, and generalizability should be addressed.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those developing deep learning models for transcription factor binding prediction. The findings are also relevant to researchers applying transfer learning in other genomic prediction tasks, as the study provides a framework for incorporating biological prior knowledge into pre-training strategies. The interpretability analyses will interest those studying the mechanisms of deep learning models in genomics.

- **Major strengths** The construction of a large, carefully curated binding matrix with explicit handling of ambiguous regions is a methodological strength. The systematic comparison of different pre-training strategies, including biologically relevant versus random transcription factors, is well designed. The inclusion of multiple model architectures (CNN and hybrid CNN-RNN) strengthens the generalizability of the findings. The interpretability analyses provide valuable mechanistic insight into the transfer learning process.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor
  - **Claim pointer** The authors claim that transfer learning significantly improves model performance for 39 of 49 transcription factors (79.6 percent), supported by a Wilcoxon signed-rank test with p value 1.91e-07.
  - **Evidence pointer** Figure 3B, Table S2
  - **Concern** The Wilcoxon signed-rank test is applied across all transcription factors collectively, but the authors do not report whether individual transcription factor improvements are statistically significant after multiple testing correction. Given that 49 factors are tested, the false discovery rate could be substantial. The authors should report per-factor confidence intervals or apply multiple testing corrections to identify which specific factors benefit significantly.
  - **Why it matters** Without per-factor statistical assessment, the claim that transfer learning benefits a specific proportion of factors is not rigorously supported. The collective test could be driven by a subset of factors with large improvements while others show no significant change.
  - **Resolution test** Provide per-factor confidence intervals for AUCPR differences or apply Benjamini-Hochberg correction to per-factor p values and report the number of factors that remain significant.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Baseline comparison
  - **Claim pointer** The authors state that transfer learning performance was comparable to that of de novo PWMs (0.845 vs. 0.856, p value 0.667, not significant), but that de novo PWMs outperformed transfer learning for transcription factors with small training datasets.
  - **Evidence pointer** Figure 3C
  - **Concern** The comparison to de novo PWMs is presented as a baseline, but the authors do not clarify whether the de novo PWM approach uses the same training data or a different methodology. The statement that de novo PWMs outperform transfer learning for small datasets appears to contradict the earlier claim that transfer learning is particularly beneficial for transcription factors with approximately 500 peaks. The authors should clarify the conditions under which each method is preferred and whether the comparison is fair in terms of data usage.
  - **Why it matters** The relative performance of transfer learning versus simpler baselines is central to the manuscript's claims. If de novo PWMs are consistently better for small datasets, the practical utility of transfer learning for the stated use case is questionable.
  - **Resolution test** Clarify the de novo PWM methodology and provide a direct comparison of transfer learning versus de novo PWMs stratified by training set size, with statistical tests for each stratum.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** The authors conclude that pre-training with biologically relevant transcription factors improves transfer learning performance, based on experiments with five target transcription factors (HNF4A, JUND, MAX, SPI1, SP1) and one additional factor (EGR1).
  - **Evidence pointer** Figures 6, 7, 8
  - **Concern** The conclusion about the benefits of biologically relevant pre-training is based on a small number of target transcription factors. The authors test five main factors and one additional factor, which may not be representative of the diversity of transcription factor families and binding mechanisms. The authors should either expand the number of target factors tested or temper the generalizability of their conclusions.
  - **Why it matters** The central claim of the manuscript is that biologically relevant pre-training improves transfer learning. If this is only demonstrated for a handful of factors, the broader applicability of the approach is not established.
  - **Resolution test** Include additional target transcription factors from diverse families, or explicitly state the limitations of the current factor selection and frame conclusions accordingly.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The authors describe their model architecture and training procedure in the methods section.
  - **Evidence pointer** Methods section, model architecture
  - **Concern** The manuscript does not state whether the code and trained models are publicly available. For a computational study of this nature, code availability is essential for reproducibility and for the broader adoption advocated in the conclusions.
  - **Why it matters** Without access to the code, other researchers cannot reproduce the results or apply the transfer learning strategy to their own data, limiting the impact of the work.
  - **Resolution test** Provide a statement on code and data availability, with a repository link if applicable.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1 legend
  - **Issue** The figure legend describes the two matrices but does not clearly explain the visual encoding of the heatmap or the meaning of the colors.
  - **Required correction** Add a color scale or explicit description of the color encoding in the figure legend.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Figure 5
  - **Evidence pointer** Figure 5 legend
  - **Issue** The p value for the Welch t test comparing transcription factors with the same versus different binding modes is reported, but the effect size is not stated.
  - **Required correction** Report the mean difference and confidence interval in addition to the p value.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Abstract and results
  - **Evidence pointer** Abstract, Results section
  - **Issue** The term "biologically relevant" is used throughout but is not formally defined until later in the results. Early in the manuscript, it may be unclear to readers what constitutes biological relevance.
  - **Required correction** Define "biologically relevant" in the abstract or early in the introduction.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Table S2
  - **Evidence pointer** Table S2
  - **Issue** The table reports performance for 148 transcription factors, but the main text focuses on a subset. It would be helpful to indicate in the table which factors were used in the detailed analyses.
  - **Required correction** Add a column or annotation in Table S2 indicating which factors were used in the detailed analyses.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, transfer learning
  - **Evidence pointer** Methods section
  - **Issue** The learning rate for fine-tuning is stated as 0.0003, but the learning rate schedule and number of epochs are not specified.
  - **Required correction** Provide full training details including number of epochs, learning rate schedule, and early stopping criteria.

- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are the primary technical concerns that need to be resolved. The statistical rigor of the main claim and the fairness of the baseline comparison are essential to establishing the case for biologically relevant transfer learning.

## Risk / unsupported claims
- The claim that transfer learning is beneficial for transcription factors with approximately 500 ChIP-seq peaks is supported by the downsampling experiments, but the specific threshold at which transfer learning ceases to be beneficial is not systematically characterized.
- The claim that pre-training with cofactors improves transfer learning is based on a single target factor (JUND) and should be considered preliminary.
- The statement that "transfer learning reduced the variation in model performance resulting from different data splits" is supported by Figure S1, but the magnitude of this effect is not quantified in the main text.
- The generalizability of the findings to other model architectures beyond those tested is not established.