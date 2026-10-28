## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, footnotes) as provided
- **Assessment boundary** Scientific claims, methodological soundness, and evidentiary support based solely on the supplied text; no external data or unpublished materials consulted
- **Shared manuscript claim summary** The authors investigate whether BTB domains from the ZBTB transcription factor family can form heterodimers in a cellular context. Using a fluorescent two-hybrid (F2H) assay, they screen 64 pairwise combinations of eight BTB domains and identify PATZ1-PATZ2 as the only heterodimer-forming pair. They support this with co-expression analysis using ImmGen data and molecular dynamics simulations with MM-GBSA free energy calculations on five homodimers and four putative heterodimers. They conclude that heterodimer formation is rare but energetically feasible for PATZ1-PATZ2, potentially increasing combinatorial specificity of this transcription factor family.
- **Visible evidence base** Abstract; Introduction; Methods sections (cloning, F2H assay, conservation analysis, docking/modelling, MD simulations, MM-GBSA); Results sections (F2H screening, MD analysis of homodimers and heterodimers); Discussion; Supplementary figure/table references (Table S1, Fig. S1-S6); Author contributions; Data availability statement
- **Missing materials affecting confidence** Full figures and tables (Figs. 1-4, Tables 1-3, Supplementary figures and tables) are referenced but not provided; specific numerical data from F2H assays, MD trajectories, and MM-GBSA calculations are not included; details on statistical methods for correlation analysis are incomplete; no information on replicates, controls, or validation of the F2H assay beyond the description; no raw data or analysis scripts

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in transcription factor biology, namely whether BTB domains from the ZBTB family can form heterodimers and what the energetic determinants of such interactions might be. The combination of a cellular screening assay, expression analysis, and computational modelling is potentially powerful. However, the current text does not provide sufficient quantitative data to evaluate the robustness of the key claims. The F2H assay results are described qualitatively, the MM-GBSA calculations lack error estimates and convergence criteria, and the correlation analysis is under-specified. The conclusion that PATZ1-PATZ2 is a unique heterodimer among the tested pairs is supported only if the assay sensitivity and specificity are adequately demonstrated, which is not evident from the text. The computational results are suggestive but not conclusive without additional validation. The manuscript would benefit from clearer presentation of data, more rigorous statistical treatment, and a more cautious interpretation of the energetic calculations.
- **Who would be interested in the results, and why** Researchers studying BTB domain-containing proteins, particularly the ZBTB family of transcription factors, would find this work relevant. Those interested in protein-protein interaction specificity, dimerization energetics, and the functional consequences of homo- versus heterodimer formation in transcriptional regulation would also be engaged. The F2H assay adaptation for BTB domains could be of methodological interest to the broader protein interaction community. The potential link to immune cell function and disease states such as ICF2 syndrome may attract immunologists and clinical geneticists.
- **Major strengths** The study addresses a gap in understanding BTB domain dimerization specificity, moving beyond structural descriptions to functional screening. The use of a cellular assay (F2H) to test pairwise interactions is appropriate and potentially high-throughput. The integration of expression data with physical interaction data adds a layer of biological relevance. The computational analysis attempts to provide mechanistic insight into the observed specificity. The identification of PATZ1-PATZ2 as a candidate heterodimer with co-expression in immune cells is a concrete, testable finding.
- **Major Concerns** The major concerns are detailed below. The most critical issues are the lack of quantitative data for the F2H assay, the absence of error analysis for MM-GBSA calculations, and the incomplete specification of the correlation analysis. These gaps prevent a full assessment of the validity of the central claims.
- **Minor Comments** Several minor issues are listed below, including clarity of writing, missing methodological details, and suggestions for additional analyses that would strengthen the manuscript.
- **Technical failings that need to be addressed before the case is established** The F2H assay results are presented without quantitative thresholds, controls, or replicates. The MM-GBSA calculations are reported as single values without standard deviations or convergence checks. The correlation analysis lacks specification of multiple testing corrections. These are technical shortcomings that must be resolved before the claims can be considered robust.
- **Assessment against Nature-style criteria**  
  *Originality*: The question of BTB heterodimerization is not entirely new, but the systematic screening approach and the combination with energetic analysis provide a fresh perspective. The finding that only one pair forms heterodimers among eight tested is a useful contribution.  
  *Scientific importance*: The potential impact on understanding combinatorial control of gene expression by ZBTB factors is significant. However, the current evidence is preliminary and would need stronger validation to have broad impact.  
  *Interdisciplinary readership*: The work bridges structural biology, biophysics, and cell biology, which could appeal to a diverse audience. The methodological aspects of the F2H assay may interest cell biologists, while the MD simulations may attract computational biologists.  
  *Technical soundness*: The technical execution is difficult to evaluate fully due to missing data. The F2H assay is established, but its application here needs more rigorous validation. The MD simulations are standard but the analysis is incomplete.  
  *Readability for nonspecialists*: The manuscript is generally well-written and accessible, but some sections, particularly the MM-GBSA description, may be challenging for readers without a biophysics background. The abstract is clear and appropriately summarizes the findings.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the approach is potentially valuable, but the current evidence is insufficient to fully support the conclusions. The authors should provide quantitative data, error analysis, and additional validation before the claims can be accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "only the PATZ1-PATZ2 pair formed a heterodimer in this assay" based on the F2H screening of 64 pairwise combinations.
- **Evidence pointer** Results section "PATZ1-PATZ2 is a unique BTB domain heterodimer"; Figure 2 (not provided)
- **Concern** The F2H assay results are described only qualitatively. No quantitative data are provided, such as fluorescence intensity measurements, thresholds for positive interaction, or statistical comparison between pairs. The number of biological replicates and technical replicates is not stated. Without these data, it is impossible to assess whether the assay is sufficiently sensitive to detect weak heterodimers or whether the negative results for other pairs are meaningful. The authors should provide representative images, quantification, and a clear definition of a positive interaction.
- **Why it matters** The central claim of the manuscript, that PATZ1-PATZ2 is a unique heterodimer, rests entirely on the F2H assay. If the assay is not adequately validated or quantified, the conclusion is not supported. This is the foundation for the rest of the study, including the computational analysis.
- **Resolution test** Provide quantitative F2H data with at least three independent experiments, including positive and negative controls. Define a threshold for positive interaction based on fluorescence intensity. Show that the assay can detect known heterodimers and does not produce false positives for known non-interacting pairs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report MM-GBSA free energy calculations for homo- and heterodimers, including a ΔG of −529.5 kcal/mol for the PATZ1-PATZ2 heterodimer, and use these to argue that this heterodimer is energetically favorable.
- **Evidence pointer** Methods section "Estimating free energy differences by MM-GBSA calculations"; Results sections on homodimers and heterodimers; Tables 2 and 3 (not provided)
- **Concern** The MM-GBSA calculations are presented as single values without any measure of uncertainty. No standard deviations, standard errors, or confidence intervals are reported. The text mentions "averaged between two duplicate MD runs" for PATZ1, but no details are given for other systems. The convergence of the calculations is not demonstrated, and the choice of the "most stable conformation" based on RMSD is not described in sufficient detail. MM-GBSA is known to be sensitive to the choice of frames and parameters, and the lack of error analysis makes it impossible to judge whether the reported differences between homo- and heterodimers are significant.
- **Why it matters** The energetic calculations are used to support the biological relevance of the PATZ1-PATZ2 heterodimer. If the calculations are not robust, the conclusion that this heterodimer is energetically favorable is not established. The comparison between homo- and heterodimers, which is a key part of the discussion, depends on the reliability of these numbers.
- **Resolution test** Provide error estimates for all reported ΔG values, such as standard deviations from multiple independent simulations or block averaging. Show convergence of the energies over the simulation time. Describe the criteria for selecting the equilibrated portion of the trajectory in more detail. If possible, validate the MM-GBSA results with an independent method, such as umbrella sampling or free energy perturbation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** The authors state that "Patz1-Bcl6 expression was negatively correlated in dendritic, mast, basophil and eosinophil cells" based on ImmGen data analysis.
- **Evidence pointer** Methods section "ImmGen cell type analysis of RNA co-expression"; Results section "PATZ1-PATZ2 is a unique BTB domain heterodimer"; Table 1 and Figure S1 (not provided)
- **Concern** The correlation analysis is described only briefly. The text does not specify which cell types were included, how many samples per cell type, or how the correlation coefficients were calculated beyond "least-squares linear regression." The p-values are mentioned but no correction for multiple testing is described. Given that 46 genes were analyzed, the number of pairwise comparisons is large, and the risk of false positives is high. The authors should provide a more detailed description of the statistical methods and the results.
- **Why it matters** The co-expression analysis is used to support the biological relevance of the PATZ1-PATZ2 interaction. If the analysis is not statistically rigorous, the claim that these two genes are co-expressed in relevant cell types is weakened. This is important for the argument that the heterodimer could have functional significance in the immune system.
- **Resolution test** Provide a detailed description of the statistical methods, including the number of samples, the correlation test used, and the multiple testing correction applied. Show the full correlation matrix or a heatmap of all pairwise correlations. Report the specific p-values and confidence intervals for the key comparisons.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors constructed models of four putative heterodimers using docking and homology modelling, and used these models for MD simulations.
- **Evidence pointer** Methods section "Structure of heterodimers: docking and modelling"; Results section "Heterodimerization results from additional interactions"
- **Concern** The modelling approach is described but the quality of the models is not assessed. For example, no information is provided on the sequence identity between the templates and the targets, the expected accuracy of the homology models, or the validation of the docking poses. The authors state that the PATZ2 and ThPOK BTB domains were homology modelled, but the templates are only listed, not evaluated. The reliability of the MD simulations depends on the quality of the starting structures, and this is not addressed.
- **Why it matters** The conclusions about the stability and energetics of the heterodimers are based on simulations of models that may contain significant errors. If the models are inaccurate, the calculated energies and interaction patterns may not reflect the true behavior of the proteins. This is a critical issue for the validity of the computational part of the study.
- **Resolution test** Provide an assessment of model quality, such as Ramachandran plots, QMEAN or MolProbity scores, and the sequence identity between templates and targets. Validate the docking poses by comparing with known structures or by using cross-validation. Discuss the potential impact of model errors on the simulation results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "over 200 proteins encoded in the human genome" is vague. It is unclear whether this refers to all BTB domain-containing proteins or specifically to ZBTB family members.
- **Required correction** Specify the exact number of BTB domain-containing proteins and clarify the distinction between BTB domains in general and the ZBTB subfamily.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods, F2H assay
- **Evidence pointer** Methods section "Transfection, live-cell microscopy and F2H assay"
- **Issue** The description of the F2H assay does not mention how the cells were scored for interaction. The text states that colocalization was analyzed "manually or by using the JACoP plugin," but no criteria for a positive interaction are given.
- **Required Correction** Define the criteria for scoring a pair as interacting, including the number of cells analyzed, the threshold for colocalization, and how observer bias was minimized.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, correlation analysis
- **Evidence pointer** Results section "PATZ1-PATZ2 is a unique BTB domain heterodimer"; Table 1
- **Issue** The text mentions "positive and negative correlations" but does not report the actual correlation coefficients or their ranges. The reader cannot assess the strength of the correlations.
- **Required Correction** Report the correlation coefficients and p-values for the key pairs, or provide a supplementary table with all values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph on energetic calculations
- **Issue** The authors state that "homo and heterodimers are characterized by numerous and sometimes short-lived electrostatic interactions" but do not provide specific data to support this claim. It is unclear whether this is a general observation from the simulations or a specific finding.
- **Required Correction** Provide specific examples or quantitative measures of the electrostatic interactions, such as the number of salt bridges or their occupancy over the simulation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, MM-GBSA
- **Evidence pointer** Methods section "Estimating free energy differences by MM-GBSA calculations"
- **Issue** The equation for ΔG is mentioned but not fully written out. The text refers to "equation (1)" but the equation itself is not displayed in the provided text.
- **Required Correction** Include the full equation and define all terms clearly.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Footnotes
- **Evidence pointer** Footnotes, data availability statement
- **Issue** The data availability statement only mentions model coordinates in ModelArchive. It does not mention the availability of the F2H data, the correlation analysis results, or the MD simulation trajectories.
- **Required Correction** Provide a more comprehensive data availability statement, including all raw data and analysis scripts.

## Risk / unsupported claims
- The claim that "only the PATZ1-PATZ2 pair formed a heterodimer" is unsupported without quantitative F2H data and controls.
- The claim that "the PATZ1-PATZ2 heterodimer is as stable as the PATZ1 or PATZ2 homodimers" is not directly supported by the data presented, as the comparison is based on MM-GBSA calculations without error estimates.
- The claim that "heterodimer formation is a possible mechanism to increase the combinatorial specificity" is speculative and not directly tested in this study.
- The claim that "the AT-hook is not necessary for heterodimer formation" is based on the use of minimal BTB domains, but the authors do not test whether the full-length proteins behave similarly.
- The claim that "the F2H assay can be used as a high-throughput screening tool" is not validated in this study, as no demonstration of scalability or reproducibility is provided.
- The correlation analysis results are not fully reported, making it impossible to evaluate the strength and significance of the claimed co-expression patterns.