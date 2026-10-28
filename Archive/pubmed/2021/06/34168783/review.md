## Review setup
- **Input scope** Full manuscript text (perspective article)
- **Assessment boundary** Scientific content, technical soundness, and clarity of the presented arguments and simulation studies
- **Shared manuscript claim summary** The authors present a perspective on molecular simulation of DNA, focusing on hierarchical structure and dynamics from base flipping to chromatin organization, drawing primarily on their own recent simulation studies
- **Visible evidence base** Full text including abstract, introduction, four main thematic sections, summary, and references cited inline
- **Missing materials affecting confidence** Figures referenced but not provided; specific simulation parameters and methodological details for some studies are summarized rather than fully described; no supplementary information included

## Reviewer
- **Overall assessment** This perspective provides a useful overview of the authors' contributions to DNA simulation, particularly in base flipping mechanisms, DNA allostery, i-motif structure, and chromatin organization. The writing is generally clear and the thematic organization is logical. However, the manuscript reads more as a summary of the authors' own work than a balanced perspective on the field, and several technical claims lack sufficient detail to be fully evaluated. The connection between simulation results and biological function is often asserted rather than critically examined. The article would benefit from a more critical assessment of limitations and a broader contextualization within the field.

- **Who would be interested in the results, and why** Computational biophysicists and chemists working on nucleic acid simulations would find this perspective relevant, as it summarizes recent methodological advances and applications. Researchers studying DNA repair mechanisms, epigenetic modifications, and chromatin structure may also be interested in the specific findings highlighted. However, the narrow focus on the authors' own studies limits its appeal to a broader readership.

- **Major strengths** The manuscript covers a wide range of DNA simulation topics in a coherent narrative. The discussion of base flipping mechanisms and the role of enhanced sampling methods is informative. The section on i-motif structure provides a useful summary of recent work in this less-reviewed area. The authors make a reasonable attempt to connect sequence-level properties to higher-order chromatin organization.

- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
  - R1-M5

- **Minor Comments**
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
  - R1-m6

- **Technical failings that need to be addressed before the case is established** The manuscript does not present a single new experimental or computational result. As a perspective, the primary claims are interpretive and synthetic. The main technical concern is that several quantitative claims (e.g., free energy barriers, correlation coefficients) are presented without sufficient methodological detail or error analysis to assess their reliability. The force field limitations are acknowledged but not systematically addressed in the context of the specific results discussed.

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The perspective synthesizes the authors' prior work but does not present fundamentally new concepts or frameworks. The attempt to connect DNA sequence to chromatin structure through simulation is not entirely novel.
  - Scientific importance: Moderate. The topics covered are important in the field, but the perspective does not offer a critical evaluation that would significantly advance understanding beyond the authors' prior publications.
  - Interdisciplinary readership: Limited. The manuscript is written primarily for computational biophysicists and may be challenging for experimental biologists or non-specialists due to technical jargon and assumed background knowledge.
  - Technical soundness: The simulation methods referenced are generally appropriate, but the lack of detailed methodological descriptions and error analysis for the summarized results prevents full assessment of technical soundness.
  - Readability for nonspecialists: The manuscript is reasonably well written but assumes familiarity with DNA simulation techniques and terminology. Some sections, particularly the methods descriptions, would be difficult for nonspecialists to follow.

- **Recommendation posture** Supportive if technical concerns are resolved. The perspective has merit as a summary of the authors' contributions, but it requires a more balanced treatment of the field, clearer methodological details, and a more critical discussion of limitations before it can be considered a strong contribution.

### Major Concern R1-M1
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Scope and balance
- **Claim pointer** The authors state this is a perspective on molecular simulation of DNA, but the content is almost exclusively focused on their own recent studies
- **Evidence pointer** Abstract, Introduction, all thematic sections
- **Concern** The manuscript is framed as a general perspective on DNA simulation, yet nearly all discussed results come from the authors' own publications. This creates a narrow and potentially biased view of the field. Other important contributions to DNA simulation, particularly from other groups, are mentioned only in passing or not at all.
- **Why it matters** A perspective should provide a balanced overview of a field to be useful to readers. The current approach reads more like a review of the authors' own work, which limits its value as an objective assessment of the state of the art.
- **Resolution test** The authors should either broaden the scope to include a more representative selection of work from the wider community, or explicitly frame the manuscript as a summary of their own research program rather than a general perspective.

### Major Concern R1-M2
- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical detail and reproducibility
- **Claim pointer** The manuscript presents specific quantitative results, such as free energy barriers of approximately 18 kcal/mol for base flipping and correlation coefficients with periodic oscillations, without sufficient methodological detail
- **Evidence pointer** Section "The mechanism of DNA base flipping and modification of DNA bases", Section "DNA structural correlation in short and long ranges"
- **Concern** Several quantitative claims are presented without adequate description of simulation parameters, force fields used, convergence criteria, or statistical uncertainties. For example, the free energy values for base flipping are stated without error bars or details on the enhanced sampling protocol. The correlation coefficients are presented without confidence intervals.
- **Why it matters** Reproducibility is a core principle of computational science. Without sufficient methodological detail, readers cannot assess the reliability of the results or reproduce them independently.
- **Resolution test** The authors should provide more detailed methodological descriptions for each highlighted result, including force field versions, simulation lengths, enhanced sampling parameters, and uncertainty estimates. If this information is available in the original publications, clear references should be provided.

### Major Concern R1-M3
- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Critical assessment of limitations
- **Claim pointer** The authors discuss limitations of force fields and simulation methods, but do not critically evaluate how these limitations affect the specific results they present
- **Evidence pointer** Section "Summary and outlook"
- **Concern** While the authors acknowledge general limitations of current force fields, they do not discuss how these limitations might impact the specific findings highlighted in the perspective. For example, the claim that i-motif structures are unstable at neutral pH is based on simulations that may be sensitive to force field parameters, yet this sensitivity is not discussed.
- **Why it matters** A critical assessment of limitations is essential for readers to understand the confidence level of the presented results. Without this, the perspective may overstate the reliability of simulation findings.
- **Resolution test** The authors should explicitly discuss how force field uncertainties, sampling limitations, and other methodological issues might affect each major conclusion presented.

### Major Concern R1-M4
- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Connection between simulation and biology
- **Claim pointer** The authors claim that simulation results have implications for gene regulation and chromatin structure, but the causal links are often asserted rather than demonstrated
- **Evidence pointer** Section "Structural aspect and gene regulatory function of non-canonical i-motif DNA", Section "Molecular basis of DNA condensation and structural organization of chromatin"
- **Concern** The manuscript frequently moves from simulation observations to biological conclusions without sufficient evidence or discussion of alternative explanations. For example, the claim that DNA sequence-dependent phase separation drives chromatin organization is presented as a plausible hypothesis but is not critically examined against competing models.
- **Why it matters** Overinterpretation of simulation results can mislead readers, particularly those less familiar with computational methods. A perspective should clearly distinguish between established findings, plausible hypotheses, and speculation.
- **Resolution test** The authors should clearly label which conclusions are directly supported by simulation data, which are extrapolations, and which are speculative hypotheses requiring further testing.

### Major Concern R1-M5
- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Readability and accessibility
- **Claim pointer** The manuscript is intended as a perspective for a broad scientific audience, but contains substantial technical detail that may be inaccessible to nonspecialists
- **Evidence pointer** Throughout, particularly Section "The mechanism of DNA base flipping and modification of DNA bases"
- **Concern** The manuscript assumes significant background knowledge in molecular dynamics simulation techniques, enhanced sampling methods, and nucleic acid biophysics. Terms such as "SITS", "US", "PMF", and "eversion distance" are used without adequate introduction for nonspecialist readers.
- **Why it matters** A perspective in a general chemistry journal should be accessible to a broad readership. If the intended audience is limited to computational specialists, this should be clarified.
- **Resolution test** The authors should either provide more accessible explanations of technical concepts or explicitly state the target audience and adjust the level of technical detail accordingly.

### Minor Comment R1-m1
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and does not clearly outline the structure of the perspective or the main take-home messages.
- **Required correction** Consider revising the abstract to more clearly state the scope, main topics covered, and key conclusions.

### Minor Comment R1-m2
- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction cites several references but does not provide a clear overview of the broader field of DNA simulation, making it difficult for readers to contextualize the authors' contributions.
- **Required correction** Consider adding a brief overview of key developments in DNA simulation from other groups to provide context.

### Minor Comment R1-m3
- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures
- **Evidence pointer** Figures referenced but not provided
- **Issue** The figures are referenced but not included in the provided manuscript, making it impossible to assess their quality or relevance.
- **Required correction** Ensure all figures are included and clearly labeled, with appropriate captions that explain the key findings.

### Minor Comment R1-m4
- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section "The mechanism of DNA base flipping and modification of DNA bases"
- **Evidence pointer** Section "The mechanism of DNA base flipping and modification of DNA bases"
- **Issue** The term "eversion distance" is used without a clear definition or explanation of how it is calculated.
- **Required correction** Provide a brief definition or reference for this technical term.

### Minor Comment R1-m5
- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section "DNA structural correlation in short and long ranges"
- **Evidence pointer** Section "DNA structural correlation in short and long ranges"
- **Issue** The discussion of DNA allostery would benefit from a clearer distinction between the authors' simulation results and experimental observations from other groups.
- **Required correction** Clearly label which findings come from simulations and which are experimental, and discuss any discrepancies.

### Minor Comment R1-m6
- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Molecular basis of DNA condensation and structural organization of chromatin"
- **Evidence pointer** Section "Molecular basis of DNA condensation and structural organization of chromatin"
- **Issue** The discussion of chromatin organization would benefit from a more explicit connection to experimental data on chromosome conformation capture and other experimental techniques.
- **Required correction** Consider adding a brief discussion of how simulation results relate to experimental observations of chromatin structure.

## Risk / unsupported claims
- The claim that "the lifetime of the tested mismatched bases stayed at an extra-helical position far away from their intra-helical state" is presented without quantitative details or statistical analysis, making it difficult to assess the strength of this claim.
- The statement that "the perturbation generated by a primary protein binding event travels as a wave to distant regions of DNA following a hopping mechanism" is presented as a finding but is not supported by detailed evidence in this manuscript.
- The claim that "the distinction between the compartments strongly correlates with the local variation of TA richness" is presented without specific data or statistical measures.
- The assertion that "the nucleotide sequence can be the driving force for the phase segregation and structural organization of chromatin" is a hypothesis that is not critically examined against alternative models.
- Several quantitative results (free energy barriers, correlation coefficients, binding energies) are presented without error bars or uncertainty estimates, making their reliability unassessable from the provided text.