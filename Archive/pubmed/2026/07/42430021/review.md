## Review setup
- **Input scope** Full manuscript text (review article, no figures or tables included in the provided material)
- **Assessment boundary** Scientific content, conceptual framework, internal consistency, and evidentiary support as presented in the text; figures and tables referenced but not directly assessable
- **Shared manuscript claim summary** The authors argue that WRKY transcription factor specificity in plant stress responses cannot be explained by W-box DNA binding alone, and instead emerges from the integration of five regulatory layers: cis-regulatory motif grammar, chromatin accessibility and epigenetic state, protein–protein interactions, post-translational modifications and proteostasis, and signaling context. They term this integrative model the "WRKY regulatory code" and propose that it resolves paradoxes in WRKY biology, provides a falsifiable framework, and can be tested and applied through multi-omics and machine learning approaches.
- **Visible evidence base** The manuscript cites a range of primary literature, including structural studies of W-box recognition, chromatin and epigenetic analyses, protein–protein interaction studies, post-translational modification studies, and multi-omics or computational approaches. Specific experimental examples include WRKY33, WRKY53, and group IId WRKY–OBE complexes. The text references four figures and two tables, none of which were provided in the submitted material.
- **Missing materials affecting confidence** Figures 1–4 and Tables 1–2 were not included in the provided material. Their absence limits assessment of how well the visual and tabular summaries support the textual claims. Additionally, the reference list was not provided, so the accuracy and completeness of citations could not be verified.

## Reviewer
- **Overall assessment** This review article addresses a genuine and important problem in plant transcriptional regulation: the apparent paradox between the broad genomic distribution of W-box motifs and the highly selective, context-dependent outputs of WRKY transcription factors. The authors propose a conceptual framework, the "WRKY regulatory code," that integrates five regulatory layers. The framework is clearly articulated, internally consistent, and useful for organizing a disparate literature. The emphasis on falsifiability and the inclusion of specific predictions are commendable and elevate the manuscript beyond a purely descriptive review. However, the manuscript has several weaknesses. The novelty of the framework is partially overstated, as many of the individual layers have been discussed in prior reviews, and the claim that this constitutes a "code" in a strong sense is not fully justified. The evidence base is heavily weighted toward Arabidopsis and a small number of WRKY factors, and the authors acknowledge but do not fully address the question of generalizability. The sections on multi-omics and machine learning are programmatic and lack concrete examples of successful application to WRKY biology. The writing is generally clear but occasionally repetitive, and some sections would benefit from tighter organization. Overall, the manuscript presents a valuable conceptual synthesis, but its impact would be strengthened by a more critical engagement with the limits of the framework and by more specific guidance on how to test it empirically.

- **Who would be interested in the results, and why** Researchers studying plant transcription factors, particularly WRKY family members, will find the integrative framework useful for situating their work within a broader regulatory context. Plant molecular biologists and geneticists working on stress responses, especially those interested in the mechanistic basis of specificity, will appreciate the synthesis of chromatin, post-translational, and interaction-based regulation. The sections on multi-omics and machine learning may appeal to computational biologists and systems biologists working on plant gene regulatory networks. Finally, crop biotechnologists interested in engineering stress tolerance may find the discussion of promoter and epigenetic editing relevant to translational applications.

- **Major strengths**
  1. The manuscript addresses a fundamental and unresolved question in plant biology: how specificity is achieved by transcription factors that bind short, abundant DNA motifs.
  2. The five-layer framework is clearly defined and provides a useful organizational structure for integrating diverse experimental findings.
  3. The inclusion of specific, falsifiable predictions is a notable strength and distinguishes this review from many others in the field.
  4. The use of representative examples (WRKY33, WRKY53, WRKY–OBE complexes) grounds the conceptual discussion in concrete experimental evidence.
  5. The discussion of multi-omics and machine learning approaches is forward-looking and identifies practical strategies for testing the framework.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Conceptual novelty and framing
- **Claim pointer** The authors claim that the "WRKY regulatory code" is a novel integrative framework that resolves key paradoxes in WRKY biology.
- **Evidence pointer** Abstract; Introduction; Section "The WRKY regulatory code as an integrative model"
- **Concern** The claim of novelty is not fully substantiated. Many of the individual regulatory layers, including chromatin accessibility, post-translational modifications, and protein–protein interactions, have been discussed in previous reviews of WRKY biology and transcription factor function more broadly. The term "code" implies a systematic, decipherable mapping between regulatory inputs and outputs, but the manuscript does not provide evidence that such a mapping exists or is achievable. The framework is better described as a heuristic organizing principle than a code in the strong sense. The authors should more carefully distinguish what is genuinely new in their synthesis from what has been previously proposed, and should temper the claim that the framework "resolves" paradoxes when it primarily reframes them.
- **Why it matters** If the novelty is overstated, the manuscript risks being seen as a repackaging of known concepts rather than a genuine conceptual advance. This affects the perceived contribution to the field and the likelihood that the framework will be adopted by other researchers.
- **Resolution test** The authors should revise the introduction and discussion to explicitly acknowledge prior integrative models of transcription factor specificity, and should articulate what specific, testable predictions follow from their framework that would not follow from a simpler additive model of the individual layers.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and evidence base
- **Claim pointer** The authors state that the WRKY regulatory code provides a general framework for understanding WRKY specificity across stresses, tissues, and developmental contexts, and across plant species.
- **Evidence pointer** Abstract; Section "The WRKY regulatory code as an integrative model"; Table 2 (referenced, not provided)
- **Concern** The evidence base is heavily weighted toward Arabidopsis and a small number of WRKY factors (WRKY33, WRKY53, group IId WRKYs). The authors acknowledge this limitation in the final section but do not adequately address how the framework might apply to the large number of WRKY family members in crop species with expanded gene families and distinct regulatory landscapes. The claim of generalizability is therefore not well supported by the evidence presented. The manuscript would benefit from a more systematic survey of what is known about WRKY regulation in diverse species, or from a more explicit statement of the conditions under which the framework is expected to apply.
- **Why it matters** The stated ambition of the framework is to provide a general model for WRKY biology. If the evidence is limited to a few well-studied cases, the framework may be overgeneralized, and its utility for crop improvement may be overstated.
- **Resolution test** The authors should either provide additional examples from non-Arabidopsis species and a broader range of WRKY factors, or explicitly scope the framework as applying primarily to the well-characterized cases and identify what additional data would be needed to test its generality.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Empirical grounding of the multi-omics and machine learning sections
- **Claim pointer** The authors state that multi-omics integration and machine learning can decode and empirically test the WRKY regulatory code.
- **Evidence pointer** Sections "Multi-omics approaches to dissect WRKY regulatory specificity" and "Artificial intelligence and predictive modeling of WRKY regulatory networks"
- **Concern** The sections on multi-omics and machine learning are largely programmatic. The authors describe general approaches (ATAC-seq, ChIP-seq, single-cell RNA-seq, PlantDeepSEA, ChromBPNET, GenomicLinks) but do not provide a single concrete example of a study that has successfully integrated these data types to predict WRKY target genes or regulatory outputs. The claim that these approaches "can decode" the regulatory code is therefore not empirically supported. The authors should either provide examples of successful applications in related systems or clearly frame these sections as proposals for future work rather than established capabilities.
- **Why it matters** The credibility of the framework depends in part on the feasibility of the proposed testing strategies. If the computational and multi-omics approaches are presented as more mature than they are, the manuscript may mislead readers about the current state of the field.
- **Resolution test** The authors should either identify published studies that have applied integrative multi-omics or machine learning to WRKY regulation, or revise the language to clearly indicate that these are proposed approaches that have not yet been fully realized.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency and terminology
- **Claim pointer** The authors define the WRKY regulatory code as comprising five layers, but the relationship between the layers is not always clearly specified, and the terminology varies across sections.
- **Evidence pointer** Abstract; Introduction; Section "The WRKY regulatory code as an integrative model"; Table 1 (referenced, not provided)
- **Concern** The manuscript describes the five layers as operating "sequentially and cooperatively," but the nature of the sequential relationship is not clearly defined. For example, does chromatin accessibility always precede protein–protein interaction, or can these layers act in any order? The term "regulatory code" is used interchangeably with "framework" and "model," which may confuse readers about the epistemic status of the proposal. Additionally, the relationship between the "cis-regulatory motif grammar" layer and the "chromatin accessibility" layer is not fully clarified, as both could be considered aspects of the same regulatory logic.
- **Why it matters** A conceptual framework is only as useful as its clarity. If the relationships between layers are vague, the framework becomes difficult to apply or test, and the claim of providing a "code" is weakened.
- **Resolution test** The authors should provide a more precise specification of how the five layers interact, perhaps with a formal diagram or a set of explicit rules, and should consistently use a single term (e.g., "framework" or "model") to describe the proposal.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability and organization
- **Affected element** Section "Cis-regulatory logic of W-box recognition"
- **Evidence pointer** Section text
- **Issue** This section contains substantial repetition. The point that W-box motifs are abundant and that their presence alone does not predict regulation is made multiple times, sometimes in nearly identical language.
- **Required correction** Condense the section to eliminate redundancy and focus on the key points: the structure of the W-box, the evidence for quantitative binding, and the implications for specificity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "Chromatin and epigenetic gating of WRKY occupancy"
- **Evidence pointer** Section text
- **Issue** The statement that "single-cytosine methylation within a W-box can lower the binding by multiple WRKY domains" is imprecise. It is unclear whether this refers to reduced binding affinity, reduced binding occupancy, or reduced transcriptional output. The cited evidence (Charvin [8]) is not described in sufficient detail to evaluate the claim.
- **Required correction** Clarify the nature of the effect (affinity, occupancy, or output) and provide more detail on the experimental system and the magnitude of the effect.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of evidence
- **Affected element** Section "Complex-dependent specificity via protein-protein interactions"
- **Evidence pointer** Section text
- **Issue** The section on WRKY–WRKY interactions cites Liu et al. [29] for the cooperative repression of ABI4 and ABI5, but does not describe the experimental approach (e.g., genetic, biochemical, or genomic) used to establish this conclusion. Without this context, the reader cannot assess the strength of the evidence.
- **Required correction** Briefly describe the experimental approach used in the cited study, and indicate whether the conclusion is based on genetic, biochemical, or genomic evidence.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity of figures
- **Affected element** Figures 1–4 (referenced, not provided)
- **Evidence pointer** Figure legends in text
- **Issue** The figure legends are descriptive but do not indicate what data or evidence each figure is based on. For example, Figure 1 is described as a schematic, but it is unclear whether it is based on specific experimental data or is a conceptual illustration. Similarly, Figure 4 presents a workflow, but it is unclear whether this workflow has been implemented or is proposed.
- **Required correction** Clarify in each figure legend whether the figure is based on published data, is a conceptual illustration, or is a proposed workflow. This will help readers interpret the figures correctly.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and style
- **Affected element** Throughout
- **Evidence pointer** Manuscript text
- **Issue** The manuscript uses the phrase "regulatory code" repeatedly, which becomes repetitive. Additionally, some sentences are overly long and could be split for clarity.
- **Required correction** Vary the terminology (e.g., "integrative framework," "multi-layer model") and edit for sentence length and clarity.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scope of literature coverage
- **Affected element** Section "Artificial intelligence and predictive modeling of WRKY regulatory networks"
- **Evidence pointer** Section text
- **Issue** The section cites PlantDeepSEA, ChromBPNET, and GenomicLinks as relevant computational tools, but does not discuss any studies that have applied these or similar tools specifically to WRKY transcription factors. The relevance of these tools to WRKY biology is therefore asserted rather than demonstrated.
- **Required correction** Either provide examples of WRKY-specific computational analyses or acknowledge that these tools have not yet been applied to WRKY regulation and discuss what would be needed to adapt them.

- **Technical failings that need to be addressed before the case is established**
  - R1-M3: The multi-omics and machine learning sections present proposed approaches as if they were established capabilities. The authors must either provide concrete examples of successful application or clearly frame these as future directions.
  - R1-M4: The relationship between the five regulatory layers is not specified with sufficient precision to allow the framework to be tested. A more formal specification of the interactions between layers is needed.
  - R1-m2: The description of the effect of cytosine methylation on WRKY binding is imprecise and needs clarification.

- **Assessment against Nature-style criteria**
  - **Originality**: The manuscript offers a synthesis of existing knowledge into a five-layer framework, which is a useful organizational contribution. However, the individual layers are well established, and the claim of a "code" is not fully justified. The originality is moderate and lies primarily in the integration rather than in new concepts or data.
  - **Scientific importance**: The question of transcription factor specificity is of fundamental importance in plant biology and beyond. The framework has the potential to guide future research and to inform crop improvement strategies. The importance is high, but the impact will depend on whether the framework can be operationalized and tested.
  - **Interdisciplinary readership**: The manuscript is likely to appeal primarily to plant molecular biologists and geneticists. The sections on multi-omics and machine learning may attract computational biologists, but the treatment of these topics is not sufficiently detailed to engage this audience deeply. The interdisciplinary reach is moderate.
  - **Technical soundness**: The manuscript is generally technically sound in its description of the cited literature, but the lack of detail on experimental approaches in some sections (e.g., the description of the Liu et al. study) and the imprecise description of methylation effects weaken the technical rigor. The absence of figures and tables limits full assessment.
  - **Readability for nonspecialists**: The manuscript is written in a clear and accessible style, with minimal jargon. The conceptual framework is explained well, and the use of examples (WRKY33, WRKY53) helps to ground the discussion. However, some sections are repetitive, and the multi-omics and machine learning sections may be challenging for readers without computational background. Overall readability is good.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable conceptual framework that addresses an important question in plant biology. The main issues are the overstatement of novelty, the lack of empirical grounding for the multi-omics and machine learning sections, and the imprecise specification of the relationships between regulatory layers. If these concerns are addressed, the manuscript would be a useful contribution to the field. However, in its current form, the case for the "WRKY regulatory code" as a novel and testable framework is not fully established.

## Risk / unsupported claims
- The claim that the "WRKY regulatory code" resolves key paradoxes in WRKY biology is not fully supported, as the framework primarily reframes the paradoxes rather than resolving them with new evidence.
- The claim that multi-omics integration and machine learning "can decode" the regulatory code is not supported by any concrete example of successful application to WRKY transcription factors.
- The claim that the framework is generalizable across the full WRKY family and across plant species is not supported by the evidence presented, which is heavily weighted toward Arabidopsis and a small number of WRKY factors.
- The statement that "single-cytosine methylation within a W-box can lower the binding by multiple WRKY domains" is imprecise and not adequately supported by the description of the cited evidence.
- The assertion that "WRKY-WRKY associations enable combinatorial regulation within the family, through distinct homo and heteromeric assemblies that modulate promoter selectivity, stabilize DNA binding, and diversify transcriptional outcomes" is presented as a general statement but is supported by only a limited number of examples.
- The claim that "disruption of WRKY–OBE complexes increases expression of stress-responsive genes and enhances drought tolerance" is presented without sufficient experimental detail to evaluate its robustness.