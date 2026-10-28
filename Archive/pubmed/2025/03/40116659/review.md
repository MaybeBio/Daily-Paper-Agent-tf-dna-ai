## Review setup
- **Input scope** Full manuscript text (abstract, methods, results, discussion, conclusion) without figures, tables, or supplementary materials
- **Assessment boundary** Technical soundness, methodological novelty, experimental design, and validity of conclusions based solely on the provided text
- **Shared manuscript claim summary** The authors propose AttentionGRN, a graph transformer-based model for gene regulatory network reconstruction from scRNA-seq data. The model incorporates directed structure encoding and functional gene sampling to capture both network topology and functional relationships. Claims include consistent outperformance over existing methods across 88 benchmark datasets and successful identification of novel hub genes and regulatory associations in human mature hepatocytes.
- **Visible evidence base** Text descriptions of experimental results, parameter sensitivity analyses, ablation studies, and a case study on human hepatocytes. No actual figures, tables, or numerical results are visible.
- **Missing materials affecting confidence** All figures (Figs 1-7), supplementary figures (S1-S9), supplementary tables (S1-S9), and the GitHub repository contents. Numerical performance metrics (AUROC, AUPR values) are referenced but not shown in the provided text.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely the reconstruction of gene regulatory networks from single-cell RNA sequencing data. The motivation for applying graph transformers to overcome limitations of GNNs is reasonable and timely. However, the current text does not provide sufficient technical detail or visible quantitative evidence to fully evaluate the claims. Several methodological aspects require clarification, and the experimental validation would benefit from more rigorous statistical analysis and comparison with a broader set of baselines. The application to human hepatocytes is interesting but the biological validation appears largely literature-based rather than experimental.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, particularly those interested in graph-based deep learning methods. Researchers studying transcriptional regulation in liver biology may also find the hepatocyte application relevant. The methodological contribution could interest the broader machine learning for genomics community.

- **Major strengths** The problem is well-motivated with clear limitations identified in existing GNN-based approaches. The combination of directed structure encoding and functional gene sampling within a graph transformer framework is a sensible design choice. The evaluation across 88 datasets spanning multiple cell types and prior network types is comprehensive in scope. The authors provide code and data, supporting reproducibility.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that AttentionGRN "consistently outperforms existing methods" across 88 datasets
  - **Evidence pointer** Results sections "Performance on GRN inference" and "Performance on TRN inference"; figures referenced as Fig. 3 and Fig. 4
  - **Concern** The text states that AttentionGRN outperforms baselines on "most datasets" for GRN inference and "all datasets" for TRN inference, but no actual numerical results are provided in the visible text. Without AUROC/AUPR values, confidence intervals, or statistical significance tests, the superiority claim cannot be assessed. The phrase "most datasets" is ambiguous and does not quantify the extent of improvement.
  - **Why it matters** The central claim of the paper rests on demonstrated performance improvement over existing methods. Without visible quantitative results and appropriate statistical testing, the reader cannot determine whether the improvements are meaningful or within noise.
  - **Resolution test** Provide full numerical results for all datasets and baselines, including standard deviations across repeated runs. Perform and report statistical significance tests (e.g., paired Wilcoxon signed-rank test) comparing AttentionGRN against each baseline.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The methodological description of the graph transformer architecture, including directed structure encoding and functional gene sampling
  - **Evidence pointer** Methods sections "Overview of AttentionGRN", "Functionally related genes", "Directed structure encoding", "Dual-stream feature extraction"
  - **Concern** The equations referenced (Equations 1-13) are not visible in the provided text. The description of the directed structure encoding is incomplete, as it lists centrality measures (degree, closeness, betweenness, Katz) but does not explain how these are combined or embedded. The functional gene sampling threshold is described qualitatively ("very few" vs "excessive") without a clear selection criterion. The interaction between the gene expression stream and the network structure stream in the dual-stream architecture is not fully specified.
  - **Why it matters** Reproducibility is a core requirement for computational methods. The current description is insufficient for an independent implementation. The novelty claim depends on understanding exactly how the directed structure encoding differs from prior work.
  - **Resolution test** Provide complete equations with all variable definitions. Clarify how the centrality measures are normalized and combined. Specify the exact algorithm for functional gene sampling, including the threshold selection procedure. Describe how the two feature streams are integrated.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Experimental design
  - **Claim pointer** The evaluation methodology using independent testing for GRN inference and TF-aware three-fold cross-validation (TTCV) for TRN inference
  - **Evidence pointer** Methods section "Evaluation strategies"
  - **Concern** The text states that positive samples are ground-truth TF-gene pairs and negative samples are "unknown TF-target gene pairs" for independent testing. This negative sampling strategy may introduce bias, as "unknown" does not necessarily mean "non-interacting." The TTCV procedure is described but the rationale for using different evaluation strategies for GRN versus TRN tasks is not fully justified. The potential for data leakage between training and test sets in the independent testing scenario is not addressed.
  - **Why it matters** Biased negative sampling can inflate performance metrics. The choice of evaluation strategy affects the comparability of results across methods and tasks. Data leakage would compromise the validity of the reported performance.
  - **Resolution test** Clarify the negative sampling strategy and discuss its potential biases. Justify the use of different evaluation protocols for GRN and TRN tasks. Describe measures taken to prevent data leakage, particularly in the independent testing scenario.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological validation
  - **Claim pointer** The identification of "novel hub genes" including ZNF101, ZNF143, BRCA2, EED, and ZNF146 in human mature hepatocytes
  - **Evidence pointer** Results section "AttentionGRN identifies novel hub genes in human mature hepatocytes"
  - **Concern** The validation of novel hub genes relies entirely on literature association with liver diseases. This is correlational evidence and does not demonstrate that these genes are actual hubs in the regulatory network or that the predicted regulatory relationships are functional. The claim that 27 of 30 predicted BRCA1 associations have supporting evidence in Harmonizome is noted, but the nature and strength of that evidence is not described.
  - **Why it matters** The biological application is presented as a demonstration of practical utility. Without functional validation (e.g., perturbation experiments, chromatin immunoprecipitation, or reporter assays), the biological significance of the predictions remains uncertain.
  - **Resolution test** Provide additional validation such as comparison with independent experimental datasets, motif enrichment analysis for predicted TF binding sites, or discussion of how the predictions could be experimentally tested. Acknowledge the limitations of literature-based validation.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The phrase "functional and directed graph transformer" in the title and abstract is somewhat ambiguous. It is not immediately clear whether "functional" refers to functional gene relationships or to the functionality of the model itself.
  - **Required correction** Clarify the meaning of "functional" in this context, perhaps by rephrasing to "function-aware" or "functionality-informed" if referring to biological function.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, "Model input"
  - **Evidence pointer** Methods section "Model input", paragraph on preprocessing
  - **Issue** The text mentions "Two preprocessing methods [35] were applied" but does not describe these methods in sufficient detail. The filtering criteria (10% expression, p-value threshold) are mentioned, but the normalization and scaling procedures are not specified.
  - **Required correction** Provide a more detailed description of the preprocessing pipeline, including normalization methods, scaling, and any batch effect correction.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, performance comparisons
  - **Evidence pointer** Results sections "Performance on GRN inference" and "Performance on TRN inference"
  - **Issue** The text reports that AttentionGRN "outperforms" or achieves "superior performance" but does not report variance measures or statistical significance for the comparisons.
  - **Required correction** Report standard deviations or confidence intervals for all metrics, and include statistical tests where appropriate.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results, ablation study
  - **Evidence pointer** Results section "Ablation study"
  - **Issue** The ablation study is described as having five different models, but the specific components being ablated are not clearly enumerated in the text. The reader cannot determine which modules are being tested.
  - **Required correction** Clearly list the five model variants and specify which components are removed or modified in each.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results, time complexity
  - **Evidence pointer** Results section "Time complexity analysis"
  - **Issue** The text reports average runtime in seconds but does not provide hardware specifications or compare runtime scaling with dataset size.
  - **Required correction** Provide hardware details and discuss how runtime scales with the number of genes and cells.

- **Technical failings that need to be addressed before the case is established** R1-M1 (missing numerical results and statistical testing), R1-M2 (incomplete methodological description), R1-M3 (potential bias in negative sampling and evaluation protocol)

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of graph transformers to GRN inference is a natural progression from GNN-based methods, and the specific combination of directed structure encoding with functional gene sampling has some novelty. However, the core idea of using attention mechanisms for GRN inference is not entirely new.
  - Scientific importance: Moderate. Improved GRN inference methods are valuable for understanding gene regulation, but the demonstrated improvements over existing methods need to be more rigorously established.
  - Interdisciplinary readership: Limited. The work is primarily of interest to computational biologists and bioinformaticians. The biological application to hepatocytes is a step toward broader relevance, but the validation is not strong enough to attract a wider biological audience.
  - Technical soundness: Currently insufficient. The methodological description is incomplete, and the experimental validation lacks visible quantitative results and statistical rigor.
  - Readability for nonspecialists: The text is generally well-written and accessible, with clear motivation and logical flow. However, some technical details are presented without sufficient context for a general reader.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant problem with a reasonable approach, but the central claims of consistent outperformance and biological discovery cannot be verified from the visible text. The methodological description is incomplete, and the experimental validation lacks quantitative detail and statistical rigor. Substantial revisions are required to establish the case for this work.

## Risk / unsupported claims
- The claim that AttentionGRN "consistently outperforms existing methods" is unsupported in the visible text, as no numerical results are provided.
- The claim of identifying "novel hub genes" is only supported by literature association, which is correlational and does not establish functional significance.
- The claim that 27 of 30 predicted BRCA1 associations have supporting evidence is noted but the nature of that evidence is not described.
- The methodological novelty relative to existing graph transformer approaches for GRN inference is not clearly established, as no direct comparison with other graph transformer methods is mentioned.
- The claim that the model "effectively captures local network structures, long-range dependencies, and functional relationships" is not directly supported by specific analyses demonstrating these capabilities.