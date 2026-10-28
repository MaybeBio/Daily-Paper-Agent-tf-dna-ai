## Review setup
- **Input scope** Full manuscript text (abstract, introduction, models and methods, results and discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence. No assessment of code availability, reproducibility scripts, or peer-review history.
- **Shared manuscript claim summary** The authors propose an atomistic mechanism for uranyl ion (UO2 2+) toxicity toward the DNA-binding domain of PARP-1, specifically the Zn2 zinc finger. They claim that uranyl replaces zinc in the native binding site, that the resulting complex undergoes spontaneous internal hydrolysis of the U-Cys162 bond, and that subsequent reorganization involving association with a Glu190/Asp191 acidic cluster stabilizes a non-functional state. They report free energy changes along this pathway, with a final free energy difference of approximately -7.4 kcal/mol favoring the "broken" state.
- **Visible evidence base** QM/MM molecular dynamics with umbrella sampling, classical MD simulations, DFT calculations on model complexes, GIST/MIST-based solvation and configurational entropy analyses, and comparison with prior experimental findings (Cooper et al. 2016; Zhou et al. 2021). Figures referenced: Fig. 1, Fig. 2A, Fig. 2B, Fig. 3, Fig. 4, Fig. 5. Tables referenced: Table S1, Table S2, Table S3. Supplementary figures referenced: Fig. S1, Fig. S2.
- **Missing materials affecting confidence** The manuscript text provided does not include the actual figures, tables, or supplementary materials. Numerical values for free energy components in Tables S2 and S3 are referenced but not shown. The umbrella sampling profiles (Fig. S1, Fig. S2) are not visible. The classical MD simulation parameters for the uranyl force field parametrization are described only briefly. No error bars or convergence criteria for the QM/MM free energy calculations are reported in the text. The manuscript appears to be a preprint and may lack some methodological details that would be present in a final version.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant toxicological question with a plausible computational approach, combining QM/MM, classical MD, and solvation thermodynamics. The proposed mechanism is chemically reasonable and consistent with available experimental observations. However, the evidence presented in the text is insufficient to fully establish the quantitative claims. Key thermodynamic quantities are referenced to supplementary tables that are not provided, and the uncertainty in the free energy estimates is not discussed. The claim of near-irreversible transformation (-7.4 kcal/mol) rests on a chain of approximations whose cumulative error is not assessed. The work is potentially interesting to the computational toxicology and metalloprotein communities, but the current presentation does not meet the standard required for a high-impact journal without substantial additional detail and validation.
- **Who would be interested in the results, and why** Researchers in computational toxicology, metalloprotein biochemistry, and uranium bioremediation. The study provides a mechanistic hypothesis for uranyl-induced protein dysfunction that could inform experimental design for chelation therapy or biomonitoring. The methodological combination of QM/MM with solvation thermodynamics may also interest method developers in the molecular simulation community.
- **Major strengths** 1) The study addresses a clinically and environmentally relevant problem with a clear mechanistic hypothesis. 2) The combination of QM/MM, classical MD, and solvation thermodynamics is appropriate and state-of-the-art. 3) The proposed mechanism reconciles apparently conflicting experimental observations (in vitro vs. in vivo zinc displacement). 4) The authors explicitly consider entropic contributions, which are often neglected in similar studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative data), R1-M2 (uncertainty not assessed), R1-M3 (force field parametrization details), R1-M4 (convergence of QM/MM simulations).
- **Assessment against Nature-style criteria** Originality: Moderate. The application of QM/MM to uranyl-protein interactions is not entirely new, but the specific focus on PARP-1 zinc finger and the proposed two-step mechanism (hydrolysis followed by acidic cluster association) is a novel contribution. Scientific importance: Moderate. Uranium toxicity is a real concern, and understanding molecular mechanisms could aid in therapeutic development. However, the study is purely computational and does not provide direct experimental validation. Interdisciplinary readership: Limited. The work will primarily appeal to computational biochemists and toxicologists; the level of methodological detail may deter general readers. Technical soundness: The methods are appropriate in principle, but the presentation lacks sufficient detail to verify the calculations. The absence of error analysis is a significant weakness. Readability for nonspecialists: The abstract is accessible, but the methods and results sections assume substantial expertise in QM/MM and statistical thermodynamics. The manuscript would benefit from a clearer summary of the key findings for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is plausible and the methodological approach is sound, but the manuscript in its current form does not provide enough quantitative evidence to support the strong claims made. The authors must provide the missing data, include error estimates, and clarify methodological details before the case is established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the free energy difference between the "broken" and functional states is close to -7.4 kcal/mol, indicating near-irreversible transformation.
- **Evidence pointer** Results and Discussion, section "Binding site reorganization"; Table S3 (not provided)
- **Concern** The central quantitative claim of the paper, the -7.4 kcal/mol free energy difference, is presented without showing the actual values in the main text. The authors reference Table S3, which is not available in the provided material. Without seeing the breakdown of configurational and solvation contributions, the reader cannot assess whether the calculation is reliable. Furthermore, the text states that the association free energy is -12.1 kcal/mol and the hydrolysis free energy is -0.6 kcal/mol, but the relationship between these values and the final -7.4 kcal/mol is not explicitly derived in the text.
- **Why it matters** The quantitative free energy value is the primary evidence for the claim of irreversible toxicity. If this value is not robustly supported, the central conclusion of the paper is weakened.
- **Resolution test** The authors must provide the full contents of Table S2 and Table S3 in the main text or supplementary material, with a clear derivation of how the final free energy difference is obtained from the individual components. They should also discuss the statistical uncertainty of each term.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Uncertainty quantification
- **Claim pointer** The authors report free energy changes from umbrella sampling and enthalpy calculations without any error bars or convergence analysis.
- **Evidence pointer** Models and Methods, section on QM/MM simulations; Results and Discussion, sections on hydrolysis and binding site reorganization
- **Concern** No statistical uncertainty is reported for any of the computed quantities. The umbrella sampling free energy profiles (Fig. S1, Fig. S2) are not shown, and the number of sampling windows, the total simulation time per window, and the convergence criteria are not stated. The enthalpy calculations are based on only 20 snapshots, which is a very small sample. The classical MD simulations used for configurational entropy are described as 1500 ns, but the number of independent samples and the statistical error of the entropy estimate are not given.
- **Why it matters** Free energy differences of a few kcal/mol are meaningful in biological contexts, and the difference between -0.6 and -7.4 kcal/mol is substantial. Without error estimates, the reader cannot determine whether the reported values are statistically distinguishable from zero or from each other.
- **Resolution test** The authors should provide error bars for all reported free energy differences, describe the convergence of the umbrella sampling calculations (e.g., by showing the overlap of histograms or the evolution of the free energy estimate with simulation time), and report the statistical uncertainty of the entropy calculations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The authors state that they parametrized the classical force field for uranyl coordination complexes using the Force Field Toolkit (ffTK) and RESP charges, with VdW parameters from a previous study.
- **Evidence pointer** Models and Methods, section on classical MD simulations
- **Concern** The description of the force field parametrization is too brief. The authors do not specify which atoms were assigned RESP charges, how the charges were derived (e.g., from which QM level), whether the VdW parameters for uranium were validated against experimental or high-level QM data, or how the parametrization was tested. The choice of the previous study for VdW parameters is not justified.
- **Why it matters** The classical MD simulations are used to compute configurational entropies and to assess the stability of the "broken" state. If the force field is not accurate for uranyl coordination, the resulting free energy estimates could be systematically biased.
- **Resolution test** The authors should provide a more detailed description of the parametrization procedure, including the QM method used for charge derivation, the validation of the force field against QM/MM or experimental data, and a discussion of the limitations of the chosen VdW parameters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Simulation convergence
- **Claim pointer** The authors report that the lifetime of the hydrolyzed state in the native configuration does not exceed 20-30 ns, based on classical MD simulations.
- **Evidence pointer** Results and Discussion, section "Cysteine 162 discoordination leads to the loss of zinc finger tertiary structure"; Fig. 4 (not provided)
- **Concern** The claim that the hydrolyzed state has a lifetime of 20-30 ns is based on a single or few MD trajectories. The authors do not report how many independent simulations were performed, whether the lifetime estimate is statistically robust, or whether the simulations were long enough to observe multiple transitions between the two states. The RMSD plot in Fig. 4 is referenced but not shown.
- **Why it matters** The lifetime estimate is used to support the claim that the hydrolyzed state is transient and that subsequent reorganization is required for stabilization. If the lifetime is not well characterized, the proposed mechanism could be incorrect.
- **Resolution test** The authors should report the number of independent simulations, the total simulation time, and the statistical uncertainty of the lifetime estimate. They should also show the RMSD plot and discuss whether the observed transitions are reproducible.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, last sentence
- **Issue** The abstract states that the final free energy difference is -0.6 kcal/mol for the hydrolysis step, but the conclusion states -7.4 kcal/mol for the overall transformation. This could confuse readers who do not read the full text.
- **Required correction** Clarify in the abstract that the -0.6 kcal/mol refers to the hydrolysis step alone, and that the overall free energy change including subsequent reorganization is -7.4 kcal/mol.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Models and Methods
- **Evidence pointer** Models and Methods, section on QM/MM simulations
- **Issue** The authors do not specify the software versions for NAMD and ORCA beyond version numbers, nor do they state the QM/MM coupling scheme (e.g., electrostatic embedding details, link atom treatment) beyond a brief mention.
- **Required correction** Provide the full citation for the NAMD-ORCA interface and describe the QM/MM coupling scheme in sufficient detail for reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results and Discussion, section "Binding site reorganization"
- **Evidence pointer** Results and Discussion, section "Binding site reorganization"
- **Issue** The authors state that the association with the Glu190/Asp191 cluster is "most likely" to proceed by substitution of a water ligand, but they do not discuss alternative mechanisms, such as direct coordination to the acidic cluster without prior hydrolysis.
- **Required correction** Briefly discuss why alternative pathways are less likely, or acknowledge that they were not explored.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures and tables
- **Evidence pointer** All figures and tables
- **Issue** The figures and tables are referenced but not included in the provided text. This makes it impossible to evaluate the quality of the data presentation.
- **Required correction** Ensure that all figures and tables are included in the final submission and that they are self-explanatory with clear captions.

## Risk / unsupported claims
- The claim that the final free energy difference is -7.4 kcal/mol is not verifiable from the provided text because Table S3 is not included.
- The claim that the hydrolyzed state has a lifetime of 20-30 ns is not verifiable because Fig. 4 is not included and no statistical analysis is reported.
- The claim that the apo-protein maintains its original structure over 3000 ns is based on a single simulation and is not supported by quantitative data in the text.
- The claim that the proposed mechanism reconciles the findings of Zhou et al. and Cooper et al. is plausible but is not directly tested by the simulations, as the authors do not model the peptide used by Zhou et al.
- The statement that "the fraction of SI will be less than 0.5%" is derived from a free energy difference of -3.4 kcal/mol, but the calculation assumes a two-state model that is not explicitly validated.