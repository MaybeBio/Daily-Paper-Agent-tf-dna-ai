## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and figure legends
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and significance of claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors introduce GrID-Net, a graph neural network that generalizes Granger causal inference to DAG-structured single-cell trajectories, enabling detection of causal locus-gene associations from co-assayed scATAC-seq and scRNA-seq data. They apply this to schizophrenia GWAS variants, reporting increased variant coverage, identification of 132 dysregulated genes, and evidence for neural transcription-factor binding disruptions in SCZ etiology.
- **Visible evidence base** Main text figures (Fig. 1-4), supplementary figure references, methods descriptions, and statistical analyses as described
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; detailed GrID-Net formulation relegated to Supplementary Information; code repository not independently verified; full parameter sensitivity analyses not visible

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting extension of Granger causality to partial orderings represented as DAGs, applied to single-cell multimodal data. The "cell-state parallax" framing is evocative and potentially useful. However, the manuscript as presented has several critical gaps that prevent full evaluation of the method's validity and the strength of the biological claims. The core methodological details are deferred to supplementary materials, making it impossible to assess the soundness of the causal inference framework. The benchmarking strategy, while reasonable in principle, raises questions about circularity and the interpretation of eQTL overlap as ground truth. The biological findings, while potentially interesting, are presented with limited validation and may overstate causal certainty given the observational nature of the data and the indirectness of the inference.

- **Who would be interested in the results, and why** Computational biologists developing methods for single-cell multi-omics integration and causal inference; statistical geneticists working on variant-to-function mapping for complex diseases; researchers studying gene regulation in neurodevelopment and psychiatric disorders. The methodological advance of Granger causality on DAGs could have broader applicability beyond genomics.

- **Major strengths**
  1. The conceptual framing of "cell-state parallax" is novel and provides an intuitive way to think about asynchronous relationships between epigenetic and transcriptional states.
  2. The generalization of Granger causality to partial orderings is a genuine theoretical contribution that could have impact beyond this specific application.
  3. The application to schizophrenia genetics addresses a critical bottleneck in the field, and the identification of specific genes and TF binding disruptions provides testable hypotheses.
  4. The benchmarking against multiple existing methods across four diverse datasets strengthens the claims of generalizability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The claim that GrID-Net "generalizes Granger causal inference to detect new causal locus-gene associations in graph-structured systems" is central to the paper, but the actual implementation is not described in sufficient detail.
- **Evidence pointer** Methods section "GrID-Net formulation" refers to Supplementary Information; no algorithmic details, loss functions, or architectural specifics are provided in the main text
- **Concern** The core methodological contribution is entirely deferred to supplementary materials. The main text provides only a high-level description of "lagged message-passing on a graph neural network" without specifying how the lag is parameterized, how the DAG is constructed from the k-NN graph, how cycles are broken, or how the Granger test statistic is computed. This is insufficient for a methods-focused paper in a Nature journal. The reader cannot evaluate whether the method is correctly implementing Granger causality, whether the statistical test is valid, or whether the approach has the claimed advantages over existing methods.
- **Why it matters** Without access to the full methodological details, the central claims of the paper cannot be independently assessed or reproduced. This is a fundamental requirement for publication in a high-impact venue.
- **Resolution test** The full GrID-Net formulation, including architectural details, loss functions, hyperparameter choices, and the exact procedure for computing Granger causal strengths and significance, must be included in the main text or a fully accessible supplement. The authors should provide pseudocode or a clear algorithmic description.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmarking validity
- **Claim pointer** The claim that GrID-Net "significantly outperforms existing state-of-the-art approaches" for identifying locus-gene links is based on eQTL overlap as ground truth.
- **Evidence pointer** Figure 2a-c; Methods "eQTL evaluations"
- **Concern** The use of eQTL overlap as the primary benchmark for causal locus-gene links is problematic. eQTLs represent statistical associations between genetic variants and gene expression, which are themselves subject to confounding and do not necessarily reflect causal regulatory relationships. More critically, the comparison against correlation-based methods may be inherently biased: GrID-Net is designed to detect asynchronous relationships, and the eQTL benchmark may preferentially capture such relationships if the underlying eQTL data come from tissues undergoing dynamic processes. The authors do not address this potential circularity. Additionally, the eQTL data are from bulk tissues, while the single-cell predictions are cell-type-specific, creating a mismatch in resolution that could bias results.
- **Why it matters** If the benchmark is biased in favor of the proposed method, the claimed superiority may not reflect genuine methodological advantage. The validity of the entire evaluation strategy depends on the appropriateness of eQTLs as ground truth for causal locus-gene relationships.
- **Resolution test** The authors should provide a more critical discussion of the limitations of eQTL-based benchmarking, including potential biases. They should also consider additional validation strategies, such as comparison against experimentally validated enhancer-gene pairs (e.g., from CRISPR screens) or demonstrating that GrID-Net's predictions are enriched for known causal variants in independent datasets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The claim that GrID-Net identifies "132 genes" dysregulated by SCZ variants and that these are enriched for relevant biological pathways.
- **Evidence pointer** Figure 3; Methods "Linking SCZ GWAS variants to genes"
- **Concern** The statistical framework for determining significance of GrID-Net scores is not described. How are p-values or false discovery rates computed for the 132 gene associations? What is the null distribution? How is multiple testing correction applied across the genome-wide set of peak-gene pairs? The enrichment analyses (GSEA, Enrichr) are reported with FDR values, but the input gene sets are derived from a thresholded list of 132 genes, and the sensitivity of these enrichments to the threshold is not explored. Furthermore, the comparison with the original SCZ GWAS study's gene assignments is not clearly quantified beyond a statement of overlap.
- **Why it matters** Without a clear statistical framework, the reader cannot assess whether the 132 genes represent a robust signal or are an artifact of thresholding and multiple testing. The biological conclusions depend critically on the validity of these statistical inferences.
- **Resolution test** The authors should provide a complete description of the statistical testing procedure, including how significance is determined, how multiple testing is controlled, and how the 132-gene set is derived. They should also provide sensitivity analyses showing how results change with different thresholds and demonstrate that the enrichment signals are robust.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** The claim that GrID-Net "uncovered causal regulatory mechanisms" and specifically that TF binding disruptions are "putative drivers of SCZ disease pathogenesis."
- **Evidence pointer** Figure 4; Discussion
- **Concern** The biological validation is limited. The correlation between predicted TF binding affinity changes and differential expression in SCG GPCs is suggestive but does not establish causality. The specific examples (e.g., SLC12A6 repression via increased TF binding) are presented as mechanistic hypotheses but are not experimentally validated. The manuscript would be substantially strengthened by at least one experimental validation, such as CRISPR perturbation of a predicted enhancer or TF binding site, or demonstration that the predicted regulatory effects are consistent with chromatin conformation data.
- **Why it matters** The title and framing of the paper emphasize "causal regulatory mechanisms," but the evidence presented is entirely computational. Without experimental validation, the causal claims are overstated and the practical utility of the method for therapeutic target discovery remains unproven.
- **Resolution test** The authors should either provide experimental validation of at least one or two key predictions or substantially temper the causal language throughout the manuscript, clearly framing the results as computational predictions that require experimental follow-up.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Robustness and generalizability
- **Claim pointer** The claim that GrID-Net's performance is "robust to various hyperparameter choices" and that it generalizes across datasets.
- **Evidence pointer** Supplementary Figures S2, S5; Methods "GrID-Net training details and hyperparameters"
- **Concern** The hyperparameter sensitivity analysis is referenced but not visible. The manuscript reports results on four datasets, but the DAG construction procedure, which is critical to the method, may be sensitive to the choice of k in the k-NN graph, the pseudotime inference method, and the cycle-breaking procedure. The authors do not discuss how these choices affect results. Additionally, the application to SCZ uses only one dataset (10x Multiome corticogenesis), and the generalizability of the method to other tissues and disease contexts is not demonstrated.
- **Why it matters** For a method to be broadly useful, its performance should be robust to reasonable variations in preprocessing and hyperparameter choices. The current presentation does not allow the reader to assess this robustness.
- **Resolution test** The authors should provide the full hyperparameter sensitivity analysis and discuss the impact of DAG construction choices on results. They should also demonstrate the method's applicability to at least one additional disease or tissue context beyond corticogenesis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1 legend
- **Issue** The figure legend is dense and attempts to explain the entire framework in a single panel. The connection between "cell-state parallax" and the DAG representation is not immediately clear from the figure alone.
- **Required correction** Consider splitting Figure 1 into multiple panels with clearer annotations, or providing a schematic that more explicitly maps the conceptual framework to the computational implementation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The term "causal" is used liberally throughout, but the method infers Granger causality, which is a specific statistical notion of predictive causality and does not necessarily imply true causal mechanisms. This distinction should be made more explicit.
- **Required correction** Add a sentence clarifying that Granger causality is a form of statistical causality based on predictive power, and that the inferred relationships are causal hypotheses requiring experimental validation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Code availability
- **Evidence pointer** Introduction (code link), Methods
- **Issue** The code repository is mentioned but not described in terms of dependencies, installation instructions, or usage examples. The exact version of the code used for the analyses is not specified.
- **Required correction** Provide a detailed README with installation and usage instructions, specify the exact code version used, and consider depositing the code in a permanent archive (e.g., Zenodo) with a DOI.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods, Data sources
- **Evidence pointer** Methods "Single-cell multimodal datasets"
- **Issue** The specific accessions or download links for the four datasets are not provided in the main text. While the original studies are cited, direct access to the processed data would facilitate reproduction.
- **Required correction** Provide explicit data access information (e.g., GEO accession numbers, SRA IDs) for each dataset in the Methods or Data Availability section.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Figure 3c
- **Evidence pointer** Figure 3c legend
- **Issue** The figure shows long-range variant-gene associations, but the biological significance of these long-range interactions is not discussed. Are these consistent with known 3D genome architecture in the relevant cell types?
- **Required correction** Add a brief discussion of whether the long-range interactions are supported by independent evidence, such as Hi-C data in similar cell types, and what fraction of the identified associations are consistent with known chromatin loops.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 2a-c
- **Evidence pointer** Figure 2 legend
- **Issue** The figure legend states that Welch's t-test was used, but the number of comparisons and how multiple testing was handled across the four datasets is not stated.
- **Required correction** Clarify whether multiple testing correction was applied across datasets and, if so, what method was used.

## Risk / unsupported claims
1. The claim that GrID-Net "uncovered causal regulatory mechanisms" is not supported by the evidence presented, which is entirely computational and based on Granger causality, a statistical notion of predictive causality.
2. The claim of "132 genes dysregulated by SCZ variants" is presented without a clear statistical framework for how these genes were identified and whether this list is robust to threshold choices.
3. The claim that TF binding disruptions are "putative drivers of SCZ disease pathogenesis" is speculative and not validated experimentally.
4. The claim of superior performance over existing methods is based on eQTL overlap as ground truth, which may be biased in favor of the proposed method and does not necessarily reflect true causal relationships.
5. The generalizability of the method beyond the four tested datasets and the specific application to corticogenesis is not demonstrated.
6. The robustness of the method to DAG construction choices (k-NN parameter, pseudotime inference, cycle-breaking) is referenced but not visible in the provided materials.