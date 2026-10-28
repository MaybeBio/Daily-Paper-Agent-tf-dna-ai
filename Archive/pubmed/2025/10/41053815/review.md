## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and figure legends
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present Cisformer, a cross-attention-based generative transformer model for bidirectional single-cell RNA-ATAC translation. They claim superior performance over existing methods (BABEL, scButterfly, ArchR, SCARlink) in generation accuracy and generalization, and demonstrate interpretability via attention scores to identify cell-type-specific transcription factors and cis-regulatory elements in cancer and aging contexts.
- **Visible evidence base** Main text descriptions of results, figure legends (Figs 1-5), methods section, and supplementary figure list
- **Missing materials affecting confidence** Actual figures and supplementary figures are not provided; quantitative results (exact metrics, confidence intervals, statistical test details) are only described qualitatively; no code or data availability statement is visible; no detailed benchmark hyperparameters or ablation studies are shown

## Reviewer

- **Overall assessment** The manuscript addresses an important problem in single-cell genomics: cross-modality generation between gene expression and chromatin accessibility. The proposed architecture, particularly the feature duplication and index encoding strategy for handling ultra-long peak sequences, is a novel and potentially impactful contribution. However, the current evidence base is insufficient to fully evaluate the claims. Key quantitative results are described only in text without visible figures or tables, making it impossible to assess the magnitude of improvements, statistical significance, or robustness of the findings. The interpretability analyses are intriguing but require more rigorous validation against established regulatory annotations. The manuscript is well-written and the methods are described in sufficient detail for replication, but the lack of visible results limits confidence in the stated conclusions.

- **Who would be interested in the results, and why** Computational biologists developing deep learning methods for single-cell multiomics integration would be directly interested. Researchers studying gene regulation, particularly cis-regulatory element function and transcription factor biology, would find the interpretability framework valuable. The cancer and aging applications broaden the appeal to translational researchers. The scalable architecture and memory-efficient attention mechanism may also interest those working on large-scale single-cell datasets.

- **Major strengths**
  1. The cross-attention decoder-only architecture is a well-motivated departure from AE/VAE-based approaches, potentially offering better interpretability without sacrificing generation quality.
  2. The feature duplication and index encoding strategy directly addresses a practical bottleneck (ultra-long peak sequences) in a creative way.
  3. The bidirectional design (RNA-to-ATAC and ATAC-to-RNA) is comprehensive and allows for cross-validation of regulatory inferences.
  4. The application to pan-cancer and aging datasets demonstrates real-world utility beyond benchmark performance.
  5. The attention-based interpretability framework is a significant step toward making generative models biologically useful.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** "Cisformer substantially outperformed BABEL and scButterfly in both inter-dataset scenarios" and "Cisformer achieved superior or comparable performance in gene expression prediction"
- **Evidence pointer** Figure 2, Additional file 1: Fig. S2, S4; location not provided for exact metrics
- **Concern** The quantitative results supporting the central performance claims are not visible in the provided materials. The text describes bar plots, UMAP visualizations, and correlation metrics, but the actual figures are absent. Without seeing the magnitude of differences, error bars, or statistical tests, it is impossible to verify whether the claimed improvements are meaningful or within noise.
- **Why it matters** The core contribution of this manuscript is the claimed performance advantage over existing methods. If this advantage is marginal or not statistically robust, the practical value of Cisformer is substantially diminished. The inter-dataset generalization claim is particularly important because it addresses a known limitation of existing methods.
- **Resolution test** Provide the actual figures with clear axis labels, error bars or confidence intervals, and statistical significance tests (e.g., paired tests across cell types or datasets). Report exact numeric values for all metrics in the text or tables.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** "Cisformer effectively captures the relationship between genes and CREs when translating transcriptome to chromatin accessibility"
- **Evidence pointer** Figure 3, Additional file 1: Fig. S3; location not provided
- **Concern** The interpretability validation relies on attention scores as proxies for regulatory relationships. While the correlation with TF binding data (ChIP-seq) and GWAS variant enrichment is encouraging, the validation is limited to a small number of TFs and cell types. The manuscript does not compare attention-based regulatory inferences against established methods for enhancer-gene linking (e.g., ABC model, Hi-C-based approaches) or against known regulatory databases beyond the limited ChIP-seq comparison.
- **Why it matters** The claim that Cisformer "captures" regulatory effects is strong. Attention scores in transformers are known to be imperfect explanations. Without systematic benchmarking against established regulatory annotations and alternative linking methods, the biological interpretability claim remains suggestive rather than conclusive.
- **Resolution test** Expand validation to include multiple independent regulatory databases (e.g., ENCODE cCREs, FANTOM5 enhancers), compare against state-of-the-art enhancer-gene linking tools, and quantify performance using established metrics (e.g., AUROC for known regulatory pairs). Include negative controls (e.g., shuffled peak sets, non-regulatory regions).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** "Cisformer employs a decoder-only architecture with a cross-attention mechanism" and "we propose an innovative feature duplication and selection strategy"
- **Evidence pointer** Methods section, Figure 1; location not provided
- **Concern** The methods section describes the architecture but lacks critical details needed for replication and fair comparison. Specifically: (1) the exact training procedure, including number of epochs, learning rate schedule details, and early stopping criteria, is only partially specified; (2) the feature duplication strategy is described conceptually but the implementation details (how many times features are duplicated, how selection is performed) are unclear; (3) no ablation studies are presented to justify design choices such as the number of layers, embedding dimensions, or the duplication factor; (4) the baseline methods (BABEL, scButterfly, ArchR, SCARlink) are not described in terms of their hyperparameters or whether they were used with default settings.
- **Why it matters** Without these details, the reported performance cannot be independently reproduced, and it is unclear whether the improvements come from the architecture, the data preprocessing, or the training strategy. Ablation studies are essential to establish which components contribute to the claimed performance.
- **Resolution test** Provide complete training details, including all hyperparameters and a clear description of the feature duplication and selection algorithm. Add ablation studies that systematically remove or vary key components (e.g., duplication factor, cross-attention vs. self-attention, number of layers) and report their impact on performance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** "Cisformer demonstrated the ability to mitigate batch effects" and "the high-confidence CRE-gene pairs exhibited significantly stronger peak-gene expression correlations than the random background"
- **Evidence pointer** Additional file 1: Fig. S4c, Figure 3d; location not provided
- **Concern** The statistical methods used to support these claims are not described. For the batch effect mitigation claim, no quantitative metric (e.g., kBET, LISI, or batch entropy) is mentioned. For the correlation comparison, the text states "significantly stronger" but does not specify the test used, the sample size, or how multiple testing was handled across the different thresholds.
- **Why it matters** These claims are central to demonstrating both practical utility (batch effect handling) and biological validity (CRE-gene linking). Without proper statistical reporting, the significance of these findings cannot be assessed.
- **Resolution test** Specify the exact statistical tests used, report effect sizes with confidence intervals, and describe how multiple testing corrections were applied. For batch effects, use established quantitative metrics and report their values.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "Cisformer is a scalable cross-modality generation framework" and "we applied it to a pan-cancer dataset encompassing over 1 million cells"
- **Evidence pointer** Figure 4, Additional file 1: Fig. S4; location not provided
- **Concern** The scalability claim is supported by application to a large dataset, but no runtime, memory usage, or scaling analysis is presented. The manuscript does not report how training time or inference time scales with dataset size, number of peaks, or number of cells. Additionally, the pan-cancer analysis uses only 144,409 cells with paired data, which is a subset of the over 1 million cells mentioned.
- **Why it matters** Scalability is a key claimed advantage, but without quantitative evidence, it is unclear whether Cisformer can handle datasets at the scale of modern atlases (millions of cells) within reasonable computational budgets. The discrepancy between the total dataset size and the analyzed subset needs clarification.
- **Resolution test** Provide runtime and memory benchmarks across different dataset sizes. Clarify why only a subset of cells was used and whether the full dataset was processed. Report scaling behavior in terms of both training and inference.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1b description
- **Evidence pointer** Figure 1b, Methods section
- **Issue** The description of the feature duplication and selection strategy is difficult to follow. The text mentions "multiple pseudo-cells from a single original cell" but does not clearly explain how this relates to the duplication factor or how the selection of active and inactive CREs is balanced.
- **Required correction** Provide a step-by-step algorithmic description or pseudocode for the feature duplication and selection process, including how the number of pseudo-cells is determined and how the balance between active and inactive CREs is maintained.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Methods section
- **Issue** The manuscript does not include a data availability statement or a code availability statement. Given the importance of reproducibility in computational biology, this is a significant omission.
- **Required correction** Add explicit statements on data and code availability, including links to repositories, version numbers, and any relevant accession codes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Figure 3a
- **Evidence pointer** Figure 3a, Additional file 1: Fig. S3a
- **Issue** The text states that chromatin remodeler genes exhibited the highest attention scores, followed by transcription factor genes. However, the biological interpretation of this ranking is not discussed. It is unclear whether this reflects a genuine biological signal or an artifact of the model's training data composition.
- **Required correction** Discuss the potential biological basis for this ranking and consider whether it could be influenced by gene length, expression level, or peak density. If possible, include a control analysis using randomly selected gene sets.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Aging analysis
- **Evidence pointer** Figure 5, Methods section
- **Issue** The aging analysis is limited to two cell types (PCT and TAL) in the mouse kidney. The rationale for focusing on these cell types and the generalizability of the findings to other kidney cell types or other tissues is not discussed.
- **Required correction** Justify the choice of cell types and discuss whether the identified aging-associated TFs are expected to be cell-type-specific or broadly applicable. Consider including a broader analysis if feasible.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations is brief and focuses primarily on future extensions rather than current weaknesses. The manuscript does not address potential failure modes of the model, such as performance on rare cell types or highly sparse datasets.
- **Required correction** Expand the limitations section to include a candid assessment of scenarios where Cisformer may underperform, and suggest potential mitigation strategies.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (missing quantitative evidence), R1-M2 (insufficient validation of interpretability), R1-M3 (incomplete methodological details and missing ablations)

## Risk / unsupported claims
- The claim of "substantially outperformed" existing methods cannot be verified without visible quantitative results.
- The claim that Cisformer "effectively captures" regulatory relationships is supported only by limited validation and requires more systematic benchmarking.
- The scalability claim is not supported by any quantitative runtime or memory analysis.
- The batch effect mitigation claim is not supported by any quantitative metric.
- The statement that "Cisformer emerges as a powerful tool" in the conclusions is an overstatement given the current evidence base.
- The claim that the model "holds great potential for providing deeper insights" is speculative and not directly supported by the presented results.
- The specific numbers mentioned in the methods (e.g., 38,244 genes, 1,033,239 CREs, 144,409 cells) are stated but not contextualized with respect to how they affect model performance or generalizability.