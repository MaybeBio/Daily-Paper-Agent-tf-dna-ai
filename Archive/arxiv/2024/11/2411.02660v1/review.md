## Review setup
- **Input scope** Full manuscript text, including main text, appendices, and figure captions (figures themselves not provided)
- **Assessment boundary** Theoretical framework, analytical derivations, simulation methodology, and biological application claims as presented in the manuscript
- **Shared manuscript claim summary** The authors present a general theoretical framework for target search on hierarchical networks-within-networks, modeled as a three-layer multiplex network (bulk, spatial, internal). They derive closed-form expressions for steady-state flux through a target node, identify universal scaling relationships, and apply their results to protein-DNA interactions, particularly transcription factor target search.
- **Visible evidence base** Analytical derivations (Eqs. 1-20), simulation results (Figs. 3-9), and comparison between analytical and stochastic simulation results
- **Missing materials affecting confidence** Actual figures and their data points, simulation code, parameter values for all simulations, and detailed derivations of several equations referenced in the main text

## Reviewer

- **Overall assessment** The manuscript presents a potentially valuable theoretical framework for target search in hierarchical network structures. The generalization from single-layer to three-layer multiplex networks is a natural and useful extension, and the closed-form expressions for steady-state flux are elegant. However, the presentation has significant gaps in derivations, the connection to biological systems is largely qualitative, and several claims about universality and optimality require stronger evidence. The work is likely of interest to researchers in stochastic processes, network science, and biophysics, but the current form does not fully establish the case for its broader claims.

- **Who would be interested in the results, and why** Researchers in stochastic processes and first-passage phenomena, network scientists studying multiplex and multilayer systems, and biophysicists working on protein-DNA interactions and gene regulation. The framework provides a tractable approach to a class of problems that has been difficult to analyze, and the closed-form results could serve as building blocks for more complex models.

- **Major strengths** 
  1. The three-layer hierarchical model is a natural and important generalization of existing search models, addressing a real gap in the literature.
  2. The derivation of closed-form expressions for steady-state flux in terms of network-specific parameters (Γ and K) is a significant technical achievement.
  3. The identification of an optimal off-rate as a geometric mean of on-rates is a clean and memorable result.
  4. The application to transcription factor search provides a concrete biological context that motivates the abstract framework.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims to derive "general closed-form solutions for the steady-state flux through a target node" (Abstract) and presents Eq. (11) as "one of our manuscript's key results."
- **Evidence pointer** Section III.1, Eqs. (6)-(11); Appendix A
- **Concern** The derivation from Eqs. (6)-(11) is presented with insufficient detail. The definitions of Γ and K in Eq. (8) involve inverse matrices of transition operators, but the steps connecting the steady-state solution of Eq. (1) to these expressions are not shown. The assumption that the target node is a small fraction of the spatial network (Eq. 5) is stated but its validity regime is not discussed. Furthermore, the claim that these are "general" solutions requires clarification of the assumptions on the transition matrices (e.g., reversibility, detailed balance, spectral properties).
- **Why it matters** The central contribution of the paper is the closed-form expression for flux. If the derivation is not fully transparent and the validity conditions are not clearly stated, readers cannot assess the range of applicability of the key result.
- **Resolution test** Provide a complete derivation of Eqs. (6)-(11) in the main text or Appendix, explicitly stating all assumptions on the transition matrices. Discuss the regime of validity of the approximation in Eq. (5) and provide numerical evidence for when it breaks down.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that the results "have broad implications for fields ranging from epidemiology to cellular biology" (Abstract) and that the framework "adds specific value for the general understanding of site-specific search by DNA-binding proteins" (Section III.5).
- **Evidence pointer** Section III.5; Section IV
- **Concern** The biological application section is largely qualitative. The connection between the abstract network parameters (Γ, K) and measurable biological quantities is not made explicit. For example, the claim that the optimal sliding length scales as ℓ* ~ (2D_DNA)^{1/2}(k_on k_on')^{-1/4} is presented without comparison to experimental data or existing theoretical predictions for transcription factor search. The discussion of "rewiring" and "mutations" is speculative and not tied to specific biological observations or predictions that could be tested.
- **Why it matters** The stated significance of the work depends on its applicability to real biological systems. Without concrete, testable predictions or quantitative connections to experimental observables, the biological relevance remains asserted rather than demonstrated.
- **Resolution test** Provide quantitative predictions for transcription factor search times or sliding lengths that can be compared with existing experimental data. Alternatively, clearly state what new experimental measurements would be needed to test the theory's predictions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "the optimal off-rate is a geometric average between the on-rate from the bulk to the spatial node (k_on) and the on-rate from the spatial node to the internal network (k_on')" (Section III.2, Eq. 14).
- **Evidence pointer** Section III.2, Eq. (14); Fig. 3
- **Concern** The derivation of the optimal off-rate k_off* is not shown. The statement that this is a "geometric average" is clear, but the conditions under which this result holds are not specified. Does it require the free bulk approximation? Does it depend on the internal network structure? The authors state that "N and K are network-specific parameters" but do not discuss how the optimal off-rate depends on these parameters beyond the geometric mean form.
- **Why it matters** The optimal off-rate is a key practical result that could guide experimental design or interpretation. If its validity conditions are not clear, it may be misapplied.
- **Resolution test** Provide the full derivation of Eq. (14) and state explicitly the conditions under which the geometric mean result holds. Discuss how the optimal off-rate changes when these conditions are violated.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "the random network shows a larger flux for large Ω, as the network has shorter mean path lengths D in the internal network" and that "before some threshold value, this is no longer true, and the linear chain predicts a larger flux than the random network for smaller Ω" (Section III.2, Fig. 5).
- **Evidence pointer** Section III.2, Fig. 5
- **Concern** The crossover behavior between linear chain and random network as a function of Ω is interesting but the explanation is incomplete. The authors attribute the difference to mean path length, but the non-monotonic behavior suggests a more subtle competition between exploration and absorption. The threshold value of Ω where the crossover occurs is not characterized, and its dependence on network parameters is not discussed.
- **Why it matters** This crossover is a non-trivial prediction of the model that could have practical implications for understanding when network structure matters for search efficiency. Without a clear characterization of the crossover, the practical utility of this finding is limited.
- **Resolution test** Provide a quantitative characterization of the crossover threshold as a function of network parameters. Discuss the physical mechanism underlying the crossover in more detail.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The manuscript claims that the framework "can be applied to many disciplines" and that the findings "can be used to better understand a range of physical and biological systems" (Section IV).
- **Evidence pointer** Section IV
- **Concern** The conclusion section is brief and does not provide concrete guidance for how researchers in other fields would apply this framework. The extension to "general multiplex networks" is mentioned but not developed. The discussion of RNA polymerase as another application is speculative and not analyzed within the model.
- **Why it matters** The stated interdisciplinary significance is a key selling point of the work. Without concrete examples or guidance, the broader impact may not be realized.
- **Resolution test** Provide at least one additional concrete application example beyond transcription factors, with specific model parameters and predictions. Alternatively, provide a clear "how to apply this framework" guide for researchers in other fields.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, Section I
- **Evidence pointer** Section I
- **Issue** The introduction provides examples of networks-within-networks but does not clearly define the key terms (bulk, spatial, internal layers) before the model is introduced. The connection between the motivating examples and the abstract model could be made more explicit.
- **Required correction** Add a brief paragraph in the introduction that defines the three layers in general terms and maps the motivating examples onto this structure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Simulation methodology, Section II.2
- **Evidence pointer** Section II.2
- **Issue** The simulation section is very brief. The Gillespie algorithm is mentioned, but details about the network generation, the number of simulation runs, the error bars, and the parameter values used are not provided. This makes it difficult to assess the quality of the agreement between theory and simulation.
- **Required correction** Provide a more detailed description of the simulation setup, including network generation parameters, number of realizations, and how error bars are computed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section III.4, Eq. (20)
- **Evidence pointer** Section III.4, Eq. (20); Appendix B
- **Concern** The expression for K in the linear chain case (Eq. 20) is presented with limited context. The limiting behaviors for C << 1 and C >> 1 are discussed, but the intermediate regime is not characterized.
- **Required correction** Provide a brief discussion of the behavior of K in the intermediate regime C ~ 1, where the most interesting dynamics are expected.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section III.5
- **Evidence pointer** Section III.5
- **Issue** The biological application section assumes familiarity with transcription factor search literature. Key concepts such as "sliding length" and "speed-stability paradox" are introduced but not fully explained for readers outside the field.
- **Required correction** Add brief definitions or explanations of these terms when first introduced.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Appendix C
- **Evidence pointer** Appendix C, Fig. 9
- **Concern** The analysis of optimal quotients in the linear chain is interesting, but the claim that the maximum flux case yields a "40% speed increase" compared to the fixed quotient case is presented without error bars or statistical significance assessment.
- **Required correction** Provide error estimates for the 40% speed increase claim and discuss whether this difference is statistically significant.

- **Technical failings that need to be addressed before the case is established** 
  - R1-M1: Incomplete derivation of the central result (Eq. 11)
  - R1-M2: Lack of quantitative biological predictions or comparison with experimental data
  - R1-M3: Unclear validity conditions for the optimal off-rate result

- **Assessment against Nature-style criteria** 
  - **Originality**: The three-layer hierarchical model is a genuine extension of existing search models. The closed-form results for steady-state flux in terms of network-specific parameters are novel. However, the individual components (multiplex networks, first-passage theory, transcription factor search) are well-established, and the novelty lies primarily in their combination.
  - **Scientific importance**: The framework addresses a real gap in the literature and could provide a foundation for future work. However, the demonstrated applications are limited, and the biological significance is asserted rather than demonstrated with quantitative predictions.
  - **Interdisciplinary readership**: The abstract model is general enough to appeal to multiple fields, but the presentation is heavily weighted toward the mathematical formalism. The biological application section is too brief and qualitative to engage biologists, while the biological motivation may not be sufficient to engage pure network scientists.
  - **Technical soundness**: The mathematical framework appears sound, but the derivations are incomplete in key places, and the simulation methodology is underdescribed. The agreement between theory and simulation is claimed but not fully demonstrated with the provided information.
  - **Readability for nonspecialists**: The main text is generally clear, but the derivations in Section III.1 are dense and would benefit from additional explanatory text. The biological section assumes too much background knowledge.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is valuable and the framework is potentially important, but the manuscript in its current form does not fully establish the case. The derivations need to be completed, the biological applications need to be made quantitative, and the simulation methodology needs to be fully described. If these issues are addressed, the work could make a significant contribution to the field.