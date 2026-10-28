## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific content, methodology, validation, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors introduce COFFEE, a coarse-grained energy function for DNA-protein complexes, combining SOP-SC (protein) and TIS (DNA) models with a statistical potential for DNA-protein interactions. They claim transferability by reproducing crystallographic B-factors, SAXS profiles, and NMR chemical shifts, and demonstrate applications to salt-induced nucleosome unwrapping and ARG-to-LYS mutation effects.
- **Visible evidence base** Abstract, Introduction, Methodology, Results and Discussion, Concluding Remarks, figure references (Figs. 1–9), table references (Tables S1–S13)
- **Missing materials affecting confidence** Supplementary Information (detailed potential forms, parameter tables, PDB ID list), figure panels, simulation protocols (timestep, equilibration, system sizes), error bars and statistical uncertainties, comparison to alternative CG models, and experimental details for SAXS/NMR references

## Reviewer

- **Overall assessment** The manuscript presents a timely and potentially useful coarse-grained model for DNA-protein complexes. The modular integration of two established CG models with a statistical potential is conceptually sound, and the validation across multiple experimental observables is commendable. However, several technical aspects require clarification and additional analysis to fully establish the model's transferability and the robustness of the reported findings, particularly regarding the statistical potential derivation, the calibration procedure, and the interpretation of nucleosome mutation effects.

- **Who would be interested in the results, and why** Researchers in computational biophysics, molecular dynamics method development, and chromatin biology. The model offers a computationally efficient approach to simulate large DNA-protein assemblies, which is relevant for studying transcription, chromatin organization, and nucleosome dynamics. The sequence-specific statistical potential is a distinctive feature that could interest groups working on protein-DNA recognition and specificity.

- **Major strengths**
  - Modular integration of two well-tested CG models without re-calibration is a practical and transparent approach.
  - The single adjustable parameter (λDNAPRO) is a significant simplification that enhances the model's potential transferability.
  - Validation against multiple orthogonal experimental observables (B-factors, SAXS, NMR) strengthens the credibility of the model.
  - The application to nucleosome unwrapping and mutation effects demonstrates the model's utility for biologically relevant questions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The statistical potential (SP) is derived from a dataset of high-resolution crystal structures and is a key novel feature of COFFEE.
- **Evidence pointer** Methodology, "Statistical potential for native DNA-protein contacts" section; Figure 1; Tables S8–S13
- **Concern** The derivation of the statistical potential is described only briefly. Key details are missing: the exact dataset composition (number of complexes, redundancy filtering, resolution cutoff), the definition of "contact" for the SP (distance threshold, which bead types), the treatment of sequence composition bias, and the reference state formulation. The choice of reference state is acknowledged as important, but the specific form used is not stated. Without these details, the SP cannot be reproduced or critically evaluated.
- **Why it matters** The SP is the central novel contribution of COFFEE. If the derivation is not fully specified, the model is not reproducible, and the validity of the interaction energies (ϵ values) cannot be assessed. This undermines the core claim of the manuscript.
- **Resolution test** Provide a complete description of the SP derivation in the main text or SI, including dataset selection criteria, contact definitions, reference state, and any normalization procedures. Show that the derived ϵ values are robust to dataset composition (e.g., jackknife or bootstrap analysis).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** "For an optimal choice of λDNAPRO, the crystallographic B-factors for DNA-protein complexes, with varying sizes and topologies, are quantitatively reproduced."
- **Evidence pointer** Results and Discussion, "COFFEE reproduces the crystallographic B-factors" section; Figure 2
- **Concern** The calibration of λDNAPRO is performed using a single complex (PDB ID: 1CDW), and the same parameter is then used for all other systems. The manuscript does not report a systematic sensitivity analysis of λDNAPRO. It is unclear how the choice of calibration system affects the optimal value and whether a different calibration target would yield significantly different results. Additionally, the quantitative agreement with B-factors is stated but not quantified (e.g., correlation coefficients, RMSD values in absolute units). The visual comparison in Figure 2 is insufficient to assess "quantitative" agreement.
- **Why it matters** The claim of transferability rests on the assumption that a single λDNAPRO value works across diverse systems. Without a sensitivity analysis and quantitative error metrics, this assumption is not adequately supported. The calibration procedure is central to the model's practical use.
- **Resolution test** Perform a sensitivity analysis of λDNAPRO (e.g., vary over a range and report B-factor agreement for multiple complexes). Provide quantitative metrics (e.g., Pearson correlation, mean absolute error) for B-factor agreement across all six complexes. If possible, test calibration on a different complex and show that results are consistent.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** "COFFEE predicts the scattering profiles that are in quantitative agreement with SAXS experiments."
- **Evidence pointer** Results and Discussion, "Calculated scattering profiles" section; Figure 4
- **Concern** The comparison with SAXS data is presented for three complexes, but the manuscript does not report the simulation conditions (e.g., salt concentration, temperature, box size, ionic strength) for these calculations. The SAXS profiles are computed using Debye formula with CG form factors, but the accuracy of these form factors is not discussed. The agreement is stated as "quantitative" and "remarkable," but no statistical measure of goodness-of-fit is provided. The deviation at high q is acknowledged but not quantified.
- **Why it matters** SAXS validation is a key pillar of the transferability claim. Without detailed simulation conditions and quantitative fit metrics, the reader cannot assess whether the agreement is meaningful or coincidental. The choice of form factors could significantly affect the computed profiles.
- **Resolution test** Provide full simulation conditions for SAXS calculations. Report χ² or similar goodness-of-fit metrics for each complex. Discuss the accuracy and limitations of the CG form factors used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** "Strikingly, our nucleosome simulations explain the destabilization effect of ARG to LYS mutations, which does not alter the balance of electrostatic interactions, but affects chemical interactions in subtle ways."
- **Evidence pointer** Results and Discussion, "Mutations at superhelical locations enhance nucleosome flexibility" section; Figure 9
- **Concern** The claim that ARG-to-LYS mutations destabilize the nucleosome via "subtle chemical effects" is based on simulations with a single mutant construct (eight simultaneous mutations). The manuscript does not provide a per-residue analysis of which mutations contribute most to destabilization, nor does it compare to single-mutation effects. The mechanism of destabilization is not dissected: is it due to loss of specific contacts, changes in local packing, or altered dynamics? The statement "explain" is too strong given the level of analysis presented.
- **Why it matters** The nucleosome application is presented as a key demonstration of COFFEE's utility. If the mechanistic explanation is not rigorously supported, the biological significance of the finding is weakened. Overinterpretation of simulation results can mislead the field.
- **Resolution test** Perform single-mutation simulations or alchemical analysis to identify the dominant contributors. Provide a detailed structural analysis of the mutant vs. wild-type ensembles (e.g., contact maps, hydrogen bond occupancy, salt bridge persistence) to support the proposed mechanism.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methodology, "Simulations" section
- **Evidence pointer** Methodology, "Simulations" section
- **Issue** The simulation protocol is described only briefly. Key parameters such as timestep, friction coefficient (γ), integration scheme, equilibration time, and total simulation length are not stated. The statement "108 steps" is ambiguous without a timestep.
- **Required correction** Provide a complete simulation protocol in the SI, including all relevant parameters and a justification for the choice of the underdamped regime.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methodology, "Statistical potential" section
- **Evidence pointer** Methodology, "Statistical potential for native DNA-protein contacts" section; Tables S8–S13
- **Issue** The list of PDB IDs used for the statistical potential is only in the SI. The number of complexes and the redundancy criteria are not mentioned in the main text.
- **Required correction** State the number of complexes and the redundancy threshold in the main text. Consider adding a supplementary figure showing the distribution of contact counts.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results and Discussion, "COFFEE reproduces the crystallographic B-factors" section
- **Evidence pointer** Figure 2
- **Issue** The figure panels are referenced but not described in the text. It is unclear what exactly is plotted (e.g., B-factors vs. residue number, correlation plots).
- **Required correction** Add a clear description of each panel in the figure legend and refer to specific panels in the text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and Discussion, "Calculated scattering profiles" section
- **Evidence pointer** Figure 4
- **Issue** The manuscript states that Rgsim and Rgexp are "practically indistinguishable," but the actual values are not reported in the text.
- **Required correction** Report the numerical values of Rg for both simulation and experiment in the text or a table.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Context
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction does not clearly position COFFEE relative to existing CG models for DNA-protein systems (e.g., 3SPN, oxDNA, MARTINI). The novelty is implied but not explicitly stated.
- **Required correction** Add a brief paragraph comparing COFFEE to existing models, highlighting the specific advantages of the statistical potential approach.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Incomplete specification of the statistical potential derivation.
  - R1-M2: Lack of sensitivity analysis for λDNAPRO and quantitative B-factor agreement metrics.
  - R1-M3: Missing simulation conditions and quantitative fit metrics for SAXS validation.

- **Assessment against Nature-style criteria**
  - **Originality** The modular combination of SOP-SC and TIS with a statistical potential is a novel approach, though the individual components are established. The application to nucleosome mutations is a useful demonstration.
  - **Scientific importance** The model addresses a real need for efficient, sequence-specific CG simulations of DNA-protein complexes. The potential for broad applicability in chromatin biology is significant.
  - **Interdisciplinary readership** The work is relevant to biophysics, computational chemistry, and molecular biology. The writing is generally accessible, but the methodology section assumes familiarity with CG modeling.
  - **Technical soundness** The validation strategy is appropriate in principle, but the lack of quantitative metrics and sensitivity analyses weakens the technical case. The statistical potential derivation is not fully specified, which is a critical gap.
  - **Readability for nonspecialists** The abstract and introduction are clear. The results section is readable, but the methodology is dense. The figures are referenced but not fully described in the text.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the validation strategy is sound, but the manuscript currently lacks the detail and quantitative rigor needed to fully establish the model's transferability and the robustness of the nucleosome findings. The authors should address R1-M1, R1-M2, and R1-M3 before the case is fully established.

## Risk / unsupported claims
- The claim that COFFEE "explains" the destabilization effect of ARG-to-LYS mutations is not fully supported by the presented analysis, as the mechanistic basis is not dissected.
- The claim of "quantitative" agreement with B-factors and SAXS profiles is not backed by numerical metrics in the provided text.
- The transferability of COFFEE to arbitrary DNA-protein complexes is asserted but only demonstrated on a limited set of six complexes for B-factors and three for SAXS.
- The statement that the statistical potential captures "sequence-specific chemistry" is plausible but not directly validated by mutation or sequence-variation tests beyond the nucleosome example.