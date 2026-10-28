## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided by the author.
- **Assessment boundary** Scientific content, methodological soundness, interpretation of results, and alignment with claims. No assessment of formatting, grammar, or editorial fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors use a minimalist coarse-grained model to show that DNA length, flexibility, and heterotypic protein–DNA interaction strength control condensate morphology, internal organization, and protein dynamics. They report multiphasic (core–shell) condensate architectures and up to five distinct protein diffusion modes under strong heterotypic interactions.
- **Visible evidence base** Main text figures (referenced as Figure A–D, Figure 1–4, Figure S1–S14 in supplementary), simulation methods, and analysis descriptions. No raw data, simulation trajectories, or parameter files were provided.
- **Missing materials affecting confidence** Simulation parameter files, force field details, full figure panels with axis labels and legends, convergence criteria, error analysis methodology, and supplementary figures S1–S14 were not included in the provided material. This limits quantitative verification of several claims.

## Reviewer
- **Overall assessment** The manuscript presents a systematic computational study of protein–DNA condensate organization using a minimal coarse-grained model. The work addresses a timely question and produces several interesting observations, particularly the multiphasic core–shell organization and the identification of multiple protein diffusion modes. However, the evidence provided is insufficient to fully establish the mechanistic claims. Key quantitative details, convergence checks, and a more rigorous connection between simulation observables and experimental predictions are needed. The manuscript is promising but requires substantial revision and additional analysis before the case is established.
- **Who would be interested in the results, and why** Researchers studying biomolecular condensates, phase separation, chromatin organization, and genome regulation. The work is also relevant to computational biophysicists developing coarse-grained models for nucleic acid–protein systems. The findings on DNA-mediated multiphasic organization and heterogeneous protein dynamics could inform experimental design in FRAP and single-molecule tracking studies.
- **Major strengths** 1) The study addresses an important and under-explored question: how DNA physical properties modulate the internal architecture and dynamics of protein–DNA condensates. 2) The minimal model is computationally efficient and allows broad parameter sweeps. 3) The identification of up to five distinct protein diffusion modes is a novel and potentially impactful observation. 4) The authors connect their findings to experimental systems (HP1α, FUS, protamine) and discuss biological implications.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative validation of the model), R1-M2 (insufficient evidence for the multiphasic claim), R1-M3 (inadequate support for the five diffusion modes), R1-M4 (missing convergence and equilibration analysis).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate to high. The application of a minimal model to dissect DNA-driven multiphasic organization and differential dynamics is a fresh angle, though related work exists on protein–RNA condensates and chromatin models.  
  *Scientific importance*: Moderate. The findings could inform understanding of chromatin condensate function, but the model's simplicity limits direct biological extrapolation.  
  *Interdisciplinary readership*: Moderate. The topic bridges biophysics, molecular biology, and computational biology, but the presentation is heavily simulation-focused and may not fully engage experimentalists.  
  *Technical soundness*: Currently insufficient. Several claims lack quantitative support, and the analysis methods are not fully described or validated.  
  *Readability for nonspecialists*: Acceptable but could be improved. The introduction and conclusions are clear, but the results section assumes familiarity with coarse-grained simulation conventions.
- **Recommendation posture** Supportive if technical concerns are resolved. The core ideas are interesting and potentially publishable, but the current evidence base does not fully establish the mechanistic claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their model "successfully recapitulates key qualitative features observed experimentally" and that the chosen interaction strengths are "physically reasonable for biological systems."
- **Evidence pointer** Methods section, Nonbonded Interactions; Figure S1 (referenced, not provided)
- **Concern** The validation of the model against experimental data is not presented in the provided material. The authors reference Figure S1 for dissociation constant calculations, but the figure and the calculation details are not available. Without this, the claim that the model parameters are biologically relevant cannot be assessed. Additionally, the comparison to experimental systems (FUS, HP1α) is qualitative and not systematically quantified.
- **Why it matters** The entire study rests on the assumption that the coarse-grained model captures essential physics. If the interaction strengths are not calibrated to realistic values, the phase behavior and dynamics reported may be artifacts of the parameter choice rather than general principles.
- **Resolution test** Provide Figure S1 and the full calculation details for K D values. Show a quantitative comparison between simulated and experimental K D values, including error bars. If possible, demonstrate that the model reproduces known experimental phase boundaries or condensate properties for at least one system.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that "condensates adopt a multiphasic architecture, characterized by DNA-bound protein-rich cores surrounded by a protein-enriched shell" under strong heterotypic interactions.
- **Evidence pointer** Results section, Multiphasic Nature of Protein–DNA Condensates; Figure 4 (referenced, not fully described)
- **Concern** The evidence for multiphasic organization is described qualitatively. The radial density profile in Figure 4B is said to reveal "two distinct regions," but the fitting procedure (double hyperbolic tangent) is not described in the provided text, and the criteria for distinguishing phases are not defined. It is unclear whether the two regions are thermodynamically distinct phases or simply a continuous density gradient. The authors also do not provide a free energy or interfacial tension analysis to support the phase-in-phase interpretation.
- **Why it matters** Multiphasic organization is a central claim of the paper. If the evidence is only a fitted density profile, the conclusion may be overinterpreted. A more rigorous demonstration of distinct phases is needed.
- **Resolution test** Provide the full radial density profiles with error bars, the fitting procedure, and a statistical test for the presence of two distinct density plateaus. Consider computing a local order parameter or performing a Gibbs dividing surface analysis. Show that the two regions are stable over time and not a transient artifact.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to identify "up to five distinct diffusion modes" of proteins within the condensate, including proteins bound to DNA, confined within the dense phase, or freely diffusing.
- **Evidence pointer** Results section, Differential Protein Dynamics; Figures 5, S11–S14 (referenced, not provided)
- **Concern** The method for decomposing the displacement distribution into multiple Gaussian components is described, but the criteria for choosing the number of components (n) are vague ("until the fit achieves minimal residuals"). The authors do not report the fitted diffusion coefficients, their uncertainties, or the fractional populations for each mode. It is also unclear how the assignment of each mode to a physical interpretation (e.g., DNA-bound vs. confined) is justified. The sensitivity analysis to bin size is mentioned but not shown.
- **Why it matters** The claim of five distinct diffusion modes is a key novel finding. If the decomposition is not robust or the assignment is speculative, the conclusion is not supported.
- **Resolution test** Provide the fitted diffusion coefficients and populations for each mode with uncertainties, for all conditions. Show the residual analysis for n = 3, 4, 5, 6 to justify the choice of n. Provide a validation of the assignment of modes to physical states, e.g., by correlating the slowest mode with direct measurements of protein–DNA contacts in the simulation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the system reached equilibrium" based on monitoring the dilute-phase protein concentration, and that the first 400 ns were discarded as equilibration.
- **Evidence pointer** Results section, Phase Behavior; Figure S2 (referenced, not provided)
- **Concern** The equilibration criterion is based on a single observable (dilute-phase protein concentration). It is not clear whether other order parameters (e.g., cluster size, density profile, energy) have converged. The simulation time of 2 μs may be insufficient for systems with slow dynamics, especially at strong interaction strengths where the condensate may be glassy or gel-like. No autocorrelation analysis or multiple independent runs are reported.
- **Why it matters** If the simulations are not fully equilibrated, the reported phase behavior and dynamics may be biased by initial conditions or non-steady-state effects.
- **Resolution test** Show convergence of multiple observables (e.g., cluster size, density profile, potential energy) over time. Perform at least three independent runs with different initial configurations and report the spread. Consider longer simulations or enhanced sampling for the strongest interaction regimes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, Protein Model
- **Evidence pointer** Methods section, Protein Model
- **Issue** The choice of protein bead diameter (σP = 50 Å) is justified by reference to R g values of TFAM and HP1α, but the source of these values is not cited.
- **Required correction** Add citations for the R g values used and clarify whether these are experimental or computational estimates.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, DNA Model
- **Evidence pointer** Methods section, DNA Model
- **Issue** The persistence length calculation is referenced to the Supporting Information, but the details are not provided in the main text. The relationship between K θ values and persistence length is not shown.
- **Required correction** Provide the persistence length values for each K θ used, either in the main text or by including the relevant supplementary figure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, Role of DNA Length
- **Evidence pointer** Results section, Role of DNA Length; Figure 3 (referenced)
- **Issue** The peak in the R g ratio at 100 bp for λPP = 3.0 and 4.0 is described as "intriguing," but no mechanistic explanation is offered. The authors should discuss possible causes, such as a crossover between bridging and compaction regimes.
- **Required correction** Add a brief discussion of the possible origin of the 100 bp peak, or explicitly state that the mechanism is unresolved.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Differential Protein Dynamics
- **Evidence pointer** Results section, Differential Protein Dynamics
- **Issue** The assignment of diffusion modes to physical states (e.g., "proteins at the interface") is speculative and not directly verified.
- **Required correction** Either provide direct evidence for the assignment (e.g., by tracking individual proteins and correlating their diffusion coefficient with their local environment) or soften the language to indicate that these are plausible interpretations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Conclusions
- **Evidence pointer** Conclusions section
- **Issue** The authors state that the model "can be readily adapted to protein–RNA systems," but no details are given on how the parameters would be adjusted.
- **Required correction** Provide a brief outline of the parameter changes needed for RNA, or remove this claim if it is not substantiated.

## Risk / unsupported claims
- The claim that the model "successfully recapitulates key qualitative features observed experimentally" is not supported by the provided material, as the relevant comparison (Figure S1) is not included.
- The claim of "up to five distinct diffusion modes" is not fully supported without the fitted parameters, uncertainties, and model selection criteria.
- The claim of "multiphasic organization" as a distinct thermodynamic state is not rigorously established; the evidence is limited to a fitted density profile.
- The statement that "DNA acts as a scaffold for recruiting proteins" is a reasonable interpretation but is not directly proven by the data presented.
- The claim that "longer DNA chains and more flexible DNA molecules undergo a higher degree of compaction" is only partially supported; the data for the longest chains (1000 bp) and the most flexible cases are not shown in the provided text.
- The biological implications discussed (e.g., relevance to transcriptional condensates) are speculative and not directly tested in the model.