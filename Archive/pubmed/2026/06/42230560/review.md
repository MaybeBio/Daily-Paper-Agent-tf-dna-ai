## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure/table legends as embedded in the text.
- **Assessment boundary** Scientific content, technical soundness, structural biology claims, biochemical validation, computational methodology, and consistency of conclusions with presented evidence. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors report the first crystal structures of human SMUG1, including an apo form at 1.38 Å, product complexes with uracil and 5-fluorouracil, and an enzyme-product complex with double-stranded DNA. They identify key residues for DNA binding and catalysis, propose a post-excision uracil rotation mechanism supported by molecular dynamics simulations and free energy calculations, and present neutron diffraction data to determine protonation states of catalytic residues.
- **Visible evidence base** X-ray crystal structures (apo, uracil complex, 5FU complex, dsDNA complex), neutron diffraction data, molecular dynamics simulations, free energy perturbation calculations, fluorescence-based activity assays, microscale thermophoresis binding measurements, and sequence/structure comparisons with related glycosylases.
- **Missing materials affecting confidence** Electron density maps and refinement statistics are referenced as supplementary but not fully visible in the provided text. Coordinates and structure factors are deposited but not independently verified here. Full details of MD simulation convergence, force field validation, and FEP error analysis are not fully described in the visible text. The neutron diffraction structure is mentioned but its refinement details and quality metrics are not fully presented.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and long-awaited structural characterization of human SMUG1, a key enzyme in base excision repair. The work fills a significant gap, as no human SMUG1 structure has been previously reported despite extensive biochemical characterization. The crystal structures are of high quality, with the apo structure at 1.38 Å and the uracil complex at 0.95 Å representing excellent resolution. The identification of arginine residues R124, R215, and R243 as critical for DNA binding is well supported by mutagenesis and binding data. The proposed uracil rotation mechanism following excision is intriguing and supported by multiple complementary approaches, though the functional significance remains somewhat speculative. The neutron diffraction data add a unique dimension by directly determining protonation states. However, several concerns regarding the interpretation of the product complexes, the functional relevance of the rotation mechanism, and the discrepancy with a previous report on R243A activity need to be addressed. Overall, this is a valuable contribution that will be of interest to the DNA repair and structural biology communities.

- **Who would be interested in the results, and why** DNA repair researchers, particularly those studying base excision repair and uracil DNA glycosylases, will find the structural information directly relevant to understanding substrate recognition and catalysis. Structural biologists interested in protein-DNA interactions and base-flipping mechanisms will appreciate the detailed structural analysis. Cancer biologists may find relevance given the role of SMUG1 in chemotherapy response, particularly to 5-fluorouracil. Drug discovery scientists targeting DNA repair enzymes for cancer therapy will benefit from the structural framework presented. The neutron diffraction work will interest the broader structural biology community as a demonstration of this technique for determining protonation states in enzyme active sites.

- **Major strengths**
  1. First structural characterization of human SMUG1, filling a significant gap in the field.
  2. High-resolution structures, particularly the 0.95 Å uracil complex, enabling detailed analysis of active site interactions.
  3. Multi-technique approach combining X-ray crystallography, neutron diffraction, MD simulations, FEP calculations, and biochemical assays.
  4. Clear identification and validation of key DNA-binding residues through mutagenesis and binding studies.
  5. The proposed uracil rotation mechanism is novel and supported by multiple lines of evidence.
  6. Direct determination of protonation states of catalytic residues via neutron diffraction.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance of proposed mechanism
- **Claim pointer** The authors propose that uracil rotation following excision is functionally important, potentially preventing the reverse reaction and contributing to product inhibition relief.
- **Evidence pointer** Results section "SMUG1 product complexes suggest potential base rotation following cleavage"; Discussion section; Figures 4 and 5
- **Concern** The functional significance of the proposed uracil rotation mechanism is not directly tested. While the structural and computational data support the existence of a rotated conformation, the authors do not provide experimental evidence that this rotation is functionally relevant. The claim that rotation prevents re-ligation of uracil to the AP site is speculative. No mutagenesis experiments targeting residues that would specifically disrupt the rotated conformation (while preserving the native conformation) are presented. The authors should either provide direct experimental evidence for the functional role of rotation or temper the claims about its biological significance.
- **Why it matters** The rotation mechanism is presented as a key finding of the paper. Without functional validation, the biological relevance of this observation remains uncertain. The DNA repair field has seen multiple examples where structurally observed conformational changes do not translate to functional significance in vivo. The authors' conclusion that rotation is part of the product release mechanism needs experimental support.
- **Resolution test** Provide mutagenesis data on residues that specifically stabilize or destabilize the rotated conformation and test their effects on product inhibition, catalytic efficiency, or product release kinetics. Alternatively, use single-molecule approaches to directly observe rotation events and correlate them with catalytic turnover.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Discrepancy with previous functional data
- **Claim pointer** The authors report that the R243A mutation significantly reduces both DNA binding affinity and catalytic activity, contradicting a previous 2007 study that showed this mutant retained near-wild-type activity.
- **Evidence pointer** Results section "SMUG1-arginine-to-alanine mutants lose affinity and activity towards dsDNA"; Discussion section; Figure 6; Table 1
- **Concern** The authors acknowledge a discrepancy with a 2007 study (reference 40) where R243A was reported to be nearly as active as wild-type. The authors attribute this to differences in assay conditions, specifically substrate concentration. However, the magnitude of the discrepancy is large: the authors report a 7-fold reduction in kcat/Km, while the previous study reported near-wild-type activity. The authors should more thoroughly investigate this discrepancy. For example, they could test the R243A mutant under the exact conditions of the previous study, or use the same substrate as the previous study. The current explanation, while plausible, is not fully convincing without direct comparison.
- **Why it matters** The functional importance of R243 is a central claim of the paper. If the previous report is correct, the interpretation of R243's role in DNA binding and catalysis would need substantial revision. The discrepancy also raises questions about the robustness of the activity assay used in this study.
- **Resolution test** Perform side-by-side activity assays using both the fluorescent substrate used in this study and the radiolabeled substrate used in the 2007 study, under identical conditions. If the discrepancy persists, provide additional structural or biophysical evidence that R243 is critical for function.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of product complex structures
- **Claim pointer** The authors interpret the dsDNA complex as an enzyme-product complex representing a post-excision state, with the AP site in the DNA and uracil absent from the active site.
- **Evidence pointer** Results section "hSMUG1 binds to DNA via R124, R215 and region H239-K249"; Figure 3
- **Concern** The dsDNA complex was obtained by co-crystallization with a uracil-containing substrate, and the resulting structure shows an AP site, indicating that catalysis occurred during crystallization. The authors interpret this as a product complex. However, it is unclear whether this represents a true product inhibition state or an artifact of the crystallization conditions. The authors should clarify whether the AP site is in the expected conformation for a natural product complex and whether the DNA conformation observed is consistent with other glycosylase product complexes. Additionally, the authors should discuss whether the low pH of the crystallization condition (pH 4.9) could affect the interpretation.
- **Why it matters** The product complex is used to support the proposed mechanism of product inhibition and the role of specific residues in DNA binding. If the complex does not accurately represent the physiological product state, the conclusions drawn from it may be compromised.
- **Resolution test** Compare the AP site conformation and DNA distortion with other published glycosylase product complexes. Perform structural analysis at different pH conditions or use a catalytically inactive mutant to capture a true substrate complex.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Computational methodology and validation
- **Claim pointer** The MD simulations and FEP calculations support the rotated uracil conformation as energetically favorable and stable.
- **Evidence pointer** Methods section "Computational methodology"; Results section "SMUG1 product complexes suggest potential base rotation following cleavage"; Supplementary Figures 7, 10
- **Concern** The computational results are presented as supporting evidence for the rotation mechanism, but the methodology has several potential issues. First, the FEP calculations use the OPLS-AA/M force field while the MD simulations use AMBER force fields, and the consistency between these approaches is not discussed. Second, the convergence of the FEP calculations is not fully demonstrated. Third, the authors should provide more details on the error analysis and statistical significance of the 1.59 kcal/mol free energy difference. Fourth, the simulations of the ternary product complexes are relatively short (300 ns) and may not sample all relevant conformational states.
- **Why it matters** The computational results are a key pillar of the rotation mechanism proposal. If the calculations are not robust, the conclusions drawn from them are weakened.
- **Resolution test** Provide convergence plots for the FEP calculations, show block error analysis, and discuss the consistency between force fields. Consider extending the simulations or using enhanced sampling methods to verify the stability of the rotated conformation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Neutron diffraction data quality and interpretation
- **Claim pointer** The neutron diffraction data at 2.3 Å resolution directly determine the protonation states of key catalytic residues, including H239 and N85.
- **Evidence pointer** Methods section "Neutron diffraction experiments"; Results section "SMUG1 product complexes suggest potential base rotation following cleavage"; Supplementary Figures 9
- **Concern** Neutron diffraction at 2.3 Å resolution is challenging, and the authors should provide more details on the quality of the nuclear density maps. The assignment of protonation states based on neutron data requires careful validation, especially for residues with ambiguous density. The authors should provide quantitative measures of map quality, such as the nuclear density map correlation coefficients, and discuss the confidence in the protonation state assignments. Additionally, the authors should clarify whether the neutron structure is the same as the X-ray structure or a separate refinement.
- **Why it matters** The protonation states of catalytic residues are important for understanding the catalytic mechanism. If the assignments are uncertain, the mechanistic conclusions drawn from them are weakened.
- **Resolution test** Provide detailed statistics for the neutron refinement, including R-factors, map quality indicators, and omit maps for the key residues. Consider validating the protonation states with quantum mechanical calculations or other independent methods.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the structures "suggest a mechanism by which the substrate uracil rotates following base excision" but does not clearly state the proposed functional significance of this rotation. The abstract would benefit from a more explicit statement of the proposed biological role.
- **Required correction** Clarify in the abstract whether the rotation is proposed to prevent re-ligation, facilitate product release, or serve another function.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Activity assay methodology
- **Evidence pointer** Methods section "Fluorescence-based hSMUG1 enzyme activity assay"
- **Issue** The assay description mentions that experiments were performed twice with data points in triplicate, but does not specify the statistical analysis used to determine kinetic parameters and errors. The authors should clarify how kcat and Km values were calculated and what error estimates are reported.
- **Required correction** Provide details on the fitting procedure, error analysis, and the number of independent experiments used for each reported kinetic parameter.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Structural comparison
- **Affected element** Discussion of SMUG1 vs. UNG2 substrate specificity
- **Evidence pointer** Discussion section; Supplementary Figure 18
- **Issue** The comparison with UNG2 substrate specificity is informative but brief. The authors could strengthen this section by providing a more detailed structural comparison of the active site residues that determine substrate specificity between SMUG1 and UNG2.
- **Required correction** Expand the discussion of structural determinants of substrate specificity, potentially with a supplementary figure showing a detailed active site overlay.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Structure deposition
- **Evidence pointer** Methods section "Structure determination"
- **Issue** The authors state that structures are deposited in the PDB but do not provide validation metrics or a summary of structure quality in the main text. While this is common practice, a brief statement of the overall structure quality would be helpful.
- **Required correction** Add a sentence in the results or methods summarizing the key refinement statistics for each structure.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Figure 6
- **Evidence pointer** Figure 6
- **Issue** The activity assay data in Figure 6B would benefit from showing individual data points rather than only mean ± SD, especially given the small number of experiments (n=2).
- **Required correction** Consider showing individual data points in the figure or providing a supplementary figure with the full dataset.

## Risk / unsupported claims
1. The claim that uracil rotation following excision is functionally important for preventing the reverse reaction is not directly supported by experimental evidence. The structural and computational data show that rotation can occur, but the functional significance is inferred rather than demonstrated.
2. The statement that the dsDNA complex represents a "catalytically competent state" is not fully supported. The complex contains an AP site, indicating that catalysis has already occurred, and the authors themselves describe it as a "relaxed, product inhibited state."
3. The claim that the neutron diffraction data "clearly" show the protonation states of key residues may be overstated given the 2.3 Å resolution and the inherent challenges of neutron crystallography. The authors should provide more quantitative evidence for the confidence in these assignments.
4. The suggestion that the negatively charged surface of SMUG1 may mediate interactions with protein partners such as DKC1 is speculative and not supported by any direct experimental evidence in this manuscript.
5. The statement that the structural information "will be vital for the future development of inhibitors and/or activators" is a reasonable outlook but is not a claim supported by the data presented.

## Assessment against Nature-style criteria
- **Originality** High. This is the first structural characterization of human SMUG1, a key enzyme in base excision repair. The structures fill a significant gap in the field, as only the Xenopus ortholog has been previously characterized. The neutron diffraction data add a unique dimension by directly determining protonation states in the active site.
- **Scientific importance** High. SMUG1 is important for genomic stability and has been implicated in cancer biology and chemotherapy response. Understanding its structure and mechanism has implications for DNA repair research and potentially for drug development. The proposed uracil rotation mechanism, if validated, would be a novel contribution to understanding glycosylase product release.
- **Interdisciplinary readership** Moderate to high. The work will primarily interest structural biologists and DNA repair researchers. The neutron diffraction component may attract interest from the broader structural biology community. The potential implications for cancer therapy may draw interest from cancer biologists, though this is not the primary focus.
- **Technical soundness** Generally strong, with some concerns. The X-ray crystallography appears well-executed with high-resolution structures. The biochemical validation is appropriate. The computational methodology is reasonable but has some potential issues with force field consistency and convergence that should be addressed. The neutron diffraction work is ambitious but the quality of the data and the confidence in protonation state assignments need further validation.
- **Readability for nonspecialists** Good. The manuscript is clearly written and the figures are well-designed. The introduction provides sufficient background for readers unfamiliar with base excision repair. The discussion effectively contextualizes the findings. Some sections, particularly the computational methods, may be challenging for nonspecialists but are not excessively technical.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents valuable structural data that fills a significant gap in the field. The quality of the crystallographic work is high, and the multi-technique approach is commendable. However, the functional significance of the proposed uracil rotation mechanism needs to be more directly tested or the claims tempered. The discrepancy with the previous R243A study needs to be more thoroughly investigated. The computational methodology should be more rigorously validated. If these concerns are adequately addressed, this work would be suitable for publication in Nature Communications.