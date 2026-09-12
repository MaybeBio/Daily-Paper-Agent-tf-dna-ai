## Review setup
- **Input scope** Full manuscript (including abstract, introduction, experimental, results and discussion, conclusions, and supplementary information reference)
- **Assessment boundary** Scientific content, methodology, data interpretation, and conclusions as presented in the manuscript
- **Shared manuscript claim summary** The authors claim that multivalent cations stabilize DNA duplexes beyond simple charge neutralization through a mechanism involving minor-groove clamping, and that this stabilization increases monotonically with cation valency, as demonstrated by force-induced unpeeling experiments and all-atom molecular dynamics simulations.
- **Visible evidence base** Abstract, Introduction, Experimental (HRM, MT, MD), Results and Discussion (Figures 1-5, Tables S1), Conclusions, Author contributions, Conflicts of interest, Data availability, Acknowledgements
- **Missing materials affecting confidence** Supplementary Information (SI) is referenced but not provided for review; this includes Method S1, Method S2, Figures S1-S9, and Table S1, which are essential for evaluating experimental details, simulation protocols, and supporting data.

## Reviewer
- **Overall assessment** This manuscript presents a compelling single-molecule approach to quantify DNA duplex stability in the presence of multivalent cations, overcoming the limitations of bulk melting assays that are confounded by DNA condensation. The combination of magnetic tweezers experiments and all-atom MD simulations provides a powerful framework for understanding the valency-dependent stabilization of DNA. The observation of minor-groove clamping as a distinct mechanism beyond charge screening is novel and potentially significant. However, the manuscript suffers from several technical weaknesses, particularly in the MD simulation analysis, the lack of error propagation in thermodynamic calculations, and the absence of key control experiments. The conclusions are partially supported but require substantial strengthening before the case is fully established.
- **Who would be interested in the results, and why** Researchers in biophysics, nucleic acid chemistry, and molecular biology would be interested because the work provides a quantitative framework for understanding how multivalent ions (e.g., polyamines, protamine) modulate DNA stability, which is relevant to genome packaging, DNA-protein interactions, and the design of ion-responsive DNA nanostructures. The methodological advance of using force-induced unpeeling to bypass condensation effects is of broad interest to the single-molecule community.
- **Major strengths** 1. The use of magnetic tweezers to measure DNA unpeeling at equilibrium under high tension is a clever and effective way to circumvent DNA condensation, a long-standing obstacle in studying multivalent cation effects. 2. The systematic study across a wide range of cation valencies (1+ to 21+) provides a comprehensive dataset that reveals a clear monotonic trend in maximum stabilization. 3. The MD simulations offer a plausible structural mechanism (minor-groove clamping) that goes beyond simple electrostatic screening, providing a molecular-level interpretation for the experimental observations.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Data analysis and interpretation
    - **Claim pointer** The authors claim that the maximum DNA duplex stability (ΔGmaxchem) increases monotonically with cation valency, with values ranging from 3.33 kBT/bp for Na+ to 3.98 kBT/bp for protamine.
    - **Evidence pointer** Figure 3C, Results and discussion section
    - **Concern** The calculation of ΔGchem from the equilibrium unpeeling force (Fe) and extension change (Δl) relies on the equation ΔG = ΔGchem - Fe·Δl = 0. The authors report ΔGmaxchem values with high precision (e.g., 3.33 kBT/bp) but do not provide error bars or confidence intervals for these values. The uncertainty in Fe (from Figure 2D) and Δl (from Figure 2E) must be propagated to assess whether the differences between adjacent valencies (e.g., Na+ vs. Ca2+, or PLL6+ vs. protamine) are statistically significant. Without error analysis, the claim of a monotonic increase is not rigorously supported.
    - **Why it matters** The central conclusion of the paper—that DNA duplex stability increases monotonically with cation valency—depends entirely on the precision and accuracy of these ΔGchem values. If the differences are within experimental noise, the claim is invalidated.
    - **Resolution test** Provide error bars for ΔGchem values in Figure 3C, calculated by propagating uncertainties from Fe and Δl measurements (e.g., using standard deviations from multiple independent experiments or bootstrapping). Perform a statistical test (e.g., t-test or ANOVA) to confirm that the differences between successive valencies are significant (p < 0.05).

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Methodology and controls
    - **Claim pointer** The authors claim that the force-induced unpeeling approach prevents DNA condensation and allows measurement of intrinsic duplex stability.
    - **Evidence pointer** Figure 2, Results and discussion section
    - **Concern** The manuscript does not provide direct evidence that DNA condensation is fully prevented under the high-tension conditions used. The authors state that "the applied force can prevent DNA condensation," but no control experiments are shown to verify this. For example, does the extension-force curve show any hysteresis or signatures of condensation (e.g., abrupt shortening) at high cation concentrations? The authors should demonstrate that the unpeeling force measurements are not influenced by residual condensation or aggregation, especially at the highest concentrations of protamine and PLL6+.
    - **Why it matters** If condensation is not fully suppressed, the measured unpeeling forces and derived ΔGchem values could be contaminated by contributions from inter-duplex interactions or higher-order structures, undermining the claim that the results reflect intrinsic duplex stability.
    - **Resolution test** Include control experiments showing that the extension-force curves are reversible and lack hysteresis when cycling through the unpeeling force range at the highest cation concentrations tested. Alternatively, show that the unpeeling force is independent of DNA tether density or the presence of free DNA in solution under these conditions.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Simulation analysis and interpretation
    - **Claim pointer** The authors claim that higher-valent cations preferentially embed in the minor groove of DNA and clamp the minor groove, thereby stabilizing the helix more efficiently.
    - **Evidence pointer** Figure 5, Results and discussion section
    - **Concern** The MD simulation analysis defines "clamping ions" as those within 6 Å of both DNA strands. This distance criterion is arbitrary and may not capture the true bridging interaction. Furthermore, the authors classify clamping ions as minor- or major-groove based on their location, but the method for determining groove location is not described in sufficient detail. The fraction of clamping cations for PLL6+ (0.94 ± 0.04) and protamine (0.97 ± 0.02) is extremely high, suggesting that nearly all bound cations are clamping. This seems physically implausible for a large, flexible peptide like protamine, which could bind in multiple modes. The authors should provide a more rigorous definition of clamping and validate it with additional metrics (e.g., hydrogen bonding, ion-DNA contact lifetimes).
    - **Why it matters** The structural mechanism of minor-groove clamping is a key claim of the paper. If the definition of clamping is too permissive or the classification is ambiguous, the mechanistic interpretation may be incorrect or overstated.
    - **Resolution test** Provide a detailed description of the groove classification method. Re-analyze the clamping fraction using a stricter distance criterion (e.g., 4 Å) or a contact-based definition (e.g., ion within 3.5 Å of atoms from both strands). Include analysis of ion residence times or binding free energies to support the claim that clamping is a stable, stabilizing interaction.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Data completeness and reproducibility
    - **Claim pointer** The authors claim that the unpeeling force exhibits a non-monotonic dependence on cation concentration, with a maximum at the charge inversion threshold.
    - **Evidence pointer** Figure 2D, Results and discussion section
    - **Concern** The manuscript presents only a single representative dataset for each cation in Figure 2D. No information is provided on the number of independent experiments (e.g., number of DNA tethers, number of beads, number of experimental replicates) or the variability between measurements. The error bars in Figure 2D are not defined (e.g., standard deviation, standard error, or confidence interval). Without this information, the reproducibility and reliability of the non-monotonic trend cannot be assessed.
    - **Why it matters** The non-monotonic dependence is a critical observation that links the stabilization to charge inversion. If the data are from a single experiment or show high variability, the conclusion is not robust.
    - **Resolution test** Clearly state the number of independent experiments (N) and the number of tethers measured for each condition. Define the error bars in Figure 2D and provide a statistical analysis (e.g., mean ± SD) to demonstrate that the non-monotonic trend is reproducible and significant.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and presentation
    - **Affected element** Figure 1
    - **Evidence pointer** Figure 1C and 1D
    - **Issue** The melting curves in Figure 1C and 1D are difficult to interpret because the y-axis (fluorescence) is not normalized. The flattening of the curves at high cation concentrations could be due to dye exclusion or quenching rather than condensation.
    - **Required correction** Normalize the fluorescence curves to the maximum and minimum values for each condition, or provide a control showing that the dye fluorescence is not directly affected by the cations at the concentrations used.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Methodology
    - **Affected element** Experimental section (MT)
    - **Evidence pointer** Figure 2C, Experimental section
    - **Issue** The description of the force-cycling protocol is unclear. The authors state that the force is increased incrementally by ~0.1 pN in each cycle, but it is not specified how the force is calibrated or how the equilibrium unpeeling force is determined from the hopping kinetics.
    - **Required correction** Provide a more detailed description of the force calibration method (e.g., based on bead Brownian motion) and the algorithm used to identify the equilibrium unpeeling force from the extension variance or hopping kinetics.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Data interpretation
    - **Affected element** Results and discussion section
    - **Evidence pointer** Figure 3A
    - **Issue** The authors attribute the non-monotonic dependence of ΔGchem on cation concentration to charge inversion. However, the charge inversion concentrations are cited from previous work (refs. 18, 57) and are not directly measured in this study. The agreement between the reversal concentrations in Figure 2D and the reported charge inversion thresholds is noted but not quantitatively validated.
    - **Required correction** Either directly measure the zeta potential or electrophoretic mobility of the DNA under the experimental conditions to confirm charge inversion, or explicitly state that the attribution to charge inversion is based on prior literature and is a hypothesis that requires further testing.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Simulation analysis
    - **Affected element** MD simulation section
    - **Evidence pointer** Figure 5A
    - **Issue** The fraction of total clamping cations for Na+ and Ca2+ is reported as 0.15 ± 0.06 and 0.20 ± 0.06, respectively. However, the authors state that "Na+ and Ca2+ cations in the major groove are negligible." This is inconsistent because the clamping fraction for these ions is non-zero, implying some major-groove clamping must occur.
    - **Required correction** Clarify the statement. If the major-groove clamping fraction is negligible, then the total clamping fraction should equal the minor-groove clamping fraction. The data show that for Na+, the total clamping fraction (0.15) equals the minor-groove fraction (0.15), which is consistent. For Ca2+, the total (0.20) equals the minor-groove fraction (0.20), also consistent. The text should be revised to avoid the misleading statement.

- **Technical failings that need to be addressed before the case is established** R1-M1 (error propagation), R1-M2 (condensation control), R1-M3 (simulation analysis rigor), R1-M4 (reproducibility)

- **Assessment against Nature-style criteria** 
    - **Originality**: High. The use of force-induced unpeeling to bypass condensation and the identification of minor-groove clamping as a distinct stabilization mechanism are novel contributions.
    - **Scientific importance**: High. The work addresses a fundamental question in nucleic acid biophysics and has implications for understanding genome organization, DNA-protein interactions, and the design of DNA-based materials.
    - **Interdisciplinary readership**: Moderate to high. The topic is of interest to biophysicists, biochemists, and materials scientists, but the technical details of the single-molecule and simulation methods may limit accessibility for a broader biological audience.
    - **Technical soundness**: Moderate. The experimental design is clever, but the analysis is incomplete (lack of error propagation, missing controls) and the simulation analysis requires more rigorous validation.
    - **Readability for nonspecialists**: Good. The manuscript is well-written and the main findings are clearly stated, though some sections (e.g., the thermodynamic derivation) could be simplified for a broader audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea and experimental approach are strong, but the manuscript requires substantial revisions to address the concerns about data analysis, controls, and simulation rigor before the conclusions can be considered fully established.

## Risk / unsupported claims
- The claim that the maximum DNA duplex stability increases monotonically with cation valency is not fully supported due to the lack of error propagation in ΔGchem values (R1-M1).
- The claim that force-induced unpeeling fully prevents DNA condensation is not supported by direct experimental evidence (R1-M2).
- The claim that minor-groove clamping is the primary mechanism for stabilization by higher-valent cations is based on a simulation analysis that requires more rigorous validation (R1-M3).
- The claim that the non-monotonic dependence of unpeeling force on cation concentration is due to charge inversion is based on literature correlations rather than direct measurements in this study (R1-m3).