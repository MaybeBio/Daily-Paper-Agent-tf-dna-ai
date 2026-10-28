## Review setup
- **Input scope** Full manuscript text (abstract, methods, results, discussion, data availability) without supplementary figures/tables or extended methods
- **Assessment boundary** Structural and biochemical claims presented in the main text, including cryo-EM structure interpretation, functional assays, and mechanistic conclusions
- **Shared manuscript claim summary** The authors report two cryo-EM structures of Rob-dependent transcription activation complexes (Rob-TACI and Rob-TACII) from E. coli, showing a monomeric Rob engaging RNAP via αCTD and σ70R4, occluding σ70R4 from the -35 element, binding the Rob box through two HTH motifs, and inducing DNA bending aided by an acidic loop from the Rob CTD. The Rob CTD is proposed to function as an allosteric effector-binding domain that coordinates with the NTD to promote transcription activation.
- **Visible evidence base** Main text figures referenced (Figures 1-5, Supplementary Figures S1-S14), cryo-EM density maps (EMD-32165, EMD-32166), atomic coordinates (PDB 7VWY, 7VWZ), in vitro transcription assays, EMSA, molecular docking, and single-molecule FRET (described in supplementary)
- **Missing materials affecting confidence** Supplementary figures and tables (including Supplementary Table S1, Supplementary Methods for FRET), full cryo-EM validation statistics beyond resolution values, and detailed model building/refinement metrics are not provided in the submitted text

## Reviewer

- **Overall assessment** This manuscript presents the first cryo-EM structures of a full-length AraC/XylS family transcription activator in complex with RNAP and promoter DNA, providing valuable molecular insights into Rob-dependent transcription activation. The structural data are potentially significant for understanding this important regulator family. However, several technical concerns regarding structure interpretation, functional validation, and the strength of the allosteric model need to be addressed before the conclusions are fully established.

- **Who would be interested in the results, and why** Researchers studying bacterial transcription regulation, particularly the AraC/XylS family of activators, will find these structures highly relevant. The work also has implications for understanding multidrug resistance mechanisms in pathogenic bacteria, which could interest investigators in antimicrobial resistance and drug discovery. Structural biologists studying transcription complexes and protein-DNA interactions would also find value in these data.

- **Major strengths**
  1. First cryo-EM structures of a full-length AraC/XylS family activator in complex with RNAP and promoter DNA, filling an important gap in the field
  2. Two alternative conformations of Rob captured, providing potential insight into conformational dynamics
  3. Comprehensive biochemical validation of key structural observations through mutagenesis and functional assays
  4. Clear demonstration of a monomeric activator engaging RNAP through multiple interfaces, distinct from dimeric activators
  5. The proposed role of the acidic loop in DNA bending is a novel and interesting observation

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of structural interpretation
- **Claim pointer** The authors claim that Rob CTD in Rob-TACI exhibits a rotation of approximately 35 degrees relative to Rob-TACII, and that Rob-TACI represents a pre-state of the stable Rob-TACII
- **Evidence pointer** Figure 1B-C, Supplementary Figures S7B-D, Results section "Overall structure of Rob-TAC"
- **Concern** The local resolution at the Rob CTD is reported as 5.5-7.0 Å, which is relatively low for confident interpretation of domain orientation and conformational differences. The claim of a 35-degree rotation between the two states relies on accurate domain positioning at this resolution. Additionally, the authors state that the density and occupancy of Rob CTD in Rob-TACI are "significantly weaker and lower" than in Rob-TACII, which raises questions about whether the observed differences reflect genuine conformational states or simply differential map quality/occupancy.
- **Why it matters** The interpretation of two distinct conformational states and the proposed trajectory from TACI to TACII is central to the mechanistic model presented. If the differences are artifacts of resolution or occupancy, the conformational dynamics claim would be weakened.
- **Resolution test** Provide local resolution maps for the Rob CTD region in both complexes, quantitative occupancy estimates, and validation of the domain rotation through independent methods such as 3D variability analysis or focused classification with explicit comparison of map-to-model correlation in the CTD region.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation of the allosteric model
- **Claim pointer** The authors propose that Rob CTD functions as an effector-binding domain that allosterically regulates Rob activity through a sequestration-dispersal mechanism, and that ligand binding to the CTD is required for transcription activation
- **Evidence pointer** Figure 5, Results section "Rob CTD activates transcription through allosteric coordination with Rob NTD", Discussion
- **Concern** The allosteric model is primarily supported by molecular docking predictions and mutagenesis of putative ligand-binding residues. However, no direct binding assay for any ligand to Rob CTD is presented. The docking analysis is purely computational and the authors acknowledge that the structures represent a dispersal state that "may include an effector molecule during expression and purification," yet no ligand is actually observed in the cryo-EM density. The functional data show that mutations in the putative binding pocket reduce activity, but this could reflect structural destabilization rather than loss of ligand binding.
- **Why it matters** The sequestration-dispersal model is a major conceptual contribution of this work. Without direct evidence of ligand binding and ligand-induced conformational changes, this model remains speculative.
- **Resolution test** Provide direct binding measurements (e.g., ITC, MST, or SPR) for proposed ligands to Rob CTD, demonstrate that ligand binding induces conformational changes consistent with the proposed mechanism, and show that the mutant phenotypes correlate with loss of ligand binding rather than protein misfolding or instability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the proposed mechanism
- **Claim pointer** The authors suggest that the interaction pattern observed for Rob with RNAP αCTD and σ70R4 reveals "generally important regulatory roles" and that the mechanism may apply broadly to AraC/XylS family transcription factors
- **Evidence pointer** Results sections "RNAP αCTD is required for Rob-dependent transcription activation of class II promoters" and "Rob occludes σ70R4 from binding to promoter -35 element", Discussion
- **Concern** The structural and functional data are derived from a single promoter (micF) and a single activator (Rob). While sequence conservation of key residues is mentioned, no comparative analysis with other AraC/XylS family members is presented to support the generalizability claim. The authors note that Rob differs from MarA in DNA binding mode, which suggests diversity within the family.
- **Why it matters** The broader significance of this work depends on whether the mechanism is representative of the family or specific to Rob. Overgeneralization could mislead future studies on other family members.
- **Resolution test** Provide sequence alignment analysis showing conservation of the key interaction residues across a broader set of AraC/XylS family members, or present preliminary structural or biochemical data on at least one additional family member to support the generalizability claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative assessment of functional data
- **Claim pointer** The authors state that mutations of key residues "led to obvious decrease in both transcription activation activities" and that certain mutations "confer significant defects"
- **Evidence pointer** Figure 2D, Figure 3F, Figure 4F, Supplementary Figure S10
- **Concern** The functional data are described qualitatively. No quantitative values, statistical analyses, or effect sizes are reported in the main text. The reader cannot assess the magnitude of the defects or whether they are statistically significant. The figure legends are not provided in the submitted text, so the actual data presentation cannot be evaluated.
- **Why it matters** Quantitative assessment is essential to determine which interactions are critical versus modulatory. Without statistical analysis, the relative importance of different interfaces cannot be established.
- **Resolution test** Report quantitative activity values with statistical analysis (e.g., mean ± SEM, n, p-values) for all mutant comparisons, and clearly indicate which mutations cause complete loss versus partial reduction of activity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1A
- **Evidence pointer** Results section "Overall structure of Rob-TAC"
- **Issue** The description of the DNA scaffold design is brief. The authors mention a 20 bp Rob binding box and a 13 bp non-complementary transcription bubble, but the rationale for the specific scaffold boundaries (-57 to +13) and how this relates to the native promoter context is not fully explained.
- **Required correction** Provide additional detail on the scaffold design rationale, including why these specific boundaries were chosen and whether the scaffold supports open complex formation in the absence of full promoter sequences.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Cryo-EM data processing
- **Evidence pointer** Methods section "Cryo-EM data acquisition and processing"
- **Issue** The description of 3D classification and focused classification steps is somewhat abbreviated. The authors state that particles were combined from multiple classes but do not fully explain the criteria for class selection or the rationale for combining specific classes.
- **Required correction** Expand the methods to include more detail on classification strategy, including how many classes were examined, what distinguished the selected classes, and how the final particle sets were chosen.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of FRET data
- **Affected element** Supplementary Figure S14, Discussion
- **Evidence pointer** Results section "Rob CTD activates transcription through allosteric coordination with Rob NTD"
- **Issue** The single-molecule FRET experiment is described in one sentence in the main text with details relegated to supplementary methods. The authors state that FRET values were "comparable and consistent with a distance of 5.5 nm from Rob-TACII rather than 7.7 nm from Rob-TACI," but the significance of this finding and how it supports the conformational model is not clearly explained.
- **Required correction** Provide a clearer explanation of what the FRET measurements demonstrate and how they support the proposed conformational equilibrium between TACI and TACII states.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The authors mention that during review, Hao et al. published a structure of the RamA-class II activator complex. This is mentioned briefly, but the comparison with the Rob structures could be more developed to highlight similarities and differences.
- **Required correction** Expand the comparison with the RamA structure to more clearly articulate what is conserved and what is unique about the Rob mechanism.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability section
- **Evidence pointer** Data Availability section
- **Issue** The authors provide accession numbers for cryo-EM maps and coordinates but do not mention deposition of the in vitro transcription data, EMSA data, or other biochemical results.
- **Required correction** Consider depositing raw data for biochemical assays in a public repository or providing them as source data files.

## Risk / unsupported claims
1. The claim that Rob-TACI represents a "pre-state" of the stable Rob-TACII is not directly supported by the data presented. The two structures may represent alternative conformations without a defined temporal relationship.
2. The proposal that the Rob CTD shares "great structural similarity with the global Gyrl-like domains in effector binding and allosteric regulation" is based on structural comparison, but the functional equivalence of the allosteric mechanism is not experimentally demonstrated.
3. The statement that the findings "provide favorable evidences for understanding the physiological roles of the other AraC/XylS-family transcription factors" is speculative without direct comparative data on other family members.
4. The claim that Rob acts through a "pre-recruitment" mechanism is supported only by the observation of complex formation in the absence of promoter DNA (Supplementary Figure S10C), which is indirect evidence.
5. The assertion that the acidic loop "facilitates DNA bending" is supported by mutagenesis data, but the precise mechanism and the extent of its contribution relative to the HTH motifs are not quantitatively established.
6. The statement that ligand binding is "required for Rob-dependent transcription activity" is not directly tested, as no ligand was added or removed in the functional assays.
7. The claim that the two structures show "Rob in alternative conformations" is based on the CTD position, but given the resolution limitations in this region, this interpretation carries uncertainty.