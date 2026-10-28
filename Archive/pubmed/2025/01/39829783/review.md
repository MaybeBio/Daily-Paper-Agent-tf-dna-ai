## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific claims, methodology, validation, and interpretation as presented in the provided text; no external data or code were accessed
- **Shared manuscript claim summary** The authors present ChromBPNet, a deep learning framework for base-resolution chromatin accessibility modeling that factorizes assay-specific enzyme biases from regulatory sequence determinants. They claim that this enables robust discovery of TF motif lexicons, cooperative syntax, footprints, and variant effect prediction across assays, cell types, and ancestries, with performance competitive to or better than larger models like Enformer.
- **Visible evidence base** Main text figures (Fig. 1–7), Extended Data figures (Extended Fig. 1–10), tables (Table 1–5), methods section, and supplementary file references
- **Missing materials affecting confidence** Actual figures, tables, and supplementary files were not provided; only figure captions and in-text references were available. This limits verification of quantitative results, statistical details, and visual data.

## Reviewer
- **Overall assessment** This manuscript presents a technically sophisticated and potentially impactful framework for modeling chromatin accessibility at base resolution. The core idea of explicitly learning and deconvolving enzyme biases from regulatory signals is well motivated and the authors provide extensive benchmarking across multiple assays, cell types, and variant effect prediction tasks. However, the current version has several concerns that need to be addressed, particularly around the clarity of the bias-correction mechanism, the statistical rigor of some benchmarks, and the generalizability claims. The manuscript is promising but requires revisions to fully establish its claims.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and functional genomics would be interested. Specifically, those working on TF footprinting, cis-regulatory sequence modeling, variant effect prediction, and deep learning applications to genomics. The framework's ability to impute high-resolution profiles from low-coverage data is also relevant to single-cell genomics communities.
- **Major strengths**
  1. Novel bias-factorized architecture that explicitly separates enzyme bias from regulatory signal, addressing a known limitation in chromatin accessibility modeling.
  2. Comprehensive benchmarking across multiple assays (ATAC-seq, DNase-seq), cell lines, and ancestries, including comparisons with state-of-the-art methods like Enformer.
  3. Demonstrated utility in variant effect prediction, including prioritization of fine-mapped GWAS variants and de novo variants in rare disease.
  4. The framework is lightweight and trainable on individual datasets, making it accessible to the broader community.
  5. The authors provide a well-documented code repository and standardized benchmark datasets, which is commendable for reproducibility.
- **Major Concerns**
  - **R1-M1** (Severity: Major, Blocking: Yes, Axis: Technical soundness)
    - **Claim pointer** The claim that ChromBPNet "deconvolves" enzyme biases from regulatory determinants is central to the paper. The two-stage training procedure is described, but the mathematical and conceptual basis for why this decomposition is valid is not fully articulated. Specifically, the assumption that the bias model trained on background regions captures the same bias present in peak regions is not rigorously justified.
    - **Evidence pointer** Methods: "Bias-factorized ChromBPNet architecture" and "BPNet based bias model training and hyperparameter tuning"; Results: "A bias-factorized neural network (ChromBPNet) deconvolves enzyme sequence preferences..."
    - **Concern** The manuscript does not provide a formal proof or a clear theoretical argument for why the multiplicative combination of bias and residual predictions (as implied by the loss function) leads to a clean separation of enzyme bias and regulatory signal. The authors show empirical evidence (e.g., elimination of bias motifs), but the underlying assumption that the bias is independent of the regulatory sequence context is not tested. This is a critical assumption that, if violated, could lead to incorrect biological interpretations.
    - **Why it matters** If the decomposition is not valid, the "bias-corrected" profiles and contribution scores may still contain residual bias or may remove genuine regulatory signal. This would undermine the core claims of the paper and the utility of the framework for downstream analyses.
    - **Resolution test** The authors should provide a more rigorous theoretical justification for the decomposition, or at least a series of controlled experiments that test the independence assumption. For example, they could train a bias model on background regions from one cell type and apply it to correct peaks from another cell type with different chromatin features, to see if the correction remains valid. They could also compare the bias-corrected profiles to profiles from a different assay (e.g., MNase-seq) that does not have the same enzyme bias, to validate that the correction is not removing real signal.
  - **R1-M2** (Severity: Major, Blocking: Yes, Axis: Statistical rigor)
    - **Claim pointer** The claim that ChromBPNet "substantially improves concordance between ATAC-seq and DNase-seq profiles" is based on JSD comparisons. However, the statistical significance of these improvements is not reported.
    - **Evidence pointer** Results: "ChromBPNet substantially improves concordance between ATAC-seq and DNase-seq profiles & predictive sequence features"; Figure 3b,c.
    - **Concern** The manuscript reports mean JSD values with standard deviations but does not provide confidence intervals or p-values for the differences between uncorrected and bias-corrected predictions. It is unclear if the observed improvements are statistically significant, especially given the large number of peaks tested.
    - **Why it matters** Without statistical significance testing, the reader cannot assess the robustness of the claimed improvement. This is particularly important given that the improvement in JSD, while large in relative terms, may be driven by a subset of peaks or may not be reproducible across different datasets.
    - **Resolution test** The authors should perform paired statistical tests (e.g., Wilcoxon signed-rank test) on the JSD values across peaks for uncorrected vs. bias-corrected predictions, and report the resulting p-values. They should also report effect sizes and confidence intervals.
  - **R1-M3** (Severity: Major, Blocking: No, Axis: Generalizability)
    - **Claim pointer** The claim that ChromBPNet models "exhibit robust variant effect predictions across ancestries" is based on correlations with QTL effect sizes. However, the manuscript does not discuss potential confounding factors such as linkage disequilibrium (LD) or population structure.
    - **Evidence pointer** Results: "ChromBPNet predicts effects of genetic variants on chromatin accessibility across assays, ancestry groups, cell-lines and primary cells"; Figure 6.
    - **Concern** The manuscript shows high correlations between predicted and observed effect sizes across ancestries, but it is not clear if these correlations are driven by causal variants or by variants in LD with causal variants. The authors do not perform conditional analyses or fine-mapping to address this.
    - **Why it matters** If the predictions are driven by LD, the model may not be learning causal regulatory mechanisms, which would limit its utility for interpreting disease-associated variants.
    - **Resolution test** The authors should perform a conditional analysis, where they condition on the lead variant in each locus and assess whether the predicted effect sizes still correlate with the observed QTL effect sizes. They could also use fine-mapped variants (as they do for the blood trait analysis) and assess enrichment specifically at credible sets.
  - **R1-M4** (Severity: Major, Blocking: No, Axis: Technical soundness)
    - **Claim pointer** The claim that ChromBPNet "can impute base-resolution profiles, footprints and predictive sequence motifs from low coverage ATAC-seq and DNase-seq datasets" is based on comparisons to a reference model trained on deep data. However, the manuscript does not compare to other imputation methods.
    - **Evidence pointer** Results: "ChromBPNet can impute base-resolution profiles, footprints and predictive sequence motifs from low coverage ATAC-seq and DNase-seq datasets"; Figure 4.
    - **Concern** The manuscript shows that ChromBPNet models trained on subsampled data perform well relative to the reference model, but it does not compare this to existing imputation methods (e.g., imputation based on peak calls or other deep learning models). This makes it difficult to assess the added value of ChromBPNet for this specific application.
    - **Why it matters** If existing methods perform similarly, the claim of "imputation" may not be a significant contribution. The authors should benchmark against at least one or two existing imputation approaches to contextualize their results.
    - **Resolution test** The authors should compare their imputation performance to a simple baseline (e.g., using the reference model's predictions as a gold standard and comparing to a method that uses peak calls to impute profiles) and to a state-of-the-art imputation method if available.
- **Minor Comments**
  - **R1-m1** (Severity: Minor, Axis: Clarity)
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract: "bias factorized, base-resolution deep learning models"; Introduction: "we introduce ChromBPNet..."
    - **Issue** The term "bias factorized" is used without a clear definition in the abstract. A reader unfamiliar with the prior BPNet work may not understand what this means.
    - **Required correction** Define "bias factorized" in the abstract, e.g., "a model that explicitly separates assay-specific enzymatic cleavage bias from regulatory sequence determinants."
  - **R1-m2** (Severity: Minor, Axis: Reproducibility)
    - **Affected element** Methods: "Data pre-processing for ATAC-seq and DNase-seq"
    - **Evidence pointer** Methods: "Bulk ATAC/DNase-seq" section
    - **Issue** The manuscript states that "we download bam files from ENCODE website" but does not provide the specific accession IDs for all datasets used in the main analyses. Table 1 is referenced but not provided.
    - **Required correction** Ensure that Table 1 (or a supplementary table) lists all ENCODE accession IDs for the datasets used in each analysis, including the single-cell datasets.
  - **R1-m3** (Severity: Minor, Axis: Statistical rigor)
    - **Affected element** Results: "ChromBPNet reveals compact TF motif lexicons, cooperative composite elements and predictive motif instances that influence chromatin accessibility and TF occupancy"
    - **Evidence pointer** Results: "Count contribution scores revealed between 26 to 47 predictive motifs supported by over 100 seqlets..."
    - **Issue** The manuscript reports the number of motifs but does not provide a measure of uncertainty or a comparison to a null expectation. It is unclear if these numbers are significantly different from what would be expected by chance.
    - **Required correction** Provide a null model or permutation-based test to assess the significance of the number of discovered motifs.
  - **R1-m4** (Severity: Minor, Axis: Interpretation)
    - **Affected element** Discussion: "Limitations, Caveats and future opportunities"
    - **Evidence pointer** Discussion: "ChromBPNet's predictions of total accessibility still lag behind pseudo-replicate concordance..."
    - **Issue** The manuscript acknowledges that total accessibility prediction lags behind pseudo-replicate concordance but does not discuss potential reasons or implications for the biological interpretation of the model's predictions.
    - **Required correction** Add a brief discussion of why total accessibility prediction may be limited (e.g., distal regulation) and how this might affect the interpretation of variant effect predictions.
  - **R1-m5** (Severity: Minor, Axis: Clarity)
    - **Affected element** Methods: "ChromBPNet variant effect prediction metrics"
    - **Evidence pointer** Methods: "We then use all these three measures computed across 5-folds as follows to define:"
    - **Issue** The sentence is incomplete; the actual formulas for the integrative scores (IES, IPS) are not provided in the text.
    - **Required correction** Provide the complete formulas for IES and IPS, or refer to a supplementary file where they are defined.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1 (theoretical justification for bias decomposition)
  - R1-M2 (statistical significance of concordance improvements)
  - R1-M4 (lack of comparison to existing imputation methods)
- **Assessment against Nature-style criteria**
  - **Originality** High. The bias-factorized architecture is a novel contribution that addresses a known limitation in the field. The idea of explicitly modeling enzyme bias as a separate component is conceptually new and has the potential to influence future work.
  - **Scientific importance** High. Chromatin accessibility is a widely used assay, and the ability to accurately model and interpret base-resolution profiles has broad implications for understanding gene regulation and interpreting non-coding variants. The demonstrated utility in variant effect prediction is particularly important.
  - **Interdisciplinary readership** Moderate. The manuscript is primarily targeted at computational biologists and genomics researchers. The methods are complex and may be challenging for a broader biological audience. However, the potential applications to disease genetics could attract interest from clinical researchers.
  - **Technical soundness** Moderate. The methods are generally sound, but the lack of statistical rigor in some benchmarks and the incomplete theoretical justification for the core bias-decomposition mechanism are significant concerns. The benchmarking is extensive but needs to be more rigorous.
  - **Readability for nonspecialists** Moderate. The manuscript is well-written but dense. The abstract and introduction are accessible, but the methods and results sections require specialized knowledge. The authors should consider adding a plain-language summary of the key findings and their implications.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially important contribution, but the core claims need to be more rigorously supported. Specifically, the authors need to (1) provide a stronger theoretical or empirical justification for the bias-decomposition mechanism, (2) add statistical significance testing to the concordance benchmarks, and (3) compare their imputation approach to existing methods. If these concerns are addressed, the manuscript would be suitable for publication in a high-impact journal.

## Risk / unsupported claims
- The claim that ChromBPNet "deconvolves" enzyme biases is not fully supported without a rigorous theoretical or empirical demonstration of the independence assumption.
- The claim of "robust variant effect predictions across ancestries" is not fully supported without addressing potential confounding by LD.
- The claim that ChromBPNet "can impute base-resolution profiles... from low coverage datasets" is not fully supported without comparison to existing imputation methods.
- The claim that ChromBPNet "reveals compact TF motif lexicons" is not supported with a statistical null model.
- The claim that ChromBPNet "outperforms alternative footprinting approaches" is based on a specific benchmark (correlation with ChIP-seq contribution scores) and may not generalize to all contexts.