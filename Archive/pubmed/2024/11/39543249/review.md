## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the manuscript
- **Shared manuscript claim summary** The manuscript reports the synthesis of a β-ionone-derived ester (4-TM.P) and evaluates its cytotoxic and apoptosis-inducing effects on K562 human myeloid leukemia cells, alongside a characterization of its DNA binding mode using spectroscopic and computational methods. The authors claim that 4-TM.P inhibits K562 cell growth with an IC50 of 25 ± 5.0 µM at 72 h, induces apoptosis via G0/G1 cell cycle arrest and caspase-3 activation, and binds to DNA in the minor groove through a non-intercalative mode.
- **Visible evidence base** Full text including abstract, introduction, materials and methods, results and discussion, figures (1-8), tables (1-6), and conclusion
- **Missing materials affecting confidence** Raw data files, original spectra, flow cytometry scatter plots, statistical analysis outputs, MD simulation trajectory files, and compound characterization spectra (NMR, FT-IR) are not provided

## Reviewer

- **Overall assessment** The manuscript presents a straightforward study combining in vitro cytotoxicity assays with biophysical DNA binding experiments and computational simulations. The topic is of moderate interest to the cancer biology and drug discovery communities, particularly those focused on natural product derivatives. However, the study has several significant technical weaknesses that undermine the strength of the conclusions. The apoptosis data are incomplete and somewhat contradictory, the DNA binding experiments lack important controls and quantitative rigor, and the computational methods contain errors and insufficient detail. The novelty is limited, as β-ionone derivatives have been extensively studied for anticancer activity, and the specific contribution of this compound is not clearly established. The manuscript would benefit from substantial revision and additional experiments before the claims can be considered fully supported.

- **Who would be interested in the results, and why** Researchers in medicinal chemistry and natural product-based drug discovery would find the compound synthesis and preliminary biological evaluation of interest. Investigators studying DNA-binding small molecules as potential anticancer agents may also find the biophysical characterization relevant. The leukemia research community might have peripheral interest given the use of K562 cells, though the study does not provide deep mechanistic insight into leukemia-specific pathways.

- **Major strengths** The manuscript employs a multi-technique approach to characterize DNA binding, combining UV-vis spectroscopy, fluorescence spectroscopy, viscosity measurements, molecular docking, and molecular dynamics simulations. The integration of experimental and computational methods is commendable. The compound synthesis is clearly described and the compound is characterized by standard spectral methods. The dose- and time-dependent cytotoxicity data are presented with statistical analysis.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that 4-TM.P induces apoptosis in K562 cells based on morphological changes, cell cycle analysis, and Annexin V/PI staining.
- **Evidence pointer** Section "Results and discussion", Figures 2 and 3
- **Concern** The apoptosis data are incomplete and partially contradictory. The AO/EtBr staining images are described qualitatively but no quantification is provided. The cell cycle analysis shows a G0/G1 arrest at 24 h, but at 72 h the sub-G1 population increases to 40.5% while the G0/G1 population decreases to 34.7% compared to 45.7% in controls, which is inconsistent with a sustained G0/G1 arrest. The Annexin V/PI data are not shown in any figure, only described in text. The caspase-3 activity data show a 4.5-fold increase at 72 h, but the relationship between this increase and the cell cycle data is not discussed. The authors do not distinguish between early and late apoptosis in their interpretation, and the high sub-G1 fraction at 72 h could also indicate necrosis.
- **Why it matters** The central claim of the manuscript is that 4-TM.P induces apoptosis. If the apoptosis data are incomplete or contradictory, the primary biological conclusion is not established. The discrepancy between the G0/G1 arrest at early time points and the decrease in G0/G1 at 72 h needs explanation.
- **Resolution test** Provide quantitative analysis of AO/EtBr staining with statistical comparison. Show the Annexin V/PI flow cytometry plots. Reconcile the cell cycle data by explaining the relationship between G0/G1 arrest and the increasing sub-G1 population. Include a time-course experiment showing the progression from cell cycle arrest to apoptosis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that 4-TM.P binds to DNA in the minor groove based on spectroscopic and computational results.
- **Evidence pointer** Sections "UV-visible absorption spectral studies", "Fluorescence spectroscopy studies", "Viscosity studies", "Molecular docking study", "Molecular dynamics simulation"
- **Concern** The DNA binding mode determination has several weaknesses. First, the UV-vis experiments are performed in two directions: titrating DNA into 4-TM.P and titrating 4-TM.P into DNA, but the binding constant is only calculated from one direction. The Kb value of 7.6 × 10³ M⁻¹ from UV-vis is inconsistent with the Kb values of ~10⁴ M⁻¹ from fluorescence (Table 3), and this discrepancy is not discussed. Second, the fluorescence quenching experiments lack a control with a known intercalator or groove binder to validate the methodology. Third, the viscosity measurements show no change in DNA viscosity, which is interpreted as groove binding, but this is a negative result and should be supported by a positive control. Fourth, the molecular docking uses AutoDock4.2 with a Lamarckian Genetic Algorithm, but the grid box parameters are not fully described, and the reported inhibition constant of 77,267.00 µM in the text contradicts the value of 772.67 nM in Table 5. This is a significant numerical error. Fifth, the MD simulation methods contain errors: a cubic box with side length 1.1 nm is too small to contain a DNA dodecamer with adequate solvation, and the pressure equilibration target of 4.5 × 10⁻⁵ bar is not standard (typical is 1 bar).
- **Why it matters** The DNA binding mode is a central claim of the manuscript. If the experimental and computational evidence is not rigorous, the conclusion that 4-TM.P binds in the minor groove is not reliable. The numerical inconsistencies and methodological errors undermine confidence in the results.
- **Resolution test** Reconcile the binding constants from different methods and explain discrepancies. Include positive controls for viscosity and fluorescence experiments. Correct the inhibition constant error. Provide complete docking parameters and correct the MD simulation setup. Consider using a well-validated minor groove binder (e.g., DAPI or netropsin) as a comparative control.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that 4-TM.P "appears promising for further pharmaceutical evaluation" and "may offer a novel chemotherapeutic approach."
- **Evidence pointer** Conclusion section
- **Concern** The novelty and significance of this compound are not clearly established. The manuscript does not compare 4-TM.P with the parent β-ionone compound or other known β-ionone derivatives in terms of anticancer activity. The IC50 of 25 µM is modest, and no selectivity data against non-cancerous cells are provided. The mechanism of apoptosis induction is not explored beyond caspase-3 activation, and the link between DNA binding and apoptosis is not experimentally demonstrated. The authors do not discuss whether the DNA binding affinity is sufficient to be biologically relevant.
- **Why it matters** For a study to be significant, the compound must show some advantage or novel feature compared to existing agents. Without comparative data or mechanistic depth, the claim that this compound is promising for pharmaceutical development is not supported.
- **Resolution test** Include a comparison of 4-TM.P with β-ionone and other derivatives in terms of cytotoxicity. Test the compound on non-cancerous cell lines to assess selectivity. Investigate the link between DNA binding and apoptosis, for example by using a DNA-binding-deficient analog or by measuring cellular DNA damage. Discuss the therapeutic window and potential advantages over existing treatments.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the growth of K562 cells was inhibited during incubation with 10-100 μM β-ionone-derived ester in a dose- and time-dependent manner" and report IC50 values.
- **Evidence pointer** Section "Cell viability and growth inhibition", Figure 1, Table 1
- **Concern** The MTT assay methodology has potential issues. The cell density is stated as 4 × 10⁴ cells/well, which is relatively high for a 96-well plate and may lead to overconfluence during 72 h incubation. The DMSO concentration used as vehicle control is not specified. The statistical analysis is described as one/two-way ANOVA, but the number of independent experiments and replicates is not clearly stated. The IC50 values are reported with standard deviations, but the method of calculation (e.g., nonlinear regression) is not described.
- **Why it matters** The cytotoxicity data form the foundation of the biological claims. If the assay conditions are not optimal or the statistical analysis is not rigorous, the IC50 values may not be reliable.
- **Resolution test** Provide details on DMSO concentration, number of replicates, and IC50 calculation method. Consider using a lower cell density to avoid overconfluence. Show the full dose-response curves with error bars.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MD simulations confirmed "the stability of 4-TM.P and DNA complex over a 100 ns simulation."
- **Evidence pointer** Section "Molecular dynamics simulation", Figure 8, Table 6
- **Concern** The MD simulation analysis is superficial. The authors report average RMSD, RMSF, Rg, and SASA values but do not show the time evolution of these parameters in a meaningful way. The RMSD plot in Figure 8A appears to show convergence, but no error analysis is provided. The claim that the complex is "more stable" than free DNA based on a lower average RMSD is not statistically validated. The simulation setup is incompletely described: the force field parameters for 4-TM.P are not detailed, the water model and ion concentration are mentioned but not specified, and the temperature and pressure coupling methods are not fully described. The observation that the displaced 4-TM.P migrated back to the minor groove is interesting but is based on a single simulation and lacks statistical sampling.
- **Why it matters** The MD simulation is used to support the DNA binding mode and stability claims. If the simulation is not rigorously performed and analyzed, the computational support for the conclusions is weak.
- **Resolution test** Provide complete simulation parameters, including force field details for the ligand, water model, ion concentration, and coupling methods. Show time evolution plots with error estimates. Perform multiple independent simulations to assess reproducibility. Use binding free energy calculations or other quantitative measures to support the stability claim.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and does not clearly state the main findings in a way that is accessible to a broad audience. The IC50 value is reported, but the significance of the DNA binding mode is not explained in the context of the anticancer activity.
- **Required correction** Revise the abstract to clearly state the key findings, including the IC50 value, the apoptosis induction mechanism, and the DNA binding mode, in a way that is understandable to nonspecialists.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and methods, "Molecular dynamics simulation"
- **Evidence pointer** Section "Molecular dynamics simulation"
- **Issue** The description of the MD simulation box is inconsistent. The text states "A cubic simulation box with a side length of 1.1 nm was employed," which is too small for a DNA dodecamer. This is likely a typographical error, but it needs correction.
- **Required correction** Correct the box size description. A cubic box for a DNA dodecamer with adequate solvation would typically be at least 5-6 nm in each dimension.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "Molecular docking study"
- **Evidence pointer** Table 5
- **Issue** The inhibition constant is reported as 77,267.00 µM in the text but 772.67 nM in Table 5. These values differ by a factor of 100,000 and one of them must be incorrect.
- **Required correction** Correct the inhibition constant value and ensure consistency between the text and table.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results and discussion
- **Evidence pointer** Section "Results and discussion"
- **Issue** The section headings are inconsistent. Some are formatted as questions or statements, while others are not. This makes the structure of the results section difficult to follow.
- **Required correction** Use consistent, descriptive section headings throughout the results and discussion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and methods, "Cell culture and cell viability assay"
- **Evidence pointer** Section "Cell culture and cell viability assay"
- **Issue** The DMSO concentration used as vehicle control is not specified. DMSO can affect cell viability at high concentrations, and this is an important control.
- **Required correction** Specify the DMSO concentration used in the vehicle control and ensure it is consistent across all experiments.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "UV-visible absorption spectral studies"
- **Evidence pointer** Figure 4
- **Issue** The UV-vis titration is performed in two directions (DNA into 4-TM.P and 4-TM.P into DNA), but the binding constant is only calculated from one direction. The authors should explain why only one direction was used for the calculation.
- **Required correction** Explain the choice of titration direction for the binding constant calculation, or calculate Kb from both directions and report both values.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure legends
- **Evidence pointer** Figures 1-8
- **Issue** Some figure legends are incomplete and do not fully describe the experimental conditions. For example, Figure 4 legend does not specify the buffer conditions or the concentration ranges used.
- **Required correction** Expand the figure legends to include all relevant experimental conditions.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "Thermodynamic parameters of DNA binding"
- **Evidence pointer** Table 4
- **Issue** The thermodynamic parameters are reported with only one significant figure for ΔH and ΔS, which limits the precision of the interpretation. The errors on these values are not reported.
- **Required correction** Report the thermodynamic parameters with appropriate errors and significant figures.

## Risk / unsupported claims

- The claim that 4-TM.P "appears promising for further pharmaceutical evaluation" is not supported by the data, as no selectivity, in vivo efficacy, or pharmacokinetic data are provided.
- The claim that the compound "may offer a novel chemotherapeutic approach" is overstated, as the novelty of this specific compound compared to other β-ionone derivatives is not established.
- The conclusion that 4-TM.P binds to DNA in the minor groove is not fully supported due to the lack of positive controls and the inconsistencies in the binding constant values.
- The claim that MD simulations confirmed the stability of the complex is not statistically validated, as only a single simulation was performed and no error analysis was provided.
- The statement that the Kb value from UV-vis "appears to be within the same range as groove binders" is based on a comparison with literature values that are not cited or discussed in detail.
- The assertion that the pyrazine ring's electrophilicity is "the most important factor" in the compound's reactivity is speculative and not experimentally tested.