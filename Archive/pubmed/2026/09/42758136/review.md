## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, tables, methods details, or supplementary materials were provided for evaluation
- **Shared manuscript claim summary** The authors propose scHPGT, a transformer-based method integrating unpaired single-cell RNA and ATAC data using regulatory-prior-guided attention and domain-adversarial training. They claim improved clustering agreement, label transfer, biological structure preservation, and modality alignment across four benchmarks, plus recovery of regulatory relationships and transcription factor programs.
- **Visible evidence base** Abstract text only; benchmark names (PBMC3k, mouse spleen, CITE-seq/ASAP-seq PBMC, PBMC10k) and qualitative performance statements; code repository URL
- **Missing materials affecting confidence** Full methods, all quantitative results, figures, tables, supplementary data, hyperparameter choices, baseline comparisons, statistical significance tests, and implementation details

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially useful methodological contribution to single-cell multimodal integration. The core idea of using regulatory priors to constrain cross-modal attention is conceptually sound and addresses a recognized limitation of purely distribution-matching approaches. However, the abstract provides only qualitative performance claims without any quantitative evidence, effect sizes, or statistical comparisons. The biological structure preservation claim is central but not substantiated with specific metrics. The regulatory recovery claims are intriguing but lack validation details. The manuscript cannot be evaluated for technical soundness from the supplied material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or applying single-cell multimodal integration methods would be the primary audience. Researchers studying gene regulation, chromatin accessibility, and cell-type identification would also find value if the regulatory recovery claims hold. Method developers in deep learning for genomics may be interested in the architectural innovation of prior-guided attention.
- **Major strengths** The problem addressed is timely and relevant. The proposed architecture combines modality-specific encoders, prior-guided cross-modal attention, and domain-adversarial training in a coherent framework. The inclusion of partial-overlap and condition-shift settings suggests awareness of realistic integration challenges. The claim of recovering regulatory relationships adds potential biological utility beyond mere alignment.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The prior-guided attention mechanism appears novel in the context of single-cell integration, though the abstract does not fully distinguish it from existing attention-based integration methods. Scientific importance: High, given the widespread need for robust RNA-ATAC integration. Interdisciplinary readership: Potentially broad, spanning genomics, machine learning, and regulatory biology. Technical soundness: Not assessable from the abstract alone; no quantitative results or methodological details are provided. Readability for nonspecialists: The abstract is reasonably clear but uses field-specific terminology without sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual contribution is promising, but the abstract lacks the quantitative and methodological detail required to assess whether the claims are supported. A supportive posture would require full manuscript review with results.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "scHPGT improves clustering agreement, label transfer and biological structure preservation while maintaining effective modality alignment"  
- **Evidence pointer** Results section, location not provided  
- **Concern** The abstract states performance improvements across four benchmarks but provides no quantitative metrics, no baseline comparisons, no effect sizes, and no statistical significance assessments. Terms such as "improves" and "maintaining" are undefined without numbers.  
- **Why it matters** Without quantitative evidence, the central performance claims cannot be verified or compared against existing methods. The reader cannot determine whether improvements are marginal or substantial, or whether they hold across all benchmarks or only some.  
- **Resolution test** Provide tables or figures with specific metrics (e.g., adjusted Rand index, F1 score, label transfer accuracy) for scHPGT and all baselines on each benchmark, with confidence intervals or significance tests.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim support  
- **Claim pointer** "scHPGT aligns shared populations without forcing unmatched or condition-specific states into inappropriate correspondence"  
- **Evidence pointer** Results section, location not provided  
- **Concern** This is a strong claim about avoiding over-alignment, which is a key differentiator from distribution-matching approaches. However, the abstract provides no details on how over-alignment was measured, what specific states were tested, or how "inappropriate correspondence" was defined and evaluated.  
- **Why it matters** Over-alignment is a known failure mode in integration methods. If scHPGT genuinely avoids it, this would be a significant contribution. But without a defined evaluation protocol, the claim is unfalsifiable from the abstract.  
- **Resolution test** Describe the partial-overlap and condition-shift experimental designs, specify the metrics used to detect over-alignment (e.g., separation of known distinct states, preservation of condition-specific signatures), and show quantitative comparisons against baselines.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "Attention-derived links recover regulatory relationships, highlight marker-gene regulatory regions, recover transcription factor programs and produce regulatory activity profiles consistent with cell-type-specific transcriptional programs"  
- **Evidence pointer** Results section, location not provided  
- **Concern** These are biologically substantive claims with potentially high impact. The abstract offers no validation strategy, no ground-truth comparisons, no enrichment analyses, and no quantitative assessment of recovery accuracy.  
- **Why it matters** If the attention mechanism truly recovers known regulatory relationships, this would extend the method's utility beyond integration to hypothesis generation. However, attention weights are notoriously difficult to interpret, and without validation against known regulatory databases or experimental data, these claims remain speculative.  
- **Resolution test** Provide validation against curated regulatory databases (e.g., ENCODE, ChIP-seq data), show enrichment statistics for recovered links, compare recovered transcription factor programs against known regulons, and quantify concordance of regulatory activity profiles with established cell-type markers.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical reproducibility  
- **Claim pointer** "scHPGT uses modality-specific encoders, a prior-guided cross-modal Transformer to constrain gene-peak attention using regulatory links, and a domain-adversarial objective"  
- **Evidence pointer** Methods section, location not provided  
- **Concern** The abstract describes the architecture at a high level but omits critical technical details: how regulatory priors are constructed and incorporated, the exact attention mechanism, the adversarial training setup, loss function weights, hyperparameter choices, and training stability considerations.  
- **Why it matters** Reproducibility is a core requirement for computational methods. Without these details, other researchers cannot implement or fairly benchmark the method. The code repository is mentioned but its contents and documentation quality cannot be assessed from the abstract.  
- **Resolution test** Provide a complete methods section with architectural diagrams, mathematical formulations, training procedures, and hyperparameter tables. Confirm that the code repository includes documentation, example data, and trained model checkpoints.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, Motivation section  
- **Evidence pointer** Location not provided  
- **Issue** The term "regulatory-prior-guided" is used without defining what constitutes a regulatory prior or how it differs from other prior knowledge used in integration methods.  
- **Required correction** Briefly define regulatory priors in the abstract or refer to a specific data source (e.g., ENCODE, chromHMM) used to construct them.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract, Results section  
- **Evidence pointer** Location not provided  
- **Issue** The abstract lists four benchmarks but does not indicate their diversity or why they were chosen. PBMC datasets are all blood-derived, which may limit generalizability claims.  
- **Required correction** Briefly state the rationale for benchmark selection and acknowledge any potential limitations in dataset diversity.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Availability section  
- **Evidence pointer** Location not provided  
- **Issue** The code repository is mentioned but no version, license, or dependency information is provided in the abstract.  
- **Required correction** Specify the software version, license, and key dependencies in the availability statement or ensure these are clearly documented in the repository.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract, Results section  
- **Evidence pointer** Location not provided  
- **Issue** The phrase "regulatory activity profiles consistent with cell-type-specific transcriptional programs" is vague and could be interpreted in multiple ways.  
- **Required correction** Clarify what specific metric or analysis was used to establish this consistency (e.g., correlation with known marker gene expression, enrichment scores).

## Risk / unsupported claims
- The claim of improved clustering agreement, label transfer, and biological structure preservation is unsupported without quantitative results.
- The claim of avoiding over-alignment in partial-overlap and condition-shift settings is unsupported without defined evaluation protocols.
- The claim of recovering regulatory relationships, transcription factor programs, and regulatory activity profiles is unsupported without validation against ground-truth data.
- The generalizability of the method across diverse tissue types is not assessable from the four benchmarks listed, three of which are PBMC-derived.