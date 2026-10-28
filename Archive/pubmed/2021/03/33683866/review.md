## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report the design of a cyclic heptapeptide, c[(D)-beta-homoAla-DPETGE], that recapitulates the 20 nM binding affinity of Nrf2 for KEAP1, starting from a linear peptide GDEETGE (K(D) = 4.3 muM). They attribute the affinity improvement to conformational optimization without altering KEAP1-interacting residues, supported by X-ray crystallography, NMR, modeling, and machine learning analysis of ligand strain. They also identify conserved hydrophobic residues flanking the core DxETGE motif as conformationally important.
- **Visible evidence base** Abstract text only; no experimental details, structural coordinates, affinity measurements, or machine learning methodology are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, crystallographic statistics, NMR data, machine learning model details, binding assay protocols, and any statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a compelling and potentially significant result: the recapitulation of a native protein-protein interaction affinity in a minimal cyclic peptide through conformational optimization alone. The conceptual framework, distinguishing conformational preorganization from ligand strain, is intellectually appealing and could have broad utility. However, the abstract alone provides insufficient evidence to evaluate the rigor of the structural analyses, the validity of the machine learning approach, or the robustness of the binding data. The claim that no differences in binding residue conformation or interactions were observed despite large affinity variations is surprising and requires careful scrutiny of the crystallographic evidence. The identification of conserved hydrophobic residues as conformationally important is an interesting addition but is not substantiated in the abstract.
- **Who would be interested in the results, and why** Researchers in peptide and macrocycle drug design, particularly those targeting protein-protein interactions; structural biologists using crystallography and NMR to study ligand binding; computational chemists developing machine learning tools for analyzing ligand strain and conformational preorganization; and medicinal chemists interested in KEAP1-Nrf2 as a therapeutic target for oxidative stress and inflammation.
- **Major strengths** The conceptual advance of separating conformational preorganization from ligand strain is novel and potentially generalizable. The use of multiple orthogonal techniques (X-ray, NMR, ML) is commendable. The achievement of full native affinity in a 7-mer cyclic peptide is a significant practical result. The identification of flanking hydrophobic residues adds a new dimension to understanding KEAP1-Nrf2 recognition.
- **Major Concerns** 
  - R1-M1: The central claim that affinity improvement is due solely to conformational optimization, without any change in KEAP1-interacting residues, is not verifiable from the abstract. The statement that "no obvious differences" were observed in binding residue conformation or interactions is qualitative and requires quantitative structural comparison.
  - R1-M2: The machine learning analysis identifying "locations of strain" through "subangstrom distortions" is described without any methodological detail. The validity, training set, features, and statistical significance of this approach cannot be assessed.
  - R1-M3: The binding affinity data (20 nM for the cyclic peptide vs 4.3 muM for the linear peptide) are presented without experimental context, such as assay type, replicates, or error estimates.
  - R1-M4: The claim that conserved hydrophobic residues flanking the DxETGE motif play a "conformational role" is not supported by any specific evidence in the abstract.
- **Minor Comments** 
  - R1-m1: The abstract does not specify the NMR experiments used or what information they provided beyond the X-ray structures.
  - R1-m2: The term "recapitulating" in the title is strong; the abstract should clarify whether this means achieving equivalent affinity or reproducing the full binding mechanism.
  - R1-m3: The role of the non-natural residue (D)-beta-homoAla is not explained; its contribution to the design is unclear.
  - R1-m4: The abstract would benefit from stating the number of peptide variants studied and the range of affinities observed.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** 
  - Originality: High. The conceptual separation of conformational preorganization from ligand strain, and the use of ML to identify strain locations, is a fresh approach.
  - Scientific importance: High for the PPI targeting field and for KEAP1-Nrf2 specifically. The generalizability claim, if supported, would elevate importance further.
  - Interdisciplinary readership: Moderate to high. The work bridges structural biology, computational chemistry, and peptide design, but the abstract is written in a specialized manner that may limit accessibility.
  - Technical soundness: Not assessable from the abstract. The structural and computational claims require full experimental detail.
  - Readability for nonspecialists: Moderate. The abstract is dense and assumes familiarity with peptide design and PPI concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the result is potentially significant, but the abstract alone does not establish the case. Full evaluation of the structural, computational, and binding data is required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** "We show that the full 20 nM binding affinity of Nrf2 for KEAP1 can be recapitulated in a cyclic 7-mer peptide... solely by optimizing the conformation of the cyclic compound, without changing any KEAP1 interacting residue."
- **Evidence pointer** Abstract; location not provided
- **Concern** The claim that affinity improvement is achieved solely through conformational optimization, with no changes to interacting residues, is central to the paper's thesis. However, the abstract provides no quantitative comparison of the binding conformations or interaction networks between the linear and cyclic peptides. The statement that "no obvious differences" were observed is qualitative and could mask subtle but functionally important changes.
- **Why it matters** If the interacting residues do adopt different conformations or make different contacts, the conclusion that conformational preorganization alone drives affinity would be weakened. The distinction between preorganization and strain is the conceptual core of the paper.
- **Resolution test** Provide quantitative structural comparisons (e.g., RMSD of binding residue side chains, interaction distance/angle distributions) between the linear and cyclic peptide complexes, with appropriate statistical analysis, demonstrating that the binding epitope is effectively identical.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Analysis of the X-ray structures by machine learning showed that locations of strain in the bound ligand could be identified through patterns of subangstrom distortions from the geometry observed for unstrained linear peptides."
- **Evidence pointer** Abstract; location not provided
- **Concern** The machine learning methodology is described in a single sentence with no details on the training data, features, model architecture, validation, or statistical significance. The concept of identifying "strain" through "subangstrom distortions" is not defined, and it is unclear how this differs from conventional structural analysis.
- **Why it matters** The ML analysis is presented as a key methodological innovation and a primary source of evidence for the strain hypothesis. Without methodological transparency, the results cannot be reproduced or independently verified.
- **Resolution test** Provide a full description of the ML approach, including training set composition, feature definitions, model selection, cross-validation, and a clear definition of how "strain" is quantified. Show that the ML predictions are statistically robust and that the identified strain locations correlate with experimentally measured affinities.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "The full 20 nM binding affinity of Nrf2 for KEAP1 can be recapitulated in a cyclic 7-mer peptide... This compound was identified from the Nrf2-derived linear peptide GDEETGE (K(D) = 4.3 muM)."
- **Evidence pointer** Abstract; location not provided
- **Concern** The binding affinities are presented as single values without experimental context. No assay type, number of replicates, error estimates, or statistical analysis are provided. The 200-fold improvement in affinity is the quantitative foundation of the paper.
- **Why it matters** Binding affinity measurements can vary significantly depending on assay conditions. Without error estimates and experimental details, the reliability of the reported values cannot be assessed.
- **Resolution test** Provide full binding assay details, including method (e.g., ITC, SPR, fluorescence polarization), buffer conditions, temperature, number of independent replicates, and standard errors or confidence intervals for all reported K(D) values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim validity
- **Claim pointer** "We also identify a pair of conserved hydrophobic residues flanking the core DxETGE motif which play a conformational role in facilitating the high-affinity binding of Nrf2 to KEAP1."
- **Evidence pointer** Abstract; location not provided
- **Concern** This claim introduces a new finding about conserved hydrophobic residues but provides no evidence in the abstract. It is unclear which residues are meant, how conservation was established, or what "conformational role" means mechanistically.
- **Why it matters** This appears to be a secondary finding that may be of interest to the KEAP1-Nrf2 field, but as presented it is an unsupported assertion.
- **Resolution test** Provide sequence alignment data showing conservation, structural evidence for the conformational role (e.g., mutagenesis or structural comparison), and a clear mechanistic explanation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods description
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract mentions NMR as a guiding technique but does not specify what NMR data were collected or how they informed the design.
- **Required correction** Briefly state the NMR experiments performed (e.g., NOESY, chemical shift perturbation) and their role in the design process.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Precision
- **Affected element** Title and terminology
- **Evidence pointer** Title; location not provided
- **Issue** The term "recapitulating" could be interpreted as reproducing the full binding mechanism, not just the affinity. The abstract should clarify the intended meaning.
- **Required correction** Define "recapitulating" in the context of this work, e.g., "achieving equivalent binding affinity" or "reproducing the key binding interactions."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Compound design
- **Evidence pointer** Abstract; location not provided
- **Issue** The role of the non-natural residue (D)-beta-homoAla in the cyclic peptide is not explained. Its inclusion is presumably important for the design but is not discussed.
- **Required correction** Briefly explain the rationale for incorporating this residue and its contribution to the peptide's properties.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Context
- **Affected element** Results summary
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not state how many peptide variants were synthesized and tested, which would provide context for the optimization process.
- **Required correction** Include the number of variants studied and the range of affinities observed to contextualize the final result.

## Risk / unsupported claims
- The claim that affinity improvement is due solely to conformational optimization without changes in interacting residues is unsupported without quantitative structural comparison.
- The machine learning identification of strain locations is unsupported without methodological details.
- The reported binding affinities are unsupported without experimental context and error estimates.
- The identification of conserved hydrophobic residues and their conformational role is unsupported without sequence and structural evidence.
- The generalizability of the approach to other ligand-receptor systems is a reasonable speculation but is not demonstrated.