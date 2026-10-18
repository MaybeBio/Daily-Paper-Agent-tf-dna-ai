## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary references)
- **Assessment boundary** Scientific validity of the machine learning workflow, docking analysis, and cell-based validation; claims regarding RAD51 modulation and cisplatin sensitization
- **Shared manuscript claim summary** The authors report a machine learning-guided virtual screening workflow that identified madecassoside as a potential RAD51 modulator. They claim that madecassoside sensitizes MDA-MB-231 breast cancer cells to cisplatin and inhibits cisplatin-induced RAD51 foci formation, suggesting impairment of homologous recombination repair.
- **Visible evidence base** Abstract, full methods, results and discussion sections, Figures 1–5 (referenced), Tables 1–2 (referenced), Supplementary Table S1 (referenced)
- **Missing materials affecting confidence** Figures and tables are referenced but not provided in the manuscript text; raw data, model training/test splits, docking scores for all candidates, and full statistical outputs are not available; no dose-response curves or quantitative image analysis data are shown

## Reviewer
- **Overall assessment** The manuscript presents a potentially interesting application of machine learning to natural product screening for RAD51 inhibition. The workflow is logical and the combination of computational and experimental approaches is commendable. However, several technical issues undermine the strength of the claims. The dataset is very small (119 compounds after filtering), the docking analysis is limited to two compounds with no comparison to known RAD51 inhibitors, and the biological validation is restricted to a single cell line with no mechanistic depth. The claim that madecassoside is a "RAD51 modulator" is not fully supported by the evidence presented, as direct RAD51 binding or biochemical inhibition is not demonstrated. The manuscript would benefit from additional experiments and more rigorous computational validation.

- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, cancer therapeutics, and computer-aided drug discovery would find this work of interest. The application of machine learning to identify natural products targeting RAD51 could inform future screening efforts. Clinically oriented researchers focused on overcoming cisplatin resistance in breast cancer may also find the sensitization data relevant, though the preliminary nature of the results limits immediate translational impact.

- **Major strengths** 
  1. The integration of multiple public databases (ChEMBL, PubChem, BindingDB) with a clear curation pipeline is methodologically sound.
  2. The systematic comparison of five machine learning algorithms across four preprocessing strategies is thorough and well described.
  3. The use of both computational (docking) and experimental (cell-based) validation provides a multi-pronged approach.
  4. The authors acknowledge limitations regarding dataset size, mechanistic depth, and lack of in vivo studies.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data sufficiency and model validity
  - **Claim pointer** The claim that the RF model achieved "accuracy of 0.933, sensitivity of 0.800, specificity of 1.000, Cohen's kappa of 0.842, and ROC-AUC of 0.980" and that this model is suitable for virtual screening.
  - **Evidence pointer** Results section "Performance Evaluation of Machine Learning Models"; Figure 2 (not provided)
  - **Concern** The final dataset contains only 119 compounds (39 active, 80 inactive) after filtering. This is an extremely small dataset for training a machine learning model, particularly with 2185 molecular features. The reported performance metrics are likely optimistic due to the small sample size and the use of random sampling for train/test splits. No external validation on an independent dataset is reported, which is critical for assessing generalizability.
  - **Why it matters** A model trained on such a small dataset may not generalize to the diverse chemical space of natural products. The virtual screening results (188 hits from 1142 compounds) could be an artifact of overfitting. Without external validation or a more robust cross-validation scheme (e.g., repeated stratified k-fold), the reliability of the screening predictions is questionable.
  - **Resolution test** Provide external validation on a held-out dataset or an independent set of known RAD51 inhibitors. Report performance metrics with confidence intervals. Consider using a more conservative evaluation scheme such as repeated stratified cross-validation or leave-one-out cross-validation.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic evidence
  - **Claim pointer** The claim that madecassoside "inhibits ATP-dependent RAD51 activation and filament stabilization" and acts as a "RAD51 modulator."
  - **Evidence pointer** Discussion section; docking analysis (Figure 4, not provided)
  - **Concern** The mechanistic claim is based solely on docking simulations and indirect cell-based assays. No direct biochemical evidence is provided, such as RAD51 ATPase activity assays, electrophoretic mobility shift assays for DNA binding, or surface plasmon resonance for direct binding affinity. The docking analysis is limited to two compounds with no comparison to known RAD51 inhibitors or a positive control. The statement that madecassoside inhibits "ATP-dependent RAD51 activation" is speculative without functional validation.
  - **Why it matters** The central claim of the manuscript is that madecassoside modulates RAD51 function. Without direct biochemical evidence, the mechanism remains hypothetical. This weakens the significance of the findings and limits the conclusions that can be drawn about the compound's mode of action.
  - **Resolution test** Perform biochemical assays to demonstrate direct RAD51 inhibition, such as measuring RAD51 ATPase activity in the presence of madecassoside, or testing RAD51 filament formation on DNA in vitro. Include a known RAD51 inhibitor (e.g., B02) as a positive control in docking and biochemical experiments.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological validation scope
  - **Claim pointer** The claim that madecassoside "sensitizes breast cancer cells to cisplatin" based on clonogenic survival assays in MDA-MB-231 cells.
  - **Evidence pointer** Results section "Madecassoside Inhibits RAD51 Foci Formation Induced by Cisplatin in Cancer Cells"; Figure 5 (not provided)
  - **Concern** The biological validation is limited to a single cell line (MDA-MB-231). No dose-response curves for madecassoside alone or in combination with cisplatin are shown. The concentration of madecassoside used (5 μM) is not justified, and no toxicity data for madecassoside alone are presented. The effect on RAD51 foci is qualitative, and no quantification or statistical analysis is described.
  - **Why it matters** The translational relevance of the findings depends on the robustness of the sensitization effect. A single cell line with limited dose-response data is insufficient to establish that madecassoside enhances cisplatin sensitivity. The lack of quantification for RAD51 foci makes it difficult to assess the magnitude of the effect.
  - **Resolution test** Include additional breast cancer cell lines (e.g., MCF-7, HCC1937) and a non-cancerous control. Provide full dose-response curves for madecassoside and cisplatin, both alone and in combination, with combination index analysis. Quantify RAD51 foci per nucleus with statistical analysis and include representative images.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods section "Model Development and Training Strategy"
  - **Evidence pointer** Methods section, location not provided
  - **Issue** The hyperparameters for each machine learning algorithm are not reported. The RF model is described as "optimized" but the tuning process is not described.
  - **Required correction** Provide details on hyperparameter tuning (e.g., grid search ranges, final parameters) for all five algorithms to ensure reproducibility.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data Availability Statement
  - **Evidence pointer** Data Availability Statement
  - **Issue** The statement indicates that data are available in public databases but does not specify which specific assay endpoints or compound identifiers were used. The in-house natural product library is not described in detail.
  - **Required correction** Provide a detailed list of the natural product library compounds (or a representative subset) and specify the exact data fields retrieved from each database. Consider depositing the curated dataset and model code in a public repository.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results section "Performance Evaluation of Machine Learning Models"
  - **Evidence pointer** Results section, location not provided
  - **Issue** Performance metrics are reported as single values without confidence intervals or standard deviations. The variability across cross-validation folds is not described.
  - **Required correction** Report mean and standard deviation for all performance metrics across cross-validation folds. Include confidence intervals where appropriate.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Figure quality
  - **Affected element** Figure 5 (referenced)
  - **Evidence pointer** Results section, Figure 5 (not provided)
  - **Issue** The description of the immunofluorescence data does not specify the number of cells analyzed, the criteria for foci counting, or whether the analysis was blinded.
  - **Required correction** Provide detailed methods for image analysis, including the number of cells counted per condition, the threshold for foci detection, and whether the analysis was performed blinded to treatment conditions.

- **Technical failings that need to be addressed before the case is established** 
  - R1-M1: Small dataset and lack of external validation for the machine learning model
  - R1-M2: Absence of direct biochemical evidence for RAD51 inhibition
  - R1-M3: Limited biological validation with a single cell line and no dose-response analysis

## Risk / unsupported claims
- The claim that madecassoside "inhibits ATP-dependent RAD51 activation and filament stabilization" is unsupported by direct experimental evidence.
- The claim that the RF model is "optimized" and suitable for virtual screening is not fully supported due to the small dataset and lack of external validation.
- The statement that madecassoside "strongly inhibiting DNA damage repair" is an overstatement based on indirect evidence from foci formation alone.
- The claim that madecassoside is a "promising RAD51-modulating lead compound" is premature without in vivo data or mechanistic validation.
- The assertion that the workflow "accelerate[s] early drug development" is not substantiated by the data presented.