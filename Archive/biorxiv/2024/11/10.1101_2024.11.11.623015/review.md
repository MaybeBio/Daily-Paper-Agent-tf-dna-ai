## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present LOL-EVE, a conditional autoregressive transformer trained on 13.6 million mammalian promoter sequences, for zero-shot prediction of promoter variant effects including indels and complete promoter haplotypes. They introduce three benchmarks for promoter indel prediction and report superior performance, plus an application to Genomics England clinical data for prioritizing promoter haplotypes in developmental disorder genes.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, or clinical data descriptions are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, benchmark definitions, training data details, model architecture specifics, and clinical analysis results

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable contribution to regulatory genomics by extending variant effect prediction to indels and haplotypes, an area where existing methods are acknowledged to be limited. The concept of using evolutionary patterns from a large mammalian promoter corpus is scientifically appealing. However, the abstract provides no quantitative evidence to support the claims of superior performance or clinical utility. The three benchmarks are named but not described in terms of construction, size, or evaluation metrics. The clinical application is mentioned without any specificity. As presented, the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in human genetics, particularly those focused on noncoding variant interpretation, clinical genomics, and regulatory element biology. The work also targets developers of genomic language models and computational methods for variant effect prediction. Clinicians involved in rare disease diagnosis may find the haplotype-level prioritization potentially relevant, though this remains speculative from the abstract.
- **Major strengths** The problem selection is well motivated, addressing a genuine gap in indel and haplotype-level promoter variant prediction. The use of a large mammalian training corpus for zero-shot prediction is a reasonable and potentially powerful approach. The introduction of three distinct benchmarks suggests an intention to evaluate across complementary biological contexts.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The approach of applying a conditional autoregressive transformer to promoter sequences for zero-shot indel and haplotype prediction appears novel, though the abstract does not clarify how it differs from existing genomic language models beyond the training data and task focus.  
  Scientific importance: If the performance claims are substantiated, the work could address a real gap in noncoding variant interpretation, which is of high importance in human genetics.  
  Interdisciplinary readership: The topic bridges computational biology, genomics, and clinical genetics, which could attract a broad audience, but the abstract does not currently make the work accessible to nonspecialists due to a lack of context and quantitative framing.  
  Technical soundness: Cannot be assessed from the abstract alone. No metrics, baselines, or statistical details are provided.  
  Readability for nonspecialists: The abstract is concise but assumes familiarity with terms such as "conditional autoregressive transformer," "zero-shot," and "causal eQTL." The clinical relevance is stated but not explained in a way that a general reader could evaluate.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but lacks all quantitative support. A full manuscript with detailed methods, benchmark results, and clinical analysis would be required to assess whether the claims hold.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "LOL-EVE's superior performance demonstrates that evolutionary patterns learned from indels enable accurate assessment of broader promoter function."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The claim of superior performance is made without any quantitative comparison to existing methods. No metrics, baseline names, effect sizes, or statistical significance values are reported.  
- **Why it matters** Without quantitative evidence, the central claim of the paper cannot be evaluated. Superior performance is the foundation for the subsequent claims about clinical utility and broader applicability.  
- **Resolution test** Provide benchmark results with clear metrics (e.g., AUROC, AUPRC, correlation coefficients) and comparisons to at least one or more established methods, with confidence intervals or significance tests.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Benchmark validity  
- **Claim pointer** "We introduce three benchmarks for promoter indel prediction: ultra rare variant prioritization, causal eQTL identification, and transcription factor binding site disruption analysis."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The three benchmarks are named but not described. There is no information on how they were constructed, what data sources were used, how ground truth was defined, or what evaluation protocols were followed.  
- **Why it matters** Benchmarks are only meaningful if their design is transparent and methodologically sound. Without this information, the reported performance cannot be interpreted or reproduced.  
- **Resolution test** Describe each benchmark in detail, including data sources, variant selection criteria, labeling procedures, and evaluation metrics. Ideally, make the benchmarks publicly available.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Clinical claim support  
- **Claim pointer** "Application to Genomics England clinical data shows that LOL-EVE can prioritize promoter haplotypes in known developmental disorder genes, suggesting potential utility for clinical variant assessment."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The clinical application is stated without any results. No information is given on the number of cases, the genes examined, the prioritization performance, or how this compares to existing clinical variant interpretation methods.  
- **Why it matters** Clinical utility is a strong claim that requires robust evidence. Without specifics, the suggestion of clinical potential is unsupported and could be misleading if the analysis was preliminary or underpowered.  
- **Resolution test** Provide detailed results from the Genomics England analysis, including cohort size, gene list, prioritization accuracy, and comparison to current clinical interpretation standards.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Model description  
- **Claim pointer** "LOL-EVE (Language Of Life for Evolutionary Variant Effects), a conditional autoregressive transformer trained on 13.6 million mammalian promoter sequences that enables both zero-shot indel prediction and complete promoter sequence scoring."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The model is described only at a high level. No details are given on architecture, training procedure, input representation, or how zero-shot prediction is operationalized for indels and haplotypes.  
- **Why it matters** Reproducibility is a core requirement for computational methods. Without architectural and training details, the method cannot be replicated or compared fairly with other approaches.  
- **Resolution test** Provide a full methods section with model architecture, hyperparameters, training data processing, and inference procedures. Release code and trained model weights where possible.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The phrase "evolutionary patterns learned from indels" is ambiguous. It is unclear whether the model learns from indels as training examples or from sequence context that includes indels.  
- **Required correction** Clarify whether indels are part of the training data or only used at inference time, and specify what "evolutionary patterns" refers to in this context.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "zero-shot" usage  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "zero-shot" is used but not defined in the context of this model. It is unclear whether it means no fine-tuning on downstream tasks, no task-specific training data, or something else.  
- **Required correction** Define "zero-shot" explicitly in the abstract or introduction, and state what the model has and has not seen during training.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scope  
- **Affected element** Benchmark coverage  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The three benchmarks focus on indels, but the model also claims to score complete promoter sequences. It is unclear whether the benchmarks assess haplotype-level performance or only individual variant effects.  
- **Required correction** Clarify whether the benchmarks include haplotype-level evaluation, and if not, state that haplotype scoring is validated separately.

## Risk / unsupported claims
- "LOL-EVE's superior performance" is unsupported without quantitative results.
- "Potential utility for clinical variant assessment" is unsupported without clinical analysis details.
- The three benchmarks are unverifiable as described.
- The model's zero-shot capability and its basis in "evolutionary patterns learned from indels" are not defined or evidenced.
- Any claim of generalizability to broader promoter function is not supported by the abstract alone.