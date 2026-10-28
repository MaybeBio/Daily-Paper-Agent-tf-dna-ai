## Review setup
- **Input scope** Full manuscript text (main text, figures referenced, supplementary materials referenced but not provided)
- **Assessment boundary** Technical soundness, methodological novelty, experimental validation, interpretability claims, and reproducibility of the described framework
- **Shared manuscript claim summary** The authors propose BertSNR, a deep learning framework based on a pre-trained DNA language model (DNABERT) with multi-task learning, to identify transcription factor binding sites at single-nucleotide resolution. They claim superior performance over existing methods across 188 ChIP-seq datasets, enhanced interpretability via attention weight visualization and motif analysis, and successful identification of TFBSs in the POU5F1 promoter region.
- **Visible evidence base** Main text with figures referenced (Figs 1-4), supplementary tables and figures referenced but not provided, GitHub repository link for source code
- **Missing materials affecting confidence** Supplementary Tables S1-S12, Supplementary Figures S1-S7, Supplementary Methods, actual figure images, benchmark dataset details, hyperparameter configurations, and code implementation details

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful application of DNA language models to single-nucleotide resolution TFBS prediction. The core idea of adapting a token-level classification task analogous to named entity recognition is conceptually sound and represents a reasonable extension of prior work. However, the current manuscript has several critical gaps in experimental reporting, statistical validation, and methodological detail that prevent full assessment of the claims. The performance improvements reported are modest in absolute terms, and the interpretability analysis, while interesting, lacks quantitative validation. The manuscript would benefit from more rigorous benchmarking, ablation studies, and statistical significance testing.
- **Who would be interested in the results, and why** Computational biologists working on regulatory genomics, particularly those developing deep learning methods for TFBS prediction and motif discovery. Researchers interested in applying transformer-based language models to biological sequence analysis would also find the framework relevant. The interpretability analysis may appeal to those studying model explainability in genomics.
- **Major strengths** The application of DNA language models to single-nucleotide resolution TFBS prediction is timely and addresses a real limitation of existing methods. The multi-task learning framework that combines sequence-level and token-level classification is a sensible design choice. The attention-based interpretability analysis provides qualitative insights into model behavior. The evaluation across 188 datasets is comprehensive in scale.
- **Major Concerns** (see detailed items below)
- **Minor Comments** (see detailed items below)
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical validation), R1-M2 (baseline comparison fairness), R1-M3 (interpretability validation), R1-M4 (reproducibility)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of DNA language models to nucleotide-resolution TFBS prediction is novel, but the underlying techniques (transformers, multi-task learning, attention visualization) are established. The conceptual analogy to NER is insightful but not transformative.
  - Scientific importance: Moderate. Improving TFBS prediction resolution has practical value for regulatory genomics, but the reported improvements are incremental and the biological insights derived are limited.
  - Interdisciplinary readership: Limited. The manuscript is primarily of interest to computational biology specialists. The interpretability analysis may attract some broader interest, but the presentation assumes significant domain expertise.
  - Technical soundness: Currently insufficient. Several methodological details are missing, statistical validation is inadequate, and the interpretability claims lack quantitative support.
  - Readability for nonspecialists: Acceptable for the target audience. The writing is generally clear, though some sections (particularly the methods) assume familiarity with deep learning and genomics terminology.
- **Recommendation posture** Currently not established from the provided evidence. The core claims require additional statistical validation, more rigorous baseline comparisons, and quantitative interpretability analysis. The manuscript has potential but needs substantial revision and additional experiments.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** "BertSNR outperforms the existing state-of-the-art methods in TFBS predictions" (Results section 3.1)
- **Evidence pointer** Section 3.1, Figure 3a, Supplementary Tables S4-S7
- **Concern** The claim of superior performance is based on a Paired Student t-test with a single P-value of 2.15e-15 for AUPR comparison against D-AEDNet. No effect sizes, confidence intervals, or per-dataset breakdowns are reported. The manuscript does not specify whether the t-test was applied to per-dataset AUPR values or aggregated metrics, nor does it report results for the other five evaluation metrics with statistical testing. Additionally, no correction for multiple testing across 188 datasets is described.
- **Why it matters** Without proper statistical validation, the observed performance differences could be within normal variation, particularly given the modest absolute improvements typical in this domain. The claim of consistent superiority across all metrics and datasets requires rigorous statistical support.
- **Resolution test** Provide per-dataset performance distributions, report effect sizes with confidence intervals, apply appropriate multiple testing corrections, and include statistical tests for all six evaluation metrics. Consider paired non-parametric tests (e.g., Wilcoxon signed-rank) as complementary evidence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmarking fairness
- **Claim pointer** "BertSNR outperforms the existing state-of-the-art methods" and "superior performance compared to state-of-the-art methods across all datasets" (Sections 3.1 and 1)
- **Evidence pointer** Section 3.1, Section 2.3, Supplementary Methods
- **Concern** The manuscript does not describe the hyperparameter tuning process for the baseline methods (Matching, DeepSNR, D-AEDNET). It is unclear whether these baselines were optimized to the same extent as BertSNR. The description states that "all models were trained on the same training dataset" but does not specify whether the same cross-validation splits were used, whether baselines received equivalent hyperparameter optimization, or whether the evaluation protocol was identical across methods.
- **Why it matters** Unfair comparisons can lead to inflated claims of superiority. If baselines are not properly tuned, the reported performance gap may reflect suboptimal baseline configurations rather than genuine methodological advances.
- **Resolution test** Describe the hyperparameter search space and optimization procedure for each baseline method. Use identical data splits and evaluation protocols across all methods. Consider reporting results with baselines using their originally published hyperparameters as well as tuned versions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability validation
- **Claim pointer** "we enhanced the interpretability of the model through attentional weight visualization and motif analysis, and discovered the subtle relationship between attention weight and motif" (Abstract and Section 3.5)
- **Evidence pointer** Section 3.5, Figure 4, Section 2.4
- **Concern** The interpretability analysis is entirely qualitative. The manuscript shows attention maps and compares them to known motifs, but provides no quantitative measure of how well attention weights correlate with actual binding sites. The claim of a "subtle relationship" is vague and not supported by statistical evidence. The motif analysis in Section 3.6 compares against database motifs but does not report how many of the 33 datasets yielded significant matches, nor the distribution of P-values, e-values, and q-values.
- **Why it matters** Interpretability is a key claimed contribution. Without quantitative validation, the attention-based explanations remain anecdotal. The field increasingly demands rigorous evaluation of interpretability methods, and the current analysis does not meet this standard.
- **Resolution test** Compute quantitative metrics such as the correlation between attention weights and known binding site positions across datasets. Report the fraction of datasets where the top attention regions overlap with annotated motifs. For motif analysis, report the distribution of significance metrics and the number of datasets with significant matches. Consider comparing attention-based motif discovery against established methods like MEME.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "The BertSNR source code can be found at https://github.com/lhy0322/BertSNR" (Availability section)
- **Evidence pointer** Availability section, Section 2.3, Supplementary Tables S2-S3
- **Concern** The manuscript does not provide sufficient detail for reproduction. The exact data processing pipeline, model architecture specifications (number of layers, hidden dimensions, attention heads), training hyperparameters (learning rate, batch size, optimizer), and the λ balancing parameter for the multi-task loss are not fully described in the main text. The supplementary tables are referenced but not provided for review. The GitHub repository could not be assessed from the manuscript alone.
- **Why it matters** Reproducibility is a fundamental requirement for computational biology methods. Without complete implementation details, other researchers cannot validate or build upon the work.
- **Resolution test** Provide complete architecture specifications, training details, and data processing code. Ensure the GitHub repository contains all necessary scripts, configuration files, and instructions for reproducing the reported results. Include a detailed README with dependencies and usage examples.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, data description
- **Evidence pointer** Section 2.1, Supplementary Tables S1-S2
- **Issue** The description of the 188 datasets is incomplete. The manuscript states that data were obtained from JASPAR with ChIP-seq experiments, but does not specify the cell types, experimental conditions, or how binding sites were defined (e.g., peak calls, motif instances). The relationship between the 188 prediction datasets and the 33 motif analysis datasets is unclear.
- **Required correction** Provide a detailed description of the data sources, including cell types, peak calling methods, and the criteria for including datasets. Clarify how the 33 motif analysis datasets were selected and whether they overlap with the 188 prediction datasets.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Section 2.2.4, multi-task learning
- **Evidence pointer** Section 2.2.4, Equation for loss function
- **Issue** The loss function is defined as Loss = λ * loss_sequence + (1-λ) * loss_token, but the manuscript does not specify the value of λ used in experiments or whether it was tuned. The relative weighting of the two tasks can significantly affect performance.
- **Required correction** Report the value of λ used and describe any sensitivity analysis or tuning performed. If λ was fixed, justify the choice.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evaluation metrics
- **Affected element** Section 3.1, evaluation
- **Evidence pointer** Section 3.1, Figure 3a
- **Concern** The manuscript reports six metrics but does not discuss potential class imbalance issues. With a 1:15 positive-to-negative ratio at the nucleotide level, accuracy can be misleading. The choice of AUPR as the primary metric is appropriate, but the manuscript should discuss the implications of class imbalance for the reported metrics.
- **Required correction** Add a discussion of class imbalance and its effect on the reported metrics. Consider reporting Matthews correlation coefficient or balanced accuracy as additional metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Related work
- **Affected element** Section 1, Introduction
- **Evidence pointer** Section 1
- **Issue** The introduction does not adequately discuss recent deep learning approaches for nucleotide-resolution TFBS prediction beyond DeepSNR and D-AEDNet. There are other relevant methods (e.g., BPNet, FactorNet, ChIP-nexus based approaches) that should be mentioned and compared.
- **Required correction** Expand the related work discussion to include recent nucleotide-resolution prediction methods and clarify the specific advantages of the proposed approach over these alternatives.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 4
- **Evidence pointer** Figure 4
- **Issue** The attention visualization figures are described but not visible in the manuscript text. The description of Figure 4b mentions "darker colors indicate higher attention weights" but does not explain how the attention weights are aggregated across heads and layers for visualization.
- **Required correction** Clarify the visualization methodology, including how attention weights are aggregated and normalized. Ensure the figures are legible and include appropriate color scales and annotations.

## Risk / unsupported claims
- The claim of "superior performance compared to state-of-the-art methods across all datasets" is not supported by the provided evidence, as statistical significance is only reported for one metric against one baseline.
- The claim of discovering a "subtle relationship between attention weight and motif" is not quantitatively validated.
- The claim that BertSNR "effectively identifies TFBSs in promoter regions" is based on a single example (POU5F1) and lacks systematic evaluation.
- The performance comparison against "state-of-the-art methods" is incomplete, as the manuscript does not compare against recent transformer-based or other nucleotide-resolution methods beyond the two cited baselines.
- The generalizability of the framework beyond human data is not assessed, despite the claim of a "generalized model."
- The computational cost and efficiency of BertSNR compared to baselines are not reported, which is relevant for practical utility.