## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary material description.
- **Assessment boundary** Scientific validity, technical soundness, and interpretation of the reported data. No assessment of editorial fit or publication policy.
- **Shared manuscript claim summary** The authors identify two peptide segments in the androgen receptor (AR) A/B domain, spanning amino acids 357-457 and 514-557, that mediate functional association with the transcription factor ELK1. These segments are validated through deletion mapping, orthogonal binding assays, and functional assays in prostate cancer cells, with implications for therapeutic targeting.
- **Visible evidence base** Results sections describing two-hybrid assays, GST-pulldown, BRET, and colony formation assays; figures referenced as Fig. 1-5 and Supplemental Fig. 1; methods sections for reagents, plasmids, and assays.
- **Missing materials affecting confidence** Raw data (e.g., western blot images, quantitative values with error bars) are not provided. Figure panels are referenced but not shown. Statistical details for specific comparisons are incomplete. No structural or biophysical data beyond binding assays.

## Reviewer
- **Overall assessment** The manuscript presents a systematic and well-controlled mapping of ELK1-interacting regions in the AR A/B domain, with corroborating evidence from multiple assays. The identification of two discrete segments is plausible and potentially useful for future structural and drug design studies. However, several technical and interpretive issues need clarification, particularly regarding the specificity of the two-hybrid assay, the quantitative interpretation of deletion effects, and the physiological relevance of the colony formation data. The case for a parallel binding mode is suggestive but not definitive.
- **Who would be interested in the results, and why** Researchers studying androgen receptor biology, prostate cancer therapeutics, and protein-protein interactions involving intrinsically disordered transcription factor domains. The findings may inform efforts to develop small molecule inhibitors targeting the AR-ELK1 complex, which is of interest to the prostate cancer drug development community.
- **Major strengths** The study uses a logical deletion mapping strategy with appropriate controls to distinguish effects on ELK1 binding from effects on intrinsic transcriptional activity. Validation across multiple assay platforms (two-hybrid, GST-pulldown, BRET) strengthens confidence in the identified segments. The functional relevance is tested in a physiologically relevant prostate cancer cell line. The discussion of structural implications is measured and appropriately cautious.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (two-hybrid assay specificity), R1-M2 (quantitative interpretation of deletion effects), R1-M3 (BRET validation scope), R1-M4 (colony formation assay interpretation).
- **Assessment against Nature-style criteria** Originality: Moderate. The study extends prior work by the same group on AR-ELK1 interaction, but the identification of specific interacting segments is a useful incremental advance. Scientific importance: Moderate. The findings have potential therapeutic implications but do not fundamentally alter current understanding of AR or ELK1 function. Interdisciplinary readership: Limited. The work is primarily of interest to prostate cancer and transcription factor researchers. Technical soundness: Generally adequate, but with concerns as detailed below. Readability for nonspecialists: The manuscript is clearly written, though some assay details assume familiarity with molecular biology techniques.
- **Recommendation posture** Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The two-hybrid assay identifies amino acids 357-457 and 514-557 as required for association with ELK1.
- **Evidence pointer** Results section "Deletion mapping to identify ELK1 recognition segments in the A/B domain of AR", Fig. 1B
- **Concern** The two-hybrid assay relies on transcriptional activation by VP16 fused to AR(A/B) deletion constructs. The control assay (Fig. 1D) shows that deletions do not reduce intrinsic transcriptional activity of Gal4-AR(A/B)-VP16 fusions, but this control uses a different fusion configuration (Gal4-AR(A/B)-VP16) than the test assay (AR(A/B)-VP16 with Gal4-ELK1). It is unclear whether the control fully recapitulates the context of the test assay, particularly regarding potential steric effects of deletions on VP16 activity or on the Gal4-ELK1 interaction surface. The authors should clarify whether the control assay was performed with the same promoter-reporter and cell line, and whether any deletions could affect VP16 function independently of ELK1 binding.
- **Why it matters** If the two-hybrid results are confounded by deletion effects on VP16 activity or on the Gal4-DNA binding domain, the mapping conclusions could be incorrect.
- **Resolution test** Provide a detailed description of the control assay conditions, or perform an additional control using a Gal4-VP16 fusion with the same deletions to directly test VP16 activity in the absence of ELK1.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** Deletion of amino acids 357-457 and 514-557 in full-length AR reduces synergy with ELK1, with the downstream deletion having a greater effect.
- **Evidence pointer** Results section "Validation of mapped ELK1 recognition segments in full-length AR", Fig. 3A
- **Concern** The quantitative difference between the effects of the upstream and downstream deletions is described qualitatively (partial vs. near-full inhibition). No statistical analysis is provided for the comparison between the two deletion constructs. Additionally, the authors do not report whether the deletion constructs are expressed at comparable levels to wild-type AR, which could affect the interpretation of the synergy assays.
- **Why it matters** The claim that the downstream segment is more critical for ELK1 synergy is central to the proposed parallel binding model. Without statistical support and expression controls, this conclusion is not robust.
- **Resolution test** Provide quantitative data with statistical analysis for the synergy assays, and include western blot data showing expression levels of the deletion constructs relative to wild-type AR.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** BRET assay validates the ELK1-interacting region in AR-V7 (amino acids 358-557).
- **Evidence pointer** Results section "Validation of ELK1 binding segments in AR using orthogonal methods", Fig. 4B
- **Concern** The BRET assay uses an AR-V7 construct with a large deletion (amino acids 50-357), leaving only the region containing the two mapped segments. This does not directly test whether the individual segments are required for binding, as the deletion removes most of the A/B domain. The negative control (Supplemental Fig. 1) is mentioned but not described in detail.
- **Why it matters** The BRET data support the general region but do not validate the specific mapping of the two segments. This weakens the orthogonal validation claim.
- **Resolution test** Perform BRET with AR constructs containing deletions of the individual segments (e.g., Δ358-457 and Δ514-557) to directly test their requirement for ELK1 binding.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** Deletion of the ELK1-interacting segments in AR inhibits prostate cancer cell colony formation.
- **Evidence pointer** Results section "Physiological validation of the ELK1 interacting segments in AR", Fig. 5B
- **Concern** The colony formation assay shows that deletion of either segment reduces colony growth, but the authors do not discuss whether this effect is specifically due to loss of ELK1 binding or to other functions of the deleted regions. The A/B domain is known to interact with multiple co-regulators, and the deletions could disrupt these interactions independently of ELK1.
- **Why it matters** The physiological relevance claim depends on the specificity of the effect. If the deletions affect other AR functions, the data do not directly support the role of ELK1 interaction in cell growth.
- **Resolution test** Include a rescue experiment with an ELK1-binding-deficient AR mutant that retains other A/B domain functions, or show that the deletion constructs do not affect other known AR activities.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "Disruption of the ELK1-AR complex is a validated potential means of therapeutic intervention in PCa."
- **Issue** The term "validated" is strong, as the therapeutic potential is based on prior studies by the same group. Consider softening to "proposed" or "suggested."
- **Required correction** Revise wording to reflect the level of evidence.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Statistical Analysis"
- **Evidence pointer** Methods section "Statistical Analysis"
- **Issue** The statistical methods are described briefly. It is unclear how many independent replicates were performed for each assay, and whether error bars represent standard deviation or standard error.
- **Required correction** Provide details on the number of replicates and the definition of error bars in figure legends.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, Fig. 2
- **Evidence pointer** Results section "Deletion mapping to identify ELK1 recognition segments in the A/B domain of AR", Fig. 2
- **Issue** The small internal deletions within amino acids 457-514 are described as having no effect, but the data are not shown in the text. It is unclear how many deletions were tested and whether they covered the entire segment.
- **Required correction** Clarify the number and positions of the internal deletions tested.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, "It is possible that KCI807 binds to one of the two ELK1 interacting segments in AR"
- **Evidence pointer** Discussion section
- **Issue** This speculation is not directly supported by data in the manuscript. It is acceptable as a hypothesis but should be clearly labeled as such.
- **Required correction** Add a phrase such as "we speculate" or "it is plausible."

## Risk / unsupported claims
- The claim that the two segments are "necessary and sufficient" for ELK1 association is not fully supported, as the sufficiency is inferred from deletion data but not directly tested with isolated peptides or minimal constructs.
- The proposed parallel binding mode of AR and ELK1 is speculative and not directly tested.
- The statement that the downstream segment deletion "nearly fully inhibited" cell growth is not quantitatively supported.
- The physiological relevance of the identified segments for prostate cancer growth is inferred from a single cell line and may not generalize.