## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion) without figures or supplementary materials
- **Assessment boundary** Scientific validity, methodological soundness, evidence quality, and clarity of claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose TraceBind, a computational framework for ATAC-seq footprinting that corrects sample-specific Tn5 cleavage bias by fine-tuning a pretrained model on mitochondrial DNA reads, and demonstrate improved specificity and sensitivity across bulk and single-cell datasets, with applications to aging and disease.
- **Visible evidence base** Text descriptions of results, methods, and figure legends; no actual figures, tables, or supplementary data provided
- **Missing materials affecting confidence** All figures, supplementary figures, supplementary data files, and code availability information are not provided; statistical details and effect sizes are only partially described in text

## Reviewer

- **Overall assessment** This manuscript addresses a timely and important problem in ATAC-seq analysis: the assumption of a global Tn5 cleavage bias across samples. The authors provide compelling evidence that Tn5 bias varies substantially across samples and introduce a practical solution using mitochondrial DNA as an internal control. The methodological framework is well-motivated and the validation strategy is thorough, including multiple independent benchmarks. However, the current text leaves several critical technical details underspecified, and the absence of figures and supplementary materials prevents full verification of the claims. The biological applications, particularly the aging and disease analyses, are intriguing but would benefit from clearer presentation of effect sizes and controls.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing and applying regulatory genomics tools, particularly those working on ATAC-seq footprinting, transcription factor binding inference, and single-cell epigenomics. The sample-specific bias correction approach is broadly relevant to any assay using Tn5 transposition. Additionally, researchers studying aging-related chromatin changes and kidney disease will find the applications of interest.

- **Major Strengths**
  - The identification of sample-specific Tn5 bias variability is a significant and previously underappreciated finding that challenges existing assumptions in the field
  - The use of mitochondrial DNA as an internal negative control is elegant and practical, leveraging data that is typically discarded
  - The validation strategy is comprehensive, including naked DNA controls, matched ChIP-seq/CUT&RUN, and perturbation experiments
  - The integration with downstream tools (chromVAR, Epitrace) demonstrates practical utility beyond footprint detection
  - The comparison with DNA foundation models addresses an emerging and important question about the relationship between sequence-based predictions and experimental measurements

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that fine-tuning a pretrained model on mitochondrial DNA reads provides accurate sample-specific Tn5 bias correction
- **Evidence pointer** Methods section "Fine-tuning PRINT with mitochondrial Tn5 reads"; Results section "TraceBind: footprinting with sample-specific bias correction"
- **Concern** The manuscript does not provide sufficient detail on how the fine-tuning procedure avoids overfitting to the mitochondrial genome, which is small (~16 kb) and has distinct sequence properties compared to nuclear DNA. The freezing strategy is described, but there is no discussion of how many epochs are used, what regularization is applied, or how the model generalizes from mitochondrial to nuclear sequences. The validation on held-out mitochondrial test regions is described, but this does not directly demonstrate that the fine-tuned model improves bias correction on nuclear DNA.
- **Why it matters** The core innovation of TraceBind depends on the assumption that mitochondrial DNA provides a faithful proxy for nuclear Tn5 bias. If the fine-tuned model overfits to mitochondrial-specific features, the correction could introduce new artifacts in nuclear regions. Without explicit validation on nuclear DNA (e.g., comparing predicted vs. observed insertion rates at known unbiased regions), the central claim is not fully established.
- **Resolution test** Provide quantitative evidence that the fine-tuned model improves Tn5 bias prediction on nuclear DNA, e.g., by comparing predicted and observed insertion rates at nucleosome-free regions or at regions without known protein binding. Additionally, demonstrate that the fine-tuning procedure does not degrade performance on sequences with different GC content or repeat structure compared to mitochondria.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The claim that TraceBind reduces false positives while maintaining high sensitivity compared to existing methods
- **Evidence pointer** Results section "TraceBind enables high-fidelity footprinting across datasets"; Figure 3f, 3i
- **Concern** The benchmarking results are described in text but the actual numbers are not provided. The claim of "reducing false positive rate by several orders of magnitude" compared to TOBIAS, HINT-ATAC, and PRINT is striking but cannot be evaluated without the underlying data. Furthermore, the choice of benchmarks and the criteria for defining true/false positives need clarification. For the naked DNA control, it is stated that no true binding events are expected, but the text does not specify how many false positives were detected by each method or how sensitivity was computed in the absence of ground truth.
- **Why it matters** The central performance claim of the manuscript is that TraceBind substantially improves specificity. Without quantitative results, this claim is not verifiable. The magnitude of improvement (e.g., ">60 fold" reduction in false positives) is impressive but requires statistical context, such as confidence intervals and the range across datasets.
- **Resolution test** Provide the full benchmarking results, including ROC/PR curves, AUROC/AUPR values with confidence intervals, and the number of true/false positives for each method across all datasets. Clarify how sensitivity was defined for the naked DNA control and how the trade-off between sensitivity and specificity was handled.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that TraceBind enables improved downstream single-cell analyses, including transcription factor activity inference and cell age prediction
- **Evidence pointer** Results section "TraceBind improves TF regulatory analysis and cell age prediction"; Figure 5
- **Concern** The improvements in chromVAR and Epitrace are presented as qualitative observations (e.g., "age-associated upregulation of AP-1 family members") without quantitative metrics. For the chromVAR analysis, it is unclear how the footprint-refined results were compared to standard results beyond visual inspection. For Epitrace, the claim of "much stronger monotonic trend" is not supported by specific numbers, such as correlation coefficients or prediction accuracy. The comparison with random DML subsets is mentioned but the results are not described.
- **Why it matters** The biological applications are a key selling point of the manuscript, demonstrating that improved footprinting translates to meaningful biological insights. Without quantitative comparisons, it is difficult to assess whether the improvements are substantial or marginal.
- **Resolution test** Provide quantitative metrics for the chromVAR comparison, such as the number of TFs with significantly changed activity or the correlation between biological replicates. For Epitrace, report the correlation between predicted and actual ages, the mean absolute error, and the statistical significance of the improvement over baseline methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that the Cauchy Combination Method is appropriate for combining p-values across different window sizes
- **Evidence pointer** Methods section "Computation of p-values and effect sizes"
- **Concern** The Cauchy combination method is typically used for combining p-values from dependent tests, but the manuscript does not justify its use here or discuss its properties in the context of spatially correlated genomic tests. The choice of the exponential decay function for weights is also not motivated. It is unclear whether the method controls the type I error rate appropriately under the spatial dependence structure of ATAC-seq data.
- **Why it matters** The statistical validity of the footprint detection depends on the p-value combination method. If the method is not well-calibrated, the reported FDR control may be inaccurate, leading to inflated false positives or reduced power.
- **Resolution test** Provide simulations or theoretical justification demonstrating that the Cauchy combination method controls the FDR under the specific dependence structure of ATAC-seq insertion data. Compare the empirical FDR against the nominal level across a range of scenarios.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "sequence-dependent Tn5 cleavage bias" is used without defining what "sequence-dependent" means in this context. It would be clearer to specify that the bias depends on the local DNA sequence context around the cleavage site.
- **Required correction** Rephrase to "sequence-context-dependent Tn5 cleavage bias" or provide a brief definition.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Fine-tuning PRINT with mitochondrial Tn5 reads"
- **Evidence pointer** Methods section
- **Issue** The hyperparameter optimization is described as "optimized using the validation set" but no details are given on the hyperparameter search space, the number of trials, or the final hyperparameter values. This limits reproducibility.
- **Required correction** Provide the full list of hyperparameters and their final values, or state that the code will be made available with these details.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, "TraceBind captures footprint loss with nucleosome depletion"
- **Evidence pointer** Figure 4b
- **Issue** The text states that effect sizes for nucleosome footprints decrease with depletion, but the statistical test used is not described. It is unclear whether the comparison is paired or unpaired and whether multiple testing correction was applied.
- **Required correction** Specify the statistical test used and whether adjustments for multiple comparisons were made.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Footprinting and DNA models show complementary regulatory signals"
- **Evidence pointer** Figure 6d
- **Issue** The chi-squared test for the 2x2 contingency table is mentioned, but the construction of the table is not fully described. Specifically, it is unclear how "high" versus "low" Decatur attribution and "presence" versus "absence" of footprints were defined.
- **Required correction** Provide the exact thresholds used to define high/low attribution and significant/non-significant footprints.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Estimating cross-sample Tn5 bias from mitochondrial reads"
- **Evidence pointer** Methods section
- **Issue** The formula for Tn5 bias is described as "fold enrichment of insertion count at each position relative to the average count across a local window," but the window size is not specified. It is also unclear whether the average is computed over the same window for all positions or a sliding window.
- **Required correction** Specify the window size and the exact formula used.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The statement that "footprinting provides complementary regulatory information beyond what can be inferred from DNA sequence alone" is an important claim, but the text does not discuss potential confounding factors, such as the influence of chromatin accessibility on both footprinting and sequence model predictions.
- **Required correction** Add a brief discussion of potential confounders and how the analysis controls for them.

## Risk / unsupported claims
- The claim that Tn5 bias varies "substantially" across samples is supported by correlation values in Figure 1, but the actual range of correlations and the number of samples with low correlations are not stated in the text.
- The claim that TraceBind "reduces false positives while maintaining high sensitivity" is not quantitatively supported in the text; the specific numbers are only referenced in figures.
- The claim that footprint-refined chromVAR reveals "age-associated upregulation of AP-1 family members" is presented without statistical significance values or effect sizes.
- The claim that TraceBind-derived sub-peak features enable "more accurate cell age estimation" is not supported by quantitative metrics in the text.
- The claim that "around 26% of the footprints identified by TraceBind are new and not supported by either technology" is presented without confidence intervals or a discussion of potential false positives in this subset.
- The claim that the fine-tuned model provides "accurate estimation of nucleotide-resolution cleavage propensity within each sample" is not directly validated on nuclear DNA.