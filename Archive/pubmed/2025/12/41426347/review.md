## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methodology, experiments, results, conclusion) as provided
- **Assessment boundary** Scientific and technical evaluation of the presented framework, methodology, experimental design, and reported results
- **Shared manuscript claim summary** The authors propose Leonine, a framework that uses a DNA large language model (HyenaDNA) fine-tuned with multimodal cell context (cell type, gene expression, promoter sequence) to generate cell-type-specific enhancer sequences. They report superior performance over a from-scratch GPT-2 model across seven cell types using TF motif enrichment and FID-based metrics.
- **Visible evidence base** Abstract, introduction, methodology, experimental setup, results sections, Figures 1-3 (referenced), Tables 1-3 (referenced), supplementary material (referenced)
- **Missing materials affecting confidence** Figures and tables are referenced but not provided in the supplied text. Appendix sections A3 and A11 are referenced but not included. No code, hyperparameters, training details, or full evaluation protocols are available. The PsychENCODE dataset details and preprocessing steps are only partially described.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach to conditional DNA sequence generation by framing enhancer design as a multimodal Q&A task. The integration of cell type and gene expression context into a DNA LLM is a reasonable direction. However, the evidence provided is insufficient to establish the core claims. Key evaluation metrics are described only qualitatively, figures and tables are not available for inspection, and the comparison against a single from-scratch baseline is limited. The technical soundness of the approach cannot be fully assessed from the supplied material.
- **Who would be interested in the results, and why** Researchers in synthetic biology, regulatory genomics, and computational biology would be interested in methods for context-aware regulatory sequence design. Those working on applying large language models to genomic tasks would also find the instruction tuning approach relevant. The potential for generating cell-type-specific enhancers has implications for gene therapy and precision medicine.
- **Major strengths** The framing of enhancer generation as a conditional multimodal problem is novel and addresses a real gap in existing generative models. The use of a pre-trained DNA LLM (HyenaDNA) with a two-stage fine-tuning strategy is methodologically sensible. The evaluation attempts to capture both biological (TF motif enrichment) and semantic (FID) quality dimensions.
- **Major Concerns** The evaluation is incomplete without access to the referenced figures and tables. The baseline comparison is limited to a single from-scratch GPT-2 model, which is not a state-of-the-art DNA generation model. The biological validation of generated enhancers is indirect, relying on motif enrichment rather than functional assays. The handling of endothelial cells, which consistently underperform, is not adequately addressed. The statistical significance of reported differences is not established.
- **Minor Comments** The manuscript would benefit from clearer definitions of the evaluation metrics. The choice of GC content thresholds (20% and 80%) for promoter categorization is not justified. The description of the Geneformer encoder usage is brief and lacks detail on feature extraction. The conclusion overstates the findings given the indirect nature of the biological validation.
- **Technical failings that need to be addressed before the case is established** The absence of the actual figures and tables prevents verification of the reported quantitative results. The lack of statistical testing undermines confidence in the claimed improvements. The single baseline comparison is insufficient to demonstrate superiority over existing methods.
- **Assessment against Nature-style criteria** Originality: The multimodal instruction tuning approach for DNA sequence generation is a novel contribution. Scientific importance: The problem of cell-type-specific enhancer design is significant, but the evidence for practical utility is not yet established. Interdisciplinary readership: The work bridges AI and genomics, which could attract broad interest, but the presentation assumes familiarity with both fields. Technical soundness: The methodology is plausible but cannot be fully evaluated without the missing materials. Readability for nonspecialists: The abstract is accessible, but the methodology section is dense and would benefit from clearer explanations of key concepts.
- **Recommendation posture** Currently not established from the provided evidence. The core claims require verification of the missing figures, tables, and statistical analyses. Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that Leonine outperforms state-of-the-art LLMs in generating biologically and functionally coherent enhancer sequences across seven cell types.
- **Evidence pointer** Figures 2-3, Tables 1-3, location not provided
- **Concern** The quantitative results supporting the main claims are presented only through references to figures and tables that are not included in the supplied material. Without these, the reported improvements in JS divergence, R-squared values, and FID scores cannot be verified or interpreted.
- **Why it matters** The central conclusion of the paper rests on these quantitative comparisons. The absence of the actual data prevents any assessment of whether the claimed performance is real, meaningful, or statistically significant.
- **Resolution test** Provide the full figures and tables with clear axis labels, legends, and error bars or confidence intervals. Include the underlying data or a reproducible analysis pipeline.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline adequacy
- **Claim pointer** The manuscript claims that pre-training on DNA sequences is crucial for high-quality generation, based on comparison between Leonine (HyenaDNA) and Leonine-Gpt-2 (from-scratch GPT-2).
- **Evidence pointer** Section "Pre-training Is a Crucial Step for High-Quality DNA Sequence Generation", location not provided
- **Concern** The comparison is made against a single from-scratch GPT-2 model. This does not constitute a state-of-the-art baseline for DNA sequence generation. Other generative models for regulatory sequences exist, and the claim of superiority over "state-of-the-art LLMs" is not supported by the presented comparison.
- **Why it matters** The conclusion that pre-training is crucial is only meaningful if the alternative is a competitive approach. A from-scratch GPT-2 is a weak baseline, and the observed difference may reflect architectural or training details rather than the value of pre-training per se.
- **Resolution test** Include comparisons with additional baselines, such as other DNA generative models or LLMs fine-tuned without the multimodal context. Report performance of the same HyenaDNA backbone without instruction tuning to isolate the effect of the proposed method.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports differences in JS divergence, R-squared values, and FID scores between conditions and models, implying these differences are meaningful.
- **Evidence pointer** Section "Results", location not provided
- **Concern** No statistical tests, confidence intervals, or measures of variability are reported for any of the quantitative comparisons. It is unclear whether the observed differences are reproducible or within the range of random variation.
- **Why it matters** Without statistical rigor, the reported improvements could be due to chance, particularly given the large number of comparisons across seven cell types and multiple metrics.
- **Resolution test** Report the number of independent samples or replicates, and provide appropriate statistical tests (e.g., permutation tests, bootstrap confidence intervals) for all key comparisons.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** The manuscript claims that generated enhancers are "biologically plausible" and "biologically and functionally coherent."
- **Evidence pointer** Section "Multimodal Cellular Context Tuning Enables Biologically Plausible Enhancer Generation via DNA LLMs", location not provided
- **Concern** The biological plausibility is assessed only through TF motif enrichment scores compared to observed enhancers. This is an indirect proxy. No functional validation, such as reporter assays, CRISPR perturbation, or comparison with experimentally validated enhancer activity, is presented.
- **Why it matters** The claim of biological plausibility is central to the potential utility of the method. Motif enrichment alone does not demonstrate that the generated sequences would function as enhancers in a cellular context.
- **Resolution test** Provide functional validation of a subset of generated enhancers, or clearly reframe the claims to indicate that the evaluation is computational and predictive only.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes a two-stage training strategy and specific model components, implying the method is reproducible.
- **Evidence pointer** Section "Methodology", location not provided
- **Concern** Key implementation details are missing, including hyperparameters, training epochs, learning rates, batch sizes, computational resources, and the specific version of the HyenaDNA checkpoint. The Geneformer encoder usage is described only briefly. The data preprocessing steps for the PsychENCODE dataset are not fully specified.
- **Why it matters** Reproducibility is a core requirement for scientific claims. Without these details, other researchers cannot replicate or build upon the work.
- **Resolution test** Provide a detailed implementation section or a link to publicly available code, including all training and evaluation scripts, configuration files, and data processing pipelines.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Evaluation metrics
- **Evidence pointer** Section "Evaluation Protocols", location not provided
- **Issue** The description of the FID-based metric is brief. It is unclear how the Wasserstein distance is computed between Gaussian distributions fitted to embeddings, and what the dimensionality of the embedding space is.
- **Required correction** Provide a more detailed mathematical description of the FID computation, including the architecture of the classifier and the layer used for embeddings.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Justification
- **Affected element** GC content thresholds
- **Evidence pointer** Section "Evaluation Protocols", location not provided
- **Issue** The choice of 20% and 80% as thresholds for low and high GC content is not justified. It is unclear whether these thresholds are biologically motivated or arbitrary.
- **Required correction** Provide a rationale for the chosen thresholds, or cite literature supporting these cutoffs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Endothelial cell results
- **Evidence pointer** Section "Results", location not provided
- **Issue** The manuscript notes that endothelial cells consistently underperform but does not explore the reasons beyond limited representation. This could indicate a systematic issue with the method or the data.
- **Required correction** Discuss potential reasons for the endothelial cell results in more depth, and consider whether additional analysis or data could resolve the discrepancy.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Conclusion
- **Evidence pointer** Section "Conclusion", location not provided
- **Issue** The conclusion states that the framework "sets a new benchmark" but does not specify what the benchmark is or how it compares to existing benchmarks in the field.
- **Required correction** Define the benchmark explicitly and place the results in the context of existing methods and benchmarks.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract uses the term "multimodal question-and-answer task" without explaining what the question and answer are in this context. This may confuse readers unfamiliar with the framing.
- **Required correction** Briefly clarify in the abstract what constitutes the question and answer in the proposed framework.

## Risk / unsupported claims
- The claim that Leonine "outperforms state-of-the-art LLMs" is unsupported because only a single from-scratch GPT-2 baseline is compared, and the actual results are not visible.
- The claim that generated enhancers are "biologically and functionally coherent" is unsupported because only indirect computational metrics are used, with no functional validation.
- The claim that the framework "sets a new benchmark" is unsupported because no comparison to existing benchmarks or methods is provided.
- The claim that pre-training is "crucial" is only weakly supported by a comparison against a from-scratch model, which does not isolate the effect of pre-training from other factors.
- The quantitative results reported in the text (e.g., JS divergence ranges, R-squared values, FID scores, normalized Frobenius norms) cannot be verified without the corresponding figures and tables.