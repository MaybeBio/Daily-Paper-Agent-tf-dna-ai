## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors benchmark four general-purpose large language models (Claude 3.5 Sonnet, Gemini 1.0 Pro, GPT-4o, Llama3 8b) on identifying transcription factor (TF)-target regulatory interactions using literature-curated (TRRUST v2) and experimentally derived (TFLink) ground truth datasets. They evaluate performance across four regulatory direction categories (bidirectional, ambiguous, self-regulated, unidirectional), test the effects of zero temperature and multi-turn prompting, and report that prompt engineering and parameter settings influence model performance, with Claude 3.5 Sonnet and GPT-4o generally outperforming others.
- **Visible evidence base** Full text including Methods, Results, Discussion, figure captions (Figures 1-6 referenced), supplementary figure references (Figures 2, 3, 5, 7, 8), and Table 1 reference
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; exact prompts for multi-turn task not fully specified in text; detailed per-category results for all metrics not fully reported in main text

## Reviewer
- **Overall assessment** The manuscript addresses a timely and practical question: whether general-purpose LLMs can reliably identify TF-target regulatory interactions. The benchmarking framework is clearly described and the use of two complementary ground truth datasets (literature-curated and experimentally derived) is a strength. However, the reported performance is modest (best balanced accuracy around 50-72%), and the manuscript does not adequately address the practical utility of these models given the availability of curated databases. The claim that LLMs offer a more accessible alternative is plausible but not quantitatively supported by a comparison with existing computational tools or database queries. The analysis of data leakage is superficial, and the statistical treatment of results is limited. The manuscript would benefit from a clearer articulation of what new knowledge or capability is demonstrated beyond existing benchmarks.
- **Who would be interested in the results, and why** Researchers in regulatory genomics and bioinformatics who are considering using LLM-based chatbots for literature mining or hypothesis generation. The study provides a practical benchmark that could inform tool selection and prompt design. The findings may also interest computational biologists developing LLM-based applications for biomedical knowledge extraction.
- **Major strengths** 1) Clear and reproducible benchmarking framework with well-defined categories and metrics. 2) Use of two independent ground truth sources (literature-curated and experimentally derived) to address potential data leakage. 3) Systematic evaluation of model parameters (temperature) and prompting strategies (multi-turn). 4) Practical focus on accessibility for non-expert users, which is relevant to the broader research community.
- **Major Concerns** 1) The performance of the best models is modest (balanced accuracy around 50-72%), and the manuscript does not provide a clear threshold or comparison to establish whether this is practically useful. 2) The claim that LLMs are "more accessible" than existing databases is not empirically tested; a comparison with a simple database query or existing computational tool would strengthen the case. 3) The data leakage analysis is limited; the authors acknowledge the risk but do not quantify the potential overlap between training data and TRRUST. 4) The statistical significance of differences between models or conditions is not assessed. 5) The multi-turn prompting analysis is only applied to self-regulated pairs, limiting the generalizability of the finding.
- **Minor Comments** 1) The manuscript would benefit from a table summarizing all model performances across all conditions and metrics. 2) The exact multi-turn prompts are not fully specified in the text; this should be included for reproducibility. 3) The definition of "ambiguous" regulation is clear, but the handling of multiple ground truth types in evaluation could be more explicit. 4) The discussion of limitations is appropriate but could be expanded on the issue of model version drift (e.g., Claude 3.5 Sonnet vs. newer versions).
- **Technical failings that need to be addressed before the case is established** 1) Lack of statistical comparison between models and conditions. 2) Incomplete specification of multi-turn prompts. 3) No quantitative assessment of data leakage risk. 4) No comparison with existing non-LLM methods or database queries.
- **Assessment against Nature-style criteria** Originality: Moderate. The application of LLMs to TF-target interaction identification is not entirely new, but the systematic benchmarking across multiple models and conditions is a useful contribution. Scientific importance: Moderate. The results are informative for practitioners but do not fundamentally advance understanding of regulatory biology or LLM capabilities. Interdisciplinary readership: Limited. The manuscript is primarily of interest to bioinformatics and computational biology audiences. Technical soundness: Adequate but with gaps in statistical rigor and completeness of reporting. Readability for nonspecialists: Good. The manuscript is clearly written and accessible, though some methodological details require domain knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The benchmarking framework is valuable, but the manuscript needs to address the statistical rigor, provide a comparison with existing tools, and more thoroughly assess the data leakage issue before the claims are fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports performance differences between models and conditions (e.g., "Claude 3.5 Sonnet and GPT-4o outperformed the others") without statistical testing.
- **Evidence pointer** Section 3.1, Figures 2-6
- **Concern** The manuscript reports differences in balanced accuracy and other metrics across models and conditions but does not provide any statistical analysis (e.g., confidence intervals, hypothesis tests) to support claims of superiority or equivalence. The standard deviations reported are across iterations, not across independent samples, and do not account for the paired nature of the data (same items queried across models).
- **Why it matters** Without statistical assessment, the reader cannot determine whether observed differences are meaningful or within the range of random variation. This is critical for the central claim that some models outperform others.
- **Resolution test** Provide appropriate statistical tests (e.g., paired bootstrap, McNemar's test for classification) with correction for multiple comparisons, and report effect sizes and confidence intervals for key comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative benchmarking
- **Claim pointer** The manuscript claims LLMs offer a "more accessible alternative" to existing computational methods and databases for identifying TF-target interactions.
- **Evidence pointer** Introduction, Discussion
- **Concern** The manuscript does not compare LLM performance against existing non-LLM methods or even a simple database query baseline. The claim of accessibility is not empirically supported. For example, querying TRRUST or TFLink directly would provide a baseline accuracy of 100% on the curated data, and the value of LLMs would need to be demonstrated in terms of novel interactions or ease of use.
- **Why it matters** The practical utility of LLMs for this task is a central motivation. Without a comparison to existing tools, the reader cannot assess whether the modest performance reported is acceptable or whether existing methods are superior.
- **Resolution test** Include a baseline comparison, such as direct database lookup or a simple rule-based method, and discuss the trade-offs in terms of accuracy, coverage, and usability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data leakage assessment
- **Claim pointer** The manuscript states that using experimentally derived TFLink data "addresses potential data leakage" from literature-curated TRRUST data.
- **Evidence pointer** Section 2.1, Section 3.5
- **Concern** The TFLink dataset is described as "experimentally derived," but the manuscript also notes that TFLink combines data from multiple databases, some of which may be literature-based. The claim that this dataset avoids data leakage is not fully substantiated. The authors do not quantify the potential overlap between LLM training data and either ground truth source.
- **Why it matters** Data leakage is a known issue in LLM evaluation, and the manuscript's approach to mitigating it is a key methodological contribution. If the mitigation is incomplete, the reported performance may be inflated.
- **Resolution test** Provide a more detailed analysis of the TFLink data sources and their potential overlap with LLM training data. Consider using a temporal holdout (e.g., interactions published after the LLM training cutoff) as a stricter test.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of multi-turn prompting
- **Claim pointer** The manuscript claims that "multi-turn prompting improved performance for most models" based on analysis of self-regulated pairs.
- **Evidence pointer** Section 3.3, Figure 4
- **Concern** The multi-turn prompting analysis is only applied to self-regulated pairs (24 pairs in the ground truth). This is a very small and specific subset, and the results may not generalize to other regulatory categories. The manuscript does not test multi-turn prompting on the larger unidirectional or ambiguous categories.
- **Why it matters** The claim that multi-turn prompting is beneficial is a key finding, but its limited scope weakens the generalizability of the conclusion.
- **Resolution test** Apply multi-turn prompting to at least one additional regulatory category (e.g., unidirectional) to demonstrate that the benefit is not specific to self-regulated pairs.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Multi-turn prompt specification
- **Evidence pointer** Section 2.4
- **Issue** The exact prompts used for the multi-turn task are not fully specified in the text. The manuscript states "the following queries per multi-turn prompt" but the actual queries are not shown.
- **Required correction** Include the full multi-turn prompt sequence in the main text or supplementary materials.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reporting completeness
- **Affected element** Performance metrics
- **Evidence pointer** Section 3.1, Figures 2-6
- **Issue** The main text reports balanced accuracy for key comparisons but does not consistently report all five metrics (accuracy, balanced accuracy, macro F1, macro precision, macro recall) for all conditions. Some results are only in supplementary figures.
- **Required correction** Provide a summary table in the main text with all metrics for all models and conditions, or clearly indicate where each metric is reported.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of definitions
- **Affected element** "Ambiguous" category
- **Evidence pointer** Section 2.1, Section 3.1
- **Issue** The definition of "ambiguous" is given as "a combination of activation, repression, or unknown from different sources," but it is not clear how the ground truth label is assigned when multiple types are present. The evaluation treats any of the ground truth types as correct, but this is not explicitly stated.
- **Required correction** Clarify the evaluation rule for ambiguous pairs in the Methods section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Model version specificity
- **Affected element** Model descriptions
- **Evidence pointer** Section 2.2
- **Issue** The manuscript specifies model versions (e.g., "2024-06-20 version via API") but does not discuss the potential for version drift or the relevance of these specific versions at the time of publication.
- **Required correction** Add a brief note on model versioning and the potential for results to change with newer versions.

## Risk / unsupported claims
- The claim that LLMs are "more accessible" than existing databases is not empirically supported.
- The claim that multi-turn prompting improves performance is based on a very small subset (self-regulated pairs) and may not generalize.
- The claim that the TFLink dataset addresses data leakage is not fully substantiated.
- The performance of models on the "unknown" category is not separately analyzed, making it difficult to assess whether models are simply defaulting to common answers.
- The manuscript does not report the distribution of model responses (e.g., how often models return "unknown" vs. a specific type), which is relevant for interpreting accuracy.