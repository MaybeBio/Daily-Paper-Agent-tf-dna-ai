## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure descriptions as provided.
- **Assessment boundary** Scientific validity, technical soundness, and support for claims based solely on the supplied text. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The authors claim that Dsup binds to DNA in living mammalian cells (demonstrated via FLIM-FRET) and that Dsup expression enhances survival of HEK293T cells and yeast under hydrogen peroxide-induced oxidative stress. They also present MD simulations suggesting a protective mechanism via physical shielding of DNA.
- **Visible evidence base** Results sections describe MD simulations (Figure 1), FLIM-FRET experiments (Figure 2), and cell survival assays (Figures 3 and 4). Methods provide details on plasmids, cell culture, stable cell line generation, CCK-8 assays, yeast culture, viability experiments, fluorescence imaging, FLIM-FRET analysis, and MD simulation protocols. Statistical methods are described.
- **Missing materials affecting confidence** Figure panels are referenced but not shown. Supplementary Information, Source Data files, and custom code are not provided. Exact numerical values for FRET efficiencies, cell viability percentages, and statistical outputs (e.g., P values, effect sizes) are not included in the text. Details on the number of replicates for MD simulations and the criteria for selecting "representative" trajectories are incomplete.

## Reviewer
- **Overall assessment** The manuscript addresses an important question regarding the mechanism of Dsup-mediated stress protection. The combination of MD simulations and live-cell FLIM-FRET is a strong approach. However, the evidence as presented is incomplete. Key quantitative data (e.g., FRET efficiency values, cell viability curves with error bars, statistical test results) are not provided in the text, making it impossible to fully evaluate the robustness of the claims. The MD simulation results are qualitative and lack convergence analysis. The yeast experiments show only modest effects, and the link between DNA binding and oxidative stress protection is inferred rather than directly demonstrated. The manuscript is technically sound in design but currently under-supported by the visible evidence.
- **Who would be interested in the results, and why** Researchers in extremophile biology, DNA repair, oxidative stress, and aging. The potential universal applicability of Dsup across species (mammalian and yeast) could interest synthetic biologists and those exploring stress-resistance engineering. The FLIM-FRET methodology for DNA-protein interactions may appeal to cell biologists and biophysicists.
- **Major strengths** 1. Novel combination of MD simulations and live-cell FLIM-FRET to study Dsup-DNA interactions. 2. Use of multiple model systems (mammalian cells and yeast) to assess functional effects. 3. Clear negative controls (NLS-EGFP) for FRET specificity. 4. Inducible expression systems to control Dsup levels. 5. Direct measurement of DNA binding in living cells, which addresses a gap in prior studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative FRET data missing), R1-M2 (MD simulation validation), R1-M3 (statistical reporting), R1-M4 (dose-response and time-course data), R1-M5 (mechanistic link).
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The study applies existing techniques (FLIM-FRET, MD) to a new protein, but the conceptual advance (direct visualization of Dsup-DNA binding in live cells) is incremental.  
  - **Scientific importance** Moderate. Confirming Dsup-DNA binding in vivo and showing cross-species protection is useful, but the mechanism remains speculative.  
  - **Interdisciplinary readership** Moderate. Will appeal to biophysicists, cell biologists, and stress biologists, but may not attract broad general interest.  
  - **Technical soundness** Currently insufficient. Missing quantitative data and statistical details prevent full assessment.  
  - **Readability for nonspecialists** Good. The text is clear, but some jargon (e.g., FLIM-FRET, Tet-on) may require prior knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The core claims are plausible but not fully established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence completeness  
- **Claim pointer** "FLIM-FRET demonstrates Dsup binding to DNA in living mammalian cells" (Results section).  
- **Evidence pointer** Figure 2, "FLIM-FRET imaging and analysis" in Methods.  
- **Concern** The text reports significantly shorter fluorescence lifetimes for Dsup-EGFP with SYTO 59 staining (τ = 1.79 ± 0.02 ns) compared to without (τ = 2.51 ± 0.02 ns), but no FRET efficiency values, representative decay curves, or statistical test results (e.g., P values) are provided. The number of cells (n = 24 vs 19) is given, but the distribution of data and effect size are not shown.  
- **Why it matters** Without quantitative FRET data and statistical analysis, the reader cannot assess the magnitude or reliability of the interaction. A 0.72 ns lifetime change could be due to artifacts (e.g., photobleaching, refractive index changes) rather than specific binding.  
- **Resolution test** Provide FRET efficiency values (e.g., E = 1 - τ_DA/τ_D) with standard errors, representative fitted decay curves, and P values from appropriate tests (e.g., unpaired t-test). Show that the lifetime reduction is concentration-dependent and reversible.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "MD simulations of Dsup-DNA interactions" (Results section) and "Dsup slows down the melting of DNA" (Discussion).  
- **Evidence pointer** Figure 1, "MD simulations" in Methods.  
- **Concern** The MD simulations are described qualitatively. No data on convergence (e.g., RMSD over time), force field validation, or replicate variability are shown. The claim that Dsup "slows down" DNA melting is based on a single comparison at 500 K, but the text does not state how many replicates were used for the melting simulations or whether the difference is statistically significant.  
- **Why it matters** MD simulations are sensitive to initial conditions and force field parameters. Without convergence analysis and replicate statistics, the protective mechanism (physical shielding) remains speculative.  
- **Resolution test** Show RMSD and radius of gyration plots for all replicates. Report the number of intact base pairs over time for each replicate at 500 K, with mean ± SD, and perform a statistical test (e.g., t-test) comparing melting rates with and without Dsup.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** "Dsup expression enhances cell survival in the presence of hydrogen peroxide" (Results section).  
- **Evidence pointer** Figure 3, "CCK-8 colorimetric assay" in Methods.  
- **Concern** The text states that Dsup increased cell viability at certain H2O2 concentrations, but no numerical data (e.g., viability percentages, error bars, P values) are provided. The description of "no significant differences" at other concentrations is not supported by any statistical output.  
- **Why it matters** Without effect sizes and statistical tests, the reader cannot determine whether the observed differences are biologically meaningful or within experimental noise.  
- **Resolution test** Provide bar graphs or dose-response curves with mean ± SEM for at least three independent experiments, and report P values from ANOVA or t-tests for each concentration.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Experimental design  
- **Claim pointer** "Dsup expression in yeast is beneficial for its survival under oxidative stresses" (Results section).  
- **Evidence pointer** Figure 4, "Yeast viability experiments" in Methods.  
- **Concern** The yeast experiments use only a single H2O2 concentration (2 µM) and a single time point (4 hours). The effect size is modest (e.g., 42.4% vs 52.1% cell death at 4 hours), and the text does not report whether the difference is statistically significant at 3 hours.  
- **Why it matters** A single concentration and time point may not capture the full protective effect or its kinetics. The modest effect size raises questions about biological relevance.  
- **Resolution test** Perform a dose-response curve (e.g., 0.5–10 µM H2O2) and a time course (e.g., 2, 4, 6 hours). Report statistical significance for each condition.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Mechanistic link  
- **Claim pointer** "Dsup may provide a physical barrier to prevent ROS-induced double-stranded breaks" (Discussion).  
- **Evidence pointer** Figure 1 (MD simulations), Figure 3 (cell survival).  
- **Concern** The manuscript does not directly test whether DNA binding is required for the observed cytoprotective effects. No mutant Dsup (e.g., with reduced DNA binding) is used to establish causality.  
- **Why it matters** The central claim of the paper is that Dsup's DNA binding underlies its protective function. Without a loss-of-function experiment, alternative mechanisms (e.g., ROS scavenging, protein-protein interactions) cannot be excluded.  
- **Resolution test** Generate Dsup mutants with reduced DNA binding (e.g., charge-neutralizing mutations in the C-terminal region) and test their protective effects in both HEK293T and yeast assays.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract  
- **Issue** The abstract states "Dsup binding to DNA in living mammalian cells" but does not mention the yeast results, which are a significant part of the study.  
- **Required correction** Add a sentence summarizing the yeast findings to the abstract.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods, "MD simulations"  
- **Evidence pointer** Methods  
- **Issue** The method states that "three conformations with radii of gyration close to that expected" were selected, but the selection criteria are not quantitative.  
- **Required correction** Specify the range of acceptable Rg values and the method for random selection.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Figure 3  
- **Evidence pointer** Figure 3  
- **Issue** The text mentions "HLOL" in the results section, which is likely a typo for "H2O2".  
- **Required correction** Correct the typo to "H2O2".

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Statistical reporting  
- **Affected element** Figure 4  
- **Evidence pointer** Figure 4  
- **Issue** The text states "statistically significant lower cell death" but does not report the test used or the P value.  
- **Required correction** Report the statistical test and P value in the text or figure legend.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Discussion  
- **Evidence pointer** Discussion  
- **Issue** The discussion mentions "the observed toxicity resulting from high-level over-expression of Dsup" but does not provide data or a reference for this claim.  
- **Required correction** Either provide data or cite the relevant study.

## Risk / unsupported claims
- The claim that Dsup "slows down the melting of DNA" is unsupported without quantitative MD data and statistical analysis.
- The claim that Dsup binding to DNA is directly demonstrated in living cells is weakened by the lack of FRET efficiency values and statistical tests.
- The claim that Dsup expression "enhances cell survival" in HEK293T cells is not supported by visible numerical data.
- The claim that Dsup's protective effect is due to physical shielding of DNA is speculative and not tested with loss-of-function mutants.
- The statement that "the function of Dsup could be universal across different species" is an overgeneralization based on two model systems.