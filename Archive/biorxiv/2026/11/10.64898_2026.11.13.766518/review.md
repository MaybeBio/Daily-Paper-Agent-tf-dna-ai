## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Methods, Results, Discussion, Conclusions, and supplementary figure references)
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and alignment with stated claims. No line-by-line editorial review.
- **Shared manuscript claim summary** The authors use enhanced-sampling molecular dynamics (OneOPES), circuit topology analysis, and a thermodynamic decomposition scheme ("Divide et impera") to characterize the coupled folding and binding of the intrinsically disordered C-terminal region of FCP1 phosphatase to the folded transcription factor Rap74. They report a multimodal binding landscape with native, flipped, and disordered-bound states; identify early hydrophobic contacts followed by progressive helix formation; and compute an absolute binding free energy of −33 ± 5 kJ/mol, in close agreement with experimental values.
- **Visible evidence base** Abstract, Introduction, Methods (partial), Results sections (FCP1 term folding, complex dynamics, enhanced sampling landscape, thermodynamic decomposition, direct estimation), Discussion, Conclusions, and references to supplementary figures and tables. No supplementary material was provided.
- **Missing materials affecting confidence** Supplementary figures (S1–S14), supplementary results (1–4), supplementary movies (1–2), full Methods details, force field parameters, simulation input files, and experimental NMR data. These are referenced extensively and are essential for verifying convergence, reproducibility, and the accuracy of the reported free energies.

## Reviewer

- **Overall assessment** This manuscript addresses a challenging and important problem in the biophysics of intrinsically disordered proteins: resolving the conformational landscape and thermodynamics of coupled folding and binding. The combination of enhanced-sampling simulations, circuit topology, and a thermodynamic decomposition is conceptually appealing and potentially useful. However, the provided text does not include sufficient methodological detail or primary evidence to fully assess the validity of the central claims. The reported agreement with experiment is encouraging, but the convergence of the enhanced-sampling simulations, the robustness of the free-energy decomposition, and the mechanistic conclusions require closer scrutiny. The manuscript is likely of interest to a specialized biophysics audience, but its broader impact will depend on the strength of the evidence presented in the supplementary materials.

- **Who would be interested in the results, and why** Researchers in computational biophysics, specifically those studying intrinsically disordered proteins, protein-protein interactions, and enhanced-sampling methods. The thermodynamic decomposition approach may also interest method developers. The system itself (FCP1-Rap74) is relevant to transcription regulation, so structural biologists and biochemists studying RNA polymerase II regulation may find the results useful. The potential application to peptide therapeutics is mentioned but not developed.

- **Major strengths**
  1. The study tackles a difficult and biologically relevant problem: coupled folding and binding of an IDR.
  2. The use of multiple complementary approaches (enhanced sampling, circuit topology, thermodynamic decomposition) is a strength.
  3. The reported agreement between the calculated and experimental binding free energy is a notable positive result.
  4. The identification of a flipped binding state and the analysis of multiple binding pathways add conceptual depth.
  5. The "Divide et impera" decomposition is a potentially generalizable methodological contribution.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the OneOPES enhanced-sampling simulations reveal a multimodal binding landscape and that the free-energy calculations are converged.
- **Evidence pointer** Methods (partial), Results sections "Enhanced sampling reveals a multimodal folding-and-binding landscape" and "Free energy of binding", Figures 4 and 5, Figure S10
- **Concern** The manuscript does not provide sufficient evidence for convergence of the enhanced-sampling simulations. The text states that "All simulations converged at around 300 ns of the simulations" but does not show the convergence metrics, such as time-dependent free-energy estimates, bias evolution, or reweighting diagnostics. The exploratory simulations (OPES_METAD_EXPLORE) are described as not converged, yet the OneOPES results are presented as converged without demonstrating this. The choice of collective variables (LDA interchain, LDA helix, S N , S F , z) is described, but the justification for their sufficiency to capture the relevant slow degrees of freedom is not provided.
- **Why it matters** The central quantitative claim of the paper, the absolute binding free energy of −33 ± 5 kJ/mol, depends entirely on the convergence and accuracy of the enhanced-sampling simulations. Without demonstrated convergence, the reported value and its uncertainty cannot be evaluated. The mechanistic conclusions about pathways also rely on the simulations having adequately sampled the conformational space.
- **Resolution test** Provide convergence plots for each simulation repeat, including free-energy estimates as a function of simulation time, and show that the final values are stable. Show that the collective variables used adequately distinguish the relevant states and that the simulations have explored the relevant regions of configuration space. Provide block-averaged or otherwise statistically robust error estimates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The "Divide et impera" thermodynamic decomposition separates the free-energy cost of folding from the binding free energy of the folded conformation, and the sum reproduces the experimental binding free energy.
- **Evidence pointer** Results section "Free energy of folding", Figure 5A, E
- **Concern** The thermodynamic decomposition is a central methodological contribution, but the text does not provide a rigorous derivation or a clear statement of the assumptions underlying the decomposition. Specifically, the folding free energy ΔF folding is calculated for the isolated peptide, and the binding free energy ΔF binding is calculated for a peptide restrained to a helical conformation. The validity of combining these two quantities to obtain the total coupled folding-binding free energy depends on the choice of the reference state and the definition of the "folded" state. The text does not clarify how the folded state is defined (e.g., by the number of hydrogen bonds, S h-bonds > 9?) and whether the restraints used in the binding simulation are consistent with this definition. The correction for the restraints is mentioned but not described in detail.
- **Why it matters** If the decomposition is not rigorously justified, the reported total free energy may be incorrect or not comparable to the experimental value. The claim that the method "reduces the conformational complexity of individual calculations while preserving the thermodynamic connection" needs to be supported by a clear theoretical framework.
- **Resolution test** Provide a formal derivation of the decomposition, including the definition of all states and the relationship between the restrained and unrestrained ensembles. Show that the sum of the decomposed free energies is independent of the chosen definition of the folded state, within statistical uncertainty. Describe the restraint corrections in detail and show that they are accurately computed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality
- **Claim pointer** The authors state that "hydrophobic contacts are early determinants of association followed by progressive helix formation" and that both induced-fit and conformational-selection pathways contribute to binding.
- **Evidence pointer** Results section "Mechanism of folding-and-binding", Figures 6A–D, Supplementary Results 4
- **Concern** The mechanistic conclusions are based on the analysis of simulation trajectories, but the text does not provide quantitative evidence to support the ordering of events (hydrophobic contacts before helix formation) or the relative contributions of the proposed pathways. The statement that "the unrestricted peptide samples a broader ensemble of partially bound and partially folded conformations" is qualitative. No flux analysis or committor analysis is presented to quantify the pathway contributions.
- **Why it matters** The claim that both induced-fit and conformational-selection contribute is interesting but requires quantitative support. Without a measure of the relative flux through each pathway, the conclusion remains speculative. The ordering of events is also a strong claim that needs to be backed by time-resolved analysis of contact and secondary-structure formation.
- **Resolution test** Provide quantitative analysis of the order of events, such as the average time of formation of hydrophobic contacts versus helix completion. Perform a flux analysis or use transition path theory to estimate the relative contributions of the induced-fit and conformational-selection pathways. Show that the conclusions are robust across simulation repeats.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The methods section states that "All simulations were performed using GROMACS 2023.5 patched with the PLUMED 2.9.3" and refers to the supporting materials for details.
- **Evidence pointer** Methods section "Molecular Dynamics Simulations"
- **Concern** The provided methods are insufficient to reproduce the simulations. Key details are missing, including the force field (DES-amber is mentioned in the Discussion but not in the Methods), water model, ion concentration, temperature and pressure coupling schemes, the specific implementation of the OneOPES algorithm, the parameters for the funnel restraint, and the definitions of all collective variables. The text states that "A detailed description of the methods is provided in the supporting materials," but the supporting materials were not provided for review.
- **Why it matters** Reproducibility is a fundamental requirement for computational studies. Without full methodological details, the results cannot be independently verified or built upon.
- **Resolution test** Provide the full methods in the supporting materials, including all simulation parameters, input files, and analysis scripts. Ensure that the main text includes sufficient detail for a knowledgeable reader to understand the setup.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the "Divide et impera" approach "reduces the conformational complexity of individual calculations while preserving the thermodynamic connection between unbound and bound states." This is a key claim, but the abstract does not explain what "Divide et impera" means or how it works.
- **Required correction** Briefly explain the decomposition in the abstract, e.g., "we separate the free-energy cost of folding from the binding free energy of the folded conformation."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "FCP1 term is predominantly disordered but transiently folds into an α-helical conformation"
- **Evidence pointer** Figure 1A
- **Issue** The text states that "at 5.8 µs and 9.8 µs, more than eight residues adopt a helical conformation, corresponding to 6.4% of the trajectory frames." It is unclear whether these are two isolated events or whether the helical state is populated for a continuous period. The 6.4% figure seems inconsistent with "at 5.8 µs and 9.8 µs" suggesting two specific time points.
- **Required correction** Clarify the duration and frequency of the helical state. For example, state that the helical conformation is populated for a total of 6.4% of the trajectory, with the longest-lived event occurring at 5.8–6.0 µs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "The FCP1 term :Rap74 complex retains a dynamic binding interface"
- **Evidence pointer** Figure 3D
- **Issue** The orientation CV is described as "the normalized projection of two vectors: one describing the direction of the binding pocket and the other describing the orientation of the FCP1 term helix." The text then states that "the pocket vector connects the Cα atom of Pro502 with the & atom of Leu474." The "& atom" appears to be a typographical error.
- **Required correction** Correct the typo, likely "the Cα atom of Leu474" or "the carbonyl oxygen of Leu474."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Free energy of binding"
- **Evidence pointer** Figure 5C
- **Issue** The text states that "the minimum of the surface is located around the initial state, and after a rapid increase, it approaches a plateau." This is confusing because the "initial state" is not defined. It would be clearer to state that the minimum is at the bound state (z ≈ 1.7 nm) and the plateau corresponds to the unbound state (z > 3.5 nm).
- **Required correction** Define the bound and unbound states in terms of the z coordinate before describing the free-energy profile.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion mentions that "the balance between favourable intrachain interactions and the energetic cost of exposing hydrophobic residues to solvent may thus contribute to the conformational equilibrium." This is a plausible interpretation, but it is not directly tested in the simulations.
- **Required correction** Either provide additional analysis to support this interpretation (e.g., solvent-accessible surface area calculations) or soften the language to indicate that this is a hypothesis.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data and Code Availability
- **Evidence pointer** Data and Code Availability section
- **Issue** The code repository is provided, but it is unclear whether the simulation input files, topology files, and analysis scripts are included.
- **Required correction** Clarify what is included in the repository and provide a README with instructions for reproducing the simulations and analyses.

## Risk / unsupported claims
- The absolute binding free energy of −33 ± 5 kJ/mol is presented as a key result, but its accuracy cannot be assessed without evidence of convergence and a rigorous description of the thermodynamic decomposition.
- The claim that both induced-fit and conformational-selection pathways contribute to binding is not quantitatively supported.
- The claim that hydrophobic contacts form before helix formation is not supported by time-resolved analysis.
- The statement that the "Divide et impera" approach "reduces the conformational complexity" is not formally justified.
- The comparison with experimental NMR data is mentioned but not shown; the quality of the agreement cannot be evaluated.
- The claim that the well-tempered ensemble shows "improved agreement with experiment" is not supported by data in the provided text.
- The statement that the flipped state is "40 kJ/mol less stable than the native state" appears in the Discussion, but the Results section reports a value of "more than 30 kJ/mol" from Figure S10F. This discrepancy is not explained.