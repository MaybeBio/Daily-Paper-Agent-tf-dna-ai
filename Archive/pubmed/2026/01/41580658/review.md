## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, limitations, conclusion, future work) as provided. No supplementary materials, figures, or tables were available beyond in-text references.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided text. No code, datasets, or full experimental outputs were inspected.
- **Shared manuscript claim summary** The authors propose EDEN, a multiscale nucleotide encoding based on kernel density estimation, integrated with a hybrid CNN, and claim state-of-the-art average performance across sixteen GUE benchmark datasets with orders-of-magnitude fewer parameters than existing models.
- **Visible evidence base** In-text descriptions of methods, architecture (Table 1), dataset details (Table 2), kernel comparison (Table 3), ablation study (Table 4), benchmark comparisons (Tables 5-6), statistical tests (Table 7), and figures referenced (Figs. 1-6). No raw data, code, or supplementary results were available.
- **Missing materials affecting confidence** Full experimental details (hyperparameters, training epochs, data preprocessing), actual figure contents, supplementary tables with per-dataset results, code repository contents, and any statistical test assumptions. The absence of these limits verification of all claims.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting encoding scheme that bridges one-hot and k-mer representations via KDE, with a plausible biological rationale. The hybrid CNN architecture is straightforward and parameter-efficient. However, the evidence provided is insufficient to fully substantiate the central claims of state-of-the-art performance and broad generalizability. Several methodological details are underspecified, and the comparison against baselines and prior work lacks critical rigor. The work has potential, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational genomics and deep learning for regulatory element prediction would find this relevant. The parameter efficiency and interpretability angle may appeal to those working on large-scale genome annotation or resource-constrained settings. The encoding scheme could also interest method developers in sequence representation learning.
- **Major strengths**
  1. The EDN encoding is conceptually novel, unifying one-hot and k-mer approaches within a principled KDE framework.
  2. The biological rationale for multiscale bandwidth selection (1-, 3-, 5-, 7-mer) is clearly articulated and interpretable.
  3. The architecture is parameter-efficient, which is a meaningful practical advantage.
  4. The ablation study and kernel comparison provide useful internal validation.
  5. Statistical testing against a baseline strengthens the claim that gains are not due to chance.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that EDEN achieves "the best average performance" across sixteen datasets while using "orders of magnitude fewer parameters" compared to state-of-the-art models.
  - **Evidence pointer** Table 5, Table 6, Section "Comparison with state-of-the-art methods"
  - **Concern** The comparison against state-of-the-art models (DNABERT, DNABERT-2, NT variants) relies on values "as reported in their respective studies." This is problematic because those studies may have used different training protocols, data splits, or evaluation procedures. The authors do not demonstrate that the comparison is apples-to-apples. Furthermore, the reported average ranks in Table 6 are derived from mean MCC values, but the per-dataset breakdown is not shown, making it impossible to assess variance or identify tasks where EDEN underperforms. The claim of "best average performance" is also ambiguous: EDEN's average rank (3.25) is not the best (NT-2500M-multi has 3.5, but DNABERT-2 has 4.25; the best average rank appears to be EDEN's, but this is not clearly stated as such). More critically, the magnitude of improvement over DNABERT-2 and NT-2500M-multi is not reported per task, and the statistical significance is only tested against the OneHot+HFBranch baseline, not against the state-of-the-art models.
  - **Why it matters** The central claim of the paper is that EDEN is competitive or superior to much larger models. Without a rigorous, controlled comparison, this claim is not substantiated. The reader cannot determine whether the reported performance differences are meaningful or artifacts of inconsistent evaluation.
  - **Resolution test** Provide per-dataset MCC values for all methods, ideally re-running baseline models under identical training and evaluation conditions. Report statistical significance of EDEN's performance against each state-of-the-art model, not just the baseline. Clarify what "best average performance" means and justify the ranking methodology.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The manuscript claims that all code, pretrained models, and datasets are publicly available, and that the method is fully described.
  - **Evidence pointer** Abstract, Section "Proposed method: EDEN framework", GitHub link in abstract
  - **Concern** The method description lacks critical implementation details. Specifically: (a) the exact kernel functions used (cosine, linear, exponential, Gaussian) are named but their mathematical forms are not given; (b) the bandwidth calibration procedure is described qualitatively but the precise algorithm for computing h for each kernel and k-mer scale is not specified; (c) the architecture in Table 1 lists layer types and output channels but omits activation functions, pooling strategies, dropout rates, batch normalization, and the input dimensionality at each stage; (d) training hyperparameters (learning rate, optimizer, batch size, number of epochs, early stopping criteria) are not reported; (e) the procedure for generating positive and negative samples for each dataset is not described. Without these details, the work cannot be reproduced.
  - **Why it matters** Reproducibility is a core requirement for computational biology method papers. The authors claim public availability, but the manuscript itself must contain sufficient detail for independent implementation. The current level of detail is inadequate.
  - **Resolution test** Provide complete mathematical definitions of kernels, the bandwidth selection algorithm, full architecture specifications (including all hyperparameters), and training details. If the GitHub repository contains all of this, state so explicitly and cross-reference specific files.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The claim that EDEN offers "a pathway toward interpretable, density-aware base-resolution modeling" and that its multiscale representation is "biologically informed."
  - **Evidence pointer** Sections "Fundamental Distinction from Convolutional Operations", "Biological interpretation of EDN", "Future work"
  - **Concern** The biological interpretability claims are largely speculative. The manuscript describes how EDN signals could relate to biological features (e.g., GC-rich regions, poly-A signals) but provides no empirical validation, such as motif enrichment analysis, comparison to known regulatory elements, or visualization of learned features. The "pathway toward base-resolution modeling" is mentioned as future work, not demonstrated. The distinction from convolutional operations is asserted but not empirically shown; the authors do not demonstrate that EDN features are more interpretable than learned convolutional filters.
  - **Why it matters** The novelty of the approach rests partly on its interpretability and biological grounding. Without empirical evidence, these claims remain rhetorical. The paper would be stronger if it showed concrete examples of EDN features corresponding to known biological patterns.
  - **Resolution test** Add an analysis section showing, for example, that EDN peaks align with known transcription factor binding motifs or that EDN-derived features correlate with chromatin accessibility. Alternatively, temper the interpretability claims to match the evidence provided.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The claim that "the expected density of points in the immediate vicinity of x" and the normalization property that the sum of the four nucleotide density signals equals one.
  - **Evidence pointer** Section "EDN numerical representation", Equations 1-6, Figure 4
  - **Concern** The mathematical derivation is unclear. Equation (6) defines EDN(x) = N * f(x), but the text states that the sum of the four nucleotide density signals equals one. If f(x) is a probability density function, then N * f(x) is not a density but an expected count, and the sum over four nucleotides would equal N, not 1. The normalization property is asserted but not derived. Additionally, the use of KDE with discrete data points (nucleotide positions) and the choice of kernel functions require more careful mathematical treatment. The relationship between the bandwidth h and the k-mer scale is also not rigorously defined.
  - **Why it matters** The mathematical foundation of the encoding is central to the method. If the normalization property is incorrect or the derivation is flawed, the encoding may not behave as described, affecting downstream performance and interpretability.
  - **Resolution test** Provide a rigorous derivation of the normalization property, clarify the distinction between density and expected count, and specify the exact kernel functions and bandwidth calibration procedure with mathematical precision.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section "EDN numerical representation"
  - **Evidence pointer** Equations 1-6
  - **Issue** The notation is inconsistent. Equation (1) uses f̂(x) for the KDE estimate, but Equation (6) uses f(x) without the hat. The variable k is used for the kernel function in Equation (1) but K is used in the text. The symbol N is used both for the total number of data points and for the sequence length, which may be confusing.
  - **Required correction** Standardize notation throughout. Use consistent symbols for the kernel function, the density estimate, and the sequence length. Define all variables explicitly.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Table 1
  - **Evidence pointer** Table 1
  - **Issue** The parameter counts listed in Table 1 appear inconsistent. For example, the first Conv1d layer with 64 output channels and kernel size 5 would have 64 * (4 * 5 + 1) = 1,344 parameters if the input has 4 channels (one per nucleotide), which rounds to 1.3k. However, the input to the high-resolution branch is described as Scale 1 EDN features, which would have 4 channels. The parameter counts for subsequent layers are not verifiable without knowing the input dimensions. The total of 1.07M parameters is stated but not derived.
  - **Required correction** Provide a full derivation of parameter counts, including input and output dimensions at each layer. Clarify the input channel structure for both branches.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section "Comparison with state-of-the-art methods"
  - **Evidence pointer** Table 5, Table 6
  - **Issue** The tables are dense and difficult to interpret. Table 5 reports mean MCC values but does not show per-dataset results. Table 6 reports ranks but the methodology for breaking ties or handling missing values is not described. The text refers to "Figure 5" and "Figure 6" but these are not available in the provided material.
  - **Required correction** Include per-dataset results in a supplementary table. Describe the ranking methodology explicitly. Ensure all figures are self-explanatory and referenced correctly.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section "Biological interpretation of EDN"
  - **Evidence pointer** Section 3.4
  - **Issue** The biological interpretations are presented as established facts rather than hypotheses. For example, "High EDNG peaks often correspond to GC-rich regions" is stated without citation or empirical support. The section reads more like speculation than analysis.
  - **Required correction** Either provide citations for these claims or reframe them as hypotheses that could be tested. Consider moving this section to the discussion or future work.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Section "Experimental setup"
  - **Evidence pointer** Section 4.2
  - **Issue** The experimental setup does not describe how the GUE datasets were preprocessed, how sequences were tokenized or aligned, or whether any data augmentation was applied. The train/validation/test splits are mentioned as "predefined" but the source of these splits is not cited.
  - **Required correction** Provide details on data preprocessing and cite the original GUE benchmark paper for the splits.

- **Technical failings that need to be addressed before the case is established**
  1. R1-M1: Inconsistent and non-controlled comparison against state-of-the-art models.
  2. R1-M2: Insufficient methodological detail for reproducibility.
  3. R1-M4: Unclear or potentially incorrect mathematical derivation of the normalization property.

- **Assessment against Nature-style criteria**
  - **Originality** The KDE-based encoding is a novel contribution that has not, to my knowledge, been proposed in this exact form. The unification of one-hot and k-mer concepts within a density estimation framework is conceptually interesting. However, the novelty is incremental rather than transformative; it is a new encoding scheme applied to existing benchmarks with a standard CNN architecture.
  - **Scientific importance** The problem of efficient and interpretable DNA sequence encoding is relevant, and parameter efficiency is a practical concern. However, the demonstrated improvements over baselines are modest (2.5-6.0% MCC), and the comparison against state-of-the-art is not rigorous enough to establish a clear advantage. The broader impact on the field is not yet clear.
  - **Interdisciplinary readership** The work sits at the intersection of machine learning and genomics. The encoding concept could interest both communities, but the manuscript is written primarily for a bioinformatics audience. The mathematical formulation is accessible, but the biological interpretation section is speculative and would not convince a rigorous genomics audience.
  - **Technical soundness** The core idea is plausible, but the mathematical derivation has gaps, the experimental comparison is not controlled, and the statistical analysis is limited to a single baseline. These issues undermine confidence in the technical claims.
  - **Readability for nonspecialists** The manuscript is generally well-structured and readable. The figures and tables are referenced clearly, but the lack of per-dataset results and the dense tables make it hard for a nonspecialist to assess the claims. The biological interpretation section is accessible but speculative.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea has merit, and the parameter efficiency is a genuine advantage. However, the manuscript in its current form does not fully establish the central claims. The authors must address the comparison methodology, provide complete reproducibility details, and clarify the mathematical foundations. If these are resolved, the paper could make a solid contribution to the field.