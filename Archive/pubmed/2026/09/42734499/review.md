## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract, evaluated against the evidence described therein
- **Shared manuscript claim summary** The authors report 5 microsecond all-atom molecular dynamics simulations of human FOXM1b NRD-TAD complexes in unphosphorylated and tetra-phosphorylated states. They claim that phosphorylation induces local unfolding of a beta-hairpin beginning at Ser715, leading to global disruption of the NRD interface, and that Ser715 phosphorylation is sufficient to initiate this transition. They further claim that MM-PBSA energy decomposition identifies Ser715 as the dominant locus of energetic perturbation.
- **Visible evidence base** Abstract text only. No figures, tables, methods details, or supplementary materials were provided.
- **Missing materials affecting confidence** Full methods, simulation parameters, force field details, convergence criteria, structural figures, energy decomposition data, replicate simulation details, and validation of the phosphosite modeling approach.

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting mechanistic hypothesis for FOXM1 autoinhibition release via phosphorylation. However, the evidence as described is insufficient to fully evaluate the robustness of the central claims. The simulation length is substantial, but key technical details that would establish confidence in the results are absent. The claim that Ser715 phosphorylation is sufficient to initiate unfolding rests on a single monophosphorylated simulation, which is a weak basis for such a strong conclusion. The MM-PBSA decomposition results are mentioned but not quantified, making the energetic claims unverifiable from the provided material.
- **Who would be interested in the results, and why** Researchers studying FOXM1 biology, transcription factor regulation by phosphorylation, and the broader field of intrinsically disordered proteins and autoinhibitory domains. Computational biophysicists interested in long-timescale simulations of phosphorylation-induced conformational changes would also find the work relevant. The potential therapeutic angle for targeting FOXM1 in cancer could attract translational researchers.
- **Major strengths** The use of 5 microsecond all-atom simulations is ambitious and appropriate for capturing slow conformational transitions. The study addresses a biologically important regulatory mechanism with clear relevance to cell proliferation and cancer. The inclusion of replicate simulations and a monophosphorylated control is commendable for testing reproducibility and sufficiency. The focus on a specific residue, Ser715, provides a testable and mechanistically concrete hypothesis.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The sufficiency claim for Ser715 based on a single simulation is not statistically robust. The absence of any quantitative energetic data in the abstract prevents assessment of the MM-PBSA claims. The lack of methodological details on how phosphorylation was modeled and how the simulations were validated for convergence undermines confidence in the structural conclusions.
- **Assessment against Nature-style criteria** Originality: The work addresses a known regulatory switch but claims to provide the first detailed molecular characterization of the unlocking mechanism. This is a moderate advance rather than a conceptual breakthrough. Scientific importance: FOXM1 is a relevant cancer target, and understanding its activation mechanism has potential translational value. However, the importance is incremental. Interdisciplinary readership: The work would primarily interest computational biophysicists and FOXM1 biologists, with limited appeal beyond these communities. Technical soundness: Cannot be fully assessed from the abstract. The simulation length is a strength, but the sufficiency claim is underpowered. Readability for nonspecialists: The abstract is clearly written and accessible, with appropriate context for the biological question.
- **Recommendation posture** Currently not established from the provided evidence. The central claims are plausible but require additional data and analysis to be convincing. A revised manuscript with full methods, quantitative results, and additional validation of the sufficiency claim could change this assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Sufficiency of evidence
- **Claim pointer** The authors claim that a monophosphorylated Ser715 simulation reproduced the beta-hairpin unfolding event, supporting the sufficiency of Ser715 phosphorylation in initiating this transition.
- **Evidence pointer** Abstract, replicate simulations description. Location not provided.
- **Concern** The sufficiency claim is based on a single monophosphorylated simulation. A single trajectory cannot establish that Ser715 phosphorylation is sufficient to induce unfolding, as the observed event could be stochastic or dependent on initial conditions. No information is provided on whether this simulation was replicated or whether the unfolding event was observed reproducibly.
- **Why it matters** The sufficiency of Ser715 is a central mechanistic claim of the paper. If this claim is not robust, the conclusion that Ser715 is a key structural and energetic switch is substantially weakened. The distinction between a necessary and a sufficient role for Ser715 has direct implications for therapeutic targeting strategies.
- **Resolution test** Provide multiple independent monophosphorylated Ser715 simulations with consistent unfolding outcomes, or provide a statistical analysis of the probability of unfolding across an ensemble of simulations. Alternatively, present a free energy calculation that demonstrates a clear thermodynamic preference for the unfolded state upon Ser715 phosphorylation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support
- **Claim pointer** The authors claim that per-residue MM-PBSA energy decomposition reveals that phosphorylation redistributes interdomain interaction energetics, with Ser715 emerging as the dominant locus of energetic perturbation.
- **Evidence pointer** Abstract, MM-PBSA decomposition description. Location not provided.
- **Concern** No quantitative values are provided for the MM-PBSA results. The abstract states that Ser715 is the dominant locus of energetic perturbation but does not report the magnitude of the effect, the comparison to other phosphosites, or the statistical significance of the difference. Without these numbers, the claim cannot be evaluated.
- **Why it matters** The energetic analysis is presented as a key piece of evidence supporting the mechanistic model. If the quantitative support is weak or the differences between residues are small, the conclusion that Ser715 is uniquely important may not hold. The absence of data prevents the reader from assessing the strength of this claim.
- **Resolution test** Report the per-residue energy decomposition values for all four phosphosites in both phosphorylated and unphosphorylated states, with error bars and statistical comparisons. Show that the energetic perturbation at Ser715 is significantly larger than at the other sites.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors claim that 5 microsecond all-atom molecular dynamics simulations of the NRD-TAD complexes were performed in unphosphorylated and tetra-phosphorylated states.
- **Evidence pointer** Abstract, methods description. Location not provided.
- **Concern** No methodological details are provided regarding the simulation setup. Critical information is missing, including the force field used, the water model, the ionic conditions, the temperature and pressure coupling schemes, the equilibration protocol, and how the phosphorylated residues were parameterized. Additionally, no information is given on how convergence was assessed or whether the simulations reached equilibrium.
- **Why it matters** The validity of the structural conclusions depends entirely on the quality and appropriateness of the simulation methodology. Without these details, the reader cannot assess whether the observed unfolding events are physically meaningful or artifacts of the simulation setup. The parameterization of phosphorylated residues is particularly important, as incorrect parameters could bias the results.
- **Resolution test** Provide a complete methods section with all simulation parameters, force field details, and phosphosite parameterization. Include convergence analysis, such as RMSD stabilization, block averaging, or replica comparisons, to demonstrate that the simulations are well-equilibrated and the observed transitions are not artifacts.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, description of the tetra-phosphorylated state
- **Evidence pointer** Abstract, first paragraph. Location not provided.
- **Issue** The abstract states that four experimentally validated regulatory phosphosites were modeled but does not specify which residues these are beyond Ser715. The reader is left to infer the identity of the other three sites.
- **Required correction** List all four phosphosites explicitly in the abstract or refer to a figure or table that identifies them.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Abstract, description of the unfolding mechanism
- **Evidence pointer** Abstract, second paragraph. Location not provided.
- **Issue** The abstract describes a sequence of events from local unfolding at Ser715 to global disruption of the NRD interface. It is unclear whether this is a temporal sequence observed in the simulations or a logical ordering of events inferred from the final state.
- **Required correction** Clarify whether the propagation from Ser715 to global disruption was directly observed as a time-ordered process in the trajectories or is a mechanistic interpretation of the end states.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Abstract, concluding statement about targeting FOXM1
- **Evidence pointer** Abstract, final sentence. Location not provided.
- **Issue** The abstract concludes that the study provides a framework for targeting FOXM1 activation via its regulatory fold. However, no discussion is provided on how this framework might be translated into a therapeutic strategy, and the connection between the simulation results and drug design is not elaborated.
- **Required correction** Either expand on the potential targeting strategies in the abstract or soften the claim to reflect that the study provides a structural basis that could inform future targeting efforts.

## Risk / unsupported claims
- The sufficiency of Ser715 phosphorylation for initiating beta-hairpin unfolding is not established from a single simulation.
- The claim that Ser715 is the dominant locus of energetic perturbation is unsupported without quantitative MM-PBSA data.
- The claim that phosphorylation propagates from local unfolding to global disruption is not verifiable without trajectory analysis details.
- The generalizability of the findings to other FOXM1 isoforms or to the in vivo context is not addressed and cannot be assessed from the abstract.