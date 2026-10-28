## Review setup
- **Input scope** Full manuscript text (abstract, background, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with stated evidence; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors report that circulating DNA (cirDNA) fragment data can be used to identify well-positioned nucleosomes (WPNs), that WPN occupancy correlates with nucleosome-DNA affinity as evidenced by fragment size and codon usage bias, and that WPN occupancy patterns differ between healthy individuals and cancer patients, enabling high-performance cancer detection via machine learning.
- **Visible evidence base** Methods descriptions, results narrative, figure legends (Figs. 1-5), supplementary file references, cohort descriptions
- **Missing materials affecting confidence** Raw data files, complete figure panels, supplementary tables (Table S1, S2), detailed algorithm parameters, validation dataset details, code repository access

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting application of cirDNA fragmentomics to infer nucleosome occupancy and detect cancer. The authors have assembled a large dataset and applied a combination of established and novel computational methods. The central claims regarding the relationship between WPN occupancy, fragment size, and codon usage are intriguing but require stronger statistical support and clearer presentation. The cancer detection performance is impressive on the surface, but the validation approach and potential confounding factors need more thorough examination. The manuscript is well-written and the methods are described in sufficient detail to be reproducible, though some computational choices require justification. Overall, the work has merit but the evidence as presented does not fully establish all claims.

- **Who would be interested in the results, and why** Researchers in liquid biopsy and cancer diagnostics would be interested in the high-performance cancer detection approach. Scientists studying nucleosome positioning and chromatin structure would find the WPN identification and codon usage analysis relevant. The broader epigenomics community may be interested in the use of cfDNA as a readout of chromatin state. Clinicians involved in early cancer detection could find the method potentially applicable, though clinical validation is not yet demonstrated.

- **Major strengths** The study leverages a large public dataset and provides a substantial WPN atlas (~5 million positions). The multi-faceted analysis (fragment size, codon usage, genomic annotations) provides converging evidence for the biological relevance of WPN occupancy. The cancer detection performance is high, and the authors address the important issue of sequencing depth requirements. The inclusion of external validation cohorts (Jiang, Sun) strengthens some observations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that codon usage bias differs significantly between high- and low-occupancy WPNs (Fig. 2I), and that this supports a relationship between nucleosome occupancy and DNA-histone affinity.
- **Evidence pointer** Fig. 2I, Methods "Codons usage bias"
- **Concern** The statistical analysis of codon usage bias is described only as computing log-odds of codon frequencies. No information is provided on how significance was assessed, whether multiple testing correction was applied across the 61 sense codons, or what the effect sizes are. The reported P-value (P < 1.6 × 10⁻⁶) appears to be a single threshold, but the number of codons tested and the method for combining them is unclear. Additionally, the biological interpretation that codon usage differences reflect DNA-histone affinity adaptation is speculative and not directly tested.
- **Why it matters** The codon usage claim is a central piece of evidence for the fundamental biological insight of the paper. Without proper statistical framework, the claim is not established, and the interpretation may be confounded by other factors such as GC content, gene expression level, or chromatin state.
- **Resolution test** Provide a clear statistical framework: specify the test used, the number of comparisons, the correction method, and effect sizes. Consider permutation-based approaches that preserve genomic structure. Address potential confounders such as GC content and gene expression.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation methodology
- **Claim pointer** The authors claim high-performance cancer detection with specificity and sensitivity > 0.95 for seven cancer types (Fig. 3G).
- **Evidence pointer** Fig. 3G, Methods "Model construction, and AUC, sensitivity and specificity computations"
- **Concern** The validation methodology is not fully described. The authors mention 10-fold cross-validation repeated 15 times, but it is unclear whether the PCA projection is computed within each training fold or on the full dataset. If PCA is computed on all samples including test data, this constitutes data leakage and inflates performance estimates. Additionally, the authors do not report whether hyperparameter tuning was performed within cross-validation or on the full dataset. The handling of the class imbalance between healthy (245) and cancer (25-53 per type) samples is not described.
- **Why it matters** The cancer detection performance is a key translational claim. If the validation is not properly nested, the reported performance may be optimistically biased and not reproducible in independent datasets.
- **Resolution test** Clarify the validation pipeline: PCA must be fit on training data only, hyperparameters must be tuned within cross-validation, and class imbalance handling must be described. Consider reporting performance on a fully independent held-out cohort.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The authors claim that WPN occupancy at TFBS reflects transcriptional regulation and that cancer-related changes indicate shared, pan-cancer regulation of hematopoietic differentiation and neutrophil biology.
- **Evidence pointer** Fig. 5, Results "Nucleosome occupancy and transcriptional regulation"
- **Concern** The link between WPN occupancy at TFBS and actual transcription factor binding or gene expression is indirect. The authors correlate WPN occupancy at TSS with gene expression in healthy hematopoietic cells (Fig. 5A), but the correlation is modest (r = -0.36) and the analysis is limited to one cell type. The interpretation that reduced occupancy at TFBS indicates "stronger transcriptional regulation" in cancer is not directly supported by functional data. The KEGG pathway enrichment analysis is descriptive and the P-value for the NET association (P = 0.059) is not significant.
- **Why it matters** The biological interpretation extends beyond the data and may overstate the significance of the findings. The claim of pan-cancer regulation of specific transcriptional programs requires more direct evidence.
- **Resolution test** Provide additional analyses linking WPN occupancy changes to gene expression changes in the same samples, or validate a subset of TFBS findings with independent methods (e.g., ChIP-seq data). Soften the interpretation or provide direct functional validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation
- **Claim pointer** The authors claim that their WPN identification algorithm produces reliable nucleosome positions, validated by comparison with cell line-derived nucleosome maps.
- **Evidence pointer** Fig. S9D, Results "Comparison of WPN positions with cell line-derived nucleosome maps"
- **Concern** The comparison with cell line-derived nucleosome maps is described as showing "highly significant inclusion" but no quantitative metrics are provided in the main text. The authors state they did not compute P-values due to "very strong separation" from randomized positions, which is not a standard approach. The use of two different cell types (lymphoblastoid, CD4+ T cells) for validation is appropriate, but the overlap statistics should be reported.
- **Why it matters** The reliability of the WPN set underpins all subsequent analyses. Without quantitative validation metrics, the quality of the WPN atlas cannot be assessed.
- **Resolution test** Report the overlap statistics (e.g., Jaccard index, fraction of WPNs overlapping cell line nucleosomes) with confidence intervals. Consider computing empirical P-values from the randomization procedure.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods "Principal component analyses"
- **Evidence pointer** Methods section
- **Issue** The description of the PCA implementation using the PRIMME library is overly detailed and includes mathematical notation that is not necessary for understanding the approach. The key point is that an iterative algorithm was used for computational efficiency.
- **Required correction** Simplify the description to state that an iterative eigensolver was used to handle the high-dimensional data, and move the mathematical details to supplementary material.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods "Software"
- **Evidence pointer** Methods section
- **Issue** The authors state that code is available but do not provide a repository link or accession number in the text provided.
- **Required correction** Provide a clear statement of code availability with a repository URL or DOI.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 3G
- **Evidence pointer** Fig. 3G
- **Issue** The performance metrics are reported as sensitivity and specificity > 0.95, but the exact values and confidence intervals are not shown in the figure legend or text.
- **Required correction** Provide a table with exact sensitivity, specificity, and AUC values with 95% confidence intervals for each cancer type.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The statement that "cancer-specific nucleosome occupancy regulation does not occur predominantly at nucleosomes identified as well-positioned in healthy individuals" is presented as a conclusion, but it is based on the observation that differences are modest. This is an interpretation, not a direct finding.
- **Required correction** Rephrase as a hypothesis or speculation, clearly distinguishing it from directly supported findings.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results "Nucleosome occupancy and transcriptional regulation"
- **Evidence pointer** Results section
- **Concern** The number of TFBSs analyzed and the criteria for selecting the 644 human TFs from JASPAR are not stated.
- **Required correction** Provide the number of TFBSs tested, the filtering criteria, and the multiple testing correction approach.

## Risk / unsupported claims
- The claim that codon usage bias at high- versus low-occupancy WPNs reflects DNA-histone affinity adaptation is not directly supported; the statistical framework is incomplete and alternative explanations are not excluded.
- The cancer detection performance may be optimistically biased if the PCA projection is not properly nested within cross-validation; this cannot be assessed from the provided text.
- The biological interpretation of TFBS occupancy changes as indicating specific transcriptional program regulation in cancer is speculative and not directly validated.
- The claim that WPN positions are highly reproducible across datasets is not quantitatively supported in the main text.
- The statement that the approach is "not suitable for shallow sequencing" is based on one analysis with the Jiang dataset and may be overly general.
- The relationship between WPN occupancy and nucleosome-DNA affinity is inferred from fragment size differences but not directly measured; this inference should be clearly labeled as such.