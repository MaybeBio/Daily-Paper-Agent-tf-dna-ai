## Review setup
- **Input scope** Full manuscript text (Introduction, Methods, Results, Discussion, Conclusion) as provided. Figures, tables, and supplementary material referenced but not supplied.
- **Assessment boundary** Scientific validity, mechanistic support, methodological rigor, and clarity of the claims as presented in the text. No assessment of formatting or editorial style beyond readability.
- **Shared manuscript claim summary** The authors claim that farrerol, a flavonoid from Rhododendron, protects against LPS-induced acute lung injury (ALI) by directly binding to and stabilizing the transcription factor RUNX1, which in turn transcriptionally upregulates SLC7A11, thereby inhibiting ferroptosis in pulmonary epithelial cells.
- **Visible evidence base** Text descriptions of in vitro (BEAS-2B cells) and in vivo (mouse) experiments, including cell viability, LDH release, histopathology, Evans blue staining, TUNEL, pull-down/mass spectrometry, CETSA, co-immunoprecipitation, immunofluorescence, molecular docking, PCR array, qPCR, western blotting, ChIP, dual-luciferase reporter assays, and toxicity assessments. Figures 1–9 and Supplementary Figure 1 are referenced but not provided.
- **Missing materials affecting confidence** All figures, tables (including Table 1 with primer sequences), supplementary data, and statistical details (exact n, replicates, error bars, statistical tests per figure) are not available. This substantially limits verification of quantitative claims and data quality.

## Reviewer
- **Overall assessment** The manuscript addresses a clinically relevant question and proposes a novel mechanistic axis (farrerol–RUNX1–SLC7A11) linking a natural compound to ferroptosis inhibition in ALI. The experimental design is broad and includes both in vitro and in vivo models, with multiple orthogonal approaches to support the proposed mechanism. However, the absence of key data (figures, replicates, statistical details) and several methodological ambiguities prevent full assessment of the claims. The central claim of direct farrerol–RUNX1 binding and transcriptional regulation of SLC7A11 is plausible but not fully established from the provided text alone.
- **Who would be interested in the results, and why** Researchers in pulmonary medicine, particularly those studying ALI/ARDS pathophysiology and ferroptosis; investigators interested in natural product pharmacology and drug repurposing; and those studying RUNX family transcription factors in non-hematopoietic contexts. The potential therapeutic application of farrerol for a condition with limited treatment options would attract translational and clinical interest.
- **Major strengths**
  - Clinically relevant disease model with both in vitro and in vivo validation.
  - Mechanistic depth: multiple techniques (pull-down, CETSA, Co-IP, ChIP, luciferase, docking) used to establish the farrerol–RUNX1–SLC7A11 axis.
  - Inclusion of a classic ferroptosis inducer (erastin) to validate ferroptosis specificity independent of LPS.
  - Toxicity assessment in vivo strengthens translational potential.
  - Honest acknowledgment of limitations (binding site not experimentally validated, single cell type focus, single ALI model).
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "Farrerol directly binds to and stabilizes runt-related transcription factor 1 (RUNX1)"
- **Evidence pointer** Results section, Figures 3A–I, L–O; Methods: pull-down, CETSA, Co-IP, molecular docking
- **Concern** The claim of direct binding is supported by pull-down, CETSA, Co-IP, and docking, but the actual data (gels, thermal shift curves, binding affinities, docking scores) are not visible. CETSA is described but no quantitative readout (e.g., melting curves, ΔTm) is provided. Molecular docking is predictive and the authors acknowledge it is not experimentally validated. Co-IP can show interaction but does not prove direct binding. The stoichiometry and affinity of the farrerol–RUNX1 interaction are not reported.
- **Why it matters** The entire mechanistic model hinges on this direct interaction. If the binding is weak, non-specific, or an artifact of overexpression, the downstream claims (RUNX1 stabilization, SLC7A11 upregulation) lose their causal foundation. Without quantitative binding data or mutagenesis validation, the claim is not established.
- **Resolution test** Provide CETSA melting curves with replicates and statistical comparison; report binding affinity (e.g., ITC, SPR, or MST) if available; show Co-IP with endogenous proteins; validate docking predictions with site-directed mutagenesis of the proposed binding pocket and demonstrate loss of binding and function.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal evidence
- **Claim pointer** "Farrerol... thereby transcriptionally activating the expression of solute carrier family 7 member 11" and "RUNX1 directly binds to and transcriptionally activates the SLC7A11 promoter"
- **Evidence pointer** Results section, Figures 6A–M; Methods: PCR array, qPCR, ChIP, dual-luciferase
- **Concern** The causal chain from farrerol to RUNX1 to SLC7A11 transcription is supported by overexpression and knockdown experiments, but the text does not specify whether the ChIP and luciferase assays were performed with endogenous RUNX1 or only under overexpression conditions. The PCR array identified 13 upregulated genes, but only 4 were validated, and the selection criteria for these 4 are not stated. The functional relevance of SLC7A11 as the key downstream effector is inferred from expression changes, but rescue experiments (e.g., SLC7A11 overexpression or knockdown in the context of farrerol treatment) are not described.
- **Why it matters** Transcriptional regulation claims require demonstration that the transcription factor binds the promoter in a physiologically relevant context and that the target gene is necessary and sufficient for the phenotype. Without rescue or loss-of-function experiments for SLC7A11, the claim that this is the key mediator is not fully supported.
- **Resolution test** Show ChIP with endogenous RUNX1 at the SLC7A11 promoter; perform luciferase assays with promoter truncations or mutations to map the responsive element; include SLC7A11 knockdown or overexpression in farrerol-treated cells to demonstrate functional necessity and sufficiency.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and data availability
- **Claim pointer** All quantitative results (cell viability, LDH, ROS, Fe2+, GSH, MDA, histopathology scores, etc.)
- **Evidence pointer** Results section, Figures 1–9; Methods: statistical analysis
- **Concern** The text reports statistical significance (p < 0.05) but does not provide effect sizes, exact p-values, number of replicates, or whether experiments were performed in biological or technical triplicates. The statistical methods section mentions one-way ANOVA with Tukey's post hoc and t-tests, but the specific tests used for each figure are not indicated. No information on blinding, randomization, or sample size calculation is provided for the animal studies.
- **Why it matters** Without these details, the robustness of the findings cannot be evaluated. The reproducibility of the results, particularly for in vivo studies with n = 5 per group, is uncertain. This is a fundamental requirement for establishing the case.
- **Resolution test** Provide full statistical details for each figure, including exact n, replicates, test used, and effect sizes. Include a statement on randomization and blinding for animal experiments. Make raw data available or provide representative images with quantification.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model relevance
- **Claim pointer** "Farrerol could directly bind and stabilize the expression of RUNX1, thereby enhancing SLC7A11 transcription and ultimately inhibiting ferroptosis" as the mechanism in ALI
- **Evidence pointer** Results section, Figures 2, 7; Methods: in vivo model
- **Concern** The in vivo model uses LPS-induced ALI, which is a well-established but limited model that primarily reflects acute inflammation and does not fully recapitulate the complexity of human ALI/ARDS. The authors acknowledge this limitation. However, the text does not specify whether the protective effects of farrerol were observed in both prophylactic and therapeutic treatment regimens, or only with pre-treatment. The timing of farrerol administration relative to LPS is described as "1 hour prior" in the methods, which limits clinical translatability.
- **Why it matters** Pre-treatment models are less clinically relevant than post-treatment or therapeutic models. The claim that farrerol is a "potential therapeutic agent" requires demonstration of efficacy when given after injury onset.
- **Resolution test** Include a therapeutic treatment group where farrerol is administered after LPS challenge. If not feasible, temper the therapeutic claim and clearly state the prophylactic nature of the intervention.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Specificity
- **Claim pointer** "Farrerol inhibits ferroptosis" and "RUNX1 specifically modulated ferroptosis-related markers"
- **Evidence pointer** Results section, Figures 4C–I, 5C–G; Methods: western blotting, flow cytometry
- **Concern** The text states that RUNX1 overexpression "specifically modulated ferroptosis-related markers, notably GPX4 and 4-HNE" and did not affect apoptosis, necroptosis, or pyroptosis markers. However, the full panel of markers tested is not listed, and the criteria for "specificity" are not defined. The possibility that farrerol or RUNX1 affects other cell death pathways or crosstalk between pathways is not fully excluded.
- **Why it matters** Ferroptosis inhibitors often have pleiotropic effects. If the compound also modulates other pathways, the claim of ferroptosis-specificity is overstated. This affects the mechanistic interpretation.
- **Resolution test** Provide the full list of cell death markers assessed, including positive controls for each pathway. Consider testing a broader panel or using a ferroptosis-specific inhibitor (e.g., ferrostatin-1) as a comparator.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods: Cell culture and transfection
- **Evidence pointer** Methods section, "Cell culture and transfection"
- **Issue** The siRNA sequences are written with "5¢" and "3¢" symbols, which appear to be typographical errors for "5'" and "3'".
- **Required correction** Replace "¢" with "'" in the siRNA sequence notation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Methods: Animal care and welfare
- **Evidence pointer** Methods section, "Animal care and welfare"
- **Issue** The text states "A total of 70 healthy male C57BL/6 mice" but then describes using 50 mice for the ALI model and 20 mice for the mechanism study. The total is consistent, but the text later says "An additional 20 mice were divided into four groups (n = 5 per group)" which is clear. However, the ethics statement lists approval number "CMC- 115 IACUC-2021024" with a space and "115" inserted, while the methods section lists "CMC-IACUC-2021024". This discrepancy needs correction.
- **Required correction** Unify the ethics approval number across the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods: Molecular docking
- **Evidence pointer** Methods section, "Molecular docking and binding mode prediction of RUNX1-farrerol complex"
- **Issue** The docking protocol is described, but no docking score, binding energy, or comparison with a control ligand is provided in the text.
- **Required correction** Report the docking score and, if possible, compare with a known RUNX1 binder or a negative control to support the specificity of the predicted interaction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results: Farrerol directly binds to and upregulates RUNX1
- **Evidence pointer** Results section, "Farrerol directly binds to and upregulates RUNX1"
- **Issue** The text states "farrerol upregulated RUNX1 protein expression in a dose-dependent manner, without affecting its mRNA levels (Figures 3, K)." The figure reference "Figures 3, K" is ambiguous; it likely means Figure 3J and 3K.
- **Required correction** Clarify the figure reference to "Figure 3J, K".

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The phrase "it's in vivo toxicity profile" in the Results section (Potential toxicity and safety evaluation) uses "it's" instead of "its".
- **Required correction** Change "it's" to "its".

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods: Statistical analysis
- **Evidence pointer** Methods section, "Statistical analysis"
- **Issue** The statistical methods are described generically. No information is provided on how normality was tested, whether data were transformed, or how outliers were handled.
- **Required correction** Add details on normality testing, data transformation, and outlier handling.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Direct binding claim not quantitatively supported without CETSA curves, binding affinity, or mutagenesis validation.
  - R1-M2: Transcriptional regulation claim requires endogenous ChIP and functional rescue experiments for SLC7A11.
  - R1-M3: Statistical reporting is insufficient to evaluate robustness of quantitative claims.
  - R1-M4: Prophylactic-only treatment design limits the therapeutic claim.

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The combination of farrerol with the RUNX1/SLC7A11 axis is novel, and the identification of RUNX1 as a regulator of SLC7A11 in this context is a new finding. However, the general concept of ferroptosis inhibition in ALI and the use of natural flavonoids for this purpose are not new.
  - **Scientific importance** Moderate to high. ALI/ARDS is a major clinical problem with limited therapeutic options. A mechanistic link between a natural compound and a specific transcription factor–target gene axis could inform new therapeutic strategies. However, the clinical relevance of the LPS model and the prophylactic dosing limit immediate translational impact.
  - **Interdisciplinary readership** Moderate. The work bridges natural product pharmacology, pulmonary biology, and cell death research. It would appeal to a specialized audience but may not have broad interdisciplinary reach beyond these fields.
  - **Technical soundness** Currently not fully assessable. The experimental design is reasonable and uses appropriate techniques, but the absence of raw data, replicates, and statistical details prevents verification. The lack of experimental validation for the docking predictions and the absence of rescue experiments weaken the mechanistic case.
  - **Readability for nonspecialists** Acceptable. The manuscript is generally well-structured and the logic is clear. However, some sections (e.g., the PCR array and ChIP descriptions) assume familiarity with molecular biology techniques. The abstract and introduction are accessible.

- **Recommendation posture** Supportive if technical concerns are resolved. The proposed mechanism is interesting and potentially significant, but the current evidence base, as presented in the text, is insufficient to fully establish the direct binding claim and the causal role of the RUNX1/SLC7A11 axis. Provision of the missing data (figures, statistics, replicates) and additional experiments (mutagenesis, rescue, therapeutic dosing) would substantially strengthen the case.

## Risk / unsupported claims
- Direct physical binding of farrerol to RUNX1 is claimed but not quantitatively supported without binding affinity data or mutagenesis validation.
- The claim that RUNX1 "specifically" modulates ferroptosis (and not other cell death pathways) is not fully supported without a complete list of markers tested and positive controls.
- The claim that SLC7A11 is the key downstream effector is not established without functional rescue or knockdown experiments.
- The therapeutic potential of farrerol is overstated given the prophylactic-only treatment design.
- The discrepancy with a previous study reporting no protective effect of farrerol in LPS-induced ALI is discussed but not experimentally addressed.
- Toxicity assessment is described as favorable, but the text does not provide specific data on body weight, organ weights, or histopathology of major organs beyond a general statement.