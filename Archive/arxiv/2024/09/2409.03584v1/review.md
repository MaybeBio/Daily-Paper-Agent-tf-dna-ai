## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodological soundness, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present a multi-scale computational study of the CzrA transcription repressor, combining microsecond-long all-atom MD simulations of apo and holo (zinc-bound) states with the mapping entropy optimisation workflow (MEOW) to identify functionally important residues and characterize allosteric changes induced by metal ion binding. They report that zinc coordination does not significantly alter the overall protein architecture but does modulate internal dynamics, reducing flexibility and redistributing conformational variability, with specific changes in the DNA binding region.
- **Visible evidence base** Main text (Sections I-IV), Figures 1-9 (described in text), Methods section (Section IV)
- **Missing materials affecting confidence** Figure files, supplementary information, simulation parameter files, convergence analysis details, and raw trajectory data were not provided for direct inspection

## Reviewer
- **Overall assessment** This manuscript presents a computational analysis of the CzrA repressor using a recently developed information-theoretic method (MEOW) applied to microsecond-long MD simulations. The work is technically competent and the application of MEOW to compare apo and holo states is novel. However, the scientific advance over existing knowledge is incremental, and several methodological details and validations are missing that would be needed to fully support the claims made. The manuscript would be of interest to the computational biophysics community, particularly those working on allosteric regulation and coarse-graining methods, but the biological insights are limited by the absence of direct functional validation and the relatively modest differences observed between the two states.
- **Who would be interested in the results, and why** Computational biophysicists and structural biologists studying allosteric regulation, particularly in metal-sensor proteins. Researchers developing and applying information-theoretic methods for analyzing MD simulations would also be interested in seeing MEOW applied to a new system. The work may also appeal to those studying the ArsR/SmtB family of metalloregulatory proteins, though the biological community would likely require more direct experimental validation or functional predictions.
- **Major strengths** The application of MEOW to compare two functional states of the same protein is a novel use of the method. The multi-scale approach combining standard MD analysis with information-theoretic methods is commendable. The manuscript is clearly written and the methodological framework is well explained. The use of microsecond-long simulations is appropriate for the questions addressed.
- **Major Concerns** The central claim that MEOW reveals allosteric changes is not fully supported by quantitative comparisons or statistical validation. The differences between apo and holo states, while described qualitatively, lack rigorous statistical treatment. The biological interpretation of the information field changes is speculative without experimental validation or connection to known functional data. The manuscript does not adequately address whether the observed differences are significant given the simulation length and sampling limitations.
- **Minor Comments** The manuscript would benefit from a more detailed comparison with the previous computational study by Chakravorty et al. The choice of simulation parameters, particularly the use of position restraints for zinc ions, could be better justified. The relationship between the information field and experimentally measurable quantities could be clarified.
- **Technical failings that need to be addressed before the case is established** Lack of statistical error analysis on the information field differences; absence of convergence assessment for the MEOW optimizations; no block-averaging or bootstrapping analysis to establish significance of observed differences; missing validation that the number of optimization runs (M_opt = 48) is sufficient for stable probability estimates.
- **Assessment against Nature-style criteria** Originality: Moderate. The application of MEOW to compare functional states is new, but the underlying approach is established. Scientific importance: Moderate. The work provides incremental insights into CzrA allostery but does not fundamentally advance understanding of allosteric mechanisms. Interdisciplinary readership: Limited. The work is primarily of interest to computational biophysicists; the biological community would need more direct functional relevance. Technical soundness: Adequate but with gaps in statistical validation. Readability for nonspecialists: The manuscript is well-written and the methods are explained clearly, though the significance of the findings for a broad audience is not strongly articulated.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical validation of the information field differences and clearer demonstration that MEOW provides insights beyond standard MD analysis.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validation
- **Claim pointer** The authors claim that "the application of the MEOW approach to the configurations sampled in the MD simulations of the apo and holo forms of CzrA has shown important differences between them" (Section II.3)
- **Evidence pointer** Section II.3, Figures 6-9
- **Concern** The differences in information fields between apo and holo states are described qualitatively, but no statistical analysis is provided to establish that these differences are significant. The information field is computed from 48 independent optimizations, but the variance across these optimizations is not reported. Without error bars or statistical tests, it is impossible to determine whether the observed differences in p_i values (e.g., the increase in the DNA binding region from apo to holo) are meaningful or within the noise of the method.
- **Why it matters** The central claim of the paper rests on the differences between the two states. If these differences are not statistically robust, the conclusions are not supported. The lack of error analysis undermines the reliability of the findings and prevents readers from assessing the significance of the results.
- **Resolution test** Provide error estimates on the information field values (e.g., standard deviation across the 48 optimizations, or bootstrapped confidence intervals). Perform a statistical test (e.g., permutation test or Mann-Whitney U test) comparing the p_i distributions between apo and holo states for the regions of interest. Report effect sizes and confidence intervals for the key differences highlighted in Figures 8 and 9.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Convergence and sampling
- **Claim pointer** The authors state that "within the investigated timescale of 1 μs, both the apo and holo systems individually explore a single conformational basin" (Section II.1)
- **Evidence pointer** Section II.1, Figure 2
- **Concern** The claim of conformational convergence is based on qualitative inspection of RMSD time series and distributions. No quantitative convergence assessment is provided, such as block-averaging of RMSD, autocorrelation analysis, or comparison of conformational ensembles from different time windows. The observation of a single basin in 1 μs does not guarantee that the simulations have fully sampled the relevant conformational space, particularly for a protein that may undergo slow conformational transitions relevant to allostery.
- **Why it matters** The interpretation of both the standard MD analysis and the MEOW results depends on the assumption that the simulations have adequately sampled the equilibrium ensembles of both states. If the simulations are not converged, the observed differences (or lack thereof) between apo and holo states may be artifacts of insufficient sampling rather than genuine biophysical properties.
- **Resolution test** Provide quantitative convergence metrics, such as: (1) block-averaged RMSD with standard errors, (2) convergence of the RMSF profiles over time (e.g., comparing first vs. second half of the trajectory), (3) principal component analysis showing overlap of sampled conformations between time windows, and (4) assessment of whether the MEOW information field stabilizes with increasing simulation time.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and added value of MEOW
- **Claim pointer** The authors claim that MEOW "is capable of pinpointing key features of the protein's allosteric regulation that occurs upon zinc coordination" and that it provides "novel and complementary insight into the allosteric mechanism employed by CzrA" (Sections I, III)
- **Evidence pointer** Sections II.2, II.3, III
- **Concern** The manuscript does not clearly demonstrate that MEOW provides information beyond what could be obtained from standard MD analysis (e.g., RMSF, dynamic cross-correlation analysis, or principal component analysis). The observation that the DNA binding region shows increased information field values in the holo state could potentially be explained by the reduced flexibility already shown in the RMSF analysis (Figure 3). The authors should explicitly compare MEOW results with standard analysis methods and demonstrate that MEOW identifies residues or features that are not apparent from conventional approaches.
- **Why it matters** The novelty of the work rests on the claim that MEOW provides unique insights into allosteric regulation. If the information field simply recapitulates what is already known from RMSF or other standard measures, the scientific contribution is substantially diminished. The authors need to establish the added value of their approach.
- **Resolution test** Perform a direct comparison between MEOW information fields and standard metrics (RMSF, dynamical cross-correlation, community analysis) for both states. Identify residues that are highlighted by MEOW but not by conventional analysis, and discuss their potential functional significance. Alternatively, demonstrate that MEOW captures multi-body correlations that are not accessible from pairwise or single-residue analyses.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The authors interpret changes in the information field as indicating "activation" of the DNA binding region and "deactivation" of the zinc coordination site upon metal binding (Section II.3)
- **Evidence pointer** Section II.3, Figures 8-9
- **Concern** The interpretation of information field changes in terms of functional "activation" or "deactivation" is speculative. The MEOW method identifies residues that are informative for describing the conformational ensemble, but the connection between this information-theoretic measure and biological function is not established. The authors do not provide experimental evidence or known functional data to support these interpretations, and the link between increased information field values and functional relevance is not justified.
- **Why it matters** The biological significance of the findings is a key aspect of the paper's impact. If the interpretation of the MEOW results in functional terms is not well-founded, the conclusions may overstate the biological implications of the computational findings. This could mislead readers about the functional relevance of the observed changes.
- **Resolution test** Provide a more cautious interpretation of the results, explicitly stating the assumptions underlying the connection between information fields and functional relevance. Discuss how the MEOW results relate to known experimental data on CzrA function (e.g., mutational studies, binding affinity measurements). Consider whether the observed changes are consistent with the established allosteric mechanism or if they suggest new hypotheses that could be experimentally tested.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological justification
- **Affected element** Choice of N (number of retained atoms) in MEOW analysis
- **Evidence pointer** Section II.3
- **Issue** The choice of N equal to the number of Cα atoms (187 and 190 for apo and holo, respectively) is stated but not justified. It is unclear whether this choice affects the results and whether the conclusions are robust to this parameter.
- **Required correction** Provide a brief justification for the choice of N, or include a sensitivity analysis showing that the main conclusions are robust to reasonable variations in N.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Comparison with previous work
- **Affected element** Discussion of Chakravorty et al. 2012
- **Evidence pointer** Sections I, II.1
- **Issue** The manuscript mentions differences from the previous computational study by Chakravorty et al., particularly regarding the conformational basins explored by the apo state, but does not discuss possible reasons for these discrepancies (e.g., different force fields, simulation lengths, or analysis methods).
- **Required correction** Add a brief discussion of potential sources of discrepancy between the current results and those of Chakravorty et al., such as differences in simulation protocols or analysis approaches.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 6-9
- **Evidence pointer** Section II.3
- **Issue** The figures are described in the text but were not provided for review. Based on the description, it is unclear how the information fields are visualized and whether the differences between states are readily apparent to the reader.
- **Required correction** Ensure that figures clearly show the differences between apo and holo states, with appropriate color scales and annotations. Consider including a quantitative comparison (e.g., difference map) to highlight the changes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Simulation and analysis parameters
- **Evidence pointer** Section IV
- **Issue** While the Methods section provides a general description of the simulation setup, some parameters are missing, such as the specific version of the force field, the water model parameters, the equilibration protocol details, and the exact parameters used for the MEOW optimizations (e.g., cooling schedule, number of Monte Carlo steps).
- **Required correction** Provide complete simulation and analysis parameters to ensure reproducibility, either in the main text or in supplementary materials.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Information field"
- **Evidence pointer** Section II.2
- **Issue** The term "information field" is introduced but its relationship to the underlying probability distribution and the mapping entropy is not fully clarified. It would be helpful to explicitly define how the information field relates to the mapping entropy and what physical interpretation can be assigned to it.
- **Required correction** Provide a more explicit definition of the information field and its relationship to the mapping entropy, possibly with a brief mathematical formulation.

## Risk / unsupported claims
- The claim that MEOW reveals "activation" of the DNA binding region and "deactivation" of the zinc coordination site is not supported by direct evidence and relies on speculative interpretation of information-theoretic measures.
- The statement that the results "corroborate previous studies" is not quantitatively substantiated; the manuscript does not provide a systematic comparison with prior experimental or computational findings.
- The claim that the apo state is capable of excursions to a "high DNA binding affinity" conformation based on serine-serine distances reaching ~4.0 nm is weakly supported, as this is based on a single geometric criterion without functional validation.
- The assertion that the MEOW approach is "a novel and enabling tool" for studying allostery is not fully established, as the manuscript does not demonstrate clear advantages over existing methods for this specific application.
- The biological significance of the observed differences in information fields between apo and holo states is not experimentally validated, and the connection to the allosteric mechanism remains speculative.