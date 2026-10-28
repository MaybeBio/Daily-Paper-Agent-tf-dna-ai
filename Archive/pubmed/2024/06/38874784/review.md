## Review setup
- **Input scope** Full manuscript text including Introduction, Materials and methods, Results, Discussion, and figure legends
- **Assessment boundary** Scientific claims, methodological soundness, and evidence consistency within the provided manuscript
- **Shared manuscript claim summary** The authors use molecular dynamics simulations and experimental biophysics to propose that eight directed-evolution mutations in the TadA8e deaminase of the adenine base editor ABE8e enhance DNA-binding affinity primarily through increased positive charge density in the DNA-binding region, and that these mutations also increase protein thermal stability, together contributing to the editor's high catalytic activity.
- **Visible evidence base** MD simulation analyses (RMSD, Rg, free energy landscapes, MM/PBSA binding energies, per-residue decomposition), APBS electrostatic surface calculations, MST binding measurements, nanoDSF thermal stability assays, and in-cell base editing reversion experiments at three genomic loci
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; raw MD trajectory data not available; sequence-level details of guide RNAs and target sites not fully specified; statistical analysis details for MST and editing efficiency comparisons not described

## Reviewer
- **Overall assessment** The manuscript addresses a mechanistically important question in base editor engineering, namely how directed evolution improved the catalytic performance of ABE8e. The combination of MD simulation with experimental validation is appropriate and the central claim that the mutations enhance DNA binding and protein stability is plausible. However, the evidence as presented has several gaps. The MM/PBSA binding energy calculations are used to support a quantitative claim about binding affinity ratios, but the method is known to be sensitive to setup parameters and the manuscript does not report convergence or error estimates. The MST experiments measure binding to a short ssDNA substrate that may not recapitulate the full nucleic acid context of the editor, and the reported Kd values lack confidence intervals. The thermal stability measurements are clear but limited to two constructs. The in-cell reversion experiments are supportive but the editing efficiency data are presented without statistical testing. The structural interpretation of how the mutations reorganize the electrostatic surface is qualitatively compelling but would benefit from direct comparison of simulated and experimental structures. Overall, the case is directionally supported but not fully established from the provided evidence.

- **Who would be interested in the results, and why** Researchers in genome editing, protein engineering, and CRISPR biology would be interested. The work provides a mechanistic rationale for the improved activity of ABE8e, which is directly relevant to efforts aimed at engineering next-generation base editors with higher efficiency and specificity. The finding that electrostatic steering dominates DNA substrate recognition could inform rational design of other deaminase-based editors. The thermal stability data are also relevant to those interested in the biophysical properties of gene editing reagents for therapeutic applications.

- **Major strengths**
  - The study addresses a clearly defined and mechanistically important question about the molecular basis of directed evolution in a widely used genome editing tool.
  - The combination of computational and experimental approaches is appropriate and mutually reinforcing.
  - The identification of specific residues (R111, N119, N167) and their validation through reversion mutations provides a concrete and testable model.
  - The thermal stability measurements add a distinct and valuable dimension beyond binding affinity.
  - The discussion of dimerization independence is an interesting and potentially actionable insight.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of binding energy calculations
- **Claim pointer** The manuscript claims that "the DNA-binding affinity of TadA8e was approximately 1.9~8.9 times that of TadA7.10" based on MM/PBSA calculations.
- **Evidence pointer** Results section, Figure 3A, Figure S4
- **Concern** The MM/PBSA method is known to produce absolute binding energies that are highly sensitive to the choice of dielectric constants, entropic contributions, and the conformational ensemble used. The manuscript reports ratios of binding energies across four dielectric constants, but does not provide standard errors, convergence checks, or a demonstration that the ranking is robust beyond the specific simulation trajectories analyzed. The range of 1.9 to 8.9 fold is very wide, which weakens the quantitative claim. Additionally, the manuscript does not report whether the binding energy differences between TadA7.10 and TadA8e are statistically significant given the fluctuations in the MD trajectories.
- **Why it matters** The quantitative claim about binding affinity enhancement is a central pillar of the paper. If the MM/PBSA results are not robust, the conclusion that the mutations enhance DNA binding through electrostatics is not firmly supported.
- **Resolution test** Provide per-replica or block-averaged binding energies with standard deviations, demonstrate convergence of the MM/PBSA estimates over the simulation time, and show that the ranking of TadA8e versus TadA7.10 is consistent across multiple independent simulations or alternative analysis methods (e.g., umbrella sampling, FEP).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation of binding affinity
- **Claim pointer** The manuscript states that MST measurements show the Kd of TadA7.10-3mut is approximately 2.8 times lower than that of TadA7.10, supporting the role of the three key mutations in enhancing DNA binding.
- **Evidence pointer** Results section, Figure 5A
- **Concern** The MST experiments use a 19-nt ssDNA substrate that was engineered to avoid secondary structure, but this substrate may not represent the physiological nucleic acid context in which ABE8e operates. The manuscript does not report the error or confidence interval for the Kd values, nor the number of independent replicates used for the reported mean. The difference between 106.1 nM and 38.5 nM is reported without statistical testing, so it is unclear whether this difference is significant given typical MST variability. Additionally, the manuscript does not report whether the purified TadA7.10-3mut protein is properly folded and monomeric under the assay conditions, which could affect the measured affinity.
- **Why it matters** The MST data are the primary experimental evidence for the binding affinity claim. Without error estimates and statistical testing, the strength of the conclusion is uncertain.
- **Resolution test** Report Kd values with standard errors from at least three independent MST experiments, include a statistical test (e.g., t-test) comparing the two Kd values, and characterize the oligomeric state and folding of the purified proteins (e.g., by SEC-MALS or CD).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural interpretation of electrostatic changes
- **Claim pointer** The manuscript claims that the mutations D119N and D167N eliminate electrostatic repulsions, allowing the R153-K161 loop to move closer to the active site and form a continuous positively charged surface.
- **Evidence pointer** Results section, Figure 3C, Figure 4B-C
- **Concern** The structural interpretation is based on MD simulations of homology models, not on experimentally determined structures of the mutant and wild-type proteins. The manuscript does not provide validation of the homology models (e.g., comparison to the cryo-EM structure of ABE8e) or an assessment of whether the observed loop movement is statistically significant across the simulation ensemble. The distance measurements between residues 119 and 167 are reported as single values, without distributions or error bars, making it difficult to assess the reliability of the claim.
- **Why it matters** The proposed mechanism of electrostatic surface reorganization is a key explanatory element. If the structural changes are not robustly supported, the mechanistic model is weakened.
- **Resolution test** Provide distance distributions with confidence intervals, compare the simulated wild-type and mutant structures to any available experimental structures, and consider validating the loop conformation with enhanced sampling or experimental structural data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical analysis of in-cell editing data
- **Claim pointer** The manuscript states that reversion mutations reduce the editing activity of ABE8e, with specific effects for R111T, N119D, N167D, and the double mutant.
- **Evidence pointer** Results section, Figure 5B
- **Concern** The editing efficiency data are presented as individual dots with mean and SD, but no statistical test is reported to compare the variants to the wild-type ABE8e. The number of biological replicates is stated as three, but it is unclear whether the differences observed are statistically significant given the variability. Additionally, the manuscript does not report the transfection efficiency or the expression levels of the different ABE8e variants, which could confound the editing efficiency measurements.
- **Why it matters** The in-cell data are used to link the biophysical findings to functional activity. Without statistical analysis, the claim that the mutations affect editing activity is not rigorously supported.
- **Resolution test** Perform appropriate statistical tests (e.g., one-way ANOVA with post-hoc comparisons) and report p-values. Include controls for transfection efficiency and protein expression levels.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** MD simulation setup
- **Evidence pointer** Materials and methods, "MD simulations and analyses"
- **Issue** The manuscript states that the systems were equilibrated after 150 ns based on RMSD stabilization, but does not report the number of independent simulations or the total simulation time per system beyond the 500 ns production run. It is unclear whether the results are based on a single trajectory per system.
- **Required correction** Specify the number of replicate simulations and report the total simulation time. If only one trajectory per system was used, acknowledge this limitation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** MST binding experiments
- **Evidence pointer** Materials and methods, "Microscale thermophoresis (MST)"
- **Issue** The MST buffer composition is not fully described, and the manuscript does not state whether the DNA substrate was labeled at the 5' end only or if any quenching or competitor DNA was used.
- **Required correction** Provide the full buffer composition and any additional experimental details needed to reproduce the MST measurements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of thermal stability data
- **Affected element** Thermal shift assay results
- **Evidence pointer** Results section, Figure 6C
- **Issue** The manuscript reports Tm values for TadA7.10, TadA8e, miniABEmax, and ABE8e, but does not discuss whether the increased thermal stability of TadA8e is due to the mutations alone or to the different fusion context (e.g., the presence of the second TadA in the dimer).
- **Required correction** Clarify whether the Tm differences are attributable to the eight mutations or to other differences in the constructs.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion, final paragraph
- **Issue** The manuscript acknowledges the difficulty of measuring binding affinity for TadA8e but does not discuss the limitations of the MM/PBSA approach or the potential for the MD simulations to be biased by the initial homology model.
- **Required correction** Add a paragraph acknowledging the limitations of the computational methods and the need for experimental structural validation.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of error estimates and convergence analysis for MM/PBSA binding energies
  - R1-M2: Missing statistical analysis and error reporting for MST Kd values
  - R1-M3: Insufficient validation of structural interpretations from homology models
  - R1-M4: Absence of statistical testing for in-cell editing efficiency comparisons

- **Assessment against Nature-style criteria**
  - **Originality** The work is not entirely novel in concept, as the role of electrostatic interactions in DNA binding by deaminases has been discussed, but the specific focus on the eight directed-evolution mutations of TadA8e and the combination of MD with experimental validation provides a useful contribution.
  - **Scientific importance** The findings are of moderate importance. Understanding why ABE8e is more active than earlier editors is relevant for the field, but the study does not provide a transformative new principle or a broadly generalizable mechanism.
  - **Interdisciplinary readership** The topic is of interest to genome editing and protein engineering communities, but the methods and findings are unlikely to attract a broad interdisciplinary audience beyond these fields.
  - **Technical soundness** The technical approach is appropriate but the execution has gaps in statistical rigor and validation, as detailed in the major concerns.
  - **Readability for nonspecialists** The manuscript is generally well written and accessible, with clear figures and a logical structure, though some sections assume familiarity with MD simulation methods.

- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is plausible and the combination of methods is appropriate, but the quantitative claims require stronger statistical support and the structural interpretations need validation. If the authors can provide error estimates, convergence analyses, and statistical testing, the case would be substantially strengthened.

## Risk / unsupported claims
- The claim that "the DNA-binding affinity of TadA8e was approximately 1.9~8.9 times that of TadA7.10" is not fully supported due to lack of error estimates and convergence analysis in the MM/PBSA calculations.
- The claim that the three mutations (R111, N119, N167) are the key determinants of enhanced DNA binding is supported by the reversion experiments, but the quantitative contribution of each mutation is not established.
- The claim that the mutations increase thermal stability is supported by the nanoDSF data, but the mechanistic link between thermal stability and catalytic activity is not directly demonstrated.
- The statement that "dimerisation may not be a prerequisite for binding to the DNA substrate" is speculative and based on indirect evidence from simulations.
- The in-cell editing efficiency data are presented without statistical analysis, so the claim that specific mutations reduce activity is not rigorously established.