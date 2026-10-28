## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, conclusions, and materials and methods
- **Assessment boundary** Scientific claims, methodological soundness, and interpretation of results as presented in the provided text
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations to characterize the search and binding mechanism of the bacterial protein HU to DNA. They propose a multistep process involving weak electrostatic initial contacts, protein reorientation via rolling, and DNA flexibility that facilitates the transition to specific binding at damaged DNA sites. They link their simulation observations to existing experimental structures and propose a structural model for the three experimentally observed diffusion modes of HU.
- **Visible evidence base** Simulation trajectories (replicas 0–10), hydrogen bond interaction analyses, DNA bending angle measurements, comparisons with experimental structures (PDB 4YEW, PDB 1P78), and references to supplementary movies and figures
- **Missing materials affecting confidence** Supplementary figures and movies referenced but not provided; specific simulation parameters and convergence criteria not fully detailed; force field validation data not shown; statistical analysis details for bending angle comparisons not fully described

## Reviewer
- **Overall assessment** This manuscript presents a valuable contribution to the understanding of protein-DNA search mechanisms at atomic resolution. The authors demonstrate that all-atom simulations can capture spontaneous binding events and provide mechanistic insights that complement experimental observations. The proposed multistep binding model is plausible and well-supported by the simulation data presented. However, several technical aspects require clarification, particularly regarding simulation convergence, force field limitations, and the statistical robustness of the bending angle measurements. The connection between the simulated observations and the proposed structural model for the three diffusion rates is intriguing but would benefit from more direct evidence or a clearer articulation of the inference chain.

- **Who would be interested in the results, and why** Researchers in the fields of molecular biophysics, computational chemistry, and DNA-protein interactions would find this work of interest. The demonstration that all-atom simulations can capture binding events opens new possibilities for studying similar systems. The proposed multistep binding mechanism and the "concerted" model for DNA flexibility in recognition could inform future experimental and computational studies of architectural DNA-binding proteins. The work may also appeal to those studying facilitated diffusion and target search mechanisms in general.

- **Major strengths** The use of state-of-the-art all-atom simulations to capture spontaneous binding events is a significant technical achievement. The authors successfully link their simulation results to existing experimental structures, providing a coherent framework for interpreting their observations. The identification of specific residues involved in different binding stages offers testable predictions. The proposed "concerted" mechanism provides a nuanced perspective that bridges induced-fit and conformational selection models.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that their simulations captured spontaneous binding events and that the observed multistep process is representative of the actual binding mechanism.
  - **Evidence pointer** Results and Discussion, "HU Hops and Jumps DNA via Its β-Ribbon Arms That Serve as Antennae" section; "HU's Residues Involved in the Process of DNA Binding" section
  - **Concern** The manuscript reports a limited number of binding events across replicas (e.g., one hopping event in replica 1, one rolling event in replica 2, and three replicas with no contact). The statistical robustness of conclusions drawn from such a small number of events is questionable. Additionally, the simulation timescales (100–140 ns for most replicas, 2 μs for one extended simulation) may be insufficient to sample the full conformational space relevant to the binding process. The authors do not provide convergence analyses or error estimates for their observations.
  - **Why it matters** The central claims of the manuscript rest on the representativeness and reproducibility of the observed binding events. Without evidence that these events are not rare stochastic occurrences or artifacts of the specific initial conditions, the generalizability of the proposed mechanism is not established.
  - **Resolution test** Provide additional replicas with varied initial conditions, demonstrate convergence of key observables (e.g., contact patterns, binding poses), and include statistical analyses (e.g., bootstrapping or block averaging) to quantify the uncertainty in the reported observations.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that DNA flexibility facilitates the transition from nonspecific to specific binding, and that this represents a "concerted" mechanism.
  - **Evidence pointer** Results and Discussion, "DNA Flexibility Facilitates Transition to Specific Binding" section
  - **Concern** The bending angle measurements are reported as mean ± standard deviation, but the statistical comparison between conditions (damaged vs. undamaged DNA, with vs. without HU) is not described. The claim that damaged DNA is more flexible than B-DNA is based on a difference of 6° (34 ± 17° vs. 28 ± 13°), which may not be statistically significant given the large standard deviations. Furthermore, the authors acknowledge that the simulated bending (55 ± 23°) is significantly lower than the crystal structure value (~100°), indicating that the simulation may not have captured the full conformational change. The interpretation of a "concerted" mechanism is inferred from a single trajectory and lacks direct evidence for the proposed coupling between DNA flexibility and protein binding.
  - **Why it matters** The proposed "concerted" mechanism is a key conceptual contribution of the manuscript. If the underlying data do not robustly support the claim that DNA flexibility is required for the transition, the mechanistic model is weakened.
  - **Resolution test** Provide statistical tests comparing bending angle distributions across conditions, report confidence intervals, and demonstrate that the observed differences are significant. Consider additional simulations or enhanced sampling methods to more fully explore the conformational landscape and support the "concerted" mechanism.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors propose a structural model linking their simulation observations to the three experimentally observed diffusion rates of HU along DNA.
  - **Evidence pointer** Conclusions section; Results and Discussion, "HU Hops and Jumps DNA via Its β-Ribbon Arms That Serve as Antennas" section
  - **Concern** The proposed model connecting the three diffusion rates (slowest: recognition state sliding; intermediate: searching state sliding; fastest: hopping via β-ribbon arms) is presented as a conclusion, but the evidence linking specific simulation observations to each diffusion mode is indirect. The authors did not directly simulate sliding along DNA over extended distances or timescales, nor did they measure diffusion coefficients. The assignment of the intermediate diffusion rate to the lateral binding mode is plausible but not directly demonstrated.
  - **Why it matters** The structural model for the three diffusion rates is a significant claim that extends beyond the direct simulation observations. If this model is to be accepted, the authors need to more clearly articulate the evidence supporting each assignment or acknowledge the speculative nature of these connections.
  - **Resolution test** Provide a more detailed and explicit mapping between simulation observations and each diffusion mode, or clearly label the proposed model as a hypothesis requiring further validation. Consider additional simulations designed to directly measure diffusion behavior in each binding mode.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction
  - **Evidence pointer** Introduction, first paragraph
  - **Issue** The introduction contains several incomplete sentences and citation placeholders (e.g., "The limitations in the resolution of experimental techniques in terms of time and space have made it difficult to characterize the mechanisms behind DNA–protein association. ,  As a result, simulations have been employed to complement experimental studies, particularly using coarse-grained models due to their capacity to sample experimentally relevant time scales in contrast to all-atom simulations. −"). These appear to be formatting artifacts but hinder readability.
  - **Required correction** Complete the sentences and properly format citations throughout the introduction.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Materials and Methods
  - **Evidence pointer** Materials and Methods, simulation setup paragraph
  - **Issue** The description of the simulation setup is brief and lacks some details that would be important for reproducibility, such as the specific equilibration protocol, the number of steps for minimization, and the thermostat/barostat algorithms used.
  - **Required correction** Provide a more detailed description of the simulation protocol, including equilibration steps, temperature/pressure coupling methods, and any restraints applied during the simulations.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion of limitations
  - **Evidence pointer** Results and Discussion, "DNA Flexibility Facilitates Transition to Specific Binding" section
  - **Issue** The authors acknowledge that the simulated bending angle for damaged DNA bound to HU (55 ± 23°) is significantly lower than the crystal structure value (~100°), but they do not discuss the implications of this discrepancy for their conclusions about the "concerted" mechanism.
  - **Required correction** Add a brief discussion of how the incomplete bending in simulations might affect the interpretation of the transition mechanism and whether this limitation could influence the proposed model.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Conclusions
  - **Evidence pointer** Conclusions, final paragraph
  - **Issue** The statement "We anticipate that the same principles discovered here will apply to other DNA-binding proteins, especially architectural ones" is presented without sufficient caveats about the limitations of the simulation approach and the need for experimental validation.
  - **Required correction** Soften the generalization and add a sentence acknowledging that experimental validation is needed to confirm the broader applicability of the proposed mechanism.

- **Technical failings that need to be addressed before the case is established** R1-M1 (limited sampling and lack of convergence analysis), R1-M2 (insufficient statistical support for the DNA flexibility claim)

## Risk / unsupported claims
- The claim that the three diffusion rates observed experimentally correspond to specific binding modes (recognition state sliding, searching state sliding, and hopping via β-ribbon arms) is not directly supported by the simulation data presented. This is an inference that requires additional evidence or should be clearly labeled as a hypothesis.
- The statement that "large positive patches are not required for establishing encounter complexes and that they may even be detrimental due to slowing down the searching dynamics" is presented as a general conclusion but is based on observations from a single protein system and a limited number of binding events.
- The generalization that "other DNA-binding proteins with multiple surface-charged regions and DNA-bend induction capability might follow a similar strategy" is speculative and not supported by direct evidence in this manuscript.
- The claim that the "concerted" mechanism represents a middle ground between induced-fit and conformational selection is conceptually interesting but is inferred from a limited set of observations and requires more direct evidence to be fully established.