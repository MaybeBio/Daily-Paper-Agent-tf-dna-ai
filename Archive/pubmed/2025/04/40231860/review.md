## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided by the author.
- **Assessment boundary** Scientific and technical evaluation of the methodology, results, and claims as presented. No assessment of literature novelty beyond the provided text.
- **Shared manuscript claim summary** The authors present a deep ensemble docking pipeline combining AlphaFold-Metainference structural ensembles, binding site filtering, and a multilabel QSAR classifier to screen small molecules against the partially disordered protein AR-V7. They report identification of 41 functional binding sites, a 17-fold improvement in multibinding site hit rate over naive docking, and modulation of AR-V7 dynamics by the selected compound ChEMBL22003, including reduced conformational entropy and altered solvent exposure of phase separation-prone regions.
- **Visible evidence base** Methods sections for structural ensemble generation, binding site detection, docking, machine learning, and atomistic simulations. Results sections for structural ensemble, binding site selection, docking, QSAR model performance, and ChEMBL22003 modulation. Figures 1-6 and Tables S1-S2 referenced but not provided. Supplementary figures S1-S16 referenced but not provided.
- **Missing materials affecting confidence** All figures and supplementary tables (Figures 1-6, S1-S16; Tables S1-S2) are referenced but not included in the provided material. Convergence analysis (Figure S4), validation statistics (Figure S3), and detailed model performance metrics (Figure S2) are not visible. The GitHub repository containing SMILES and binding energies for the 402 screened compounds is not accessible from the provided text.

## Reviewer
- **Overall assessment** The manuscript presents a methodologically ambitious pipeline that addresses a genuine challenge in structure-based drug discovery for partially disordered proteins. The integration of AlphaFold-Metainference with binding site filtering and machine learning acceleration is conceptually sound and the application to AR-V7 is clinically relevant. However, the evidence base as provided is insufficient to fully evaluate the validity of the core claims. Key quantitative results, validation metrics, and convergence analyses are referenced but not visible. The claim of functional modulation by ChEMBL22003 rests on a single compound and a limited set of analyses, and the interpretation of the entropy and solvent exposure changes requires more careful consideration of statistical significance and mechanistic basis. The comparison with naive docking is suggestive but the practical significance of the hit rate improvement is not contextualized against known AR-V7 binders or experimental validation.
- **Who would be interested in the results, and why** Computational chemists and structural biologists working on intrinsically disordered proteins and their targeting by small molecules. Drug discovery researchers focused on transcription factors, particularly androgen receptor splice variants in castration-resistant prostate cancer. Method developers interested in integrating machine learning with ensemble-based docking. The pipeline concept could be transferable to other partially disordered targets, which broadens the potential readership.
- **Major strengths** The manuscript addresses a real and under-served problem: structure-based screening against partially disordered proteins with multiple transient binding sites. The use of AlphaFold-Metainference to generate a structural ensemble is a modern and appropriate choice. The binding site filtering criteria (RMSF, hydropathy, volume) are physically motivated and the reduction from 3718 to 41 sites is a substantial computational saving. The multilabel QSAR approach is a sensible way to handle the multi-site screening problem. The application to AR-V7 is clinically meaningful, and the identification of binding sites in LLPS-prone regions is an interesting and potentially important observation. The inclusion of atomistic MD to assess the effect of a selected binder is a valuable validation step.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (validation of structural ensemble), R1-M2 (QSAR model evaluation), R1-M3 (statistical significance of MD results), R1-M4 (EPI-001 comparison).
- **Assessment against Nature-style criteria** Originality: The combination of AF-Metainference, binding site filtering, and multilabel QSAR for PDP targeting is novel, though each component is established. Scientific importance: The problem is important and the AR-V7 application is clinically relevant, but the impact is currently limited by lack of experimental validation and incomplete evidence. Interdisciplinary readership: The work bridges computational chemistry, machine learning, and cancer biology, which could attract a broad audience if the claims are substantiated. Technical soundness: The methodology is generally sound in design, but the provided evidence is insufficient to verify key technical claims, particularly regarding ensemble quality, model performance, and statistical significance. Readability for nonspecialists: The manuscript is clearly written and the logic is accessible, though some technical details (e.g., Metainference equations) may be dense for a general reader. Overall, the manuscript has potential but does not currently meet the standard of evidence required for a high-impact journal.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the application is relevant, but the manuscript requires substantial additional evidence and analysis to establish the validity of the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validity of structural ensemble
- **Claim pointer** The authors claim that the AF-Metainference ensemble "well captures the current understanding of the IDR part of the AD domain" and that secondary structure predictions show high propensity regions consistent with NMR data.
- **Evidence pointer** Results and Discussion, "AR-V7 Structural Ensemble"; Figure 1; Figure S3
- **Concern** The validation of the structural ensemble is not visible. The authors reference Figure S3 for MolProbity statistics, but these are not provided. The comparison with NMR data is qualitative and the authors acknowledge sequence differences between their construct and the NMR construct (WT*). The claim that the ensemble "well captures" experimental understanding is not quantitatively supported. The pLDDT-based definition of structured regions and the RMSF threshold of 4.5 nm for sticky residues are presented without justification or sensitivity analysis.
- **Why it matters** The entire pipeline depends on the quality and representativeness of the structural ensemble. If the ensemble is biased or incomplete, the identified binding sites and subsequent docking results may be unreliable. The lack of visible validation metrics prevents the reader from assessing whether the ensemble is fit for purpose.
- **Resolution test** Provide the MolProbity validation statistics for the backmapped ensemble. Include a quantitative comparison of secondary structure propensities with the NMR data, accounting for sequence differences. Justify the RMSF threshold for sticky residues with reference to the NMR data or other experimental evidence. Perform a sensitivity analysis on the pLDDT threshold and the RMSF cutoff to show that the identified binding sites are robust to these choices.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validity of QSAR model
- **Claim pointer** The authors claim that the multilabel QSAR model can "swiftly screen a larger space of 2 million ChEMBL compounds" and that the screened set shows a 17-fold improvement in multibinding site hit rate compared to naive docking.
- **Evidence pointer** Methods, "Machine Learning"; Results and Discussion, "Deep Learning Multilabel Classification Model"; Figure 4; Figure 5; Table S1; Figure S2
- **Concern** The evaluation of the QSAR model is not visible. The authors reference Table S1 for best results and Figure S2 for training/testing metrics, but these are not provided. The MCC values are mentioned but the actual numbers are not given. The comparison between naive docking and screened docking is presented as a distribution shift (Figures 4 and 5), but the statistical significance of this difference is not assessed. The claim of a 17-fold improvement is based on a threshold of "active against more than 30 binding sites," which is arbitrary and not justified. The practical utility of the model for prospective screening is not demonstrated.
- **Why it matters** The QSAR model is the core acceleration component of the pipeline. Without visible performance metrics, the reader cannot assess whether the model is sufficiently accurate to be useful. The hit rate comparison is the key quantitative claim of the paper, and it must be rigorously established with appropriate statistical tests and meaningful thresholds.
- **Resolution test** Provide the full evaluation report (Table S1, Figure S2) including MCC, precision, recall, and F1 scores per binding site and overall. Report the distribution of binding energies for naive and screened sets with appropriate statistical tests (e.g., Mann-Whitney U test). Justify the 70% threshold for defining "active" compounds and the 30-binding-site threshold for the hit rate comparison. Consider reporting enrichment factors or ROC curves to demonstrate the model's screening utility.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical significance of MD results
- **Claim pointer** The authors claim that ChEMBL22003 binding leads to "less conformational entropy" and "smaller solvent exposure of phase separation-prone regions" in AR-V7, promoting it as a potential phase separation modulator.
- **Evidence pointer** Results and Discussion, "Structural Ensemble Modulation of AR-V7 by ChEMBL22003"; Figure 6; Figure S4; Figure S16
- **Concern** The MD results are presented with error bars of ±0.005 kJ/mol·K for entropy and a ratio of 0.95625 for solvent exposure, but the statistical significance of these differences is not established. The entropy difference of 0.08 kJ/mol·K (NN) and 0.15 kJ/mol·K (MIST) is small relative to the absolute values, and the error bars suggest the difference may be within noise. The solvent exposure ratio is presented as an average without confidence intervals or per-residue analysis. The convergence analysis (Figure S4) is referenced but not visible. The selection of 33/41 starting configurations for the holo simulations is not justified, and the potential for bias in the initial binding poses is not addressed.
- **Why it matters** The claim that ChEMBL22003 modulates AR-V7 dynamics is the central biological finding of the paper. If the effect is not statistically robust, the compound cannot be promoted as a potential phase separation modulator. The small magnitude of the observed changes requires careful statistical treatment to rule out noise.
- **Resolution test** Provide the convergence analysis (Figure S4) and demonstrate that the free energy surfaces are converged. Perform a statistical test (e.g., bootstrap or permutation test) on the entropy and solvent exposure differences across the 33 replicas. Report confidence intervals for the solvent exposure ratios. Justify the choice of 33 starting configurations and show that the results are not sensitive to this choice. Consider additional analyses, such as per-residue entropy decomposition, to identify the specific regions affected by ChEMBL22003 binding.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** External validation and comparison
- **Claim pointer** The authors compare their findings with the known AR-V7 binder EPI-001 and find that it is inactive in their QSAR model, attributing this to limitations in docking methodology or a different binding mechanism.
- **Evidence pointer** Results and Discussion, "Deep Learning Multilabel Classification Model"
- **Concern** The failure of the QSAR model to identify EPI-001 as a binder is a significant concern for the model's validity. The authors offer two possible explanations (docking limitations or different binding mechanism) but do not test either. The claim that EPI-001 binds via conformational selection is speculative and not supported by data presented. The absence of any positive control (a known AR-V7 binder that the model correctly identifies) weakens the credibility of the screening results.
- **Why it matters** The QSAR model is proposed as a tool for identifying AR-V7 binders. If it cannot identify a known binder, its predictive utility is questionable. The lack of a positive control means the reader cannot distinguish between a model that is genuinely identifying novel binders and one that is producing false positives.
- **Resolution test** Include a positive control set of known AR-V7 binders (if available) and demonstrate that the model can identify them. Test the hypothesis of conformational selection by performing docking against an ensemble that includes EPI-001-induced conformations. Discuss the limitations of the docking scoring function in the context of the EPI-001 result and consider whether the model should be recalibrated or the binding site selection criteria revised.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Methods, "Structural Ensemble of AR-V7"
- **Evidence pointer** Location not provided
- **Issue** The description of the AF-Metainference protocol is brief and refers to reference 12 for details. The choice of six replicas and the specific collective variables for bias metainference are not justified.
- **Required correction** Provide a brief justification for the number of replicas and the choice of collective variables. If this is standard practice from reference 12, state so explicitly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Machine Learning"
- **Evidence pointer** Location not provided
- **Issue** The neural network architecture is described but hyperparameters (learning rate, batch size, number of epochs, regularization strength) are not provided. The oversampling strategy for the imbalanced dataset is mentioned but not detailed.
- **Required correction** Provide the full set of hyperparameters and the oversampling procedure (e.g., SMOTE, random oversampling) to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Results and Discussion, "Structural Ensemble Modulation of AR-V7 by ChEMBL22003"
- **Evidence pointer** Figure 6
- **Issue** The statement that ChEMBL22003 "remains bound" to AR-V7 is based on a minimum distance analysis, but the threshold for "bound" is not defined. The RMSD of 0.56 ± 0.17 nm from the initial docking pose is reported, but the significance of this value is not discussed.
- **Required correction** Define the distance threshold for "bound" and discuss the RMSD value in the context of typical binding site fluctuations. Consider whether the RMSD indicates stable binding or significant rearrangement.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Conclusions
- **Evidence pointer** Location not provided
- **Issue** The conclusions section is largely a summary of the methods and results, with limited discussion of the broader implications or limitations of the approach.
- **Required correction** Add a paragraph discussing the limitations of the pipeline (e.g., dependence on ensemble quality, scoring function accuracy, lack of experimental validation) and the potential for generalization to other partially disordered proteins.

## Risk / unsupported claims
- The claim that the AF-Metainference ensemble "well captures the current understanding of the IDR part of the AD domain" is not quantitatively supported by visible evidence.
- The claim of a 17-fold improvement in multibinding site hit rate is based on an arbitrary threshold and lacks statistical testing.
- The claim that ChEMBL22003 is a "potential AR-V7 phase separation modulator" is based on small, potentially non-significant changes in entropy and solvent exposure.
- The claim that the QSAR model can "swiftly screen" 2 million compounds is not supported by timing or computational cost data.
- The failure of the QSAR model to identify EPI-001 as a binder is not adequately explained or resolved.
- The statement that binding sites are "functionally relevant" based on LLPS propensity is correlative and not experimentally validated.