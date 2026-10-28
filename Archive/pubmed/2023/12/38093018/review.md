## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and proposals presented in the abstract; no methods, figures, or supplementary material were provided
- **Shared manuscript claim summary** The authors argue that the cis-regulatory code will not be solved by training models on genomic sequences alone, owing to homology-driven overestimation of performance and insufficient sequence diversity in the human genome. They propose that massively parallel assays using randomly synthesized and designed DNA sequences, combined with machine learning, provide a path toward solving this code, and assert that models trained on synthetic data can predict genomic activity, often better than genome-trained models.
- **Visible evidence base** Abstract text only; no experimental data, model descriptions, benchmark results, or prior work citations are visible
- **Missing materials affecting confidence** Full text, figures, tables, methods, model architecture details, dataset descriptions, performance comparisons, and any quantitative support for the central claims

## Reviewer
- **Overall assessment** The abstract presents a compelling and timely perspective on a major open problem in regulatory genomics. The central argument, that genomic sequence alone is insufficient for learning the cis-regulatory code and that synthetic DNA libraries offer a scalable alternative, is intellectually sound and aligns with recent trends in the field. However, the abstract is a perspective piece and contains no primary evidence. The strength of the case rests entirely on the full manuscript, which was not provided. As such, the claims are plausible but currently unverifiable from the supplied material.
- **Who would be interested in the results, and why** Computational biologists, machine learning researchers working on regulatory genomics, experimentalists using high-throughput reporter assays, and scientists interested in the principles of gene regulation. The proposed roadmap would be of broad interest to anyone seeking to understand how cis-regulatory information is encoded and how to build predictive models of gene expression.
- **Major strengths** The abstract clearly identifies a fundamental limitation of genome-only training data, namely homology-driven overfitting and insufficient sequence diversity. The proposal to use synthetic DNA to expand sequence space is logical and well motivated. The claim that synthetic-data-trained models can outperform genome-trained models is provocative and, if substantiated, would be an important contribution. The writing is accessible and the roadmap concept is well framed.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** No technical details are available from the abstract. The central empirical claim, that synthetic-data-trained models predict genomic activity better than genome-trained models, requires direct comparative benchmarks. The abstract does not specify what assays, model classes, or evaluation metrics are used. Without these, the case is not established.
- **Assessment against Nature-style criteria** 
  - Originality: High. The perspective is original in framing the problem as a data limitation issue and proposing synthetic DNA as a general solution.
  - Scientific importance: High. Solving the cis-regulatory code is a central goal in genomics and would have broad implications.
  - Interdisciplinary readership: Moderate to high. The topic bridges molecular biology, genomics, and machine learning, and the abstract is written to be accessible across these fields.
  - Technical soundness: Not assessable from the abstract. No methods or results are provided.
  - Readability for nonspecialists: Good. The abstract explains key concepts clearly and avoids unnecessary jargon.
- **Recommendation posture** Supportive if technical concerns are resolved. The perspective is promising, but the central claims require full manuscript evidence. Currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that models trained on synthetic DNA data can predict genomic activity, often better than genome-trained models.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract asserts a performance advantage for synthetic-data-trained models without presenting any comparative data, benchmarks, or model specifications. No datasets, assay types, or evaluation metrics are mentioned.
- **Why it matters** This is the central empirical claim of the perspective. Without direct evidence, the reader cannot assess whether the claim is robust, generalizable, or dependent on specific conditions.
- **Resolution test** Provide a comparison of synthetic-data-trained versus genome-trained models on held-out genomic loci, with clear metrics such as AUROC or correlation, across multiple cell types or contexts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scope of proposal
- **Claim pointer** The authors propose a roadmap to solving the cis-regulatory code using synthetic DNA and machine learning.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not describe the specific components of the roadmap, such as the design of synthetic libraries, the choice of assays, the model architectures, or the iterative strategy for improving predictions. The roadmap is mentioned but not outlined.
- **Why it matters** A roadmap is only useful if it provides actionable steps. Without details, the proposal remains a high-level idea rather than a concrete plan that others could follow or evaluate.
- **Resolution test** Include a figure or section in the full manuscript that lays out the roadmap steps, with clear milestones and expected outputs at each stage.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of claims
- **Claim pointer** The authors state that the cis-regulatory code will probably never be solved if models are trained only on genomic sequences.
- **Evidence pointer** Abstract only; location not provided
- **Concern** This is a strong negative claim. While the reasoning about homology and sequence diversity is plausible, the abstract does not discuss potential counterexamples or partial successes from genome-only models, nor does it address the possibility that larger genomic datasets from multiple species could mitigate the diversity problem.
- **Why it matters** The claim is central to motivating the synthetic DNA approach. If genome-only models can achieve sufficient performance with enough data, the proposed roadmap would be less necessary.
- **Resolution test** Provide a discussion in the full manuscript of the limits of genome-only models, including quantitative evidence of performance plateaus or failure cases, and justify why synthetic data is uniquely positioned to overcome these limits.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of "cis-regulatory code"
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "cis-regulatory code" is defined in the abstract, but the definition is broad and could be interpreted in multiple ways, such as sequence-to-expression mapping or sequence-to-binding specificity.
- **Required correction** Clarify the scope of the code, for example by specifying whether it includes transcription factor binding, chromatin state, or expression levels, and at what resolution.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "randomly synthesized" and "designed" DNA
- **Evidence pointer** Abstract; location not provided
- **Issue** The distinction between randomly synthesized and designed DNA sequences is introduced but not elaborated. The reader may not understand how these two types of sequences are generated or used differently.
- **Required correction** Briefly explain the difference, for example that random sequences sample sequence space broadly while designed sequences target specific hypotheses or model weaknesses.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Prior work
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not reference any prior studies that have used synthetic DNA for regulatory genomics, which would help position the proposal within the existing literature.
- **Required correction** Add citations to key prior works in the full manuscript and mention them briefly in the abstract if space permits.

## Risk / unsupported claims
- The claim that synthetic-data-trained models predict genomic activity better than genome-trained models is unsupported in the abstract and cannot be evaluated without full manuscript data.
- The claim that the cis-regulatory code will "probably never" be solved with genome-only training is a strong assertion that is not backed by quantitative evidence in the abstract.
- The proposed roadmap is mentioned but not described, making its feasibility and novelty unassessable from the supplied material.