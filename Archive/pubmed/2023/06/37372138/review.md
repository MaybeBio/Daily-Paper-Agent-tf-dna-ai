## Review setup
- **Input scope** Full manuscript text (title, abstract, introduction, methods, results, discussion, conclusions) provided as plain text; no figures, tables, or supplementary materials included.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and internal consistency as presented in the text; no external literature verification or replication attempted.
- **Shared manuscript claim summary** The authors report that overexpression of the DNA-binding protein Dps in two engineered E. coli strains (Top10/pBAD-Dps and BL21-Gold(DE3)/pET-Dps) enhances survival during slow desiccation over six months, preserves DNA–Dps co-crystal integrity, and that coarse-grained molecular dynamics simulations explain the protective mechanism of Dps during dehydration.
- **Visible evidence base** Text descriptions of viability assays (CFU, Live/Dead staining), SEM and TEM observations, and MD simulation results; tables and figures referenced but not visible.
- **Missing materials affecting confidence** All figures, tables, supplementary data, strain construction details, simulation parameter files, and statistical output are absent; these are essential for verifying quantitative claims and image-based interpretations.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in bacterial stress physiology, namely the role of Dps in desiccation tolerance, and combines experimental and computational approaches. The topic is of interest to microbiologists and biotechnologists. However, the current text has several weaknesses that prevent full confidence in the conclusions. Key issues include incomplete reporting of quantitative data, ambiguous interpretation of microscopy and simulation results, and a lack of mechanistic depth linking Dps overexpression to the observed survival advantage. The claims are plausible but not fully established from the provided material.
- **Who would be interested in the results, and why** Researchers studying bacterial stress responses, desiccation tolerance, and DNA-binding proteins; biotechnologists developing preservation methods for industrial bacterial strains; and those interested in the biophysics of protein–DNA assemblies under extreme conditions.
- **Major strengths** The study tackles a poorly understood stress condition and uses a combination of experimental and computational methods. The use of two engineered strains with inducible Dps overexpression is a reasonable approach. The long-term desiccation design (six months) is a strength, as it mimics realistic environmental conditions. The MD simulations provide a molecular-level hypothesis for Dps-mediated protection.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality: moderate; the role of Dps in stress is known, and the desiccation angle is relatively underexplored, but the novelty is incremental. Scientific importance: moderate; findings could inform preservation technologies but do not fundamentally shift understanding. Interdisciplinary readership: limited; primarily microbiologists and biophysicists. Technical soundness: not fully assessable due to missing data; several methodological ambiguities. Readability for nonspecialists: acceptable but could be improved with clearer explanations of simulation and microscopy methods.
- **Recommendation posture** Supportive if technical concerns are resolved; currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that Dps overexpression leads to higher survival after desiccation, with 1.5–8.5-fold higher viable cell titers in experimental variants.
- **Evidence pointer** Section 3.1.2, Table 2, Table 3; location not provided
- **Concern** The quantitative basis for the survival claim is not verifiable from the text. The abstract states a 1.5–8.5-fold increase, but Section 3.1.3 reports an 11-fold difference for Top10 and 3-fold for BL21-Gold. These numbers are inconsistent. Additionally, the tables are not visible, so the raw data, replicates, and statistical analysis cannot be assessed. The text mentions that CFU counts became undetectable at certain points, but the criteria for "undetectable" and how this was handled in the analysis are unclear.
- **Why it matters** The central conclusion of the paper rests on the survival advantage conferred by Dps overexpression. Without consistent and verifiable quantitative data, the claim is not supported.
- **Resolution test** Provide the actual data in tables with replicate numbers, standard deviations, and statistical tests. Reconcile the discrepancy between the abstract and results sections. Clarify how undetectable CFU counts were treated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "desiccation stress leads to 'breakage' of the DNA–Dps crystal structure" based on TEM observations.
- **Evidence pointer** Section 3.2.2, Figures 4 and 5; location not provided
- **Concern** The interpretation of TEM images is not adequately supported. The text describes "dark stained regions" and "presumed 'damaged' crystal structure" but does not provide a clear definition of what constitutes a broken crystal versus an intact one. The Fourier transform analysis is mentioned but not explained in sufficient detail. The claim that these regions are "damaged" crystals is speculative, as the authors acknowledge they did not aim to study crystal structure in detail. Without a quantitative or well-defined criterion for crystal integrity, the conclusion is not robust.
- **Why it matters** The claim that Dps crystals lose their structure during desiccation is a key mechanistic point. If the interpretation is ambiguous, the mechanistic narrative is weakened.
- **Resolution test** Provide clear criteria for identifying intact versus broken crystals, ideally with quantitative measures (e.g., Fourier transform peak intensity, lattice spacing). Include representative images with scale bars and a blinded analysis if possible.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The MD simulations are used to "explain the protective function of Dps in DNA–Dps co-crystals during desiccation."
- **Evidence pointer** Section 3.3, Figures 6–8; location not provided
- **Concern** The simulation methodology is described only superficially. Key parameters such as the force field version, water model, ion concentrations, simulation box size, and equilibration protocol are mentioned but not fully specified. The results are described qualitatively (e.g., "crystal becomes denser," "DNA bends and shrinks") without quantitative metrics such as RMSD, interaction energies, or density profiles. The claim that the simulations explain the protective mechanism is not supported by the presented data.
- **Why it matters** The computational component is presented as a major contribution. Without rigorous methodology and quantitative results, the simulations do not add convincing evidence.
- **Resolution test** Provide full simulation details, including input files or a detailed methods section. Present quantitative results (e.g., energy plots, density profiles, structural parameters) with error estimates. Clearly state what the simulations demonstrate and what they do not.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The authors claim that the extracellular matrix is greater in Dps-overexpressing samples and that this helps cells survive.
- **Evidence pointer** Section 3.2.1, Figure 3; location not provided
- **Concern** The claim that Dps overexpression increases extracellular matrix production is based solely on visual assessment of SEM images. No quantitative measurement of matrix volume or composition is provided. The mechanism by which Dps, a DNA-binding protein, would increase matrix production is not explained. This is a speculative interpretation that is not supported by the data.
- **Why it matters** The matrix is proposed as a key survival factor. If this claim is not substantiated, the survival mechanism remains unclear.
- **Resolution test** Quantify matrix abundance using image analysis or biochemical assays. Provide a mechanistic explanation for how Dps overexpression leads to increased matrix production.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors state that "the majority of the population survives" after desiccation and rehydration.
- **Evidence pointer** Section 3.1.3, Table 3; location not provided
- **Concern** The survival percentages are not clearly reported. The text mentions 0.6% to 19.2% survival relative to counts at 60 days, but the baseline for this calculation is unclear. It is also not clear whether the survival is measured immediately after rehydration or after a recovery period. The claim that "the majority survives" is contradicted by the reported percentages, which are well below 50%.
- **Why it matters** The survival rate is a key outcome measure. Ambiguity in how it is calculated and reported undermines the conclusions.
- **Resolution test** Clearly define the survival calculation, including the time points and conditions. Report absolute numbers and percentages with appropriate controls.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states a 1.5–8.5-fold survival increase, but the results section reports different values (11-fold and 3-fold). This inconsistency is confusing.
- **Required correction** Align the abstract with the results section or explain the range in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Section 2.9
- **Evidence pointer** Section 2.9; location not provided
- **Issue** The DNA sequence used in simulations is described as "the part of this gene," but the gene is not named. This is ambiguous.
- **Required correction** Specify the gene and the exact DNA sequence used, or provide a reference.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Section 3.3.3
- **Evidence pointer** Section 3.3.3; location not provided
- **Issue** The sentence "DNA became" is incomplete, leaving the reader without the intended information.
- **Required correction** Complete the sentence and describe the state of DNA at this stage.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Methods, Section 2.11
- **Evidence pointer** Section 2.11; location not provided
- **Issue** The statistical methods are described as using Student's t-test, but no specific tests or p-values are reported in the results.
- **Required correction** Report p-values or confidence intervals for the key comparisons.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion, Section 4
- **Evidence pointer** Section 4; location not provided
- **Issue** The discussion includes broad statements about the importance of the work but does not clearly connect the findings to specific implications or limitations.
- **Required correction** Add a paragraph on limitations and future directions.

## Risk / unsupported claims
- The claim that Dps overexpression increases extracellular matrix production is unsupported; no quantitative data or mechanism is provided.
- The claim that DNA–Dps crystals "break" during desiccation is based on ambiguous TEM interpretation and is not fully substantiated.
- The MD simulation results are described qualitatively without sufficient methodological detail or quantitative output, making the mechanistic claims unverifiable.
- The survival percentages (0.6–19.2%) are inconsistent with the statement that "the majority of the population survives."
- The abstract and results sections report different fold-increases in survival, creating an internal inconsistency.