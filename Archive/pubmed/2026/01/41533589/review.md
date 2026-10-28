## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and data availability statements.
- **Assessment boundary** Scientific content, technical soundness, structural interpretation, functional validation, and claims as presented in the provided text. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors report the discovery of a novel small-molecule modulation site on TREX1, formed by the intrinsically disordered α7–α8 loop. They present X-ray crystal structures of mouse TREX1 bound to three newly identified inhibitors, show that inhibitor binding induces a disordered-to-ordered transition with inhibitor-specific conformations, and propose a "multivertex clamping" mechanism. Molecular dynamics simulations are used to characterize fuzzy interactions, and biochemical and cell-based assays are used to show that these inhibitors disrupt DNA binding and restore cGAS-STING-mediated interferon expression.
- **Visible evidence base** X-ray crystallographic structures (apo and inhibitor-bound mTREX1), in vitro nuclease activity assays, electrophoretic mobility shift assays, fluorescence anisotropy, all-atom MD simulations, and cell-based assays measuring IFNB1 mRNA in MCF-7, Calu-3, and HCC1395 cells.
- **Missing materials affecting confidence** The manuscript text references Supplementary Figures, Tables, and Movies extensively, but these are not provided in the submitted material. The full crystallographic statistics are only summarized in Table 1 and Supplementary Table 4, which are not available. The docking methodology used for initial compound identification is described only briefly. The specific structures deposited in the PDB are listed but not independently verifiable from the provided text.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question: whether intrinsically disordered regions in a clinically relevant nuclease can be targeted by small molecules. The crystallographic observation of an inhibitor-bound, ordered conformation of the α7–α8 loop is a valuable contribution, and the combination of structural, computational, and cellular data is commendable. However, several technical concerns must be resolved before the central claims are fully established. The evidence that the α7–α8 loop is a bona fide DNA-binding SLiM is indirect, the functional significance of the modulation site is not quantitatively linked to inhibition efficacy, and the cellular data rely on a single compound with limited mechanistic controls. The "amphicon" concept is interesting but is presented with insufficient definition and validation to be generalizable at this stage.
- **Who would be interested in the results, and why** Researchers in the fields of cancer immunotherapy, innate immune signaling (cGAS-STING), nuclease enzymology, and intrinsically disordered proteins. The work may also interest medicinal chemists focused on allosteric or non-active-site inhibition strategies, as well as structural biologists studying protein–ligand interactions involving IDRs.
- **Major strengths** The identification of a previously uncharacterized small-molecule binding site on TREX1, formed by a disordered loop, is a novel finding. The crystallographic evidence that the α7–α8 loop can adopt multiple ordered conformations depending on the bound inhibitor is compelling and provides rare atomic-level detail for IDR-ligand interactions. The combination of X-ray crystallography, MD simulations, and functional assays is a strong multi-method approach. The cellular data linking inhibition to cGAS-STING pathway activation are relevant and potentially translational.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of structural interpretation
  - **Claim pointer** The authors claim that the α7–α8 loop forms a "modulation site" and that inhibitor binding induces a disordered-to-ordered transition, with the loop adopting inhibitor-specific conformations.
  - **Evidence pointer** Results section "Inhibitors bind mTREX1 at a novel modulation site by multivertex clamping"; Table 1; Supplementary Tables 1–8; PDB IDs 9KJD–9KJS.
  - **Concern** The crystallographic evidence is central to the paper, but the full refinement statistics and electron density quality are not available in the submitted material. The claim of a disordered-to-ordered transition relies on comparing apo structures (where the loop is unresolved) with inhibitor-bound structures (where it is resolved). However, the apo structures were obtained under different crystallization conditions (Supplementary Table 1), and it is not clear whether the loop is disordered in the apo state or simply unresolved due to crystal packing or lower resolution. The authors should provide a more rigorous analysis, including B-factor comparisons, omit maps, and a discussion of whether the loop is truly disordered in solution (e.g., using NMR or SAXS) or only in the crystal lattice.
  - **Why it matters** The central novelty of the paper is the discovery of a druggable site on a disordered loop. If the loop is not genuinely disordered in the apo state, or if the observed conformations are crystallization artifacts, the mechanistic claims are substantially weakened.
  - **Resolution test** Provide electron density maps (2Fo-Fc and Fo-Fc omit maps) for the α7–α8 loop in all structures. Include a quantitative comparison of loop mobility (B-factors, TLS parameters) between apo and bound states. If possible, include solution-state data (e.g., NMR or SAXS) demonstrating disorder in the apo state and ordering upon inhibitor binding.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional validation of the modulation site
  - **Claim pointer** The authors claim that the newly identified inhibitors "disrupt the DNA binding and immunosuppressive activity of TREX1" and that this is mediated by binding at the α7–α8 loop modulation site.
  - **Evidence pointer** Results sections "Inhibitors targeting the IDR-involved modulation site impede substrate binding" and "Inhibitors modulating the IDR exhibit efficacy in cellular models"; Figures 6 and 7; Supplementary Figures 12–16.
  - **Concern** The functional data are largely correlative. The EMSA and fluorescence anisotropy experiments show that the inhibitors reduce DNA binding, but the link to the modulation site is inferred from the crystal structures. No mutagenesis experiments are presented to demonstrate that disruption of the modulation site (e.g., mutation of key residues such as Trp188, Arg174, or Lys175) abolishes inhibitor binding and restores DNA binding. The cellular data are limited to one compound (NSC37215) with a single functional readout (IFNB1 mRNA). The claim that NSC292217 acts through a "nonspecific mechanism" is not supported by data shown in the main text.
  - **Why it matters** Without mutagenesis or other direct evidence, the causal link between inhibitor binding at the modulation site and the observed functional effects is not established. The specificity of the inhibitors for the modulation site versus other potential binding sites (e.g., the active site or DNA-binding groove) is not rigorously demonstrated.
  - **Resolution test** Perform site-directed mutagenesis of key residues in the α7–α8 loop and α8 helix (e.g., W188A, R174A, K175A) and test the effects on inhibitor binding (e.g., by ITC or MST) and on DNA binding and nuclease activity. Include a negative control compound that does not bind the modulation site. In cellular assays, include a mutant TREX1 that cannot bind the inhibitor to demonstrate on-target specificity.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of the "amphicon" concept
  - **Claim pointer** The authors propose a new concept, "amphicons," defined as "chemical-scale amphiphilic units" that mediate robust interactions with IDRs, and suggest this may be generalizable to targeting other IDRs.
  - **Evidence pointer** Results section "Chemical-scale amphiphilicity for anchoring to IDR-involved sites"; Figure 5; Discussion.
  - **Concern** The "amphicon" concept is introduced with limited quantitative or comparative support. It is not clear how an amphicon differs from well-known concepts such as "hot spots" or "hydrophobic patches" in protein–ligand interactions. The authors do not provide a systematic analysis of the amphicon properties (e.g., size, polarity, solvent exposure) across the different inhibitor complexes, nor do they demonstrate that the concept predicts or explains binding affinity or specificity beyond what is already known. The claim of generalizability is speculative without testing on other IDR-ligand systems.
  - **Why it matters** The paper's broader significance partly rests on the claim that the mechanistic principles uncovered here may be generalized to other IDRs. If the "amphicon" concept is not rigorously defined and validated, this claim is overstated.
  - **Resolution test** Provide a quantitative definition of amphicons (e.g., based on solvent-accessible surface area, hydrophobicity, and hydrogen-bonding potential) and apply it systematically to the three inhibitor complexes. Test the predictive power of the concept by analyzing known IDR-ligand complexes from the PDB or by performing additional MD simulations with modified inhibitor structures. Alternatively, temper the generalizability claims in the Discussion.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of writing
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract, first sentence; Introduction, first paragraph
  - **Issue** The phrase "short linear motifs (SLiMs)—an important subclass of intrinsically disordered regions (IDRs)" is imprecise. SLiMs are functional elements within IDRs, not a subclass of IDRs per se. The distinction should be clarified.
  - **Required correction** Revise to "short linear motifs (SLiMs), which are functional elements often located within intrinsically disordered regions (IDRs),..."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** Materials and methods, "Inhibitor sources"
  - **Evidence pointer** Materials and methods, "Inhibitor sources"
  - **Issue** The source of the inhibitors is stated as the NCI DTP database, but the criteria for selection from the docking screen are not described. The docking methodology is mentioned only briefly in the Results.
  - **Required correction** Provide a brief description of the docking protocol, including the software used, the scoring function, and the selection criteria for compounds chosen for experimental testing.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results, "Inhibitors bind mTREX1 at a novel modulation site by multivertex clamping"
  - **Evidence pointer** Results, second paragraph; Figure 2
  - **Issue** The authors state that "only one of the mTREX1 monomers binds an inhibitor molecule" in all complex structures. This is an interesting observation, but the potential reasons (e.g., negative cooperativity, crystal packing, or half-of-sites reactivity) are not discussed.
  - **Required correction** Add a brief discussion of possible explanations for the observed asymmetry in inhibitor binding.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results, "Inhibitors modulating the IDR exhibit efficacy in cellular models"
  - **Evidence pointer** Figure 7; Supplementary Figure 16
  - **Issue** The number of independent biological replicates for the cellular assays is not stated in the main text. The error bars are shown but the statistical test used is not specified.
  - **Required correction** State the number of replicates and the statistical test used in the figure legends or Methods.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Results, "Chemical-scale amphiphilicity for anchoring to IDR-involved sites"
  - **Evidence pointer** Results, fifth paragraph; Figure 5
  - **Issue** The term "amphiphilic units" is used to describe both the inhibitor moieties and the protein residues. This dual usage is confusing. The authors should distinguish between the amphiphilic character of the ligand and the complementary amphiphilic character of the protein surface.
  - **Required correction** Clarify the terminology, e.g., by referring to "ligand amphiphilic moieties" and "protein amphiphilic patches" separately.
- **Technical failings that need to be addressed before the case is established** R1-M1 (structural interpretation of disorder-to-order transition) and R1-M2 (functional link between modulation site binding and inhibition) are the primary technical issues. The lack of mutagenesis data is a significant gap. The absence of full crystallographic statistics and electron density maps in the submitted material prevents independent verification of the structural claims.
- **Assessment against Nature-style criteria**  
  *Originality*: The discovery of a small-molecule binding site on a disordered loop of TREX1 is original and of potential interest to a broad community. However, the conceptual framework ("amphicons") is not yet sufficiently developed to be considered a major advance.  
  *Scientific importance*: TREX1 is a validated target in cancer immunotherapy, and the identification of a non-active-site modulatory mechanism is clinically relevant. The work could influence future drug discovery efforts.  
  *Interdisciplinary readership*: The topic bridges structural biology, enzymology, immunology, and drug discovery, and should appeal to readers across these fields.  
  *Technical soundness*: The crystallographic work appears carefully executed, but the lack of mutagenesis and the limited functional validation weaken the overall technical case. The MD simulations are described in reasonable detail but the analysis of "fuzzy interactions" is largely qualitative.  
  *Readability for nonspecialists*: The manuscript is generally well-written and accessible, though the introduction of the "amphicon" concept could be clearer for readers unfamiliar with IDR biology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core structural findings are potentially valuable, but the manuscript requires additional experimental evidence, particularly mutagenesis to link the modulation site to function, and a more rigorous treatment of the disorder-to-order transition, before the claims are fully established.

## Risk / unsupported claims
- The claim that the α7–α8 loop is a "DNA-binding SLiM" is not directly demonstrated. The evidence is indirect: the loop is resolved in DNA-bound structures and is near the DNA-binding groove, but no direct binding assay (e.g., ITC with a peptide spanning the loop) is presented.
- The claim that the "amphicon" concept is generalizable to other IDR-ligand systems is speculative and not supported by comparative analysis.
- The statement that NSC292217 acts through a "nonspecific mechanism" in cells is not supported by data in the main text.
- The claim that the inhibitors "disrupt the immunosuppressive activity of TREX1" is based on a single cell line (MCF-7) with a single readout (IFNB1 mRNA) and requires additional validation (e.g., protein-level analysis, additional cell lines, or in vivo data).
- The assertion that the modulation site is "novel" is supported by comparison with previously published TREX1-inhibitor structures, but the authors do not provide a systematic structural comparison to rule out overlap with known sites.