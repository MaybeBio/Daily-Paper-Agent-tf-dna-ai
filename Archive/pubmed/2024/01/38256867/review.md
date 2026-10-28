## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and conclusions
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors identify small molecules (110FA and 102FA) that inhibit HIV-1 transcription in T cells and myeloid cells. They propose that 110FA disrupts Tat–TAR RNA interaction, while 102FA interferes with the Cyclin T1–Cdk9 interaction within P-TEFb. They further report chromatin remodeling changes at the HIV-1 LTR and significant transcription inhibition in primary PBMCs.
- **Visible evidence base** Figures 1–9 (referenced but not fully visible in the provided text), Supplementary Figures S1–S8, Supplementary Tables S1–S2, and methods sections 4.1–4.14
- **Missing materials affecting confidence** Actual figure images and full data panels are not provided; only figure legends and in-text descriptions are available. Raw numerical data, statistical outputs, and detailed experimental replicates are not accessible. This limits independent verification of quantitative claims.

## Reviewer
- **Overall assessment** The manuscript addresses a clinically relevant gap in HIV-1 therapy by targeting the Tat–TAR interaction, a viral-specific process. The identification of two small molecules with distinct mechanisms is potentially interesting. However, the evidence presented is incomplete in several key areas: the screening data are not fully shown, the molecular docking and simulation results are descriptive rather than quantitative, the pulldown and immunoprecipitation experiments lack dose-response and control details, and the ChIP data are presented without clear statistical treatment. The primary cell data are promising but limited to three donors. The mechanistic distinction between 110FA and 102FA is plausible but not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in antiviral drug development, particularly those focused on HIV-1 transcription and latency; structural biologists studying RNA–protein interactions; and clinicians interested in adjunct therapies to cART. The potential for targeting both TAR RNA and P-TEFb components may appeal to groups working on RNA-targeting therapeutics.
- **Major strengths** The study addresses an underexplored therapeutic target (HIV-1 transcription) with no current FDA-approved drugs. The use of both cell lines and primary cells adds translational relevance. The combination of experimental and computational approaches is commendable. The observation that different cell types respond differently to the same molecules is an important consideration for future therapeutic design.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (screening data not fully presented), R1-M2 (docking and simulation claims not quantitatively supported), R1-M3 (pulldown and immunoprecipitation lack controls and quantification), R1-M4 (ChIP data without statistical analysis), R1-M5 (primary cell data limited and incomplete)
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. Targeting Tat–TAR is not new, but the specific molecules and the proposed dual mechanism (RNA and protein targeting) add some novelty.  
  - Scientific importance: Moderate to high. HIV-1 transcription inhibitors could complement cART and address latency, a major clinical challenge.  
  - Interdisciplinary readership: Moderate. The work spans virology, medicinal chemistry, and computational biology, but the presentation is specialized.  
  - Technical soundness: Currently insufficient. Several key experiments lack controls, quantification, or statistical rigor.  
  - Readability for nonspecialists: Acceptable but could be improved. The introduction and discussion are accessible, but the results section assumes familiarity with HIV-1 transcription machinery and molecular dynamics terminology.
- **Recommendation posture** Currently not established from the provided evidence. The core claims are plausible but require additional experimental validation and clearer data presentation before the case is convincing.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence completeness  
- **Claim pointer** The authors claim that five molecules effectively inhibit viral transcription in myeloid and T cells without apparent toxicity.  
- **Evidence pointer** Figure 1, Section 2.1  
- **Concern** The screening results are described in text but the actual data in Figure 1 are not visible in the provided material. The claim of "statistically significant 2–5-fold decrease" and "5–10-fold" reductions cannot be independently assessed. Additionally, the criteria for selecting the five molecules from the larger panel are not described.  
- **Why it matters** The identification of active compounds is the foundation of the entire study. Without clear screening data, the reader cannot evaluate whether the selection was robust or whether the observed effects are specific.  
- **Resolution test** Provide the full screening data with individual data points, statistical tests used, and clear annotation of which molecules were selected and why. Include dose-response curves and toxicity data for all tested concentrations.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Computational validation  
- **Claim pointer** The authors state that molecular docking and simulation show 110FA binds stably in the TAR RNA pocket and that the TAR loop shifts toward Cyclin T1 upon binding.  
- **Evidence pointer** Figure 5, Section 2.5, Section 2.9, Supplementary Table S2  
- **Concern** The docking and simulation results are described qualitatively. No quantitative metrics such as binding free energies, RMSD values, or interaction energies are provided. The claim that 110FA is "pulled-out" toward Cyclin T1 is not supported by numerical data. The simulation methodology is described in Section 4.12, but the analysis of the trajectories is not presented in a way that allows verification.  
- **Why it matters** The proposed mechanism of action for 110FA relies heavily on these computational results. Without quantitative support, the mechanistic interpretation remains speculative.  
- **Resolution test** Provide binding free energy calculations, RMSD and RMSF plots, contact maps with numerical values, and a clear description of how the "pulled-out" position was determined. Include error estimates and replicate simulations.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Experimental validation  
- **Claim pointer** The biotinylated RNA pulldown assay shows that 110FA reduces Tat binding to TAR RNA by 65%, while 102FA does not affect Tat binding.  
- **Evidence pointer** Figure 4, Section 2.4, Supplementary Figures S4 and S5  
- **Concern** The pulldown assay is described, but the actual blots are not visible. The claim of 65% reduction is presented without error bars or replicate information. The dose-response experiment in Supplementary Figure S5 is mentioned but not shown. The negative controls (delta TAR and gamma TAR) are described, but the results for these controls are not presented in the text.  
- **Why it matters** This experiment is central to distinguishing the mechanisms of 110FA and 102FA. Without proper quantification and controls, the conclusion that 110FA disrupts Tat–TAR interaction is not firmly established.  
- **Resolution test** Show representative blots with all controls, provide densitometry data with standard deviations from at least three independent experiments, and include the full dose-response data for 110FA.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The ChIP assay results show significant changes in BAF200, BAF250, BRG1, HDAC1, RNAP II, and Src-1 occupancy at the HIV-1 LTR following treatment with 110FA and 102FA.  
- **Evidence pointer** Figure 7, Section 2.7  
- **Concern** The ChIP data are described in text, but the figure is not visible. The claims of "10–20-fold" and "5–16-fold" reductions are presented without statistical analysis. The number of biological replicates is not stated. The statement that p300 levels were "lower than the IgG control" is concerning, as this suggests a potential technical issue with the assay.  
- **Why it matters** The chromatin remodeling data are used to support the mechanism of action. Without statistical rigor, the conclusions about chromatin state changes are not reliable.  
- **Resolution test** Provide ChIP data with statistical analysis (e.g., t-tests or ANOVA), include the number of replicates, and address the p300 result relative to IgG control. Show representative data and full quantification.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Primary cell data  
- **Claim pointer** The authors claim significant transcription inhibition in PBMCs from three donors, with 89%, 57%, and 70% reduction in TAR RNA and 95%, 34%, and 2% reduction in env RNA.  
- **Evidence pointer** Figure 8, Section 2.8  
- **Concern** The primary cell data are presented for only three donors, and the variability is substantial, particularly for env RNA (2% to 95%). The experimental details for infection, treatment, and measurement are described in Section 4.1, but the figure is not visible. The claim of "significant" inhibition is not supported by statistical analysis in the text.  
- **Why it matters** Primary cell data are critical for translational relevance. The high variability and small sample size weaken the conclusion that 110FA is effective in primary cells.  
- **Resolution test** Provide individual donor data points, statistical analysis (e.g., paired t-tests), and a clear description of the infection efficiency and treatment protocol. Consider increasing the number of donors or providing a power analysis.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 2.3, Figure 3  
- **Evidence pointer** Figure 3, Section 2.3  
- **Issue** The text states that 110FA reduced all viral proteins in T cells, but the percentages for p24, Nef, and gp120 are only given for 110FA. The corresponding data for 102FA in MDMs are described qualitatively.  
- **Required correction** Provide the quantitative reduction percentages for 102FA in MDMs and include the densitometry data in the main text or clearly reference the supplementary figures.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Methodology  
- **Affected element** Section 4.8  
- **Evidence pointer** Section 4.8  
- **Issue** The pulldown assay description does not specify the concentration of 110FA used in the binding reaction, nor does it describe how the 65% reduction was calculated.  
- **Required correction** Specify the concentration of 110FA used, describe the quantification method, and state the number of replicates.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Section 2.5, Figure 5  
- **Evidence pointer** Figure 5, Section 2.5  
- **Issue** The statement that 110FA is in a "pulled-out" position is ambiguous. It is unclear whether this refers to a conformational change in the RNA or a displacement of the ligand.  
- **Required correction** Clarify the terminology and provide a structural representation or schematic to illustrate the proposed mechanism.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Consistency  
- **Affected element** Section 2.7, Figure 7  
- **Evidence pointer** Figure 7, Section 2.7  
- **Issue** The text mentions "120FA" in the description of BRG1 occupancy, but the rest of the manuscript refers to 110FA and 102FA. This appears to be a typographical error.  
- **Required correction** Correct the typo to 110FA.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Referencing  
- **Affected element** Section 4.12  
- **Evidence pointer** Section 4.12  
- **Issue** The methods section for molecular dynamics does not specify the force field used for the RNA or the protein, nor does it describe the equilibration protocol in sufficient detail for reproduction.  
- **Required correction** Provide the force field parameters, water model, and ion concentration used in the simulations.

## Risk / unsupported claims
- The claim that 110FA is a better inhibitor than JB181 is not directly supported by experimental comparison; it is inferred from docking results and should be tested experimentally.
- The statement that "targeting the TAR loop and Tat-binding UCG bulge together should be an essential feature" is presented as a conclusion but is based on simulation observations that are not quantitatively validated.
- The claim that 102FA acts as a Cdk9 inhibitor is inferred from docking and immunoprecipitation but lacks direct kinase activity assays.
- The assertion that the molecules do not impact normal cellular transcription is based on the absence of observed changes in Cyclin T1/Cdk9 levels, but no global transcription or cell viability data in uninfected cells are shown for the relevant conditions.
- The significance of the "pulled-out" position of 110FA toward Cyclin T1 is not established; it is unclear whether this is a stable or transient state and whether it correlates with functional outcomes.