## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, methods, and supplemental file descriptions
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided text; no external data or figures were available for independent verification
- **Shared manuscript claim summary** The authors propose a mechanistic model for DNA loading by the bacterial SMC complex MukBEF, based on cryo-EM structures of an open-gate state and a DNA capture state, and identify the bacteriophage T7 protein gp5.9 as a specific inhibitor that blocks DNA loading by mimicking DNA at the MukE binding site
- **Visible evidence base** Cryo-EM reconstructions (open-gate state at 3.9 Å, DNA capture state at 7.8 Å, dimer at 9.1 Å), biochemical DNA entrapment assays, pull-down experiments, TMT-MS proteomics, bacterial genetics, and phylogenetic analysis
- **Missing materials affecting confidence** Figures, tables, and supplemental data files (including Movies, Data S1-S5) were not provided; exact numerical values for entrapment assay quantifications and statistical details are absent; structural validation metrics (e.g., FSC curves, model-to-map fit) are referenced but not shown

## Reviewer
- **Overall assessment** This manuscript presents a compelling and largely coherent structural and biochemical analysis of MukBEF DNA loading, with the discovery of a viral inhibitor adding notable interest. The cryo-EM structures are plausibly interpreted, and the proposed "release and rotate" mechanism is conceptually attractive. However, the central claim that the DNA capture state is an obligatory intermediate in loading rests on indirect evidence, and the resolution of the DNA-bound state limits the strength of molecular-level conclusions. The gp5.9 story is well supported by the data described, though the physiological relevance remains speculative. Overall, the work is of high quality and likely to interest the SMC and chromosome biology communities, but several technical and interpretive concerns must be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers studying SMC complexes, chromosome organization, DNA loop extrusion, and bacterial chromosome segregation will find the structural insights directly relevant. The identification of a phage-encoded inhibitor of MukBEF will also appeal to virologists and those interested in host-pathogen arms races. The proposed loading mechanism, if validated, could inform studies of eukaryotic SMC complexes such as cohesin and condensin.
- **Major strengths** 1) The cryo-EM structures reveal a novel open-gate state with clear conformational changes, providing the first direct visualization of gate opening in a bacterial SMC complex. 2) The discovery of gp5.9 as a MukBEF inhibitor is unexpected and opens new avenues for studying SMC regulation. 3) The biochemical entrapment assay is well-designed and rigorously controlled, with ATP dependence and mutant controls. 4) The proposed unidirectional loading mechanism integrates structural, biochemical, and genetic data into a coherent model. 5) The phylogenetic analysis contextualizes MukBEF within the broader Wadjet family.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (resolution of DNA capture state), R1-M2 (evidence for capture state as loading intermediate), R1-M3 (gp5.9 mechanism of action), R1-M4 (specificity of gp5.9 inhibition)
- **Assessment against Nature-style criteria** Originality: High. The open-gate state and the viral inhibitor are novel findings that advance the field. Scientific importance: High for the SMC field, with potential broader relevance to genome organization. Interdisciplinary readership: Moderate. The work will appeal primarily to structural biologists and chromosome dynamics researchers; the virology angle adds breadth. Technical soundness: Generally strong, but the resolution of key structures and the indirect evidence for the loading pathway require attention. Readability for nonspecialists: The main text is clearly written, but the methods section is dense and assumes significant prior knowledge. The authors do a good job of framing the significance for a broad audience.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the resolution of the DNA capture state and the direct evidence for its role in loading.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the DNA capture state is a distinct structural state with DNA positioned at the open neck gate, and use this to propose a loading mechanism.
- **Evidence pointer** Results section, "DNA capture at the open neck gate"; Figure 2D-E; PDB: 9GM8, 9GMA
- **Concern** The DNA capture state is reported at 7.8 Å nominal resolution (monomer) and 9.1 Å (dimer). At these resolutions, the registration of the DNA sequence, the precise protein-DNA contacts, and the conformational details of the protein are highly uncertain. The authors model ideal B-form DNA into the density, which is a reasonable approach, but the claim that the DNA is "positioned" at a specific site with specific contacts is not strongly supported. The distinction between this state and the open-gate state (3.9 Å) is based on the presence of DNA density, but the low resolution of the DNA-bound map makes it difficult to exclude alternative interpretations, such as non-specific DNA binding or a mixture of states.
- **Why it matters** The DNA capture state is the cornerstone of the proposed loading mechanism. If the structural interpretation is not robust, the entire model is weakened. The resolution is insufficient to define the molecular interactions that are claimed to be important for capture and subsequent ingestion.
- **Resolution test** The authors should provide additional validation of the DNA capture state, such as: 1) local resolution estimates for the DNA-binding region; 2) a comparison of the DNA density with simulated maps from the modeled B-form DNA at the reported resolution; 3) cross-validation with a DNA sequence that is known to bind more weakly or strongly, if such data exist; 4) a discussion of the limitations of modeling at this resolution and how the conclusions are affected.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors propose that the DNA capture state is an intermediate in the loading pathway, stating "we reason that entrapment may be achieved by ingestion through the gate" and that gp5.9 inhibits loading by blocking this capture step.
- **Evidence pointer** Discussion, "The DNA capture state as a first step of loading"; Figure 5A-C
- **Concern** The evidence that the capture state is on-pathway for loading is circumstantial. The authors show that gp5.9 inhibits loading and binds to the MukE DNA-binding site, which is also used in the capture state. However, this is a correlation, not a demonstration of causality. The capture state could represent an off-pathway or dead-end complex. The authors do not provide time-resolved experiments, mutational analysis of the capture interface, or single-molecule data to show that the capture state is kinetically competent to proceed to entrapment. The proposed "release and rotate" mechanism is speculative and not directly tested.
- **Why it matters** The central claim of the paper is a mechanistic model for loading. Without direct evidence that the capture state is an intermediate, the model remains a hypothesis. The distinction between a loading intermediate and a regulatory or off-pathway state is critical for understanding MukBEF function.
- **Resolution test** The authors should: 1) perform mutational analysis of residues in the MukE/MukF DNA-binding interface and test the effect on loading in the entrapment assay; 2) if possible, use time-resolved or single-molecule approaches to observe the transition from capture to entrapment; 3) test whether the capture state can be trapped with a non-hydrolyzable ATP analog and then chased into the entrapped state upon ATP addition; 4) provide a more detailed kinetic model with rate constants, if data are available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that gp5.9 binds to the MukE DNA-binding cleft and inhibits DNA loading by blocking the capture step.
- **Evidence pointer** Results, "gp5.9 targets the MukE DNA-binding cleft and inhibits DNA loading"; Figure 4A-B; PDB: 9GMD
- **Concern** The cryo-EM structure of the gp5.9/MukEF complex is reported at 4.1 Å (and 4.0 Å for the focused map). While this is better than the DNA capture state, it is still at a resolution where side-chain assignments can be ambiguous. The claim that gp5.9 is a DNA mimic is based on the overall shape and the positioning of acidic residues, but the authors do not provide a quantitative comparison of the electrostatic surfaces or a demonstration that the gp5.9 binding surface is truly complementary to the DNA-binding site. The functional data showing inhibition of loading are strong, but the structural basis for specificity (E. coli vs. P. thracensis) is not fully explained.
- **Why it matters** The gp5.9 story is a key novelty of the paper. If the structural basis of inhibition is not rigorously established, the claim of DNA mimicry is weakened. Understanding the specificity is important for assessing the physiological relevance.
- **Resolution test** The authors should: 1) provide a more detailed analysis of the gp5.9-MukE interface, including a figure showing the electrostatic potential of both surfaces; 2) perform mutagenesis of gp5.9 residues predicted to be important for binding and test the effect on inhibition; 3) if possible, compare the binding affinity of gp5.9 for MukE with the affinity of DNA for MukE; 4) discuss the structural basis for the species specificity, perhaps with a sequence alignment of MukE from E. coli and P. thracensis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim support
- **Claim pointer** The authors state that "loading was stimulated both by P. thracensis Topo IV and E. coli Topo I, but not by DNA gyrase" and conclude that DNA relaxation facilitates MukBEF loading.
- **Evidence pointer** Results, "DNA relaxation facilitates MukBEF loading"; Figure 1G-H
- **Concern** The conclusion that DNA relaxation facilitates loading is based on the effect of topoisomerases, but the interpretation is complicated. Topo IV and Topo I both relax DNA, but they have different mechanisms and may have other effects. The authors do not directly measure the supercoiling density of the DNA under their assay conditions. The effect could be due to changes in DNA topology, but it could also be due to direct protein-protein interactions between the topoisomerases and MukBEF. The authors do not test whether the topoisomerases are incorporated into the final complex or whether their catalytic activity is required.
- **Why it matters** The claim that DNA topology influences loading is interesting and could have implications for the mechanism. However, if the effect is due to non-specific protein interactions, the conclusion would be incorrect. This is a secondary point, but it is presented as a distinct finding.
- **Resolution test** The authors should: 1) measure the supercoiling density of the DNA before and after the reaction; 2) test topoisomerase mutants that bind but do not relax DNA; 3) test whether the topoisomerases are present in the final protein-DNA complex; 4) consider alternative explanations, such as the topoisomerases acting as a "crowding agent" or altering the effective DNA concentration.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "we discover that the gp5.9 protein of bacteriophage T7 blocks this capture site by DNA mimicry"
- **Issue** The abstract states that gp5.9 blocks the capture site "by DNA mimicry," but the structural evidence for this is presented later in the paper. The abstract could be more precise by stating that gp5.9 binds to the MukE DNA-binding site and inhibits loading, with the structural basis described in the results.
- **Required correction** Revise the abstract to say "blocks the DNA capture site" or "binds to the MukE DNA-binding site," and reserve the term "DNA mimicry" for the results and discussion sections where the evidence is presented.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "DNA relaxation facilitates MukBEF loading"
- **Evidence pointer** Figure 1G-H
- **Issue** The figure legends are not provided, so it is unclear what the error bars represent, how many replicates were performed, and what statistical tests were used. The text mentions "a ladder of bands" but does not provide quantification.
- **Required correction** Provide figure legends with full experimental details, including the number of replicates, error bar definitions, and statistical analysis. Quantify the entrapment efficiency (e.g., fraction of DNA with at least one bound complex) and report the mean and standard deviation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "DNA relaxation facilitates MukBEF loading"
- **Evidence pointer** Figure 1H
- **Issue** The text states that "both nicked and relaxed substrates showed a strong increase in loading efficiency compared to negatively supercoiled DNA." It is unclear whether the nicked and relaxed substrates are equivalent in terms of torsional strain. A nicked circle is relaxed but has a single-strand break, which could affect MukBEF binding.
- **Required correction** Clarify the difference between nicked and relaxed substrates and discuss whether the single-strand break in the nicked substrate could influence the results. If possible, include a control with a ligated, relaxed circle.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Evidence pointer** Methods, "Cysteine mutant P. thracensis MukBEF dimers were mixed at 1 μM with 6 ng/μL of negatively supercoiled pFB527"
- **Issue** The molar ratio of MukBEF to DNA is not stated. This is important for interpreting the entrapment assay, as the number of complexes per DNA molecule will affect the ladder pattern.
- **Required correction** Calculate and state the molar ratio of MukBEF dimers to plasmid DNA molecules in the assay. Discuss how this ratio affects the interpretation of the results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "gp5.9 targets the MukE DNA-binding cleft and inhibits DNA loading"
- **Evidence pointer** Figure 4C-D
- **Issue** The text mentions that gp5.9 inhibits loading of E. coli MukBEF but not P. thracensis MukBEF. The structural basis for this specificity is not fully explained. A sequence alignment of the MukE DNA-binding site from both species would be helpful.
- **Required correction** Add a supplementary figure with a sequence alignment of MukE from E. coli and P. thracensis, highlighting the residues that interact with gp5.9 and the DNA. Discuss the differences that explain the species specificity.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion, "Inhibition of SMC complexes by pathogens"
- **Evidence pointer** Discussion section
- **Issue** The discussion of pathogen-encoded SMC inhibitors is interesting but somewhat speculative. The authors mention HBV X protein and HIV-1 Vpr, but do not discuss whether these proteins act by a similar mechanism to gp5.9 (i.e., DNA mimicry). A brief comparison would strengthen the discussion.
- **Required correction** Add a sentence or two comparing the mechanism of gp5.9 with that of HBV X and HIV-1 Vpr, noting whether they also target DNA-binding sites or use different strategies.

## Risk / unsupported claims
- The claim that the DNA capture state is an obligatory intermediate in the loading pathway is not directly supported by the data; it is a reasonable hypothesis but is presented with more certainty than the evidence warrants.
- The claim that gp5.9 is a "DNA mimic" is supported by the structural and functional data, but the term implies a level of mechanistic detail that is not fully established. The authors show that gp5.9 binds to the DNA-binding site, but they do not demonstrate that it mimics the specific interactions of DNA with MukE.
- The statement that "loading is more efficient on relaxed DNA" is based on indirect evidence with topoisomerases and is not fully controlled for potential protein-protein interactions.
- The physiological relevance of gp5.9-mediated MukBEF inhibition for bacteriophage T7 infection is speculative; the authors note that gp5.9 is not essential for T7 propagation, and the conditions under which this inhibition matters are unknown.
- The proposed "release and rotate" mechanism for DNA ingestion is a model that is not directly tested; the authors should clearly label it as a hypothesis.