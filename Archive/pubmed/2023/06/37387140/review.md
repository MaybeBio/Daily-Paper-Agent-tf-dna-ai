## Review setup
- **Input scope** Full manuscript text (main text, methods, results, discussion) as provided by the author. No supplementary files, figures, or tables were available for inspection.
- **Assessment boundary** Scientific and technical evaluation of the proposed architecture, its performance claims, interpretability claims, and biological findings. No assessment of code quality, reproducibility of the software repository, or data availability beyond what is stated in the manuscript.
- **Shared manuscript claim summary** The authors propose tiSFM, a multilayer convolutional neural network for sequence-to-function prediction, in which all internal parameters are claimed to be intrinsically interpretable in terms of sequence motifs and transcription factor activities. They claim superior predictive performance over a state-of-the-art CNN (AI-TAC) on a hematopoietic ATAC-seq dataset, identification of known lineage-specific transcription factors, and utility for predicting chromatin changes along developmental transitions.
- **Visible evidence base** Main text figures referenced (Figs 1–5) but not provided. Supplementary tables and figures referenced (Tables S1–S2, Figs S1–S4) but not provided. Model equations described in text but not numbered or fully specified. Training details, hyperparameters, and data preprocessing steps described in text.
- **Missing materials affecting confidence** All figures and supplementary materials. Exact model equations (only described verbally). Hyperparameter values for regularization path. Details of the "tree-diff" data transformation. Full results of ablation studies. Statistical significance tests for performance comparisons.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing architecture that aims to address a well-recognized limitation in genomic deep learning, namely the opacity of model internals. The idea of constraining the architecture so that parameters are directly interpretable as motifs, pooling strategies, and TF–TF interactions is timely and potentially valuable. However, the evidence provided in the text alone is insufficient to fully evaluate the strength of the claims. Key quantitative results, comparisons, and visualizations are relegated to figures and supplementary materials that were not available for review. The performance advantage over AI-TAC is stated but not demonstrated with numbers or statistical tests. The interpretability claims are plausible but require closer inspection of the actual parameter values and their stability across cross-validation folds. The biological findings are consistent with known literature, which is encouraging, but the novelty of these findings relative to what was already reported by Maslova et al. (2020) is not fully clarified. The manuscript would benefit from a more detailed description of the architecture, explicit equations, and a clearer statement of what exactly is "intrinsically" interpretable versus what still requires post hoc analysis.
- **Who would be interested in the results, and why** Researchers developing interpretable deep learning methods for genomics, particularly those working on sequence-to-function models, regulatory genomics, and transcription factor biology. The architecture's emphasis on intrinsic interpretability could appeal to computational biologists who are skeptical of post hoc attribution methods. The biological findings on hematopoietic differentiation may also interest immunologists studying gene regulation in blood cell development.
- **Major strengths**
  1. The core idea of designing an architecture where interpretability is built-in rather than achieved through post hoc analysis is conceptually strong and addresses a real limitation in the field.
  2. The use of prior knowledge (cisBP PWMs) as fixed initial kernels, with the option to fine-tune, is a sensible design choice that bridges knowledge-driven and data-driven approaches.
  3. The trainable pooling mechanism that interpolates between average and max pooling is an elegant way to model different aggregation strategies, and the observed correlation with motif information content is a biologically meaningful result.
  4. The "tree-diff" analysis, which focuses on developmental transitions rather than static cell states, is a thoughtful extension that could provide more mechanistic insight.
  5. The authors are transparent about limitations, including the issue of similar PWMs within TF families and the lack of cell-type specificity in the interaction layer.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for performance claims
- **Claim pointer** "tiSFM outperforms a state-of-the-art convolutional neural network model custom-tailored to this dataset" (Abstract, Results Section 3.1)
- **Evidence pointer** Figure 1B and C, Supplementary Table S1 (not provided)
- **Concern** The central performance claim is presented without any quantitative values in the text. No R² values, correlations, or error metrics are reported for either tiSFM or AI-TAC. The claim of "outperforms" is made without statistical significance testing or effect sizes. The ablation study results are also only shown in figures, not described numerically.
- **Why it matters** The performance advantage over an existing state-of-the-art model is a core justification for the proposed architecture. Without quantitative evidence, the reader cannot assess the magnitude of the improvement, its consistency across cell types, or whether it is within noise. This is particularly important given that the authors themselves note that the base model (without interaction and attention layers) can outperform AI-TAC after kernel fine-tuning, which raises questions about which architectural components are actually responsible for the improvement.
- **Resolution test** Provide mean and standard error of R² (or equivalent metrics) for all model variants and AI-TAC across the 10 cross-validation folds, with statistical tests (e.g., paired t-test or Wilcoxon signed-rank test) comparing tiSFM to AI-TAC. Report these values in the main text or in a table that is accessible to the reader.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of architecture description
- **Claim pointer** The manuscript describes a "totally interpretable" architecture with specific components: data transformation, convolution with fixed PWMs, trainable pooling, interaction layer, and final linear layer (Sections 2.3, 3.1)
- **Evidence pointer** Section 2.3, Equations (1) and (2) (not fully specified)
- **Concern** The architecture is described verbally and with incomplete equations. The data transformation step is not explained (what is the "positional embedding"? how is it computed?). The interaction layer is described as a matrix A that multiplies motif contributions, but the exact form of this multiplication, its initialization, and its regularization are not specified. The self-attention mechanism is mentioned but its role and placement in the architecture are unclear. The equations are referenced as (1) and (2) but are not displayed in the text provided.
- **Why it matters** For a methods paper in a computational journal, the architecture must be specified precisely enough for others to reproduce it. The claim of "intrinsic interpretability" depends on the exact form of each layer. Without full equations and a clear description of how each component works, the method cannot be evaluated or reimplemented.
- **Resolution test** Provide complete, numbered equations for every layer of the architecture, including the data transformation, convolution, pooling, interaction, and final linear layers. Specify all hyperparameters, initialization schemes, and regularization choices. Include a clear diagram or pseudocode that shows the data flow through the network.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability claim strength
- **Claim pointer** "internal model parameters are intrinsically interpretable in terms of relevant sequence motifs" (Abstract); "the final linear layer directly maps TFs to outputs and can produce a meaningful TF by output matrix with no post-processing" (Section 1)
- **Evidence pointer** Figure 2A and B, Section 3.3 (figures not provided)
- **Concern** The claim of "intrinsic interpretability" is strong, but the evidence presented in the text is limited. The authors state that known TFs are highlighted (Pax5, Ebf1, etc.) and that inclusion ratios are high, but no quantitative comparison is made to the AI-TAC results. It is unclear how the TF-by-cell-type matrix from tiSFM compares to the attribution-based results from AI-TAC in terms of ranking, magnitude, or consistency. The authors also note that kernel fine-tuning does not degrade interpretability, but the metric used to assess this (average MSE of 0.04 between initial and final kernels) is not a direct measure of interpretability.
- **Why it matters** The central selling point of the paper is that interpretability is built into the architecture. If the resulting TF rankings are similar to what post hoc attribution methods produce, the advantage may be primarily computational (avoiding expensive attribution analyses) rather than conceptual. The authors should demonstrate that the intrinsic parameters provide information that is not readily available from standard post hoc analysis, or at least that they are equally reliable with less effort.
- **Resolution test** Provide a direct comparison between tiSFM's TF-by-cell-type matrix and the AI-TAC attribution results, including correlation coefficients between the two sets of rankings. Show that the intrinsic parameters are stable across cross-validation folds and that the identified TFs are not simply an artifact of the initial PWMs used. Consider reporting precision-recall curves against a gold standard set of known regulators.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological novelty of findings
- **Claim pointer** "tiSFM identifies key regulatory events along differentiation trajectories" (Section 3.6); "we identify specific developmental transitions that are highly predictable from sequence" (Discussion)
- **Evidence pointer** Figure 5, Section 3.6 (figure not provided)
- **Concern** The "tree-diff" analysis is interesting, but the text does not provide enough detail to evaluate the novelty of the findings. The authors state that transitions leading to NK, ILC, and myeloid subtypes are well predicted, and that Zbtb7b is identified for the CD4/CD8 split. However, it is unclear whether these findings are new or simply recapitulate known biology. The authors also note that the R² values for the tree-diff data are low (around 0.05), which raises questions about the reliability of the TF importance rankings for individual transitions.
- **Why it matters** For a paper in a bioinformatics journal, the biological insights should be either novel or provide a methodological advance that enables new discoveries. If the findings are largely confirmatory, the value of the paper rests primarily on the methodological contribution, which needs to be more rigorously demonstrated.
- **Resolution test** Clearly state which findings are new relative to the AI-TAC analysis and other published work. Provide confidence intervals or stability measures for the TF importance rankings on the tree-diff data. Consider validating the Zbtb7b finding with an independent analysis or experimental reference.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparison fairness and completeness
- **Claim pointer** "tiSFM outperforms a state-of-the-art convolutional neural network model custom-tailored to this dataset" (Abstract)
- **Evidence pointer** Section 3.1, Figure 1 (not provided)
- **Concern** The comparison to AI-TAC is described as being performed with the same train/validation/test splits and stopping criteria, which is good. However, it is unclear whether the AI-TAC model was re-trained with the same hyperparameter optimization effort as the original paper. The authors state they "re-trained the original AI-TAC model architecture" but do not specify whether they performed hyperparameter tuning for AI-TAC or used the original hyperparameters. If the latter, the comparison may be unfair.
- **Why it matters** A fair comparison requires that both models are given similar opportunities for optimization. If AI-TAC was not tuned for the new data split, the performance difference could be due to suboptimal hyperparameters rather than architectural advantages.
- **Resolution test** Describe the hyperparameter tuning procedure for both models. If AI-TAC was not tuned, acknowledge this as a limitation and consider reporting results with a tuned version of AI-TAC. Report the number of parameters and training time for both models to give a sense of computational cost.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Section 2.3, model architecture description
- **Evidence pointer** Section 2.3
- **Issue** The description of the data transformation step is vague. The text mentions "positional embedding" and "self-attention" but does not explain how these are implemented or why they are needed. The phrase "Data transformation" appears to be a placeholder for a more detailed description.
- **Required correction** Provide a clear explanation of the data transformation step, including what positional information is encoded, how the self-attention mechanism works, and what role it plays in the overall architecture.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.1, performance comparison
- **Evidence pointer** Section 3.1
- **Issue** The text reports "mean and standard error" for performance but does not state the number of replicates or the statistical test used. It is unclear whether the standard error is across cross-validation folds or across multiple training runs.
- **Required correction** Specify the number of replicates and the statistical test used for comparing models. Report exact p-values or confidence intervals.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract, Section 1
- **Evidence pointer** Abstract, Section 1
- **Issue** The term "totally interpretable" is used repeatedly. While the authors clarify that this means each layer is interpretable, the term is somewhat absolute and could be misleading. Some components, such as the self-attention mechanism, may not have a straightforward biological interpretation.
- **Required correction** Consider using a more measured term such as "architecturally interpretable" or "intrinsically interpretable" and acknowledge that some components may require additional analysis to fully understand.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility of regularization path
- **Affected element** Section 3.5
- **Evidence pointer** Section 3.5
- **Issue** The regularization path is described as starting from the fully trained model and progressively increasing λ. The text does not specify the range of λ values, the number of steps, or the criterion for selecting the "best-performing model."
- **Required correction** Provide the range of λ values tested, the number of steps in the path, and the model selection criterion (e.g., validation loss, sparsity level).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability statement
- **Affected element** Data availability section
- **Evidence pointer** Data availability section
- **Issue** The data availability statement mentions the ATAC-seq dataset but does not mention the code repository beyond the URL in the abstract. It would be helpful to state the license and version of the code.
- **Required correction** Add a statement about the code license and version, and consider depositing the code in a permanent repository such as Zenodo or Figshare.

## Risk / unsupported claims
- The claim that tiSFM "outperforms" AI-TAC is unsupported in the text without quantitative results or statistical tests.
- The claim that internal parameters are "intrinsically interpretable" is plausible but not fully demonstrated without inspection of the actual parameter values and their stability.
- The claim that the model "correctly identifies context-specific activities of transcription factors" is supported only by qualitative statements and references to figures not provided.
- The claim that the "tree-diff" analysis identifies "key regulatory events" is not supported by quantitative measures of reliability or novelty.
- The statement that "subsequent CNN layers in deep CNNs mostly perform kernel refinement rather than compute complex regulatory grammar" is an overgeneralization based on a single dataset and architecture comparison.
- The claim that the interaction layer provides "homotypic and heterotypic TF–TF interaction insights" is not supported by any specific examples or validation in the text provided.