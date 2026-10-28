## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors investigate the conformational behavior of the NUP98-HOXA9 (NHA9) oncoprotein across different assembly states, from dilute monomers to nanoclusters and macroscopic condensates. They report that the FG domain of NHA9 progressively expands as it transitions from monomeric to oligomeric to condensed states, with the oligomeric state exhibiting micelle-like organization with the DNA-binding domain exposed at the periphery. The study combines single-molecule FRET, FLIM-FRET, FCS, coarse-grained simulations, and phase separation assays.
- **Visible evidence base** Full text including all main figures (1-6), supplementary figure references, methods section, and figure legends
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; source data files not accessible; detailed simulation parameters only partially described

## Reviewer

- **Overall assessment** This manuscript presents a comprehensive multi-technique investigation of the conformational behavior of the NHA9 oncoprotein across different assembly states. The combination of experimental single-molecule approaches with coarse-grained simulations is commendable and provides a multi-scale view of the system. The central finding, that the FG domain progressively expands from compact monomers to more extended conformations in nanoclusters and condensates, is potentially interesting. However, several technical concerns regarding data analysis, particularly in the FLIM-FRET measurements and the interpretation of the micelle-like structures, need to be addressed before the conclusions can be fully supported.

- **Who would be interested in the results, and why** Researchers studying transcription factor phase separation, particularly those interested in oncogenic fusion proteins and their biophysical properties. The work also has relevance for the broader community studying intrinsically disordered proteins and their conformational behavior in different assembly states. The methodological combination of smFRET, FLIM-FRET, and simulations may interest biophysicists developing approaches to study protein assemblies.

- **Major strengths** The multi-technique approach provides complementary views of the system. The use of single-molecule methods to probe conformations in heterogeneous assemblies is technically challenging and well-executed. The combination of experimental measurements with coarse-grained simulations strengthens the interpretation. The study addresses an important question about how protein conformation changes during assembly, which has implications for understanding transcriptional regulation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the FG domain of NHA9 adopts a more expanded conformation in nanoclusters compared to monomers, based on the appearance of a lower-efficiency FRET peak at increasing protein concentrations.
- **Evidence pointer** Figure 2b, 2d, 2e; Results section "NHA9 forms nanoclusters in subsaturated solutions with reduced compactness"
- **Concern** The interpretation of the lower FRET efficiency peak as evidence of conformational expansion within nanoclusters is complicated by the observation of acceptor quenching during nanocluster formation (Supplementary Fig. 4). The authors acknowledge this and switch to lifetime-based analysis, but the validity of the Gaussian chain model for extracting distances in the context of potential dye interactions within dense assemblies is not fully established. Additionally, the possibility that the lower-efficiency peak arises from intermolecular FRET between different NHA9 molecules within the nanocluster, rather than intramolecular conformational changes, needs to be more rigorously excluded. The control experiments for intermolecular FRET are described for cellular condensates but not clearly for the in vitro nanocluster measurements.
- **Why it matters** The central claim of progressive conformational expansion depends critically on the correct assignment of the FRET signals. If intermolecular FRET contributes to the observed lower-efficiency peak, the interpretation of conformational expansion would be incorrect.
- **Resolution test** Provide explicit control experiments demonstrating the absence of intermolecular FRET in the in vitro nanocluster measurements, such as mixing experiments with donor-only and acceptor-only labeled proteins at the same concentrations. Additionally, validate the Gaussian chain model for distance extraction in the nanocluster context by comparing with alternative models or demonstrating insensitivity of the conclusions to the model choice.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the oligomeric state exhibits micelle-like organization with the DNA-binding domain exposed at the periphery, based on coarse-grained simulations.
- **Evidence pointer** Figure 6c, 6d; Results section "Molecular simulations confirm NHA9's expansion within the nanocluster and reveal non-stoichiometric micelle-like structures"
- **Concern** The simulations use the HPS-Urry force field with elastic network constraints for the folded domains. The authors acknowledge potential inaccuracies from this approach but do not provide sufficient validation. The claim of micelle-like structures is based on density profiles from simulations of clusters containing up to 50 chains. It is unclear whether these simulations have reached equilibrium, and the timescales may be insufficient to observe true equilibrium structures. The relationship between the simulated clusters and the experimentally observed nanoclusters is not quantitatively established.
- **Why it matters** The micelle-like structural model is a key conceptual contribution of the paper. If the simulations are not reliable or the structures are kinetic artifacts, this conclusion would be weakened.
- **Resolution test** Provide evidence of simulation convergence, such as time evolution of cluster properties. Validate the force field approach by comparing simulated single-chain dimensions with experimental smFRET data more quantitatively. Discuss the limitations of the elastic network approach for the folded domains and how this might affect the predicted micelle-like structures.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that DNA binding modulates NHA9 nanocluster formation, with specific DNA reducing nanocluster formation more effectively than shuffled DNA.
- **Evidence pointer** Figure 3a, 3b; Results section "DNA binding on NHA9 nanocluster formation"
- **Concern** The effect of DNA on nanocluster formation is modest, and the interpretation is complicated by the observation that even shuffled DNA has some effect. The authors suggest that specific interactions partially mediate the effect, but the quantitative difference between specific and nonspecific DNA appears small. The proposed mechanism, that DNA binding solubilizes NHA9 molecules, is plausible but not directly tested. The authors also note that this result seems counterintuitive given previous reports that DNA enhances condensation of transcription factors.
- **Why it matters** The modulatory role of DNA on NHA9 assembly is presented as a significant finding with implications for understanding transcriptional regulation. If the effect is weak or largely nonspecific, the biological significance would be diminished.
- **Resolution test** Provide quantitative analysis of the difference between specific and nonspecific DNA effects, including statistical significance. Consider testing a range of DNA concentrations to establish a dose-response relationship. Discuss more thoroughly why the results differ from previous reports and what experimental conditions might explain the discrepancy.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the FG domain of NHA9 remains disordered and dynamic within nanoclusters and condensates, based on the observation of dynamic behavior in 2D histograms of lifetime versus intensity-based transfer efficiency.
- **Evidence pointer** Supplementary Fig. 5c, 12c; Results sections on nanocluster and condensate measurements
- **Concern** The evidence for dynamics within the condensed phase is indirect. The 2D histogram analysis shows deviations from the static FRET line, but this could also arise from static heterogeneity in the sample rather than fast dynamics. The timescales of the proposed dynamics are not specified, and no direct measurement of conformational fluctuations (e.g., using fluorescence correlation spectroscopy on the FRET signal) is provided.
- **Why it matters** The claim of dynamics within assemblies is important for understanding the functional properties of these condensates. If the evidence is not conclusive, the interpretation should be tempered.
- **Resolution test** Perform additional experiments to directly probe dynamics, such as time-resolved fluorescence anisotropy or fluorescence correlation spectroscopy on the FRET signal within condensates. Alternatively, clearly state the limitations of the current approach in distinguishing static heterogeneity from dynamic fluctuations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract uses the term "macrophases" which is unusual and not clearly defined. The term "macroscopic phase" or "condensate" would be more standard.
- **Required correction** Replace "macrophases" with "macroscopic phases" or "condensates" for clarity and consistency with standard terminology.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, simulation section
- **Evidence pointer** Methods section "Molecular Dynamics simulations"
- **Issue** The simulation methods lack some details necessary for reproduction, such as the specific version of the HPS-Urry parameters used, the exact protocol for generating initial configurations, and the criteria for determining equilibration.
- **Required correction** Provide additional details on the simulation setup, including parameter values, initialization protocol, and equilibration criteria. Consider including a table with all simulation parameters.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2b, 2d
- **Issue** The FRET histograms in Figure 2b and 2d show peaks that are labeled as "monomer" and "nanocluster" populations, but the assignment of these peaks to specific species is not explicitly justified. The overlap between the peaks could complicate the interpretation.
- **Required correction** Provide a clearer explanation of how the peaks were assigned to monomer versus nanocluster populations, including any fitting procedures used. Consider showing the individual fits and the criteria for peak assignment.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the biological implications of the conformational expansion is somewhat speculative. The connection between the observed biophysical behavior and transcriptional regulation in cancer could be more clearly articulated.
- **Required correction** Strengthen the discussion by providing more specific hypotheses about how the conformational expansion might affect NHA9 function, and suggest experiments that could test these hypotheses.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, cellular measurements
- **Evidence pointer** Figure 5, Results section "Probing NHA9 FG domain conformation in cells"
- **Issue** The cellular measurements are performed under overexpression conditions, and the authors acknowledge this limitation. However, the potential impact of overexpression on the observed conformational properties is not discussed in detail.
- **Required correction** Add a discussion of how overexpression might affect the measured conformational properties and whether the conclusions are likely to hold at endogenous expression levels.

## Risk / unsupported claims
- The claim that NHA9 forms micelle-like structures with the DNA-binding domain exposed at the periphery is based solely on simulations and requires experimental validation.
- The claim that the FG domain remains dynamic within condensates is inferred from indirect evidence and requires more direct measurements.
- The biological significance of the observed conformational expansion for transcriptional regulation is speculative and not directly tested.
- The quantitative difference between specific and nonspecific DNA effects on nanocluster formation is not clearly established.
- The relationship between the in vitro nanoclusters and the cellular condensates is not fully established, and the relevance of the in vitro findings to the cellular context remains uncertain.