## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors construct a prognostic transcription factor (TF) machine learning model (HTFSS) for triple-negative breast cancer (TNBC) using LASSO regression on TCGA-BRCA data, validate it in external cohorts, associate it with immune infiltration and immunotherapy response, and propose a targeted drug combination strategy (TSA + DOX ± Calcitriol) supported by in vitro and in vivo experiments.
- **Visible evidence base** Abstract, Introduction, Results (Sections 2.1–2.8), Discussion, Conclusions, Materials and Methods (Sections 4.1–4.10), figure and table references
- **Missing materials affecting confidence** Raw data files, complete figure panels, supplementary tables (S1, S2), supplementary figures (S1–S4), code for model construction, detailed statistical outputs, and full experimental protocols are not provided

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful prognostic model based on three transcription factors for TNBC, with a plausible workflow combining public transcriptomic data, machine learning, and experimental validation. However, several methodological details are insufficiently described, some claims exceed the evidence presented, and the experimental validation is limited in scope. The drug combination strategy, while interesting, is supported by preliminary data only and requires substantial additional evidence to establish clinical relevance.
- **Who would be interested in the results, and why** Researchers in breast cancer genomics and prognostic biomarker discovery, computational oncology groups working on machine learning applications in cancer, and translational researchers interested in drug repurposing or combination therapy strategies for TNBC. The online Shiny app may be of practical interest to clinicians seeking prognostic tools.
- **Major strengths** The study addresses a clinically relevant gap by integrating TF-focused modeling in TNBC. The use of housekeeping gene normalization to improve cross-cohort applicability is a thoughtful methodological choice. The combination of bulk and single-cell RNA-seq data provides complementary perspectives. The inclusion of both in vitro and in vivo experiments strengthens the translational aspect. The development of an interactive web tool enhances potential clinical utility.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5, R1-M6
- **Assessment against Nature-style criteria** Originality: moderate. While TF-based prognostic models exist in other cancers, their specific application to TNBC with this combination of approaches has some novelty. Scientific importance: moderate. The prognostic model may have clinical utility, but the mechanistic and therapeutic claims are not fully substantiated. Interdisciplinary readership: limited. The work is primarily relevant to oncology and computational biology specialists. Technical soundness: partially adequate. Several methodological details are missing or unclear, and some analyses appear incomplete. Readability for nonspecialists: acceptable but could be improved with clearer explanations of the machine learning and bioinformatics steps.
- **Recommendation posture** Supportive if technical concerns are resolved. The core prognostic model is promising, but the current evidence does not fully establish the mechanistic claims or the clinical utility of the drug combination strategy.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The HTFSS model has "broad applicability" with AUC values of 0.877 and 0.987 in training and validation cohorts, respectively.
- **Evidence pointer** Section 2.2, Figure 2D,F
- **Concern** The validation cohort AUC of 0.987 is unusually high and may indicate overfitting or data leakage. The manuscript does not describe how the validation cohorts (GSE58812, GSE173839) were processed, whether batch effects were addressed, or whether the same normalization procedure was applied. The LASSO model was built on TCGA data, and the validation cohorts are from different platforms; without detailed normalization and harmonization steps, the reported performance is difficult to interpret.
- **Why it matters** Overly optimistic performance estimates undermine the reliability of the prognostic model and its potential clinical application. If the validation is not properly conducted, the model may not generalize to independent patient populations.
- **Resolution test** Provide a detailed description of the validation cohort processing, including normalization steps, batch effect correction, and whether the housekeeping gene normalization was applied identically. Report performance metrics with confidence intervals and consider additional external validation datasets.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model can be used to predict "the adverse effects of immunotherapy in patients with TNBC."
- **Evidence pointer** Section 2.3, Figure 4
- **Concern** The claim that HTFSS predicts immunotherapy response is based on a single paclitaxel-based combination immunotherapy cohort. The manuscript does not specify the cohort size, treatment regimen, response criteria, or how "adverse effects" were defined and measured. The analysis appears to be correlational rather than predictive, and no independent validation of this finding is provided.
- **Why it matters** Predicting immunotherapy outcomes is a clinically significant claim that requires robust evidence. A single cohort with unclear methodology is insufficient to support this assertion, and overinterpretation could mislead clinical decision-making.
- **Resolution test** Provide full details of the immunotherapy cohort, including sample size, treatment protocol, response assessment criteria, and statistical methods. Validate the predictive value in an independent immunotherapy-treated cohort or clearly state the exploratory nature of this finding.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "TSA + DOX was able to effectively reduce DOX dosage" and "TSA + DOX + Calcitriol may be able to effectively reduce the toxic side effects of DOX on the heart."
- **Evidence pointer** Sections 2.7, 2.8, Figures 9, 10
- **Concern** The in vitro experiments use only one TNBC cell line (MDA-MB-231). The in vivo study uses 20 mice divided into 5 groups, which is a very small sample size per group (n=4). The statistical analysis section states that experiments were repeated at least three times, but this is not clearly reflected in the presented data. The claim about reducing cardiac toxicity is based on histological observation and body weight changes, but no functional cardiac assessments or molecular markers of cardiotoxicity are provided.
- **Why it matters** The therapeutic claims are central to the translational value of the study. Insufficient sample sizes, lack of cell line diversity, and absence of robust cardiotoxicity measures weaken the conclusions and limit the generalizability of the findings.
- **Resolution test** Include additional TNBC cell lines, increase animal group sizes, and provide quantitative assessments of cardiac function (e.g., echocardiography, cardiac enzyme levels) and statistical power calculations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The three TF genes (E2F8, FOXM1, MYBL2) affect tumor proliferation through PI3K-AKT, FOXO, Wnt, and mTOR signaling pathways.
- **Evidence pointer** Sections 2.4, 2.6, Figures 8, S3, S4
- **Concern** The pathway enrichment analyses are based on computational predictions from bulk and single-cell data. The experimental validation is limited to Western blotting for a few proteins in the PI3K-AKT pathway. The link between the three TFs and the specific pathways is largely inferred rather than directly demonstrated. No loss-of-function or gain-of-function experiments are performed to establish causality.
- **Why it matters** The mechanistic claims are a key part of the study's contribution. Without direct experimental evidence of TF regulation of these pathways, the proposed mechanism remains speculative.
- **Resolution test** Perform knockdown or overexpression experiments for the three TFs and assess pathway activity changes. Use pathway-specific inhibitors or reporters to confirm the involvement of the proposed signaling pathways.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The HTFSS is constructed after "cohort normalization based on housekeeping gene expression levels."
- **Evidence pointer** Section 4.3
- **Concern** The normalization method is described only briefly. It is unclear how the four housekeeping genes (ACTB, GAPDH, TFRC, TUBB) were selected, whether their expression stability was assessed across cohorts, and how the normalization was applied. The choice of housekeeping genes is critical because their expression can vary across tissues and conditions, and inappropriate normalization could introduce artifacts.
- **Why it matters** The validity of the entire model depends on the quality of the normalization. If the method is not rigorously described and justified, the model's performance and generalizability cannot be properly evaluated.
- **Resolution test** Provide a detailed description of the normalization procedure, including housekeeping gene selection criteria, stability assessment, and the exact formula used. Show that the normalization improves cross-cohort comparability compared to standard methods.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The study uses "molecular docking" to screen targeted drugs.
- **Evidence pointer** Section 2.5, Figure 7
- **Concern** The molecular docking methodology is not described in the Materials and Methods section. The docking software (AutoDock) is mentioned, but parameters, scoring functions, protein structure preparation, ligand preparation, and validation of docking results are not provided. The binding energy values are presented without statistical uncertainty or comparison to known binders.
- **Why it matters** Molecular docking results are highly dependent on the methodology used. Without a detailed protocol, the reliability of the drug screening results cannot be assessed, and the selection of DOX, TSA, and Calcitriol as candidates is not fully justified.
- **Resolution test** Provide a complete description of the docking protocol, including software versions, parameters, structure sources, and validation steps. Consider experimental validation of binding (e.g., surface plasmon resonance, isothermal titration calorimetry) to support the computational predictions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states the model has "broad applicability" but does not specify the clinical context or limitations. The phrase "adverse effects of immunotherapy" is ambiguous.
- **Required correction** Clarify the intended clinical use of the model and specify what "adverse effects" means in this context.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Section 4.1
- **Issue** The manuscript does not provide a data availability statement or information on how to access the code used for the analyses.
- **Required correction** Add a data availability statement and provide access to the code and processed data to enable reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 2.3, Figure 3
- **Issue** The box plots in Figure 3 appear to lack indication of statistical significance levels or effect sizes. The text mentions significant differences but does not report exact p-values or confidence intervals.
- **Required correction** Report exact p-values and effect sizes for all comparisons, and indicate significance levels in the figures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.4, Figure 5
- **Issue** The scRNA-seq analysis identifies 21 cell types, but the criteria for cell type annotation are not fully described. The marker gene list is in Table S2, which is not provided.
- **Required correction** Provide the marker gene list and describe the annotation process in more detail, including any manual curation steps.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Issue** Some sentences are overly long and contain redundant phrasing, which reduces readability.
- **Required correction** Revise for conciseness and clarity, particularly in the Discussion section.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Ethical compliance
- **Affected element** Section 4.9
- **Issue** The animal study section does not mention ethical approval or compliance with animal welfare guidelines.
- **Required correction** Add a statement on ethical approval for animal experiments.

## Risk / unsupported claims
- The claim that HTFSS predicts immunotherapy adverse effects is not supported by the evidence presented, as only one cohort with unclear methodology is used.
- The claim that the drug combination reduces cardiac toxicity is based on limited histological and body weight data without functional cardiac assessment.
- The mechanistic link between the three TFs and the proposed signaling pathways is inferred from computational analyses and limited Western blotting, not directly demonstrated.
- The molecular docking results are presented without sufficient methodological detail to assess their validity.
- The "broad applicability" of the model is overstated given the limited validation cohorts and lack of diverse patient populations.