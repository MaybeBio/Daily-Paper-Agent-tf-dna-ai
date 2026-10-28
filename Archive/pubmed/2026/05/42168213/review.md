## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without supplementary figures/tables or referenced external data.
- **Assessment boundary** Scientific claims, methodological soundness, evidence consistency, and alignment with Nature-style criteria. Editorial or formatting issues are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors report a hierarchical multi-timescale structural dynamics of the intrinsically disordered p53 N-terminal transactivation domain (p53-TAD), spanning fast (ns) reorientation, sub-microsecond helix folding/unfolding, and multi-microsecond transient tertiary structure formation. They combine high-power 1HN E-CPMG relaxation dispersion NMR at 1.2 GHz and supercooled conditions with millisecond-scale atomistic MD simulations, and validate the simulations against multiple experimental observables. They propose that the free energy landscape of this IDP is hierarchically structured, similar to folded proteins, with implications for binding promiscuity.
- **Visible evidence base** Main text figures 1–5 (described in text), methods section, and references to supplementary figures/tables (not provided in the supplied material).
- **Missing materials affecting confidence** Supplementary figures and tables (e.g., all RD profiles, force field comparisons, convergence analyses, Markov state model details, PDB search results), the reporting summary, and any source data files. Without these, several quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious and largely compelling combination of state-of-the-art NMR relaxation dispersion and long-timescale MD simulations to characterize the structural dynamics of a prototypical IDP. The central claim, that p53-TAD exhibits a hierarchical multi-timescale dynamics landscape with sub-microsecond helix folding and multi-microsecond transient tertiary structure formation, is well supported by the qualitative agreement between simulations and multiple independent experimental observables. The work addresses a significant gap in IDP biophysics, namely the slow (supra-τc) dynamics that are difficult to access experimentally. However, several concerns regarding quantitative rigor, convergence of the MD sampling, and the interpretation of the stretched CPMG model need to be addressed before the case is fully established. The manuscript is well written and will be of broad interest to the IDP and biophysics communities.
- **Who would be interested in the results, and why** Researchers in the fields of intrinsically disordered proteins, NMR spectroscopy, molecular dynamics simulations, and protein folding. The work is also relevant to those studying p53 biology and the molecular basis of promiscuous protein-protein interactions. The methodological combination of high-power RD NMR and millisecond MD simulations, and the introduction of a stretched CPMG model, will be of interest to method developers.
- **Major strengths**
  - The combination of high-power 1HN E-CPMG at 1.2 GHz with supercooled conditions to access supra-τc dynamics is a significant technical advance, addressing a previously inaccessible timescale window for IDPs.
  - The unbiased, millisecond-scale MD simulations, validated against a wide range of independent experimental observables (chemical shifts, RD profiles, TRACT, SAXS, FRET, PET-FCS), provide a strong basis for structural interpretation.
  - The identification of a hierarchy of three distinct dynamic tiers, with the slow tier 0 involving transient tertiary structure formation, challenges the prevailing view of IDP energy landscapes as shallow and unstructured.
  - The use of a stretched CPMG model to account for a broad distribution of relaxation timescales is conceptually novel and well motivated by the simulation data.
  - The manuscript is clearly written and the figures (as described) effectively summarize the key findings.
- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: No)
  - **R1-M4** (Blocking: No)
  - **R1-M5** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
- **Technical failings that need to be addressed before the case is established** R1-M1 (MD convergence and rare-event sampling), R1-M2 (quantitative agreement between simulated and experimental RD profiles), and R1-M3 (interpretation of the stretched CPMG model).
- **Assessment against Nature-style criteria**
  - **Originality** High. The work introduces a novel combination of techniques and presents a new conceptual framework for IDP dynamics, moving beyond simple two-state or shallow landscape models.
  - **Scientific importance** High. The findings have implications for understanding IDP function, particularly binding promiscuity and molecular recognition, and for the general understanding of protein energy landscapes.
  - **Interdisciplinary readership** High. The work bridges NMR spectroscopy, MD simulations, polymer physics, and cell biology (p53 function), making it of interest to a broad readership.
  - **Technical soundness** Moderate to high. The experimental and simulation methodologies are state-of-the-art, but the quantitative agreement between simulation and experiment, and the convergence of the MD sampling, require further scrutiny.
  - **Readability for nonspecialists** Good. The manuscript is well structured and the main concepts are explained clearly, although some sections (e.g., the stretched CPMG model) may be challenging for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are novel and potentially important, but the quantitative rigor of the simulation-experiment comparison and the interpretation of the stretched CPMG model need to be strengthened.

### Major Concern Details

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their MD simulations "reveal" the structural dynamics underlying the observed NMR RD signals, and that the simulations are "validated against NMR" based on good agreement of RD profiles and other observables.
- **Evidence pointer** Results section "Unbiased atomistic simulations validated against NMR"; Figure 2B, F–I; Methods section "Markov state model analysis".
- **Concern** The manuscript reports a total of 2.4 ms of MD simulation (30 trajectories of 20-60 μs each). While this is substantial, the identification of rare, long-lived (multi-μs) transient tertiary structures, and the claim that these are the structural origin of the tier 0 dynamics, requires evidence that the sampling is converged. The authors state that "rare and longer-lived tertiary structures may have been missed by our simulations," which is an honest caveat, but it also undermines the quantitative interpretation of the tier 0 timescale (215 μs). The convergence of the Markov state model, and the statistical significance of the 18 (WT) and 75 (P27A) identified long-lived events, are not demonstrated. The authors should provide a more rigorous analysis of sampling convergence (e.g., split-half analysis, implied timescale plots, or comparison of independent trajectory blocks) to support the claim that the observed dynamics are representative of the equilibrium ensemble.
- **Why it matters** The central claim of the paper is the identification of a hierarchical dynamics landscape. If the MD sampling is not converged, the relative populations and lifetimes of the identified states, and hence the interpretation of the tier 0 and tier 1 dynamics, may be unreliable. This would weaken the central conclusion that the free energy landscape of p53-TAD is hierarchically structured.
- **Resolution test** Provide a convergence analysis of the MD simulations, e.g., by showing that the identified long-lived states and their lifetimes are reproducible across independent trajectory blocks, or by demonstrating that the Markov state model is robust to changes in the number of states or the lag time. If convergence cannot be demonstrated, the authors should temper their claims about the quantitative nature of the tier 0 dynamics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim "good agreement" between measured and simulated RD profiles, with an "average deviation of ~15%".
- **Evidence pointer** Results section "Unbiased atomistic simulations validated against NMR"; Figure 2B, F–I; Supplementary Figures 4 and 5.
- **Concern** The manuscript states that the comparison between experiment and simulation was "restricted to the low CPMG-frequency region" due to high-power artifacts. This is a reasonable approach, but the criteria for "good agreement" are not quantified beyond the average deviation. A 15% average deviation may be acceptable for some residues, but the authors also note "typical deviation" for Leu25 (Figure 2I). The manuscript does not provide a statistical test of the agreement, nor does it discuss whether the deviations are systematic (e.g., due to force field inaccuracies) or random. Furthermore, the comparison of RD amplitudes (Figure 2B) is made at a single CPMG frequency (100 s⁻¹), which may not be the most sensitive frequency for the dynamics of interest. The authors should provide a more detailed and quantitative comparison, e.g., by fitting the simulated and experimental RD profiles over the full accessible frequency range and reporting the goodness-of-fit for each residue.
- **Why it matters** The validation of the MD simulations against NMR is the cornerstone of the paper's claim that the simulations can be used to interpret the experimental data. If the agreement is only qualitative, or if it is not rigorously quantified, the structural interpretation of the dynamics (e.g., the identification of helix folding as the cause of tier 1) is less secure.
- **Resolution test** Provide a residue-by-residue comparison of simulated and experimental RD profiles, including a statistical measure of agreement (e.g., reduced chi-squared). Discuss any systematic deviations and their potential causes (e.g., force field, missing proline isomerization). If the agreement is not quantitative, the authors should clearly state the limitations of the validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors interpret the stretched CPMG model (γ ≈ 0.6) as evidence for a broad distribution of relaxation timescales, arising from a multi-state Markov model with a hierarchy of energy barriers.
- **Evidence pointer** Results section "Tier 1: sub-microsecond supra-τc dynamics"; Methods section "Fitting of 2-state CPMG model and stretched CPMG model to RD profiles calculated from MD simulations"; Supplementary Figure 6.
- **Concern** The stretched CPMG model is introduced as a generalization of the two-state model, but the physical interpretation of the stretching parameter γ is not fully developed. The authors state that γ = 1 indicates a two-state process and smaller values indicate a broader distribution of timescales, but they do not provide a direct link between the fitted γ and the underlying energy barrier distribution. The manuscript would benefit from a more explicit discussion of how the stretched model relates to the Markov state model, and whether the fitted γ is consistent with the distribution of transition times extracted from the MD simulations (Figure 3C). Furthermore, the authors should discuss whether other models (e.g., a sum of discrete exponentials) could also fit the data, and whether the stretched model is uniquely justified.
- **Why it matters** The stretched CPMG model is a key methodological innovation of the paper, and its interpretation underpins the claim of a hierarchical energy landscape. If the model is not uniquely justified, or if its interpretation is ambiguous, the strength of this claim is reduced.
- **Resolution test** Provide a more detailed analysis of the stretched CPMG model, including a comparison of the fitted γ with the distribution of transition times from the MD simulations. Discuss alternative models and why the stretched model is preferred. If possible, provide a direct visualization of the energy barrier distribution implied by the fitted γ.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the P27A mutation increases the helical population from 30% to 60% and that this is "probably a consequence" of the increased affinity to MDM2.
- **Evidence pointer** Results section "Tier 1: sub-microsecond supra-τc dynamics"; Figure 2C.
- **Concern** The manuscript does not provide a direct experimental measurement of the helical population of the P27A mutant. The 60% value appears to be derived from the MD simulations, but the text is ambiguous. If this is a simulation prediction, it should be clearly stated as such, and the authors should discuss whether this prediction is consistent with any experimental data (e.g., circular dichroism or NMR chemical shifts). The link between increased helical population and increased MDM2 affinity is speculative and should be presented as such.
- **Why it matters** The P27A mutant is used as a key control to test the hypothesis that tier 1 dynamics are related to helix folding. If the helical population of the mutant is not experimentally verified, the interpretation of the mutant data is less secure.
- **Resolution test** Clarify the source of the 60% helical population value. If it is from simulations, state this explicitly and discuss any experimental evidence that supports or contradicts it. If possible, provide experimental measurements of the helical population of the P27A mutant.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the MD simulations are validated against a wide range of experimental observables, including SAXS, FRET, PET-FCS, and PRE.
- **Evidence pointer** Results section "Unbiased atomistic simulations validated against NMR"; Supplementary Figures 12–15.
- **Concern** The manuscript states that "good agreement is seen for all these observables" but does not provide the actual comparisons in the main text. The supplementary figures are not provided in the supplied material, so the quality of the agreement cannot be assessed. The authors should provide at least a summary of these comparisons in the main text, including the quantitative measures of agreement (e.g., chi-squared values, correlation coefficients).
- **Why it matters** The claim that the simulations are validated against multiple independent observables is a major strength of the paper. If the agreement is not quantitatively demonstrated, this strength is weakened.
- **Resolution test** Provide a summary of the comparisons to SAXS, FRET, PET-FCS, and PRE data in the main text, including quantitative measures of agreement. If the agreement is poor for some observables, discuss the implications.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1B
- **Evidence pointer** Figure 1B
- **Issue** The schematic in Figure 1B is described as showing "three distinct tiers of structural dynamics" but the timescales are given as ranges (e.g., "215 µs and 4 µs" for tier 0, "4 µs and 80 ns" for tier 1). It is unclear whether these are the timescales at 263 K or 298 K, and how the extrapolation from 263 K to 298 K was performed.
- **Required correction** Clarify the temperature at which the timescales are reported and describe the extrapolation method in the figure legend or methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Tier 1"
- **Evidence pointer** Results section "Tier 1: sub-microsecond supra-τc dynamics"
- **Issue** The term "supra-τc dynamics" is used throughout the manuscript but is not defined explicitly. It is implied to mean dynamics slower than the overall tumbling time, but a formal definition would help the reader.
- **Required correction** Define "supra-τc dynamics" at first use, e.g., "dynamics occurring on timescales longer than the rotational correlation time τc".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Molecular dynamics simulations"
- **Evidence pointer** Methods section "Molecular dynamics simulations"
- **Issue** The methods state that "all WT simulations were 20 μs long and all P27A simulations were 60 μs long," but the number of independent trajectories and the total aggregate simulation time are not stated clearly. The text mentions "30 independent trajectories" in the Markov model section, but it is unclear if this applies to both WT and P27A.
- **Required correction** State the number of independent trajectories for each system and the total aggregate simulation time.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Fitting of 2-state CPMG model and stretched CPMG model"
- **Evidence pointer** Methods section "Fitting of 2-state CPMG model and stretched CPMG model to RD profiles calculated from MD simulations"
- **Issue** The methods describe the Bayesian fitting procedure but do not provide the specific priors used for the stretched CPMG model parameters (γ, Φ, τ). The priors for the two-state model are given, but not for the stretched model.
- **Required correction** Provide the priors used for all parameters in the stretched CPMG model.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors speculate that the transient tertiary structures may be "potential drug targets." This is an interesting but highly speculative statement, and it is not supported by any data in the manuscript. It may be better placed in a "future directions" context.
- **Required correction** Soften the claim or provide a more nuanced discussion of the potential implications.

## Risk / unsupported claims
- The claim that the MD simulations are "validated" against SAXS, FRET, PET-FCS, and PRE data is not verifiable from the supplied material, as the relevant supplementary figures are not provided.
- The claim that the P27A mutant has a 60% helical population is not clearly attributed to experiment or simulation.
- The claim that the transient tertiary structures may be "potential drug targets" is speculative and not supported by data.
- The quantitative interpretation of the tier 0 dynamics (215 µs) is limited by the acknowledged possibility that longer-lived structures may have been missed in the simulations.
- The claim that the stretched CPMG model is uniquely justified over other multi-state models is not fully established.