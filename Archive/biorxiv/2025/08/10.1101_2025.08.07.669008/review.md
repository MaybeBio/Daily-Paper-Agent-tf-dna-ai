## Review setup
- **Input scope** Full manuscript text (summary, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific content, methodological rigor, claims vs. evidence, reproducibility, and suitability for a high-impact general audience
- **Shared manuscript claim summary** The authors present a benchmarking framework (scBAMpler) for evaluating three single-cell genomic footprinting tools (HINT, PRINT, TOBIAS) across data quality conditions, report consistency and reproducibility metrics, identify peak read coverage as the dominant factor, and propose an ensemble model that improves concordance with ChIP-seq.
- **Visible evidence base** Main text figures referenced (Figures 1–7), supplementary figures referenced (S1–S8), Table 1, methods section, resource availability
- **Missing materials affecting confidence** Figure panels and actual data values not visible in the provided text; supplementary tables (Table S1) referenced but not provided; exact numerical results for many claims not stated in text; code availability for benchmark pipeline not fully described

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important problem: the lack of rigorous, independent benchmarking of single-cell genomic footprinting tools. The authors have invested substantial effort in constructing a large, realistic dataset and in developing a flexible downsampling framework. The finding that peak read coverage is the dominant predictor of footprint stability is practically useful. However, the manuscript's impact is limited by several factors: the benchmark is restricted to three tools, the ground truth (ChIP-seq) is acknowledged as imperfect but the implications are not fully explored, and the ensemble model's improvement is modest and demonstrated for only two TFs. The recommendations section is extensive but some claims lack direct quantitative support in the text. The writing is clear but the manuscript would benefit from more precise reporting of effect sizes and confidence intervals.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on single-cell ATAC-seq analysis, regulatory genomics, and TF binding prediction. Practitioners who need guidance on tool selection and experimental design for footprinting experiments. Developers of footprinting algorithms who need to understand how their methods compare and where improvements are needed. The practical recommendations and the scBAMpler framework will be of direct use to the single-cell genomics community.

- **Major strengths**
  1. Addresses a critical gap: independent, systematic benchmarking of footprinting tools in single-cell data.
  2. The scBAMpler framework is a valuable contribution that enables controlled manipulation of data quality parameters.
  3. The dataset is large and realistic, derived from ENCODE cell lines with available ChIP-seq ground truth.
  4. The analysis is thorough, covering consistency, reproducibility, equivalence, and TF-specific biases.
  5. The practical recommendations are actionable and will help users design better experiments.
  6. The ensemble approach is a sensible direction and shows improvement over individual tools.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "peak-read coverage emerged as the strongest predictor of stable footprints" and that "applying a universal filtering threshold of 100 reads per peak can improve the consistency of footprint calls."
- **Evidence pointer** Figures 2B, 2C, S2C, S2D; location not provided for exact values
- **Concern** The claim that 100 reads per peak is a universal threshold is strong and potentially overgeneralized. The analysis appears to be based on a specific set of cell lines, tools, and peak-calling parameters. It is unclear whether this threshold holds across different data types (e.g., scATAC vs. snATAC, different Tn5 concentrations, different library preparation protocols) or across different peak callers. The text states that "applying a universal filtering threshold of 100 reads per peak... did improve performance" but does not provide the magnitude of improvement or the variability across cell lines and tools. Without quantitative effect sizes and confidence intervals, the universality of this threshold is not established.
- **Why it matters** If the 100-read threshold is adopted as a universal standard by the community, it could lead to suboptimal results in datasets where the relationship between coverage and footprint stability differs. The claim has direct practical implications for experimental design and data filtering.
- **Resolution test** Provide the distribution of F1 scores before and after applying the 100-read threshold across all cell lines, tools, and downsampling conditions, with effect sizes and variability. Demonstrate that the threshold is robust across a wider range of data qualities and, ideally, validate on an independent dataset.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Ground truth validity
- **Claim pointer** The authors use ChIP-seq as a ground truth for evaluating footprinting tools and state that "ChIP-seq is an imperfect gold standard" but proceed to use it as the primary benchmark.
- **Evidence pointer** Methods section "Evaluation methodology"; Figures 7A–D, S7
- **Concern** The manuscript acknowledges ChIP-seq limitations but does not systematically address how these limitations affect the benchmark conclusions. For example, the authors note that "even replicated experiments for the same TF, cell line, and antibody under basal conditions can vary substantially," yet the analysis treats ChIP-seq as a fixed reference. The decision to restrict analysis to TFs with "reliable PWM recall" introduces a selection bias that may favor certain tools or TF families. The authors do not report how many TFs were excluded and whether the conclusions are sensitive to this filtering.
- **Why it matters** If the ground truth is noisy or biased, the benchmark results may reflect artifacts of ChIP-seq rather than true differences in footprinting performance. This undermines the validity of the comparative claims and the ensemble model's evaluation.
- **Resolution test** Perform a sensitivity analysis using alternative ground truth definitions (e.g., different ChIP-seq peak callers, different thresholds for defining bound/unbound). Report the number of TFs excluded by the filtering criteria and re-run key analyses without this filter. Discuss how ChIP-seq noise might differentially affect tools with different underlying assumptions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state that "our results will help users design single-cell experiments, optimize pseudobulking strategies, and perform meaningful cross-sample comparisons of TFBSs" and provide recommendations for "strong performance (F1 > 0.6)" requiring "~100 million read pairs per cell population."
- **Evidence pointer** Recommendations section; Figures 2A, S2K
- **Concern** The benchmark is limited to five ENCODE cell lines and three tools. The recommendation of ~100 million read pairs is derived from this specific context. It is unclear how this translates to other scenarios: different tissues with more complex cell type composition, different numbers of cell types in a sample, different genome sizes, or different experimental protocols. The authors note that "other datasets will return different cell-level estimates" but do not provide a framework for how users should adapt the recommendation to their specific context.
- **Why it matters** The practical value of the manuscript depends on the generalizability of its recommendations. If users apply the 100 million read pair guideline to a dataset with different characteristics, they may over- or under-sequence, wasting resources or compromising power.
- **Resolution test** Provide a more nuanced model or framework that allows users to estimate required depth based on their specific parameters (e.g., number of cell types, expected TF activity, genome size). Alternatively, validate the recommendation on an independent dataset with different characteristics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Ensemble model evaluation
- **Claim pointer** The authors claim that "all two- and three-tool ensembles outperformed individual models, with the three-tool ensemble reaching an auPR of 0.72 (CTCF) and 0.30 (JUND)."
- **Evidence pointer** Methods section "Ensemble models"; Figures 7C, S7H
- **Concern** The ensemble model is evaluated for only two TFs (CTCF and JUND) in one cell line (HepG2). This is a very limited demonstration. The improvement over individual tools is modest (e.g., from 0.64 to 0.72 for CTCF). It is unclear whether the ensemble approach would generalize to other TFs, cell lines, or data qualities. The authors do not report the variability of the ensemble performance across cross-validation folds or whether the improvement is statistically significant.
- **Why it matters** The ensemble model is presented as a key contribution, but the evidence for its general utility is thin. If the improvement is not robust or significant, the recommendation to use ensembles may not be justified.
- **Resolution test** Evaluate the ensemble on a larger set of TFs and cell lines. Report confidence intervals or statistical tests for the improvement. Assess whether the ensemble's advantage holds under downsampling conditions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1A
- **Evidence pointer** Figure 1A; location not provided
- **Issue** The text states that the benchmark is summarized in Figure 1A, but the figure itself is not described in the text. It is unclear what the schematic shows and how it relates to the workflow.
- **Required correction** Add a brief description of Figure 1A in the text, explaining the overall workflow and how the components fit together.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** scBAMpler code
- **Evidence pointer** Resource Availability section
- **Issue** The code is available on GitHub, but the manuscript does not specify the version or commit hash used for the analyses. This makes it difficult to reproduce the exact results.
- **Required correction** Provide a version number or commit hash for the scBAMpler and scFootprintBenchmark repositories in the Resource Availability section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Multiple claims throughout
- **Evidence pointer** Figures 2A, 3A, 4C, 5B, 7A–D
- **Issue** The text frequently reports qualitative trends (e.g., "gradual and consistent decreases," "strong concordance") without providing numerical values or confidence intervals. This makes it difficult to assess the magnitude and reliability of the effects.
- **Required correction** Add key numerical results to the text, including effect sizes, confidence intervals, or p-values where appropriate. For example, report the range of F1 scores across tools and conditions, the correlation coefficients for PWM rankings, and the improvement from the ensemble model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Table 1
- **Evidence pointer** Table 1; location not provided
- **Issue** Table 1 is referenced in the text but its contents are not described. It is unclear what the R² values represent and how they support the claim that "~20% of the variance in real PWM occupancy could be attributed to PWM properties."
- **Required correction** Add a brief description of Table 1 in the text, explaining the model, the training/testing scenarios, and the interpretation of the R² values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Universal filtering threshold"
- **Evidence pointer** Results section, paragraph on peak read coverage
- **Issue** The term "universal" is too strong given the limited scope of the benchmark. It implies a general principle that has not been established.
- **Required correction** Replace "universal" with "suggested" or "recommended" and qualify the claim by noting the benchmark's scope.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Comparison to prior work
- **Affected element** Discussion of prior benchmarks
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript mentions that "existing footprinting tools have not yet been rigorously and independently benchmarked across diverse single-cell conditions," but does not provide a detailed comparison to prior benchmarking efforts (e.g., for bulk data). This makes it difficult to assess what is new.
- **Required correction** Add a brief review of prior benchmarking studies for footprinting tools, highlighting what they covered and what gaps remain, to better position the current work.

## Risk / unsupported claims
- The claim that "peak-read coverage was the strongest predictor" of F1 scores is supported by the analysis but the exact statistical model and its performance are not described in the text.
- The recommendation of "~100 million read pairs per cell population" for F1 > 0.6 is presented as a general guideline but is derived from a specific dataset and may not generalize.
- The claim that "applying a universal filtering threshold of 100 reads per peak can improve the consistency of footprint calls" is not quantified in the text.
- The ensemble model's improvement is demonstrated for only two TFs in one cell line; the generalizability of this result is not established.
- The statement that "much of the signal is likely shared across conditions" is speculative and not directly tested.
- The claim that "RNA-seq can support differential binding interpretation but was not effective as a filtering step" is not supported by specific data in the text.
- The assertion that "union-based methods retain more biologically relevant information than intersecting sets" is presented as a recommendation but is not directly tested in the results.