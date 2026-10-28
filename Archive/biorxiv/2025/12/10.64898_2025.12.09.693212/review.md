## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and figure legends (as provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and consistency between experiments, simulations, and conclusions
- **Shared manuscript claim summary** The authors propose that monovalent cation concentration modulates topo II binding kinetics, and that faster off-rates accelerate decatenation but slow down relaxation, explained by a trade-off between 3D search and processivity
- **Visible evidence base** Single-molecule koff measurements, EMSA, relaxation and decatenation gel assays, coarse-grained MD simulations
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; no raw data or statistical analysis details; no quantification of gel band intensities for relaxation assays; no error bars or replicates shown for single-molecule measurements; simulation parameters only partially described

## Reviewer
- **Overall assessment** This manuscript addresses an interesting and potentially important question: whether topo II binding kinetics differentially regulate its two major catalytic activities. The combination of single-molecule measurements, bulk biochemical assays, and simulations is commendable. However, the current version has several issues that prevent full confidence in the conclusions. The link between salt concentration and koff is established, but the causal connection to the opposite effects on decatenation versus relaxation is not rigorously demonstrated. The simulations are suggestive but rely on assumptions that need clearer justification. The physiological relevance claims are speculative and not directly tested. The manuscript would benefit from additional controls, quantitative analysis, and a more careful treatment of alternative explanations.
- **Who would be interested in the results, and why** Researchers studying topoisomerase mechanism and regulation, biophysicists interested in protein-DNA interactions and target search, and cell biologists interested in chromosome organization and genome stability. The finding that binding kinetics can oppositely regulate two catalytic activities is conceptually novel and could have implications for understanding how cells tune topo II function in different contexts.
- **Major strengths** 1) The question is well-motivated and addresses a gap in the field. 2) The combination of experimental and computational approaches is powerful. 3) The single-molecule measurements provide direct quantification of koff. 4) The observation of opposite effects on decatenation versus relaxation is striking and potentially important. 5) The simulations provide a mechanistic framework for interpreting the experimental results.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The finding that binding kinetics oppositely regulate two topo II activities is novel and interesting. However, the conceptual framework (enhanced 3D sampling versus processivity) has been previously proposed in computational studies, and the experimental demonstration is incremental. Scientific importance: The work has potential importance for understanding topo II regulation, but the physiological relevance is not directly demonstrated. The claim that this could matter in vivo is speculative. Interdisciplinary readership: The work bridges single-molecule biophysics, enzymology, and simulation, which could appeal to a broad readership. However, the presentation is somewhat technical and may not be accessible to nonspecialists. Technical soundness: The experimental approaches are generally sound, but there are concerns about controls, quantification, and the strength of the causal claims. The simulations are simplified and their connection to the experiments needs more careful justification. Readability for nonspecialists: The abstract is clear, but the results section is dense and assumes significant background knowledge. The figures are not provided, making it difficult to assess clarity.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that "increasing dissociation rates accelerate decatenation while slowing down relaxation catalytic activities" and that this is due to the trade-off between 3D search and processivity
- **Evidence pointer** Figure 3, Figure 4, Results section "Faster binding kinetics accelerates decatenation and slows down relaxation"
- **Concern** The causal link between koff and the observed activity changes is not rigorously established. Salt concentration affects many aspects of enzyme-DNA interactions beyond koff, including DNA structure, enzyme conformation, and ATP hydrolysis. The authors do not rule out that the observed effects are due to salt-dependent changes in catalytic rate (kcat) or processivity independent of binding kinetics. The simulations assume that the only effect of salt is on koff, which may not be valid. Additionally, the claim that the opposite effects are due to a trade-off between 3D search and processivity is presented as a conclusion but is only one possible explanation. Alternative models, such as salt-dependent changes in the conformation of the DNA substrate or the enzyme, are not discussed or tested.
- **Why it matters** The central claim of the paper is that binding kinetics causally regulate the two activities in opposite directions. If this causal link is not established, the main conclusion is not supported. The physiological relevance claim depends on this causal relationship.
- **Resolution test** The authors should perform experiments that directly manipulate koff without changing salt concentration, for example by using mutant topo II with altered DNA binding affinity, or by using a competitive DNA binding agent. Alternatively, they could measure kcat and processivity directly at different salt concentrations to rule out alternative explanations. They should also test whether the simulations reproduce the experimental results when koff is varied independently of salt.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The authors claim that "the values of koff measured range within 0.1-10 s-1 and significantly increase with higher concentrations of monovalent cations"
- **Evidence pointer** Figure 2, Results section "Topo II binding kinetics is modulated by monovalent cations"
- **Concern** The single-molecule measurements are described but no quantitative details are provided. The number of molecules, the distribution of dwell times, the fitting procedure, and the statistical significance of the differences between salt conditions are not reported. The claim that koff "significantly increases" is not supported by statistical analysis. Additionally, the comparison between the measured koff and the estimated koff from the Smoluchowski equation is not rigorous; the estimated koff of 50 s-1 is an order of magnitude higher than the measured values, and the authors do not discuss this discrepancy.
- **Why it matters** The quantitative relationship between salt concentration and koff is the foundation for the rest of the paper. Without proper statistical analysis and reporting, the reader cannot assess the reliability of this relationship. The discrepancy between measured and estimated koff also raises questions about the interpretation of the single-molecule data.
- **Resolution test** The authors should provide a full statistical analysis of the dwell time distributions, including the number of events, the fitting model, and confidence intervals. They should also discuss the discrepancy between measured and estimated koff and explain why the Smoluchowski estimate is not appropriate or why the discrepancy is expected.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation-experiment consistency
- **Claim pointer** The authors claim that "our simulated results – in line with the experimental findings – suggest that whilst efficient decatenation benefits from fast binding kinetics, torsional relaxation is favoured by more processive topo II with longer binding times"
- **Evidence pointer** Figure 4, Results section "MD simulations explain the opposite catalytic regulation by monovalent cations"
- **Concern** The simulations are used to explain the experimental results, but the connection between the two is not quantitative. The simulations vary koff over a range that is not directly mapped to the salt concentrations used in the experiments. The simulation model assumes that topo II acts as a phantom segment that allows strand crossing, but this is a significant simplification. The authors do not validate that the simulation model reproduces the experimental results quantitatively, only qualitatively. Additionally, the simulation results are presented as averages over 50 replicates, but no error bars or statistical analysis are shown.
- **Why it matters** The simulations are a key part of the paper's argument. If the simulations do not quantitatively reproduce the experimental results, or if the model is too simplified to capture the relevant physics, then the mechanistic explanation is not well supported.
- **Resolution test** The authors should map the simulation koff values to the experimental salt concentrations and show that the simulation results quantitatively match the experimental activity measurements. They should also test the robustness of the simulation results to changes in model parameters, such as the length of the phantom segment or the on-rate.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Alternative explanations
- **Claim pointer** The authors claim that "this opposite behaviour is due to a trade-off between search of target through facilitated diffusion and processivity of the enzyme in catenated versus super-coiled DNA"
- **Evidence pointer** Discussion section
- **Concern** The proposed mechanism is plausible but not directly tested. The authors do not provide evidence that the trade-off between 3D search and processivity is the actual mechanism. For example, they do not measure the processivity of topo II at different salt concentrations, nor do they measure the search time. Alternative explanations, such as salt-dependent changes in the topology of the DNA substrate (e.g., changes in supercoil density or catenane structure) or salt-dependent changes in the conformation of the topo II-DNA complex, are not discussed.
- **Why it matters** The proposed mechanism is the main explanatory framework of the paper. If it is not directly tested, the paper is more descriptive than mechanistic. The physiological relevance claims depend on the mechanism being correct.
- **Resolution test** The authors should design experiments to directly test the proposed mechanism. For example, they could measure the processivity of topo II at different salt concentrations using single-molecule assays, or they could use mutants with altered processivity to test the predictions of the model. They should also discuss and, if possible, rule out alternative explanations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "we discover that increasing dissociation rates accelerate decatenation while slowing down relaxation catalytic activities" but does not mention that this is observed at different salt concentrations. This could be misleading, as the reader might think the effect is directly on koff rather than on salt concentration.
- **Required correction** Clarify that the effect is observed by varying salt concentration, which modulates koff.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, DNA relaxation assay
- **Evidence pointer** Methods section "DNA relaxation assay"
- **Issue** The relaxation assay description mentions "25 mM KCl" in the methods but the main text and figure legends refer to varying NaCl concentrations. This inconsistency is confusing.
- **Required correction** Ensure consistency in the salt used and described throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 3
- **Evidence pointer** Figure 3
- **Issue** The gel-based activity assays are described as "independent triplicates" but no error bars or statistical analysis are shown in the description. It is unclear how the quantification was performed and whether the differences are statistically significant.
- **Required correction** Provide quantification of gel bands with error bars and statistical tests.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The term "enhanced 3D sampling" is used without a clear definition. It would be helpful to define this term and explain how it relates to the simulation results.
- **Required correction** Define "enhanced 3D sampling" and explain its relevance to the proposed mechanism.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, MD simulations
- **Evidence pointer** Methods section "Molecular Dynamics Simulations"
- **Issue** The simulation methods are described but key parameters, such as the system size, simulation time, and the specific values of koff and kon used, are not provided in the main text. This makes it difficult to assess the robustness of the simulation results.
- **Required correction** Provide a table of simulation parameters and refer to the SI for full details.

## Risk / unsupported claims
- The claim that "modulation of topo II binding kinetics can oppositely regulate its topological simplification activity, and in turn can have a significant impact in vivo" is not directly supported by the data, as no in vivo experiments are presented.
- The claim that the observed effects are due to a trade-off between 3D search and processivity is not directly tested and is presented as a conclusion rather than a hypothesis.
- The claim that the simulations "recapitulate" the experimental results is only qualitative, and the quantitative mapping between simulation and experiment is not established.
- The physiological relevance discussion, while interesting, is speculative and not grounded in specific experimental evidence.