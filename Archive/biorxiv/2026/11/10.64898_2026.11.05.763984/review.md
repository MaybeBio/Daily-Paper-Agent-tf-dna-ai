## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce Protein-DNA Language Models (PDLMs), built by continued pretraining from ESM2 with masked language modeling on paired protein-DNA sequences. A shared encoder and a domain-aware masking strategy are claimed to improve protein-DNA pair classification, mutation-associated binding change prediction, zero-shot scoring of DNA recognition specificity, variant prioritization for editing activity, cross-study base editor activity prediction, and direct prediction of DNA motifs from protein sequences after fine-tuning on transcription factor binding data.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, dataset descriptions, or methodological specifics are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, dataset descriptions, training and evaluation protocols, baseline definitions, statistical analyses, and code or model availability statements

## Reviewer

- **Overall assessment** The abstract presents a conceptually interesting approach to joint protein-DNA language modeling with a plausible methodological innovation in domain-aware masking. However, the evidence provided is entirely qualitative. No performance numbers, benchmark comparisons, or statistical validations are reported. The claims span a wide range of downstream tasks, but the abstract does not allow assessment of whether the improvements are meaningful, generalizable, or statistically robust. The work may be of interest to the computational biology and genome engineering communities, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Computational biologists working on protein-DNA interaction prediction, machine learning researchers developing multimodal or cross-molecular language models, and experimentalists in genome editing and synthetic biology who seek predictive tools for designing proteins with altered DNA recognition specificity. The potential to predict motifs directly from protein sequences and to prioritize variants with higher editing activity would be practically relevant to these groups.
- **Major strengths** The conceptual framing of joint protein-DNA representation in a shared encoder is timely and addresses a real limitation in existing language models that treat protein and DNA sequences independently. The domain-aware masking strategy is a sensible and potentially generalizable innovation. The breadth of downstream applications, from classification to zero-shot scoring to motif prediction, suggests a versatile framework with practical potential.
- **Major Concerns** The abstract provides no quantitative evidence for any of the claimed improvements. Without effect sizes, baseline comparisons, or statistical significance, the central claims are unverifiable. The claim of "improved" performance relative to independent-encoder baselines is vague and cannot be evaluated. The zero-shot scoring claims are particularly strong and require demonstration of specificity and calibration. The cross-study prediction claim raises concerns about dataset leakage and generalizability that cannot be assessed from the abstract. The motif prediction claim after fine-tuning is interesting but requires evaluation against established motif discovery methods.
- **Minor Comments** The abstract does not specify the scale of pretraining data, model size, or computational cost. The relationship between PDLMs and existing protein-DNA interaction predictors is not positioned clearly. The phrase "interaction-aware" is used repeatedly but its operational definition is not precise. The competing interest statement is present but the abstract does not clarify whether any of the tools or models are commercially related to the declared interests.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: the joint modeling approach with domain-aware masking is a novel contribution, though the abstract does not distinguish it sufficiently from prior multimodal language models. Scientific importance: potentially high if the claims hold, particularly for genome editing and transcriptional regulation research. Interdisciplinary readership: the work bridges machine learning, molecular biology, and genome engineering, which fits a broad audience. Technical soundness: cannot be assessed from the abstract; no methodological detail or validation is provided. Readability for nonspecialists: the abstract is generally clear but relies on domain jargon such as "masked language modeling" and "zero-shot scoring" without brief explanation.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual contribution is promising, but the abstract alone does not support the breadth of claims made. A full manuscript with quantitative results, baselines, and statistical analyses would be required to assess whether the case can be made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "PDLMs improved protein-DNA pair classification relative to independent-encoder baselines"
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract claims improved classification performance but provides no quantitative results, no baseline definitions, no dataset descriptions, and no statistical significance measures. It is impossible to determine whether the improvement is marginal or substantial, whether it generalizes across datasets, or whether it is driven by specific architectural choices.
- **Why it matters** Classification performance is a core claim of the work. Without numbers, the reader cannot judge whether PDLMs offer a practical advantage over existing methods. This is the foundation on which the other downstream claims rest.
- **Resolution test** Provide classification metrics such as AUROC or AUPRC on defined benchmark datasets, with comparisons to independent-encoder baselines and existing state-of-the-art methods, including confidence intervals and significance tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Zero-shot scoring recovered known changes in DNA-recognition specificity and prioritized variants with higher editing activity"
- **Evidence pointer** Abstract, location not provided
- **Concern** Zero-shot claims are strong and require demonstration that the model's scoring function is well calibrated and discriminative without task-specific training. The abstract does not specify which known changes were recovered, how many were tested, what the success rate was, or how "higher editing activity" was defined and measured.
- **Why it matters** Zero-shot capability is a key differentiator for practical use in protein engineering. If the model cannot reliably rank variants, its utility for guiding experimental design is limited. The claim as stated is unfalsifiable from the abstract.
- **Resolution test** Provide a defined set of known specificity-changing mutations with recovery rates, rank correlation between model scores and measured editing activity, and comparison to appropriate baselines such as ESM2 or other zero-shot predictors.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Learned representations also supported cross-study prediction of base editor activity"
- **Evidence pointer** Abstract, location not provided
- **Concern** Cross-study prediction is a demanding generalization test. The abstract does not describe the training and evaluation studies, how they differ, whether any preprocessing harmonization was applied, or what performance metric was achieved. The risk of dataset leakage or hidden batch effects cannot be assessed.
- **Why it matters** Cross-study generalization is essential for real-world applicability. If the model only works within a single study's distribution, its practical value is substantially reduced. The claim as stated cannot be evaluated.
- **Resolution test** Describe the source and target studies, the evaluation protocol, and report performance metrics with appropriate baselines. Address potential batch effects and demonstrate that performance is not driven by study-specific artifacts.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "After fine-tuning on transcription factor binding data, PDLMs predicted DNA motifs directly from protein sequences"
- **Evidence pointer** Abstract, location not provided
- **Concern** Motif prediction from protein sequences is a challenging task that requires comparison to established motif discovery and prediction methods. The abstract does not specify the transcription factor binding data used, the evaluation metric, the number of factors tested, or how predicted motifs were compared to known motifs.
- **Why it matters** This claim suggests a novel capability that could be widely useful. However, without rigorous evaluation against existing tools such as DeepBind, DeepSEA, or position weight matrix based methods, the added value of PDLMs is unclear.
- **Resolution test** Provide motif prediction accuracy metrics on a defined benchmark set of transcription factors, with comparison to existing methods, and show examples of predicted versus known motifs.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "interaction-aware" is used to describe the models but is not operationally defined. It is unclear whether this refers to the shared encoder, the masking strategy, or both.
- **Required correction** Define "interaction-aware" explicitly in terms of the architectural and training choices that make the model interaction-aware.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Model scale and data
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not report the scale of pretraining data, model parameter count, or computational resources required. This information is important for assessing reproducibility and practical feasibility.
- **Required correction** Include model size, pretraining data scale and source, and training compute in the full manuscript, and summarize key numbers in the abstract if space permits.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Positioning
- **Affected element** Related work
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not position PDLMs relative to existing multimodal or joint embedding models for protein-DNA interactions, such as those based on cross-attention or contrastive learning.
- **Required correction** Add a brief statement in the introduction or discussion that distinguishes PDLMs from prior joint modeling approaches.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Availability
- **Evidence pointer** Abstract, location not provided
- **Issue** No statement is made about code, model weights, or data availability. For a methods-driven paper, this is a significant omission.
- **Required correction** Include a data and code availability statement in the full manuscript.

## Risk / unsupported claims

- The claim that PDLMs "improved protein-DNA pair classification relative to independent-encoder baselines" is unsupported by any quantitative evidence in the abstract.
- The claim that "zero-shot scoring recovered known changes in DNA-recognition specificity" is unsupported without specification of the changes tested and the recovery rate.
- The claim that PDLMs "prioritized variants with higher editing activity" is unsupported without definition of the activity assay and the prioritization metric.
- The claim that "learned representations supported cross-study prediction of base editor activity" is unsupported without description of the studies and the performance achieved.
- The claim that PDLMs "predicted DNA motifs directly from protein sequences" is unsupported without evaluation details or comparison to existing methods.
- The overall claim that PDLMs provide "a framework for interaction-aware biomolecular language modeling" is a reasonable framing but is not substantiated by evidence in the abstract.