## Review setup
- **Input scope** Full manuscript text (review article, published in Polymers, 2023)
- **Assessment boundary** Scientific content, structural coherence, evidence quality, and clarity of the review as presented in the supplied text; no external literature verification performed
- **Shared manuscript claim summary** The authors present a narrative review of nucleosome dynamics, focusing on three regulatory categories: histone modifications, DNA methylation, and nucleosome-interacting factors (transcription factors, remodeling proteins, cations). They argue that these factors jointly modulate dynamic modes (unwrapping/wrapping, sliding, stacking) and propose that integrating computational modeling, experiments, and deep learning will advance mechanistic understanding.
- **Visible evidence base** Abstract, Introduction, Sections 2.1–2.3, Section 3, Section 4, Section 5; references cited numerically but not listed in the supplied material; figures mentioned (Figure 1a–e, Figure 2, Figure 3a,b) but not provided
- **Missing materials affecting confidence** Reference list, figure images, figure captions, table contents (Table 1 mentioned in Section 1), and any supplementary information; no experimental data or simulation details are included beyond narrative descriptions

## Reviewer
- **Overall assessment** This is a broad, descriptive review that catalogues selected studies across three regulatory factors influencing nucleosome dynamics. The topic is timely and of potential interest to biophysicists, chromatin biologists, and computational biologists. However, the manuscript reads more as an annotated summary of individual findings than as a critical synthesis. The central claim that these factors operate in a "unified framework" is asserted but not developed into a mechanistic model. The review lacks depth in evaluating methodological strengths and limitations of the cited studies, and the proposed integration with deep learning is speculative without concrete examples or validation. The writing is generally clear but occasionally repetitive, and the absence of figures and reference details in the supplied material limits full assessment.
- **Who would be interested in the results, and why** Researchers in chromatin structure and dynamics, epigenetic regulation, and computational biophysics would find this review useful as an entry point to the literature. Those working on nucleosome remodeling, histone post-translational modifications, or DNA methylation effects on chromatin may appreciate the organized summary of representative studies. The discussion of multiscale modeling and deep learning could appeal to computational scientists seeking application areas. However, specialists may find the treatment too superficial to provide new insights.
- **Major strengths** The manuscript covers a wide range of relevant studies and organizes them into clear thematic categories. The distinction between dynamic modes (unwrapping, sliding, stacking) provides a useful conceptual scaffold. The inclusion of both experimental and computational approaches is commendable, and the authors make an effort to connect molecular-level dynamics to higher-order chromatin structure and disease relevance. The writing is accessible to nonspecialists, with technical terms generally explained.
- **Major Concerns** The review lacks critical evaluation of the cited studies; it often reports findings without assessing methodological rigor or conflicting evidence. The "unified framework" claim is not substantiated by a coherent model or synthesis. The section on deep learning is underdeveloped and reads as a forward-looking statement rather than a substantive discussion. The manuscript does not clearly distinguish established findings from speculative interpretations. The absence of a critical discussion on limitations of current computational methods (e.g., force field accuracy, sampling limitations) weakens the review's utility.
- **Minor Comments** Some terminology is used loosely (e.g., "dynamic features" is not precisely defined). The transition between sections could be smoother, with more explicit connections between regulatory factors. The role of cations is discussed briefly but could be expanded given its mechanistic importance. The figures are referenced but not described in the text, making it difficult to assess their contribution. The conclusion is somewhat generic and does not highlight specific open questions or testable predictions.
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide a critical comparison of computational methods (e.g., all-atom vs. coarse-grained vs. mesoscale) in terms of accuracy and applicability. The claim that deep learning will provide "promising opportunities" is not supported by any specific example or feasibility analysis. The review does not address potential contradictions between studies (e.g., conflicting results on DNA methylation effects on nucleosome stability). The "unified framework" is never explicitly defined or diagrammed, despite being a central claim.
- **Assessment against Nature-style criteria** Originality: The review does not present new data or a novel conceptual framework; it synthesizes existing literature in a conventional manner. Scientific importance: The topic is important, but the review does not advance the field beyond existing summaries. Interdisciplinary readership: The manuscript could appeal to a broad audience, but the depth is insufficient for specialists and the synthesis is too shallow for nonspecialists to gain deep insight. Technical soundness: The descriptions of cited studies appear accurate based on the text, but the lack of critical evaluation limits confidence. Readability for nonspecialists: The writing is clear and accessible, with adequate background provided. Overall, the manuscript does not meet the standard of a Nature-level review, which would require a more critical, integrative, and forward-looking perspective.
- **Recommendation posture** Currently not established from the provided evidence. The review is competent as a descriptive summary but lacks the critical depth, synthesis, and novel perspective expected of a high-impact review. It may be suitable for a specialized journal with a more permissive review standard, but it does not make a compelling case for publication in a top-tier venue.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** The authors claim that the review provides "a unified framework of three main factors" for understanding nucleosome dynamics regulation.
- **Evidence pointer** Section 1, last paragraph; Section 3, first paragraph
- **Concern** The manuscript asserts a "unified framework" but never defines what this framework entails. The three categories (histone modifications, DNA methylation, interacting factors) are presented as parallel lists of studies, with no explicit model of how they interact, compete, or synergize. The term "crosstalk" is used in Section 3, but the discussion is limited to a single example (UHRF1 binding) and does not generalize. The review does not propose testable hypotheses or a mechanistic diagram that would constitute a framework.
- **Why it matters** A central claim of the review is that these factors operate together, but without a defined framework, the claim is rhetorical rather than substantive. Readers cannot evaluate or build upon the proposed synthesis.
- **Resolution test** The authors should either (a) explicitly define the framework, including a diagram or conceptual model showing how the three factors interact at molecular and structural levels, or (b) revise the claim to accurately reflect that the review is a catalogue of individual regulatory mechanisms without a unifying model.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Critical evaluation
- **Claim pointer** The review presents findings from multiple studies as established facts without assessing methodological strengths, limitations, or conflicting results.
- **Evidence pointer** Sections 2.1–2.3, throughout
- **Concern** For example, in Section 2.2.2, the authors cite studies with apparently contradictory conclusions: Li et al. report that DNA methylation does not constrain breathing motion, while Lee et al. report tighter wrapping induced by methylation. The review does not discuss these discrepancies or attempt to reconcile them. Similarly, computational studies are described without commenting on force field limitations, sampling timescales, or model validation. The review reads as an uncritical summary rather than a critical assessment.
- **Why it matters** A review's value lies in its ability to evaluate evidence quality and guide readers through contested findings. Without critical evaluation, the review risks misleading nonspecialists and offers little to specialists.
- **Resolution test** The authors should add a critical discussion for each regulatory factor, highlighting methodological strengths and weaknesses of key studies, and explicitly addressing conflicting results with possible explanations (e.g., differences in experimental conditions, sequence context, or computational methods).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Depth of computational discussion
- **Claim pointer** The review states that "computational modeling and simulation can be applied as an alternative tool to complement experimental approaches" and later discusses multiscale models and deep learning.
- **Evidence pointer** Section 1, paragraph 4; Section 4, paragraphs 2–3
- **Concern** The discussion of computational methods is superficial. The authors mention all-atom MD, coarse-grained modeling, and mesoscale modeling but do not explain the trade-offs between these approaches (e.g., accuracy vs. computational cost, timescales accessible, system sizes). The description of the 1-Cylinder-per-Nucleosome (1CPN) model is brief and does not explain how it improves upon existing models. The deep learning discussion is speculative, citing only two examples without explaining how deep learning would be applied to nucleosome dynamics or what challenges exist (e.g., data availability, feature representation, interpretability).
- **Why it matters** For a review that claims to integrate computational and experimental approaches, the computational side is underdeveloped. Readers interested in using these methods would not gain sufficient understanding to evaluate or apply them.
- **Resolution test** The authors should expand the computational discussion to include: (a) a comparison of method capabilities and limitations, (b) specific examples of how computational predictions were validated experimentally, and (c) a more concrete proposal for deep learning applications, including potential input features, training data sources, and expected outcomes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scope and focus
- **Claim pointer** The review aims to cover "multifactorial regulation" of nucleosome dynamics, but the treatment of each factor is uneven.
- **Evidence pointer** Sections 2.1–2.3
- **Concern** Section 2.1 (histone modifications) is the longest and most detailed, while Section 2.3.3 (cations) is brief and lacks depth. The discussion of transcription factors focuses heavily on pioneer factors (Oct4, Sox2) but does not address other classes of TFs that bind nucleosomes. The review does not clearly justify why these three categories were chosen over others (e.g., histone variants, DNA sequence effects, non-coding RNAs).
- **Why it matters** Uneven coverage undermines the claim of a comprehensive review and may reflect selection bias in the literature cited. Readers may question whether the review is representative of the field.
- **Resolution test** The authors should either (a) expand the underdeveloped sections to match the depth of Section 2.1, or (b) explicitly state the criteria for selecting the covered factors and acknowledge the limitations of scope.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Section 1
- **Evidence pointer** Abstract, first sentence; Section 1, paragraph 1
- **Issue** The term "nucleosome dynamics" is used throughout but not explicitly defined. It appears to encompass wrapping/unwrapping, sliding, and stacking, but the relationship between these modes and the term "dynamics" is not clarified.
- **Required correction** Provide a brief definition of "nucleosome dynamics" in the Introduction, specifying which dynamic modes are included and how they relate to each other.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure integration
- **Affected element** Figures 1–3
- **Evidence pointer** Section 1, paragraph 2; Section 3, first paragraph; Section 4, paragraph 2
- **Issue** Figures are referenced but not described in the text. For example, Figure 1a,b is mentioned as showing structural components, but the text does not explain what the reader should observe or how the figure supports the narrative. Figure 3b is referenced in the context of deep learning but its content is not described.
- **Required correction** Add brief figure descriptions in the text, explaining the key features and how they illustrate the points being made.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reference completeness
- **Affected element** All sections
- **Evidence pointer** Throughout
- **Issue** The reference list is not provided in the supplied material, making it impossible to verify the accuracy of citations or assess the currency of the literature. Some statements are presented without citations (e.g., "the thermal energy is reported on the scale of ~0.6 kcal/mol" in Section 1).
- **Required correction** Ensure all factual claims are supported by citations, and provide a complete reference list with full bibliographic details.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity of conclusions
- **Affected element** Section 5
- **Evidence pointer** Section 5, entire
- **Issue** The conclusion summarizes the main points but does not identify specific open questions or future directions beyond a general call for "further development of specific physical models" and "application of deep learning." It does not synthesize the three regulatory factors into a coherent take-home message.
- **Required correction** Strengthen the conclusion by highlighting key unresolved questions, potential experimental approaches to address them, and how the proposed framework could guide future research.

## Risk / unsupported claims
- The claim that "the integration of computational and experimental approaches, the construction of physical modes for nucleosomes, and the application of deep learning techniques will provide promising opportunities" is speculative and not supported by specific evidence or examples in the text.
- The statement that "the thermal energy is reported on the scale of ~0.6 kcal/mol" (Section 1) is presented without a citation, making it unverifiable.
- The assertion that "the existence of methyl groups was deduced to account for the observed structural and dynamic differences of nucleosomes" (Section 2.2.2) is presented as a conclusion without discussing alternative explanations or limitations.
- The claim that "the combination of these regulatory factors determines the dynamic characteristics of the nucleosome" (Section 3) is asserted but not demonstrated with specific examples of combined effects beyond the single UHRF1 case.
- The deep learning discussion in Section 4 implies feasibility without addressing data requirements, model interpretability, or validation challenges, making the claim of "promising opportunities" unsupported.