## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and conclusion. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and consistency between stated results and provided evidence. No assessment of formatting or editorial style beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors present a non-equilibrium molecular dynamics simulation protocol, based on steered MD and Jarzynski's equality, to quantify the dissociation free energy of sequence-specific protein-DNA complexes. They apply it to the minor groove binding protein H-NS (high-affinity AT-rich vs GC-analogue DNA) and the major groove binding ETS domain (three sequences), reporting predictions consistent with experimental binding preferences.
- **Visible evidence base** Main text figures (Figures 2, 3, 4, 5), methods descriptions, and results narrative. Supplementary figures and tables are referenced but not included in the provided material.
- **Missing materials affecting confidence** Supplementary Information (Figures S1-S8, Tables S1-S2), which contains the ETS domain results, convergence analyses, and additional methodological details. Also missing: exact simulation parameters for the ETS domain system, error analysis details, and raw data.

## Reviewer

- **Overall assessment** The manuscript presents a potentially useful and generalizable simulation protocol for estimating protein-DNA dissociation free energies. The application to H-NS is reasonably well supported by the main text evidence, and the agreement with experimental binding preferences is encouraging. However, the central claim of general applicability rests substantially on the ETS domain results, which are only described in the Supplementary Information and cannot be evaluated from the provided material. Several methodological details require clarification, and the statistical treatment of the non-equilibrium work measurements needs strengthening. The work is of interest to the computational biophysics and molecular recognition communities, and the protocol could be a practical addition to the field if the technical concerns are resolved.

- **Who would be interested in the results, and why** Computational biophysicists and chemists developing or applying enhanced sampling methods to biomolecular interactions. Experimentalists studying protein-DNA recognition mechanisms, particularly those interested in sequence specificity determinants, would find the predictive capability and mechanistic insights relevant. The protocol's claimed generalizability to other protein-DNA complexes broadens its appeal to researchers studying transcription factors, DNA repair proteins, and chromatin-associated factors.

- **Major strengths**
  1. The contact-map-based pulling coordinate is a thoughtful design choice that addresses a known limitation of center-of-mass-based coordinates, and the authors provide a clear rationale for this choice.
  2. The application to two structurally distinct DNA-binding proteins (minor groove vs major groove binding) is a good demonstration of potential generalizability.
  3. The systematic benchmarking of hyperparameters (force constant, pulling speed) adds practical value for users wishing to adopt the protocol.
  4. The mechanistic insights into dissociation pathways (sequential vs. simultaneous) and the identification of DNA deformation as a source of work variation are informative.
  5. The computational cost is modest (approximately one week on a single GPU/CPU node), making the approach accessible to many research groups.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "We show that our protocol correctly predicts that the ETS domain-DNA complex with the strongest interaction indeed contains the sequence experimentally identified as the consensus sequence."
- **Evidence pointer** Supplementary Information, Figures S7-S8, Tables S1-S2 (location not provided in main text)
- **Concern** The ETS domain application is presented as a key validation of the protocol's generalizability, but all results for this system are confined to the Supplementary Information, which was not provided for review. The main text states agreement with experimental data but provides no quantitative values, no comparison of the three sequences, and no methodological details specific to this system.
- **Why it matters** The H-NS system alone demonstrates the protocol works for one protein-DNA complex. The claim of general applicability, which is central to the manuscript's significance, rests on the ETS domain results. Without access to these data, the generalizability claim cannot be assessed.
- **Resolution test** Provide the Supplementary Information for review, including the ETS domain PMFs, the predicted free energy differences for all three sequences, and the comparison with experimental values.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "Dissociation of the H-NS complex from the high affinity sequence requires almost twice as much work (23.27 kcal/mol) compared to the GC-analogue (15.05 kcal/mol), resulting in a sequence specific difference ΔΔW of 8.22 kcal/mol."
- **Evidence pointer** Figure 3A, Results section "Dissociation of the complex"
- **Concern** The free energy difference is estimated from 20 non-equilibrium simulations per system using Jarzynski's equality. The manuscript reports a single value for ΔW and ΔΔW without confidence intervals, standard errors, or any measure of statistical uncertainty. The convergence of the exponential average is not demonstrated, and the number of simulations (20) is relatively small for this estimator, which is known to be sensitive to rare large-work events.
- **Why it matters** The central quantitative claim of the paper is the sequence-specific free energy difference. Without error bars or convergence analysis, the reader cannot assess whether the 8.22 kcal/mol difference is statistically meaningful or within the noise of the method. This is particularly important given the authors' own observation of high variance in the work curves.
- **Resolution test** Provide bootstrap or block-averaged confidence intervals for ΔW and ΔΔW, demonstrate convergence of the Jarzynski estimator with respect to the number of simulations, and discuss the expected bias of the exponential average for this system.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological justification
- **Claim pointer** "The pulling coordinate is based on distances between atom pairs in the protein and DNA... a contact map is thus already a quantitative indicator of binding strength, while centers of mass only provide relative distance between the groups."
- **Evidence pointer** Methods section "Steered molecular dynamics", Results section "Dissociation of the complex", Figure S5
- **Concern** The choice of the contact-map-based pulling coordinate is well motivated, but the manuscript does not address whether the results depend on the specific functional form of the switching function, the cutoff parameters, or the selection of atoms included in the contact map. The authors state that "a larger contact map slows down the calculation" and that "with a too small contact map, comparison of different sequences is no longer possible," but no systematic analysis of this sensitivity is presented.
- **Why it matters** The protocol's generalizability depends on the robustness of the pulling coordinate choice. If the predicted free energy differences are sensitive to the contact map definition, users would need system-specific tuning, which would undermine the claim of a generally applicable protocol.
- **Resolution test** Perform a sensitivity analysis varying the contact map composition (e.g., number of atoms, inclusion of backbone vs side-chain atoms) and the switching function parameters, and show that the predicted ΔΔW remains consistent within statistical uncertainty.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of mechanism
- **Claim pointer** "The increased variance in the GC-analogue suggest the FI state is less stable than in the high affinity sequence." and "The hypothesis that the widening of the minor groove width weakens the electrostatic interactions of the R114 with the nucleobases... has now been further supported by the PMFs obtained via the SMD simulations."
- **Evidence pointer** Figure 2A, Figure 3A, Results section "Stability of the H-NS DNA complexes" and "Dissociation of the complex"
- **Concern** The manuscript draws mechanistic conclusions about binding stability and dissociation pathways from the PMFs and contact analysis, but the connection between the observed variance in work curves and the proposed molecular mechanism is largely qualitative. The claim that minor groove width directly modulates R114 binding strength is plausible but is not quantitatively tested (e.g., by correlating local groove width with R114 contact stability along the pulling coordinate).
- **Why it matters** The mechanistic insights are presented as a significant outcome of the work. If the proposed mechanism is not rigorously supported, the manuscript's contribution beyond the methodological protocol is weakened.
- **Resolution test** Provide a quantitative analysis linking groove width, R114 contacts, and work values along the pulling coordinate, or temper the mechanistic claims to match the level of evidence.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Steered molecular dynamics"
- **Evidence pointer** Equation for contact definition, parameters r0, d0, nn, mm
- **Issue** The manuscript states that the parameters for the switching function were "adjusted to r0 = 3.0 nm, d0 = 0.3 nm, nn = 1, mm = 12" for the pulling simulations, but the rationale for these specific values is not explained. The relationship between the contact count at the start (108) and end (65) of the pulling and the physical states (FI vs. BB) is also not fully clarified.
- **Required correction** Provide a brief justification for the parameter choices and clarify how the start and end contact counts correspond to the FI and BB states, possibly with a reference to the supplementary figure showing the functional form.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Dissociation of the complex"
- **Evidence pointer** Figure 4, discussion of dissociation pathways
- **Issue** The classification of trajectories into Q-G-R and R-G-Q pathways uses a threshold of CQ-minor = 5 at CQGR-minor = 30, but the sensitivity of this classification to the threshold choice is not discussed. The authors note that 14 versus 6 runs follow the two pathways, but the statistical significance of this asymmetry is not assessed.
- **Required correction** Briefly discuss the robustness of the pathway classification to the threshold choice and, if appropriate, provide a simple statistical test for the asymmetry.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Molecular dynamics"
- **Evidence pointer** Table 1, simulation parameters
- **Issue** The manuscript mentions that simulations were performed with GROMACS 2020.4 and PLUMED 2.6.3, but does not specify the version of the AMBER14sb-parmbsc1 force field parameters or the source of the initial H-NS-DNA structure beyond the PDB code. The equilibration protocol is described only briefly.
- **Required correction** Provide additional details on the equilibration protocol, the exact force field files used, and any modifications to the initial structure (e.g., protonation states, missing residues).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 3B, snapshot description
- **Evidence pointer** "Panel B of Figure 3 shows for the high affinity sequence snapshots of the lowest work SMD trajectory along the pulling coordinate at the FI state (λ = 1.0) to a state disconnected from the DNA"
- **Issue** The sentence describing Figure 3B appears incomplete, ending with "disconnected from the DNA" without specifying the final λ value or the state label. This makes the figure caption and text inconsistent.
- **Required correction** Complete the sentence and ensure the figure caption clearly describes the states shown at each λ value.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "Dissociation of the complex", discussion of high work runs
- **Evidence pointer** Figure 5B, correlation analysis
- **Issue** The correlation between maximum work and maximum RMSD of DNA is reported with coefficients of 0.77 and 0.51 for the high affinity sequence, but the authors do not discuss whether this correlation reflects a causal relationship (DNA deformation causing high work) or a common underlying factor. The near-zero correlation for the GC-analogue is attributed to lower DNA deformability, but this interpretation is speculative.
- **Required correction** Acknowledge the correlational nature of this analysis and consider alternative explanations, or provide additional analysis to support the causal interpretation.

## Risk / unsupported claims
- The general applicability of the protocol to any protein-DNA complex is not established from the provided evidence, as the second application (ETS domain) is only described in the unavailable Supplementary Information.
- The claim that the protocol "yields results fast" is supported only by a single timing estimate for the ETS domain system; no systematic benchmarking is provided.
- The statement that the approach "is generally able to quantify the binding strengths and characterize the dissociation mechanism of protein-DNA complexes with the current settings" is an extrapolation beyond the two systems studied.
- The mechanistic claim that minor groove width directly modulates R114 binding strength is plausible but not quantitatively demonstrated.
- The statistical significance of the 8.22 kcal/mol ΔΔW cannot be assessed without confidence intervals or convergence analysis.
- The claim that the protocol "can be easily extended to include transient contacts or additional contacts" is not demonstrated.