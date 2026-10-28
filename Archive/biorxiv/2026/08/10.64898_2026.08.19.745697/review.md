## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose a self-supervised DNA-centric multimodal foundation model that fuses DNA sequence embeddings with local and global chromatin accessibility signals in a shared encoder. They claim that global normalization prevents representation collapse, enabling reusable window-level embeddings. They report a 4.6-fold AUPRC improvement over a DNA-only baseline for regulatory activity prediction, regulatory signal ranking, and chromatin accessibility peak detection, with additional gains on external ClinVar, GTEx eQTL, and PBMC caQTL datasets.
- **Visible evidence base** Abstract text only; no quantitative details beyond the reported AUPRC fold improvement and external dataset names
- **Missing materials affecting confidence** Full manuscript, methods section, model architecture details, training and evaluation protocols, baseline specifications, dataset descriptions, statistical significance tests, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable contribution to genomic foundation models by addressing multimodal fusion of sequence and chromatin accessibility data. The core idea of using global normalization to mitigate collapse in heterogeneous modality fusion is interesting and could be of broad interest. However, the abstract alone provides insufficient evidence to evaluate the technical soundness, the validity of the reported improvements, or the generalizability of the approach. The claims are plausible but currently not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational genomics, particularly those working on foundation models for regulatory genomics, chromatin accessibility analysis, and variant effect prediction. The work may also interest machine learning researchers focused on multimodal representation learning and collapse prevention in self-supervised settings.
- **Major strengths** The problem addressed is timely and relevant, as sequence-only genomic models have known limitations in capturing regulatory information. The proposed solution of integrating multiple chromatin accessibility modalities in a self-supervised manner is conceptually sound. The reported external validation on ClinVar, GTEx eQTL, and PBMC caQTL datasets suggests potential practical utility.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The model integrates DNA sequence embeddings with local and global chromatin accessibility in a shared encoder to produce reusable window-level embeddings, and global normalization alleviates collapse.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract provides no details on the model architecture, the fusion mechanism, the definition of local versus global chromatin accessibility, or how global normalization is implemented. Without this information, it is impossible to assess whether the proposed approach is technically sound, novel relative to existing multimodal fusion methods, or reproducible.
  - **Why it matters** The central technical claim is that global normalization prevents collapse in multimodal fusion. This is a specific and testable claim, but the abstract does not describe the mechanism, the baseline fusion approach, or the collapse dynamics observed. The reader cannot evaluate whether the solution is general or tailored to this specific setting.
  - **Resolution test** Provide a detailed methods section describing the encoder architecture, the fusion strategy, the normalization scheme, and the training objective. Include ablation studies showing collapse without global normalization and the effect of alternative normalization strategies.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The resulting embeddings improve regulatory activity prediction, regulatory signal ranking and chromatin accessibility peak detection, achieving a 4.6-fold AUPRC improvement over the DNA-only baseline.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The reported 4.6-fold AUPRC improvement is presented without context. It is unclear what tasks are evaluated, what the baseline model is, what datasets are used for evaluation, and whether the improvement is statistically significant. The abstract also does not specify whether the improvement is averaged across tasks or specific to one task.
  - **Why it matters** AUPRC improvements can be misleading if baseline performance is very low or if the evaluation set is small or imbalanced. Without task definitions, dataset sizes, baseline specifications, and confidence intervals, the magnitude of the reported improvement cannot be interpreted.
  - **Resolution test** Provide a full evaluation section with task definitions, dataset descriptions, baseline model details, per-task results, and statistical significance testing. Report AUPRC values for both baseline and proposed model, not just the fold change.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generalizability
  - **Claim pointer** Further gains on external ClinVar, GTEx eQTL and PBMC caQTL datasets.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract claims external validation on three datasets but provides no details on the tasks, the evaluation metrics, the comparison baselines, or the magnitude of the gains. It is unclear whether these datasets are used for fine-tuning, zero-shot evaluation, or transfer learning.
  - **Why it matters** External validation is a key strength claim, but without specifics, the reader cannot assess whether the gains are meaningful, consistent across datasets, or simply reflect favorable evaluation conditions.
  - **Resolution test** Describe the evaluation protocol for each external dataset, including the task, the metric, the baseline, and the quantitative results. Clarify whether the model is fine-tuned or used in a zero-shot setting.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The terms "local and global chromatin accessibility" are not defined. It is unclear whether these refer to different genomic scales, different data sources, or different aggregation strategies.
  - **Required correction** Define these terms explicitly in the abstract or methods, and clarify how they are computed and integrated.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Model availability
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract does not mention whether the model, code, or pretrained weights will be made publicly available.
  - **Required correction** State the availability of code, model weights, and any relevant resources in the abstract or a data availability statement.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Comparison
  - **Affected element** Baseline selection
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The comparison is only against a DNA-only baseline. It is unclear how the proposed model compares to existing multimodal genomic models or to simpler fusion approaches.
  - **Required correction** Include comparisons against existing multimodal models and alternative fusion strategies to demonstrate the specific benefit of the proposed approach.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The abstract does not provide sufficient technical detail to assess the architecture, the evaluation methodology, or the validity of the reported improvements. Without these, the central claims cannot be verified.

## Risk / unsupported claims
- The claim that global normalization alleviates collapse is unsupported without architectural and training details.
- The 4.6-fold AUPRC improvement is uninterpretable without baseline values, task definitions, and statistical context.
- The external validation gains on ClinVar, GTEx eQTL, and PBMC caQTL datasets are unquantified and cannot be evaluated.
- The claim of producing "reusable window-level embeddings" is not substantiated by any downstream task demonstrating reusability beyond the reported tasks.

## Assessment against Nature-style criteria
- **Originality** The idea of addressing collapse in multimodal genomic fusion via global normalization is potentially novel, but the abstract does not provide enough context to distinguish it from existing multimodal representation learning methods. The originality claim is plausible but not established.
- **Scientific importance** If the claims hold, the work could advance genomic foundation models by incorporating regulatory information beyond sequence, which is a significant gap. The potential impact on variant effect prediction and regulatory genomics is high.
- **Interdisciplinary readership** The work bridges genomics and machine learning, and the abstract is written in a way that is accessible to both communities. However, the lack of technical detail limits its immediate utility to either audience.
- **Technical soundness** Not assessable from the abstract. The core technical claims require detailed methods and evaluation to verify.
- **Readability for nonspecialists** The abstract is clear and concise, with minimal jargon. The key concepts are introduced adequately for a broad audience.

## Recommendation posture
Currently not established from the provided evidence. The abstract presents an interesting and potentially important contribution, but the lack of methodological detail and quantitative context prevents verification of the central claims. I would be supportive if the technical concerns are resolved with a full manuscript providing detailed methods, comprehensive evaluations, and statistical rigor.