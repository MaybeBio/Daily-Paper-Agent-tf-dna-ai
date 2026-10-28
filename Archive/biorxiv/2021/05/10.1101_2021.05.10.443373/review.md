## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary data descriptions
- **Assessment boundary** Scientific content, methodological soundness, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that three ParA dimers, not four monomers as previously suggested, cooperatively assemble on the type Ia partition promoter of plasmid F, with a perfect inverted repeat motif serving as the primary binding site and overlapping degenerate motifs facilitating cooperative binding, a feature potentially conserved across type Ia plasmid partition systems
- **Visible evidence base** SPR stoichiometry data, gel filtration, MST, EMSA, homology modeling, HADDOCK docking, MD simulations, nanoDSF thermal stability, sequence comparisons across related plasmids
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided, raw SPR sensorgrams, detailed sequence alignments, MD simulation trajectories, statistical analysis details, and full experimental replicates

## Reviewer
- **Overall assessment** The manuscript presents a well-structured investigation into ParA-DNA interactions on the type Ia partition promoter, with a clear revision of the previously proposed stoichiometry. The combination of quantitative biochemical approaches with computational modeling is commendable. However, several technical concerns regarding the interpretation of SPR stoichiometry, the indirect nature of the modeling evidence, and the generalizability claims based on limited sequence analysis need to be addressed before the central conclusions can be fully established.
- **Who would be interested in the results, and why** Researchers studying bacterial plasmid segregation, transcriptional autoregulation mechanisms, ParA/ParB partition systems, and those interested in protein-DNA cooperative binding. The findings have implications for understanding conserved regulatory mechanisms across diverse plasmid systems and potentially for synthetic biology applications involving partition systems.
- **Major strengths** The study directly challenges a previously published stoichiometry using quantitative methods, providing a clear and testable alternative model. The combination of multiple orthogonal techniques (SPR, MST, EMSA, gel filtration) strengthens the experimental foundation. The identification of a perfect inverted repeat as the primary binding site is a concrete and mechanistically plausible finding. The comparative analysis across related and distant plasmid systems adds evolutionary context.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (SPR stoichiometry interpretation), R1-M2 (modeling evidence for dimer binding), R1-M3 (generalizability claim based on limited comparative data)
- **Assessment against Nature-style criteria** Originality: The revised stoichiometry and the proposed overlapping IR binding model represent a meaningful advance over prior work, though the conceptual framework of cooperative ParA binding is not entirely new. Scientific importance: The findings are relevant to the partition field and may have broader implications for understanding autoregulatory mechanisms in plasmid biology, but the significance is moderate rather than transformative. Interdisciplinary readership: The work will primarily appeal to microbiologists and molecular biologists; the biophysical and computational components are supportive rather than central. Technical soundness: The experimental design is generally sound, but the interpretation of SPR stoichiometry requires additional validation, and the modeling evidence is indirect. Readability for nonspecialists: The manuscript is clearly written and accessible, with logical flow from experimental observations to model building.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the SPR stoichiometry interpretation and the strength of the modeling evidence for the proposed binding model.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental interpretation
- **Claim pointer** The authors claim that SPR measurements demonstrate a stoichiometry of three ParA dimers per promoter DNA fragment, contradicting the previously proposed four monomers.
- **Evidence pointer** Results section, Figure 2C, Supplementary Figure S1B
- **Concern** The calculation of stoichiometry from SPR response units relies on the assumption that the signal is directly proportional to the mass of bound protein and that the immobilized DNA is fully active. The authors acknowledge variability in binding isotherms (Supplementary Table S1) but do not provide a detailed error analysis for the stoichiometry calculation. The claim of exactly three dimers (six monomers) requires a precision that may not be achievable with the described approach, especially given the reported variability. Additionally, the authors do not discuss how the orientation of immobilized DNA or potential steric effects might influence the maximum achievable stoichiometry.
- **Why it matters** The central conclusion of the paper rests on this stoichiometric determination. If the actual stoichiometry is between two and four dimers, or if the measurement is not sufficiently precise, the proposed model of three dimers binding to overlapping motifs would be weakened.
- **Resolution test** Provide a detailed statistical analysis of the stoichiometry measurements across multiple independent experiments, including confidence intervals. Include control experiments demonstrating that the immobilized DNA is fully accessible and that the response unit to mass conversion is valid for this system. Consider an orthogonal method, such as analytical ultracentrifugation or native mass spectrometry, to confirm the stoichiometry.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors propose that ParA dimers bind to the inverted repeat motifs IR3-4 and IR2-2, with the dimer spanning the two hexamer sequences separated by 28 bp.
- **Evidence pointer** Results section, Figure 5A, Figure 5C
- **Concern** The evidence for dimer binding to the IR motifs is derived primarily from homology modeling and docking simulations, not from direct experimental interrogation of the protein-DNA complex. The authors state that mutations in motif 2 abolished protection of motif 2, but this is cited from previous work and not demonstrated here. The docking model relies on a homology model of ParA, which may not accurately represent the true structure, particularly in the flexible wHTH region that the authors themselves show undergoes significant conformational changes.
- **Why it matters** The proposed model of overlapping IR motifs as the basis for cooperative binding of three dimers depends critically on the assumption that a single ParA dimer can simultaneously contact two hexamer motifs separated by 28 bp. If the dimer cannot span this distance, the model would need substantial revision.
- **Resolution test** Provide direct experimental evidence for dimer binding to the IR motifs, such as footprinting with a defined dimeric ParA construct, or crosslinking studies to demonstrate simultaneous contact with both hexamer sequences. Alternatively, use a higher-resolution structural approach, such as cryo-EM or X-ray crystallography, to visualize the ParA-DNA complex.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors propose that the overlapping IR binding organization is conserved across type Ia plasmid partition systems, based on analysis of a limited set of related promoters and two more distant systems.
- **Evidence pointer** Results section, Figure 5C-E, Supplementary Figure S5
- **Concern** The comparative analysis is based on sequence inspection and logo generation from 16 related promoters, but the functional significance of the identified motifs is not experimentally tested in any system other than plasmid F. The claim of conservation is therefore speculative, particularly for the more distant systems where the binding motifs are described as degenerate.
- **Why it matters** The broader significance of the work depends on the generality of the proposed mechanism. If the overlapping IR organization is not functionally conserved, the impact of the findings is limited to the F plasmid system.
- **Resolution test** Perform mutational analysis of the proposed IR motifs in at least one additional plasmid system to demonstrate functional conservation. Alternatively, clearly frame the conservation claim as a hypothesis requiring further testing, and temper the language in the abstract and discussion accordingly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that "three ParA dimers bind to this region" without explicitly mentioning that this is a revision of the previously proposed four-monomer model. The novelty of the finding would be clearer if the contrast with prior work was stated directly.
- **Required correction** Add a brief phrase in the abstract noting that this contradicts the previously proposed stoichiometry, for example "in contrast to the previously proposed four monomers."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** SPR methods
- **Evidence pointer** Materials and Methods, Surface Plasmon Resonance assays
- **Issue** The description of SPR experiments does not specify the DNA immobilization strategy (e.g., biotinylation position, density) or the range of protein concentrations tested. This information is important for assessing the reliability of the stoichiometry calculation.
- **Required correction** Add details on DNA probe design, immobilization density, and the concentration range used for the stoichiometry experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3D
- **Evidence pointer** Results section, Figure 3D
- **Issue** The EMSA binding curve is described as having a "sharp slope suggesting high cooperativity," but no Hill coefficient or quantitative measure of cooperativity is provided.
- **Required correction** Report the Hill coefficient or other quantitative measure of cooperativity from the fitted curve, or state explicitly why such a measure cannot be reliably extracted.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, ParB stimulation
- **Evidence pointer** Results section, Figure 3E
- **Issue** The eight-fold stimulation of ParA binding by ParB is reported, but the mechanism is not discussed in the context of the proposed overlapping IR model. It is unclear whether ParB affects the stoichiometry or the cooperativity of ParA binding.
- **Required correction** Add a brief discussion of how ParB-mediated stimulation might relate to the proposed model, or state that the mechanism remains to be determined.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Location not provided
- **Issue** The term "monomers" is used in the introduction to describe the previously proposed binding mode, but the authors later use "dimers" for their own model. The transition between these terms could be confusing for readers.
- **Required correction** Ensure consistent use of "monomer" and "dimer" throughout, and explicitly define the oligomeric state being discussed in each context.

## Risk / unsupported claims
- The claim that three ParA dimers bind to the promoter region is supported by SPR data, but the precision of the stoichiometry measurement is not fully established given the acknowledged variability in binding isotherms.
- The proposal that the wHTH domain mediates cooperative protein-protein interactions between ParA dimers is speculative and not directly tested.
- The claim that the overlapping IR organization is conserved across type Ia plasmid partition systems is based on sequence analysis alone and lacks functional validation in other systems.
- The statement that the last alpha-helix of ParA is not conserved among ParA members is presented without supporting data or references.
- The assertion that the IR3-4 motif is sufficient to nucleate binding of three dimers is based on a single SPR experiment with an 85-bp probe, and the authors note that higher protein concentrations were required, suggesting the binding may be less stable than on the full promoter.