## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, funding, acknowledgements)
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence. No assessment of formatting or editorial style beyond readability.
- **Shared manuscript claim summary** The authors present a quantitative model for ligand binding to topologically closed DNA, where the global constraint of fixed linking number modulates binding affinity in a manner dependent on initial supercoiling and ligand concentration. They validate this model using bulk fluorescence measurements with intercalating dyes (EtBr, SYBR Gold), reanalysis of published psoralen crosslinking data, and single-molecule fluorescence assays with SYTOX Orange.
- **Visible evidence base** Abstract, full introduction, full methods section, full results section, full discussion, data availability statement, funding and acknowledgements. Figures are referenced but not provided. Supplementary figures and movies are referenced but not provided. Table 1 is referenced but not provided.
- **Missing materials affecting confidence** Figures 1-6, Supplementary Figures S1-S7, Supplementary Movies S1-S2, Table 1, and the referenced equations (Equations 1-7) are not included in the provided material. The MATLAB code is available at a repository but was not inspected.

## Reviewer
- **Overall assessment** This manuscript addresses a genuinely important and under-explored problem: how the global topological constraint of closed circular DNA modulates the binding equilibrium of intercalating ligands. The authors develop a physically motivated model that couples McGhee-von Hippel binding isotherms with torsional mechanics, and they test it across multiple experimental platforms. The conceptual framework is sound and the results, as described, appear to support the central claim that topology can either enhance or suppress binding depending on the sign and magnitude of supercoiling and the ligand concentration relative to Kd. The single-molecule experiments add a dynamic dimension that strengthens the study. However, the absence of the actual figures, tables, and equations in the provided material prevents full verification of the quantitative claims. The model relies on several assumptions (e.g., fixed twist-writhe partitioning, constant torsional stiffness upon intercalation) that are stated but not critically examined. The claim that psoralen crosslinking is "quantitatively accounted for" by the model is based on reanalysis of published data, and the strength of this claim cannot be fully assessed without seeing the comparison. Overall, this is a promising and potentially impactful contribution, but the evidence base as provided is incomplete for a definitive judgment.
- **Who would be interested in the results, and why** Researchers studying DNA-ligand interactions, DNA supercoiling and topology, chromatin structure and function, and developers of DNA detection and quantification assays. The work is also relevant to the biophysics community interested in mechanochemical coupling in biomolecules. The practical guidance on choosing dye concentrations to avoid topological bias in DNA quantification will be of direct use to many laboratories.
- **Major strengths** 1. The conceptual framing is clear and important: topology as a global constraint that fundamentally alters binding equilibria is a point that has been underappreciated. 2. The model is physically grounded and integrates established components (McGhee-von Hippel, White's theorem, torsional mechanics) in a novel way. 3. The multi-platform experimental validation (bulk fluorescence, gel electrophoresis, plate reader, qPCR, single-molecule) is comprehensive and convincing in scope. 4. The single-molecule experiments provide kinetic information that goes beyond equilibrium measurements. 5. The practical recommendations for unbiased DNA quantification are valuable and actionable.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
- **Technical failings that need to be addressed before the case is established** R1-M1 (model assumptions), R1-M2 (missing quantitative verification), R1-M3 (psoralen claim strength)
- **Assessment against Nature-style criteria** Originality: High. The concept of topology-dependent binding is not entirely new, but the quantitative framework and the breadth of experimental validation are novel. Scientific importance: High. The work has implications for basic understanding of DNA transactions in cells and for practical applications in DNA detection. Interdisciplinary readership: Moderate to high. The topic bridges biophysics, molecular biology, and analytical chemistry. Technical soundness: Cannot be fully assessed from the provided material. The model derivation is plausible, but the missing figures and equations prevent verification of the quantitative fits and error analysis. Readability for nonspecialists: The main text is generally well written and accessible, though the model section is dense. The abstract is clear and compelling.
- **Recommendation posture** Supportive if technical concerns are resolved. The central idea is strong and the experimental approach is appropriate, but the manuscript as provided does not allow full verification of the quantitative claims. The authors should be encouraged to resubmit with the complete set of figures, tables, and equations, and with a more critical discussion of model assumptions.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Model assumptions
- **Claim pointer** The model assumes a fixed partitioning of excess linking number into twist and writhe (approximately 20% twist, 80% writhe) that is independent of the presence of intercalators, and a constant torsional stiffness C that is not altered by intercalation.
- **Evidence pointer** Results section, "Model for ligand binding under topological constraint"; Equations 5 and 6 (not provided in full)
- **Concern** The assumption that twist-writhe partitioning remains unchanged upon intercalation is critical to the model's predictions. Intercalation changes the local helix geometry and bending stiffness, which could plausibly alter the energetic balance between twist and writhe. Similarly, the torsional stiffness C is assumed constant, but intercalation is known to stiffen DNA. The authors state these assumptions but do not justify them with independent evidence or a sensitivity analysis. If the partitioning or stiffness changes with intercalation, the model predictions could shift significantly.
- **Why it matters** The central quantitative claim of the paper, that the model accurately predicts topology-dependent binding, depends on these assumptions. Without justification or a sensitivity analysis, the agreement between model and experiment could be fortuitous or could mask compensating errors.
- **Resolution test** Provide a sensitivity analysis showing how model predictions change with reasonable variations in the twist-writhe partitioning ratio and torsional stiffness. Alternatively, cite direct experimental measurements of these parameters in the presence of intercalators, or perform measurements that constrain them.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative verification
- **Claim pointer** The authors claim "excellent agreement" between model predictions and experimental data across multiple platforms (bulk fluorescence, gel electrophoresis, single-molecule).
- **Evidence pointer** Results sections "DNA topology modulates intercalation", "Topology dependent binding depends on initial topology and intercalator affinity", "Single-molecule assay monitors topology dependent binding in real time"; Figures 2, 3, 5 (not provided)
- **Concern** The manuscript text describes the agreement as "excellent" but the actual figures, fits, residuals, and statistical measures (e.g., R-squared, chi-squared, confidence intervals) are not provided in the material under review. Without these, the strength of the agreement cannot be independently assessed. The claim of "excellent agreement" is a central pillar of the paper and must be verifiable.
- **Why it matters** The paper's main contribution is a quantitative model. The quality of the agreement between model and data is the primary evidence for the model's validity. If the agreement is not rigorously demonstrated, the model's predictive power is not established.
- **Resolution test** Provide the figures with model fits overlaid on data, including residuals and appropriate statistical measures of goodness-of-fit. For the single-molecule data, provide the distribution of ratios and the number of molecules analyzed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim strength for psoralen data
- **Claim pointer** "Our model quantitatively accounts for observations obtained using psoralen for UV-induced DNA crosslinking, which is frequently used to quantify supercoiling in vivo."
- **Evidence pointer** Results section "Psoralen-based DNA crosslinking to quantify DNA supercoiling"; Figure 4 (not provided)
- **Concern** The claim that the model "quantitatively accounts" for psoralen crosslinking data is based on reanalysis of previously published data (references 41 and 43). The manuscript does not describe the details of this reanalysis, the uncertainties in the original data, or the quality of the fit. The statement that "crosslinking is directly proportional to binding" is an assumption that is stated but not tested. The range of supercoiling densities over which the model is valid is also not clearly defined.
- **Why it matters** This is a key application of the model to a widely used experimental technique. If the model's ability to describe psoralen data is overstated, it could mislead researchers who use this technique to quantify supercoiling.
- **Resolution test** Provide the reanalysis details, including the original data, the model fit, and the residuals. Discuss the limitations of the proportionality assumption and the range of supercoiling densities over which the model is applicable.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Single-molecule assay interpretation
- **Claim pointer** The single-molecule assay "provides direct access to binding kinetics and DNA supercoil dynamics."
- **Evidence pointer** Results section "High-speed fluorescence tracking reveals binding dynamics"; Figure 6 (not provided)
- **Concern** The kinetic analysis fits a single exponential to the fluorescence intensity change upon nicking. The authors interpret the fitted rate as the off-rate (for the negative supercoiling case) or on-rate (for the positive supercoiling case) of the dye. However, the process of nicking, writhe relaxation, and dye unbinding/binding are coupled. The authors argue that dye binding/unbinding is rate-limiting based on comparison with published rates, but this argument is indirect. A more direct test would be to vary the dye concentration and show that the off-rate is independent of concentration and the on-rate scales linearly with concentration.
- **Why it matters** The claim of direct access to binding kinetics is a significant selling point of the single-molecule approach. If the interpretation is not rigorously established, the kinetic parameters derived from this assay could be questioned.
- **Resolution test** Perform control experiments varying dye concentration to demonstrate the expected concentration dependence of the on- and off-rates. Alternatively, use a non-intercalating dye or a mutant DNA to test the specificity of the signal.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of model description
- **Affected element** Results section, "Model for ligand binding under topological constraint"
- **Evidence pointer** Equations 1-6 (not provided in full)
- **Issue** The model description in the text is dense and the equations are not fully presented in the provided material. The relationship between the McGhee-von Hippel binding isotherm and the torque-dependent binding constant is described but the derivation is not shown.
- **Required correction** Provide the full set of equations in the main text or supplementary material, with a step-by-step derivation or a clear reference to where the derivation can be found.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Parameter justification
- **Affected element** Table 1 (not provided)
- **Evidence pointer** Table 1
- **Issue** The values for Kd, n, Δz, and Δθ for the different dyes are stated to be from previous studies, but the table is not provided. The choice of C = 100 nm is stated as a default, but the sensitivity of the model to this parameter is not discussed.
- **Required correction** Provide Table 1 with references for each parameter value. Add a brief discussion of the sensitivity of the model to the torsional stiffness C, or cite evidence for the chosen value.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections describing quantitative comparisons
- **Evidence pointer** Figures 2, 3, 5 (not provided)
- **Issue** The text reports "excellent agreement" but does not provide statistical measures of the agreement (e.g., R-squared, reduced chi-squared, confidence intervals) in the text.
- **Required correction** Include statistical measures of goodness-of-fit in the text or figure legends.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address potential limitations of the model, such as the assumption of a single binding mode, the neglect of electrostatic effects, or the applicability to non-intercalative ligands.
- **Required correction** Add a paragraph discussing the limitations of the model and the conditions under which it is expected to be valid.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability statement
- **Evidence pointer** Data availability section
- **Issue** The data availability statement says "All data are included in the article" but the figures and supplementary materials are not provided in the submitted material. The MATLAB code is available, but the input data files are not mentioned.
- **Required correction** Clarify that all data are included in the article and supplementary materials, and specify where the input data files for the model can be obtained.

## Risk / unsupported claims
- The claim of "excellent agreement" between model and experiment is not verifiable without the figures and statistical measures.
- The claim that the model "quantitatively accounts" for psoralen crosslinking data is not fully supported without details of the reanalysis.
- The assumption that crosslinking is directly proportional to binding is stated but not tested.
- The claim of "direct access to binding kinetics" in the single-molecule assay is not fully established without concentration-dependent control experiments.
- The assumption of fixed twist-writhe partitioning and constant torsional stiffness in the presence of intercalators is not justified with independent evidence or sensitivity analysis.