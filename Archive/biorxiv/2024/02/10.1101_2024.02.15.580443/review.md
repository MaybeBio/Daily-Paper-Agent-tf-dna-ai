## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, figure legends, and supplementary figure/table descriptions
- **Assessment boundary** Scientific validity, technical soundness, and significance of the structural and functional claims presented; no assessment of editorial fit or formatting
- **Shared manuscript claim summary** The authors present cryoEM structures of the bacterial hexameric motors RadA (S. pneumoniae) and ComM (L. pneumophila) bound to DNA and ATP analogues, revealing active-state conformations. They identify a salt bridge switch in RadA (R301/E76-E239) that couples ATP hydrolysis to DNA binding, describe the Lon domain as a common hexamerization scaffold, and propose a unified model of dsDNA translocation for branch migration during homologous recombination.
- **Visible evidence base** CryoEM density maps and atomic models (RadA at 3.15 Å; ComM at 3.1 Å with local refinements), biochemical assays (ATPase, DNA binding, helicase) for wild-type and R301A mutant RadA, in vivo transformation assays, structural comparisons with T7-gp4 and MCM helicases, PDB-PISA interface analysis
- **Missing materials affecting confidence** No electron density maps or validation statistics shown in main text (deferred to supplementary); no raw data for biochemical assays (e.g., representative gels, quantification replicates); no negative-stain or apo-state structures for comparison; no structural data for ComM in the absence of DNA at high resolution; no kinetic parameters for ATP hydrolysis; no direct demonstration of branch migration activity for the specific constructs used

## Reviewer

- **Overall assessment** This manuscript presents the first structures of ComM and the first active-state structure of RadA bound to DNA, representing a significant advance in understanding bacterial hexameric motor mechanisms in homologous recombination. The structural work appears technically sound at the reported resolutions, and the identification of a salt bridge switch in RadA is a novel and mechanistically interesting finding. However, the manuscript would be substantially strengthened by more direct functional validation linking the structural states to the proposed translocation mechanism, and by clearer presentation of validation statistics and biochemical data. The comparative analysis between RadA and ComM is thoughtful but somewhat speculative in places, particularly regarding the dodecameric state of ComM and its functional relevance.

- **Who would be interested in the results, and why** Structural biologists studying hexameric helicases and AAA+ ATPases will find the RadA and ComM structures valuable, particularly the comparison with MCM and T7-gp4 systems. Researchers in bacterial homologous recombination and natural transformation will be interested in the mechanistic insights into branch migration. The proposed salt bridge switch mechanism may also attract interest from those studying allosteric regulation in ring-shaped ATPases more broadly. The work has potential relevance for understanding how DNA repair and horizontal gene transfer are coordinated in bacteria.

- **Major strengths**
  1. First reported structure of ComM and first active-state structure of RadA, filling a clear gap in the field
  2. High-quality cryoEM work with multiple local refinements to improve map quality in functionally important regions
  3. Identification of a specific salt bridge switch (R301/E76-E239) with functional validation through mutagenesis, biochemical assays, and in vivo transformation experiments
  4. Thoughtful comparative analysis between RadA and ComM, highlighting both shared and distinct features of their translocation mechanisms
  5. The proposed 12 bp/6 ATP translocation model is clearly articulated and testable

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the cryoEM structures represent "active" states of RadA and ComM bound to DNA and ATP analogues, and that the observed conformations correspond to a translocation-competent state.
- **Evidence pointer** Results section "Cryo-electron microscopy reveals the active conformation of RadA bound to DNA"; Results section "CryoEM structures of Legionella pneumophila ComM"; Supplementary Table 3
- **Concern** The designation of these structures as "active" states requires more rigorous justification. The authors use ATPγS and AMP-PNP, which are non-hydrolyzable analogues that trap the ATP-bound state, but this does not necessarily correspond to a single functional state in the ATP hydrolysis cycle. The manuscript does not demonstrate that the observed conformations are catalytically relevant, nor does it rule out that the structures represent inhibited or non-productive states. Additionally, the resolution of the ATPase domains in the RadA structure is not clearly stated, and the authors note that subunit F is poorly ordered, which complicates interpretation of the full hexameric state.
- **Why it matters** The central mechanistic claims of the manuscript depend on the interpretation that these structures capture the motor in a state relevant to translocation. If the observed conformations are not functionally meaningful, the proposed model for branch migration would lack a structural foundation.
- **Resolution test** The authors should provide additional evidence that the observed state is catalytically relevant, such as: (1) comparison with a structure in the ADP or apo state to show conformational changes; (2) demonstration that the ATPγS-bound state is competent for DNA binding and translocation in ensemble assays; (3) clearer reporting of local resolution in the ATPase domains and how this affects interpretation of the active site geometry.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the R301 salt bridge switch is "critical for coupling ATP hydrolysis to DNA binding" and that its disruption causes "futile ATP consumption."
- **Evidence pointer** Results section "RadA and ComM share the same Lon-protease-like scaffold"; Figure 5; Methods section "DNA-binding assays", "ATPase assays", "Helicase assays"
- **Concern** The biochemical data supporting the salt bridge switch mechanism are presented without sufficient quantitative detail. The ATPase assays show that R301A has high basal activity in the absence of DNA, but the manuscript does not report the fold-stimulation by DNA for wild-type versus mutant, nor does it provide kinetic parameters (kcat, Km) that would allow assessment of whether the mutant truly uncouples ATP hydrolysis from DNA binding. The DNA binding assays are described qualitatively ("significantly lower affinity") without reporting dissociation constants or showing representative binding curves. The helicase assay shows very low activity for R301A, but the manuscript does not address whether this is due to defective DNA binding, defective ATP hydrolysis, or defective coupling.
- **Why it matters** The salt bridge switch is presented as a key mechanistic finding, but the functional evidence is currently insufficient to support the strong claim that it couples ATP hydrolysis to DNA binding. Without quantitative biochemical characterization, alternative explanations (e.g., global destabilization of the protein) cannot be excluded.
- **Resolution test** The authors should provide: (1) quantitative DNA binding data (Kd values) for wild-type and R301A; (2) ATPase kinetic parameters in the presence and absence of DNA for both proteins; (3) a demonstration that the R301A mutant retains structural integrity (e.g., via size-exclusion chromatography or thermal stability assays); (4) a more detailed analysis of the helicase assay, including time courses and multiple substrate concentrations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript proposes that the ComM dodecamer, observed in 24% of particles, may represent a pre-activation complex analogous to MCM dodecamers, and suggests a possible role in branch migration.
- **Evidence pointer** Results section "CryoEM structures of Legionella pneumophila ComM"; Supplementary Figure 7
- **Concern** The functional relevance of the ComM dodecamer is highly speculative. The authors note that the dodecamer coordinates a single dsDNA molecule, but they do not provide any biochemical or genetic evidence that this state exists in solution or is functionally important. The comparison to MCM dodecamers is reasonable but the MCM dodecamer is a well-established pre-loading complex with clear functional roles, whereas no such evidence is presented for ComM. The additional density observed at the expected ZF domain position is intriguing but unexplained.
- **Why it matters** The dodecamer observation could be a significant finding if functionally validated, but as presented it remains an interesting but unsubstantiated observation. Over-interpretation of this state could mislead the field about its biological relevance.
- **Resolution test** The authors should either: (1) provide biochemical evidence for dodecamer formation in solution (e.g., via analytical ultracentrifugation, native mass spectrometry, or cross-linking); (2) test whether mutations that disrupt dodecamerization affect branch migration activity; or (3) clearly frame the dodecamer as a speculative observation requiring future validation, rather than implying functional significance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that RadA and ComM share a conserved Lon-protease-like scaffold that functions as a hexamerization module, and that this domain contributes to DNA binding.
- **Evidence pointer** Results section "RadA and ComM share the same Lon-protease-like scaffold"; Figure 4; Supplementary Table 2
- **Concern** The structural comparison between the Lon domains of RadA and ComM is based on a sequence identity of only 28%, and the manuscript does not report the RMSD for the Lon domain superposition or provide a clear structural alignment figure. The claim that the Lon domain contributes to DNA binding is supported by reference to prior work on T. thermophilus RadA, but the specific residues involved in DNA binding in the S. pneumoniae and L. pneumophila structures are not clearly identified or validated by mutagenesis. The PDB-PISA analysis showing different interface properties between RadA and ComM is interesting but the functional implications are not explored.
- **Why it matters** The Lon domain is presented as a key shared feature of these motors, but the evidence for its functional role in DNA binding and hexamerization is largely indirect. A clearer structural and functional characterization would strengthen the comparative claims.
- **Resolution test** The authors should: (1) report the RMSD for the Lon domain superposition; (2) identify specific Lon domain residues that contact DNA in the structures and test their functional importance through mutagenesis; (3) provide a more detailed analysis of the differences in interface properties between RadA and ComM and discuss their potential functional consequences.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states that RadA is "involved in both DNA repair in all species and in natural transformation in Gram positive firmicutes," but this phrasing is ambiguous. It could be read as RadA being involved in DNA repair in all species, which is not accurate, or as RadA being involved in DNA repair in all bacterial species.
- **Required correction** Rephrase to clarify the taxonomic scope, e.g., "RadA is a highly conserved bacterial helicase involved in DNA repair across bacterial species and additionally in natural transformation in Gram-positive firmicutes."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, DNA-binding assays
- **Evidence pointer** Methods section "DNA-binding assays"
- **Issue** The DNA binding assay description does not specify the DNA substrate used (ssDNA vs dsDNA) for the R301A mutant experiments, nor does it describe how binding was quantified. The figure legend for Figure 5b is also minimal.
- **Required correction** Provide a clear description of the DNA substrates used, the concentration range of protein tested, and the method of quantification (e.g., fraction of bound DNA, apparent Kd).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, ComM dodecamer section
- **Evidence pointer** Results section "CryoEM structures of Legionella pneumophila ComM"; Supplementary Figure 7
- **Issue** The description of the dodecamer structure is brief and does not clearly explain how the two hexamers are oriented relative to each other, or how the DNA is coordinated across the two hexamers. The supplementary figure legend is also sparse.
- **Required correction** Expand the description of the dodecamer architecture, including the relative orientation of the two hexamers, the path of the DNA through the complex, and the nature of the additional density at the ZF position.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, CryoEM data processing
- **Evidence pointer** Methods section "RadA CryoEM Data collection and processing"; Methods section "ComM cryoEM Data collection and processing"
- **Issue** The methods describe processing in both Relion and Cryosparc for ComM, but it is not clear how the final maps from different software packages were reconciled or which maps were used for model building. The resolution of the final maps is reported in the text but not in a summary table in the main text.
- **Required correction** Clarify the relationship between the maps generated in different software packages, and include a summary table of map resolution, model statistics, and validation metrics in the main text or clearly reference Supplementary Table 3.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion, model of translocation
- **Evidence pointer** Discussion section "RadA and ComM translocate on DNA in a helical arrangement"
- **Issue** The proposed model of 12 bp/6 ATP translocation is described but the reasoning is not fully explained. It is not clear how this step size is derived from the structural data, and whether this is a prediction or an established observation.
- **Required correction** Clearly state whether the 12 bp/6 ATP step is a prediction from the structures or supported by experimental data, and provide the structural basis for this specific step size.

- **Technical failings that need to be addressed before the case is established**
  1. Quantitative biochemical data for the R301A mutant are lacking; the manuscript reports qualitative differences but does not provide the kinetic and binding parameters needed to support the coupling mechanism (R1-M2)
  2. The designation of the structures as "active" states requires additional validation, including clearer reporting of local resolution and comparison with other nucleotide states (R1-M1)
  3. The functional relevance of the ComM dodecamer is not established; without biochemical or genetic evidence, this observation should be framed as speculative (R1-M3)
  4. The structural basis for the proposed 12 bp/6 ATP translocation step is not clearly explained (R1-m5)

- **Assessment against Nature-style criteria**
  - **Originality** The structures of ComM and active-state RadA are novel and represent a clear advance over previous work. The salt bridge switch mechanism is a new finding. However, the overall concept of hexameric motors translocating on DNA is well established, and the manuscript does not present a fundamentally new paradigm.
  - **Scientific importance** The work addresses an important question in homologous recombination and provides structural insights that will be of interest to the field. The functional validation is currently insufficient to fully establish the mechanistic claims, which limits the immediate impact.
  - **Interdisciplinary readership** The work will appeal primarily to structural biologists and researchers in DNA repair and recombination. The broader significance to fields such as bacterial evolution or antibiotic resistance is mentioned but not developed in a way that would attract a wide interdisciplinary audience.
  - **Technical soundness** The cryoEM work appears technically competent, but the biochemical validation is not presented with sufficient rigor. The lack of quantitative data for the key mutant experiments is a significant weakness.
  - **Readability for nonspecialists** The manuscript is generally well-written and the figures are informative, but the results section assumes substantial background knowledge of helicase mechanisms and homologous recombination. The abstract is accessible, but the main text would benefit from clearer explanations of the proposed model and its implications.

- **Recommendation posture** Supportive if technical concerns are resolved. The structural findings are potentially significant and the manuscript addresses an important question. However, the current evidence does not fully establish the central mechanistic claims, particularly regarding the salt bridge switch and its role in coupling ATP hydrolysis to DNA binding. The authors should provide quantitative biochemical data, clarify the structural basis for the proposed translocation model, and temper claims about the functional relevance of the ComM dodecamer. With these revisions, the manuscript could make a strong contribution to the field.

## Risk / unsupported claims
- The claim that the observed structures represent "active" or "translocation-competent" states is not fully supported; the use of non-hydrolyzable ATP analogues traps a pre-hydrolysis state that may not correspond to a single functional conformation
- The proposal that R301 functions as a "salt bridge switch" coupling ATP hydrolysis to DNA binding is supported by structural observation and limited mutagenesis, but the biochemical evidence is not quantitative enough to establish the mechanism
- The functional relevance of the ComM dodecamer is speculative; no biochemical or genetic data support a role in branch migration
- The claim that the Lon domain functions as a "clamp on DNA" is inferred from structural observation and prior work on T. thermophilus, but direct evidence in the S. pneumoniae and L. pneumophila systems is lacking
- The proposed 12 bp/6 ATP translocation step size is not clearly derived from the data presented and appears to be a prediction rather than an experimentally supported observation
- The statement that RadA and ComM "share the same Lon-protease-like scaffold" implies functional equivalence, but the differences in interface properties and DNA binding modes are not fully explored