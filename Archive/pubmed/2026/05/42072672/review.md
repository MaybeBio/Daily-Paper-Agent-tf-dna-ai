## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusions) as provided
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the supplied text; no supplementary files, figures, or raw data were available for inspection
- **Shared manuscript claim summary** The authors report that thirty 2-methyl-quinazolinone hydroxamic acid derivatives (free OH, OEt, and OBn series) bind to CT DNA, exhibit DNA photocleavage under UV-A and visible light, generate singlet oxygen, and that selected nitro-substituted derivatives show photo-induced cytotoxicity in melanoma cell lines, supporting their potential as photodynamic therapy agents
- **Visible evidence base** Abstract; Sections 1 (Introduction), 2 (Materials and Methods), 3 (Results), 4 (Conclusions); Tables 1-4 referenced; Figures 3-16 referenced; Supporting Information referenced but not provided
- **Missing materials affecting confidence** Supporting Information (Parts S1-S7, Figures S1-S8); raw UV-vis, viscosity, fluorescence, gel electrophoresis, and cell viability data; full figure images; compound characterization data; statistical analysis details; supplementary docking results

## Reviewer
- **Overall assessment** The manuscript presents a systematic evaluation of a focused compound library with a clear workflow from DNA binding to photocleavage, mechanistic studies, and cellular phototoxicity. The finding that O-alkyl and O-benzyl derivatives outperform their free hydroxamic acid counterparts is interesting and potentially significant. However, the evidence as presented is incomplete in several critical areas. The absence of the Supporting Information, which contains essential data (full gel images, raw spectra, statistical details, docking figures), prevents full verification of the claims. The cell viability data are presented only qualitatively with no dose-response curves, IC50 values, or statistical comparisons. The mechanistic studies are limited to two compounds with conflicting results that are not fully reconciled. The molecular docking methodology contains inconsistencies (rigid docking with Lamarckian genetic algorithm is not standard for AutoDock Vina). The manuscript would benefit from clearer presentation of quantitative data and more rigorous statistical analysis.
- **Who would be interested in the results, and why** Researchers in photodynamic therapy, medicinal chemistry, and nucleic acid chemistry would find interest. The demonstration of nanomolar-range DNA photocleavage activity and the structure-activity relationships for quinazolinone-based photosensitizers are relevant to those developing new PDT agents. The comparative analysis of free versus protected hydroxamic acids provides useful design principles for this compound class.
- **Major strengths** Systematic evaluation of a 30-compound library with consistent methodology across three series; integration of multiple complementary techniques (UV-vis, viscosity, fluorescence, gel electrophoresis, docking, cell-based assays); identification of clear structure-activity relationships, particularly the superiority of O-alkyl and O-benzyl derivatives; demonstration of nanomolar-range activity for nitro-substituted compounds; inclusion of singlet oxygen quantum yield measurements to support mechanistic claims
- **Major Concerns** See detailed items below
- **Minor Comments** See detailed items below
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing Supporting Information), R1-M2 (inadequate cell viability data), R1-M3 (docking methodology inconsistency), R1-M4 (incomplete mechanistic reconciliation)
- **Assessment against Nature-style criteria** Originality: Moderate. While the specific compound series is new, the general approach of evaluating DNA photocleavage and singlet oxygen generation for PDT candidates is well established. The finding that protected hydroxamic acids outperform free ones is a useful contribution but not paradigm-shifting. Scientific importance: Moderate. The results are of interest to the PDT and medicinal chemistry communities but do not address a fundamental question or open a new direction. Interdisciplinary readership: Limited. The work sits primarily within medicinal chemistry and photobiology; the broader significance for fields beyond these is not clearly articulated. Technical soundness: Partially established. The core techniques are appropriate, but the missing Supporting Information and methodological inconsistencies prevent full assessment. Readability for nonspecialists: Acceptable. The manuscript is generally clearly written, though some sections assume familiarity with photochemical and DNA-binding terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially valuable, but the manuscript in its current form does not provide sufficient verifiable evidence to fully establish the claims. The authors must provide the Supporting Information, quantitative cell viability data with statistical analysis, corrected docking methodology, and a more complete reconciliation of the mechanistic results.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims specific DNA binding constants, photocleavage percentages, singlet oxygen quantum yields, and cell viability reductions, all of which depend on data presented in the Supporting Information.
- **Evidence pointer** Supporting Information Parts S1-S7, Figures S1-S8; Tables 1-4
- **Concern** The Supporting Information is referenced extensively throughout the manuscript but was not provided for review. This includes the detailed procedures and equations for DNA binding studies (Parts S1-S3), UV-vis spectra of all compounds (Part S4), all gel images and quantitative data (Part S5), singlet oxygen data (Figure S6), and docking figures (Part S7). Without these materials, the quantitative claims in the manuscript cannot be independently verified. The gel images are particularly critical for assessing photocleavage activity, and the raw spectra are necessary to evaluate the quality of the binding and singlet oxygen measurements.
- **Why it matters** The central claims of the manuscript, including the nanomolar-range activity of compounds 18, 19, 28, and 29, and the singlet oxygen quantum yields, rest entirely on data that the reviewer cannot access. Scientific claims must be verifiable from the provided evidence.
- **Resolution test** Provide the complete Supporting Information for review. Ensure all figures are legible, all quantitative data are presented with appropriate error bars and statistical analysis, and all methods are described in sufficient detail to be reproduced.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative data and statistical rigor
- **Claim pointer** The manuscript claims that compounds 18, 19, and 28 "reduced cell viability by approximately 50%" in melanoma cell lines at concentrations up to 10 μM.
- **Evidence pointer** Section 3.6, Figure 16
- **Concern** The cell viability results are presented only as qualitative descriptions ("reduced viability by approximately 50%") with no quantitative data shown in the text. No dose-response curves, IC50 values, standard deviations, or statistical significance values are provided. The figure is referenced but not shown. Additionally, the choice of concentrations (50 μM for most compounds, 10 μM for 28 and 29) is not systematically justified, and no dose-response relationship is established. The comparison between compounds is therefore difficult to assess.
- **Why it matters** The claim that these compounds are "promising candidates for the development of photodynamic therapy agents" depends critically on their photocytotoxicity. Without quantitative dose-response data and statistical analysis, the relative potency of the compounds and the significance of the findings cannot be evaluated. The field standard for cytotoxicity studies requires IC50 values or at minimum multiple concentrations with statistical comparison.
- **Resolution test** Provide full dose-response curves for all tested compounds in all three cell lines, with IC50 values (or % viability at specified concentrations) presented as mean ± SD from at least three independent experiments. Include statistical analysis (e.g., two-way ANOVA with appropriate post-hoc tests) comparing irradiated vs. dark conditions and between compounds. Clarify the rationale for concentration selection.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological consistency
- **Claim pointer** The molecular docking section states that "the rigid docking protocol and 100 runs of the Lamarckian genetic algorithm for searching ligand conformations were performed" using AutoDock Vina.
- **Evidence pointer** Section 2.5, Section 3.5, Table 4
- **Concern** AutoDock Vina does not use the Lamarckian genetic algorithm; this is a feature of AutoDock 4. The manuscript appears to conflate two different docking programs. Additionally, the statement "rigid docking protocol" is ambiguous, as it is unclear whether the ligand, the DNA, or both are treated as rigid. The grid box dimensions (60 x 80 x 114 with 0.375 Å spacing) are unusually large and would result in a very computationally expensive search, which is inconsistent with standard Vina usage. The level of theory for geometry optimization (B3LYP/6-31g* with LanL2DZ for iodine) is appropriate, but the docking methodology needs clarification.
- **Why it matters** The docking results are used to support the DNA binding and photocleavage findings. If the methodology is incorrect or inconsistently described, the docking results cannot be interpreted reliably. Reproducibility is a core requirement for computational studies.
- **Resolution test** Clarify which docking program was used for which step. If AutoDock 4 was used, describe the parameters appropriately. If Vina was used, remove the reference to the Lamarckian genetic algorithm. Specify what was treated as rigid and what was flexible. Justify the grid box dimensions and search space. Provide the exhaustiveness parameter if Vina was used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The manuscript states that "in the case of compound 18, a significant decrease in its biological activity was observed in the presence of argon, whereas for compound 8, no similarly distinct effects were detected" and that singlet oxygen measurements "verified these findings."
- **Evidence pointer** Section 3.3.2, Section 3.4, Table 3, Figure 10B
- **Concern** The mechanistic studies show that compound 8 has oxygen-independent photocleavage activity, while compound 18 is oxygen-dependent. However, the manuscript does not discuss what alternative mechanism might explain compound 8's activity under argon. The singlet oxygen quantum yield for compound 8 is reported as 0.157, which is low but not negligible, yet the argon experiment suggests minimal oxygen involvement. This apparent inconsistency is not addressed. Additionally, the manuscript does not discuss whether the observed photocleavage under argon could be due to direct electron transfer or hydrogen abstraction mechanisms, which would be relevant for understanding the compound's mode of action.
- **Why it matters** Understanding the mechanism of action is important for the rational design of improved photosensitizers. If compound 8 operates via an oxygen-independent pathway, this could be advantageous in hypoxic tumor environments, which is a clinically relevant consideration for PDT. The manuscript misses an opportunity to discuss this potentially important finding.
- **Resolution test** Provide a more detailed discussion of the mechanistic implications of the argon experiments. Address the apparent discrepancy between the singlet oxygen data and the oxygen-dependence results for compound 8. Consider whether additional experiments (e.g., using specific reactive oxygen species scavengers or different quenchers) would help clarify the mechanism.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Table 1
- **Evidence pointer** Section 3.2, Table 1
- **Issue** The Kb values are presented with standard deviations, but the number of replicates and the fitting procedure are not described in the main text. The statement "all compounds besides derivative 24 show relatively good binding constancies" is vague and not supported by specific criteria.
- **Required correction** Specify the number of independent measurements, the fitting procedure used, and the criteria for "good binding constancies." Consider providing a measure of goodness-of-fit for the Wolfe-Shimer plots.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 3.2
- **Evidence pointer** Section 3.2, Figure 3
- **Issue** The terms "hyperchromism" and "hypochromism" are used, but the direction of the spectral changes is not consistently described for each compound. Some compounds show hyperchromism while others show hypochromism, and the significance of this difference is not discussed.
- **Required correction** Clarify which compounds show hyperchromism versus hypochromism and discuss what this difference might indicate about the binding mode or the electronic properties of the compounds.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3
- **Issue** The DNA photocleavage experiments are described as using "UV-A and visible light irradiation," but the light sources, fluence rates, and irradiation times are not specified in the main text. The distance from the light source to the sample is also not given.
- **Required correction** Provide the specifications of the light sources, the fluence rate (mW/cm2), the total light dose, and the irradiation geometry. This information is essential for reproducibility and for comparing results across studies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Section 3.6
- **Evidence pointer** Section 3.6, Figure 16
- **Issue** The cell viability data are described qualitatively, and no statistical analysis is reported in the text. The number of independent experiments and replicates is not stated.
- **Required correction** Report the number of independent experiments, the number of technical replicates, and the statistical tests used. Present the data as mean ± SD or SEM with significance levels indicated.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 1
- **Evidence pointer** Section 1
- **Issue** The introduction mentions that "several benzyl and allyl hydroxamates (non-free HMAs) have been synthesized and found to exhibit antitubercular, anticancer and amyloid beta aggregation inhibition," but does not provide a critical comparison with the current work or explain how the present study advances beyond these prior findings.
- **Required correction** Strengthen the introduction by explicitly stating the novelty of the present work relative to prior studies on hydroxamate-containing compounds and quinazolinone derivatives.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Section 3.5, Table 4
- **Evidence pointer** Section 3.5, Table 4
- **Issue** The docking results are presented as binding energies, but the relationship between the calculated binding energies and the experimentally determined Kb values is not discussed quantitatively. For example, compound 28 has the highest Kb and the most negative binding energy, but the correlation across all 30 compounds is not examined.
- **Required correction** Consider adding a correlation analysis between the experimental Kb values and the calculated docking scores. If no correlation exists, discuss possible reasons (e.g., solvation effects, entropic contributions, or limitations of the docking approach).

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Compound characterization
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The manuscript states that compounds 1-30 were prepared following a previously described procedure, but no characterization data (NMR, HRMS, purity) are provided in the main text or referenced as available in the Supporting Information.
- **Required correction** Confirm that characterization data for all compounds are available in the Supporting Information and reference the specific section. If not, provide a summary table of key characterization data.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Experimental conditions
- **Affected element** Section 2.6
- **Evidence pointer** Section 2.6
- **Issue** The cell culture experiments use different concentrations for different compounds (50 μM for most, 10 μM for 28 and 29) due to solubility issues. This makes direct comparison of photocytotoxicity between compounds difficult.
- **Required correction** Discuss the limitations of using different concentrations and consider whether alternative formulations (e.g., different solvents, sonication) could allow testing at matched concentrations. If not, acknowledge this limitation explicitly in the discussion.

## Risk / unsupported claims
- The claim that compounds 18, 19, 28, and 29 exhibit photocleavage activity at "concentrations of 100 nM" is not fully supported by the data presented, as the gel images and quantitative analysis are only in the Supporting Information.
- The statement that "high singlet oxygen generation efficiencies" for compounds 18 and 28 place them "among the highly efficient photosensitizers, comparable to or exceeding many commonly used PDT reference compounds" is not supported by a direct comparison with reference photosensitizers under identical conditions in the provided text.
- The claim that "molecular docking studies provided further insight into the interactions between the compounds and DNA" is not fully supported, as the docking results are presented as binding energies without validation against the experimental binding data.
- The conclusion that "these 2-methylquinazolinone-based hydroxamic acid derivatives are promising candidates for the development of photodynamic therapy agents" is premature given the limited cell-based data (no selectivity index, no comparison with established PDT agents, no in vivo data).
- The statement that "all compounds besides derivative 24 show relatively good binding constancies" is vague and not supported by specific quantitative criteria.
- The mechanistic interpretation that oxygen is "essential" for activity is based on experiments with only two compounds (8 and 18), and the manuscript does not address the possibility of alternative mechanisms for compound 8.