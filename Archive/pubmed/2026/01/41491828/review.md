## Review setup
- **Input scope** Full manuscript text including Introduction, Results, Discussion, Methods, and Supplementary Information references
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that the yeast transcriptional regulator Ixr1 contains intrinsically disordered regions (IDRs) with prion-like characteristics, supported by bioinformatic predictions, biophysical characterization, in vitro amyloid formation assays, in vivo foci formation, and a Sup35-based prion assay
- **Visible evidence base** Figures 1-8 as referenced in text, Supplementary Figures S1-S4, Tables S1-S3 (referenced but not provided in detail)
- **Missing materials affecting confidence** Full figure images, supplementary data files, raw experimental data, statistical analysis details, strain and plasmid construction details, and complete methods for some assays

## Reviewer
- **Overall assessment** The manuscript presents a comprehensive characterization of Ixr1 as a potential prion-like protein, combining computational predictions with experimental validation. The work addresses an interesting question regarding the functional significance of Q/N-rich regions in a transcriptional regulator with established roles in stress responses. However, several technical concerns regarding the interpretation of key experiments, particularly the prion assay and the in vivo relevance of the observed phenomena, need to be addressed before the prion-like claim is fully established. The study is potentially valuable for the prion biology and IDP fields, but the current evidence does not fully exclude alternative explanations for the observed aggregation behavior.

- **Who would be interested in the results, and why** Researchers studying prion biology, intrinsically disordered proteins, fungal stress responses, and transcriptional regulation would find this work relevant. The study contributes to the growing understanding of how Q/N-rich regions in transcription factors may confer prion-like properties, which has implications for understanding protein-based inheritance and stress adaptation mechanisms in yeast.

- **Major strengths** The study combines multiple complementary approaches including bioinformatic prediction, biophysical characterization, in vitro aggregation assays, and in vivo functional assays. The use of the Sup35-based prion assay provides a functional readout for prion-like behavior. The identification of a new candidate prion-like protein in yeast adds to the catalog of potentially prionogenic proteins and opens new questions about the physiological relevance of such phenomena.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence for prion-like behavior
- **Claim pointer** The authors claim that Ixr1 shows "characteristic of a prion-like protein" based on the Sup35-based prion assay results
- **Evidence pointer** Results section, Figure 8, "location not provided"
- **Concern** The Sup35-based prion assay is described with minimal detail. The text states "we obtain positive results (data not shown)" for the initial chimera test, and the quantitative data in Figure 8a is not described in sufficient detail. The distinction between true prion induction and non-specific aggregation effects on read-through is not clearly established. The cytoduction experiments are mentioned but the methodology and controls are not adequately described.
- **Why it matters** The prion assay is the central functional evidence for the prion-like claim. Without rigorous demonstration that the Ade+ phenotype is due to bona fide prion formation rather than other mechanisms (e.g., transcriptional effects, protein stabilization, or non-specific aggregation), the core conclusion is not fully supported.
- **Resolution test** Provide complete details of the prion assay including all controls, quantitative data with statistical analysis, demonstration of the heritable and transmissible nature of the phenotype, and evidence that the observed effects are specifically due to prion formation (e.g., dependence on Hsp104 for at least some of the constructs, or alternative chaperone dependencies clearly demonstrated).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo relevance of observed aggregation
- **Claim pointer** The authors suggest that Ixr1 prion-like behavior may have physiological relevance in stress adaptation
- **Evidence pointer** Discussion section, "location not provided"
- **Concern** The in vivo experiments rely on overexpression of PrD-EGFP fusions, which may not reflect the behavior of endogenous Ixr1 at physiological concentrations. The authors acknowledge that Ixr1 was not identified in a genome-wide screen for prion-like proteins, but do not adequately address why their candidate would be missed in such screens if it indeed forms prions under physiological conditions.
- **Why it matters** The physiological relevance of the observed prion-like behavior is a key aspect of the manuscript's significance. If the phenomena only occur under artificial overexpression conditions, the biological importance of the findings is substantially diminished.
- **Resolution test** Address whether endogenous Ixr1 forms foci or aggregates under relevant stress conditions without overexpression. Discuss the discrepancy with the genome-wide screen results and provide a plausible explanation for why Ixr1 was not identified in that screen.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural characterization of Ixr1 IDRs
- **Claim pointer** The authors state that "Ixr1 is an intrinsically disordered protein with high aggregation propensity" based on computational predictions and limited biophysical data
- **Evidence pointer** Results section, Figures 1-3, "location not provided"
- **Concern** The biophysical characterization relies primarily on computational predictions and CD spectroscopy. While the CD data support the presence of disordered regions, the claim of approximately 50% disorder would be strengthened by additional experimental validation such as limited proteolysis coupled with mass spectrometry (which is partially provided), NMR spectroscopy, or size-exclusion chromatography coupled with multi-angle light scattering. The aggregation propensity is inferred from ThT fluorescence and filter retardation assays, but the relationship between the observed aggregation and the specific IDRs is not directly demonstrated.
- **Why it matters** The identification and characterization of the specific regions responsible for the prion-like behavior is important for understanding the molecular basis of the observed phenomena and for comparison with other known prion proteins.
- **Resolution test** Provide additional experimental evidence for the disordered nature of the identified regions, such as NMR spectroscopy of the isolated IDRs, or demonstrate that deletion of specific IDR regions abolishes the aggregation and prion-like behavior.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Specificity of prion-like behavior
- **Claim pointer** The authors imply that the prion-like behavior is specific to Ixr1 IDRs and not a general property of Q/N-rich regions
- **Evidence pointer** Results section, Figures 5-8, "location not provided"
- **Concern** The manuscript does not include negative controls using other Q/N-rich proteins or mutated versions of Ixr1 IDRs to demonstrate that the observed aggregation and prion-like behavior is specific to the Ixr1 sequences. Without such controls, it is difficult to assess whether the observed phenomena are biologically meaningful or a general property of Q/N-rich sequences.
- **Why it matters** The specificity of the prion-like behavior is important for establishing Ixr1 as a bona fide prion-like protein rather than a protein that simply contains a generic aggregation-prone region.
- **Resolution test** Include negative controls with Q/N-rich regions from non-prion proteins or with mutated Ixr1 IDRs lacking key residues, and demonstrate that these controls do not show the same aggregation or prion-like behavior.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Molecular modeling interpretation
- **Claim pointer** The authors use AlphaFold modeling to predict that Ixr1-Ssn8 interaction increases secondary structure content in Ixr1
- **Evidence pointer** Discussion section, Supplementary Figure S4, "location not provided"
- **Concern** The AlphaFold predictions are presented with limited validation and the significance of the predicted structural changes is not clearly connected to the prion-like behavior. The pTM and ipTM scores (0.42 and 0.28, respectively) indicate low confidence in the predicted complex structure, which is not adequately discussed.
- **Why it matters** The modeling results are used to support a speculative mechanism for regulation of Ixr1 prion-like behavior. If the structural predictions are unreliable, this part of the discussion is not well-supported.
- **Resolution test** Acknowledge the limitations of the AlphaFold predictions given the low confidence scores, or provide experimental validation of the predicted interaction and structural changes.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of experimental details
- **Affected element** Methods section, prion assay
- **Evidence pointer** Methods, "location not provided"
- **Issue** The description of the Sup35 prion assay lacks sufficient detail regarding strain construction, plasmid combinations, and the specific readout used to score prion induction.
- **Required correction** Provide complete details of the strains, plasmids, and assay conditions used for the prion assay, including how the Ade+ phenotype was quantified and the criteria for scoring prion-positive colonies.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Results section, Figure 8
- **Evidence pointer** Figure 8, "location not provided"
- **Issue** The quantitative data in Figure 8a is described without statistical analysis. It is unclear whether the differences in prion induction frequencies between constructs are statistically significant.
- **Required correction** Include statistical analysis of the prion induction frequencies, including the number of independent experiments and appropriate statistical tests.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** "location not provided"
- **Issue** The terms "prion-like," "prionogenic," and "prion" are used somewhat interchangeably throughout the text, which could lead to confusion about the strength of the claims being made.
- **Required correction** Define the terms clearly and use them consistently, with appropriate qualifiers when referring to the evidence for each level of prion behavior.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 1-8
- **Evidence pointer** "location not provided"
- **Issue** The figure legends are not provided in the manuscript text, making it difficult to fully assess the data presented.
- **Required correction** Ensure that all figure legends are complete and self-explanatory, including all experimental conditions and statistical annotations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** "location not provided"
- **Issue** The discussion does not adequately address the limitations of the study, particularly the reliance on overexpression systems and the lack of direct evidence for endogenous Ixr1 prion formation.
- **Required correction** Add a paragraph discussing the limitations of the current study and the experiments needed to establish the physiological relevance of Ixr1 prion-like behavior.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Discussion section, reference to Chakrabortee et al.
- **Evidence pointer** Discussion, "location not provided"
- **Issue** The text states "the stress conditions tested in the work from Chakrabortee and col17. do not coincide" but the reference number appears to be incorrectly formatted.
- **Required correction** Correct the reference formatting and ensure all citations are accurate and complete.

## Risk / unsupported claims
- The claim that Ixr1 is a "prion-like protein" is not fully supported by the presented evidence, as the key functional assay (Sup35-based prion assay) lacks sufficient detail and controls
- The physiological relevance of the observed prion-like behavior is not established, as all in vivo experiments rely on overexpression
- The AlphaFold-based predictions of Ixr1-Ssn8 interaction and its functional significance are speculative given the low confidence scores
- The statement that Ixr1 IDRs "switch between random coil-like to pre-molten and molten globule forms" is inferred from limited biophysical data and requires additional experimental support
- The claim that Ixr1 was not identified in genome-wide prion screens is acknowledged but not adequately reconciled with the proposed prion-like behavior