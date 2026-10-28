## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary file descriptions.
- **Assessment boundary** Scientific soundness, technical rigor, and support for the central claims based solely on the provided manuscript material. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics simulations to propose that multicomponent transcriptional condensates formed by Nanog, Oct4, and Sox2 exhibit non-additive, emergent properties. They report that Nanog and Sox2 drive condensate formation, that Oct4 is excluded when Nanog and Sox2 coexist, that Oct4 acts as a DNA "deliverer" while Nanog/Sox2 act as "receivers," and that condensate formation reshapes DNA-protein interaction landscapes.
- **Visible evidence base** Simulation trajectories, density profiles, contact frequency maps, residue-residue contact maps, and DNA affinity quantifications, all derived from the described coarse-grained model. Figures referenced include Figures 1-7 and Supplementary Figures 1-9.
- **Missing materials affecting confidence** No figure panels or actual data plots were provided in the manuscript text. The manuscript references figures and supplementary materials that were not included in the submitted text. No methodological validation data (e.g., force field benchmarks, convergence tests beyond z-position monitoring) were shown. No experimental validation data are presented.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question in the field of transcriptional condensates: whether multi-component TF assemblies behave additively or exhibit emergent, non-additive properties. The simulation approach is appropriate and the central hypothesis, a "deliverer-receiver" mechanism, is conceptually interesting. However, the manuscript as presented has several critical technical and presentational weaknesses. The most significant concern is that the central claims of non-additivity and the deliverer-receiver mechanism are not fully supported by the quantitative data presented in the text. The manuscript relies heavily on qualitative descriptions of snapshots and contact maps, and key quantitative analyses (e.g., statistical significance of the ~20% difference in DNA content, error bars on critical concentrations) are either missing or only described in text. The distinction between "deliverer" and "receiver" roles is not dynamically demonstrated; the authors themselves acknowledge this in the discussion. The lack of any experimental validation or connection to in vivo relevance, while not fatal for a simulation paper, weakens the broader impact claim. The manuscript is technically sound in its use of established models (AICG2+, HPS, 3SPN.2C) but the presentation of results needs substantial revision to meet the standards of a high-impact journal.
- **Who would be interested in the results, and why** Researchers in the fields of gene regulation, transcriptional mechanisms, phase separation, and biophysics of biomolecular condensates. The work is also relevant to those studying pluripotency and early development, given the focus on Nanog, Oct4, and Sox2. The proposed non-additive mechanism and the deliverer-receiver concept would be of interest to a broad readership interested in how condensates function as regulatory hubs.
- **Major strengths**
  1. The study tackles a complex, multi-component system and attempts to move beyond pairwise interaction analyses, which is a significant step forward in the field.
  2. The use of a well-established coarse-grained model (AICG2+ for proteins, 3SPN.2C for DNA) lends credibility to the technical approach.
  3. The central hypothesis of a deliverer-receiver mechanism is novel and provides a clear, testable framework for future experimental work.
  4. The systematic comparison of binary and ternary mixtures is a logical and effective way to probe non-additive effects.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence strength for central claim
  - **Claim pointer** The claim that "phase separation reshapes DNA-protein interaction landscapes, altering the intramolecular regions that engage DNA" and the related claim that condensate formation changes the binding mode (e.g., from CTD to NTD for Sox2).
  - **Evidence pointer** Results section "DNA-Protein interactions change upon condensate formation", Figure 6j-k, Supplementary Figures 5, 7-9.
  - **Concern** The manuscript states that upon condensation, DNA interactions with the CTDs of Nanog and Sox2 weaken and shift to the NTD/DBD. However, the provided text does not include the actual contact maps or quantitative comparisons between the single-molecule and condensate states. The claim is based on a qualitative visual comparison of figures that are not included in the text provided. Without seeing the data, it is impossible to assess the magnitude of this shift or whether it is statistically significant. The authors need to provide a quantitative comparison (e.g., normalized contact frequencies per residue) between the single-molecule and condensate simulations to support this claim.
  - **Why it matters** This is a central mechanistic claim of the paper. The "reshaping" of interaction landscapes is presented as a key emergent property of condensate formation. If this claim is not rigorously supported, the entire conceptual framework of the paper is weakened.
  - **Resolution test** Provide the actual contact maps (as in Fig. 6j-k) with clear quantitative annotations. Include a statistical comparison (e.g., mean +/- SD over the three independent simulations) of the contact frequency for each protein region (NTD, DBD, CTD) with DNA, in both the single-molecule and condensate conditions. A clear, statistically significant shift in the dominant binding region must be demonstrated.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Support for functional mechanism
  - **Claim pointer** The claim that Oct4 acts as a DNA "deliverer" that captures and transports DNA, while Nanog/Sox2 act as "receivers" that provide a stable scaffold.
  - **Evidence pointer** Discussion section, Figure 7.
  - **Concern** The proposed "deliverer-receiver" mechanism implies a dynamic process of capture, transport, and transfer. However, the simulations presented are equilibrium or quasi-equilibrium simulations of pre-formed condensates. The authors do not present any dynamic analysis (e.g., tracking of individual DNA molecules over time, calculation of residence times, or evidence of directed movement) that would support the "deliverer" role. The authors acknowledge this limitation in the discussion, but the use of the term "deliverer" in the title and abstract overstates the evidence. The data support a static correlation (Oct4 has higher DNA affinity and is in DNA-rich regions), not a dynamic mechanism.
  - **Why it matters** The title and abstract promise a "mechanism." If the simulations only show a steady-state distribution, the claim of a mechanism is not established. This is a matter of scientific accuracy and appropriate interpretation of the data.
  - **Resolution test** Either (a) provide new dynamic analyses from the simulations that directly demonstrate DNA capture and transfer by Oct4 (e.g., time-resolved tracking of DNA molecules moving from the exterior to the interior of the condensate via Oct4), or (b) substantially temper the language in the title, abstract, and discussion to describe the observed steady-state partitioning as a "potential" or "proposed" mechanism that requires experimental validation. The current framing is not supported by the evidence.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Quantitative rigor
  - **Claim pointer** The claim that condensates containing Oct4 have "~20% higher DNA content" and that Oct4 has "markedly and statistically significantly higher affinity for DNA (about 39 ± 2%)" compared to Nanog and Sox2.
  - **Evidence pointer** Results sections "Three-to-One TF-DNA simulations" and "Architecture of Phase-Separated Transcriptional Condensates", Figure 4e, Figure 5m.
  - **Concern** The text reports specific numbers with error bars (e.g., 39 ± 2%) and claims statistical significance, but the statistical test used is not described. For the "~20% higher DNA content" claim, no error bars or statistical analysis are mentioned. The authors need to clearly state the statistical methods used (e.g., t-test, ANOVA) and report the p-values or confidence intervals for these key quantitative claims.
  - **Why it matters** The quantitative claims are a key part of the evidence for the non-additive effects. Without proper statistical reporting, the reader cannot assess the robustness of these findings.
  - **Resolution test** Add a "Statistical Analysis" subsection to the Methods. For each quantitative claim (DNA affinity, DNA content, critical concentrations), state the statistical test used, the number of independent simulations (n=3), and report the exact p-values or 95% confidence intervals.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of methods
  - **Affected element** Methods section "Molecular dynamics simulations"
  - **Evidence pointer** Methods section, location not provided.
  - **Issue** The description of the simulation setup is incomplete. The text mentions "pre-assembled condensate states" and "artificially compressed" configurations but does not provide details on how the initial condensate was assembled, the equilibration protocol, or the criteria used to determine that the system was equilibrated.
  - **Required correction** Provide a more detailed description of the system preparation, including the initial placement of molecules, the compression protocol, and the equilibration time. Also, describe the criteria used to assess convergence (e.g., stability of the condensate radius of gyration, density profiles).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Presentation of results
  - **Affected element** Results section "Architecture of Phase-Separated Transcriptional Condensates"
  - **Evidence pointer** Figure 5, location not provided.
  - **Issue** The text refers to "reduced density (ρ*)" and defines it, but the definition is somewhat buried in the text. A clear equation or a more prominent definition would improve readability.
  - **Required correction** Define ρ* explicitly in the Results section where it is first used, or refer the reader to a clearly labeled equation in the Methods.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Biological relevance
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion, location not provided.
  - **Issue** The discussion of biological implications is somewhat speculative. While the authors correctly note the limitations, the leap from simulation to "gene expression regulation" could be better contextualized with specific, testable predictions.
  - **Required correction** Add a short paragraph in the Discussion that explicitly lists 2-3 specific, experimentally testable predictions arising from the model (e.g., "We predict that mutations in the Oct4 DBD that reduce DNA affinity will decrease DNA partitioning into condensates without affecting condensate formation").
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Figure accessibility
  - **Affected element** All figures
  - **Evidence pointer** Figures 1-7, location not provided.
  - **Issue** The figure legends are not provided in the text. It is impossible to fully interpret the results without them.
  - **Required correction** Ensure that all figure legends are included and are self-contained, clearly describing the simulation conditions, the quantities plotted, and the color schemes used.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative evidence for the "reshaping" of DNA-protein interaction landscapes.
  - R1-M2: Overstatement of the "deliverer-receiver" mechanism without dynamic evidence.
  - R1-M3: Incomplete statistical reporting for key quantitative claims.
- **Assessment against Nature-style criteria**
  - **Originality** The concept of a "deliverer-receiver" mechanism is a novel and interesting framing for the role of different TFs within a condensate. The systematic comparison of binary and ternary mixtures to probe non-additivity is a creative approach. However, the underlying observation that different proteins have different propensities for phase separation and DNA binding is not entirely new. The originality lies in the specific combination and the proposed mechanistic model.
  - **Scientific importance** The question of whether multi-component condensates have emergent properties is of high importance to the fields of gene regulation and condensate biology. If the non-additive effects are real and generalizable, this would significantly advance our understanding of how condensates function. The work has the potential to be important, but the current evidence is not fully convincing.
  - **Interdisciplinary readership** The topic is inherently interdisciplinary, bridging molecular biology, biophysics, and computational biology. The paper would appeal to researchers in all these areas. However, the presentation is quite technical and may be challenging for a purely biological audience. The authors should make a greater effort to explain the significance of the simulation results in more accessible terms.
  - **Technical soundness** The choice of models (AICG2+, HPS, 3SPN.2C) is appropriate and well-established. The simulation lengths (1 μs) are reasonable for this type of system. However, the lack of detailed convergence analysis and the incomplete statistical reporting are technical weaknesses that need to be addressed.
  - **Readability for nonspecialists** The abstract is clear, but the results section is dense and relies heavily on jargon. The paper would benefit from a more narrative-driven results section that guides the reader through the key findings. The lack of figure legends in the provided text makes it impossible to assess the clarity of the figures.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the simulation approach is sound, but the manuscript in its current form does not fully support its central claims. The authors must provide the missing quantitative data, perform the necessary statistical analyses, and temper the language of the "deliverer-receiver" mechanism to match the evidence. After these revisions, the paper could be a valuable contribution to the field.

## Risk / unsupported claims
- The claim that the "deliverer-receiver" mechanism is a dynamic process of DNA capture and transfer is unsupported by the presented equilibrium simulations.
- The claim that "phase separation reshapes DNA-protein interaction landscapes" is not quantitatively supported in the provided text.
- The claim that the observed effects are "non-additive" is supported by the comparison of binary and ternary systems, but the statistical significance of the key differences (e.g., ~20% higher DNA content) is not established.
- The biological relevance and in vivo implications of the proposed mechanism are speculative and not directly supported by the simulation data.