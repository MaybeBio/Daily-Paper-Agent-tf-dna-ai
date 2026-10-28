## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, technical soundness, and clarity of the review article, including its synthesis of existing literature and proposed methodological integration
- **Shared manuscript claim summary** The authors review current knowledge on pioneer transcription factor (PF) induced nucleosome dynamics and chromatin opening, focusing on structural and dynamic aspects. They synthesize evidence from genome-wide studies, cryo-EM structures, molecular dynamics simulations, and NMR spectroscopy, and propose that integrating NMR with MD simulations is a powerful approach to study PF-mediated nucleosome and chromatin fiber dynamics using native DNA sequences
- **Visible evidence base** Full text including abstract, introduction, sections on genome-wide studies, nucleosome binding site locations, structural studies, molecular simulations, NMR spectroscopy, and concluding remarks. Figures 1-5 are referenced but not directly viewable
- **Missing materials affecting confidence** Figure content could not be directly inspected. Some primary study details (e.g., specific simulation parameters, NMR experimental conditions) are summarized rather than fully described, which is expected for a review article

## Reviewer
- **Overall assessment** This is a well-structured and timely review that addresses an important and rapidly evolving topic in gene regulation. The authors successfully synthesize diverse experimental and computational approaches to understand how pioneer transcription factors engage nucleosomes and initiate chromatin opening. The review is comprehensive in scope, covering genome-wide studies, structural biology, molecular dynamics simulations, and NMR spectroscopy. The proposed integration of NMR and MD simulations is well reasoned and represents a valuable forward-looking perspective. The manuscript is generally well written and accessible to a broad biophysics audience, though some sections could benefit from additional clarity. The main limitations are the lack of a critical comparative analysis of conflicting results in the literature and the absence of a clear framework for how the proposed NMR-MD approach would overcome specific technical challenges
- **Who would be interested in the results, and why** Researchers in chromatin biology, transcription regulation, structural biology, and computational biophysics would find this review valuable. It provides a useful synthesis of recent structural and dynamic studies on PF-nucleosome interactions, which is directly relevant to those studying cell fate determination, reprogramming, and developmental biology. The methodological discussion on integrating NMR and MD simulations would also interest biophysicists developing hybrid experimental-computational approaches
- **Major strengths** 1) Comprehensive and up-to-date synthesis of diverse experimental approaches, from genome-wide methods to high-resolution structures. 2) Clear articulation of key open questions in the field, particularly regarding histone tail dynamics and the link between nucleosome opening and chromatin opening. 3) Balanced treatment of experimental and computational approaches, with appropriate acknowledgment of limitations. 4) Well-reasoned proposal for integrating NMR and MD simulations as a future direction. 5) Useful timeline figure (Fig. 2) that contextualizes landmark studies
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** None identified from the supplied material
- **Assessment against Nature-style criteria** Originality: The review provides a valuable synthesis but does not present fundamentally new concepts. Its originality lies in the specific integration of NMR and MD approaches for PF-nucleosome dynamics, which is a reasonable but not entirely novel proposal. Scientific importance: The topic is of high importance given the central role of PFs in development and reprogramming. The review addresses key unresolved questions. Interdisciplinary readership: The review bridges structural biology, biophysics, computational biology, and genomics, making it relevant across disciplines. Technical soundness: The presentation of existing studies is accurate and appropriately caveated. The proposed NMR-MD integration is technically plausible. Readability for nonspecialists: The manuscript is generally accessible, though some sections assume familiarity with specialized techniques. The figures help convey complex structural concepts
- **Recommendation posture** Supportive if minor technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Critical analysis and synthesis
- **Claim pointer** The review presents conflicting findings in the literature (e.g., Sox2 binding site preferences, Oct4-induced nucleosome opening vs. sliding) without providing a critical comparative analysis to help readers understand the sources of discrepancy
- **Evidence pointer** Sections "Identifying binding locations of individual pioneer factors on engineered nucleosomes" and "Pioneer-factor induced nucleosome dynamics from experimental structures"
- **Concern** The authors describe contradictory results from different studies, such as Sox2 preferring nucleosome ends versus dyad regions, and Oct4-induced opening versus sliding of nucleosomes. However, they do not critically analyze why these discrepancies arise. Potential explanations could include differences in DNA sequences used, experimental conditions, or technical limitations of different methods. A more critical synthesis would strengthen the review's value to the field
- **Why it matters** Readers need guidance to interpret conflicting literature. Without critical analysis, the review risks presenting a confusing picture rather than clarifying the current state of knowledge. This is particularly important for a field where methodological differences can substantially impact conclusions
- **Resolution test** Add a dedicated discussion section that systematically compares conflicting results, identifies potential sources of discrepancy (e.g., sequence context, experimental conditions, resolution limits), and provides a balanced assessment of which conclusions are robust across studies

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Methodological integration
- **Claim pointer** The authors propose that integrating NMR spectroscopy with MD simulations is a powerful approach to study PF-mediated nucleosome dynamics, but they do not adequately address the technical challenges and limitations of this integration
- **Evidence pointer** Sections "Pioneer factor and nucleosome dynamics from NMR spectroscopy" and "Concluding remarks and outlook"
- **Concern** While the proposal to combine NMR and MD is reasonable, the authors do not discuss specific technical hurdles. For example, the size of nucleosome-PF complexes may limit solution NMR approaches, isotopic labeling strategies for large complexes are challenging, and the timescales accessible to MD simulations may not match those probed by NMR relaxation experiments. The authors should address how these challenges would be overcome
- **Why it matters** A methodological proposal is only valuable if it is technically feasible. Without addressing practical limitations, the proposal may be seen as aspirational rather than actionable. This is particularly important for a review that aims to guide future research directions
- **Resolution test** Add a subsection that explicitly discusses technical challenges of NMR-MD integration for nucleosome systems, including size limitations, labeling strategies, timescale matching, and potential solutions such as solid-state NMR or advanced MD sampling techniques

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scope and depth
- **Claim pointer** The review focuses heavily on Oct4, Sox2, and a few other PFs, but the title suggests a broader coverage of pioneer transcription factors in general
- **Evidence pointer** Throughout the manuscript, particularly in sections on structural studies and molecular simulations
- **Concern** While Oct4 and Sox2 are the most extensively studied PFs, the review would benefit from broader coverage of other PFs with distinct DNA binding domains and mechanisms, such as FoxA, GATA factors, p53, and Nr5a2. The current focus may not fully represent the diversity of PF mechanisms
- **Why it matters** The title promises a general review of pioneer transcription factors. If the scope is limited to a few well-studied examples, this should be acknowledged and justified. A broader perspective would increase the review's utility to researchers studying different PFs
- **Resolution test** Either expand coverage of additional PFs or explicitly state in the introduction that the review focuses on the best-characterized PFs and explain why this focus is justified

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and could benefit from clearer articulation of the review's specific contributions and conclusions
- **Required correction** Consider restructuring the abstract to more explicitly state the key findings from the literature synthesis and the specific rationale for the NMR-MD integration proposal

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1-5
- **Evidence pointer** Figures 1-5
- **Issue** The figures are referenced extensively but could not be directly evaluated. Based on the text descriptions, some figures may benefit from additional annotation to guide readers through complex structural representations
- **Required correction** Ensure all figures include clear labels, color legends, and sufficient annotation to be interpretable without extensive reference to the text

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section "Pioneer transcription factor activity from genome-wide experiments"
- **Evidence pointer** Section "Pioneer transcription factor activity from genome-wide experiments"
- **Issue** The term "pioneer activity" is used throughout but is not explicitly defined early in the manuscript. Some readers may benefit from a clear operational definition
- **Required correction** Add a brief definition of "pioneer activity" in the introduction, distinguishing it from general transcription factor activity

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Pioneer factor and nucleosome dynamics from NMR spectroscopy"
- **Evidence pointer** Section "Pioneer factor and nucleosome dynamics from NMR spectroscopy"
- **Issue** The NMR section is relatively brief compared to the structural and simulation sections. Given the emphasis on NMR in the proposed future direction, this section could be expanded
- **Required correction** Consider adding more detail on specific NMR techniques applicable to nucleosome systems, such as methyl-TROSY, CEST, or relaxation dispersion methods, and their potential for studying PF-nucleosome dynamics

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** Some statements about specific findings could benefit from more explicit citation to primary literature, particularly in sections summarizing multiple studies
- **Required correction** Review the manuscript to ensure all specific claims are properly attributed to their original sources

## Risk / unsupported claims
- The claim that "integrating NMR spectroscopy with molecular dynamics simulations is a powerful approach" is presented as a proposal rather than a demonstrated approach. While reasonable, it is not yet validated for PF-nucleosome systems specifically
- The statement that "none of the structures reveals the complete histone tails" is presented as a general observation, but the completeness of histone tail visualization may vary across structures and could be better qualified
- The suggestion that "coarse-grained MD simulations may be combined with solid-state NMR in the future" is speculative and not supported by specific evidence of feasibility
- The claim that "the structures, while ground-breaking, present end-states reached after binding" is an interpretation that may not apply uniformly to all structures discussed