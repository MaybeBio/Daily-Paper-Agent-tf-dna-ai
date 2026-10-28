## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use homology modeling and all-atom simulations with a dual-basin structure-based potential to test whether a remodeled NTD beta-hairpin (beta3-beta4) lowers CTD stability and promotes domain dissociation in the metamorphic protein RfaH. They report partial support for this hypothesis, and additionally characterize a temperature-dependent reverse fold switch with an optimal temperature for switching kinetics.
- **Visible evidence base** Abstract text only; no quantitative data, simulation details, or statistical measures are provided
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, convergence criteria, error estimates, all figures and tables, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible and mechanistically motivated computational study of RfaH fold switching. The central hypothesis, that NTD beta-hairpin conformation modulates CTD stability and domain dissociation, is clearly stated and the simulation design is reasonable in principle. However, the abstract provides insufficient quantitative detail to evaluate the robustness of the findings. The absence of error estimates, convergence metrics, and a clear definition of the "optimal T" claim limits the current assessability. The reverse fold switch results are interesting but presented without sufficient kinetic or thermodynamic context. The work may be of interest to computational biophysicists and those studying metamorphic proteins, but the case for a definitive mechanistic conclusion is not fully established from the abstract alone.
- **Who would be interested in the results, and why** Computational biophysicists studying protein conformational switching and metamorphic proteins; structural biologists interested in transcription regulation mechanisms; method developers using structure-based models for domain dynamics. The study addresses a specific mechanistic question about RfaH that could inform broader understanding of coupled domain dissociation and fold switching.
- **Major strengths** The hypothesis is well-defined and mechanistically motivated. The use of a dual-basin structure-based potential is appropriate for studying conformational transitions. The study addresses both forward and reverse fold switching, providing a more complete picture than many single-direction studies. The authors acknowledge the limitation that complete refolding was not observed, which is scientifically honest.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative support for the central claim), R1-M2 (definition and support for the optimal T claim), R1-M3 (lack of convergence and error assessment)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of a dual-basin model to RfaH is not entirely novel, but the specific focus on the beta3-beta4 hairpin as a trigger is a targeted and somewhat original angle.
  - Scientific importance: Moderate. RfaH is a well-studied model for metamorphic proteins, and understanding the coupling between domain dissociation and fold switching has general relevance. However, the findings are incremental and do not fundamentally challenge existing models.
  - Interdisciplinary readership: Limited. The work is primarily of interest to computational biophysicists and structural biologists; the abstract does not frame the results for a broader biological audience.
  - Technical soundness: Not fully assessable from the abstract. The methods are appropriate in principle, but the lack of quantitative detail and error analysis prevents a robust evaluation.
  - Readability for nonspecialists: The abstract is clearly written and the logic is easy to follow, though some terms (e.g., "dual-basin structure-based potential") assume familiarity with computational methods.
- **Recommendation posture** Supportive if technical concerns are resolved. The hypothesis is interesting and the simulation approach is appropriate, but the current abstract does not provide sufficient quantitative evidence to fully establish the central claims. A revised version with detailed error analysis, convergence metrics, and clearer definitions of key quantities would strengthen the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for central claim
- **Claim pointer** "For H(1) we find, in line with our hypothesis, that the CTD exhibits lower stability and the domains dissociate at a lower temperature T, as compared to free RfaH."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract states that H(1) shows lower CTD stability and lower dissociation temperature, but no quantitative values, error bars, or statistical significance are reported. It is unclear how "lower" is defined and whether the difference is robust across simulation replicates or initial conditions.
- **Why it matters** The central hypothesis rests on this comparison. Without quantitative support, the claim that the beta-hairpin conformation aids domain dissociation is not established. A difference of a few degrees or a marginal stability change could be within simulation noise.
- **Resolution test** Provide numerical values for dissociation temperatures and stability measures (e.g., free energy differences) for both free RfaH and H(1), with error estimates from multiple independent simulations. Report whether the differences are statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Definition and support for optimal T claim
- **Claim pointer** "Consequently, our simulations suggest an optimal T at which fold switching is most rapid. At this T, the stabilities of both folds are reduced."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The concept of an "optimal T" for fold switching is presented without a clear definition. Is this the temperature at which the rate is maximal? What is the shape of the rate versus temperature curve? The claim that "stabilities of both folds are reduced" at this T is vague and not quantified.
- **Why it matters** This is a potentially interesting kinetic prediction, but without a defined rate law, a clear measure of stability, or a quantitative description of the temperature dependence, the claim is not testable or falsifiable from the abstract.
- **Resolution test** Provide a plot or table of fold-switching rates as a function of temperature, with error bars. Define how "stability" is measured (e.g., free energy of the folded state relative to unfolded) and show how it varies with T. State the uncertainty in the location of the optimal T.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Convergence and error assessment
- **Claim pointer** "We then use an all-atom physics-based model enhanced with a dual basin structure-based potential to simulate domain separation driven by the thermal unfolding of the CTD with NTD in a fixed, folded conformation."
- **Evidence pointer** Abstract only; location not provided
- **Concern** No information is provided about simulation length, number of replicates, equilibration protocols, or convergence criteria. For a study that draws conclusions about relative stability and kinetics, the absence of any convergence or error assessment is a significant gap.
- **Why it matters** Structure-based models can be sensitive to simulation length and initial conditions. Without evidence that the observed differences between free RfaH and H(1) are reproducible and converged, the conclusions may be artifacts of insufficient sampling.
- **Resolution test** Report simulation lengths, number of independent runs, and convergence metrics (e.g., block averaging, autocorrelation times). Show that the key observables (dissociation temperature, switching rates) are stable across replicates and simulation time.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** "dual-basin structure-based potential"
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "dual-basin structure-based potential" is not defined. Readers unfamiliar with this specific method may not understand what it means or how it differs from standard structure-based models.
- **Required correction** Provide a brief definition or a reference to the method in the abstract, or clarify in the full text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of the reverse switch description
- **Affected element** "we study the reverse fold switch in which RfaH returns from a domain-open all-beta state to its domain-closed all-alpha state"
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that the reverse switch is studied but does not describe the simulation setup for this direction. Is the starting structure the same H(1) or a different construct? How is the "domain-open all-beta state" modeled?
- **Required correction** Briefly describe the initial conditions for the reverse switch simulations in the abstract or indicate where this is detailed in the full text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Biological relevance framing
- **Affected element** "both inter-domain interactions and conformational changes within NTD may be important for the proper functioning of RfaH"
- **Evidence pointer** Abstract; location not provided
- **Issue** The concluding sentence is vague. It does not specify how the simulation results inform the biological function of RfaH in transcription regulation or translation initiation.
- **Required correction** Add a sentence that connects the simulation findings to a specific functional consequence, or state explicitly that such a connection is beyond the scope of the current study.

## Risk / unsupported claims
- The claim that H(1) exhibits "lower stability" and "dissociate at a lower temperature" is unsupported without quantitative data and error estimates.
- The claim of an "optimal T" for fold switching is unsupported without a defined rate measure and temperature-dependent data.
- The statement that "a change in beta3-beta4 orientation aids in, but is not sufficient for, domain dissociation" is partially supported by the observation that complete refolding was not seen, but the negative result is not quantified.
- The general conclusion that "both inter-domain interactions and conformational changes within NTD may be important" is a reasonable inference but is not directly tested as a hypothesis in the described simulations.
- Any claim about biological relevance to transcription regulation or translation initiation is not supported by the abstract, as no functional assays or in vivo data are mentioned.