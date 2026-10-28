## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use molecular dynamics simulations and dynamic network analyses to propose that UPF1's ATPase cycle requires synergistic binding of ATP and RNA, mediated by allosteric coupling between the Apo, ATP-bound, and ATP-RNA-bound (catalytic transition) states. They further claim that allostery signaling preferentially involves the RecA1 domain over RecA2, correlating with sequence conservation across human SF1 helicases.
- **Visible evidence base** Abstract text only; no quantitative data, simulation parameters, or methodological details provided
- **Missing materials affecting confidence** Full methods, simulation protocols, force field parameters, convergence criteria, free energy calculation details, allostery potential definitions, network analysis parameters, sequence conservation analysis, and all figures/tables

## Reviewer
- **Overall assessment** The abstract presents an interesting hypothesis that allosteric coupling between ATP and RNA binding drives UPF1's ATPase cycle, potentially reconciling its mutually exclusive binding behavior with its dual enzymatic activities. However, the evidence base is entirely descriptive at the abstract level, with no quantitative results, error estimates, or methodological validation. The central claims, particularly the "first come, first served" mechanism and the domain preference argument, cannot be evaluated from the supplied material. The work may be of interest to computational biophysicists and RNA surveillance researchers, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Researchers studying nonsense-mediated mRNA decay, SF1 helicase mechanisms, and allosteric regulation in ATP-dependent enzymes would find the proposed framework relevant. Computational biologists interested in dynamic network analysis and free energy landscape approaches for protein conformational transitions may also be interested, as the study applies these methods to a biologically significant system.
- **Major strengths** The abstract addresses a genuine mechanistic puzzle, namely the mutually exclusive binding of ATP and RNA in UPF1, and proposes a unifying allosteric framework. The use of multiple crystal states (Apo, ATP-bound, ATP-RNA-bound) is appropriate for probing conformational transitions. The attempt to generalize findings to other SF1 helicases via sequence conservation adds potential broader relevance.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is moderate, as allosteric coupling in helicases has been explored, though the specific "first come, first served" proposal is novel. Scientific importance is potentially high for the NMD and helicase fields, but this is not demonstrated from the abstract. Interdisciplinary readership is plausible, spanning structural biology, computational chemistry, and RNA biology, but the abstract lacks sufficient detail to engage nonspecialists. Technical soundness cannot be assessed without methods and quantitative results. Readability for nonspecialists is adequate in prose but the mechanistic claims require more context and evidence to be accessible.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is intriguing, but the abstract provides no quantitative support, and the key claims are unverifiable without full methodological and numerical details.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that free energy calculations show an uphill transition from Apo to ATP-bound state and a downhill transition to the catalytic transition state in the presence of ATP and RNA.
- **Evidence pointer** Abstract, free energy calculations section, location not provided
- **Concern** The abstract reports qualitative directions of free energy changes but provides no numerical values, error bars, or comparison to experimental data. Without quantitative free energy differences, the claim that one transition is uphill and another is downhill is not verifiable. Additionally, the simulation conditions, convergence criteria, and statistical sampling are not described.
- **Why it matters** The central mechanistic conclusion depends on the relative free energy barriers and minima among the three states. If the free energy calculations are not converged or are based on insufficient sampling, the entire proposed cycle could be an artifact of the simulation setup.
- **Resolution test** Provide the computed free energy differences with uncertainties, demonstrate convergence through block analysis or replicate simulations, and compare to any available experimental binding or kinetic data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Conceptual validity
- **Claim pointer** The authors propose a "first come, first served" mechanism where synergistic binding of ATP and RNA is required to drive the ATPase cycle, based on allostery potential analyses.
- **Evidence pointer** Abstract, allostery potential analyses section, location not provided
- **Concern** The concept of "allostery potential" is not defined in the abstract, and the criteria for classifying a state as "allosterically trapped" or "mutually allosterically activated" are absent. The interpretation that high allostery potential leads to a "first come, first served" mechanism is a significant conceptual leap that requires a clear operational definition and validation of the allostery metric.
- **Why it matters** The proposed mechanism is the main novel contribution. If the allostery potential metric is not rigorously defined or validated against known allosteric systems, the mechanistic conclusion is unsupported.
- **Resolution test** Define the allostery potential metric explicitly, validate it on systems with known allosteric behavior, and show that the classification of states is robust to parameter choices and simulation length.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** The authors claim that UPF1's allostery signaling pathways prefer the RecA1 domain over RecA2, and that this preference coincides with higher sequence conservation in RecA1 across typical human SF1 helicases.
- **Evidence pointer** Abstract, final sentence, location not provided
- **Concern** The abstract states this as a demonstration, but no data are shown. The sequence conservation analysis is not described, the number of SF1 helicases examined is not given, and the statistical significance of the correlation is not reported. The claim that this "may apply to other SF1 helicases" is speculative without comparative simulation or experimental evidence.
- **Why it matters** The broader relevance to SF1 helicases is a key selling point for interdisciplinary interest. Without a rigorous comparative analysis, this claim is an unsupported extrapolation.
- **Resolution test** Provide the sequence conservation data, the list of SF1 helicases analyzed, statistical tests for the correlation, and ideally comparative simulations on at least one other SF1 helicase to test the domain preference.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, "catalytic transition state" phrase, location not provided
- **Issue** The term "catalytic transition state" is ambiguous. It could refer to a transition state in the chemical reaction or a conformational state along the ATPase cycle. This ambiguity may confuse readers.
- **Required correction** Clarify whether this is a Michaelis complex, a transition state analog, or a distinct conformational state, and use standard nomenclature if available.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods description
- **Evidence pointer** Abstract, simulation methods, location not provided
- **Issue** The abstract does not specify the force field, water model, simulation length, or number of replicas. This is insufficient for reproducibility.
- **Required correction** Include key simulation parameters in the abstract or indicate that full details are in the methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Biological relevance
- **Evidence pointer** Abstract, "reconcile UPF1's ATPase and RNA helicase activities" phrase, location not provided
- **Issue** The abstract claims reconciliation but does not explain how the proposed allosteric cycle resolves the mutually exclusive binding observation in a way that is consistent with known biochemical data on UPF1's helicase activity.
- **Required correction** Add a brief statement connecting the proposed cycle to experimental observations of ATPase and helicase activities, or acknowledge that this is a hypothesis requiring experimental testing.

## Risk / unsupported claims
- The claim that the transition from Apo to ATP-bound state is uphill and to catalytic transition state is downhill is unsupported without quantitative free energy data.
- The "first come, first served" mechanism is unsupported without a defined and validated allostery potential metric.
- The claim that allostery signaling prefers RecA1 over RecA2 and correlates with sequence conservation is unsupported without data.
- The generalization to other SF1 helicases is speculative and not demonstrated.
- The reconciliation of ATPase and helicase activities is asserted but not explained mechanistically in the abstract.