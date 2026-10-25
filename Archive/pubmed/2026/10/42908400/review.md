## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and conclusions as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present a polymer-based simulation framework for the E. coli chromosome that separates nonspecific polymer confinement effects from biologically specific-folding interactions (SFIs). They claim that a null model of random polymer configurations recapitulates global Hi-C organization, that a small subset of SFIs (<7%) drives domain structure and single-cell heterogeneity, and that SFIs are enriched in the ter region, associated with cryptic prophages, depleted in positively supercoiled regions, and correlate with reduced gene expression.
- **Visible evidence base** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and data availability statements. No figures, tables, or supplementary materials were provided for direct inspection.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials referenced in the text (e.g., Fig. 1A-F, Fig. 2A-E, Fig. 3A-E, Fig. 4A-E, Fig. 5A-E, Supplementary Figs. S1-S7, Supplementary Tables S1-S2) were not available for review. This substantially limits the ability to verify quantitative claims, statistical analyses, and visual comparisons.

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting approach to decomposing Hi-C signals into polymer-physics-driven and biologically specific components in a circular bacterial chromosome. The methodological framework is clearly described and the authors are appropriately cautious about the interpretation of SFIs as statistical enrichments rather than direct molecular interactions. However, the absence of all figures and supplementary materials prevents verification of the central quantitative claims, including the reported correlation coefficients, statistical significance values, and the visual correspondence between null model predictions and experimental data. The manuscript would benefit from additional validation of the null model assumptions and a more direct comparison with existing Hi-C-integrated modeling approaches.
- **Who would be interested in the results, and why** Researchers studying bacterial chromosome organization, computational biophysicists developing polymer models of genome architecture, and experimentalists using Hi-C who seek to interpret ensemble-averaged contact maps in terms of underlying physical and molecular mechanisms. The framework's generalizability to other bacterial species and its potential for in silico perturbation testing would also interest the broader chromosome biology community.
- **Major strengths** The conceptual separation of polymer confinement from specific interactions addresses a genuine limitation in the field. The null model approach is principled and avoids circularity by not directly fitting Hi-C data. The extension to single-cell conformational ensembles and the integration with ChIP-seq, supercoiling, and expression data provide a multi-dimensional view of chromosome organization. The authors are appropriately cautious in their interpretation of SFIs as statistical constructs rather than direct molecular contacts.
- **Major Concerns** The absence of all figures and supplementary materials is a critical limitation for this review. The null model's ability to recapitulate global Hi-C organization with r = 0.83 is presented without visual verification or comparison to alternative null models. The identification of SFIs relies on statistical enrichment relative to the null model, but the sensitivity of this approach to null model assumptions, while partially addressed, requires more thorough validation. The causal claims regarding gene expression and prophage silencing are correlational and would benefit from experimental or in silico perturbation evidence.
- **Minor Comments** The manuscript would benefit from a more explicit statement of the computational cost and runtime of the simulations. The choice of 5-kb resolution and the 80-nm contact threshold are justified but could be discussed in more depth. The relationship between the 12 identified clusters and the 9 experimentally observed clusters warrants more detailed comparison.
- **Technical failings that need to be addressed before the case is established** The central quantitative claims (correlation coefficients, SFI percentages, statistical significance values) cannot be verified without access to the figures and supplementary materials. The null model's predictive power for global organization is reported but not demonstrated visually. The statistical framework for identifying SFIs and the FDR correction procedure are described but their robustness to null model parameter choices requires more extensive validation than presented in the text alone.
- **Assessment against Nature-style criteria** Originality: The approach of explicitly separating polymer confinement from specific interactions in a circular bacterial chromosome is a novel contribution. Scientific importance: The findings have implications for interpreting Hi-C data in bacteria and for understanding the relative roles of physical and molecular forces in chromosome organization. Interdisciplinary readership: The work bridges polymer physics, computational biology, and bacterial genetics, and would appeal to a broad audience. Technical soundness: The methodology is well-described, but the absence of figures and supplementary materials prevents full assessment of technical rigor. Readability for nonspecialists: The manuscript is clearly written and accessible, though some sections assume familiarity with Hi-C analysis and polymer modeling.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim pointer** The claim that the null model recapitulates global Hi-C organization (r = 0.83, ρ = 0.80) and that the specific-fold model reproduces CID boundaries and single-cell heterogeneity.
- **Evidence pointer** Figures 1C-F, 2B-C, Supplementary Figures S1, S3, S4
- **Concern** All figures and supplementary materials referenced in the text were not provided for review. The central quantitative claims of the manuscript, including the correlation between null model and experimental Hi-C maps, the identification of SFIs, and the reproduction of CID boundaries, cannot be independently verified.
- **Why it matters** The manuscript's core conclusions rest on these quantitative comparisons and visual demonstrations. Without access to the figures, it is impossible to assess whether the reported correlations are visually convincing, whether the null model truly captures global organization, or whether the specific-fold model reproduces the key features claimed.
- **Resolution test** Provide all figures and supplementary materials for review, or provide detailed numerical summaries of the key results (e.g., correlation coefficients with confidence intervals, SFI counts and percentages, cluster assignments) that allow independent verification.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The identification of SFIs as contacts significantly enriched in experimental Hi-C relative to the null model, with FDR = 0.05, and the claim that reconstruction accuracy is insensitive to FDR threshold.
- **Evidence pointer** Materials and methods (Identification of specific-folding interactions), Supplementary Figure S1
- **Concern** The statistical framework for identifying SFIs is described but the details of the multiple testing correction, the handling of spatial correlations between nearby genomic bins, and the potential for false positives due to systematic biases in Hi-C data are not fully addressed. The claim that reconstruction accuracy is insensitive to FDR threshold is presented without supporting data.
- **Why it matters** The identification of SFIs is the central methodological contribution of the manuscript. If the statistical framework is not robust, the subsequent analyses of SFI distribution, protein co-localization, and gene expression correlations could be compromised.
- **Resolution test** Provide a more detailed description of the statistical framework, including the null distribution construction, the handling of multiple testing, and the sensitivity analyses. Show the reconstruction accuracy as a function of FDR threshold in a figure or table.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Model validation
- **Claim pointer** The claim that the null model's predictions are consistent with scaling relationships derived from experimental Hi-C maps and with single-cell imaging data.
- **Evidence pointer** Results (Simulated chromosome-fold null model reproduces experimentally determined global organization), Supplementary Figure S3
- **Concern** The validation of the null model relies on comparisons to experimental Hi-C data and to previously published imaging results. However, the manuscript does not provide a systematic comparison of the null model's predictions to alternative polymer models (e.g., models with different persistence lengths, confinement geometries, or excluded volume treatments). The sensitivity of the results to the choice of bead size (5 kb) and contact threshold (80 nm) is only partially addressed.
- **Why it matters** The claim that the null model captures "generic polymer behavior" depends on the model being a faithful representation of the physical system. Without comparison to alternative models, it is difficult to assess whether the null model is truly minimal or whether its success reflects specific parameter choices.
- **Resolution test** Provide a systematic comparison of the null model to alternative polymer models with different parameters. Show that the key conclusions (e.g., the fraction of SFIs, their distribution) are robust to reasonable variations in model parameters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Causal inference
- **Claim pointer** The claim that high-SFI regions are associated with reduced gene expression and that this reflects a functional relationship between chromosome folding and transcriptional activity.
- **Evidence pointer** Results (Genes in low-SFI regions are expressed at higher levels than genes in high-SFI regions), Figure 5, Supplementary Figure S7
- **Concern** The correlation between SFI density and gene expression is interpreted as evidence that chromosome folding influences transcription. However, the analysis is purely correlational and does not establish causality. The authors acknowledge this limitation but do not provide any perturbation experiments or alternative analyses to support a causal interpretation.
- **Why it matters** The claim that SFIs "shape" gene expression is a strong statement that goes beyond the correlational evidence presented. Without causal evidence, the interpretation remains speculative.
- **Resolution test** Provide in silico perturbation experiments (e.g., removing specific SFIs and assessing the effect on gene expression) or discuss how the correlational findings could be tested experimentally.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Computational cost
- **Affected element** Materials and methods (Polymer model setup)
- **Evidence pointer** Materials and methods
- **Issue** The manuscript does not report the computational cost or runtime of the simulations, which is relevant for assessing the practicality of the approach for other researchers.
- **Required correction** Add a statement about the computational resources required and the typical runtime for generating the null model and specific-fold ensembles.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Parameter justification
- **Affected element** Materials and methods (Polymer model setup)
- **Evidence pointer** Materials and methods
- **Issue** The choice of 5-kb bead size and 80-nm contact threshold is justified by reference to previous studies, but a more detailed discussion of the sensitivity of the results to these parameters would strengthen the manuscript.
- **Required correction** Add a brief discussion of how the results depend on the choice of bead size and contact threshold, referencing the sensitivity analysis in Supplementary Figure S2.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Cluster comparison
- **Affected element** Results (Isolating specific-folding interactions)
- **Evidence pointer** Results, Supplementary Figure S4
- **Concern** The manuscript reports 12 distinct spatial clusters from k-means clustering and compares them to 9 experimentally identified clusters. The relationship between these two sets of clusters is not discussed in detail.
- **Required correction** Provide a more detailed comparison of the 12 modeled clusters with the 9 experimental clusters, including a discussion of potential reasons for the discrepancy.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The term "specific-folding interactions" is used throughout but is not explicitly defined in the introduction or methods. The authors note that these are statistically enriched contacts, but the term could be misinterpreted as implying direct molecular interactions.
- **Required correction** Add an explicit definition of SFIs in the introduction or methods, clarifying that they are statistical enrichments relative to the null model and do not necessarily correspond to direct molecular contacts.

## Risk / unsupported claims
- The claim that the null model recapitulates global Hi-C organization with r = 0.83 cannot be verified without access to Figure 1D and the underlying data.
- The claim that SFIs constitute less than 7% of all contacts cannot be verified without access to the SFI identification results.
- The claim that the specific-fold model reproduces CID boundaries and single-cell heterogeneity cannot be verified without access to Figures 2B-C and Supplementary Figure S4.
- The claim that H-NS and MatP are major determinants of SFIs relies on cross-correlation analyses presented in Figure 4E, which was not available for review.
- The claim that high-SFI regions are associated with reduced gene expression is based on correlational analyses presented in Figure 5 and Supplementary Figure S7, which were not available for review.
- The claim that the framework is generalizable to other bacterial species is plausible but not demonstrated in the current manuscript.