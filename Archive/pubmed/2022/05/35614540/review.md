## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract, with no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report 20.8 microseconds of molecular dynamics simulations of wildtype p53 in apo and DNA-bound states at 300 K and 310 K, followed by Markov State Modeling (MSM) using C(alpha)-C(alpha) distances filtered by correlation with time-independent components. They claim that at physiological temperature (310 K), apo-p53 exposes its hydrophobic core due to movement of the S6/7 beta-turn and N-terminal apart, and that DNA-bound p53 shows an open conformation of loop L1 weakening DNA binding. They propose the S6/7 beta-turn and loop L2 as potential therapeutic targets.
- **Visible evidence base** Abstract text only; no simulation details, MSM validation metrics, structural figures, or quantitative results are provided
- **Missing materials affecting confidence** Full methods, simulation parameters, force field details, convergence criteria, MSM validation (e.g., implied timescales, Chapman-Kolmogorov tests), structural ensembles, free energy surfaces, error estimates, and any comparison with experimental data

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting application of MSM to study temperature-sensitive conformational changes in p53, but the claims are largely qualitative and cannot be evaluated without the underlying data. The central conclusions about hydrophobic core exposure and weakened DNA binding at 310 K are plausible but unsupported by quantitative evidence in the abstract. The study may be of interest to computational biophysicists and cancer researchers, but the current evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Computational biophysicists studying protein conformational dynamics and allostery would be interested in the MSM methodology applied to a cancer-relevant protein. Structural biologists and cancer researchers focused on p53 function and mutant rescue strategies may find the proposed target regions (S6/7 beta-turn, loop L2) relevant, though experimental validation would be needed.
- **Major strengths** The use of long-timescale simulations (20.8 microseconds total) is commendable. The focus on temperature-sensitive behavior at physiological versus sub-physiological temperatures addresses a biologically relevant question. The identification of specific structural regions (N-terminal, S6/7 beta-turn, loop L2) provides a concrete hypothesis for future studies.
- **Major Concerns** The abstract lacks quantitative support for all major claims. No free energy differences, population shifts, or structural metrics are reported. The MSM construction and validation are not described in sufficient detail to assess reliability. The link between simulated conformational changes and functional outcomes (DNA binding weakening) is inferred rather than demonstrated.
- **Minor Comments** The abstract would benefit from clearer definitions of "temperature-sensitive" regions and how they were identified. The statement about "rescue strategies" is speculative and not supported by the presented data.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative evidence for hydrophobic core exposure), R1-M2 (lack of MSM validation details), R1-M3 (unsupported inference of functional impact on DNA binding)
- **Assessment against Nature-style criteria** Originality: Moderate, as MSM has been applied to p53 before, but the temperature comparison is a useful angle. Scientific importance: Potentially high for p53 biology, but not established from the abstract. Interdisciplinary readership: Limited, as the abstract is technical and lacks accessible context for non-specialists. Technical soundness: Cannot be assessed without methods and validation data. Readability for nonspecialists: Poor, as terms like tICs and MSM are used without explanation.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if technical concerns are resolved with full data and validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "At physiological temperatures, apo-p53 exhibits exposure of its hydrophobic core, where the temperature-sensitive hotspot residues were also located."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The claim of hydrophobic core exposure is presented without any quantitative metric, such as solvent accessible surface area changes, residue-residue contact probabilities, or free energy differences between states at 300 K and 310 K. No error bars or statistical significance are reported.
- **Why it matters** Without quantitative evidence, the reader cannot judge whether the observed difference is robust or an artifact of limited sampling or analysis choices. The claim is central to the paper's biological conclusion.
- **Resolution test** Provide numerical values for solvent accessible surface area or contact maps for the hydrophobic core residues at both temperatures, with uncertainty estimates and statistical tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Markov State Modeling (MSM) analyses were performed, considering C(alpha)-C(alpha) distances as reaction coordinates."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not describe how the MSM was validated, including the number of states, lag time selection, implied timescale convergence, or Chapman-Kolmogorov tests. Without these, the MSM results cannot be considered reliable.
- **Why it matters** MSM results are only meaningful if the model is Markovian and converged. Inadequate validation can lead to spurious states and incorrect conclusions about conformational populations.
- **Resolution test** Include in the full manuscript a detailed MSM validation section with implied timescale plots, state count sensitivity analysis, and Chapman-Kolmogorov test results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** "In the DNA-bound p53 system, loop L1 attains an open conformation at physiological temperatures, which weakens the DNA binding."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract asserts that an open loop L1 conformation weakens DNA binding, but no binding free energy calculations, contact analysis with DNA, or experimental correlation are provided. The causal link is inferred, not demonstrated.
- **Why it matters** The functional interpretation is a key selling point of the study. Without direct evidence linking the conformational change to binding affinity, the claim remains speculative.
- **Resolution test** Provide binding free energy estimates (e.g., MM-PBSA or similar) or DNA contact occupancy changes between 300 K and 310 K, or cite experimental data supporting the correlation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract text
- **Issue** The term "temperature-sensitive" is used without defining which residues or regions are considered temperature-sensitive and how this was determined.
- **Required correction** Define temperature-sensitive regions explicitly, e.g., based on prior experimental data or on observed structural changes in this study.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract structure
- **Evidence pointer** Abstract text
- **Issue** The abstract uses technical terms (tICs, MSM) without brief explanations, which may alienate non-specialist readers.
- **Required correction** Add a brief parenthetical explanation for tICs and MSM, or rephrase to be more accessible.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Speculation
- **Affected element** Conclusion
- **Evidence pointer** Abstract text
- **Issue** The statement about "rescue strategies" and "regions to be targeted" is speculative and not supported by the data presented.
- **Required correction** Soften the language to indicate these are potential directions for future work, not established conclusions.

## Risk / unsupported claims
- The claim of hydrophobic core exposure at 310 K is unsupported without quantitative structural data.
- The claim that loop L1 opening weakens DNA binding is unsupported without binding affinity or contact analysis.
- The proposal of S6/7 beta-turn and loop L2 as therapeutic targets is speculative and not backed by functional experiments.
- The overall reliability of the MSM results is unassessable without validation details.