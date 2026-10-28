## Review setup
- **Input scope** Full manuscript text including abstract, methods, results, discussion, and supplementary figure legends
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report crystal structures of LlaI.R1 and LlaI.R2 from the non-canonical McrBC anti-phage defense system, showing conserved catalytic machinery, nucleotide promiscuity, and a model for DNA organization in McrBC complexes
- **Visible evidence base** Structural data (X-ray crystallography), biochemical assays (SEC, SEC-MALS, MST, nucleotide hydrolysis), mutagenesis, computational modeling (AlphaFold, docking)
- **Missing materials affecting confidence** Electron density maps, crystallographic statistics table, full supplementary figures, raw kinetic data, experimental details for MST and EMSA, coordinates validation reports

## Reviewer
- **Overall assessment** This manuscript presents structurally and biochemically significant findings on a non-canonical McrBC family member, with high-quality crystallographic data and thoughtful functional validation. The work addresses an important gap in understanding how McrBC systems diversify and organize DNA binding. However, several technical concerns regarding the interpretation of the alternating conformations, the nucleotide promiscuity claims, and the computational modeling require clarification before the conclusions can be fully supported.
- **Who would be interested in the results, and why** Researchers studying anti-phage defense systems, AAA+ motor proteins, DNA translocation mechanisms, and the evolution of nucleotide specificity in molecular machines. The structural homology between LlaI.R1 and eukaryotic DNA repair proteins (XPF/Mus81 family) will also interest the DNA repair community.
- **Major strengths** High-resolution crystal structures (1.80 Å and 1.52 Å) of two components from a non-canonical McrBC system; clear demonstration of conserved catalytic architecture despite sequence divergence; thorough biochemical characterization of nucleotide promiscuity; integration of computational modeling with experimental validation; potential translational relevance to phage therapy
- **Major Concerns** See detailed items below
- **Minor Comments** See detailed items below
- **Technical failings that need to be addressed before the case is established** R1-M1 (alternating conformation interpretation), R1-M2 (nucleotide promiscuity claims), R1-M3 (computational model validation)
- **Assessment against Nature-style criteria** Originality is high, as this is the first structural characterization of a non-canonical McrBC system with separated R1 and R2 components. Scientific importance is substantial given the growing interest in anti-phage defense systems and their potential therapeutic applications. Interdisciplinary readership is plausible, spanning microbiology, structural biology, enzymology, and evolutionary biology. Technical soundness is generally strong, though concerns about the interpretation of crystal packing artifacts and the strength of the computational modeling need addressing. Readability for nonspecialists is good, with clear explanations of complex structural concepts, though the discussion of AAA+ motor mechanisms may be dense for some readers.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the interpretation of the alternating conformations and the validation of the computational model

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The crystallized LlaI.R2 hexamer traps two distinct active site conformations that correlate to different states of the nucleotide hydrolysis cycle
- **Evidence pointer** Results section, Figure 2, Supplementary Figures S5 and S7
- **Concern** The authors attribute the alternating GDP- and citrate-bound conformations to distinct catalytic states, but they acknowledge that crystal packing interactions involving the C-terminal 6xHis tag stabilize these conformations. The 6xHis tag from a symmetry-related molecule physically prevents the nucleotide sandwiching segment from interacting with GDP, which is a non-physiological artifact. The claim that these represent "hydrolysis primed" and "post-hydrolysis" states is therefore not directly supported by the data, as the conformations may be entirely induced by crystal contacts.
- **Why it matters** The central mechanistic conclusion about the conformational cycle of the LlaI.R2 motor depends on the interpretation that these two states are catalytically relevant. If they are crystal packing artifacts, the structural basis for the proposed hydrolysis cycle is not established.
- **Resolution test** The authors should either obtain structures without the 6xHis tag interference, demonstrate that the same conformations exist in solution (e.g., via SAXS, FRET, or crosslinking), or substantially temper the claims about these representing distinct catalytic states. Alternatively, they could show that the conformations are consistent with those observed in the cryo-EM structures of canonical McrBC complexes in different nucleotide states.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** R2 proteins from LlaI and BsuMI do not discriminate between different nucleotides, even when in complex with their respective R1 partners
- **Evidence pointer** Results section, Figure 4, Figure 5, Supplementary Tables S2 and S3
- **Concern** The nucleotide hydrolysis data show that LlaI.R2 hydrolyzes ATP, XTP, and ITP at rates approximately 3-4 fold lower than GTP, and BsuMI.R2 actually hydrolyzes ATP faster than GTP. While the authors interpret this as "promiscuity," the data also show that the R1 proteins do not alter this pattern. However, the physiological relevance of this promiscuity is unclear. The authors do not test whether the R1-R2-R3 complex (the complete restriction system) shows the same nucleotide profile, and they do not measure DNA-stimulated hydrolysis, which is the relevant condition for the active restriction complex. The claim that this promiscuity may be advantageous in specific contexts is speculative without testing the complete system.
- **Why it matters** The evolutionary argument about nucleotide specificity loss in non-canonical systems depends on the functional relevance of the observed promiscuity. If the complete R1-R2-R3 complex shows different nucleotide selectivity, or if DNA binding alters the hydrolysis profile, the conclusions about the evolution of nucleotide specificity would need revision.
- **Resolution test** The authors should measure nucleotide hydrolysis in the presence of DNA substrates (methylated or unmethylated) and ideally with the complete R1-R2-R3 complex. If this is not feasible, they should clearly state this limitation and temper the evolutionary claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** These observations support computational modelling of the assembled LlaI restriction system bound to DNA
- **Evidence pointer** Results section, Discussion, Supplementary Figures S11-S16
- **Concern** The computational model of the assembled LlaI restriction system is presented as a key outcome, but the validation is limited. The authors validate the R1-R2 interface using two mutations (R2A/R46A) that disrupt heterodimerization, and one mutation in Patch 1 (R211A/R213A/K214A) that abolishes DNA binding. However, the model includes the R3 nuclease and the full DNA path, which are not experimentally validated. The claim that the model is "supported" by the mutagenesis data is overstated, as only the R1-R2 interface and one DNA-binding patch are tested.
- **Why it matters** The proposed model for DNA organization and cleavage in McRBC complexes is a major conceptual contribution. If the model is not adequately validated, the mechanistic conclusions about DNA translocation and cleavage are not established.
- **Resolution test** The authors should either provide additional experimental validation of the model (e.g., crosslinking, hydrogen-deuterium exchange, or single-particle analysis of the R1-R2-R3 complex), or clearly present the model as a hypothesis that requires further testing rather than a validated structure.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states "Canonical McrBC enzymes are nucleotide-powered, motor-driven endonucleases that bind and cleave modified bacteriophage DNA." This is accurate but could be more specific about the modification types (methylated cytosine) to orient readers unfamiliar with the system.
- **Required correction** Consider revising to "bind and cleave cytosine-methylated bacteriophage DNA" for precision.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Nucleotide hydrolysis assays
- **Evidence pointer** Methods section, "Nucleotide hydrolysis assays"
- **Issue** The hydrolysis assay description states "colorimetric malachite green assay that monitors the amount of free phosphate released over time 9" but the reference number 9 is not defined in the visible text. Additionally, the specific activity values in Supplementary Table S2 are mentioned but the calculation method is not described.
- **Required correction** Provide the full reference for the malachite green assay and describe how specific activity was calculated (e.g., nmol phosphate/min/mg protein).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, R1-R2 complex formation
- **Evidence pointer** Results section, Figure 1C and 1D
- **Issue** The SEC data for LlaI.R1-R2 complex formation show precipitation when nucleotides are added, which the authors attribute to "intrinsic propensity for aggregation and/or instability." This is a significant technical limitation that is mentioned but not discussed in detail.
- **Required correction** Provide additional discussion of this limitation and its potential impact on the interpretation of the LlaI R1-R2 complex properties.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, Mutational analysis
- **Evidence pointer** Results section, "Mutational analysis supports a model for LlaI.R1-R2 complex formation"
- **Issue** The authors state that mutations in Patches 2, 3, and 4 "reduced protein solubility, hampering our ability to purify and test these mutant constructs." This is a significant limitation for the validation of the DNA-binding model, as only Patch 1 is functionally tested.
- **Required correction** Acknowledge this limitation more prominently in the Discussion and consider alternative approaches (e.g., surface plasmon resonance with peptide fragments) to test the other patches.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion, evolutionary implications
- **Evidence pointer** Discussion section, paragraph on evolution
- **Issue** The evolutionary argument that LlaI and BsuMI "more closely resemble ancestral McrBC systems" is speculative and not directly supported by the data presented. The authors do not provide phylogenetic analysis or ancestral sequence reconstruction.
- **Required correction** Soften this claim or provide additional evolutionary analysis to support it.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Crystallization
- **Evidence pointer** Methods section, "Crystallization, X-ray data collection, and structure determination of LlaI.R2"
- **Issue** The crystallization condition for LlaI.R2 includes GDP.AlF x as a transition state mimic, but the final structure shows GDP and citrate bound. The authors speculate that crystal contacts prevent ALF x stabilization, but this is not experimentally tested.
- **Required correction** Consider testing whether the citrate-bound form is also observed in the absence of GDP.AlF x to confirm that citrate alone can induce this conformation.

## Risk / unsupported claims
- The claim that the two LlaI.R2 conformations represent "hydrolysis primed" and "post-hydrolysis" states is not fully supported, as the conformations are stabilized by non-physiological crystal packing interactions involving the 6xHis tag
- The evolutionary argument that LlaI and BsuMI resemble ancestral McrBC systems is speculative without phylogenetic analysis
- The computational model of the assembled LlaI restriction system bound to DNA is presented as supported by data, but only the R1-R2 interface and one DNA-binding patch are experimentally validated
- The claim that nucleotide promiscuity "may be advantageous in specific contexts" is speculative without testing the complete R1-R2-R3 complex or DNA-stimulated conditions
- The statement that LlaI.R1 shares structural homology with eukaryotic genome maintenance proteins is supported by DALI scores, but the functional significance of this homology is not experimentally addressed