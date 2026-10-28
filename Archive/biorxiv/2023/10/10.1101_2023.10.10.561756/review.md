## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplementary figure/table references) as provided on bioRxiv.
- **Assessment boundary** Scientific content, technical soundness, structural biology claims, and crystallographic methodology as described. No assessment of formatting or journal-specific style beyond Nature criteria.
- **Shared manuscript claim summary** The authors report the site-specific positioning and X-ray crystal structure determination of four minor groove binding molecules (DAPI, Hoechst 33342, netropsin, and a synthetic imidazole-pyrrole-pyrrole polyamide, IPP) within self-assembled three-dimensional DNA crystals. They demonstrate control over occupancy and spatial presentation via crystal symmetry, and report a co-crystal structure containing two different ligands at distinct sites.
- **Visible evidence base** Abstract, full introduction, results and discussion sections, materials and methods, supplementary figure/table references, accession codes, and author contributions. No supplementary PDF, PDB validation reports, or raw diffraction data were available for inspection.
- **Missing materials affecting confidence** Supplementary Information (figures S1-S26, tables S1-S10), PDB coordinate files and validation reports, electron density maps (2Fo-Fc and polder omit maps), and crystallographic data collection/refinement statistics tables. These are essential for independent verification of the structural claims.

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious and potentially valuable demonstration of using self-assembled DNA crystals as scaffolds for the structural characterization of minor groove binding molecules. The concept is timely and the inclusion of a two-ligand co-crystal is a notable step forward. However, the core claims rest heavily on crystallographic evidence that cannot be fully evaluated from the provided text alone. The resolution range (2.45-3.1 Å) is moderate, and the manuscript does not adequately address the limitations of ligand modeling at this resolution, particularly regarding the claimed reversed binding modes and the IPP dimer arrangement. The work is of interest to the DNA nanotechnology and structural biology communities, but the case for broad significance and the robustness of the structural interpretations is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers in structural DNA nanotechnology, particularly those working on DNA crystals as scaffolds for guest molecule arrangement. Also of interest to the chemical biology community studying minor groove binders and DNA-ligand interactions, and to structural biologists exploring alternative crystallization platforms for small molecule or peptide structure determination. The demonstration of controlled occupancy and multi-ligand positioning could inspire applications in nanophotonics, catalysis, and drug delivery.
- **Major strengths** 1) The concept of using programmable DNA crystals to both position and structurally characterize small molecules is original and addresses a long-standing goal in the field. 2) The demonstration of site-specific placement at two distinct locations within the same crystal lattice is a significant technical advance. 3) The systematic comparison of ligand binding modes across different crystal symmetries and occupancy states provides useful design principles. 4) The use of polder omit maps is an appropriate and rigorous approach for validating ligand placement at moderate resolution.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (crystallographic evidence not verifiable), R1-M2 (ligand binding mode reversal claims), R1-M3 (IPP dimer modeling at 3.05 Å), R1-M4 (occupancy control claim).
- **Assessment against Nature-style criteria** **Originality**: High. The use of DNA crystals as hosts for structural determination of small molecules, and the demonstration of multi-ligand positioning, is a novel contribution. **Scientific importance**: Moderate to high. The work provides a proof-of-principle that could enable future applications, but the immediate impact is limited by the moderate resolution and the lack of new biological or chemical insight beyond the demonstration itself. **Interdisciplinary readership**: Moderate. The work bridges DNA nanotechnology, structural biology, and chemical biology, but the technical nature of the crystallography may limit broader appeal. **Technical soundness**: Cannot be fully assessed from the provided material. The methodology described is appropriate, but the key structural claims require inspection of the supplementary data and PDB validation. **Readability for nonspecialists**: The manuscript is clearly written and the figures are well-referenced, but the crystallographic details and symmetry discussions may be challenging for a general audience. The abstract is accessible and conveys the significance effectively.
- **Recommendation posture** Supportive if technical concerns are resolved. The concept is promising and the work is likely to be of interest to the community, but the structural claims must be verifiable from the deposited data and supplementary information. The manuscript is not currently established from the provided evidence alone.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have solved the structures of DAPI, Hoechst, netropsin, and IPP bound to DNA crystals at resolutions of 2.45-3.1 Å, with ligand models validated by polder omit maps.
- **Evidence pointer** Results and Discussion, "Crystal structures of MGBs in self-assembling DNA lattices"; Materials and Methods, "Data Collection, Processing and Structure Solution"; Supplementary Tables 6-9 and Supplementary Figures 6-11 (not provided).
- **Concern** The core of the manuscript is the crystallographic determination of ligand-bound structures. However, none of the supporting crystallographic data (electron density maps, refinement statistics, PDB validation reports) are available for inspection. At resolutions of 2.45-3.1 Å, ligand modeling is challenging, and the distinction between alternative binding orientations or conformations can be ambiguous. The authors state that polder omit maps were calculated, which is good practice, but the actual maps and the quality of the fit are not shown. Without these data, the structural claims cannot be independently verified.
- **Why it matters** The manuscript's central contribution is the structural characterization of the ligands. If the ligand models are incorrect or over-interpreted, the conclusions regarding binding modes, occupancy, and design principles would be compromised. The scientific record requires that such claims be supported by accessible and inspectable evidence.
- **Resolution test** Provide the supplementary crystallographic tables (data collection, refinement, and validation statistics) and the electron density maps (2Fo-Fc and polder omit) for all ligand-bound structures. Deposit the coordinates and structure factors in the PDB and provide the validation reports. The authors should also discuss the real-space correlation coefficients (RSCC) or equivalent metrics for the ligands to demonstrate the reliability of the models.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report that the binding mode of DAPI reverses when placed at Pos1 compared to Pos2, and that Hoechst and netropsin also show reversed orientations relative to previously published structures.
- **Evidence pointer** Results and Discussion, "Electrostatic coordination of MGBs in the lattices"; Supplementary Figures 12-16 (not provided).
- **Concern** The claim of reversed binding modes is a significant finding, as it suggests that the DNA crystal environment can alter ligand orientation. However, at the reported resolutions (2.45-3.1 Å), distinguishing between two nearly isoenergetic orientations of a symmetric or pseudo-symmetric ligand is extremely difficult. The authors do not provide quantitative evidence (e.g., B-factors, occupancy refinement, or difference map analysis) to support the reversed orientation over the canonical one. The statement that "the models and polar contacts are in good agreement with 1D30" for DAPI at Pos2, but reversed at Pos1, raises questions about the robustness of the assignment.
- **Why it matters** If the reversed binding modes are not rigorously established, the conclusions about how crystal symmetry and lattice context influence ligand presentation would be weakened. This is a key aspect of the "design principles" the authors claim to elucidate.
- **Resolution test** Provide a detailed comparison of the fit of the canonical versus reversed ligand orientations to the electron density, including refinement statistics (e.g., R-free, RSCC) for both models. Discuss the chemical rationale for the reversed binding mode and whether it is supported by the hydrogen bonding patterns. If the reversed mode is only observed at lower resolution, acknowledge the ambiguity and temper the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have solved the structure of IPP bound to TGTCA at 3.05 Å resolution, and that the anti-parallel dimer arrangement and sequence selectivity are consistent with the original design.
- **Evidence pointer** Results and Discussion, "Crystal structure of ImPyPy-β-Dp (IPP) in the 4x5 lattice"; Supplementary Figures 18-20 (not provided).
- **Concern** The IPP structure is a central claim, as it demonstrates the ability to solve the structure of a designed polyamide with sequence specificity. However, the resolution is 3.05 Å, which is marginal for accurately modeling a small molecule with flexible tails and for defining the details of the anti-parallel dimer interface. The authors note that the initial maps did not show definitive separation for each IPP monomer, and the extended tails were not resolved. This suggests that the model may be partially speculative. The higher-resolution co-crystal with netropsin (2.45 Å) is encouraging, but the single-ligand structure at 3.05 Å is less convincing.
- **Why it matters** The IPP structure is presented as a validation of the design principles for sequence-specific polyamide binding. If the model is not well-supported by the data, the claim that the structure confirms the original design would be overstated.
- **Resolution test** Provide the electron density maps for the IPP ligand in both the single-ligand and co-crystal structures, with the model superimposed. Discuss the occupancy and B-factors of the ligand atoms, and the confidence in the placement of the flexible tails. If the tails are disordered, state this explicitly and describe how the model was built in those regions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim to control the occupancy of the guest molecules within the crystal by positioning the binding sequence at one or both minor grooves, yielding 50% or 100% occupancy.
- **Evidence pointer** Results and Discussion, "Programming the lattice for site-specific positioning of MGBs"; Figure 2 and Supplementary Figure 1 (not provided).
- **Concern** The concept of controlling occupancy is interesting, but the manuscript does not provide a quantitative analysis of occupancy. The authors state that crystals with the binding sequence at one position yield 50% occupancy, but this is not supported by refined occupancies or a comparison of electron density peak heights. The claim is plausible, but it is presented as an assumption rather than a measured result.
- **Why it matters** The ability to control occupancy is presented as a key feature of the system. If this is not rigorously demonstrated, the practical utility of the approach for applications such as controlled loading of guest molecules would be less certain.
- **Resolution test** Provide refined occupancies for the ligands in the 50% and 100% occupancy structures, or a quantitative comparison of electron density peak heights. Discuss any evidence for partial occupancy or disorder at the unoccupied sites.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, first sentence; Introduction, first paragraph
- **Issue** The phrase "has proven elusive since its conception" is vague and could be more specific about what has been elusive (e.g., the structural analysis of guests in DNA crystals, or the crystallization of such complexes).
- **Required correction** Rephrase to clearly state the specific challenge that has been difficult to overcome, such as "the structural analysis of guest molecules within rationally designed DNA crystals has remained a significant challenge since the concept was first proposed."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Results and Discussion, "Experimental design"
- **Evidence pointer** "Kd values of 1.8 nM, 38 nM, and 1.0 x nM, respectively"
- **Issue** The Kd value for netropsin is given as "1.0 x nM", which appears to be a typographical error. The value is incomplete.
- **Required correction** Correct the Kd value for netropsin to a specific number (e.g., 1.0 nM or 10 nM, depending on the source) and ensure all values are complete and accurate.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Results and Discussion, "Crystal structure of ImPyPy-β-Dp (IPP) in the 4x5 lattice"
- **Evidence pointer** "the initial maps did not show definitive separation for each IPP monomer, and the extended tails were not resolved"
- **Issue** This statement is important for assessing the reliability of the IPP model, but it is buried in the text. It should be highlighted and discussed more explicitly in the context of the model building process.
- **Required correction** Move this caveat to a more prominent position in the section and discuss how the model was built despite these limitations, including any assumptions made.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and Discussion, "Symmetry dictates lattice presentation of MGBs"
- **Evidence pointer** "see videos in Section SX"
- **Issue** The reference to "Section SX" is a placeholder and does not specify where the videos can be found in the supplementary information.
- **Required correction** Replace "Section SX" with the actual section or figure number in the supplementary information where the videos are located.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Materials and Methods, "Data Collection, Processing and Structure Solution"
- **Evidence pointer** "Known ligand coordinates (DAP, HT1, and NT) for DAPI, Hoechst 33342, and netropsin, respectively were automatically retrieved in Phenix"
- **Issue** The use of "automatically retrieved" is unclear. It would be helpful to specify the source of these coordinates (e.g., from the PDB, from a ligand library) and whether they were manually checked for consistency with the electron density.
- **Required correction** Clarify the source of the ligand coordinates and describe any manual adjustments made during model building.

## Risk / unsupported claims
- The claim that the reversed binding mode of DAPI at Pos1 is a real phenomenon is not supported by quantitative evidence in the provided text.
- The claim that the IPP structure at 3.05 Å confirms the original design rules is not fully supported, given the noted limitations in the electron density.
- The claim of controlled occupancy (50% vs 100%) is not supported by refined occupancy values or quantitative electron density analysis.
- The statement that the work "opens new potential opportunities for the use of DNA crystals to display and structurally characterize small molecules, peptides, and ultimately proteins of unknown structure" is speculative and not directly demonstrated by the results.
- The claim that the ability to position two guests in one crystal "will enable a range of applications" is forward-looking and not substantiated by experimental demonstration.