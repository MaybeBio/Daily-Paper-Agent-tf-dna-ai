## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report the structure-guided design of an artificial transcription factor (ProB) assembled from the QF DNA-binding domain, a ligand-binding domain, a linker, and the QF activation domain. ProB acts on a synthetic promoter (QT) to control GFP expression in *E. coli*, yielding a progesterone biosensor with reported sensitivity (LOD 0.15 µg/L, EC50 26.58 µg/L), working temperature range (20–30 °C), detection time (56.4 min), and working concentration range (0.15–40 µg/L). The authors claim the design strategy and performance meet clinical application requirements.
- **Visible evidence base** Abstract text only; no experimental methods, data figures, statistical analyses, or validation details provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental protocols, MD simulation parameters, characterization data for ProB assembly, biosensor calibration curves, specificity data, reproducibility statistics, and any comparison with existing progesterone biosensors

## Reviewer
- **Overall assessment** The abstract presents an interesting concept: the transfer of a eukaryotic transcription factor architecture into a prokaryotic host through rational design informed by molecular dynamics simulations. The reported performance metrics are notable, particularly the low detection limit and short detection time. However, the abstract alone provides insufficient evidence to evaluate the validity of the design rationale, the robustness of the biosensor performance, or the claim of clinical applicability. Several key claims are unsupported or under-specified, and the absence of methodological detail precludes a rigorous technical assessment.
- **Who would be interested in the results, and why** Researchers in synthetic biology, particularly those working on transcription factor engineering, biosensor design, and prokaryotic gene circuits. The work may also interest investigators developing whole-cell biosensors for clinical or environmental steroid detection, and those exploring the transfer of eukaryotic regulatory components into bacterial hosts.
- **Major strengths** The concept of using MD simulations to guide the design of a chimeric transcription factor with a defined domain architecture is timely and potentially impactful. The reported performance metrics, if reproducible, would represent a meaningful advance for progesterone detection. The bacterial enrichment strategy for biosensor optimization is a practical contribution. The work addresses a gap in the literature, as eukaryotic TFs are rarely transferred to prokaryotes.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The artificial TF ProB was designed through MD simulations, and the linker fine-tuned the convergence of the DNA-binding domain and activation domain as the desired conformation guide.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that MD simulations guided the design and that the linker fine-tuned domain convergence, but no simulation details, structural models, or validation of the predicted conformation are provided. It is unclear how the linker sequence was selected, what conformational criteria were used, and whether the designed ProB actually adopts the predicted structure in vitro or in vivo.
  - **Why it matters** The central claim of the paper is that structure-guided design, specifically linker-mediated domain convergence, is the key innovation. Without evidence that the MD predictions were validated experimentally, the design rationale remains speculative, and the reported biosensor performance cannot be attributed to the structural design rather than to empirical optimization.
  - **Resolution test** Provide MD simulation methods, including force field, simulation length, and convergence criteria. Show structural validation of ProB, such as circular dichroism, size-exclusion chromatography, or mutagenesis experiments that confirm the role of the linker in domain orientation and function.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The whole-cell progesterone biosensor was optimized via a bacterial enrichment strategy, which made the biosensor highly sensitive (LOD 0.15 µg/L and EC50 26.58 µg/L), preferably in the working temperature range (20–30 °C), with only a 56.4 min detection time and a working concentration range of 0.15–40 µg/L.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The reported performance metrics are presented as single values without any indication of variability, number of replicates, or statistical analysis. The LOD, EC50, detection time, and working range are stated as definitive, but no calibration curves, error bars, or confidence intervals are shown. The term "bacterial enrichment strategy" is not defined, and its role in achieving the reported performance is unclear.
  - **Why it matters** Biosensor performance claims are only meaningful with appropriate statistical characterization. Without replicate data and error estimates, the reproducibility and reliability of the sensor cannot be assessed. The enrichment strategy is presented as a key optimization step, but its mechanism and contribution are not explained.
  - **Resolution test** Provide full calibration data with replicates, standard deviations, and statistical tests. Define the enrichment strategy and show how it improves sensitivity, response time, or dynamic range. Include a comparison of sensor performance with and without the enrichment step.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The performance reached the requirements of clinical application.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract claims clinical applicability but provides no clinical context, such as the relevant progesterone concentration range in human samples, the required sensitivity and specificity for diagnostic use, or any validation in biological matrices (e.g., serum, saliva, urine). No comparison with established progesterone detection methods is given.
  - **Why it matters** The claim of clinical applicability is a strong statement that, if unsupported, overstates the significance of the work. Clinical biosensors must meet matrix-specific performance criteria, and a laboratory-based *E. coli* sensor may not translate directly to clinical samples.
  - **Resolution test** Specify the clinical target range for progesterone and show that the sensor performs adequately in relevant biological matrices. Provide a comparison with gold-standard methods (e.g., immunoassays or LC-MS) and discuss potential interferences.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Domain nomenclature
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The terms QF(DBD), QF(AD), QUAS, and QT are introduced without definition or context. A reader unfamiliar with the QF system will not understand the design.
  - **Required correction** Define all abbreviations at first use and briefly explain the origin and function of the QF system.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Specificity claim
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract does not mention selectivity of the biosensor for progesterone over other steroids or structurally related compounds. Specificity is a critical parameter for any biosensor.
  - **Required correction** Add a statement on specificity testing, including cross-reactivity data for related steroids.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Detection time definition
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The detection time of 56.4 min is reported, but it is unclear whether this includes sample preparation, cell growth, or signal readout.
  - **Required correction** Define the detection time precisely and describe the assay workflow.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Temperature range
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The working temperature range of 20–30 °C is stated, but the effect of temperature on sensor performance is not quantified.
  - **Required correction** Provide data showing sensor response as a function of temperature, including the acceptable performance window.

## Technical failings that need to be addressed before the case is established
- R1-M1: MD simulation design rationale is not validated experimentally.
- R1-M2: Biosensor performance metrics lack statistical characterization and methodological detail.
- R1-M3: Clinical applicability claim is unsupported by clinical context or matrix validation.

## Assessment against Nature-style criteria
- **Originality** The concept of transferring a eukaryotic TF architecture into a prokaryotic host with MD-guided linker design is original and addresses a gap in the literature. However, the abstract does not demonstrate that this approach yields a fundamentally new capability beyond existing biosensors.
- **Scientific importance** The reported sensitivity and detection time are potentially significant for progesterone monitoring, but the lack of clinical validation and comparison with existing methods limits the current assessment of importance.
- **Interdisciplinary readership** The work bridges structural biology, synthetic biology, and biosensor engineering, which could appeal to a broad audience. However, the abstract is too technical and under-defined for nonspecialists to fully appreciate the significance.
- **Technical soundness** The abstract provides insufficient methodological detail to assess technical soundness. Key claims regarding MD-guided design and biosensor performance are not supported by visible evidence.
- **Readability for nonspecialists** The abstract is dense and uses undefined jargon, which reduces accessibility. The significance of the work is not clearly framed for a general scientific audience.

## Recommendation posture
Currently not established from the provided evidence. The concept is promising and the reported performance metrics are intriguing, but the abstract alone does not provide sufficient evidence to validate the design rationale, the reproducibility of the biosensor, or the clinical applicability claim. A full manuscript with detailed methods, validation data, and statistical analysis would be required to assess whether the case is established.

## Risk / unsupported claims
- The claim that MD simulations guided the design of ProB is unsupported without simulation details and experimental validation.
- The claim that the linker fine-tuned domain convergence is unsupported without structural or functional evidence.
- The claim that the biosensor performance "reached the requirements of clinical application" is unsupported without clinical context or matrix validation.
- The reported LOD, EC50, detection time, and working range are unverifiable without replicate data and calibration curves.
- The "bacterial enrichment strategy" is mentioned but not defined, making its contribution to performance unassessable.