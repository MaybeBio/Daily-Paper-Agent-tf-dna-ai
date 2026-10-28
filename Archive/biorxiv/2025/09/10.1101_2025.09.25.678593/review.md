## Review setup
- **Input scope** Full manuscript text (abstract, introduction, modeling, methods, results, discussion, code availability, acknowledgments)
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality as presented in the supplied material
- **Shared manuscript claim summary** The authors propose a two-state mechanistic model to distinguish biologically relevant from spurious transcription factor binding sites in ChIP-seq data, based on the positional distribution of called peaks relative to the TSS. They claim the model reduces subjectivity in choosing interaction distance thresholds, is validated by RNA Polymerase II co-localization and mRNA expression correlations, and predicts that over 70% of reported BCL3 differential binding events in dexamethasone-treated A549 cells are spurious.
- **Visible evidence base** Abstract, Introduction, Modeling section (Section 2), Data and Methods (Section 3), Results (Section 4), Discussion (Section 5), Code Availability, Acknowledgments. Figures referenced include Fig. 1, 2, 3, 4, 5 and supplementary figures S1-S11. Tables 1-3 are referenced but not shown.
- **Missing materials affecting confidence** Figures and tables are referenced but not provided. Supplementary figures S1-S11 are not available. Table 1 (TF list), Table 2 and Table 3 (interaction comparisons) are not shown. Statistical details of model fitting, goodness-of-fit measures, and confidence intervals for parameter estimates are not provided. Details of the dexamethasone perturbation experiment (e.g., replicates, time points) are not fully described.

## Reviewer
- **Overall assessment** The manuscript addresses a genuine and important problem in genomics: distinguishing functional from spurious TF binding events in ChIP-seq data. The conceptual framing, distinguishing a rapid exponential accumulation of binding sites near the TSS from a uniform background, is elegant and biologically plausible. The authors demonstrate sensitivity of inferred networks to parameter choices, which is a valuable cautionary result. However, the manuscript as presented has several significant gaps. The model derivation is incomplete, with key equations referenced but not shown. The validation claims, while directionally supportive, rely on correlational evidence and lack rigorous statistical benchmarking against existing methods. The central claim that 70% of BCL3 differential binding events are spurious is striking but the supporting analysis is not fully described. The absence of figures and tables makes it impossible to assess the quality of the fits or the robustness of the conclusions. The manuscript has potential but is not yet established from the provided evidence.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on ChIP-seq analysis, TF binding site prediction, and gene regulatory network inference would be the primary audience. Researchers studying transcriptional regulation, particularly those using perturbation experiments to link TF binding to gene expression changes, would also find the framework relevant. The work could inform best practices for setting analysis parameters in standard pipelines, which has broad utility across genomics laboratories.
- **Major strengths** 1. The conceptual model is simple, mechanistically motivated, and potentially generalizable across TFs and cell types. 2. The sensitivity analysis highlighting the impact of arbitrary parameter choices on inferred networks is a valuable contribution to reproducibility discussions. 3. The validation strategy using independent data modalities (RNA Pol II occupancy, mRNA expression correlations) is appropriate in principle. 4. The application to a real perturbation experiment (dexamethasone/BCL3) demonstrates practical utility.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
  - R1-M5
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
- **Technical failings that need to be addressed before the case is established** R1-M1 (model derivation incomplete), R1-M2 (validation lacks comparison to existing methods), R1-M3 (BCL3 claim not fully supported), R1-M4 (parameter estimation and uncertainty not reported)
- **Assessment against Nature-style criteria** Originality: The two-state model framing is a novel conceptual contribution, though related ideas exist in the literature on background binding models. Scientific importance: The problem of spurious binding is widely recognized and the proposed framework could have practical impact on analysis standards. Interdisciplinary readership: The work bridges genomics, statistical modeling, and molecular biology, which could appeal to a broad readership if clearly presented. Technical soundness: The modeling framework is plausible but the incomplete presentation of equations and fitting procedures prevents full assessment. Readability for nonspecialists: The manuscript is generally well-written and the conceptual argument is accessible, but the missing equations and figures hinder comprehension of the technical core.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the validation strategy is appropriate, but the manuscript requires substantial revision to fully establish the claims, particularly the model derivation, statistical rigor, and the headline BCL3 result.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that a two-state mechanistic model captures the positional distribution of both biologically relevant and spurious binding events, and that this model yields a statistically sound way to decide whether a called peak is biologically relevant or spurious.
- **Evidence pointer** Section 2.2, equations 1-3 referenced but not shown; Figure 2 referenced but not provided
- **Concern** The model derivation is presented in a fragmented manner. Equations 1, 2, and 3 are referenced in the text but not displayed. The assumptions underlying the two-state model, particularly the claim that the background distribution is uniform and the biologically relevant distribution is exponential, are stated but not justified mathematically or empirically. The parameter estimation procedure is not described. It is unclear how the model is fit to data, what constraints are imposed, and how goodness-of-fit is assessed. Without these details, the central methodological contribution cannot be evaluated.
- **Why it matters** The entire manuscript rests on the validity of the two-state model. If the model derivation is incomplete or the assumptions are not justified, the classification of peaks as biologically relevant or spurious is not reliable. Readers cannot assess whether the model is overfitting, whether the exponential decay assumption is appropriate for all TFs, or whether the uniform background assumption holds in practice.
- **Resolution test** Provide the full derivation of the model, including all equations. Describe the fitting procedure in detail, including optimization criteria, constraints, and initialization. Report goodness-of-fit statistics for each TF-cell line pair. Justify the exponential and uniform assumptions with reference to empirical distributions or prior literature. Show representative fits in the main text or supplementary material.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that biologically relevant binding events identified by their model are capable of recruiting RNA Polymerase II and regulating mRNA expression levels of target genes, and that these validations confirm the ability of the model to accurately identify transcriptionally relevant peaks.
- **Evidence pointer** Section 4.3, Figure 3; Section 4.4, Figure 4
- **Concern** The validation analyses compare RNA Pol II occupancy and mRNA expression correlations between peaks classified as biologically relevant versus spurious. However, no comparison is made to existing methods for filtering ChIP-seq peaks, such as peak intensity thresholds, motif presence, evolutionary conservation, or other published approaches. The observed differences, while statistically significant, may not be superior to simpler heuristics. The choice of correlation threshold (absolute value greater than 0.5, p less than 0.05) is arbitrary and not justified. The analysis in Section 4.4 is limited to K562 cells, the only cell line with more than 30 samples, which raises questions about generalizability.
- **Why it matters** The claim that the model identifies biologically relevant peaks requires demonstrating that it outperforms or at least matches existing approaches. Without a benchmark comparison, the added value of the model over simpler methods is unclear. The arbitrary correlation threshold weakens the strength of the validation claim.
- **Resolution test** Include a comparison of the model's classification against at least one or two standard approaches (e.g., peak intensity threshold, motif-based filtering) using the same validation metrics. Justify the correlation threshold or perform a sensitivity analysis. If possible, extend the RNA expression correlation analysis to additional cell lines with sufficient sample sizes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for central claim
- **Claim pointer** The authors claim that in A549 cells treated with 100nM dexamethasone, close to 70% of differential binding events for BCL3 fail to elicit a change in mRNA expression, and these interactions are accurately captured as spurious binding events by the model. They also claim the model identifies genes that display a shift from spurious to biologically relevant binding accounting for close to 17% of genes with sharp changes in mRNA expression.
- **Evidence pointer** Section 4.5, Figure 5, Supplementary Figure 10
- **Concern** The analysis of the dexamethasone perturbation experiment is described at a high level but critical details are missing. The number of replicates, the statistical method for calling differential binding, the criteria for defining "sharp change in mRNA expression," and the specific comparison groups are not fully specified. The claim that 70% of reported interactions are spurious is striking and would benefit from a clear description of how this percentage is computed and what the uncertainty around this estimate is. The 17% figure for genes shifting from spurious to biologically relevant binding is presented without confidence intervals or statistical testing.
- **Why it matters** These quantitative claims are the most impactful results of the manuscript. If the underlying analysis is not fully described, readers cannot assess the reliability of these percentages or reproduce the analysis. The claims could be overinterpreted if the analysis has hidden assumptions or if the uncertainty is large.
- **Resolution test** Provide a detailed description of the differential binding analysis, including the statistical test, multiple testing correction, and the exact definition of "expected" and "predicted" gene classes. Report the number of genes in each category and the uncertainty around the 70% and 17% estimates. Consider adding a permutation or bootstrap analysis to assess the stability of these percentages.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the model identifies interaction distance thresholds that minimize spurious binding, and that the parameter tau (decay constant) is relatively invariant across TFs and cell lines, while r_b and r_s vary by up to 10-fold across TFs.
- **Evidence pointer** Section 4.2, Figures 2, S6-S8
- **Concern** The parameter estimates are presented as point values without confidence intervals or measures of uncertainty. The claim that tau varies by less than 2-fold across TFs is made without statistical testing. The relationship between the model parameters and biological variables (e.g., chromatin accessibility, TF expression) is discussed qualitatively but not tested quantitatively. The robustness analysis with respect to the p-value threshold (Figure S9) is mentioned but not described in detail.
- **Why it matters** The model parameters are the basis for the classification of peaks. Without uncertainty estimates, it is unclear how reliable the parameter estimates are and whether the observed differences across TFs and cell lines are statistically meaningful. The claim of tau invariance is important for the generalizability of the model but is not rigorously supported.
- **Resolution test** Report confidence intervals or bootstrap estimates for all model parameters. Perform statistical tests for differences in parameters across TFs and cell lines. Describe the p-value robustness analysis in more detail, including the range of p-values tested and the effect on parameter estimates and classifications.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors claim that the approach increases reproducibility of analysis by providing a systematic, TF-specific method to identify biologically relevant binding events.
- **Evidence pointer** Section 5, Discussion; Section 6, Code Availability
- **Concern** While code availability is stated, the manuscript does not describe the computational environment, dependencies, or input data formats required to run the analysis. The specific versions of tools (e.g., MACS2, bedtools, deepTools) are not mentioned. The analysis pipeline is not described as a reproducible workflow (e.g., no container, workflow language, or step-by-step protocol). The GitHub repository is mentioned but its contents are not described.
- **Why it matters** A central claim of the manuscript is improved reproducibility. If the code and analysis pipeline are not fully documented, other researchers cannot easily apply the method to their own data or verify the results. This undermines the practical impact of the work.
- **Resolution test** Provide a detailed description of the computational environment, including software versions. Describe the analysis pipeline as a step-by-step protocol or provide a workflow file. Document the input data formats and any preprocessing steps. Consider adding a tutorial or example dataset to the repository.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, equation formatting
- **Evidence pointer** Section 2.2, location not provided
- **Issue** The text references equations 1, 2, and 3 but the equations are not displayed. Some symbols appear to be missing from the text, such as the set of binding sequences in the sentence "If there is no selection pressure for the presence or absence of any of the ."
- **Required correction** Display all equations in full. Correct the sentence with the missing symbol, likely referring to the set of k binding sequences.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.2, notation
- **Evidence pointer** Section 4.2, location not provided
- **Issue** The notation "N ( > x )?" appears twice with a question mark, which seems to be a typographical error or placeholder.
- **Required correction** Replace "N ( > x )?" with the correct notation, likely N(>x) or N(x), and ensure consistent use throughout.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.1, data processing details
- **Evidence pointer** Section 3.1, location not provided
- **Issue** The description of ChIP-seq data processing is brief. Details on read trimming, quality filtering, alignment parameters, and peak calling parameters beyond the p-value threshold are not provided. The use of input or control samples for peak calling is not mentioned.
- **Required correction** Provide a more complete description of the data processing pipeline, including all relevant parameters and whether control samples were used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 4.4, correlation analysis
- **Evidence pointer** Section 4.4, location not provided
- **Issue** The definition of "strong and significant" correlation (absolute value greater than 0.5 and p less than 0.05) is presented without justification. The number of TF-target gene pairs in each class is not reported.
- **Required correction** Justify the correlation threshold or cite precedent for its use. Report the number of pairs in each class and consider a sensitivity analysis with different thresholds.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 4.5, Figure 5
- **Evidence pointer** Section 4.5, location not provided
- **Issue** The text refers to "SFig. 10" while other references use "Figure S10" or similar. The supplementary figure numbering is inconsistent.
- **Required correction** Standardize the supplementary figure references throughout the manuscript.

## Risk / unsupported claims
- The claim that "over 70% of reported interactions are spurious" for BCL3 in dexamethasone-treated cells is not fully supported because the statistical details of the differential binding analysis and the uncertainty around this estimate are not provided.
- The claim that the model "will increase reproducibility of analysis" is aspirational and not directly demonstrated; no comparison to existing pipelines or inter-laboratory reproducibility data is shown.
- The claim that tau is "the same value for all equally important TFs" is stated as an expectation but not tested across a diverse set of TFs.
- The biological interpretation of spurious binding events as potentially involved in chromatin organization or transcriptional condensate formation is speculative and not addressed by the data presented.
- The claim that predicted genes for BCL3 show enrichment for cell cycle and DNA damage response terms is based on a single perturbation experiment and a single cell line; generalizability is unclear.