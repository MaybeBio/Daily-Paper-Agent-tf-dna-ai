## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, figures referenced but not provided)
- **Assessment boundary** Scientific soundness, methodological rigor, internal consistency, and support of claims based solely on the supplied text; figures and tables referenced but not available for inspection
- **Shared manuscript claim summary** The authors report synthesis of a Zn(II) dichloroethylenediamine complex (Zn(en)Cl2), its characterization by conductivity, UV-Vis, FT-IR, and XRD, its antiproliferative activity against HeLa cervical cancer cells (IC50 = 898.35 µg/mL), and computational evidence (molecular docking and molecular dynamics) suggesting DNA binding via coordinate covalent bonds to guanine (DG), with stability maintained throughout a 20 ns simulation.
- **Visible evidence base** Text descriptions of methods and results; references to Figures 1–15 and Tables 1–4; no actual spectra, diffractograms, docking poses, MD trajectories, or statistical analyses are included in the supplied material
- **Missing materials affecting confidence** All figures and tables; raw experimental data; statistical analysis details; docking scoring function details; MD simulation parameters beyond those stated; cell viability raw data; positive/negative control quantitative results; compound purity verification data; replication information

## Reviewer
- **Overall assessment** The manuscript addresses a relevant topic in inorganic medicinal chemistry, namely the synthesis and biological evaluation of a zinc-ethylenediamine complex as a potential anticancer agent. However, the current text contains multiple internal inconsistencies, methodological ambiguities, and unsupported claims that preclude a positive assessment. The reported IC50 value (898.35 µg/mL) is orders of magnitude higher than established anticancer agents, yet the authors describe the activity as "promising." The computational results are presented without sufficient quantitative detail, and several statements in the results contradict standard chemical interpretation. The manuscript requires substantial revision and additional experimental evidence before the claims can be considered established.

- **Who would be interested in the results, and why** Researchers in inorganic medicinal chemistry, particularly those investigating zinc-based coordination compounds as potential anticancer agents, may find the synthesis and preliminary characterization of Zn(en)Cl2 of interest. Computational chemists studying metal-DNA interactions could also find the docking and MD methodology relevant. However, the very weak antiproliferative activity and lack of mechanistic depth limit the broader appeal to cancer biology or drug discovery audiences.

- **Major strengths** The manuscript addresses a relevant and underexplored area, namely zinc-based coordination complexes as alternatives to platinum-based chemotherapeutics. The combination of experimental synthesis and characterization with computational docking and MD simulation represents a reasonable initial screening approach. The authors correctly identify the need for less toxic alternatives to cisplatin and acknowledge the limitations of current platinum-based therapies.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency and data interpretation
- **Claim pointer** The authors claim the complex exhibits "promising anticancer activity against HeLa cancer cells" based on an IC50 of 898.35 µg/mL.
- **Evidence pointer** Results section, antiproliferative activity; Figure 12 (not provided)
- **Concern** An IC50 of 898.35 µg/mL corresponds to approximately 4.5 mM (assuming a molecular weight of ~200 g/mol for Zn(en)Cl2), which is several orders of magnitude higher than clinically relevant concentrations of cisplatin (typically low micromolar). Describing this as "promising" is not supported by the data presented. Furthermore, the calculation method described ("substituting y with 50" in the equation y = -0.0005x + 0.8142) is mathematically incorrect; substituting y = 50 into this equation yields a negative x value, not 898.35. The reported IC50 cannot be derived from the stated equation.
- **Why it matters** The central biological claim of the manuscript rests on this value. If the IC50 calculation is erroneous or the activity is negligible, the conclusion that the complex has potential as an anticancer agent is not supported.
- **Resolution test** Provide raw absorbance data, dose-response curves, the correct IC50 calculation method (e.g., nonlinear regression), and comparison with a positive control (e.g., cisplatin) under identical conditions. Clarify the discrepancy between the stated equation and the reported IC50 value.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor and reproducibility
- **Claim pointer** The synthesis method states: "0.136 g (1 mmol) of zinc (II) chloride was dissolved in a small amount of water and 0.664 g (4 mmol) KI was added. Afterward, 1 mL of 1 M (1 mmol) ethylenediamine and 0.34 g of (2 mmol) AgNO3 were introduced into the mixture. The deposits produced were filtered out, and the yielded filtrate was reacted with excess KCl and ethylenediamine."
- **Evidence pointer** Materials and Methods, Synthesis section
- **Concern** The synthetic procedure is chemically problematic. The addition of KI to ZnCl2 would form ZnI2 and KCl, not a defined intermediate. The subsequent addition of AgNO3 would precipitate AgCl and AgI, but the stoichiometry is unclear. The role of "excess KCl and ethylenediamine" in the final step is not explained. The authors do not specify reaction conditions (temperature, time, pH, solvent volumes), purification methods, or yield. The identity of the final product as Zn(en)Cl2 is not established by elemental analysis or mass spectrometry.
- **Why it matters** Reproducibility is a fundamental requirement. Without a clear, chemically rational synthesis and product verification, the entire study cannot be replicated or trusted.
- **Resolution test** Provide a detailed, stepwise synthesis protocol with exact quantities, conditions, and purification steps. Include elemental analysis (CHN), mass spectrometry, or single-crystal X-ray diffraction to confirm the molecular formula and structure.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Characterization data interpretation
- **Claim pointer** The authors state: "The infrared absorption spectrum showed peaks at 511 and 509 cm-1, providing evidence of a reaction between the metal and ethylene ligands. Additionally, the spectrum indicated the absence of ethylenediamine by exhibiting the presence of -NH2, -CH2-, and C-N groups at 1597, 1458, and 1008 cm-1 wavelengths, respectively."
- **Evidence pointer** Results, IR Characterization; Figure 3 (not provided)
- **Concern** This statement is internally contradictory. The authors claim the spectrum "indicated the absence of ethylenediamine" while simultaneously "exhibiting the presence of -NH2, -CH2-, and C-N groups," which are the functional groups of ethylenediamine. The peaks at 511 and 509 cm-1 are assigned to metal-ligand vibrations, but the difference of 2 cm-1 between two reported peaks is within typical instrumental resolution and should not be reported as distinct. No assignment table is provided.
- **Why it matters** The characterization is central to confirming the complex structure. Contradictory interpretation of IR data undermines confidence in the structural assignment.
- **Resolution test** Provide the full IR spectrum with a detailed peak assignment table, including literature references for each vibrational mode. Clarify whether ethylenediamine is present or absent in the final complex.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational methodology and interpretation
- **Claim pointer** The authors claim the complex "bound to DNA at the nitrogenous base Guanine (DG) by coordinate covalent bonds" and that "DG maintained interaction with the complex until the end of the docking simulation" and throughout the MD simulation.
- **Evidence pointer** Results, Molecular Docking and Molecular Dynamics sections; Figures 5–11, Tables 1–4 (not provided)
- **Concern** The docking methodology is described only as using "PLANTS software" with "Basic validation of the PLANTS protocol" mentioned but not detailed. No docking scores, RMSD values for validation, or comparison with known DNA binders are provided. The MD simulation parameters are partially given (20 ns, 310 K, AMBER14), but no convergence criteria, equilibration details, or error estimates are reported. The claim of "coordinate covalent bonds" from docking alone is not justified; docking typically identifies non-covalent interactions. The statement that "the positive value of binding free energies shows that the binding of the metal complexes to DNA in water is favorable" is thermodynamically incorrect; positive binding free energies indicate unfavorable binding.
- **Why it matters** The computational results are used to propose a mechanism of action. If the methodology is not validated and the thermodynamic interpretation is wrong, the mechanistic claims are unsupported.
- **Resolution test** Provide docking validation results (e.g., RMSD of redocked reference ligand), docking scores for all complexes, a clear description of the binding mode, and corrected interpretation of binding free energy values. Report MD convergence metrics and error bars for all calculated quantities.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and controls
- **Claim pointer** The antiproliferative activity was tested against HeLa cells with cisplatin as a positive control, and the IC50 was determined.
- **Evidence pointer** Materials and Methods, Antiproliferative Activity Test; Results, Figure 12 (not provided)
- **Concern** The methods section does not specify the concentration range tested, the number of replicates, the statistical analysis method, or the criteria for determining IC50. The cisplatin positive control is mentioned but no comparative IC50 value for cisplatin is reported. The statement "The level of cell death was directly proportional to the concentration" is presented without quantitative data. No cytotoxicity data on non-cancerous cells is provided, which is essential for assessing selectivity.
- **Why it matters** Without proper experimental design details and statistical analysis, the biological activity claim cannot be evaluated. Selectivity is critical for any potential therapeutic application.
- **Resolution test** Provide full experimental details: concentration range, replicate numbers, statistical tests, dose-response curves for both Zn(en)Cl2 and cisplatin, and cytotoxicity data on a non-cancerous cell line.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency and scope
- **Claim pointer** The author contribution statement mentions "in vitro test analysis of breast cancer" while the manuscript title and abstract refer to cervical cancer (HeLa cells).
- **Evidence pointer** Author Contribution Statement
- **Concern** The contribution statement refers to breast cancer, which is inconsistent with the stated focus on cervical cancer. This suggests either a copy-paste error or confusion about the experimental scope.
- **Why it matters** Inconsistencies of this type raise questions about the overall care and accuracy of the manuscript.
- **Resolution test** Correct the contribution statement to accurately reflect the experimental work performed.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and precision
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Objective section
- **Issue** The abstract states the research "aims to synthesize and characterize Zinc (II) dichloroethylenediamine (Zn(en)Cl2) complex, as well as determine its antiproliferative activity against HeLa cells" and then immediately states "The Zn(en)Cl2 complex was successfully synthesized, and the antiproliferative activity was tested," which is redundant.
- **Required correction** Remove the redundant sentence and provide a concise summary of key findings, including the actual IC50 value and its significance.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results, UV-Vis Characterization
- **Evidence pointer** Results section
- **Issue** The statement "The resulting transition was π → π* with a maximum wavelength of 233 nm" is presented without supporting data or context. The assignment of the electronic transition is speculative without a detailed analysis of the spectrum.
- **Required correction** Provide the UV-Vis spectrum and a detailed assignment of the observed transitions with appropriate references.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Language and grammar
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The manuscript contains numerous grammatical errors and awkward phrasings (e.g., "dihedral engle energies," "van der Walls energies," "The high difference value between Zn(en)Cl2 and cisplatin may reveal that DNA is not the suitable target"). These errors detract from readability.
- **Required correction** The manuscript should be carefully edited by a native English speaker or professional editing service.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Introduction
- **Evidence pointer** Introduction section
- **Issue** Several statements lack proper citations, including the claim that zinc "has the ability to both cause apoptosis in some tumors and shield other cancer cells from apoptosis" and the statement about the dithiocarbamate ligand's applications.
- **Required correction** Add appropriate references for all factual claims.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1–15
- **Evidence pointer** Referenced throughout Results
- **Issue** The figures are referenced but not provided in the manuscript text. The quality and clarity of the figures cannot be assessed.
- **Required correction** Ensure all figures are included in the submission with appropriate resolution, labels, and legends.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Tables 1–4
- **Evidence pointer** Referenced in Results
- **Issue** The tables are referenced but not provided. The content and organization of the tables cannot be evaluated.
- **Required correction** Include all tables in the submission with clear headings, units, and footnotes.

## Risk / unsupported claims
- The claim of "promising anticancer activity" based on an IC50 of 898.35 µg/mL is unsupported; this value indicates very weak activity and the calculation method described is mathematically inconsistent with the reported result.
- The claim that the complex binds to DNA via "coordinate covalent bonds" is not supported by the docking methodology described, which typically identifies non-covalent interactions.
- The statement that "positive value of binding free energies shows that the binding of the metal complexes to DNA in water is favorable" is thermodynamically incorrect and unsupported.
- The claim that the complex "remained bound to the DNA binding pocket all through the process" of MD simulation cannot be evaluated without the trajectory data and quantitative analysis.
- The structural assignment of the complex as Zn(en)Cl2 is not adequately supported by the characterization data presented; elemental analysis or mass spectrometry is required.
- The claim that the complex "can increase the stability of DNA" is not supported by the data presented.
- The statement that "the absence of electron donors between ethylenediamine and zinc (II)" explains the UV-Vis shift is chemically unclear and unsupported.
- The claim that the high melting point "showed that the ligands were strongly bonded to the metal" is an oversimplification and not a definitive proof of coordination.
- The conductivity value of 2.02 mS/cm is used to classify the complex as a non-electrolyte, but the threshold for this classification is not provided and the value seems high for a non-electrolyte in typical organic solvents.
- The manuscript title and abstract focus on cervical cancer, but the author contribution statement mentions breast cancer, creating an inconsistency that undermines confidence in the reported scope.