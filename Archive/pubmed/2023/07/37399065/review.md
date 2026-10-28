## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract, without access to full manuscript text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use molecular dynamics simulations and dynamical network theory to propose that the SF3B1 K700E mutation, located approximately 60 Å from the branch point sequence recognition site, disrupts RNA-mediated allosteric cross-talk between these distal regions, thereby contributing to aberrant pre-mRNA splicing in cancer.
- **Visible evidence base** Abstract text only; no methodological details, simulation parameters, statistical analyses, or quantitative results are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation protocols, force field parameters, convergence criteria, network analysis details, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible and mechanistically interesting hypothesis linking a distal cancer-associated mutation to altered splicing via allosteric communication. However, the current evidence base is insufficient to evaluate the technical rigor of the simulations, the robustness of the network analysis, or the strength of the proposed causal link. The claim of "scrambled" allosteric cross-talk is asserted without quantitative support in the abstract, and the absence of methodological detail precludes assessment of whether the findings are reproducible or statistically meaningful.
- **Who would be interested in the results, and why** Researchers in RNA splicing biology, cancer genomics, and computational biophysics would find these results relevant. The work addresses a long-standing question about how distal mutations in SF3B1 exert functional effects, which is of interest to those studying spliceosomal dysfunction in hematologic malignancies and to computational biologists developing allostery prediction methods.
- **Major strengths** The study addresses a clinically significant and mechanistically unresolved problem, namely the long-range effect of the K700E mutation. The combination of molecular dynamics and dynamical network theory is an appropriate and potentially powerful approach for probing allosteric communication. The hypothesis of RNA-mediated cross-talk is novel and could stimulate further experimental work.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of methodological detail), R1-M2 (absence of quantitative evidence for the allostery claim), R1-M3 (no validation or convergence assessment)
- **Assessment against Nature-style criteria**  
  - Originality: The hypothesis of RNA-mediated allostery between the K700E site and the BPS is original and not previously established in the literature, based on the abstract.  
  - Scientific importance: The topic is important given the prevalence of SF3B1 mutations in cancer, but the abstract does not demonstrate that the findings change current understanding of splicing regulation.  
  - Interdisciplinary readership: The work bridges computational chemistry and cancer biology, which could attract a broad audience, but the abstract is too specialized for nonspecialists to fully appreciate the significance.  
  - Technical soundness: Cannot be assessed from the abstract alone; no simulation or analysis details are provided.  
  - Readability for nonspecialists: The abstract is concise but uses jargon (e.g., "dynamical network theory," "allosteric cross-talk") without sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is intriguing, but the abstract lacks the technical and quantitative detail necessary to support the central claim. A revised manuscript with full methodological transparency and robust evidence would be needed for a supportive posture.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that molecular dynamics simulations and dynamical network theory analysis "unlock the molecular terms underpinning the impact" of SF3b mutations on pre-mRNA selection.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract provides no information on simulation length, force field parameters, system setup, number of replicates, or convergence criteria. Without these details, it is impossible to assess whether the simulations adequately sampled the conformational space or whether the observed effects are robust or artifacts of insufficient sampling.  
- **Why it matters** Molecular dynamics results are highly sensitive to simulation protocols, and allostery inferences require statistically converged ensembles. The absence of this information undermines confidence in the reliability of the reported findings.  
- **Resolution test** Provide full simulation details in the manuscript, including system construction, equilibration protocol, production run lengths, replicate numbers, and convergence metrics (e.g., RMSD stability, block averaging). Show that key results are reproducible across independent simulations.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence strength  
- **Claim pointer** The authors state that K700E "scrambles RNA-mediated allosteric cross-talk between the BPS and the mutation site."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The central claim of altered allosteric cross-talk is presented as a definitive conclusion, but no quantitative evidence is shown in the abstract. There are no metrics such as correlation coefficients, communication pathway strengths, or free energy differences that would substantiate the "scrambling" effect.  
- **Why it matters** The claim is the core contribution of the study. Without quantitative support, it remains an assertion rather than a demonstrated finding, and the causal link to cancer-associated missplicing is speculative.  
- **Resolution test** Present quantitative comparisons between wild-type and K700E systems, such as changes in dynamical network metrics (e.g., edge betweenness, community structure), and demonstrate statistical significance with appropriate error analysis. Ideally, relate these changes to experimentally known splicing outcomes.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation  
- **Claim pointer** The authors propose that "altered allostery contributes to cancer-associated missplicing by mutated SF3B1."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract offers no experimental validation or comparison with existing experimental data on K700E-induced splicing changes. The link between computational predictions and biological phenotype is asserted without any supporting evidence.  
- **Why it matters** Computational predictions of allostery require experimental corroboration or at least consistency with known functional data to be convincing. Without this, the biological relevance of the proposed mechanism remains unverified.  
- **Resolution test** Include comparisons with published experimental data on K700E splicing targets or perform additional simulations that predict testable outcomes (e.g., altered binding affinities) that could be experimentally verified. Clearly state any limitations in connecting simulation results to in vivo phenotypes.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The phrase "pillar of faithful premature-messenger (pre-mRNA) splicing" is awkward and could be simplified for clarity.  
- **Required correction** Rephrase to "Faithful pre-mRNA splicing relies on precise recognition of key intronic sequences by specific splicing factors."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Abstract background  
- **Evidence pointer** Abstract, second sentence  
- **Issue** The abstract does not explain why the 60 Å distance is significant or how it motivates the allostery hypothesis, which is central to the study.  
- **Required correction** Add a brief statement clarifying that the large distance precludes direct interaction, thus implying a long-range communication mechanism.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Abstract, "dynamical network theory"  
- **Evidence pointer** Abstract, methods description  
- **Issue** The term "dynamical network theory" is not defined or contextualized, which may confuse nonspecialist readers.  
- **Required correction** Briefly describe the method, e.g., "a graph-based analysis of correlated motions in the simulation trajectories."

## Risk / unsupported claims
- The claim that K700E "scrambles" allosteric cross-talk is unsupported by quantitative evidence in the abstract.
- The causal link between altered allostery and cancer-associated missplicing is speculative and not validated by experimental data.
- The general statement that the findings "broaden our comprehension" of pre-mRNA metabolism is not substantiated by specific results.
- The reliability of the simulation results cannot be assessed due to missing methodological details.