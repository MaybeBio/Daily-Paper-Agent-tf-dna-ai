## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose DeepD2V, a hybrid deep learning framework combining CNN and bi-LSTM with word2vec-based k-mer embeddings and combined DNA sequence inputs (original, inverse, complementary, complementary inverse) to predict transcription factor binding sites, reporting superior performance over existing methods on 50 ChIP-seq benchmark datasets.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Conclusions, Figures 1-9 (referenced), Table 1-2 (referenced), Supplementary File (referenced)
- **Missing materials affecting confidence** Actual figure images, table data, supplementary file contents, source code, and dataset access details are not provided; statistical significance testing details are absent

## Reviewer
- **Overall assessment** The manuscript presents a reasonable engineering contribution combining existing techniques (word2vec, CNN, bi-LSTM) for TF binding site prediction. The core novelty is limited to the combination of components rather than fundamental methodological advances. The experimental design is adequate but lacks rigorous statistical validation and comparison fairness. The claims of superiority are only partially supported by the evidence described.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those developing or applying deep learning methods for sequence-based functional prediction. The work may also interest researchers exploring word embedding techniques for biological sequences.
- **Major strengths** 1) Systematic evaluation across 50 public benchmark datasets provides breadth. 2) Ablation studies (Section 3.2-3.4) help isolate contributions of individual components. 3) Clear description of the pipeline from sequence conversion to model architecture. 4) Code and data availability statements are provided.
- **Major Concerns** [R1-M1, R1-M2, R1-M3, R1-M4]
- **Minor Comments** [R1-m1, R1-m2, R1-m3, R1-m4]
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical validation), R1-M2 (comparison fairness), R1-M3 (parameter optimization details)
- **Assessment against Nature-style criteria** Originality: Moderate. The combination of word2vec, CNN, and bi-LSTM is not conceptually new, though the specific integration for this task has limited precedent. Scientific importance: Moderate. TF binding prediction is an active field, but incremental improvements over existing methods without clear biological insights limit broader impact. Interdisciplinary readership: Limited. The work is primarily of interest to computational specialists; biological insights are not deeply explored. Technical soundness: Adequate but with gaps in statistical rigor and comparison methodology. Readability for nonspecialists: Acceptable. The manuscript is generally clear, though some methodological details assume familiarity with deep learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical validation and comparison fairness.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims "superior performance and robustness of DeepD2V" and "DeepD2V performs superior to DeepBind, DanQ, and WSCNNLSTM" based on average metrics across 50 datasets.
- **Evidence pointer** Section 3.5, Figures 8-9, Table 2
- **Concern** The performance comparisons lack any statistical significance testing. With 50 datasets, paired tests (e.g., Wilcoxon signed-rank test) should be applied to determine whether observed differences in AUC and F1-score are statistically significant. The scatter plots in Figure 8 show individual dataset performance, but no confidence intervals or p-values are reported.
- **Why it matters** Without statistical validation, the claimed superiority could be due to random variation. The field requires rigorous evidence before accepting new methods as state-of-the-art.
- **Resolution test** Provide paired statistical tests (e.g., Wilcoxon signed-rank) comparing DeepD2V against each baseline across the 50 datasets for all reported metrics, with effect sizes and confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparison fairness
- **Claim pointer** The manuscript states "All competing methods are run using the source code released by their authors" and "we optimize the hyper-parameters of these competing methods via cross-validation."
- **Evidence pointer** Section 3.5
- **Concern** The description of hyperparameter optimization for competing methods is vague. It is unclear whether the same computational budget, search space, and cross-validation procedure were used for baselines as for DeepD2V. If baselines were not optimized to the same extent, comparisons may be biased in favor of DeepD2V.
- **Why it matters** Unfair comparisons undermine the validity of performance claims. The field requires consistent evaluation protocols for meaningful benchmarking.
- **Resolution test** Detail the exact hyperparameter search spaces, optimization budgets, and selection criteria for all methods. Ideally, use published optimal hyperparameters for baselines and demonstrate that results are reproducible.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Parameter optimization methodology
- **Claim pointer** The manuscript states "Hyper-parameters were sampled randomly from search space on each ChIP-seq data set and adjusted to optimal values via cross-validation" and "the model with the highest ROC AUC value on the validation set was selected."
- **Evidence pointer** Section 2.4, Table 1
- **Concern** The parameter optimization procedure is described at a high level without specifics. The search space ranges, number of random samples, and criteria for convergence are not provided. More critically, selecting the model based on validation ROC AUC and then reporting test performance on the same datasets risks overfitting to the validation set, especially with only three-fold cross-validation.
- **Why it matters** Reproducibility and generalizability are fundamental scientific requirements. Inadequate description of optimization prevents replication and raises concerns about potential validation set overfitting.
- **Resolution test** Provide complete hyperparameter search spaces, sampling strategy, and the distribution of selected hyperparameters across datasets. Consider nested cross-validation or reporting performance variability across folds.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The manuscript states "the combined sequences potentially capture high-order dependencies among different patterns of DNA sequences, such as implicit DNA shape" and "dna2vec embedding vector explicitly considers the distance and abstract dependencies among k-mers (including implicit DNA structure information)."
- **Evidence pointer** Sections 3.2-3.3, Conclusions
- **Concern** The biological interpretations are speculative and not directly tested. No analysis is provided to demonstrate that the learned embeddings or combined sequence inputs actually capture DNA shape or structural information. The claims about biological relevance are not supported by targeted experiments or analyses.
- **Why it matters** Overinterpretation of results without direct evidence can mislead readers and the field. Biological claims should be substantiated with appropriate analyses.
- **Resolution test** Provide analyses that directly test biological interpretations, such as examining whether learned filters correspond to known motifs, or comparing performance on datasets with known structural dependencies.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2
- **Evidence pointer** "the sequence with l bases is divided into (l−k + 1) k-mers" and "a new sequence with length ((l−k)s+1) words in total"
- **Issue** The formula for the number of k-mers appears inconsistent. With stride s, the number should be floor((l-k)/s) + 1, not (l-k)s+1. The text also states stride size 1 in one place but uses variable s in the formula.
- **Required correction** Correct the formula to reflect the actual number of k-mers with stride s, and clarify whether stride 1 is used throughout or if variable strides are considered.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.1
- **Evidence pointer** "we selected ∼15,000 top-ranking sequences as positive samples from each record in a peak file"
- **Issue** The criterion for "top-ranking" is not defined. It is unclear whether this refers to peak scores, signal values, or another metric. This affects reproducibility.
- **Required correction** Specify the exact ranking criterion used for selecting positive sequences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.1
- **Evidence pointer** "the model achieves better performance at k = 3" and "we set the k and s values to 3 and 1"
- **Issue** The parameter optimization was performed on only 23 datasets from one cell line (Gm12878), but the final model is applied to all 50 datasets. It is unclear whether optimal parameters are consistent across cell lines.
- **Required correction** Discuss whether parameter sensitivity was assessed across cell lines or justify the transferability of parameters.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.5
- **Evidence pointer** "the performance of DeepD2V was apparently higher than that of DeepBind"
- **Issue** The term "apparently" is informal and imprecise for a scientific manuscript. Quantitative differences should be stated with appropriate statistical measures.
- **Required correction** Replace informal language with precise quantitative statements and statistical evidence.

## Risk / unsupported claims
- The claim that "dna2vec embedding vector explicitly considers the distance and abstract dependencies among k-mers (including implicit DNA structure information)" is not directly supported by experiments in this manuscript.
- The claim that "combined sequences potentially capture high-order dependencies among different patterns of DNA sequences, such as implicit DNA shape" is speculative and untested.
- The assertion of "superior performance and robustness" lacks statistical significance testing and is therefore not fully supported.
- The statement that "DeepD2V achieves state-of-the-art performance" is not supported by comparison with all existing methods, only three specific baselines.
- The biological relevance of the approach is claimed but not demonstrated through functional validation or biological interpretation analyses.