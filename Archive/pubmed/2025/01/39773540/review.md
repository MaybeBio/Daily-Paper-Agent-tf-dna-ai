## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and internal consistency of the reported findings
- **Shared manuscript claim summary** The authors propose that PRRT1 is an epigenetically regulated gene in Alzheimer's disease, identify DNA methylation signatures associated with its reduced expression, predict the transcription factor MAZ as an upstream regulator via multi-omics integration and explainable machine learning, and provide experimental evidence in SH-SY5Y cells that MAZ regulates PRRT1 expression and that PRRT1 modulates viability, apoptosis, phosphorylated tau, and autophagy in an Aβ1-42 cellular model
- **Visible evidence base** Bioinformatics analyses of GEO datasets (GSE109627, GSE109887, GSE132903), ELMER motif analysis, luciferase reporter assays, ChIP-qPCR, western blotting, CCK8 assays, flow cytometry, and single-cell trajectory analysis from public datasets
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (Supplementary Figs. 1-11, Supplementary Tables 1-7) were not provided; detailed statistical outputs, model hyperparameters, and raw data are not available; no information on biological replicates for key experiments beyond stated n values

## Reviewer
- **Overall assessment** This manuscript presents a multi-omics bioinformatics pipeline combined with targeted experimental validation to implicate PRRT1 and its putative regulator MAZ in Alzheimer's disease pathogenesis. The computational framework is reasonable and the experimental data are internally consistent, but several concerns limit the strength of the conclusions. The causal link between the identified methylation sites and PRRT1 downregulation is inferred rather than directly demonstrated, the specificity of MAZ binding to the PRRT1 promoter is only partially established, and the mechanistic connection between PRRT1 and tau pathology remains correlative. The study is of interest to the AD epigenetics and biomarker community, but the evidence as presented does not fully establish the claimed regulatory mechanism.

- **Who would be interested in the results, and why** Researchers in Alzheimer's disease epigenetics, DNA methylation biomarkers, and transcriptional regulation in neurodegeneration would find this work relevant. The integration of explainable machine learning with multi-omics data may also interest computational biologists working on disease gene prioritization. Clinicians focused on blood or tissue-based diagnostic biomarkers for AD may find the proposed epigenetic signatures of potential translational value, though clinical utility is not demonstrated.

- **Major strengths** The study combines public multi-omics datasets with experimental validation, which is a strength relative to purely computational analyses. The use of explainable machine learning (SHAP) to interpret the diagnostic model adds transparency. The experimental confirmation of MAZ-PRRT1 interaction via luciferase and ChIP-qPCR is a positive feature. The functional experiments linking PRRT1 to viability, apoptosis, tau phosphorylation, and autophagy provide a plausible biological narrative.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The manuscript claims that DNA methylation at the identified sites regulates PRRT1 expression in AD, and that this epigenetic mechanism contributes to AD pathogenesis.
- **Evidence pointer** Results section "Identification of epigenetic signatures", ELMER analysis, Fig. 5, Supplementary Table 7
- **Concern** The study identifies four hypermethylated CpG sites associated with PRRT1 and infers a regulatory relationship based on negative correlation between methylation and expression. However, no direct experimental evidence is provided that methylation at these specific sites causes reduced PRRT1 expression. The ELMER analysis predicts regulatory potential but does not demonstrate causality. The experimental validation focuses on MAZ binding and PRRT1 function, not on the methylation sites themselves.
- **Why it matters** The central claim of the paper is that PRRT1 is under epigenetic regulation in AD. Without direct manipulation of methylation at the identified CpG sites (e.g., via CRISPR-dCas9-TET1 or DNMT targeting, or in vitro methylation assays), the causal role of these specific methylation changes remains unproven. The correlation-based inference is a common limitation in epigenome-wide association studies and weakens the mechanistic conclusion.
- **Resolution test** Provide experimental evidence that altering methylation at cg14270302, cg24138857, cg23145336, or cg20636526 directly changes PRRT1 expression. Alternatively, demonstrate in a relevant cell model that treatment with a demethylating agent (e.g., 5-aza-2'-deoxycytidine) restores PRRT1 expression in a manner dependent on these specific sites.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for MAZ-PRRT1 regulatory axis
- **Claim pointer** The manuscript claims that MAZ is a functional upstream transcription factor that promotes PRRT1 transcription, and that this regulation is relevant to AD.
- **Evidence pointer** Results section "ELMER analysis", "Luciferase reporter assay", "ChIP-qPCR", Figs. 6-7
- **Concern** The luciferase assay shows that MAZ overexpression increases reporter activity driven by the PRRT1 promoter, and ChIP-qPCR shows enrichment of MAZ at the PRRT1 promoter region. However, the manuscript does not report whether MAZ knockdown or knockout reduces endogenous PRRT1 expression. The ChIP-qPCR data show enrichment relative to IgG but no negative control region is described. The specificity of MAZ binding to the PRRT1 promoter among the four predicted sites is not systematically addressed. Additionally, the functional experiments with MAZ overexpression in Aβ-treated cells do not include a MAZ knockdown condition to confirm that the observed effects are specifically mediated through PRRT1.
- **Why it matters** The claim that MAZ regulates PRRT1 in AD requires evidence that endogenous MAZ is necessary for PRRT1 expression. Overexpression experiments alone cannot establish this. The rescue experiments (Fig. 10) partially address this by showing that si-PRRT1 reverses MAZ effects, but the absence of MAZ loss-of-function data leaves the regulatory direction and necessity unclear.
- **Resolution test** Perform MAZ knockdown in SH-SY5Y cells and measure PRRT1 expression. Include a ChIP-qPCR negative control region (e.g., a gene desert or a known non-bound region) to demonstrate binding specificity. If feasible, show that MAZ binding to the PRRT1 promoter is altered in AD-relevant conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Model validation and generalizability
- **Claim pointer** The manuscript claims that the random forest model built on 10 epigenetic signatures has good diagnostic performance and generalizability for AD.
- **Evidence pointer** Results section "Construction and evaluation of AD diagnostic model", Fig. 3, Supplementary Tables 2-5
- **Concern** The model achieves an AUC of 0.829 on the test set and 0.708 on the external validation set. While the external validation is commendable, the manuscript does not report confidence intervals for AUC values, calibration metrics, or a comparison against a baseline model using clinical variables alone. The external validation set GSE132903 is mentioned as having a larger sample size, but the manuscript does not describe the demographic or clinical characteristics of this cohort, nor whether it is comparable to the training cohort. The possibility of batch effects or platform differences between datasets is not discussed.
- **Why it matters** For a diagnostic model to be clinically useful, its performance must be robust across cohorts and its added value over existing predictors must be demonstrated. The current reporting does not allow assessment of whether the 10 epigenetic signatures provide incremental diagnostic value beyond age, sex, or APOE genotype, which are known AD risk factors.
- **Resolution test** Report AUC with 95% confidence intervals for both internal and external validation. Compare the model against a clinical-only model (age, sex, APOE). Describe the external cohort characteristics and any batch correction methods applied.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance of PRRT1 in AD
- **Claim pointer** The manuscript claims that PRRT1 mediates apoptosis and autophagy in AD, and that its downregulation contributes to AD pathogenesis.
- **Evidence pointer** Results section "Targeted regulation of PRRT1 effects viability in AD cells", "Overexpression of PRRT1 reduces apoptosis rate in AD cells", "Overexpression of PRRT1 reduces phosphorylated tau production and affects autophagy in AD cells", Figs. 8-10
- **Concern** The functional experiments are performed exclusively in SH-SY5Y neuroblastoma cells treated with Aβ1-42. This is a widely used but limited model of AD. The manuscript does not provide evidence from primary neurons, iPSC-derived neurons, or in vivo models. The connection between PRRT1 and phosphorylated tau is demonstrated only by western blotting in this cell line; no mechanistic explanation is provided for how PRRT1 influences tau phosphorylation. The autophagy findings are limited to LC3-I/LC3-II ratios without assessment of autophagic flux (e.g., using lysosomal inhibitors).
- **Why it matters** The translational relevance of the findings depends on whether the observed effects are specific to AD-relevant pathology and not artifacts of the cell line model. The lack of mechanistic depth for the tau and autophagy findings limits the strength of the conclusions about PRRT1's role in AD pathogenesis.
- **Resolution test** Validate key findings in at least one additional model system (e.g., primary cortical neurons, differentiated iPSC neurons, or an in vivo AD model). Assess autophagic flux using chloroquine or bafilomycin A1. Provide a mechanistic hypothesis for how PRRT1 affects tau phosphorylation, supported by additional experiments.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor and multiple testing
- **Claim pointer** The manuscript identifies differentially methylated positions and differentially expressed genes using threshold-based criteria.
- **Evidence pointer** Methods section "Identification and selection of differentially methylated positions", "Selection of differentially expressed genes", Supplementary Figs. 1-2
- **Concern** The criteria for differential methylation (|Δβ| > 0.02, P < 0.005) and differential expression (|logFC| > 0.2, adj.P.Val < 0.05) are relatively lenient. The manuscript does not report whether multiple testing correction was applied to the methylation analysis (the P < 0.005 threshold without adjustment is likely insufficient given the number of CpG sites tested on the 450K array). The WGCNA module selection is described but the choice of soft-thresholding power and module stability are not reported.
- **Why it matters** Lenient thresholds increase the risk of false positives, which could undermine the reliability of the identified epigenetic signatures. The reproducibility of the findings depends on robust statistical methods.
- **Resolution test** Apply Benjamini-Hochberg correction for multiple testing in the methylation analysis and report the number of significant CpGs after correction. Provide details on WGCNA parameter selection and module stability assessment.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reporting transparency
- **Affected element** Methods section, model training
- **Evidence pointer** Methods section "Machine learning algorithm for selection of epigenetic signatures", "Construction and evaluation of AD diagnostic models"
- **Issue** The manuscript does not specify the hyperparameter tuning procedure for the random forest model, the number of trees, or the feature importance calculation method. The LightGBM threshold of 0.9999 for cumulative importance is mentioned but the rationale is not explained.
- **Required correction** Provide full details of model hyperparameters, tuning strategy, and feature selection criteria. State the software versions and random seeds used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary materials
- **Evidence pointer** Electronic Supplementary Material section
- **Issue** All supplementary figures and tables are referenced but were not available for review. This prevents verification of key results including ROC curves for individual genes, immune infiltration analyses, and GO/KEGG enrichment results.
- **Required correction** Ensure all supplementary materials are accessible and clearly labeled. Consider depositing analysis code and processed data in a public repository.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality and labeling
- **Affected element** Figures 5-6, 11-12
- **Evidence pointer** Results section "ELMER analysis", "Single-cell transcriptome analysis"
- **Issue** The figures for methylation site locations and single-cell trajectory analyses are described but their content is not fully interpretable from the text alone. The manuscript does not specify which cell types are shown in Fig. 11C or how "high expression" was defined in the single-cell analyses.
- **Required correction** Clarify figure legends to include all relevant annotations, cell type labels, and statistical comparisons. Define thresholds for high/low expression in single-cell analyses.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language and clarity
- **Affected element** Discussion section
- **Evidence pointer** Discussion section "Epigenetic mechanism of PRRT1"
- **Issue** The discussion contains speculative statements about clinical applications and therapeutic implications that extend beyond the data presented. The phrase "offering innovative application value" is vague.
- **Required correction** Temper speculative claims and focus the discussion on what the data directly support. Remove or revise vague statements about innovation and clinical translation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction section, Discussion section
- **Issue** The introduction cites general reviews on AD epigenetics but does not position this work relative to prior studies on PRRT1 or MAZ in neurodegeneration. The discussion of MAZ in AD is limited.
- **Required correction** Add a brief review of what is known about PRRT1 and MAZ in neurological contexts, and explicitly state how this study advances beyond prior work.

- **Technical failings that need to be addressed before the case is established** The causal role of the identified methylation sites in PRRT1 downregulation is not experimentally demonstrated (R1-M1). The necessity of MAZ for endogenous PRRT1 expression is not shown (R1-M2). Statistical rigor in the differential methylation analysis is insufficiently documented (R1-M5). These issues must be resolved before the central claims of epigenetic regulation and MAZ-mediated control of PRRT1 can be considered established.

## Assessment against Nature-style criteria
- **Originality** Moderate. The combination of multi-omics analysis with explainable machine learning for epigenetic biomarker discovery is not entirely novel, but the specific focus on PRRT1 and the identification of MAZ as a putative regulator represents a new contribution to the AD epigenetics literature.
- **Scientific importance** Moderate. PRRT1 is a relatively understudied gene in AD, and the potential link between its epigenetic regulation and tau pathology is of interest. However, the clinical and mechanistic significance of the findings is not yet established, and the study does not provide a major conceptual advance in understanding AD pathogenesis.
- **Interdisciplinary readership** Limited. The work is primarily relevant to AD epigenetics researchers and computational biologists. The clinical implications are speculative, and the mechanistic depth is insufficient to attract a broad neuroscience audience.
- **Technical soundness** The computational pipeline is reasonable but the statistical thresholds are lenient and the model validation is incomplete. The experimental work is competent but limited in scope and model systems. The absence of direct methylation manipulation and MAZ loss-of-function experiments weakens the technical foundation.
- **Readability for nonspecialists** The manuscript is generally readable but contains jargon and methodological details that may be challenging for nonspecialists. The figures are referenced but not fully described in the text, which reduces accessibility.

## Risk / unsupported claims
- The claim that DNA methylation at the identified CpG sites "affects" PRRT1 expression is unsupported; only correlation is demonstrated.
- The claim that MAZ "promotes" PRRT1 transcription is only partially supported by overexpression data; no loss-of-function evidence is provided.
- The claim that PRRT1 downregulation "contributes to AD pathogenesis" is speculative and not directly tested in disease-relevant models.
- The statement that the interactive SHAP panel can be used to "identify high-risk patients for early intervention" is not supported by prospective or clinical validation data.
- The claim that the MAZ-PRRT1 mechanism is "previously unreported" and offers "innovative application value" is not substantiated by a comprehensive literature search presented in the manuscript.
- The hypothesis that PRRT1 improves AD conditions by affecting autophagy is speculative; autophagic flux was not measured.