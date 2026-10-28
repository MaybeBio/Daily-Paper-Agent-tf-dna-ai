## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce GerNA-Bind, a geometric deep learning framework for predicting RNA-ligand binding specificity. They claim state-of-the-art performance on multiple benchmarks, a 20.8% precision improvement over AlphaFold3 for binding site prediction, well-calibrated uncertainty quantification, and experimental validation of 18 compounds targeting MALAT1 RNA with submicromolar affinities, including one lead compound with functional effects.
- **Visible evidence base** Abstract text only; no quantitative benchmark tables, method descriptions, dataset specifications, or experimental protocols are available
- **Missing materials affecting confidence** Full manuscript, methods section, benchmark dataset definitions, baseline comparisons, AlphaFold3 evaluation protocol, virtual screening details, experimental validation procedures, statistical analyses, and code or data availability statements

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially impactful framework for RNA-ligand binding specificity prediction. The combination of geometric deep learning with multi-state RNA representations and experimental validation is timely and relevant. However, the abstract alone does not provide sufficient methodological detail or quantitative evidence to assess the validity of the central claims. The performance improvements over AlphaFold3 and the experimental results require careful scrutiny of the full manuscript. The work addresses an important problem in RNA-targeted drug discovery, but the current evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on RNA structure and ligand interactions would find the methodological advances relevant. Drug discovery researchers focused on RNA-targeted therapeutics, particularly those working on MALAT1 and other noncoding RNAs, would be interested in the experimental validation and virtual screening results. Researchers developing geometric deep learning methods for biomolecular applications would also find the framework of interest.
- **Major strengths** The problem addressed is significant and underexplored relative to protein-ligand interaction prediction. The integration of multi-state RNA representations is conceptually novel. The inclusion of experimental validation for virtual screening hits, including functional assays, strengthens the translational relevance. The explicit focus on low-homology RNA-ligand pairs addresses a known limitation in the field. The claim of well-calibrated uncertainty quantification is valuable for practical applications.
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
- **Assessment against Nature-style criteria** Originality appears high given the focus on RNA-ligand specificity with geometric deep learning and multi-state representations. Scientific importance is potentially substantial for RNA-targeted drug discovery. Interdisciplinary readership could include computational biologists, medicinal chemists, and RNA biologists. Technical soundness cannot be assessed from the abstract alone. Readability for nonspecialists is adequate in the abstract, though some terms such as "multi-state RNA-ligand representations" and "well-calibrated predictions" would benefit from brief clarification.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents promising results, but the absence of methodological details, benchmark specifications, and experimental protocols prevents verification of the central claims. A supportive posture would require review of the full manuscript.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "GerNA-Bind achieves state-of-the-art performance on multiple benchmark datasets"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract claims state-of-the-art performance without specifying which benchmarks were used, which baselines were compared, or what metrics were evaluated. The term "multiple benchmark datasets" is vague and does not allow assessment of whether the comparisons were fair, comprehensive, or statistically robust.  
- **Why it matters** State-of-the-art claims require transparent benchmark selection and rigorous comparison protocols. Without knowing the datasets, baselines, and evaluation metrics, the claim cannot be verified or reproduced.  
- **Resolution test** The full manuscript must provide benchmark dataset names, sizes, split protocols, baseline methods with versions and hyperparameters, and statistical significance tests for performance differences.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "It achieves a 20.8% improvement in precision for binding site prediction compared to AlphaFold3"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The comparison to AlphaFold3 raises several questions. AlphaFold3 is a general-purpose structure prediction model, not specifically designed for RNA-ligand binding site prediction. The evaluation protocol, dataset, and definition of "precision" are not specified. It is unclear whether AlphaFold3 was fine-tuned, what input representations were used, and whether the comparison was apples-to-apples.  
- **Why it matters** A specific quantitative claim of improvement over a widely known model requires a carefully controlled comparison. If the evaluation protocol is biased or the baseline is disadvantaged, the 20.8% figure is misleading.  
- **Resolution test** The manuscript must describe the AlphaFold3 evaluation setup in detail, including input preparation, output interpretation, dataset composition, and whether any adaptation was performed. The precision metric must be defined and the comparison must be shown to be fair.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality  
- **Claim pointer** "GerNA-Bind identified 18 structurally diverse compounds targeting the oncogenic MALAT1 RNA, with experimentally confirmed submicromolar affinities"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The experimental validation is described in a single sentence. No information is provided about the assay type, the range of affinities, the selectivity controls, or the criteria for "structurally diverse." The hit rate from the virtual screening is not reported, which is critical for assessing the practical utility of the method.  
- **Why it matters** Experimental validation is the strongest evidence for practical utility, but without assay details, affinity values, and hit rate information, the claim cannot be evaluated. The absence of negative controls or selectivity data raises questions about specificity.  
- **Resolution test** The full manuscript must provide assay protocols, dose-response curves or affinity values, selectivity data against other RNAs, and the total number of compounds screened to enable hit rate calculation.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality  
- **Claim pointer** "one lead compound selectively binds the MALAT1 triple-helix, reduces its transcript levels, and inhibits cancer cell migration"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The functional claims for the lead compound are stated without any experimental context. The binding selectivity assay, the transcript level measurement method, and the cell migration assay are not described. The magnitude of effects and statistical significance are not reported.  
- **Why it matters** Functional claims in a drug discovery context require rigorous experimental evidence. Without knowing the assay conditions, concentrations, controls, and effect sizes, the biological significance cannot be assessed.  
- **Resolution test** The manuscript must provide detailed experimental methods for binding assays, transcript quantification, and cell migration studies, including concentrations, replicates, controls, and statistical analyses.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** "multi-state RNA-ligand representations"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "multi-state" is not defined. It could refer to multiple conformational states of RNA, multiple binding poses, or multiple representation types.  
- **Required correction** Define what "multi-state" means in this context in the abstract or provide a brief clarification.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** "well-calibrated predictions with built-in uncertainty quantification"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The claim of well-calibrated predictions is not supported by any quantitative metric in the abstract. Calibration is typically assessed with reliability diagrams or expected calibration error.  
- **Required correction** Provide a calibration metric or reference to a figure in the full manuscript that demonstrates calibration quality.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** "low-homology RNA-ligand pairs"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The definition of "low-homology" is not provided. It is unclear what sequence or structure similarity threshold defines this category.  
- **Required correction** Define the homology threshold used to categorize low-homology pairs.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** "GerNA-Bind"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No mention of code or data availability. For a computational method, reproducibility is essential.  
- **Required correction** State in the abstract or manuscript whether code and data will be made publicly available.

## Risk / unsupported claims
- State-of-the-art performance on multiple benchmark datasets is unsupported without benchmark names, baselines, and metrics.
- The 20.8% precision improvement over AlphaFold3 is unsupported without the evaluation protocol and dataset details.
- The identification of 18 compounds with submicromolar affinities is unsupported without assay details and affinity values.
- The functional claims for the lead compound are unsupported without experimental methods and effect sizes.
- The claim of well-calibrated predictions is unsupported without calibration metrics.
- The claim of excelling in low-homology RNA-ligand pairs is unsupported without a definition of low-homology and comparative results.