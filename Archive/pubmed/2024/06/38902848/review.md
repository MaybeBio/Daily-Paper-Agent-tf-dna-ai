## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors employ integrated single-cell RNA sequencing (scRNA-seq) and single-cell ATAC sequencing (scATAC-seq) to profile transcriptomic and epigenomic states of approximately 125,000 latently infected CD4+ T cells (cell line and primary cells) after treatment with three latency-reversing agents. They identify cellular transcripts and transcription factor activities correlated with HIV reactivation, build machine learning models to predict viral reactivation, and functionally validate two candidates, FOXP1 and GATA3, as regulators of HIV latency.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Materials and methods, figure legends referenced in text, supplementary figure/table references, data and code availability statements
- **Missing materials affecting confidence** Actual figures and supplementary tables (Tables S1–S12, Figures S1–S22) were not provided; exact statistical values for several comparisons are not fully reported in text; details of machine learning hyperparameter tuning outcomes are only partially described

## Reviewer
- **Overall assessment** This manuscript presents a substantial and technically ambitious dataset that combines single-cell transcriptomic and chromatin accessibility profiling of HIV latency models. The integration of multiomic measurements with machine learning to predict viral reactivation is a novel and potentially valuable contribution. The identification of FOXP1 and GATA3 as candidate regulators, with some functional validation, strengthens the study. However, several technical and interpretive concerns need to be addressed, particularly regarding the strength of the functional validation, the interpretation of weak correlations, and the generalizability of the findings across the two primary cell donors. The manuscript is of interest to the HIV persistence and gene regulation communities, but the current evidence does not fully establish the central claims as presented.
- **Who would be interested in the results, and why** Researchers studying HIV latency and persistence, particularly those focused on transcriptional regulation of the provirus and latency reversal strategies. The multiomic approach and machine learning framework will also be of interest to computational biologists working on single-cell data integration. The identification of novel regulators such as FOXP1 and GATA3 may inform future therapeutic development for HIV cure strategies.
- **Major strengths** 1) The use of integrated scRNA-seq and scATAC-seq on the same cells is a powerful and relatively rare approach in the HIV field, allowing direct correlation between transcriptomic and epigenomic states. 2) The scale of the dataset (approximately 125,000 cells) is substantial and provides statistical power for correlation analyses. 3) The inclusion of three mechanistically distinct LRAs enables comparative analysis of reactivation pathways. 4) The machine learning approach to predict viral reactivation from multiomic features is innovative and demonstrates the potential of multivariate models. 5) Functional validation of two candidates (FOXP1 and GATA3) using knockdown and knockout approaches adds biological relevance beyond correlative findings.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (functional validation strength), R1-M2 (donor variability and generalizability), R1-M3 (correlation strength and causal inference), R1-M4 (machine learning model evaluation)
- **Assessment against Nature-style criteria** **Originality:** The integrated multiomic approach applied to HIV latency at single-cell resolution is original and extends prior bulk and single-modality studies. The identification of novel candidate regulators adds originality. **Scientific importance:** The question of why latency reversal is inefficient is of high importance for HIV cure research. The findings have potential translational relevance. **Interdisciplinary readership:** The work bridges virology, immunology, and computational biology, and would appeal to a broad readership in these areas. **Technical soundness:** The experimental design and data generation appear sound, but several analytical and validation aspects require clarification and strengthening (see Major Concerns). **Readability for nonspecialists:** The manuscript is generally well-written and accessible, though some sections on machine learning and bioinformatics may be challenging for non-specialists. The abstract and introduction are clear.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the strength of functional validation and the interpretation of correlative data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The manuscript claims that FOXP1 and GATA3 are "regulators of HIV latency and reactivation" based on knockdown and knockout experiments.
- **Evidence pointer** Results section, Figure 8, Figure S22
- **Concern** The functional validation data for FOXP1 and GATA3 appear limited in scope and depth. For GATA3, the knockdown in 2D10 cells shows only a modest reduction in the response to prostratin (30.8% vs 36.9% GFP+), which, while statistically significant, represents a relatively small effect. The biological significance of this magnitude of change is unclear. For FOXP1, the knockdown data in 2D10 cells show reactivation of vRNA expression, but the effect size and reproducibility across biological replicates are not fully described. The knockout experiments in primary CD4+ T cells are mentioned but the data are not shown in detail. The manuscript does not report on potential off-target effects of the sgRNAs or shRNAs, nor does it provide rescue experiments to confirm specificity. Additionally, the manuscript does not address whether the effects of FOXP1 and GATA3 are direct or indirect, which is acknowledged in the Discussion but not experimentally addressed.
- **Why it matters** The central claim of the manuscript rests on the identification of novel regulators. If the functional validation is not robust, the claim that these factors are bona fide regulators is weakened. The modest effect sizes and lack of mechanistic depth limit the confidence in the biological relevance of these findings.
- **Resolution test** Provide more comprehensive functional validation, including: (1) dose-response experiments with different LRA concentrations; (2) time-course experiments to assess the kinetics of the effect; (3) rescue experiments with shRNA-resistant or sgRNA-resistant cDNA constructs; (4) assessment of off-target effects, for example by using multiple independent sgRNAs or shRNAs and confirming with RNA-seq; (5) more detailed presentation of the primary cell knockout data, including the efficiency of knockout and the magnitude of the effect on viral reactivation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and generalizability
- **Claim pointer** The manuscript claims that the findings are consistent across two primary cell donors, but the data show notable differences in the magnitude of response to LRAs between donors.
- **Evidence pointer** Results section, Figure 1C, Figure 2A, Figure S2C, Figure S5A
- **Concern** The manuscript reports that prostratin was less potent at up-regulating vRNAs in donor 2 than in donor 1. This donor-to-donor variability is acknowledged but not thoroughly explored. The correlation analyses between vRNA levels and cellular features are performed on aggregated data from both donors, which may obscure donor-specific effects. The manuscript does not report whether the identified candidate regulators are consistently correlated with vRNA levels in each donor individually, or whether the correlations are driven primarily by one donor. This is important because the primary cell model is intended to represent the physiological state of latent infection, and variability between donors could indicate that the findings are not generalizable.
- **Why it matters** If the identified regulators are not consistently associated with viral reactivation across donors, the generalizability of the findings is questionable. The manuscript's claim of identifying "novel regulators" implies a degree of universality that may not be supported by the data.
- **Resolution test** Perform and report the correlation analyses separately for each donor. Provide a statistical comparison of the correlation coefficients between donors. Discuss the potential sources of donor variability and whether the identified regulators are consistently implicated across donors. If the findings are donor-specific, temper the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and causal inference
- **Claim pointer** The manuscript claims that "cellular transcripts and TFs whose expression/activity was correlated with viral reactivation" were identified, and that these correlations are biologically meaningful.
- **Evidence pointer** Results section, Figure 5, Tables 1–2, Tables S5–S9
- **Concern** The manuscript reports that individual correlations between vRNA levels and cellular features are weak, with the most highly correlated transcript in 2D10 cells having an R2 value that is not explicitly stated but implied to be low. The manuscript acknowledges this in the Discussion, attributing it to stochastic processes and background noise. However, the biological significance of such weak correlations is unclear. The manuscript does not report the effect sizes or confidence intervals for the correlations in a systematic way. The use of a 0.05 FDR threshold for identifying correlated transcripts and TFs may be too lenient given the large number of features tested, potentially leading to a high number of false positives. The manuscript does not report the number of expected false positives under the chosen threshold.
- **Why it matters** The identification of candidate regulators is based on these correlations. If the correlations are weak and potentially subject to a high false discovery rate, the list of candidates may not be reliable. The manuscript's claim that the approach "successfully identifies known regulators" is reassuring, but the presence of known regulators does not guarantee that the novel candidates are also genuine.
- **Resolution test** Provide a more detailed statistical analysis, including: (1) reporting the distribution of correlation coefficients and effect sizes; (2) reporting the expected number of false positives under the chosen FDR threshold; (3) performing a permutation-based analysis to assess the significance of the observed correlations; (4) validating the candidate list using an independent method, such as a different correlation metric or a different statistical test; (5) considering a more stringent significance threshold.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Machine learning model evaluation
- **Claim pointer** The manuscript claims that a machine learning model trained on the multiomic data was 75%–79% accurate at predicting viral reactivation.
- **Evidence pointer** Results section, Figure 7, Figure S21
- **Concern** The evaluation of the machine learning model is incomplete. The manuscript reports accuracy (or AUC) but does not provide a full set of performance metrics, such as precision, recall, F1 score, or a confusion matrix. The manuscript does not describe the cross-validation strategy in sufficient detail, nor does it report the variance of the performance estimates across folds. The manuscript does not compare the performance of the model to a baseline model (e.g., a model trained on a reduced feature set or a model using only the most highly correlated single feature). The manuscript does not report on the potential for data leakage between training and test sets, particularly given the use of aggregated data from multiple conditions. The manuscript does not provide an analysis of which features are most important for the model's predictions, beyond a brief mention of the top features.
- **Why it matters** The machine learning model is presented as a key demonstration of the value of the multiomic approach. If the model's performance is not rigorously evaluated, the claim that it can predict viral reactivation is not well supported. A thorough evaluation is necessary to establish the model's utility and to provide insights into the biological features that drive its predictions.
- **Resolution test** Provide a more comprehensive evaluation of the machine learning model, including: (1) a full set of performance metrics (precision, recall, F1, confusion matrix); (2) a detailed description of the cross-validation strategy, including the number of folds and the variance of performance estimates; (3) a comparison to baseline models; (4) an analysis of feature importance, for example using SHAP values or permutation importance; (5) a discussion of potential data leakage and how it was avoided.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of reporting
- **Affected element** Figure 1C
- **Evidence pointer** Results section, Figure 1C
- **Issue** The manuscript states that "vorinostat and prostratin both significantly increased the fraction of GFP+ primary CD4+ T cells for both donors by 10%–15%." The exact p-values for these comparisons are not reported in the text.
- **Required correction** Report the exact p-values for the comparisons between LRA-treated and DMSO-treated conditions for each donor.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Tables 1 and 2
- **Evidence pointer** Results section, Tables 1 and 2
- **Issue** The tables list the top 20 significantly linked genes and TFs, but the full lists are only provided in supplementary tables. The criteria for inclusion in the top 20 are not explicitly stated.
- **Required correction** State the criteria used to select the top 20 genes and TFs for display in the main tables.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology clarity
- **Affected element** Machine learning feature selection
- **Evidence pointer** Materials and methods, Machine learning model of HIV reactivation
- **Issue** The description of the feature selection process for the machine learning model is somewhat vague. The manuscript states that "features with top k ranking Spearman correlation coefficients were then selected for modeling" but does not specify how k was determined for the primary cell data.
- **Required correction** Provide a more detailed description of the feature selection process, including how the value of k was chosen for each dataset.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The Discussion mentions that "additional functional experiments will be needed to confirm whether these novel factors contribute directly or indirectly to HIV gene expression." This is appropriate, but the manuscript could be strengthened by a more explicit discussion of the limitations of the correlative approach.
- **Required correction** Expand the Discussion to more thoroughly address the limitations of correlative analyses and the potential for false discoveries, and to outline specific experimental strategies to address these limitations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code availability
- **Evidence pointer** Code availability section
- **Issue** The code availability statement provides a GitHub repository, but it is not clear if the code is versioned or if it includes all necessary scripts and dependencies for full reproducibility.
- **Required correction** Provide a more detailed description of the code repository, including version information, dependencies, and instructions for use.

## Risk / unsupported claims
- The claim that FOXP1 and GATA3 are "regulators of HIV latency and reactivation" is only partially supported by the functional data presented. The effects are modest and the mechanistic basis is not established.
- The claim that the machine learning model is 75%–79% accurate is not fully supported by the evaluation presented, as key performance metrics and methodological details are missing.
- The claim that the identified correlations represent "novel regulators" is based on correlative data with weak effect sizes and may be subject to a high false discovery rate.
- The generalizability of the findings across primary cell donors is not fully established, given the observed donor-to-donor variability.
- The manuscript's statement that "these data demonstrate the power of integrated multimodal single-cell analysis to uncover novel relationships" is somewhat overstated given the limitations described above.