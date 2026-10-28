## Review setup
- **Input scope** Full manuscript text including abstract, background, results, discussion, conclusions, methods, and declarations
- **Assessment boundary** Scientific validity, methodological soundness, evidence quality, and interpretation of results as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present a novel computational approach using deep convolutional neural networks trained on differential CTCF ChIP-seq peak data (wild-type versus individual zinc finger mutants) to infer the DNA binding preferences of individual CTCF zinc fingers. They report identification of known motifs for ZFs 3-11 and novel putative motifs for ZF1 (GAGCCA) and ZF2 (ATT), supported by HT-SELEX re-analysis, CTCF-s comparison, and peak strength correlations.
- **Visible evidence base** Abstract, full background, results narrative, discussion, conclusions, methods, data availability statement, competing interests, funding, author contributions, acknowledgements
- **Missing materials affecting confidence** Figures 1-3 and Supplemental Figures 1-7 are referenced but not provided; Supplemental Files 1-3 are referenced but not provided; Supplemental Table 1 is referenced but not provided; Supporting Website content is referenced but not accessible; no quantitative performance metrics (e.g., AUPRC values) are reported in the text; no model architecture details beyond layer counts; no hyperparameter search results; no code or data files

## Reviewer

- **Overall assessment** This manuscript presents a conceptually interesting approach to a genuinely difficult problem: deconvolving the individual DNA binding preferences of multiple zinc finger domains within a multi-ZF transcription factor. The core idea, training a neural network on differential binding between wild-type and mutant CTCF and interpreting the model to recover domain-specific motifs, is creative and represents a meaningful methodological advance over prior approaches that relied on de novo motif discovery within mutant peak sets. The authors provide multiple lines of supporting evidence for their novel ZF1 and ZF2 motif predictions, including HT-SELEX enrichment, CTCF-s isoform comparisons, and peak strength correlations. However, the manuscript as provided has several significant limitations that prevent full evaluation. The absence of all figures and supplemental materials makes it impossible to assess the quality of the TF-MoDISco motifs, the model performance, or the statistical analyses. The methods section lacks critical details about model evaluation, cross-validation, and the interpretation pipeline. The authors acknowledge that direct experimental validation (e.g., EMSA) of ZF1-ZF2 binding to the predicted motifs has not been performed, which is a substantial gap given the strength of the claims. The causal interpretation, that the discovered downstream motif is bound by ZF1, is supported by correlational and indirect evidence but not definitively established. The writing is generally clear and well-organized, though some sections are dense and would benefit from additional explanation for a broader readership. Overall, the approach is promising and the findings are potentially important, but the case is not fully established from the provided evidence.

- **Who would be interested in the results, and why** Researchers studying transcription factor DNA binding specificity, particularly those focused on multi-ZF proteins and the relationship between protein structure and DNA recognition. Computational biologists developing methods for interpreting neural network models of genomic data will find the approach of interest. Investigators studying CTCF biology, chromatin architecture, and 3D genome organization would be interested in the potential new binding motifs and their implications for CTCF function. The methodological framework could also be of interest to researchers working on other multi-domain DNA binding proteins where individual domain specificities are unknown.

- **Major strengths** The approach directly addresses a significant gap in the field by attempting to identify binding preferences of individual ZFs within a multi-ZF TF in vivo, rather than relying on in vitro assays of isolated domains. The use of differential peak prediction between wild-type and mutant datasets is a clever design that leverages the natural experimental contrast. The authors provide multiple independent lines of evidence supporting their novel motif predictions, including HT-SELEX enrichment analysis, CTCF-s isoform comparisons, and peak strength correlations. The approach is generalizable and could be applied to other multi-ZF TFs with available mutant ChIP-seq data. The authors are appropriately cautious in some of their interpretations and acknowledge the need for experimental validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that their neural network models had "good performance" and that TF-MoDISco identified motifs for all ZFs, including novel motifs for ZF1 and ZF2.
- **Evidence pointer** Results section, Figure 1, Figure 2, location not provided
- **Concern** All figures and supplemental materials are referenced but not included in the provided manuscript. This includes the TF-MoDISco motif visualizations (Figure 1), the performance comparisons (Figure 2a), the motif comparisons (Figure 2b), the HT-SELEX enrichment results (Figure 3b), the CTCF-s comparison (Figure 3c), and all supplemental figures and files. Without these materials, it is impossible to evaluate the quality of the identified motifs, the actual performance metrics of the neural networks, the statistical significance of the enrichment analyses, or the validity of the motif comparisons.
- **Why it matters** The core claims of the manuscript rest entirely on the quality of the motif identifications and the statistical analyses presented in the figures. The text alone provides insufficient quantitative detail to assess whether the models performed well, whether the TF-MoDISco motifs are of high quality, or whether the supporting analyses are statistically robust. The reader cannot verify any of the central findings.
- **Resolution test** Provide all figures and supplemental materials with appropriate resolution and detail. Include quantitative performance metrics (e.g., AUPRC values with confidence intervals) for each model. Show the TF-MoDISco motifs with sequence logos and supporting seqlet counts. Present the full statistical results for the HT-SELEX enrichment, CTCF-s comparison, and peak strength analyses, including effect sizes and confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors state that the discovered downstream GAGCCA motif "may be bound by ZF 1" and that the ATT motif represents a "putative weak interaction between ZF 2 and the sequence ATT." They further claim that the presence of the ZF1 motif is associated with CTCF peak strength.
- **Evidence pointer** Results section, Discussion section, location not provided
- **Concern** The causal claim that ZF1 binds the GAGCCA motif and ZF2 binds the ATT motif is inferred from the neural network interpretation and indirect supporting evidence, but no direct experimental validation is provided. The authors acknowledge this limitation but still frame the findings as "putative binding preferences." The correlational evidence (HT-SELEX enrichment, CTCF-s comparison, peak strength correlation) is suggestive but does not establish direct physical interaction between specific ZFs and the predicted motifs. The possibility remains that the motifs are recognized by other ZFs in a context-dependent manner or that the model has learned indirect sequence features.
- **Why it matters** The central contribution of the manuscript is the identification of novel binding preferences for ZF1 and ZF2. Without direct experimental validation, the claims remain speculative. The distinction between a model-derived hypothesis and an experimentally validated finding is critical for the scientific community, as subsequent studies may build on these results. The strength of the language should match the strength of the evidence.
- **Resolution test** Perform direct binding assays (e.g., EMSA or in vitro binding assays) with purified CTCF proteins containing wild-type or mutant ZF1 and ZF2 and DNA probes containing the predicted motifs. Alternatively, perform targeted mutagenesis of the predicted motifs in vivo and assess effects on CTCF binding. If direct validation is not feasible, temper the language to clearly indicate that these are model-generated hypotheses requiring experimental confirmation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor
- **Claim pointer** The authors describe their neural network architecture as "three convolutional layers" with specific filter sizes and pooling, and state that hyperparameters were "selected after evaluating performance of multiple sets of hyperparameters on the validation set."
- **Evidence pointer** Methods section, location not provided
- **Concern** The methods section lacks critical details about the model training and evaluation procedure. No information is provided about the number of training epochs, the learning rate schedule, the batch size rationale, the class weighting scheme, or the specific hyperparameter values tested. The early stopping criterion is described but no results are shown. The pre-training procedure is mentioned but not detailed. The evaluation metric (AUPRC) is mentioned but no values are reported. The train-validation-test split is described but the sizes of these sets are not given. The potential for data leakage between training and test sets is not addressed.
- **Why it matters** Reproducibility is a fundamental requirement for computational studies. The lack of detail makes it impossible for other researchers to replicate the models or assess whether the reported performance is robust. The choice of hyperparameters can significantly affect model performance and the resulting interpretations. Without this information, the reliability of the findings cannot be fully assessed.
- **Resolution test** Provide complete details of the model architecture, training procedure, hyperparameter search, and evaluation in the methods section or as supplemental material. Report the final hyperparameter values used for each model. Provide the AUPRC values for each model on the test set. Describe the data splitting procedure in detail and address potential data leakage concerns.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report several statistical comparisons, including the HT-SELEX enrichment analysis (p = 1.17 x 10^-245), the CTCF-s comparison (p = 4.00 x 10^-6), and the peak strength correlations (p = 3.24 x 10^-106 for the default cutoff).
- **Evidence pointer** Results section, Figure 3, location not provided
- **Concern** The statistical methods for these analyses are not described in sufficient detail. For the HT-SELEX enrichment, the authors state they used a Wilcoxon rank-sum test but do not describe how the scores were calculated, how the background was defined, or how multiple testing was addressed. For the CTCF-s comparison, the details of the overlap analysis and the statistical test are not provided. For the peak strength correlations, the authors report p-values but do not describe the effect sizes, the correlation coefficients, or the statistical model used. The Bonferroni correction is mentioned but the number of comparisons is not specified.
- **Why it matters** The supporting evidence for the novel motifs relies heavily on these statistical analyses. Without proper description of the methods, the reader cannot assess whether the analyses are appropriate, whether the assumptions are met, or whether the reported p-values are reliable. The extremely small p-values reported (e.g., 10^-245) may indicate issues with the statistical model or the sample size.
- **Resolution test** Provide complete descriptions of all statistical analyses, including the exact tests used, the variables compared, the handling of multiple testing, and the effect sizes with confidence intervals. For the HT-SELEX analysis, describe the scoring method, the background model, and the number of reads in each cycle. For the peak strength analysis, report the correlation coefficients and the sample sizes.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence interpretation
- **Claim pointer** The authors state that the presence of the ZF1 motif is associated with CTCF peak strength and that this relationship is consistent across tissues (p = 3.24 x 10^-106 for the default cutoff, with similar results for liver and heart).
- **Evidence pointer** Results section, Supplemental Figure 7, location not provided
- **Concern** The interpretation of the peak strength correlation is not straightforward. The authors compare peaks with the core motif and the downstream motif to peaks with only the core motif, but the direction of causality is unclear. It is possible that stronger peaks simply have more reads and therefore are more likely to contain a motif by chance. The authors do not address this potential confound. Additionally, the relationship between motif presence and peak strength could be influenced by other factors, such as chromatin accessibility or cofactor binding.
- **Why it matters** The peak strength correlation is presented as supporting evidence for the functional relevance of the downstream motif. If this correlation is confounded or spurious, the support for the motif's importance is weakened. The interpretation of this analysis should be more cautious and should address potential alternative explanations.
- **Resolution test** Perform additional analyses to control for potential confounds, such as matching peaks by read count or using a regression model that includes other relevant features. Discuss the potential for reverse causality and address how the analysis design mitigates this concern. Consider using a more direct measure of binding affinity, such as ChIP-seq signal normalized by peak width.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Background
- **Evidence pointer** Abstract, Background section, location not provided
- **Issue** The abstract states that the authors "identified a GAG binding motif for ZF1 and a weak ATT binding motif for ZF2," but the results section describes the ZF1 motif as GAGCCA. The abstract should be consistent with the full results.
- **Required correction** Revise the abstract to state "GAGCCA" instead of "GAG" for the ZF1 motif, or clarify that GAG is the core of the GAGCCA motif.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, Discussion
- **Evidence pointer** Methods section, Discussion section, location not provided
- **Issue** The authors mention that the R339W mutant for ZF3 was excluded from model training but do not explain why. The discussion mentions limitations of the approach but does not address the potential impact of the R339W exclusion on the interpretation of ZF3 results.
- **Required correction** Provide a brief explanation for excluding the R339W mutant and discuss any potential implications for the ZF3 findings.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section, location not provided
- **Issue** The methods state that the authors used "recently recommended methods for filtering reads and identifying reproducible peaks" and cite references, but the specific versions of tools and parameters are not fully described. The AQUAS pipeline is mentioned but the specific version and configuration are not given.
- **Required correction** Provide the specific versions of all software tools used and the complete parameter settings for the AQUAS pipeline and other analysis steps.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, Discussion
- **Evidence pointer** Results section, Discussion section, location not provided
- **Issue** The authors note that the neural network for ZF8 placed higher importance on downstream nucleotides of the upstream motif but do not provide a biological interpretation for this observation. The discussion of ZF8-specific findings is limited.
- **Required correction** Add a brief discussion of the potential biological significance of the ZF8-specific pattern or acknowledge that the significance is unclear.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods
- **Evidence pointer** Methods section, location not provided
- **Issue** The description of the TF-MoDISco parameters is incomplete. The authors state they used "seqlet FDR threshold = 0.2" and other settings, but do not describe how these parameters were chosen or whether the results are sensitive to these choices.
- **Required correction** Provide a rationale for the chosen TF-MoDISco parameters and, if possible, a sensitivity analysis showing that the identified motifs are robust to parameter variations.

- **Technical failings that need to be addressed before the case is established** The absence of all figures and supplemental materials is the most critical technical failing, as the core evidence cannot be evaluated. The lack of quantitative performance metrics for the neural network models prevents assessment of model quality. The incomplete description of the statistical methods for the supporting analyses (HT-SELEX, CTCF-s, peak strength) undermines confidence in the reported p-values. The absence of direct experimental validation for the ZF1 and ZF2 motif predictions means the central claims remain unverified. The potential for confounding in the peak strength analysis is not addressed.

- **Assessment against Nature-style criteria** Originality: The approach of using differential binding between wild-type and mutant TF ChIP-seq data with neural network interpretation is novel and represents a creative methodological contribution. The application to CTCF ZFs 1-2, which have not been previously characterized, addresses a genuine gap. Scientific importance: The findings have potential importance for understanding CTCF biology and for the broader field of multi-ZF TF DNA recognition. However, the importance is tempered by the lack of experimental validation and the indirect nature of the supporting evidence. Interdisciplinary readership: The work bridges computational biology, genomics, and molecular biology, and the findings could interest researchers across these fields. The approach could be applied to other TFs, increasing its potential impact. Technical soundness: The methodological framework is sound in principle, but the incomplete description of methods and the absence of figures prevent full assessment. The statistical analyses appear appropriate but are not described in sufficient detail. Readability for nonspecialists: The manuscript is generally well-written and the logic is clear, but some sections are dense and assume familiarity with neural network interpretation methods and ChIP-seq analysis. The abstract and introduction are accessible, but the methods and results would benefit from additional context for nonspecialist readers.

- **Recommendation posture** Supportive if technical concerns are resolved. The core approach is innovative and the findings are potentially significant, but the manuscript in its current form does not provide sufficient evidence to fully establish the claims. The authors must provide all figures and supplemental materials, complete the methods descriptions, address the potential confounding in the peak strength analysis, and either provide direct experimental validation or substantially temper the language of the claims. If these concerns are addressed, the manuscript could make a valuable contribution to the field.

## Risk / unsupported claims
- The claim that ZF1 binds the GAGCCA motif is not directly supported by experimental evidence and relies on model interpretation and indirect correlations.
- The claim that ZF2 binds the ATT motif is described as "weak" but the evidence for even a weak interaction is indirect.
- The claim that the neural network models had "good performance" cannot be evaluated without quantitative metrics.
- The claim that the presence of the ZF1 motif is associated with CTCF peak strength may be confounded by read depth or other factors not addressed in the analysis.
- The claim that the approach can be applied to any TF with multiple DBDs is plausible but not demonstrated beyond the CTCF case.
- The claim of providing "unprecedently comprehensive understanding" of CTCF ZF binding preferences is overstated given the lack of experimental validation for ZF1 and ZF2.
- The statement that the discovered downstream motif "has been shown to bind CTCF in a previous EMSA study" is presented as supporting evidence, but the specific study and the context of the binding are not described in sufficient detail to assess relevance.