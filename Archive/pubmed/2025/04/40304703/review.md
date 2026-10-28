## Review setup
- **Input scope** Full manuscript text, including abstract, main text, figures (referenced but not provided), supplementary figure references, and methods.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with stated conclusions. Not assessed: editorial quality, formatting, or grammatical issues.
- **Shared manuscript claim summary** The authors use the artificial membrane protein ROCKET to dissect determinants of cardiolipin (CDL) binding and stabilization. They combine coarse-grained and atomistic molecular dynamics simulations with native mass spectrometry and cryo-EM to show that inter-helix CDL binding stabilizes the tetramer, while distal binding does not. They extend these findings to identify a stabilizing CDL site in the E. coli rhomboid protease GlpG, which modulates substrate preference.
- **Visible evidence base** Main text, methods section, figure legends (not all figures provided), supplementary figure references, and data availability statement.
- **Missing materials affecting confidence** Figures and supplementary figures (including Figure 1—figure supplement 1, Figure 2—figure supplements 1-3, Figure 3—figure supplements 1-2, Figure 4—figure supplements 1-2), supplementary tables (S1-S3), and cryo-EM density maps (EMD-50106, EMD-50107) were not provided. These are essential for evaluating the validity of the structural and quantitative claims.

## Reviewer
- **Overall assessment** This manuscript presents a well-designed, multi-method study that addresses a significant question in membrane protein biology: what features distinguish stabilizing from non-stabilizing lipid interactions. The use of a designed protein scaffold is a creative and powerful approach. The combination of MD simulations and native MS is appropriate and well-executed. The identification of a CDL site in GlpG with functional consequences is a valuable extension. However, the absence of key figures and supplementary data prevents full verification of several central claims, particularly the quantitative MS data and the cryo-EM analysis. The claim that the identified features are generalizable to natural proteins is plausible but not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in membrane protein biophysics, lipid-protein interactions, structural biology, and computational biology. The work is also relevant to those studying rhomboid proteases and the role of lipids in membrane protein function and stability. The methodological framework (design + simulation + MS) will be of interest to a broad audience.
- **Major strengths**
  1. The use of a de novo designed protein (ROCKET) as a minimal, controllable system to dissect lipid-binding determinants is a major strength, allowing systematic perturbation that is difficult in natural proteins.
  2. The combination of CG-MD, atomistic MD, and native MS provides complementary views of binding, dynamics, and stability.
  3. The finding that inter-helix CDL binding stabilizes the tetramer, while distal binding does not, is a clear and mechanistically insightful result.
  4. The extension to GlpG, showing a functional consequence of CDL binding (substrate preference), demonstrates the broader relevance of the findings.
  5. The honest discussion of the limitations and challenges in predicting stabilizing lipid interactions is commendable.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that native MS shows CDL stabilizes ROCKETAAXWA more than ROCKET, based on reduced monomer release.
  - **Evidence pointer** Figure 2f-g, Figure 3b-d, "location not provided" for raw spectra.
  - **Concern** The quantitative MS data, which is central to the stabilization claims, is not fully visible in the provided text. The method of quantifying monomer release and the statistical treatment (n=4) are described, but the actual spectra and the magnitude of the effect are not shown. The claim that CDL stabilizes ROCKETAAXWA more than ROCKET is based on a comparison of monomer peak intensities, but without seeing the data, it is impossible to assess whether the effect is robust and specific.
  - **Why it matters** The central conclusion of the paper—that inter-helix binding stabilizes while distal binding does not—rests on this MS data. If the effect is small or variable, the conclusion is weakened.
  - **Resolution test** Provide the raw and processed MS data (e.g., spectra showing monomer/tetramer peaks with and without CDL for all variants) and a clear statistical analysis demonstrating the significance of the differences.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that cryo-EM confirms the overall structure of ROCKET and ROCKETAAXWA is preserved and shows diffuse density consistent with CDL at Site 2.
  - **Evidence pointer** Figure 2—figure supplement 1, Supplementary file 1, table S1.
  - **Concern** The cryo-EM maps are referenced but not shown. The resolution (3.8 and 3.9 Å) is stated, but the quality of the maps, the local resolution, and the interpretation of the diffuse density as CDL cannot be evaluated. The claim that the mutations do not disrupt the structure is important for the interpretation of the MS data, but it cannot be verified.
  - **Why it matters** The structural integrity of the variants is a prerequisite for attributing differences in stability to the designed mutations. The interpretation of the diffuse density as CDL is a key piece of evidence for the binding mode.
  - **Resolution test** Show the cryo-EM maps with the model overlaid, including a clear representation of the diffuse density and its assignment to CDL. Provide validation metrics (FSC curves, etc.).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Claim strength
  - **Claim pointer** The claim that the features identified in ROCKET (inter-helix binding, local flexibility) can be used to identify functionally relevant CDL sites in natural proteins, specifically GlpG.
  - **Evidence pointer** Figure 4, "location not provided" for the database.
  - **Concern** The identification of the GlpG site is based on a database screen and MD simulations. The functional data (substrate preference) is compelling, but the causal link between CDL binding at this specific site and the observed effect on substrate preference is not fully established. The authors show that CDL inhibits cleavage of a transmembrane substrate, but it is not shown that this is due to binding at the identified site (e.g., via a mutant that abrogates CDL binding).
  - **Why it matters** The claim that the ROCKET-based design principles can predict functional lipid sites in natural proteins is a key translational aspect of the work. Without a direct test of the role of the identified site, the claim remains correlative.
  - **Resolution test** Perform a mutation in GlpG that disrupts the identified CDL binding site (e.g., R92A/K167A) and show that this abolishes the CDL effect on substrate cleavage and/or thermal stability.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "Gas-phase molecular dynamics simulations"
  - **Evidence pointer** Methods section, "location not provided"
  - **Issue** The description of the gas-phase MD simulations is brief. The rationale for the specific pulling protocol and the choice of the 16+ charge state could be explained more clearly.
  - **Required correction** Expand the methods to clarify the choice of charge state and the pulling setup, and how this relates to the experimental MS conditions.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion
  - **Evidence pointer** Discussion, "location not provided"
  - **Issue** The discussion of the limitations of the gas-phase stability measurements is good, but it could be more explicit about how the gas-phase results might differ from solution-phase behavior.
  - **Required correction** Add a sentence or two acknowledging that gas-phase stability is not a direct proxy for solution stability and that the relative stabilization observed may be influenced by the transfer to the gas phase.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 4
  - **Evidence pointer** Figure 4, "location not provided"
  - **Issue** The thermal shift assay data in Figure 4c is described in the text, but the figure itself is not provided. The magnitude of the stabilization and the error bars are not visible.
  - **Required correction** Ensure the figure is included in the final version and that the data is clearly presented with appropriate statistical analysis.

## Risk / unsupported claims
- The claim that CDL stabilizes ROCKETAAXWA more than ROCKET is not fully verifiable without the raw MS data.
- The claim that the cryo-EM density is consistent with CDL at Site 2 is not verifiable without the maps.
- The claim that the identified features in ROCKET can predict functional CDL sites in natural proteins is plausible but not fully established, as the role of the specific GlpG site is not directly tested.
- The claim that the ROCKET scaffold is "extraordinarily stable" is stated but not quantified in the provided text.