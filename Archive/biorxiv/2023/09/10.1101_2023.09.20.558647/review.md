## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supporting information description
- **Assessment boundary** Scientific content, methodology, claims, and evidence presented in the manuscript; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The authors use dynamic Monte Carlo simulations to show that multivalent particles with the same net binding affinity to a host surface diffuse faster as valency increases, and that rigid pattern matching between ligands and receptors can control diffusion
- **Visible evidence base** Main text figures (Figures 1-5), supporting information figures (Figures S1-S5), simulation code and data availability statements
- **Missing materials affecting confidence** The supporting information is not fully provided; only partial descriptions of Figures S1-S5 are included. Tables S1 and S2 are referenced but not shown. The potential function equation is not fully displayed in the methods section.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially important result: that increasing valency while maintaining constant net affinity can dramatically accelerate diffusion of adsorbed particles. The simulation approach is straightforward and the main finding is clearly demonstrated. However, the manuscript has several technical gaps that need to be addressed, particularly regarding the completeness of the methods description, the interpretation of the "pattern matching" effect, and the generalizability of the results beyond the specific model parameters studied. The claim that this finding is counterintuitive and has broad implications is somewhat overstated given the simplicity of the model and the lack of connection to specific experimental systems.
- **Who would be interested in the results, and why** Researchers in biophysics, soft matter physics, and nanoscience would be interested in this work. Specifically, those studying molecular walkers, DNA-binding proteins, nanoparticle-surface interactions, and multivalent binding phenomena would find the results relevant. The finding that multivalency can enhance rather than hinder diffusion could inform the design of synthetic molecular motors and drug delivery vehicles. The pattern matching effect could be relevant for understanding how receptor organization on cell surfaces influences the mobility of bound particles.
- **Major strengths** The central finding is clearly demonstrated with systematic simulations. The parameter space explored is appropriate for establishing the main effect. The normalization of diffusion rates to free diffusion provides a clear metric. The authors address a potentially counterintuitive result with a plausible mechanistic explanation. The code and data are made available, which is commendable for reproducibility.
- **Major Concerns** The methods section is incomplete, particularly regarding the potential function and simulation details. The interpretation of the pattern matching effect relies on entropic arguments that are only partially supported. The generalizability of the results to real systems is not adequately discussed. The relationship between the model parameters and experimentally relevant quantities is not established.
- **Minor Comments** The manuscript would benefit from a more detailed discussion of the limitations of the model. The significance statement is somewhat informal and could be more precise. The use of "walking" to describe the diffusion mechanism is potentially misleading.
- **Technical failings that need to be addressed before the case is established** The incomplete methods description (missing potential function, incomplete simulation parameters) prevents full evaluation of the technical soundness. The entropic explanation for the pattern matching effect requires more direct evidence.
- **Assessment against Nature-style criteria** Originality: The finding that multivalency can enhance diffusion is novel and somewhat counterintuitive, which is a positive aspect. Scientific importance: The result could have implications for understanding and designing multivalent systems, but the connection to real systems is not established. Interdisciplinary readership: The topic spans biophysics, materials science, and nanoscience, which could attract broad interest. Technical soundness: The simulation approach is appropriate, but the incomplete methods description is a concern. Readability for nonspecialists: The abstract and significance statement are accessible, but the main text assumes familiarity with simulation techniques and multivalent binding concepts.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the completeness of the methods description and the evidence for the entropic explanation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The methods section states that particles interact with a surface potential given by an equation that is not fully displayed in the manuscript.
- **Evidence pointer** Methods section, location not provided
- **Concern** The potential function describing the interaction between ligands and the surface is not fully specified. The equation is cut off in the methods section, and the amplitude A and well distance λ are defined but the functional form of the potential is not clear. This is a fundamental aspect of the model that must be fully described for the results to be reproducible and interpretable.
- **Why it matters** Without a complete description of the potential, the simulation results cannot be reproduced or fully understood. The shape of the potential wells (e.g., sinusoidal, Gaussian, harmonic) could significantly affect the diffusion behavior and the interpretation of the results.
- **Resolution test** Provide the complete potential function in the methods section, including any parameters that define its shape. If the potential is sinusoidal, this should be stated explicitly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the origin of this effect is entropic and relates to the system setup" when explaining the minimum in diffusion rate at λ/λ_eq = 1.1 rather than 1.0.
- **Evidence pointer** Results section, Figure 4; Supporting Information, Figure S3
- **Concern** The entropic explanation for the unexpected minimum at λ/λ_eq = 1.1 is based on a detailed analysis presented in the supporting information, but the supporting information is not fully provided. The main text only gives a brief summary of this analysis. The claim that the effect is entropic is supported by the path analysis in Figure S3, but the connection between the number of available paths and the diffusion rate is not rigorously established. The authors show that blocking half of the paths reduces diffusion by 40% for λ/λ_eq = 1.0 and 16% for λ/λ_eq = 1.1, which is consistent with their hypothesis, but this does not directly prove that the difference in diffusion rates is entirely due to entropic effects.
- **Why it matters** The pattern matching effect is a key finding of the manuscript, and the explanation for the unexpected minimum at λ/λ_eq = 1.1 is important for understanding the mechanism. If the entropic explanation is not fully supported, the interpretation of the results could be incorrect.
- **Resolution test** Provide the full supporting information analysis, including the potential energy surfaces and the path analysis. Consider whether additional simulations or analyses could more directly demonstrate the entropic origin of the effect, such as calculating the entropy of the system as a function of λ/λ_eq.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "our results could find applications in various fields utilizing the design of fast-diffusing particles that maintain a strong affinity for target, such as molecular walkers or DNA-binding sliding proteins."
- **Evidence pointer** Discussion section
- **Concern** The connection between the simulation results and the proposed applications is not developed. The model is highly simplified, with harmonic springs connecting ligands and a periodic potential representing receptors. It is not clear how the results would translate to real molecular walkers or DNA-binding proteins, which have much more complex interactions and dynamics. The authors do not discuss what parameter regimes would be relevant for these applications or how the model could be extended to capture the essential features of these systems.
- **Why it matters** The broader significance of the work depends on its relevance to real systems. Without a more detailed discussion of the connection to applications, the impact of the findings may be limited.
- **Resolution test** Add a discussion of how the model parameters relate to experimentally relevant quantities (e.g., binding energies, spring constants, receptor spacing) and what predictions the model makes that could be tested in specific experimental systems.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the maximum displacement was arbitrarily set to 0.1 λ_eq which also defined the time-scale of the simulation."
- **Evidence pointer** Methods section
- **Concern** The use of a maximum displacement of 0.1 λ_eq in the Monte Carlo moves defines the time scale, but it is not clear how this choice affects the results. The authors do not discuss whether the results are sensitive to this parameter or whether a different choice would lead to different conclusions. Additionally, the relationship between the Monte Carlo time and physical time is not established, which limits the interpretation of the diffusion coefficients.
- **Why it matters** The diffusion coefficients are reported as relative values (D/D0), which partially mitigates this concern. However, the absolute values of the diffusion coefficients are not physically meaningful without a connection to real time. The choice of maximum displacement could also affect the dynamics of the system and the observed diffusion behavior.
- **Resolution test** Discuss the sensitivity of the results to the maximum displacement parameter. If possible, relate the Monte Carlo time to physical time using a known diffusion coefficient for a reference system.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "non-diffusing monovalent particle can attain almost unrestricted diffusion when becoming multivalent while retaining its affinity for the host tether or surface." This is a strong claim that is not fully supported by the results, which show diffusion rates approaching but not reaching free diffusion (D/D0 ≈ 0.9 for the best case).
- **Required correction** Soften the language to "nearly unrestricted" or "approaching free diffusion" to accurately reflect the results.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction states that "multivalent molecules encompass molecular walkers such as kinesin, myosin V, and various synthetic counterparts." This is somewhat imprecise, as kinesin and myosin V are not typically described as multivalent in the same sense as the particles in this study. They have two binding domains, but their function involves processive motion driven by ATP hydrolysis, which is not captured by the model.
- **Required correction** Clarify the distinction between the model system and biological molecular motors, or rephrase to avoid implying that the model directly applies to these systems.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The methods section states that "Tables S1 and S2 for detailed information about the simulated patterns" but these tables are not provided in the manuscript or the supporting information description.
- **Required correction** Ensure that Tables S1 and S2 are included in the supporting information and referenced correctly.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure caption for Figure 1 is not provided in the manuscript text. It is unclear what the figure shows and how it relates to the model description.
- **Required correction** Provide a complete figure caption that describes the model setup, including the representation of ligands, springs, and the surface potential.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results
- **Evidence pointer** Results section, Figure 3
- **Issue** The authors state that "with increasing valency the diffusion rate seems to be converging to free diffusion, D0." This is an interesting observation, but the authors do not discuss the physical reason for this convergence or whether it would continue for even higher valencies.
- **Required correction** Add a brief discussion of why the diffusion rate converges to free diffusion and whether this is expected to hold for arbitrarily high valency.

## Risk / unsupported claims
- The claim that "non-diffusing monovalent particle can attain almost unrestricted diffusion when becoming multivalent" is supported by the simulation results but is stated too strongly in the abstract; the results show D/D0 ≈ 0.9, not 1.0.
- The claim that the pattern matching effect can be used to control diffusion of particles is supported by the simulations but the practical implementation of this control is not discussed.
- The claim that the results "could find applications in various fields" is speculative and not supported by any specific analysis of how the model relates to real systems.
- The entropic explanation for the minimum at λ/λ_eq = 1.1 is plausible but not fully proven; the supporting information analysis is not fully visible.
- The relationship between the model parameters and experimentally relevant quantities is not established, so the quantitative predictions of the model cannot be directly compared to experiments.