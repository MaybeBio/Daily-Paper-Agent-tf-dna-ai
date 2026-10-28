## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, conclusions, author contributions, conflicts, acknowledgements) as provided by the user. Supplementary material (ESI) referenced but not supplied.
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No external literature verification or replication of experiments performed.
- **Shared manuscript claim summary** The authors report synthesis and characterization of two rhenium complexes (I: cis-tetrachlorotetrabenzimidazoldirhenium(III) chloride; II: tetrabenzimidazoldioxorhenium(V)), with X-ray structure for II. They claim both complexes interact with G-quadruplex DNA (G4) with binding constants up to 10^6 M^-1, stabilize ckit1/ckit2 quadruplexes in FRET-melting assays, show differential toxicity in macrophages, and accumulate intracellularly. Molecular dynamics simulations provide binding models for II with ckit1/ckit2.
- **Visible evidence base** Main text figures (Fig. 1-8), tables (Table 1-3), and text descriptions. ESI referenced for synthesis details, additional spectra, sequences, and simulation parameters, but not available for review.
- **Missing materials affecting confidence** ESI (synthesis procedures, characterization data, DNA sequences, simulation details, supplementary figures S1-S9, Tables S1-S2), raw titration data, crystallographic CIF file, and full simulation trajectories. These omissions limit verification of several quantitative claims.

## Reviewer
- **Overall assessment** The manuscript presents a straightforward synthesis and preliminary biophysical characterization of two rhenium complexes with benzimidazole ligands. The work is competent but incremental, building on the authors' prior publication (ref. 16) on dirhenium(III) carboxylates. The most novel claims, regarding macrophage accumulation and potential immunomodulatory roles, are supported by limited data and speculative interpretation. The G4 interaction studies are standard and adequately executed, but the selectivity and mechanism claims require stronger evidence. The manuscript is readable and logically organized, but several technical details and statistical considerations are missing.
- **Who would be interested in the results, and why** Researchers in bioinorganic chemistry, particularly those studying rhenium-based anticancer agents and G-quadruplex DNA interactions. The macrophage accumulation data may interest immunologists working on tumor-associated macrophages, though the preliminary nature limits immediate impact. The work could also appeal to medicinal chemists exploring benzimidazole scaffolds in metal complexes.
- **Major strengths** 1) Clear synthetic strategy linking aromatic ligand design to G4 binding, building logically on prior work. 2) Combined experimental (fluorescence titration, FRET-melting) and computational (MD) approach provides complementary perspectives. 3) The macrophage accumulation finding, while preliminary, opens a potentially interesting avenue for dirhenium complexes in immunomodulation. 4) The manuscript is well-written and accessible to a broad chemistry audience.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (X-ray structure interpretation), R1-M2 (binding constant methodology), R1-M3 (cell viability data), R1-M4 (MD simulation validation), R1-M5 (selectivity claim).
- **Assessment against Nature-style criteria** **Originality**: Moderate. The use of benzimidazole ligands on dirhenium(III) is a logical extension of prior work (ref. 16), and the dioxo Re(V) complex is new, but the overall concept is not transformative. **Scientific importance**: Limited. The findings are incremental, with no clear therapeutic advantage demonstrated over existing G4 binders. The macrophage data are intriguing but underdeveloped. **Interdisciplinary readership**: Narrow. The work primarily serves bioinorganic and medicinal chemistry communities; the immunology angle is too preliminary to attract broader interest. **Technical soundness**: Adequate in parts, but several methodological gaps (binding constant derivation, MD validation, cell viability statistics) undermine confidence. **Readability for nonspecialists**: Good. The text is clear, figures are generally informative, and the context is well-explained. However, the manuscript does not meet the high-impact, broad-appeal threshold expected for Nature.
- **Recommendation posture** Currently not established from the provided evidence. The core claims regarding G4 binding and stabilization are plausible but require methodological clarification and additional controls. The macrophage accumulation claim, highlighted as a primary finding, is insufficiently supported. Major revisions and additional experiments are needed before the case is convincing.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The crystal structure of II is solved in P4/mnc with four [ReO2(Benzim)4]+ cations and six perrhenate anions, requiring an average +1.5 charge per complex unit, attributed to shared protons between adjacent units.
- **Evidence pointer** Section "Solid state analysis of II", Table 1, Table 2, Fig. 3
- **Concern** The charge-balance model is speculative. The authors state "we do not have any direct evidence either of the presence of shared protons or of their location," yet they proceed to place protons at specific positions (H1A at 0.5, 0.5, 1.0; H2A at 0.5, 0.5, 0.5). This is a critical assumption that affects the structural model, bond distances, and chemical formula. The O1-O1 distance of 2.64(4) Å is short and could indicate a strong hydrogen bond, but the proton placement is not experimentally justified. The authors should provide refinement details, difference Fourier maps, or spectroscopic evidence (e.g., IR, neutron diffraction) to support the proton positions. Without this, the structural assignment is not reliable.
- **Why it matters** The crystal structure is a primary characterization claim for a new compound. An incorrect charge model or proton placement would invalidate the molecular formula, oxidation state assignment, and any structure-property correlations. This is foundational for the rest of the study.
- **Resolution test** Provide full crystallographic refinement data (including R-factors, residual electron density maps, and proton positions from difference Fourier or other methods). Alternatively, re-refine the structure with a different charge model and demonstrate which is statistically preferred. If protons cannot be located, state this explicitly and discuss the implications for the formula.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** Binding constants (Kb) for I and II with G4s cKit1 and Bcl2 are in the order of 10^6 M^-1, suggesting strong interaction.
- **Evidence pointer** Section "Evaluation of the G-quadruplex DNA interaction", Fig. 5, Table 3
- **Concern** The methodology for determining Kb from fluorescence titration is not described. The authors reference "analysis of the relative luminescence intensity" but do not specify the fitting model (e.g., 1:1 binding, Hill equation, etc.), the concentration ranges, stoichiometry assumptions, or whether inner-filter effects were corrected. The quenching mechanism is also not established (static vs. dynamic), which is essential for interpreting the data. Without these details, the Kb values are not reproducible or verifiable.
- **Why it matters** The binding affinity is a central quantitative claim supporting the G4 interaction. If the methodology is flawed or the model is inappropriate, the reported Kb values could be inaccurate, undermining the conclusion of strong binding.
- **Resolution test** Provide a detailed description of the titration protocol, including excitation/emission wavelengths, slit widths, DNA and complex concentrations, and the mathematical model used to fit the data. Include control experiments (e.g., with duplex DNA, or a non-G4 sequence) and demonstrate that the quenching is specific. Show residuals or goodness-of-fit statistics for the fitted curves.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** I is toxic against RAW 264.7 macrophages only at high concentrations (50 and 100 μM, reducing viability to 65% and 39%), while II shows no toxicity. I accumulates in cells at levels seven times higher than II.
- **Evidence pointer** Section "Assessment of the cell activity of the rhenium complexes", Fig. 8, Table S2
- **Concern** The cell viability data are presented without statistical analysis (e.g., error bars, replicates, significance testing). The claim of "no toxicity" for II is based on a single concentration range, and the accumulation data are not shown in the main text (only referenced in Table S2). The relationship between accumulation and toxicity is not mechanistically explored. Additionally, the statement that "the accumulation of rhenium in the cells that were treated with I was very significant and seven times larger" lacks quantitative context (e.g., ng Re per million cells, time course, efflux).
- **Why it matters** The macrophage data are presented as a "primary finding" in the conclusions, but the evidence is preliminary and lacks rigor. Without proper statistics and quantitative details, the claims of differential toxicity and accumulation are not substantiated.
- **Resolution test** Provide full dose-response curves with at least three independent replicates, error bars, and statistical tests (e.g., ANOVA). Include a detailed description of the accumulation assay (e.g., ICP-MS, number of cells, normalization). Show time-dependent uptake and, ideally, a correlation between intracellular rhenium concentration and viability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** Molecular dynamics simulations provide insights into the binding modes of II with ckit1 and ckit2 G-quadruplexes.
- **Evidence pointer** Section "Evaluation of the G-quadruplex DNA interaction", Fig. 7, ESI Fig. S7-S8
- **Concern** The MD simulation details are entirely in the ESI, which is not provided. The main text describes the final binding modes but does not specify the force field, simulation length, water model, or how the starting structures were obtained. The claim that the complex "stays stable until the end of the simulation" is vague without convergence criteria or RMSD analysis. The functional significance of the observed π-stacking interactions is not validated experimentally.
- **Why it matters** The simulations are used to propose a binding mechanism, but without methodological transparency, the results cannot be evaluated. Overinterpretation of MD data without experimental validation is a common pitfall.
- **Resolution test** Provide full simulation parameters in the main text or ESI, including force field, box size, equilibration protocol, and production run length. Show RMSD and RMSF plots to demonstrate stability. Ideally, validate the predicted binding mode with experimental data (e.g., mutagenesis, NMR, or ITC).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The results "show the DNA binding activity of the rhenium complexes and their ability to be players in the anti-cancer fight since they can bind to non-canonical DNA forms in oncogene promoters, accumulate in some cancer cells, and influence the cancer cells microenvironment."
- **Evidence pointer** Conclusions section
- **Concern** The claim that these complexes can "influence the cancer cells microenvironment" is not supported by any direct experimental evidence. The macrophage experiments are preliminary and do not demonstrate a functional effect on tumor-associated macrophages or the tumor microenvironment. The link between G4 binding and anticancer activity is speculative, as no cellular or in vivo anticancer efficacy data are presented.
- **Why it matters** Overstated conclusions can mislead readers and overstate the significance of the work. The manuscript should clearly distinguish between demonstrated findings and speculative implications.
- **Resolution test** Either provide direct evidence for a functional effect on the tumor microenvironment (e.g., cytokine profiling, co-culture assays, in vivo studies) or temper the conclusions to reflect the preliminary nature of the observations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "I was more selective for binding G4-than II" but does not specify which G4 sequences were compared or the basis for selectivity (e.g., Kb ratios, ΔTm values). This is vague and could be misinterpreted.
- **Required correction** Specify the G4 sequences and the quantitative measure of selectivity (e.g., "I showed 2-fold higher Kb for ckit1 compared to II").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** UV-vis and fluorescence properties
- **Evidence pointer** Section "UV-vis and fluorescence properties of the complexes", Fig. 4
- **Issue** The assignment of the 350 nm absorption to L→M charge transfer is tentative and not supported by any computational or experimental evidence (e.g., TD-DFT, spectroelectrochemistry). The authors acknowledge this is "tentatively assigned" but should be more cautious.
- **Required correction** Rephrase to indicate this is a tentative assignment and suggest further studies to confirm.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Cell studies
- **Evidence pointer** Section "Assessment of the cell activity of the rhenium complexes"
- **Issue** The choice of RAW 264.7 cells is not justified. The authors mention "tumor-associated macrophages" but use a transformed cell line, which may not accurately represent TAMs. The relevance to the tumor microenvironment is unclear.
- **Required correction** Justify the use of RAW 264.7 as a model for TAMs, or acknowledge the limitation and suggest future studies with primary macrophages or TAM-like cells.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusions
- **Evidence pointer** Conclusions section
- **Issue** The statement "the G4-quadruplex binders on the base of the rhenium(iii) clusters, were first described in our work" is grammatically awkward and could be clearer.
- **Required correction** Rephrase to "To our knowledge, this is the first description of G4-quadruplex binders based on rhenium(III) clusters, as reported in our prior work."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Synthesis
- **Evidence pointer** Section "Synthesis and characterization of the complexes"
- **Issue** The synthesis procedure for II is only described in the ESI. For a new compound, key characterization data (e.g., NMR, elemental analysis, HRMS) should be summarized in the main text to allow initial assessment.
- **Required correction** Include a brief summary of characterization data for II in the main text, with full details in the ESI.

## Risk / unsupported claims
- The crystal structure of II with the proposed proton-sharing model is not fully supported by direct evidence (R1-M1).
- Binding constants (Kb) of 10^6 M^-1 are not verifiable without detailed methodology (R1-M2).
- The claim that I and II "influence the cancer cells microenvironment" is unsupported by direct experimental data (R1-M5).
- The selectivity of I for G4 over II is stated but not quantified or statistically tested.
- The statement that "the accumulation of rhenium in the cells... was very significant" lacks quantitative data and statistical analysis.
- The MD simulation results are not assessable without the ESI, and the stability claim is vague.
- The relevance of RAW 264.7 cells to tumor-associated macrophages is assumed but not justified.