## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions)
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and internal consistency of the reported findings
- **Shared manuscript claim summary** The authors report identification of 14 CcWOX transcription factors in Cinnamomum camphora, their phylogenetic classification into three clades, tissue-specific expression patterns, AlphaFold3-predicted 3D structures, and a putative CcWOX3–CcLBD33 interaction supported by BiFC assays
- **Visible evidence base** Tables 1; Figures 1–7 (referenced but not provided); Methods sections 4.1–4.5; statistical descriptions in Sections 2.4 and 4.3
- **Missing materials affecting confidence** Figures 1–7 (all referenced but not visible); Table 1 (referenced but not visible); raw RNA-seq data; qRT-PCR primer sequences; AlphaFold3 confidence metrics (pLDDT values, PAE plots); BiFC quantification raw data; statistical test outputs (F-values, degrees of freedom, effect sizes)

## Reviewer
- **Overall assessment** This manuscript presents a descriptive genomic characterization of the WOX gene family in Cinnamomum camphora, combined with computational structure prediction and a single protein–protein interaction validation. The work is competent in its bioinformatic scope and the BiFC experiment is appropriately controlled. However, the scientific advance over existing WOX family characterizations in other woody species is incremental, and the central claim of a functional WOX–LBD module is not established from the provided evidence. The interaction between CcWOX3 and CcLBD33 is demonstrated physically but its biological relevance remains speculative. The manuscript would benefit from clearer presentation of structural prediction confidence and more rigorous statistical reporting.
- **Who would be interested in the results, and why** Researchers studying plant transcription factor families, particularly WOX genes in woody species, may find the genomic inventory and expression patterns useful as a reference. Those interested in AI-based protein structure prediction applied to plant proteins may note the AlphaFold3 workflow. The CcWOX3–CcLBD33 interaction, if further validated, could interest root development biologists, though the current evidence is too preliminary for broad appeal.
- **Major strengths** 1) Systematic identification pipeline combining HMM and BLASTp with cross-validation. 2) Comprehensive phylogenetic analysis across three species with clear clade assignment. 3) Inclusion of synteny analysis to infer duplication mechanisms. 4) Integration of AlphaFold3 prediction with in planta BiFC validation, representing a modern structural biology approach. 5) Transparent acknowledgment of limitations and future directions.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (structural prediction confidence not reported), R1-M2 (statistical reporting inadequate), R1-M3 (BiFC swapped construct interpretation), R1-M4 (functional significance claim unsupported)
- **Assessment against Nature-style criteria** Originality: Moderate. WOX family characterizations exist for multiple species; the novelty here is limited to the specific organism and the AlphaFold3 application. Scientific importance: Low to moderate. The descriptive genomic analysis does not reveal new biological principles, and the interaction claim lacks functional validation. Interdisciplinary readership: Limited. The work is primarily of interest to plant molecular biologists and genomicists; the structural prediction component is not developed deeply enough to attract structural biology audiences. Technical soundness: Generally adequate for the bioinformatic analyses, but the structural prediction confidence metrics are absent and statistical reporting is incomplete. Readability for nonspecialists: Acceptable. The manuscript is clearly written, though some sections assume familiarity with plant development terminology.
- **Recommendation posture** Currently not established from the provided evidence. The descriptive genomic characterization is acceptable as a family-level report, but the interaction claim and its implied functional relevance require substantial additional evidence. Supportive if technical concerns are resolved and the scope is narrowed to a descriptive report without overclaiming functional significance.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims AlphaFold3 predicted 3D structures for CcWOX proteins and an interface model compatible with CcWOX3–CcLBD33 interaction (Abstract; Section 2.5)
- **Evidence pointer** Section 2.5; Figure 5; Figure 6; Section 4.4
- **Concern** The manuscript reports AlphaFold3 predictions but provides no confidence metrics. pLDDT scores are mentioned in Section 2.5 as a general concept, but no actual values are reported for any of the 14 CcWOX models. Similarly, predicted aligned error (PAE) plots, which are critical for assessing interface prediction reliability in multimer models, are not presented. The statement that the interface model is "compatible with" an interaction is vague and cannot be evaluated without quantitative confidence data.
- **Why it matters** AlphaFold3 predictions vary widely in reliability depending on the protein and the interface. Without pLDDT and PAE data, readers cannot assess whether the predicted structures and the CcWOX3–CcLBD33 interface are high-confidence or speculative. This directly affects the credibility of the central interaction claim.
- **Resolution test** Provide pLDDT scores for all 14 CcWOX models, with per-residue plots for the homeodomain regions. For the CcWOX3–CcLBD33 multimer, provide PAE plots and ipTM/pTM scores. If the interface confidence is low, the claim should be softened accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims qRT-PCR validation confirmed tissue-specific expression patterns with significant differences (Section 2.4; Section 4.3)
- **Evidence pointer** Section 2.4; Figure 4B; Section 4.3
- **Concern** The statistical reporting is incomplete. The manuscript states that one-way ANOVA followed by Tukey's HSD was performed and that significant differences (p < 0.05) were found for certain genes, but no F-values, degrees of freedom, effect sizes, or specific p-values are reported. The number of biological replicates is stated as three in Section 4.1, but it is unclear whether all qRT-PCR experiments included three independent biological replicates with technical replicates. The statement "for certain genes" is imprecise and does not allow readers to determine which genes showed significant differences.
- **Why it matters** Without complete statistical reporting, the claim of tissue-specific expression patterns cannot be independently verified. The vague description of which genes showed significant differences undermines the reproducibility of the findings.
- **Resolution test** Report complete ANOVA results for each gene tested, including F-values, degrees of freedom, and p-values. Specify which pairwise comparisons were significant in the Tukey's HSD post hoc tests. Clarify the replication structure (biological vs. technical replicates) and include all raw data points in supplementary materials.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The manuscript interprets the lack of fluorescence in the swapped construct (nEYFP-CcWOX3 + cEYFP-CcLBD33) as likely due to steric hindrance or orientation effects (Section 2.6; Section 3)
- **Evidence pointer** Section 2.6; Figure 7; Section 3
- **Concern** The swapped construct produced no fluorescence, and the authors attribute this to orientation constraints inherent to BiFC. While this is a plausible explanation, it is also possible that the interaction is orientation-specific or that the negative result indicates a weak or non-specific interaction. The manuscript does not provide any additional evidence to distinguish between these possibilities. The claim that the interaction is "confirmed" is too strong given that one of the two reciprocal configurations failed.
- **Why it matters** BiFC results are known to be sensitive to fusion orientation. A single positive configuration with a failed reciprocal configuration weakens the confidence in the interaction. The interpretation should be more cautious and acknowledge alternative explanations.
- **Resolution test** Provide additional validation using an orthogonal method such as co-immunoprecipitation or pull-down, as the authors themselves note is needed. Alternatively, test additional fusion configurations or use a different split-Venus system to confirm the interaction is not an artifact of the specific construct design.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim scope
- **Claim pointer** The manuscript claims the findings "support a putative WOX–LBD interaction module in C. camphora" and that this "provides a framework for dissecting WOX-mediated developmental programs" (Abstract; Section 3; Section 5)
- **Evidence pointer** Abstract; Section 3; Section 5
- **Concern** The manuscript demonstrates a physical interaction between CcWOX3 and CcLBD33 in a heterologous system (N. benthamiana). However, no functional data are provided to show that this interaction has biological relevance in C. camphora. The connection to adventitious root formation, which is the framing context in the Introduction, is entirely speculative. The claim of a "module" implies functional significance that is not supported by the evidence.
- **Why it matters** Physical interaction in a heterologous overexpression system does not establish biological function. The manuscript overreaches in its conclusions by implying developmental relevance without any loss-of-function, gain-of-function, or expression correlation data in C. camphora.
- **Resolution test** Either remove or substantially soften claims about functional relevance. If the interaction claim is to be maintained, provide evidence of co-expression in relevant tissues, or genetic evidence (e.g., overexpression or knockdown phenotypes) linking CcWOX3 and CcLBD33 to root development.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** Table 1
- **Issue** The manuscript states that CcWOX12 is predicted to localize to the cytoplasm, which is unusual for a transcription factor. This is mentioned without further comment or validation.
- **Required correction** Provide additional discussion of this prediction, including whether it is supported by any experimental evidence or whether it may reflect a technical artifact of the prediction tool.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.3
- **Evidence pointer** Section 4.3
- **Issue** The qRT-PCR primer sequences are not provided, and the reference gene (CcActin) is mentioned but its stability across tissues is not validated.
- **Required correction** Include primer sequences in supplementary materials and provide evidence for the stability of the reference gene across the seven tissues/organs examined.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 2.5
- **Evidence pointer** Figure 5
- **Issue** The manuscript states that "variations were observed in the overall conformations of the predicted structures" but does not describe what these variations are or whether they have any functional implications.
- **Required correction** Briefly describe the structural differences observed, particularly in the homeodomain and any other conserved regions, and comment on whether these variations are likely to affect DNA binding or protein interactions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section 2.2
- **Evidence pointer** Figure 1B
- **Issue** The manuscript notes a 61-amino acid homeodomain in several members rather than the canonical 60 residues, but does not specify which members or show the alignment clearly.
- **Required correction** Specify which CcWOX proteins have the extended homeodomain and show the alignment with the canonical 60-residue homeodomain for comparison.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2
- **Issue** The citation "[46]" appears at the end of a sentence about the GTP-binding domain in CcWOX12, but it is unclear whether this citation supports the existence of GTP-binding domains in WOX proteins generally or specifically in CcWOX12.
- **Required correction** Clarify the citation context and ensure that the reference supports the specific claim being made.

## Risk / unsupported claims
- The claim of a "putative WOX–LBD interaction module" with implied functional relevance in adventitious root formation is unsupported by functional evidence
- The statement that AlphaFold3 predictions are "compatible with" an interaction is unverifiable without confidence metrics
- The claim that qRT-PCR confirmed tissue-specific expression patterns is not fully supported due to incomplete statistical reporting
- The interpretation of the failed swapped BiFC construct as solely due to steric hindrance is speculative
- The prediction of cytoplasmic localization for CcWOX12 is presented without validation or discussion of its implications