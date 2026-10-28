## Review setup
- **Input scope** Full manuscript text (preprint, arXiv:2303.12775v2)
- **Assessment boundary** Scientific content, methodological soundness, validation strategy, and claims as presented in the provided text. No line numbers were available; references to sections and figures are used.
- **Shared manuscript claim summary** The authors present (i) an implementation of the CTPOL polarizable/charge-transfer model in OpenMM, (ii) an open-source parameterization tool (FFAFFURR) for OPLS-AA and CTPOL models, and (iii) evidence that this workflow improves the accuracy of force-field energies relative to DFT and stabilizes the Zn²⁺ binding domain of a Zinc-finger protein in MD simulations compared to standard OPLS-AA.
- **Visible evidence base** Sections 2 (Methods), 3 (Results and Discussion), and 4 (Conclusion); Figures 1–16; Tables 1–2; Supplementary references (Figures S1–S4, Table S2). Equations are referenced but not fully reproduced in the provided text.
- **Missing materials affecting confidence** Full equation definitions (eqs. 1–13) are not shown in the provided text, limiting assessment of the functional forms. Supplementary figures and tables (S1–S4, Table S2) are referenced but not provided. Details of the MD simulation protocols (thermostat, barostat, integration time step for CTPOL, equilibration criteria) are incomplete. The exact composition of the training and test sets (e.g., number of conformers per system) is not fully specified.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important problem: the accurate simulation of metal–protein interactions, which remains a major challenge for classical force fields. The authors combine a polarizable/charge-transfer model (CTPOL) with a flexible parameterization workflow (FFAFFURR) and demonstrate improvements in both energy reproduction and MD stability for a Zinc-finger protein. The work is technically sound in its core approach, and the open-source availability of the tools is a significant contribution. However, several concerns regarding the completeness of the methodological description, the statistical robustness of the MD validation, and the generalizability of the conclusions need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers in computational chemistry and biophysics, particularly those working on force-field development, metalloprotein simulations, and ion–protein interactions. The open-source tools (FFAFFURR and CTPOL-in-OpenMM) will be of direct utility to practitioners seeking to parameterize force fields for specific metal-containing systems. The study also has relevance for method developers interested in polarizable models and automated parameterization workflows.
- **Major strengths**
  1. The manuscript addresses a well-recognized limitation of classical force fields (metal–protein interactions) and proposes a practical, open-source solution.
  2. The FFAFFURR tool is designed to be flexible (LASSO, Ridge, PSO) and system-specific, which is a useful departure from generic parameter transferability assumptions.
  3. The validation strategy is multi-layered: energy reproduction against DFT, MD stability, and comparison with NMR structures.
  4. The authors are transparent about the limitations of their approach (e.g., contracted binding domain in opt-CTPOL) and discuss plausible causes and remedies.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that FFAFFURR enables "rapid construction of FFs for troublesome metal centers" and that the optimized parameters are validated by MD simulations.
  - **Evidence pointer** Section 3.3, Figures 5–11, Table 1
  - **Concern** The MD validation is based on only three 40 ns simulations per parameter set, and the authors report that CTPOL (without LJ optimization) shows instability in some initial conditions. The statistical significance of the observed differences between models is not established. For example, the claim that opt-CTPOL is "stable for all initial conditions" is based on 40 × 1 ns simulations, which may be too short to capture slow conformational changes. Additionally, the choice of the NMR structure as the sole starting point for the 40 ns simulations may bias the results.
  - **Why it matters** The central claim of the manuscript is that the FFAFFURR workflow produces force fields that are suitable for MD simulations of metalloproteins. If the validation is not statistically robust, the reliability of this claim is weakened.
  - **Resolution test** Provide additional independent MD simulations (e.g., 5–10 replicates of 100–200 ns) for each parameter set, and report ensemble-averaged metrics with error bars. Alternatively, demonstrate that the observed differences are consistent across multiple starting structures and simulation lengths.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The claim that FFAFFURR is a functional, open-source parameterization tool.
  - **Evidence pointer** Section 2.5, GitHub links
  - **Concern** The manuscript does not provide sufficient detail on the FFAFFURR workflow to allow independent reproduction. Key equations (eqs. 1–13) are not fully presented, and the exact objective functions, regularization procedures, and convergence criteria are not described. The GitHub repository is referenced, but the manuscript should stand alone as a scientific record.
  - **Why it matters** For a tool that is meant to be used by the community, the methodological description must be complete enough for others to implement or understand the approach without relying solely on external code.
  - **Resolution test** Include the full set of equations in the main text or a clearly referenced appendix. Provide a step-by-step description of the parameterization workflow, including the objective function, regularization, and optimization settings.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The claim that CTPOL outperforms OPLS-AA for divalent cation–peptide systems.
  - **Evidence pointer** Section 3.2, Figures 3–4
  - **Concern** The improvement in energy reproduction for CTPOL over OPLS-AA is demonstrated for a limited set of dipeptide–cation systems. The generalizability of this conclusion to other metal ions, coordination geometries, and protein environments is not established. The authors note that the ab initio data set lacks systems with simultaneous S and N coordination, which is a key feature of the actual Zinc-finger binding site.
  - **Why it matters** The broader claim that CTPOL is a superior model for metalloprotein simulations requires evidence across a wider range of chemical contexts.
  - **Resolution test** Expand the validation to include additional metal ions (e.g., Ca²⁺, Mg²⁺, Cu²⁺) and coordination environments, or clearly state the limitations of the current study in the conclusions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 2.2, CTPOL model description
  - **Evidence pointer** Section 2.2
  - **Issue** The description of the CTPOL model is brief, and the relationship between the charge-transfer parameters (a_L, b_L) and the physical meaning of the cutoff distance is not fully explained.
  - **Required correction** Provide a more detailed explanation of the CTPOL functional form and the physical rationale for the parameter choices.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Section 2.3, Reference data set
  - **Evidence pointer** Section 2.3, Figure 1
  - **Issue** The manuscript states that the data set covers a wide range of relative energies, but the exact energy range and the distribution of conformers are not quantified.
  - **Required correction** Provide a histogram or table summarizing the energy range and the number of conformers per system.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 3.3, MD validation
  - **Evidence pointer** Figures 5–11
  - **Issue** The figures are dense and the captions are not fully self-explanatory. For example, the definition of "binding domain RMSD" and the color coding in Figure 5 are not immediately clear.
  - **Required correction** Expand the figure captions to clearly define all metrics and visual elements.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Section 2.6, MD simulation details
  - **Evidence pointer** Section 2.6
  - **Issue** The MD simulation protocol is described only briefly. Details such as the integration time step, thermostat/barostat settings, and the treatment of long-range electrostatics for the CTPOL model are not fully specified.
  - **Required correction** Provide a complete description of the MD simulation parameters, either in the main text or in a supplementary table.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1 (statistical robustness of MD validation)
  - R1-M2 (incomplete methodological description)
- **Assessment against Nature-style criteria**
  - **Originality** The combination of a polarizable/charge-transfer model with a flexible, system-specific parameterization workflow is a novel contribution. The open-source implementation of CTPOL in OpenMM is also a valuable addition.
  - **Scientific importance** The problem addressed (metal–protein interactions) is of high importance in biophysics and drug design. The work has the potential to enable more accurate simulations of metalloproteins, which are involved in many biological processes.
  - **Interdisciplinary readership** The work will appeal to computational chemists, biophysicists, and method developers. The open-source tools lower the barrier for adoption, but the manuscript is written in a way that assumes familiarity with force-field parameterization and MD simulation.
  - **Technical soundness** The core methodology is sound, but the incomplete description of the workflow and the limited statistical validation of the MD results are significant gaps that need to be addressed.
  - **Readability for nonspecialists** The manuscript is generally well-written, but the dense figures and the lack of a clear summary of the FFAFFURR workflow may make it challenging for nonspecialists to fully appreciate the contribution.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a promising and useful contribution, but the methodological completeness and the statistical robustness of the validation need to be improved before the claims are fully established.

## Risk / unsupported claims
- The claim that FFAFFURR enables "rapid construction of FFs" is not quantified; no timing or usability benchmarks are provided.
- The claim that CTPOL "outperforms" OPLS-AA is based on a limited set of systems and may not generalize.
- The statement that "the data set covers a wide range of relative energies" is not supported by quantitative data in the provided text.
- The assertion that opt-CTPOL is "stable for all initial conditions" is based on 40 × 1 ns simulations, which may be insufficient to support this strong claim.