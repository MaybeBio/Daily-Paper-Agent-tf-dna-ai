## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific soundness, methodological clarity, validity of claims relative to provided evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors propose GP-DHT, a dual-head transformer with supervised contrastive learning for shared-gene pretraining and single-cell GRN prediction. They claim improved predictive performance over baselines on BEELINE datasets, enhanced representation separability via contrastive learning, robustness to negative-label uncertainty, and interpretability via post-hoc attribution analysis.
- **Visible evidence base** Text descriptions of methods and results, including reported AUROC/AUPRC values, embedding quality metrics, and qualitative descriptions of figures and tables
- **Missing materials affecting confidence** All figures, tables, supplementary tables, implementation code, hyperparameter details, baseline configuration specifics, and statistical significance tests

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in single-cell GRN inference and proposes a technically plausible architecture combining heterogeneous graph learning, transformer encoding, and supervised contrastive learning. However, the provided text alone is insufficient to verify the central claims. Key methodological details are missing or ambiguous, baseline comparisons are described only qualitatively, and no statistical significance testing is reported. The manuscript would benefit from substantial revision and additional evidence before its claims can be considered established.
- **Who would be interested in the results, and why** Computational biologists and machine learning researchers working on gene regulatory network inference, single-cell transcriptomics analysis, and representation learning for biological data. The shared-gene pretraining aspect may also interest researchers focused on cross-species modeling, though the authors explicitly limit claims in this direction.
- **Major strengths** The problem is well motivated and relevant. The architecture design is thoughtful, particularly the separation of classification and contrastive objectives. The authors address important practical issues such as negative-label construction and representation quality assessment. The discussion of limitations is candid and appropriately scoped.
- **Major Concerns** 
  - R1-M1: Core performance claims are not verifiable from the provided text
  - R1-M2: Baseline comparisons are inadequately described
  - R1-M3: Statistical significance of reported improvements is not established
  - R1-M4: Methodological details for the contrastive learning component are incomplete
  - R1-M5: The post-hoc attribution analysis lacks sufficient validation
- **Minor Comments** 
  - R1-m1: Notation inconsistencies in the methods section
  - R1-m2: Figure descriptions are insufficiently detailed
  - R1-m3: The relationship between shared-gene pretraining and downstream performance is unclear
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The combination of heterogeneous graph encoding with dual-head transformer and supervised contrastive learning is novel in its specific configuration, though each component is established individually.
  - Scientific importance: Moderate. GRN inference is an active and important field, and improvements in robustness and representation quality are valuable. However, the claimed gains are incremental rather than transformative.
  - Interdisciplinary readership: Limited. The manuscript is written primarily for a specialized computational biology audience. The broader significance for cell biology or medicine is not clearly articulated.
  - Technical soundness: Not fully assessable from the provided text. Key implementation details and validation procedures are missing.
  - Readability for nonspecialists: Adequate for the target audience, though the methods section contains several undefined terms and incomplete equations.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential but requires major revision, additional experiments, and clearer reporting before the claims can be evaluated.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that GP-DHT "consistently outperforms representative GRN inference methods" with "improvements of approximately 5%–7% in both AUROC and AUPRC across most datasets."
- **Evidence pointer** Section 3, Figure 3, Table 1 (location not provided)
- **Concern** The performance comparison is described only in text. No actual numerical results, error bars, or per-dataset breakdowns are visible in the provided material. The claim of consistent improvement cannot be verified without the actual data.
- **Why it matters** The central contribution of the manuscript is the claimed predictive improvement. Without verifiable results, the scientific contribution cannot be assessed.
- **Resolution test** Provide full numerical results for all datasets and baselines, including per-fold standard deviations and effect sizes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The manuscript states that GP-DHT is compared with "several baseline methods: HGATLink, GMFGRN, IGEGRN, GNN-Link, and GATCL."
- **Evidence pointer** Section 3, Figure 3 (location not provided)
- **Concern** No details are provided on how baselines were configured, whether hyperparameters were tuned per dataset, how many runs were averaged, or whether the same train/test splits were used. Without this information, the comparison may be unfair or uninterpretable.
- **Why it matters** Baseline comparisons are only meaningful if all methods are evaluated under identical conditions with appropriate hyperparameter tuning.
- **Resolution test** Describe baseline configurations, tuning procedures, and evaluation protocols in full detail.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports performance differences between GP-DHT and baselines, and between different negative-label settings.
- **Evidence pointer** Section 3.1, Section 3.3, Table 2 (location not provided)
- **Concern** No statistical significance tests are reported for any comparison. The differences in AUROC, AUPRC, and embedding quality metrics are presented as meaningful without confidence intervals or p-values.
- **Why it matters** Without statistical testing, observed differences may be due to random variation, particularly given the small number of datasets and potential fold-to-fold variability.
- **Resolution test** Report confidence intervals and appropriate statistical tests for all key comparisons.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The contrastive learning component (GenePairSupCon) is described as a key contribution that "improves representation separability" and "stabilizes the ranking of weak edges."
- **Evidence pointer** Section 2.3.3, Section 2.3.4, Table 2 (location not provided)
- **Concern** The contrastive loss formulation is incomplete. The temperature parameter tau is mentioned but its value is not specified. The weighting factor lambda is introduced but its value or tuning procedure is not described. The augmentation procedure (Gaussian noise injection) lacks a specified noise level. The projection head architecture is not described.
- **Why it matters** Reproducibility requires complete specification of all hyperparameters and architectural details.
- **Resolution test** Provide complete specifications for all hyperparameters, architectures, and augmentation procedures.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive validity
- **Claim pointer** The post-hoc attribution analysis is described as providing "decision-level support for prioritized TF-target pairs" and the results are presented in Figures 7, 8, and Table 4.
- **Evidence pointer** Section 3.6, Figures 7-8, Table 4 (location not provided)
- **Concern** The attribution analysis is described as auxiliary, but its validation is limited to stability diagnostics and score-ranked retention/removal analyses. It is unclear whether the attribution scores provide information beyond the original prediction scores, and no comparison with alternative attribution methods is provided.
- **Why it matters** Without validation against alternative explanation methods or ground truth, the added value of the attribution analysis is unclear.
- **Resolution test** Compare attribution scores with prediction scores directly, and validate against independent biological evidence or alternative attribution methods.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2.1
- **Evidence pointer** Equations for log transformation, clipping range, and discretization (location not provided)
- **Issue** The equations are referenced but not shown in the provided text. The notation for the discretization process is incomplete.
- **Required correction** Display all equations explicitly and define every symbol used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3, Figures 4-6
- **Evidence pointer** Figure descriptions (location not provided)
- **Issue** The figure descriptions are too brief to understand what is being shown. For example, "PR curves" and "Top-K regulatory network graphs" are mentioned without specifying which datasets, which methods, or what the axes represent.
- **Required correction** Expand figure captions to include full methodological details and clear axis labels.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretive clarity
- **Affected element** Section 2.1, Section 4
- **Evidence pointer** Shared-gene pretraining description (location not provided)
- **Issue** The manuscript states that shared-gene pretraining is used "only for representation initialization" and that "strict species-to-species GRN transfer is not claimed." However, the value of the shared-gene component is not quantified. It is unclear whether pretraining on both species improves within-species performance compared with training on each species separately.
- **Required correction** Add an ablation comparing shared-gene pretraining with single-species pretraining or no pretraining.

## Risk / unsupported claims
- The claim of "consistent outperformance" over baselines is unsupported without numerical results and statistical testing.
- The claim that GenePairSupCon "substantially improved representation geometry" is based on metrics reported in Table 2, which is not visible in the provided material.
- The claim that the model "can also recover prior-supported candidate regulatory modules" is presented without specific examples or quantitative enrichment analysis.
- The robustness claims in Section 3.7 are described only qualitatively, with no numerical results provided.
- The statement that "the full GP-DHT model maintains the most favorable performance trajectory" under stress conditions is unverifiable without the actual data from Figures 9-13.