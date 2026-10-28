## Review setup
- **Input scope** Abstract and author summary only
- **Assessment boundary** Claims and evidence presented in the supplied abstract and author summary
- **Shared manuscript claim summary** The authors present maxATAC, a suite of deep neural network models for genome-wide transcription-factor binding site (TFBS) prediction from ATAC-seq data. They claim to have curated a benchmark dataset covering 127 human TFs, that maxATAC is the first high-performance TFBS prediction model collection for ATAC-seq, that performance extends to primary cells and single-cell ATAC-seq, and that the method enables improved TFBS prediction in vivo. They demonstrate utility by identifying TFBS associated with allele-dependent chromatin accessibility at atopic dermatitis genetic risk loci.
- **Visible evidence base** Abstract text and author summary only. No figures, tables, methods, or quantitative results are provided.
- **Missing materials affecting confidence** Full manuscript, methods description, benchmark dataset details, model architecture specifications, performance metrics, comparison against existing methods, validation details for primary cells and single-cell ATAC-seq, and the atopic dermatitis case study results are all absent.

## Reviewer
- **Overall assessment** The authors address a timely and important problem in regulatory genomics. The shift from DNase-seq to ATAC-seq as the dominant chromatin accessibility assay is real, and the lack of accessible, high-performance TFBS prediction tools for ATAC-seq is a genuine gap. The proposed resource, if delivered as described, would be valuable to a broad community. However, the supplied material is an abstract-level summary with no quantitative evidence. The core claims of benchmark quality, model performance, generalizability to primary cells and single-cell data, and biological utility cannot be assessed from the provided text. The work is potentially significant, but the case is not established from the supplied evidence.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulation, chromatin accessibility, and TF binding prediction would be the primary audience. Experimental biologists using ATAC-seq, particularly those working with primary cells or single-cell ATAC-seq, would also benefit from a user-friendly tool that infers TFBS without requiring additional experimental profiling. Researchers studying disease-associated genetic variants, especially in non-coding regions, would find the application to atopic dermatitis risk loci relevant.
- **Major strengths** The problem is well-motivated and timely. The proposed resource addresses a clear community need. The scope, covering 127 TFs, is ambitious and potentially transformative. The emphasis on user-friendly access and applicability to single-cell ATAC-seq is forward-looking and practical.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The concept of applying deep learning to ATAC-seq for TFBS prediction is not entirely new, but the scale (127 TFs) and the specific focus on ATAC-seq as the primary input, including single-cell data, may constitute a meaningful advance. Scientific importance: High, if the performance claims hold. The ability to predict TFBS from ATAC-seq at scale would have broad utility in regulatory genomics. Interdisciplinary readership: Potentially broad, spanning computational and experimental biology. Technical soundness: Cannot be assessed from the supplied material. No architecture details, training procedures, or evaluation metrics are provided. Readability for nonspecialists: The abstract and author summary are clearly written and accessible, which is a positive sign.
- **Recommendation posture** Currently not established from the provided evidence. The authors should be encouraged to submit the full manuscript for review, as the described resource has clear potential value.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Performance claims
- **Claim pointer** "maxATAC is the first collection of high-performance TFBS prediction models for ATAC-seq" and "maxATAC performance extends to primary cells and single-cell ATAC-seq, enabling improved TFBS prediction in vivo"
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract claims high performance and superiority over existing methods, but no quantitative metrics, comparisons, or benchmarks are provided. The phrase "high-performance" is undefined. No AUPRC, AUROC, or other relevant metrics are given. No comparison against existing tools such as ChIP-nexus, HINT-ATAC, or motif-scanning baselines is shown.
- **Why it matters** The central value proposition of the resource is its performance. Without quantitative evidence, the claim of being "high-performance" and "first" cannot be verified. The community cannot judge whether maxATAC is an improvement over existing approaches or merely a convenience wrapper.
- **Resolution test** Provide performance metrics on held-out test sets for all 127 TFs, with clear baselines including motif scanning and any existing ATAC-seq-based TFBS prediction methods. Include comparisons on standard benchmarks such as ENCODE ChIP-seq data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmark dataset quality
- **Claim pointer** "we curated an extensive benchmark dataset (127 TFs) for ATAC-seq model training"
- **Evidence pointer** Abstract, location not provided
- **Concern** The nature of the benchmark dataset is not described. It is unclear whether the 127 TFs have matched ChIP-seq data for training and evaluation, how the positive and negative sets were defined, how cell-type diversity was handled, and whether the dataset is publicly available. The curation process is a critical component of the resource, and its quality directly affects model reliability.
- **Why it matters** A poorly curated benchmark can lead to inflated performance estimates and models that do not generalize. The community needs to know the data sources, filtering criteria, and potential biases to trust the models.
- **Resolution test** Describe the benchmark construction in detail, including data sources, TF selection criteria, peak calling methods, negative set generation, and train/test splits. Provide access to the dataset and demonstrate its quality through basic statistics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability claims
- **Claim pointer** "maxATAC performance extends to primary cells and single-cell ATAC-seq, enabling improved TFBS prediction in vivo"
- **Evidence pointer** Abstract, location not provided
- **Concern** The claim of generalizability to primary cells and single-cell ATAC-seq is made without any supporting data. Single-cell ATAC-seq data are sparse and noisy compared to bulk data, and it is not obvious that models trained on bulk ATAC-seq will transfer. No validation strategy, evaluation metrics, or example applications are described.
- **Why it matters** The stated advantage of ATAC-seq is its applicability to single-cell and primary cell contexts. If the models do not perform well in these settings, the practical utility of the resource is substantially diminished.
- **Resolution test** Provide validation results on at least one primary cell type and one single-cell ATAC-seq dataset, with appropriate metrics and comparison to baselines. Describe how the models were adapted or fine-tuned for these data types.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological application
- **Claim pointer** "We demonstrate maxATAC's capabilities by identifying TFBS associated with allele-dependent chromatin accessibility at atopic dermatitis genetic risk loci"
- **Evidence pointer** Abstract, location not provided
- **Concern** The atopic dermatitis application is presented as a demonstration of utility, but no results are shown. It is unclear whether the identified TFBS are novel, whether they are validated experimentally or through orthogonal data, and how allele-dependent accessibility was measured. The biological significance of the findings cannot be assessed.
- **Why it matters** A compelling biological application would strengthen the case for the resource's utility. Without results, the demonstration is only a promise.
- **Resolution test** Present the atopic dermatitis results, including the number of risk loci analyzed, the TFBS identified, the evidence for allele-dependent effects, and any validation or functional interpretation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** "maxATAC"
- **Evidence pointer** Abstract, location not provided
- **Issue** The name "maxATAC" is introduced without explanation. It is unclear whether "max" refers to a specific architectural component, a maximization objective, or is simply a branding choice.
- **Required correction** Briefly explain the rationale for the name, or remove the "max" prefix if it has no technical meaning.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model availability
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that maxATAC is a "suite of user-friendly" models, but no information is provided on software availability, code repository, or model download locations.
- **Required correction** State where the code and models will be made available, and under what license.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope of TF coverage
- **Affected element** "127 human TFs"
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not specify how the 127 TFs were selected. It is unclear whether they represent all TFs with available ChIP-seq data, a curated subset, or a biased sample.
- **Required correction** Describe the TF selection criteria, including any filtering based on data availability, motif quality, or expression patterns.

## Risk / unsupported claims
- The claim that maxATAC is "the first collection of high-performance TFBS prediction models for ATAC-seq" is unsupported, as no comparison to prior work is provided.
- The claim that performance "extends to primary cells and single-cell ATAC-seq" is unsupported, as no validation data are shown.
- The claim of "improved TFBS prediction in vivo" is unsupported, as no in vivo validation is described.
- The atopic dermatitis application is described but no results are presented, making the demonstration unverifiable.
- The benchmark dataset of 127 TFs is mentioned but its construction, quality, and accessibility are not described, making the resource's foundation unassessable.