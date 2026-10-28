## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, computational methods, and acknowledgments. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive validity of the simulation study as presented. No assessment of experimental verification, which is outside the scope of this computational work.
- **Shared manuscript claim summary** The authors propose that highly charged Hero11 proteins antagonize TDP-43-LCD biomolecular condensation through electrostatic repulsion between Hero11 molecules, while attractive Hero11–TDP-43-LCD interactions increase the saturation concentration and alter conformational dynamics. Three mechanisms are proposed: (i) dense-phase loosening via Hero11–Hero11 repulsion, (ii) dilute-phase stabilization via attractive heterotypic interactions, and (iii) surface accumulation preventing condensate fusion.
- **Visible evidence base** Multiscale MD simulations: all-atom CHARMM36m simulations of single Hero11 chains (~1 μs), CG simulations using HPS/HPS-Urry potentials with AICG2+ for helical restraints, slab simulations of 100-chain homotypic and heterotypic systems, phase diagram construction, contact analysis, Rg analysis, and MSD-based diffusion measurements.
- **Missing materials affecting confidence** Supplementary figures (S1–S19), Table S1 (sequences), and the Supporting Information Methods section are referenced but not provided. These are essential for verifying simulation details, convergence criteria, and the full set of results.

## Reviewer
- **Overall assessment** This is a carefully executed computational study addressing an important and timely question: how highly charged "Hero" proteins protect clients from pathological aggregation. The multiscale approach combining all-atom and CG simulations is appropriate, and the systematic comparison of wild-type and charge-reduced mutants provides a clear causal test of the electrostatic repulsion hypothesis. The proposed mechanisms are plausible and mechanistically informative. However, the study is entirely computational, and the connection to experimental observables is largely indirect. The manuscript would be strengthened by clearer articulation of testable predictions and by addressing the limitations of the CG model in quantitative terms. The writing is generally clear, though some methodological details are deferred to the Supporting Information, which limits full assessment.
- **Who would be interested in the results, and why** Researchers in the fields of biomolecular condensates, phase separation, intrinsically disordered proteins, and neurodegeneration. The study provides mechanistic hypotheses for how charged IDPs regulate condensation, which is relevant to understanding cellular organization and designing therapeutic strategies against protein aggregation diseases. Computational biophysicists developing and applying CG models to phase-separating systems will also find the methodological framework of interest.
- **Major strengths**
  1. The study addresses a significant open question: the molecular mechanism of Hero protein anti-aggregation function, which has been experimentally characterized but not mechanistically explained.
  2. The multiscale approach (all-atom to CG) is well suited to the problem, and the use of charge-reduced mutants provides a clean computational "knockout" experiment.
  3. The phase diagram analysis and the distinction between dense- and dilute-phase effects are rigorous and provide a quantitative framework for understanding the regulatory mechanism.
  4. The authors are appropriately cautious about the limitations of their models, particularly regarding the secondary structure of Hero11 and the applicability of CG potentials at low temperatures.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that Hero11–Hero11 repulsive interactions "loosen" the TDP-43-LCD condensate and increase TDP-43-LCD diffusion in the dense phase.
  - **Evidence pointer** Figure 5B, 5D, 5F; location not provided
  - **Concern** The dense-phase diffusion increase is reported as a function of Hero11 concentration, but the statistical significance of these differences is not established. The manuscript does not report error bars, replicate simulations, or statistical tests for the MSD and contact number comparisons. Given that the differences in Rg are small (31.2 to 31.5 Å), it is unclear whether the reported effects are robust or within simulation noise.
  - **Why it matters** The central mechanistic claim that repulsive Hero11–Hero11 interactions physically loosen the condensate rests on these quantitative comparisons. Without statistical rigor, the conclusion that the effect is due to electrostatic repulsion rather than trivial dilution or finite-size effects is not fully supported.
  - **Resolution test** Provide replicate simulations (at least 3 independent runs per condition) with standard errors or confidence intervals for all reported quantities (density, contact number, Rg, MSD). Perform a statistical test (e.g., t-test or bootstrap) comparing heterotypic conditions to the homotypic control. If the differences are not statistically significant, temper the corresponding claims.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Model validation
  - **Claim pointer** The claim that the CG model with HPS/HPS-Urry potentials and AICG2+ restraints provides quantitatively reliable predictions of phase behavior, including the critical temperature shift induced by Hero11.
  - **Evidence pointer** Figures 2C, 4E, 5A; location not provided
  - **Concern** The CG model is parameterized for IDPs, but the authors apply it at temperatures down to 200 K and use it to extract critical temperatures. The HPS model was not designed for such low temperatures, and the authors acknowledge this concern but do not address it quantitatively. The phase diagram for TDP-43-LCD is compared to a previous study, but no direct validation against experimental phase behavior (e.g., saturation concentrations from in vitro assays) is provided. The predicted Tc values are therefore of unknown quantitative accuracy.
  - **Why it matters** The quantitative claims about the magnitude of Tc reduction (e.g., from ~310 K to ~295 K) and the density changes in the condensate depend on the accuracy of the CG model. If the model is not quantitatively reliable at these conditions, the specific numbers are not meaningful, and only qualitative trends can be claimed.
  - **Resolution test** Validate the CG model against available experimental data for TDP-43-LCD phase behavior (e.g., saturation concentration as a function of temperature, if available). Alternatively, perform all-atom simulations of a small system to check the CG predictions at a representative state point. If quantitative validation is not possible, explicitly state that the results are qualitative and avoid overinterpreting specific Tc values.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Completeness of evidence
  - **Claim pointer** The claim that Hero11 with a higher fraction of disordered region tends to assemble on the surface of condensates, contributing to antifusion.
  - **Evidence pointer** Figure 6; location not provided
  - **Concern** The surface accumulation and antifusion mechanism is presented as a third possible mechanism, but the evidence is limited to concentration profiles along the z-axis in slab simulations. The authors do not directly simulate two condensates approaching each other, nor do they measure the fusion barrier or the interfacial tension. The claim that surface accumulation "can contribute to avoiding their fusion" is therefore speculative and not directly tested.
  - **Why it matters** The antifusion mechanism is a distinct and potentially important function of Hero proteins, but the current evidence does not directly support it. Overstating this mechanism could mislead readers about the strength of the evidence.
  - **Resolution test** Either (a) perform simulations of two condensates with and without Hero11 to directly test the fusion barrier, or (b) explicitly label this mechanism as speculative and propose experimental tests (e.g., FRAP or fluorescence microscopy of condensate fusion in the presence of Hero11) to validate it.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract, Introduction
  - **Issue** The term "Hero11" is used without defining what "Hero" stands for beyond "heat-resistant obscure." The abstract states "Hero proteins" but does not explain the acronym or the protein family context.
  - **Required correction** Define "Hero" and provide a brief context for the protein family in the Introduction, including the original experimental reference.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods
  - **Evidence pointer** Computational Methods section
  - **Issue** The manuscript states that "more detailed information on the atomistic simulations can be found in the Supporting Information Methods section," but this section is not provided. Key parameters such as the number of ions, salt concentration, and equilibration protocol are not fully specified in the main text.
  - **Required correction** Provide the full simulation details in the main text or ensure the Supporting Information is accessible to reviewers and readers. At minimum, specify the salt concentration, ion placement, and equilibration times in the main text.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of entropy
  - **Evidence pointer** Discussion section
  - **Issue** The authors discuss conformational entropy changes (Figure 5E) but do not directly compute entropy. The inference that larger sRg implies higher conformational entropy is reasonable but indirect, and the connection to the free energy of phase separation is not quantified.
  - **Required correction** Clarify that sRg is a proxy for conformational fluctuations and not a direct measure of entropy. If possible, compute the conformational entropy difference between phases using established methods (e.g., quasi-harmonic analysis) or temper the language accordingly.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Generalizability
  - **Affected element** Discussion of other Hero proteins
  - **Evidence pointer** Discussion section
  - **Issue** The authors speculate that the mechanism applies to other Hero proteins based on their high net charge, but no simulations or analysis of other Hero proteins are presented.
  - **Required correction** Clearly state that this is a hypothesis and suggest how it could be tested computationally or experimentally for other Hero family members.

## Risk / unsupported claims
- The claim that Hero11–Hero11 repulsive interactions "loosen" the condensate and increase TDP-43-LCD diffusion is not statistically supported due to missing error analysis and replicate simulations.
- The quantitative values of critical temperatures (Tc) and their shifts are not validated against experimental data and may be unreliable given the CG model's limitations at low temperatures.
- The antifusion mechanism (mechanism iii) is speculative and not directly tested by the simulations presented.
- The claim that the mechanism generalizes to other Hero proteins is a hypothesis without direct evidence.
- The inference from sRg to conformational entropy is indirect and not quantified.
- The statement that "Hero11 permeates into the condensate" is supported by the simulations, but the timescale and reversibility of this permeation are not characterized, and the biological relevance of the simulation timescale is not discussed.