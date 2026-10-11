## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, tables, or supplementary materials were available for evaluation
- **Shared manuscript claim summary** The authors propose that Type III secretion system effectors (Nop proteins) from symbiotic rhizobia contain previously unrecognised structural modules, including nucleic acid-binding and RNA-dependent RNA polymerase domains, and that these modules are conserved in plant pathogens. They further claim discovery of a BPN domain that structurally mimics plant B3 transcription factors, suggesting a direct mechanism for host developmental hijacking.
- **Visible evidence base** Abstract text only; no experimental data, structural predictions, alignments, or validation experiments are shown
- **Missing materials affecting confidence** Full manuscript, methods, all figures and tables, structural prediction confidence metrics, experimental validation data, sequence alignments, and any functional assays

## Reviewer
- **Overall assessment** The abstract presents a provocative and potentially field-changing hypothesis: that rhizobial Nop effectors act as direct genetic modulators via modular structural domains, including mimics of plant transcription factors. The use of AlphaFold2-mediated structural proteomics is timely and appropriate for addressing the challenge of extreme sequence divergence. However, the abstract alone provides insufficient evidence to evaluate the robustness of the structural predictions, the statistical significance of the domain conservation claims, or the functional relevance of the proposed mechanisms. The claim of a "direct mechanism for hijacking legume development" is not supported by any functional data presented in the abstract. The work is likely to interest researchers in plant-microbe interactions, symbiosis, and effector biology, but the current evidence base is too limited to establish the central claims.
- **Who would be interested in the results, and why** Researchers studying plant-microbe interactions, particularly legume-rhizobia symbiosis and bacterial effector biology, would be the primary audience. The proposed conservation of effector modules between symbionts and pathogens, and the potential mimicry of plant transcription factors, would also attract those interested in convergent evolution of host manipulation strategies and in the application of structural prediction methods to diverse protein families.
- **Major strengths** The study addresses a significant knowledge gap in rhizobial effector function using a modern and appropriate methodology. The proposal of a modular domain architecture is a plausible framework for understanding sequence-divergent effectors. The connection between symbiont and pathogen effector modules is conceptually interesting and could have broad implications.
- **Major Concerns** The abstract lacks any experimental validation of the predicted functions. The claim that effectors are "cryptic transcriptional or post-transcriptional regulators" is presented as a finding but no supporting data are described. The BPN domain mimicry claim is central to the paper's significance but is supported only by structural prediction, not by functional demonstration. The conservation with Pantoea is mentioned but the strength and significance of this conservation are not assessable.
- **Minor Comments** The abstract would benefit from clarifying how many effectors were analysed and how many contain the proposed modules. The term "cryptic" is used without definition. The relationship between the 22 structural units and the specific domains mentioned (nucleic acid-binding, RdRP, BPN) is not explained.
- **Technical failings that need to be addressed before the case is established** No functional validation of predicted DNA or RNA binding is presented. No evidence that the BPN domain actually binds DNA or affects transcription is shown. No experimental demonstration that these modules are required for symbiosis or nodule organogenesis is provided. The structural predictions are not accompanied by confidence metrics or experimental corroboration.
- **Assessment against Nature-style criteria** Originality: high, as the proposed modular architecture and transcription factor mimicry are novel concepts for rhizobial effectors. Scientific importance: potentially high, as this could redefine how rhizobial effectors are understood to function, but the importance is contingent on validation. Interdisciplinary readership: the topic bridges microbiology, plant biology, and structural biology, and would appeal to a broad audience if the claims are substantiated. Technical soundness: cannot be assessed from the abstract alone; the reliance on AlphaFold2 predictions without experimental validation is a concern. Readability for nonspecialists: the abstract is generally clear but uses specialised terms (e.g., BPN, PUA-like) without sufficient context for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is intriguing and worthy of investigation, but the abstract does not provide sufficient evidence to support the central claims of functional modulation and developmental hijacking. A revised manuscript with experimental validation and detailed structural evidence would be needed to establish the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** "We reveal that many Nop effectors are cryptic transcriptional or post-transcriptional regulators, harbouring unrecognised nucleic acid-binding modules and RNA-dependent RNA polymerase domains."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract claims that Nop effectors are transcriptional or post-transcriptional regulators based on predicted structural modules, but no functional data are presented. The presence of a predicted domain does not establish regulatory activity.
- **Why it matters** The central thesis of the paper is that these effectors act as genetic modulators. Without experimental evidence of DNA or RNA binding, or effects on transcription, the claim is speculative and cannot support the paper's conclusions.
- **Resolution test** Provide experimental data showing that representative effectors bind nucleic acids and/or alter gene expression in plant or heterologous systems.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural prediction validation
- **Claim pointer** "Using AlphaFold2-mediated structural proteomics, we identified a modular architecture in rhizobial effectors composed of 22 distinct structural units."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not report any confidence metrics (e.g., pLDDT, PAE) or experimental validation for the predicted structures. The identification of 22 structural units is presented as a definitive result, but the reliability of these predictions is unknown.
- **Why it matters** AlphaFold2 predictions are valuable but can be unreliable for highly divergent or disordered proteins. Without confidence measures or experimental corroboration, the structural claims are not verifiable.
- **Resolution test** Include per-residue confidence scores, show representative predicted structures with aligned experimental data where available, or validate key predictions using biophysical methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance of BPN domain
- **Claim pointer** "We discovered the BPN (B3 and PUA-like nucleic acid binding) domain as a structural mimic of plant B3-domain transcription factors, pointing to a direct mechanism for hijacking legume development."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The claim that the BPN domain mimics plant B3 transcription factors is based solely on structural prediction. No evidence is provided that this domain binds DNA, affects transcription, or influences nodule development.
- **Why it matters** This is the most significant and novel claim in the abstract. If true, it would represent a major advance in understanding effector function. However, without functional validation, the claim of a "direct mechanism" is unsupported.
- **Resolution test** Demonstrate that the BPN domain binds DNA with sequence specificity, that it can affect transcription in a reporter assay, and that mutation of this domain alters effector function in planta.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Conservation claim
- **Claim pointer** "These modules are conserved in specific plant pathogens, such as gall-inducing Pantoea, where our predicted structural units align with experimentally validated DNA-binding domains."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract states that predicted structural units align with experimentally validated DNA-binding domains in Pantoea, but the nature and significance of this alignment are not described. It is unclear whether this is a sequence, structural, or functional conservation.
- **Why it matters** This claim is used to support the broader relevance of the findings. If the conservation is weak or only structural, the functional implications may be overstated.
- **Resolution test** Provide alignment statistics, structural superposition metrics, and functional data from Pantoea to demonstrate that the conserved modules are functionally equivalent.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "cryptic" is used to describe the regulators but is not defined. It is unclear whether this means previously unrecognised, functionally hidden, or something else.
- **Required correction** Define "cryptic" in the context of the study, or replace with a more precise term.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Quantitative reporting
- **Affected element** Abstract results
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not state how many effectors were analysed or how many contain the proposed modules. This makes it difficult to gauge the breadth of the findings.
- **Required correction** Include the number of effectors analysed and the proportion containing the identified modules.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract structure
- **Evidence pointer** Abstract; location not provided
- **Issue** The relationship between the 22 structural units and the specific domains (nucleic acid-binding, RdRP, BPN) is not explained. It is unclear whether these domains are among the 22 units or are separate findings.
- **Required correction** Clarify how the 22 structural units relate to the specific domains mentioned.

## Risk / unsupported claims
- The claim that Nop effectors are "cryptic transcriptional or post-transcriptional regulators" is unsupported by functional evidence in the abstract.
- The claim of a "direct mechanism for hijacking legume development" via BPN domain mimicry is unsupported by any experimental data.
- The conservation of modules with Pantoea is mentioned but not substantiated with alignment or functional data.
- The overall conclusion that rhizobia "employ a modular domain-fusion strategy to act as direct genetic modulators" is a reasonable hypothesis but is not established by the evidence presented in the abstract.