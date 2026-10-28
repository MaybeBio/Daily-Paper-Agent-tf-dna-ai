## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends as embedded in text)
- **Assessment boundary** Scientific content, technical soundness, and internal consistency of the provided manuscript only; no external literature verification or replication of experiments
- **Shared manuscript claim summary** The authors present four cryo-EM structures of E. coli MutS in nucleotide-bound states (ADP, ATP:ADP, AMPPNP, ADP-Vi) and propose a mechanistic model where ATP binding closes the MutS dimer, two ATPs are required for clamp formation, DNA binding modulates the ATPase cycle, and ssDNA triggers nucleotide release and reset
- **Visible evidence base** Four cryo-EM structures (resolution 3.3–4.8 Å), negative stain EM, FRET assays, bio-layer interferometry (BLI) dissociation measurements, and reference to prior published structures (cited as refs 22, 25, 36)
- **Missing materials affecting confidence** Full figure panels and supplementary figures not provided; Table 1 (cryo-EM data collection and refinement statistics) and Table 2 (mutation effects) referenced but not included; Supplementary Table 1 (DNA substrates) not included; Supplementary Videos 1–3 not accessible; detailed methods for FRET data analysis and BLI fitting not fully described; no raw data or statistical analysis details for FRET and BLI experiments

## Reviewer
- **Overall assessment** The manuscript addresses a significant and timely question in DNA mismatch repair: how ATP binding and hydrolysis in MutS coordinate conformational changes across the repair cascade. The four cryo-EM structures provide a valuable series of snapshots that, if validated, would substantially advance mechanistic understanding. However, the current presentation has several technical gaps that limit confidence in the central claims. The resolution of the ADP-bound structure (4.8 Å) is modest, and the interpretation of conformational states relies heavily on comparisons with previously published structures. The FRET and BLI experiments are described with insufficient quantitative detail to assess robustness. The claim that ssDNA triggers nucleotide release is supported by indirect measurements and would benefit from direct binding or structural evidence. Overall, the work is potentially important but not yet fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in DNA repair, ATP-dependent molecular machines, and structural biology. The structures provide a framework for understanding how ABC ATPase family members couple nucleotide state to conformational change, which is relevant beyond mismatch repair. The proposed model of DNA-modulated ATPase cycling and ssDNA-triggered release has implications for understanding MutS homolog function in eukaryotes and for therapeutic targeting of repair pathways.
- **Major strengths** The study provides a series of nucleotide-bound structures that capture sequential states of the ATPase cycle, which is a notable advance over single-state structures. The combination of structural and biophysical approaches (FRET, BLI) strengthens the functional interpretation. The proposed model integrates prior observations and offers testable predictions. The writing is clear and accessible for a broad audience.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (ADP structure resolution and interpretation), R1-M2 (FRET quantitative support), R1-M3 (BLI ssDNA release claim), R1-M4 (ATP:ADP asymmetry interpretation)
- **Assessment against Nature-style criteria** Originality: High. The sequential cryo-EM structures of MutS across the ATPase cycle are novel and provide mechanistic insight not previously available. Scientific importance: High. The work addresses a fundamental question in a conserved DNA repair pathway and has implications for ABC ATPase mechanisms broadly. Interdisciplinary readership: Moderate to high. The topic will appeal to structural biologists, biochemists, and DNA repair specialists, but the broader cell biology community may find the scope narrow. Technical soundness: Moderate. The cryo-EM structures are generally well-executed, but the modest resolution of the ADP state and the indirect nature of some functional assays weaken the overall rigor. Readability for nonspecialists: Good. The abstract and introduction are accessible, and the figures are described clearly, though the results section assumes familiarity with the field.
- **Recommendation posture** Supportive if technical concerns are resolved. The core structural work is valuable and likely publishable in a high-impact venue, but the functional claims require stronger quantitative support and clearer presentation of the data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The ADP-bound structure is described as an "open" form, and the transition to the ATP-bound state involves a 35° rotation. The authors use this to propose that ATP binding closes the dimer.
- **Evidence pointer** Results section "Structures apo MutS at sequential stages of the ATP hydrolysis cycle"; Figure 1; Table 1 (not provided)
- **Concern** The ADP-bound structure is determined at 4.8 Å resolution, which is relatively low for cryo-EM. At this resolution, the assignment of specific conformational states and the interpretation of domain movements (e.g., the 35° rotation) may be unreliable. The authors state that the clamp domains are poorly resolved in all four structures, which further complicates interpretation. The comparison between the ADP and ATP states relies on rigid-body fitting and may be sensitive to model bias. The authors should provide additional validation, such as local resolution maps, cross-validation of the domain movements, or higher-resolution data for the ADP state.
- **Why it matters** The central mechanistic claim that ATP binding induces a large conformational closure depends on the accuracy of the ADP and ATP structures. If the ADP structure is not reliable, the proposed sequence of conformational changes is not established.
- **Resolution test** Provide local resolution estimates for the ADP map, show that the domain movements are robust to different refinement strategies, or obtain a higher-resolution ADP structure. Alternatively, support the conformational change with an independent method (e.g., SAXS or FRET in solution).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The FRET experiments are used to conclude that "a single ATP bound in the MutS dimer is not sufficient to generate enough force to displace the mismatch and connector domains" and that two ATPs are needed for clamp formation.
- **Evidence pointer** Results section "Two ATP molecules are needed to bring about clamp-state MutS"; Figure 3
- **Concern** The FRET data are described qualitatively. The authors report "low FRET" with ADP and ATP, and an increase with AMPPNP, but no quantitative values (e.g., FRET efficiency, distances) or statistical analysis are provided. The interpretation that the lack of FRET increase with ATP is due to hydrolysis and single ATP occupancy is plausible but not directly tested. The authors do not show control experiments (e.g., with a hydrolysis-deficient mutant) to confirm that the ATP effect is due to hydrolysis. The FRET signal in the presence of DNA and ATP is described as a "strong increase," but the magnitude and reproducibility are not documented.
- **Why it matters** The claim that two ATPs are required for clamp formation is a key mechanistic conclusion. Without quantitative FRET data and appropriate controls, the conclusion is not robustly supported.
- **Resolution test** Provide FRET efficiency values with standard deviations, show representative traces, include a hydrolysis-deficient MutS mutant (e.g., E713A) as a control, and perform the experiments at multiple ATP concentrations to demonstrate a dose response.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The BLI experiments are used to conclude that "the ten-nucleotide gap is equal in size to the DNA footprint of the MutS dimer" and that ssDNA triggers release of MutS from DNA.
- **Evidence pointer** Results section "In clamp state MutS, dsDNA prevents nucleotide release from the ATPase active site"; Figure 4
- **Concern** The BLI experiments measure dissociation of MutS from DNA substrates with different gap sizes, but the authors do not provide the raw data, fitting procedures, or statistical analysis. The claim that the dissociation rate plateaus at a 10-nucleotide gap is based on a single figure panel, and the relationship between the gap size and the MutS footprint is inferred rather than directly measured. The authors do not show that the effect is specific to ssDNA versus other DNA structures (e.g., bulges or flaps). The interpretation that ssDNA triggers nucleotide release is indirect, as the BLI assay measures DNA dissociation, not nucleotide release.
- **Why it matters** The proposed release mechanism is central to the model of how MutS terminates the repair cascade. If the BLI data are not robust or the interpretation is overextended, the model is weakened.
- **Resolution test** Provide representative BLI traces, show the fitting model and goodness-of-fit, include statistical analysis (e.g., error bars, replicates), and test additional DNA substrates (e.g., ssDNA of varying lengths, bulged DNA) to confirm specificity. Consider a direct assay for nucleotide release (e.g., mant-ATP fluorescence).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The ATP:ADP structure is interpreted as an asymmetric state where one ATP is bound and the other site contains ADP, and this asymmetry is linked to the alternating ATPase activity.
- **Evidence pointer** Results section "Structures apo MutS at sequential stages of the ATP hydrolysis cycle"; Figure 1; Extended Data Figures 1–4
- **Concern** The authors state that the ATP:ADP structure shows one ATP and one ADP, but the occupancy and identity of the nucleotides are not clearly described. The resolution of this structure (3.3 Å) is sufficient to identify nucleotides, but the authors do not provide details on how the nucleotide identities were assigned (e.g., based on density shape, coordination, or comparison with AMPPNP/ADP-Vi structures). The functional significance of the asymmetry is discussed but not directly tested. The authors do not address whether the asymmetry is a stable feature or a snapshot of a dynamic process.
- **Why it matters** The asymmetric nucleotide binding is a notable finding that could explain the alternating ATPase activity, but the evidence is not fully presented. If the assignment is incorrect, the mechanistic model would need revision.
- **Resolution test** Provide clear density maps for the nucleotide-binding sites in the ATP:ADP structure, describe the criteria for nucleotide assignment, and consider mutational analysis to test the functional role of asymmetry.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "ATP binding and hydrolysis induces a closing and opening of the MutS dimer, respectively," but the results show that the opening is associated with ADP release and the transition to the open state, not hydrolysis per se. The wording is imprecise.
- **Required correction** Rephrase to clarify that ATP binding closes the dimer and nucleotide hydrolysis/release opens it, or specify the exact step.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, BLI assay
- **Evidence pointer** Methods section "Biolayer Interferometry DNA assay"
- **Issue** The BLI assay uses a single MutS concentration (200 nM) and a single ATP concentration (2 mM). The authors do not report whether the dissociation rates are concentration-dependent, which would strengthen the interpretation.
- **Required correction** Include a concentration series for MutS and ATP, or justify the chosen concentrations with reference to prior work.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Figure 1
- **Evidence pointer** Results section "Structures apo MutS at sequential stages of the ATP hydrolysis cycle"; Figure 1
- **Issue** The description of the domain movements (35° rotation, 6° twist) is clear, but the pivot point and axis of rotation are not defined in the text. This makes it difficult to visualize the conformational changes.
- **Required correction** Define the pivot point and axis of rotation in the text or figure legend, or refer to a supplementary video for clarity.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions that the "open conformation of the ATPase domains is retained when MutS first encounters a mismatch," but the structural basis for this is not shown in the current manuscript. The authors refer to prior work (ref 22), but a brief explanation would help the reader.
- **Required correction** Add a sentence summarizing the prior structural evidence for the mismatch-bound open state.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, FRET assay
- **Evidence pointer** Methods section "FRET assay"
- **Issue** The FRET assay uses a heterodimeric MutS with labels at specific positions, but the authors do not report the labeling efficiency or whether the labels affect MutS function. This is important for interpreting the FRET signal.
- **Required correction** Report labeling efficiency and include a functional assay (e.g., ATPase activity) to confirm that labeled MutS is active.

## Risk / unsupported claims
- The claim that "both monomers need to have hydrolysed ATP before MutS can bind DNA" is inferred from the structures but not directly tested. The authors do not provide experimental evidence for this temporal ordering.
- The claim that "the ten-nucleotide gap is equal in size to the DNA footprint of the MutS dimer" is based on a single BLI experiment and is not supported by direct structural or footprinting data.
- The claim that "ssDNA triggers nucleotide release" is inferred from BLI dissociation measurements but not directly demonstrated. No assay for nucleotide release is presented.
- The functional significance of the asymmetric ATP:ADP state is discussed but not experimentally validated. The authors do not test whether disrupting asymmetry affects ATPase activity or clamp formation.
- The statement that "the DNA keeps the ATPase domains in an open, non-catalytic state" during scanning is based on prior structures (ref 22) and is not directly addressed in the current manuscript.