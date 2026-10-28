## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and alignment with Nature-style criteria. Editorial and formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors claim that allosteric communication pathways in viral TAR RNA can be systematically mapped using contact-based PCA and graph-network analysis, and that a single-nucleotide insertion (C24) in HIV-1 TAR rewires these pathways, switching the Tat-binding mechanism from conformational selection (HIV-2) to induced fit (HIV-1), with consequences for binding affinity and downstream CycT1 recruitment.
- **Visible evidence base** Methods descriptions (system setup, simulation protocols, steered MD, umbrella sampling, contact-PCA, contact probability maps, graph-network construction); results narrative referencing Figures 1–5 and supplementary figures/tables; abstract and conclusion claims.
- **Missing materials affecting confidence** Figures and supplementary information (Figures S1–S10, Tables S1–S6) are referenced but not provided. No numerical data (free energy values, Kd comparisons, statistical errors) are given in the text. No simulation convergence metrics are reported. The graph-network algorithm is described but not validated against known or experimental allosteric pathways.

## Reviewer

- **Overall assessment** This manuscript addresses a timely and mechanistically important question: how RNA sequence variation encodes allosteric control of protein binding. The comparative design across BIV, HIV-1, and HIV-2 TAR is well motivated, and the combination of long-timescale MD, free energy calculations, and network analysis is ambitious. However, the central claims—particularly the proposed switch between conformational selection and induced fit, and the functional relevance of the identified allosteric pathways—are not quantitatively supported by the evidence presented in the text. The manuscript would benefit from clearer reporting of numerical results, validation of the network method, and a more cautious interpretation of mechanism inferred from 1D reaction coordinates.

- **Who would be interested in the results, and why** Researchers in RNA biology, biophysics, and computational chemistry would find the comparative TAR analysis of interest, particularly those studying RNA allostery, protein-RNA recognition mechanisms, and the design of RNA-targeting therapeutics. The methodological combination of contact-PCA and graph-network analysis for RNA may also attract method developers. The clinical relevance to HIV transcriptional regulation broadens the potential audience to virologists and antiviral drug designers.

- **Major Strengths**
  - The comparative design across three viral TAR variants is well conceived and allows for systematic interrogation of sequence effects.
  - The combination of multiple computational techniques (MD, SMD, umbrella sampling, contact-PCA, network analysis) is comprehensive and ambitious.
  - The focus on allosteric rewiring and the distinction between conformational selection and induced fit is mechanistically important and timely.
  - The authors acknowledge limitations of the 1D reaction coordinate and the dependence on explicit solvent conditions, which is commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that HIV-2 TAR employs conformational selection while HIV-1 TAR employs induced fit, and that this switch is caused by the C24 insertion.
- **Evidence pointer** Results section "Active Site Bulge Mutation Alters Protein Binding Mechanism"; Figures 3A–H; location not provided for specific numerical data
- **Concern** The mechanistic distinction between conformational selection and induced fit is inferred from qualitative features of the free energy profiles and apo-state dynamics. No quantitative metrics (e.g., binding kinetics, population shifts, relaxation times) are provided that would distinguish these mechanisms. The free energy profiles are described only qualitatively ("broad single minimum" vs. "broader global well subdivided into two basins"), and no numerical values (barrier heights, well depths, errors) are reported. The claim of a mechanism switch is therefore not established from the provided evidence.
- **Why it matters** The central mechanistic claim of the paper rests on this distinction. Without quantitative support, the conclusion that a single nucleotide switches binding mechanism is speculative and could be an artifact of the chosen reaction coordinate or simulation conditions.
- **Resolution test** Provide numerical free energy differences, barrier heights, and statistical uncertainties. Show that the proposed conformational selection and induced fit pathways are kinetically distinguishable (e.g., via committor analysis or transition path sampling). Demonstrate that the mechanism assignment is robust to changes in force field, simulation length, and reaction coordinate definition.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Method validation
- **Claim pointer** The authors claim to have applied a graph-network algorithm "first-time for 3D RNA structures" to map allosteric pathways from bulge to loop.
- **Evidence pointer** Methods section "Graph-Network Construction to Map Allosteric Path"; Results section "Navigating Shortest Allosteric Pathways"; location not provided
- **Concern** The graph-network method is described as novel for RNA, but no validation is provided. There is no benchmark against known allosteric pathways, no comparison to alternative methods (e.g., mutual information, dynamical network analysis on proteins), and no assessment of the sensitivity of the identified pathways to the correlation metric, edge definition, or threshold parameters. The claim of "first application" requires demonstration that the method produces meaningful and robust results.
- **Why it matters** If the network method is not validated, the identified pathways (canonical vs. noncanonical) and their rewiring upon mutation or binding cannot be interpreted with confidence. The novelty claim also invites scrutiny; without validation, the method may be seen as an arbitrary application of a protein-based approach to RNA.
- **Resolution test** Validate the method on a system with known allosteric communication (e.g., a riboswitch with experimentally characterized pathways). Perform sensitivity analysis on edge thresholds, correlation metrics, and node definitions. Compare identified pathways to those from independent methods or experimental mutagenesis data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Simulation convergence and sampling
- **Claim pointer** The authors performed "tens of microseconds" of MD simulations and report equilibrium and steered MD results.
- **Evidence pointer** Methods section "Simulation protocols"; Tables S4–S6; location not provided
- **Concern** No convergence metrics are reported. For a study claiming to distinguish subtle mechanistic differences between two similar RNA systems, it is essential to demonstrate that the simulations have adequately sampled the relevant conformational space. The text mentions "∼1µs simulation data" for network construction, but the total simulation time, number of replicas, and convergence of free energy estimates are not stated in the main text.
- **Why it matters** Without convergence evidence, the observed differences between HIV-1 and HIV-2 could reflect insufficient sampling rather than genuine mechanistic differences. This is particularly concerning for the free energy profiles and the proposed bimodal vs. unimodal distributions.
- **Resolution test** Report block-averaged free energy estimates with uncertainties, show convergence of PMF profiles over time, and provide RMSD or other metrics demonstrating equilibration. If possible, include multiple independent replicas to assess sampling variability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model construction validity
- **Claim pointer** The HIV-1 TAR-Tat complex was constructed by "manually inserting a C24 nucleotide at the bulge region and removing the terminal G:C base pair from the HIV-2 framework."
- **Evidence pointer** Methods section "System Setup"; Figure S1; location not provided
- **Concern** The construction of the HIV-1 complex model from the HIV-2 structure by manual insertion is a significant approximation. The authors do not describe how the insertion was modeled (e.g., loop modeling, energy minimization, equilibration protocol), nor do they assess the structural validity of the resulting model. The removal of the terminal G:C base pair is also not justified.
- **Why it matters** The conclusions about HIV-1 binding mechanisms and the role of C24 depend critically on the quality of this model. If the insertion introduces artifacts, the observed differences between HIV-1 and HIV-2 could be model artifacts rather than real biological differences.
- **Resolution test** Provide structural validation of the constructed model (e.g., comparison to known HIV-1 TAR structures, assessment of steric clashes, backbone geometry). Justify the removal of the terminal base pair. If possible, validate key findings with simulations starting from an experimentally determined HIV-1 TAR structure.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance of identified pathways
- **Claim pointer** The authors claim that the identified allosteric pathways and the G32 flip dynamics are relevant for CycT1 recruitment and downstream transcriptional signaling.
- **Evidence pointer** Results section "Post-Tat-Binding Allosteric Interplay"; Figures 4A–D, S9, S10; location not provided
- **Concern** The connection between the observed G32 dynamics and CycT1 recruitment is speculative. No simulations or experiments involving CycT1 are presented. The claim that G32 flipping "likely" promotes CycT1 binding is not tested. The functional significance of the identified pathways for transcriptional signaling is asserted but not demonstrated.
- **Why it matters** The broader significance of the work, as stated in the abstract and conclusion, depends on the relevance of the identified allosteric mechanisms to biological function. Without direct evidence linking G32 dynamics to CycT1 binding, the functional claims are unsupported.
- **Resolution test** Perform simulations of the TAR-Tat-CycT1 ternary complex, or experimentally test the effect of G32 mutations on CycT1 recruitment. At minimum, provide a more cautious interpretation that clearly distinguishes observed dynamics from inferred functional consequences.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of reporting
- **Affected element** Free energy results
- **Evidence pointer** Results section "Binding Free Energy Uncovers Different Modes of Protein Accommodation in RNA Groove"; Figures 2A–B; location not provided
- **Issue** The free energy profiles are described only qualitatively. No numerical values for barrier heights, well depths, or binding free energies are given in the text.
- **Required correction** Report numerical free energy values with uncertainties, and include the PMF profiles as figures with clear axis labels and error bars.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Contact-PCA and network analysis
- **Evidence pointer** Methods section "Contact-Based Principal Component Analysis"; Results section "A Single Point Mutation in Active Site Bulge of Apo HIV TAR RNA Alters Distant Loop Dynamics"; location not provided
- **Issue** The contact-PCA and network analyses are based on single trajectories. No error estimates or replicate analyses are provided.
- **Required correction** Provide uncertainty estimates (e.g., via block bootstrapping or multiple independent simulations) for the PCA loadings and network metrics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of conformational selection vs. induced fit
- **Evidence pointer** Results section "Active Site Bulge Mutation Alters Protein Binding Mechanism"; location not provided
- **Issue** The distinction between conformational selection and induced fit is presented as binary, but the literature recognizes these as extremes of a continuum. The authors do not discuss how their findings fit into this broader framework.
- **Required correction** Add a brief discussion of the conformational selection/induced fit continuum and where the TAR-Tat systems fall on this spectrum.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Figures 1–5; location not provided
- **Issue** The figures are referenced but not described in sufficient detail in the text. Readers cannot fully interpret the results without seeing the figures.
- **Required correction** Ensure each figure is described in sufficient detail in the text, and consider adding a figure legend summary in the main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** "Allosteric rewiring"
- **Evidence pointer** Title, abstract, conclusion; location not provided
- **Issue** The term "allosteric rewiring" is used throughout but is not precisely defined. It is unclear whether it refers to changes in communication pathways, changes in binding mechanism, or both.
- **Required correction** Define "allosteric rewiring" explicitly in the introduction and use the term consistently throughout.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Mechanism switch claim not quantitatively supported
  - R1-M2: Graph-network method not validated
  - R1-M3: No convergence metrics for simulations
  - R1-M4: HIV-1 model construction not validated

- **Assessment against Nature-style criteria**
  - **Originality**: The application of graph-network analysis to RNA allostery is novel, and the comparative TAR design is creative. However, the conceptual framework (allostery, conformational selection vs. induced fit) is well established, and the novelty lies primarily in the methodological application rather than in a new biological principle.
  - **Scientific importance**: The question of how RNA sequence encodes allosteric control is important and has implications for understanding viral gene regulation and designing RNA therapeutics. However, the importance is somewhat diminished by the lack of direct experimental validation and the speculative nature of the functional claims.
  - **Interdisciplinary readership**: The work bridges RNA biology, biophysics, and computational chemistry, and would appeal to researchers in these fields. The clinical relevance to HIV may attract a broader audience. However, the technical complexity and lack of accessible summaries of key findings may limit broader appeal.
  - **Technical soundness**: The simulation protocols are standard and generally appropriate, but the lack of convergence metrics, validation of the network method, and quantitative reporting of free energy results undermine confidence in the technical rigor.
  - **Readability for nonspecialists**: The abstract is clear and accessible, but the results and discussion sections are dense and assume significant background in MD simulation and network analysis. The manuscript would benefit from clearer explanations of the methods and their significance for a broader audience.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an important question with an ambitious methodological approach, but the central claims are not quantitatively supported, the novel network method is not validated, and the functional significance is speculative. The authors should be encouraged to revise and resubmit with additional analyses and more cautious interpretation.

## Risk / unsupported claims
- The claim that HIV-2 TAR employs conformational selection and HIV-1 TAR employs induced fit is not quantitatively supported.
- The claim that the graph-network algorithm is the "first such application to RNA systems" is unverifiable from the provided text and requires a thorough literature search.
- The claim that G32 flipping "likely" promotes CycT1 recruitment is speculative and not tested.
- The claim that the identified allosteric pathways are relevant for transcriptional signaling is asserted but not demonstrated.
- The claim that the C24 insertion "rewires" allosteric communication is based on qualitative comparisons and lacks statistical support.
- The functional significance of the "canonical" vs. "noncanonical" pathways is not established.