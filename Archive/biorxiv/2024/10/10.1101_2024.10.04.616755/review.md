## Review setup
- **Input scope** Full manuscript text (abstract, introduction, background, methods, results, discussion, conclusion, supplementary references) as provided in the submission.
- **Assessment boundary** Scientific and technical evaluation of the claims, methodology, results, and reproducibility as presented in the supplied material. No external data or code verification performed.
- **Shared manuscript claim summary** The authors claim that a feed-forward neural network trained on ProtT5 protein language model embeddings, named pLM-DBPs, achieves superior performance for plant DNA-binding protein prediction compared to existing tools, with an MCC of 83.8% on an independent test set, and that the methodology generalizes to multiclass DNA/RNA/SSB classification tasks.
- **Visible evidence base** Abstract, Introduction, Background, Existing tools, Proposed work, Materials and Methods (Dataset, Workflow, Feature extraction, Model selection), Results and Discussion (5-fold cross-validation, Feature analysis, Independent test comparison, Multiclass evaluation), Conclusion, Author contributions, Supplementary materials description, Data availability statement.
- **Missing materials affecting confidence** Full tables (Table 1, 2, 3, 4, 5) and figures (Figure 1, 2, 3, 4, 5) referenced in the text are not provided. Supplementary information (Table T1, T2, Figure S1) is not provided. Detailed hyperparameter search ranges and final model training configurations are not fully specified. Statistical significance testing results are not reported.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant gap in plant-specific DNA-binding protein prediction by applying protein language model embeddings. The methodological approach is reasonable and the reported performance improvements are potentially significant. However, the absence of key tables, figures, and supplementary materials prevents a full evaluation of the claims. The comparison with existing tools relies heavily on previously reported results, and the lack of statistical significance testing weakens the strength of the performance claims. The multiclass generalization experiment is promising but requires more detail on dataset composition and class balance.
- **Who would be interested in the results, and why** Researchers in plant genomics, computational biology, and protein function prediction would be interested. The work demonstrates a practical application of protein language models to a plant-specific prediction task, which could inform similar approaches for other plant protein functions. Agricultural biotechnologists may find the potential for crop improvement applications relevant.
- **Major strengths** The study addresses a clear gap in plant-specific DBP prediction. The exploration of multiple pLMs (ProtT5, Ankh, ESM-2 variants) is systematic. The final model architecture is simple and computationally efficient, which is practical for broader use. The inclusion of a multiclass generalization experiment adds value beyond the primary binary classification task. The data and code availability statement supports reproducibility.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing data presentation), R1-M2 (lack of statistical significance testing), R1-M3 (incomplete comparison methodology), R1-M4 (insufficient multiclass dataset details).
- **Assessment against Nature-style criteria** Originality: Moderate. The application of pLMs to plant DBP prediction is novel in the specific context, but the general approach of using pLM embeddings for protein function prediction is well established. Scientific importance: Moderate. The work addresses a practical gap but does not introduce fundamentally new biological insights or methodological paradigms. Interdisciplinary readership: Limited. The work is primarily of interest to computational biologists and plant scientists, with limited appeal beyond these fields. Technical soundness: Currently not fully assessable due to missing tables, figures, and supplementary materials. The described methodology is sound in principle, but the evidence base is incomplete. Readability for nonspecialists: The manuscript is generally readable, but the results section relies heavily on tables and figures that are not provided, making it difficult for nonspecialists to follow the performance comparisons.
- **Recommendation posture** Currently not established from the provided evidence. The core claims are plausible but cannot be fully verified without the missing data. The manuscript would benefit from major revisions to present complete results and strengthen the statistical analysis.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim superior performance of pLM-DBPs with MCC of 83.8% on the independent test set and comprehensive outperformance of existing tools.
- **Evidence pointer** Tables 1, 4, 5; Figures 2, 4; location not provided
- **Concern** The manuscript references multiple tables and figures that are essential for evaluating the claims, but none of these are included in the provided material. Table 4 (cross-validation results), Table 5 (independent test comparison), and Figure 4 (radar plot) are critical for assessing the performance claims. Without these, the reader cannot verify the reported MCC values, compare metrics across models, or evaluate the claimed superiority.
- **Why it matters** The central claims of the manuscript rest entirely on quantitative performance comparisons. The absence of the actual data tables and figures makes the results impossible to verify or reproduce from the manuscript alone. This is a fundamental issue that prevents any meaningful assessment of the work.
- **Resolution test** Provide all referenced tables and figures in full. Ensure that Table 4 includes all models tested with all metrics (Sn, Sp, ACC, MCC, AUROC, AUPR) with standard deviations. Table 5 must include all comparison tools with all metrics. Figure 4 should be a clear radar plot with labeled axes and values.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that pLM-DBPs outperforms existing approaches and that the performance improvement is significant.
- **Evidence pointer** Results and Discussion, Comparison with existing approach; location not provided
- **Concern** No statistical significance testing is reported for any of the performance comparisons. The claim of "superior performance" and "10% improvement" over the previous state-of-the-art is presented without confidence intervals, p-values, or any measure of variance across multiple runs or cross-validation folds. The statement that ProtT5 showed "slightly better performance" than ESM models is noted as "not statistically significant," but no formal test is described.
- **Why it matters** In machine learning applications, performance differences between models can arise from random variation, especially with small datasets. Without statistical testing, the reader cannot determine whether the reported improvements are robust or merely artifacts of a particular data split or training run. This is essential for establishing the reliability of the claims.
- **Resolution test** Report mean and standard deviation for all metrics across cross-validation folds. Perform and report appropriate statistical tests (e.g., paired t-test, Wilcoxon signed-rank test) for comparisons between pLM-DBPs and each baseline model on the independent test set. State the significance threshold used.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparison methodology
- **Claim pointer** The authors claim that pLM-DBPs outperforms existing tools including DNAbinder, DPP_PseAAC, IDRBP_MMC, IDRBP-PPCT, PDBP-fusion, DeepDRBP, StackDPPred, and PlDBPred.
- **Evidence pointer** Results and Discussion, Comparison with existing approach; location not provided
- **Concern** The manuscript states that "most of the comparison results are adopted from PlDBPred." This raises concerns about the fairness and consistency of the comparison. It is unclear whether the baseline tools were retrained on the same training data, whether the same independent test set was used for all tools, and whether the hyperparameters for the baselines were optimized. If the comparison results are taken from a previous publication, the experimental conditions may differ.
- **Why it matters** For a fair comparison, all methods should be evaluated under identical conditions, including the same data splits, preprocessing steps, and evaluation protocols. Adopting results from a previous study introduces potential confounds that could bias the comparison in favor of the proposed method.
- **Resolution test** Clearly describe the comparison protocol. If baseline results are adopted from PlDBPred, state this explicitly and justify why the comparison is valid. Ideally, retrain all baseline models on the same training set and evaluate on the same independent test set. Report any differences in data preprocessing or evaluation protocols.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Multiclass evaluation completeness
- **Claim pointer** The authors claim that their methodology generalizes well to multiclass DNA/RNA/SSB classification, with substantial improvements over previously reported accuracies.
- **Evidence pointer** Results and Discussion, Evaluation of methodology on the multiclass DNA/RNA/SSB dataset; location not provided
- **Concern** The multiclass experiment is described briefly without details on the dataset composition, class distribution, or the specific architecture and training procedure used for this task. The reported improvements (e.g., SSB accuracy from 39.4% to 85.71%) are dramatic and would benefit from additional validation, such as confusion matrices or per-class precision and recall. It is also unclear whether the same ProtT5 features and ANN architecture were used directly or if modifications were made.
- **Why it matters** The multiclass experiment is presented as evidence of the methodology's generalizability, which is a significant claim. Without sufficient detail, the reader cannot assess the validity of the comparison or the robustness of the results. The large improvement in SSB classification, in particular, warrants closer scrutiny.
- **Resolution test** Provide a detailed description of the multiclass dataset, including class sizes and source. Describe the model architecture and training procedure used for this task. Report per-class precision, recall, and F1-score, and include a confusion matrix. Discuss any potential class imbalance issues and how they were addressed.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states "This represents a 10% improvement over the previous state-of-the-art model" but does not specify the metric on which this improvement is measured. It is unclear whether this refers to MCC, accuracy, or another metric.
- **Required correction** Specify the metric in the abstract, e.g., "10% improvement in MCC over the previous state-of-the-art model."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model training details
- **Evidence pointer** Materials and Methods, Model selection; location not provided
- **Issue** The manuscript mentions using KerasTuner for hyperparameter optimization but does not provide the search space, the number of trials, or the final selected hyperparameters for the ANN model.
- **Required correction** Provide the hyperparameter search ranges and the final hyperparameter values for the ANN model in the main text or supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Cross-validation results
- **Evidence pointer** Results and Discussion, 5-fold cross-validation results; location not provided
- **Issue** The cross-validation results are described as "averages across all folds," but no standard deviations or variance measures are reported. This makes it difficult to assess the stability of the model performance.
- **Required correction** Report mean and standard deviation for all metrics across the five folds.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3 description
- **Evidence pointer** Results and Discussion, Analysis of features; location not provided
- **Issue** The description of Figure 3 states that the UMAP projections show "clear separation" and "even clearer distinction" but does not provide any quantitative measure of cluster separation or overlap.
- **Required correction** Consider adding a quantitative cluster separation metric (e.g., silhouette score) to support the visual interpretation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Supplementary materials
- **Evidence pointer** Supplementary Materials section; location not provided
- **Issue** The supplementary materials are mentioned but not provided. The manuscript references Table T1, Table T2, and Figure S1, which are essential for understanding the pooling comparison and model architecture details.
- **Required correction** Ensure all supplementary materials are included with the submission and referenced appropriately in the text.

## Risk / unsupported claims
- The claim of "10% improvement over the previous state-of-the-art model" is not verifiable without the actual performance tables and specification of the metric.
- The claim of "comprehensive outperformance" over existing tools is not verifiable without Table 5 and Figure 4.
- The claim that the methodology "generalizes well" to multiclass classification is not fully supported without detailed dataset and model descriptions.
- The statement that "the choice of pLM is not critical" is based on a comparison that is described as "not statistically significant," but no statistical test is reported.
- The claim that the UMAP visualization shows "clear separation" is subjective and not quantitatively supported.
- The overall performance claims cannot be fully assessed due to the absence of all referenced tables, figures, and supplementary materials.