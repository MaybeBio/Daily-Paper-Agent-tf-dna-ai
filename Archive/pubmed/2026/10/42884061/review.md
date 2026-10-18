## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract
- **Shared manuscript claim summary** The abstract reviews three generations of computational methods for plant gene regulatory network (GRN) inference, proposes a five-level evidence ladder, and advocates a lab-in-the-loop framework where foundation models act as hypothesis engines to prioritize candidate TF-target pairs for experimental validation.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or references provided
- **Missing materials affecting confidence** Full manuscript, figures, tables, methods section, references, and any quantitative performance comparisons

## Reviewer
- **Overall assessment** The abstract presents a well-structured conceptual overview of computational GRN inference in plants, with a clear historical framing and a forward-looking proposal. However, the evidence base is limited to the abstract, and several claims regarding method capabilities and the proposed framework lack quantitative support or specific examples. The five-level evidence ladder is an interesting organizing principle but its operationalization is not described. The proposal for foundation models as hypothesis engines is plausible but currently asserted rather than demonstrated.
- **Who would be interested in the results, and why** Plant molecular biologists seeking an accessible overview of computational GRN inference tools; computational biologists developing GRN inference methods; researchers interested in the application of deep learning and foundation models to plant genomics; and experimental biologists looking for prioritization strategies to reduce the burden of validating TF-target interactions.
- **Major strengths** The abstract provides a clear and logical historical progression from classical statistics to deep learning. The five-level evidence ladder offers a useful conceptual framework for evaluating GRN inference quality. The lab-in-the-loop proposal is pragmatic and addresses a real bottleneck in the field. The writing is accessible to nonspecialists.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide quantitative evidence for the claimed performance of any method generation. The five-level ladder is introduced but not defined with operational criteria. The claim that foundation models can "share regulatory insights across different species" is not supported by any example or benchmark. The lab-in-the-loop framework is described qualitatively without a concrete implementation or validation strategy.
- **Assessment against Nature-style criteria** 
  - Originality: The five-level evidence ladder and the lab-in-the-loop framing are somewhat novel organizational concepts, but the underlying ideas are not entirely new to the field.
  - Scientific importance: The topic is important, and the proposed framework could be impactful if substantiated, but the abstract does not establish this.
  - Interdisciplinary readership: The abstract is written accessibly and could appeal to both experimental and computational biologists.
  - Technical soundness: Cannot be assessed from the abstract alone; no technical details or validation are provided.
  - Readability for nonspecialists: The abstract is clear and well-written, with jargon explained in context.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising as a conceptual review, but the full manuscript must provide technical details, examples, and validation to support the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that "classical statistics and machine learning have simplified complex gene expression data into clear, prioritised predictions" and that "deep learning can interpret cis-regulatory grammar directly from genome sequences."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract asserts the capabilities of each method generation without providing any quantitative performance metrics, benchmark comparisons, or specific examples. No data are shown to support the claim that these methods produce "clear, prioritised predictions" or that deep learning successfully interprets cis-regulatory grammar.
- **Why it matters** Without evidence of method performance, the reader cannot evaluate whether the proposed historical progression is accurate or whether the claims are overstated. This is central to the review's purpose.
- **Resolution test** The full manuscript should include benchmark results, case studies, or comparative analyses demonstrating the claimed capabilities of each method generation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Conceptual clarity
- **Claim pointer** The abstract introduces a "five-level ladder of evidence, including statistical association, conditional dependence, physical binding, functional regulation and causal circuits."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The five levels are listed but not defined. It is unclear how each level is operationalized, how methods map onto the levels, or how a researcher would assign a GRN inference result to a specific level. The ladder is presented as a central organizing framework, yet its criteria are absent.
- **Why it matters** The ladder appears to be a key contribution of the review. Without clear definitions, the framework cannot be applied or evaluated by readers.
- **Resolution test** The full manuscript should define each level with explicit criteria, provide examples of methods or studies at each level, and explain how the ladder can be used to assess GRN inference quality.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The abstract states that "foundation models trained on plant genomes and millions of cells hold exciting potential to share regulatory insights across different species."
- **Evidence pointer** Abstract text; location not provided
- **Concern** This is a strong claim about cross-species transfer of regulatory insights, but no example, pilot study, or benchmark is cited. The claim is presented as potential, but the wording implies a level of demonstrated capability that is not supported.
- **Why it matters** Cross-species transfer is a major selling point of the proposed framework. If unsupported, the central proposal loses credibility.
- **Resolution test** The full manuscript should provide at least one concrete example or proof-of-concept demonstrating cross-species regulatory insight sharing, or clearly frame this as a hypothesis with preliminary supporting data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** "tens of millions of candidate TF-target pairs"
- **Evidence pointer** Abstract text; location not provided
- **Issue** The number is stated without a citation or calculation. It is unclear whether this refers to a specific species or is a general estimate.
- **Required correction** Provide a citation or clarify the basis for this estimate.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "lab-in-the-loop"
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term is used without definition. While the concept is understandable from context, a brief definition would improve accessibility.
- **Required correction** Define the term on first use, for example as an iterative framework where experimental validation informs subsequent computational predictions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope
- **Affected element** "three generations of computational approaches"
- **Evidence pointer** Abstract text; location not provided
- **Issue** The three generations are described but not explicitly enumerated or named. The reader must infer the boundaries between generations.
- **Required correction** Explicitly list the three generations with clear defining characteristics and representative methods.

## Risk / unsupported claims
- The claim that classical statistics and machine learning have produced "clear, prioritised predictions" is unsupported by quantitative evidence in the abstract.
- The claim that deep learning can "interpret cis-regulatory grammar directly from genome sequences" is presented as established fact but no supporting data or examples are provided.
- The claim that foundation models can "share regulatory insights across different species" is unsupported and currently speculative.
- The five-level evidence ladder is introduced without operational definitions, making it unevaluable.
- The estimate of "tens of millions of candidate TF-target pairs" is stated without citation or calculation.