## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological soundness, claims substantiation, and significance assessment based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors present ChromatinHD, a pair of scale-adaptive machine learning models for single-nucleus ATAC-seq data that operate on raw fragment data without peak calling or fixed windows. The models link chromatin accessibility to gene expression (ChromatinHD-pred) and identify differentially accessible regions (ChromatinHD-diff). The authors claim consistent outperformance over existing peak- and window-based approaches across five benchmarking tasks, and report novel biological findings including a 1-5 kb juxtaposition between co-predictive regions and DNA contact, and the identification of submononucleosomal fragments as indicators of dense TF binding.
- **Visible evidence base** Main text figures 1-6 (referenced), supplementary figures 1-8 (referenced), methods section with model architecture and training details, benchmarking protocols, and statistical procedures
- **Missing materials affecting confidence** Supplementary figures and notes referenced but not provided; source data files not accessible; detailed hyperparameter settings for baseline methods not fully specified; exact dataset characteristics and quality metrics not provided

## Reviewer
- **Overall assessment** This manuscript presents a technically sophisticated and potentially impactful computational framework for analyzing single-nucleus ATAC-seq data. The core idea of operating on raw fragment data with scale-adaptive architectures is conceptually sound and addresses a genuine limitation of current peak- and window-based approaches. The benchmarking is comprehensive across multiple tasks and datasets, and the reported performance improvements are consistent. However, several technical aspects require clarification and additional validation before the claims can be fully substantiated. The biological findings, while intriguing, are largely correlative and would benefit from additional experimental or orthogonal validation. The manuscript is well-written and the methods are described in sufficient detail for reproduction, though some implementation specifics remain unclear.

- **Who would be interested in the results, and why** Computational biologists developing methods for single-cell epigenomics, researchers studying gene regulation and chromatin architecture, and experimentalists using snATAC-seq or multiome assays who seek improved tools for regulatory element identification and functional interpretation. The co-predictivity analysis and its connection to 3D genome organization would interest the chromatin structure community. The fragment size findings have implications for understanding TF binding dynamics and could inform assay interpretation broadly.

- **Major strengths**
  1. The scale-adaptive approach is conceptually novel and addresses a real limitation of fixed-window and peak-based methods
  2. Comprehensive benchmarking across five distinct tasks with multiple baseline methods and datasets
  3. The decoupling of baseline accessibility from differential accessibility provides a useful conceptual framework
  4. The co-predictivity analysis offers a new way to infer regulatory cooperativity from accessibility data alone
  5. The fragment size analysis reveals a potentially important and underappreciated signal in ATAC-seq data
  6. The software is made available as an accessible Python package with documentation

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "ChromatinHD consistently outperforms existing peak and window-based approaches" (Abstract, Results section "ChromatinHD outperforms current methods")
- **Evidence pointer** Figures 1d, 2a-b, 3a-g; Methods section "Benchmark"
- **Concern** The benchmarking methodology may introduce bias in favor of ChromatinHD. The baseline methods are evaluated using their default or standard configurations, but it is unclear whether extensive hyperparameter tuning was performed for each baseline method on each dataset. The choice of evaluation metrics (correlation, R2) may also favor the more flexible ChromatinHD model. Additionally, the comparison of DAR calling methods uses different statistical frameworks (e.g., Wilcoxon test, logistic regression) which may not be directly comparable. The authors should clarify whether baseline methods were given equal opportunity for optimization and whether sensitivity analyses were performed with alternative metric choices.
- **Why it matters** The central claim of the manuscript is that ChromatinHD outperforms existing methods. If the benchmarking is not fair or robust, this claim is weakened, and the practical utility of the method becomes less clear. The computational cost of ChromatinHD is acknowledged to be higher, so the performance advantage must be convincingly demonstrated.
- **Resolution test** Provide details on hyperparameter optimization for all baseline methods, including the search space and selection criteria. Perform sensitivity analyses using alternative evaluation metrics (e.g., AUC for DAR classification, Spearman correlation for expression prediction). Consider reporting performance across a range of thresholds or model capacities for baselines.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "ChromatinHD-diff can delineate regulatory regions, including their preferential genomic conformations, that drive gene expression" (Abstract, Results section "ChromatinHD identifies a 1-5 kb outward juxtaposition")
- **Evidence pointer** Figure 5c-m; Methods section "Co-predictivity"
- **Concern** The co-predictivity analysis and its interpretation rely on several assumptions that are not fully validated. First, the correlation between per-cell prediction errors across windows is used as a proxy for regulatory cooperativity, but this could also reflect technical artifacts such as library complexity or batch effects. Second, the comparison with Hi-C data is performed on a different cell type (GM12878) than the primary data (PBMCs), and the authors do not adequately address potential cell-type-specific differences in chromatin architecture. Third, the statistical significance of the observed juxtaposition pattern is not rigorously established; the authors should provide confidence intervals or permutation-based tests for the enrichment patterns shown in Figure 5d.
- **Why it matters** The claim of identifying preferential genomic conformations is a strong biological statement that goes beyond methodological development. If the statistical foundation is weak, this finding may not be reproducible or may reflect artifacts rather than true biological phenomena. The cross-cell-type comparison is particularly concerning given known cell-type-specific differences in 3D genome organization.
- **Resolution test** Perform additional validation of co-predictivity as a measure of regulatory cooperativity, such as comparison with known enhancer-promoter pairs or CRISPR perturbation data. Conduct the Hi-C comparison in matched cell types where possible, or explicitly test for cell-type-specific effects. Provide permutation-based null distributions or bootstrap confidence intervals for the juxtaposition enrichment analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "ChromatinHD can identify submononucleosomal fragments as indicative of dense TF binding and active gene regulation" (Abstract, Results section "ChromatinHD identifies submononucleosomal fragments")
- **Evidence pointer** Figure 6a-d; Methods section "Fragment size interpretation"
- **Concern** The interpretation of fragment size effects relies on the assumption that fragment length distributions directly reflect TF binding density. However, fragment size in ATAC-seq is influenced by multiple factors including nucleosome positioning, chromatin compaction, and technical aspects of the assay such as tagmentation efficiency and PCR amplification bias. The authors do not adequately control for these potential confounders. Additionally, the comparison with ChIP-seq data from a different cell line (GM12878) than the primary data (PBMCs) introduces potential cell-type-specific biases. The claim that submononucleosomal fragments indicate "dense TF binding" requires more direct validation.
- **Why it matters** This is a novel biological claim that could have broad implications for interpreting ATAC-seq data. If the fragment size signal is confounded by technical factors, the conclusion may be misleading. The cross-cell-type comparison weakens the evidence for a general phenomenon.
- **Resolution test** Validate the fragment size findings in matched cell types with ChIP-seq data. Perform additional controls such as spike-in experiments or computational simulations to rule out technical artifacts. Consider orthogonal validation using methods that directly measure TF occupancy, such as ChIP-seq or CUT&Tag in the same cell types.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "ChromatinHD, available at https://chromatinhd.org, is a suite of computational tools" (Abstract, Data availability)
- **Evidence pointer** Methods section "ChromatinHD"; Code availability statement
- **Concern** While the software is stated to be available, the manuscript does not provide sufficient detail on the computational environment, dependencies, or expected runtime for the full analysis pipeline. The methods describe the model architecture but do not specify all hyperparameters (e.g., number of training epochs for ChromatinHD-pred, learning rate schedules, batch sizes, early stopping criteria). The preprocessing steps are described but exact parameters for filtering, normalization, and quality control are not fully specified. This limits the reproducibility of the results.
- **Why it matters** Reproducibility is a core requirement for computational methods papers. Without complete specifications, other groups may not be able to replicate the results or apply the method to their own data effectively.
- **Resolution test** Provide a complete specification of all hyperparameters and preprocessing parameters, either in the main text or as a supplementary table. Include information on software versions, hardware requirements, and expected runtime. Consider providing a containerized environment (e.g., Docker) or a configuration file that fully specifies the analysis pipeline.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1c
- **Evidence pointer** Figure 1c; Results section "ChromatinHD enables scale-adaptive sn(ATAC+RNA)-seq analysis"
- **Issue** The schematic in Figure 1c is described as showing "three nested regions exemplifying how ChromatinHD models capture predictive and differential accessibility at different scales," but the figure itself is not provided in the manuscript text. The description is insufficient to understand the visual representation.
- **Required correction** Provide the figure or a more detailed textual description of what is shown, including the specific scales and how they relate to the model architecture.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Benchmark results
- **Evidence pointer** Figures 2a-b, 3a-g; Methods section "Benchmark"
- **Issue** The manuscript reports performance improvements but does not consistently provide measures of variability (e.g., standard errors, confidence intervals) across cross-validation folds or datasets. Some comparisons appear to be based on single runs.
- **Required correction** Report variability measures for all benchmark results, including standard errors or confidence intervals across folds and datasets. Specify the number of independent runs performed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Fragment size analysis
- **Evidence pointer** Figure 6a-b; Results section "ChromatinHD identifies submononucleosomal fragments"
- **Issue** The authors state that "nucleosomal fragments were about 3 times less predictive than submononucleosomal fragments" but do not discuss potential reasons for this difference beyond dense TF binding. Alternative explanations such as differences in chromatin state or technical factors are not considered.
- **Required correction** Add a brief discussion of alternative interpretations and potential confounding factors in the fragment size analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Benchmark datasets
- **Evidence pointer** Methods section "Benchmark"; Results section "ChromatinHD outperforms current methods"
- **Issue** The manuscript mentions nine datasets but does not provide a summary table of dataset characteristics (e.g., number of cells, number of genes, sequencing depth, species, tissue type). This information is important for assessing the generalizability of the results.
- **Required correction** Add a supplementary table summarizing key characteristics of all datasets used in the study.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Co-predictivity"
- **Evidence pointer** Methods section "Co-predictivity"
- **Issue** The description of the co-predictivity calculation is dense and difficult to follow. The relationship between per-cell prediction errors and the final co-predictivity score could be explained more clearly with a step-by-step description or a pseudocode algorithm.
- **Required correction** Provide a more detailed step-by-step description of the co-predictivity calculation, possibly with pseudocode or a worked example.

- **Technical failings that need to be addressed before the case is established**
  1. R1-M1: Benchmarking fairness and robustness
  2. R1-M2: Statistical validation of co-predictivity findings
  3. R1-M3: Validation of fragment size interpretation
  4. R1-M4: Reproducibility specifications

- **Assessment against Nature-style criteria**
  - **Originality**: High. The scale-adaptive approach to single-cell accessibility analysis is novel, and the co-predictivity concept represents a new analytical framework. The fragment size findings are unexpected and potentially transformative for interpreting ATAC-seq data.
  - **Scientific importance**: High. The method addresses a fundamental limitation in current approaches and could improve regulatory element identification, variant prioritization, and understanding of gene regulation across many studies. The biological findings have implications for chromatin biology and TF binding interpretation.
  - **Interdisciplinary readership**: Moderate to high. The methods will appeal to computational biologists and bioinformaticians, while the biological findings (co-predictivity, fragment size, 3D genome organization) will interest molecular biologists, chromatin biologists, and geneticists. The clear writing and figures make it accessible to a broad audience.
  - **Technical soundness**: Moderate. The core methodology is well-designed and the benchmarking is comprehensive, but several technical concerns (R1-M1 through R1-M4) need to be addressed to fully establish the validity of the claims. The statistical rigor of the biological findings requires strengthening.
  - **Readability for nonspecialists**: Good. The manuscript is well-structured with clear figures and logical flow. The abstract and introduction are accessible, though the methods section is necessarily technical. The discussion effectively contextualizes the findings for a broad audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable and potentially impactful computational framework with novel biological insights. However, the benchmarking fairness, statistical validation of the co-predictivity and fragment size findings, and reproducibility specifications must be addressed before the claims can be fully substantiated. I recommend major revision to address these concerns.

## Risk / unsupported claims
- The claim that ChromatinHD "consistently outperforms" existing methods is not fully supported without evidence of fair hyperparameter optimization for baselines and sensitivity analyses with alternative metrics
- The interpretation of the 1-5 kb juxtaposition between co-predictive regions and DNA contact as evidence of "preferential genomic conformations" is not directly validated and relies on cross-cell-type comparisons
- The claim that submononucleosomal fragments indicate "dense TF binding" is not directly validated and may be confounded by technical factors
- The statement that "about 51% of information is gained outside of peaks once regions are normalized by baseline accessibility" requires clarification on how this percentage is calculated and whether it is statistically significant
- The generalizability of the method across diverse cell types, tissues, and species is not fully established given the limited number of datasets and the focus on immune and blood-related cell types