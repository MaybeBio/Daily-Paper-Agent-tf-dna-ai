## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, methods, or supplementary material provided
- **Shared manuscript claim summary** The authors report that salmon protamine, an arginine-rich intrinsically disordered protein, binds DNA with nucleobase specificity, preferring GC over AT at the major groove (2.6:1) and AT over GC at the minor groove (2.1:1), with a net moderate GC bias. They support this with all-atom molecular dynamics simulations, free-energy calculations, and experimental aggregation assays using designed DNA sequences of varying GC content.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data
- **Missing materials affecting confidence** Full methods, simulation parameters, force field details, free-energy calculation protocols, experimental aggregation assay conditions, statistical analyses, and all primary data

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting claim that an intrinsically disordered protein can achieve nucleobase-specific DNA recognition, which would extend current understanding of IDP-DNA interactions. However, the evidence as summarized is insufficient to establish the central claims. The simulation-based selectivity ratios are presented without error estimates or convergence details, and the experimental aggregation data are described qualitatively. The mechanistic interpretation linking groove-specific preferences to net GC bias requires more rigorous support. The work is likely of interest to the biophysics and chromatin biology communities, but the current abstract does not provide enough detail for a robust evaluation.
- **Who would be interested in the results, and why** Researchers studying protein-DNA recognition mechanisms, particularly those focused on intrinsically disordered proteins and their functional roles. Chromatin biologists interested in sperm chromatin packaging and protamine function would also find the results relevant, as would computational biophysicists developing and testing force fields for IDP-nucleic acid interactions.
- **Major strengths** The study addresses a timely and important question about whether IDPs can exhibit sequence-specific DNA binding, which has been underexplored. The combination of all-atom simulations with experimental validation is commendable. The observation of groove-dependent selectivity reversal is a nuanced finding that could have mechanistic implications.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  **Originality** The claim that an IDP can achieve nucleobase-specific DNA recognition is conceptually novel, as sequence specificity is typically attributed to folded domains. However, the abstract does not fully contextualize this against prior work on IDP-DNA interactions, so the degree of novelty is difficult to assess.  
  **Scientific importance** If substantiated, the findings would have implications for understanding protamine function in sperm chromatin remodeling and transcription silencing, and more broadly for IDP-DNA recognition mechanisms. The importance is moderate to high, but the current evidence does not yet support the strength of the claims.  
  **Interdisciplinary readership** The topic bridges computational biophysics, molecular recognition, and chromatin biology, which could attract a broad readership. However, the abstract assumes familiarity with simulation methods and DNA structure terminology that may limit accessibility.  
  **Technical soundness** The technical approach is appropriate in principle, but the abstract lacks critical details on simulation convergence, force field validation, free-energy calculation methodology, and experimental reproducibility. The selectivity ratios are presented without statistical confidence, which undermines technical soundness as currently reported.  
  **Readability for nonspecialists** The abstract is generally clear but uses specialized terms (e.g., major groove, minor groove, G-tracts) without brief definitions. The logical flow from simulation to experiment is understandable, but the quantitative claims would benefit from more accessible framing.
- **Recommendation posture** Currently not established from the provided evidence. The central claims are plausible but require substantial additional detail and analysis to be convincing. I would be supportive if the technical concerns regarding simulation convergence, statistical rigor, and experimental quantification are resolved.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that protamine prefers GC over AT at the major groove by a 2.6-to-1 ratio and AT over GC at the minor groove by a 2.1-to-1 ratio, based on all-atom molecular dynamics simulations.  
- **Evidence pointer** Abstract, simulation results section (location not provided)  
- **Concern** The selectivity ratios are presented as single values without any indication of statistical uncertainty, convergence criteria, or replicate analysis. Molecular dynamics simulations of IDP-DNA interactions are notoriously sensitive to force field parameters and sampling length. Without error bars, convergence tests, or multiple independent simulations, these ratios cannot be evaluated for reliability.  
- **Why it matters** The central claim of nucleobase-specific recognition rests entirely on these quantitative ratios. If the ratios are not statistically robust or are force field dependent, the entire conclusion is undermined.  
- **Resolution test** Provide standard deviations or confidence intervals for the selectivity ratios, demonstrate convergence of the simulations (e.g., block averaging or multiple independent runs), and show that the results are consistent across at least two different force field parameter sets.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract states that free-energy calculations reinforce the simulation observations of GC preference.  
- **Evidence pointer** Abstract, free-energy calculations (location not provided)  
- **Concern** No details are given on the free-energy method used (e.g., umbrella sampling, metadynamics, MM-PBSA), the reaction coordinate, or the convergence of these calculations. Free-energy estimates for protein-DNA interactions are highly method dependent and can be subject to large systematic errors.  
- **Why it matters** The free-energy calculations are presented as independent support for the main claim. Without methodological details and convergence assessment, this supporting evidence cannot be evaluated.  
- **Resolution test** Specify the free-energy method, describe the reaction coordinate and sampling protocol, and provide convergence metrics (e.g., free-energy difference as a function of simulation time, hysteresis checks).

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality  
- **Claim pointer** The abstract claims that protamine-DNA mixtures form aggregates with increasing propensity at higher GC content and upon shuffling into G-tracts, as experimental validation.  
- **Evidence pointer** Abstract, experimental validation (location not provided)  
- **Concern** The experimental results are described only qualitatively. No quantitative measures of aggregation propensity are provided, such as turbidity values, particle sizes, or binding affinities. The number of DNA sequences tested, the range of GC content, and the experimental conditions are not specified.  
- **Why it matters** The experimental data are intended to validate the computational predictions. Without quantitative metrics and clear experimental design, the validation is not convincing and cannot be independently assessed.  
- **Resolution test** Provide quantitative aggregation measurements (e.g., absorbance at 350 nm, dynamic light scattering) with replicates and statistical analysis, and describe the full set of DNA sequences and experimental conditions.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Interpretation  
- **Claim pointer** The abstract concludes that the net effect is a moderate bias for GC over AT in protamine-base interactions, and that this has implications for protamine-mediated transcription silencing and remodeling of paternal chromatin.  
- **Evidence pointer** Abstract, conclusions (location not provided)  
- **Concern** The link between the observed GC bias and the proposed biological implications is speculative. The abstract does not explain how a moderate GC preference would lead to transcription silencing or chromatin remodeling, nor does it discuss whether the magnitude of the bias is biologically meaningful in the context of the sperm genome.  
- **Why it matters** The broader significance of the work depends on this interpretive leap. Without a mechanistic argument connecting the binding preference to functional outcomes, the implications remain unsupported.  
- **Resolution test** Provide a quantitative or mechanistic argument linking the observed selectivity to known features of protamine function, or temper the claims to match the evidence presented.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, first sentence  
- **Evidence pointer** Abstract, opening (location not provided)  
- **Issue** The term "intrinsically disordered proteins" is used without a brief definition, which may reduce accessibility for nonspecialist readers.  
- **Required correction** Add a brief parenthetical definition, such as "proteins lacking a fixed three-dimensional structure."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract, simulation details  
- **Evidence pointer** Abstract, methods summary (location not provided)  
- **Issue** The abstract states that eight copies of protamine wrap around a 35-bp DNA molecule, but does not specify the simulation time scale or whether this represents an equilibrium state.  
- **Required correction** Include the simulation length and a statement on whether the wrapping was stable over the simulation.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Precision  
- **Affected element** Abstract, selectivity ratios  
- **Evidence pointer** Abstract, results (location not provided)  
- **Issue** The ratios "2.6-to-1" and "2.1-to-1" are presented without context on how they were computed (e.g., per-residue contacts, hydrogen-bond occupancy).  
- **Required correction** Briefly specify the metric used to derive these ratios.

## Risk / unsupported claims
- The quantitative selectivity ratios (2.6:1 and 2.1:1) are unsupported without statistical uncertainty and convergence data.
- The claim that free-energy calculations reinforce the simulation observations is unsupported without methodological details.
- The experimental validation is unsupported as described, lacking quantitative measures and experimental design details.
- The biological implications for transcription silencing and paternal chromatin remodeling are speculative and not supported by the evidence presented in the abstract.
- The claim that this work demonstrates IDP nucleobase-specific DNA binding is not established from the provided evidence.