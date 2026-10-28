## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and figure legends. Supplementary material not provided.
- **Assessment boundary** Scientific claims, methodological soundness, and interpretation of results as presented in the manuscript. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors investigate whether melatonin is a direct ligand for the nuclear receptor RORβ. Using sequence analysis, homology modeling, molecular docking, molecular dynamics simulation, differential scanning fluorometry (DSF), isothermal titration calorimetry (ITC), and gene expression analysis in SH-SY5Y cells, they conclude that melatonin is unlikely to be a direct ligand for RORβ, though melatonin exposure does upregulate RORα and RORβ mRNA expression.
- **Visible evidence base** Results sections on sequence analysis, molecular docking (SwissDock and AutoDock Vina), homology modeling, 1 µs MD simulation, DSF, ITC, and ddPCR/qPCR gene expression data. Figures 1–8 and Tables 1 as referenced.
- **Missing materials affecting confidence** Supplementary figures and tables (Supplementary Fig. 1–2, Supplementary Tables 1–2) not provided. Raw DSF and ITC thermograms not shown in full. No statistical details for gene expression experiments beyond stated p < 0.05. No information on replicate numbers for ITC experiments.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and contested question in melatonin biology: whether RORβ is a bona fide nuclear receptor for melatonin. The authors combine computational predictions with two biophysical methods and gene expression analysis. The negative biophysical results are clear and support the conclusion that melatonin does not directly bind RORβ under the tested conditions. However, several methodological details are insufficiently described, particularly regarding protein quality, ITC experimental design, and the interpretation of docking results. The gene expression experiments are interesting but preliminary and do not fully resolve the mechanism of melatonin action on ROR expression. The manuscript is generally well written and accessible, but the strength of the conclusion is limited by the absence of key experimental controls and details.
- **Who would be interested in the results, and why** Researchers in melatonin biology, chronobiology, and nuclear receptor pharmacology would find these results relevant. The study challenges a long-standing hypothesis and provides biophysical evidence that may redirect research toward alternative nuclear targets of melatonin. The gene expression findings may also interest those studying circadian regulation and melatonin signaling in neuroblastoma models.
- **Major strengths** The study addresses a controversial question with a combination of computational and experimental approaches. The use of two orthogonal biophysical techniques (DSF and ITC) strengthens the negative conclusion. The inclusion of a positive control (SRC-1 peptide) in both DSF and ITC validates the assay conditions. The gene expression analysis using ddPCR provides quantitative data on ROR isoform responses to melatonin. The authors acknowledge limitations of docking and interpret results cautiously.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that ITC confirmed no interaction between the LBD of RORβ and melatonin in all settings.
  - **Evidence pointer** Figure 6, "Isothermal calorimetry (ITC) results"
  - **Concern** The ITC experimental details are insufficient to assess the validity of the negative result. The authors do not report the concentration of protein in the cell, the concentration of melatonin in the syringe, the number of injections, the injection volume, the stirring speed, the temperature, or the duration of each injection. Without these parameters, it is impossible to determine whether the absence of a signal reflects true lack of binding or suboptimal experimental conditions (e.g., insufficient ligand concentration, solubility issues, or aggregation). Additionally, the authors do not report whether melatonin was titrated into buffer alone as a control for heats of dilution, which is essential for interpreting ITC data.
  - **Why it matters** A negative ITC result is only meaningful if the experimental design is capable of detecting binding in the expected affinity range. Without adequate controls and detailed methods, the conclusion that melatonin does not bind RORβ is not fully supported.
  - **Resolution test** Provide full ITC experimental parameters, including concentrations, injection protocols, and dilution controls. Show representative raw thermograms and integrated heat data for all conditions. If possible, include a positive control ligand for RORβ to demonstrate that the assay can detect binding to this protein.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors conclude that melatonin is unlikely to be a direct ligand for RORβ based on DSF and ITC results.
  - **Evidence pointer** "Biophysical Assays Could Not Confirm Binding Interaction Between the LBD of RORβ and Melatonin" section, Figures 5 and 6
  - **Concern** The quality and functional integrity of the recombinant RORβ LBD protein used in DSF and ITC are not adequately demonstrated. The authors do not show any characterization of the purified protein, such as SDS-PAGE, size-exclusion chromatography profile, circular dichroism spectrum, or an activity assay confirming the protein is properly folded and functional. If the protein is misfolded or aggregated, the absence of binding to melatonin would be uninformative. The SRC-1 peptide binding does demonstrate some degree of functional competence, but this is not sufficient to rule out that the protein is partially unfolded or that the ligand-binding pocket is not in a native conformation.
  - **Why it matters** A negative binding result is only interpretable if the protein is shown to be properly folded and functional. Without this evidence, the conclusion that melatonin does not bind RORβ is weakened.
  - **Resolution test** Provide protein characterization data, including purity assessment, oligomeric state, and evidence of proper folding. If possible, demonstrate that the protein can bind a known RORβ ligand or co-activator peptide with a measurable affinity in the same assay conditions.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation
  - **Claim pointer** The authors state that molecular docking predicted melatonin binding to RORβ with comparable energies to those for MT1 and MT3, but that MD simulation revealed only weak interactions.
  - **Evidence pointer** "Molecular Docking Revealed Potential Binding of Melatonin on Rat RORβ" and "Molecular Docking Revealed Potential Melatonin Binding to All Human RORs" sections, Figures 2 and 4
  - **Concern** The docking results are presented as supporting the possibility of melatonin binding, but the authors do not critically evaluate the limitations of the docking approach. The ΔG values from docking are approximate and depend heavily on the scoring function, the protein conformation used, and the treatment of flexibility. The authors do not report the docking scores from AutoDock Vina for comparison, nor do they discuss whether the predicted binding poses are physically plausible (e.g., whether the ligand is buried, whether key hydrogen bonds are formed). The MD simulation is described as showing "unstable binding," but the criteria for instability are not defined. The authors do not report RMSD values for the protein or ligand over the simulation, nor do they describe the convergence of the simulation.
  - **Why it matters** The computational results are used to motivate the biophysical experiments, but their interpretation is ambiguous. A more rigorous analysis of the docking and MD results would strengthen the manuscript and help readers understand the relationship between computational predictions and experimental outcomes.
  - **Resolution test** Provide docking scores from both SwissDock and AutoDock Vina, including a comparison of binding poses. Report MD simulation metrics, such as protein and ligand RMSD over time, and define criteria for stable versus unstable binding. Discuss the limitations of the computational approach in the context of the negative experimental results.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors conclude that melatonin upregulates RORα and RORβ mRNA expression in SH-SY5Y cells and that this effect is unlikely mediated via MT1/MT2 receptors based on luzindole experiments.
  - **Evidence pointer** "Melatonin Substantially Altered ROR Gene Expressions" section, Figure 7
  - **Concern** The gene expression experiments lack important controls and details. The authors do not report the vehicle control conditions (e.g., DMSO concentration) for melatonin treatments. The luzindole experiment uses only one concentration of luzindole (1 µM) and one time point, and the authors do not demonstrate that this concentration is sufficient to block MT1/MT2 signaling in their system. The statistical analysis is described only as "p < 0.05" without specifying the test used, the number of biological replicates, or whether multiple comparisons were corrected for. The ddPCR data are presented as absolute copy numbers, but the normalization strategy is not fully described.
  - **Why it matters** The gene expression results are used to support the claim that melatonin affects ROR expression independently of direct receptor binding. Without adequate controls and statistical rigor, this conclusion is not fully supported.
  - **Resolution test** Provide full details of the experimental design, including vehicle controls, luzindole concentration-response data, and statistical methods. Report the number of biological and technical replicates. If possible, include a positive control for MT1/MT2 signaling to demonstrate that luzindole is effective in this cell line.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** "Introduction" section
  - **Issue** The abstract and introduction state that melatonin has been "long proposed" as a ligand for RORβ, but the historical context is brief. The authors mention a 1997 correction to a 1994 paper but do not provide details on the nature of the correction or its implications.
  - **Required correction** Expand the historical context to clarify the status of the melatonin-RORβ hypothesis, including the correction and subsequent conflicting reports.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods, "Molecular Docking and Molecular Dynamics Simulation"
  - **Evidence pointer** "Materials and Methods" section
  - **Issue** The methods for molecular docking and MD simulation are described briefly. The authors do not specify the force field used for MD, the water model, the equilibration protocol, or the number of replicates.
  - **Required correction** Provide additional methodological details for the MD simulation to allow reproducibility.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Figure 5
  - **Evidence pointer** Figure 5 legend
  - **Issue** The DSF data are presented as normalized fluorescent intensities, but the normalization method is not described in the figure legend or methods.
  - **Required correction** Describe the normalization procedure for DSF data in the methods or figure legend.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion
  - **Evidence pointer** "Discussion" section
  - **Issue** The authors speculate that melatonin may bind to an unidentified nuclear receptor, but this speculation is not supported by experimental evidence in this study.
  - **Required correction** Clearly label this as speculation and avoid overstating the claim.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 7
  - **Evidence pointer** Figure 7 legend
  - **Issue** The figure legend states "Experiments were performed with at least triplicates," but it is unclear whether this refers to biological or technical replicates.
  - **Required correction** Specify the type and number of replicates in the figure legend.

## Technical failings that need to be addressed before the case is established
- R1-M1: Insufficient ITC experimental details and lack of dilution controls.
- R1-M2: Lack of protein quality and functional characterization for the recombinant RORβ LBD.
- R1-M3: Incomplete reporting of docking scores and MD simulation metrics.
- R1-M4: Inadequate controls and statistical details for gene expression experiments.

## Risk / unsupported claims
- The claim that melatonin is "unlikely a putative receptor for RORβ" is supported by the biophysical data, but the strength of this conclusion is limited by the lack of protein characterization and ITC methodological details.
- The claim that melatonin upregulates RORα and RORβ mRNA expression is supported by the data, but the mechanism (independent of MT1/MT2) is not fully established due to the limited luzindole experiments.
- The speculation that melatonin may bind to an unidentified nuclear receptor is unsupported by experimental evidence in this study.
- The docking results are presented as suggestive but are not rigorously validated; the claim that melatonin "potentially" binds all RORs is weakly supported.
- The statement that "molecular docking, although useful for predicting ligand binding modes and affinities computationally, may not always align with experimental data" is a general observation and not a specific finding of this study.

## Assessment against Nature-style criteria
- **Originality** The study addresses a long-standing controversy in the field and provides new biophysical evidence against the melatonin-RORβ hypothesis. The combination of computational and experimental approaches is not entirely novel, but the specific application to this question is of interest.
- **Scientific importance** The question of whether melatonin directly binds RORβ has implications for understanding melatonin signaling and circadian biology. A definitive answer would be valuable, but the current study does not fully resolve the issue due to methodological limitations.
- **Interdisciplinary readership** The topic is relevant to chronobiology, nuclear receptor biology, and pharmacology. The methods span computational biology, biophysics, and molecular biology, which may appeal to a broad audience, but the technical detail may limit accessibility.
- **Technical soundness** The biophysical experiments are conceptually sound but lack sufficient methodological detail and protein characterization to fully support the conclusions. The computational results are presented without rigorous validation. The gene expression experiments are preliminary.
- **Readability for nonspecialists** The manuscript is generally well written and the logic is clear. However, some sections, particularly the docking and MD simulation descriptions, may be difficult for nonspecialists to follow. The figures are informative but could benefit from more detailed legends.

## Recommendation posture
Supportive if technical concerns are resolved. The core question is relevant and the negative biophysical results are potentially important, but the manuscript requires additional experimental details, protein characterization, and more rigorous computational analysis before the conclusions can be fully accepted.