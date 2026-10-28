## Review setup
- **Input scope** Full manuscript text (abstract, main text, references cited within text)
- **Assessment boundary** Scientific content, methodological accuracy, completeness of method descriptions, decision framework utility, and alignment with stated aims
- **Shared manuscript claim summary** The manuscript presents a decision-oriented review of experimental and computational methods for identifying transcription factor (TF) targets in plants, comparing biochemical, genome-wide binding, expression-based, and computational approaches, and offering integration guidance for model and non-model systems.
- **Visible evidence base** Full text of the review, including sections on individual binding assays, genome-wide methods, expression analysis, computational tools, integrated approaches, and emerging technologies. Figures and tables are referenced but not provided.
- **Missing materials affecting confidence** Figures (Figure 1), Table 1, and Box 1 are referenced but not included in the provided material. This limits assessment of the decision framework's practical utility and the accuracy of comparative summaries.

## Reviewer
- **Overall assessment** This review addresses a timely and practically important topic: how to choose among the expanding toolkit of methods for identifying TF targets in plants. The authors correctly emphasize the distinction between binding potential and functional regulation, and the need for integrative workflows. The structure is logical, moving from individual assays to genome-wide methods, expression profiling, computational tools, and integration strategies. The inclusion of plant-specific challenges (polyploidy, genome complexity, non-model species limitations) is a strength. However, the manuscript has several weaknesses. The decision framework is described but its actual content (Figure 1, Table 1, Box 1) is not assessable from the provided material. Some method descriptions lack critical technical detail, and the treatment of computational tools is uneven, with dynGENIE3 and dynverse mentioned only in passing. The emerging technologies section is forward-looking but somewhat speculative. The writing is generally clear but occasionally verbose and repetitive. Overall, the manuscript has merit as a practical guide, but the case for its novelty and the robustness of its decision framework cannot be fully evaluated without the missing figures and tables.

- **Who would be interested in the results, and why** Plant molecular biologists, particularly those studying transcription factors in crops or non-model species, will find this review useful for method selection. Graduate students and postdocs entering the field will benefit from the comparative overview. Researchers working on gene regulatory network inference will appreciate the integration of experimental and computational perspectives. The emphasis on practical constraints (antibody availability, genome complexity, cost) makes it relevant for labs with limited resources. The review may also interest bioinformaticians seeking to understand the experimental basis of TF-target data.

- **Major strengths**
  1. Clear conceptual distinction between binding potential and functional regulation, maintained throughout.
  2. Plant-specific focus with explicit discussion of polyploidy, genome complexity, and non-model species challenges.
  3. Practical orientation with decision-oriented framing, including scenario-based workflows (Box 1, not provided).
  4. Up-to-date coverage including emerging technologies (ENIRAP-seq, PIVOT, single-cell multi-omics, Perturb-seq).
  5. Balanced treatment of strengths and limitations for each method category.
  6. Good use of illustrative examples (e.g., maize ARF DAP-seq, SLIM1 overexpression, CCT39 integration).

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness of decision framework
- **Claim pointer** The manuscript claims to provide a "decision-oriented framework" and "concrete selection criteria summarized in Figure 1 and Table 1" to guide method selection.
- **Evidence pointer** Figure 1, Table 1, Box 1 (referenced but not provided)
- **Concern** The central value proposition of this review is the decision framework, yet the actual content of Figure 1, Table 1, and Box 1 is not available for assessment. Without these, it is impossible to evaluate whether the framework is genuinely actionable, whether the selection criteria are well-chosen, or whether the scenario-based workflows are realistic. The text alone provides general guidance but does not constitute a concrete decision tool.
- **Why it matters** The manuscript's stated novelty over prior reviews rests on this practical, decision-oriented contribution. If the figures and tables do not deliver clear, implementable guidance, the review becomes largely redundant with existing comprehensive overviews.
- **Resolution test** Provide Figure 1, Table 1, and Box 1 for assessment. The framework should include explicit criteria (e.g., throughput, cost, resolution, species applicability, question type) with clear decision paths. The table should compare methods across multiple dimensions. Box 1 should present realistic scenarios with recommended workflows.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical accuracy and completeness of method descriptions
- **Claim pointer** The manuscript states that DAP-seq "bypasses the constraints of antibody availability or specificity" and provides "higher resolution and higher likelihood of honing in on the motif."
- **Evidence pointer** Section "DNA affinity purification sequencing and derivatives"
- **Concern** The claim that DAP-seq provides "higher resolution" than ChIP-seq is not universally true and depends on the specific comparison. DAP-seq uses naked genomic DNA, which removes chromatin context but also eliminates the possibility of capturing chromatin-dependent binding. The resolution advantage is primarily in motif identification, not in mapping functional binding sites. The text should be more nuanced about what "resolution" means in this context.
- **Why it matters** Overstating DAP-seq advantages could mislead readers into choosing it for questions where chromatin context is essential. The trade-off between in vitro and in vivo methods is a key decision point, and the text should present it accurately.
- **Resolution test** Revise the claim to specify that DAP-seq offers higher resolution for identifying intrinsic sequence preferences, while noting that it cannot capture chromatin-dependent or cofactor-dependent binding. Clarify the distinction between sequence-level resolution and functional relevance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Coverage of computational methods
- **Claim pointer** The manuscript states that GENIE3 "offers a machine learning framework for identifying regulatory targets of specific TFs" and that dynGENIE3 is "a time-series extension."
- **Evidence pointer** Section "GEne network inference with ensemble of trees"
- **Concern** The treatment of computational methods is uneven. GENIE3 is described in some detail, but dynGENIE3 is mentioned only in a single sentence. The broader computational landscape section lists tools (MEME, HOMER, PlantPAN, RSAT Plants, JASPAR, PlantTFDB, FootprintDB) but does not critically compare them or explain when to use which. Given the review's decision-oriented aim, this is a missed opportunity. Additionally, the claim that GENIE3 is suitable for "focused TF characterization" needs more nuance, as its performance depends heavily on dataset size and quality.
- **Why it matters** Computational tools are increasingly central to TF-target identification, and readers need guidance on tool selection and limitations. The current treatment is too superficial to support informed decisions.
- **Resolution test** Expand the computational section with a comparative table or structured discussion of tool strengths, limitations, and recommended use cases. Provide more detail on dynGENIE3 and other time-series methods. Discuss the importance of dataset quality and the risk of false positives in network inference.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Integration guidance
- **Claim pointer** The manuscript states that "the most powerful insights emerge from integrating multiple approaches" and that "integrated workflows are essential."
- **Evidence pointer** Section "Integrated approaches"
- **Concern** The integration section is largely conceptual. The CCT39 example is illustrative but does not provide a generalizable protocol or decision tree for when and how to combine methods. The text does not address practical issues such as how to reconcile conflicting results from different methods, how to prioritize validation experiments, or how to handle the cost and time implications of multi-method approaches.
- **Why it matters** The review's stated aim is to guide researchers from "initial TF discovery through comprehensive network characterization." Without concrete integration guidance, readers may struggle to apply the concepts to their own systems.
- **Resolution test** Provide a step-by-step integration workflow, possibly in Box 1, that addresses common scenarios (e.g., unknown TF in non-model species, known TF with existing antibodies, TF family with many members). Include guidance on resolving discrepancies between binding and expression data.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Use of "binding potential" vs. "functional regulation"
- **Evidence pointer** Throughout
- **Issue** The distinction between binding potential and functional regulation is central to the review, but the terms are not formally defined at first use. Some readers may benefit from explicit definitions and examples.
- **Required correction** Add a brief definition of both terms in the Introduction, with an example of a method that measures each.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Citation of Morffy et al. and Hummel et al.
- **Evidence pointer** Section "TF effector domain characterization"
- **Issue** The citations appear as "Morffy et al. (2024)" and "Hummel et al. (2024)" but the reference list is not provided. The text also has a typo: "Morffy" is spelled "Moffrey" in one instance.
- **Required correction** Ensure consistent spelling of author names and verify that all cited references appear in the reference list.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of emerging technologies section
- **Affected element** Discussion of Perturb-seq
- **Evidence pointer** Section "Chromatin accessibility and single-cell multi-omics"
- **Issue** The mention of Perturb-seq is brief and speculative. Given the review's forward-looking stance, a more detailed discussion of technical challenges and current status in plants would be valuable.
- **Required correction** Expand the Perturb-seq discussion with specific challenges (e.g., delivery efficiency, guide RNA design, data analysis) and any existing plant applications.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Sentence structure in the Abstract
- **Evidence pointer** Abstract
- **Issue** The sentence "This review provides a decision-oriented framework, that integrates experimental and computational plant TF–target identification" contains an unnecessary comma and is grammatically awkward.
- **Required correction** Revise to "This review provides a decision-oriented framework that integrates experimental and computational approaches for plant TF–target identification."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency of method naming
- **Affected element** "ENIRAP-seq" vs. "ENTRAP-seq"
- **Evidence pointer** Section "Enrichment of nuclear trans-elements reporter assay in plants"
- **Issue** The section title uses "ENIRAP-seq" but the text uses "ENTRAP-seq". This inconsistency is confusing.
- **Required correction** Use one consistent abbreviation throughout.

- **Technical failings that need to be addressed before the case is established**
  1. Missing Figure 1, Table 1, and Box 1, which are central to the decision-oriented claim (R1-M1).
  2. Inconsistent abbreviation for ENTRAP-seq (R1-m5).
  3. Typo in author name "Moffrey" vs. "Morffy" (R1-m2).
  4. Unclear claim about DAP-seq resolution (R1-M2).

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The review covers familiar ground but adds a decision-oriented framing and plant-specific focus. The integration of emerging technologies (ENIRAP-seq, PIVOT) is relatively novel. However, the conceptual framework (binding vs. function) is not new.
  - **Scientific importance** High for the plant biology community. TF-target identification is a fundamental challenge, and practical guidance is valuable. The review addresses a real need, particularly for non-model species researchers.
  - **Interdisciplinary readership** Moderate. The review is primarily aimed at plant molecular biologists and will have limited appeal beyond that community. Computational aspects are covered but not deeply enough to attract bioinformaticians as primary readers.
  - **Technical soundness** Generally sound, but with some overstatements (DAP-seq resolution) and uneven coverage (computational tools). The missing figures and tables prevent full assessment of the decision framework's technical validity.
  - **Readability for nonspecialists** Good. The writing is clear and accessible, with appropriate use of examples. Some sections are verbose and could be tightened. The abstract is concise and informative.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a useful topic and is generally well-written. However, the central decision framework cannot be evaluated without the missing figures and tables. The DAP-seq resolution claim needs revision, and the computational section should be expanded. If these issues are addressed, the review would be a valuable contribution to the plant TF field.

## Risk / unsupported claims
- The claim that DAP-seq provides "higher resolution" than ChIP-seq is not fully supported and needs qualification.
- The claim that the review provides "concrete selection criteria" cannot be verified without Figure 1 and Table 1.
- The claim that "the most powerful insights emerge from integrating multiple approaches" is asserted but not systematically demonstrated with comparative evidence.
- The statement that PIVOT "directly identifies functional TF-promoter interactions within plant cells" is somewhat overstated, as the method relies on a synthetic reporter system and may not fully recapitulate endogenous conditions.
- The claim that ENTRAP-seq "links what a TF does in its true plant cellular environment" is partially contradicted by the use of a synthetic reporter and overexpression, which the authors acknowledge.
- The assertion that "computational approaches... provide the benefit of more efficient, in-depth analysis" is vague and not quantified.