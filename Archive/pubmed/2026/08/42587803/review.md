## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, structural coherence, evidence quality, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors argue that PPAR nuclear receptor function is best understood through an ensemble-based conformational model rather than a static H12-switch mechanism, and that molecular dynamics simulations, particularly when integrated with experimental structural and biophysical methods, are essential for capturing the dynamic and allosteric nature of PPAR regulation across isoforms, ligand classes, and protein interaction contexts.
- **Visible evidence base** The manuscript is a narrative review citing published literature; no new experimental or simulation data are presented. The text references figures (Figures 1–5) and supplementary tables (Tables S1–S4) that were not provided for assessment.
- **Missing materials affecting confidence** Figures 1–5, Tables S1–S4, full reference list, and any supplementary text were not provided. This limits verification of specific claims tied to these materials and of the completeness of literature coverage.

## Reviewer
- **Overall assessment** This is a well-structured and thoughtful narrative review that synthesizes a broad and complex literature on PPAR conformational dynamics. The central thesis, that PPAR function is governed by conformational ensembles rather than a simple H12 switch, is timely and well supported by the cited literature. The authors demonstrate strong command of the field and make a compelling case for the integration of MD with experimental methods. The review is particularly strong in its treatment of PPARγ, ligand entry pathways, and the emerging role of multi-ligand occupancy. However, the review would benefit from a more critical and quantitative treatment of the MD methods themselves, a clearer articulation of the limitations of current simulation approaches, and a more balanced discussion of the evidence for and against the ensemble model across all three isoforms. The discussion of PPARβ/δ, while acknowledged as underdeveloped, could be more specific about what is known and what is missing. The section on disease-associated mutations is informative but could be strengthened by a more systematic framework for how MD can be used to predict or interpret pathogenic variants. Overall, the manuscript is a valuable contribution that will be of interest to the nuclear receptor and computational biology communities, but it requires revisions to sharpen its critical edge and to ensure that its claims are consistently calibrated to the strength of the underlying evidence.
- **Who would be interested in the results, and why** Researchers in nuclear receptor biology, structural biology, computational chemistry, and drug discovery will find this review valuable. It provides a comprehensive and current synthesis of how MD simulations have advanced understanding of PPAR dynamics, ligand recognition, and allosteric regulation. The review is also relevant for investigators studying other nuclear receptors, as the ensemble-based framework and methodological insights are broadly applicable. The discussion of disease-associated mutations and PTMs will interest clinicians and translational researchers focused on metabolic disease and cancer.
- **Major strengths** The review provides a clear and well-organized synthesis of a complex literature, effectively arguing for a paradigm shift from static to dynamic models of PPAR function. The emphasis on integrating MD with experimental validation is methodologically sound and appropriately cautious. The treatment of ligand entry/exit pathways and multi-ligand occupancy is particularly insightful and highlights important recent developments. The authors are also careful to distinguish between screening-oriented and mechanistic MD studies, which is a useful and necessary distinction for the field.
- **Major Concerns** The review is largely descriptive and could be more critical in evaluating the methodological quality and limitations of the cited MD studies. The central claim that MD has reshaped understanding of PPAR function is well supported, but the review does not adequately address the challenges of force field accuracy, sampling convergence, and the timescale gap between simulations and biological processes. The treatment of the three isoforms is uneven, with PPARγ receiving extensive coverage while PPARα and PPARβ/δ are comparatively brief; while this reflects the literature, the review could more explicitly discuss what specific questions remain unanswered for the less-studied isoforms. The section on disease-associated mutations, while useful, does not provide a clear framework for how MD can be used prospectively to interpret variants of unknown significance. The discussion of PTMs is forward-looking but lacks concrete examples of how MD has been or could be applied to these systems beyond the cited phosphorylation studies.
- **Minor Comments** The review would benefit from a figure summarizing the key conformational states and transitions discussed, as the current figures are referenced but not available for assessment. The authors use the term "conformational ensemble" frequently but could more precisely define what constitutes a distinct substate and how these are experimentally or computationally distinguished. The discussion of "graded activation" could be more quantitative, referencing specific energetic or population-based measures. The review would be strengthened by a brief discussion of the limitations of the ensemble model and alternative interpretations of the available data. The authors should ensure that all claims about specific studies are accurately represented and that the supplementary tables are comprehensive and well-organized.
- **Technical failings that need to be addressed before the case is established** No specific technical failings were identified in the text provided. However, the absence of the figures and supplementary tables prevents a full assessment of the technical accuracy of the presented data and summaries.
- **Assessment against Nature-style criteria** **Originality:** The review synthesizes existing literature but does not present new data or a novel conceptual framework. Its originality lies in the synthesis and perspective offered, which is valuable but not groundbreaking. **Scientific importance:** The topic is of high importance given the central role of PPARs in metabolism and disease, and the review addresses a key conceptual shift in the field. **Interdisciplinary readership:** The review is relevant to structural biology, computational chemistry, pharmacology, and cell biology, but its focus on MD methods may limit its accessibility to a broader biological audience. **Technical soundness:** The review is technically sound in its description of MD methods and their applications, but it lacks a critical assessment of the limitations of these methods. **Readability for nonspecialists:** The review is well-written and generally accessible, but assumes familiarity with nuclear receptor biology and MD terminology. It would benefit from a brief primer on key concepts for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The review makes a valuable contribution to the field and is well-suited for publication in a specialized journal. However, it requires revisions to strengthen its critical analysis of MD methods, to more explicitly address the limitations of the ensemble model, and to provide a more balanced treatment of the three isoforms. The absence of figures and supplementary tables in the provided materials must be resolved to allow full assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor
- **Claim pointer** The review states that MD simulations have become "essential" for interpreting PPAR regulation and that they can provide "atomistic resolution" of conformational dynamics.
- **Evidence pointer** Sections 1.1, 4.7, and 5.1
- **Concern** The review is largely uncritical of the MD methods used in the cited studies. It does not discuss the well-known limitations of MD, such as force field inaccuracies, limited sampling timescales, and the sensitivity of results to simulation parameters. The claim that MD is "essential" is strong and should be qualified by a discussion of what MD can and cannot currently deliver. For example, the review does not address whether the cited simulations have been validated against experimental data or whether the observed conformational states are robust across different force fields or simulation protocols.
- **Why it matters** A review that advocates for the use of MD should also educate the reader about its limitations. Without this critical perspective, the review may overstate the reliability of MD predictions and mislead readers who are not experts in computational methods. A balanced assessment is crucial for the field to progress and for experimentalists to appropriately interpret and use MD results.
- **Resolution test** The authors should add a section or paragraph that critically discusses the limitations of MD, including force field accuracy, sampling convergence, and the need for experimental validation. They should also provide specific examples where MD predictions have been confirmed or contradicted by experimental data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Balance and completeness
- **Claim pointer** The review concludes that "PPARγ is the clear benchmark for dynamic and integrative structural studies" and that "PPARα and PPARβ/δ remain less comprehensively characterized."
- **Evidence pointer** Sections 1.2 and 6
- **Concern** While this statement is likely accurate, the review does not adequately explore the reasons for this imbalance or its consequences. The authors could more explicitly discuss what specific aspects of PPARα and PPARβ/δ dynamics are unknown, what experimental or computational challenges have hindered progress, and what opportunities exist for future research. The review would be more valuable if it provided a more detailed roadmap for studying the less-characterized isoforms, rather than simply noting the gap.
- **Why it matters** The review's stated goal is to provide a comprehensive overview of PPAR dynamics. A more detailed discussion of the gaps in our understanding of PPARα and PPARβ/δ would make the review more useful for researchers planning future studies and would highlight the potential for new discoveries in these areas.
- **Resolution test** The authors should expand the discussion of PPARα and PPARβ/δ to include specific unanswered questions, potential experimental approaches, and the likely impact of addressing these gaps. This could be integrated into the existing sections or presented as a separate subsection.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Conceptual clarity
- **Claim pointer** The review uses the term "conformational ensemble" to describe the functional states of PPARs and argues that ligands "reshape" this ensemble.
- **Evidence pointer** Sections 1.1, 4.3, and 5.2
- **Concern** The concept of a "conformational ensemble" is central to the review's thesis, but it is not precisely defined. The authors do not specify how many distinct substates are thought to exist, what the structural features of these substates are, or how they are experimentally or computationally distinguished. The review would be strengthened by a more rigorous definition of the ensemble model and a discussion of the evidence for and against it. For example, are the substates discrete or continuous? What is the energy landscape connecting them? How do different ligands shift the populations?
- **Why it matters** A vague central concept weakens the review's argument. A more precise definition would help readers understand the model and evaluate the evidence. It would also provide a clearer framework for future research aimed at testing the model.
- **Resolution test** The authors should provide a more detailed description of the conformational ensemble model, including a definition of substates, a discussion of the energy landscape, and a summary of the experimental and computational evidence supporting it. This could be presented as a new figure or a dedicated subsection.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 1.1
- **Evidence pointer** Section 1.1
- **Issue** The term "conformational ensemble" is used repeatedly but not defined for the reader.
- **Required correction** Provide a brief definition of the term when it is first introduced.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 5.4
- **Evidence pointer** Section 5.4
- **Issue** The discussion of PTMs is forward-looking but lacks specific examples of how MD has been applied to study these modifications beyond the cited phosphorylation studies.
- **Required correction** Add a brief discussion of any existing MD studies on SUMOylation or ubiquitination of PPARs, or explicitly state that such studies are lacking.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.3
- **Evidence pointer** Section 4.3
- **Issue** The term "graded activation" is used but not quantitatively defined.
- **Required correction** Briefly explain what is meant by graded activation and how it is measured or inferred.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Figures 1–5
- **Issue** The figures are referenced but were not provided for assessment.
- **Required correction** Ensure that all figures are included in the final submission and that they are of high quality and clearly support the text.

## Risk / unsupported claims
- The claim that MD simulations are "essential" for interpreting PPAR regulation is a strong statement that is not fully supported by the evidence presented, as the review does not critically assess the limitations of MD.
- The claim that "PPARγ is the clear benchmark" is supported by the literature cited, but the review does not provide a detailed comparison of the depth of research across isoforms.
- The statement that "MD is most informative when integrated with experimental validation" is a reasonable perspective, but the review does not provide a systematic analysis of which studies have achieved this integration and which have not.
- The discussion of "graded activation" and "conformational ensembles" is presented as established fact, but the review does not critically evaluate the evidence for these concepts.
- The claim that "future simulations should increasingly model biologically realistic assemblies" is a reasonable recommendation, but the review does not discuss the technical challenges of doing so.