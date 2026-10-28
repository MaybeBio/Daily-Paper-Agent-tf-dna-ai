## Review setup
- **Input scope** Full manuscript text (main text, no supplementary figures or tables provided)
- **Assessment boundary** Scientific claims, experimental design, statistical analysis, theoretical modeling, and interpretation as presented in the main text
- **Shared manuscript claim summary** The authors report that DNA looping in the lac system of individual E. coli bacteria confers robustness to transcriptional repression across multiple cell divisions, despite perturbations from cell division, gene dosage changes, and repressor concentration variations. They observe exponential (memoryless) distributions of OFF intervals in looping strains, insensitivity to a 100-fold increase in repressor concentration, and propose a three-state kinetic model to explain these findings.
- **Visible evidence base** Main text figures (Figs. 1–3), statistical values reported in text (means, SEs), qualitative descriptions of distributions, reference to SI Appendix (Figs. S5–S8, Table S1) without full data
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S8), raw time-series data, full strain construction details, complete model parameter values, statistical test details, and code implementation specifics

## Reviewer
- **Overall assessment** This manuscript addresses an important question in gene regulation: how DNA looping maintains stable repression in individual cells over many generations despite intracellular perturbations. The experimental approach using the mother machine with single-cell resolution is appropriate and technically demanding. The observation of exponential OFF intervals in looping strains is surprising and potentially significant. However, the manuscript has several weaknesses that need to be addressed: the statistical analysis is incompletely described, the theoretical model is simplified and not rigorously validated against alternatives, and the mechanistic interpretation of the "local concentration" hypothesis remains speculative. The claim of robustness across cell divisions is supported by the data, but the mechanistic basis is not fully established.
- **Who would be interested in the results, and why** Researchers in gene regulation, single-cell biology, biophysics of transcription, and synthetic biology would be interested. The findings challenge assumptions about the fragility of DNA-looping-mediated repression and have implications for understanding how cells maintain stable gene expression states. The work also contributes to the growing literature on stochastic gene expression and phenotypic variability.
- **Major strengths** 1) The use of the mother machine to track individual cells over many generations is a powerful approach that provides direct evidence for multigenerational repression stability. 2) The comparison between Loops and No-loop strains with and without high repressor concentration is well designed and yields clear qualitative differences. 3) The observation of exponential OFF intervals in looping strains is unexpected and provides a strong constraint for theoretical models. 4) The theoretical model, while simplified, captures key qualitative features and generates testable predictions.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical analysis incompleteness), R1-M2 (model validation), R1-M3 (mechanistic interpretation)
- **Assessment against Nature-style criteria** **Originality**: The finding that DNA looping confers robustness across cell divisions with memoryless OFF intervals is novel and challenges existing assumptions. **Scientific importance**: The work addresses a fundamental question in gene regulation with implications for understanding phenotypic stability. **Interdisciplinary readership**: The topic bridges molecular biology, biophysics, and quantitative biology, making it of interest to a broad audience. **Technical soundness**: The experimental approach is sound, but the statistical analysis and model validation are incomplete, reducing confidence in the conclusions. **Readability for nonspecialists**: The manuscript is generally well-written and accessible, though some sections (theoretical model) may be challenging for non-quantitative readers. Overall, the manuscript has the potential to be a significant contribution, but the current evidence does not fully establish the mechanistic claims.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical rigor and model validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that OFF intervals follow exponential distributions in Loops strains and that burst sizes show specific distributional properties (long tails, linear regions in semilog space).
- **Evidence pointer** Fig. 2C, Fig. 3A, text in "Statistics of Promoter Leakiness with and without DNA Looping"
- **Concern** The manuscript does not provide sufficient statistical details to evaluate the claim of exponential distributions. No goodness-of-fit tests, confidence intervals, or comparisons against alternative distributions (e.g., gamma, Weibull) are reported. The number of cells, number of OFF intervals per cell, and how these were pooled across cells are not stated. The statement that distributions are "exponential" appears to be based on visual inspection of semilog plots, which is insufficient. Additionally, the comparison between Loops and No-loop strains (e.g., mean OFF intervals, burst sizes) lacks formal statistical testing (e.g., p-values, effect sizes).
- **Why it matters** The exponential distribution is a central claim of the paper, as it underpins the memoryless one-step process interpretation. Without rigorous statistical validation, the claim is not established. Similarly, the quantitative comparisons between strains are essential for the robustness argument.
- **Resolution test** Provide formal statistical tests for distribution fitting (e.g., likelihood ratio tests, Kolmogorov-Smirnov tests with appropriate corrections), report sample sizes and pooling methods, and include statistical comparisons (with effect sizes and uncertainty) for all strain comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The authors claim that a three-state model without cell division can reproduce the experimentally observed statistics, including exponential OFF intervals and robustness to repressor concentration.
- **Evidence pointer** Fig. 2C (Insets), "A Theoretical Model without Cell Division" section, SI Appendix (Fig. S8)
- **Concern** The theoretical model is presented with only a few parameter values (ku = 0.10 min⁻¹, kt = 20 VenusNB·min⁻¹, kon = 0.28 per molecule per min, nL = 1,080 for Loops). No details are given on how these parameters were estimated or constrained. The model's ability to reproduce the data is only shown qualitatively in insets, with no quantitative comparison (e.g., goodness-of-fit metrics, parameter uncertainty). The claim that simulations without cell division can reproduce the data is central, but the failure of the cell-division-perturbation model (SI Appendix, Fig. S8) is not described in sufficient detail to evaluate. Furthermore, the model assumes a specific mechanism (local concentration) that is not directly tested.
- **Why it matters** The model is used to support the mechanistic interpretation of robustness. Without rigorous model validation and parameter estimation, the model's predictions are not convincing, and alternative models (e.g., with different kinetic schemes) cannot be excluded.
- **Resolution test** Provide a detailed description of parameter estimation (e.g., fitting procedure, data used), quantify the agreement between model and data (e.g., likelihood, chi-square), and perform model comparison against plausible alternatives (e.g., models with cell division effects, different looping kinetics).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The authors propose that a high "local" repressor concentration, shared between old and new DNA copies during replication, explains the robustness of DNA looping across cell divisions.
- **Evidence pointer** "Discussion" section
- **Concern** The "local concentration" hypothesis is speculative and not directly supported by experimental evidence. The authors acknowledge this in the Discussion, but the claim is presented as a plausible explanation without alternative hypotheses being considered. The estimate that the in vivo loop lifetime is ~10³ s and the open loop ~1 s is based on in vitro measurements and assumptions that are not fully detailed. The argument that the local concentration is shared during replication is not mechanistically explained.
- **Why it matters** The mechanistic interpretation is a key part of the paper's significance. If the local concentration hypothesis is not well-supported, the broader implications for gene regulation are weakened.
- **Resolution test** Provide additional experimental or theoretical support for the local concentration mechanism, or explicitly discuss alternative explanations (e.g., slow rebinding kinetics, chromatin structure effects) and how they could be distinguished.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 2C
- **Evidence pointer** Fig. 2C
- **Issue** The figure legend does not specify the number of cells or biological replicates represented in the distributions. The inset simulations are not clearly labeled with parameter values.
- **Required correction** Add sample sizes and replicate information to the figure legend, and clearly label simulation parameters in the inset.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data and code availability
- **Evidence pointer** "Data, Materials, and Software Availability" section
- **Issue** The statement that time-series data are deposited in Harvard Dataverse is good, but the code link is provided without a version or DOI. The code is described as available at a GitHub URL, but no specific release or commit is referenced.
- **Required correction** Provide a DOI or versioned release for the code, and ensure the Dataverse deposit includes all raw data and analysis scripts.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** "Materials and Methods" section
- **Evidence pointer** "Materials and Methods" section
- **Issue** The description of the probabilistic algorithm for promoter activity inference is only referenced to SI Appendix. Given its importance, a brief summary of the algorithm's key steps should be included in the main text.
- **Required correction** Add a concise description of the algorithm in the main text, including how autofluorescence fluctuations are handled.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Fig. 3B
- **Evidence pointer** Fig. 3B
- **Issue** The collapse of normalized promoter activity curves across strains is interpreted as evidence for a common cell-cycle dependence. However, the normalization by mean activity may obscure differences in the shape of the cell-cycle dependence. The authors should show the unnormalized data or provide a quantitative test of curve collapse.
- **Required correction** Provide a quantitative comparison of the normalized curves (e.g., confidence intervals on the collapsed curve) or show unnormalized data for clarity.

## Risk / unsupported claims
- The claim that OFF intervals follow exponential distributions is not statistically validated (R1-M1).
- The claim that the three-state model reproduces experimental data is not quantitatively demonstrated (R1-M2).
- The "local concentration" hypothesis for robustness across cell divisions is speculative and not directly supported (R1-M3).
- The statement that "the particular choice of carbon source is not expected to profoundly affect the spontaneous leakiness of the promoter" is based on a reference to SI Appendix, Fig. S7, which was not provided for review; this claim is not assessable from the supplied material.
- The claim that "the burst size of the Loops strain has already been reduced to its lowest limit, which, we reasoned, may be associated with the synthesis of only one mRNA per pulse" is an interpretation not directly tested.
- The estimate of in vivo loop lifetime (~10³ s) is based on in vitro measurements and assumptions not fully detailed in the main text; this is not assessable from the supplied material.