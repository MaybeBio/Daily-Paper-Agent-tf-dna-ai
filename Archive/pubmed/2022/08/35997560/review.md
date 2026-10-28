## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, experimental design, and conclusions as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose NetTIME, a multitask learning framework with TF- and cell-type-specific embeddings and a CRF post-processing step, for base-pair resolution prediction of cell-type-specific TF binding sites. They claim improved performance over single-task approaches and over two existing methods (Catchitt and Leopard) under both supervised and transfer learning settings.
- **Visible evidence base** Main text, Figures 1–7 (referenced), Supplementary Figures S1–S5 and Tables S1 (referenced), Methods section (Section 2), Results section (Section 3)
- **Missing materials affecting confidence** Supplementary figures and tables not provided; detailed hyperparameter settings, architecture specifications, and training details only partially described; exact dataset accession numbers not listed in main text; code repository not inspected

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology: improving TF binding site prediction through multitask learning and base-pair resolution. The core idea of using learned embeddings to distinguish TF and cell-type identities within a multitask framework is sensible and potentially useful. The inclusion of a CRF for noise reduction is also a reasonable contribution. However, the manuscript as presented has several weaknesses that prevent full confidence in the claims. The ablation studies are partially informative but the interpretation of the embedding-swapping experiments is not fully convincing. The comparison with baseline methods, while favorable, raises questions about fairness given differences in training data and feature availability. The transfer learning evaluation is interesting but the practical utility for truly unseen TFs or cell types is not fully demonstrated. The writing is generally clear but some methodological details are missing, and the statistical significance of performance differences is not rigorously established. Overall, the work is promising but requires additional analysis and clarification to fully support its claims.

- **Who would be interested in the results, and why** Researchers in computational genomics, specifically those working on TF binding site prediction, regulatory genomics, and deep learning applications to biology. The multitask learning framework and the use of embeddings for condition identity could be of interest to the broader machine learning for genomics community. The CRF post-processing approach for noise reduction may also interest researchers working on peak calling or boundary detection in genomic signals.

- **Major strengths**
  1. The problem is well-motivated: the skew in available ChIP-seq data towards a few TFs and cell types is a real limitation, and the potential of multitask learning to address this is clearly articulated.
  2. The framework is technically sound in its overall design: combining CNN and RNN in an encoder-decoder with condition embeddings is a reasonable architecture choice.
  3. The inclusion of a CRF for classification is a thoughtful addition that addresses a practical issue (noise in base-pair predictions) and is shown to be beneficial.
  4. The transfer learning evaluation, including comparisons with alternative strategies (Average Train, No Embedding Transfer), is a valuable contribution.
  5. The manuscript is generally well-written and the figures are described clearly.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the multitask learning strategy is more efficient due to increased data availability rather than data diversity (Section 3.1).
- **Evidence pointer** Figure 2, Section 3.1
- **Concern** The authors conclude that the performance improvement from multitask learning is due to increased data quantity, not diversity, based on a subsampling experiment. However, the description of this experiment is brief. It is unclear whether the subsampled single-task models were trained with the same number of total samples as the multitask model, or whether each single-task model received the same reduced number of samples. If each single-task model was trained on a subset of its own data, the comparison may not isolate the effect of data diversity versus quantity. A more detailed description of the subsampling procedure is needed.
- **Why it matters** This is a central claim about the mechanism by which multitask learning helps. If the conclusion is not rigorously supported, the motivation for the multitask approach is weakened.
- **Resolution test** Provide a detailed description of the subsampling procedure, including the exact number of samples used for each model. Ideally, also include a control where the multitask model is trained on a dataset with reduced diversity (e.g., from fewer cell types) but with the same total sample count, to directly test the diversity hypothesis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that NetTIME outperforms Catchitt and Leopard under both supervised and transfer learning settings (Section 3.2, Section 3.4).
- **Evidence pointer** Figure 3, Figure 5, Supplementary Figure S5
- **Concern** The comparison with baseline methods may not be entirely fair. Catchitt and Leopard use only DNase-seq as cell-type-specific input, while NetTIME can use DNase-seq plus histone modifications. In the comparison shown in Figure 3b, it appears all methods were evaluated with the same input features (DNA + DNase), which is good. However, the authors also state that adding histone modifications improves NetTIME performance (Figure 3a). It is unclear whether the comparison in Figure 3d (ENCODE-DREAM Challenge) uses the same feature sets for all methods. If NetTIME uses additional features not available to the baselines, the comparison is not apples-to-apples. Additionally, the baselines may have been trained with different data splits or preprocessing steps.
- **Why it matters** The claim of superiority over existing methods is a key selling point. If the comparison is not fair, the conclusion is not valid.
- **Resolution test** Clearly state the input features used for each method in each comparison. Ensure that all methods are trained and evaluated on the same data splits and with the same available features. If NetTIME uses additional features, either restrict the comparison to common features or justify why the comparison is still meaningful.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that TF and cell-type embeddings allow accurate transfer predictions beyond the training panels (Section 3.4).
- **Evidence pointer** Figure 6, Section 3.4
- **Concern** The transfer learning evaluation for unseen TFs and cell types (Figure 6) is limited to four new TFs and three new cell types. This is a small sample size, and the choice of these specific conditions may bias the results. It is unclear how representative these conditions are of the broader space of possible TFs and cell types. Additionally, the fine-tuning procedure for these new conditions is not described in detail. It is not clear how many epochs of fine-tuning were performed, what learning rate was used, and whether overfitting was controlled for.
- **Why it matters** The ability to generalize to unseen conditions is a major claimed advantage of the embedding approach. A limited and potentially biased evaluation does not provide strong evidence for this claim.
- **Resolution test** Expand the evaluation to a larger and more diverse set of unseen TFs and cell types. Provide a detailed description of the fine-tuning protocol, including hyperparameters and early stopping criteria. Report the variance in performance across the different transfer conditions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The overall reproducibility of the method.
- **Evidence pointer** Section 2, Data Availability
- **Concern** The manuscript lacks sufficient detail for full reproducibility. The exact architecture (number of layers, filter sizes, hidden dimensions) is not fully specified. The training procedure (learning rate schedule, batch size, number of epochs, early stopping criteria) is only briefly mentioned in the Supplementary Material, which was not provided. The hyperparameter search procedure is not described. The code is available, but the manuscript should be self-contained enough for a skilled researcher to reimplement the method without excessive reverse-engineering.
- **Why it matters** Reproducibility is a core requirement for scientific publications. Without sufficient detail, the work cannot be independently verified or built upon.
- **Resolution test** Provide a complete description of the model architecture and training procedure in the main text or a comprehensive Supplementary Material. Include all hyperparameters and the search strategy used to select them.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The claim that NetTIME significantly outperforms baseline methods.
- **Evidence pointer** Figure 3, Figure 5
- **Concern** The manuscript does not report any statistical significance testing for the performance differences between NetTIME and the baseline methods. The differences in auPRC may be within the range of random variation, especially given the relatively small number of test conditions (13 in the ENCODE-DREAM Challenge). Error bars or confidence intervals are not shown in the figures.
- **Why it matters** Without statistical significance testing, it is not possible to determine whether the observed improvements are meaningful or due to chance.
- **Resolution test** Perform statistical significance testing (e.g., paired Wilcoxon signed-rank test across test conditions) for the comparisons in Figures 3b, 3d, and 5b. Report p-values and effect sizes. Show error bars or confidence intervals in the figures.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2.4, Equation 4
- **Evidence pointer** Equation 4
- **Issue** The definition of the CRF potential function is incomplete. The equation is cut off and the transition matrix V is not defined. The text says "where" but the equation is not fully displayed.
- **Required correction** Complete the equation and define all variables, including the dimensions and initialization of the transition matrix V.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2, Figure 3a
- **Evidence pointer** Figure 3a
- **Issue** The statement "adding TF motif enrichment features... does not introduce significant performance improvement" is made, but no statistical test is reported to support the word "significant."
- **Required correction** Either perform a statistical test to support this claim or rephrase to "does not introduce performance improvement" without the word "significant."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The selection criteria for the 7 cell types and 22 TFs are described as "representative" but the specific criteria are not detailed. It is unclear how these were chosen and whether they are truly representative.
- **Required correction** Provide a brief justification for the selection of these specific cell types and TFs, or refer to a supplementary table that lists them with relevant properties.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.3, Figure 4
- **Evidence pointer** Figure 4
- **Issue** The description of the embedding-swapping experiment is somewhat confusing. It is not immediately clear what "swapping at prediction time" versus "swapping at training time" means in practice. A more explicit description of the experimental setup would be helpful.
- **Required correction** Clarify the experimental procedure for the embedding-swapping experiments, perhaps with a step-by-step description.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure is described as having panels a, b, and c, but the text does not always refer to the specific panels. This makes it harder to follow the description of the architecture.
- **Required correction** Refer to specific panels in the text when describing the architecture and data flow.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The subsampling experiment needs to be described in more detail to support the claim about data quantity versus diversity.
  - R1-M2: The fairness of the comparison with baseline methods needs to be clarified, particularly regarding input features and data splits.
  - R1-M3: The transfer learning evaluation needs to be expanded and the fine-tuning protocol described in detail.
  - R1-M4: The manuscript needs to provide sufficient detail for reproducibility.
  - R1-M5: Statistical significance testing is needed for the main performance comparisons.

- **Assessment against Nature-style criteria**
  - **Originality**: The combination of multitask learning with explicit TF and cell-type embeddings for base-pair resolution prediction is a novel contribution. The use of a CRF for post-processing is also a creative addition. However, the individual components (CNN, RNN, embeddings, CRF) are all established techniques, and the novelty lies primarily in their integration for this specific problem.
  - **Scientific importance**: TF binding site prediction is an important problem in regulatory genomics. The potential to improve predictions for under-studied TFs and cell types through transfer learning is of significant practical value. The work addresses a real limitation in the field.
  - **Interdisciplinary readership**: The work is primarily of interest to computational biologists and bioinformaticians. The methods are drawn from deep learning, which is now a standard tool in this community. The biological questions are specific to transcriptional regulation. The interdisciplinary appeal is moderate; it is unlikely to attract a broad readership beyond these fields.
  - **Technical soundness**: The overall approach is technically sound, but the concerns raised above about experimental validation, statistical rigor, and reproducibility need to be addressed. The architecture is reasonable, but the evaluation is not yet fully convincing.
  - **Readability for nonspecialists**: The manuscript is written in a clear and accessible style. The introduction and motivation are easy to follow. The methods section is more technical but is generally understandable for readers with a background in machine learning and genomics. The figures are helpful.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the results are suggestive, but the current evidence is not sufficient to fully establish the claims. The authors need to address the concerns about experimental rigor, statistical significance, and reproducibility before the work can be fully endorsed.