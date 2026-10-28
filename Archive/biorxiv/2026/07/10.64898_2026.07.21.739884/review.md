## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, supplementary information, and cited literature.
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims based solely on the provided material.
- **Shared manuscript claim summary** The authors propose that flexibly tethered small DNA-binding domains, exemplified by the α-CTDs of bacterial RNA polymerase, accelerate diffusion-limited protein-DNA association by forming a transient intermediate that tethers the larger protein near the DNA, thereby increasing the probability of stable binding.
- **Visible evidence base** Single-molecule fluorescence microscopy measurements of RNAP binding kinetics for wild-type and mutant constructs; kinetic modeling; Brownian dynamics simulations; supplementary figures and tables.
- **Missing materials affecting confidence** Raw data files, full experimental protocols for single-molecule assays, detailed simulation code, and complete statistical analyses are not fully provided. The manuscript is a preprint and has not undergone peer review.

## Reviewer
- **Overall assessment** The manuscript presents a compelling and well-structured study combining single-molecule experiments, theory, and simulation to address a fundamental question in protein-DNA association kinetics. The experimental design is thoughtful, and the modeling framework is rigorous. However, several technical details and potential alternative interpretations require clarification before the conclusions can be fully accepted.
- **Who would be interested in the results, and why** Researchers in biophysics, molecular biology, and biochemistry, particularly those studying transcription mechanisms, protein-DNA interactions, and diffusion-limited reaction kinetics. The proposed general mechanism may also interest scientists working on other DNA-binding proteins with flexible tethers or intrinsically disordered regions.
- **Major strengths** The study directly tests a specific hypothesis with well-controlled mutant constructs. The combination of experimental kinetics, analytical theory, and Brownian dynamics provides a multi-pronged validation approach. The finding that α-CTDs accelerate association without affecting dwell times is a clear and important result. The proposed mechanism is generalizable and quantitatively framed.
- **Major Concerns** The following concerns are detailed below.
- **Minor Comments** The following minor comments are detailed below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3.
- **Assessment against Nature-style criteria** Originality: High. The proposed mechanism, while conceptually related to "fly-casting" or tethering effects, is quantitatively developed and experimentally tested in a new context. Scientific importance: High. The results have implications for understanding transcription initiation and general protein-DNA recognition. Interdisciplinary readership: Moderate to high. The work bridges single-molecule biophysics, theory, and molecular biology. Technical soundness: Generally strong, but with concerns about model assumptions and data analysis that need addressing. Readability for nonspecialists: The abstract and introduction are clear, but the results and methods sections are dense and may be challenging for a broad audience.
- **Recommendation posture** Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the presence of α-CTDs accelerates DNA binding by ~10-fold and ~55-fold for one- and two-CTD constructs, respectively, relative to zero-CTD.
- **Evidence pointer** Results section, Figure 2E-F, Table S1
- **Concern** The measurement of association rate constants relies on the assumption that the binding of RNAP to surface-tethered DNA is diffusion-limited and that the observed first-order kinetics accurately reflect the bimolecular association. The manuscript does not provide sufficient detail on how the active fraction (A_f) is determined and how potential artifacts from surface immobilization, such as partial DNA accessibility or non-specific interactions with the slide, are excluded. The higher protein concentrations used for zero-CTD and one-CTD constructs could lead to increased non-specific surface binding, which may bias the measured rates.
- **Why it matters** The quantitative fold-changes in association rates are central to the paper's conclusions. If the rate measurements are systematically biased by surface effects or incorrect assumptions about the binding model, the derived acceleration factors and the subsequent model fitting would be unreliable.
- **Resolution test** Provide a more detailed description of the data analysis, including how A_f is estimated and how the model accounts for potential surface artifacts. Show control experiments demonstrating that the binding kinetics are not limited by diffusion to the surface or by non-specific interactions. Ideally, compare the surface-based measurements with a solution-based method, if feasible.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the kinetic model, which assumes a single effective tether for the two α-CTDs, is validated by Brownian dynamics simulations.
- **Evidence pointer** Results section, Figure 5, Supplementary Text
- **Concern** The Brownian dynamics simulations are used to validate the assumptions of the kinetic model, but the simulation model itself is highly coarse-grained. The representation of RNAP as a triangle and the α-CTD as a point at the end of a polymer tether may not capture the relevant physics, such as the flexibility of the full RNAP structure, the precise geometry of the DNA-binding sites, or the potential for simultaneous interactions of both α-CTDs with the DNA. The sensitivity analysis in the SI is a good start, but it may not cover all relevant parameter space.
- **Why it matters** The simulations are a key piece of evidence supporting the proposed mechanism. If the simulation model is not a faithful representation of the real system, the agreement between simulations and experiments could be coincidental or misleading.
- **Resolution test** Provide a more detailed justification for the coarse-grained model parameters. Show that the simulation results are robust to variations in the model geometry, such as the size and shape of the RNAP, the tether attachment point, and the interaction potentials. Ideally, compare the simulation predictions with additional experimental measurements, such as the effect of tether length on acceleration.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the α-CTDs do not affect the dwell times of RNAP on DNA, based on the observation that wild-type and zero-CTD RNAP have indistinguishable dwell time distributions.
- **Evidence pointer** Results section, Figure 3
- **Concern** The dwell time analysis is used to argue that the α-CTDs do not stabilize the bound state. However, the manuscript reports that the dwell time distribution is multi-exponential, indicating multiple bound states. It is not clear whether the comparison between wild-type and zero-CTD is sensitive enough to detect a change in the relative populations or lifetimes of these states, especially if the α-CTD effect is small or affects a minor component. The statistical power of the comparison is not discussed.
- **Why it matters** The conclusion that α-CTDs only affect association, not dissociation, is important for the proposed mechanism. If the dwell time analysis is not sufficiently sensitive, the conclusion may be premature.
- **Resolution test** Provide a more detailed statistical analysis of the dwell time distributions, including a comparison of the fitted parameters for each component. State the minimum effect size that could be detected with the current sample size. Consider whether the experiment is powered to detect a small change in the major dwell time component.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction use the term "general physical mechanism" which is a strong claim. While the authors provide evidence for this mechanism in the case of RNAP, the generality is inferred from the physical principles, not directly demonstrated for other proteins.
- **Required correction** Soften the language in the abstract and introduction to "a potentially general physical mechanism" or "a general physical mechanism that may apply to other proteins" to avoid overstating the scope of the findings.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Methods, "Single-molecule observation of RNAP binding to DNA"
- **Concern** The methods for the single-molecule experiments are described, but some details are missing, such as the exact buffer conditions, temperature, and the method for determining the surface density of DNA molecules. This information is crucial for reproducibility.
- **Required correction** Add the missing experimental details to the Methods section or the Supplementary Information.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2E-F
- **Concern** The error bars in Figure 2E-F are described as standard errors from bootstrapping, but it is not clear if they represent the uncertainty in the fitted parameter or the variability between experimental replicates. This distinction is important for interpreting the significance of the differences between constructs.
- **Required correction** Clarify in the figure legend what the error bars represent and how many independent experiments were performed.

## Risk / unsupported claims
- The claim that the mechanism is "general" is not directly supported by experiments on other proteins, only inferred from the physical model.
- The claim that the α-CTDs do not affect dwell times is based on a comparison that may lack statistical power, as discussed in R1-M3.
- The quantitative predictions of the model (e.g., the specific values of k_CTD^off) are not directly measured but inferred from fitting, and their accuracy is dependent on the validity of the model assumptions.
- The statement that the mechanism "may allow the polymerase to rapidly bind DNA while minimizing non-functional sequestration on the genome" is speculative and not directly tested.