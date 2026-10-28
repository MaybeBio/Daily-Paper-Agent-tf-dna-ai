## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific claims, methodology, data interpretation, and internal consistency as presented in the provided text. No external validation or replication attempted.
- **Shared manuscript claim summary** The authors report that all three eukaryotic SMC complexes (cohesin, condensin, SMC5/6) extrude DNA asymmetrically during active phases, that cohesin and SMC5/6 can switch direction, and that direction switching in cohesin is linked to NIPBL exchange, with STAG1 stabilizing NIPBL and suppressing switches.
- **Visible evidence base** Single-molecule DNA loop extrusion assays; kymograph-based segmentation; fluorescence imaging; AlphaFold2 structural predictions; statistical analyses (Markov chain testing, Mann-Whitney U tests, Fisher's exact tests). Figures referenced: 1, 2, 3, 4, 5; supplementary figures S1–S5.
- **Missing materials affecting confidence** No raw data, full statistical outputs, or source videos provided. Supplementary figures and methods are referenced but not fully included in the provided text. No detailed description of image analysis algorithms or validation of the symmetry indicator metric.

## Reviewer
- **Overall assessment** This manuscript presents a significant and potentially field-altering claim: that all eukaryotic SMC complexes share an asymmetric DNA loop extrusion mechanism, with apparent symmetric extrusion being a result of frequent direction switches. The single-molecule data appear carefully acquired and the analysis is thoughtful. However, the central claims rest on a novel metric (the "symmetry indicator") and on interpretations of NIPBL exchange dynamics that require stronger quantitative support and clearer presentation. The manuscript is of high interest but currently does not fully establish the case from the provided evidence.
- **Who would be interested in the results, and why** Researchers in chromosome biology, genome organization, single-molecule biophysics, and molecular motor mechanisms. The claim of a unified asymmetric extrusion mechanism across SMC complexes would reshape models of loop extrusion and genome folding. The proposed direction-switch mechanism involving NIPBL exchange is also of direct relevance to understanding cohesin regulation and CTCF boundary function.
- **Major strengths** 1. Direct single-molecule comparison of three SMC complexes under comparable conditions. 2. Clear distinction between active extrusion, diffusion, and slipping phases, with quantitative segmentation. 3. The symmetry indicator provides a simple, interpretable metric for classifying extrusion symmetry. 4. The NIPBL exchange data directly link subunit turnover to direction switching. 5. Mechanistic models (DNA strand exchange) are well-reasoned and testable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (symmetry indicator validation), R1-M2 (NIPBL exchange causality), R1-M3 (SMC5/6 monomer claim), R1-M4 (statistical power and reporting).
- **Assessment against Nature-style criteria**  
  *Originality*: High. The claim that all SMC complexes extrude asymmetrically and that direction switching is a shared feature is novel and challenges existing literature.  
  *Scientific importance*: High. If correct, this unifies the mechanism of SMC-driven loop extrusion and has implications for genome organization models.  
  *Interdisciplinary readership*: Broad. The work bridges biophysics, molecular biology, and genomics. The writing is generally accessible, though some methods sections are dense.  
  *Technical soundness*: Moderate. The experimental design is sound, but the central metric and the causal link between NIPBL exchange and direction switching require stronger validation.  
  *Readability for nonspecialists*: Good. The introduction and discussion are clear, but the results section assumes familiarity with single-molecule techniques.
- **Recommendation posture** Supportive if technical concerns are resolved. The core observations are likely correct, but the manuscript currently overreaches in its causal claims and would benefit from additional validation and more cautious interpretation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The symmetry indicator (ΔL_dir1/ΔL_dir2) is used to classify extrusion phases as asymmetric or symmetric, with thresholds of <0.1 for asymmetric and ≍1 for symmetric.
- **Evidence pointer** Results section "All eukaryotic SMC complexes extrude DNA asymmetrically"; Figure 2D–H
- **Concern** The symmetry indicator is introduced without a formal derivation of its expected distribution under different models. The threshold of 0.1 is arbitrary and not justified by error analysis. It is unclear how measurement noise, DNA dye intercalation effects, or localization uncertainty propagate into this ratio. The authors report 92 ± 4% of cohesin phases as asymmetric, but the confidence interval is binomial only and does not account for systematic errors in phase segmentation.
- **Why it matters** The central claim of the paper rests on this metric. If the threshold is too permissive, phases that are actually symmetric could be misclassified as asymmetric, inflating the conclusion that all SMC complexes extrude asymmetrically.
- **Resolution test** Provide a calibration of the symmetry indicator using simulated data with known ground truth (e.g., simulated symmetric vs. asymmetric extrusion traces with realistic noise). Show that the 0.1 threshold robustly separates the two classes. Alternatively, present the full distribution of ΔL_dir1/ΔL_dir2 values and demonstrate bimodality or a clear separation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** "Extrusion direction switches coincide with an exchange of NIPBL on cohesin" and "STAG1 stabilizes NIPBL on cohesin, preventing NIPBL turnover and direction switches."
- **Evidence pointer** Results section "Extrusion direction switches coincide with an exchange of NIPBL on cohesin"; Figures 3H–M, 4F–I
- **Concern** The correlation between NIPBL exchange and direction switching is strong, but the causal direction is not established. It is possible that direction switching causes NIPBL release, or that both are downstream of a common trigger (e.g., ATP hydrolysis state). The claim that STAG1 "prevents" direction switches is based on correlative data (excess STAG1 reduces switch frequency) but no direct manipulation of STAG1 binding was performed. The statement "STAG1 stabilizes NIPBL" is inferred from residence time measurements, but alternative explanations (e.g., STAG1 affecting NIPBL rebinding kinetics rather than dissociation) are not excluded.
- **Why it matters** The proposed model (NIPBL exchange enables direction switching) is a key mechanistic claim. If the causality is reversed or confounded, the model would need substantial revision.
- **Resolution test** Perform experiments where NIPBL exchange is prevented (e.g., using a non-exchangeable NIPBL mutant or crosslinking) and test whether direction switching is abolished. Alternatively, use a FRET-based sensor to directly monitor NIPBL binding state during direction switching with higher temporal resolution.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "All three monomeric SMC complexes extrude DNA strictly asymmetrically within these phases" and "yeast SMC5/6 extrudes already as a monomer."
- **Evidence pointer** Results section "All eukaryotic SMC complexes extrude DNA asymmetrically"; Figure 2G–H; Supplementary Figures S2F–I
- **Concern** The claim that SMC5/6 functions as a monomer contradicts a previous report (Pradhan et al., ref. 7) that only dimers extrude. The authors provide evidence for monomeric extrusion, but the stoichiometry determination relies on single-molecule fluorescence intensity, which can be ambiguous. The manuscript does not provide a rigorous calibration of the fluorescence intensity to the number of SMC5/6 complexes, nor does it address potential artifacts from incomplete labeling or photobleaching.
- **Why it matters** If SMC5/6 can extrude as a monomer, this has major implications for the mechanism of loop extrusion and the role of dimerization. The discrepancy with prior work must be resolved convincingly.
- **Resolution test** Provide a detailed calibration of the fluorescence intensity per SMC5/6 complex, including a step-wise photobleaching analysis to confirm the number of labeled subunits. Additionally, perform a control experiment with a labeled SMC5/6 subunit that is known to be essential for dimerization and show that monomeric complexes still extrude.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** Various quantitative claims, including "92 ± 4% of all extrusion phases exhibited a value of ΔL_dir1/ΔL_dir2 below 0.1" and "NIPBL-ΔN resides on average 1.7-times longer on cohesin in the presence of a 12-fold excess of STAG1."
- **Evidence pointer** Results sections; Figures 2D, 4H
- **Concern** The manuscript reports confidence intervals and p-values, but the number of independent experiments, the number of molecules analyzed, and the statistical methods are not fully described. For example, the Mann-Whitney U test p-values are reported, but the effect sizes and the number of independent replicates are not stated. The Fisher's exact test p-values are reported, but the contingency tables are not shown. The manuscript would benefit from a more transparent reporting of sample sizes and statistical power.
- **Why it matters** The conclusions rely on quantitative comparisons. Without clear reporting of sample sizes and statistical methods, the robustness of the findings cannot be assessed.
- **Resolution test** Provide a supplementary table with the number of molecules, number of independent experiments, and the full statistical output for each key comparison. State the statistical software and version used.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Introduction; Results section "Phases of active DNA loop extrusion are interspersed by loop diffusion and loop slipping"
- **Issue** The terms "asymmetric," "unidirectional," and "bidirectional" are used in ways that may confuse readers. "Asymmetric" refers to the geometry of DNA incorporation, while "unidirectional" and "bidirectional" refer to the temporal sequence of direction changes. This distinction should be made explicit early in the manuscript.
- **Required correction** Define these terms clearly in the introduction and use them consistently throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "Quantification and segmentation of kymographs"
- **Issue** The manual segmentation of kymographs is a potential source of bias. The manuscript states that segmentation was performed manually but does not describe any inter- or intra-observer variability checks or a blinded analysis protocol.
- **Required correction** Describe the segmentation protocol in more detail, including whether the analyst was blinded to the experimental condition, and report a measure of segmentation reproducibility (e.g., a subset of traces segmented by two independent analysts).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section "Mechanistic models that enable DNA strand exchange"
- **Issue** The discussion of the two mechanistic models is interesting but does not clearly state which predictions would distinguish them experimentally. The authors mention that the models are "sufficiently general" but do not provide specific, testable predictions.
- **Required correction** Add a paragraph outlining specific experimental tests that could discriminate between the two models (e.g., FRET-based measurements of DNA strand position during switching, or mutations that specifically disrupt one pathway).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Figure 2
- **Issue** The symmetry indicator is plotted as a distribution, but the figure does not show the raw data points or the number of phases analyzed. The reader cannot assess the spread of the data or the robustness of the threshold.
- **Required correction** Add a panel showing the raw data points (e.g., a scatter plot) and state the number of phases analyzed in the figure legend.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section "The physiological relevance of extrusion direction switching"
- **Issue** The claim that "direction switching is likely inherent to cohesin-mediated DNA loop extrusion" is based on in vitro observations. The extrapolation to in vivo relevance is reasonable but speculative. The authors should more clearly distinguish between what is demonstrated in vitro and what is hypothesized for in vivo function.
- **Required correction** Soften the language in this section and explicitly state that the in vivo relevance is a hypothesis that remains to be tested.

## Risk / unsupported claims
- The claim that "all eukaryotic SMC complexes extrude DNA asymmetrically" is supported for the three complexes tested, but the generalization to all eukaryotic SMCs is an extrapolation.
- The claim that "apparent 'symmetric' loop extrusion is the result of frequent direction switches" is presented as a general conclusion but is only directly demonstrated for cohesin and SMC5/6.
- The statement that "STAG1 stabilizes NIPBL on cohesin, preventing NIPBL turnover and direction switches" implies a causal role for STAG1 that is not directly tested.
- The mechanistic models in Figure 5 are speculative and not directly tested by the experiments presented.
- The claim that "direction switching is likely inherent to cohesin-mediated DNA loop extrusion" is an interpretation that goes beyond the direct observations.