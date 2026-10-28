## Review setup
- **Input scope** Full manuscript text (review article, no figures or supplementary materials provided)
- **Assessment boundary** Scientific content, technical accuracy, completeness of coverage, and clarity of the presented review; no assessment of figures, tables, or supplementary data as they were not supplied
- **Shared manuscript claim summary** The manuscript argues that fluorescence correlation spectroscopy (FCS) and its spatiotemporal derivatives, implemented across different optical platforms, provide a uniquely quantitative bridge between molecular dynamics and cellular decision-making by mapping protein diffusion across three cellular compartments: the plasma membrane, the cytoplasm, and the nucleus. The authors claim that each compartment imposes distinct physical constraints on protein motion, and that FCS-based approaches reveal a common organisational principle: each environment is structured on spatial and temporal scales invisible to conventional imaging but accessible through correlation-based analyses.
- **Visible evidence base** The manuscript cites a substantial body of published literature (references 1–160) to support its claims. Specific quantitative values are provided for diffusion coefficients, confinement times, and oligomer-dependent transit times, attributed to cited studies. Methodological descriptions of FCS variants (e.g., pCF, RICS, STICS, iTIR-FCS, pCOMB) are presented with reference to original sources.
- **Missing materials affecting confidence** Figures 1–4 are referenced but not provided, limiting assessment of how well the visual summaries support the textual claims. No supplementary materials, tables, or detailed methodological protocols were supplied. The manuscript is a review, so primary data are not expected, but the absence of figures reduces the ability to evaluate the clarity and accuracy of the presented summaries.

## Reviewer
- **Overall assessment** This is a well-structured and comprehensive review that successfully synthesises a large body of FCS literature across three distinct cellular compartments. The organisation from plasma membrane to nucleus is logical and effective, and the authors make a compelling case for FCS as a uniquely quantitative tool for linking molecular dynamics to cellular function. The manuscript is clearly written and accessible to a broad audience, with technical concepts introduced in a digestible manner. The major strength is the integration of methodological detail with biological insight, particularly the emphasis on how oligomeric state and chromatin architecture govern nuclear transport. However, the review would benefit from a more critical discussion of the limitations and potential artefacts of the techniques described, and from a clearer articulation of how the field should prioritise future developments. The claims are generally well supported by the cited literature, though some statements lack specific references or quantitative context.
- **Who would be interested in the results, and why** This review will be of interest to researchers in quantitative cell biology, biophysics, and molecular imaging, particularly those using or considering FCS-based methods. It will also appeal to cell biologists studying membrane organisation, cytoplasmic transport, and nuclear dynamics, as it provides a clear framework for how FCS can address biological questions in these areas. The review is suitable for a broad readership, including graduate students and postdoctoral researchers entering the field, as well as established investigators seeking a current overview of FCS capabilities.
- **Major strengths** The manuscript provides a comprehensive and well-organised overview of FCS methodologies and their applications across three cellular compartments. The authors successfully integrate technical descriptions with biological insights, making the review accessible to nonspecialists while retaining sufficient depth for experts. The emphasis on how physical organisation of compartments actively regulates protein function is a valuable conceptual contribution. The inclusion of recent advances, such as SPAD arrays and machine learning-assisted analysis, demonstrates forward-looking perspective. The writing is clear, concise, and free of unnecessary jargon.
- **Major Concerns** The review lacks a critical assessment of the limitations and potential artefacts of the techniques described. For example, the challenges of FCS in live cells, such as photobleaching, fluorophore blinking, and the influence of optical aberrations on quantitative accuracy, are not discussed in depth. The authors also do not address the reproducibility of FCS measurements across laboratories or the standardisation of analysis protocols. Additionally, the claim that FCS provides a "uniquely quantitative bridge" is somewhat overstated, as other techniques such as single-particle tracking and FRAP also provide quantitative insights. The review would benefit from a more balanced discussion of the relative strengths and weaknesses of FCS compared to complementary methods. Finally, the conclusions section introduces several technical advances (e.g., iSCORS) without sufficient context or critical evaluation of their current maturity.
- **Minor Comments** The manuscript would benefit from a brief glossary of acronyms, as the number of FCS variants and related techniques is large and may overwhelm nonspecialist readers. The figures are referenced frequently but not provided, so their content cannot be assessed; the authors should ensure that the figures are self-explanatory and consistent with the text. Some statements in the introduction (e.g., "the physical organisation of cellular compartments is an active regulator of protein function") are presented as established fact but could be framed as a hypothesis supported by the reviewed evidence. The references are comprehensive, but a few key primary sources for specific quantitative claims (e.g., diffusion coefficients for eGFP in the nucleus) are not explicitly cited in the text.
- **Technical failings that need to be addressed before the case is established** None identified from the supplied material. The manuscript is a review, and the technical claims are consistent with the cited literature. However, the absence of figures and supplementary materials limits the ability to fully assess the accuracy of the presented summaries.
- **Assessment against Nature-style criteria**  
  *Originality*: The review is not entirely original in its topic, as other reviews on FCS exist, but it offers a novel organisational framework by tracing protein diffusion from the plasma membrane to the nucleus within a single narrative. This compartment-by-compartment approach is a distinctive contribution.  
  *Scientific importance*: The topic is of high importance to quantitative cell biology, and the review synthesises a large body of work that is currently dispersed across many primary papers. The emphasis on the physical organisation of compartments as a regulator of function is a timely and important perspective.  
  *Interdisciplinary readership*: The review is likely to appeal to researchers in biophysics, cell biology, and molecular imaging, and the writing is accessible enough to engage readers from adjacent fields. However, the heavy use of acronyms may limit accessibility for nonspecialists.  
  *Technical soundness*: The technical descriptions of FCS methods are accurate and consistent with the published literature. The authors correctly describe the capabilities and limitations of each technique, though a more critical discussion of artefacts and pitfalls would strengthen the review.  
  *Readability for nonspecialists*: The manuscript is generally well written and clear, but the density of technical detail and acronyms may be challenging for readers unfamiliar with FCS. A glossary and more explicit explanations of key concepts would improve accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The review is well executed and makes a valuable contribution to the field, but it would be strengthened by a more critical discussion of limitations and a clearer articulation of how FCS compares to complementary techniques. The absence of figures in the provided material prevents full assessment, but the textual content is of high quality.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Balance and critical assessment
- **Claim pointer** The manuscript presents FCS as a "uniquely quantitative bridge between molecular dynamics and cellular decision-making" and emphasises its strengths without a correspondingly detailed discussion of its limitations.
- **Evidence pointer** Abstract; Section 5 (Conclusions)
- **Concern** The review is strongly positive in its assessment of FCS capabilities but does not adequately address the known limitations and potential artefacts of the techniques. For example, photobleaching, fluorophore blinking, and the influence of optical aberrations on quantitative accuracy are not discussed in depth. The authors also do not address the reproducibility of FCS measurements across laboratories or the standardisation of analysis protocols. A more balanced treatment would strengthen the review's credibility and usefulness.
- **Why it matters** Readers, particularly those new to the field, may overestimate the reliability and ease of FCS measurements without an understanding of the technical challenges. A critical assessment of limitations is essential for a review to serve as a reliable guide for experimental design and interpretation.
- **Resolution test** The authors should add a subsection or paragraph in each compartment section (or in the conclusions) discussing the specific limitations and potential artefacts of the FCS variants described, with reference to published studies that have addressed these issues. The claim of "uniquely quantitative" should be tempered or justified with a comparison to complementary techniques.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Comparative context
- **Claim pointer** The manuscript positions FCS as superior to or more informative than other techniques, such as single-particle tracking (SPT) and fluorescence recovery after photobleaching (FRAP), but does not provide a systematic comparison.
- **Evidence pointer** Section 1 (Introduction), Section 5 (Conclusions)
- **Concern** The introduction briefly mentions SPT and FRAP as complementary techniques, but the review does not provide a systematic comparison of the strengths and weaknesses of FCS relative to these methods. For example, SPT offers single-molecule trajectories that can reveal heterogeneity and transient states that ensemble-averaged FCS may miss, while FRAP is simpler to implement and interpret for certain questions. The claim that FCS is a "uniquely quantitative bridge" is not fully justified without such a comparison.
- **Why it matters** A review that aims to establish FCS as a central tool in quantitative cell biology should provide readers with a clear understanding of when FCS is the method of choice and when other techniques may be more appropriate. Without this context, the review may be seen as one-sided.
- **Resolution test** The authors should add a comparative discussion, either in the introduction or in a dedicated section, that systematically compares FCS with SPT and FRAP in terms of temporal resolution, spatial resolution, sensitivity to heterogeneity, and suitability for different biological questions. This would strengthen the review's utility as a guide for method selection.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Future directions and prioritisation
- **Claim pointer** The conclusions section lists several technical advances (SPAD arrays, machine learning, phasor-based analysis, iSCORS) but does not critically evaluate their current maturity or prioritise the most impactful directions.
- **Evidence pointer** Section 5 (Conclusions)
- **Concern** The final section introduces several emerging technologies and analytical approaches, but the discussion is brief and does not provide a critical assessment of their readiness, limitations, or potential impact. For example, iSCORS is mentioned as a label-free approach, but its current sensitivity, specificity, and applicability to live-cell measurements are not discussed. The authors also do not prioritise which advances are most likely to transform the field in the near term.
- **Why it matters** A forward-looking review should help readers understand which developments are most promising and which are still in early stages. Without this critical evaluation, the conclusions section reads as a list of possibilities rather than a strategic assessment of the field's trajectory.
- **Resolution test** The authors should expand the conclusions section to provide a more detailed and critical assessment of each emerging technology, including its current stage of development, key challenges, and potential impact. They should also prioritise the most promising directions and explain their reasoning.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Overall manuscript
- **Evidence pointer** Throughout
- **Issue** The manuscript uses a large number of acronyms (e.g., FCS, pCF, RICS, STICS, iTIR-FCS, pCOMB, iSCORS) without a glossary, which may overwhelm readers who are not already familiar with the field.
- **Required correction** Add a glossary of acronyms at the end of the manuscript, or expand the first use of each acronym with a brief explanation of its meaning and purpose.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 3.3, Section 4.3
- **Evidence pointer** Location not provided
- **Issue** Some specific quantitative claims (e.g., diffusion coefficients for eGFP in the nucleus, transit times for oligomers) are presented without explicit citation to the primary source in the text, although references are listed in the bibliography.
- **Required correction** Ensure that all quantitative values are accompanied by a citation to the specific primary study from which they are drawn, to allow readers to verify the data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3
- **Evidence pointer** Location not provided
- **Issue** The statement that "cholesterol depletion with methyl-β-cyclodextrin (MβCD) or actin disruption with latrunculin A increases DiI mobility by less than 20%" is presented without a clear indication of the experimental context or the significance of this finding.
- **Required correction** Provide a brief interpretation of this result, explaining what it implies about the organisation of the plasma membrane and how it relates to the broader conclusions of the section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.4
- **Evidence pointer** Location not provided
- **Issue** The discussion of nuclear transport across NPCs is brief and does not mention the role of importin/exportin families beyond a single reference to importin α and β.
- **Required correction** Consider expanding this discussion to include a brief overview of the broader nuclear transport machinery and how FCS has contributed to understanding its dynamics.

## Risk / unsupported claims
- The claim that FCS is a "uniquely quantitative bridge between molecular dynamics and cellular decision-making" is not fully supported by the evidence presented, as the review does not systematically compare FCS with other quantitative techniques such as SPT or FRAP.
- The statement that "the physical organisation of cellular compartments is an active regulator of protein function" is presented as a conclusion, but the review does not critically evaluate alternative interpretations or the strength of the evidence for this claim.
- The assertion that "iSCORS provides complementary measurements of chromatin condensation dynamics in unlabelled nuclei on the millisecond timescale" is presented without sufficient detail on the technique's current limitations or validation, making it difficult to assess its readiness for routine use.
- The claim that "machine learning-assisted fitting is reducing the data and time required for robust diffusion-coefficient extraction" is presented without specific examples or references, making it difficult to evaluate the maturity and reliability of these approaches.