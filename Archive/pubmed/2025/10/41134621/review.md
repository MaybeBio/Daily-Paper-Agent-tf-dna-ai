## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and presentation quality based solely on the supplied text
- **Shared manuscript claim summary** The authors use coarse-grained polymer simulations to show that transcription factor (TF) phase separation modulates enhancer-promoter (E-P) communication across genomic distances, with an optimal "golden mean" level of condensation maximizing E-P contact probability. They report that excessive TF condensation impairs E-P contacts via molecular crowding and competitive binding, and that the scaling exponent of mean first passage time with genomic distance decreases as TF phase separation strengthens.
- **Visible evidence base** Main text figures (Figs. 1-5) are referenced but not provided; supplementary figures (Figs. S1-S8) are referenced but not provided; methods section is complete
- **Missing materials affecting confidence** All figures and supplementary information are absent from the provided material. This substantially limits verification of quantitative claims, statistical analyses, and visual representations of simulation results.

## Reviewer
- **Overall assessment** This manuscript presents a computational study addressing a timely and important question in gene regulation: how transcriptional condensates modulate enhancer-promoter communication across genomic distances. The authors employ a coarse-grained polymer model with explicit TF beads capable of phase separation, and systematically vary TF concentration and interaction strength to map E-P contact probability across six genomic separations. The central claim of a "golden mean" optimum in TF condensation is biologically plausible and consistent with emerging experimental evidence. However, the manuscript has several significant issues that must be addressed before the case is fully established. First, the abstraction of "TF" as a single generalized unit, while acknowledged, raises questions about the specificity of the conclusions. Second, the thermodynamic analysis and the proposed bridging-versus-competition mechanism require more rigorous validation. Third, the absence of any experimental validation or connection to quantitative experimental data weakens the translational relevance of the claims. The writing is generally clear, but some methodological details are underspecified, and the relationship between the simulation parameters and in vivo conditions is not adequately discussed.

- **Who would be interested in the results, and why** Researchers in gene regulation, transcriptional control, chromatin organization, and phase separation biology would find these results relevant. The work provides a theoretical framework for understanding how condensate properties might be tuned for optimal gene activation, which is of interest to those studying developmental biology, disease mechanisms involving transcriptional dysregulation, and synthetic biology applications. The methodological approach may also appeal to computational biophysicists working on polymer models of chromatin.

- **Major strengths**
  1. The study addresses a fundamental and timely question in transcriptional regulation with clear biological relevance.
  2. The systematic parameter sweep across genomic distances and TF condensation strengths is thorough and well-designed.
  3. The identification of a nonmonotonic "golden mean" relationship between TF condensation and E-P communication is a novel and testable prediction.
  4. The thermodynamic analysis provides mechanistic insight into the observed behavior.
  5. The authors acknowledge limitations of their model and discuss alternative mechanisms.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "an optimal level of TF phase separation may possess a golden mean property for promoting E-P communication" and that this is consistently observed across all six genomic distances.
- **Evidence pointer** Fig. 1B, Fig. 1C, SI Appendix Figs. S2-S3 (figures not provided)
- **Concern** The central claim of a "golden mean" optimum rests entirely on the simulation results presented in Fig. 1B. However, the figures are not available for inspection, and the text does not provide quantitative measures of the effect sizes, confidence intervals, or statistical significance of the observed optima. The claim that the optimal combinations align along the linear relation nTF+400ϵTF−800=0 is presented without any statistical assessment of the goodness of fit or the variability across independent simulation runs. Without these quantitative details, it is difficult to assess the robustness of the claimed universal relationship.
- **Why it matters** The "golden mean" claim is the central finding of the manuscript. If the optima are shallow or the linear relationship is not robust across parameter combinations, the conclusion would be substantially weakened. The manuscript's title and significance statement depend critically on this claim being quantitatively well-supported.
- **Resolution test** Provide the actual figures with error bars or confidence intervals for pE-P at each parameter combination. Report the statistical significance of the nonmonotonicity (e.g., comparison against a null model of monotonic increase). Provide a quantitative assessment of how well the linear relationship nTF+400ϵTF−800=0 fits the optimal parameter combinations, including residuals and variability across independent simulation batches.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** The authors model "TF" as a single generalized transcriptional regulatory unit that "collectively captures the functions of TFs that bind enhancers, RNA Polymerase II that localizes to promoters, and coactivators such as MED1."
- **Evidence pointer** Results section "E-P Communication with Varying Genomic Distances and Degrees of TF Phase Separation"; Materials and Methods
- **Concern** The abstraction of all transcriptional regulators into a single bead type is a significant simplification. Real systems involve multiple distinct factors with different binding specificities, stoichiometries, and interaction partners. The authors acknowledge this simplification but do not adequately justify why a single generalized unit is sufficient to capture the essential physics of E-P communication. The claim that this abstraction is "consistent with previous modeling approaches" does not address whether the specific conclusions about the golden mean and the bridging-versus-competition mechanism are robust to the inclusion of multiple TF types with distinct properties.
- **Why it matters** The biological relevance of the findings depends on whether the model captures the essential features of real transcriptional condensates. If the golden mean behavior arises from the specific single-species model rather than being a general property of multicomponent condensates, the conclusions may not transfer to biological systems. The bridging-versus-competition mechanism is proposed as a general principle, but it may be an artifact of the simplified model.
- **Resolution test** Discuss how the conclusions would be affected by including multiple TF types with different binding affinities for enhancers versus promoters. Provide evidence from the literature or preliminary simulations that the golden mean behavior is robust to model complexity. Alternatively, clearly state the conditions under which the single-species model is expected to be valid.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** External validity
- **Claim pointer** The authors state that "the minimum slope of 0.80 observed for MFPT as a function of LE-P (Fig. 3) agrees well with the experimental measurement of 0.7±0.2 (33)" and use this agreement to support the biological relevance of their model.
- **Evidence pointer** Fig. 3, reference (33)
- **Concern** The comparison between the simulated scaling exponent and the experimental measurement is presented as a validation of the model, but the text does not provide details on how the experimental value was obtained, what system was studied, or whether the comparison is appropriate. The experimental measurement of 0.7±0.2 presumably comes from a specific biological system with specific properties, and it is not clear that the simulation parameters correspond to that system. The agreement could be coincidental.
- **Why it matters** The claim of agreement with experimental data is used to support the biological relevance of the model. If the comparison is not rigorous, this support is weakened. The manuscript would benefit from a more careful discussion of what the agreement means and what conditions would be required for a meaningful comparison.
- **Resolution test** Provide more details about the experimental system in reference (33) and justify why the simulation parameters are appropriate for comparison. Discuss the range of scaling exponents that would be consistent with the experimental measurement and whether the simulated values fall within this range. If the comparison is not intended as validation, clarify its purpose.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The authors propose that "excessive TF condensation inhibits E-P contact by reducing the stability of the transcriptionally active state, Pon" and that this arises from a shift in the balance between "bridging" and "competing" TF effects.
- **Evidence pointer** Fig. 4C-E, SI Appendix (figures not provided)
- **Concern** The mechanistic interpretation relies on the definitions of bridge TF count (BTC), competing TF count (CTC), and local packing fraction (LPF). However, the text does not provide sufficient detail on how these quantities are defined operationally, how they are calculated from the simulation trajectories, and whether the results are robust to the specific definitions used. The claim that CTC "surpasses BTC" at high condensation levels is presented without quantitative thresholds or statistical assessment.
- **Why it matters** The bridging-versus-competition mechanism is a key contribution of the manuscript. If the operational definitions of BTC and CTC are arbitrary or the results are sensitive to the specific definitions, the mechanistic conclusion is not well-supported. The manuscript would benefit from a sensitivity analysis of these quantities.
- **Resolution test** Provide precise operational definitions of BTC, CTC, and LPF, including the distance cutoffs and criteria used. Show that the qualitative conclusions are robust to reasonable variations in these definitions. Report the statistical significance of the crossover point where CTC exceeds BTC.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "E-P Communication with Varying Genomic Distances and Degrees of TF Phase Separation"
- **Evidence pointer** Fig. 1A
- **Issue** The notation of negative genomic distances (LE-P=−60, −200, −400 kb) is confusing. The authors explain that this is due to the spatial similarity of the looped configuration, but the rationale is not immediately clear to the reader.
- **Required correction** Provide a clearer explanation of why negative distances are used, perhaps with a schematic in Fig. 1A that explicitly shows the relationship between the linear genomic distance and the effective spatial distance in the looped configuration.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and Methods section "Quantifying E-P-Mediated TF Condensate Size and Its Relationship with pE-P"
- **Evidence pointer** Materials and Methods
- **Issue** The choice of DBSCAN parameters (Nmin=5, δ=3σ) is stated but not justified. The sensitivity of the results to these parameters is not discussed.
- **Required correction** Provide a brief justification for the chosen parameters and, if possible, a sensitivity analysis showing that the qualitative conclusions are robust to reasonable variations in Nmin and δ.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results section "Genomic Distance Dependence of E-P Contact Kinetics Weakens As TF Phase Separation Strengthens"
- **Evidence pointer** Fig. 3
- **Issue** The text states that "the MFPT exhibits a nonmonotonic dependence on nTF" at ϵTF=1.5kT, but the specific values of nTF at which the minimum occurs are not reported for each LE-P.
- **Required correction** Report the optimal nTF values for each LE-P at ϵTF=1.5kT, or state that the minimum is consistently at nTF=400 if that is the case.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The authors state that "the entropic constraints imposed by genomic distance can be effectively overcome by sufficiently strong transcriptional condensation" but do not discuss the energetic cost of achieving such strong condensation or whether this cost is biologically feasible.
- **Required correction** Add a brief discussion of the potential energetic or material costs of maintaining high levels of TF condensation and whether these costs are accounted for in the model.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods section "Coarse-Grained Chromatin Model and MD Simulations"
- **Evidence pointer** Materials and Methods
- **Issue** The manuscript states that "the two boundary ends of the TAD were connected and fixed in space" but does not specify the exact geometry of the connection (e.g., are the ends connected by a harmonic spring, or is the polymer a ring?). This affects the interpretation of the looped configuration.
- **Required correction** Clarify the exact implementation of the boundary conditions, including the functional form of the connection potential and its parameters.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The manuscript cites experimental studies on the negative effects of excessive TF condensation (refs 38-41) but does not discuss whether the specific mechanism proposed here (competitive binding) has been observed experimentally.
- **Required correction** Add a brief discussion of whether the bridging-versus-competition mechanism is supported by any experimental evidence, or clearly state that this is a novel prediction of the model.

## Risk / unsupported claims
- The claim that the optimal TF condensation level follows the linear relation nTF+400ϵTF−800=0 across all genomic distances is presented without statistical assessment. This is a strong claim that requires quantitative support.
- The claim that the scaling exponent of MFPT with genomic distance reaches 0.80, close to the experimental value of 0.7±0.2, is presented as agreement but the comparison is not rigorously justified.
- The claim that "the entropic constraints imposed by genomic distance can be effectively overcome by sufficiently strong transcriptional condensation" is a broad generalization from simulation data without experimental validation.
- The mechanistic interpretation involving bridging and competing TF effects is plausible but is based on operational definitions (BTC, CTC) that are not fully specified or validated.
- The claim that the model "reconciles the stochastic nature of chromatin dynamics with the precision demands of developmental transcription" is speculative and goes beyond the simulation results presented.
- The relationship between the simulation parameters (e.g., ϵTF in kT units) and in vivo conditions is not established, making it difficult to assess the biological relevance of the specific parameter ranges explored.