## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, footnotes) as provided
- **Assessment boundary** Scientific validity, technical soundness, clarity, and support of claims based solely on the supplied material
- **Shared manuscript claim summary** The authors present Ledidi, a computational method for designing minimal edits to cis-regulatory elements using pre-trained deep learning models. They claim broad applicability across transcription factor binding, chromatin accessibility, transcription, and enhancer activity; demonstrate cell type-specific enhancer design validated by STARR-seq; and introduce "affinity catalogs" for controlling transcriptional dosage and interpreting model logic.
- **Visible evidence base** Abstract, Sections 1–7 (Main), Section 8 (Methods subsections 8.1–8.10), Data and Code Availability statements, Competing Interests, Acknowledgements, Footnotes. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** All figures, supplementary figures, supplementary tables, and detailed experimental protocols for STARR-seq are absent. This limits verification of quantitative claims, statistical analyses, and experimental reproducibility.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially useful method for cis-regulatory element design. The core idea of reformulating discrete sequence editing as continuous optimization with an edit penalty is elegant and well-motivated. However, the provided text lacks the essential figures and supplementary data needed to evaluate the strength of the experimental validation and the generality of the claims. Several quantitative statements are made without visible supporting data. The method's novelty relative to existing approaches (e.g., FastSeqProp) is not fully delineated. The manuscript is well-written and accessible, but the evidence base as provided is insufficient to fully establish the central claims.
- **Who would be interested in the results, and why** Researchers in synthetic biology, regulatory genomics, and computational biology would be interested. The method offers a practical tool for designing minimal edits to achieve desired regulatory outcomes, which is relevant for gene therapy, cell engineering, and functional genomics. The affinity catalog concept may also appeal to those studying cis-regulatory logic and model interpretability.
- **Major strengths** 1. The conceptual framing of design as continuous optimization with an explicit edit penalty is clear and compelling. 2. The method is model-agnostic, allowing use with any pre-trained deep learning model, which is a practical advantage. 3. The inclusion of experimental validation via STARR-seq strengthens the translational relevance. 4. The affinity catalog concept is a novel contribution that extends the utility of design methods beyond single-target optimization.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
- **Technical failings that need to be addressed before the case is established** R1-M1 (experimental validation data missing), R1-M2 (baseline comparisons not described), R1-M3 (statistical analysis not reported), R1-M4 (generality claim not fully supported)
- **Assessment against Nature-style criteria** 
  - **Originality** The method is a novel combination of existing ideas (continuous relaxation, edit penalty, model-agnostic design). The affinity catalog concept is original. However, the incremental advance over FastSeqProp and similar methods needs clearer articulation.
  - **Scientific importance** The problem of designing minimal edits to achieve regulatory outcomes is important for synthetic biology and therapeutic applications. The method addresses a real bottleneck.
  - **Interdisciplinary readership** The work bridges computational biology, genomics, and experimental molecular biology. The writing is generally accessible, but some sections (e.g., optimization details) may be dense for non-specialists.
  - **Technical soundness** The core optimization approach is sound in principle. However, the lack of visible figures and supplementary data prevents full assessment of the experimental results and statistical rigor.
  - **Readability for nonspecialists** The abstract and main text are well-structured and clear. The methods section is appropriately detailed for specialists. Some terminology (e.g., "straight-through estimator") may require prior knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual contribution is promising, but the provided evidence is incomplete. The authors must supply the missing figures, supplementary data, and statistical details to substantiate the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** "By using several deep learning models simultaneously, we design cell type-specific enhancers and experimentally validate them in cellulo." Also, "we found that Ledidi's designs exhibit strong cell type-specific signals and that many of the designs exhibit stronger regulatory activity than the strongest endogenous elements."
- **Evidence pointer** Section 4, Figure 2 (not provided), Supplementary Figures 2, 3, 7, 8, 9 (not provided)
- **Concern** The central experimental validation claim is not verifiable from the provided text. The authors report quantitative results (e.g., median enrichments, percentages of designs exceeding endogenous activity) but the corresponding figures and supplementary data are absent. Without these, the reader cannot assess the magnitude of effects, variability, or the robustness of the conclusions.
- **Why it matters** The experimental validation is the key evidence that the method works outside of in silico predictions. If the data are not available, the claim that Ledidi designs functional cell type-specific enhancers is unsupported.
- **Resolution test** Provide the figures and supplementary tables showing STARR-seq enrichments, statistical comparisons, and the distribution of activities across designs and controls. Include details on the number of replicates, the variability, and the criteria for calling a design "active" or "specific."

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline comparison
- **Claim pointer** "Ledidi can use any pre-trained deep learning model to guide the optimization, yielding an edited sequence that exhibits the desired outcome while explicitly minimizing the number of edits used."
- **Evidence pointer** Section 2, Figure 1 (not provided), Section 8.3
- **Concern** The manuscript does not describe any baseline or comparison against alternative design methods (e.g., FastSeqProp, genetic algorithms, or random mutation). The claim that Ledidi is superior or even comparable to existing approaches is not supported by any comparative data. The speed comparison in Section 3 (Figure 1G) is mentioned but the figure is not provided.
- **Why it matters** Without a baseline, the reader cannot judge whether Ledidi offers a meaningful improvement over existing methods. The claim of "general purpose designer" requires demonstration that it performs at least as well as current state-of-the-art.
- **Resolution test** Include a comparison of Ledidi against at least one alternative method (e.g., FastSeqProp) on the same design tasks, reporting the number of edits, predicted activity, and experimental validation if available. Provide the speed comparison data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "On average, Ledidi made 16.54 edits per sequence, driving the predicted activity from the 50th to the 99.27th percentile." Also, "419 out of 448 (93.5%) of the designed S2-specific enhancers and 72 out of 423 (17.0%) of the designed OSC-specific enhancers exhibited stronger activity than the average endogenous enhancer."
- **Evidence pointer** Section 2, Section 4, Supplementary Figures 1, 2, 3 (not provided)
- **Concern** The manuscript reports means, percentages, and percentiles without any measure of variance, confidence intervals, or statistical tests. It is unclear whether the differences between conditions (e.g., on-target vs. off-target activity) are statistically significant. The number of replicates and the handling of technical vs. biological variability are not described.
- **Why it matters** The conclusions depend on the reliability of these quantitative claims. Without error bars or statistical tests, the reader cannot assess the robustness of the findings or the reproducibility of the method.
- **Resolution test** Provide standard deviations, confidence intervals, or statistical tests for all key quantitative claims. Describe the number of biological and technical replicates and the statistical methods used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generality of claims
- **Claim pointer** "Ledidi can use any pre-trained deep learning model to guide the optimization" and "we find that Ledidi's designs can precisely control transcription factor binding, chromatin accessibility, transcription, and enhancer activity in silico."
- **Evidence pointer** Section 2, Section 3, Supplementary Table 1 (not provided)
- **Concern** The claim of generality across "dozens of settings" and "ten different oracle models" is made, but the details of these settings are not fully described. The criteria for selecting the 14 design settings and the 46 subsequent settings are not given. The performance across these settings is summarized only as averages, which may hide important variability.
- **Why it matters** The claim of broad applicability is a key selling point. If the method works well only for certain models or tasks, the claim of generality is overstated.
- **Resolution test** Provide a table listing all design settings, the oracle model used, the number of edits, and the resulting percentile improvement. Describe the criteria for selecting these settings and any cases where the method failed or performed poorly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 8.1, Equation 1
- **Evidence pointer** Section 8.1
- **Issue** The objective function is described in words but the actual equation is not shown in the provided text. The description is understandable but the formal definition would aid precision.
- **Required correction** Include the full equation for the objective function in Section 8.1.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 8.7
- **Evidence pointer** Section 8.7
- **Issue** The description of the ladder construction is brief. The criteria for selecting the 50 strongest, 50 weakest, and 50 intermediate elements are not specified.
- **Required correction** Provide the exact criteria for selecting ladder elements and the source of the genome-wide STARR-seq data used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 5, "affinity catalog"
- **Evidence pointer** Section 5
- **Issue** The term "affinity catalog" is introduced but not formally defined. The relationship to "affinity" (presumably binding affinity) is implicit.
- **Required correction** Provide a formal definition of "affinity catalog" and clarify the intended meaning of "affinity" in this context.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Section 8.9
- **Evidence pointer** Section 8.9
- **Issue** The GEO accession number is provided, but the specific data files and their organization are not described.
- **Required correction** Briefly describe the contents of the GEO submission and how to access the processed data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Typographical
- **Affected element** Section 8.8
- **Evidence pointer** Section 8.8
- **Issue** The phrase "mapping quality ¿= 20" contains a typographical error.
- **Required correction** Change "¿=" to ">=".

## Risk / unsupported claims
- The claim that Ledidi designs "cell type-specific enhancers" that are experimentally validated is unsupported without the figures and supplementary data.
- The claim that Ledidi is a "general purpose designer of edits" is not fully supported without baseline comparisons.
- The quantitative claims (e.g., average edits, percentile improvements, enrichment values) are not verifiable without the underlying data and statistical analyses.
- The claim that "many of the designs exhibit stronger regulatory activity than the strongest endogenous elements" is not verifiable without the data.
- The claim that affinity catalogs "control not only cell type-specificity but also transcriptional dosage" is based on data not shown.
- The claim that Ledidi "can use any pre-trained deep learning model" is plausible but not demonstrated across a sufficiently diverse or well-described set of models.