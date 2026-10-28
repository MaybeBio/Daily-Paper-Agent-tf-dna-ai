## Review setup
- **Input scope** Full manuscript text (ArXiv preprint, 2024)
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the provided text; no external validation or replication attempted
- **Shared manuscript claim summary** The authors propose that a long compressible polymer coupled to a phase-separating protein mixture undergoes a generalized prewetting transition, where polymer collapse and local liquid droplet formation occur coincidentally, even when each transition is unstable in isolation. They support this with lattice Monte-Carlo simulations and mean-field theory, and discuss implications for chromatin organization and transcriptional regulation.
- **Visible evidence base** Monte-Carlo simulation results (Figs. 1, 2, 4, 5), mean-field theory predictions (Fig. 3), and qualitative comparisons between theory and simulation
- **Missing materials affecting confidence** Full simulation parameters (e.g., exact values of Jbulk, Jint, μb, vp used in each figure), error bars or statistical uncertainties on simulation data, finite-size scaling analysis, phase diagram coordinates in Fig. 2E/F, and details of the multi-component polymer simulation (e.g., segment length distribution, equilibration times)

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially significant idea: coupling polymer collapse to bulk phase separation via a prewetting-like mechanism. The combination of mean-field theory and lattice simulations is appropriate and generally well-executed. However, the evidence as presented is incomplete in several key respects, particularly regarding quantitative validation of the theory against simulations, finite-size effects, and the biological relevance of the parameter regimes explored. The claims of novelty and biological applicability are plausible but not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers in biophysics, soft matter physics, and chromatin biology. The work addresses fundamental questions about polymer phase behavior in multicomponent environments, with direct relevance to understanding transcriptional condensates, heterochromatin organization, and the role of phase separation in gene regulation. The prewetting framework could also interest theorists working on surface phase transitions and polymer physics.
- **Major Strengths**  
  - The conceptual framing of polymer collapse as a prewetting transition is novel and potentially unifying.  
  - The combination of mean-field theory and lattice simulations provides complementary perspectives.  
  - The multi-component polymer extension (Fig. 5) adds biological relevance and demonstrates a pathway to sequence-specific regulation.  
  - The discussion of biological implications is thoughtful and appropriately speculative.
- **Major Concerns**  
  - R1-M1: Quantitative agreement between theory and simulation is not demonstrated.  
  - R1-M2: Finite-size effects and their impact on the claimed phase transitions are not addressed.  
  - R1-M3: The biological relevance of the parameter regimes is not established.  
  - R1-M4: The multi-component polymer results are presented without sufficient methodological detail.
- **Minor Comments**  
  - R1-m1: The phase diagram in Fig. 2E/F is described but not fully labeled or explained.  
  - R1-m2: The relationship between the "Generalized Prewet - Collapsed" phase and classical prewetting is not rigorously defined.  
  - R1-m3: The discussion of squelching and heterochromatin is speculative and could be better tied to specific model predictions.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M4
- **Assessment against Nature-style criteria**  
  - **Originality** High. The prewetting framework for polymer-protein co-condensation is a fresh perspective.  
  - **Scientific importance** Moderate to high. If validated, the results could influence how chromatin phase behavior is understood, but the current evidence does not yet establish broad significance.  
  - **Interdisciplinary readership** Moderate. The work bridges polymer physics and cell biology, but the presentation may be too technical for a general biology audience without additional context.  
  - **Technical soundness** Moderate. The methods are appropriate, but the lack of quantitative validation and finite-size analysis weakens the technical case.  
  - **Readability for nonspecialists** Moderate. The abstract and discussion are accessible, but the theory and simulation sections assume significant background.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the manuscript currently does not provide sufficient quantitative evidence to fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Quantitative validation  
- **Claim pointer** The authors claim that "Monte-Carlo simulations support theoretical predictions" (Section: Monte-Carlo simulations support theoretical predictions).  
- **Evidence pointer** Figure 4A/B, Section: Monte-Carlo simulations support theoretical predictions  
- **Concern** The manuscript states that simulations "support" the theory, but no quantitative comparison (e.g., fitting of phase boundaries, scaling exponents, or order parameter values) is provided. The figures show qualitative trends, but it is unclear whether the theory quantitatively predicts the simulation results or merely captures the same qualitative behavior.  
- **Why it matters** Without quantitative validation, the claim that the theory captures the essential physics is not established. This is critical for the manuscript's central thesis that the prewetting mechanism is robust and general.  
- **Resolution test** Provide a quantitative comparison between theory and simulation, such as overlaying theoretical phase boundaries on simulation data, or reporting the deviation between predicted and observed order parameters across a range of parameters.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Finite-size effects  
- **Claim pointer** The authors claim that the observed transitions are "abrupt" or "continuous" (Section: Monte-Carlo simulations support theoretical predictions).  
- **Evidence pointer** Figure 4A/B, Section: Monte-Carlo simulations support theoretical predictions  
- **Concern** The simulations are performed on a lattice of linear dimension L = 64, and the polymer length is capped at Nmax = 1500. The manuscript does not discuss how finite-size effects might influence the sharpness or location of the claimed transitions. For a phase transition, finite-size scaling analysis is typically required to distinguish genuine transitions from finite-size artifacts.  
- **Why it matters** The distinction between abrupt and continuous transitions is a central claim. If the observed behavior is a finite-size artifact, the conclusions about the phase diagram would be incorrect.  
- **Resolution test** Perform simulations at multiple system sizes (e.g., L = 32, 64, 128) and polymer lengths, and show that the transition sharpens or scales as expected for a true phase transition.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Biological relevance  
- **Claim pointer** The authors state that "these phases could be stable even in regimes where both polymer collapse and coexisting liquid phases are unstable in isolation" (Abstract) and discuss implications for transcriptional regulation (Discussion).  
- **Evidence pointer** Abstract, Discussion  
- **Concern** The parameter regimes explored in the simulations and theory are not mapped to biologically relevant values (e.g., protein concentrations, DNA lengths, interaction energies). Without such a mapping, it is unclear whether the predicted prewetting phases are accessible in vivo.  
- **Why it matters** The biological significance of the work depends on whether the predicted phenomena occur under physiological conditions. If the required parameters are far from biological ranges, the relevance to chromatin biology is limited.  
- **Resolution test** Provide estimates of the model parameters in biological units (e.g., using known protein-DNA interaction energies and nuclear concentrations) and discuss whether the predicted phases are plausible in vivo.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological detail  
- **Claim pointer** The authors claim that "changes in the concentration of bulk components can lead to changes in three-dimensional polymer structure" for multi-component polymers (Abstract).  
- **Evidence pointer** Figure 5, Section: Multi-component polymers, Materials & Methods  
- **Concern** The multi-component polymer simulations are described only briefly. Key details are missing, including how the segment length distribution is maintained (the Δ parameter is mentioned but not fully explained), how the two monomer types are distributed along the polymer, and how the results depend on these choices.  
- **Why it matters** The multi-component results are a key extension of the work and are used to argue for biological relevance. Without sufficient methodological detail, these results cannot be reproduced or fully evaluated.  
- **Resolution test** Provide a complete description of the multi-component simulation protocol, including the initialization, the segment length constraint, and the range of parameters tested.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Figure 2E/F  
- **Evidence pointer** Figure 2E/F, Section: Bulk Molecules Phase Separate and Modify the Polymer Phase Diagram  
- **Issue** The phase diagram in Fig. 2E/F is described in the text but the axes, labels, and regions are not fully explained. It is difficult to interpret the diagram without additional annotation.  
- **Required correction** Add clear axis labels, legend, and a brief description of the phases in the figure caption.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "Generalized Prewet - Collapsed" phase  
- **Evidence pointer** Section: Bulk Molecules Phase Separate and Modify the Polymer Phase Diagram  
- **Issue** The term "Generalized Prewet - Collapsed" is introduced but not rigorously defined. It is unclear how this phase differs from a simple collapsed polymer in a dense phase.  
- **Required correction** Provide a formal definition of the phase, including the order parameters that distinguish it from other phases.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Speculation  
- **Affected element** Discussion of squelching and heterochromatin  
- **Evidence pointer** Discussion  
- **Issue** The discussion of squelching and heterochromatin is speculative and not directly tied to the model's predictions.  
- **Required correction** Either provide a more explicit connection between the model and these biological phenomena, or clearly label these as speculative extensions.

## Risk / unsupported claims
- The claim that "these phases can be stable even in regimes where both polymer collapse and coexisting liquid phases are unstable in isolation" is supported by simulation and theory, but the quantitative agreement is not demonstrated (R1-M1).
- The claim that "changes in the concentration of bulk components can lead to changes in three-dimensional polymer structure" for multi-component polymers is not fully supported due to missing methodological details (R1-M4).
- The biological relevance of the predicted phases is asserted but not established through parameter mapping (R1-M3).
- The phase diagram in Fig. 2E/F is not fully interpretable from the provided text and figure description (R1-m1).