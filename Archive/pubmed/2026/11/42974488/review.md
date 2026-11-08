## Review setup
- **Input scope** Full manuscript text including introduction, methods, results, discussion, figure legends, and supplementary declarations
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors propose that ELF3 acts as a transcriptional repressor of CLDN1 in psoriasis, linking inflammatory signaling to epidermal barrier dysfunction. They integrate WGCNA, scRNA-seq, machine learning, genetic colocalization, virtual knockout simulations, and in vitro reporter assays to support this axis.
- **Visible evidence base** Figures 1-8 with legends, methods descriptions, statistical annotations in figure legends, and discussion of limitations
- **Missing materials affecting confidence** Raw data files, complete statistical outputs, exact sample sizes for all experiments, primer validation data, cell line authentication statements, and detailed bioinformatics parameter settings

## Reviewer

### Overall assessment
The manuscript presents a multi-omics integration strategy to identify transcriptional regulators of CLDN1 in psoriasis, culminating in the proposal of an ELF3-CLDN1 regulatory axis. The computational framework is ambitious and the in vitro validation is a positive step. However, several methodological concerns undermine the strength of the conclusions. The machine learning approach using survival analysis algorithms in a cross-sectional binary classification context is unconventional and requires stronger justification. The genetic colocalization analysis is presented without sufficient methodological detail to assess its validity. The in vitro experiments are limited to a single cell line and a single reporter construct, and the absence of protein-level data or chromatin binding assays weakens the claim of direct transcriptional repression. The manuscript would benefit from clearer presentation of effect sizes, confidence intervals, and the biological relevance of observed fold changes.

### Who would be interested in the results, and why
Dermatology researchers studying psoriasis pathogenesis, particularly those focused on epidermal barrier function and tight junction biology. Investigators working on transcriptional regulation of skin barrier genes and the intersection of inflammation and differentiation programs would find the ELF3-CLDN1 axis of interest. Computational biologists developing multi-omics integration pipelines for skin disease may also find the methodological framework useful, though they would need to carefully evaluate the machine learning approach.

### Major strengths
1. The multi-omics integration strategy is comprehensive, combining bulk transcriptomics, single-cell data, and multiple regulatory databases.
2. The identification of CLDN1 as a consistently downregulated barrier gene across independent cohorts and single-cell trajectories is well supported.
3. The dual-luciferase reporter assay provides direct evidence of ELF3-mediated repression of the CLDN1 promoter, with a mutation control demonstrating sequence specificity.
4. The TNF-α stimulation experiment connects inflammatory signaling to the proposed axis in a keratinocyte model.
5. The authors acknowledge key limitations, including the need for chromatin binding confirmation and functional permeability assays.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of machine learning methodology
- **Claim pointer** The StepCox and CoxBoost combination is claimed to be an optimal machine learning approach for feature prioritization in a binary classification setting.
- **Evidence concern** The methods state that StepCox and CoxBoost, originally designed for survival analysis with time-to-event outcomes, were repurposed for binary classification by parameterizing class labels with "uniform synthetic coordinate weights." This is a nonstandard application that requires substantial justification. The manuscript does not explain how binary outcomes were converted to survival-type data, what censoring indicators were used, or why standard binary classification algorithms (e.g., random forest, XGBoost, logistic regression with regularization) were not sufficient. The claim of "optimal" performance is based on AUC values that appear implausibly high (1.000 in training, 0.991 in validation), which may indicate overfitting or data leakage.
- **Why it matters** The core diagnostic signature identification depends entirely on this machine learning pipeline. If the methodology is not statistically sound, the prioritization of CLDN1 as a "robust diagnostic feature" is called into question, which would undermine the foundation for all downstream analyses.
- **Resolution test** Provide a detailed explanation of how binary labels were transformed for survival analysis, including the exact parameterization of synthetic weights and censoring. Justify the choice of survival algorithms over standard classifiers with benchmark comparisons. Report cross-validated performance with confidence intervals and demonstrate that the results are not driven by overfitting. Alternatively, rerun the analysis with conventional binary classification algorithms and show that CLDN1 remains a top-ranked feature.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for direct transcriptional regulation
- **Claim pointer** The manuscript claims that ELF3 functions as a "candidate transcriptional repressor" of CLDN1 based on dual-luciferase reporter assays and computational prediction.
- **Evidence concern** The dual-luciferase assay demonstrates that ELF3 overexpression suppresses CLDN1 promoter activity in HEK293T cells. However, HEK293T is a kidney epithelial cell line, not a keratinocyte. The relevance of this finding to keratinocyte biology is unclear. Additionally, the manuscript does not report whether endogenous ELF3 levels in HaCaT cells are sufficient to repress CLDN1, nor does it show chromatin immunoprecipitation (ChIP) or electrophoretic mobility shift assay (EMSA) data to confirm direct binding of ELF3 to the CLDN1 promoter. The claim of "sequence-dependent" repression is supported by the mutation experiment, but this only demonstrates that the predicted motif is necessary for repression in the reporter context, not that ELF3 directly binds this motif in vivo.
- **Why it matters** The central mechanistic claim of the paper is that ELF3 directly represses CLDN1 transcription. Without evidence of direct binding in a relevant cell type, the proposed regulatory axis remains speculative. The title and abstract present this as a key finding, so the evidence must be commensurate with the claim.
- **Resolution test** Perform ChIP-qPCR in HaCaT keratinocytes to demonstrate ELF3 occupancy at the CLDN1 promoter. Alternatively, conduct EMSA with recombinant ELF3 protein and the CLDN1 promoter fragment. If direct binding cannot be demonstrated, revise the claims to state that ELF3 overexpression represses CLDN1 promoter activity in a reporter context, without asserting direct transcriptional regulation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Genetic colocalization methodology
- **Claim pointer** The manuscript states that regional association mapping via LocusZoom illustrated overlapping signals between psoriasis GWAS loci and skin-specific eQTLs at the CLDN1 region, suggesting a genetic basis for CLDN1 downregulation.
- **Evidence concern** The methods section does not describe the colocalization analysis in sufficient detail. LocusZoom plots are visualization tools, not formal colocalization tests. The manuscript does not report whether a statistical colocalization method (e.g., coloc, eCAVIAR, SMR) was used, what priors were assumed, or what posterior probabilities were obtained. The figure legend for Figure 6 shows five panels for different genes, but the text only discusses CLDN1. The claim of "overlapping signals" is qualitative and does not establish genetic colocalization in the statistical sense.
- **Why it matters** The authors use this analysis to argue that CLDN1 downregulation is a primary genetic event rather than a secondary response to inflammation. This is an important distinction for the proposed model. Without proper statistical colocalization, the claim is unsupported.
- **Resolution test** Perform formal colocalization analysis using a recognized method (e.g., coloc with appropriate priors) and report posterior probabilities for the CLDN1 locus. If formal colocalization is not significant, temper the claim to state that regional association signals are in proximity without asserting genetic colocalization.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance of the proposed axis
- **Claim pointer** The manuscript suggests that the ELF3-CLDN1 axis represents a mechanism linking inflammatory stimuli to barrier breakdown and that targeting ELF3 could restore barrier integrity.
- **Evidence concern** The functional evidence is limited to mRNA expression changes in a single immortalized keratinocyte cell line (HaCaT) treated with TNF-α. No protein-level data are presented. The manuscript does not include measurements of barrier function (e.g., transepithelial electrical resistance, paracellular flux) or junctional localization of CLDN1 by immunofluorescence. The virtual knockout simulation is purely computational and does not substitute for functional validation. The claim that targeting ELF3 could be a therapeutic approach is speculative without evidence that ELF3 modulation affects barrier function in a physiologically relevant model.
- **Why it matters** The translational relevance of the findings depends on demonstrating that the ELF3-CLDN1 axis has functional consequences for epidermal barrier integrity. Without functional assays, the clinical implications remain hypothetical.
- **Resolution test** Include barrier function measurements in keratinocyte models with ELF3 knockdown or overexpression. Alternatively, use a 3D skin equivalent model to assess the impact of ELF3 modulation on epidermal permeability. If functional data are not available, clearly state that the functional consequences are inferred from expression correlations and require further validation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility of computational analyses
- **Affected element** Methods section, data availability
- **Evidence concern** The manuscript does not provide the full code or parameter settings for the WGCNA, machine learning, and virtual knockout analyses. The R version is specified, but package versions for Seurat, Monocle3, and other tools are not fully listed. The scTenifoldKnk analysis parameters are not described.
- **Required correction** Provide a detailed supplementary methods file with all analysis parameters, or deposit the analysis code in a public repository (e.g., GitHub, Zenodo) with a DOI. List all package versions used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figures 1-8, results text
- **Evidence concern** The manuscript reports p-values but does not consistently report effect sizes or confidence intervals. For the correlation analyses in Figure 8C, the R values are shown but confidence intervals are not provided. The box plots in Figure 4A show significance stars but the statistical test used is not specified in the figure legend.
- **Required correction** Specify the statistical tests used for each comparison in the figure legends. Report effect sizes and confidence intervals where appropriate. For correlation analyses, provide 95% confidence intervals for the correlation coefficients.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Cell line authentication
- **Affected element** Methods, cell culture section
- **Evidence concern** The manuscript does not state whether the HaCaT and HEK293T cell lines were authenticated (e.g., by STR profiling) or tested for mycoplasma contamination. This is standard practice for cell-based experiments.
- **Required correction** Add a statement regarding cell line authentication and mycoplasma testing in the methods section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Figure 6
- **Evidence concern** The figure legend for Figure 6 states that five panels (A-E) are shown for different genes, but the text only discusses CLDN1. The relevance of the other four genes is unclear.
- **Required correction** Either explain the significance of all five genes shown in Figure 6 or reduce the figure to focus on CLDN1. Ensure the figure legend clearly describes what each panel represents.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Title, abstract, discussion
- **Evidence concern** The title uses the term "Integrative Analysis of Epidermal Barrier Dysfunction Regulators" which implies a broader scope than what is presented. The manuscript focuses specifically on CLDN1 and ELF3. The term "regulators" is plural, suggesting multiple regulators are characterized, but only ELF3 is experimentally tested.
- **Required correction** Consider revising the title to more accurately reflect the scope, such as "Integrative Analysis Identifies ELF3 as a Candidate Regulator of CLDN1 in Psoriasis-Associated Epidermal Barrier Dysfunction."

### Technical failings that need to be addressed before the case is established
1. The machine learning methodology using survival analysis algorithms for binary classification requires substantial justification and validation (R1-M1).
2. Direct evidence of ELF3 binding to the CLDN1 promoter in keratinocytes is lacking (R1-M2).
3. Formal statistical colocalization analysis is not performed (R1-M3).
4. Functional barrier assays are absent (R1-M4).

### Assessment against Nature-style criteria
- **Originality** Moderate. The integration of multiple computational methods to identify transcriptional regulators of CLDN1 is not entirely novel, but the specific focus on ELF3 as a repressor of CLDN1 in psoriasis is a new contribution. The virtual knockout approach adds a computational dimension that is relatively uncommon in dermatology research.
- **Scientific importance** Moderate. The ELF3-CLDN1 axis could be relevant to psoriasis pathogenesis, but the evidence presented is preliminary. The clinical significance of this axis relative to established inflammatory pathways in psoriasis is not demonstrated.
- **Interdisciplinary readership** Limited. The manuscript is primarily of interest to dermatology researchers and computational biologists working on skin disease. The findings are unlikely to attract broad interdisciplinary attention beyond these fields.
- **Technical soundness** The computational framework is ambitious but the machine learning methodology is questionable. The in vitro experiments are technically sound but limited in scope. The lack of protein-level data and functional assays weakens the overall technical rigor.
- **Readability for nonspecialists** The manuscript is generally well-written and the figures are informative. However, the methods section assumes substantial familiarity with bioinformatics tools and the machine learning approach is not explained in a way that would be accessible to a general scientific audience.

### Recommendation posture
Currently not established from the provided evidence. The manuscript presents an interesting hypothesis and a multi-omics framework, but the methodological concerns regarding the machine learning approach and the lack of direct evidence for ELF3-mediated transcriptional repression in keratinocytes prevent the conclusions from being fully supported. The authors should address the major concerns, particularly the machine learning justification and the need for chromatin binding or functional data, before the case for an ELF3-CLDN1 regulatory axis in psoriasis can be considered established.

## Risk / unsupported claims
1. The claim that StepCox and CoxBoost constitute an "optimal" machine learning approach for this binary classification problem is unsupported without benchmark comparisons against standard classifiers.
2. The claim of "overlapping signals" between GWAS and eQTL at the CLDN1 locus implying genetic colocalization is unsupported without formal statistical testing.
3. The assertion that ELF3 is a "transcriptional repressor" of CLDN1 is not fully supported, as the evidence shows repression of a reporter construct in HEK293T cells but does not demonstrate direct binding or repression in a keratinocyte context.
4. The statement that targeting ELF3 could "restore epidermal integrity" is speculative and not supported by functional data.
5. The claim that CLDN1 downregulation is a "primary genetic risk factor" rather than a secondary response to inflammation is not established by the colocalization analysis presented.