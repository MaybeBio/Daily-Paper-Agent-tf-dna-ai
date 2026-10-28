## Review setup
- **Input scope** Full manuscript text (main text only; SI Appendix referenced but not provided)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and internal consistency of the presented results; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors use AWSEM-3SPN.2C coarse-grained simulations to predict the dimeric structure of human estrogen receptor α (hERα) bound to DNA, and to characterize domain–domain communication in antagonist-bound, agonist-bound, and agonist-plus-coactivator states. They propose a "marionette mechanism" whereby ligand-induced conformational changes in the LBDs propagate through intrinsically disordered hinge domains to modulate DBD–DNA binding.
- **Visible evidence base** Main text figures (Figs. 1–6), supplementary figure/table references (SI Appendix Figs. S1–S21, Tables S1–S4), simulation methodology description, comparison to experimental SAXS data and binding affinity measurements
- **Missing materials affecting confidence** SI Appendix (all supplementary figures, tables, and detailed methods), Movies S1–S13, experimental SAXS data files, simulation input files and analysis codes (deposited on GitHub but not reviewed), PDB structures used as templates

## Reviewer
- **Overall assessment** This manuscript presents a computational study of hERα dynamics using a well-established coarse-grained force field (AWSEM-3SPN.2C). The central claim, that domain–domain communication in agonist-bound hERα occurs through a "marionette mechanism" involving the intrinsically disordered hinge domains, is potentially interesting and could have implications for understanding nuclear receptor signaling. However, the evidence presented in the main text is largely qualitative, relying on visual inspection of free energy surfaces, frustration patterns, and principal component analyses. The manuscript would benefit from more quantitative validation of the predicted structures and clearer statistical treatment of the simulation results. The connection between the proposed mechanism and experimentally observed functional differences between antagonist and agonist responses is suggestive but not fully established. The writing is generally clear, though some mechanistic claims appear to exceed what the presented data can support.
- **Who would be interested in the results, and why** Researchers in computational biophysics and molecular dynamics, particularly those studying multidomain proteins and intrinsically disordered regions; structural biologists studying nuclear receptors, especially estrogen receptor signaling; and potentially drug discovery groups interested in understanding how ligand binding modulates receptor function at a mechanistic level.
- **Major strengths** 1) The study addresses a significant and long-standing question in the nuclear receptor field: how ligand binding in the LBD communicates to the DBD through disordered linkers. 2) The use of a physically realistic coarse-grained model (AWSEM-3SPN.2C) that includes both protein and DNA is appropriate for studying large multidomain complexes. 3) The validation against experimental SAXS data and binding affinity measurements provides some confidence in the predicted structures. 4) The systematic comparison of antagonist-bound, agonist-bound, and agonist-plus-coactivator states is a logical approach to dissecting ligand-specific effects. 5) The proposed "marionette mechanism" is a memorable and potentially useful conceptual framework.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the predicted hERα dimeric structure "agrees well with experiments at the structural and energetic levels" based on a χ² value of 1.215 against SAXS data and a binding free energy of −11.14 kcal/mol.
  - **Evidence pointer** Fig. 1C, SI Appendix Fig. S1, SI Appendix Fig. S3
  - **Concern** The χ² value of 1.215 is presented as evidence of good agreement with SAXS data, but the authors do not provide context for what constitutes an acceptable χ² for this system. The comparison to the Huang et al. model (χ² = 1.339) shows only a marginal improvement. More critically, the binding free energy calculation appears to be a single value without error bars or a description of how the free energy profile was computed and how the uncertainty was estimated. The authors state the experimental range is (−10.03 to −11.93) kcal/mol, but it is unclear whether this range represents experimental uncertainty or variation across different experimental conditions. Without error estimates on the computed value, the agreement could be fortuitous.
  - **Why it matters** The structural validation is foundational for all subsequent claims about domain–domain communication. If the predicted structure is not reliably validated, the mechanistic conclusions drawn from simulations starting from this structure are compromised.
  - **Resolution test** Provide error bars or confidence intervals for the computed binding free energy. Report the χ² value for multiple independent simulation runs or structural ensembles. Discuss what range of χ² values would be considered acceptable for a coarse-grained model of this size. If possible, compare the predicted structure to additional experimental data (e.g., cross-linking mass spectrometry, FRET) that could independently validate the domain arrangement.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The authors claim that "domain–domain communication exists only through the binding process of agonist-bound hERα" and that the differences in free energy landscapes between antagonist-bound, agonist-bound, and agonist-plus-coactivator states reveal distinct mechanisms of domain communication.
  - **Evidence pointer** Fig. 3, SI Appendix Figs. S4–S11
  - **Concern** The free energy landscapes in Fig. 3 are projected onto two collective variables (electrostatic interactions between DBDs and DNA, and between hinge domains and DNA). The authors identify different numbers of basins for each state and interpret these as evidence for different communication mechanisms. However, the statistical significance of these basins is not established. The manuscript does not report the statistical uncertainty in the free energy surfaces, the number of umbrella sampling windows used, the convergence criteria, or the total simulation time per window. The claim that the apo form "incorporates the features of the antagonist-bound and agonist-bound forms" is based on comparing the largest PC of the apo form to the largest PC of the antagonist-bound form and the 5th PC of the apo form to the largest PC of the agonist-bound form, which is a weak basis for such a conclusion.
  - **Why it matters** The central mechanistic claim of the paper, that agonist binding enables a unique mode of domain–domain communication, rests on the differences between the free energy landscapes of the different states. If these differences are not statistically robust, the conclusion is not supported.
  - **Resolution test** Provide convergence analysis for the free energy surfaces (e.g., block averaging, multiple independent umbrella sampling runs). Report the number of umbrella sampling windows, the force constants, and the total simulation time. Quantify the uncertainty in the free energy differences between basins. Consider using additional collective variables or dimensionality reduction methods to confirm that the identified basins are robust features of the landscape.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors propose a "marionette mechanism" in which "the motions of LBDs transfer their changes to the hinge domains which shorten and thereby transfer information to the DBDs finally," and that this mechanism is supported by the free energy landscapes constructed using "the averaged length of the hinge domains and the number of contacts between DBDs and DNA as coupled collective coordinates."
  - **Evidence pointer** Fig. 5, SI Appendix Figs. S20, Movies S11–S13
  - **Concern** The "marionette mechanism" is presented as a novel conceptual framework, but the evidence for it is largely descriptive. The free energy landscape in Fig. 5A shows three basins that differ in hinge length and DBD–DNA contacts, but the authors do not demonstrate a causal relationship between hinge length changes and DBD–DNA binding. The claim that "the hinge controls DNA-binding activity" is an interpretation of correlation, not a demonstration of causation. The authors also do not address whether the observed hinge length changes are within the range of thermal fluctuations expected for intrinsically disordered regions, or whether they represent functionally significant conformational changes. The comparison to puppetry, while evocative, does not add mechanistic insight beyond what is already captured by the free energy landscape.
  - **Why it matters** The "marionette mechanism" is the central conceptual contribution of the paper. If the causal relationship between hinge dynamics and DBD–DNA binding is not established, the mechanism remains a descriptive observation rather than a validated model.
  - **Resolution test** Perform perturbation analyses (e.g., mutations that alter hinge length or charge) and show that these perturbations specifically affect DBD–DNA binding in the predicted manner. Use time-correlation analysis to demonstrate that hinge length fluctuations precede DBD–DNA contact changes. Compare the free energy barriers between basins to thermal energy (kBT) to assess whether the transitions are biologically accessible.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The authors state that "the simulations were carried out using the AWSEM-3SPN.2C forcefield for protein–DNA complexes in the LAMMPS open-source software package" and that input files and analysis codes are deposited on GitHub.
  - **Evidence pointer** Methods section, Data Availability section
  - **Concern** The methods description is extremely brief and defers all details to the SI Appendix, which was not provided for review. The authors mention "template and coevolutionary information" and "AWSEM-Suite model" but do not specify the exact version of the force field, the parameter settings, the simulation protocol (e.g., integration time step, thermostat, equilibration procedure), or the system setup (e.g., box size, salt concentration, number of water ions). The GitHub repository link is provided, but the contents were not reviewed.
  - **Why it matters** Reproducibility is a core requirement for computational studies. Without sufficient methodological detail, other researchers cannot replicate the simulations or assess the robustness of the results.
  - **Resolution test** Provide a complete description of the simulation protocol in the main text or ensure the SI Appendix contains all necessary details. Verify that the GitHub repository contains all input files, parameter files, and analysis scripts needed to reproduce the simulations and analyses. Consider depositing the data in a permanent repository (e.g., Zenodo) with a DOI.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Fig. 2 description
  - **Evidence pointer** Fig. 2
  - **Issue** The description of Fig. 2 states that "the largest PC of antagonist-bound hERα" shows "large motions of one of the DNA-binding domains but relatively small motions of the other DBD." It is unclear whether the asymmetry in DBD motions is a consequence of the intrinsic asymmetry of the dimer (which the authors discuss later) or an artifact of the PCA projection.
  - **Required correction** Clarify whether the asymmetric DBD motions in the antagonist-bound state are expected given the asymmetric domain–domain interactions described in the structural analysis, or whether they represent a distinct dynamical feature.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of apo hERα
  - **Evidence pointer** SI Appendix Fig. S7
  - **Issue** The authors state that the apo form "incorporates the features of the antagonist-bound and agonist-bound forms, although the features of the antagonist-bound form dominate." This is based on comparing different principal components (PC1 vs. PC5), which is an unusual comparison. It is unclear what physical meaning is attributed to the 5th PC of the apo form.
  - **Required correction** Provide a clearer explanation of why the 5th PC of the apo form is comparable to the 1st PC of the agonist-bound form, and what this comparison implies for the dynamics of the apo state.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Discussion of knot analysis
  - **Evidence pointer** "Knot analysis" paragraph in "The Marionette Mechanism" section
  - **Issue** The authors mention that they examined the structures for knots and found none, and then speculate about "topological isomers" with knotted hinge domains. This is an interesting aside but is not connected to the main argument. The relevance of knot analysis to the proposed mechanism is unclear.
  - **Required correction** Either remove this speculation or connect it more explicitly to the proposed mechanism, for example by discussing whether knot formation could disrupt or modulate the proposed marionette communication.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Fig. 6
  - **Evidence pointer** Fig. 6
  - **Issue** Fig. 6 is described as a schematic summary of the proposed mechanism, but the figure itself was not visible in the provided text. The description in the Discussion suggests it is a conceptual diagram, but it is unclear what specific simulation data it summarizes.
  - **Required correction** Ensure that Fig. 6 clearly distinguishes between simulation-derived data and schematic/conceptual elements, and that the figure caption explains what each component represents.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Free energy values
  - **Evidence pointer** Fig. 3, Fig. 4, Fig. 5
  - **Issue** The free energy values are reported without units or error estimates. It is unclear whether the values are in kcal/mol, kBT, or arbitrary units.
  - **Required correction** Report free energy values with appropriate units and provide error estimates or confidence intervals for the basin depths and barrier heights.

## Risk / unsupported claims
- The claim that the predicted hERα structure "agrees well with experiments" is only weakly supported by the single χ² value and binding free energy comparison; the statistical significance of these comparisons is not established.
- The claim that "domain–domain communication exists only through the binding process of agonist-bound hERα" is not supported by the presented evidence, as the authors do not provide a quantitative definition of "communication" or a statistical test for its presence or absence in different states.
- The "marionette mechanism" is presented as a causal model, but the evidence is correlational (free energy landscape features) rather than causal (perturbation experiments).
- The claim that mutations found in breast cancer and psychiatric diseases "support the hinge domains' important role in hERα's function" is based on a correlation between mutation location and hinge region, which does not establish a mechanistic link.
- The statement that "the structural similarity and functional similarity of these receptors to hERα suggest that the marionette mechanism may be a universal mechanism for nuclear receptor action" is speculative and not supported by any comparative analysis.
- The claim that "the flexible regions of the receptors undergo a collective motion, much like the dancing of a marionette" is a metaphor that is not operationally defined or quantitatively characterized.
- The assertion that "the agonists act as marionettists that first control the motions of the LBDs" attributes agency to a small molecule in a way that is not supported by the simulation data.
- The statement that "the disordered hinges domains have lots of local minima on the energy landscape" is plausible but not demonstrated in the presented results.
- The claim that "the length, the critical position, and the diverse local minima of the disordered region make the dimer asymmetric" is presented as a conclusion but appears to be an interpretation without direct evidence linking these features to the observed asymmetry.
- The statement that "the DNA allosteric transition upon binding is hindered for these mutated hERαs" is based on perturbation theory calculations whose accuracy and limitations are not discussed.
- The claim that "all the mutated residues have highly frustrated interactions with the residues on the LBDs and the DNA" is presented without quantitative thresholds for what constitutes "highly frustrated."
- The statement that "the input files, simulation data, and analysis codes used in this work are deposited in GitHub" could not be verified, as the repository was not accessed during review.

## Assessment against Nature-style criteria
- **Originality** The "marionette mechanism" concept, while evocative, is not fundamentally novel. The idea that intrinsically disordered linkers mediate allosteric communication between domains has been proposed in other systems. The specific application to hERα and the use of AWSEM-3SPN.2C to study full-length receptor dynamics is a useful contribution, but the conceptual advance is incremental rather than transformative.
- **Scientific importance** The question of how ligand binding in the LBD of nuclear receptors communicates to the DBD is of significant interest to the nuclear receptor field and to drug discovery efforts. If the proposed mechanism were rigorously validated, it could inform the design of modulators that exploit or disrupt this communication. However, the current evidence is not sufficient to establish the mechanism with confidence.
- **Interdisciplinary readership** The topic bridges structural biology, computational biophysics, and cancer biology. The writing is generally accessible, though some sections (e.g., the frustration analysis) may be challenging for nonspecialists. The significance statement is clear and should appeal to a broad audience.
- **Technical soundness** The use of AWSEM-3SPN.2C is appropriate for this system, and the validation against SAXS and binding affinity data is a positive feature. However, the lack of statistical rigor in the free energy calculations, the absence of convergence analysis, and the qualitative nature of the frustration analysis weaken the technical foundation. The perturbation theory approach for studying mutants is not described in sufficient detail to assess its validity.
- **Readability for nonspecialists** The main text is generally well-written and the figures are likely to be informative, though the figure content could not be fully assessed from the text alone. The "marionette" metaphor is memorable and helps communicate the core idea, but it may oversimplify the underlying complexity. The Discussion section provides useful context for the broader implications of the work.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses an important question and uses an appropriate computational approach, but the central mechanistic claims are not yet established from the provided evidence. The authors should strengthen the statistical analysis of their free energy surfaces, provide convergence data, and ideally include perturbation experiments (in silico or in vitro) that directly test the proposed causal role of the hinge domains. The validation of the predicted structure should be more rigorous, with error estimates and comparisons to multiple experimental datasets. If these concerns are addressed, the manuscript could make a valuable contribution to the field.