## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and data availability statements
- **Assessment boundary** Scientific content, structural and biochemical evidence, internal consistency, and support for claims as presented in the provided text
- **Shared manuscript claim summary** The authors present cryo-EM structures of the Polθ helicase domain in apo, AMP-PNP-bound, and DNA-bound states, and propose a stepwise mechanism for microhomology search and annealing during MMEJ, involving dimerization, conformational opening, and D5 domain relocation
- **Visible evidence base** Cryo-EM reconstructions at 3.1-3.8 Å resolution, native gel shift and fluorescence anisotropy DNA binding assays, structural comparisons with a previously reported crystal structure (PDB 5AGA)
- **Missing materials affecting confidence** Figures and extended data figures referenced but not provided; Table 1 referenced but not provided; no validation statistics or map quality metrics beyond resolution values; no biochemical data directly testing the proposed mechanism beyond binding affinity

## Reviewer
- **Overall assessment** This manuscript presents a substantial structural dataset that will be of considerable interest to the DNA repair community. The cryo-EM structures of Polθ-hel in multiple functional states are a valuable contribution, and the proposed model for microhomology search and annealing is mechanistically plausible. However, the current evidence base is insufficient to fully establish several key claims, particularly regarding the functional significance of the D5 domain relocation and the assignment of specific states to distinct steps in the MMEJ pathway. The manuscript would be strengthened by additional biochemical or mutational experiments that directly test the proposed mechanism.
- **Who would be interested in the results, and why** Researchers studying DNA double-strand break repair, particularly alternative end-joining pathways, will find these structures highly relevant. The work also has direct implications for cancer biology and therapeutic development, given the ongoing clinical interest in Polθ inhibitors for HR-deficient tumors. Structural biologists studying helicase mechanisms and protein-DNA interactions will also find the conformational analyses of interest.
- **Major strengths** The manuscript provides a comprehensive set of cryo-EM structures covering multiple functional states of Polθ-hel, which is a significant technical achievement. The observation of a DNA-bound dimeric state and the identification of a mobile D5 domain are novel findings that advance our understanding of Polθ function. The proposed model is clearly articulated and provides a useful framework for future studies.
- **Major Concerns** The major concerns are detailed below. The most significant issues relate to the limited functional validation of the structural observations, the lack of quantitative support for several key claims, and the absence of critical methodological details that would allow assessment of map quality and model reliability.
- **Minor Comments** Several minor issues are noted that would improve clarity and rigor.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** The manuscript addresses a question of high scientific importance in DNA repair and cancer biology. The structural data are original and technically sound, though the functional claims extend beyond what the current evidence directly supports. The topic has clear interdisciplinary relevance spanning structural biology, DNA repair, and oncology. The manuscript is generally well-written and accessible to nonspecialists, though some sections assume familiarity with helicase nomenclature. The main weakness is the gap between the structural observations and the functional conclusions drawn from them.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly if the authors provide additional functional validation of the proposed mechanism and clarify the limitations of the current evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The authors claim that the D5 domain relocation is "critical for facilitating the tetramer-to-dimer transition and further solidifying the dimer interface for the MMEJ process" and that the observed states represent "sequential conformations adopted by Polθ-hel during the critical phases of DNA binding, microhomology searching, and microhomology annealing."
- **Evidence pointer** Results sections "Architecture of Polθ-hel bound to DNA in multiple states" and "Polθ-hel D5 is a mobile domain"; Discussion
- **Concern** The assignment of specific structural states to distinct functional steps in the MMEJ pathway is largely inferential. The authors observe different D5 positions in different DNA constructs, but no experiments directly test whether D5 relocation is required for microhomology annealing or whether the proposed "search" and "annealed" states are functionally distinct. The claim that D5 relocation is "critical" for the process is not supported by any loss-of-function or mutational analysis. Without such experiments, the mechanistic model remains speculative.
- **Why it matters** The central claim of the manuscript is that the structures reveal the mechanism of microhomology search and annealing. If the assignment of states to functional steps is not validated, the mechanistic conclusions are not established.
- **Resolution test** Provide mutational or biochemical experiments that disrupt D5 relocation (e.g., deletion of the D5 domain, mutations at the D5-D4 interface) and demonstrate a defect in microhomology annealing or MMEJ activity in vitro or in cells.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support
- **Claim pointer** The authors state that DNA binding promotes "dissociation of the tetramers into two dimers" and that the dimer is the "functional oligomeric unit."
- **Evidence pointer** Results section "Architecture of Polθ-hel bound to DNA in multiple states"; Figure 1g
- **Concern** The claim that DNA binding promotes tetramer dissociation is based on qualitative observations of 2D class averages and particle distributions. No quantitative analysis is provided, such as the relative proportions of dimer, tetramer, and monomer in the presence versus absence of DNA. The statement that the tetramer is "incompatible with DNA binding" is based on the absence of DNA density in one tetramer reconstruction, but this could reflect a low-affinity or transient interaction rather than incompatibility.
- **Why it matters** The oligomeric state of Polθ-hel is central to the proposed mechanism. If the tetramer-to-dimer transition is not quantitatively demonstrated, the functional significance of the dimeric state is not established.
- **Resolution test** Provide quantitative particle classification statistics for each dataset, showing the distribution of oligomeric states in the presence and absence of DNA. If possible, perform size-exclusion chromatography or mass photometry to independently confirm the DNA-induced shift in oligomeric state.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural validation
- **Claim pointer** The authors report cryo-EM reconstructions at resolutions ranging from 3.1 to 3.8 Å and state that "well-defined nucleotide densities inside the channel facilitated the DNA model building process."
- **Evidence pointer** Results section "Architecture of Polθ-hel bound to DNA in multiple states"; Methods section "CryoEM data processing"; Table 1
- **Concern** The manuscript does not provide sufficient validation details for the cryo-EM structures. Table 1 is referenced but not provided, and no information is given on map quality metrics such as local resolution, B-factors, or model-to-map correlation. The statement that DNA density is "well-defined" is not supported by any figures or quantitative measures. Additionally, the DNA density outside the channel is described as "less well-defined," yet a standard B-form duplex was placed into this density and used to support the "annealed" state assignment. This is a potential overinterpretation of weak density.
- **Why it matters** The structural conclusions depend entirely on the quality of the cryo-EM maps and the accuracy of the models built into them. Without adequate validation, the reliability of the proposed conformations and interactions cannot be assessed.
- **Resolution test** Provide Table 1 and representative map quality figures, including local resolution maps, FSC curves, and model-to-map fit statistics. For the annealed DNA density, provide evidence that the duplex placement is justified, such as a comparison of the density with a simulated map or an independent validation method.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic evidence
- **Claim pointer** The authors propose that Polθ-hel "binds to resected 3′-overhangs and dissociates replication protein A (RPA), thereby exposing the microhomology sequences necessary for end alignment and annealing."
- **Evidence pointer** Discussion
- **Concern** The claim that Polθ-hel dissociates RPA is presented without any experimental evidence. No RPA competition assays, pull-down experiments, or functional studies are described that would support this assertion. This is a significant mechanistic claim that goes beyond the structural data presented.
- **Why it matters** RPA displacement is a critical step in the proposed model of MMEJ. If this claim is not supported by evidence, the model is incomplete and potentially misleading.
- **Resolution test** Provide biochemical evidence for RPA displacement, such as a competition assay showing that Polθ-hel can displace RPA from single-stranded DNA, or a functional assay showing that Polθ-hel promotes annealing in the presence of RPA.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "DNA binding induces dimer conformational change"
- **Evidence pointer** Location not provided
- **Issue** The text states "This shit indicates a degree of flexibility in the channel exit" which appears to be a typographical error for "shift."
- **Required correction** Correct the typographical error.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods section "CryoEM sample preparation and data acquisition"
- **Evidence pointer** Location not provided
- **Issue** The manuscript states that the apo form dataset included DNA substrates with "internal loop structures," but it is unclear why DNA was present in a sample intended to represent the apo state. This could affect the interpretation of the apo structure.
- **Required correction** Clarify the composition of the apo form sample and whether any DNA was present in the final reconstruction.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results section "Architecture of Polθ-hel bound to DNA in multiple states"
- **Evidence pointer** Location not provided
- **Issue** The text describes the "MH annealed state" and "MH search state" as distinct, but the criteria for assigning a given reconstruction to one state versus the other are not clearly defined. The presence or absence of density in the dimer cleft appears to be the main criterion, but this is not stated explicitly.
- **Required correction** Define the operational criteria used to assign each structure to a specific functional state.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Results section "DNA binding induces dimer conformational change"
- **Evidence pointer** Location not provided
- **Issue** The text refers to "the previously reported crystal structure of the Polθ-hel tetramer form" and cites reference 24, but the specific PDB ID is only mentioned in the Methods section. It would be helpful to include the PDB ID at the point of first mention in the Results.
- **Required correction** Include the PDB ID when first referencing the crystal structure.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "DNA binding assay by native PAGE and fluorescence anisotropy"
- **Evidence pointer** Location not provided
- **Issue** The fluorescence anisotropy data are described as showing "similar affinity" for the different DNA substrates, but no Kd values are reported in the text. The Kd calculations are mentioned in the Methods, but the actual values are not presented.
- **Required correction** Report the calculated Kd values for each DNA substrate in the Results or in a table.

## Risk / unsupported claims
- The claim that D5 relocation is "critical" for MMEJ is unsupported by direct experimental evidence.
- The claim that Polθ-hel dissociates RPA during MMEJ is presented without any supporting data.
- The assignment of specific structural states to "search" and "annealed" phases is not validated by functional experiments.
- The claim that DNA binding promotes tetramer dissociation is based on qualitative observations without quantitative support.
- The placement of a B-form duplex into "less well-defined" density to model the annealed state is potentially overinterpreted without additional validation.