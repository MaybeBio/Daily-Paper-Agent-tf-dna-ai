## Review setup
- **Input scope** Full manuscript text (abstract, background, results, discussion, methods, figure legends, tables)
- **Assessment boundary** Technical soundness, methodological clarity, validity of performance claims, reproducibility, and alignment with stated conclusions
- **Shared manuscript claim summary** The authors present DeepTSS, a multi-branch convolutional neural network that integrates genomic signal processing (GSP) features, structural DNA features, evolutionary conservation, and raw one-hot encoded DNA sequence to identify transcription start sites (TSSs) from CAGE data at single-nucleotide resolution. They claim superior performance over existing tools across multiple benchmarks, including protein-coding gene annotation, ChromHMM chromatin states, and TF/H3K4me3 ChIP-seq overlap.
- **Visible evidence base** Full text including methods, results, tables (Tables 1 and 2), figures (Figs 1–5), and supplementary file descriptions
- **Missing materials affecting confidence** Supplementary tables (S1–S6) and figures (S1, S2) are referenced but not provided; no code repository contents, trained model weights, hyperparameter search details, or raw data accessions are included; no statistical significance testing is reported

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in transcriptomics, namely the removal of technical and biological noise from CAGE data for accurate TSS identification. The multi-branch architecture is a reasonable extension of prior work (DiS-TSS) and the integration of diverse feature types is conceptually sound. However, the evidence presented is insufficient to fully support the strong performance claims. Key methodological details are missing, particularly regarding training/validation splits, class imbalance handling, statistical significance of performance differences, and the construction of the negative set. The evaluation strategy, while multifaceted, lacks rigorous statistical comparison and does not adequately address potential biases in the benchmark design. The manuscript is readable and well-structured, but the technical depth required to assess reproducibility is not fully met.
- **Who would be interested in the results, and why** Researchers working on CAGE data analysis, promoter and enhancer annotation, and computational methods for regulatory genomics. The work is also relevant to those applying deep learning to genomic signal processing and to method developers interested in multi-branch CNN architectures for sequence-based prediction tasks.
- **Major strengths**
  - The problem is well-motivated and practically important, with clear evidence of noise in CAGE data (Fig. 1).
  - The multi-branch architecture that processes distinct feature types separately is a thoughtful design choice, allowing the model to learn modality-specific patterns.
  - The evaluation strategy is multifaceted, incorporating gene annotations, chromatin states, and experimental ChIP-seq data, which provides a broader view of performance than a single benchmark.
  - The method is made available as an open-source Python tool with documentation, which supports usability and reproducibility.
  - The comparison with multiple existing tools (CAGER, RECLU, PARACLU, iTiSS, TOMETOOLS, ADAPT-CAGE) is comprehensive.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "DeepTSS was found to outperform existing algorithms on all benchmarks, achieving 98% precision and 96% sensitivity (accuracy 95.4%) on the protein-coding gene strategy"
- **Evidence pointer** Table 1, Figure 3, Methods section "DeepTSS training"
- **Concern** The performance comparison lacks any statistical significance testing. The reported differences in precision and sensitivity between DeepTSS and ADAPT-CAGE (e.g., 0.98 vs 0.97 precision, 0.96 vs 0.94 sensitivity) are small and may not be meaningful without confidence intervals or hypothesis tests. Additionally, the evaluation appears to be based on a single test set, and it is unclear whether the results are stable across different random seeds or data splits. The authors do not report any variance or uncertainty estimates.
- **Why it matters** Without statistical rigor, the claim of "outperforming" existing algorithms is not substantiated. Small differences in metrics could be due to chance, and readers cannot assess the reliability of the reported performance.
- **Resolution test** Provide confidence intervals or perform statistical tests (e.g., McNemar's test or bootstrap) for pairwise comparisons. Report results across multiple independent test sets or cross-validation folds, and include variance estimates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "DeepTSS is a Python framework specifically designed for ease-of-use that is freely accessible at https://github.com/DianaLaboratory/DeepTSS"
- **Evidence pointer** Methods section "Software requirements and benchmarking"
- **Concern** The manuscript does not provide sufficient detail on the training procedure to allow reproduction. Specifically, the exact number of training, validation, and test samples is not stated. The description of the negative set construction is incomplete: it is unclear how many peaks were removed as "promoter-proximal" and whether the remaining negative peaks are truly representative of non-promoter regions. The hyperparameter search is described only as "data not shown," and the final architecture choices (filter numbers, kernel sizes, layer counts) are given but without justification or ablation studies. The data augmentation procedure (7 additional samples per peak) is described but its impact on performance is not evaluated.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without clear details on data splits, negative set construction, and hyperparameter tuning, other researchers cannot reliably apply or extend the method.
- **Resolution test** Provide explicit numbers for training/validation/test set sizes, a detailed description of the negative set filtering process, and a table or figure showing the hyperparameter search results. Include an ablation study to justify the inclusion of each feature type and the augmentation strategy.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evaluation methodology
- **Claim pointer** "The first benchmark is based only on protein-coding gene annotations that were used to divide the genome into promoter (positive) and non-promoter (negative) regions"
- **Evidence pointer** Methods section "Annotation and experimental data", Figure 3, Table 1
- **Concern** The benchmark design may introduce a bias in favor of DeepTSS. The positive set is defined as peaks overlapping both H3K4me3 and Pol II marks and within 1 kb of annotated TSSs, while the negative set consists of intergenic peaks without these marks. This creates a clear separation between positive and negative classes that may not reflect real-world conditions where TSS-associated signals are more heterogeneous. Furthermore, the "gene-oriented" evaluation (counting a gene as positive if any predicted peak overlaps its TSS region) may inflate performance metrics, as a single correct prediction per gene is sufficient. The authors do not discuss these potential biases or their implications.
- **Why it matters** A biased benchmark can lead to overestimated performance and unfair comparisons with other tools that were not designed for this specific evaluation setup. The generalizability of the method to diverse CAGE datasets and cell types is not established.
- **Resolution test** Include additional benchmarks with more realistic positive/negative definitions, such as using CAGE-defined TSSs from independent sources or evaluating on a held-out cell type. Report performance using alternative metrics (e.g., area under the precision-recall curve) and discuss the potential impact of benchmark design on the conclusions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "DeepTSS was found to outperform existing algorithms on all benchmarks"
- **Evidence pointer** Tables 1 and 2, Figure 5
- **Concern** The comparison with existing tools may not be entirely fair. For example, TOMETOOLS predictions were obtained by overlapping a precomputed file of scored loci with K562 CAGE peaks, which may not reflect the intended usage of the tool. Similarly, ADAPT-CAGE and other tools were run with default parameters, but it is unclear whether these defaults are optimal for the K562 dataset. The authors do not discuss whether any tool-specific parameter tuning was performed or whether the comparison is intended to reflect out-of-the-box performance.
- **Why it matters** Unfair comparisons can undermine the validity of the performance claims. If some tools are disadvantaged by suboptimal settings, the reported improvements may be overstated.
- **Resolution test** Clarify the parameter settings for all tools and justify the choices. Consider running additional analyses with tuned parameters for each tool or using published performance benchmarks as a reference.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2
- **Evidence pointer** Figure 2 caption
- **Issue** The figure caption is dense and does not clearly explain the flow from data input to final prediction. The relationship between the four branches and the final concatenation is not visually obvious.
- **Required correction** Simplify the caption and consider adding annotations or a schematic diagram to clarify the architecture.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "DeepTSS training"
- **Evidence pointer** Location not provided
- **Issue** The manuscript states that "Chromosomes 15 and 14 were completely left out of the training process" but does not specify which chromosome was used for testing during hyperparameter search and which for evaluation during training. This is ambiguous.
- **Required correction** Clearly state the role of each held-out chromosome.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Location not provided
- **Issue** The discussion is largely descriptive and does not critically evaluate the limitations of the method or the benchmarks. For example, the potential impact of the training cell type (H9) on generalization to other cell types is not discussed.
- **Required correction** Add a paragraph on limitations and future directions, including the need for cross-cell-type validation and the potential for transfer learning.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Software requirements and benchmarking"
- **Evidence pointer** Location not provided
- **Issue** The computational time for DeepTSS is reported, but the hardware specifications are only partially described. The time for training the model is not reported, only inference time.
- **Required correction** Report training time and provide full hardware specifications.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data section
- **Evidence pointer** Location not provided
- **Issue** The manuscript does not provide accession numbers or URLs for the ENCODE and Roadmap Epigenomics datasets used, beyond the sample codes. This makes it difficult for readers to access the exact data.
- **Required correction** Provide direct links or accession identifiers for all external datasets.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of statistical significance testing for performance comparisons
  - R1-M2: Insufficient detail on training data splits, negative set construction, and hyperparameter tuning
  - R1-M3: Potential bias in benchmark design that may favor DeepTSS
  - R1-M4: Unclear fairness of comparisons with existing tools

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The combination of GSP, structural features, conservation, and raw sequence in a multi-branch CNN is novel, but the overall approach is an incremental extension of existing methods (DiTSS, ADAPT-CAGE). The novelty lies primarily in the feature integration strategy rather than a fundamentally new conceptual framework.
  - **Scientific importance** Moderate. Accurate TSS identification from CAGE data is a practical need, and improving signal-to-noise ratio is valuable. However, the impact is limited to a specific data type and the improvements over existing tools are modest in absolute terms.
  - **Interdisciplinary readership** Limited. The manuscript is primarily of interest to computational biologists and bioinformaticians working on regulatory genomics. The methods and evaluation are too specialized for a broad interdisciplinary audience.
  - **Technical soundness** The architecture is reasonable, but the evaluation lacks statistical rigor and the training details are incomplete. The benchmark design has potential biases that are not addressed. The technical soundness is currently not fully established.
  - **Readability for nonspecialists** The manuscript is generally well-written and the figures are informative. However, the methods section assumes familiarity with deep learning and genomic signal processing, which may limit accessibility for nonspecialists.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant problem and presents a plausible method, but the performance claims are not statistically substantiated, and key methodological details are missing. The authors should address the major concerns, particularly the lack of statistical testing, the incomplete training description, and the potential benchmark biases, before the case for superiority over existing tools can be accepted.