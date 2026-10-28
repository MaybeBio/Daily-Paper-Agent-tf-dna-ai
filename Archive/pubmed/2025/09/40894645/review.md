## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided; no figures, tables, or supplementary information were available for inspection.
- **Assessment boundary** Scientific claims, methodological soundness, and technical rigor as assessable from the text alone. Figure content, numerical data, and supplementary algorithms could not be independently verified.
- **Shared manuscript claim summary** The authors present a multi-objective, machine learning-guided cell-free gene expression workflow for engineering allosteric transcription factor (aTF)-based biosensors. They apply this to PbrR, a lead-responsive aTF, to simultaneously improve lead sensitivity and reduce zinc cross-reactivity, ultimately demonstrating a freeze-dried, colorimetric biosensor capable of detecting lead in real municipal drinking water samples at concentrations near the U.S. EPA action level (10 ppb).
- **Visible evidence base** Text descriptions of screening rounds (Rounds 0, 1, 2, 2b, 3, 3b, 5), mutant counts, selection criteria, and endpoint assay results. References to Figures 1-6, Figures S1-S6, Tables S1, and Algorithms S1-S2, none of which were provided.
- **Missing materials affecting confidence** All figures, tables, supplementary information, source data, and code. Without these, quantitative claims (e.g., detection limit of ~5.7 ppb, fold-change values, specificity metrics) cannot be verified. The ML model architecture details are partially described but training curves, validation metrics, and generation statistics are absent.

## Reviewer
- **Overall assessment** This manuscript describes a technically ambitious integration of active learning, sequence-to-sequence language models, and cell-free expression for multi-objective biosensor engineering. The conceptual advance—using directional tokens on paired mutant comparisons rather than numerical predictors—is genuinely interesting and could have broad applicability. The application to PbrR is well-motivated given the public health relevance of lead contamination. However, the manuscript as presented has several critical gaps: the core quantitative claims cannot be evaluated without the figures and supplementary data; the ML methodology lacks sufficient detail on validation, baselines, and failure modes; and the comparison to prior work is incomplete. The engineering outcome (a lead sensor with improved selectivity) is plausible but the evidence base provided is insufficient to establish it rigorously.
- **Who would be interested in the results, and why** Researchers in synthetic biology, protein engineering, and biosensor development would be the primary audience. Those working on ML-guided directed evolution, particularly with allosteric proteins or multi-objective optimization, would find the directional token approach of interest. Environmental monitoring and point-of-use diagnostics communities would also be interested given the demonstrated application to lead detection in drinking water. The cell-free expression and lyophilization aspects may appeal to those developing field-deployable diagnostics.
- **Major strengths** 1) The conceptual framing of multi-objective optimization via directional tokens on paired data is a novel and potentially powerful departure from standard MLDE approaches. 2) The integration of a high-throughput cell-free screening platform with ML-guided design is practically compelling and addresses a real bottleneck in biosensor engineering. 3) The application is well-chosen: lead contamination is a serious public health issue, and the EPA action level provides a clear, quantitative target. 4) The iterative DBTL loop with rational design complementing ML predictions is a pragmatic and thoughtful strategy. 5) The demonstration of lyophilized, colorimetric detection in real municipal water samples is a strong translational step.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "We tune the sensitivity of PbrR to sense at the U.S. Environmental Protection Agency (EPA) action level for lead and modify the selectivity away from zinc" and "enabling a diagnostic capable of detecting lead in drinking water down to ~5.7 ppb."
  - **Evidence pointer** Figures 2, 6; Figure S1-S4; location not provided for specific data points
  - **Concern** The central quantitative claims—detection at the EPA action level, selectivity over zinc, and the ~5.7 ppb detection limit—are presented in the abstract and results text but the actual data supporting them (dose-response curves, selectivity ratios, detection limit calculations) are in figures that were not provided for review. The text describes outcomes qualitatively (e.g., "higher fluorescent signal to lead than zinc") but without numerical values, error bars, or statistical tests, these claims cannot be assessed.
  - **Why it matters** The entire premise of the work is that the engineered biosensor meets specific performance criteria. Without access to the underlying data, the core claims are unverifiable. The detection limit of 5.7 ppb is a precise number that must be traceable to a specific calculation method (e.g., 3σ above blank, 95% confidence interval) and replicate data.
  - **Resolution test** Provide the dose-response curves for lead and zinc for the final engineered variant, including replicate data, fitted parameters, and the statistical method used to determine the detection limit. Show the selectivity comparison against wild-type and previously engineered variants.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological rigor
  - **Claim pointer** "Our approach rapidly generates high-quality sequence-to-function data, which we transform into an augmented paired dataset to train an ML model using directional labels that capture how aTF mutations alter performance."
  - **Evidence pointer** Materials and Methods, "Multi-Objective Controlled Extrapolation" and "Training Data Construction"; Figure 4; Algorithms S1-S2
  - **Concern** The ML methodology is described at a high level but lacks critical details needed to evaluate its validity. Specifically: (1) The threshold τκ for assigning direction labels is mentioned but its determination is not described. (2) The augmentation strategy (up to M² pairs) raises concerns about data leakage between training and validation, which is not addressed. (3) No baseline comparisons are provided (e.g., against standard regression-based MLDE, or against random mutagenesis). (4) The model's predictive accuracy on held-out data is not reported. (5) The claim that the model "eliminates the need for numerical predictors" is presented as an advantage, but the trade-offs (e.g., loss of magnitude information) are not discussed.
  - **Why it matters** The methodological novelty is the core intellectual contribution. If the ML approach cannot be shown to outperform simpler alternatives, or if the evaluation protocol is flawed, the central claim of the paper is undermined. The paired-data augmentation strategy in particular could lead to inflated performance estimates if not carefully handled.
  - **Resolution test** Provide: (1) a clear description of how τκ was set, (2) an evaluation protocol that prevents data leakage (e.g., grouping pairs by source mutant), (3) comparison against at least one baseline method, and (4) quantitative metrics of model performance (e.g., top-k accuracy, correlation with experimental measurements on held-out variants).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Completeness of comparison
  - **Claim pointer** "An in vivo directed evolution study improved lead selectivity of PbrR but did not address lead sensitivity. Additionally, our previous engineering campaign improved lead sensitivity of PbrR to the EPA action level64, but the best mutants also activate in the presence of zinc."
  - **Evidence pointer** Introduction, paragraph 3; Results, "PbrR as a model allosteric transcription factor for biosensor design"
  - **Concern** The manuscript references prior PbrR engineering efforts but does not provide a quantitative comparison of the final engineered variants against these prior best performers. The claim of improvement is implicit but not demonstrated with head-to-head data under identical assay conditions.
  - **Why it matters** For the field to assess the value of the ML-guided approach, it must be shown to outperform not just wild-type but also previously engineered variants. Without this comparison, the incremental benefit of the new method is unclear.
  - **Resolution test** Include a direct comparison of the final engineered variant(s) against the best previously reported PbrR variants (from both the in vivo evolution study and the authors' prior work) for lead sensitivity, zinc cross-reactivity, and dynamic range, measured in the same assay.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** "We next tested if our PbrR-based biosensor could be freeze-dried and remain functional to detect lead in water samples" and "we demonstrated that the biosensor works in real-world municipal water samples to detect lead."
  - **Evidence pointer** Results, "Freeze-dried, cell-free PbrR biosensors as a diagnostic assay for lead in drinking water"; Figure 6
  - **Concern** The demonstration in real water samples is described but the number of samples, the range of water chemistries tested, the criteria for "detection," and the reproducibility across batches of lyophilized sensors are not specified. The text mentions samples from Evanston and Chicago but does not state how many households, how many replicates per sample, or whether the sensor performance was consistent across different water matrices.
  - **Why it matters** For a point-of-use diagnostic, robustness across real-world sample matrices is essential. A demonstration in one or two water samples is anecdotal; the claim of practical utility requires a broader validation.
  - **Resolution test** Specify the number of independent water samples tested, the range of background ion concentrations, the false positive/negative rates, and the batch-to-batch variability of lyophilized sensor performance.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results, "Active learning-guided optimization" section
  - **Evidence pointer** Figure 4B, Figure S1
  - **Issue** The text states "there were two mutants (D64K_N83F and N83I_K104V) that showed a higher fluorescent response to lead than zinc" but does not specify the magnitude of this difference or the assay conditions (e.g., lead and zinc concentrations used for the comparison).
  - **Required correction** Provide the specific lead and zinc concentrations used for the selectivity screen and the quantitative fluorescence values (or fold differences) for these two mutants.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Results, "Active learning-guided optimization" section
  - **Evidence pointer** Figure 4D
  - **Issue** The term "Round 2b" is introduced for a rational design round, but the naming convention is not explained. It is unclear whether this is a sub-round of Round 2 or a separate round.
  - **Required correction** Clarify the naming convention for rounds (e.g., "b" indicating a rational design round interleaved between ML-guided rounds).
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results, "Freeze-dried, cell-free PbrR biosensors" section
  - **Evidence pointer** Figure 6C, 6D, 6G
  - **Issue** The text states "n = 3 replicates unless otherwise noted" but does not report error bars, confidence intervals, or statistical significance for the key comparisons (e.g., lyophilized vs. fresh sensor performance, lead-spiked vs. unspiked water samples).
  - **Required correction** Add statistical details to figure legends or text for all quantitative comparisons, including the test used and the resulting p-values or confidence intervals.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Discussion, paragraph 2
  - **Evidence pointer** Location not provided
  - **Issue** The discussion mentions "we expect that our dataset will help support general advances in ML-model development for synthetic biology" but does not describe the dataset size, composition, or how it will be made available beyond the code repository link.
  - **Required correction** Provide dataset statistics (number of variants, sequence diversity, assay conditions) and clarify the data availability format.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Materials and Methods, "DNA library generation"
  - **Evidence pointer** Location not provided
  - **Issue** The method for generating mutant libraries via linear expression templates (LETs) is referenced to prior work, but the specific primers and PCR conditions for this study are not fully described.
  - **Required correction** Include the full primer sequences and PCR cycling conditions, or provide a clear reference to the prior protocol with explicit indication of any modifications.
- **Technical failings that need to be addressed before the case is established** 1) The absence of all figures and supplementary data prevents verification of the central quantitative claims (R1-M1). 2) The ML evaluation methodology lacks baseline comparisons and leakage controls (R1-M2). 3) No head-to-head comparison against prior PbrR variants is provided (R1-M3). 4) The real-world water sample validation is insufficiently described (R1-M4).
- **Assessment against Nature-style criteria**  
  *Originality*: The directional token approach for multi-objective optimization on paired mutant data is a creative and potentially original contribution. The application to aTF-based biosensors in cell-free systems is not entirely new (the authors cite prior work), but the specific combination of ML-guided design with cell-free screening for simultaneous multi-parameter tuning appears novel.  
  *Scientific importance*: The public health motivation (lead in drinking water) is strong, and the general problem of engineering allosteric proteins for biosensing is of broad significance. If the claims are substantiated, the work could provide a template for similar engineering efforts. However, the importance is somewhat tempered by the lack of demonstrated superiority over existing approaches.  
  *Interdisciplinary readership*: The work bridges ML, synthetic biology, and environmental diagnostics, which could attract readers from multiple communities. The writing is generally accessible, though the ML methods section assumes familiarity with transformer architectures.  
  *Technical soundness*: Cannot be fully assessed from the text alone. The experimental workflow appears carefully designed, but the ML methodology has unresolved questions about validation and baselines. The absence of data makes it impossible to evaluate the robustness of the conclusions.  
  *Readability for nonspecialists*: The abstract and introduction are clear and well-motivated. The results section is reasonably accessible, though some ML-specific terminology (e.g., "directional tokens," "sequence-to-sequence architecture") may be opaque to readers without computational background. The methods section is appropriately detailed for specialists.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising and the application is well-motivated, but the absence of figures, data, and sufficient methodological detail prevents verification of the core claims. The manuscript could become publishable if the authors provide the missing data, strengthen the ML evaluation with baselines and leakage controls, and include direct comparisons against prior engineered variants. I would be supportive if these technical concerns are resolved.

## Risk / unsupported claims
- The detection limit of ~5.7 ppb for lead in drinking water is unverifiable without the underlying dose-response data and calculation methodology.
- The claim of "500-fold improvement in sensitivity from a previous report" is not traceable to specific data in the provided text.
- The assertion that the ML model "eliminates the need for numerical predictors" is presented as an advantage but is not supported by comparative analysis.
- The claim that the workflow "can generalize to other biosensors and proteins" is speculative and not demonstrated in this manuscript.
- The statement that "137 mutants have lead selectivity over zinc" in Round 3b is a specific quantitative claim that cannot be verified without the underlying screening data.
- The claim that the engineered biosensor "could be used as an effective point-of-use diagnostic" is supported only by a limited demonstration in municipal water samples; the number of samples and reproducibility are not specified.