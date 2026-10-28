## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion)
- **Assessment boundary** Scientific validity of the computational modelling approach, the mutagenesis predictions, the MD simulation analyses, and the strength of the conclusions drawn regarding therapeutic targeting for type 2 diabetes
- **Shared manuscript claim summary** The authors use AlphaFold 3.0 to model the KLF15 zinc finger domain bound to DNA, perform in silico alanine scanning to identify key binding residues, and use 100-ns MD simulations with MM/GBSA free energy calculations to characterise the impact of four mutations (K334A, R344A, Y332A, R392A) on complex stability. They conclude these residues are essential for DNA recognition and represent potential therapeutic targets for type 2 diabetes.
- **Visible evidence base** Full text including methods, results, discussion, tables referenced (Tables 1 and 2), figures referenced (Figures 1-9), and supplementary methodological details
- **Missing materials affecting confidence** Figures and tables are referenced but not provided in the submitted text. Specific numerical data for RMSD, RMSF, Rg values are described qualitatively but not presented. The DNA sequence used for modelling is mentioned but not fully specified. No information on simulation convergence checks or replica runs is provided.

## Reviewer
- **Overall assessment** The manuscript presents a computational study of the KLF15 zinc finger domain interaction with DNA, using state-of-the-art tools including AlphaFold 3.0 and MD simulations. The validation approach using KLF4 as a benchmark is commendable. However, the study has several significant limitations. The AlphaFold 3.0 validation against KLF4 is presented with RMSD values but the methodology for comparing protein-DNA complexes is not fully described. The alanine scanning results from PremPDI are presented but the selection threshold for "significant" effects is not justified. The MD simulation analysis is described in detail but key quantitative results are only presented qualitatively. Most critically, the leap from identifying four residues that affect binding in silico to claiming these are "potential therapeutic targets for type 2 diabetes" is not supported by the evidence presented. No functional validation, cellular assays, or demonstration of disease relevance is provided. The manuscript would benefit from tempering its conclusions and providing more rigorous quantitative analysis of the simulation data.

- **Who would be interested in the results, and why** Computational structural biologists studying transcription factor-DNA interactions would find the AlphaFold 3.0 modelling approach of interest. Researchers working on Krüppel-like factors, particularly KLF15, may find the identification of key binding residues useful for designing mutagenesis experiments. However, the therapeutic claims would need substantial additional evidence to attract interest from the diabetes research community.

- **Major strengths** The use of AlphaFold 3.0 for protein-DNA complex modelling is timely and relevant. The validation strategy using the experimentally determined KLF4 structure is a good approach. The combination of alanine scanning, MD simulations, and MM/GBSA free energy calculations provides a multi-pronged computational approach. The identification of specific residues (K334, R344, Y332, R392) that appear critical for DNA binding provides testable hypotheses for experimental validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Overclaiming of therapeutic relevance
- **Claim pointer** The title and conclusion state that KLF15 represents a "potential therapeutic target for type 2 diabetes" and that the identified residues "can be considered potential hotspots for the therapeutics development for type 2 diabetes."
- **Evidence pointer** Abstract, Introduction, Conclusion
- **Concern** The manuscript provides no direct evidence linking the identified KLF15 DNA-binding residues to type 2 diabetes pathology or treatment. The connection is entirely inferential, based on prior literature showing KLF15 involvement in gluconeogenesis. No cellular assays, animal models, or patient data are presented. The computational identification of binding residues does not establish therapeutic relevance.
- **Why it matters** The title and conclusions make claims that go far beyond what the computational evidence can support. This overclaiming could mislead readers and is not consistent with the evidence presented. The therapeutic claim is the primary selling point of the paper but is entirely unsupported by the data shown.
- **Resolution test** The authors should either provide experimental validation demonstrating that modulating these residues affects glucose metabolism in relevant models, or substantially revise the title and conclusions to reflect that these are computational predictions requiring experimental validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Insufficient validation of AlphaFold 3.0 predictions
- **Claim pointer** The authors claim that AlphaFold 3.0 accurately models the KLF15 ZnF-DNA complex based on validation against KLF4 (RMSD 0.805 Å for apo and 1.317 Å for complex) and KLF15 H2 NMR structure (RMSD 0.684 Å and 0.529 Å).
- **Evidence pointer** Results section "Structural Validation KL15 and KLF15-DNA Interactions Modelling", Figures 1 and 2
- **Concern** The validation is performed against a homologous protein (KLF4) and a partial structure (H2 helix only of KLF15). The RMSD values reported are for the protein component only; no validation of the predicted protein-DNA interface accuracy is provided. AlphaFold 3.0 is known to have variable accuracy for protein-DNA complexes, and the authors do not assess whether the predicted DNA conformation or the specific protein-DNA contacts are reliable. The RMSD of 4.4 Å between the modelled KLF15-DNA complex and the KLF4-DNA crystal structure is notably high and not discussed as a limitation.
- **Why it matters** The entire study depends on the accuracy of the AlphaFold 3.0 model. If the predicted protein-DNA interface is incorrect, all subsequent alanine scanning and MD simulation results are built on an unreliable foundation. The validation presented is insufficient to establish confidence in the specific atomic contacts that form the basis of the study.
- **Resolution test** The authors should provide a more rigorous validation, including comparison of predicted protein-DNA contacts with known KLF family binding patterns, assessment of the DNA conformation accuracy, and discussion of the 4.4 Å RMSD discrepancy. Ideally, cross-validation with an independent docking method or experimental data on KLF15 binding specificity should be included.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Inadequate description of MD simulation methodology and results
- **Claim pointer** The authors state that 100-ns MD simulations were performed and that RMSD, RMSF, and Rg analyses demonstrate instability of mutant complexes compared to wild-type.
- **Evidence pointer** Methods section "Dynamics of the KLF15 ZnF Domain–DNA Complex", Results section "Dynamic Analysis of the KLF15 ZnF–DNA Complex", Figures 5-8
- **Concern** The methods section lacks critical details: the force field parameters for DNA are not specified (only FF19SB for protein is mentioned), the number of replicates is not stated, convergence criteria are not described, and the equilibration protocol is only briefly outlined. The results are presented entirely qualitatively ("significant perturbation", "highly dynamic", "stable and compact") without reporting actual RMSD, RMSF, or Rg values. No error bars or standard deviations are provided. The figures are referenced but not available for review. A single 100-ns simulation per system is generally considered insufficient for drawing robust conclusions about protein-DNA complex stability.
- **Why it matters** The MD simulation results are the primary evidence for the claim that the identified mutations destabilise the KLF15-DNA complex. Without proper methodological detail and quantitative results, these claims cannot be evaluated or reproduced. The lack of replicates and convergence analysis raises concerns about the reliability of the conclusions.
- **Resolution test** The authors should provide complete methodological details, report quantitative RMSD/RMSF/Rg values with standard deviations, include at least three independent simulation replicates, and demonstrate convergence of the simulations. The figures should be made available for review.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Inconsistent reporting of alanine scanning results
- **Claim pointer** The authors state that K334A, R344A, Y332A and R392A "significantly affect the binding affinities (ΔΔG) to DNA" based on PremPDI predictions, with K334A showing the largest effect (ΔΔG = 1.70 kcal/mol).
- **Evidence pointer** Results section "In Silico Alanine Mutagenesis of the KLF15 Zinc Finger Domain", Table 1
- **Concern** The text mentions "Twelve residues of the KL15 ZnF domain formed H-bonds with the DNA molecule" but only four are discussed in detail. The selection criteria for focusing on these four residues are not clearly justified. The ΔΔG values are reported inconsistently: the abstract mentions K334A, R334A, Y332A and R392A, but the results section discusses K334A, R344A, Y332A and R392A. This discrepancy between R334A and R344A is confusing and needs clarification. Additionally, the threshold for what constitutes a "significant" ΔΔG is not defined.
- **Why it matters** The identification of key residues is central to the study's conclusions. Inconsistent reporting of which residues were studied undermines confidence in the results. Without clear selection criteria and consistent reporting, the reader cannot assess whether the choice of residues for detailed analysis was appropriate or biased.
- **Resolution test** The authors should clarify which residues were studied (R334A or R344A), provide the complete PremPDI results for all twelve residues, and justify the selection of the four residues for further analysis.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** MM/GBSA results not adequately presented or interpreted
- **Claim pointer** The authors report total binding energies from MM/GBSA calculations, with wild-type showing -94.0 ± 0.17 kcal/mol compared to mutants with weaker binding.
- **Evidence pointer** Results section "Binding Free Energy Calculation of KLF15 ZnF-DNA Complex", Table 2
- **Concern** The MM/GBSA results are presented in a table that is not available for review. The text describes the wild-type as having the most favourable binding energy but does not provide the actual values for the mutants in the text. The decomposition of energy terms (van der Waals, electrostatic, polar solvation, non-polar solvation) is discussed qualitatively but the numbers are not given. The text mentions "K334A and R392A demonstrating the weakest binding affinities" but does not reconcile this with the earlier statement that R392A showed relatively stable MD behaviour. The relationship between the MM/GBSA results and the MD simulation findings needs clearer integration.
- **Why it matters** The MM/GBSA calculations provide quantitative support for the claim that the identified mutations reduce DNA binding affinity. Without the actual values and proper interpretation, the reader cannot evaluate the magnitude of the effects or the statistical significance of the differences between wild-type and mutants.
- **Resolution test** The authors should report the complete MM/GBSA results in the text, including all energy components for all systems, and provide a more detailed interpretation that reconciles the MM/GBSA results with the MD simulation findings.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and consistency
- **Affected element** Abstract and Results section
- **Evidence pointer** Abstract, Results section "In Silico Alanine Mutagenesis"
- **Issue** The abstract mentions "R334A" while the results section discusses "R344A". This inconsistency is confusing and needs to be resolved.
- **Required correction** Verify which residue was actually studied and use the correct notation consistently throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods section
- **Evidence pointer** Methods section "Structural Modelling of KlF15-Zinc Finger Domain DNA Complex"
- **Issue** The DNA sequence used for modelling is described as "5′GAGGCGTGGC3′" but the source and rationale for choosing this specific sequence are not explained. The relationship between this sequence and the KLF15 consensus binding site is not discussed.
- **Required Correction** Provide the source of the DNA sequence, explain why this particular sequence was chosen, and discuss its relationship to known KLF15 binding motifs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Results section
- **Evidence pointer** Results section "Dynamic Analysis of the KLF15 ZnF–DNA Complex"
- **Issue** The manuscript reports RMSD, RMSF, and Rg values qualitatively without statistical analysis. No standard deviations, confidence intervals, or statistical tests are reported.
- **Required Correction** Provide quantitative values with appropriate statistical measures and describe the statistical methods used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript does not discuss previous computational studies of KLF15 or other KLF family members' DNA binding. The novelty of the approach relative to existing literature is not clearly established.
- **Required Correction** Add a brief review of previous computational studies on KLF-DNA interactions and clearly state what new information this study provides.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1-9
- **Evidence pointer** Figures referenced throughout Results
- **Issue** The figures are not available for review. Based on the text descriptions, it is unclear whether the figures include appropriate labels, scale bars, and clear visual representations of the key findings.
- **Required Correction** Ensure all figures are clearly labelled, include appropriate scales, and effectively communicate the key results described in the text.

## Risk / unsupported claims
- The claim that the four identified residues are "potential hotspots for the therapeutics development for type 2 diabetes" is unsupported by the evidence presented. No functional or disease-relevant validation is provided.
- The claim that the wild-type KLF15 ZnF domain demonstrates "more robust binding affinity to DNA" compared to mutants is based on MM/GBSA calculations from a single MD simulation per system, which is insufficient for robust conclusions.
- The assertion that "the four identified residues are essential to recognise KLF15 ZnF DNA binding" is based solely on computational predictions and requires experimental validation.
- The statement that the findings "can be considered potential hotspots for the therapeutics development" implies therapeutic relevance that is not demonstrated by any experimental data.
- The manuscript does not provide evidence that the identified residues are druggable targets or that modulating their interaction with DNA would have therapeutic benefit in type 2 diabetes.
- The validation of AlphaFold 3.0 for protein-DNA complex prediction is based on comparison with a homologous protein (KLF4) and a partial structure, which may not be sufficient to establish confidence in the specific protein-DNA interface predictions for KLF15.