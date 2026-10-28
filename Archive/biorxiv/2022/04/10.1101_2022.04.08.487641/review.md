## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table legends
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment of evidence with conclusions
- **Shared manuscript claim summary** The authors propose MOCCS profiles, a k-mer-based representation of TF DNA-binding specificity derived from ChIP-seq data, and use them to characterize TF-binding sequence diversity across cell types, predict variant effects on TF binding, and interpret non-coding GWAS SNPs
- **Visible evidence base** Abstract, full introduction, results narrative, discussion, methods, and supplementary figure/table legends
- **Missing materials affecting confidence** Main figures and tables are referenced but not provided; supplementary figures S1-S12 and Table S1 are described but not shown; no code or data availability verification possible

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable computational framework for representing and comparing TF binding specificities across many ChIP-seq samples. The core idea of using k-mer profiles is not entirely novel but the scale of application and the systematic comparison across cell types is commendable. However, the absence of the main figures and tables makes it impossible to evaluate the strength of the evidence supporting the central claims. The statistical methods for differential k-mer detection and the validation against external datasets are described but their implementation and results cannot be assessed. The claim that one-third of TFs show cell type-dependent binding specificity is interesting but the criteria and robustness of this classification are not fully transparent from the text alone. The GWAS interpretation section is promising but the clinical relevance and biological validation are limited to computational predictions.

- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational biology, and functional genomics would be interested. Those working on TF binding specificity, cis-regulatory variant interpretation, and GWAS follow-up studies would find the ΔMOCCS2score approach potentially useful for prioritizing non-coding variants and identifying responsible TFs and cell types. The resource of precomputed MOCCS profiles for over 10,000 ChIP-seq samples could serve as a community reference.

- **Major strengths**
  1. The scale of the analysis, covering over 10,000 ChIP-seq samples across diverse TFs and cell types, is substantial and could provide a valuable community resource.
  2. The k-mer-based representation avoids some limitations of PWM-based approaches, such as position dependency and low-frequency motif detection.
  3. The validation against in vitro (SNP-SELEX) and in vivo (ASB) datasets is a strong feature, providing orthogonal evidence for the utility of ΔMOCCS2scores.
  4. The application to GWAS SNPs with disease-specific predictions of responsible TFs and cell types has translational potential.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that MOCCS profiles reveal global distributions of DNA-binding specificities and that one-third of analyzed TFs show cell type-dependent differences
- **Evidence pointer** Results sections "MOCCS profile comparisons reveal TF- and TF family-dependent similarities of binding sequences" and "MOCCS profile comparison reveals cell type-dependent TFs and TF similarity patterns"; figures referenced as Fig 2, Fig 3, Fig S4-S7, Table S1
- **Concern** The main figures and tables supporting the central claims are not provided in the submitted material. Without seeing the actual UMAP visualizations, similarity distributions, heatmaps, and the list of cell type-dependent TFs, the strength and validity of these claims cannot be assessed. The text describes statistical tests but the effect sizes, data distributions, and the robustness of the classification of cell type-dependent versus non-dependent TFs are not verifiable.
- **Why it matters** The central contribution of the paper is the systematic comparison of MOCCS profiles. If the visualizations or statistical summaries reveal weak separation or marginal effects, the conclusions would be substantially weakened. The claim that one-third of TFs are cell type-dependent is a quantitative statement that requires the underlying data to be evaluated.
- **Resolution test** Provide the main figures and tables, including UMAP plots with clear annotations, the distribution of similarity scores across comparison groups, and the complete list of cell type-dependent TFs with their statistical support.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The manuscript claims that ΔMOCCS2scores predict the effect of variants on TF binding, validated by in vitro and in vivo assay datasets
- **Evidence pointer** Results section "ΔMOCCS2score profiles agree with in vitro SNP-SELEX data and in vivo allele-specific binding data"; Methods section "Calculation of the ΔMOCCS2score in a single ChIP-seq sample and comparison of the ΔMOCCS2score with the SNP-SELEX, ASB SNPs, and GWAS-SNPs"; Fig 5, Fig S9
- **Concern** The statistical framework for differential k-mer detection between two samples is described but the derivation appears incomplete. The test statistic formula references variances that are not fully defined in the text. The validation against SNP-SELEX and ASB data is described in terms of correlation coefficients and concordance fractions, but the specific numbers, significance thresholds, and the handling of multiple testing across many k-mers and samples are not reported. The permutation test for concordance uses only 100 permutations, which may be insufficient for stable p-value estimation.
- **Why it matters** The predictive validity of ΔMOCCS2scores is a key claim with potential applications in variant interpretation. If the statistical methods are not rigorous or the validation is weak, the utility of the approach for real-world applications is questionable.
- **Resolution test** Provide complete details of the statistical derivation, report the actual correlation coefficients and concordance fractions with confidence intervals, and justify the number of permutations used. Consider increasing permutations or using analytic methods for stability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological interpretation
- **Claim pointer** The manuscript claims that ΔMOCCS2scores can be used to interpret non-coding GWAS SNPs as TF-affecting SNPs and provide candidate responsible TFs and cell types
- **Evidence pointer** Results section "Evaluation of GWAS-SNPs in TF-binding regions and prediction of SNP-affected TFs through ΔMOCCS2score profiles"; Fig 6, Fig S10-S12
- **Concern** The GWAS analysis is presented as a demonstration but the biological validation is limited. The authors identify TFs and cell types for disease-associated SNPs but do not provide experimental validation or comparison with other variant effect prediction methods. The selection of four diseases is arbitrary and the clinical relevance of the predictions is not established. The relationship between allele frequency and ΔMOCCS2score is tested but the biological interpretation of this relationship is not discussed in depth.
- **Why it matters** The translational claim of interpreting GWAS SNPs is a significant part of the paper's impact. Without validation or benchmarking against existing methods, the added value of the ΔMOCCS2score approach over current tools is unclear.
- **Resolution test** Provide benchmarking against existing variant effect prediction tools, include experimental validation for at least a subset of predictions, or clearly state the limitations of the computational predictions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The manuscript claims that MOCCS profiles can detect TF binding sequences with high sensitivity and specificity based on simulation studies
- **Evidence pointer** Results section "Overview of the MOCCS profile"; Methods section "Significant k-mer detection"; Fig S2, Fig S8
- **Concern** The simulation studies are described but the parameters and results are not fully reported in the text. The sensitivity, specificity, and FDR values are mentioned as being high but the actual numbers are not given. The simulation conditions vary in the percentage of sequences containing true k-mers, number of peaks, and standard deviation, but the rationale for these parameter choices is not explained. The performance of the q-value calculation in real data scenarios with varying sample sizes and noise levels is not assessed.
- **Why it matters** The reliability of the significant k-mer detection is foundational to all downstream analyses. If the method has poor performance in realistic conditions, the conclusions drawn from real data would be compromised.
- **Resolution test** Report the simulation results in detail, including sensitivity, specificity, and FDR for each condition. Discuss the choice of simulation parameters and their relevance to real ChIP-seq data characteristics.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, first paragraph of Introduction
- **Issue** The abstract contains a grammatical error in the first sentence, "in natural conditions)" with an unmatched parenthesis. The introduction would benefit from a clearer statement of the gap in knowledge that MOCCS profiles address, particularly distinguishing from existing k-mer-based methods.
- **Required correction** Fix the grammatical error. Clarify the novelty of MOCCS profiles relative to existing approaches such as HOMER or DREME.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Preprocessing of ChIP-seq data"
- **Evidence pointer** Methods section
- **Issue** The description of the trimming of peak regions to +/- 350 bp from TFBSs is clear, but the rationale for this specific window size is not provided. The choice of window size could affect the k-mer profiles and downstream analyses.
- **Required correction** Provide justification for the window size or cite previous work that used similar parameters.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "Sample filtering"
- **Evidence pointer** Methods section
- **Issue** The soft filter uses a mapping rate threshold of "mean - 2SD (54.09364)" but it is unclear what distribution this mean and standard deviation are calculated from. The hard filter criteria are listed but the number of samples passing each filter is only given in the Results section without a breakdown by TF or cell type.
- **Required correction** Clarify the source of the mean and SD for the mapping rate threshold. Provide a table of sample counts by TF and cell type before and after filtering.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, "MOCCS profile comparison reveals cell type-dependent TFs and TF similarity patterns"
- **Evidence pointer** Results section, Fig 3
- **Concern** The definition of cell type-dependent TFs relies on statistical significance of the k-mer Jaccard similarity between same and different cell type classes. The threshold for significance and the handling of multiple comparisons across many TFs are not described in the text.
- **Required correction** Describe the multiple testing correction procedure for identifying cell type-dependent TFs and report the number of TFs tested and the significance threshold used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, "Calculation of the ΔMOCCS2score"
- **Evidence pointer** Methods section
- **Issue** The description of the two-sample z-test for differential k-mer detection is incomplete. The variance terms are not explicitly defined in terms of the MOCCS2score distributions, and the assumption of constant variance regardless of the score value is stated but not justified.
- **Required correction** Provide the complete formula for the test statistic with all terms defined. Discuss the validity of the constant variance assumption and its potential impact on results.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results, "Evaluation of GWAS-SNPs"
- **Evidence pointer** Results section, Fig 6
- **Concern** The selection of four diseases is not justified. The authors should explain why these specific diseases were chosen and whether the results are representative of broader GWAS applications.
- **Required correction** Add a sentence justifying the disease selection or acknowledge the limitation of the demonstration.

## Risk / unsupported claims
- The claim that one-third of analyzed TFs show cell type-dependent differences in binding specificity is unsupported without the underlying data and statistical details.
- The claim that ΔMOCCS2scores predict variant effects on TF binding is partially supported by correlation with external datasets, but the effect sizes and practical significance are not reported.
- The claim that ΔMOCCS2scores can interpret non-coding GWAS SNPs is demonstrated only computationally without experimental validation or benchmarking against existing methods.
- The performance metrics of the significant k-mer detection method (sensitivity, specificity, FDR) are stated as high but the actual values are not provided.
- The biological interpretation of the relationship between allele frequency and ΔMOCCS2score is not discussed, leaving the claim of evolutionary relevance unsupported.