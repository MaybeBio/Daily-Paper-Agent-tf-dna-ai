## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors critically evaluate the REST2 protocol for sampling intrinsically disordered proteins (IDPs), identify artificial conformational compaction at high effective temperatures leading to replica segregation, and propose a new REST3 protocol with re-calibrated solute-solvent van der Waals scaling to improve sampling efficiency and reduce replica requirements.
- **Visible evidence base** Abstract, Introduction, Methods, Results and Discussion, Conclusions, figure captions referenced in text (Figures 1-8, S1-S11), tables referenced (Tables S1, S2)
- **Missing materials affecting confidence** Full figures and tables not provided; simulation parameter details (e.g., specific REST3 scaling values beyond κm) partially described; no access to raw trajectory data or convergence diagnostics beyond those described

## Reviewer
- **Overall assessment** This manuscript addresses an important technical limitation in a widely used enhanced sampling method. The identification of REST2-induced artificial compaction in IDPs is a significant finding with practical implications. The proposed REST3 protocol is conceptually sound and supported by the presented simulation data. However, the evidence base is incomplete without access to the actual figures and tables, and several claims regarding convergence and efficiency improvements require more rigorous quantitative support. The work is likely of interest to the computational biophysics community, but the case for broad applicability would be strengthened by additional validation across diverse systems.
- **Who would be interested in the results, and why** Computational biophysicists and chemists who use enhanced sampling methods for biomolecular simulations, particularly those studying IDPs or other dynamic protein systems. Developers of enhanced sampling algorithms and force field parameterization efforts would also find the analysis of REST2 limitations and the REST3 protocol design relevant. The work has potential methodological impact for anyone performing explicit solvent simulations of disordered proteins.
- **Major strengths** The manuscript identifies a specific, mechanistically explained artifact in REST2 (solute-solvent interaction imbalance) and connects it to practical consequences (replica segregation, reduced sampling efficiency). The proposed REST3 modification is simple, physically motivated, and directly addresses the identified problem. The use of two IDPs with distinct structural features (p53-NTD and KID) provides some generality. The analysis of replica exchange metrics (round trips, acceptance rates) and conformational properties (radius of gyration, helicity) is appropriate for evaluating sampling quality.
- **Major Concerns** The most significant concern is the lack of a rigorous theoretical or systematic basis for the κm calibration. The choice of κm = 1.06 at 500 K appears empirical, and the linear interpolation for intermediate temperatures is not justified. The claim that REST3 "eliminates" conformational trapping is strong, given that only one folding simulation per system was performed for REST3 (except p53-NTD with 2 μs). The comparison of convergence between REST2 and REST3 relies on visual inspection of distributions and PCA plots, which is subjective; quantitative metrics (e.g., overlap coefficients, effective sample sizes) would strengthen the case. The statement that "at least about half of the computational sources can be saved" is based on a single comparison (16 vs 8 replicas) and may not generalize. The manuscript does not address potential limitations of REST3 for folded proteins or systems where compaction at high temperature might be physically realistic.
- **Minor Comments** The notation for scaling factors (λ, κ) could be clarified with a summary table in the main text. The choice of a99SB-disp as the sole force field for REST3 validation limits generalizability; testing with another force field would be informative. The discussion of "entropic barriers" in the Conclusions is brief and could be expanded to explain why tempering alone is insufficient. The manuscript would benefit from a more explicit statement of the computational cost comparison (e.g., total CPU/GPU hours) between REST2 and REST3 protocols.
- **Technical failings that need to be addressed before the case is established** The empirical calibration of κm without a systematic optimization or theoretical derivation; the lack of quantitative convergence metrics beyond qualitative distribution comparisons; the absence of error estimates for key quantities (e.g., round trip rates, ensemble averages) in some analyses; the single-system demonstration of the 8-replica REST3 protocol.
- **Assessment against Nature-style criteria** Originality: The identification of REST2's compaction artifact and the proposal of a tunable solute-solvent scaling parameter represent a novel contribution, though the concept of re-balancing Hamiltonian scaling is not entirely new. Scientific importance: The work addresses a practical limitation of a widely used method, with potential to improve sampling of IDPs, which is a growing area of interest. Interdisciplinary readership: The topic is specialized to computational biophysics; broader interest would require clearer demonstration of biological insights enabled by REST3. Technical soundness: The simulation protocols are generally appropriate, but the κm calibration lacks rigor and the convergence analysis is not fully quantitative. Readability for nonspecialists: The manuscript is clearly written for a specialist audience; the abstract and introduction are accessible, but the methods and results assume familiarity with enhanced sampling techniques.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the justification of κm calibration and the addition of quantitative convergence metrics.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of the proposed method
- **Claim pointer** The authors claim that "the scaling of the solute-solvent interactions can be treated as free parameters" and propose a specific κm calibration to "reproduce the levels of protein chain expansion at high effective temperatures."
- **Evidence pointer** Methods section, REST algorithm; Results and Discussion, "Re-balancing the solute-solvent interactions in REST3"; Table S2
- **Concern** The calibration of κm is presented as a proof of concept, but the choice of κm = 1.06 at 500 K and the linear interpolation for other temperatures appear arbitrary. The authors do not provide a systematic procedure for determining κm for a given system or temperature range, nor do they demonstrate that this calibration is transferable beyond the two IDPs tested. The claim that κm can be "tuned" implies a general strategy, but the manuscript lacks guidance on how to do this in practice.
- **Why it matters** Without a clear calibration protocol, the REST3 method cannot be reliably applied by other researchers. The empirical nature of κm selection undermines the methodological contribution and raises questions about whether the observed improvements are specific to the chosen parameters rather than a general property of the re-balancing approach.
- **Resolution test** The authors should provide a systematic method for determining κm, such as matching radius of gyration or other conformational properties to short unbiased simulations at each temperature, or a theoretical derivation based on the balance of interaction energies. Alternatively, they should demonstrate that the results are robust to reasonable variations in κm (e.g., sensitivity analysis) and that the chosen value is not finely tuned to the specific systems.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality for convergence claims
- **Claim pointer** The authors claim that REST3 "eliminates conformational trapping at high temperatures and the resulting replica segregation problem" and that it "greatly improves the efficiency of random walk in the temperature space."
- **Evidence pointer** Results and Discussion, "Over-compaction at high temperatures can lead to replica segregation in REST2" and "Re-balancing the solute-solvent interactions in REST3"; Figures 3, 5, S4-S6, S10
- **Concern** The evidence for improved convergence is largely qualitative, based on visual inspection of replica trajectories, radius of gyration distributions, and PCA plots. The authors report round trip rates (e.g., 30.3/μs vs 9-10/μs) but do not provide error bars or statistical tests to confirm these differences are significant. The claim that REST3 "eliminates" trapping is based on a single simulation per condition (except p53-NTD folding), which is insufficient to rule out stochastic variability. Additionally, the comparison of convergence between REST2 and REST3 for KID shows "substantial residual differences even for REST3 simulations," which undermines the claim of improved convergence.
- **Why it matters** The central argument for REST3's superiority rests on improved sampling efficiency and convergence. If the evidence is not quantitatively robust, the advantage of REST3 over REST2 is not convincingly established. The authors themselves acknowledge that "significant challenges" remain for tempering alone, which tempers the strength of their claims.
- **Resolution test** The authors should provide quantitative convergence metrics, such as ensemble overlap coefficients, effective sample sizes, or autocorrelation times for key observables, with error estimates from multiple independent simulations. They should also perform replicate simulations (at least 3) for each condition to assess variability and demonstrate that the observed improvements are reproducible.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and scope of claims
- **Claim pointer** The authors state that "REST3 leads much more efficient temperature random walk and improved sampling efficiency, which also further reduces the number of replicas required" and suggest that "at least about half of the computational sources can be saved compared to REST2."
- **Evidence pointer** Results and Discussion, "REST3 can further reduce the required number of replicas"; Figure 5, S10, S11
- **Concern** The claim of reduced replica requirements is based on a single comparison: a 16-replica REST3 run vs an 8-replica REST3 run for p53-NTD. The authors do not systematically explore the minimum number of replicas needed for REST3 to achieve convergence, nor do they compare the 8-replica REST3 to an equivalent 8-replica REST2 run. The generalizability of this finding to other systems, force fields, or temperature ranges is not demonstrated. The statement about "half of the computational sources" is an extrapolation that may not hold for larger or more complex systems.
- **Why it matters** The practical advantage of REST3 is a key selling point. If the replica reduction is not robustly demonstrated, the computational benefit may be overstated, and users may not achieve the claimed savings.
- **Resolution test** The authors should perform a systematic analysis of the minimum number of replicas required for both REST2 and REST3 to achieve comparable convergence for the same system, and ideally test this on at least one additional IDP or folded protein. They should also provide a more nuanced discussion of when replica reduction is feasible.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methodology
- **Affected element** Methods section, REST algorithm
- **Evidence pointer** Equations 1-6
- **Issue** The notation for scaling factors is somewhat confusing, particularly the distinction between λ and κ and how they combine in Equation 5. The relationship between the effective temperature Tm and the scaling factors is not explicitly stated for REST3.
- **Required correction** Provide a clear summary table or text explaining the values of λ and κ for each replica condition, and explicitly state how Tm is related to the scaling factors in REST3.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of validation
- **Affected element** Results and Discussion, "Conformational sampling and convergence of REST2 and REST3"
- **Evidence pointer** Figures 6-8
- **Issue** The comparison of convergence between REST2 and REST3 for p53-NTD is based on a single folding run for REST3, while REST2 has both control and folding runs. The lack of a control run for REST3 p53-NTD limits the ability to assess convergence from different initial conditions.
- **Required correction** Either perform a control REST3 simulation for p53-NTD or explicitly acknowledge this limitation and discuss its potential impact on the conclusions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Results and Discussion, "Severe over-compaction at high temperatures in REST2"
- **Evidence pointer** Figures 1, S2, S3
- **Issue** The authors attribute the compaction to the scaling scheme but do not discuss whether this artifact could be system-specific or force-field-specific. The observation that compaction occurs across all six force fields is noted, but the mechanistic explanation is brief.
- **Required correction** Expand the discussion to consider alternative explanations (e.g., force field biases) and whether the compaction artifact is expected to occur in all IDPs or only those with certain sequence properties.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation of computational cost
- **Affected element** Results and Discussion, "REST3 can further reduce the required number of replicas"
- **Evidence pointer** Not specified
- **Issue** The claim of computational savings is not quantified in terms of actual wall-clock time or GPU hours, which would be useful for practitioners.
- **Required correction** Provide a quantitative comparison of computational cost (e.g., total GPU hours) for the REST2 and REST3 simulations, and discuss the trade-offs.

## Risk / unsupported claims
- The claim that REST3 "eliminates" conformational trapping is not fully supported by the evidence, as only one simulation per condition was performed for REST3 (except p53-NTD folding).
- The statement that "at least about half of the computational sources can be saved" is an extrapolation from a single comparison and is not robustly demonstrated.
- The generalizability of the κm calibration to other systems, force fields, or temperature ranges is not established.
- The claim that REST2's compaction artifact is "force field and protein independent" is based on observations from six force fields but only two IDPs; this may not hold for all systems.
- The assertion that REST3 "reproduces the levels of protein chain expansion at high effective temperatures" is based on comparison to standard MD at 500 K, but the statistical significance of this match is not quantified.