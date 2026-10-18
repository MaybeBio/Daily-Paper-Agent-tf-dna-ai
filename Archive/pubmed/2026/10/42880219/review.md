## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Conceptual framework and claims as presented in the abstract; no methods, figures, or data were available for evaluation
- **Shared manuscript claim summary** The authors propose a two-layer framework for cis-regulatory element (CRE) logic: binding-level integration (cooperative TF interactions modulating DNA occupancy) and transcriptional-level integration (TF effector domains and cofactors converting binding configurations into expression). They classify TF cooperativity along orthogonal axes (specific versus general, symmetric versus asymmetric) and describe cofactor-driven additive, synergistic, or antagonistic logic. They claim a recurring quantitative pattern, "multiplication plus saturation," reconciles binding specificity with flexibility, explains how short DNA motifs generate precise expression while maintaining evolvability, and informs synthetic biology and therapeutic applications.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials were provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods section, any quantitative analyses or models supporting the "multiplication plus saturation" pattern, and any experimental or computational validation data

## Reviewer

- **Overall assessment** This abstract presents a potentially valuable conceptual synthesis of cis-regulatory mechanisms, organizing a complex literature into a two-layer framework with defined axes of cooperativity. The ambition to identify unifying quantitative principles is commendable and aligns with current interests in predictive models of gene regulation. However, the abstract provides no empirical or computational evidence for the central claims, particularly the "multiplication plus saturation" pattern, which is asserted rather than demonstrated. The framework's novelty relative to existing reviews on enhancer logic and TF cooperativity is not clearly established from the abstract alone. The manuscript may be of interest to a specialized audience in gene regulation, but the case for broad significance and for the specific quantitative claim requires the full manuscript.
- **Who would be interested in the results, and why** Researchers in gene regulation, transcriptional control, chromatin biology, and synthetic biology would be the primary audience. Those working on predictive models of gene expression from sequence, enhancer design, and therapeutic targeting of transcriptional mechanisms would find the framework potentially useful for organizing hypotheses and designing experiments. The evolutionary implications regarding motif grammar and evolvability may also interest evolutionary biologists studying regulatory evolution.
- **Major strengths** The two-layer distinction between binding-level and transcriptional-level integration provides a clear organizational principle that could help unify disparate observations. The proposed orthogonal axes for classifying cooperativity (specific versus general, symmetric versus asymmetric) offer a structured vocabulary for comparing different mechanisms. The identification of a recurring quantitative pattern, if substantiated, could provide a valuable design principle for both understanding natural CREs and engineering synthetic ones.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that a recurring quantitative pattern, "multiplication plus saturation," emerges from the complexity of cis-regulatory control and reconciles binding specificity with flexibility
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The central quantitative claim of a "multiplication plus saturation" pattern is stated without any supporting evidence. No data, model, or analysis is referenced in the abstract to demonstrate that this pattern is indeed recurring across different CREs, TFs, or contexts. The abstract does not indicate whether this pattern is derived from published data, new computational analyses, or theoretical reasoning.
  - **Why it matters** This pattern is presented as the key unifying insight of the framework and underpins the claimed implications for evolvability, synthetic biology, and therapeutics. Without evidence establishing its recurrence and predictive utility, the claim remains an assertion rather than a demonstrated principle. The scientific value of the framework depends critically on whether this pattern is empirically grounded.
  - **Resolution test** The full manuscript must provide quantitative evidence, either from new analyses or from systematic re-analysis of published datasets, demonstrating that the "multiplication plus saturation" pattern holds across multiple CREs and TF combinations. Ideally, the authors would show that this pattern improves predictive accuracy for expression outcomes compared to alternative models.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Novelty and positioning
  - **Claim pointer** The implicit claim that the proposed framework offers a new organizing principle for cis-regulatory logic
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not clearly differentiate this framework from existing conceptual models of enhancer function, such as the billboard and enhanceosome models, or from prior reviews that have discussed TF cooperativity, nucleosome competition, and cofactor logic. The axes proposed for classifying cooperativity may overlap with existing categorizations in the literature.
  - **Why it matters** For a framework paper to be impactful, it must clearly articulate what is new relative to prior conceptualizations. If the two-layer division and the cooperativity axes largely recapitulate existing ideas with new terminology, the contribution is primarily organizational rather than conceptual. The claim of a unifying principle requires demonstrating that this framework captures phenomena that prior models cannot.
  - **Resolution test** The full manuscript should include an explicit comparison with existing models of enhancer logic, identifying specific predictions or classifications that are unique to this framework. The authors should articulate what new insights or experimental predictions arise from their specific axes and layer division that would not arise from prior frameworks.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scope and generalizability
  - **Claim pointer** The claim that the framework explains how short DNA motifs generate precise expression while maintaining evolvability
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract asserts that the "multiplication plus saturation" pattern explains the relationship between short motif length and expression precision, as well as evolvability. However, no mechanistic argument or evidence is provided in the abstract to connect the quantitative pattern to these evolutionary and functional properties. The logic of this connection is not apparent from the abstract alone.
  - **Why it matters** The claimed implications for evolvability and the motif-to-precision relationship are among the most broadly interesting aspects of the framework. If these connections are not rigorously argued and supported, the framework's significance is substantially reduced. These claims also suggest testable evolutionary predictions that should be articulated.
  - **Resolution test** The full manuscript should provide a clear mechanistic explanation for how "multiplication plus saturation" gives rise to precision and evolvability, ideally with formal modeling or comparative genomic evidence. The authors should specify what empirical observations would distinguish their framework from alternatives on these points.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Definition of "multiplication plus saturation"
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The term "multiplication plus saturation" is introduced without definition or mathematical formalization. It is unclear whether this refers to a specific functional form, a qualitative pattern, or an analogy.
  - **Required correction** Provide a clear definition in the abstract or indicate where in the manuscript the formal definition appears. A brief mathematical expression or a concrete example would help readers understand the concept.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Use of "specific versus general" cooperativity
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The distinction between "specific" and "general" cooperativity is not defined. It is unclear whether "general" refers to cooperativity that applies across many TF pairs, cooperativity involving generic cofactors, or something else.
  - **Required correction** Define these terms explicitly, ideally with examples of each class, to avoid ambiguity.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Coverage of transcriptional-level integration
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The transcriptional-level layer is described more briefly than the binding-level layer. The abstract mentions additive, synergistic, and antagonistic logic from cofactor interactions but does not indicate how these are classified or predicted.
  - **Required correction** Provide additional detail on the classification of transcriptional-level logic or indicate where this is addressed in the manuscript.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The central quantitative claim requires evidence, and the novelty relative to existing frameworks must be established. Without addressing these, the case for the framework as a unifying principle is not established from the provided material.
- **Assessment against Nature-style criteria** Originality: The framework may offer a novel organizational synthesis, but its originality relative to existing models cannot be fully assessed from the abstract. Scientific importance: The topic is important, and a genuine unifying principle would be valuable, but the importance of this specific framework depends on evidence not provided. Interdisciplinary readership: The abstract has potential appeal beyond core gene regulation, particularly to synthetic biology and evolutionary biology, but the current framing is specialized. Technical soundness: Cannot be assessed from the abstract; no methods or data are presented. Readability for nonspecialists: The abstract is reasonably clear for a specialized audience but uses jargon that would limit accessibility to nonspecialists.
- **Recommendation posture** Currently not established from the provided evidence. The framework is potentially interesting, and the review would be supportive if the full manuscript provides the quantitative evidence for the "multiplication plus saturation" pattern and clearly articulates the novelty relative to existing models. The decision should be conditional on these technical concerns being resolved.

## Risk / unsupported claims

- The "multiplication plus saturation" pattern as a recurring quantitative principle is unsupported in the abstract; no evidence is provided.
- The claim that this pattern reconciles binding specificity with flexibility is unsupported; the mechanistic connection is not explained.
- The claim that the framework explains how short DNA motifs generate precise expression while maintaining evolvability is unsupported; no argument or evidence is provided.
- The claim that the framework informs synthetic biology and therapeutic applications is plausible but unsupported; no specific applications or examples are given.
- The completeness and accuracy of the classification of cooperativity axes cannot be evaluated without the full manuscript.