## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and supplementary information description
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No access to raw data, supplementary figures, or original images.
- **Shared manuscript claim summary** The authors report a screening pipeline combining in silico molecular docking with functional assays to identify small molecules targeting the CLOCK circadian clock protein. They identify chlorhexidine (CHX) as a clock activator that promotes CLOCK/Bmal1 interaction, enhances clock gene expression, and stimulates myogenic differentiation, proliferation, and migration in a clock-dependent manner.
- **Visible evidence base** Figures 1-7 as described in text, supplementary figures S1-S4, raw data figures S5-S8, supplementary tables 1-4
- **Missing materials affecting confidence** Raw data files, uncropped blots, full supplementary figures, detailed statistical outputs, compound concentration-response curves, and experimental replicates beyond those described in figure legends

## Reviewer

- **Overall assessment** This manuscript presents a systematic approach to identify circadian clock modulators targeting the CLOCK protein, with chlorhexidine emerging as a candidate with pro-myogenic activity. The work builds logically on prior findings from the same group regarding circadian clock regulation of myogenesis. The screening pipeline is well-structured, and the experimental validation is reasonably comprehensive. However, several technical concerns regarding target specificity, dose-response relationships, and the mechanistic link between clock activation and myogenic outcomes require clarification before the conclusions can be fully supported.

- **Who would be interested in the results, and why** Researchers in circadian biology, skeletal muscle biology, and regenerative medicine would find this work relevant. The identification of a CLOCK-targeting small molecule with pro-myogenic activity could inform drug development for muscular dystrophy and other muscle-wasting conditions. The screening platform itself may interest investigators seeking to discover modulators of other protein-protein interactions within the circadian clock machinery.

- **Major strengths** The study addresses a gap in the field by targeting the CLOCK activator rather than clock repressors. The multi-stage screening pipeline combining computational docking with functional validation is methodologically sound. The use of Bmal1-deficient myoblasts to demonstrate clock dependence of CHX effects is a key experimental strength. The inclusion of myogenic differentiation, proliferation, and migration assays provides a broad functional assessment.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Target specificity
- **Claim pointer** The authors claim CHX specifically targets the CLOCK protein hydrophobic pocket within the PAS-A domain to enhance CLOCK/Bmal1 interaction.
- **Evidence pointer** Figure 2E, 2F; Figure 1C, 1D
- **Concern** The evidence for direct CHX binding to CLOCK is indirect. The co-immunoprecipitation experiments show increased CLOCK/Bmal1 association with CHX treatment, and the C267A mutation abolishes this effect. However, no direct binding assay (e.g., surface plasmon resonance, isothermal titration calorimetry, or cellular thermal shift assay) is presented to demonstrate physical interaction between CHX and CLOCK. The docking predictions are computational and require experimental validation.
- **Why it matters** The central claim of the manuscript is that CHX acts through direct CLOCK binding. Without direct binding evidence, alternative explanations such as off-target effects on upstream regulators of CLOCK expression or stability cannot be excluded. This weakens the mechanistic foundation of the study.
- **Resolution test** Provide direct binding data using purified CLOCK protein and CHX, or demonstrate CHX-induced thermal stabilization of CLOCK in cells. Alternatively, show that CHX fails to affect clock function in cells expressing CLOCK mutants lacking the predicted binding pocket.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Dose-response relationship
- **Claim pointer** The authors state that CHX activates the circadian clock and promotes myogenesis at concentrations of 0.2 to 2 µM, with higher concentrations showing toxicity.
- **Evidence pointer** Figure 2A-C; Figure 5A-F; Figure 7A-D
- **Concern** The manuscript does not present a systematic dose-response analysis for CHX effects on clock parameters or myogenic outcomes. The text mentions that 5 and 10 µM reduced amplitude suggesting toxicity, but the transition from beneficial to toxic effects is not characterized. The concentration dependence of CHX effects on CLOCK/Bmal1 interaction, clock gene expression, and myogenic differentiation is not shown in a unified manner.
- **Why it matters** A clear dose-response relationship is essential to establish the pharmacological relevance of CHX and to distinguish specific clock-modulatory effects from general cellular stress responses. The narrow therapeutic window implied by the data requires careful characterization.
- **Resolution test** Present full dose-response curves for CHX effects on clock period, amplitude, CLOCK/Bmal1 interaction, myogenic differentiation markers, and cell viability across a range of concentrations (e.g., 0.05 to 10 µM) in both C2C12 and U2C2 cells.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic link between clock activation and myogenesis
- **Claim pointer** The authors conclude that CHX promotes myogenic differentiation in a clock-dependent manner, implying that clock activation directly drives the myogenic program.
- **Evidence pointer** Figure 5A-F; Figure 6A-G
- **Concern** While the loss of CHX effect in Bmal1-deficient myoblasts supports clock dependence, the manuscript does not establish a direct mechanistic link between CHX-induced clock activation and the myogenic gene program. The Wnt pathway genes examined are known clock targets, but the temporal relationship between clock gene induction and myogenic marker expression is not explored. It remains possible that CHX affects myogenesis through parallel pathways that also require Bmal1 for their function.
- **Why it matters** The therapeutic rationale for CHX in muscle disease depends on the premise that clock activation is the primary driver of enhanced myogenesis. If CHX acts through Bmal1-dependent but clock-independent mechanisms, the specificity of the approach is reduced.
- **Resolution test** Perform time-course experiments showing that clock gene activation precedes myogenic gene induction. Use genetic tools to constitutively activate clock in Bmal1-deficient cells to determine whether this rescues CHX effects. Alternatively, test whether CHX affects myogenesis in cells with clock disruption but intact Bmal1 expression.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report statistically significant effects of CHX on clock parameters and myogenic outcomes.
- **Evidence pointer** Figure legends for Figures 2, 5, 6, 7
- **Concern** The statistical methods are described only briefly in the methods section. The figure legends mention t-tests and ANOVA but do not specify which comparisons were made, whether corrections for multiple testing were applied, or how normality and variance assumptions were assessed. The number of independent experiments is stated but the number of technical replicates within each experiment is not always clear.
- **Why it matters** Transparent statistical reporting is essential for evaluating the robustness of the findings, particularly for relatively modest effect sizes such as the 26% increase in CLOCK/Bmal1-mediated transcription.
- **Resolution test** Provide detailed statistical methods including specific tests used for each comparison, correction for multiple testing where applicable, and clear reporting of sample sizes and replicate structure. Consider presenting effect sizes with confidence intervals.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of screening pipeline
- **Affected element** Figure 1A
- **Evidence pointer** Figure 1A
- **Issue** The screening pipeline diagram is described in the text but the figure itself is not visible in the provided manuscript. The description mentions a multi-stage process but the specific criteria for advancing compounds between stages are not fully detailed.
- **Required correction** Clarify the advancement criteria at each screening stage, including the specific thresholds for docking scores, clock activity modulation, and toxicity exclusion.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Concentration selection rationale
- **Affected element** Methods section, cell culture and treatments
- **Evidence pointer** Methods section, location not provided
- **Issue** The rationale for selecting CHX concentrations of 0.2, 0.5, and 1 µM for different assays is not explained. The text notes toxicity at higher concentrations but does not describe how the working concentrations were determined.
- **Required correction** Provide a brief rationale for concentration selection, ideally referencing preliminary toxicity or activity data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Cell type relevance
- **Affected element** Results section, myogenesis assays
- **Evidence pointer** Figure 5, Figure 6
- **Issue** The myogenesis experiments use C2C12 myoblasts, a mouse cell line. The relevance to human muscle regeneration is not discussed, and no human muscle cell experiments are presented.
- **Required correction** Add a discussion of the limitations of using mouse cell lines and the need for validation in human myogenic cells or in vivo models.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** CHX specificity
- **Affected element** Discussion section
- **Evidence pointer** Discussion, location not provided
- **Issue** CHX is a widely used antiseptic with known membrane-active properties. The manuscript does not discuss potential membrane-related effects that could confound the observed myogenic outcomes.
- **Required correction** Add a paragraph addressing potential off-target effects of CHX related to its antiseptic mechanism of action and how the experimental design controls for these.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary information
- **Evidence pointer** Supplementary information section
- **Issue** The supplementary materials are described but not provided for review. Key data such as uncropped blots and full dose-response curves are not accessible.
- **Required correction** Ensure all supplementary data are made available for review and publication.

- **Technical failings that need to be addressed before the case is established** Direct binding evidence for CHX to CLOCK is lacking. Dose-response relationships are incomplete. The mechanistic link between clock activation and myogenic outcomes requires temporal and genetic evidence. Statistical reporting needs to be more detailed and transparent.

- **Assessment against Nature-style criteria** Originality: The work is original in targeting the CLOCK activator for small molecule modulation, an area less explored than clock repressor targeting. Scientific importance: The potential application to muscular dystrophy and muscle regeneration is clinically relevant, though the study is at an early preclinical stage. Interdisciplinary readership: The work bridges circadian biology, pharmacology, and muscle biology, which could attract readers across these fields. Technical soundness: The experimental design is generally sound, but the lack of direct binding data and incomplete dose-response analysis weaken the technical foundation. Readability for nonspecialists: The manuscript is clearly written and accessible, with logical flow from screening to functional validation.

- **Recommendation posture** Supportive if technical concerns are resolved. The core concept is interesting and the screening platform is potentially valuable, but the evidence for direct CLOCK targeting and the dose-response characterization need strengthening before the conclusions can be fully accepted.