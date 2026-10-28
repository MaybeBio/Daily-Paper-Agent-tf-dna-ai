## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, data analysis, and interpretation as presented in the manuscript
- **Shared manuscript claim summary** The authors systematically characterize Tn5 transposase insertion preferences across multiple species and contexts, identify DNA sequence motif and shape as key determinants, develop a bias correction pipeline, and demonstrate that correction improves ATAC-seq peak calling and recovers biologically relevant regulatory elements.
- **Visible evidence base** Main text, figures referenced (Figures 1–5), supplementary figure references, methods section, data availability statement
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; no access to code repository or raw data; no detailed model hyperparameters or feature importance values; no statistical test details for several comparisons

## Reviewer
- **Overall assessment** This manuscript presents a systematic and potentially valuable characterization of Tn5 insertion preferences across multiple organisms and contexts. The finding that DNA shape, particularly minor groove width, plays a dominant role in Tn5 insertion bias is novel and mechanistically plausible. The demonstration that bias correction improves peak calling and recovers TF-bound regions is practically important. However, several technical aspects require clarification and additional validation before the conclusions are fully established. The machine learning framework is described at a high level, and key details about model construction, validation, and interpretation are missing. The causal link between DNA shape and Tn5 insertion is inferred from correlation-based models. The peak calling improvement, while suggestive, needs more rigorous statistical evaluation and replication across diverse datasets.

- **Who would be interested in the results, and why** Researchers using ATAC-seq for regulatory genomics, particularly those performing peak calling, footprinting analysis, or single-cell ATAC-seq. The bias correction pipeline has direct practical utility. The mechanistic insights into Tn5 insertion preferences will interest molecular biologists studying transposition mechanisms and computational biologists developing sequencing analysis tools.

- **Major strengths** 
  1. Systematic multi-species analysis of Tn5 insertion preferences, addressing conflicting prior reports.
  2. Novel finding that DNA shape, especially MGW, is a dominant determinant of Tn5 insertion, exceeding the contribution of sequence motif alone.
  3. Demonstration that nucleotide dependence information (dinucleotide features) can effectively capture both motif and shape effects, providing a practical framework for bias correction.
  4. Practical demonstration that bias correction improves ATAC-seq peak calling and recovers TF-bound regulatory elements.
  5. Open availability of the pipeline and code.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that DNA shape cooperatively works with DNA motif to affect Tn5 insertion preference, with MGW ranked as the most influential parameter.
- **Evidence pointer** Figure 3, Figure 4B, Methods section "Quantitative assessment of effect of DNA shape and motif"
- **Concern** The machine learning framework is described at a high level, but critical details are missing. The authors state that elastic-net logistic regression was used with three types of input vectors (motif, 4shapes, motif+14shapes), but do not provide: (1) the exact feature encoding scheme for motif vectors, (2) the window size and position relative to insertion sites, (3) the regularization parameter selection procedure, (4) the distribution of the 20,000 positive and negative samples across genomic features, and (5) the variance of accuracy estimates across cross-validation folds. The claim that MGW "ranked first" in importance is based on summed absolute coefficients, but the authors do not report the actual coefficient values, confidence intervals, or whether this ranking is stable across the 31 samples. The shuffling control for DNA shape values is described, but the procedure for shuffling the "original pentamer table" is unclear.
- **Why it matters** The central mechanistic claim of the paper rests on the relative importance of DNA shape versus motif features. Without detailed model specifications and uncertainty quantification, the reader cannot assess whether the reported ranking is robust or an artifact of the specific feature encoding, sample selection, or regularization scheme. The practical utility of the bias correction pipeline depends on the reliability of the underlying model.
- **Resolution test** Provide complete model specifications, including feature encoding details, hyperparameter selection, and cross-validation results with variance estimates. Report coefficient values with confidence intervals for all features across all samples. Show that the MGW importance ranking is consistent across samples and robust to alternative feature encodings and model specifications.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that correcting for Tn5 insertion preference improves ATAC-seq peak calling performance and recovers false-negative peaks with TF enrichment.
- **Evidence pointer** Figure 5, Methods section "Measuring Tn5 insertion preference effect on peak calling analysis"
- **Concern** The peak calling comparison is based on a single ATAC-seq dataset from mouse ESCs. The authors report 75,017 and 80,041 peaks for uncorrected and corrected signals, respectively, with 473 uncorrected-specific and 5,657 corrected-specific peaks. However, no statistical significance is provided for the difference in peak numbers. The TF enrichment analysis using GIGGLE scores shows higher enrichment in corrected-specific peaks (median 120.2) compared to uncorrected-specific peaks (median 8.3), but the authors do not report whether this difference is statistically significant. The sampling control (n=400) is described, but the number of sampling iterations and the variance of the GIGGLE scores across iterations are not reported. The choice of MACS2 parameters and the threshold q<0.01 are not justified. The generalizability of the improvement to other cell types, datasets, or peak callers is not demonstrated.
- **Why it matters** The practical claim that bias correction improves ATAC-seq analysis is a key contribution. If the improvement is not statistically robust or is specific to one dataset and parameter set, the general recommendation to modify analysis pipelines may be premature. The biological interpretation that corrected-specific peaks represent false negatives depends on the reliability of the peak calling comparison.
- **Resolution test** Provide statistical tests for the difference in peak numbers and GIGGLE score distributions. Report the number of sampling iterations and variance for the control analysis. Validate the improvement across multiple independent ATAC-seq datasets, different cell types, and alternative peak callers. Justify the choice of MACS2 parameters and demonstrate robustness to parameter variations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that DNA methylation promotes Tn5 insertion in naked genomic DNA, based on the context-dependent approach.
- **Evidence pointer** Figure 4A, Methods section "Context-dependent approach for dissecting DNA methylation effect"
- **Concern** The context-dependent approach for assessing DNA methylation effects is described briefly. The authors classify 9mers into four groups based on methylation status in two cell types and compare Tn5 insertion frequencies. However, the analysis appears to be limited to two cell types (mouse ESCs and germ cells), and the number of 9mers in each group is not reported. The Z-score normalization procedure is described, but the statistical test used to compare distributions across groups is not specified. The conclusion that "DNA methylation promotes Tn5 insertion" is based on a comparison of median values in boxplots, but no effect size or confidence interval is provided. The authors later state that DNA methylation has "negligible overall importance" in the regression model, which appears to contradict the earlier claim of a promoting effect.
- **Why it matters** The role of DNA methylation in Tn5 insertion is a secondary but relevant claim. The apparent inconsistency between the context-dependent analysis and the regression model results needs resolution. If DNA methylation has a promoting effect in some contexts but negligible importance overall, this nuance should be explicitly discussed.
- **Resolution test** Report the number of 9mers in each methylation group, the statistical tests used, and effect sizes with confidence intervals. Reconcile the apparent discrepancy between the context-dependent analysis and the regression model results. Discuss the conditions under which DNA methylation effects may be relevant.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that Tn5 insertion patterns near TSSs are cell type specific and can separate stem cells from differentiated cells.
- **Evidence pointer** Figure 1, Results section "Tn5 insertion is not uniformly random in naked genomic DNA"
- **Concern** The authors state that Tn5 insertion patterns near TSSs are cell type specific and can be used to separate stem cells from terminally differentiated cells, but no quantitative analysis is presented to support this claim. No clustering analysis, classification accuracy, or statistical test is shown. The statement appears in the results section but is not accompanied by any figure or table demonstrating this finding.
- **Why it matters** This claim suggests that Tn5 insertion patterns carry biological information beyond sequence preferences, potentially reflecting epigenetic states that persist in naked DNA. If true, this would be a notable finding. However, without quantitative evidence, the claim is unsupported.
- **Resolution test** Provide a quantitative analysis demonstrating cell type specificity, such as hierarchical clustering with bootstrap support, classification accuracy with cross-validation, or a statistical test comparing within-cell-type versus between-cell-type similarity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that the identified Tn5 motifs are consistent across species and with previous reports.
- **Evidence pointer** Figure 2, Results section "DNA motif signature is insufficient to explain Tn5 insertion preference"
- **Concern** The authors identify one significant motif per species using MEME and report that these motifs are consistent with previous reports of a G/C pair at the edges of the 9-bp core. However, the motif discovery is based on 500,000 randomly selected insertion sites per sample, and the authors do not report the motif width, the number of sites used for motif refinement, or the statistical significance of the motifs (e.g., E-values). The comparison with previous reports appears qualitative. The statement that "only 16–29% of the Tn5 insertion sites fall inside motif sites" suggests that the motif is a weak predictor, which is consistent with the authors' conclusion that motif alone is insufficient, but the implications for the motif's biological relevance are not discussed.
- **Why it matters** The motif analysis is foundational to the paper's argument that sequence features are insufficient to explain Tn5 insertion. The quality and statistical support of the identified motifs need to be established for this argument to be convincing.
- **Resolution test** Report motif widths, E-values, and the number of sites used for refinement. Provide a quantitative comparison of the identified motifs across species (e.g., motif similarity scores). Discuss the implications of the low fraction of insertion sites within motifs for the biological relevance of the motif.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that Tn5 insertion is "not uniformly distributed or random" on naked genomic DNA, but this is a somewhat circular statement. The more precise claim is that insertion is non-random with respect to sequence features.
- **Required correction** Rephrase to state that Tn5 insertion is non-random and influenced by specific sequence features.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "Measuring Tn5 insertion preference effect on peak calling analysis"
- **Issue** The description of the seqOutBias parameters is incomplete. The authors state they set k=19 but do not specify other relevant parameters such as the genome build, read filtering criteria, or how multi-mapping reads were handled.
- **Required correction** Provide complete parameter specifications for seqOutBias and all other tools used in the pipeline.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Figure 5B
- **Issue** The comparison of peak occupancy and significance between uncorrected and corrected shared peaks is described qualitatively. No statistical test is reported for the differences.
- **Required correction** Report statistical tests for the differences in peak occupancy and significance between conditions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions that the pipeline could be applied to single-cell ATAC-seq data but does not elaborate on potential challenges or modifications needed for sparse single-cell data.
- **Required correction** Add a brief discussion of potential limitations and adaptations needed for single-cell applications.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 4B
- **Evidence pointer** Figure 4B
- **Issue** The importance ranking in Figure 4B is described in the text, but the figure itself is not described in sufficient detail. It is unclear what exactly is plotted and how the "importance" is calculated.
- **Required correction** Provide a clear figure legend explaining the calculation of importance and what is displayed.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The data availability statement mentions the GEO accession for in-house data but does not specify which public datasets were used and their accession numbers.
- **Required correction** Provide a complete list of all datasets used, including public dataset accession numbers.

## Risk / unsupported claims
- The claim that Tn5 insertion patterns near TSSs are cell type specific and can separate stem cells from differentiated cells is not supported by any quantitative analysis in the provided text.
- The claim that DNA methylation promotes Tn5 insertion in naked genomic DNA is based on a comparison that lacks statistical detail and appears partially contradicted by the regression model results.
- The claim that the peak calling improvement is generalizable is based on a single dataset and lacks statistical validation.
- The relative importance ranking of DNA shape features (MGW ranked first) lacks uncertainty quantification and may be sensitive to model specifications not fully described.
- The statement that "DNA shape has an independent role in regulating Tn5 insertion" is inferred from correlation-based models and requires causal validation.