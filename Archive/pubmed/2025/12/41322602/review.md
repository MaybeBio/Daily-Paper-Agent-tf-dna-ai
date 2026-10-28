## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusions, experimental section) as provided
- **Assessment boundary** Scientific soundness, methodological rigor, internal consistency, and support of claims based solely on the supplied material
- **Shared manuscript claim summary** The authors report a computational–experimental pipeline that screened 13,142 natural compounds from the TCMSP database against the essential response regulator HsrA of Helicobacter pylori using molecular docking, followed by MD simulations and in vitro assays. They identify sesamolin (3) and coptisine (6) as candidate HsrA inhibitors, with sesamolin showing stronger binding affinity (KD = 17.08 nM), more potent anti-H. pylori activity (MIC 7 μg/mL), and broader regulatory effects on HsrA-linked genes compared to coptisine.
- **Visible evidence base** Abstract; Introduction; Results sections covering virtual screening, pocket identification, preliminary and extended MD simulations, MIC/MBC, time-kill kinetics, EMSA, SPR, RT-qPCR, chemotaxis, and SOD assays; Discussion; Conclusions; Experimental section
- **Missing materials affecting confidence** Figures and tables referenced throughout (Figures 1–6, Tables 1–3, Tables S1–S5) are not provided; raw MD trajectory data, docking scores for all 13,142 compounds, EMSA gel images, SPR sensorgrams, RT-qPCR raw data, and statistical outputs are not accessible; no information on compound purity verification beyond supplier claims; no cytotoxicity data

## Reviewer
- **Overall assessment** This manuscript presents a systematic and reasonably designed workflow combining virtual screening, MD simulations, and multiple in vitro assays to identify natural-product inhibitors of HsrA in H. pylori. The integration of computational predictions with experimental validation is commendable, and the identification of sesamolin as a candidate with sub-micromolar binding affinity and low MIC values is potentially interesting. However, the manuscript has several significant weaknesses that currently prevent the conclusions from being fully established. These include incomplete reporting of key data (figures and tables not visible), potential overinterpretation of MD simulation results, lack of direct evidence for the proposed mechanism of action, and insufficient discussion of the physiological relevance of the observed transcriptional changes. The claim that sesamolin acts specifically through HsrA binding to exert its anti-H. pylori effects is not fully supported by the evidence presented, as alternative mechanisms (e.g., membrane disruption, off-target effects) are not excluded.
- **Who would be interested in the results, and why** Researchers in the fields of antimicrobial drug discovery, natural product pharmacology, and H. pylori pathogenesis would find this work relevant. The study addresses the clinically important problem of antibiotic resistance in H. pylori and explores a relatively underexploited target (HsrA) using a combined computational and experimental approach. The identification of a food-derived compound (sesamolin) with anti-H. pylori activity may also interest investigators studying dietary interventions for gastrointestinal infections.
- **Major strengths** The study addresses a clinically relevant problem (antibiotic resistance in H. pylori) and targets a promising but underexplored essential transcription factor. The workflow is logical and integrates multiple complementary techniques, from virtual screening through MD simulations to a range of in vitro assays. The use of a natural product database (TCMSP) is appropriate for the goal of identifying accessible, potentially safe lead compounds. The comparative analysis of two hit compounds (sesamolin and coptisine) with differential activities provides internal controls and strengthens the structure-activity interpretation. The inclusion of multiple functional assays (MIC, MBC, time-kill, chemotaxis, SOD) provides a broad phenotypic characterization.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing data), R1-M2 (mechanism of action), R1-M3 (MD interpretation), R1-M4 (dose-response and specificity), R1-M5 (statistical reporting)
- **Assessment against Nature-style criteria** Originality: Moderate. The application of virtual screening against HsrA is not entirely novel, as the authors themselves cite prior work by González et al. and Antoniciello et al. using similar approaches. The novelty lies primarily in the use of a natural product database and the specific identification of sesamolin, which is a modest incremental advance. Scientific importance: Moderate. The clinical problem is important, but the study does not provide definitive evidence that HsrA inhibition is the mechanism of action, nor does it demonstrate in vivo efficacy. The potential impact is therefore limited at this stage. Interdisciplinary readership: Limited. The work is primarily of interest to specialists in antimicrobial drug discovery and H. pylori biology. The computational methods are standard, and the biological validation is preliminary. Technical soundness: The experimental design is generally sound, but the lack of accessible data (figures, tables) and the incomplete statistical reporting prevent full assessment. The MD simulation methodology appears appropriate, but the interpretation of results is somewhat overreaching. Readability for nonspecialists: The manuscript is written in a clear and logical manner, with adequate background information. However, the density of technical detail in the results section may be challenging for readers outside the immediate field.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential merit, but the conclusions regarding sesamolin as a specific HsrA-targeting anti-H. pylori agent require additional experimental support and more complete data reporting. Major revisions are needed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability and reporting
- **Claim pointer** The manuscript claims identification of 12 candidate HsrA inhibitors from virtual screening and subsequent selection of sesamolin (3) and coptisine (6) based on MD stability and MIC values.
- **Evidence pointer** Figures 1–6, Tables 1–3, Tables S1–S5 (location not provided)
- **Concern** All figures and tables referenced in the Results section are missing from the provided material. This includes the docking scores for the 12 selected compounds (Table 1), pocket identification data (Figure 1A, Table S2), MD simulation trajectories (Figures 2, 3, S2, S3), MIC/MBC data (Table 2), EMSA results (Figure 4), SPR sensorgrams and KD values (Figure 4C,D), RT-qPCR data (Figure 5), chemotaxis results (Figure 6C), and SOD activity data (Figure 6D). Without access to these primary data, the claims cannot be independently evaluated.
- **Why it matters** The core conclusions of the manuscript rest on these data. The selection of compounds 3 and 6, the comparison of their binding stabilities, the demonstration of HsrA-DNA binding inhibition, and the transcriptional effects all depend on the figures and tables that are not visible. Peer review requires access to primary evidence.
- **Resolution test** Provide all figures and tables with appropriate resolution and legends. Ensure that all data points, error bars, statistical annotations, and experimental conditions are clearly labeled and legible.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanism of action
- **Claim pointer** The manuscript claims that sesamolin (3) exerts its anti-H. pylori effects by binding to HsrA and regulating HsrA-linked genes, thereby inhibiting bacterial growth.
- **Evidence pointer** EMSA (Figure 4A,B), SPR (Figure 4C,D), RT-qPCR (Figure 5), Discussion section
- **Concern** The evidence presented does not establish a causal link between HsrA binding and the observed antibacterial activity. While EMSA shows that both compounds can inhibit HsrA-DNA complex formation at millimolar concentrations, and SPR demonstrates binding affinity, the manuscript does not demonstrate that this binding is responsible for growth inhibition. The concentrations used in EMSA (0.05–1 mM) are far above the MIC values (7 μg/mL for sesamolin, approximately 20 μM), raising questions about the physiological relevance of the EMSA results. Furthermore, the RT-qPCR data show transcriptional changes, but the manuscript does not establish that these changes are a direct consequence of HsrA inhibition rather than a secondary effect of general cellular stress or toxicity. The possibility that sesamolin acts through additional or alternative targets (e.g., membrane disruption, inhibition of other essential proteins) is not addressed.
- **Why it matters** The central claim of the manuscript is that sesamolin is an HsrA-targeting agent. Without direct evidence linking HsrA binding to the antibacterial phenotype, the mechanistic conclusion is not supported. This distinction is critical for the potential development of sesamolin as a specific anti-H. pylori therapeutic.
- **Resolution test** Perform genetic or biochemical experiments to establish causality. For example, overexpress HsrA in H. pylori and test whether this confers resistance to sesamolin; generate HsrA point mutants that are defective in DNA binding and test whether sesamolin still inhibits growth; or use a reporter system where HsrA activity can be monitored in live cells. Additionally, test whether sesamolin affects the growth of other bacteria lacking HsrA homologs to assess specificity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of MD simulation results
- **Claim pointer** The manuscript claims that compound 3 exhibits more stable binding to HsrA than compound 6 based on RMSD, RMSF, hydrogen bonding, and binding free energy calculations from MD simulations.
- **Evidence pointer** Figures 2, 3, Table 3, Table S5 (location not provided)
- **Concern** The MD simulation results are used to support the selection of compounds 3 and 6 and to argue for the superior binding of compound 3. However, several issues need clarification. First, the manuscript reports that compound 3 formed an average of 0.57 H-bonds, while compound 6 formed 0.03. These values are very low and suggest that hydrogen bonding is not a major contributor to binding for either compound. The manuscript also states that van der Waals interactions are the primary contributors to binding, which is consistent with hydrophobic interactions but raises questions about the specificity of binding. Second, the RMSD values reported for compound 3 (0.893 ± 0.042 nm) are relatively high, indicating significant conformational changes in the protein upon ligand binding. The manuscript does not discuss whether these changes are physiologically relevant or whether they represent simulation artifacts. Third, the binding free energy calculations are based on MM-GBSA and MM-PBSA methods, which are known to have limitations in accuracy. The manuscript does not provide convergence criteria or error estimates for these calculations. Finally, the manuscript does not report the initial docking poses or the specific binding sites for compounds 3 and 6, making it difficult to assess whether the MD simulations are sampling relevant conformations.
- **Why it matters** The MD simulation results are a key component of the compound selection process and the comparative analysis of compounds 3 and 6. If the simulations are not well-converged or the results are overinterpreted, the selection of these compounds and the conclusions about their relative binding affinities may not be reliable.
- **Resolution test** Provide more detailed MD simulation data, including RMSD and RMSF plots for all systems, hydrogen bond occupancy analysis, and binding free energy decomposition with error estimates. Discuss the convergence of the simulations and the significance of the observed conformational changes. Consider performing additional replicates or longer simulations to confirm the stability of the binding modes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Dose-response and specificity
- **Claim pointer** The manuscript claims that sesamolin (3) exhibits potent anti-H. pylori activity with MIC and MBC values of 7 and 10 μg/mL, respectively, and that this activity is superior to that of coptisine (6).
- **Evidence pointer** Table 2, Figure 3 (time-kill kinetics) (location not provided)
- **Concern** The MIC and MBC values are reported for a single H. pylori strain (ATCC 43504, metronidazole-resistant). The manuscript does not provide data on the activity of sesamolin against other H. pylori strains, including antibiotic-sensitive strains, which would be important to assess the generalizability of the findings. Additionally, the manuscript does not report the activity of sesamolin against other bacterial species, which would help assess its specificity for H. pylori. The time-kill kinetics data are described but not shown, and the manuscript does not provide quantitative comparisons between compounds 3 and 6 at equivalent concentrations. The statement that sesamolin exhibited "more rapid anti-H. pylori activity" than coptisine is not supported by the data presented in the text.
- **Why it matters** The clinical relevance of a potential anti-H. pylori agent depends on its activity against diverse clinical isolates and its selectivity for H. pylori over other commensal bacteria. The lack of such data limits the significance of the findings.
- **Resolution test** Test sesamolin against a panel of H. pylori strains, including antibiotic-sensitive and resistant clinical isolates. Test sesamolin against a panel of other Gram-negative and Gram-positive bacteria to assess selectivity. Provide the time-kill kinetics data in a figure with quantitative comparisons at matched concentrations.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical analysis and reproducibility
- **Claim pointer** The manuscript claims statistically significant differences in gene expression and SOD activity between treatment groups based on RT-qPCR and SOD assays.
- **Evidence pointer** Figure 5, Figure 6D, Statistical Analysis section
- **Concern** The Statistical Analysis section states that one-way ANOVA with Tukey's post hoc test was used for RT-qPCR data, but no statistical details are provided for the SOD assay, chemotaxis assay, or time-kill kinetics. The number of biological replicates is not clearly stated for each experiment. The manuscript states that experiments were "independently repeated twice" with three technical replicates, but this is insufficient to establish statistical significance for most biological assays. The lack of effect size measures and confidence intervals further limits the interpretation of the results.
- **Why it matters** The conclusions about the differential effects of compounds 3 and 6 on gene expression and SOD activity depend on the statistical robustness of the data. Inadequate statistical reporting prevents the reader from assessing the reliability of these findings.
- **Resolution test** Provide complete statistical details for all experiments, including the number of biological and technical replicates, the statistical tests used, and the resulting p-values or confidence intervals. Consider increasing the number of biological replicates to at least three independent experiments.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of compound selection criteria
- **Affected element** Results section, Virtual Screening
- **Evidence pointer** Table 1, Table S1 (location not provided)
- **Issue** The manuscript states that 12 compounds were selected from 1,743 compounds with docking scores below -7.0 kcal/mol, but the specific criteria for selecting these 12 from the 1,743 are not clearly described. The text mentions "commercially available, relatively inexpensive" as criteria, but the threshold for "relatively inexpensive" is not defined.
- **Required correction** Clearly state the full selection criteria, including any additional filters applied after docking (e.g., availability, cost thresholds, chemical diversity considerations). Provide a flowchart or decision tree for the selection process.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency of hydrogen bond data
- **Affected element** Results section, Preliminary MD Simulation
- **Evidence pointer** Table 2, Figure 2C (location not provided)
- **Issue** The text states that no H-bonds were observed for compound 6 in the preliminary 50 ns simulations, but the extended 200 ns simulations report an average of 0.03 H-bonds for compound 6. This discrepancy is not explained.
- **Required correction** Clarify whether the preliminary simulations used different hydrogen bond detection criteria than the extended simulations, or whether the difference reflects the longer sampling time. Provide consistent reporting of hydrogen bond data across all simulations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Solubility discussion
- **Affected element** Discussion section
- **Issue** The manuscript attributes the weaker EMSA effect of compound 3 to its poor aqueous solubility, but no solubility measurements are provided. The claim that compound 6 showed a slightly stronger EMSA effect "may be attributed to differences in their solubility" is speculative without supporting data.
- **Required correction** Provide experimental solubility data for compounds 3 and 6 in the relevant buffers, or temper the statement to acknowledge that the solubility difference is a hypothesis rather than a demonstrated explanation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality and labeling
- **Affected element** All figures (location not provided)
- **Issue** The figures are not available for review, but based on the text descriptions, it is unclear whether all figures include appropriate error bars, statistical annotations, and axis labels. The manuscript should ensure that all figures are self-contained and legible.
- **Required correction** Ensure all figures include clear axis labels, units, error bars, and statistical annotations. Provide figure legends that fully describe the experimental conditions and the number of replicates.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Issue** The manuscript uses both "minimum inhibitory concentration (MIC)" and "minimum bactericidal concentration (MBC)" but does not define the units consistently. The MIC values are reported in μg/mL, but the concentrations used in EMSA are reported in mM, making direct comparisons difficult.
- **Required correction** Use consistent units throughout the manuscript, or clearly state the conversions used. Consider reporting all concentrations in molar units for consistency.

## Risk / unsupported claims
- The claim that sesamolin (3) is a "potential anti-H. pylori agent" that acts "by binding with HsrA and regulating the related key genes" is not fully supported, as the causal link between HsrA binding and antibacterial activity is not established.
- The claim that this is "the first study to screen for HsrA inhibitors using the TCMSP natural-product database" is plausible but cannot be fully verified from the provided material.
- The claim that compound 3 "exhibits potent anti-H. pylori activity" is based on data from a single strain and requires validation against a broader panel of strains.
- The statement that compound 3 showed "broader transcriptional modulation of the HsrA regulon" compared to compound 6 is based on RT-qPCR data that are not fully presented or statistically validated.
- The claim that sesamolin has "favorable drug-like properties" is based on computational predictions (AlogP, OB, DL) and requires experimental validation.
- The physiological relevance of the EMSA results is questionable given the high concentrations (0.05–1 mM) used relative to the MIC values.
- The manuscript does not address potential off-target effects of sesamolin or coptisine, which could contribute to the observed antibacterial activity.