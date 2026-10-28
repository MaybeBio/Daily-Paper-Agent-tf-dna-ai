## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency of the presented evidence
- **Shared manuscript claim summary** The authors report that the transcription factors ERα and Sox2 exhibit multiphasic DNA and RNA binding kinetics, propose distinct mechanistic models for each protein, and suggest that ERα binding involves a novel reaction mechanism with product feedback and complex isomerization
- **Visible evidence base** Fluorescence polarization equilibrium binding, FP-based competitive dissociation, FP-based jump dilution, surface plasmon resonance, and kinetic simulations
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (Supplemental Figures 1-7, Supplemental Table 1) were not provided; raw data files and complete simulation parameter sets were not available for independent verification

## Reviewer

- **Overall assessment** This manuscript presents a detailed biophysical characterization of nucleic acid binding kinetics for two transcription factors, ERα and Sox2. The observation of multiphasic binding kinetics is potentially interesting, and the authors are appropriately cautious in proposing models. However, the manuscript has several significant weaknesses. The central claim of a "novel" ERα reaction mechanism rests on simulations that are acknowledged to be imperfect fits, and the authors do not provide sufficient evidence to exclude simpler alternative explanations. The distinction between the proposed models for ERα and Sox2 is not always clearly supported by the data presented. The manuscript would benefit from a more rigorous quantitative treatment, additional experimental validation of the proposed models, and clearer presentation of the evidence for nonspecialist readers.

- **Who would be interested in the results, and why** Researchers studying transcription factor nucleic acid binding mechanisms, particularly those interested in RNA-mediated regulation of transcription factor activity. The work may also be of interest to biophysicists studying protein-nucleic acid interaction kinetics and to those studying ERα and Sox2 biology, given their importance in development and disease. The proposed kinetic frameworks could inform future studies on how RNA competes with DNA for transcription factor binding in vivo.

- **Major strengths** The authors use multiple complementary biophysical techniques (FP and SPR) to characterize binding kinetics. The systematic evaluation of multiple candidate models is a strength, as is the explicit acknowledgment that the proposed ERα model is a "framework" rather than a definitive mechanism. The comparison between ERα and Sox2, two structurally distinct transcription factors, provides a useful contrast. The authors also appropriately test and rule out some alternative explanations, such as direct transfer artifacts and the "locked" conformation model.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** The authors claim that ERα nucleic acid binding proceeds via a novel reaction mechanism involving complex isomerization and product feedback, and that this mechanism differs from that of Sox2.
- **Evidence pointer** Results section "ERα DBD-Ext multiphasic dissociation is not due to a 'locked' binding conformation"; Discussion section "A model for ERα DBD-Ext DNA and RNA binding"; Figure 6c; Supplemental Figures 6-7
- **Concern** The central claim of a novel ERα mechanism is supported primarily by simulations that the authors themselves state are "certainly not a perfect fit to the experimental data." The manuscript does not provide a rigorous statistical comparison between the proposed model and alternative models, nor does it provide independent experimental validation of the predicted intermediate states or feedback mechanism. The claim that changing a single rate constant (k-2) can recapitulate the differences between DNA and RNA binding is presented qualitatively, without quantitative fitting or error analysis. Without stronger evidence, the "novel mechanism" claim is not established.
- **Why it matters** The novelty of the proposed ERα mechanism is a central claim of the manuscript. If the model is not well-constrained by the data, the conclusion that ERα uses a fundamentally different mechanism from Sox2 is not justified. This affects the overall significance of the work.
- **Resolution test** Provide quantitative model fitting with confidence intervals, perform model comparison using appropriate statistical criteria (e.g., AIC or BIC), and/or provide independent experimental evidence (e.g., stopped-flow kinetics, single-molecule experiments, or mutagenesis) that tests specific predictions of the proposed model.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Alternative explanations not excluded
- **Claim pointer** The authors claim that the multiphasic dissociation kinetics are not due to direct transfer, based on FP-based jump dilution experiments showing biphasic dissociation in the absence of competitor.
- **Evidence pointer** Results section "ERα DBD-Ext and Sox2 ligand dissociation are multiphasic"; Figure 2
- **Concern** The jump dilution experiment is performed for only one ERα construct-ligand pair (ERα DBD-Ext with ΔERE dsDNA). The authors do not perform jump dilution experiments for ERα with ERE or RNA ligands, nor for Sox2 with any ligand. The claim that multiphasic dissociation is a general property of these protein-ligand interactions, rather than an artifact of the specific experimental conditions, is therefore not fully supported. Additionally, the authors note that the fast component is accelerated 4-5x in the presence of competitor, which is not fully explained by their model.
- **Why it matters** If direct transfer or another experimental artifact contributes to the observed multiphasic kinetics for some ligand pairs, the interpretation of the kinetic data and the proposed models would be affected.
- **Resolution test** Perform jump dilution experiments for additional ERα-ligand pairs and for Sox2-ligand pairs, or provide a clear justification for why the single experiment is sufficient to generalize the conclusion.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of kinetic analysis
- **Claim pointer** The authors report apparent association and dissociation rate constants for ERα and Sox2 binding to various nucleic acid ligands.
- **Evidence pointer** Results section "ERα DBD-Ext and Sox2 HMG ligand dissociation are multiphasic"; Results section "ERα DBD-Ext, but not Sox2 HMG, exhibits multiphasic association to target DNA"; Table 1; Figure 3
- **Concern** The manuscript reports rate constants with associated errors, but the methods for determining these values are not described in sufficient detail. For example, the smoothing spline approach for determining initial association rates is not standard practice, and the criteria for "pruning" data to include only initial linear phases are not specified. The authors do not report goodness-of-fit statistics for the biexponential regressions, nor do they report how many independent experiments were used for each reported value. The comparison of rate constants between DNA and RNA ligands is done qualitatively, without statistical testing.
- **Why it matters** The quantitative values of the rate constants are central to the conclusions. If the methods for determining them are not rigorous or reproducible, the conclusions are weakened.
- **Resolution test** Provide a more detailed description of the data analysis methods, including specific criteria for data inclusion/exclusion, goodness-of-fit statistics, and statistical comparisons between conditions. Consider using more standard kinetic analysis methods where possible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model identifiability and parameter estimation
- **Claim pointer** The authors propose a specific kinetic model for ERα binding (Figure 6c) and claim that simulations with this model recapitulate the general kinetic trends for both DNA and RNA binding.
- **Evidence pointer** Discussion section "A model for ERα DBD-Ext DNA and RNA binding"; Figure 6c; Supplemental Figures 6-7; Materials and Methods "ERα Reaction Scheme Simulations"
- **Concern** The model in Figure 6c has multiple parameters (k1, k-1, k2, k-2, k3, k-3, k3b, kα, kβ), and the authors state that they used "fixed rate constant values" for simulations. However, they do not report how these values were chosen, whether the model is identifiable from the available data, or whether other parameter sets could produce similar results. The claim that changing a single parameter (k-2) can explain the difference between DNA and RNA binding is not supported by a systematic parameter sensitivity analysis.
- **Why it matters** A model with many free parameters can fit many datasets. Without demonstrating that the parameters are constrained by the data and that the model is identifiable, the proposed mechanism remains speculative.
- **Resolution test** Perform a parameter identifiability analysis, report the parameter values used, and demonstrate that the model predictions are robust to reasonable parameter variations. Alternatively, simplify the model to the minimum number of parameters needed to explain the data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The authors state that their findings "reveal that Sox2 and ERα bind RNA and DNA with previously unappreciated multiphasic binding kinetics, and that their reaction mechanisms differ."
- **Evidence pointer** Abstract; Discussion
- **Concern** The study uses truncated constructs (ERα DBD-Ext and Sox2 HMG) rather than full-length proteins. The authors do not discuss how the absence of other domains (e.g., the ligand-binding domain of ERα, the transactivation domains of both proteins) might affect the binding kinetics. The physiological relevance of the observed multiphasic kinetics is not addressed experimentally.
- **Why it matters** The conclusions are framed in terms of ERα and Sox2 as transcription factors, but the experiments use isolated DNA-binding domains. The relevance of the findings to the full-length proteins and to cellular contexts is unclear.
- **Resolution test** Discuss the potential limitations of using truncated constructs, and if possible, perform key experiments with full-length proteins or provide evidence that the truncated constructs recapitulate the behavior of the full-length proteins.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 3
- **Evidence pointer** Results section "ERα DBD-Ext, but not Sox2 HMG, exhibits multiphasic association to target DNA"
- **Issue** The description of the triphasic association is difficult to follow. The authors state that "an approximately monophasic association phase was complete in ~2 minutes, followed by a 10-20 minute 'lag' phase, and ending in a second association phase." It is unclear how the "lag" phase is defined and quantified, and how the authors distinguish this from a simple biphasic association with a slow second phase.
- **Required correction** Provide a clearer definition of the "lag" phase, including how it is identified and measured. Consider showing representative raw association curves with the phases annotated.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** Table 1
- **Evidence pointer** Results section "ERα DBD-Ext and Sox2 HMG equilibrium ligand binding"
- **Issue** The table reports Kd app values and Hill coefficients, but the number of independent experiments and the method for calculating errors are not specified in the table legend or in the main text.
- **Required correction** Add information about the number of replicates and the error calculation method to the table legend or the main text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of SPR data
- **Evidence pointer** Results section "ERα DBD-Ext multiphasic DNA dissociation is conserved across methodology and temperature"; Supplemental Figure 5
- **Issue** The authors note that the percent contribution of the fast phase was lower for SPR than for FP, and that the SPR signal had not plateaued at the highest protein concentrations. This discrepancy is not fully discussed, and the authors do not address whether the SPR surface density or immobilization could affect the observed kinetics.
- **Required correction** Discuss the potential reasons for the quantitative differences between SPR and FP results, and address whether surface effects could influence the SPR measurements.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Accessibility for nonspecialists
- **Affected element** Discussion section "A model for ERα DBD-Ext DNA and RNA binding"
- **Evidence pointer** Figure 6c
- **Issue** The proposed model in Figure 6c is complex, with multiple states and transitions. The figure legend is brief, and the model is not described in sufficient detail in the text for a reader who is not a kineticist to understand the key features and predictions.
- **Required correction** Expand the description of the model in the text, and consider simplifying the figure or providing a step-by-step explanation of the model's features and predictions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of how these findings relate to previous studies of transcription factor binding kinetics is limited. The authors mention prior work on ERα and Sox2 RNA binding but do not place their kinetic findings in the broader context of what is known about transcription factor target search dynamics.
- **Required correction** Add a brief discussion of how the observed multiphasic kinetics might relate to transcription factor target search mechanisms and to previous kinetic studies of other transcription factors.

- **Technical failings that need to be addressed before the case is established** The central claim of a novel ERα mechanism is not quantitatively established. The model simulations are acknowledged to be imperfect fits, and no statistical model comparison is provided. The generalizability of the findings from truncated constructs to full-length proteins is not addressed. The jump dilution control is performed for only one protein-ligand pair, limiting the strength of the claim that multiphasic dissociation is not due to direct transfer.

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The observation of multiphasic binding kinetics for transcription factors is not entirely new, but the specific comparison between ERα and Sox2 and the proposal of a feedback mechanism for ERα have some novelty.
  - Scientific importance: Moderate. The findings could be relevant to understanding how RNA regulates transcription factor activity, but the physiological relevance is not demonstrated, and the proposed mechanism is not firmly established.
  - Interdisciplinary readership: Limited. The manuscript is primarily of interest to biophysicists and biochemists studying protein-nucleic acid interactions. The presentation is technical and may not be accessible to a broad biological audience.
  - Technical soundness: The experimental methods are generally sound, but the data analysis and model fitting lack rigor. The simulations are not quantitatively validated, and alternative models are not systematically excluded.
  - Readability for nonspecialists: The manuscript is written in a technical style that assumes familiarity with kinetic analysis. The key findings and their significance could be communicated more clearly.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents interesting observations and a plausible framework, but the central claim of a novel ERα mechanism is not quantitatively supported. The authors should strengthen the model validation, address the generalizability of their findings, and improve the clarity of the presentation before the case is established.