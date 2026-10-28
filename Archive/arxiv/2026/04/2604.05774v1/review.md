## Review setup
- **Input scope** Full manuscript text including main text, appendices, and figure/table references
- **Assessment boundary** Evaluation of the benchmark design, dataset construction methodology, experimental results, and claims made about general-purpose LLM performance on raw genome sequences
- **Shared manuscript claim summary** The authors introduce GenomeQA, a benchmark of 5,200 samples across six task families, to evaluate general-purpose LLMs on sequence-based genome inference tasks. They report that frontier LLMs outperform random baselines, exploit local sequence signals, but struggle with tasks requiring indirect or multi-step inference.
- **Visible evidence base** Main text sections 1-5, appendices A-D, Tables 1-4, Figures 1-5, and referenced supplementary materials
- **Missing materials affecting confidence** Actual dataset samples, full prompt templates beyond examples, model output examples beyond failure cases, code implementation details, and complete statistical analyses

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely gap in evaluating general-purpose LLMs on raw genomic sequences. The benchmark design is thoughtful, with attention to biological hierarchy and controlled evaluation settings. However, several methodological concerns regarding dataset construction, evaluation protocol, and interpretation of results need to be addressed before the claims are fully established.
- **Who would be interested in the results, and why** Researchers working on LLM applications in genomics, developers of DNA-language models, and computational biologists interested in understanding the capabilities and limitations of general-purpose LLMs on sequence-level tasks. The benchmark could serve as a useful diagnostic tool for the broader AI-for-science community.
- **Major strengths** The benchmark fills a clear gap in existing evaluation resources. The task design preserves biological hierarchy and includes both direct and indirect inference settings. The failure mode analysis provides actionable insights into model limitations. The controlled comparison between direct and implicit target inference is a valuable experimental design.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Dataset construction methodology
  - **Claim pointer** The benchmark comprises 5,200 curated samples spanning six biologically grounded task families, with quality control measures to ensure label reliability.
  - **Evidence pointer** Section 3.1-3.3, Table 1
  - **Concern** The dataset construction process lacks sufficient detail on how negative samples are generated for tasks beyond splice site identification. For Enhancer/Promoter, Histone Mark, and TFBS tasks, the manuscript does not describe how negative or alternative-label samples are selected. The composition-matched negative generation is only described for splice sites. This raises questions about potential dataset biases that could inflate or deflate model performance.
  - **Why it matters** Without clear negative sample generation protocols, it is difficult to assess whether the benchmark measures genuine sequence understanding or is confounded by dataset artifacts such as sequence composition differences between classes.
  - **Resolution test** Provide detailed descriptions of negative sample generation for all tasks, including any matching procedures for sequence composition, GC content, or other confounding variables. Include validation analyses showing that performance differences are not driven by simple sequence statistics.
  
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evaluation protocol
  - **Claim pointer** We use a single fixed system prompt across all tasks and models, with details provided in Appendix B. No task-specific few-shot examples are included.
  - **Evidence pointer** Section 4.1, Appendix B
  - **Concern** The prompt optimization process is described as using a development set of 90 samples, but the manuscript does not report whether the optimized prompt was validated on a held-out set or whether the reported results are on the same data used for prompt development. This creates a potential for overfitting to the development set, which could inflate reported performance.
  - **Why it matters** If the prompt was optimized on a subset of the evaluation data, the reported results may not generalize to new data or reflect true model capabilities on unseen sequences.
  - **Resolution test** Clarify whether the development set is disjoint from the evaluation set. If not, report results on a held-out test set using the final optimized prompt. Provide details on the development set composition and how it relates to the full benchmark.
  
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Result interpretation
  - **Claim pointer** Models consistently outperform random baselines and can exploit local sequence signals such as GC content and short motifs, while performance degrades on tasks that require more indirect or multi-step inference over sequence patterns.
  - **Evidence pointer** Section 4.2, Table 2, Figure 3
  - **Concern** The manuscript does not provide statistical significance testing for performance differences between models or between tasks. The claim that models "consistently outperform" random baselines is based on point estimates without confidence intervals or hypothesis tests. Additionally, the interpretation that performance differences reflect task complexity is not supported by any formal analysis controlling for other factors such as sequence length, number of classes, or dataset size.
  - **Why it matters** Without statistical rigor, the reported performance differences may not be reliable, and the conclusions about model capabilities and task difficulty may be overstated.
  - **Resolution test** Provide confidence intervals or standard errors for all reported accuracies. Conduct formal statistical tests comparing model performance to random baselines and between tasks. Consider regression or other analyses to isolate the effect of task complexity from other confounding variables.
  
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Benchmark scope and generalizability
  - **Claim pointer** GenomeQA establishes a diagnostic benchmark for studying and improving the use of general-purpose LLMs on raw genomic sequences.
  - **Evidence pointer** Section 1, Section 5
  - **Concern** The benchmark covers only six task families, with a limited number of samples per task (approximately 500-600 per task). The manuscript does not discuss how representative these tasks are of the broader space of genome sequence inference problems, nor does it provide guidance on how results from GenomeQA might generalize to other genomic tasks or species.
  - **Why it matters** The claim that GenomeQA serves as a diagnostic benchmark for general-purpose LLM use in genomics requires evidence that the selected tasks are representative and that the benchmark has sufficient coverage to support general conclusions.
  - **Resolution test** Discuss the rationale for task selection and how these tasks map to real-world genomics applications. Consider adding tasks that cover a broader range of sequence lengths, regulatory mechanisms, and evolutionary distances. Provide guidance on how the benchmark could be extended.
  
  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Failure mode analysis
  - **Claim pointer** We present a fine-grained analysis of failure modes such as Sequence Motif Over-reliance and Character Fidelity Loss, highlighting systematic error patterns and directions for future research.
  - **Evidence pointer** Section 4.5, Figure 4, Appendix D
  - **Concern** The failure mode analysis is based on only 200 error samples from a single model (Gemini-3-Pro). The manuscript does not report whether these failure modes are consistent across other models, nor does it provide inter-rater reliability for the qualitative categorization. The prevalence of each failure mode is reported as percentages, but the coding scheme and criteria for categorization are not fully described.
  - **Why it matters** The failure mode taxonomy is presented as a general finding about LLM limitations, but the evidence base is narrow and may not generalize across models or tasks.
  - **Resolution test** Expand the failure mode analysis to include multiple models. Provide a detailed coding scheme and report inter-rater reliability. Consider quantitative measures of each failure mode rather than qualitative categorization alone.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 3.2, TFBS Prediction
  - **Evidence pointer** Section 3.2
  - **Issue** The description of the TFBS prediction task mentions selecting 20 transcription factors with distinct motifs, but does not specify how these factors were chosen or whether they represent a diverse range of DNA-binding domains.
  - **Required correction** Provide a brief justification for the selection of the 20 transcription factors and describe their diversity in terms of binding motifs and biological functions.
  
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Section 4.1, Baseline Models
  - **Evidence pointer** Section 4.1
  - **Issue** The manuscript mentions enabling thinking mode "whenever supported" but does not specify which models support this feature or how it was configured.
  - **Required correction** Provide a table or list indicating which models have thinking mode enabled and the specific configuration used for each.
  
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Section 4.2, Main Results
  - **Evidence pointer** Table 2
  - **Issue** The manuscript reports average accuracy across tasks but does not provide per-task standard deviations or confidence intervals.
  - **Required correction** Include measures of variability for all reported accuracies, either in the main tables or in supplementary materials.
  
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Dataset availability
  - **Affected element** Data availability statement
  - **Evidence pointer** Footnote 1
  - **Issue** The data availability statement provides an anonymous link, but it is unclear whether the dataset includes all necessary files for full reproduction (e.g., raw sequences, labels, prompts, and evaluation scripts).
  - **Required correction** Clarify the contents of the released data and code, and provide a detailed README describing how to reproduce the main results.
  
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Related work
  - **Affected element** Section 2.2
  - **Evidence pointer** Section 2.2
  - **Issue** The related work section on genome benchmarks does not discuss recent benchmarks for evaluating LLMs on biological sequences beyond those mentioned, such as those focused on protein or RNA sequences.
  - **Required correction** Briefly mention related benchmarks in adjacent domains to position GenomeQA within the broader landscape of biological sequence evaluation.
- **Technical failings that need to be addressed before the case is established** R1-M1 (negative sample generation), R1-M2 (prompt overfitting), R1-M3 (statistical rigor)
- **Assessment against Nature-style criteria** 
  - Originality: The benchmark addresses a genuine gap in evaluating general-purpose LLMs on raw genome sequences, which is a novel contribution relative to existing benchmarks that focus on specialized DNA models or text-only knowledge tests.
  - Scientific importance: The work has potential importance for understanding LLM capabilities in genomics and for guiding future development of genome-aware language models. However, the limited task coverage and small dataset size constrain the strength of the conclusions.
  - Interdisciplinary readership: The work bridges AI and genomics, and the findings are likely to interest researchers in both communities. The writing is generally accessible, though some genomics-specific terminology may require background knowledge.
  - Technical soundness: The benchmark construction and evaluation methodology are generally sound, but the concerns raised about negative sample generation, prompt optimization, and statistical rigor need to be addressed to fully establish the technical validity of the results.
  - Readability for nonspecialists: The manuscript is well-structured and the main findings are clearly presented. However, the appendices contain technical details that may be challenging for readers without a genomics background.
- **Recommendation posture** Supportive if technical concerns are resolved. The benchmark addresses a relevant gap and the experimental design is thoughtful, but the methodological issues around dataset construction, evaluation protocol, and statistical reporting need to be addressed before the claims are fully established.

## Risk / unsupported claims
- The claim that models "consistently outperform random baselines" is not supported by statistical testing.
- The claim that performance differences reflect task complexity is not formally tested against confounding variables.
- The failure mode taxonomy is based on a single model and may not generalize.
- The benchmark's representativeness of the broader space of genome inference tasks is not established.
- The effectiveness of the optimized prompt is not validated on a held-out set.