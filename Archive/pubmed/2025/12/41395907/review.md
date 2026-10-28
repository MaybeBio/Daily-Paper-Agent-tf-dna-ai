## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, methods, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose that contact-network architecture in ATP-like states of condensin encodes asymmetric and temperature-dependent formation of ATP-competent pockets, with the Smc4-associated pocket (ATP1) forming first and being more thermally stable, and that this asymmetry explains the experimentally observed ATP-binding order.
- **Visible evidence base** Coarse-grained switching-Go model simulations, all-atom molecular dynamics simulations, contact-network analysis; specific quantitative results are summarized but no numerical data, error estimates, or methodological details are visible
- **Missing materials affecting confidence** Full methods, simulation parameters, force field details, convergence criteria, statistical analyses, figures, and any comparison with experimental data beyond the cited qualitative observation

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting thermodynamic framework for ATP-binding asymmetry in condensin. The central claim, that contact-network connectivity encodes asymmetric and temperature-sensitive pocket formation, is coherent and aligns with known experimental observations. However, the abstract alone provides insufficient detail to evaluate the robustness of the simulations, the statistical significance of the reported differences, or the strength of the link between the computational predictions and the experimental ATP-binding order. The work is likely of interest to the biophysics and molecular machinery communities, but the evidence base as presented is too thin to establish the case.
- **Who would be interested in the results, and why** Researchers studying SMC complexes, DNA loop extrusion, ATP-driven conformational changes in molecular machines, and those developing coarse-grained and all-atom simulation approaches to capture dynamic asymmetry in multidomain proteins. The proposed thermodynamic framework could also interest experimentalists seeking to interpret or design ATP-binding and hydrolysis experiments in condensin and related complexes.
- **Major strengths** The study addresses a specific and mechanistically important question, namely the molecular origin of asymmetric ATP binding in condensin, which is not well understood. The combination of coarse-grained switching-Go models with all-atom simulations is a sensible multi-scale strategy. The proposed temperature-dependent shift from independent to sequential pocket formation is a testable and conceptually novel hypothesis that could unify disparate observations.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The idea that contact-network connectivity, rather than intrinsic pocket stability alone, encodes asymmetric and temperature-sensitive ATP engagement is a fresh perspective, though it builds on established concepts in protein allostery and network analysis.  
  Scientific importance: If fully validated, the framework could inform understanding of ATP-coupled conformational cycles in SMC complexes and other ring-shaped ATPases, which is a topic of broad significance.  
  Interdisciplinary readership: The work bridges computational biophysics, structural biology, and enzymology, and could appeal to a broad readership if the presentation is accessible.  
  Technical soundness: Cannot be fully assessed from the abstract; the lack of methodological detail and statistical reporting prevents verification of the central claims.  
  Readability for nonspecialists: The abstract is reasonably clear but uses domain-specific terms (e.g., switching-Go models, contact-network architecture) without sufficient explanation for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is intriguing and the approach is appropriate, but the abstract does not provide enough quantitative or methodological detail to support the central claims. A full manuscript with detailed methods, statistical analyses, and direct comparison to experimental data would be required to assess whether the case can be made.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The claim that "the Smc4-associated ATP pocket (ATP1) exhibits higher local contact density and greater thermal stability than the Smc2-associated pocket (ATP2), favoring initial ATP1 pocket formation" is central to the paper.  
- **Evidence pointer** Abstract, results summary; location not provided  
- **Concern** The abstract reports differences in contact density and thermal stability between ATP1 and ATP2 pockets but provides no quantitative values, no error estimates, and no statistical tests. It is unclear whether these differences are robust across simulation replicates, initial conditions, or model parameter choices.  
- **Why it matters** The entire thermodynamic framework rests on the reliability of these simulated differences. Without statistical validation, the observed asymmetry could be an artifact of the specific coarse-grained model or a single trajectory.  
- **Resolution test** Provide quantitative measures (e.g., mean contact density, melting temperatures, free energy differences) with standard deviations or confidence intervals, and demonstrate reproducibility across multiple independent simulations and parameter sets.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The claim that "as temperature increases, the formation of ATP2-binding-competent conformations becomes increasingly dependent on prior ATP1 pocket organization" and that this reflects a "temperature-dependent shift from independent to sequential pocket formation."  
- **Evidence pointer** Abstract, results summary; location not provided  
- **Concern** The abstract does not specify how "dependence" was quantified, what temperature range was explored, or how the transition from independent to sequential formation was identified. No free energy profiles, transition rates, or correlation metrics are reported.  
- **Why it matters** This is the key mechanistic prediction of the study. Without a clear operational definition and quantitative support, the claim is not falsifiable from the presented material.  
- **Resolution test** Define a quantitative metric for pocket formation order (e.g., time lag, conditional probability, or mutual information) and show how it changes with temperature, with appropriate error bars and statistical significance.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence strength  
- **Claim pointer** The claim that the simulation results are "consistent with the experimentally observed ATP-binding order at the two head sites."  
- **Evidence pointer** Abstract, comparison to experimental studies; location not provided  
- **Concern** The abstract cites experimental studies showing asymmetric ATP-binding order but provides no quantitative comparison between simulation predictions and experimental measurements. It is unclear whether the agreement is qualitative or quantitative, and whether the experimental data were used to parameterize or validate the model.  
- **Why it matters** The experimental consistency is a major selling point of the work. Without a direct, quantitative comparison, the claim of consistency is weak and potentially circular if the model was tuned to match the experimental outcome.  
- **Resolution test** Present a direct comparison of simulated and experimental observables (e.g., binding order, rate constants, or temperature dependence) with appropriate metrics of agreement, and clarify whether any experimental data were used in model construction.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract, methods description; location not provided  
- **Issue** The term "contact-network architecture" is used without a precise definition. It is unclear whether this refers to residue-residue contacts, domain-level contacts, or a graph-theoretic measure.  
- **Required correction** Define contact-network architecture explicitly in the methods or introduction, and specify how it was computed from the simulations.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** All-atom simulation results  
- **Evidence pointer** Abstract, all-atom simulations; location not provided  
- **Issue** The all-atom simulation results are described in a single sentence, with no details on system size, simulation length, force field, or how "persistence" and "pre-organization" were quantified.  
- **Required correction** Provide a brief summary of all-atom simulation setup and the metrics used to assess pocket persistence and pre-organization, or refer to a methods section with these details.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Model parameters  
- **Evidence pointer** Abstract, coarse-grained model; location not provided  
- **Issue** The switching-Go model parameters are not described, including how the "ATP-like states" were defined and how the model was parameterized.  
- **Required correction** Specify the model construction, including the reference structures used, the switching scheme, and any parameter fitting procedures.

## Risk / unsupported claims
- The claim that ATP1 pockets are "highly persistent" in the presence of ATP and "destabilize" upon removal is not supported by quantitative data in the abstract.
- The claim that ATP2 pockets show "greater intrinsic pre-organization in the ATP-absent state" is not supported by quantitative data.
- The claim of "consistency" with experimental ATP-binding order is not quantitatively substantiated.
- The temperature-dependent shift from independent to sequential pocket formation is asserted without a defined metric or statistical evidence.
- The identification of "specific structural regions that mediate this thermodynamic shift" is mentioned but no such regions are named or characterized in the abstract.