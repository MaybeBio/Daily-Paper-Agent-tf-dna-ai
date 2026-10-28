## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, author contributions, acknowledgements, footnotes)
- **Assessment boundary** Scientific content, methodological soundness, and internal consistency of the reported simulation study. No external replication or experimental validation was performed for this review.
- **Shared manuscript claim summary** The authors use coarse-grained LASSI simulations to argue that the spatial patterning of N-protein interaction motifs along the SARS-CoV-2 genome, specifically the concentration of phase-separation-promoting elements at the 5ʹ and 3ʹ ends, is sufficient for single-genome packaging, compaction, and cyclization, and that this arrangement is necessary for cyclization. They further propose that dispersed or clustered phase-separating elements can enhance packaging metrics and that the model generalizes to other viruses and cellular ribonucleoprotein bodies.
- **Visible evidence base** Abstract, Introduction, Methods (LASSI parameterization, simulation protocols), Results (phase behavior of N-protein with 5ʹ and FE RNA; whole-genome simulations with packaging, compaction, cyclization metrics; spatial patterning mutants; optimized design), Discussion, Conclusion, Author Contributions, Acknowledgements, Footnotes. Figures and tables referenced but not provided in the submitted material.
- **Missing materials affecting confidence** All figures (Fig 1-6), supplementary figures (Fig S1-S9), and tables (Tables 1-2) are referenced but not included. Simulation parameter values, energy values, and quantitative results are therefore not directly verifiable. The manuscript text alone does not provide sufficient quantitative detail to independently assess the robustness of the reported findings.

## Reviewer
- **Overall assessment** This manuscript presents a computationally tractable coarse-grained model to address a biologically important question: how SARS-CoV-2 selectively packages its large genome. The conceptual framing is clear and the use of LASSI is appropriate for the stated goal. The authors make a reasonable effort to connect their simulation parameters to prior experimental observations, particularly their own work on N-protein phase separation. However, the absence of all figures, tables, and quantitative parameter values in the provided material severely limits the ability to evaluate the technical soundness of the simulations, the validity of the metrics used, and the strength of the conclusions. The central claims, particularly the necessity of 5ʹ/3ʹ localization for cyclization and the optimality of the proposed "optimized" design, rest on simulation outputs that cannot be inspected. The manuscript is well-written and the logical flow is coherent, but the evidence base as presented is incomplete.
- **Who would be interested in the results, and why** Virologists studying coronavirus assembly and packaging mechanisms would be the primary audience. Researchers interested in the physical chemistry of RNA-protein phase separation, particularly in the context of long viral genomes, would also find the modeling approach relevant. Additionally, computational biologists developing coarse-grained models for nucleic acid-protein systems may be interested in the methodological extensions to LASSI described here. The potential generalization to cellular bodies such as paraspeckles broadens the appeal to cell biologists studying ribonucleoprotein granule assembly.
- **Major strengths** 1. The manuscript addresses a significant and unresolved question in coronavirus biology, namely the mechanism of selective genome packaging. 2. The use of a coarse-grained simulation approach grounded in prior experimental characterization of N-protein-RNA interactions is a logical and potentially powerful strategy. 3. The authors explicitly consider multiple packaging metrics (single-genome packaging, compaction, cyclization) and systematically explore spatial patterning variants, which is a thoughtful approach. 4. The discussion of the biophysical interpretation of different binding modes and the "boomerang" phase boundary shape demonstrates conceptual depth. 5. The writing is clear and accessible, with a logical progression from parameterization to whole-genome simulations to mutant analysis.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative data), R1-M2 (unverifiable metrics), R1-M3 (parameter sensitivity), R1-M4 (generalization claim).
- **Assessment against Nature-style criteria**  
  *Originality*: The application of coarse-grained phase separation modeling to viral genome packaging is not entirely novel, as the authors themselves cite prior work by Cubuk et al. on SARS-CoV-2 N-protein. However, the specific focus on spatial patterning of interaction motifs along a full-length genome and the systematic exploration of patterning variants does represent a distinct contribution. The originality is moderate.  
  *Scientific importance*: The question of how SARS-CoV-2 packages its genome is of high importance, given the ongoing pandemic and the need to understand viral assembly mechanisms. If the model predictions are robust, they could inform future experimental studies. However, the current manuscript is purely computational and lacks experimental validation, which limits its immediate impact. The importance is conditional on the validity of the model.  
  *Interdisciplinary readership*: The topic bridges virology, biophysics, and computational biology. The writing is accessible to nonspecialists in each field, and the conceptual framing is clear. However, the lack of quantitative detail and figures would make it difficult for a broad readership to fully appreciate the findings. The interdisciplinary appeal is present but not fully realized in the submitted material.  
  *Technical soundness*: This is the weakest area based on the provided material. The simulation methodology is described in principle, but the absence of parameter values, figures, and quantitative results makes it impossible to assess whether the simulations are correctly implemented, whether the metrics are well-defined, or whether the conclusions are robust. The technical soundness cannot be established from the supplied text.  
  *Readability for nonspecialists*: The manuscript is well-written and the logical structure is clear. The authors make an effort to explain the biological context and the significance of their findings. However, the heavy reliance on simulation jargon and the absence of visual aids would make it challenging for a nonspecialist to fully grasp the results. The readability is good but not excellent.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an important question and the conceptual framework is promising, but the absence of all figures, tables, and quantitative parameter values prevents a rigorous evaluation of the technical soundness and the validity of the central claims. The authors should be invited to resubmit a complete version with all supporting materials, after which a full assessment can be made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that the native spatial patterning of phase-separation-promoting elements at the 5ʹ and 3ʹ ends of the SARS-CoV-2 genome is sufficient for single-genome packaging and compaction, and necessary for cyclization, based on whole-genome simulations.
- **Evidence pointer** Results section, "Whole genome simulations reveal effects of phase separation on single genome packaging, genome compaction, and genome cyclization"; Figures 3-6 referenced but not provided
- **Concern** The central quantitative results of this study are presented exclusively in figures and tables that are not included in the submitted material. The text describes trends and qualitative outcomes (e.g., "up to 40-50% of genomes are cyclized", "robust compaction occurs in the concave region") but provides no numerical values, error bars, or statistical analyses. Without access to the actual simulation outputs, phase diagrams, and metric definitions, it is impossible to verify the claims or assess the magnitude and significance of the reported effects. This is a blocking issue because the entire case for the conclusions rests on these unviewable data.
- **Why it matters** The conclusions regarding the sufficiency and necessity of specific spatial patterning for packaging, compaction, and cyclization are the core contribution of the manuscript. If these data are not available for scrutiny, the scientific case cannot be evaluated. The reader cannot determine whether the observed effects are robust, whether the metrics are appropriately defined, or whether the simulation results are statistically meaningful.
- **Resolution test** Provide all figures (Fig 1-6) and supplementary figures (Fig S1-S9) with full axis labels, legends, and quantitative values. Include numerical data for all reported metrics (packaging efficiency, compaction ratio, cyclization percentage) with appropriate statistical measures (e.g., standard deviation, confidence intervals) across independent simulation runs. Ensure that all parameter values used in the simulations are listed in the main text or tables.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The authors claim that their coarse-grained model "recapitulates known phase behavior and binding patterns of N-protein with FE and 5ʹ end RNA" based on qualitative agreement with prior experimental results.
- **Evidence pointer** Results section, "Simulations recapitulate known phase behavior and binding patterns of N-protein with FE and 5ʹ end RNA"; Figures 1-2 referenced but not provided
- **Concern** The validation of the model against experimental data is described only in qualitative terms. The text states that the simulations "report a similar distinct pattern of protein interactions" and that the phase behavior is "consistent with" prior work, but no quantitative comparison is shown. The specific experimental data from reference (11) are not reproduced or overlaid with simulation results. The criteria for "agreement" are not defined. This is a blocking issue because the credibility of the entire simulation framework depends on its ability to faithfully represent the real N-protein-RNA system.
- **Why it matters** If the model cannot be shown to quantitatively reproduce known experimental observations, then the predictions about spatial patterning and packaging metrics are built on an unvalidated foundation. The reader cannot assess whether the model is a reliable tool for the questions being asked.
- **Resolution test** Provide a quantitative comparison between simulation results and experimental data from reference (11), such as binding curves, phase boundaries, or interaction stoichiometries. Define explicit criteria for what constitutes "agreement" (e.g., within a certain percentage or statistical equivalence). Show the comparison in a figure with both simulation and experimental data plotted together.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Parameter sensitivity
- **Claim pointer** The authors state that they "performed extensive parameter sweeps" and that the most sensitive interactions are the isotropic binding between N-proteins and the isotropic binding of N-protein with 5ʹ end RNA.
- **Evidence pointer** Results section, "Simulations recapitulate known phase behavior and binding patterns of N-protein with FE and 5ʹ end RNA"; Supplementary Figures S2-S4, S7-S8 referenced but not provided
- **Concern** The parameter sweeps are mentioned but the results are not shown in the provided material. The text identifies the most sensitive parameters but does not report the range of values tested, the resulting changes in phase behavior, or the criteria for determining sensitivity. Without this information, it is impossible to assess whether the model's predictions are robust to parameter variation or whether the conclusions depend on finely tuned parameter choices. This is a blocking issue because the generality of the findings cannot be established.
- **Why it matters** Coarse-grained models are only useful if their predictions are robust to reasonable parameter uncertainty. If the conclusions change dramatically with small parameter variations, the model's relevance to the biological system is questionable. The reader needs to see the sensitivity analysis to judge the reliability of the results.
- **Resolution test** Provide the full parameter sweep results in supplementary figures, including the range of parameters tested, the resulting phase diagrams, and a clear description of how sensitivity was quantified. Show that the qualitative conclusions (sufficiency of 5ʹ/3ʹ patterning, necessity for cyclization) hold across a reasonable range of parameter values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors hypothesize that their model "should be generalizable to multiple viruses as well as cellular organelles like paraspeckles."
- **Evidence pointer** Discussion section, "Generalization to other viruses and systems with long RNAs or DNA"
- **Concern** The generalization claim is speculative and not supported by any additional simulations or analyses. The authors draw analogies to other systems, such as paraspeckles and the NEAT1 lncRNA, but do not test whether their model would produce similar predictions for those systems. The claim is presented as a hypothesis, which is acceptable, but the discussion does not provide a concrete framework for how such generalization would be tested. This is a non-blocking concern because it is clearly framed as speculation, but it weakens the broader impact of the manuscript.
- **Why it matters** The potential applicability to other viruses and cellular bodies is a significant part of the claimed significance. Without any preliminary evidence or a clear proposal for testing, this claim remains an untested assertion. The reader cannot evaluate whether the model has the generality the authors suggest.
- **Resolution test** Either provide preliminary simulation results for a second system (e.g., a different virus or a simplified model of a paraspeckle-like structure) or clearly articulate a testable set of predictions that would distinguish the model's applicability to other systems. Alternatively, soften the claim to reflect the speculative nature more explicitly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, LASSI model parameterization
- **Evidence pointer** Methods section, "LASSI model parameterization"; Tables 1-2 referenced but not provided
- **Issue** The methods section describes the simulation setup but the actual parameter values (e.g., interaction energies, temperature range, concentration ranges) are not listed in the text. The tables are referenced but not included in the submitted material.
- **Required correction** Include the parameter values directly in the text or ensure the tables are provided in the final submission. This will allow readers to understand the simulation setup without needing to access supplementary materials.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section, "Whole genome simulations reveal effects of phase separation on single genome packaging, genome compaction, and genome cyclization"
- **Evidence pointer** Results section, paragraph on "single genome packaging"
- **Issue** The term "single genome packaging" is used throughout but is not explicitly defined. It is implied to mean one genome per cluster, but the metric is described as "the number of gRNA-containing clusters divided by the total number of gRNA chains." This definition should be stated clearly when the metric is first introduced.
- **Required correction** Define "single genome packaging" explicitly when the metric is first introduced, and clarify how the metric distinguishes between clusters containing one versus multiple genomes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, "Whole genome simulations reveal effects of phase separation on single genome packaging, genome compaction, and genome cyclization"
- **Evidence pointer** Results section, paragraphs on packaging, compaction, and cyclization
- **Issue** The text reports qualitative trends (e.g., "robust", "enhanced", "more efficient") without providing numerical values or statistical measures. For a simulation study, it is standard practice to report mean values with standard deviations or confidence intervals across independent runs.
- **Required correction** Add quantitative values for all reported metrics, including means and measures of variability, for each condition (WT, mutants, optimized design). This will strengthen the claims and allow readers to assess the reliability of the findings.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Discussion section, "Compatibility with the single packaging signal model"
- **Evidence pointer** Discussion section, paragraph on Cubuk et al.
- **Issue** The discussion of the Cubuk et al. model is brief and does not clearly articulate the differences and similarities between the two models beyond the valence argument. A more detailed comparison would help readers understand the novelty of the current approach.
- **Required correction** Expand the comparison with Cubuk et al. to include a more detailed discussion of model assumptions, parameter choices, and predictions. This will clarify the specific contribution of the current work.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Abstract, Statement of significance
- **Evidence pointer** Abstract, "Statement of significance"
- **Issue** The statement of significance is written in a somewhat general manner and does not clearly state what the specific findings are. It mentions that the model "informs future in silico experiments" but does not summarize the key results.
- **Required correction** Revise the statement of significance to include a brief summary of the main findings (e.g., the necessity of 5ʹ/3ʹ patterning for cyclization) and their implications for understanding viral packaging.

## Risk / unsupported claims
- The claim that the native spatial patterning of phase-separation-promoting elements at the 5ʹ and 3ʹ ends is "necessary for genome cyclization" is unsupported in the provided text because the quantitative results from Figure 3E and Figure 5D are not available for inspection.
- The claim that the "optimized" gRNA design enhances all packaging metrics relative to WT is unsupported because the data from Figure 6 are not provided.
- The claim that the model "should be generalizable to multiple viruses as well as cellular organelles like paraspeckles" is speculative and not supported by any simulation or analysis in the provided material.
- The claim that the simulations "recapitulate known phase behavior and binding patterns" is only qualitatively supported by the text; no quantitative comparison with experimental data is shown.
- The parameter sweep results described in the text are not visible, so the claim that the identified interactions are the "most sensitive" cannot be evaluated.