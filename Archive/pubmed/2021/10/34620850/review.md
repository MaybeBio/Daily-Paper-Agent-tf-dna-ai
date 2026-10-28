## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and conclusions as presented in the provided text. No external data or supplementary figures were available for review.
- **Shared manuscript claim summary** The authors propose that PRC1 Polycomb complexes form multicomponent condensates through hetero-oligomerization, which can read H3K27me3 marks and write H2AK119Ub marks. They argue that while induced PRC1 condensation can promote chromatin compaction, sustained condensates are not required to maintain the compacted state. Instead, repressive histone marks written during condensation sustain compaction, linking phase separation thermodynamics to epigenetic memory.
- **Visible evidence base** Main text figures 1-5, methods section, and figure legends. Supplementary figures referenced but not provided.
- **Missing materials affecting confidence** Supplementary figures (S1-S4), supplementary tables (S1-S2), raw data files, and the Reporting Summary were not available. This limits full assessment of reproducibility and some quantitative claims.

## Reviewer
- **Overall assessment** This manuscript addresses an important question in chromatin biology: the relationship between phase-separated Polycomb condensates, histone mark deposition, and chromatin compaction. The authors use an optogenetic approach to induce PRC1 condensation and observe downstream effects on histone modifications and chromatin structure. The central claim, that condensates promote but are not required for sustained compaction, is conceptually interesting and potentially impactful. However, the evidence presented has several gaps. The distinction between "promoting" marks and "not required for" compaction relies heavily on correlative imaging data and a simplified simulation model. The mechanistic link between H2AK119Ub deposition and sustained compaction is inferred rather than directly demonstrated. The manuscript would benefit from additional experiments to strengthen causality, such as blocking ubiquitination or using mutants that separate condensation from enzymatic activity. The simulation model, while useful, makes assumptions that may not fully capture in vivo complexity. Overall, the work is promising but the current evidence does not fully establish the mechanistic model proposed.
- **Who would be interested in the results, and why** Researchers studying chromatin organization, epigenetic regulation, phase separation in biology, and Polycomb group proteins. The work bridges biophysical principles of phase separation with epigenetic mechanisms, which will interest both biophysicists and molecular biologists. The optogenetic approach for studying PRC1 function may also be of interest to tool developers.
- **Major strengths** The use of an inducible optogenetic system to control PRC1 condensation with temporal precision is a powerful approach. The combination of live-cell imaging with molecular dynamics simulations provides complementary perspectives. The finding that compaction persists after condensate dissolution is a notable observation that challenges simple physical models of condensate-driven compaction. The read-write mechanism linking PRC1 condensation to histone marks is a conceptually appealing framework.
- **Major Concerns** 
  - R1-M1: The causal link between H2AK119Ub marks and sustained compaction is not directly demonstrated. The authors infer this from the observation that compaction persists after condensate dissolution, but they do not show that blocking ubiquitination prevents sustained compaction.
  - R1-M2: The molecular dynamics simulation model makes several assumptions (e.g., ubiquitinated beads stick to each other) that are not directly validated by experimental data. The model's predictive power for the in vivo situation is unclear.
  - R1-M3: The claim that condensates are "not required" for sustained compaction is based on observations over a relatively short time window (20-30 min after deactivation). It is unclear whether compaction would persist over longer timescales relevant to epigenetic inheritance.
  - R1-M4: The quantitative analysis of chromatin compaction relies on variance measurements of H2B signal, which is an indirect readout. No direct measurement of chromatin compaction (e.g., Hi-C, super-resolution microscopy) is provided.
  - R1-M5: The authors state that CBX2_F12A mutant condensates cannot compact chromatin, but the mechanism by which H3K27me3 recognition is required for compaction is not explored in depth.
- **Minor Comments** 
  - R1-m1: The authors should clarify whether the "OFF" state in their experiments truly represents no condensation, given that endogenous PRC1 complexes are still present.
  - R1-m2: The statistical analysis for the PCC measurements in Figure 2 should be described more clearly, including how many cells were analyzed per condition.
  - R1-m3: The western blot data in Figure S3C is mentioned but not shown in the main text; the authors should consider including this data in the main figures.
  - R1-m4: The authors should discuss potential off-target effects of the optogenetic system, particularly whether light activation alone (without PRC1 fusion) has any effect on chromatin.
  - R1-m5: The manuscript would benefit from a more detailed description of the simulation parameters and how they were chosen to match experimental conditions.
- **Technical failings that need to be addressed before the case is established** 
  - R1-M1 (causal link between ubiquitination and compaction)
  - R1-M2 (simulation model validation)
  - R1-M4 (indirect compaction measurement)
- **Assessment against Nature-style criteria** 
  - Originality: High. The concept that condensates act as "reaction chambers" that write marks which then sustain compaction is a novel contribution to the phase separation field.
  - Scientific importance: High. The work addresses a fundamental question about how transient condensates can have lasting epigenetic effects, which is relevant to development and disease.
  - Interdisciplinary readership: Moderate. The work bridges biophysics and chromatin biology, but the technical nature of the optogenetic and imaging approaches may limit accessibility to a broad audience.
  - Technical soundness: Moderate. The experimental approaches are generally sound, but the causal claims are not fully supported by the data presented. The simulation model requires more validation.
  - Readability for nonspecialists: Moderate. The manuscript is generally well-written, but some sections (particularly the simulation methods) may be challenging for readers without a biophysics background.

## Risk / unsupported claims
- The claim that "Polycomb condensates can promote epigenetic marks" is supported by the data showing H2AK119Ub accumulation in condensates, but the quantitative significance of this increase is not fully established.
- The claim that condensates are "not required for sustained chromatin compaction" is only supported for the time window tested (20-30 min). Longer-term stability is not demonstrated.
- The statement that "the time integral of Polycomb phase-separation is progressively recorded in repressive histone marks" is a conceptual model that is not directly tested.
- The claim that the simulation model is "consistent with" the experimental data is weak; consistency does not establish the model's validity.
- The assertion that "phase separation... can facilitate non-equilibrium reactions such as epigenetic writing" is an interpretation that requires more direct evidence linking condensation to enzymatic activity.