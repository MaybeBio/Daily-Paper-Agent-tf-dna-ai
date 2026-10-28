## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and evidence presented in the manuscript; no assessment of code functionality or web server availability beyond what is described
- **Shared manuscript claim summary** The authors present TFTF, a multimodal deep language model integrating DNA sequence and multiomics signals (histone modifications, chromatin accessibility) for transcription factor binding site prediction. They claim state-of-the-art accuracy, first-of-kind capability for genome-wide detection in experimentally unexplored biosamples, threshold-free operation, and interpretability via attention analysis.
- **Visible evidence base** Main text, figures referenced (Fig. 1a-e, 2a-d, 3a-c, 4a-c, 5a-b, 6a-c), supplementary figures referenced (S1a-d, S2a-d, S3a-c, S4a-b), supplementary tables referenced (S1, S2)
- **Missing materials affecting confidence** Supplementary figures and tables not provided; figure contents not visible; exact hyperparameter values for grid search not reported; details of DNABERT comparison setup partially described; web server functionality not assessed

## Reviewer

- **Overall assessment** The manuscript addresses a relevant problem in regulatory genomics: predicting TFBS in cell types and species without direct experimental data. The integration of multiomics signals with a transformer architecture is a reasonable direction, and the reported improvements over DNABERT are notable. However, the evidence as presented has several gaps that prevent full evaluation of the claims. Key concerns include incomplete reporting of experimental setup, unclear statistical comparisons, potential data leakage in the cross-validation scheme, and insufficient detail on the attention analysis methodology. The claims of "first" and "state-of-the-art" require more careful benchmarking against a broader set of baselines. The manuscript is potentially of interest to computational biologists and regulatory genomics researchers, but the current evidence base is insufficient to fully establish the central claims.

- **Who would be interested in the results, and why** Computational biologists developing deep learning methods for regulatory genomics; experimental biologists seeking in silico tools for TFBS prediction in understudied cell types; researchers working on cross-species regulatory element prediction; bioinformaticians interested in multimodal integration of epigenomic data.

- **Major strengths**
  1. The problem addressed is practically important: predicting TFBS in unexplored biosamples is a real bottleneck in regulatory genomics.
  2. The multimodal architecture integrating DNA sequence with multiomics signals is a sensible design choice, and the Balancer layer is a novel contribution.
  3. The evaluation includes multiple scenarios: in-cell prediction, cross-cell prediction, genome-wide scanning, and cross-species transfer.
  4. The attention analysis provides some interpretability, which is valuable for trust in deep learning models.
  5. The inclusion of ChIP-qPCR validation for predicted peaks strengthens the practical relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "TFTF showed 5.66%–14.35% improvement for each cell line... and achieved an impressive F1-score of 94.05%... This marked a 9.97% increase in overall performance when compared to DNABERT"
- **Evidence pointer** Section 3.1, Fig. 1c, Supplementary Fig. S1b
- **Concern** The cross-validation scheme is described as "modified 10-fold cross-validation" but the exact procedure is not fully specified. It is unclear whether the random splitting was performed per cell line or across all cell lines jointly, and whether the same folds were used for both TFTF and DNABERT. If the data from the same cell line appears in both training and testing sets across different folds, this could lead to inflated performance estimates. Additionally, the statistical significance of the reported improvements is not established; no confidence intervals or significance tests are reported for the F1-score comparisons.
- **Why it matters** Without a clearly specified and statistically rigorous evaluation protocol, the claimed improvements over DNABERT cannot be reliably assessed. Data leakage or improper cross-validation would invalidate the central performance claims.
- **Resolution test** Provide a detailed description of the cross-validation procedure, including how folds were constructed, whether cell lines were kept separate, and whether the same folds were used for all models. Report confidence intervals or perform significance testing (e.g., paired bootstrap or Wilcoxon test across cell lines) for the F1-score comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "TFTF is also the first approach to accurately perform genome-wide detection for cell-type and species-specific TFBS in experimentally unexplored biosamples"
- **Evidence pointer** Section 1, Section 3.2, Section 3.3
- **Concern** The claim of being "the first" is strong and requires a comprehensive comparison against existing methods beyond DNABERT. The manuscript compares against DNABERT and the ENCODE-DREAM Challenge champion, but does not benchmark against other relevant methods such as DeepSEA, Basenji, Enformer, or other recent transformer-based models for regulatory genomics. The claim of "first" is not substantiated by a thorough literature survey or benchmarking.
- **Why it matters** The novelty claim is central to the manuscript's contribution. If other methods already achieve similar cross-cell or cross-species prediction, the claim of being "first" is inaccurate and the contribution is diminished.
- **Resolution test** Expand the benchmarking to include a broader set of state-of-the-art methods for TFBS prediction. Provide a literature review demonstrating that no prior method has achieved cross-cell and cross-species TFBS prediction with comparable accuracy. Alternatively, soften the claim to "to our knowledge" and support it with a systematic comparison.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Compared to peak calling methods, TFTF consistently discovers true TFBS in threshold tuning-free way, with higher recalled rates"
- **Evidence pointer** Section 3.4, Fig. 4a
- **Concern** The comparison with peak calling methods (e.g., MACS) is not a like-for-like comparison. Peak callers operate on raw ChIP-seq data, while TFTF operates on pre-defined peak regions. The claim that TFTF is "threshold tuning-free" is misleading because the model still requires a confidence score threshold for classification, and the manuscript itself describes setting confidence score cut-offs for prioritization. The ChIP-qPCR validation was performed on only 19 randomly selected IDR-discarded peaks, which is a very small sample size for drawing conclusions about the overall false positive rate.
- **Why it matters** The comparison with peak callers is conceptually different and may not be appropriate. The "threshold tuning-free" claim is contradicted by the manuscript's own use of confidence score cut-offs. The small validation sample size limits the strength of the conclusions about false positives.
- **Resolution test** Clarify the comparison with peak callers, specifying what exactly is being compared and why this comparison is appropriate. Revise the "threshold tuning-free" claim to accurately reflect the use of confidence scores. Increase the number of ChIP-qPCR validated peaks or provide additional validation evidence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "We provide a web server (https://tftf.ibreed.cn/) for users to utilize TFTF model. Users can train TFTF model and discover TFBS with their own data."
- **Evidence pointer** Availability and implementation section, Code availability section
- **Concern** The manuscript states that a web server is available, but does not provide details on the implementation, the underlying code repository, or the specific instructions for training and using the model. The URL is provided, but the manuscript does not describe the software dependencies, the model checkpoint availability, or the data processing pipeline required to reproduce the results.
- **Why it matters** Reproducibility is a core requirement for computational biology methods. Without access to the code, model weights, and detailed usage instructions, other researchers cannot validate or build upon the reported results.
- **Resolution test** Provide a link to a public code repository (e.g., GitHub) with the full implementation, model checkpoints, and a detailed README describing how to reproduce the reported results. Include information on software dependencies and hardware requirements.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "TFTF can benefit from the integration of broader and more diverse data for improvement and can be applied to multiple epigenetic scenarios."
- **Evidence pointer** Section 3.2, Section 3.6
- **Concern** The manuscript demonstrates cross-species transfer from human to mouse, but only for one mouse cell line (Bruce4). The claim of broad applicability to "multiple epigenetic scenarios" is not fully supported by the experiments presented. The evaluation of different TF types is limited to CTCF and EZH2. The manuscript does not systematically explore how performance varies across different types of TFs, different chromatin contexts, or different types of multiomics inputs.
- **Why it matters** The generalizability claims are important for the practical utility of the method. Limited evaluation across TFs, cell types, and species weakens the case for broad applicability.
- **Resolution test** Expand the evaluation to include more TFs, more cell types, and more species. Systematically vary the multiomics inputs to demonstrate the method's flexibility and robustness.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1 Datasets
- **Evidence pointer** Section 2.1
- **Issue** The description of the negative dataset generation is somewhat unclear. The text states "randomly sampled from the human reference genome outside the marked regions, and at least 2 kb away from the boundary of the marked region" but does not specify whether the negative samples were matched for GC content or other genomic features. The manuscript later states "irrespective of their GC-content" in Section 3.1, which suggests GC matching was not performed, but this is not stated in the Methods.
- **Required correction** Clarify in the Methods whether negative samples were matched for any genomic features (e.g., GC content, mappability) and state the rationale for the chosen approach.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.1
- **Evidence pointer** Fig. 1c, Supplementary Fig. S1b
- **Issue** The reported improvements are given as ranges (e.g., "5.66%–14.35%") without indicating the variability across cell lines or the statistical significance of these differences. The P-value for the overall comparison is reported, but individual cell line comparisons are not assessed.
- **Required correction** Report the distribution of performance across cell lines (e.g., box plots or scatter plots) and provide statistical tests for the per-cell-line comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** Section 3.5
- **Evidence pointer** Fig. 5a-b, Supplementary Fig. S4a-b
- **Issue** The attention analysis is presented as evidence of interpretability, but the methodology for computing attention scores and the ASFC metric is not fully described. The text states "we quantified the amount of attention of each position by calculating its attention score" but does not specify how attention from multiple heads and layers is aggregated.
- **Required correction** Provide a detailed description of the attention score calculation, including how attention from different heads and layers is combined, and how the ASFC is computed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.3.1
- **Evidence pointer** Section 2.3.1
- **Issue** The hyperparameter tuning procedure is described as "grid search algorithm" but the specific hyperparameters tuned, the ranges explored, and the selection criteria are not reported.
- **Required correction** Report the hyperparameter search space, the final hyperparameter values, and the selection criteria used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.6
- **Evidence pointer** Fig. 6a-c
- **Issue** The cross-species evaluation is described as "transfer the model to other species" but the exact procedure is not clear. It is not specified whether the model is fine-tuned on mouse data or used directly without fine-tuning.
- **Required correction** Clarify whether the cross-species evaluation involves fine-tuning on the target species or zero-shot transfer.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** location not provided
- **Issue** The manuscript contains several typographical and grammatical errors (e.g., "benificial" in Section 3.2, "manually free way" in Section 3.4, inconsistent use of "cell-type" vs "cell type").
- **Required correction** Thorough proofreading of the manuscript for language and consistency.

## Risk / unsupported claims
- The claim of being "the first approach to accurately perform genome-wide detection for cell-type and species-specific TFBS in experimentally unexplored biosamples" is not fully supported by the evidence presented, as the comparison is limited to DNABERT and the ENCODE-DREAM Challenge champion.
- The claim that TFTF is "threshold tuning-free" is contradicted by the manuscript's own use of confidence score cut-offs for prioritization.
- The claim that TFTF "consistently discovers true TFBS" is based on a small ChIP-qPCR validation set (19 samples) and may not be generalizable.
- The claim of broad applicability to "multiple epigenetic scenarios" is not fully supported by the limited evaluation across TFs, cell types, and species.
- The statistical significance of the performance improvements over DNABERT is not established beyond a single overall P-value.
- The reproducibility of the method cannot be assessed without access to the code and detailed implementation instructions.

## Assessment against Nature-style criteria
- **Originality**: The integration of multiomics signals with a transformer architecture for TFBS prediction is a reasonable extension of existing work, and the Balancer layer is a novel component. However, the overall approach builds on well-established ideas in the field, and the novelty is incremental rather than transformative.
- **Scientific importance**: The problem of predicting TFBS in unexplored biosamples is important for regulatory genomics. The potential to reduce experimental burden is significant. However, the limited evaluation across TFs, cell types, and species tempers the immediate impact.
- **Interdisciplinary readership**: The work is primarily of interest to computational biologists and bioinformaticians. The methods and results are presented in a way that is accessible to this audience, but the broader biological significance could be more clearly articulated for a wider readership.
- **Technical soundness**: The technical approach is generally sound, but several concerns about the evaluation methodology, statistical rigor, and reproducibility need to be addressed. The cross-validation scheme is not fully specified, and the comparisons with baselines are limited.
- **Readability for nonspecialists**: The manuscript is written in a technical style that assumes familiarity with deep learning and epigenomics. The abstract and introduction provide some context, but the methods and results sections would be challenging for nonspecialists. The figures are referenced but not visible in the provided text, making it difficult to assess their clarity.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses a relevant problem and presents a plausible approach with promising results. However, the central claims of state-of-the-art performance, first-of-kind capability, and threshold-free operation require stronger evidence. The evaluation methodology needs to be clarified and expanded, and the reproducibility of the method needs to be ensured. If these concerns are adequately addressed, the manuscript could make a useful contribution to the field.