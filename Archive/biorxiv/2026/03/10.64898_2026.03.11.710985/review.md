## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, author contributions, acknowledgments)
- **Assessment boundary** Scientific and technical evaluation of the proposed essential dynamics-based elastic network model (edENM) for nucleic acids and protein-nucleic acid complexes, including its parameterization, validation, and integration into the eBDIMS framework
- **Shared manuscript claim summary** The authors introduce edENM, an essential dynamics-refined elastic network model for DNA, RNA, and protein-nucleic acid complexes, parameterized using molecular dynamics simulations. They claim improved agreement with experimental conformational ensembles compared to uniform-spring ENMs, more collective normal modes, and successful integration into the eBDIMS framework for simulating large-scale conformational transitions in systems up to MDa scale.
- **Visible evidence base** Abstract, Introduction, Materials and Methods (parameterization workflow, MD dataset description, experimental ensemble dataset, NMA and comparison metrics, eBDIMS implementation), Results (parameterization and testing for nucleic acids and protein-nucleic acid complexes, eBDIMS applications), Discussion, Data Availability
- **Missing materials affecting confidence** Supplementary figures and tables (Supplementary Figs. 1-20, Supplementary Tables 1-14) are referenced but not provided; specific MD trajectory identifiers and simulation parameters are not fully detailed; quantitative results for the eBDIMS simulations (e.g., RMSD convergence values, pathway statistics) are described qualitatively; statistical test details for significance claims are not fully specified

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially valuable contribution to the field of coarse-grained modeling of nucleic acids and protein-nucleic acid complexes. The core idea of extending an ED-based parameterization approach, previously validated for proteins, to nucleic acids is scientifically sound and addresses a genuine gap in the field. The integration with the eBDIMS framework is a logical and useful extension. However, the manuscript as presented has several significant limitations that prevent full assessment of the claims. The most critical issues are: (1) the absence of the supplementary material, which contains the majority of the quantitative validation data; (2) the lack of a clear description of the MD training dataset composition and quality; (3) the qualitative nature of the eBDIMS application results; and (4) the absence of a direct comparison with other existing nucleic acid ENMs beyond the uniform-spring model. The statistical significance of the improvements over the uniform-spring model is marginal for the O_max metric, and the practical impact of the improvements needs to be more clearly demonstrated. The writing is generally clear, but the results section would benefit from more quantitative detail in the main text.

- **Who would be interested in the results, and why** Computational biophysicists and structural biologists working on nucleic acid dynamics, particularly those interested in coarse-grained modeling approaches. Researchers studying chromatin organization, ribosome assembly, and RNA-protein complexes would find the eBDIMS applications relevant. Developers of elastic network models and normal mode analysis tools would be interested in the methodological advances. The work may also appeal to the broader community interested in integrative modeling approaches that combine experimental data with computational simulation.

- **Major strengths** (1) The manuscript addresses a genuine gap in the field: the relative lack of optimized ENMs for nucleic acids compared to proteins. (2) The parameterization approach, based on MD-derived force constants, is methodologically sound and extends a previously validated protein framework. (3) The unified parameterization for both DNA and RNA is a practical advantage. (4) The integration with eBDIMS extends the utility of the model beyond harmonic analysis to anharmonic transitions. (5) The validation across multiple experimental modalities (NMR, cryo-EM, X-ray) is commendable. (6) The authors identify and discuss the issue of unphysical local deformations in standard ENMs, which is an important practical problem.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that the edENM parameterization was performed using "a diverse set of Molecular Dynamics simulations" and that the model was validated against "experimental ensembles and conformational changes."
- **Evidence pointer** Methods section "Dataset of Molecular Dynamics (MD) simulations"; Supplementary Tables 1-4
- **Concern** The supplementary material, which contains the detailed composition of the MD training and testing datasets, the list of experimental ensembles, and the full quantitative results, is not provided. Without this information, it is impossible to assess the diversity and representativeness of the training set, the appropriateness of the testing set, or the robustness of the reported improvements. The claim of "diverse" MD simulations cannot be verified.
- **Why it matters** The validity of the parameterization and the generalizability of the model depend critically on the composition and quality of the training and testing datasets. If the training set is biased toward particular structural contexts or force fields, the resulting parameters may not transfer well. The validation claims are central to the manuscript's contribution.
- **Resolution test** Provide the supplementary material with full details of the MD datasets (PDB IDs, force fields, simulation lengths, water models, etc.), the experimental ensemble lists, and the complete quantitative results for all comparisons. The main text should summarize the key dataset characteristics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "the vibrational modes of the new edENM show good agreement with NMR data and experimental ensembles, while avoiding the unrealistic and localized deformability of previous ENM parameterizations."
- **Evidence pointer** Results section "Parametrization and testing of the nucleic acid edENM"; Figures 4-5; Supplementary Figs. 9-11; Supplementary Table 6
- **Concern** The reported improvement in O_max over the uniform-spring ENM is approximately +1.5% and is stated to be not statistically significant (p-value ~0.33). The significant improvement is only observed for RMSIP (+5%, p < 0.0005). The manuscript does not adequately discuss the practical implications of this distinction. If the primary metric of individual mode overlap is not significantly improved, the claim of "good agreement" needs to be more carefully qualified. Additionally, the specific cases where edENM shows dramatic improvement (e.g., the 2PCV example with 64% to 93% improvement) appear to be selected examples, and the manuscript does not provide a systematic analysis of when and why such improvements occur.
- **Why it matters** The central claim of the manuscript is that the ED-based parameterization improves the accuracy of ENM predictions. If the improvement is marginal or inconsistent, the practical value of the new model is questionable. Understanding the conditions under which the model provides significant advantages is essential for users to decide when to employ it.
- **Resolution test** Provide a more detailed analysis of the distribution of O_max and RMSIP improvements across the testing set, including cases where edENM performs worse. Discuss the practical significance of the RMSIP improvement and provide guidance on when the model is expected to provide the most benefit.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "we are now able to explore functional motions in large protein-nucleic acid complexes such as chromatin subunits and ribosomes" and describes eBDIMS simulations for four systems.
- **Evidence pointer** Results section "Exploring conformational transitions with eBDIMS"; Figure 10
- **Concern** The eBDIMS application results are described only qualitatively. For the four systems presented, there are no quantitative metrics reported in the main text (e.g., final RMSD values, pathway lengths, computational costs, comparison with experimental intermediates). The claim that the simulations "converged to the target states with final RMSDs below 1Å" is made for the RNA system, but no such quantitative information is provided for the larger complexes. The figure descriptions suggest structural representations, but without quantitative validation, the reliability of the generated pathways cannot be assessed.
- **Why it matters** The demonstration of the method's applicability to large complexes is a key contribution of the manuscript. Without quantitative assessment of the quality of the generated pathways and intermediates, the practical utility of the approach for these systems is not established.
- **Resolution test** Provide quantitative results for all four eBDIMS applications, including final RMSD values, comparison with known experimental intermediates where available, and computational performance metrics. If space is limited, provide these in supplementary material with clear summaries in the main text.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with existing methods
- **Claim pointer** The manuscript claims that the proposed model "improves the correlation between the computed and experimental conformational changes with respect to traditional ENM parameterizations."
- **Evidence pointer** Results section "Parametrization and testing of the nucleic acid edENM"; Discussion
- **Concern** The comparison is limited to the uniform-spring ENM from Pinamonti et al. (2015). The manuscript does not compare against other existing nucleic acid ENMs or parameterization strategies, such as those that use different node representations (e.g., one bead per nucleotide vs. three beads), different spring constant assignment schemes, or models that incorporate sequence-dependence. The discussion mentions other approaches but does not provide quantitative comparisons.
- **Why it matters** To establish the value of the proposed model, it is important to demonstrate its advantages over a broader range of existing approaches. The field has seen multiple ENM variants for nucleic acids, and users need to understand the relative merits of the proposed model.
- **Resolution test** Add comparisons with at least one or two additional ENM variants for nucleic acids, or provide a clear justification for why the uniform-spring model is the most appropriate baseline.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The manuscript states that "All codes and data needed to reproduce the results shown in this work are freely available on GitHub."
- **Evidence pointer** Data Availability section
- **Concern** While the GitHub repository is mentioned, the manuscript does not describe what exactly is included (e.g., parameter files, example scripts, input/output data for the validation tests, the eBDIMS implementation). The URL is provided, but the content and usability of the repository cannot be assessed from the manuscript. Additionally, the specific MD simulation data used for parameterization are not deposited or described in sufficient detail for reproduction.
- **Why it matters** Reproducibility is a core requirement for methodological contributions. Without clear documentation of what is provided and how to use it, the practical impact of the work is limited.
- **Resolution test** Describe the contents of the GitHub repository in the Data Availability section, including the types of files provided, the software dependencies, and instructions for reproducing the key results. Consider depositing the MD simulation data or providing clear pointers to the original sources.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Parametrization workflow"
- **Evidence pointer** Equation (1) and surrounding text
- **Issue** The equation for the apparent force constants is referenced but not explicitly shown in the text provided. The description of the parameterization procedure would benefit from a clearer step-by-step explanation, particularly regarding how the MD-derived force constants are mapped to the ENM spring constants.
- **Required correction** Ensure the equation is displayed and clearly explained. Provide a more detailed step-by-step description of the parameterization workflow, including how the random search refinement is performed and how the optimal parameters are selected.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Parametrization and testing of the nucleic acid edENM"
- **Evidence pointer** Supplementary Table 6
- **Issue** The statistical tests used to compute p-values for the comparisons between edENM and ENM are not described. The manuscript reports p-values but does not specify the test used (e.g., paired t-test, Wilcoxon signed-rank test) or whether multiple testing corrections were applied.
- **Required correction** Specify the statistical tests used for each comparison and whether corrections for multiple testing were applied. Provide this information in the Methods section or in the figure/table legends.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Parametrization and testing of the protein-nucleic acid edENM"
- **Evidence pointer** Supplementary Tables 8-9
- **Issue** The results for the protein-nucleic acid parameterization are presented with less detail than the nucleic acid-only results. The manuscript states that edENM performs better than ENM and edProt, but the specific improvements and their statistical significance are only in the supplementary material.
- **Required correction** Provide a brief summary of the key quantitative results for the protein-nucleic acid testing in the main text, including the magnitude of improvements and their statistical significance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Exploring conformational transitions with eBDIMS"
- **Evidence pointer** Figure 10
- **Issue** The description of the eBDIMS simulations for the telomeric trinucleosome and pre-40S ribosomal subunit lacks detail on the simulation setup (e.g., number of simulations, computational cost, choice of starting structures).
- **Required correction** Provide brief details on the simulation setup for each system, including the number of independent simulations performed, the computational resources required, and the criteria for determining convergence.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Methods section "Parametrization workflow"
- **Evidence pointer** "The performance of yhis optimized edENM was compared"
- **Issue** There is a typographical error: "yhis" should be "this".
- **Required correction** Correct the typographical error.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations focuses on data availability and structural resolution but does not address potential limitations of the MD-based parameterization itself, such as force field dependence, the choice of MD simulation conditions, or the representativeness of the training set for the diversity of nucleic acid structures in the PDB.
- **Required correction** Add a brief discussion of the potential limitations of the MD-based parameterization approach, including force field dependence and the generalizability of the parameters to nucleic acid structures not represented in the training set.

- **Technical failings that need to be addressed before the case is established** R1-M1 (supplementary data missing), R1-M2 (marginal statistical significance of O_max improvement), R1-M3 (qualitative eBDIMS results). These are the primary technical issues that prevent full assessment of the manuscript's claims.

- **Assessment against Nature-style criteria** 
  - Originality: The work is original in its application of ED-based parameterization to nucleic acids and protein-nucleic acid complexes. While the approach extends prior work on proteins, the extension to nucleic acids with a unified parameter set is a novel contribution. The integration with eBDIMS for large complexes is also original.
  - Scientific importance: The work addresses a real need in the field, as nucleic acid ENMs are less developed than protein ENMs. The potential to model large chromatin and ribosome complexes is scientifically important. However, the demonstrated improvements over existing methods are modest, and the practical impact needs to be more clearly established.
  - Interdisciplinary readership: The work is primarily of interest to computational biophysicists and structural biologists. The applications to chromatin and ribosomes may attract a broader readership, but the technical nature of the methods limits the interdisciplinary appeal.
  - Technical soundness: The methodology is generally sound, but the absence of supplementary data and the marginal statistical significance of some results prevent full assessment. The eBDIMS applications lack quantitative validation.
  - Readability for nonspecialists: The manuscript is clearly written and accessible to readers with a background in computational structural biology. The introduction and discussion provide appropriate context. However, the methods section assumes familiarity with ENM and NMA concepts.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is valuable and the methodology is sound, but the manuscript requires substantial revision to address the missing supplementary data, provide more quantitative results for the eBDIMS applications, and clarify the statistical significance and practical implications of the improvements. The authors should also consider broadening the comparison with existing methods to strengthen the case for the proposed model.