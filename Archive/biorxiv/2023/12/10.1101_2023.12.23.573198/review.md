## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary data descriptions
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and clarity of the presented work
- **Shared manuscript claim summary** The authors present EnhancerTracker, a tool using an ensemble of deep separable convolutional neural networks to compare cell-type-specific enhancer activity across three DNA sequences, requiring only two known enhancers as reference. The tool is claimed to be applicable to all cell types, including those absent from training data, and outperforms traditional cell-type-specific enhancer prediction approaches.
- **Visible evidence base** Abstract, full methods description, results tables (Tables 1 and 2 referenced), figures (Figures 1-8 referenced), case study descriptions, and supplementary data descriptions
- **Missing materials affecting confidence** Actual figures and tables not visible in the provided text; supplementary tables and figures not accessible; no code or implementation details beyond a GitHub link; no comparison to existing tools with quantitative benchmarks

## Reviewer
- **Overall assessment** The manuscript presents an interesting and potentially useful approach to enhancer prediction that differs from existing cell-type-specific methods. The core idea of comparing sequence triplets rather than classifying single sequences is novel and could address the data sparsity problem in enhancer prediction for underrepresented cell types. However, the evidence provided in the text is insufficient to fully evaluate the claims. Key performance metrics are reported without adequate context, the case study results are described qualitatively, and critical details about the training procedure and model architecture are missing. The manuscript would benefit from clearer reporting of experimental design, more rigorous statistical analysis, and direct comparison with existing tools.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and gene regulation would be interested. The tool addresses a practical problem in enhancer annotation for cell types with limited experimental data. The triplet-based comparison approach could also interest machine learning researchers working on sequence analysis with limited training data.
- **Major strengths** The problem formulation is genuinely novel and addresses a real limitation of existing enhancer prediction tools. The data augmentation strategy is thoughtful and addresses the small-sample problem. The authors clearly articulate the distinction between their approach and traditional cell-type-specific classifiers. The case study design, using known enhancers to scan surrounding genomic regions, provides a practical demonstration of the tool's utility.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is high; the triplet-based comparison framework is a novel contribution. Scientific importance is moderate to high, as enhancer prediction for underrepresented cell types is an active problem. Interdisciplinary readership is plausible, spanning genomics and machine learning. Technical soundness cannot be fully assessed from the provided text due to missing experimental details and incomplete reporting of results. Readability for nonspecialists is adequate, though some sections assume familiarity with deep learning terminology.
- **Recommendation posture** Currently not established from the provided evidence. The core idea is promising, but the manuscript as presented does not provide sufficient evidence to support the claims of general applicability and superiority over existing approaches. Major revisions with additional experiments and clearer reporting would be needed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that EnhancerTracker achieves high specificity and precision on the testing set, with an accuracy of 64%, specificity of 93%, recall of 35%, precision of 84%, and F1 score of 49%.
- **Evidence pointer** Results and Discussion, Blind Evaluation on the Testing Dataset section; Table 2 referenced
- **Concern** The reported performance metrics are presented without adequate context. A recall of 35% means the tool misses 65% of true positive enhancers, which is a substantial limitation. The authors do not discuss the practical implications of this low recall, nor do they provide a comparison with existing enhancer prediction tools on the same benchmark. Without such comparison, it is unclear whether this performance represents an improvement over the state of the art. Additionally, the choice to favor specificity and precision over recall is stated but not justified with a quantitative analysis of the trade-off.
- **Why it matters** The central claim of the paper is that EnhancerTracker is a useful tool for enhancer discovery. A recall of 35% suggests that the tool would miss most enhancers in a genome-wide scan, which could limit its practical utility. The authors need to demonstrate that this trade-off is acceptable and that the tool outperforms or complements existing methods.
- **Resolution test** Provide a direct comparison with at least one existing enhancer prediction tool on the same testing set, including precision-recall curves and F1 scores. Discuss the practical implications of the recall level and justify the specificity-precision preference with a concrete use case.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that EnhancerTracker is applicable to all cell types, including those absent from or underrepresented in the training set, because it learns to compare enhancer activity rather than classify specific cell types.
- **Evidence pointer** Introduction, Methods Overview, Results and Discussion, Case Studies section
- **Concern** This is a strong claim that is not directly tested. The case studies use enhancers from cell types that are present in the FANTOM5 dataset, so they do not demonstrate generalization to unseen cell types. The authors do not describe any experiment where the tool is tested on enhancers from cell types not represented in the training data. The claim of general applicability is therefore unsupported by the presented evidence.
- **Why it matters** The ability to work on cell types with no training data is a key differentiator of this approach. If this claim is not validated, the tool's advantage over existing methods is substantially weakened.
- **Resolution test** Design an experiment where the model is trained on a subset of cell types and tested on held-out cell types. Report performance on these unseen cell types and compare with a traditional cell-type-specific classifier trained on the same data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the ensemble consists of 29 deep convolutional neural networks, and that the weighted-vote scheme was chosen based on validation performance.
- **Evidence pointer** Methods, Ensemble section; Results and Discussion, Ensembles section; Figure 7 referenced
- **Concern** The process for selecting the number of models (29) and the threshold (0.55) is described but the actual data supporting these choices are not presented in the text. The authors reference Figure 7, which is not visible in the provided material. Without seeing the performance curves, it is impossible to assess whether the chosen parameters are well-justified or whether the selection process could have led to overfitting on the validation set. Additionally, the authors do not report the variance across the individual models in the ensemble, which is important for understanding the stability of the predictions.
- **Why it matters** The ensemble configuration is a critical component of the tool. If the parameter selection is not robust or is overfit to the validation set, the reported testing performance could be optimistic.
- **Resolution test** Provide the performance curves for ensemble size selection and threshold selection. Report the distribution of individual model performances and the ensemble's stability across multiple training runs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors describe the case study where EnhancerTracker scanned a 100-kbp region and found 25 putative enhancers, of which 17 were confirmed as actual enhancers.
- **Evidence pointer** Results and Discussion, Case Studies section; Table 4 referenced
- **Concern** The confirmation of putative enhancers is described as "actual enhancers" but the criteria for confirmation are not clearly defined. The authors mention overlap with ENCODE enhancers and histone marks, but the specific thresholds and methods for determining overlap are not described. Additionally, the authors state that 69.2% (18/26) of putative enhancers showed evidence, but the denominator changed from 25 to 26 without explanation. This inconsistency is confusing and needs clarification.
- **Why it matters** The case study is presented as evidence of the tool's practical utility. If the confirmation criteria are not rigorous or are inconsistently applied, the validity of this evidence is questionable.
- **Resolution test** Clearly define the criteria for confirming an enhancer, including specific data sources, overlap thresholds, and how conflicting evidence is resolved. Explain the discrepancy between 25 and 26 putative enhancers.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, Data Augmentation section
- **Evidence pointer** Methods, Data Augmentation section
- **Issue** The description of the data augmentation strategy states that "the number of newly constructed triplets is double the number of sequences in a dataset." This is unclear. Does this mean the total number of triplets is twice the number of sequences, or that the number of augmented triplets is twice the original number? The sentence should be rewritten for clarity.
- **Required correction** Clarify the relationship between the number of sequences and the number of generated triplets, and provide a concrete example if helpful.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Hyperparameters section
- **Evidence pointer** Methods, Ensemble section
- **Issue** The hyperparameter ranges are listed but the specific values used for the final 29 models are not reported. This makes it difficult to reproduce the exact ensemble.
- **Required correction** Provide a table listing the specific hyperparameters for each of the 29 models in the final ensemble, or state that the full configuration is available in the code repository.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results and Discussion, Blind Evaluation on the Testing Dataset section
- **Evidence pointer** Results and Discussion, Blind Evaluation on the Testing Dataset section
- **Issue** The performance metrics on the testing set are reported as single point estimates without confidence intervals or statistical significance testing. Given the stochastic nature of neural network training, it is important to know the variability of these metrics.
- **Required correction** Report the mean and standard deviation of the metrics across multiple training runs, or provide confidence intervals.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and Discussion, Case Studies section
- **Evidence pointer** Results and Discussion, Case Studies section
- **Issue** The case study describes scanning 10-kbp and 100-kbp regions, but the number of triplets tested and the computational time required are not reported. This information would be useful for assessing the tool's scalability.
- **Required correction** Report the number of triplets evaluated in the case studies and the computational resources and time required.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that EnhancerTracker requires "only two confirmed enhancers" but does not specify whether these need to be from the same cell type or can be from different cell types. This is clarified later in the text but should be stated in the abstract.
- **Required correction** Clarify in the abstract that the two enhancers must be active in at least one common cell type.

## Risk / unsupported claims
- The claim that EnhancerTracker is applicable to all cell types, including those absent from training data, is not supported by any experiment in the provided text.
- The claim that the tool achieves high specificity and precision is supported only by point estimates without comparison to existing methods or statistical context.
- The case study results are described qualitatively and the confirmation criteria for putative enhancers are not rigorously defined.
- The performance of the ensemble relative to individual models is not quantified, so the benefit of the ensemble approach is not demonstrated.
- The claim that the tool "doesn't overfit" based on comparable training and testing metrics is weak without reporting the variance across training runs.