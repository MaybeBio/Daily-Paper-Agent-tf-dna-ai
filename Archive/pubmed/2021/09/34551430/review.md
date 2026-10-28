## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, supplementary data references)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and conclusions as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors report that azacryptand ligands TrisNP and TrisPOB bind both three-way DNA junctions (TWJs) and G-quadruplexes (G4s) in vitro with a preference for TWJs, induce DNA damage and cytotoxicity in cancer cells, and show synergistic activity when combined with DNA damage response (DDR) inhibitors. A clickable analogue, TrisNP-α, is used to visualize TWJ-like structures in cells.
- **Visible evidence base** In vitro binding assays (FRET-melting, PAGE, TWJ-Screen, ESI-MS, equilibrium dialysis), molecular dynamics simulations, cell viability assays (SRB), γH2AX immunostaining and flow cytometry, click chemistry imaging, NCI-60 screening data, and drug combination studies with DDR inhibitors.
- **Missing materials affecting confidence** Full supplementary data (including Supplementary Figures S1–S6 and Supplementary Movies 1–4) were not provided. Synthetic procedures for TrisNP-α are referenced but not included. Raw numerical data for key experiments (e.g., LD50 values, statistical analyses, combination index calculations) are not fully available for independent verification.

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting class of dual-targeting ligands for higher-order DNA structures, with a novel claim that TWJ targeting, rather than G4 targeting, drives the observed cellular effects. The in vitro characterization is reasonably thorough, and the use of a clickable probe for cellular localization is a valuable addition. However, the central claim that TWJ binding is the primary mechanism of cytotoxicity in cells is not directly demonstrated. The evidence is largely correlative, and the lack of a TWJ-specific cellular readout weakens the causal link. The synthetic lethality data are promising but require more rigorous statistical and mechanistic support. The manuscript would benefit from additional experiments that directly perturb TWJ structures or compare with a G4-selective ligand under identical conditions.
- **Who would be interested in the results, and why** Researchers in chemical biology, nucleic acid structure and function, and anticancer drug discovery would find this work of interest. The concept of multitargeting non-B DNA structures and the development of a clickable TWJ probe are conceptually appealing. The synthetic lethality strategy with DDR inhibitors may also attract interest from translational oncology groups.
- **Major strengths** 1. The in vitro binding data are multi-faceted and consistently indicate a preference for TWJs over G4s. 2. The design and use of a clickable analogue (TrisNP-α) for cellular imaging is a methodological strength. 3. The comparison with a known G4 ligand (PDS) highlights a distinct mechanism of action. 4. The synthetic lethality approach with clinically relevant DDR inhibitors is timely and potentially impactful.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim-evidence alignment
  - **Claim pointer** The abstract and discussion state that the cellular effects are "attributable to TWJ targeting" and that TrisNP-α "preferentially targets DNA junctions in cells."
  - **Evidence pointer** Results sections "Azacryptands are cytotoxic and induce DNA damage", "Traceable TrisNP analogue localizes in nucleoli and nucleoplasm", and "DNA junction ligands are synthetically lethal with DDR inhibitors"; Figures 4 and 5.
  - **Concern** The manuscript does not provide direct evidence that the cytotoxic and DNA-damaging effects of TrisNP/TrisPOB are caused by binding to TWJs in cells. The cellular imaging data show localization of TrisNP-α to nucleoli and perinucleolar regions, but this is not demonstrated to be TWJ-specific. The lack of colocalization with BG4 (a G4 antibody) is suggestive but not conclusive, as BG4 may not detect all G4s and the staining patterns are not quantitatively compared. The modulation of staining intensity by BNS-22 and Aphi is correlative and does not establish a causal relationship between TWJ stabilization and the observed phenotypes.
  - **Why it matters** The central novelty of the paper rests on the claim that TWJ targeting is the mechanism of action. Without direct evidence (e.g., a TWJ-specific reporter, a mutant cell line with altered TWJ metabolism, or a ligand with differential TWJ vs. G4 affinity that shows a corresponding difference in cellular activity), the conclusion remains speculative. This weakens the overall impact and the proposed therapeutic rationale.
  - **Resolution test** Provide direct evidence that TrisNP/TrisPOB bind to TWJs in cells. This could be achieved by: (a) a proximity ligation assay or chromatin immunoprecipitation using a TWJ-specific antibody; (b) a cellular reporter system where TWJ formation is inducible and measurable; (c) a structure-specific DNA damage assay that distinguishes TWJ- from G4-mediated damage; or (d) a structure-activity relationship study with a panel of ligands with varying TWJ/G4 selectivity, showing a correlation between TWJ affinity and cytotoxicity.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The synthetic lethality section claims "strong synergy" between TrisNP and DDR inhibitors, with average CI values of 0.71, 0.64, and 0.49 for DNA-PKi, ATMi, and RAD51i, respectively.
  - **Evidence pointer** Results section "DNA junction ligands are synthetically lethal with DDR inhibitors"; Figure 6.
  - **Concern** The combination index (CI) values are presented as averages, but the variability across replicates is not reported. The Chou-Talalay method requires careful attention to the dose-effect relationships of each drug alone and in combination. The manuscript does not provide the full isobologram data or the confidence intervals for the CI values. Furthermore, the mechanism of synergy is not explored. It is unclear whether the synergy arises from enhanced DNA damage, impaired repair, or an off-target effect. The claim of "strong synergy" is not fully supported by the data as presented.
  - **Why it matters** Synthetic lethality is a clinically relevant concept, and the claim of synergy is a key translational aspect of the paper. If the synergy is not robust or is not mechanistically linked to TWJ/DDR interplay, the therapeutic potential is overstated. The lack of statistical rigor undermines the reliability of the conclusion.
  - **Resolution test** Provide full dose-response matrices, CI values with standard deviations or confidence intervals for each drug combination ratio, and a statistical test (e.g., combination index analysis with CompuSyn or a similar tool) to confirm synergy. Include a mechanistic experiment, such as measuring DNA damage (γH2AX) and repair foci (53BP1, RAD51) in combination treatments, to demonstrate that the synergy is due to enhanced unrepaired DNA damage.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The molecular dynamics simulations are used to propose distinct binding modes for TrisPOB and TrisNP with TWJs, including a transient inclusion complex for TrisNP.
  - **Evidence pointer** Results section "Insights into how TrisNP and TrisPOB interact with TWJs"; Figure 3.
  - **Concern** The MD simulations are described briefly, and the methods for docking, force field parameters, and simulation length are not provided in the main text (referenced to supplementary data). The claim of a "transient inclusion complex" is based on a low-population state (ca. 1% of simulation time), which may not be biologically relevant. The functional significance of this binding mode is not tested experimentally.
  - **Why it matters** The proposed binding modes are used to rationalize the different cellular activities of the two ligands. If the simulations are not robust or the key binding mode is a rare event, the mechanistic interpretation is weakened. The link between the simulated binding mode and the observed biological effects is not established.
  - **Resolution test** Provide full details of the MD simulation parameters and convergence analysis. Validate the proposed binding modes with experimental data, such as NMR or X-ray crystallography, or with mutagenesis of the TWJ structure. If the inclusion complex is functionally important, design a mutant ligand that cannot form it and show a loss of activity.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first paragraph
  - **Issue** The abstract states that the ligands "demonstrate cellular effects distinct from that of G4 ligands, and attributable to TWJ targeting." This is a strong claim that is not fully supported by the data, as noted in R1-M1. The wording should be softened to reflect the correlative nature of the evidence.
  - **Required correction** Revise to "…demonstrate cellular effects distinct from that of G4 ligands, suggesting a role for TWJ targeting."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods
  - **Evidence pointer** Methods section "FRET-melting assay"
  - **Issue** The FRET-melting assay is described, but the exact buffer conditions, heating/cooling rates, and data analysis methods are not fully specified. This limits reproducibility.
  - **Required correction** Provide full experimental details, including buffer composition, temperature ramp rates, and the method for determining T1/2 (e.g., first derivative of the melting curve).
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results
  - **Evidence pointer** Results section "Azacryptands are cytotoxic and induce DNA damage"; Figure 4
  - **Issue** The γH2AX quantification data are presented as percentages of cells with >5 and >10 foci, but the number of independent experiments and the statistical test used are not stated in the main text.
  - **Required correction** State the number of biological replicates and the statistical test used (e.g., unpaired t-test with Welch's correction) and report the p-values.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion
  - **Evidence pointer** Discussion, second paragraph
  - **Issue** The discussion states that "azacryptands could prove useful to treat cancers that have developed resistance to TOP2 poisons." This is speculative and not directly tested in the manuscript.
  - **Required correction** Reframe as a hypothesis: "This raises the hypothesis that azacryptands could be useful in cancers resistant to TOP2 poisons, which warrants further investigation."
- **Technical failings that need to be addressed before the case is established** 1. Lack of direct evidence for TWJ binding in cells (R1-M1). 2. Incomplete statistical reporting for synergy data (R1-M2). 3. Insufficient detail on MD simulation methods and validation (R1-M3). 4. Missing raw data for key experiments (LD50 values, flow cytometry histograms, CI calculations).
- **Assessment against Nature-style criteria**  
  *Originality*: The concept of dual TWJ/G4 targeting is a novel extension of the multitargeting idea, and the clickable probe is a useful tool. However, the originality is somewhat tempered by the fact that the cellular mechanism is not definitively established.  
  *Scientific importance*: If the TWJ-mediated mechanism is confirmed, this would be an important contribution to the field of non-B DNA biology and anticancer drug development. The synthetic lethality data are potentially significant.  
  *Interdisciplinary readership*: The topic bridges chemistry, biology, and oncology, and would appeal to a broad audience. The writing is generally accessible, though some sections (e.g., MD simulations) may be challenging for non-specialists.  
  *Technical soundness*: The in vitro binding studies are well-executed, but the cellular and in silico studies have gaps in methodology and statistical reporting. The overall technical rigor is not yet at the level required for a high-impact journal.  
  *Readability for nonspecialists*: The abstract and introduction are clear, but the results section is dense and would benefit from more explicit explanations of the significance of each experiment.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the in vitro data are solid, but the central claim of TWJ-mediated cellular activity requires direct experimental validation. The synergy data need more rigorous statistical analysis. If these issues are addressed, the manuscript could be suitable for publication.

## Risk / unsupported claims
- The claim that cellular effects are "attributable to TWJ targeting" is not directly supported by the evidence presented.
- The claim of "strong synergy" with DDR inhibitors is not statistically substantiated.
- The proposal that azacryptands could treat TOP2 poison-resistant cancers is speculative and not tested.
- The statement that TrisNP-α "preferentially targets DNA junctions in cells" is based on indirect evidence (lack of colocalization with BG4) and is not quantitatively validated.
- The biological relevance of the "transient inclusion complex" observed in MD simulations is not established.