## Review setup
- **Input scope** Full manuscript text (abstract, introduction, models and theory, results, discussion, supplementary material description, funding, author contributions, data availability)
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims based solely on the provided manuscript text. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The authors present a combined particle-based reaction-diffusion simulation, mass-action kinetic, and theoretical framework to show that reversible protein dimerization can either enhance or impair DNA target selectivity, dwell time, and occupancy depending on target spacing, dimer lifetime, and the dimensionality factor γ. They demonstrate that dimerization always increases recruitment to DNA but can impair dwell time and occupancy for isolated targets, while strongly enhancing selectivity for clustered targets. They validate their model against ChIP-seq data for the GAGA factor (GAF) in Drosophila.
- **Visible evidence base** Main text figures (Figs. 1–6), supplementary figures (Figs. S1–S10), equations (Eqs. 1–13), and references to supplementary sections (SI SX.B, SX.C, SX.E, SXII.C, SVI, SVII, SVIII, SIX, SXI, SV.D, SV.E) and Dataset S1. No actual figure images, numerical values, or code outputs were visible in the provided text.
- **Missing materials affecting confidence** Figure images and captions, full supplementary information text, Dataset S1, and the Zenodo repository contents. Without these, quantitative validation of the model against simulations and ChIP-seq data cannot be independently assessed.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question in gene regulation: how protein dimerization modulates DNA target search and binding. The authors develop a sophisticated multiscale modeling framework that integrates spatial stochastic simulations, ODE models, and analytical theory. The central finding, that dimerization can both enhance and impair DNA binding depending on target spacing and dimer lifetime, is conceptually novel and has broad implications for interpreting experimental data. The application to GAF and comparison with ChIP-seq data is compelling. However, the manuscript as presented has several significant issues that must be addressed: (i) the derivation of key equations is not shown in the main text, (ii) the validation of the ODE model against spatial simulations is described but not quantitatively demonstrated in the visible text, (iii) the comparison with ChIP-seq data lacks statistical rigor as presented, and (iv) the parameterization of the model for GAF is not fully justified. These issues currently prevent full confidence in the conclusions.
- **Who would be interested in the results, and why** Researchers in gene regulation, transcription factor biology, biophysics of protein-DNA interactions, and computational biology. The work provides a framework for interpreting single-molecule and genome-wide binding data, and the finding that weak dimerization can dramatically alter target selectivity is directly relevant to understanding how transcription factors achieve specificity in vivo. The modeling approach will also interest theorists working on reaction-diffusion systems and multiscale modeling.
- **Major strengths** (1) The combination of three complementary modeling approaches (spatial stochastic, ODE, analytical) is rigorous and provides cross-validation. (2) The systematic exploration of parameter space reveals non-monotonic and sometimes counterintuitive behaviors that challenge simple intuitions about dimerization. (3) The application to a real biological system (GAF) with comparison to ChIP-seq data grounds the theoretical work in biology. (4) The identification of a "dimensionality factor" γ as a key control parameter is elegant and provides a compact way to understand complex behaviors. (5) The discussion of implications for interpreting experimental measurements is thoughtful and forward-looking.
- **Major Concerns**
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their ODE model quantitatively matches the spatial stochastic simulations ("supported by our results showing close agreement between survival time distributions in both models").
- **Evidence pointer** Models and theory section, "Mapping from spatial to nonspatial (well mixed)" subsection; Figure S2
- **Concern** The claim of quantitative agreement between the ODE model and spatial simulations is central to the validity of the analytical results, but no quantitative comparison is shown in the visible text. The reader is referred to Figure S2, but the figure itself is not available. The text states "close agreement" without providing any metrics (e.g., percent error, correlation coefficients, or statistical tests). This is insufficient to establish that the ODE model faithfully captures the spatial dynamics, especially given the known limitations of well-mixed approximations for reaction-diffusion systems.
- **Why it matters** If the ODE model does not accurately reproduce the spatial simulations, then all analytical results derived from it (including the key equations for dwell time and selectivity) may be unreliable. The entire theoretical framework rests on this validation.
- **Resolution test** Provide a quantitative comparison between ODE and spatial simulation results, including error metrics or statistical tests, for key observables (dwell time, occupancy, recruitment fraction) across a range of parameter values. Show this comparison in the main text or in a clearly referenced supplementary figure with full numerical details.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the fraction of targets S occupied by proteins" (ϕ) is a key metric, and they derive expressions for it, but the derivation of the central equations (Eqs. 3, 8, 9, 10, 11, 12, 13) is not shown in the main text.
- **Evidence pointer** Models and theory section, "Two-state model for calculating the mean dwell time" subsection; Results sections; Equations 3, 8–13
- **Concern** The manuscript presents a series of analytical expressions (Eqs. 3, 8, 9, 10, 11, 12, 13) that are central to the conclusions, but the derivations are not provided in the main text. The reader is referred to the SI, but the SI text is not available in the provided material. Without seeing the derivations, it is impossible to verify the correctness of these expressions or understand the assumptions underlying them. This is particularly problematic for Eq. 3, which defines the mean dwell time, and for the critical rate thresholds in Eqs. 11 and 13.
- **Why it matters** The analytical results are a major contribution of the paper. If the derivations contain errors or rely on unjustified assumptions, the conclusions would be invalid. The reader cannot assess this without seeing the derivations.
- **Resolution test** Provide the full derivations of all key equations in the main text or in a supplementary appendix that is included with the manuscript. Clearly state all assumptions and approximations used in each derivation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their model "explains how the distribution of the essential GAGA factor monomer throughout the genome is highly selective for clustered targets due to protein interactions" and that the model results are "consistent with the GAF ChIP-seq results."
- **Evidence pointer** Results section, "Simulation results reproduce ChIP-seq data on oligomer selectivity for clustered targets" subsection; Figure 5
- **Concern** The comparison with ChIP-seq data is presented qualitatively. The text states that the model results are "consistent" with the data and that the GAF occupancy "exceeds the monomer upper bound," but no quantitative statistical analysis is shown. There is no description of how the ChIP-seq data were processed, how the model predictions were mapped to genomic coordinates, or what statistical test was used to assess agreement. The figure (Fig. 5) is not visible, so the actual comparison cannot be evaluated.
- **Why it matters** The validation against experimental data is a key selling point of the paper. Without a rigorous quantitative comparison, the claim that the model explains GAF's genome-wide distribution is not established.
- **Resolution test** Provide a detailed description of the ChIP-seq data analysis, including data processing, normalization, and the specific statistical tests used to compare model predictions with experimental observations. Show the quantitative comparison in a figure with error bars and statistical significance indicators.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "dimerization can also impair measured dwell times and occupancy on target sequences because the population redistributes across DNA" and that this is a key insight of their work.
- **Evidence pointer** Abstract; Results sections; Figure 6
- **Concern** While the finding that dimerization can impair binding is interesting, the manuscript does not clearly articulate the biological significance of this impairment. The authors mention that mutations in protein interaction domains can have "unpredictable effects," but they do not discuss specific biological contexts where this impairment would be functionally relevant. The discussion of "trials" of binding is intriguing but speculative.
- **Why it matters** For a Nature-style audience, it is important to understand not just the mechanism but also why it matters for biology. The current manuscript does not fully make this connection.
- **Resolution test** Add a section in the Discussion that explicitly addresses the biological implications of dimerization-induced impairment, with specific examples of biological systems or processes where this could be important. Consider discussing how this could affect gene expression noise, developmental decisions, or disease states.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The manuscript is written for a specialized audience familiar with reaction-diffusion modeling and statistical mechanics.
- **Evidence pointer** Throughout the manuscript, particularly in the Models and theory section
- **Concern** The manuscript assumes significant background knowledge in physical chemistry and stochastic processes. Terms like "dimensionality factor," "partition coefficient," and "well-mixed assumption" are used without sufficient explanation for a broader biological audience. The biological motivation and implications are sometimes lost in the technical details.
- **Why it matters** The findings are relevant to a wide range of biologists studying gene regulation, but they may not be able to fully appreciate the work without additional context and explanation.
- **Resolution test** Revise the introduction and models section to provide more biological context and explain key physical concepts in accessible terms. Consider adding a "box" or supplementary text that explains the physical principles for non-specialists.

- **Minor Comments**
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract begins with a general statement about transcription that is somewhat vague. The key finding about dimerization impairing binding is buried in the middle of the abstract.
- **Required correction** Consider restructuring the abstract to more clearly state the main finding upfront, e.g., "Protein dimerization can both enhance and impair DNA target selectivity, depending on target spacing and dimer lifetime. We show this through a combined modeling approach..."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Model parameterization
- **Evidence pointer** Models and theory section, "Copy numbers" subsection
- **Issue** The choice of specific parameter values (e.g., diffusion coefficients, rate constants) is not justified in the main text. The reader is referred to the SI and Dataset S1, but these are not available.
- **Required correction** Provide a brief justification for the key parameter values in the main text, or at least summarize the ranges explored and the rationale for these choices.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Model limitations
- **Evidence pointer** Discussion section
- **Issue** The manuscript acknowledges several simplifications (e.g., no energy consumption, no chromatin structure) but does not discuss how these could affect the conclusions.
- **Required correction** Add a paragraph in the Discussion that explicitly addresses the potential impact of the simplifications on the robustness of the conclusions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Figure accessibility
- **Evidence pointer** Figures 1–6
- **Issue** The figure captions are not visible in the provided text, so it is unclear whether they are accessible to a broad audience.
- **Required correction** Ensure that figure captions clearly explain the biological significance of each panel and define all symbols and abbreviations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion of broader implications
- **Evidence pointer** Discussion section
- **Issue** The discussion of implications for single-molecule experiments and therapeutic targeting is brief and could be expanded.
- **Required correction** Consider adding a paragraph that discusses how the model could be used to interpret specific experimental measurements (e.g., single-particle tracking, FRAP) and how it could inform drug design targeting protein-protein interactions.

- **Technical failings that need to be addressed before the case is established** R1-M1 (ODE-simulation validation), R1-M2 (derivations not shown), R1-M3 (ChIP-seq comparison lacks rigor). These are blocking because they undermine the core technical claims of the manuscript.
- **Assessment against Nature-style criteria** 
  - Originality: High. The finding that dimerization can impair DNA binding is counterintuitive and challenges existing assumptions. The multiscale modeling approach is novel in its combination of methods.
  - Scientific importance: High. The work addresses a fundamental question in gene regulation and provides a framework for understanding how protein-protein interactions modulate DNA target selection. The implications for interpreting experimental data are significant.
  - Interdisciplinary readership: Moderate. The work will appeal to biophysicists, computational biologists, and some molecular biologists, but the technical nature may limit its accessibility to a broader biological audience.
  - Technical soundness: Currently not fully established. The lack of visible derivations and quantitative validation prevents full confidence in the results.
  - Readability for nonspecialists: Moderate. The writing is clear for a technical audience but may be challenging for biologists without a strong physical chemistry background.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual advance is significant and the modeling framework is potentially very valuable. However, the manuscript in its current form does not provide sufficient evidence to fully support the claims. The authors must provide the derivations, quantitative validation, and rigorous ChIP-seq comparison before the case is established.

## Risk / unsupported claims
- The claim that the ODE model "quantitatively matches" the spatial simulations is unsupported without visible quantitative comparison.
- The claim that the model "explains" GAF's genome-wide distribution is not fully supported without a rigorous statistical comparison to ChIP-seq data.
- The claim that "dimerization can also impair measured dwell times and occupancy" is supported by the model but the biological significance is not fully established.
- The claim that "even weak dimerization can redistribute and stabilize proteins on DNA" is supported by the model but the parameter range for "weak" is not clearly defined in the visible text.
- The claim that the model "predicts when even weak dimerization can redistribute and stabilize proteins on DNA as a necessary part of transcription" is a forward-looking statement that is not directly tested in the current work.