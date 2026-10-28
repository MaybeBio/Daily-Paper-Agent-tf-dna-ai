## Review setup

- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, footnotes) without figures, tables, or supplementary files
- **Assessment boundary** Scientific claims, experimental logic, methodological soundness, and interpretational validity based on the provided text only; figure quality and statistical details cannot be fully assessed
- **Shared manuscript claim summary** The authors propose that EcSSB undergoes liquid-liquid phase separation in vivo, forming cytoplasmic storage assemblies that are spatially segregated from the nucleoid under basal conditions, and that these assemblies dynamically disassemble and reassociate with DNA upon stress or metabolic shifts, with growth-phase-dependent modulation
- **Visible evidence base** Text descriptions of super-resolution (SIM) imaging, confocal microscopy, image analysis scripts, growth assays, and in vitro biophysical assays (turbidity, MST, MRPS, DLS, fluorescence microscopy); references to Figures 1-5, S1-S12, Tables S1-S5, and Supplementary files
- **Missing materials affecting confidence** All figures, tables, supplementary data, image analysis scripts, and statistical details; exact numerical results, sample sizes, replicates, and control data are not visible

## Reviewer

- **Overall assessment** This manuscript addresses a timely and important question regarding the in vivo organization of bacterial SSB proteins and the potential role of liquid-liquid phase separation in their function. The combination of super-resolution imaging with quantitative analysis and in vitro biophysical characterization is well conceived. However, the central claim that EcSSB foci represent liquid condensates in vivo rests on indirect evidence, and several key controls and quantitative comparisons are not visible in the provided text. The manuscript is potentially significant but requires substantial additional evidence to firmly establish the phase-separation-based model.

- **Who would be interested in the results, and why** Researchers studying bacterial cell biology, DNA replication and repair, phase separation in prokaryotes, and antimicrobial development. The work bridges biophysics and microbiology, and the proposed model of SSB storage and mobilization via phase separation would be of broad interest to the LLPS community and to those studying stress responses in bacteria.

- **Major strengths** The study addresses a significant gap in the field by extending in vitro SSB condensation studies to the in vivo context. The use of super-resolution microscopy is appropriate for the bacterial scale. The authors include a thoughtful control regarding the FM 4-64 dye artifact, demonstrating methodological rigor. The integration of in vitro biophysical data with in vivo observations provides a multi-scale perspective. The discussion of prior literature is comprehensive and balanced.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that EcSSB-GFP foci represent liquid condensates in vivo, stating that "cellular EcSSB-GFP foci may arise, at least in part, from the intrinsic condensation propensity of EcSSB"
- **Evidence pointer** Results section "EcSSB forms dynamic assemblies during growth, which consolidate upon growth arrest"; in vitro data in Figs. S4-S8
- **Concern** The in vivo evidence for liquid-like behavior is limited to size, intensity, and spatial distribution of foci. No direct measurements of liquid properties in vivo (e.g., fusion events, circularity, FRAP dynamics within foci, or exchange rates) are described in the text. The in vitro data demonstrate condensation propensity but do not establish that the observed in vivo foci are indeed liquid condensates rather than solid aggregates, membrane-associated clusters, or protein-DNA complexes.
- **Why it matters** The central thesis of the manuscript is that EcSSB phase separation underlies its in vivo organization and function. Without direct evidence of liquid-like behavior in cells, the interpretation remains speculative and alternative explanations (e.g., protein aggregation, membrane tethering, or replication factory organization) are not excluded.
- **Resolution test** Provide FRAP data on individual foci in vivo showing rapid recovery; demonstrate fusion events between foci; show that foci are spherical and deformable; or provide genetic evidence that disrupting condensation (e.g., via IDL mutations) abolishes foci formation without affecting other cellular functions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The authors state that "up to 70 % of the total EcSSB-GFP signal became localized in foci" in stationary phase and that stressed cells contained "less than 5 % of the EcSSB-GFP signal (if any) in discrete signals"
- **Evidence pointer** Results sections "EcSSB forms dynamic assemblies during growth" and "EcSSB-GFP assemblies disassemble under stress"; Figures 1-3; Tables S3-S5
- **Concern** The quantitative claims lack visible statistical support. No sample sizes, number of cells analyzed, biological replicates, or statistical tests are reported in the text. The image analysis pipeline is described but its validation (e.g., against manual counting, sensitivity to threshold parameters) is not presented. The claim that parameters were "set based on untreated cells and applied identically to all treated samples" raises concerns about potential bias if treated samples have different signal-to-noise characteristics.
- **Why it matters** The quantitative comparisons between growth phases and stress conditions are central to the conclusions. Without proper statistical treatment and validation of the analysis pipeline, the reliability of these comparisons cannot be assessed.
- **Resolution test** Report the number of cells and independent experiments for each condition; provide statistical tests for all comparisons; validate the image analysis pipeline against manual analysis or simulated data; show that conclusions are robust to threshold parameter variation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The authors propose that "stress induction is accompanied by increased DNA association" and interpret this as mobilization of SSB from storage pools to sites of DNA damage
- **Evidence pointer** Results section "Stress induction increases spatial association between EcSSB-GFP and DNA"; Figure 4
- **Concern** The colocalization analysis between EcSSB-GFP and Hoechst-stained DNA is described, but the interpretation is ambiguous. Increased overlap could reflect (i) genuine SSB recruitment to DNA damage sites, (ii) nucleoid compaction or reorganization upon stress that brings pre-existing SSB foci into closer proximity with DNA, or (iii) changes in cell morphology. The authors do not discuss these alternatives or provide time-resolved data to distinguish between them.
- **Why it matters** The proposed model of "dynamic storage and mobilization" depends on the interpretation that SSB moves from cytoplasmic stores to DNA upon stress. If the increased colocalization is due to nucleoid reorganization rather than SSB mobilization, the model would need revision.
- **Resolution test** Provide time-lapse imaging showing SSB foci dissolution and appearance at DNA damage sites; use DNA damage markers (e.g., RecA-GFP) to correlate SSB recruitment with damage sites; or perform fluorescence recovery after photobleaching to show SSB exchange between cytoplasmic and DNA-bound pools.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Direct vs. indirect effects
- **Claim pointer** The authors state that "the applied stressors modulate cellular EcSSB assemblies in vivo through cellular response mechanisms rather than through direct effects on EcSSB condensation"
- **Evidence pointer** Results section "Testing the effects of in vivo stressors on EcSSB condensates in vitro"; Figure S9
- **Concern** The in vitro tests of stressor effects on EcSSB condensation are described as showing no direct effects, but the specific concentrations tested in vitro versus those applied in vivo are not clearly compared. Some stressors (e.g., UV) cannot be directly tested in vitro in the same manner. The conclusion that stressor effects are indirect relies on the assumption that intracellular concentrations match the tested in vitro concentrations, which is not established.
- **Why it matters** The distinction between direct physicochemical effects and indirect cellular responses is important for the proposed model. If stressors directly modulate condensation at physiologically relevant concentrations, the interpretation of in vivo results would change.
- **Resolution test** Clearly state the concentrations tested in vitro and compare them to estimated intracellular concentrations; test a range of concentrations spanning physiological conditions; for UV, use a surrogate (e.g., DNA damage mimics) or discuss the limitation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors suggest that their findings "may also open avenues for new-mechanism antimicrobial discovery by targeting phase separation pathways"
- **Evidence pointer** Discussion section "Functional implications of intracellular EcSSB condensation"
- **Concern** The antimicrobial relevance is speculative and not supported by direct evidence in this manuscript. No experiments demonstrate that disrupting SSB phase separation affects bacterial viability or drug susceptibility. The connection to antimicrobial development is plausible but not established.
- **Why it matters** While speculative statements are acceptable in discussion sections, the framing suggests a translational relevance that is not supported by the data presented. This could overstate the significance of the findings.
- **Resolution test** Either temper the claim to reflect its speculative nature or provide preliminary evidence (e.g., growth inhibition by condensation-disrupting agents, or reduced fitness of condensation-defective mutants under stress).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Cell culture preparation for fluorescence imaging"
- **Evidence pointer** Methods, location not provided
- **Issue** The text contains apparent typographical errors: "MgSOO" appears twice where "MgSO4" is clearly intended. Additionally, the sentence "UV-stressed cells were also observed without incubation to avoid regeneration" is unclear; it should specify what is being avoided (e.g., DNA repair and recovery).
- **Required correction** Correct the typographical errors and clarify the sentence regarding UV-stressed cells.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Characterization of the EcSSB-GFP expressing cell line"
- **Evidence pointer** Figure S1
- **Issue** The growth comparison between the EcSSB-GFP expressing strain and the control is described qualitatively ("no detectable differences"). Quantitative growth parameters (e.g., doubling times, growth rates) are not reported.
- **Required correction** Provide quantitative growth data (e.g., doubling times with standard deviations) for both strains under normal and stress conditions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretive caution
- **Affected element** Discussion section "The cellular EcSSB pool is distributed between genome-associated complexes and storage assemblies with condensate properties"
- **Evidence pointer** Discussion, location not provided
- **Issue** The authors state that "several lines of evidence point to the existence and liquid condensate nature of cellular EcSSB storage pools," but the evidence cited from prior work (FRAP, fusion events) is from other studies, not from the current in vivo data. The distinction between prior evidence and new evidence should be clearer.
- **Required correction** Clearly separate evidence from this study versus evidence from prior literature when supporting the liquid condensate claim.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods section "Evaluation of microscopy images of E. coli cells"
- **Evidence pointer** Methods, location not provided
- **Issue** The description of the image analysis scripts is brief. The "modified Find Maxima function" and the thresholding approach are mentioned but not described in sufficient detail to be reproduced. The supplementary file is referenced but not visible.
- **Required correction** Provide a more detailed description of the image analysis algorithm in the main text or ensure the supplementary file contains complete, reproducible details.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "EcSSB-GFP assemblies disassemble under stress, but this process is attenuated in stationary-phase cells"
- **Evidence pointer** Figure 2 and Table S3
- **Issue** The text describes effects of many stressors but does not clearly indicate which stressors had the strongest effects in a quantitative manner. The ranking of stressor efficacy is not presented.
- **Required correction** Provide a quantitative summary (e.g., a table or figure) ranking the effects of different stressors on foci number and intensity.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract and Results
- **Issue** The term "dynamic" is used frequently to describe EcSSB foci, but the temporal resolution of the imaging and the specific dynamic behaviors observed (e.g., movement, intensity fluctuations) are not described in the text.
- **Required correction** Specify what dynamic behaviors were measured and over what time scales, or use more precise terminology.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Location not provided
- **Issue** The manuscript cites prior work on EcSSB foci and LLPS, but the novelty of the current findings relative to the recent study by Cherry et al. (2023) could be more explicitly articulated. The authors mention differences in labeling strategies but do not systematically compare their findings with those of Cherry et al.
- **Required correction** Add a paragraph explicitly comparing and contrasting the current findings with those of Cherry et al. and other recent studies.

## Risk / unsupported claims

- The claim that EcSSB foci are liquid condensates in vivo is not directly supported by the visible evidence; no in vivo measurements of liquid properties are presented
- The claim that stress-induced increases in EcSSB-DNA colocalization reflect SSB mobilization from storage pools is an interpretation that is not distinguished from alternative explanations (e.g., nucleoid reorganization)
- The claim that stressors act indirectly through cellular responses rather than directly on condensation is not fully established, as the concentration comparison between in vitro and in vivo conditions is not clearly presented
- The antimicrobial development relevance is speculative and not supported by direct experimental evidence
- The quantitative claims regarding percentages of EcSSB-GFP signal in foci lack visible statistical support (sample sizes, replicates, tests)
- The claim that EcSSB-GFP foci are representative of endogenous EcSSB behavior relies on the assumption that the fusion protein behaves identically to the wild-type, which is supported by growth comparisons but not by direct biochemical or functional equivalence tests
- The in vitro data are described as supporting the in vivo interpretation, but the specific conditions (e.g., protein concentrations, salt conditions, crowding agents) are not fully described in the visible text, limiting assessment of physiological relevance