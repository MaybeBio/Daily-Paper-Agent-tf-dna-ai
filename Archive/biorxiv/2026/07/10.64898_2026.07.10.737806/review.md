## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and appendices
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors propose FUSED, a multivariate functional representation of protein ligand binding sites that jointly models structural (CDPA-derived) and elemental (ILR-transformed) descriptors as functions of distance from the ligand. They claim this representation supports competitive performance in multiclass ligand discrimination (EK), binary binding-site classification (TOUGH-C1), and pairwise pocket matching (TOUGH-M1), while remaining alignment-free and computationally practical.
- **Visible evidence base** Full text with results tables (Tables 1–10), figures (Figures 1–10), appendices (A–C), and a public code repository link
- **Missing materials affecting confidence** Actual figure images and table data values are not visible in the provided text; exact numerical results for all experiments are not fully specified; details of baseline method implementations and hyperparameter tuning are partially described; no supplementary information was provided

## Reviewer

- **Overall assessment** The manuscript presents a conceptually interesting idea: representing ligand binding sites as functional objects over a distance continuum rather than at a single fixed threshold. The motivation is well-articulated and the problem is relevant. However, the current evidence base is insufficient to fully establish the claimed advantages. Several methodological details require clarification, and the comparative evaluations against existing methods are incomplete or potentially confounded. The TOUGH-M1 result, while promising, is presented without sufficient detail on baseline comparisons or statistical significance testing. The manuscript would benefit from a more rigorous evaluation framework and clearer reporting of experimental conditions.

- **Who would be interested in the results, and why** Researchers in structural bioinformatics, cheminformatics, and computational drug discovery would be interested. The functional representation concept could be useful for binding-site comparison, ligand selectivity prediction, and pocket matching. Practitioners working on protein–ligand interaction analysis and those developing machine-learning approaches for binding-site characterization would find the framework relevant. The alignment-free nature of the representation may appeal to those seeking computationally efficient alternatives to structural alignment methods.

- **Major strengths** The conceptual framing of binding sites as functional objects over a distance domain is novel and well-motivated. The combination of structural and compositional descriptors within a unified framework is sensible. The use of ILR transformation to respect compositional geometry is methodologically appropriate. The evaluation across three complementary benchmark tasks is commendable. The computational efficiency argument is well-supported by the runtime analysis. The authors are transparent about limitations and the need for further validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that FUSED achieves a mean ROC-AUC of 0.9375 on TOUGH-M1, "approaching the strongest reported benchmark performance"
- **Evidence pointer** Section 9.3, Table 10
- **Concern** The comparison with existing methods in Table 10 is presented without sufficient detail on whether the same evaluation protocol was used. The authors acknowledge that "exact evaluation implementations differ across studies," but this undermines the validity of direct performance comparisons. It is unclear whether the reported baseline values were obtained under the same sequence-cluster-disjoint splitting scheme, the same set of pockets, and the same evaluation metrics. Without a controlled re-implementation of baseline methods under identical conditions, the claim of "approaching the strongest reported benchmark performance" is not rigorously established.
- **Why it matters** The central claim of competitive performance on TOUGH-M1 is a key contribution of the paper. If the comparison is not apples-to-apples, the conclusion may be misleading. The scientific community relies on fair benchmark comparisons to assess method improvements.
- **Resolution test** The authors should either (a) re-implement and evaluate baseline methods under the exact same evaluation protocol (same splits, same pockets, same metrics), or (b) clearly qualify their results as not directly comparable and provide a more conservative interpretation. Ideally, they would also report statistical significance tests (e.g., confidence intervals or paired tests across the 20 splits) for the difference between FUSED and the closest baseline.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The claim that FUSED is a "flexible, alignment-free representation" that can be "used directly or combined with dimension-reduction, statistical-learning, and/or machine-learning procedures"
- **Evidence pointer** Sections 5, 8, 9; Appendices A–C
- **Concern** The manuscript does not provide sufficient detail on the sensitivity of results to key implementation choices. Specifically: (a) the smoothing parameter λ is fixed at 10⁻³ with sensitivity assessed only in Table A1, but the range tested and the criterion for "highly stable" are not quantified; (b) the number of MFPC components retained is determined by a 95% variance threshold, but the sensitivity to this choice is only partially explored; (c) the grid spacing of 0.1 Å is stated but not justified; (d) the choice of cubic B-splines with penalized least squares is not compared to alternative functional smoothing approaches. These choices could materially affect the representation and downstream performance.
- **Why it matters** For a methodological paper proposing a new representation, the robustness of the method to implementation choices is critical. If results are highly sensitive to these parameters, the method's practical utility is limited. Reproducibility also requires clear specification of all implementation details.
- **Resolution test** The authors should provide a more systematic sensitivity analysis for each key parameter, ideally with a table or figure showing performance across a range of values. They should also justify their default choices with reference to this analysis. If the method is robust, this should be demonstrated explicitly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that "informative threshold regions are not expected to be universal, but instead depend on the dataset, analytical objective, and procedure used to analyze the FUSED representation"
- **Evidence pointer** Section 7, Table 5, Figure 10
- **Concern** While the observation that different tasks and classifiers favor different distance intervals is interesting, the manuscript does not provide a principled framework for selecting the interval in practice. The nested cross-validation approach is described, but the criteria for selecting the "best" interval are not fully specified. Is it the interval that maximizes validation accuracy? If so, how is overfitting to the validation set avoided? The authors state that interval selection is "incorporated into the evaluation" but do not describe the selection rule in detail.
- **Why it matters** If the method requires task-specific interval selection, users need clear guidance on how to perform this selection in new applications. Without a well-defined selection procedure, the method's practical utility is diminished.
- **Resolution test** The authors should explicitly state the interval selection criterion used in the nested cross-validation (e.g., maximizing mean validation accuracy, or some other metric). They should also discuss potential overfitting issues and whether the selected intervals are stable across the 20 repeated splits.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that CDPA-derived descriptors and ILR-transformed compositions "jointly model" structural and elemental information
- **Evidence pointer** Sections 3, 4, 6
- **Concern** The manuscript does not clearly demonstrate that the joint representation provides benefits beyond what could be achieved by simply concatenating structural and compositional features at a single carefully chosen threshold. The comparison in Section 8.1 shows FUSED outperforms single-threshold CDPA, but the comparison is against CDPA alone, not against a combined single-threshold representation. It is unclear whether the improvement comes from the functional nature of the representation or simply from the addition of compositional information.
- **Why it matters** The novelty of FUSED lies in its functional treatment of the distance domain. If a single-threshold combined representation performs equally well, the functional aspect may not be necessary. The authors should isolate the contribution of the functional treatment.
- **Resolution test** The authors should include a comparison against a combined CDPA+ILR representation at a single optimized threshold (e.g., 5.3 Å or the best-performing fixed threshold). This would help disentangle the contribution of the functional treatment from the contribution of adding compositional information.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1, equations
- **Issue** The formal definition of the binding site and the distance calculation is incomplete. The equation for Euclidean distance is referenced but not fully written out, and the notation for the sets of coordinates is not fully defined.
- **Required correction** Provide the complete equation for the Euclidean distance and clearly define all notation used in the formalization.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 8, Tables 4–9
- **Evidence pointer** Section 8, Tables 4–9
- **Issue** The manuscript reports mean accuracies and standard deviations but does not report the number of repetitions used for the EK and TOUGH-C1 classification results. The text mentions "5 repeated 5-fold nested cross-validation" but the tables do not clearly indicate this.
- **Required correction** Clearly state in the table captions or in the text the number of repetitions and the total number of held-out evaluations for each reported result.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 9.2
- **Evidence pointer** Section 9.2
- **Issue** The description of the cluster-based splitting procedure is somewhat ambiguous. The authors state that "80% of the clusters were assigned to the training partition" but do not specify how clusters were sampled (e.g., random sampling, stratified by ligand class) or whether the same cluster assignments were used across all 20 repetitions.
- **Required correction** Clarify the cluster sampling procedure and whether the same cluster assignments were reused across repetitions or resampled each time.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 6.2, Appendix B
- **Evidence pointer** Section 6.2, Appendix B
- **Issue** The description of the scaling procedure for MFPCA is vague. The authors state that ILR channels are "rescaled by s_ILR" but do not provide the exact formula or the rationale for the specific scaling factor.
- **Required correction** Provide the exact scaling formula and explain why this particular scaling was chosen.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 10
- **Evidence pointer** Section 10
- **Issue** The runtime comparison with DeeplyTough is presented as a demonstration of computational advantage, but the hardware and software environments are not matched, and the specific operations timed are not fully described.
- **Required correction** Provide more detail on the computational environment and the specific operations being timed. Acknowledge the limitations of cross-hardware comparisons.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 11, Discussion
- **Evidence pointer** Section 11
- **Issue** The discussion of limitations is somewhat brief and does not address potential issues with the functional representation itself, such as the choice of basis functions, the smoothness assumptions, or the interpretability of the resulting functions.
- **Required correction** Expand the limitations section to address these methodological considerations.

- **Technical failings that need to be addressed before the case is established** R1-M1 (comparison validity), R1-M2 (sensitivity analysis), R1-M4 (isolating the contribution of the functional treatment)

- **Assessment against Nature-style criteria**
  - **Originality** The concept of treating binding-site descriptors as functional objects over a distance continuum is genuinely novel. The combination of CDPA and ILR within a functional framework has not been previously explored, to the best of my knowledge. This represents a creative contribution to the field.
  - **Scientific importance** The problem addressed is important: binding-site representation is central to many tasks in structural bioinformatics and drug discovery. However, the demonstrated advantages over existing methods are incremental rather than transformative. The TOUGH-M1 result is promising but not yet fully established as superior to state-of-the-art methods.
  - **Interdisciplinary readership** The work bridges structural biology, cheminformatics, and machine learning. The functional data analysis perspective may attract interest from statisticians. However, the presentation is somewhat technical and may be challenging for non-specialists in functional data analysis.
  - **Technical soundness** The methodological framework is sound in principle, but the evaluation has gaps as detailed in the major concerns. The sensitivity to implementation choices is not fully explored, and the comparative baselines are not rigorously controlled.
  - **Readability for nonspecialists** The manuscript is generally well-written and the motivation is clear. However, some sections (particularly the formal definitions and the MFPCA details) assume familiarity with advanced statistical concepts. The figures are referenced but not visible in the provided text, making it difficult to assess their clarity.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the framework is well-conceived. However, the current evidence does not fully establish the claimed advantages. The authors should address the comparison validity issue (R1-M1), provide a more systematic sensitivity analysis (R1-M2), and isolate the contribution of the functional treatment (R1-M4). With these revisions, the manuscript could make a solid contribution to the field.

## Risk / unsupported claims

- The claim of "approaching the strongest reported benchmark performance" on TOUGH-M1 is not fully supported due to potentially incomparable evaluation protocols across studies.
- The claim that FUSED provides a "flexible" representation is not fully established without a more systematic sensitivity analysis.
- The claim that the functional treatment provides benefits beyond a single-threshold combined representation is not directly tested.
- The runtime advantage over DeeplyTough is presented without matched hardware/software conditions and should be interpreted cautiously.
- The generalizability of the findings to other datasets and binding-site analysis tasks is asserted but not demonstrated.