## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use molecular dynamics simulations with tuned protein and DNA models to propose that dynamics of a non-canonical base generate an entropic signal guiding one-dimensional search by DNA-repair proteins, with a funnel width matching one-dimensional diffusion length, providing a generic mechanism for rapid lesion recognition.
- **Visible evidence base** Abstract text only; no quantitative results, simulation details, or validation data provided
- **Missing materials affecting confidence** Full methods, simulation parameters, force field details, control simulations, quantitative comparisons, figures, and statistical analyses

## Reviewer
- **Overall assessment** The abstract presents an intriguing hypothesis linking base-pair opening dynamics to facilitated target search by DNA-repair proteins. The concept of an entropic signal guiding one-dimensional diffusion is conceptually appealing and potentially significant. However, the abstract provides insufficient technical detail to evaluate the robustness of the simulations, the specificity of the proposed mechanism, or the strength of the claimed alignment between funnel width and diffusion length. The central claims are plausible but currently not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in DNA repair mechanisms, biophysics of protein-DNA interactions, and computational molecular dynamics would find these results relevant. The proposed generic mechanism could interest those studying facilitated diffusion and target recognition in other DNA-binding protein systems, as well as experimentalists seeking testable predictions about lesion recognition kinetics.
- **Major strengths** The hypothesis is novel and mechanistically appealing, linking local base dynamics to global search efficiency. The claim of a generic mechanism has broad potential applicability beyond specific repair proteins. The use of molecular dynamics simulations is appropriate for probing atomic-level dynamics that are difficult to access experimentally.
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
  Originality: The entropic signal concept for lesion recognition is original and distinguishes this work from prior structural or kinetic models. Scientific importance: If validated, the mechanism could unify observations across repair systems, but the current evidence is insufficient to assess impact. Interdisciplinary readership: The topic bridges biophysics, computational biology, and DNA repair, with potential appeal across these fields. Technical soundness: Cannot be evaluated from the abstract alone; simulation tuning and validation are critical unknowns. Readability for nonspecialists: The abstract is accessible but uses terms like "non-canonical base" and "funnel width" without definition, which may hinder nonspecialist comprehension.
- **Recommendation posture** Supportive if technical concerns are resolved; currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "the dynamics of a non-canonical base generate an entropic signal that guides the one-dimensional search of a repair protein."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not specify how the entropic signal is quantified, how it is distinguished from enthalpic contributions, or how the signal directionality is established. No simulation observables or analysis methods are described.  
- **Why it matters** Without a clear operational definition of the entropic signal and its computation, the central mechanistic claim cannot be independently assessed or reproduced.  
- **Resolution test** Provide explicit definitions of the entropic signal, the simulation observables used to measure it, and control simulations that isolate entropic from enthalpic effects.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "the width of the funnel perfectly aligns with the one-dimensional diffusion length of DNA-binding proteins."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract provides no quantitative values for the funnel width or the diffusion length, nor the statistical or systematic uncertainties associated with these quantities. The term "perfectly aligns" implies a precise match that cannot be evaluated without numbers.  
- **Why it matters** This alignment is a key quantitative prediction linking the proposed mechanism to known biophysical parameters. Without data, the claim is unverifiable and may overstate the agreement.  
- **Resolution test** Report numerical values for funnel width and diffusion length with error estimates, and specify the comparison method used to assess alignment.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "an appropriately tuned model of both protein and DNA" was used in simulations.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not describe the tuning procedure, the force field parameters, or the validation against experimental or known structural data. The term "appropriately tuned" is vague and could mask overfitting or model artifacts.  
- **Why it matters** The reliability of all conclusions depends on the realism of the simulation model. Without details on tuning and validation, the results may not generalize to real biological systems.  
- **Resolution test** Describe the tuning process, list the key parameters, and provide validation results comparing simulated properties to experimental data for protein-DNA interactions.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "non-canonical base" is used without specifying whether it refers to a flipped-out base, a mismatched base, or a damaged base, which is central to the lesion recognition context.  
- **Required correction** Define "non-canonical base" explicitly in the context of DNA damage and repair.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The phrase "funnel width" is introduced without explanation of what the funnel represents physically or geometrically in the search process.  
- **Required correction** Provide a brief description of the funnel concept and its biological or physical interpretation.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scientific context  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not mention which specific DNA-repair protein or lesion type was simulated, limiting the reader's ability to contextualize the claims.  
- **Required correction** Specify the protein and lesion system studied, or state explicitly if the mechanism is intended to be generic across systems.

## Risk / unsupported claims
- The claim that the entropic signal "guides" the search is unsupported without demonstrating causality or directionality in the simulation data.
- The claim of "perfect alignment" between funnel width and diffusion length is unsupported without quantitative data.
- The claim of a "generic mechanism" is unsupported from a single simulation study without evidence of applicability across multiple protein or lesion types.
- The overall assertion of "rapid recognition and specificity" is not quantitatively supported by any kinetic or thermodynamic data in the abstract.