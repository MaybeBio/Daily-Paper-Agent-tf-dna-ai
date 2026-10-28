## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, claims, and evidence presented in the manuscript
- **Shared manuscript claim summary** The authors present maxATAC, a suite of deep neural network models for genome-scale transcription-factor binding site (TFBS) prediction from ATAC-seq data. They curate a large benchmark dataset of paired ChIP-seq and ATAC-seq experiments across 20 cell types, train models for 127 human TFs, and demonstrate performance improvements over motif scanning and comparable performance to existing deep learning methods. They further show applicability to scATAC-seq and primary cells, and demonstrate utility in identifying TFBS at atopic dermatitis risk loci.
- **Visible evidence base** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supporting information references
- **Missing materials affecting confidence** Figures, tables, and supplementary data referenced in the text are not available for direct inspection. Code and data availability are stated but not verified.

## Reviewer
- **Overall assessment** This manuscript presents a valuable and timely resource for the genomics community. The authors have addressed a clear gap: the lack of state-of-the-art TFBS prediction tools specifically designed for ATAC-seq data, which has become the dominant chromatin accessibility assay. The scale of the curated benchmark dataset (127 TFs, 20 cell types) is impressive and represents a significant contribution in itself. The methodological choices, including peak-centric and pan-cell training strategies, are well-reasoned and supported by ablation-style comparisons. The demonstration of generalizability to scATAC-seq and primary cells strengthens the practical utility of the resource. The application to atopic dermatitis genetics provides a compelling use case. However, several technical aspects require clarification and additional validation before the full claims of the manuscript can be considered established.

- **Who would be interested in the results, and why** This work will be of high interest to computational biologists and bioinformaticians working on gene regulatory networks, TF binding prediction, and ATAC-seq analysis. It will also appeal to experimental biologists who use ATAC-seq and seek to interpret their data in terms of TF activity without performing ChIP-seq for every TF of interest. The clinical genetics community, particularly those studying complex diseases with noncoding risk variants, will find the application to atopic dermatitis relevant. The benchmark dataset itself will be a valuable resource for method development and comparison.

- **Major strengths**
  1. The scale and curation of the benchmark dataset is a major strength. The authors have gone to significant effort to curate paired ChIP-seq and ATAC-seq data, with careful attention to experimental conditions and quality control.
  2. The methodological innovations, particularly peak-centric and pan-cell training, are well-motivated and demonstrate clear improvements over standard approaches, especially in the low-data regime.
  3. The comprehensive benchmarking against multiple baselines (motif scanning, average ChIP-seq signal, TOBIAS, Leopard) provides a thorough assessment of performance.
  4. The demonstration of generalizability to scATAC-seq and primary cells addresses a key practical need.
  5. The application to atopic dermatitis genetics showcases a realistic and impactful use case, highlighting the unique capabilities of the method beyond simple motif analysis.
  6. The user-friendly codebase and availability of processed data will facilitate community adoption.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that maxATAC models offer "high-performance TFBS prediction from ATAC-seq at genome scale" with median AUPR of .43 and median precision at 5% recall of .85 across 74 benchmarkable TFs.
- **Evidence pointer** Results section, Figures 3A-3B, S2 Table
- **Concern** The AUPR values reported are modest in absolute terms (median .43). While the authors correctly note that this is comparable to state-of-the-art methods, the claim of "high-performance" may be overstated. More importantly, the manuscript does not provide a clear analysis of how performance varies across different types of TFs (e.g., pioneer factors vs. settler factors, TFs with strong vs. weak motifs, TFs with broad vs. narrow binding patterns). Understanding these performance characteristics is crucial for users to know when to trust predictions. The authors should provide a stratified analysis of performance by TF class, motif quality, and binding pattern.
- **Why it matters** Without understanding performance heterogeneity, users may apply maxATAC inappropriately to TFs where it performs poorly. This could lead to incorrect biological conclusions.
- **Resolution test** Provide a supplementary analysis showing AUPR distributions stratified by TF family, motif information content, and binding pattern (e.g., broad vs. narrow peaks). Discuss which classes of TFs are most and least predictable, and provide guidance to users on expected performance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "maxATAC performance extends to scATAC-seq" and demonstrate this on a mixed-cell-line experiment.
- **Evidence pointer** Results section, Figure 4
- **Concern** The scATAC-seq evaluation is limited to a single mixed-cell-line experiment. While this is a reasonable starting point, it does not adequately demonstrate generalizability to the diverse range of scATAC-seq datasets and conditions that users will encounter. The authors should evaluate performance on additional scATAC-seq datasets, including those from primary tissues, different platforms (e.g., 10x Multiome, sci-ATAC-seq), and different data processing pipelines. Additionally, the manuscript does not address how the choice of pseudobulk clustering parameters affects TFBS prediction performance.
- **Why it matters** scATAC-seq is a key application area for maxATAC, and users need confidence that the method works robustly across different experimental contexts. Limited evaluation on a single dataset does not establish this.
- **Resolution test** Evaluate maxATAC on at least 2-3 additional scATAC-seq datasets from different sources and platforms. Provide guidance on recommended pseudobulk construction parameters and their impact on prediction performance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that maxATAC "identifies TFBS associated with allele-dependent chromatin accessibility at atopic dermatitis genetic risk variants" and specifically highlight MYB and FOXP1 as TFs with the greatest differential binding.
- **Evidence pointer** Results section, Figure 7
- **Concern** The atopic dermatitis application is presented as a demonstration of maxATAC's utility, but the analysis appears to be purely computational and lacks experimental validation. The authors identify predicted differential TFBS between one AD patient and one control, but do not validate any of these predictions experimentally (e.g., by ChIP-qPCR, reporter assays, or CRISPR perturbation). Furthermore, the analysis is based on a single patient-control pair, which provides no statistical power. The authors acknowledge this limitation ("limited in statistical power") but still present the findings as demonstrating maxATAC's capabilities.
- **Why it matters** Without experimental validation or replication across multiple individuals, the biological significance of the identified TFBS remains uncertain. The claim that maxATAC can "uncover molecular regulatory mechanisms in complex diseases" is not fully supported by this analysis.
- **Resolution test** Either (a) provide experimental validation of at least a subset of the predicted differential TFBS, or (b) expand the analysis to include multiple AD patients and controls with appropriate statistical testing, or (c) reframe this section as a proof-of-concept demonstration of the computational workflow rather than a biological discovery.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that the maxATAC benchmark dataset is "organized (quality-controlled, processed, ready-to-go) for community download and development" and provide a DOI.
- **Evidence pointer** Data Availability section, Discussion
- **Concern** While the data availability statement is commendable, the manuscript does not provide sufficient detail on the exact processing steps and file formats for the benchmark dataset. The methods section describes the general approach but lacks specifics on data structures, coordinate systems, and how users should integrate the data with their own pipelines. Additionally, the code repository is mentioned but not described in terms of its structure, dependencies, or usage examples.
- **Why it matters** For a resource paper, reproducibility and ease of use are paramount. Users need clear documentation to effectively utilize the benchmark data and code.
- **Resolution test** Provide a detailed data dictionary and processing pipeline description in the supplementary materials. Include a clear README for the code repository with installation instructions, usage examples, and expected outputs.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that maxATAC is "the largest collection of high-performance TFBS prediction models for ATAC-seq" but does not provide quantitative context for this claim. It would be helpful to state the number of TFs (127) and the median AUPR in the abstract.
- **Required correction** Add the number of TFs and a summary performance metric to the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Comparison to other methods
- **Evidence pointer** Results section, Figure 3F
- **Concern** The comparison to DeepGRN, FactorNet, and Leopard is indirect, relying on published results from different benchmarks. While the authors acknowledge this limitation, a direct comparison on the same test data would be more convincing.
- **Required correction** If feasible, run the comparison methods on the maxATAC benchmark data for the overlapping TFs and report direct comparisons. If not feasible, clearly state the limitations of the indirect comparison.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods
- **Evidence pointer** Materials and Methods, Model Training
- **Concern** The description of the training strategy is somewhat brief. The authors mention "peak-centric, pan-cell training" but do not provide a detailed algorithmic description or pseudocode.
- **Required correction** Provide a more detailed description of the training algorithm, including how positive and negative examples are sampled, how the pan-cell strategy is implemented, and how class imbalance is handled.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Model interpretation
- **Evidence pointer** Materials and Methods, Model Interpretation
- **Concern** The model interpretation analysis is limited to two TFs (GATA3 and CREM). While this is a reasonable starting point, a more systematic analysis across a broader set of TFs would strengthen the claims about interpretability.
- **Required correction** Consider extending the interpretation analysis to a larger set of TFs, or at least discuss the generalizability of the findings.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Concern** The discussion of limitations is relatively brief. The authors mention the modest AUPR values and the need for more training data, but do not discuss potential failure modes or biases in the training data.
- **Required correction** Expand the limitations section to discuss potential sources of bias in the training data (e.g., cell type representation, ChIP-seq antibody quality) and their potential impact on predictions.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code availability
- **Evidence pointer** Data Availability
- **Concern** The code repository is mentioned but not described in detail. It is unclear whether the code is fully documented, tested, and ready for use by the community.
- **Required correction** Provide a brief description of the code repository structure, dependencies, and a link to documentation in the manuscript.

## Risk / unsupported claims
- The claim that maxATAC "will improve TFBS predictions and knowledge gain from ATAC-seq studies" is a forward-looking statement that is not directly testable from the presented data.
- The claim that the atopic dermatitis application "showcas[es] the potential for maxATAC to uncover molecular regulatory mechanisms in complex diseases" is not fully supported given the lack of experimental validation and limited sample size.
- The statement that maxATAC is "the largest collection of high-performance TFBS models available" is contingent on the definition of "high-performance" and the scope of comparison; this claim should be qualified.
- The claim that "maxATAC performance extends to primary cells" is based on a single cell type (CD4+ T cells) and may not generalize to other primary cell types.
- The assertion that the benchmark dataset is "ready-to-go" for community use is not fully verifiable without detailed documentation of data formats and processing steps.