## Review setup
- **Input scope** Full manuscript text (Results, Discussion, Materials and Methods, Figure legends embedded in text)
- **Assessment boundary** Structural and biochemical characterization of AlgU-MucAcyto complex and SspB-mediated degradation in *P. aeruginosa*; functional claims based on knockout phenotypes
- **Shared manuscript claim summary** The authors report the crystal structure of the *P. aeruginosa* AlgU-MucAcyto complex at 2.1 Å resolution, obtained via a fusion protein strategy. They identify an extensive charged/polar interaction network at the interface, show that multi-site alanine mutations do not disrupt binding but reduce thermal stability, and propose SspB as a dual-interface adaptor that bridges the AlgU-MucAcyto complex to ClpX/ClpP for MucAcyto degradation. They also report phenotypic effects of *algU* deletion on pyocyanin, pyoverdine, alginate, and host-cell invasion.
- **Visible evidence base** Main text figures (Fig. 1A-F, 2A-D, 3A-B, 4A-B, 5A-D, 6A-D), supplementary figures (Fig. S1-S9), crystallographic statistics table (Fig. 2B), BLI binding data (Fig. 6B, 6D), pull-down assays (Fig. 4A-B, 5B-C), DSF thermal stability data (Fig. 4B, S8)
- **Missing materials affecting confidence** Raw diffraction data statistics (completeness, I/σ, multiplicity, Wilson B-factor) not fully reported in main text; PDB validation report not available; AlphaFold3 confidence metrics (pLDDT, PAE) not shown; BLI sensorgrams not shown; statistical analysis details for phenotypic assays not provided; DSF raw curves not shown; molecular weights of proteins used in pull-downs not specified

## Reviewer

- **Overall assessment** This manuscript presents a technically sound structural study of the AlgU-MucAcyto complex, with a clear advance in obtaining a high-resolution structure via a fusion protein strategy. The structural analysis is thorough and the "binding-stability uncoupling" observation is interesting. However, the central mechanistic claim regarding SspB as the adaptor for ClpX/ClpP-mediated MucAcyto degradation rests primarily on computational modeling and qualitative pull-down data, without direct evidence of SspB-dependent degradation or functional validation in *P. aeruginosa*. The phenotypic data are presented as supporting context but are largely correlative and underpowered. The manuscript would be strengthened by direct biochemical evidence of SspB-mediated degradation and by addressing several technical concerns in the current data presentation.

- **Who would be interested in the results, and why** Researchers studying bacterial stress response signaling, particularly the σE/AlgU pathway in *Pseudomonas*; structural biologists interested in anti-sigma factor complexes and protein-protein interaction networks; investigators working on AAA+ protease adaptor mechanisms; and those studying *P. aeruginosa* pathogenesis, particularly mucoid conversion in cystic fibrosis lung infections.

- **Major strengths** 1) The fusion protein strategy to overcome expression difficulties is practical and could be broadly applicable. 2) The high-resolution structure (2.1 Å) with excellent RMSD agreement to the previously determined structure (0.01 Å over 253 Cα atoms) validates the approach. 3) The systematic mutagenesis approach (triple to sextuple mutations) combined with DSF provides a clear demonstration of binding-stability uncoupling. 4) The cross-species structural comparison with *E. coli* RopE-RseAcyto is informative. 5) The dual-interface adaptor model for SspB is mechanistically plausible and testable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central mechanistic claim
- **Claim pointer** "SspB acts as a dual-interface adaptor: its N-terminal domain recognizes the preassembled AlgU-MucAcyto complex (via the AlgU hairpin surface), whereas its flexible C-terminal tail engages ClpX, thereby bridging AlgU-MucAcyto to ClpX/ClpP and positioning MucAcyto for proteolysis-coupled AlgU release."
- **Evidence pointer** Fig. 5A-D, Fig. 6A-D; AlphaFold3 model (location not provided in main text)
- **Concern** The claim that SspB is the functional adaptor for ClpX/ClpP-mediated degradation of MucAcyto is not directly tested. The evidence consists of: (i) pull-down assays showing SspB binds to AlgU-MucAcyto and ClpX independently, and (ii) an AlphaFold3 model. No degradation assay (e.g., in vitro ClpX/ClpP proteolysis with and without SspB) is presented. The pull-down data show binding but do not establish that SspB delivers the complex for degradation. Furthermore, the AlphaFold3 model is used to make specific mechanistic claims (e.g., "degradation likely initiates at the C-terminal extended region of MucAcyto") without experimental validation. The authors acknowledge future work is needed, but the current framing overstates the strength of the evidence.
- **Why it matters** The SspB adaptor function is the central novel mechanistic claim of the manuscript. Without direct evidence of SspB-dependent degradation, the title and abstract overstate the findings. The distinction between "binds both partners" and "functions as an adaptor for degradation" is critical for the scientific contribution.
- **Resolution test** Provide in vitro degradation assays using purified ClpX, ClpP, SspB, and AlgU-MucAcyto (or a fluorescently labeled MucAcyto substrate) showing SspB-dependent proteolysis. Alternatively, provide in vivo evidence in *P. aeruginosa* (e.g., ΔsspB strain showing altered AlgU activity or MucA stability). If degradation assays are not feasible, temper the claims to reflect that SspB is a candidate adaptor requiring functional validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor of binding quantification
- **Claim pointer** "BLI measurements showed that wild-type SspB binds ClpX with a Kd of 2.683 × 10⁻⁸ M" and "wild-type SspB to the preassembled AlgU-MucAcyto complex, yielding a Kd of 5.551 × 10⁻⁸ M"
- **Evidence pointer** Fig. 6B, 6D; Materials and Methods (BLI measurements section)
- **Concern** The BLI methodology description is incomplete. The text states "Biotinylated MMLV RT-SV proteins were tethered on streptavidin (SA-XT) biosensors" which appears to be a copy-paste error from a different experiment, as MMLV RT-SV is not mentioned anywhere else in the manuscript. The correct analyte/ligand configuration is unclear. Additionally, the association and dissociation phases are described as involving different components (association with AlgU-MucAcyto or ClpX, dissociation in buffer with SspB), which is confusing. No sensorgrams or fitting details (global vs. local fitting, R² values, chi²) are shown. The Kd values are presented without error estimates or replicates.
- **Why it matters** The quantitative binding data are used to support the dual-interface model. If the experimental details are incorrect or the fitting is unreliable, the quantitative claims are not reproducible. The apparent copy-paste error raises concerns about the rigor of the methods reporting.
- **Resolution test** Correct the BLI methods description to accurately reflect the experimental setup. Provide representative sensorgrams, fitting statistics, and replicate numbers with standard deviations. Clarify which protein is immobilized and which is in solution for each measurement.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance of phenotypic data
- **Claim pointer** "Deletion of the algU gene affected the production of pyoverdine, pyocyanin, and alginate in Pseudomonas aeruginosa, as well as its cell invasiveness."
- **Evidence pointer** Fig. 1A-F, Fig. S1A-D
- **Concern** The phenotypic characterization is presented as supporting context but is underdeveloped. The pyocyanin difference between WT and ΔalgU is described as "slight, yet statistically insignificant," yet the complementation strain shows a "statistically significant" increase. This is an odd pattern that is not explained. Pyoverdine levels show "no change" between WT and ΔalgU, but the complemented strain shows a significant increase. The alginate data show a ~50% reduction in ΔalgU, but the complementation exceeds WT levels. The invasion assay shows increased invasion in ΔalgU, but the complementation only partially restores. These inconsistent patterns suggest possible off-target effects of the complementation plasmid or uncharacterized regulatory complexity. Statistical details (n, test used, effect sizes) are not provided.
- **Why it matters** The phenotypic data are used to frame the importance of AlgU in virulence-related processes. If the complementation does not cleanly restore phenotypes, the causal link between AlgU and these phenotypes is weakened. The inconsistent patterns could also indicate that the multicopy complementation creates artifacts.
- **Resolution test** Provide statistical details for all phenotypic assays. Address the inconsistent complementation patterns explicitly. Consider using a single-copy chromosomal complementation to more rigorously test phenotypic restoration. If the phenotypic data are intended as secondary context, clearly frame them as such and avoid over-interpretation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Structural interpretation of mutagenesis data
- **Claim pointer** "Multi-site alanine substitutions (up to sextuple mutations) in interfacial charged clusters of the AlgU-MucAcyto complex fail to disrupt binding but severely impair thermal stability, revealing that these residues are binding-redundant yet stability-essential."
- **Evidence pointer** Fig. 4A-B, Fig. S7, Fig. S8
- **Concern** The interpretation that these residues are "binding-redundant yet stability-essential" is based on pull-down assays (binding) and DSF (stability). However, the pull-down assay is a qualitative, binary readout (bound or not bound) and may not detect partial affinity reductions. The DSF data show reduced Tm but the magnitude of the reduction and the relationship to functional stability in vivo is unclear. Additionally, the authors do not test whether the destabilized mutants are still competent for SspB recognition or ClpX/ClpP degradation, which would connect the stability phenotype to the proposed degradation mechanism.
- **Why it matters** The "binding-stability uncoupling" is an interesting observation, but its biological relevance depends on whether the reduced stability affects the degradation pathway. Without connecting the destabilized mutants to downstream function (SspB binding, degradation), the significance of this finding is limited.
- **Resolution test** Test whether the destabilized mutants show altered SspB binding or altered susceptibility to ClpX/ClpP degradation in vitro. Alternatively, measure binding affinity quantitatively (e.g., by ITC or MST) for representative mutants to confirm that binding is truly unaffected, not just qualitatively preserved.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Model reliability and validation
- **Claim pointer** "AlphaFold3 modeling provided a structural framework for this recognition, suggesting SspB engages AlgU via its N-terminal domain while utilizing a disordered C-terminal region to dock onto ClpX."
- **Evidence pointer** Fig. 5D, Fig. 6A, 6C; location of model confidence metrics not provided
- **Concern** The AlphaFold3 model is used to make specific mechanistic claims about the ternary complex architecture, but no confidence metrics (pLDDT, PAE, or predicted aligned error) are shown. The authors also do not validate the model with mutagenesis of the predicted SspB-AlgU interface beyond the AlgU-side mutations (which were designed based on the model). The SspB mutations (R128-K135A) target the ClpX-binding tail, but no mutations are made in the SspB N-terminal domain to validate the AlgU recognition interface.
- **Why it matters** Computational models, even from state-of-the-art tools, require experimental validation when used to support mechanistic claims. Without confidence metrics or targeted validation of the SspB-AlgU interface, the specific architectural claims remain speculative.
- **Resolution test** Show pLDDT and PAE plots for the AlphaFold3 model. Design and test mutations in the SspB N-terminal domain predicted to disrupt AlgU binding. If the model is intended as a hypothesis-generating tool rather than a validated structure, state this clearly and adjust the language accordingly.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and accuracy of methods
- **Affected element** BLI methods section
- **Evidence pointer** Materials and Methods, "BLI measurements" paragraph
- **Issue** The sentence "Biotinylated MMLV RT-SV proteins were tethered on streptavidin (SA-XT) biosensors" appears to be an error, as MMLV RT-SV is not relevant to this study. This appears to be a copy-paste mistake from a different protocol.
- **Required correction** Replace with the correct description of the immobilized protein (likely biotinylated SspB or AlgU-MucAcyto complex) and clarify the experimental configuration for each binding measurement.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 2B (crystallographic statistics table)
- **Evidence pointer** Fig. 2B
- **Issue** The crystallographic statistics table is presented as a figure panel, which is unusual. Key statistics such as completeness in the highest resolution shell, I/σ in the highest resolution shell, and Wilson B-factor are not visible in the text description.
- **Required correction** Provide a complete crystallographic data collection and refinement statistics table in standard format, either in the main text or as a supplementary table, including resolution shell-specific statistics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of structural comparison
- **Affected element** Fig. S5B, Discussion section
- **Evidence pointer** Fig. S5B
- **Issue** The RMSD of 2.529 Å between AlgU-MucAcyto and RopE-RseAcyto across 156 Cα atoms is described as indicating "a relatively consistent three-dimensional arrangement." This RMSD is moderate and may reflect only the conserved core fold. The authors should clarify which regions contribute to the structural similarity and whether the interaction interfaces are truly conserved.
- **Required correction** Provide a more detailed structural comparison, including a per-residue RMSD analysis or a discussion of which structural elements are conserved versus divergent.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Fig. 1A-F, Fig. S1
- **Evidence pointer** Fig. 1A-F
- **Issue** The phenotypic assays lack statistical details. The number of biological replicates, the statistical test used, and the error bar representation are not described in the figure legends or methods.
- **Required correction** Add statistical details to the figure legends and methods, including the number of replicates, the statistical test used, and the definition of error bars.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, "dual-interface adaptor"
- **Issue** The term "dual-interface adaptor" is used to describe SspB, but the evidence supports that SspB has two binding sites (one for AlgU-MucAcyto, one for ClpX). This is more accurately described as a "bivalent adaptor" or "dual-binding adaptor." The term "dual-interface" could be confused with a single interface that has two distinct binding surfaces.
- **Required correction** Consider using "bivalent adaptor" or clarify the meaning of "dual-interface" in the text.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness of discussion
- **Affected element** Discussion section
- **Evidence pointer** Discussion, final paragraph
- **Issue** The discussion of future work mentions ΔsspB-based phenotypic analyses and in vitro reconstituted ClpXP degradation assays, but does not discuss the potential for off-target effects of the fusion protein strategy or the limitations of the AlphaFold3 model. A brief acknowledgment of these limitations would strengthen the discussion.
- **Required correction** Add a sentence acknowledging the limitations of the computational model and the fusion protein approach.

## Risk / unsupported claims
- The claim that SspB is "the key adaptor protein" for delivering AlgU-MucAcyto to ClpX/ClpP is not directly supported by functional degradation assays; the evidence is limited to binding and computational modeling.
- The statement that degradation "likely initiates at the C-terminal extended region of MucAcyto" is speculative and based solely on the AlphaFold3 model without experimental validation.
- The claim that the interaction network reflects "an evolutionary advantage" is speculative and not directly tested.
- The phenotypic data (pyocyanin, pyoverdine, alginate, invasion) are presented as evidence of AlgU function but the inconsistent complementation patterns and lack of statistical details make these claims difficult to evaluate.
- The statement that the fusion protein strategy "establishes a robust strategy for preparing and structurally characterizing recalcitrant protein complexes" is a general claim based on a single example and may be overstated.