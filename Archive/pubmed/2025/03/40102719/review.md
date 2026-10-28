## Review setup
- **Input scope** Full manuscript text (abstract, background, results, discussion, methods) as provided
- **Assessment boundary** Scientific and technical evaluation of the manuscript claims, methodology, and results as presented
- **Shared manuscript claim summary** The authors propose CacPred, a cascaded convolutional neural network for TF-DNA binding prediction, and claim it outperforms six existing deep learning models across 790 ChIP-seq and seven ChIP-nexus datasets on nine evaluation metrics, while also demonstrating interpretability through motif discovery
- **Visible evidence base** Main text, Figures 1-6, Table 1, references to supplementary tables (Table S1, Table S2) and supplementary files
- **Missing materials affecting confidence** Supplementary tables (S1, S2) and supplementary files are referenced but not provided; detailed hyperparameter values, training curves, statistical significance tests, and full comparison results across all 790 datasets are not shown; code repository contents not verified

## Reviewer

- **Overall assessment** The manuscript presents a straightforward application of cascaded convolutional neural networks to TF-DNA binding prediction. The core idea of using cascaded convolutions without pooling is not entirely novel, as similar architectures have been explored in other sequence classification tasks. The main strength is the large-scale evaluation across 790 ChIP-seq datasets and seven ChIP-nexus datasets. However, the reported improvements are modest and the manuscript lacks critical details on statistical significance, hyperparameter optimization, and architectural ablation studies. The interpretability analysis via motif discovery is a positive addition but is only demonstrated on a single dataset. The writing is generally clear but contains some inconsistencies and lacks depth in the discussion of limitations and comparison with state-of-the-art methods beyond the six selected baselines.

- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics working on transcription factor binding site prediction, regulatory genomics, and deep learning applications to genomics would be the primary audience. The large-scale benchmark comparison may be of interest to those seeking to select or develop models for TF-DNA binding prediction. The motif discovery component may appeal to those interested in model interpretability.

- **Major Strengths**
  1. Large-scale evaluation across 790 ChIP-seq datasets covering 261 TFs, providing a comprehensive benchmark.
  2. Inclusion of seven ChIP-nexus datasets to assess generalization to a different experimental protocol.
  3. Evaluation using nine metrics, including the AEMR composite score, providing a multi-faceted performance assessment.
  4. The model architecture is simple and computationally efficient, using only convolutional layers without pooling.
  5. Interpretability analysis through motif discovery adds practical value.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim CacPred "outperforms all comparison models" and report average improvements of 3.3% (ACC), 9.2% (MCC), and 6.4% (AEMR) on ChIP-seq data, and 5.5%, 16.8%, and 12.9% on ChIP-nexus data.
- **Evidence pointer** Results section, Figures 2-3, Table 1
- **Concern** The manuscript reports average improvements but does not provide any statistical significance testing (e.g., paired t-tests, Wilcoxon signed-rank tests) across the 790 datasets. Without such tests, it is impossible to determine whether the observed improvements are statistically significant or could arise from chance. Additionally, the distribution of performance differences across datasets is not shown, so the consistency of improvement is unclear.
- **Why it matters** Claims of superiority in a benchmark study require statistical validation to be credible. Without significance testing, readers cannot assess the reliability of the reported improvements, which is a fundamental requirement for a method comparison paper.
- **Resolution test** Provide statistical significance tests (e.g., paired Wilcoxon signed-rank test) comparing CacPred to each baseline across all 790 datasets for each metric, and report effect sizes and confidence intervals. Show the distribution of per-dataset performance differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The authors state that hyperparameters "are optimized by three-fold cross-validation on the training set" and that "when the AUC is highest in the validation set, hyperparameters are saved and applied to the testing data."
- **Evidence pointer** Experimental setup section
- **Concern** The manuscript does not report the specific hyperparameter values (e.g., learning rate, batch size, dropout ratio, number of filters, kernel sizes, optimization epochs) used in the final model. Additionally, the hyperparameter search space and the number of configurations tested are not described. This lack of detail prevents reproducibility and makes it difficult to assess whether the comparison with baselines is fair, as the baselines' hyperparameters may not have been optimized to the same extent.
- **Why it matters** Reproducibility is a core requirement for computational biology papers. Without detailed hyperparameter reporting, other researchers cannot replicate the experiments or apply the method to new data. Fair comparison with baselines requires equivalent hyperparameter tuning effort.
- **Resolution test** Provide a table listing all final hyperparameters for CacPred and each baseline model, describe the hyperparameter search procedure (e.g., grid search, random search) and the range of values explored, and state the number of configurations evaluated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Architectural justification
- **Claim pointer** The authors claim that "CacPred only is equipped with the convolutional algorithm, demonstrating that pooling processing of the existing models leads to losing some sequence information."
- **Evidence pointer** Discussion section
- **Concern** This is a strong causal claim about the role of pooling in performance degradation, but no ablation study is provided to support it. The authors do not compare CacPred to a version of the model with pooling layers, nor do they compare to a baseline without pooling. The observed performance difference could be due to other architectural differences (e.g., number of layers, filter sizes, skip connections) rather than the absence of pooling.
- **Why it matters** The central architectural insight of the paper is that pooling is detrimental. Without an ablation study, this claim is unsupported and the contribution of the cascaded design versus the removal of pooling cannot be disentangled.
- **Resolution test** Perform an ablation study where pooling layers are added to CacPred and where pooling is removed from a baseline model, and compare performance. Report these results to directly test the claim about pooling.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability validation
- **Claim pointer** The authors state that "motifs CacPred found are significant by comparing them to the motif database (HOCOMOCO.v11)" and that "five significant motifs are found" for the example dataset.
- **Evidence pointer** Explaining CacPred model section, Figure 5
- **Concern** The motif analysis is only demonstrated on a single dataset (wgEncodeEH001833). It is unclear how representative this is across the 790 datasets. Additionally, the significance threshold (p < 0.05) is mentioned, but the number of motifs compared, the multiple testing correction applied, and the fraction of datasets where significant motifs were found are not reported. The biological relevance of the discovered motifs is not discussed in detail.
- **Why it matters** Interpretability is a claimed contribution, but a single example is insufficient to establish that the model consistently learns meaningful motifs. Without broader validation, the interpretability claim remains anecdotal.
- **Resolution test** Report motif discovery results across a representative subset of datasets (e.g., 10-20 TFs), including the fraction of datasets with significant motif matches, the number of motifs tested, and the multiple testing correction used. Discuss the biological relevance of the discovered motifs.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The workflow figure is referenced but not described in the text. The figure legend is minimal and does not explain the steps or the data flow.
- **Required correction** Add a detailed figure legend describing each step of the workflow, including data preprocessing, model training, hyperparameter optimization, and evaluation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results section, ChIP-nexus validation
- **Evidence pointer** Validating CacPred on ChIP-nexus datasets section
- **Issue** The text states "all models are trained and tested on the seven ChIP-nexus datasets in the above way," but it is unclear whether the models were trained from scratch on ChIP-nexus data or fine-tuned from ChIP-seq pretrained models. This distinction is important for interpreting the results.
- **Required correction** Clarify the training procedure for the ChIP-nexus experiments, specifying whether models were trained from scratch or fine-tuned.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions future directions including graph neural networks but does not provide a concrete comparison or analysis of how CacPred might be extended. The discussion of limitations is brief and does not address potential overfitting, computational cost, or failure cases.
- **Required correction** Expand the discussion to include a more thorough analysis of limitations, such as the fixed input length, the binary classification setup, and potential biases in negative sample generation. Provide more concrete future directions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Methods section
- **Issue** The manuscript states the code is available at a GitHub repository, but the repository contents are not described. It is unclear whether the code includes training scripts, data preprocessing pipelines, and model definitions for all baselines.
- **Required correction** Describe the contents of the GitHub repository in the manuscript, including the structure, key scripts, and instructions for reproducing the experiments.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table reports mean values with standard deviations, but the number of datasets used for the ChIP-nexus results is only seven, which is a small sample size. The standard deviations may not be meaningful with such a small n.
- **Required correction** Acknowledge the small sample size for ChIP-nexus experiments and consider reporting individual dataset results or confidence intervals.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of statistical significance testing for performance comparisons
  - R1-M2: Insufficient hyperparameter reporting for reproducibility
  - R1-M3: No ablation study to support the claim about pooling
  - R1-M4: Motif analysis limited to a single dataset without broader validation

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. Cascaded convolutional architectures have been explored in other domains, and the application to TF-DNA binding is incremental. The removal of pooling is a minor architectural variation rather than a fundamentally new approach.
  - **Scientific importance**: Moderate. TF-DNA binding prediction is an important problem, and large-scale benchmarks are useful. However, the reported improvements are modest and the methodological novelty is limited, reducing the potential impact.
  - **Interdisciplinary readership**: Limited. The paper is primarily of interest to computational biologists and machine learning researchers working on genomics. The lack of biological validation and limited interpretability analysis reduces its appeal to a broader biological audience.
  - **Technical soundness**: The experimental setup is generally sound, but the lack of statistical testing, incomplete hyperparameter reporting, and absence of ablation studies undermine the technical rigor. The evaluation across 790 datasets is a strength, but the analysis of results is insufficiently deep.
  - **Readability for nonspecialists**: The paper is reasonably well-written and accessible to readers with a background in deep learning and genomics. However, some sections, particularly the methods, assume familiarity with convolutional architectures and ChIP-seq data. The figures are clear but could benefit from more detailed legends.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant problem and presents a large-scale evaluation, but the core claims of superiority and the architectural insight about pooling are not adequately supported. The lack of statistical testing, incomplete methodological details, and limited interpretability validation prevent the case from being fully established. The paper could become acceptable after major revisions addressing these concerns, but in its current form, the evidence is insufficient to support the claims.