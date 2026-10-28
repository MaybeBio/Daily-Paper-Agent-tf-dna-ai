## Review setup
- **Input scope** Full manuscript text (abstract, background, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors design two alternating polarity peptides, RFH and RHF, differing only in histidine/phenylalanine position, and report that central histidine positioning enhances pH-responsive DNA co-assembly and transfection efficiency
- **Visible evidence base** Gel retardation data (Fig. 1), FESEM micrographs (Fig. 2), coarse-grained MD simulation analyses (Figs. 3-5), luciferase transfection assays and MTT toxicity assays (Fig. 6)
- **Missing materials affecting confidence** Supplementary figures referenced (S1-S7) not provided; raw numerical data for transfection and toxicity assays not provided; statistical details (exact p-values, effect sizes, variance) not fully reported; DLS data mentioned as inconclusive but not shown

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in peptide-based gene delivery, namely how histidine positioning within an alternating polarity peptide sequence affects pH-responsive assembly with DNA. The experimental design comparing two sequence isomers is logical and the combination of experimental and computational approaches is commendable. However, several technical concerns limit the strength of the conclusions. The claim that central histidine positioning "enhances" pH-responsive assembly is only partially supported: the gel retardation data show a qualitative difference at acidic pH, but the transfection data do not demonstrate a statistically significant advantage for RFH over RHF at individual N/P ratios. The MD simulations, while informative, use a coarse-grained model with known limitations for capturing detailed electrostatic and aromatic interactions, and the interpretation of simulation metrics as direct proxies for assembly tendency requires more careful justification. The manuscript would benefit from additional quantitative characterization (e.g., binding affinity measurements, particle size/stability data) and clearer statistical reporting.
- **Who would be interested in the results, and why** Researchers in peptide self-assembly, non-viral gene delivery, and biomaterials design would find interest. The work contributes to the growing understanding of sequence-position effects in multifunctional peptides, which is relevant for rational design of gene carriers. The pH-responsive behavior is particularly relevant for endosomal escape mechanisms in gene therapy applications.
- **Major strengths** The study addresses a well-defined question with a clean comparative design (two isomers differing only in His/Phe position). The integration of experimental assembly data with coarse-grained MD simulations provides complementary perspectives. The inclusion of both transfection efficiency and cytotoxicity assessments is appropriate for the application context. The discussion of simulation limitations is thoughtful and demonstrates awareness of methodological constraints.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical support for claims
  - **Claim pointer** "RFH exhibited superior transfection performance at lower N/P ratios compared to RHF"
  - **Evidence pointer** Fig. 6a, 6c; Results section "RFH showed higher in vitro transfection efficiency compared to RHF"
  - **Concern** The claim of superior transfection performance for RFH is based on visual inspection of bar graphs. The text states that the difference between RFH and RHF was insignificant at all individual N/P ratios, yet the two-way ANOVA showed a significant overall effect. This is a marginal statistical result that does not robustly support the claim of "superior" performance. The magnitude of the difference, variance, and exact p-values are not reported. Without effect sizes and confidence intervals, the biological significance of this difference cannot be assessed.
  - **Why it matters** The transfection efficiency comparison is a central pillar of the manuscript's conclusion that histidine positioning affects gene delivery. If the difference is not statistically robust at individual N/P ratios, the claim of "superior" performance is overstated and the design principle proposed may not be well-supported.
  - **Resolution test** Provide exact p-values, effect sizes, and confidence intervals for pairwise comparisons at each N/P ratio. If the difference is not significant at any individual ratio, temper the claim to "comparable or marginally improved" and discuss the biological relevance accordingly.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic interpretation of simulation data
  - **Claim pointer** "Histidine ionization affects RFH's self- and DNA co-assembling tendency to a higher extent compared to RHF"
  - **Evidence pointer** Figs. 3-5; Results section "RFH assembling tendency was more profoundly affected by the histidine ionization state"
  - **Concern** The MD simulation analysis relies on metrics such as SASA, cluster number, and contact counts to infer assembly tendency. However, the manuscript does not provide a clear quantitative threshold or statistical test for what constitutes a "greater" effect on RFH versus RHF. The differences in SASA changes and cluster numbers between RFH and RHF appear modest, and the error bars (if present) are not described. Additionally, the coarse-grained MARTINI force field has known limitations in capturing aromatic ring interactions and pH-dependent protonation effects beyond simple charge assignment. The interpretation that reduced assembly upon histidine protonation is due to "increased repulsive force between the same charges of imidazole rings" is plausible but not directly tested.
  - **Why it matters** The simulation results are used to provide mechanistic support for the experimental observations. If the simulation metrics are not robustly quantified or the force field limitations are not adequately addressed, the mechanistic claims are weakened.
  - **Resolution test** Provide quantitative comparisons with statistical analysis (e.g., mean ± SD from triplicate simulations, with appropriate tests). Discuss the limitations of the MARTINI force field for aromatic interactions and consider complementary all-atom simulations or experimental validation (e.g., circular dichroism, isothermal titration calorimetry) to support the proposed mechanism.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Characterization completeness
  - **Claim pointer** "Both peptides formed stable co-assemblies with DNA at neutral pH"
  - **Evidence pointer** Fig. 1; Results section "RFH showed a reduced tendency to co-assemble with pDNA in acidic pH"
  - **Concern** The manuscript relies primarily on gel retardation to assess co-assembly. While this is a standard method, it provides only qualitative information about binding. The DLS measurements were reported as inconclusive and not shown. No quantitative binding affinity data (e.g., from fluorescence anisotropy, ITC, or surface plasmon resonance) are provided. The stability of the co-assemblies over time or under physiological conditions is not assessed. The claim of "stable" co-assemblies is therefore not well-quantified.
  - **Why it matters** For a gene delivery application, the stability and physical properties of the peptide-DNA complexes are critical parameters. Without quantitative characterization, the practical utility of these peptides cannot be fully evaluated.
  - **Resolution test** Provide quantitative binding data (e.g., dissociation constants) and particle characterization (size, zeta potential, polydispersity) with appropriate replicates. If DLS is unreliable for these anisotropic structures, consider alternative methods such as nanoparticle tracking analysis or cryo-TEM.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of N/P ratio calculation
  - **Affected element** Methods section "Peptide-pDNA co-assembly"
  - **Evidence pointer** Methods section, Table 1
  - **Issue** The N/P ratio calculation excludes histidine positive charge at acidic pH, which is reasonable for comparison, but the rationale is not fully explained. At pH 4, histidine is fully protonated, so the effective charge ratio differs from the nominal N/P ratio. This could affect interpretation of the acidic pH gel retardation results.
  - **Required correction** Clarify the rationale for excluding histidine from N/P calculation and discuss how the effective charge ratio at acidic pH might influence the interpretation of the gel retardation data.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Figure quality and presentation
  - **Affected element** Fig. 6
  - **Evidence pointer** Fig. 6a-d
  - **Issue** The figure labels in the text appear mismatched (text refers to Fig. 6a and 6c for transfection, but the figure legend describes 6a and 6c as toxicity for one cell line and transfection for another). This creates confusion about which panel corresponds to which assay.
  - **Required correction** Ensure figure panel labels in the text match the figure legend. Consider reorganizing panels so transfection and toxicity data for each cell line are clearly separated and labeled.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results section "RFH showed higher in vitro transfection efficiency compared to RHF"
  - **Evidence pointer** Fig. 6
  - **Issue** The manuscript states that differences were analyzed by two-way ANOVA with multiple comparisons, but does not report the number of replicates, the variance structure, or whether assumptions of ANOVA were met. The figure appears to show mean ± SD, but this is not explicitly stated in the legend.
  - **Required correction** Report the number of independent replicates, the statistical test used for each comparison, and the exact p-values. State in the figure legend that data are mean ± SD (or SEM, as appropriate).
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Simulation methodology details
  - **Affected element** Methods section "Molecular characterization"
  - **Evidence pointer** Methods section
  - **Issue** The manuscript does not specify the MARTINI water model used, the salt concentration, the temperature coupling scheme, or the criteria for cluster identification. These details are important for reproducibility.
  - **Required correction** Provide complete simulation parameters, including water model, ion concentration, thermostat/barostat settings, and cluster analysis criteria. Consider adding a supplementary table with simulation details.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of simulation limitations is present but could be expanded to address the specific limitations of the coarse-grained approach for studying aromatic interactions and pH effects. The authors acknowledge the issue with aggregation propensity metrics but do not discuss how this might affect their specific conclusions.
  - **Required correction** Expand the limitations paragraph to specifically address how the MARTINI force field handles aromatic ring interactions and whether the observed differences between RFH and RHF could be an artifact of the coarse-grained representation.

## Risk / unsupported claims
- The claim that RFH "exhibited superior transfection performance" is not robustly supported by the statistical analysis presented, as the difference was insignificant at individual N/P ratios
- The mechanistic claim that histidine protonation disrupts assembly via "increased repulsive force between the same charges of imidazole rings" is plausible but not directly tested experimentally
- The statement that "both peptides achieved a higher transfection efficiency in 293T and HeLa cells compared to R9" is not supported with specific p-values for each comparison at each N/P ratio
- The claim that "RFH exhibited superior transfection performance at lower N/P ratios" is based on a single experiment with three replicates and no dose-response or time-course data
- The assertion that the designed peptides form "stable" co-assemblies is not quantitatively supported, as no stability data over time or under physiological conditions are provided
- The interpretation of MD simulation cluster numbers and SASA changes as direct measures of assembly tendency requires validation against experimental assembly data, which is not provided
- The conclusion that "positioning histidine closer to the peptide center amplifies pH-responsive DNA co-assembly" is a general design principle that is not tested with additional peptide variants beyond the two reported

## Assessment against Nature-style criteria
- **Originality** Moderate. The concept of pH-responsive histidine-containing peptides for gene delivery is not new, but the specific comparison of histidine positional isomers within an alternating polarity framework provides a novel angle. The study does not introduce fundamentally new concepts but offers a systematic comparison that could inform design rules.
- **Scientific importance** Moderate. The findings are potentially useful for the peptide-based gene delivery community, but the effect sizes are modest and the mechanistic understanding remains incomplete. The study does not resolve a major outstanding question in the field, and the practical implications for improving gene delivery efficiency are not clearly demonstrated.
- **Interdisciplinary readership** Limited. The manuscript is primarily of interest to researchers in peptide chemistry, biomaterials, and gene delivery. The computational component may attract simulation-focused readers, but the overall scope is narrow and unlikely to draw broad interdisciplinary attention.
- **Technical soundness** The experimental design is logical, but several technical concerns limit confidence: incomplete statistical reporting, qualitative rather than quantitative assembly characterization, and limitations of the coarse-grained simulation approach for the specific interactions studied. The gel retardation data are clear but provide only binary binding information.
- **Readability for nonspecialists** The manuscript is generally well-written and accessible, with clear explanations of the design rationale. However, the simulation section may be challenging for readers without computational background, and the significance of specific metrics (SASA, cluster number) is not explained for a general audience.

## Recommendation posture
Supportive if technical concerns are resolved. The core question is relevant and the comparative design is sound, but the strength of the conclusions currently exceeds what the evidence robustly supports. The manuscript would be acceptable after addressing the statistical reporting, providing quantitative assembly characterization, and tempering the mechanistic claims to match the level of evidence.