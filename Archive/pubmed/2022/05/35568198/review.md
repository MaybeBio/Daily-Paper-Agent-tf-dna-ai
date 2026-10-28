## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, experimental procedures, and data availability statements
- **Assessment boundary** Scientific content, technical soundness, structural and mechanistic claims, and consistency of evidence presented in the manuscript
- **Shared manuscript claim summary** The manuscript reports that PhlH, a TetR-family regulator from Pseudomonas fluorescens, coordinates production of multiple secondary metabolites (2,4-DAPG, mupirocin, pyoverdine) by sensing bacterial and plant signaling molecules. Crystal structures of apo- and 2,4-DAPG-bound PhlH reveal a ligand-induced closed-to-open conformational transition driven by a pendulum-like movement of the DNA-binding domains. Molecular dynamics simulations and mutagenesis identify conserved hydrogen-bonding interactions (H76-K144, R124-F33/A34) that stabilize distinct conformational states and mediate allosteric signal transduction.
- **Visible evidence base** Proteomics data (Fig. 1, Table S1), crystal structures of apo-PhlH (2.4 Å) and 2,4-DAPG-bound PhlH (2.1 Å), EMSA data (Figs. 3, 6B), ITC data (Table 1, Fig. 6A), MD simulation PMF profiles (Fig. 5), sequence similarity network and genomic neighborhood analysis (Fig. 7), structural comparisons with other TetR regulators (Fig. 8)
- **Missing materials affecting confidence** Electron density maps and refinement statistics are not shown in the main text (only referenced in Table S4, not provided). Coordinates are deposited (PDB 7E1L, 7E1N) but not independently verified here. Full proteomics dataset details and statistical analysis parameters are not fully described. MD simulation convergence criteria and force field parameters for the ligand are not fully detailed. The manuscript text contains apparent typographical errors (e.g., "β-dation" in Discussion, "recources" in Acknowledgments) that suggest incomplete proofreading.

## Reviewer
- **Overall assessment** This manuscript presents a structurally and biochemically compelling study of PhlH, a TetR-family regulator that coordinates secondary metabolite production in response to both bacterial and plant signaling molecules. The crystallographic work is of good quality, and the combination of structural, biochemical, and computational approaches provides a coherent model for ligand-induced allosteric regulation. The finding that PhlH adopts a closed (DNA-binding competent) conformation in the apo state, opposite to most characterized TetR regulators, is notable and potentially significant. However, several technical concerns regarding the proteomics data interpretation, the indirect nature of the evidence linking PhlH to mupirocin and pyoverdine regulation, and the limited experimental validation of the proposed allosteric mechanism warrant careful consideration. The manuscript would benefit from additional experimental support for the physiological relevance of the proposed regulatory network and from clarification of certain methodological details.

- **Who would be interested in the results, and why** Researchers in bacterial signal transduction, TetR-family transcriptional regulation, secondary metabolite biosynthesis, and rhizosphere microbiology would find this work of interest. The structural insights into ligand recognition and allosteric switching in a TetR regulator with dual ligand specificity (bacterial and plant molecules) have implications for understanding metabolic coordination in beneficial rhizobacteria and for engineering biocontrol strains. The proposed conserved allosteric mechanism may also be relevant to the broader TetR regulator family.

- **Major strengths**
  1. The crystallographic structures of both apo- and ligand-bound PhlH provide a clear structural framework for understanding the allosteric mechanism, with the closed-to-open transition well supported by the observed conformational differences.
  2. The combination of structural biology, biochemistry (EMSA, ITC), and computational approaches (MD, GaMD) provides a multi-pronged and largely consistent picture of the regulatory mechanism.
  3. The identification of specific hydrogen-bonding interactions (H76-K144, R124-F33/A34) that stabilize distinct conformational states, supported by both simulation and mutagenesis, is a strong and testable mechanistic proposal.
  4. The comparative analysis with other TetR regulators and the sequence similarity network analysis provide useful evolutionary and functional context.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for physiological claims
- **Claim pointer** The manuscript claims that PhlH coordinates the production of 2,4-DAPG, mupirocin, and pyoverdine, and that this coordination is mediated by sensing both bacterial (2,4-DAPG) and plant (flavonoid) signaling molecules.
- **Evidence pointer** Fig. 1, Table S1, Discussion section
- **Concern** The proteomics data (Fig. 1) show differential expression of proteins involved in mupirocin and pyoverdine biosynthesis in the ΔphlH strain, but the fold changes are described as "around 1.5," which is near the threshold of 1.5 used for significance. The manuscript does not provide validation of these proteomics findings by independent methods (e.g., qRT-PCR, Western blot, or targeted metabolomics). Furthermore, the claim that PhlH "coordinates" production of these metabolites implies a regulatory hierarchy that is not directly demonstrated. The Discussion section speculates on a model where 2,4-DAPG and plant flavonoids signal PhlH to shift metabolic priorities, but this model is not tested experimentally.
- **Why it matters** The physiological relevance of the structural findings depends on the robustness of the claim that PhlH genuinely regulates these biosynthetic pathways. If the proteomics changes are marginal or not reproducible, the broader significance of the study is substantially weakened. The proposed coordination model is central to the title and abstract and requires stronger experimental support.
- **Resolution test** Provide independent validation of the proteomics results (e.g., qRT-PCR for representative genes in each pathway). Include targeted metabolomics or bioassays to demonstrate functional changes in 2,4-DAPG, mupirocin, and pyoverdine production in the ΔphlH strain. Ideally, complement the ΔphlH strain with the phlH gene to confirm that observed changes are specifically due to phlH deletion.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of structural interpretation
- **Claim pointer** The manuscript claims that 2,4-DAPG binding induces a closed-to-open conformational transition in PhlH, with the apo form adopting a DNA-binding competent (closed) conformation and the ligand-bound form adopting a DNA-binding incompetent (open) conformation.
- **Evidence pointer** Figs. 2, 4, Table S4
- **Concern** The structural comparison between apo- and 2,4-DAPG-bound PhlH is central to the proposed allosteric mechanism. However, the manuscript does not provide sufficient details on the quality of the electron density maps, particularly for the ligand-binding site and the regions that undergo conformational changes (e.g., α4, α7, α8 helices). The refinement statistics are only referenced in Table S4, which is not provided in the submitted materials. Without clear evidence of well-defined density for 2,4-DAPG and for the conformationally mobile regions, the interpretation of the conformational differences could be compromised. Additionally, the manuscript does not discuss whether the observed conformational differences could be influenced by crystal packing or by the different crystallization conditions used for the two forms.
- **Why it matters** The central mechanistic claim rests on the reliability of the two crystal structures and the interpretation of their differences. If the structural evidence is not robust, the proposed allosteric mechanism is not established.
- **Resolution test** Provide the refinement statistics and representative electron density maps (2Fo-Fc and Fo-Fc omit maps for the ligand) in the main text or supplementary materials. Discuss potential effects of crystal packing on the observed conformational states. If possible, validate the conformational transition using an orthogonal method such as small-angle X-ray scattering (SAXS) or hydrogen-deuterium exchange mass spectrometry (HDX-MS).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational methodology and interpretation
- **Claim pointer** The manuscript claims that molecular dynamics simulations confirm two distinct conformational states stabilized by specific hydrogen-bonding interactions, and that disruption of these hydrogen bonds has profound effects on the conformational transition.
- **Evidence pointer** Fig. 5, Methods section (MD simulation)
- **Concern** The MD simulation results are used to support the proposed allosteric mechanism, but several methodological details are unclear. The force field parameters for 2,4-DAPG are not described (the text mentions GAFF for the ligand but the atom types and charges are described for "indole," which appears to be a typographical error). The convergence of the simulations is not demonstrated (e.g., no RMSD time series or block analysis). The PMF calculations are described but the method used (e.g., umbrella sampling, metadynamics, or a simple histogram) is not specified. The GaMD simulation is mentioned but the boost parameters and validation are not provided. Without these details, the reliability of the computational conclusions cannot be fully assessed.
- **Why it matters** The MD simulations provide key support for the proposed mechanism, particularly the role of H76-K144 and R124-F33/A34 interactions in stabilizing distinct conformational states. If the simulations are not technically sound or are not converged, the conclusions drawn from them are weakened.
- **Resolution test** Provide full details of the simulation setup, including force field parameters for 2,4-DAPG, the method used for PMF calculation, and convergence criteria. Show RMSD time series and representative snapshots from the simulations. If possible, validate the key predictions (e.g., the role of H76-K144) with additional mutagenesis experiments targeting the proposed hydrogen-bonding network.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance of the proposed mechanism
- **Claim pointer** The manuscript claims that the proposed allosteric mechanism is conserved among PhlH homologs and may apply to other TetR-family regulators.
- **Evidence pointer** Figs. 7, 8, Discussion section
- **Concern** The sequence similarity network analysis (Fig. 7) shows the distribution of PhlH homologs, and the multiple sequence alignment (Fig. S4) indicates that the ligand-binding residues are variable while the conformational switch residues (F33, A34, R124) are conserved. However, the functional significance of this conservation is not tested. The comparison with other TetR regulators (Fig. 8B) is based on structural superposition of a limited number of structures, and the claim that the proposed mechanism is "well-conserved" is an extrapolation that goes beyond the data presented. The manuscript does not demonstrate that the conserved residues are functionally important in any homolog other than PhlH.
- **Why it matters** The broader significance of the study depends on the generality of the proposed mechanism. If the mechanism is specific to PhlH, the impact is more limited. The current evidence is suggestive but not conclusive.
- **Resolution test** Test the functional importance of the conserved residues in at least one additional PhlH homolog or closely related TetR regulator. Alternatively, temper the claims of conservation and focus on the PhlH-specific mechanism.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and accuracy of writing
- **Affected element** Discussion section, first paragraph
- **Evidence pointer** Discussion section, "β-dation" appears to be a typographical error
- **Issue** The text reads "fatty acid β-dation" which appears to be a typo for "β-oxidation." This is a factual error in the description of the pathway.
- **Required correction** Correct "β-dation" to "β-oxidation."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** EMSA methodology
- **Evidence pointer** Methods section, "Electrophoretic mobility shift assay"
- **Issue** The EMSA buffer composition is described as containing "0 mM Tris-HCl at pH 8.0," which is likely a typo (should be a nonzero concentration). The concentration of the labeled DNA probe and the protein concentration ranges used are not specified.
- **Required correction** Correct the buffer composition and provide the concentrations of DNA and protein used in the EMSA experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Proteomics analysis
- **Evidence pointer** Fig. 1, Methods section
- **Issue** The proteomics analysis criteria are described as "fold change greater than 1.5 and p-value less than 0.05," but the number of biological replicates, the statistical test used, and the multiple testing correction method are not specified. The volcano plot in Fig. 1A does not show the significance threshold lines.
- **Required correction** Provide details on the number of replicates, the statistical test, and the multiple testing correction. Add threshold lines to the volcano plot for clarity.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Fig. 5
- **Evidence pointer** Fig. 5
- **Issue** The PMF plots in Fig. 5 are described in the text but the figure itself is not provided in the submitted materials. The axes labels and units are not described in the text.
- **Required correction** Ensure the figure is included with clear axis labels and units. Describe the PMF calculation method in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency of data presentation
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The ITC data in Table 1 show thermodynamic parameters for WT and mutant PhlH proteins, but the number of replicates and the errors associated with the measurements are not reported.
- **Required correction** Report the number of replicates and the standard deviations or standard errors for the ITC measurements.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Acknowledgments section
- **Evidence pointer** Acknowledgments section
- **Issue** The word "recources" appears to be a typo for "resources."
- **Required correction** Correct "recources" to "resources."

## Risk / unsupported claims
1. The claim that PhlH "coordinates" production of 2,4-DAPG, mupirocin, and pyoverdine is not fully supported by the data. The proteomics evidence shows differential expression of some biosynthesis proteins, but the functional consequences for metabolite production are not directly measured.
2. The claim that the proposed allosteric mechanism is "well-conserved" among TetR-family regulators is an extrapolation based on limited structural comparisons and sequence analysis. This claim is not directly tested.
3. The proposed model that 2,4-DAPG and plant flavonoids signal PhlH to shift metabolic priorities (from antibiotic production to iron acquisition) is speculative and not experimentally tested.
4. The statement that "dissociation of 2,4-DAPG from the ligand-binding domain of PhlH was sufficient to allosterically trigger a pendulum-like movement" is based on comparison of two crystal structures and MD simulations, but the temporal sequence of events (ligand dissociation leading to conformational change) is not directly demonstrated experimentally.
5. The manuscript claims that PhlH "positively regulates fatty acid β-oxidation and biosynthesis of mupirocin, but negatively regulates biosynthesis of pyoverdine" based on proteomics data with fold changes around 1.5, which is near the significance threshold. These regulatory relationships are not validated by independent methods.