## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, data availability) as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No supplementary figures, tables, or datasets were available for direct inspection.
- **Shared manuscript claim summary** The authors report the biochemical and structural characterisation of the S. cerevisiae Mer3 helicase, including its oligomeric state, its interaction with Mlh1-Mlh2, and a newly identified interaction with Top3-Rmi1. They propose that Mer3 competes with Sgs1 for Top3-Rmi1 binding and protects Dmc1-mediated D-loops from Sgs1/STR-mediated dissolution, thereby promoting meiotic crossover formation.
- **Visible evidence base** Text descriptions of results from mass photometry, SEC-MALS, EMSA, pull-down assays, MST, XL-MS, AlphaFold2 modelling, and in vitro D-loop assays. Reference to supplementary figures (S1-S7) and tables (S1-S3) whose content was not provided.
- **Missing materials affecting confidence** All primary data figures (main and supplementary), raw MS data, AlphaFold2 model quality metrics (PAE plots, pLDDT scores), detailed quantification of D-loop assays, and full experimental replicates. Without these, quantitative claims and statistical robustness cannot be independently verified.

## Reviewer
- **Overall assessment** This manuscript presents a substantial body of biochemical work characterising Mer3 and its interactions, with the novel finding of a Mer3-Top3-Rmi1 complex and a proposed functional role in protecting meiotic D-loops. The combination of AlphaFold2 modelling with XL-MS validation is a modern and appropriate approach. However, the central mechanistic claim—that Mer3 protects D-loops specifically through competition with Sgs1 for Top3-Rmi1 binding—is not fully established by the data as described. The observation that Mer3 also protects D-loops from Sgs1 alone, and the lack of a direct demonstration that Mer3 displaces Sgs1 from the STR complex in a functional assay, leaves alternative explanations open. The manuscript would be strengthened by additional experiments and by clearer presentation of quantitative data.
- **Who would be interested in the results, and why** Researchers in the fields of meiosis, homologous recombination, DNA repair, and helicase biology. The work provides new molecular details on a conserved ZMM protein and its potential role in crossover assurance, which is of broad interest to those studying chromosome segregation and genome stability. The methodological approach (integrating AlphaFold2 with XL-MS) may also interest structural biologists.
- **Major strengths**
  1. The identification and validation of a novel interaction between Mer3 and Top3-Rmi1, supported by multiple independent methods (Y2H, pull-down, XL-MS, MST).
  2. The use of AlphaFold2 modelling combined with XL-MS to provide structural context for interaction interfaces, a powerful and timely approach.
  3. The demonstration that Mer3 can protect Dmc1-mediated D-loops from Sgs1/STR-mediated disassembly in a reconstituted system, providing a plausible biochemical basis for its in vivo role.
  4. The finding that Mer3 phosphorylation status influences its competition with Sgs1, adding a regulatory layer to the proposed mechanism.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental support for central claim
  - **Claim pointer** "Mer3 inhibits D-loop disassembly mediated by the Sgs1/Top3/Rmi1 complex and Sgs1 alone" and "Mer3 is able to disrupt Top3-Rmi1 binding to Sgs1BLM helicase in a phospho-dependent manner."
  - **Evidence pointer** Results sections "Mer3 and Sgs1 compete with each other for binding to the Top3/Rmi1 complex" and "Mer3 inhibits D-loop disassembly mediated by the Sgs1/Top3/Rmi1 complex and Sgs1 alone"; Figures 5 and 6 (not directly viewable).
  - **Concern** The manuscript proposes that Mer3 protects D-loops by competing with Sgs1 for Top3-Rmi1 binding. However, the data also show that Mer3 protects D-loops from Sgs1 alone (without Top3-Rmi1). This suggests that competition for Top3-Rmi1 is not the sole or primary mechanism of protection. The authors do not adequately address this discrepancy. If Mer3 can inhibit Sgs1 activity directly, the relevance of the Top3-Rmi1 competition to the protective mechanism is unclear. A direct test of whether the Mer3-Top3-Rmi1 interaction is required for D-loop protection (e.g., using a Mer3 mutant that cannot bind Top3-Rmi1) is needed.
  - **Why it matters** The central mechanistic claim of the paper is that Mer3 protects D-loops by disrupting the STR complex. If protection occurs even in the absence of Top3-Rmi1, the proposed mechanism is incomplete or incorrect, and the significance of the newly identified interaction is diminished.
  - **Resolution test** Provide D-loop protection assays using a Mer3 mutant specifically defective in Top3-Rmi1 binding (but not D-loop binding). If protection is lost, the competition mechanism is supported. If protection is retained, the authors must revise their model to account for a direct effect of Mer3 on Sgs1.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Quantitative data and statistical analysis
  - **Claim pointer** "KD of 436 ± 122 nM" (Mer3-Mlh1/Mlh2) and "KD of 844 ± 148 nM" (Mer3-Top3/Rmi1) and "478 ± 205 nM" (Mer3-Top3/Rmi1, repeat).
  - **Evidence pointer** Results sections on MST; Figures 2G and 3F (not directly viewable).
  - **Concern** The manuscript reports dissociation constants with standard deviations but does not state the number of independent replicates (n) for each MST measurement, nor the statistical test used to compare different conditions. The reported errors are large (e.g., 478 ± 205 nM), which may indicate high variability between experiments. Without this information, the reliability of these quantitative binding affinities cannot be assessed.
  - **Why it matters** Quantitative binding affinities are a key part of the characterisation. If the measurements are not robust, the conclusions drawn from them (e.g., that Mer3 binds Top3-Rmi1 with lower affinity than Mlh1/Mlh2) are not reliable.
  - **Resolution test** State the number of independent replicates for each MST measurement and provide a statistical analysis (e.g., mean ± SEM, with individual data points shown). If variability is high, discuss potential sources and consider whether the conclusions are still supported.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Structural interpretation
  - **Claim pointer** "AlphaFold2 modelling and XL-MS we further characterise the previously described interaction with Mlh1–Mlh2" and "we suggest that Mer3 binds to the same cleft on Top3/Rmi1 that is occupied by an N-terminal alpha-helix of Sgs1."
  - **Evidence pointer** Results sections on AlphaFold2 and XL-MS; Figures 1D-F, 2C-E, 3G-H, 5C (not directly viewable).
  - **Concern** The manuscript relies heavily on AlphaFold2 models to interpret XL-MS data and to propose specific binding interfaces. While this is a valid approach, the authors should be more cautious in their claims. The AlphaFold2 model of Mer3 is a prediction, and the XL-MS data, while supporting the general topology, may not have the resolution to definitively map interaction interfaces. The claim that Mer3 binds to the "same cleft" on Top3/Rmi1 as Sgs1 is based on modelling and cross-links, but this is not directly demonstrated experimentally (e.g., by mutagenesis of the predicted interface).
  - **Why it matters** Overinterpretation of low-resolution structural data can lead to incorrect models that mislead the field. The specific claim about the binding site on Top3/Rmi1 is important for the proposed competition mechanism.
  - **Resolution test** Provide experimental validation of the proposed binding interface, for example by mutating key residues predicted to be at the interface and testing the effect on binding in pull-down or MST assays. Alternatively, soften the language to clearly state that the proposed interface is speculative.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of writing
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract, Introduction
  - **Issue** The abstract and introduction are dense and use jargon that may be difficult for non-specialists to follow. For example, the term "anti-crossover factor" is used without a clear definition, and the significance of the ZMM group is not fully explained for a general reader.
  - **Required correction** Briefly define key terms (e.g., ZMM, anti-crossover) and provide a clearer context for why the protection of meiotic recombination intermediates is important. Consider adding a sentence in the abstract that explains the broader significance of the work.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Experimental detail
  - **Affected element** Methods section
  - **Evidence pointer** Materials and Methods, "D-loop assay"
  - **Issue** The D-loop assay description lacks some details, such as the specific concentrations of Mer3 used in the titration, the exact time points for sampling, and how the "relative D-loop yield" was quantified. This makes it difficult to fully reproduce the experiments.
  - **Required correction** Provide a more detailed description of the D-loop assay, including a clear statement of the concentrations used, the time course, and the quantification method (e.g., phosphorimager analysis and how the percentage was calculated).
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results section
  - **Evidence pointer** Results, "Mer3 and Sgs1 compete with each other for binding to the Top3/Rmi1 complex"
  - **Issue** The competition experiments are described qualitatively ("reproducible competition"). It would be helpful to show a quantification of the competition, e.g., a graph showing the amount of Mer3 bound to Top3-Rmi1 as a function of increasing Sgs1 concentration.
  - **Required correction** Add a quantitative representation of the competition data, such as a bar chart or dose-response curve, to support the qualitative description.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion
  - **Evidence pointer** Discussion
  - **Issue** The discussion does not explicitly address the limitations of the study, such as the use of truncated protein fragments, the lack of in vivo validation of the proposed mechanism, and the potential for artefacts in the reconstituted system.
  - **Required correction** Add a paragraph in the Discussion acknowledging these limitations and suggesting future experiments to address them.

## Risk / unsupported claims
- The claim that Mer3 "protects D-loops" from Sgs1/STR-mediated disassembly is supported by the D-loop assay data, but the mechanism (competition for Top3-Rmi1 vs. direct inhibition of Sgs1) is not fully resolved.
- The claim that Mer3 phosphorylation regulates its competition with Sgs1 is based on in vitro experiments with a limited number of phosphorylation sites; the in vivo relevance is not established.
- The proposed structural model of the Mer3-Top3-Rmi1 interaction and the specific binding interface on Top3-Rmi1 is speculative and not directly validated by mutagenesis.
- The statement that Mer3 is a monomer at low concentrations and a dimer at high concentrations is based on mass photometry and SEC-MALS, but the in vivo oligomeric state is not addressed.
- The claim that the Mer3-Mlh1/Mlh2 interaction is "compatible" with Mer3-Top3-Rmi1 binding is based on pull-down experiments, but the stoichiometry and cooperativity of the proposed 5-subunit complex are not quantitatively defined.