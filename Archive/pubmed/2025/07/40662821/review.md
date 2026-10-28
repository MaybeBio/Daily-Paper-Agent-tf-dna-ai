## Review setup
- **Input scope** Full manuscript text (main text, methods, results, and discussion sections as provided)
- **Assessment boundary** Scientific and technical evaluation of the proposed method, experimental design, results, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose scRegNet, a framework combining single-cell foundation models (scBERT, Geneformer, scFoundation) with graph neural networks for gene regulatory link prediction. They claim state-of-the-art performance over nine baseline methods across seven BEELINE benchmark datasets, improved robustness to noisy training data, and biological relevance of predicted novel interactions.
- **Visible evidence base** Main text including Methods, Experimental setup, Results sections, Tables 1-3 referenced, Figures 1-3 referenced, Supplementary sections S1-S6 and Tables S1-S4 referenced
- **Missing materials affecting confidence** Full figures and tables not provided; Supplementary Material not provided; detailed hyperparameter settings not provided; specific numerical results for all datasets and baselines not fully visible; code repository not reviewed

## Reviewer
- **Overall assessment** The manuscript presents a reasonable integration of existing single-cell foundation models with graph-based learning for gene regulatory network inference. The core idea of combining pre-trained contextual gene representations with network topology is sensible and timely. However, the evaluation methodology raises several concerns regarding the validity of the claimed state-of-the-art performance, particularly around data leakage prevention, baseline fairness, and statistical significance. The robustness analysis is a positive contribution but is limited in scope. The biological validation is anecdotal and requires stronger evidence. The manuscript is clearly written and accessible, but the technical claims require substantial additional evidence to be fully established.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, single-cell analysis, and graph-based machine learning applications in genomics. The work may also interest researchers developing foundation models for biological data, as it demonstrates a downstream application of such models. The comparative evaluation across multiple foundation models and baselines provides useful practical guidance for method selection.

- **Major strengths** 
  1. Timely integration of single-cell foundation models with graph-based learning, addressing a relevant problem in GRN inference
  2. Comprehensive evaluation across seven benchmark datasets and nine baseline methods
  3. Inclusion of robustness analysis under noisy training data, which is practically relevant
  4. Clear writing and accessible presentation of methods
  5. Ablation studies and GNN architecture comparison provide useful insights

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their data splitting strategy "prevents data leakage by ensuring that the same gene does not appear in both the training and test sets for the same TF."
- **Evidence pointer** Section "Datasets and data pre-processing", location not provided
- **Concern** The described splitting strategy is per-TF, meaning that for each TF, positive and negative target genes are divided into training and test sets. However, the same target gene can appear in the training set for one TF and in the test set for another TF. Since the model learns gene-level representations that are shared across all TF-gene pairs, this creates a potential information leak where the model may have seen the same gene in a different context during training. The claim of no data leakage is therefore not fully supported by the described methodology.
- **Why it matters** Data leakage can inflate performance estimates and undermine the validity of the claimed state-of-the-art results. If gene-level representations are learned from training pairs involving a gene, the model may perform artificially well on test pairs involving the same gene, even if the specific TF-gene relationship is novel.
- **Resolution test** The authors should clarify whether any gene appears in both training and test sets across different TFs. If so, they should either implement a gene-disjoint split or demonstrate that the current approach does not lead to inflated performance through additional experiments with gene-disjoint splits.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim scRegNet "achieves state-of-the-art results in comparison with nine baseline methods on seven scRNA-seq benchmark datasets."
- **Evidence pointer** Section "Performance on benchmark datasets", Tables 2 and 3, location not provided
- **Concern** The reported improvements are presented as average percentages, but no statistical significance testing is reported. It is unclear whether the observed differences between scRegNet and the best baselines are statistically significant across the seven datasets. Additionally, the variance across datasets is not reported, making it difficult to assess the consistency of the improvements.
- **Why it matters** Without statistical significance testing or variance reporting, the claim of state-of-the-art performance cannot be rigorously evaluated. Small average improvements may not be meaningful if the variance across datasets is high.
- **Resolution test** The authors should report per-dataset results with confidence intervals or perform paired statistical tests (e.g., Wilcoxon signed-rank test) across the seven datasets to demonstrate that the improvements are statistically significant.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "We leveraged Optuna, a powerful hyperparameter optimization framework, to systematically explore the search space."
- **Evidence pointer** Section "Parameter settings", Supplementary Table S2, location not provided
- **Concern** The hyperparameter search space and the final selected hyperparameters are not described in the main text. The authors refer to Supplementary Table S2, but this material is not available for review. Without this information, the reproducibility of the results is limited, and it is unclear whether the baselines were tuned to the same extent as scRegNet.
- **Why it matters** Hyperparameter tuning can significantly affect model performance. If baselines were not tuned as extensively as scRegNet, the comparison may be unfair. Reproducibility is a core requirement for computational biology methods.
- **Resolution test** The authors should provide the full hyperparameter search space and final settings for all models in the main text or ensure the supplementary material is accessible. They should also confirm that baselines were tuned with comparable effort.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "predicted interactions such as NANOG→BMPR1A, JUND→SNAI2, and OTX2→CITED2 align closely with established roles of these factors in pluripotency maintenance, differentiation, and early developmental transitions."
- **Evidence pointer** Section "Robustness study", Supplementary Section S5, Supplementary Table S3, location not provided
- **Concern** The biological validation is limited to three anecdotal examples on a single dataset (hESC). No systematic enrichment analysis or comparison against known GRN databases is provided. The authors do not quantify how many of the novel predictions are supported by external evidence.
- **Why it matters** The biological relevance of predictions is a key claim of the manuscript. Anecdotal examples are insufficient to establish that the method produces biologically meaningful novel predictions at scale.
- **Resolution test** The authors should perform a systematic evaluation of predicted novel interactions against external databases (e.g., ChIP-seq databases, literature-curated interactions) and report the fraction of predictions with external support, potentially using enrichment analysis.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "scRegNet is more robust than the baseline methods on noisy training data."
- **Evidence pointer** Section "Robustness study", Figure 3, location not provided
- **Concern** The robustness analysis is only performed for noise levels up to 4%, and only against a single baseline (GENELink). The authors mention extended analysis in Supplementary Section S6, but this is not available. It is unclear whether the robustness advantage holds at higher noise levels and against other baselines.
- **Why it matters** The robustness claim is presented as a key advantage of the method. Limited evaluation against a single baseline at low noise levels is insufficient to establish this claim broadly.
- **Resolution test** The authors should extend the robustness analysis to higher noise levels, include multiple baselines, and report the full results in the main text or ensure the supplementary material is available.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Gene representations from foundation models"
- **Evidence pointer** Location not provided
- **Issue** The description of how the three foundation models are applied is brief. It is unclear whether the models are used in a zero-shot manner or fine-tuned on the benchmark datasets.
- **Required correction** Clarify whether the foundation models are frozen or fine-tuned, and describe the exact procedure for extracting gene-level embeddings from each model.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Datasets and data pre-processing"
- **Evidence pointer** Location not provided
- **Issue** The description of the negative sampling strategy is incomplete. The authors state that negative samples are "gene pairs with no known regulatory interactions" but do not specify how these are selected (e.g., random sampling, degree-matched sampling).
- **Required correction** Provide details on the negative sampling strategy, including any constraints applied to ensure a balanced and realistic evaluation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section "Model training"
- **Evidence pointer** Location not provided
- **Issue** The training procedure is described at a high level, but key details such as learning rate, batch size, number of epochs, and early stopping criteria are not provided in the main text.
- **Required correction** Include the key training hyperparameters in the main text or ensure they are fully documented in the supplementary material.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Impact of GNN architecture"
- **Evidence pointer** Supplementary Table S4, location not provided
- **Issue** The conclusion that "all GNN variants show similar performance" is stated without reporting the actual performance values or the range of differences.
- **Required correction** Report the actual performance values for each GNN variant in the main text or provide a summary of the differences.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Conclusions and discussions"
- **Evidence pointer** Location not provided
- **Issue** The discussion of limitations is brief and does not address potential issues with the evaluation methodology, such as the data leakage concern raised above.
- **Required correction** Expand the limitations section to acknowledge the potential for gene-level information leakage and discuss its implications.

- **Technical failings that need to be addressed before the case is established** R1-M1 (data leakage), R1-M2 (statistical significance), R1-M3 (reproducibility of hyperparameters)

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The combination of foundation models with GNNs for GRN inference is a reasonable extension of existing work, but the individual components are well-established. The novelty lies primarily in the integration rather than in a fundamentally new approach.
  - **Scientific importance** Moderate. GRN inference is an important problem, and the use of foundation models is timely. However, the demonstrated improvements over existing methods are incremental, and the biological validation is limited.
  - **Interdisciplinary readership** Moderate. The work bridges machine learning and computational biology, which may appeal to readers in both fields. However, the methods are largely incremental, and the biological insights are limited.
  - **Technical soundness** Currently insufficient. The data leakage concern and lack of statistical significance testing undermine the validity of the main claims. The robustness analysis is limited in scope.
  - **Readability for nonspecialists** Good. The manuscript is clearly written, with accessible explanations of the methods and motivation. The figures and tables are referenced appropriately, though not available for review.

- **Recommendation posture** Currently not established from the provided evidence. The core claims of state-of-the-art performance and robustness require additional evidence to address the data leakage concern, statistical significance, and reproducibility issues. The manuscript has potential, but the technical concerns must be resolved before the case is established.

## Risk / unsupported claims
- The claim that the data splitting strategy "prevents data leakage" is not fully supported by the described methodology, as gene-level overlap across TFs may still occur.
- The claim of "state-of-the-art results" is not supported by statistical significance testing or variance reporting.
- The claim of "more robust than the baseline methods" is based on limited evaluation against a single baseline at low noise levels.
- The biological relevance of predicted interactions is supported only by anecdotal examples, not by systematic evaluation.
- The reproducibility of the results cannot be assessed without access to the supplementary material and code.