## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, conclusions, and methods
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors propose a likelihood-based framework using an over-dispersed binomial distribution to benchmark sequence-to-affinity models for transcription factor binding against allele-specific ChIP-seq data. They introduce PyProBound, a reimplementation of ProBound, and demonstrate improved TF binding models by accounting for DNA fragmentation bias. They also show de novo motif discovery from allele-aware ChIP-seq counts.
- **Visible evidence base** Abstract, full results section, discussion, conclusions, and methods. Figures referenced but not provided. Supplementary figures referenced but not provided.
- **Missing materials affecting confidence** Figures 1-5 and Supplemental Figures S1-S4 are referenced but not included. Raw data, code outputs, and detailed parameter settings for model training are not fully described. Statistical test details beyond p-values are incomplete.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting framework for benchmarking TF binding models using allele-specific data, which addresses a real limitation in current approaches. The introduction of PyProBound as a flexible, extensible tool is valuable. However, the evidence as presented is incomplete. Key figures are missing, making it impossible to evaluate the magnitude and robustness of the reported effects. The statistical framework is described but not fully validated. The claim of de novo motif discovery is intriguing but the comparison to existing methods is limited to a single correlation metric. The manuscript would benefit from clearer presentation of the model comparison methodology and more rigorous benchmarking against existing tools.
- **Who would be interested in the results, and why** Computational biologists developing TF binding models, researchers studying regulatory genomics and allele-specific effects, and bioinformaticians working on ChIP-seq analysis. The PyProBound tool would be of interest to the broader genomics community. The benchmarking framework could be adopted by others evaluating sequence-to-affinity models.
- **Major strengths** The conceptual advance of using aggregated allele-specific evidence rather than requiring per-SNV significance is sound and potentially impactful. The explicit modeling of DNA fragmentation bias is a thoughtful contribution. PyProBound as an open-source, extensible tool addresses a practical need. The use of multiple data types (ChIP-seq, ChIP-exo, CUT&Tag) is commendable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate to high; the likelihood framework is novel but builds on existing beta-binomial approaches. Scientific importance is significant for the TF binding modeling community but may be narrower than broad biological interest. Interdisciplinary readership is limited to computational genomics. Technical soundness cannot be fully assessed without figures and detailed methods. Readability for nonspecialists is adequate but assumes familiarity with TF binding models and ChIP-seq.
- **Recommendation posture** Currently not established from the provided evidence. The core ideas are promising, but the missing figures and incomplete methodological details prevent a full evaluation. Supportive if technical concerns are resolved and evidence is provided.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that the likelihood framework can aggregate evidence for allelic preference across the genome and systematically compare predictive performance of multiple binding models.
- **Evidence pointer** Figures 2, 3, 4, and Supplemental Figures S1-S3 are referenced but not provided
- **Concern** The central results supporting the main claims are presented only through figure references. Without the actual figures, it is impossible to assess the magnitude of the reported effects, the variability across models, or the statistical robustness of the comparisons. For example, the claim that the MotifCentral model predicts the direction of ASB across a 1,000-fold range in predicted affinity cannot be verified. Similarly, the comparison of model performance in Figure 4 and the de novo motif discovery results in Figure 5 are not evaluable.
- **Why it matters** The manuscript's core contribution is the demonstration that the proposed framework works. Without visual evidence of the results, the claims are unverifiable and the scientific case is not established.
- **Resolution test** Provide all referenced figures with clear axis labels, error bars or confidence intervals, and statistical annotations. Ensure that the figures directly support the claims made in the text.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The authors state that the beta-binomial likelihood function can be used to benchmark models and that the overdispersion parameter provides a measure of model performance.
- **Evidence pointer** Methods section, "Beta-binomial model of genome-wide allelic effects on the binding affinity"
- **Concern** The statistical properties of the proposed likelihood framework are not fully characterized. The authors do not demonstrate that the likelihood ratio or difference in log-likelihood between models is a reliable and calibrated measure of model quality. There is no discussion of how the overdispersion parameter interacts with model misspecification, nor is there a simulation study or ground-truth validation showing that the framework correctly identifies better models. The choice of the beta-binomial distribution is motivated by prior use in AlleleDB, but its suitability for this new purpose is not justified.
- **Why it matters** The framework is proposed as a general benchmarking tool. Without validation of its statistical behavior, users cannot trust that differences in log-likelihood reflect true differences in predictive performance.
- **Resolution test** Add a simulation study or use a held-out dataset with known ground truth to demonstrate that the likelihood framework correctly ranks models of known quality. Discuss the calibration of the log-likelihood differences and the behavior of the overdispersion parameter under model misspecification.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model comparison rigor
- **Claim pointer** The authors claim that PyProBound models trained with fragmentation bias modeling outperform those trained without, and that CUT&Tag-derived models outperform ChIP-based approaches.
- **Evidence pointer** Results section, "Taking DNA fragmentation bias into account when analyzing ChIP-seq data yields superior sequence-to-affinity models"; Figure 4 referenced but not provided
- **Concern** The comparison of models is described only qualitatively. There is no description of how models were selected, whether hyperparameters were optimized fairly across methods, or whether the differences are statistically significant beyond the reported p-values. The comparison to "motif models for CTCF from other resources" is vague; specific resources and model versions are not named. The claim that CUT&Tag-derived models outperform ChIP-based approaches is based on a single TF and may not generalize.
- **Why it matters** The superiority of the proposed approach is a key selling point. Without a rigorous and transparent comparison, the claim is not convincing.
- **Resolution test** Provide a detailed table of all models compared, including training data, hyperparameters, and performance metrics. Use statistical tests that account for multiple comparisons. Discuss potential confounders such as differences in data quality or depth across assays.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** De novo motif discovery validation
- **Claim pointer** The authors claim that the likelihood framework can be leveraged for de novo motif discovery from allele-aware ChIP-seq counts, and that the resulting model shows excellent agreement with the MotifCentral model (Pearson r = 0.94).
- **Evidence pointer** Results section, "De novo motif discovery from allele-aware ChIP-seq counts"; Figure 5 referenced but not provided
- **Concern** The de novo motif discovery result is presented as a single correlation coefficient. This is insufficient to establish that the discovered motif is biologically meaningful or that the method is generally applicable. The authors do not compare against existing motif discovery tools, do not report the recovered motif as a sequence logo or position weight matrix, and do not assess whether the motif is found at expected genomic locations. The correlation with an existing model is a weak validation, as it could be driven by a few positions or by the overall G/C content.
- **Why it matters** De novo motif discovery is a claimed capability of the framework. Without proper validation, this claim is not supported.
- **Resolution test** Provide the discovered motif as a sequence logo, compare against known CTCF motifs from multiple databases, and benchmark against at least one established motif discovery tool. Report sensitivity and specificity of motif recovery in a simulation or on a held-out dataset.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "We show that a likelihood function based on an over-dispersed binomial distribution can aggregate evidence for allelic preference across the genome"
- **Issue** The abstract states the likelihood function "can aggregate evidence" but does not specify the input data requirements or the computational cost. A brief mention of scalability would help readers assess practical utility.
- **Required correction** Add one sentence in the abstract or introduction noting the computational feasibility of the approach on genome-wide data.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods, "In vivo binding data used for de novo motif discovery using ProBound"
- **Issue** The methods describe downloading and processing data but do not specify the exact versions of tools (e.g., BBMerge, BBMap, samtools) or the reference genome build used for read mapping. This hampers reproducibility.
- **Required correction** List software versions and reference genome build in the methods or a supplementary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results
- **Evidence pointer** Results, "Prediction of CTCF allele-specific binding events using sequence-to-affinity models"
- **Issue** The text reports a Wilcoxon test p-value but does not state the number of bootstrap replicates or the exact test used (one-sided vs. two-sided). This makes the statistical claim difficult to interpret.
- **Required correction** Specify the number of bootstrap replicates, the test direction, and whether multiple testing corrections were applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, "models derived from in vivo data in an allele-agnostic manner generally perform better than those derived from in vitro binding data"
- **Issue** The discussion attributes the superior performance of in vivo models to the inclusion of co-factor effects, but this is speculative. The authors do not test this hypothesis directly.
- **Required correction** Soften the claim or add a sentence acknowledging alternative explanations, such as differences in data quality or model training procedures.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Conclusions
- **Evidence pointer** Conclusions, "our likelihood framework could again provide an objective an unbiased metric"
- **Issue** The conclusion states the framework is "unbiased," but no evidence is provided to support this strong claim. Bias could arise from the choice of background model or the aggregation procedure.
- **Required correction** Replace "unbiased" with "a principled" or "a statistically motivated" metric, or provide evidence for unbiasedness.

## Risk / unsupported claims
- The claim that the likelihood framework provides an "unbiased" metric is unsupported.
- The claim that CUT&Tag-derived models outperform ChIP-based approaches is based on a single TF and limited evidence.
- The claim of "excellent agreement" with the MotifCentral model is based solely on a Pearson correlation, which is insufficient.
- The claim that the de novo motif discovery approach is novel is not fully substantiated; the authors do not compare against existing methods that might use similar strategies.
- The statement that "models trained on in vivo binding data outperformed those trained on in vitro data" is presented as a general conclusion but is only demonstrated for CTCF.
- The assertion that the fragmentation bias is "straightforward to implement" is not supported by a detailed description of the implementation complexity.