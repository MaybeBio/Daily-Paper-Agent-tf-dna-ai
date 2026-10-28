## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific claims, methodological soundness, and evidence consistency as presented in the supplied text. No external validation performed.
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations to show that BPTF PHD finger and PHD-linker-bromodomain constructs bind histone H3 tails within full nucleosomes, displace H3 from DNA, promote compensatory H4-DNA contacts, reduce overall histone-DNA hydrogen bonding, and adopt more compact conformations when nucleosome-bound compared to peptide-bound or free states.
- **Visible evidence base** Results sections with quantitative values (contact counts, binding energies, RMSF, RMSD, radius of gyration), figures referenced (Figures 1-9, S1-S19), tables referenced (Tables 1-2, S1-S5), methods descriptions for system construction, simulation protocols, and analysis procedures.
- **Missing materials affecting confidence** Figures and tables themselves are not provided in the supplied text. Supplementary figures and tables are referenced but not included. Raw trajectory data and analysis scripts are stated to be available online but were not inspected. No experimental validation data are presented.

## Reviewer
- **Overall assessment** The manuscript presents a systematic computational study of BPTF reader domain interactions with nucleosomes, addressing an important gap between peptide-based and full-nucleosome studies. The simulation design is reasonable, with multiple replicates and appropriate force fields. The central claims regarding H3 tail displacement, compensatory H4 binding, and context-dependent conformational changes are internally consistent with the reported numbers. However, the absence of the actual figures and tables in the supplied material limits verification of several quantitative claims. The interpretation that these changes may facilitate chromatin remodeling is speculative but appropriately framed. The work is technically sound in its core methodology, though the biological significance would be strengthened by clearer connection to experimental observables.

- **Who would be interested in the results, and why** Researchers studying chromatin structure and dynamics, particularly those interested in reader domain function, histone tail behavior, and nucleosome stability. Computational biophysicists working on protein-DNA interactions and multidomain protein conformational dynamics would also find the methodological approach relevant. The findings may inform experimental studies of BPTF and related chromatin factors, especially in the context of designing experiments that account for full nucleosomal context rather than isolated peptides.

- **Major strengths**
  1. Addresses a relevant gap by comparing peptide-bound and full-nucleosome-bound states of a multidomain chromatin reader.
  2. Uses multiple independent simulations (five replicates per system) with a total of 35 microseconds of sampling, which is substantial for all-atom nucleosome simulations.
  3. Employs multiple complementary analysis methods (contacts, RMSF, MM/GBSA, geometric measures) to characterize binding effects.
  4. Reports both favorable and unfavorable energetic contributions, providing a balanced view of binding drivers.
  5. Data availability statement is thorough, with inputs, scripts, and processed data deposited.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence verification
- **Claim pointer** The manuscript reports specific quantitative values for contact counts, binding energies, RMSF changes, and conformational measures across multiple systems.
- **Evidence pointer** Figures 1-9, Tables 1-2, Supplementary Figures S1-S19, Supplementary Tables S1-S5 (location not provided in supplied text)
- **Concern** The supplied material includes only the manuscript text without the actual figures, tables, or supplementary data. While the text reports numerical values, the ability to verify the accuracy of these numbers, assess the quality of the data presentation, or evaluate whether the figures support the stated conclusions is not possible from the provided material. This is particularly important for claims involving error bars, statistical significance, and visual representations of conformational ensembles.
- **Why it matters** The core scientific claims depend on quantitative comparisons between systems. Without access to the actual data visualizations and tables, the validity of the reported differences cannot be independently assessed. This is essential for establishing that the observed effects are robust and not artifacts of specific analysis choices.
- **Resolution test** Provide the full manuscript with all figures and tables included, or make the supplementary material available for inspection. The reviewer should be able to see the actual distributions, error bars, and statistical comparisons to confirm the reported values and conclusions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The manuscript states that the first 300 nanoseconds of each simulation were considered equilibration time based on RMSD data and visual inspection of H3 tail collapse.
- **Evidence pointer** Methods section, "Molecular dynamics simulations" subsection; Results section, first paragraph (location not provided)
- **Concern** The determination of equilibration time is described qualitatively. The criteria for deciding that 300 nanoseconds is sufficient are not specified in quantitative terms. Different observables may equilibrate on different timescales, and the choice of equilibration cutoff can affect all subsequent analyses. The manuscript does not report whether convergence was assessed for the specific quantities used in the main conclusions (e.g., contact counts, binding energies, conformational distributions).
- **Why it matters** If the equilibration period is too short or too long, the reported values could be biased. The validity of the comparative claims between systems depends on all systems being analyzed in equivalent, converged regimes. Without a rigorous convergence assessment, the quantitative differences reported may not be reliable.
- **Resolution test** Provide quantitative convergence criteria, such as block averaging or split-half analysis, demonstrating that the reported observables are stable over the analyzed trajectory portions. Show that the conclusions are robust to reasonable variations in the equilibration cutoff.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation and generalizability
- **Claim pointer** The manuscript concludes that "reader engagement modulates nucleosome structure through both direct H3 tail interactions and propagated effects on histone dynamics, providing insight into the allosteric influence of reader domains within chromatin."
- **Evidence pointer** Discussion section, final paragraph (location not provided)
- **Concern** The claim of allosteric influence is based on observed changes in H4 and H2A contacts and hydrogen bonding. However, the manuscript does not clearly distinguish between direct steric or electrostatic effects of reader binding versus true allosteric propagation through the nucleosome. The observed changes could result from local restructuring near the binding site rather than long-range communication. Additionally, the relevance to chromatin remodeling is inferred but not directly tested.
- **Why it matters** The broader significance of the work depends on whether the observed effects represent a general mechanism relevant to chromatin biology. If the effects are purely local and system-specific, the implications for understanding BPTF function in vivo would be more limited.
- **Resolution test** Provide additional analysis that distinguishes local from propagated effects, such as distance-dependent contact maps or perturbation response analyses. Alternatively, temper the language to more precisely describe the observed changes without overinterpreting their mechanistic basis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Force field and model limitations
- **Claim pointer** The manuscript uses the ff19SB force field with BSC1 DNA parameters and the TIP4P-D water model, and reports quantitative binding energies from MM/GBSA calculations.
- **Evidence pointer** Methods section, "System construction" and "Simulation Analyses" subsections (location not provided)
- **Concern** The manuscript does not discuss the known limitations of the chosen force field combination for nucleic acid-protein interactions. The TIP4P-D water model is not mentioned in the methods text provided, though it is referenced in the abstract context. MM/GBSA is an approximate method, and the manuscript acknowledges this but does not quantify the expected uncertainty. The reported binding energy differences (e.g., -64.6 to -40.6 kcal/mol for H3-DNA) are large, but the error bars on these estimates are not reported.
- **Why it matters** The quantitative conclusions about binding energetics and the relative contributions of different interaction types depend on the accuracy of the force field and the MM/GBSA approximation. If the force field biases certain interactions, the reported trends could be artifacts.
- **Resolution test** Add a discussion of force field limitations and validation against available experimental data where possible. Report uncertainties on MM/GBSA estimates, such as standard errors across replicates or across trajectory blocks.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "System construction" subsection
- **Evidence pointer** Methods section (location not provided)
- **Issue** The description of how the H3 tails were remodeled to extend away from the nucleosome core is brief. The specific Modeller settings or restraints used are not described, and it is unclear whether the remodeling procedure could introduce bias in the initial conformations.
- **Required correction** Provide additional detail on the remodeling protocol, including any restraints applied and how the resulting conformations were validated.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "Reader Binding Alters H3 Tail Conformation and Dynamics" subsection
- **Evidence pointer** Results section, first subsection (location not provided)
- **Issue** The manuscript reports that H3 tail collapse occurred in both reader-bound and unbound systems, but does not compare the timescales or extent of collapse between these conditions in detail. The statement that collapse occurred on a "similar timescale" is vague.
- **Required correction** Provide quantitative comparison of collapse kinetics or final collapsed states between conditions, or clarify why this comparison is not essential for the conclusions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, "Electrostatic Repulsion and Van der Waals Attraction Govern BPTF-Nucleosome Binding" subsection
- **Evidence pointer** Results section, fourth subsection; Table 2 (location not provided)
- **Issue** The manuscript reports mean values for binding energies and contact counts but does not consistently report standard deviations or standard errors across the five replicates. This makes it difficult to assess the significance of differences between systems.
- **Required correction** Add measures of variability (e.g., standard error of the mean) for all reported quantitative values, and indicate whether differences between systems are statistically significant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion section
- **Evidence pointer** Discussion section (location not provided)
- **Issue** The term "allosteric influence" is used without a precise definition in the context of nucleosome dynamics. This could be interpreted in multiple ways.
- **Required correction** Define what is meant by allosteric in this context, or use more specific language describing the observed propagated effects.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Simulation Analyses" subsection
- **Evidence pointer** Methods section (location not provided)
- **Issue** The description of the angle measurement between the PHD finger and bromodomain is incomplete. The specific atoms or vectors used to define the angle are not fully specified, and Figure S1 is referenced but not available in the supplied material.
- **Required correction** Provide a complete definition of the angle measurement in the text, including the specific atoms or residue ranges used.

## Risk / unsupported claims
- The claim that "nucleosome engagement inducing compaction of the multidomain structure" is supported by reported RG values, but the actual distributions and statistical significance cannot be verified without the figures.
- The statement that "strong Van der Waals interactions with the H3 tail stabilize binding" is supported by MM/GBSA values, but the method's known limitations and the lack of reported uncertainties make the quantitative claim difficult to assess.
- The suggestion that observed changes "may facilitate chromatin remodeling" is presented as a hypothesis, which is appropriate, but it is not directly tested in this study.
- The claim that "the full dynamics of readers may not be fully captured in studies with short peptides" is a reasonable inference from the data but is not directly demonstrated by a head-to-head comparison of peptide versus nucleosome binding dynamics for the same construct under identical conditions.
- The statement that "electrostatic repulsion limiting direct reader-DNA contacts" is inferred from distance measurements and energy calculations, but the causal relationship is not directly established.