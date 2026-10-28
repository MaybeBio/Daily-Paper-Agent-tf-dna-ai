## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics simulations to study the coupled folding-binding process of the disordered rRNase domain of colicin E3 with its immunity protein Im3. They report that binding is dominantly triggered by the central segment of E3, that the N-terminal segment of E3 exhibits salt-concentration-dependent backtracking during binding, and that initial N-terminal binding leads to misorientation of a central hairpin, generating topological frustration that drives backtracking. They propose that topological frustration may be a general feature in IDP coupled folding-binding processes.
- **Visible evidence base** Abstract text only; no simulation details, quantitative results, figures, or statistical analyses are provided
- **Missing materials affecting confidence** Full manuscript, simulation methodology, force field parameters, salt concentration conditions, trajectory analysis details, free energy profiles, transition path sampling procedures, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a mechanistically interesting hypothesis regarding topological frustration in the coupled folding-binding of E3 and Im3, supported by coarse-grained simulations. However, the abstract alone provides insufficient quantitative evidence to evaluate the robustness of the claims. The central concepts, particularly the definition and detection of backtracking and topological frustration, are not operationally specified. The salt-concentration dependence is mentioned but not characterized. The generalization to IDP systems broadly is speculative given the single system studied. The work has potential interest for the protein folding and IDP communities, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying intrinsically disordered proteins, coupled folding-binding mechanisms, protein-protein recognition, and the role of topological effects in biomolecular dynamics. The proposed concept of topological frustration as a regulatory element in binding pathways could interest computational biophysicists and experimentalists working on IDP-target interactions, particularly those studying colicin-immunity protein systems.
- **Major strengths** The study addresses a mechanistically underexplored aspect of IDP binding, namely the role of topological frustration in pathway selection. The use of transition path analysis in addition to free energy analysis is appropriate for investigating kinetic mechanisms. The observation of salt-concentration-dependent backtracking suggests a potentially tunable regulatory feature. The system is biologically relevant and well-characterized experimentally, providing a solid context for simulation studies.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is moderate to high, as the topological frustration concept applied to IDP binding pathways is relatively novel. Scientific importance is potentially significant for the IDP field, but the abstract does not demonstrate broad implications beyond the specific system. Interdisciplinary readership is limited by the abstract's lack of accessible context for nonspecialists in simulation methodology. Technical soundness cannot be assessed from the abstract alone, as no methodological details or quantitative results are provided. Readability for nonspecialists is adequate in prose but insufficient in mechanistic clarity, as key terms are not defined.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and worth pursuing, but the abstract does not provide sufficient quantitative or methodological detail to support the claims. A revised version with full methodological transparency and quantitative results would be required for a supportive posture.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "backtracking of the N-terminal segment of E3 in the binding process" was observed and that "its occurrence depends on salt concentration."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract reports backtracking as a key observation but provides no operational definition of backtracking, no quantitative measure of its frequency or extent, and no data showing how salt concentration modulates it. No simulation conditions, salt concentrations tested, or statistical significance are given.
- **Why it matters** Backtracking is the central mechanistic claim. Without a clear definition and quantitative characterization, the phenomenon cannot be distinguished from ordinary diffusive motion or transient unbinding events. The salt-concentration dependence is stated but not demonstrated, leaving the claim unverifiable.
- **Resolution test** Provide a precise definition of backtracking with a detection criterion, report the frequency and extent of backtracking events under at least two salt concentrations, and include statistical analysis showing the difference is significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "initial binding of the N-terminal segment of E3 to Im3 usually leads to misorientation of a central hairpin of E3 on Im3, which generates topological frustration and results in backtracking."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The causal chain from N-terminal binding to hairpin misorientation to topological frustration to backtracking is asserted without any supporting quantitative evidence. No metric for misorientation, no definition of topological frustration in this context, and no correlation or causality analysis are provided.
- **Why it matters** This is the mechanistic core of the paper. If the causal relationship is not established with quantitative trajectory analysis, the proposed mechanism remains speculative. The term "topological frustration" is used without a formal definition, making the claim difficult to evaluate or reproduce.
- **Resolution test** Define a quantitative measure of hairpin orientation relative to Im3, show that N-terminal binding precedes misorientation in a statistically significant fraction of trajectories, define topological frustration operationally, and demonstrate that backtracking occurs preferentially when frustration is present.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "topological frustration could be present in the coupled folding-binding process of IDPs and play an important role in regulating the binding transition pathways."
- **Evidence pointer** Abstract text; location not provided
- **Concern** This generalization is based on a single protein pair studied with a coarse-grained model. No evidence is presented that the observed behavior extends to other IDP systems or that coarse-grained simulations capture the relevant physics with sufficient fidelity.
- **Why it matters** The broader significance of the work rests on this generalization. Without comparative analysis across multiple systems or validation against experimental or atomistic simulation data, the claim is unsupported and potentially overreaching.
- **Resolution test** Either temper the claim to the specific E3/Im3 system or provide additional evidence from other IDP-target pairs or from comparison with higher-resolution simulations or experimental data that supports the generality of the proposed mechanism.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The terms "backtracking" and "topological frustration" are used without definition or context, which may confuse readers unfamiliar with the specific simulation or polymer physics literature.
- **Required correction** Add brief definitions or explanatory phrases when these terms are first introduced.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Simulation methodology description
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states "coarse-grained molecular dynamics simulations" but provides no information on the model resolution, force field, or system setup, making it impossible to assess the relevance of the results to the real E3/Im3 system.
- **Required correction** Include a brief description of the coarse-grained model and its validation, or refer to a methods section where these details are provided.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Contextual framing
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract mentions that the N-terminal and central segments of E3 make comparable contacts with Im3, but does not explain how this relates to the observed backtracking or why the central segment dominance in triggering binding is relevant to the frustration mechanism.
- **Required correction** Clarify the connection between the segment-specific contact patterns and the proposed frustration mechanism, or remove the statement if it is not directly relevant.

## Risk / unsupported claims
- The claim that backtracking occurs and depends on salt concentration is unsupported without quantitative trajectory data and statistical analysis.
- The causal mechanism linking N-terminal binding to hairpin misorientation, topological frustration, and backtracking is unsupported without defined metrics and correlation analysis.
- The generalization that topological frustration may be present in IDP coupled folding-binding processes broadly is unsupported from a single system studied with a coarse-grained model.
- The statement that "binding of E3 with Im3 is dominantly triggered by the central segment of E3" is presented as background but is not substantiated within the abstract, and its relevance to the new findings is unclear.
- All quantitative claims regarding free energy analysis and transition path analysis are unverifiable from the abstract alone.