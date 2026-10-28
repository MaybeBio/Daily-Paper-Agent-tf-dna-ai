## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and concluding remarks. No supplementary material was provided.
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and support of claims by presented evidence. Editorial or stylistic preferences are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors propose that a conserved tyrosine at position 72 of the SRY HMG box (Y127 in intact human SRY) anchors a water-mediated clamp at the protein-DNA interface. Removal of the para-hydroxyl group (Y72F) disrupts this clamp, accelerating complex dissociation and attenuating transcriptional activity, positioning the variant at a threshold of sex-determination ambiguity.
- **Visible evidence base** Biochemical assays (electrophoretic mobility shift, permutation gel electrophoresis), circular dichroism, steady-state and time-resolved FRET, stopped-flow kinetics, NMR spectroscopy, cell-based transcriptional activation and chromatin immunoprecipitation assays, and molecular dynamics simulations based on a homologous Sox18 crystal structure.
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (e.g., Supplemental Figures S1-S22, Supplemental Tables S1-S12) were not provided. Raw kinetic traces, MD simulation parameters, convergence criteria, and statistical details for FRET distance distributions are not fully described in the main text.

## Reviewer

- **Overall assessment** This manuscript presents a detailed and interdisciplinary investigation into a clinically relevant mutation in SRY, proposing a novel mechanistic role for a conserved tyrosine in mediating water-dependent stabilization of the protein-DNA complex. The combination of biophysical, biochemical, cellular, and computational approaches is commendable and generally well integrated. However, the central claim of a "water-mediated clamp" relies heavily on MD simulations of a homologous system, and the direct experimental evidence for this specific mechanism remains indirect. The manuscript would be strengthened by clearer presentation of simulation validation, additional discussion of limitations, and more explicit linkage between the proposed atomic-level mechanism and the observed kinetic and cellular phenotypes.

- **Who would be interested in the results, and why** Researchers in the fields of sex determination and disorders of sex development, structural biology of protein-DNA interactions, biophysics of transcription factor kinetics, and molecular mechanisms of developmental robustness and canalization. The work also has broader relevance to those studying subtle mutations that cause incomplete penetrance and variable expressivity in monogenic disorders.

- **Major strengths**
  1. The study addresses a clinically important and intellectually challenging problem: how a chemically subtle mutation (Y to F) can cause a dramatic phenotypic switch in sex determination.
  2. The integration of multiple complementary techniques (NMR, FRET, stopped-flow kinetics, cell-based assays, MD simulations) provides a multi-scale view of the mutation's effects.
  3. The use of chimeric "box swap" constructs to validate the relevance of the Sox18 structural model is a thoughtful and appropriate approach.
  4. The authors are appropriately cautious in distinguishing established results from speculative interpretations, particularly in the Discussion section.
  5. The writing is generally clear and the logical flow from observation to hypothesis to test is well structured.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of computational evidence
- **Claim pointer** The authors claim that MD simulations predict a long-lived water molecule anchored by Y72 that bridges the protein-DNA interface, and that this water-mediated clamp is disrupted in the Y72F variant.
- **Evidence pointer** Results section "MD simulations predict Y72-anchored water molecule at DNA interface"; Figures 7D, 8, 9; Supplemental Figures S13, S14, S18-S22
- **Concern** The MD simulation methodology is described only briefly. Key details are missing: force field parameters for the DNA and protein, water model used, equilibration protocol, number of replicate simulations, convergence criteria, and how the 200-ns simulation length was justified. The claim of a "long-lived" water molecule (10-100 ns) is made from a single 200-ns trajectory, which may be insufficient to establish statistical significance. Furthermore, the simulations are based on the Sox18 crystal structure, not the SRY structure, and the authors acknowledge differences in DNA conformation. The extrapolation to SRY is supported by only 40 ns of a single trajectory (Supplemental Figure S14). Without convergence analysis, replicate simulations, or free energy calculations, the robustness of the water-binding predictions is uncertain.
- **Why it matters** The central mechanistic claim of the paper rests on the MD predictions. If the water-binding site is not reproducibly occupied or if the simulation is not converged, the "water-mediated clamp" hypothesis is not supported by the computational evidence.
- **Resolution test** Provide detailed simulation protocols, including force field versions, water model, equilibration and production run parameters, and convergence metrics (e.g., RMSD plateau, water occupancy autocorrelation). Perform at least three independent replicate simulations for each system and report standard deviations for water occupancy times. Ideally, use umbrella sampling or metadynamics to compute the free energy of water binding at the Y72 site. If feasible, perform simulations of the actual SRY-DNA complex rather than relying solely on the Sox18 homolog.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Strength of experimental evidence for the proposed mechanism
- **Claim pointer** The authors propose that "unclamping" of the basic tail in the Y72F variant leads to accelerated dissociation and attenuated transcriptional activity.
- **Evidence pointer** Results sections "Subtle Y72F-associated perturbations in structure and dynamics" and "Marked Y72F-associated perturbations in kinetic stability"; Figures 4, 5, 6
- **Concern** The experimental data show a fourfold increase in k_off for Y72F, but the structural basis for this increase is inferred rather than directly demonstrated. The NMR and FRET data show subtle differences between WT and Y72F, but these are not definitively localized to the tail-DNA interface. The authors do not provide direct experimental evidence (e.g., hydrogen/deuterium exchange, paramagnetic relaxation enhancement, or site-directed spin labeling) that the tail is more dynamic or less clamped in the variant. The connection between the proposed water-mediated clamp and the observed kinetic changes remains correlative.
- **Why it matters** The manuscript claims a specific mechanistic model, but the experimental data are consistent with multiple alternative explanations (e.g., altered van der Waals contacts, changes in local electrostatics, or entropic effects unrelated to water). Without direct evidence for the water-mediated clamp, the mechanistic claim is overstated.
- **Resolution test** Provide additional experimental data that directly probe the tail dynamics and solvation at the interface. This could include: (1) NMR relaxation dispersion measurements on the tail residues; (2) site-directed mutagenesis of the Y72 position to other residues (e.g., W, A, H) with corresponding kinetic and structural characterization; (3) osmotic stress experiments to test the role of water activity in complex stability; or (4) high-resolution crystal structures of both WT and Y72F SRY-DNA complexes with explicit water molecules modeled.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the "water-mediated clamp" to other SOX domains
- **Claim pointer** The authors state that "conservation of Y72 suggests that this water-mediated clamp operates generally among SRY and metazoan SOX domains."
- **Evidence pointer** Discussion section; Supplemental Figure S2
- **Concern** The manuscript provides evidence for the water-mediated clamp in one homologous system (Sox18) and extrapolates to all SOX domains based on sequence conservation. However, the authors do not test this prediction experimentally or computationally in other SOX family members. The functional significance of the clamp may vary depending on the specific DNA target, the presence of partner proteins, and the cellular context. The claim of generality is therefore speculative.
- **Why it matters** The broader significance of the work depends on the generality of the proposed mechanism. If the clamp is specific to SRY or a subset of SOX proteins, the impact of the finding is more limited.
- **Resolution test** Perform MD simulations or experimental studies on at least one additional SOX family member (e.g., SOX2, SOX9, or SOX18 with the Y72F mutation) to test whether the water-mediated clamp is conserved. Alternatively, temper the claim of generality and explicitly discuss the limitations of extrapolating from a single homolog.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 3
- **Evidence pointer** Figure 3 and its legend
- **Issue** The figure presents a large amount of data (transcriptional activity, ChIP, PGE, CD) in a compact format. The legend is dense and some panels are difficult to interpret without referring back to the text multiple times.
- **Required correction** Consider splitting Figure 3 into two figures or reorganizing panels to improve readability. Expand the legend to clearly define all abbreviations and statistical comparisons.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Kinetic and FRET measurements
- **Evidence pointer** Results section "Marked Y72F-associated perturbations in kinetic stability"; Supplemental Tables S7, S8
- **Issue** The number of independent replicates for stopped-flow FRET experiments is not explicitly stated in the main text. Error bars are shown in figures, but the statistical test used to compare WT and variant values is not described.
- **Required correction** State the number of independent experiments and the statistical test used (e.g., Student's t-test, ANOVA) in the figure legends or Methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** MD simulation details
- **Evidence pointer** Methods section "Molecular dynamic studies"
- **Issue** The description of the MD simulations is brief. Key parameters such as the specific AMBER force field version, water model (e.g., TIP3P, TIP4P), salt concentration, and temperature/pressure coupling algorithms are not specified.
- **Required correction** Provide a complete description of the simulation parameters in the Methods section, including software version, force field, water model, ion concentration, and equilibration protocol.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of CD spectroscopy
- **Affected element** Figure 3F
- **Evidence pointer** Results section "Subtle Y72F-associated perturbations in structure and dynamics"
- **Issue** The interpretation of the CD spectra as evidence for A-form DNA character is somewhat speculative. CD spectra in the near-UV region are influenced by multiple factors, including base stacking and sugar pucker, and the differences between WT and Y72F are subtle.
- **Required correction** Acknowledge the limitations of CD spectroscopy for determining DNA conformation and consider supporting the interpretation with additional structural data (e.g., circular dichroism melting curves or molecular dynamics analysis of sugar puckers).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Introduction and Discussion
- **Evidence pointer** Location not provided
- **Issue** Some statements about the role of water in protein-DNA interactions and the concept of "indirect readout" would benefit from additional citations to the broader literature.
- **Required correction** Add references to key reviews or primary papers on water-mediated protein-DNA interactions and indirect readout.

## Risk / unsupported claims
- The claim that a single water molecule anchored by Y72 acts as a "clamp" that stabilizes the SRY-DNA complex is not directly supported by experimental evidence. The MD simulations provide a plausible model, but the experimental data (NMR, FRET, kinetics) are consistent with, but do not prove, this specific mechanism.
- The claim that the water-mediated clamp is "conserved among the family of metazoan SOX factors" is extrapolated from sequence conservation and a single homologous structure. No experimental or computational evidence is provided for other SOX family members.
- The statement that "unclamping" of the Y72F variant leads to "enhanced local conformational fluctuations at the tail-DNA interface" is inferred from indirect measurements (FRET linewidth, NMR chemical shift changes) and MD simulations, but is not directly measured.
- The prediction that Y72W in SOX2 may reposition D71 and perturb the SOX2-POU interface is speculative and not tested in this manuscript.
- The "Humpty Dumpty" model of enhanceosome disassembly, while an interesting analogy, is presented without direct experimental support and should be clearly labeled as a hypothesis.