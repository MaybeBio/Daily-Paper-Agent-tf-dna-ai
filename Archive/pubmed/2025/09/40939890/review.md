## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, conclusion, and figure/table legends. Supplementary data files were referenced but not provided.
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided manuscript text. No assessment of editorial quality or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors report a machine learning-driven approach to engineer the transcription factor BmoR for strict signal molecule orthogonality. They identify critical residue regions via a Random Forest model trained on mutagenesis data, generate mutants with exclusive responsiveness to either n-pentanol or isopentanol, and apply an isopentanol-orthogonal biosensor to screen a producer strain achieving 12.6 g/L isopentanol in fed-batch fermentation.
- **Visible evidence base** Main text figures (Figs 1-7), Tables 1-2, and referenced supplementary figures/tables (Figs S1-S28, Tables S1-S5). Supplementary data files (Supporting data 1-3) were not accessible for review.
- **Missing materials affecting confidence** Supplementary data files (training and prediction datasets), detailed code for machine learning and molecular simulation pipelines, and several supplementary figures/tables referenced in the text were not provided. These are essential for independent verification of the computational and experimental claims.

## Reviewer
- **Overall assessment** This manuscript presents a potentially valuable approach for engineering transcription factor specificity using machine learning-guided semi-rational design. The integration of Random Forest modeling with molecular simulation to identify critical residue regions is conceptually interesting and the resulting biosensors show promising selectivity. However, the current evidence base has significant gaps that prevent full evaluation of the claims. The machine learning methodology is described with insufficient detail to assess its robustness, the relationship between predicted and experimentally validated mutants is not fully transparent, and several key controls and statistical analyses are missing. The application demonstration is compelling but the reported titer improvement needs more context regarding strain background and fermentation conditions. The work is likely of interest to the synthetic biology and metabolic engineering community, but the technical validation as presented is incomplete.
- **Who would be interested in the results, and why** Researchers in synthetic biology, metabolic engineering, and biosensor development would be the primary audience. The machine learning-guided approach to engineer transcription factor specificity addresses a common bottleneck in developing biosensors for metabolic pathway optimization. The demonstration of an isopentanol-orthogonal biosensor for screening overproducers has direct relevance to biofuel production. The generalizable framework for engineering ligand-binding proteins could also interest computational biologists working on protein design.
- **Major strengths**
  1. The conceptual advance of using machine learning to identify critical residue regions for ligand specificity, rather than relying on random mutagenesis alone, is a meaningful methodological contribution.
  2. The demonstration of strict orthogonality between closely related alcohol isomers (n-pentanol vs isopentanol) is technically impressive and addresses a real limitation in current biosensor technology.
  3. The end-to-end application from biosensor engineering to strain screening and fermentation achieving a high titer provides a complete use case.
  4. The combination of computational prediction with experimental validation through multiple orthogonal assays (fluorescence, binding affinity, competitive assays) strengthens the conclusions.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of machine learning methodology
  - **Claim pointer** The authors claim that "Random Forest Algorithm trained on full-length BmoR mutagenesis data generated a model BT with 88.5% prediction accuracy, revealing BmoR-SM hydrogen bond (BSH) counts were the primary determinant of activation."
  - **Evidence pointer** Methods section "Machine learning method for BmoR"; Figure 2; Supporting data 1-2 (not provided)
  - **Concern** The machine learning methodology is described with insufficient detail to assess its validity. The training dataset of 245 mutants is relatively small for a Random Forest model with five input features, and the manuscript does not report cross-validation procedures, hyperparameter tuning, or feature importance metrics beyond the claim that BSH counts were primary. The prediction accuracy of 88.5% is reported without confidence intervals or comparison to baseline models. The prediction dataset of 5,700 saturation mutants is described as being generated via "batch processing" in Discovery Studio, but the specific docking parameters, scoring functions, and quality filters are not described. Most critically, the relationship between the model predictions and the experimentally validated mutants is not transparent: the manuscript does not state how many of the 5,700 predicted mutants were experimentally tested, what the hit rate was, or how the final mutants were selected from the predictions.
  - **Why it matters** The central claim of the paper is that machine learning can guide the engineering of transcription factor orthogonality. Without a rigorous description of the model development, validation, and its actual role in guiding experimental choices, this claim cannot be evaluated. The reader cannot determine whether the approach is genuinely predictive or whether the successful mutants were identified through other means.
  - **Resolution test** The authors should provide: (1) detailed methodology for model training including cross-validation results, hyperparameter selection, and feature importance analysis; (2) the full training and prediction datasets as supplementary files; (3) a clear description of how model predictions were used to select mutants for experimental validation, including the number of predicted positives tested and the experimental hit rate; (4) comparison of model performance against simpler baselines (e.g., sequence conservation, random selection).
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental validation and statistical rigor
  - **Claim pointer** The authors claim that mutants such as BmoRA117T/F163Y and BmoRW128R exhibit "strict orthogonality" and "exclusive responsiveness" to specific alcohols, and that BmoRM94V/A117T/F163Y/F272L and BmoRM94V/W128R/F272L achieve "complete ethanol insensitivity."
  - **Evidence pointer** Figures 3-5; Tables 1-2; Methods sections on gradient assays, competitive assays, and MST
  - **Concern** The experimental validation has several gaps. First, the response curves shown in Figures 3C, 3D, 3I, 3J, 4B, 4C, 4H, 5C, 5D, and 5E appear to lack error bars or statistical analysis in several panels, despite the figure legends stating "mean and s.d. (n=3)". Second, the apparent Km values in Table 1 are reported without standard errors or confidence intervals, making it impossible to assess the precision of these estimates. Third, the competitive assays described in Figures 3F, 3G, 3L, 3M, 4D, 4I, 5D, and 5E use a limited range of concentration ratios and do not include statistical tests to demonstrate significant differences between conditions. Fourth, the MST binding data in Table 2 report Kd values for only two mutants and the wild type, with no replicates or error estimates. Fifth, the claim of "complete ethanol insensitivity" is based on a single concentration (100 mM ethanol) and does not test higher concentrations that might be relevant in industrial fermentation.
  - **Why it matters** The core claims of strict orthogonality and ethanol insensitivity are the foundation for the biosensor application. Without proper statistical treatment and comprehensive concentration ranges, the robustness of these claims is uncertain. The lack of error estimates on kinetic parameters undermines the quantitative comparisons between mutants.
  - **Resolution test** The authors should: (1) provide error bars and statistical tests for all response curves; (2) report Km values with standard errors and confidence intervals; (3) include statistical comparisons (e.g., ANOVA with post-hoc tests) for competitive assay data; (4) provide replicate MST measurements with error estimates; (5) test ethanol insensitivity across a range of concentrations (e.g., 0-500 mM) to support the claim of "complete" insensitivity.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Fermentation data and titer claims
  - **Claim pointer** The authors claim that the engineered strain Δ33 achieved "a record 12.6 g/L isopentanol titer" in fed-batch fermentation, representing a "5.09-fold improvement over the shake-flask titer" and exceeding a prior benchmark of 9.5 g/L by 33%.
  - **Evidence pointer** Figure 7I and 7J; Methods section "Fed-batch fermentation"
  - **Concern** The fermentation data are presented with insufficient detail. The fed-batch fermentation conditions are not fully described (e.g., initial glucose concentration, feeding rate, induction timing, temperature profile). The titer of 12.6 g/L is reported as a single time point without a time course showing production kinetics. The comparison to the prior benchmark of 9.5 g/L is made without specifying the strain background, fermentation conditions, or whether the comparison is apples-to-apples. The claim of "record" titer requires a more comprehensive literature comparison. Additionally, the manuscript does not report important fermentation metrics such as yield (g/g glucose), productivity (g/L/h), or final biomass concentration, which are standard for evaluating bioprocess performance.
  - **Why it matters** The fermentation result is a key demonstration of the practical utility of the engineered biosensor. Without proper fermentation characterization and fair benchmarking, the significance of the titer claim cannot be assessed. The "record" claim is particularly strong and requires robust evidence.
  - **Resolution test** The authors should provide: (1) a complete time course of fed-batch fermentation showing glucose consumption, biomass, and isopentanol production; (2) detailed fermentation conditions including feeding strategy and induction; (3) yield and productivity calculations; (4) a systematic comparison to previously reported isopentanol titers with clear specification of strain and conditions.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Molecular mechanism and structural interpretation
  - **Claim pointer** The authors claim that molecular simulations "revealed mechanistic underpinnings" for the observed orthogonality, including specific hydrogen bonds and Pi-alkyl interactions between mutants and alcohols.
  - **Evidence pointer** Figures 3E, 4E, 4J, 6A, 6B; Table S3-S4
  - **Concern** The molecular simulation results are presented in a cursory manner. The manuscript does not describe the simulation parameters, the number of docking poses analyzed, the scoring function used, or how the representative binding modes were selected. The claim that specific residues form hydrogen bonds with specific alcohols is not supported by quantitative data (e.g., bond distances, occupancy). The hexamer modeling with AlphaFold 2.0 and 3.0 is mentioned but the structural figures are not available for review. The relationship between the predicted binding modes and the experimentally observed specificity is not systematically analyzed. For example, it is unclear whether the simulations can explain why BmoRA117T/F163Y responds to n-pentanol but not isopentanol, given that these isomers differ only in branching.
  - **Why it matters** The mechanistic interpretation is important for establishing the generalizability of the approach. If the molecular basis of orthogonality is not clearly established, it is difficult to assess whether the method can be applied to other transcription factors and ligands.
  - **Resolution test** The authors should provide: (1) detailed simulation parameters and validation of docking results; (2) quantitative analysis of key interactions (bond distances, angles, occupancies); (3) a systematic comparison of binding modes across all four alcohols for each mutant; (4) structural figures with clear labeling of key residues and interactions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness of methods
  - **Affected element** Methods section "Machine learning method for BmoR"
  - **Evidence pointer** Methods section, location not provided
  - **Issue** The description of the machine learning pipeline contains inconsistencies. The text states "The model variable named model 1 was defined as a decision tree" and then "The model variable model 1 was defined as a decision tree, with 500 estimators" which appears to be a typo (should be Random Forest, not decision tree). The description of the prediction dataset construction is confusing and would benefit from a clear flowchart.
  - **Required correction** Correct the model descriptions and provide a clear step-by-step description of the data processing and model training pipeline, ideally with a schematic figure.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Figure legends and Tables 1-2
  - **Evidence pointer** Figures 3-5; Tables 1-2
  - **Issue** Several figure legends state "mean and s.d. (n=3)" but the corresponding data points do not appear to show error bars. The Km values in Table 1 and Kd values in Table 2 lack error estimates.
  - **Required correction** Ensure all data points include error bars where claimed, and report Km and Kd values with standard errors or confidence intervals.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Introduction and Discussion
  - **Evidence pointer** Introduction, Discussion
  - **Issue** The claim of a "record 12.6 g/L isopentanol titer" is not placed in adequate literature context. The Discussion mentions prior work but does not systematically compare the achieved titer with the full range of previously reported isopentanol production levels.
  - **Required correction** Provide a table or systematic comparison of isopentanol titers from previous studies, including strain, fermentation mode, and conditions.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data availability statement
  - **Evidence pointer** Data availability section
  - **Issue** The data availability statement is vague. The training and prediction datasets are described as "Supporting data" but were not provided with the manuscript. The code for the machine learning model is not mentioned.
  - **Required correction** Provide the full datasets and code as supplementary files or deposit them in a public repository with clear accession information.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Figure quality
  - **Affected element** Figure 1B
  - **Evidence pointer** Figure 1B
  - **Issue** The legend for Figure 1B states "The circles with different colours represented different signal molecules (SMs). The number of the circles represented the response ability of BmoR mutants to SMs." This is unclear and does not adequately explain the visualization.
  - **Required correction** Provide a clearer explanation of the visualization, including what the circle size, color, and number represent, and consider using a more standard representation such as a heatmap.
- **Technical failings that need to be addressed before the case is established**
  1. R1-M1: Insufficient detail on machine learning model development, validation, and its role in guiding experimental design.
  2. R1-M2: Incomplete statistical treatment of experimental data, including missing error bars and confidence intervals on key parameters.
  3. R1-M3: Inadequate characterization of fermentation performance and benchmarking against prior work.
  4. R1-M4: Cursory presentation of molecular simulation results without quantitative support for mechanistic claims.
- **Assessment against Nature-style criteria**
  - **Originality**: The concept of using machine learning to identify critical residue regions for transcription factor specificity is a novel contribution. While machine learning has been applied to protein engineering, its specific application to achieving strict ligand orthogonality in a biosensor context is relatively unexplored. The approach of combining Random Forest predictions with molecular simulation to narrow the mutagenesis space is creative.
  - **Scientific importance**: The problem of ligand cross-reactivity in biosensors is a significant bottleneck in metabolic engineering. A generalizable method to engineer strict specificity would have broad utility. The demonstration of practical application to isopentanol production adds applied value. However, the importance is somewhat limited by the narrow scope (one transcription factor, one class of ligands) and the lack of demonstrated generalizability to other systems.
  - **Interdisciplinary readership**: The work bridges machine learning, protein engineering, and metabolic engineering. This could attract readers from computational biology, synthetic biology, and bioprocess engineering. The practical fermentation demonstration may interest industrial biotechnology researchers. However, the technical depth in each area may limit accessibility to a broad interdisciplinary audience.
  - **Technical soundness**: The experimental work appears carefully executed, but the computational methodology is not described with sufficient rigor to assess its validity. The lack of statistical treatment in several key experiments is a concern. The molecular simulation results are presented without adequate methodological detail. The fermentation data lack important context and characterization.
  - **Readability for nonspecialists**: The manuscript is generally well-written and the logic is clear. The introduction provides adequate background. However, the machine learning section is difficult to follow and would benefit from clearer explanation. The figures are informative but some legends are unclear. The discussion effectively contextualizes the findings.
- **Recommendation posture** Supportive if technical concerns are resolved. The core concept is promising and the experimental demonstration is compelling, but the current evidence base is insufficient to fully establish the claims. The manuscript requires substantial revision to address the methodological gaps, statistical shortcomings, and incomplete data presentation before the case for a generalizable machine learning-guided approach to transcription factor orthogonality is convincingly made.

## Risk / unsupported claims
- The claim that BSH counts are "the primary determinant of activation" is not fully supported, as feature importance analysis is not presented and the model's predictive power relative to other features is not quantified.
- The claim of "strict orthogonality" and "exclusive responsiveness" is based on a limited set of alcohols and concentrations; the possibility of cross-reactivity with other structurally related compounds not tested cannot be excluded.
- The claim of "complete ethanol insensitivity" is based on a single concentration (100 mM) and may not hold at higher ethanol levels relevant to industrial fermentation.
- The claim of a "record 12.6 g/L isopentanol titer" is not adequately benchmarked against the full literature and lacks context regarding strain background and fermentation conditions.
- The mechanistic interpretation of orthogonality based on molecular simulations is not quantitatively supported and should be considered speculative.
- The generalizability of the machine learning approach to other transcription factors is claimed but not demonstrated; the manuscript only shows results for BmoR.
- The relationship between the 5,700 computationally predicted mutants and the experimentally validated mutants is not transparent, making it impossible to assess the predictive power of the model.