## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and internal consistency as presented in the provided text
- **Shared manuscript claim summary** The authors propose that conserved "energetic blueprints" within the LacI/GalR transcription factor family, defined by state-dependent local stability changes measured via hydrogen exchange/mass spectrometry, are distinct from those of the homologous periplasmic binding proteins, and that these family-specific energetic relationships, including structured water interactions, are evolutionarily conserved and drive function.
- **Visible evidence base** Abstract; Results sections (sequence conservation, structural comparisons, HX/MS data, water modeling, MD simulations); Methods (MSA, tree building, crystallography, HX/MS, RosettaECO, MD); Data availability statement
- **Missing materials affecting confidence** Figures and tables (referenced as Figs. 1–5, S1–S17, Tables S1–S15) are not provided; Supplementary Notes 1 and 2 are not provided; specific numerical values for ΔΔGop are only partially given; statistical details for HX/MS significance thresholds are incomplete; validation metrics for RosettaECO and MD convergence are not described in the text

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in protein evolution: whether the conservation of a protein fold reflects conservation of underlying energetic features that drive function. The authors combine a powerful set of biophysical and computational methods to compare the energetic landscapes of LacI/GalR transcription factors and periplasmic binding proteins. The central finding, that the "energetic blueprints" of these two families are largely distinct despite shared fold and ligand specificity, is potentially significant. However, the strength of the conclusions rests heavily on the HX/MS data and its interpretation, and the current text does not provide sufficient detail to fully evaluate the robustness of the analysis, particularly regarding the significance thresholds, the treatment of the "mini-peptide" concept, and the structural interpretation of the observed energetic changes. The manuscript is well-written and the conceptual framework is compelling, but the evidence as presented is incomplete.
- **Who would be interested in the results, and why** Researchers in protein evolution, biophysics, and structural biology would be interested. The work provides a new perspective on how fold conservation relates to functional diversification, and the concept of an "energetic blueprint" could be influential. Additionally, those working on transcription factor engineering or drug design targeting allosteric sites would find the identification of conserved energetic hotspots and the role of structured water relevant.
- **Major strengths**
  1. The central question is important and well-articulated.
  2. The combination of HX/MS, X-ray crystallography, bioinformatics, and MD simulations is powerful and appropriate for the question.
  3. The comparison between TFs and PBPs, which share a fold and bind the same ligands but have different functions, is a clever and informative experimental design.
  4. The identification of a conserved structured water molecule as a potential functional element is a novel and interesting finding.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of HX/MS data interpretation
  - **Claim pointer** The manuscript claims to have determined single-residue free energies of opening (ΔGop) for all proteins in multiple states and to have identified conserved, state-dependent energetic changes.
  - **Evidence pointer** Methods: HX/MS data analysis; Results: Figs. 2, 3, 4
  - **Concern** The description of the HX/MS data analysis is insufficient to assess the reliability of the reported ΔGop values. The concept of a "mini-peptide" (a set of residues covered indistinguishably by a set of fit exchange rates) is introduced, but the criteria for defining these sets, the number of peptides used per protein, the redundancy of coverage, and the spatial resolution achieved are not stated. The significance threshold is defined as mean{ΔGop,a,i-ΔGop,b,i} > std{ΔGop,a,i-ΔGop,b,i}, which is a weak criterion (a difference greater than one standard deviation) and may lead to a high false-positive rate given the number of comparisons performed. The manuscript does not report the number of sites passing this threshold, the distribution of effect sizes, or any correction for multiple testing. Without this information, the central claim of conserved energetic changes is not robustly supported.
  - **Why it matters** The entire thesis of the paper rests on the accuracy and interpretation of the ΔGop differences. If the resolution is poor or the significance criteria are too lenient, the identified "energetic blueprints" and "molecular switches" could be artifacts of the analysis method.
  - **Resolution test** The authors must provide a detailed description of the HX/MS data processing, including peptide coverage maps, redundancy, the number of exchange rates fit per peptide, and the criteria for defining mini-peptides. They should report the number of significant sites identified per protein and per state comparison, and provide a more robust statistical treatment, such as a false discovery rate control. Ideally, they would show that the identified conserved changes are robust to variations in the analysis parameters.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Support for the "molecular switch" model
  - **Claim pointer** The manuscript proposes a set of "molecular switches" that transition TFs between functional states, involving specific structural elements (e.g., transducer helix, metastable helix, beta-sheet rearrangement).
  - **Evidence pointer** Results: "Water molecules structure the induced states", "Molecular switches toggle between TF functional states"; Figs. 5D, S17
  - **Concern** The model of "molecular switches" is presented as a coherent mechanism, but the evidence linking the observed energetic changes to specific structural rearrangements is largely inferential. The text states that the transition is "invisible in structural models" and relies on comparing HX/MS data with static crystal structures. The proposed "strand slipping" mechanism in the beta-sheet is a significant structural claim that is not directly supported by the data presented. The connection between the energetic changes at specific residues and the proposed functional outcome (e.g., release of the hinge helix from DNA) is not demonstrated mechanistically.
  - **Why it matters** The "molecular switch" model is a key conceptual output of the paper. If the structural interpretation is not well-supported, the model remains a speculative hypothesis rather than a data-driven conclusion.
  - **Resolution test** The authors should clarify which specific data points support each proposed switch. For example, they could show that mutations in the proposed switch residues have the predicted effects on DNA binding affinity or inducer response, or they could use MD simulations to directly observe the proposed conformational transitions and correlate them with the energetic changes.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of the "energetic blueprint" concept
  - **Claim pointer** The manuscript claims that the "energetic blueprint" is a conserved feature of the LacI/GalR TF family and that this concept can be used for rational design.
  - **Evidence pointer** Results: "LacI/GalR TFs and PBPs have distinct sequence conservation"; Discussion
  - **Concern** The study examines three TFs (LacI, RbsR, GalR) and two PBPs (RbsB, MglB). While this is a reasonable sample, the claim of a conserved "energetic blueprint" for the entire LacI/GalR family is a strong generalization from a small number of paralogs. The sequence conservation analysis (Fig. 1B) shows valleys of diversity, but the relationship between sequence conservation and the conservation of the energetic blueprint is not explicitly established. The authors do not demonstrate that the identified energetic features are conserved across a broader phylogenetic range of TFs.
  - **Why it matters** The broader significance of the work depends on the generality of the findings. If the energetic blueprint is specific to these three TFs, its utility for understanding protein evolution and for design purposes is limited.
  - **Resolution test** The authors should temper their claims of family-wide conservation or provide additional evidence, such as HX/MS data on a more distantly related TF, or a bioinformatic analysis showing that the residues involved in the energetic switches are conserved across the family in a way that correlates with function.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Results: "LacI/GalR TFs are structurally similar in different functional states"
  - **Evidence pointer** Fig. 1E–G
  - **Issue** The statement that "an evolutionarily conserved activation mechanism in the LacI/GalR family cannot be gleaned from the available structural information" is presented as a motivation for the HX/MS work, but the logic is slightly unclear. The fact that only LacI has structures in both states, and that the structures are similar, does not preclude a conserved mechanism; it simply means it is not visible in the static structures.
  - **Required correction** Rephrase to clarify that the structural similarity across states motivates the need for a dynamic, energetic view, rather than stating that a mechanism cannot be gleaned.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods: Molecular dynamics simulations
  - **Evidence pointer** Methods section
  - **Issue** The description of the MD simulations is brief. The force field parameters for the ligands (IPTG, ribose, galactose) are not described. It is unclear if standard parameters were used or if they were derived specifically.
  - **Required correction** Provide details on how ligand parameters were generated and validated.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results: "Measuring the local stabilities of VFT protein functional states"
  - **Evidence pointer** Fig. 2
  - **Issue** The text mentions that some effects are "conserved in all VFT-fold proteins" (Fig. 2D-3, 2D-5), but the definition of "conserved" in this context is not explicitly stated. Is it a qualitative observation or a quantitative threshold?
  - **Required correction** Define the criteria for calling an effect "conserved" across the five proteins.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Results: "Binding to operator DNA has long-range allosteric effects in all TFs"
  - **Evidence pointer** Fig. 3
  - **Issue** The finding that the metastable helix (H32) is stabilized by operator binding but is not conserved in sequence is interesting. The authors suggest that evolution might tune this region. It would be helpful to know if the energetic stabilization of H32 is also observed in the apo state relative to a fully unfolded state, or if it is only a relative change between states.
  - **Required correction** Clarify whether the "metastability" is an intrinsic property of the helix or a state-dependent property.

## Risk / unsupported claims
- The claim that the "energetic blueprints" of TFs and PBPs are "largely distinct" is supported by the data, but the claim that this represents a general principle of fold evolution is an extrapolation from a small number of proteins.
- The proposed "strand slipping" mechanism in the beta-sheet is a specific structural hypothesis that is not directly supported by the presented data.
- The statement that the findings will "help us treat aberrant protein behavior in conserved domains in disease-related drug targets" is speculative and not supported by any data in the manuscript.
- The claim that the identified structured water molecule is "evolutionarily conserved" is based on modeling and a limited number of structures; this requires more direct experimental validation.