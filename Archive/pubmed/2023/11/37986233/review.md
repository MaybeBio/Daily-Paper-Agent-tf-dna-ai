## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; full manuscript, figures, and supplementary materials not provided
- **Shared manuscript claim summary** The authors report that scopoletin, a plant-derived acaricide, down-regulates the transcription factor SoxNeuroA in Tetranychus cinnabarinus. They propose that this down-regulation relieves repression of the Orai1 Ca(2+) channel gene, leading to Ca(2+) overload and mite lethality. They further identify specific amino acid residues (ASP185, ARG189, LYS217) as potential binding sites for scopoletin on TcSoxNeuroA.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full methods, all experimental data (qPCR, Western blot, RNAi, Y1H, dual-luciferase, site-directed mutagenesis, microscale thermophoresis, molecular docking), statistical analyses, and any supplementary figures or tables

## Reviewer
- **Overall assessment** The abstract presents a coherent and potentially interesting mechanistic hypothesis linking a plant-derived acaricide to a specific transcription factor and downstream calcium channel regulation. However, the evidence base is limited to the abstract, and several key claims cannot be independently evaluated without access to the full data. The causal chain from scopoletin binding to SoxNeuroA, to Orai1 derepression, to Ca(2+) overload, and to lethality is plausible but requires rigorous validation of each step, particularly the direct binding interaction and the functional significance of the identified residues.
- **Who would be interested in the results, and why** Researchers in agricultural entomology and acarology, particularly those focused on mode of action of botanical pesticides and development of novel acaricides. The work may also interest molecular biologists studying transcription factor regulation of ion channels and those working on calcium signaling in arthropods.
- **Major strengths** The study addresses a relevant and under-explored area, namely the molecular target of a plant-derived acaricide. The use of multiple complementary techniques (qPCR, Western blot, RNAi, Y1H, dual-luciferase, site-directed mutagenesis, microscale thermophoresis) suggests a comprehensive approach. The identification of a specific transcription factor and a putative binding site provides a concrete mechanistic model that could inform future acaricide design.
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
- **Assessment against Nature-style criteria**  
  - Originality: The concept of targeting a transcription factor with a botanical acaricide is not entirely novel, but the specific focus on SoxNeuroA and Orai1 in spider mites is a distinctive angle. However, the abstract does not clearly position this against existing literature on acaricide mechanisms.  
  - Scientific importance: If fully validated, the findings could have practical implications for acaricide development, but the significance is moderate and largely applied rather than fundamental. The mechanistic insight is incremental rather than paradigm-shifting.  
  - Interdisciplinary readership: The work bridges plant chemistry, molecular toxicology, and pest management, but the narrow focus on a single mite species and a specific compound limits broad interdisciplinary appeal.  
  - Technical soundness: The abstract suggests a multi-technique approach, but without full data, the robustness of each assay and the statistical rigor cannot be assessed. The causal inference from RNAi and binding assays appears logical but requires verification.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses technical jargon (e.g., Y1H, microscale thermophoresis) without explanation, which may hinder accessibility for a general scientific audience.
- **Recommendation posture** Supportive if technical concerns are resolved, but currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Causal inference  
- **Claim pointer** The abstract claims that scopoletin's acaricidal mechanism is mediated by down-regulation of SoxNeuroA, which then activates Orai1 Ca(2+) channel, leading to Ca(2+) overload and lethality.  
- **Evidence pointer** Abstract, Results section; location not provided  
- **Concern** The abstract states that RNAi silencing of SoxNeuroA enhances mite susceptibility to scopoletin, which is interpreted as evidence that the acaricidal mechanism is mediated by this gene. However, enhanced susceptibility could also result from off-target effects of RNAi, compensatory physiological changes, or a general stress response, rather than a specific interaction with scopoletin's mode of action. The abstract does not provide data on whether scopoletin's effect is additive, synergistic, or independent of SoxNeuroA knockdown.  
- **Why it matters** The central claim of the paper is that SoxNeuroA is a direct functional target of scopoletin. Without demonstrating that the effect of scopoletin is specifically dependent on SoxNeuroA expression levels (e.g., through rescue experiments or dose-response studies), the causal link remains correlational.  
- **Resolution test** Provide data showing that scopoletin's acaricidal activity is significantly reduced or abolished when SoxNeuroA is overexpressed or constitutively active, and that RNAi phenotypes are rescued by exogenous SoxNeuroA expression. Additionally, show that scopoletin does not affect mites with silenced Orai1, to confirm the pathway specificity.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Direct binding evidence  
- **Claim pointer** The abstract claims that ASP185, ARG189, and LYS217 are key binding sites for scopoletin in TcSoxNeuroA, based on molecular docking and validated by site-directed mutagenesis and microscale thermophoresis.  
- **Evidence pointer** Abstract, Results section; location not provided  
- **Concern** The abstract does not specify whether the microscale thermophoresis assays were performed with wild-type and mutant proteins, and whether the mutations at ASP185, ARG189, and LYS217 actually reduced binding affinity to scopoletin. Molecular docking predictions are often unreliable without experimental validation, and the abstract does not report binding constants or statistical comparisons.  
- **Why it matters** Identifying specific binding residues is a strong claim that could guide future drug design. If the binding data are not robust or if the mutations do not affect binding, the proposed mechanism loses a critical pillar.  
- **Resolution test** Provide quantitative binding affinity data (e.g., Kd values) for wild-type and each mutant protein, with appropriate replicates and statistical analysis. Show that mutations at these residues significantly reduce binding, and ideally correlate binding affinity with acaricidal activity in vivo.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Functional relevance of Orai1 regulation  
- **Claim pointer** The abstract claims that TcSoxNeuroA is a repressor of Orai1 transcription and that scopoletin-induced down-regulation of SoxNeuroA leads to Orai1 activation and Ca(2+) overload.  
- **Evidence pointer** Abstract, Results section; location not provided  
- **Concern** The abstract reports Y1H and dual-luciferase assays showing that SoxNeuroA represses Orai1 promoter activity, with a binding site at positions -361 to -368. However, it is not clear whether this repression is direct (i.e., SoxNeuroA binds to the promoter) or indirect. The abstract does not provide data on whether scopoletin treatment actually increases Orai1 expression or Ca(2+) levels in mites, which is essential to link the in vitro promoter assays to the in vivo phenotype.  
- **Why it matters** The proposed mechanism hinges on the derepression of Orai1 leading to Ca(2+) overload. Without direct evidence of increased Orai1 expression and elevated intracellular Ca(2+) following scopoletin exposure, the pathway remains speculative.  
- **Resolution test** Measure Orai1 mRNA and protein levels, as well as intracellular Ca(2+) concentrations, in mites treated with scopoletin and in SoxNeuroA-silenced mites. Show that these changes correlate with the observed lethality and are reversed by Orai1 knockdown.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility and data transparency  
- **Claim pointer** The abstract reports multiple assays (qPCR, Western blot, RNAi, Y1H, dual-luciferase, site-directed mutagenesis, microscale thermophoresis) but provides no numerical data, statistical details, or experimental replicates.  
- **Evidence pointer** Abstract, Results section; location not provided  
- **Concern** The abstract lacks any quantitative results, such as fold-changes in gene expression, percent mortality in bioassays, or binding affinities. Without these data, the magnitude of the reported effects and the reliability of the conclusions cannot be assessed.  
- **Why it matters** For a mechanistic claim, quantitative data are essential to evaluate the strength of the effects and to determine whether they are biologically meaningful. The absence of such data in the abstract is not necessarily a flaw, but it limits the ability to assess the paper's rigor from the provided material.  
- **Resolution test** In the full manuscript, provide all numerical data with error bars, statistical tests, and sample sizes for each experiment. Ensure that key results are presented in figures or tables with clear legends.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of terminology  
- **Affected element** Title and abstract  
- **Evidence pointer** Title, Abstract  
- **Issue** The title uses "down-regulated transcription factor-SoxNeuroA gene," which is grammatically awkward and could be misinterpreted as a gene that is down-regulated rather than a transcription factor gene.  
- **Required correction** Rephrase to "Functional analysis of the transcription factor gene SoxNeuroA, which is down-regulated in the acaricidal mechanism of scopoletin against spider mites."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Contextualization  
- **Affected element** Background section  
- **Evidence pointer** Abstract, Background  
- **Issue** The abstract states that SoxNeuroA plays a vital role in maintaining Ca(2+) homeostasis, but does not cite or explain the basis for this claim. It is unclear whether this is established in other organisms or specific to mites.  
- **Required correction** Provide a brief reference or explanation in the full manuscript to support this statement, and clarify whether this role is conserved in T. cinnabarinus.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Generalizability  
- **Affected element** Conclusion  
- **Evidence pointer** Abstract, Conclusion  
- **Issue** The conclusion states that the findings have "vital implications for the design of next-generation green acaricides," but the abstract does not discuss potential limitations, such as whether the target is conserved across other pest mite species or whether resistance could develop.  
- **Required correction** Add a brief statement in the discussion about the potential breadth of applicability and any known limitations of targeting SoxNeuroA.

## Risk / unsupported claims
- The claim that scopoletin directly binds to TcSoxNeuroA at ASP185, ARG189, and LYS217 is unsupported without quantitative binding data for mutants.
- The claim that SoxNeuroA down-regulation is the primary mediator of scopoletin's acaricidal effect is not established, as alternative mechanisms are not excluded.
- The claim that Orai1 activation leads to Ca(2+) overload and lethality is not directly evidenced in the abstract; no Ca(2+) measurements or Orai1 expression data are provided.
- The generalizability of the findings to other mite species or field conditions is not addressed and cannot be evaluated from the abstract.