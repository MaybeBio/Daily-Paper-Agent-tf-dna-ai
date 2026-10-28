## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, methods, and references to supplementary material.
- **Assessment boundary** Scientific validity, technical soundness, and support of claims based solely on the provided manuscript text. No external data, figures, or supplementary files were available for inspection.
- **Shared manuscript claim summary** The authors report a docking-based virtual screening of a proprietary natural product library (~1000 compounds) to identify small molecules that bind the DNA minor groove at AT-rich sequences and compete with HMGA1/HMGA2 for DNA binding. Sixteen compounds were selected in silico; electrophoretic mobility shift assays (EMSAs) identified Sorocein C (compound 16) as the most effective HMGA/DNA-displacing agent, with related compounds Sorocein A (17) and Sorocein B (18) also showing activity. All three Soroceins exhibited cytotoxic effects on MDA-MB-231 breast cancer cells with IC50 values in the 29–34 μM range. The authors propose these compounds as potential lead structures for anticancer strategies based on HMGA interference.
- **Visible evidence base** Text descriptions of docking methodology and results, EMSA outcomes (qualitative, with reference to Figures 1 and S1), cytotoxicity data (IC50 values, Table 3, Figure 4), and docking scores (Table 2). No actual figures, tables, or numerical data are provided in the submitted material.
- **Missing materials affecting confidence** All figures (Figures 1–4), tables (Tables 1–3), and supplementary figures/tables (S1, S2) are referenced but not included. Raw docking scores, EMSA gel images, dose-response curves, and statistical details are unavailable. This substantially limits independent verification of the reported results.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely question, namely the identification of natural compounds that can interfere with HMGA-DNA interactions, a potentially valuable strategy for anticancer drug development. The combination of virtual screening with in vitro validation is a reasonable approach. However, the evidence presented in the text alone is insufficient to fully establish the central claims. Key quantitative data, including docking scores, EMSA quantification, and full cytotoxicity curves, are not available for scrutiny. The mechanistic link between HMGA displacement and cytotoxicity remains correlative rather than causal. The work is of interest to a specialized audience in chemical biology and cancer research, but the current evidence base does not support broad claims of therapeutic potential.
- **Who would be interested in the results, and why** Researchers in the fields of cancer biology, chromatin structure and function, and drug discovery, particularly those focused on intrinsically disordered proteins as therapeutic targets. The identification of a new chemical scaffold (Sorocein family) with HMGA-interfering activity may also interest natural product chemists and medicinal chemists seeking novel minor groove binders.
- **Major strengths** The study addresses an underexplored target class (intrinsically disordered HMGA proteins) with a rational screening strategy. The use of a diverse natural product library is a strength, as it may uncover novel chemotypes. The inclusion of structurally related compounds (Soroceins A, B, C) allows for preliminary structure-activity considerations. The authors appropriately acknowledge the need for further experiments to establish causality between HMGA displacement and cytotoxicity.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative docking data), R1-M2 (lack of EMSA quantification and controls), R1-M3 (single cell line, no mechanistic causality), R1-M4 (no selectivity assessment).
- **Assessment against Nature-style criteria** Originality: moderate. While HMGA targeting is not new, the specific compounds and screening approach offer some novelty. Scientific importance: moderate. HMGA proteins are relevant cancer targets, but the study does not yet demonstrate functional significance in a biological context. Interdisciplinary readership: limited. The work is primarily of interest to chemical biologists and cancer researchers, not a broad interdisciplinary audience. Technical soundness: not fully assessable due to missing data; the described methods are standard but the reported results cannot be verified. Readability for nonspecialists: acceptable, though some sections assume familiarity with chromatin biology and docking terminology.
- **Recommendation posture** Currently not established from the provided evidence. The core claims require access to the missing quantitative data and additional experimental validation. A revised manuscript with full data presentation and additional mechanistic experiments could be reconsidered.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that docking-based virtual screening identified 16 natural compounds as potential minor groove binders that could inhibit HMGA-DNA interaction, and that Sorocein C shows binding in the minor groove with specific H-bond interactions (Figure 2, Table 2).
- **Evidence pointer** Results and Discussion, "Docking-Based Virtual Screening" section; Figure 2; Table 2; location not provided for specific numerical values.
- **Concern** The manuscript text describes docking results qualitatively but provides no numerical data, such as binding free energies, docking scores, or statistical measures of significance. Table 2 is referenced but not included. Without these data, the ranking of compounds and the claimed superiority of Sorocein C cannot be evaluated. The specific H-bond interactions described for Sorocein C (Figure 2) are not verifiable without the figure.
- **Why it matters** The entire screening strategy rests on the validity and interpretability of the docking results. If the docking scores are not presented, readers cannot assess whether the selection of the 16 compounds was justified or whether the binding poses are chemically plausible. This is a foundational element of the study.
- **Resolution test** Provide a supplementary table with docking scores (e.g., estimated free energy of binding) for all library compounds or at least the top-ranked candidates, along with a clear description of the scoring function and selection criteria. Include Figure 2 with a detailed legend explaining the interactions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that Sorocein C, A, and B efficiently disrupt HMGA1/DNA complexes down to the lower micromolar range, based on EMSA titration assays (Figure 3).
- **Evidence pointer** Results and Discussion, "In Vitro Evaluation" section; Figure 3; location not provided for quantitative EMSA data.
- **Concern** The EMSA results are described qualitatively. No quantification of band intensities, no dose-response curves, and no statistical analysis are provided. The claim that compounds "efficiently disrupted" complexes at "lower μM concentration" is not supported by numerical data. Additionally, the text states that compounds 13 and 8 showed activity with the E3 probe but were "barely detectable" or "undetectable" with the PRDII probe, yet no explanation or quantification is offered. The lack of representative gel images (Figure 1, Figure 3, Supplementary Figure S1) prevents assessment of assay quality, such as the presence of non-specific binding or compound precipitation.
- **Why it matters** The EMSA data are the primary experimental evidence for the claimed HMGA-displacing activity. Without quantification and proper controls, the central claim of the paper is not substantiated. The differential activity across probes also raises questions about specificity that are not addressed.
- **Resolution test** Provide quantified EMSA data (e.g., fraction of bound DNA vs. compound concentration) with appropriate curve fitting and IC50 or EC50 values. Include representative gel images with clear labeling of free and bound DNA, and include negative controls (e.g., compound alone, DNA alone, and a known non-binder).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors state that Soroceins exhibit cytotoxic effects on cancer cells and suggest that this cytotoxicity could be correlated with HMGA-displacing activity.
- **Evidence pointer** Results and Discussion, "Cytotoxicity to Cancer Cells" section; Figure 4; Table 3; location not provided for IC50 values.
- **Concern** Cytotoxicity is assessed in a single cell line (MDA-MB-231) with no non-cancerous control cells. The IC50 values are reported as a range (29–34 μM) but no individual values, error bars, or statistical comparisons are provided. The authors hypothesize a correlation between HMGA displacement and cytotoxicity, but no experiments are presented to test this link, such as HMGA knockdown or overexpression, or the use of a compound that binds DNA but does not displace HMGA. The text acknowledges this limitation, but the claim remains speculative.
- **Why it matters** The therapeutic relevance of the compounds depends on demonstrating that their cytotoxic effects are related to the proposed mechanism of action. Without this, the compounds could be acting through off-target effects, and the study's conclusions are not supported.
- **Resolution test** Include full dose-response curves with individual data points and statistical analysis. Add a non-cancerous cell line to assess selectivity. Perform experiments to link HMGA displacement to cytotoxicity, such as comparing effects in HMGA-proficient vs. HMGA-depleted cells, or using a mutant HMGA that cannot bind DNA.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim support
- **Claim pointer** The authors imply that the identified compounds are selective for HMGA-DNA interactions, as they were selected based on docking to the minor groove of AT-rich DNA.
- **Evidence pointer** Results and Discussion, "Docking-Based Virtual Screening" and "In Vitro Evaluation" sections; location not provided.
- **Concern** No experiments are presented to demonstrate that the compounds do not bind to other DNA sequences or to other DNA-binding proteins. The docking was performed against a single DNA structure (PDB 3UXW), and the EMSA used only two probes (E3 and PRDII). The selectivity of the compounds for HMGA over other minor groove-binding proteins is not addressed.
- **Why it matters** If the compounds are not selective, their cytotoxic effects could be due to interference with other DNA-binding proteins, undermining the proposed mechanism. Selectivity is a key requirement for a useful chemical probe or lead compound.
- **Resolution test** Perform EMSA or other binding assays with a range of DNA sequences, including GC-rich and non-AT-rich probes. Test the compounds against other minor groove-binding proteins, such as HMG-box proteins or TATA-binding protein, to assess selectivity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Molecular Docking" section
- **Evidence pointer** Methods, "Molecular Docking"; location not provided.
- **Issue** The description of the docking protocol is brief. It is unclear how the library compounds were prepared (e.g., protonation states, tautomers), how many conformers were generated, and what the specific parameters for the genetic algorithm were (e.g., number of generations, population size). The statement "Ten runs of the genetic algorithm for each docked compound were stored and visually inspected" is vague.
- **Required correction** Provide a more detailed description of the docking protocol, including software version, ligand preparation steps, and all relevant parameters. This is necessary for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion, "Cytotoxicity to Cancer Cells" section
- **Evidence pointer** Results and Discussion, "Cytotoxicity to Cancer Cells"; location not provided.
- **Issue** The text states that "It was not possible to calculate IC50 values for Netropsin, because the cell viability was higher than 95% of the relative controls at all concentrations tested." This is presented as a limitation, but it is not clear why this is the case. Is it due to poor cell permeability, as discussed later, or to some other factor? The discussion of Netropsin's permeability is somewhat disconnected from the results.
- **Required correction** Clarify the relationship between the lack of Netropsin cytotoxicity and the discussion of its permeability. Consider moving the permeability discussion to the results section for better flow.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and Discussion, "Docking-Based Virtual Screening" section
- **Evidence pointer** Results and Discussion, "Docking-Based Virtual Screening"; location not provided.
- **Issue** The authors state that "It is not surprising that a considerable part of these compounds belongs to the chemical class of alkaloids... given their positive charge in physiological conditions." However, no data are provided on the protonation states or charges of the selected compounds. This is an assumption that should be supported or at least acknowledged as a hypothesis.
- **Required correction** Either provide computational predictions of pKa or charge states for the selected compounds, or soften the statement to indicate that this is a plausible explanation rather than a demonstrated fact.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction, final paragraph
- **Evidence pointer** Introduction, final paragraph; location not provided.
- **Issue** The sentence "These molecules share a common substructure that has not been investigated yet for the interaction with DNA" is vague. It is unclear what this common substructure is and why it is significant. This is a potentially interesting point that is not elaborated.
- **Required correction** Specify the common substructure and briefly explain why it is of interest, or remove the statement if it is not substantiated.

## Risk / unsupported claims
- The claim that Sorocein C binds in the minor groove of DNA with specific H-bond interactions (Figure 2) is unsupported without the figure and underlying docking data.
- The claim that Soroceins A, B, and C "efficiently" disrupt HMGA/DNA complexes is unsupported without quantitative EMSA data.
- The hypothesis that the cytotoxic effects of Soroceins are correlated with HMGA-displacing activity is speculative and not tested.
- The claim that the selected compounds are potential minor groove binders that could compete with HMGA is based solely on docking and limited EMSA data; no direct binding measurements (e.g., ITC, SPR, NMR) are provided.
- The selectivity of the compounds for HMGA over other DNA-binding proteins is not addressed and cannot be assessed.