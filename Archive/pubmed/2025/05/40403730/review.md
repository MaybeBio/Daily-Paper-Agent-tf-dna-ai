## Review setup
- **Input scope** Full manuscript text including summary, introduction, results, discussion, resource availability, acknowledgments, STAR methods, and supplemental figure/table legends.
- **Assessment boundary** Scientific content, methodology, data analysis, interpretation, and claims as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors organized a community challenge (BICCN Challenge) to evaluate computational methods for predicting cell-type-specific enhancers in the mammalian cortex. Six teams submitted 79 predictions using 16 unique methods, benchmarked against 677 experimentally validated enhancers in 19 cortical cell types. Open chromatin accessibility was the strongest predictor of functional enhancers, while sequence models improved identification of non-functional enhancers and revealed cell-type-specific transcription factor codes.
- **Visible evidence base** In vivo enhancer validation data from a companion study (Ben-Simon et al.), single-cell multi-omics data from Zemke et al., benchmark metrics, recovery curves, statistical analyses, and method descriptions for all participating teams.
- **Missing materials affecting confidence** Full supplemental figures and tables (Figures S1–S25, Tables S1–S2) were not provided. Detailed code implementations and hyperparameters for team methods are only partially described. The companion paper (Ben-Simon et al.) is referenced but not available for cross-verification.

## Reviewer

### Overall assessment
This manuscript presents a valuable community resource and benchmark for cell-type-specific enhancer prediction. The organization of a multi-team challenge with standardized evaluation against a large in vivo validation dataset is commendable and addresses an important need in the field. The finding that open chromatin accessibility, particularly cell-type-specific ATAC-seq signal, remains the strongest predictor is informative and practically useful. The demonstration that sequence models can complement accessibility data, especially for identifying non-functional enhancers and revealing TF codes, adds conceptual depth. However, several technical aspects require clarification and strengthening before the conclusions are fully established.

### Who would be interested in the results, and why
Researchers developing genetic tools for cell-type-specific targeting in the brain, particularly those working with AAV vectors for neuroscience applications. Computational biologists developing enhancer prediction methods will find the benchmark and public resources valuable. The findings on feature importance and the comparative analysis of methods will inform future method development. The community challenge framework may also interest organizers of similar benchmarking efforts in genomics.

### Major Strengths
1. The challenge design is rigorous, with a large validation dataset (677 enhancers) and standardized scoring across multiple metrics.
2. The inclusion of diverse method categories (accessibility-based, sequence-based, integration-based) provides a comprehensive comparison.
3. The public availability of benchmark tools and data is a significant contribution to the field.
4. The post-hoc analyses, including manual annotation of enhancers and feature importance evaluation, add depth beyond simple ranking comparisons.
5. The identification of complementary information between ATAC-seq and sequence models is a nuanced and useful finding.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of benchmark metric
- **Claim pointer** The composite benchmark metric is described as capturing "different properties of enhancer activity" and is used to rank all methods.
- **Evidence pointer** STAR Methods, "Benchmark metrics of enhancer prioritization methods" section
- **Concern** The benchmark metric combines epifluorescence and SSv4 scores via an unweighted summation, but the two components have very different scales and properties. The epifluorescence metric uses arbitrary weights (2, 1.5, 1) for strength categories, and the SSv4 metric uses a continuous fraction. The manuscript does not demonstrate that this combination is optimal or even appropriate. The sensitivity of final rankings to the choice of weights and combination method is not assessed.
- **Why it matters** If the metric is sensitive to arbitrary weighting choices, the reported method rankings may not be robust, undermining the central conclusions about which methods perform best.
- **Resolution test** Provide a sensitivity analysis varying the weights and combination method (e.g., using only epifluorescence, only SSv4, or different weightings) and show that the main conclusions are unchanged. Alternatively, justify the specific weights with empirical evidence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of method comparisons
- **Claim pointer** "The final challenge ranks were statistically robust (p < 0.05) for 55 of 79 submissions based on a bootstrapping analysis."
- **Evidence pointer** Results, "A community challenge to predict functional enhancers" section; Figure S2
- **Concern** The bootstrap analysis is described only briefly. It is unclear what null distribution is being tested, whether multiple testing corrections were applied across 79 submissions, and what the practical implication is for 24 submissions that did not reach significance. The statement "statistically robust" is ambiguous without details on the test procedure.
- **Why it matters** Readers need to understand whether the rankings are meaningfully different from random or from each other. If 30% of submissions cannot be distinguished from chance, the interpretation of the leaderboard changes substantially.
- **Resolution test** Provide a complete description of the bootstrap procedure, including the null hypothesis, resampling scheme, and multiple testing correction. Report confidence intervals for each method's score and clarify the interpretation for non-significant submissions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of conclusions
- **Claim pointer** "Open chromatin was the strongest predictor of functional enhancers" and related statements about method performance.
- **Evidence pointer** Results sections throughout; Figures 1F, 2C–2E
- **Concern** The challenge is limited to mouse cortical cell types, with validation in V1 using a specific AAV delivery method (PHP.eB, retro-orbital). The authors acknowledge this in the limitations, but the abstract and discussion make broad claims about enhancer prediction without sufficiently emphasizing these constraints. The performance of methods may differ substantially for other brain regions, species, or delivery methods.
- **Why it matters** Overgeneralization could mislead researchers applying these methods to other contexts, potentially wasting resources on ineffective approaches.
- **Resolution test** Soften the language in the abstract and discussion to explicitly scope the conclusions to the tested conditions. Add a clear statement about what evidence would be needed to extend the conclusions to other contexts.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of method descriptions
- **Claim pointer** The manuscript claims to evaluate 16 unique methods from 6 teams, with detailed descriptions in STAR Methods.
- **Evidence pointer** STAR Methods, team-specific sections
- **Concern** The descriptions of team methods vary considerably in detail. The Stein team section is extensive, but the descriptions for other teams (e.g., Jesse Gillis, Kai Zhang, Yoshiaki Tanaka) are more concise. For a benchmarking paper, reproducibility of all methods is essential. It is unclear whether sufficient detail is provided for others to reimplement each method.
- **Why it matters** A key contribution of this work is the benchmark itself. If methods are not fully described, the benchmark cannot be used to evaluate future improvements or reimplementations.
- **Resolution test** Provide pseudocode or detailed algorithmic descriptions for all methods, or clearly indicate where full implementations can be accessed. Consider including a supplementary table summarizing key features of each method.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of sequence model performance
- **Claim pointer** "Sequence models improved prediction of non-functional enhancers and identified cell-type-specific transcription factor codes."
- **Evidence pointer** Results, "Meta-analysis of performance across teams and cell types" section; Figures 2E, 4F–4G
- **Concern** The claim that sequence models identify TF codes is based on motif analysis of CREsted predictions. However, the validation of these TF codes is limited. The manuscript shows examples (e.g., SOX10 in oligodendrocytes) but does not systematically validate whether the identified motifs are functionally relevant or simply correlative. The claim that sequence models "improved prediction of non-functional enhancers" needs clarification on what metric demonstrates this improvement.
- **Why it matters** The TF code finding is presented as a conceptual advance, but without systematic validation, it remains speculative. Overstating this finding could mislead researchers into overinterpreting motif predictions.
- **Resolution test** Provide a systematic analysis of motif enrichment significance across all cell types, with appropriate multiple testing corrections. For at least a subset of predicted TF codes, validate experimentally or through independent datasets.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** "Enhancer" terminology throughout
- **Evidence pointer** Throughout manuscript
- **Issue** The manuscript uses "enhancer" to refer to validated regulatory elements, but the validation is based on AAV-driven expression, which may not distinguish between enhancers, promoters, or other regulatory elements. The term "candidate enhancer" is used for predictions, but the distinction between validated and predicted elements could be clearer.
- **Required correction** Consider using "regulatory element" or "putative enhancer" where appropriate, and clarify the operational definition of "enhancer" used in this study.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 3A statistical annotations
- **Evidence pointer** Figure 3A
- **Issue** The figure legend states "∗∗p < 0.001, ∗∗∗p < 0.0001" but does not specify what test was used or how multiple comparisons were handled across the many features compared.
- **Required correction** Specify the statistical test used, whether corrections for multiple testing were applied, and report effect sizes in addition to p-values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and code availability section
- **Evidence pointer** Resource availability section
- **Issue** The statement that "all original code has been deposited at GitHub" is vague. It is unclear which repositories correspond to which methods, and whether the benchmark evaluation code is included.
- **Required correction** Provide a table listing all code repositories, their contents, and DOIs. Clarify which code is for the benchmark itself versus team submissions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of rescoring
- **Affected element** "Rescored enhancers validate model predictions" section
- **Evidence pointer** Results, "Rescored enhancers validate model predictions" section
- **Issue** The rescoring process is described as validating model predictions, but the rescoring was performed by the same group that developed the models. This creates a potential circularity concern that is not addressed.
- **Required correction** Acknowledge this limitation explicitly and discuss whether independent validation would be needed to fully confirm the rescoring results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity of method comparison
- **Affected element** Figure 1F and Table S2
- **Evidence pointer** Figure 1F
- **Issue** The normalized benchmark scores are presented, but it is unclear what the absolute scale means. A score of 0.4 versus 0.2 is not interpretable without context on the range of possible scores.
- **Required correction** Provide a description of the score distribution, including the range and what a random ranking would achieve.

### Technical failings that need to be addressed before the case is established
1. The benchmark metric's sensitivity to arbitrary weighting choices is not assessed (R1-M1).
2. The statistical framework for comparing methods is incompletely described (R1-M2).
3. The generalizability of conclusions beyond the tested conditions is overstated (R1-M3).

### Assessment against Nature-style criteria
**Originality:** The community challenge format for enhancer prediction is novel in this context, and the large standardized validation dataset is a unique contribution. The comparative analysis across diverse method types provides new insights into what features drive successful enhancer prediction.

**Scientific importance:** The work addresses a practical bottleneck in neuroscience tool development. The finding that open chromatin is the dominant predictor, while sequence models add complementary value, has direct implications for how researchers allocate resources in enhancer discovery efforts. The public benchmark will be a lasting resource.

**Interdisciplinary readership:** The work bridges computational genomics, neuroscience, and molecular tool development. The writing is generally accessible, though some sections assume familiarity with specific computational methods. The practical implications for AAV tool development will interest a broad neuroscience audience.

**Technical soundness:** The challenge design is generally sound, but the benchmark metric construction and statistical comparisons need more rigorous treatment. The post-hoc analyses are thoughtful but some claims (particularly regarding TF codes) require more systematic validation.

**Readability for nonspecialists:** The main text is well-organized and the figures are informative. However, the methods sections are dense and would benefit from additional context for readers not specialized in computational genomics. The summary and discussion are accessible.

### Recommendation posture
Supportive if technical concerns are resolved. The core contribution, a community benchmark for enhancer prediction with a large validation dataset, is valuable and appropriate for publication. However, the benchmark metric needs sensitivity analysis, the statistical framework needs clarification, and the generalizability claims need to be tempered. These are addressable with additional analyses and revisions rather than requiring new experiments.

## Risk / unsupported claims
1. The claim that sequence models "identified cell-type-specific transcription factor codes" is not fully supported without systematic validation of motif predictions across all cell types.
2. The statement that "the final challenge ranks were statistically robust" is not fully supported given the incomplete description of the bootstrap analysis and the 24 submissions that did not reach significance.
3. The claim that combining ATAC-seq and sequence model predictions provides the "best predictive factor" (AP = 0.54) is based on a single combination method and may not generalize.
4. The assertion that "open chromatin was the strongest predictor" is based on the specific benchmark metric used; different metrics might yield different conclusions.
5. The generalizability of findings to other brain regions, species, or delivery methods is not established and should not be implied.