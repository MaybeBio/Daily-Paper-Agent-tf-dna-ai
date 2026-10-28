## Review setup
- **Input scope** Full manuscript text (abstract, main text, figure legends referenced but not provided in full, supplementary figure references)
- **Assessment boundary** Scientific claims, methodology, data interpretation, and internal consistency based solely on the supplied text
- **Shared manuscript claim summary** The authors report that single-stranded DNA binding protein (SSB) undergoes a salt-induced first-order structural transition, inferred from discontinuous thermodynamic parameters measured via magnetic tweezers and supported by FTIR and time-resolved infrared spectroscopy. They propose that this transition underlies the distinct DNA binding modes of SSB.
- **Visible evidence base** Main text descriptions of MT experiments (Figures 1-3), FTIR spectral decomposition (Figure 4a-d), time-resolved IR VER data (Figure 4e-f), supplementary figure references (Supplementary Figs. 1-12), and cited literature
- **Missing materials affecting confidence** Actual figures and supplementary figures not provided; raw data, error bars, statistical analyses, experimental protocols, and detailed methods absent; no information on sample preparation, buffer conditions, temperature control, or data fitting procedures

## Reviewer
- **Overall assessment** The manuscript presents an intriguing hypothesis that free SSB undergoes a salt-induced first-order structural transition, which could explain the long-standing puzzle of SSB binding mode variability. The combination of single-molecule force spectroscopy and infrared spectroscopy is innovative. However, the evidence as presented is incomplete and contains several logical and methodological gaps that prevent full validation of the central claim. The discontinuity in thermodynamic parameters is suggestive but not conclusive, and the spectroscopic data, while supportive, lack quantitative rigor and control experiments. The manuscript would benefit from clearer presentation of raw data, error analysis, and a more direct test of the proposed transition mechanism.
- **Who would be interested in the results, and why** Researchers in biophysics, protein-nucleic acid interactions, thermodynamics of macromolecular surfaces, and single-molecule spectroscopy. The work could also interest those studying salt effects on protein conformation and the physical chemistry of protein surfaces, as it proposes a general phenomenon of surface phase transitions.
- **Major strengths** 1) The use of single-molecule magnetic tweezers to resolve distinct binding modes and measure thermodynamic parameters is technically sophisticated. 2) The observation of discontinuous thermodynamic parameters across a narrow salt concentration range is a novel and potentially important finding. 3) The combination of equilibrium (MT) and dynamic (time-resolved IR) measurements provides complementary perspectives. 4) The hypothesis linking surface salt bridges to a first-order transition is mechanistically plausible and testable.
- **Major Concerns** 
  - R1-M1: The central claim of a first-order structural transition in free SSB is not directly demonstrated. The MT data show discontinuities in binding parameters, but these could arise from other factors such as changes in DNA conformation, multivalent ion effects, or experimental artifacts. No direct structural evidence (e.g., crystallography, NMR, or SAXS) is provided.
  - R1-M2: The FTIR data, while showing spectral changes, are presented without quantitative analysis. The claim of a "jump" in peak intensities is based on visual inspection of normalized spectra, and no statistical significance or error bars are provided. The magnitude of changes is described as "very small," which raises questions about biological relevance.
  - R1-M3: The time-resolved IR VER data are limited to two salt concentrations (5 and 17 mM) and show minimal changes in decay constants. The interpretation that spectral narrowing indicates compaction is speculative and not supported by direct structural measurements.
  - R1-M4: The discrepancy between MT-derived binding site sizes (17 and 35 nt) and FRET-derived sizes (35 and 56 nt) is not adequately resolved. The authors attribute this to differential tension susceptibility, but this explanation is not rigorously tested.
  - R1-M5: The shift in transition midpoint between the MT assay (~45 mM) and literature values (~17 mM) is explained by a kinetic argument, but this explanation is not quantitatively supported and may indicate that the MT measurements are not at equilibrium.
- **Minor Comments** 
  - R1-m1: The manuscript lacks a clear description of the magnetic tweezers setup, including calibration, force accuracy, and drift correction.
  - R1-m2: The definition of "critical force" and its relationship to binding free energy should be more explicitly derived.
  - R1-m3: The text states "we were not able to measure accurately the response at very low forces," but no details on the lower force limit or how this affects the analysis are given.
  - R1-m4: The control experiment with BSA is mentioned but not shown; the authors should present these data to support the claim that the observed effects are specific to SSB.
  - R1-m5: The manuscript would benefit from a schematic model of the proposed structural transition, showing how salt bridges rearrange and how this relates to binding mode changes.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** 
  - Originality: High. The concept of a salt-induced first-order transition in a DNA-binding protein is novel and could have broad implications.
  - Scientific importance: Potentially high, but the current evidence is insufficient to establish the claim. If validated, it would significantly advance understanding of protein surface thermodynamics.
  - Interdisciplinary readership: The topic bridges biophysics, structural biology, and physical chemistry, appealing to a broad audience.
  - Technical soundness: The experimental approaches are appropriate, but the analysis and presentation are incomplete. Key controls and quantitative rigor are lacking.
  - Readability for nonspecialists: The manuscript is generally clear but assumes familiarity with single-molecule techniques and IR spectroscopy. Some concepts (e.g., first-order transitions, VER) could be explained more accessibly.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is intriguing and the experimental approach is promising, but the data as presented do not conclusively demonstrate a first-order structural transition in free SSB. Major revisions and additional experiments are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Core claim validity
- **Claim pointer** "Our data indicate that free SSB undergoes salt-induced first-order structural transitions."
- **Evidence pointer** Figures 2 and 3, main text "Discontinuousness of thermodynamic parameters"
- **Concern** The central claim is inferred from discontinuities in thermodynamic parameters (Fc, kFc, ΔX) measured via MT. However, these parameters describe the SSB-DNA complex, not free SSB. The authors argue that the transition is in free SSB, but no direct evidence (e.g., structural or spectroscopic data on free SSB alone) is provided. The FTIR data are on free SSB, but the changes are small and not quantitatively linked to a first-order transition.
- **Why it matters** A first-order transition is a specific thermodynamic phenomenon characterized by a discontinuity in the first derivative of the free energy. The data show discontinuities in binding parameters, but these could be due to changes in DNA conformation, ion effects, or experimental artifacts. Without direct evidence of a structural transition in free SSB, the central claim is not established.
- **Resolution test** Provide direct structural or spectroscopic evidence (e.g., CD, SAXS, or NMR) showing a cooperative, salt-dependent conformational change in free SSB with a clear transition midpoint. Alternatively, show that the discontinuities in binding parameters cannot be explained by other factors (e.g., DNA stretching, ion condensation).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** "When normalized to their maxima, it is obvious that the components at 1650 and 1670 cm−1 jumped down companying with the simultaneous bouncing up of 1661 cm−1 when the salt concentration was increased from 12 to 17 mM."
- **Evidence pointer** Figure 4c-d, Supplementary Figs. 8-11
- **Concern** The FTIR spectral changes are described qualitatively ("jumped down," "bouncing up") without quantitative analysis. No error bars, statistical tests, or replicate measurements are shown. The authors note that "the absolute changes of the peak intensities are very small," which raises concerns about signal-to-noise and reproducibility.
- **Why it matters** The claim of a first-order transition relies on a sharp, cooperative change in structure. If the spectral changes are small and not statistically significant, the evidence is weak. Quantitative analysis (e.g., peak area or intensity as a function of salt concentration with error bars) is essential to support the claim.
- **Resolution test** Provide quantitative analysis of FTIR peak intensities or areas as a function of salt concentration, including error bars and statistical significance. Show that the changes are reproducible and exceed noise levels.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of dynamics data
- **Claim pointer** "The time decay constants of the VER at 5 mM NaCl for the three frequencies are 212, 204 and 205 fs, respectively. When the salt concentration was increased to 17 mM, the time decay constants became 275, 206 and 207 fs, respectively."
- **Evidence pointer** Figure 4e-f
- **Concern** The VER data show minimal changes in decay constants (e.g., 204 to 206 fs for 2951 cm−1), yet the authors interpret the changes in initial amplitudes as evidence for compaction. The relationship between VER amplitude and protein conformation is not established, and the control with BSA is mentioned but not shown.
- **Why it matters** The dynamic data are used to support the structural transition claim, but the interpretation is speculative. Without a clear link between VER observables and specific structural changes, the data do not add strong support.
- **Resolution test** Show the BSA control data and provide a quantitative model linking VER amplitudes to conformational changes. Alternatively, use a more direct structural probe (e.g., time-resolved FRET or X-ray scattering) to confirm compaction.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Data consistency
- **Claim pointer** "The resulting site sizes are about 17 and 35 nt, respectively in the two [NaCl] ranges studied, which were much shorter than expected. We used FRET to check the site sizes... The resulting FRET values are 0.65 and 0.4 in 10 and 100 mM NaCl solutions, which are in accordance with the site sizes of 35 and 56 nt, respectively."
- **Evidence pointer** Figure 2c-d, Supplementary Fig. 3
- **Concern** The MT-derived binding site sizes (17 and 35 nt) are inconsistent with FRET-derived sizes (35 and 56 nt). The authors attribute this to differential tension susceptibility, but this explanation is not tested. The discrepancy is significant and undermines the quantitative interpretation of the MT data.
- **Why it matters** The binding site size is a key parameter used to identify binding modes. If the MT measurements do not accurately reflect the true site size, the assignment of modes and the interpretation of discontinuities may be incorrect.
- **Resolution test** Perform control experiments to directly measure the site size under tension (e.g., using different DNA lengths or force protocols). Alternatively, provide a quantitative model showing how tension affects the apparent site size.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Equilibrium assumption
- **Claim pointer** "The critical force Fc is higher for (SSB)35 (Fc≈16 pN) than for (SSB)56 (Fc≈9 pN)... At a concentration much lower than 45 mM, when the force is around 9 pN, once a (SSB)35 protein already binds the DNA, a (SSB)56 protein has no chance to bind the DNA because the force is not large enough to peel off the (SSB)35 protein."
- **Evidence pointer** Main text "Binding of SSB to 20 nt ssDNA"
- **Concern** The explanation for the shifted transition midpoint assumes a kinetic trapping mechanism, but the MT measurements are claimed to be quasi-static. If the system is not at equilibrium, the measured thermodynamic parameters may not be valid. The authors do not provide evidence that equilibrium is achieved.
- **Why it matters** The central claim of a first-order transition relies on the assumption that the measured parameters reflect equilibrium thermodynamics. If the system is kinetically trapped, the discontinuities may be artifacts of the measurement protocol.
- **Resolution test** Perform measurements at different loading rates to show that the results are rate-independent. Alternatively, use a different technique (e.g., equilibrium binding assays) to confirm the thermodynamic parameters.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Magnetic tweezers setup
- **Evidence pointer** Main text "MT analysis of SSB binding to 70 nt ssDNA"
- **Issue** The description of the MT setup is insufficient. No details on bead size, magnet configuration, force calibration, or temperature control are provided.
- **Required correction** Add a detailed methods section or supplementary protocol describing the MT setup, calibration, and data acquisition.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Theoretical framework
- **Affected element** Equation 4
- **Evidence pointer** Main text "MT analysis of SSB binding to 70 nt ssDNA"
- **Issue** The derivation of Equation 4 and the meaning of ΔG_stretch are not fully explained. The relationship between the observed force-dependent rate and the binding free energy should be clarified.
- **Required correction** Provide a more detailed derivation and define all terms in the equations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2
- **Issue** The figure legend is not provided, and the axes and units for the plots in Figure 2 are not described in the text.
- **Required correction** Include complete figure legends with axis labels, units, and error bars.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Control experiments
- **Affected element** BSA control
- **Evidence pointer** Main text "Infrared spectra changes of free SSB versus salt concentration"
- **Issue** The BSA control is mentioned but not shown. Without this control, it is unclear whether the observed spectral changes are specific to SSB or a general salt effect on proteins.
- **Required correction** Show the BSA control data in the main text or supplementary materials.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Proposed model
- **Evidence pointer** Main text "Infrared spectra changes of free SSB versus salt concentration"
- **Issue** The proposed model of surface salt bridge rearrangement is not illustrated. A schematic would help readers understand the proposed mechanism.
- **Required correction** Add a schematic figure showing the proposed structural transition and its relation to binding modes.

## Risk / unsupported claims
- The claim that free SSB undergoes a first-order structural transition is not directly supported by structural evidence; it is inferred from indirect measurements.
- The interpretation of FTIR spectral changes as evidence for a cooperative transition is not quantitatively supported.
- The relationship between VER dynamics and protein compaction is speculative.
- The explanation for the shifted transition midpoint in the MT assay is not quantitatively validated.
- The discrepancy between MT- and FRET-derived binding site sizes is not resolved.
- The claim that the findings "would inspire interests in thermodynamics of protein surfaces" is speculative and not supported by the data presented.