## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusion, experimental section) as provided by the user. Supplementary figures and tables are referenced but not provided.
- **Assessment boundary** The scientific claims, methodology, data interpretation, and internal consistency of the manuscript as presented. No external literature verification or replication of experiments was performed.
- **Shared manuscript claim summary** The manuscript claims that the nitrile-containing Ru(II) polypyridyl complex [Ru(phen)2(11,12-dCN-dppz)]2+ (1) acts as a sensitive infrared probe of G-quadruplex (G4) structures. The authors report enantiomer-sensitive binding to hybrid htel(K) and antiparallel htel(Na) G4s, use time-resolved infrared (TRIR) spectroscopy to identify binding site bases, and employ the nitrile transient shift to report on the hydrogen-bonding environment. Molecular dynamics (MD) simulations and binding energy calculations are used to identify favorable binding sites, which are claimed to agree with TRIR results.
- **Visible evidence base** Main text figures (Figures 1-9), tables (Tables 1-3), and referenced supplementary figures (S1-S23) and tables (S2-S14). The supplementary material itself was not provided.
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S23, S2-S14), full experimental details for synthesis and enantiomer resolution, raw TRIR kinetic data, MD simulation trajectories and force field parameters, and details of the binding constant fitting procedure.

## Reviewer
- **Overall assessment** This manuscript presents a well-structured and technically sound study combining time-resolved infrared spectroscopy with molecular dynamics simulations to characterize the binding of a ruthenium polypyridyl complex to G-quadruplex DNA. The use of an excited-state amplified nitrile IR probe is a novel and potentially powerful approach. The combination of the "site effect" with the nitrile environmental sensitivity is clever and provides complementary information. However, the manuscript would be strengthened by a more critical discussion of the limitations of the MD approach, particularly the use of MM-ISMSA without entropic contributions, and by a clearer presentation of the uncertainty in the experimental measurements. The claim of "excellent agreement" between MD and TRIR is somewhat overstated given the qualitative nature of the comparison.
- **Who would be interested in the results, and why** Researchers in the fields of bioinorganic chemistry, nucleic acid structure and recognition, photochemistry, and the development of diagnostic and therapeutic agents targeting G-quadruplexes. The methodological advance of using an excited-state IR probe to report on local environment in DNA binding sites will be of interest to the spectroscopy community. The detailed MD analysis of enantiomer-specific binding modes will interest computational chemists studying ligand-DNA interactions.
- **Major strengths**
  1. The concept of using an excited-state amplified nitrile IR probe to report on the binding site environment is novel and well-executed.
  2. The combination of TRIR "site effect" (identifying which bases are perturbed) with the nitrile shift (reporting on local polarity/H-bonding) and lifetime analysis (reporting on solvent access) provides a multi-faceted view of the binding site.
  3. The systematic MD study, considering multiple binding approaches for both enantiomers and both G4 topologies, is thorough and provides a plausible structural basis for the spectroscopic observations.
  4. The manuscript is generally well-written and the logic is easy to follow.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Data interpretation
  - **Claim pointer** The manuscript claims "excellent agreement" between the MD-identified binding sites and the TRIR-observed base perturbations (e.g., "which are in excellent agreement with the observed TRIR solution study").
  - **Evidence pointer** Results sections "TRIR Studies of G4 Bound Systems" and "MD Simulations of Λ-1 and Δ-1 to Hybrid htel(K)" and "MD Simulations of Λ-1 and Δ-1 to Antiparallel htel(Na)"; Figures 4, 5, 7, 9; Tables 2, 3.
  - **Concern** The agreement between MD and TRIR is presented as "excellent," but the comparison appears to be largely qualitative. The TRIR data identifies which bases are perturbed (e.g., guanine vs. thymine/adenine), while the MD identifies the most favorable binding site. It is not clear how the magnitude of the predicted ΔGbinding differences between sites translates to an expected population distribution, nor how the predicted structural models quantitatively explain the observed nitrile shifts (e.g., 4-5 cm⁻¹ for htel(K) vs. 2-5 cm⁻¹ for htel(Na)). A more quantitative comparison, such as calculating the expected nitrile frequency shift from the MD trajectories using a Stark model, or at least a more nuanced discussion of the limitations of the comparison, is needed to support the "excellent agreement" claim.
  - **Why it matters** The central thesis of the paper is that the combination of TRIR and MD provides a detailed and reliable picture of the binding site. If the agreement is only qualitative, the strength of this conclusion is weakened. Overstating the agreement could mislead readers about the predictive power of the MD approach.
  - **Resolution test** The authors should either (a) provide a quantitative metric for the agreement (e.g., correlation between predicted contact distances and observed spectral shifts), (b) perform MD-based spectral prediction (e.g., using a vibrational Stark shift model calibrated on the DMSO/water data), or (c) temper the language to "qualitative agreement" and explicitly discuss the limitations of the comparison.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Methodology
  - **Claim pointer** The manuscript states that the binding constants (Kb) were determined by fitting changes at 380 nm to a "modified binding model developed by Bard et al." and reports values ranging from 10⁵ to 10⁷ M⁻¹.
  - **Evidence pointer** Results section "Visible Absorption Quadruplex Binding Studies"; Figure 2; Figure S3; Table 1.
  - **Concern** The description of the binding constant determination is very brief. The "modified binding model" is not described, and the fitting procedure, the number of independent titrations, and the error estimates on the Kb values are not provided. The reported errors (e.g., ±0.6 × 10⁷) appear to be fitting errors, not standard deviations from multiple experiments. This lack of detail makes it difficult to assess the reliability of the Kb values and the subsequent interpretation of enantiomer selectivity.
  - **Why it matters** The Kb values are used to support the claim of enantiomer-selective binding and to rank the affinity of the complex for different G4 structures. If the fitting model is not properly described or the errors are underestimated, the conclusions about relative affinity could be unreliable.
  - **Resolution test** The authors should provide a more detailed description of the binding model, the fitting procedure, the number of replicates, and the standard deviation of the Kb values. A representative fit with residuals should be shown in the main text or SI.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Methodology
  - **Claim pointer** The manuscript states that "Molecular dynamics simulations together with binding energy calculations identify the most favorable binding site for each system" and that the binding energy was calculated using the MM-ISMSA method, noting that "entropic contributions were not included but assumed to be equivalent for all of the binding modes considered."
  - **Evidence pointer** Results section "MD Simulations of Λ-1 and Δ-1 to Hybrid htel(K)" and "MD Simulations of Λ-1 and Δ-1 to Antiparallel htel(Na)"; Methods section "Computational Modeling"; Tables 3, S3-S10.
  - **Concern** The assumption that entropic contributions are equivalent across different binding modes is a significant approximation that is not adequately justified. The binding modes differ in their contacts with loops and the degree of solvent exposure, which could lead to substantially different entropic penalties (e.g., due to restriction of ligand or loop flexibility). The manuscript does not discuss the potential impact of this approximation on the ranking of binding sites.
  - **Why it matters** The identification of the "most favorable binding site" is a key result of the MD study. If the ranking is significantly affected by the neglected entropic contributions, the agreement with TRIR could be coincidental or less robust than claimed.
  - **Resolution test** The authors should either (a) estimate the entropic contributions (e.g., using normal mode analysis or quasi-harmonic methods) for the top binding modes, or (b) discuss the potential limitations of this assumption and how it might affect the ranking of binding sites. A sensitivity analysis, such as comparing rankings based on different energy components (e.g., VdW vs. electrostatic), would also be informative.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction, paragraph 1
  - **Evidence pointer** Location not provided
  - **Issue** The introduction is dense and assumes significant background knowledge. The significance of G-quadruplex structures in cancer and the rationale for targeting them with metal complexes could be explained more clearly for a broader audience.
  - **Required correction** Consider adding a brief, accessible explanation of what G-quadruplexes are and why they are important therapeutic targets, perhaps with a simple schematic in Figure 1.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness / Data presentation
  - **Affected element** Results section "TRIR Studies of G4 Bound Systems"; Figures 4 and 5.
  - **Evidence pointer** Location not provided
  - **Issue** The TRIR spectra in Figures 4 and 5 are described in the text, but the figure captions are not provided in the manuscript text. It is difficult to fully assess the data without seeing the figures and their captions.
  - **Required correction** Ensure that the figure captions are complete and self-explanatory, including the time delays at which spectra were recorded and the assignment of the bands.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness / Methodology
  - **Affected element** Methods section "Computational Modeling"
  - **Evidence pointer** Location not provided
  - **Issue** The description of the MD simulation setup is missing some key details, such as the specific force field parameters for the ruthenium complex (beyond "ad hoc parametrized charges"), the water box dimensions, and the salt concentration.
  - **Required correction** Provide more complete details of the simulation setup to ensure reproducibility.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness / Data interpretation
  - **Affected element** Discussion section, paragraph 2
  - **Evidence pointer** Location not provided
  - **Issue** The discussion of the 1690 cm⁻¹ band attributed to a "shift of a guanine carbonyl vibration" is speculative. The authors should consider alternative explanations, such as a change in the vibrational coupling or a contribution from a different base.
  - **Required correction** Acknowledge the speculative nature of this assignment and discuss possible alternative interpretations.

## Risk / unsupported claims
- The claim of "excellent agreement" between MD and TRIR is not quantitatively supported and may be overstated.
- The assignment of the 1690 cm⁻¹ transient to a specific guanine carbonyl shift is speculative and not fully supported by the data presented.
- The assumption of equivalent entropic contributions in the MM-ISMSA binding energy calculations is a significant approximation that could affect the ranking of binding sites, and its impact is not discussed.
- The Kb values are reported without sufficient detail on the fitting model and experimental replicates to assess their reliability.
- The claim that the nitrile shift provides a "highly localized reporter" on the environment is plausible but not directly demonstrated; the spatial resolution of the probe is not quantified.