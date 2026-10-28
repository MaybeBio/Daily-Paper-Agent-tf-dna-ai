## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract, evaluated against the evidence described therein
- **Shared manuscript claim summary** The authors propose that both the intrinsically disordered N-terminal region and the structured DNA-binding domain of the progesterone receptor jointly regulate the formation and function of transcriptional condensates, with domain-specific effects on gene expression and oncogenic phenotypes.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, detailed methods for single-particle tracking, deep-learning trajectory analysis, transcriptomic and functional assays, statistical details, and any control experiments

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting hypothesis that structured DNA-binding domains, in addition to intrinsically disordered regions, contribute to transcriptional condensate formation and function. The combination of single-particle tracking with deep-learning-based analysis and transcriptomic/functional validation is a reasonable approach. However, the abstract provides insufficient methodological detail and quantitative evidence to evaluate the robustness of the claims. The central conclusion that both domains are "required" for condensate formation is not supported by the evidence described, as no loss-of-function or rescue experiments are mentioned. The link between domain-specific transcription and differential proliferation/migration is stated but not substantiated with effect sizes or statistical measures. The work may be of interest to researchers in transcriptional regulation and condensate biology, but the current evidence base is too limited to establish the case.
- **Who would be interested in the results, and why** Researchers studying transcriptional condensates, intrinsically disordered proteins, nuclear receptor biology, and gene regulation would find these results relevant. The potential implication that structured DNA-binding domains contribute to condensate formation challenges the prevailing focus on IDRs and could inform therapeutic strategies targeting nuclear receptors in cancer. The methodological combination of SPT with deep learning may also interest biophysicists and computational biologists.
- **Major strengths** The study addresses a timely and important question about the role of structured domains in transcriptional condensates. The use of single-particle tracking with deep-learning-based trajectory analysis is a sophisticated approach for studying dynamic condensate behavior. The inclusion of transcriptomic and functional assays to link domain-specific effects to phenotypic outcomes strengthens the potential biological relevance.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not describe any experiments that directly test whether the DBD is required for condensate formation, such as deletion or point mutation constructs with imaging validation. The claim that "mutations of either of the two domains result in the expression of a distinct set of genes" lacks any indication of the magnitude, statistical significance, or biological coherence of these changes. The functional assays linking domain-specific transcription to proliferation and migration are mentioned without any quantitative results. The deep-learning-based trajectory analysis is not described in sufficient detail to assess its validity or potential biases.
- **Assessment against Nature-style criteria** 
  - Originality: The idea that structured domains contribute to condensate formation is not entirely novel but is underexplored, particularly for nuclear receptors. The specific focus on PR DBD adds some originality.
  - Scientific importance: If fully substantiated, the findings could shift the field's understanding of condensate drivers and have implications for nuclear receptor biology and cancer. However, the importance is not yet established from the abstract alone.
  - Interdisciplinary readership: The topic bridges biophysics, molecular biology, and cancer biology, which could attract a broad audience. The methodological component may appeal to computational biologists.
  - Technical soundness: Cannot be assessed from the abstract. The described methods are plausible but lack detail on controls, replicates, and statistical treatment.
  - Readability for nonspecialists: The abstract is generally clear but uses specialized terminology without sufficient context. The logical flow from imaging to transcriptomics to function is understandable but would benefit from more explicit connections.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and the approach is promising, but the abstract does not provide sufficient evidence to support the central claims. A full manuscript with detailed methods, quantitative results, and appropriate controls would be needed to evaluate the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence mismatch
- **Claim pointer** "we demonstrated that both the IDR and the DBD are required for the formation of PR condensates"
- **Evidence pointer** Abstract, methods description for SPT and deep-learning analysis; location not provided
- **Concern** The abstract states that both domains are "required" for condensate formation, but no experimental evidence is described that directly tests this requirement. The SPT and deep-learning analysis can characterize condensate behavior, but without loss-of-function experiments (e.g., domain deletions, point mutations) or rescue experiments, the claim of requirement is not supported.
- **Why it matters** The central conclusion of the paper hinges on this claim. If the DBD is merely modulatory rather than required, the interpretation changes substantially. The term "required" implies a necessity that must be demonstrated through perturbation experiments.
- **Resolution test** Provide imaging data from cells expressing PR constructs with DBD deletions or inactivating mutations, showing that condensate formation is abolished or severely impaired, and ideally rescue with wild-type DBD. Quantify condensate number, size, and dynamics with appropriate statistical comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "transcriptomic analysis showed that mutations of either of the two domains result in the expression of a distinct set of genes"
- **Evidence pointer** Abstract, transcriptomic analysis; location not provided
- **Concern** The abstract does not provide any quantitative details about the transcriptomic results, such as the number of differentially expressed genes, effect sizes, statistical thresholds, or overlap between the two mutation conditions. Without these details, it is impossible to assess whether the observed changes are biologically meaningful or merely noise.
- **Why it matters** The claim of domain-specific transcriptional regulation is a key part of the paper's contribution. If the transcriptomic changes are small or not robustly reproducible, the link between condensate formation and gene expression is weakened.
- **Resolution test** Report the number of differentially expressed genes for each mutation, with adjusted p-values and fold-change thresholds. Show whether the gene sets are distinct or overlapping, and provide validation of a subset of changes by independent methods (e.g., qPCR).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "functional assays corroborating these findings and linking domain-specific transcription to differential effects on cell proliferation and migration"
- **Evidence pointer** Abstract, functional assays; location not provided
- **Concern** The abstract mentions functional assays but provides no data on the direction, magnitude, or statistical significance of the effects on proliferation and migration. It is unclear whether the effects are specific to one domain or shared, and whether they are causally linked to the transcriptomic changes.
- **Why it matters** The claim that domain-specific transcription leads to differential oncogenic phenotypes is a strong conclusion that requires direct evidence. Without quantitative results, the link between transcription and phenotype remains correlational.
- **Resolution test** Provide quantitative data on proliferation and migration rates for each mutant compared to wild-type, with appropriate statistical tests. Ideally, show that the phenotypic effects are rescued by expressing the missing domain or by modulating specific downstream targets.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, methods description
- **Evidence pointer** Abstract, SPT and deep-learning analysis; location not provided
- **Issue** The abstract does not specify what exactly was measured by SPT and deep-learning analysis (e.g., condensate size, mobility, dwell time) or how the analysis distinguishes condensate-associated trajectories from free diffusion.
- **Required correction** Briefly describe the key parameters extracted from the trajectory analysis and how they relate to condensate formation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Abstract, introduction
- **Evidence pointer** Abstract, first two sentences; location not provided
- **Issue** The abstract does not mention what is known about PR condensates or how this work builds on or challenges existing findings on IDR-driven condensates.
- **Required correction** Add one or two sentences providing context on prior work on PR or nuclear receptor condensates to frame the novelty.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract, "transcriptional condensates"
- **Evidence pointer** Abstract, first sentence; location not provided
- **Issue** The term "transcriptional condensates" is used without defining the operational criteria used to identify them in the imaging experiments.
- **Required correction** Clarify what constitutes a condensate in the context of the SPT measurements (e.g., size threshold, persistence, enrichment of specific components).

## Risk / unsupported claims
- The claim that both IDR and DBD are "required" for condensate formation is unsupported by the described evidence, as no perturbation experiments are mentioned.
- The claim that mutations result in "a distinct set of genes" is not evaluable without quantitative transcriptomic data.
- The claim linking domain-specific transcription to differential effects on proliferation and migration is not supported by any reported functional data.
- The overall conclusion that "domains beyond IDRs also play a role in TC formation and function" is plausible but not established from the abstract alone.