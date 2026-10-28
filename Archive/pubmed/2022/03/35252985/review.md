## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, and materials and methods
- **Assessment boundary** Scientific content, methodological soundness, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors developed structure-based models (SBMs) to study the conformational dynamics of DPO4, a Y-family DNA polymerase, during folding, DNA binding, and nucleotide binding. They report a two-step folding process, a multistep DNA binding mechanism involving an encounter complex and intermediate states, and a two-state nucleotide binding process with a high free energy barrier. They also performed frustration analyses to connect local energetic frustration to functional conformational dynamics.
- **Visible evidence base** Abstract, Results sections with figures referenced (Figures 1-6), Discussion, Materials and Methods, references to Supporting Information
- **Missing materials affecting confidence** Supporting Information (figures S5-S28, detailed methods), simulation parameter files, analysis scripts, force field parameters, and validation data against experimental measurements

## Reviewer
- **Overall assessment** This manuscript presents a computational study of conformational dynamics in a Y-family DNA polymerase using structure-based models. The work addresses an important question about how conformational dynamics facilitate translesion synthesis. The authors have developed a double-well two-bead SBM that captures both folding and conformational transitions, which represents a methodological advance over their previous single-basin models. The multistep DNA binding mechanism and the identification of an encounter complex are potentially interesting findings. However, several major concerns limit the current assessment. The validation against experimental data is indirect, the relationship between simulation temperatures and experimental temperatures relies on an unverified linear assumption, and the biological significance of the identified intermediate states requires stronger support. The frustration analysis provides complementary evidence but is presented in a somewhat disconnected manner from the main simulation results. The manuscript would benefit from clearer articulation of how the computational predictions can be tested experimentally.

- **Who would be interested in the results, and why** Researchers studying DNA polymerase mechanisms, particularly Y-family polymerases involved in translesion synthesis, would find this work relevant. The methodological developments in structure-based models for studying conformational transitions in multidomain proteins would interest computational biophysicists. The connection between local frustration and functional dynamics could appeal to those studying protein energy landscapes. The findings on multistep DNA binding mechanisms may also be relevant to researchers studying protein-DNA recognition more broadly.

- **Major strengths** The development of a double-well two-bead SBM that captures both folding and conformational transitions is a methodological improvement. The identification of a metastable intermediate state (DPO4I) during the open-to-closed transition provides a concrete mechanistic proposal. The multistep DNA binding model with distinct stages controlled by different interaction types is a nuanced picture. The inclusion of electrostatic interactions through the Debye-Hückel model and the systematic variation of salt concentration and interaction strengths demonstrates careful parameter exploration. The frustration analysis provides an independent perspective on functional dynamics.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the simulation temperatures can be approximately connected to experimental temperatures through a linear temperature dependence on energy, and they use this to compare their two-step folding with experimental melting temperatures.
- **Evidence pointer** Materials and Methods, "we assumed a linear temperature dependence on the energy and provided an approximate connection to bridge the simulation temperatures and the experimental ones with the knowledge of the folding temperatures"
- **Concern** The linear temperature mapping between reduced simulation units and experimental temperatures is a critical assumption that underpins the comparison with experimental melting data. The manuscript does not provide sufficient justification for this linear relationship, nor does it discuss potential nonlinearities or systematic errors in this mapping. The comparison with experimental melting temperatures (89.3 and 102.6 °C) is presented as validation, but the mapping itself is not independently verified.
- **Why it matters** If the temperature mapping is incorrect, the claimed agreement with experimental melting temperatures could be coincidental, and the interpretation of temperature-dependent behavior in the simulations would be unreliable.
- **Resolution test** Provide a more rigorous justification for the linear temperature mapping, possibly through calibration against multiple experimental observables or through comparison with all-atom simulations at specific temperatures. Alternatively, present the results without claiming quantitative correspondence to experimental temperatures.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for claims
- **Claim pointer** The authors claim that "DPO4 undergoes first unraveling (unfolding) and then folding for accomplishing the functional open-to-closed conformational transition" and that this is an "inevitable on-pathway intermediate state."
- **Evidence pointer** Results, "Global Folding and Local Conformational Dynamics of DPO4", Figures 1C-1E
- **Concern** The claim that the intermediate state is "inevitable" and "on-pathway" is strong. The evidence presented shows that the DPO4I state exists as a free energy minimum in the simulations, but this does not establish that it is obligatory for the transition. The authors do not demonstrate that the transition can only proceed through this state, nor do they rule out alternative pathways. The word "inevitable" implies a level of certainty that the simulation evidence may not support.
- **Why it matters** The biological significance of the intermediate state depends on whether it is truly obligatory for the conformational transition. If alternative pathways exist, the functional importance of DPO4I would be diminished.
- **Resolution test** Perform transition path sampling or committor analysis to determine whether all reactive trajectories pass through the DPO4I state. Alternatively, soften the claim to state that DPO4I is a populated intermediate state that may serve as a gateway for the transition.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for claims
- **Claim pointer** The authors claim that "nucleotide binding induces modulation of a few contacts surrounding the active site of the DPO4-DNA complex associated with a high free energy barrier" and that this is consistent with the rate-limiting step of nucleotide incorporation.
- **Evidence pointer** Results, "Two-State Nucleotide Binding to the DPO4-DNA Complex", Figures 4-5
- **Concern** The claim that the high free energy barrier for nucleotide binding corresponds to the experimentally observed rate-limiting step requires more careful justification. The simulations show a barrier of approximately 10 kTr, but the relationship between this barrier and the experimentally measured rate of nucleotide incorporation is not established. The authors do not provide quantitative comparison with experimental rate constants or activation free energies.
- **Why it matters** The biological relevance of the nucleotide binding mechanism depends on whether the simulated barrier corresponds to the experimentally observed rate-limiting step. Without quantitative comparison, the claim remains speculative.
- **Resolution test** Estimate the rate constant from the simulated free energy barrier and compare with experimentally measured nucleotide incorporation rates. Alternatively, perform simulations with different nucleotide analogs or mutated DPO4 variants to test whether changes in the barrier correlate with experimental rate changes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the two-bead homogeneous SBM can naturally lead to a decreased proportion of interdomain interactions in the total energy for stabilizing the native structures with respect to the one-bead homogeneous SBM."
- **Evidence pointer** Results, "Global Folding and Local Conformational Dynamics of DPO4", Materials and Methods
- **Concern** The manuscript does not provide a systematic comparison between the one-bead and two-bead models in terms of their ability to reproduce experimental observables. The claim that the two-bead model is superior is based on the observation of two melting temperatures, but the manuscript does not show whether the one-bead model fails to reproduce other experimental data or whether the two-bead model reproduces additional experimental observables beyond the melting temperatures.
- **Why it matters** The choice of model resolution is critical for the validity of the results. Without a thorough comparison, it is unclear whether the two-bead model is genuinely better or simply different.
- **Resolution test** Provide a systematic comparison of one-bead and two-bead models against multiple experimental observables, such as folding rates, phi-values, or binding affinities. Show that the two-bead model reproduces a broader range of experimental data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Support for claims
- **Claim pointer** The authors claim that "DNA binding dynamically modulates the conformational equilibrium in DPO4 during the stepwise binding through different types of interactions, leading to different conformational distributions of DPO4 at different DNA binding stages."
- **Evidence pointer** Results, "Conformation-, Interaction- and Salt-Dependent Multistep DPO4-DNA Binding", Figures 2-3
- **Concern** The claim of "stepwise binding" and "different conformational distributions at different stages" is based on the identification of multiple free energy minima along the binding coordinate. However, the manuscript does not clearly demonstrate that these states are kinetically distinct and that the transitions between them are sequential. The free energy landscape could also be interpreted as a rugged landscape with multiple competing pathways rather than a strictly sequential process.
- **Why it matters** The mechanistic interpretation of the binding process depends on whether the states are visited sequentially or in parallel. This affects the biological interpretation of how DPO4 finds its binding site on DNA.
- **Resolution test** Perform kinetic analysis, such as transition path sampling or Markov state model construction, to determine whether the binding process is sequential or parallel. Alternatively, present the free energy landscape without overinterpreting the order of events.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "we developed structure-based models to study the precatalytic DNA polymerization process"
- **Issue** The abstract does not clearly state the methodological novelty of the double-well two-bead SBM compared to previous models. The phrase "structure-based models" is generic and does not convey the specific advance.
- **Required correction** Briefly mention the double-well two-bead SBM and its ability to capture both folding and conformational transitions in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods
- **Evidence pointer** Materials and Methods, "The details of the models and simulations can be found in the Supporting Information"
- **Issue** The manuscript relies heavily on the Supporting Information for methodological details, but the main text does not provide sufficient information for a reader to understand the key model parameters without accessing the supplement.
- **Required correction** Include key model parameters (e.g., the strength of native contacts, Debye-Hückel parameters, simulation length, number of replicas) in the main text or provide a summary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, "we suggest that this process can be accelerated by PCNA in vivo"
- **Issue** The speculation about PCNA acceleration is not directly supported by the simulations presented in this manuscript. While plausible, this statement goes beyond the evidence.
- **Required correction** Clearly label this as speculation and suggest how it could be tested in future work.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "Localized Frustration in DPO4"
- **Evidence pointer** Results, "Localized Frustration in DPO4 at the apo, DNA Binary, and DNA-Nucleotide Ternary States", Figure 6
- **Issue** The comparison with the high-fidelity polymerase BF is interesting but brief. The authors do not discuss whether the differences in frustration patterns between DPO4 and BF are statistically significant or whether they are robust to the choice of frustration calculation method.
- **Required correction** Provide a more detailed comparison, including error estimates or statistical analysis, and discuss potential limitations of the frustration analysis.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Figures 1-6
- **Issue** The figures are referenced but not described in detail in the main text. The reader is left to interpret complex free energy landscapes and frustration maps without sufficient guidance.
- **Required correction** Add more detailed figure captions and refer to specific features in the figures within the main text.

## Risk / unsupported claims
- The claim that the DPO4I state is an "inevitable on-pathway intermediate state" is not fully supported by the evidence presented. The simulations show the existence of this state but do not demonstrate that all transition paths pass through it.
- The quantitative correspondence between simulation temperatures and experimental temperatures relies on an unverified linear assumption that is not independently validated.
- The claim that the high free energy barrier for nucleotide binding corresponds to the experimentally observed rate-limiting step of nucleotide incorporation is not quantitatively supported by comparison with experimental rate data.
- The statement that "the two-bead homogeneous SBM can naturally lead to a decreased proportion of interdomain interactions" is presented as a finding but is not systematically compared with the one-bead model in terms of overall performance.
- The speculation about PCNA accelerating DPO4-DNA binding in vivo is not directly supported by the simulations presented.
- The biological significance of the frustration differences between DPO4 and BF is discussed without statistical validation or consideration of alternative explanations.