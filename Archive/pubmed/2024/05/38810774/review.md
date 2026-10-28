## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors use ITC, NMR spectroscopy, and MD simulations to characterize secondary p53 binding sites on MDM2 and MDMX, proposing that differences in binding thermodynamics, conformational entropy, and structural adaptation of a methionine-aromatic motif explain differential binding of p53 fragments and inform selective inhibitor design.
- **Visible evidence base** Tables 1, Figures 1-7, SI Tables 1-8, SI Figures 1-17, Methods section
- **Missing materials affecting confidence** Raw ITC thermograms, NMR spectral overlays, MD trajectory validation metrics, force field parameter details, statistical error analysis for ΔCp fits, and full supplementary appendices referenced but not provided

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive thermodynamic and structural investigation of secondary p53 binding sites on MDM2 and MDMX, combining experimental calorimetry with computational simulations. The work addresses a relevant question in cancer biology regarding selective inhibitor design. However, several claims regarding the molecular basis of binding differences are inferred from indirect measurements and simulations without direct experimental validation. The interpretation of ΔCp data, particularly the attribution of differences to conformational entropy versus binding site interactions, requires more rigorous support. The manuscript would benefit from clearer presentation of error analysis and more cautious interpretation of simulation-derived conclusions.

- **Who would be interested in the results, and why** Researchers in the fields of protein-protein interactions, intrinsically disordered proteins, cancer biology, and drug discovery would find these results relevant. The thermodynamic characterization of p53-MDM2/MDMX binding and the proposed role of secondary binding sites in selective inhibitor design are of interest to those studying p53 pathway regulation and developing therapeutics targeting MDM2/MDMX.

- **Major strengths**
  1. Comprehensive thermodynamic characterization using multiple p53 peptide fragments of varying lengths
  2. Integration of experimental (ITC, NMR) and computational (MD simulations) approaches
  3. Novel observation regarding the role of MDM2 disordered tails in modulating secondary site binding
  4. Identification of a methionine-aromatic motif as a potential structural determinant of binding mode differences
  5. Direct comparison of MDM2 and MDMX secondary site properties relevant to inhibitor selectivity

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation and claim support
- **Claim pointer** The authors claim that "MDMX has a higher affinity and more negative ΔCp than MDM2 for p5317-35, which is due to MDMX stabilization and not additional interactions with the secondary binding site."
- **Evidence pointer** Table 1, Figure 3, Results section "Thermodynamics of p53 binding to MDMX"
- **Concern** The attribution of higher affinity and more negative ΔCp to "MDMX stabilization" rather than secondary site interactions is not directly supported by the presented data. The ΔCp measurements alone cannot distinguish between stabilization of the protein and additional binding interactions. The MD simulations show differences in flexibility but do not provide quantitative free energy decomposition. The claim requires either direct experimental evidence of MDMX stabilization (e.g., from NMR relaxation or hydrogen-deuterium exchange) or a more rigorous thermodynamic decomposition.
- **Why it matters** This claim is central to the mechanistic interpretation of the binding differences between MDM2 and MDMX. If incorrect, the proposed model for selective inhibitor design would be based on a flawed premise.
- **Resolution test** Provide direct experimental evidence of MDMX stabilization upon p53 binding, such as changes in MDMX dynamics from NMR relaxation measurements, or perform a rigorous thermodynamic decomposition using mutant constructs that isolate secondary site contributions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and data completeness
- **Claim pointer** The authors state that "ΔCp measurements show binding to the secondary site is inhibited by the disordered tails of MDM2 for WT p53 but not a more helical mutant where proline 27 is changed to alanine."
- **Evidence pointer** Table 1, Figure 3, Results section "Thermodynamics of p53 binding to MDM2"
- **Concern** The comparison between MDM217-125 (with tails) and MDM225-109 (without tails) is only performed for the 17-35 peptides. The claim that disordered tails inhibit secondary site binding for WT p53 is based on a single comparison. Additionally, the ΔCp differences between p5317-35 and P27A17-35 binding to MDM217-125 versus MDM225-109 are interpreted as evidence of tail displacement, but no direct structural or dynamic evidence for tail displacement is provided. The NMR titration data (Figure 7) do not show significant differences in the C-terminal tail region between WT and P27A binding.
- **Why it matters** The proposed model of tail displacement contributing to binding thermodynamics is a key mechanistic claim. Without direct evidence, alternative explanations (e.g., differences in peptide conformation, solvation effects) cannot be excluded.
- **Resolution test** Perform NMR relaxation dispersion or CPMG experiments on the MDM2 tail region in the presence and absence of p5317-35 and P27A17-35 to directly demonstrate tail displacement. Alternatively, use mutant MDM2 constructs with truncated or stabilized tails to test the functional role of the tail.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational methodology and validation
- **Claim pointer** The authors use MD simulations to propose that "an intramolecular methionine-aromatic motif found in both MDM2 and MDMX structurally adapts to support multiple p53 binding modes with the secondary site."
- **Evidence pointer** Figure 6, SI Figures 3-5, Results section "Structural adaptation of the secondary binding sites"
- **Concern** The MD simulation methodology lacks sufficient validation details. The manuscript does not report convergence criteria, force field validation against experimental data, or error estimates for the simulation-derived quantities. The DiCE method is described but its sensitivity to simulation length and starting conditions is not discussed. The claim of "structural adaptation" is based on ensemble comparisons, but the statistical significance of the observed differences is not established.
- **Why it matters** The simulation-derived conclusions about structural adaptation and binding modes are used to support the overall mechanistic model. Without proper validation, these conclusions may not be robust.
- **Resolution test** Provide convergence analysis (e.g., block averaging, multiple independent runs), validate the force field against experimental observables (e.g., chemical shifts, NOEs), and perform statistical tests to establish the significance of ensemble differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative analysis and error propagation
- **Claim pointer** The authors estimate conformational entropy changes from NMR order parameters and compare them to ITC-derived entropy values, claiming "excellent correspondence" between the two methods.
- **Evidence pointer** Results section "Estimating the conformational entropy of unbound p53", SI Tables 6-7, Figure 8
- **Concern** The conversion of order parameters to conformational entropy using the Yang-Kay and Wand methods involves significant assumptions and approximations. The manuscript does not provide error estimates for the calculated entropy values, nor does it discuss the limitations of these methods for intrinsically disordered proteins. The comparison between ITC-derived and NMR-derived entropy values is presented without statistical analysis.
- **Why it matters** The quantitative agreement between two independent methods strengthens the mechanistic interpretation. However, without proper error analysis, the "excellent correspondence" claim is not rigorously supported.
- **Resolution test** Provide error propagation for the entropy calculations, discuss the sensitivity of results to assumptions in the Yang-Kay and Wand methods, and perform a statistical comparison (e.g., t-test or confidence intervals) between the ITC and NMR-derived values.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Results section "Thermodynamics of p53 binding to MDM2"
- **Evidence pointer** Table 1
- **Issue** The table presents KD, ΔG, ΔH, −TΔS, and −TΔΔS values but does not include the number of replicates or the statistical significance of differences between constructs. The text states "two to four titrations" were averaged, but individual values and standard deviations are not shown for all conditions.
- **Required correction** Include the number of independent titrations for each condition and clearly indicate which differences are statistically significant. Consider adding a supplementary table with all individual measurements.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology transparency
- **Affected element** Methods section "Molecular dynamics (MD) simulations"
- **Evidence pointer** Methods section
- **Issue** The description of the MD simulations lacks specific details on the number of replicates, total simulation time per system, equilibration protocol, and criteria for determining when simulations reached equilibrium. The statement "a total of 52 μs of MD simulations" is provided, but the breakdown per system is only in SI Table 8.
- **Required correction** Provide a clear summary of simulation setup in the main text, including the number of independent runs, simulation length per run, and equilibration criteria. Ensure SI Table 8 is referenced appropriately.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "NMR spectroscopy titrations for MDM2 and MDMX"
- **Evidence pointer** Figure 7
- **Issue** The chemical shift perturbation data are presented as bar graphs, but the threshold for significant chemical shift changes is not defined. The text mentions changes "greater than 0.1 ppm" but does not justify this threshold or discuss how it compares to the digital resolution.
- **Required correction** Define the significance threshold for chemical shift perturbations based on the digital resolution and spectral noise, and clearly state this in the figure legend or text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of simulation data
- **Affected element** Results section "Structural adaptation of the secondary binding sites"
- **Evidence pointer** Figure 6, SI Figure 3
- **Issue** The claim that the methionine-aromatic motif "structurally adapts" is based on ensemble comparisons, but the manuscript does not provide representative structures or a clear description of the conformational changes. The distance and angle distributions are mentioned but not shown in the main text.
- **Required correction** Include representative structures or a schematic illustrating the proposed conformational adaptation. Show the distance and angle distributions in the main text or a clearly referenced supplementary figure.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction
- **Issue** The introduction mentions "emerging evidence for the presence of secondary binding sites" but does not critically evaluate prior studies that may have reached different conclusions. The discussion of previous thermodynamic studies is limited.
- **Required correction** Expand the discussion of prior work on secondary p53 binding sites, including any conflicting results, to better contextualize the novelty of the current findings.

## Risk / unsupported claims
- The claim that "MDMX stabilization" rather than secondary site interactions explains higher affinity and more negative ΔCp is not directly supported by the presented data.
- The claim that disordered tails of MDM2 inhibit secondary site binding for WT p53 is based on limited comparisons and lacks direct structural evidence.
- The proposed "structural adaptation" of the methionine-aromatic motif is inferred from simulations without experimental validation or statistical significance testing.
- The "excellent correspondence" between ITC-derived and NMR-derived entropy values is presented without error analysis or statistical comparison.
- The conclusion that results "will facilitate the design of selective p53 inhibitors" is speculative and not directly demonstrated by the data.