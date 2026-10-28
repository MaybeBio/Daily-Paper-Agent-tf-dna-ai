## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary information description
- **Assessment boundary** Technical soundness, reproducibility, and validity of claims regarding TetR- and LacI-dependent expression systems in Gluconobacter oxydans
- **Shared manuscript claim summary** The authors report that a pBBR1MCS-5-based TetR-Ptet system provides extremely tight, highly inducible, and tunable gene expression in G. oxydans, with induction ratios exceeding 3500-fold, while a LacI-PlacUV5 system is leaky and tunable only up to 40-fold. Computational modeling suggests pH-dependent differences in DNA binding between LacI and TetR may explain the observed leakiness.
- **Visible evidence base** Figures 1-6, Tables 1, supplementary figures S1-S7, supplementary text S1 and S2
- **Missing materials affecting confidence** Supplementary figures and text were not provided in full; raw fluorescence data, statistical analysis details, and complete computational modeling parameters are not fully accessible

## Reviewer

- **Overall assessment** This manuscript presents a systematic and practical evaluation of inducible expression systems for G. oxydans, a biotechnologically relevant organism. The work is technically sound in its core experimental design, and the finding that TetR-Ptet outperforms LacI-PlacUV5 in this host is useful for the community. However, the mechanistic interpretation regarding pH-dependent DNA binding is speculative and not directly supported by experimental data. The study is incremental in nature, building on prior work from the same group, and the novelty is moderate. The practical value is clear, but the scientific depth is limited by the absence of direct biochemical validation of the proposed mechanism.

- **Who would be interested in the results, and why** Researchers working on genetic tools for non-model bacteria, particularly acetic acid bacteria, will find this work directly useful. Those engineering G. oxydans for industrial biotransformations will benefit from the characterization of a tightly regulated expression system. The comparison between TetR and LacI systems and the observed differences in leakiness may also interest synthetic biologists studying heterologous regulatory elements across bacterial hosts. The computational modeling component may appeal to those interested in pH effects on protein-DNA interactions, though the speculative nature limits its impact.

- **Major strengths**
  1. Systematic comparison of TetR-Ptet and LacI-PlacUV5 systems under identical backbone conditions, allowing direct and fair evaluation.
  2. Demonstration of extremely low basal expression and high induction ratios for TetR-Ptet, which is a significant practical improvement for G. oxydans.
  3. Inclusion of population-level analysis via flow cytometry, confirming homogeneity of induction response.
  4. Careful control experiments examining the influence of terminators and plasmid backbones on expression performance.
  5. The pH-dependent modeling provides a testable hypothesis for the observed differences between TetR and LacI systems.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim support
- **Claim pointer** The authors claim that computational modeling suggests decreased DNA binding of LacI at pH below 6, which they propose as a possible cause of the leakiness of LacI-dependent systems in G. oxydans.
- **Evidence pointer** Figure 6, Supplementary Text S1 and S2
- **Concern** The computational modeling is presented as a central explanatory framework for the observed biological differences, yet the evidence is entirely in silico. The HADDOCK scores are qualitative indicators and the authors themselves note that TetR cluster scores lie within standard deviation of each other across pH conditions. The trend lines in Figure 6 are based on "similar docking poses" but the criteria for similarity are not defined. No experimental validation of pH-dependent binding is provided, and the connection between medium pH, intracellular pH, and the observed leakiness is inferred rather than demonstrated. The claim that "decreased DNA binding of LacI when pH decreases" is a mechanistic conclusion that cannot be supported by docking simulations alone.
- **Why it matters** The manuscript uses this modeling to explain a key biological observation and to generalize the findings to other acetic acid bacteria. If the mechanistic claim is not well supported, the broader implications regarding pH effects on regulator function in AAB are weakened. The practical finding of TetR-Ptet being superior remains valid, but the explanatory framework is not.
- **Resolution test** Provide direct experimental evidence of pH-dependent LacI-DNA binding, such as electrophoretic mobility shift assays or surface plasmon resonance at different pH values. Alternatively, measure intracellular pH of G. oxydans under the growth conditions used and correlate with LacI repression efficiency. If experimental validation is not feasible, the modeling should be clearly framed as hypothesis-generating rather than explanatory.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative data completeness
- **Claim pointer** The authors report induction ratios of up to 3500-fold for TetR-Ptet and 40-fold for LacI-PlacUV5, and describe graded responses to inducer concentrations.
- **Evidence pointer** Figures 1, 4, 5
- **Concern** The induction ratios are calculated from fluorescence measurements, but the raw fluorescence values, background subtraction methods, and the exact time points used for ratio calculations are not fully specified. The authors state that fluorescence values not exceeding cell-free control signals were set to 1, but the threshold and handling of negative values are unclear. For the graded response data in Figure 1c, the inducer concentration range is given (10-400 ng/mL) but the number of replicates, error propagation, and statistical significance of differences between adjacent concentrations are not reported. The claim of "highly tunable" expression would be strengthened by a dose-response curve with statistical analysis.
- **Why it matters** The quantitative claims of induction ratios and tunability are central to the manuscript's practical recommendations. Without clear reporting of data processing and statistical treatment, readers cannot fully assess the robustness of these numbers or compare them with other systems.
- **Resolution test** Provide a detailed description of fluorescence data processing, including background subtraction, normalization, and the exact formula for induction ratio calculation. Include statistical analysis (e.g., ANOVA with post-hoc tests) for the dose-response data. Report the number of biological and technical replicates for each data point in all figures.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability claim
- **Claim pointer** The authors state that the TetR-Ptet system is "highly suitable for applications in G. oxydans and possibly in other AAB."
- **Evidence pointer** Discussion section
- **Concern** The claim of suitability for other acetic acid bacteria is speculative. The authors tested only G. oxydans 621H. They reference prior work showing leakiness of TetR-Ptet in Komagataeibacter rhaeticus, but attribute this to construct differences and potential pH effects without direct comparative experiments. The statement that the system may work in other AAB is not supported by data presented in this study.
- **Why it matters** The broader applicability claim extends the practical impact of the work. If unsupported, it may mislead researchers working with other AAB species into expecting similar performance without validation.
- **Resolution test** Either temper the claim to be explicitly limited to G. oxydans, or provide comparative data in at least one additional AAB species. If the latter is not feasible, clearly state that transferability to other AAB requires further testing.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Flow cytometry gating strategy
- **Evidence pointer** Figure 1d, 3b, 5f
- **Issue** The gating strategy is described in the methods, but the percentage of cells passing the gate is only reported for the pBBR1MCS-2 comparison. For the TetR-Ptet and LacI-PlacUV5 flow cytometry data, the gating statistics are not reported, making it difficult to assess whether the populations analyzed are representative.
- **Required correction** Report the percentage of events passing each gate for all flow cytometry experiments, or state that the gating was consistent across samples and provide representative gating plots in supplementary material.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 6
- **Evidence pointer** Figure 6
- **Issue** The figure shows HADDOCK scores for clusters at different pH values, but the number of clusters, the criteria for selecting the "five best-scoring clusters," and the method for identifying "similar docking poses" across pH conditions are not described in the figure legend or methods.
- **Required correction** Add a detailed description of the cluster selection and comparison methodology in the figure legend or supplementary text, including the RMSD threshold used for defining similar poses.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The authors mention that LacI-based systems were previously found to be leaky in G. oxydans (Condon et al. 1991), but do not discuss the specific construct or conditions used in that study. A more detailed comparison would help contextualize the current findings.
- **Required correction** Briefly describe the prior LacI-based system in G. oxydans, including the promoter, plasmid backbone, and reported leakiness, to allow readers to assess whether differences in construct design might explain the observed results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figures 1-5
- **Evidence pointer** Figures 1-5
- **Issue** The figure legends state the number of replicates, but error bars are not consistently defined. It is unclear whether they represent standard deviation, standard error, or confidence intervals.
- **Required correction** Clearly state in each figure legend what the error bars represent and whether the data points are individual measurements or means.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 must be addressed by either providing experimental validation of the pH-dependent binding claim or reframing the modeling as hypothesis-generating. The quantitative data reporting issues in R1-M2 should be resolved to allow proper evaluation of the induction ratio claims. The generalizability claim in R1-M3 should be tempered or supported with additional data.

- **Assessment against Nature-style criteria**
  - Originality: Moderate. The work applies known regulatory elements to a new host and provides a systematic comparison, but the conceptual approach is not novel. The pH-dependent modeling angle is somewhat original but not experimentally validated.
  - Scientific importance: Moderate. The practical value for G. oxydans engineering is clear, but the broader scientific insights are limited. The mechanistic explanation for LacI leakiness, if validated, would increase importance.
  - Interdisciplinary readership: Limited. The work is primarily of interest to microbiologists and biotechnologists working with acetic acid bacteria. The computational component may attract some biophysicists, but the speculative nature limits cross-disciplinary appeal.
  - Technical soundness: Generally sound in experimental design and execution, but the computational modeling component is not rigorously validated and the quantitative reporting is incomplete in places.
  - Readability for nonspecialists: The manuscript is clearly written and accessible to readers with basic molecular biology background. The key findings are summarized effectively in the abstract and key points.

- **Recommendation posture** Supportive if technical concerns are resolved. The core experimental findings regarding TetR-Ptet performance in G. oxydans are valuable and likely reproducible. However, the mechanistic claims regarding pH-dependent LacI binding must be either experimentally supported or substantially reframed. The quantitative reporting should be improved to allow full assessment of the induction ratio claims. Once these issues are addressed, the manuscript would be suitable for publication in a specialized microbiology or biotechnology journal.