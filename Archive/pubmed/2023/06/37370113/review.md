## Review setup
- **Input scope** Full manuscript text including main figures and methods, excluding supplementary files
- **Assessment boundary** Scientific claims, methodological soundness, benchmarking validity, and interpretability claims as presented in the main text
- **Shared manuscript claim summary** The authors present ExplaiNN, an interpretable neural network architecture for genomics that combines multiple independent CNN units with linear combination, claiming performance comparable to state-of-the-art models across TF binding prediction, chromatin accessibility prediction, and de novo motif discovery, while providing both global and local interpretability
- **Visible evidence base** Main text figures 1-6, methods section, performance metrics (AUPRC, PCC), benchmarking comparisons against DanQ, DeepCNN, CNN variants, STREME, AI-TAC, and assay-specific motif discovery tools
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; detailed hyperparameter search results; statistical significance testing for performance comparisons; complete benchmarking protocols for all datasets

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing architecture that addresses a genuine need in genomic deep learning for interpretable models. The core idea of decomposing predictions into independent CNN units with linear combination is elegant and builds sensibly on NAMs. However, the evidence provided does not fully establish the claimed advantages. Performance comparisons lack statistical rigor, the interpretability claims require more systematic validation, and several benchmarking choices raise questions about generalizability. The work is potentially valuable but requires substantial additional evidence to support the central claims.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or applying deep learning methods to regulatory genomics. Researchers studying TF binding, chromatin accessibility, and cis-regulatory logic would find the interpretability features attractive. The plug-and-play aspects with JASPAR and pretrained models may appeal to bench biologists seeking accessible analysis tools. The de novo motif discovery application has broad relevance to the gene regulation community.
- **Major strengths** The architectural design is conceptually clean and directly addresses interpretability limitations of standard CNNs. The authors demonstrate application across diverse data types (ChIP-seq, ATAC-seq, scATAC-seq, STARR-seq, in vitro binding assays), which supports generalizability claims. The transfer learning approach with pretrained DanQ models is innovative and provides a practical solution for distinguishing paralogous TFs. The computational efficiency advantages over post-hoc interpretation methods are compelling and practically relevant.
- **Major Concerns** Performance comparisons lack statistical validation with no confidence intervals or significance testing reported. The claim that ExplaiNN performs "comparably" to state-of-the-art models is based on small performance differences that may not be meaningful without error bars. The interpretability validation is largely qualitative, relying on visual inspection of logos and heatmaps rather than quantitative assessment of interpretability quality. The inability to capture heterotypic interactions is acknowledged but the practical impact of this limitation is not systematically assessed. The choice of 100 units for de novo motif discovery appears arbitrary without systematic optimization.
- **Technical failings that need to be addressed before the case is established** Absence of statistical significance testing for all performance comparisons; lack of confidence intervals or repeated runs; no systematic ablation studies to justify architectural choices; insufficient detail on hyperparameter selection; no quantitative evaluation of interpretability quality; missing analysis of failure cases or limitations in specific data types.
- **Assessment against Nature-style criteria** Originality: The NAM-inspired architecture applied to genomics is novel and represents a meaningful conceptual contribution. Scientific importance: Addresses a real bottleneck in genomic deep learning adoption, with potential broad impact on regulatory genomics research. Interdisciplinary readership: The interpretability focus and plug-and-play design could attract non-specialist users, but the manuscript assumes familiarity with deep learning concepts. Technical soundness: The core architecture is sound, but the evaluation methodology has significant gaps in statistical rigor. Readability for nonspecialists: The main text is generally accessible, though some methodological details require domain expertise.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical validation of performance claims and more rigorous interpretability assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "ExplaiNN performed comparably to state-of-the-art models" across multiple tasks
- **Evidence pointer** Figures 1B-C, 3B-D, 4A-B; location not provided
- **Concern** All performance comparisons are reported as single point estimates without confidence intervals, standard deviations across multiple runs, or statistical significance testing. The differences between ExplaiNN and comparison models are often small (e.g., 1-2% PCC difference with AI-TAC in Figure 4A), and without error bars it is impossible to determine whether these differences are meaningful. Deep learning models are stochastic, and the absence of repeated runs or significance testing undermines the central claim of comparable performance.
- **Why it matters** The manuscript's primary claim is that ExplaiNN achieves state-of-the-art performance while providing interpretability. If the performance differences are within noise, the claim of "comparable performance" is not established. Conversely, if ExplaiNN is actually worse, the trade-off between interpretability and performance needs to be honestly quantified.
- **Resolution test** Provide performance metrics from at least 5 independent training runs for each model and dataset, report mean and standard deviation, and perform appropriate statistical tests (e.g., paired tests across test sets, or confidence interval overlap analysis) for all key comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability validation
- **Claim pointer** "ExplaiNN provides global interpretability" and "local interpretability" through unit importance scores
- **Evidence pointer** Figures 1F-G, 4C-E, 5A-C; location not provided
- **Concern** The interpretability claims are validated primarily through visual inspection of heatmaps and logos. The authors show that units can be annotated with TF motifs and that importance scores align with expected biology, but there is no quantitative assessment of interpretability quality. For example, how do unit importance scores compare to established attribution methods in terms of accuracy or reliability? How sensitive are the interpretations to hyperparameter choices or training runs? The claim that interpretations are "intuitive and simple" is subjective without user studies or quantitative metrics.
- **Why it matters** The central value proposition of ExplaiNN is interpretability. If the interpretations are not systematically validated, the main advantage over existing methods is not established. Visual inspection can be misleading, and the field needs quantitative benchmarks for interpretability.
- **Resolution test** Provide quantitative comparisons between ExplaiNN interpretations and established methods (e.g., DeepLIFT, integrated gradients) on benchmark datasets with known ground truth motifs. Include metrics such as motif recovery rate, localization accuracy, or agreement with known regulatory mechanisms. Consider user studies or structured evaluation of interpretability quality.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Benchmarking completeness
- **Claim pointer** "ExplaiNN performs as well as state-of-the-art models" and "comparable to leading methods specialized for the independent tasks"
- **Evidence pointer** Figures 1B-C, 3B-D, 4A-B; location not provided
- **Concern** The benchmarking is incomplete in several respects. First, for TF binding prediction, only DanQ and CNN variants are used as baselines; more recent state-of-the-art models (e.g., Enformer, Basenji) are not included. Second, the comparison with STREME for de novo motif discovery uses only AUPRC as a metric, which may not capture all aspects of motif discovery quality. Third, the hyperparameter optimization for comparison models is not described, raising concerns about whether they are fairly tuned. Finally, the choice of 100 units for de novo motif discovery and 300-400 units for other tasks is not systematically justified.
- **Why it matters** The claim of "comparable performance" depends on the fairness and completeness of the benchmarking. If comparison models are not optimally tuned or if more recent models are excluded, the performance claims may not hold in broader contexts.
- **Resolution test** Include more recent state-of-the-art baselines where feasible, describe hyperparameter optimization procedures for all models, provide ablation studies on the number of units, and use additional evaluation metrics for motif discovery (e.g., motif enrichment, positional accuracy).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability assessment
- **Claim pointer** "ExplaiNN is suitable for the analysis of single-cell chromatin accessibility data" and "plug-and-play platform"
- **Evidence pointer** Figures 5A-C, 6A-G; location not provided
- **Concern** The single-cell analysis is limited to one dataset (pancreatic islets) and the results are compared only qualitatively to the original study's findings. The plug-and-play experiments with JASPAR initialization show that frozen filters perform poorly, which is acknowledged, but the unfrozen case is not compared systematically against training from scratch. The transfer learning with DanQ models is demonstrated for only two TF families (IRF and PAX), and the generalizability to other families is unclear.
- **Why it matters** The claims of broad applicability and plug-and-play functionality require demonstration across diverse scenarios. The current evidence is suggestive but not conclusive, particularly given the acknowledged performance drop with frozen JASPAR filters.
- **Resolution test** Apply ExplaiNN to additional single-cell datasets from different tissues, systematically evaluate the JASPAR initialization strategy across multiple datasets and filter sets, and test the DanQ transfer learning approach on additional TF families with varying degrees of binding specificity similarity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Methodological justification
- **Claim pointer** "The main difference between ExplaiNN and a standard CNN is that the learned weights of each unit from the final linear layer are interpretable"
- **Evidence pointer** Methods section, Figure 1A; location not provided
- **Concern** The architectural choices are not systematically justified. The use of exponential activation in the convolutional layer is cited to prior work, but the specific choices of filter size (19), pooling strategy (max pooling with kernel 7 and stride 7), and fully connected layer sizes (100 nodes) are not explained or optimized. The relationship between the number of units and model capacity is not explored beyond the saturation analysis in Figure 1B. The claim that the architecture is "inspired by NAMs" is reasonable, but the specific design decisions and their impact on interpretability and performance are not thoroughly examined.
- **Why it matters** For a methods paper, the architectural choices should be justified either through theoretical arguments, ablation studies, or systematic hyperparameter optimization. Without this, it is unclear whether the reported performance is specific to these choices or general to the approach.
- **Resolution test** Provide ablation studies on key architectural components (filter size, pooling strategy, number of units, activation functions) and describe the hyperparameter search procedure. If computational constraints prevent exhaustive search, provide a clear rationale for the chosen values based on prior work or theoretical considerations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1B
- **Evidence pointer** Figure 1B; location not provided
- **Issue** The performance saturation plot would benefit from error bars or confidence bands to show the variability across training runs. The current presentation makes it difficult to assess whether the plateau at 100 units is robust.
- **Required correction** Add error bars or confidence intervals to the performance curves in Figure 1B, or state in the figure legend that these are single runs.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, model training
- **Evidence pointer** Methods, "Model training"; location not provided
- **Issue** The early stopping criteria is described as "when the model performance on the validation set did not improve" but the patience parameter and evaluation frequency are not specified. This makes it difficult to reproduce the exact training procedure.
- **Required correction** Specify the early stopping patience, evaluation frequency, and the metric used for early stopping decisions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion of limitations
- **Evidence pointer** Discussion section; location not provided
- **Issue** The discussion acknowledges the limitation regarding heterotypic interactions but does not discuss other potential limitations, such as the fixed filter size limiting motif discovery to short motifs, or the potential redundancy between units learning similar motifs.
- **Required correction** Add a more comprehensive limitations paragraph addressing these and other potential constraints of the approach.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 3C
- **Evidence pointer** Figure 3C; location not provided
- **Issue** The correlation between performance difference and dataset size is described qualitatively. A correlation coefficient and p-value would strengthen the claim that STREME performs better for small datasets.
- **Required correction** Report the correlation coefficient and p-value for the relationship shown in Figure 3C, or state that the relationship is qualitative.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Code availability
- **Evidence pointer** Methods section; location not provided
- **Issue** The manuscript mentions open-source software but does not provide a specific repository URL or version information in the main text.
- **Required correction** Include the software repository URL and version number in the main text or a dedicated availability section.

## Risk / unsupported claims
- The claim that ExplaiNN "performs as well as state-of-the-art models" is not statistically supported due to the absence of confidence intervals and significance testing
- The claim that interpretations are "intuitive and simple" is subjective and not validated through user studies or quantitative metrics
- The claim that ExplaiNN is a "plug-and-play platform" is not fully supported given the poor performance of frozen JASPAR-initialized models
- The generalizability of the transfer learning approach to other TF families beyond IRF and PAX is not demonstrated
- The claim that ExplaiNN provides "both local and global interpretability" is not quantitatively validated against existing interpretability methods
- The assertion that performance differences with AI-TAC are "comparable" (1-2% PCC difference) is not supported without error bars or statistical testing