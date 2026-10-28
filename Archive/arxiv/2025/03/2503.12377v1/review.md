## Review setup
- **Input scope** Full manuscript text (preprint, arXiv:2503.12377v1)
- **Assessment boundary** Scientific claims, methodology, experimental design, and reported results as presented in the provided text. Figures and tables referenced but not supplied are assessed only through textual description.
- **Shared manuscript claim summary** The authors propose GCBLANE, a deep learning architecture combining convolutional, multi-head attention, BiLSTM, and graph neural network components, for transcription factor binding site (TFBS) prediction from DNA sequence alone. They report superior performance over existing methods on 690 ENCODE ChIP-seq datasets (average AUC 0.943) and on a 165-dataset subset (average AUC 0.9433 per Table 4 description; abstract states 0.943 for 690 and 0.9433 for 165 in Section 4.3, while the abstract states 0.943 and 0.9495 respectively, an inconsistency noted below).
- **Visible evidence base** Text descriptions of datasets, model architecture, training procedure, and results. Referenced figures (Figures 1-13) and tables (Tables 2, 4, 5, 6) are not included in the provided material.
- **Missing materials affecting confidence** All figures and tables, including the architecture diagram, performance plots, comparison tables, and heatmaps. No quantitative results tables are visible. No baseline model descriptions or hyperparameter details beyond partial text. No code or data availability verification.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in regulatory genomics and proposes a reasonable architectural combination. However, the current text has substantial internal inconsistencies, missing critical experimental details, and the evidence base (figures and tables) is not available for verification. The core claim of state-of-the-art performance cannot be assessed from the provided material. The novelty contribution relative to existing sequence-only models is not clearly delineated.
- **Who would be interested in the results, and why** Researchers in computational genomics and regulatory biology, particularly those working on TFBS prediction, deep learning for genomics, and model interpretability. The potential for improved sequence-only prediction without external shape data would interest groups seeking scalable and cost-effective prediction tools.
- **Major strengths** The problem is well-motivated. The architectural combination is sensible and addresses known limitations of individual components. The use of de Bruijn graphs for capturing k-mer relationships is a reasonable idea. The evaluation across a large number of datasets (690) is commendable in principle. The inclusion of PR-AUC alongside ROC-AUC is appropriate for imbalanced classification.
- **Major Concerns** Multiple critical issues are identified below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (abstract inconsistency), R1-M2 (missing evidence), R1-M3 (novelty), R1-M4 (statistical rigor), R1-M5 (baseline fairness), R1-M6 (negative result on large datasets).
- **Assessment against Nature-style criteria** **Originality**: Moderate. The combination of components is new, but the individual elements are established. The novelty claim of being first to combine graph and sequential networks for sequence-only TFBS prediction requires a more thorough literature search and clearer positioning. **Scientific importance**: Potentially high if the performance claims hold, as improved TFBS prediction has broad implications. However, the importance is diminished by the acknowledged failure to outperform on large datasets and the lack of demonstrated biological insight. **Interdisciplinary readership**: The topic bridges computer science and molecular biology, but the manuscript is written primarily for a computational audience. The biological interpretation is thin. **Technical soundness**: Cannot be fully assessed due to missing figures and tables. The described methodology has some ambiguities (e.g., exact graph construction, fusion mechanism). The reported inconsistency in abstract numbers is a technical failing. **Readability for nonspecialists**: The introduction and conclusion are accessible, but the methodology section assumes significant prior knowledge. The manuscript would benefit from clearer explanations of the biological relevance of the technical choices.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential but requires major revisions, full provision of results, and resolution of internal inconsistencies before a supportive recommendation can be considered.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency
- **Claim pointer** The abstract states an average AUC of 0.943 for 690 datasets and 0.9495 for 165 datasets. Section 4.3 states an average AUC of 0.9433 for the 690 datasets. Section 4.4 describes comparisons on 165 datasets but does not provide a specific average AUC value in the text.
- **Evidence pointer** Abstract; Section 4.3; Section 4.4
- **Concern** The reported average AUC values are inconsistent between the abstract and the main text. The abstract claims 0.9495 for the 165-dataset evaluation, while Section 4.3 reports 0.9433 for the 690-dataset evaluation. It is unclear which number corresponds to which evaluation, and the discrepancy undermines confidence in the reported results.
- **Why it matters** Inconsistent reporting of primary performance metrics is a fundamental error that prevents accurate interpretation of the model's capabilities and makes the manuscript unreliable.
- **Resolution test** Provide a single, consistent set of average performance values for both the 690- and 165-dataset evaluations in both the abstract and the main text, with clear labeling.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim pointer** The manuscript claims superior performance over state-of-the-art methods across multiple metrics and dataset sizes, supported by Figures 4-13 and Tables 4-6.
- **Evidence pointer** Figures 4-13; Tables 4-6 (not provided)
- **Concern** All figures and tables containing the actual results are missing from the provided material. Without these, the central claims of the paper cannot be verified. The text descriptions are insufficient to assess the magnitude of improvements, statistical significance, or the validity of comparisons.
- **Why it matters** The core contribution of the paper is empirical. Without access to the results, the claims are unsubstantiated.
- **Resolution test** Provide all figures and tables with clear captions and axis labels. Ensure all values discussed in the text are traceable to specific figures or tables.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Novelty
- **Claim pointer** The authors claim "No existing studies have explored the combination of graph and sequential neural networks for TFBS prediction in a sequence-only context, making GCBLANE a novel and efficient approach."
- **Evidence pointer** Section 2 (Literature Review)
- **Concern** The literature review is brief and does not comprehensively cover recent work. The claim of novelty is strong and requires a more thorough survey of the field, including recent preprints and papers that may have explored similar combinations. The review mentions several models but does not systematically compare their architectures or limitations in a way that clearly establishes the gap.
- **Why it matters** The novelty claim is a key part of the paper's contribution. If the claim is inaccurate, the contribution is significantly diminished.
- **Resolution test** Expand the literature review to include a systematic search and discussion of recent sequence-only and graph-based TFBS prediction methods. Clearly articulate the specific gap that GCBLANE fills, with explicit comparisons to the closest related works.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports average performance metrics across 690 and 165 datasets, and claims superiority over other methods.
- **Evidence pointer** Section 4.3; Section 4.4
- **Concern** No statistical significance testing is reported. The text states GCBLANE "performs better than any other model" but does not provide confidence intervals, standard deviations, or paired statistical tests (e.g., Wilcoxon signed-rank test) across the datasets. The violin plots (Figure 8) are mentioned but not available for inspection.
- **Why it matters** Without statistical rigor, the observed performance differences could be due to chance, particularly given the large number of datasets and the variability expected across different TFs and cell lines.
- **Resolution test** Report standard deviations or confidence intervals for all average metrics. Perform and report a paired statistical test (e.g., Wilcoxon signed-rank test) comparing GCBLANE against each baseline across the 690 and 165 datasets.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Baseline fairness
- **Claim pointer** The manuscript compares GCBLANE against "advanced models that utilise multimodal approaches, including DNA shape information" and sequence-only models like BERT-TFBS, DLBSS, DanQ, and DeepBind.
- **Evidence pointer** Section 4.4
- **Concern** The text does not describe the training setup for the baseline models. It is unclear if the baselines were retrained under the same conditions (e.g., same data splits, same hyperparameter tuning) or if results were taken from their original publications. This is critical for a fair comparison.
- **Why it matters** Unfair comparisons (e.g., undertrained baselines) can lead to inflated claims of superiority.
- **Resolution test** Clearly describe the source of baseline results. If baselines were retrained, provide the training details. If results were taken from literature, ensure the evaluation protocols are compatible and state this explicitly.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Result interpretation
- **Claim pointer** The authors state in the Conclusion: "Even though GCBLANE performs well, there is room for development, particularly when dealing with huge datasets, where it hasn't been able to outperform alternative techniques."
- **Evidence pointer** Section 5 (Conclusion)
- **Concern** This statement directly contradicts the earlier claim in Section 4.4 that "On every dataset, we can observe that GCBLANE performs better than any other model." The manuscript does not reconcile these two statements. If GCBLANE does not outperform on large datasets, the overall claim of superiority is significantly weakened and needs to be presented with appropriate nuance.
- **Why it matters** The contradictory statements confuse the reader about the actual performance profile of the model and undermine the credibility of the reported results.
- **Resolution test** Clarify the performance profile of GCBLANE across dataset sizes. Provide a clear and consistent summary of where the model excels and where it does not, and discuss the implications for its practical utility.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.3 (Model Architecture)
- **Evidence pointer** Section 3.3
- **Issue** The equations for the CNN block, attention mechanism, and BiLSTM are referenced but not displayed in the provided text. The description of how the graph neural network output is fused with the sequential network output is vague.
- **Required correction** Ensure all equations are properly rendered and numbered. Provide a clear and detailed description of the fusion mechanism between the GNN and the sequential branches, including tensor dimensions and concatenation or weighting schemes.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 3.5 (Training Procedure)
- **Evidence pointer** Section 3.5
- **Issue** The text mentions a grid search for hyperparameters but does not report the range of values explored or the final selected hyperparameters beyond learning rate and batch size. The number of filters, kernel sizes, number of layers, dropout rates, and GNN-specific hyperparameters are not specified.
- **Required correction** Provide a complete table of hyperparameters, including the search space and the final chosen values for all model components.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data description
- **Affected element** Section 3.1 (Datasets)
- **Evidence pointer** Section 3.1
- **Issue** The description of the 690 and 165 datasets is minimal. It is unclear how the 165 datasets relate to the 690 (e.g., are they a subset? what criteria were used for selection?). The source is stated as the ENCODE Dream Challenge, but the specific accession numbers or download links are not provided.
- **Required correction** Clarify the relationship between the 690 and 165 datasets. Provide a link to the data repository or list the specific ENCODE accession identifiers.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Section 4.1 (Global Performance)
- **Evidence pointer** Section 4.1
- **Issue** The sentence "The similar performance of the model across the validation and training sets suggests suggests effective generalization" contains a duplicated word ("suggests suggests").
- **Required correction** Correct the typographical error.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 3.3 (Model Architecture)
- **Evidence pointer** Section 3.3
- **Issue** The term "graph convolutional (GCN) component" is used in Section 4.2, but the methodology section refers to a "graph neural network (GNN) module" and uses "graph convolution" with a specific equation. The relationship between GCN and GNN in this context is not explicitly defined.
- **Required correction** Use consistent terminology throughout the manuscript. Define whether the GNN module is a GCN, a GraphSAGE layer, or another variant, and specify the number of layers and hidden dimensions.

## Risk / unsupported claims
- The claim of state-of-the-art performance across all 690 datasets and the 165-dataset subset is unsupported without the actual results tables and figures.
- The claim of novelty ("No existing studies have explored...") is not fully supported by the brief literature review provided.
- The statement in the abstract of an average AUC of 0.9495 for 165 datasets is unsupported and inconsistent with the main text.
- The claim that GCBLANE is "more computationally efficient" than multimodal or language model approaches is not supported by any runtime, parameter count, or resource usage data.
- The claim that the model "represents a major step forward in TFBS prediction" is overstated given the acknowledged limitations on large datasets and the lack of biological validation.