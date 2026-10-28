## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and figure legends
- **Assessment boundary** Scientific soundness, technical validity, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present BioSeq2Seq, a transformer-based deep learning framework that integrates RO-seq data and DNA sequence to predict histone modifications, functional elements, gene expression, and transcription factor binding sites across cell lines and species, claiming state-of-the-art performance with single-cell-line training data.
- **Visible evidence base** Main text figures 1-7 (legends only), supplementary figure and table references, methods section, and abstract
- **Missing materials affecting confidence** Actual figure images, supplementary figures S1-S25, supplementary tables S1-S10, source data files, and code repository contents were not provided for verification

## Reviewer
- **Overall assessment** The manuscript presents a technically ambitious deep learning framework that addresses a genuine need in regulatory genomics. The core idea of combining RO-seq with DNA sequence in a tri-modal representation is conceptually sound and potentially valuable. However, the evidence provided in the text is insufficient to fully evaluate the claimed performance improvements, particularly regarding statistical rigor, baseline fairness, and generalizability claims. Several methodological details require clarification, and the absence of actual figure data limits verification of the quantitative claims.
- **Who would be interested in the results, and why** Computational biologists developing deep learning methods for genomics, researchers using RO-seq for genome annotation, and experimentalists seeking cost-effective alternatives to comprehensive ChIP-seq profiling across cell types and species. The framework's potential for cross-species generalization would interest comparative genomics groups.
- **Major strengths** The framework addresses a practical bottleneck in genome annotation by reducing the need for multiple molecular assays. The unified architecture across four distinct tasks is elegant and potentially impactful. The use of a single-cell-line training strategy with demonstrated cross-cell-line and cross-species generalization is a notable contribution if the claims hold. The computational efficiency gains over dHIT are practically significant.
- **Major Concerns** The statistical analysis appears incomplete, with no confidence intervals or significance testing reported for the main performance comparisons. The baseline comparisons may not be entirely fair given different training data and architectural assumptions. The claim of "end-to-end generalizable" is not fully supported by the evidence presented, as the generalization experiments appear limited in scope. The peak calling algorithm's statistical foundation requires more rigorous validation.
- **Minor Comments** Several methodological details are underspecified, including exact hyperparameter choices, data preprocessing steps, and the handling of imbalanced classes in TFBS prediction. The manuscript would benefit from clearer descriptions of the baseline methods and their configurations.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The tri-modal input strategy combining RO-seq with DNA sequence is a novel contribution, though the overall approach builds on established transformer architectures for genomics. Scientific importance: The potential to reduce experimental burden for genome annotation is significant, but the demonstrated impact is currently limited to the presented benchmarks. Interdisciplinary readership: The work bridges deep learning and regulatory genomics, with clear relevance to both communities. Technical soundness: The architecture is reasonable, but the evaluation methodology has gaps that need addressing. Readability for nonspecialists: The manuscript is generally well-written, though some technical sections assume substantial background knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical rigor, baseline fairness, and validation of the generalization claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims improvements of 14.27% in histone modification prediction, 2.50% in functional element identification, and 2.90% in gene expression prediction over state-of-the-art methods.
- **Evidence pointer** Results sections on histone modification prediction, functional element identification, and gene expression prediction; Figures 3b, 5d, 6b
- **Concern** The reported performance improvements are presented as point estimates without any measure of variability, confidence intervals, or statistical significance testing. For example, the 14.27% improvement over dHIT is reported as a single value, but it is unclear how this was computed across the seven cell lines and whether the improvement is consistent or driven by specific cell lines. The manuscript states that "individual data points across seven cell lines" are overlaid on bar plots in Figure 3a, but no statistical comparison between methods is described. Similarly, the comparison with dHIT in Figure 3b appears to be based on a single holdout chromosome, which may not be representative.
- **Why it matters** Without proper statistical analysis, the claimed improvements cannot be distinguished from noise or favorable data splits. This is particularly important given the variability in genomic data across cell lines and the known sensitivity of deep learning models to training data composition.
- **Resolution test** Provide confidence intervals or perform statistical significance testing (e.g., paired tests across cell lines or bootstrap resampling) for all reported performance comparisons. Report the distribution of performance across cell lines and chromosomes, not just aggregate statistics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline fairness
- **Claim pointer** The manuscript claims state-of-the-art performance compared to dHIT, dREG, and TransformerChrome.
- **Evidence pointer** Results sections on histone modification prediction, functional element identification, and gene expression prediction; Figures 3b, 5d, 6b
- **Concern** The baseline methods may not be evaluated under comparable conditions. For example, dHIT is described as predicting histone modifications at a single site using 50k-bp of genomic features, while BioSeq2Seq predicts within a 114k-bp window using 197k-bp of context. This difference in input context could explain part of the performance gap. Similarly, the comparison with dREG for TIR identification uses different underlying data and thresholds. For gene expression prediction, the comparison with TransformerChrome may involve different training data and feature sets. The manuscript does not describe whether baselines were retrained, fine-tuned, or used with their default configurations.
- **Why it matters** Unfair comparisons undermine the claim of state-of-the-art performance. If baselines are evaluated under suboptimal conditions, the reported improvements may not reflect genuine architectural advantages.
- **Resolution test** Describe the exact configuration of all baseline methods, including whether they were retrained on the same data, and discuss how differences in input context and training data were controlled. Consider ablations that match input context size across methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability claims
- **Claim pointer** The abstract states that BioSeq2Seq is "an end-to-end generalizable deep learning framework" and the introduction claims it can be used "in a variety of cell lines, tissues, and species."
- **Evidence pointer** Abstract; Introduction; Results sections on cross-cell-line and cross-species evaluation
- **Concern** The evidence for generalizability appears limited. The manuscript describes training on K562 data and evaluating on other cell lines and species, but the number of cell lines and species tested is not clearly stated in the text provided. The cross-species evaluation includes mouse, horse, and Drosophila, but it is unclear how many samples per species and whether the performance is consistent. The claim of "end-to-end generalizable" is strong and would require demonstration across a diverse range of cell types and conditions, including those substantially different from the training data.
- **Why it matters** Generalizability is a central claim of the manuscript and a key motivation for the framework. If the evaluation is limited to a small number of closely related cell types, the claim is overstated.
- **Resolution test** Clearly state the number and diversity of cell lines, tissues, and species used for evaluation. Provide per-cell-line and per-species performance breakdowns. Discuss any observed limitations in generalization and potential reasons.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Peak calling validation
- **Claim pointer** The manuscript states that a "dedicated statistical peak-calling algorithm" was developed to convert continuous predictions into discrete functional element calls, with a p value threshold of 1e-3.
- **Evidence pointer** Methods section on peak calling; Results section on functional element identification; Figure 5
- **Concern** The statistical foundation of the peak calling algorithm is not fully described. The manuscript mentions a "five-dimensional multivariate Gaussian distribution" and a "cumulative distribution function as the p value," but the derivation of this distribution, the estimation of its parameters, and the validation of the normality assumption are not provided. The choice of the p value threshold (1e-3) is not justified, and no sensitivity analysis is presented. The manuscript also does not describe how the peak calling performance compares to established peak callers beyond the single comparison with dREG.
- **Why it matters** The peak calling algorithm is central to functional element identification, and its statistical validity directly affects the reliability of the reported results. Without proper validation, the identified elements may not be biologically meaningful.
- **Resolution test** Provide a detailed description of the statistical model, including parameter estimation and validation of assumptions. Perform sensitivity analysis on the p value threshold and compare peak calling performance against multiple established methods.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript states that the code is publicly available on GitHub and that pre-trained model weights are provided.
- **Evidence pointer** Discussion section; Data availability statement (not provided in the text)
- **Concern** The manuscript does not provide a data availability statement or a code availability statement in the text provided. While the discussion mentions GitHub, the specific repository URL, version, and documentation are not provided. The manuscript also does not describe the computational environment, dependencies, or instructions for reproducing the results. The training data sources are described, but the exact preprocessing pipelines and data splits are not fully specified.
- **Why it matters** Reproducibility is essential for the scientific community to build upon this work. Without clear availability statements and detailed protocols, other researchers cannot verify or extend the results.
- **Resolution test** Provide a data availability statement and a code availability statement with the repository URL, version, and documentation. Describe the computational environment and provide detailed instructions for data preprocessing, training, and evaluation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3a
- **Evidence pointer** Results section on histone modification prediction
- **Issue** The description of Figure 3a mentions "six types of MSEs" but the text does not explain what these six types are. It is unclear whether these correspond to different input modalities, different histone modifications, or different evaluation settings.
- **Required correction** Clarify what the six MSE types represent and how they were computed.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** TFBS prediction evaluation
- **Evidence pointer** Results section on TFBS prediction; Figure 7
- **Issue** The manuscript reports AUPR, Pearson correlation, and precision at 5% recall for TFBS prediction, but does not report recall at fixed precision thresholds or other operating points that might be more relevant for practical use.
- **Required correction** Consider reporting additional metrics or a precision-recall curve summary to provide a more complete picture of performance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** Model architecture
- **Evidence pointer** Methods section on model architecture
- **Issue** The manuscript describes the use of "gradient-guided architectural refinement" but does not explain what this means in practice. It is unclear whether this refers to neural architecture search, pruning, or some other technique.
- **Required correction** Provide a clear explanation of the architectural refinement process and how it was applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Context
- **Affected element** Comparison with existing methods
- **Evidence pointer** Introduction; Results sections
- **Issue** The manuscript does not discuss recent deep learning approaches for similar tasks beyond the specific baselines compared. A broader discussion of related work would help position the contribution.
- **Required correction** Add a brief discussion of other recent deep learning methods for regulatory genomics and how BioSeq2Seq differs.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Practical guidance
- **Affected element** Model usage
- **Evidence pointer** Discussion
- **Issue** The manuscript does not provide guidance on the minimum quality or characteristics of RO-seq data required for reliable predictions, which would be useful for potential users.
- **Required correction** Add a note on data requirements and potential limitations when applying the model to lower-quality or non-standard RO-seq datasets.

## Risk / unsupported claims
- The claim of "end-to-end generalizable" is not fully supported by the evidence presented, as the diversity and number of evaluation cell lines and species are not clearly documented.
- The reported performance improvements over baselines lack statistical significance testing and confidence intervals.
- The claim that BioSeq2Seq "provides an efficient and low-cost alternative for genome annotation" is not quantified in terms of cost or time savings beyond the computational speed comparison with dHIT.
- The statement that the framework "enables flexible genome annotation tasks through parameterized configurations" is not demonstrated with concrete examples of such configurations.
- The claim that the model "avoids misinterpretation in genomic regions with weak RO-seq signal" is based on qualitative visual inspection and lacks quantitative validation.
- The generalizability of the peak calling algorithm to different data types and quality levels is not established.