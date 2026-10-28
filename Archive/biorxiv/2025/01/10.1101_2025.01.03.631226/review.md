## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2025-01-03, DOI 10.1101/2025.01.03.631226)
- **Assessment boundary** Scientific content, structural claims, methodological soundness, and interpretation as presented in the provided text. No external validation performed.
- **Shared manuscript claim summary** The authors report 8 cryo-EM structures of SPβ integrase (SprA) DNA complexes, with and without its cognate RDF (SprB), covering integrative and excisive recombination pathways. They propose that directionality is controlled by CC-CC interactions that stabilize synaptic complexes and handcuff product dimers, and that the RDF redirects the CC pivot point to favor a distinct excisive synaptic complex, thereby preventing back reactions.
- **Visible evidence base** Cryo-EM structures (3.15–7.18 Å), SEC data, in vivo promoter inversion assays, AlphaFold2 models, prior biochemical data (cited).
- **Missing materials affecting confidence** Figures, supplementary figures, movies, EM maps, PDB/EMDB validation reports, detailed cryo-EM statistics table, and full experimental protocols for mutagenesis and assays were not provided in the submitted text. These are essential for independent verification.

## Reviewer
- **Overall assessment** This manuscript addresses a long-standing question in the field of site-specific recombination: how large serine integrases achieve unidirectional integration and excision. The structural dataset is substantial and represents a significant advance, providing the first complete LSI-DNA complexes and the first experimental views of LSI-RDF interactions. The proposed model, in which CC-CC handshaking and handcuffing, modulated by RDF-mediated hinge repositioning, controls directionality, is coherent and well-supported by the structural data presented. However, the manuscript's reliance on a single integrase system, the moderate resolution of several key maps, and the limited functional validation of the proposed mechanism leave important gaps. The claim that the RDF "dictates a very different synaptic complex" is intriguing but requires stronger biochemical support, particularly given the absence of quantitative binding or kinetic data. Overall, the work is of high interest to the recombination and genome engineering communities, but the case for a generalizable mechanism would be strengthened by additional experiments and clearer presentation of validation metrics.
- **Who would be interested in the results, and why** Researchers studying site-specific recombination mechanisms, phage biology, and serine recombinase evolution. Also, synthetic biologists and genome engineers using LSIs for targeted DNA insertion and excision, as the structural insights could inform rational design of improved integrases and RDF pairs.
- **Major strengths** 1) First complete structures of LSI-DNA complexes, filling a critical gap. 2) Capturing both pre- and post-rotation states for both pathways provides a dynamic view of the reaction. 3) The identification of a distinct RDF-stabilized excisive synaptic complex challenges and refines prior models. 4) The proposed "handcuffing" and "handshake" model is mechanistically appealing and testable. 5) The work integrates structural, biochemical, and functional data, providing a multi-layered argument.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Structural validation
  - **Claim pointer** The manuscript claims 8 structures at resolutions "extending to 3.15 Å" and uses these to draw mechanistic conclusions about conformational changes and CC-CC interactions.
  - **Evidence pointer** Results section, "Eight structures illuminate integrative and excisive recombination"; Methods, "Image processing" and "Model building, refinement and validation"; Extended Data Table 1 (referenced but not provided).
  - **Concern** The manuscript does not provide a cryo-EM data collection and refinement statistics table (e.g., gold-standard FSC, map-model CC, B-factor validation, per-residue model confidence). Several maps are at moderate resolution (6.9–7.2 Å), where secondary structure elements are visible but side-chain placement is unreliable. The authors state that "local resolution extended to 4.69 Å" for some maps, but it is unclear which regions achieve this and whether the mechanistic conclusions (e.g., specific side-chain interactions at the CC-CC interface, helix E bending) are drawn from these higher-resolution regions or from lower-resolution areas. Without this information, the structural basis of the proposed model cannot be fully assessed.
  - **Why it matters** The central claims of the paper rest on the interpretation of cryo-EM maps. If the key interfaces and conformational states are not resolved at sufficient resolution, the proposed mechanism may be over-interpreted. The lack of validation metrics prevents readers from judging the reliability of the models.
  - **Resolution test** Provide a complete statistics table (per map) including resolution (gold-standard FSC), map sharpening B-factor, model-to-map CC (masked/unmasked), and model validation (MolProbity, Ramachandran, rotamer outliers). For key interfaces (CC-CC, CC-RDF, helix E-DNA), show representative density with fitted models at a contour level that demonstrates side-chain placement confidence. If side-chain-level interpretation is not possible, explicitly state this and temper the mechanistic claims accordingly.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance / Functional validation
  - **Claim pointer** The manuscript states that the RDF "dictates a very different synaptic complex" and that this is "fundamentally different" from the integrative complex, and that this difference is key to unidirectional excision.
  - **Evidence pointer** Results, "The RDF dictates a different synaptic complex for excision"; Discussion, "Unidirectionality in both pathways is explained by the interplay..."; Figure 5 and S13 (referenced).
  - **Concern** The structural difference between the integrative and excisive synaptic complexes is presented as the key finding, but the functional evidence that this difference is causally responsible for directionality is limited. The mutational analysis (Figure 7) focuses on the RDF-CC interface and shows that disrupting it abolishes RDF function, but does not directly test whether the altered synaptic geometry is the cause. The authors do not provide quantitative measurements of synaptic complex stability, DNA cleavage rates, or product release for the different complexes. The claim that the RDF "redirects" the CC is based on static structures; dynamic or kinetic evidence is lacking.
  - **Why it matters** The manuscript proposes a mechanistic model for directionality. Without functional data linking the structural differences to reaction outcomes, the model remains correlative. The field would benefit from experiments that directly test whether the RDF-stabilized synaptic complex is required for excision and whether its geometry prevents integration.
  - **Resolution test** Perform kinetic or equilibrium binding assays (e.g., EMSA, SPR, or stopped-flow) comparing synaptic complex formation and stability for integrative vs. excisive complexes. Test whether mutations that alter the excisive synaptic geometry (e.g., at the CC-CC interface) specifically impair excision without affecting integration. If possible, use single-molecule FRET or similar approaches to monitor conformational changes during the reaction.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Originality / Generalizability
  - **Claim pointer** The manuscript states that "these insights provide a conceptual framework for engineering efficient and versatile genome editing tools" and implies that the mechanism is generalizable across LSIs.
  - **Evidence pointer** Discussion, "The work presented here provides a framework for engineering LSI-RDF pairs..."; also, comparisons to φC31 integrase (cited as reference 66).
  - **Concern** The study is based on a single integrase (SPβ) and its cognate RDF. While the authors note similarities and differences with φC31, they do not provide evidence that the proposed mechanism (CC-CC handshaking/handcuffing, RDF-mediated hinge repositioning) is conserved across the diverse LSI family. The 4 bp vs. 5 bp shift in DBD2 positioning between SPβ and φC31 suggests potential variability, but the functional consequences are not explored. The claim of a "conceptual framework" for engineering is broad and not supported by any engineering experiments in this manuscript.
  - **Why it matters** The significance of the work for the broader LSI field depends on whether the mechanism is general or specific to SPβ. If the mechanism is not conserved, the engineering implications are limited.
  - **Resolution test** Discuss the conservation of key structural features (CC length, hinge positions, RDF binding site) across LSI family members, using sequence alignments or available structures. If possible, perform a comparative structural or biochemical analysis with at least one additional LSI-RDF pair. Alternatively, temper the generalizability claims and focus on SPβ as a model system.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction, first paragraph
  - **Evidence pointer** Introduction, "Large serine integrases (LSIs; also called large serine recombinases)..."
  - **Issue** The introduction assumes familiarity with site-specific recombination terminology (e.g., "att sites," "synaptic complex," "central dinucleotides") without defining these terms for a broader readership. The distinction between "integrative" and "excisive" recombination is not clearly explained for non-experts.
  - **Required correction** Add a brief explanation of the biological context (phage integration/excision) and define key terms (attP, attB, attL, attR, synaptic complex) in plain language. Consider a schematic figure for the reaction pathways.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "In vivo integrase mediated inversion assay"
  - **Evidence pointer** Methods, "In vivo integrase mediated inversion assay"
  - **Issue** The assay description is somewhat unclear regarding the quantification of recombination. The text states that "plates were visualized" and that "the mean and standard deviation are shown for the elongated-hinge mutants," but it is not clear how the ratio of GFP to RFP colonies was quantified or how background recombination was controlled.
  - **Required correction** Clarify the quantification method (e.g., colony counting, fluorescence measurement) and describe how the percentage of recombination was calculated. State the number of biological replicates and how statistical significance was determined.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion, paragraph on φC31 comparison
  - **Evidence pointer** Discussion, "A recent preprint describes integrative-pathway structures of φC31 integrase..."
  - **Issue** The comparison to φC31 is brief and does not fully explore the implications of the observed differences (e.g., 4 bp vs. 5 bp shift, different CC-CC interfaces). The authors note "some architectural differences" but do not discuss whether these differences might reflect distinct regulatory mechanisms.
  - **Required correction** Expand the comparison to discuss the potential functional significance of the observed differences. If the differences are minor, state this explicitly. If they are significant, discuss what they might mean for the generalizability of the model.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Results, "The attL-bound product dimer" section
  - **Evidence pointer** Results, "The attL-bound product dimer: a 4bp shift between half sites allows CC-CC handcuffing"
  - **Issue** The description of the structural differences between attP- and attB-bound subunits is dense and may be difficult to follow without visual aids. The term "handcuffing" is used repeatedly but is not defined until later in the text.
  - **Required correction** Define "handcuffing" and "handshaking" early in the Results section. Consider adding a schematic diagram to illustrate the proposed CC-CC interactions and the 4 bp shift.
- **Technical failings that need to be addressed before the case is established** 1) Absence of cryo-EM validation statistics (R1-M1). 2) Lack of functional experiments directly linking the proposed structural differences to directionality (R1-M2). 3) Insufficient evidence for generalizability beyond SPβ (R1-M3). 4) Unclear quantification in the in vivo assay (R1-m2).
- **Assessment against Nature-style criteria**  
  *Originality*: High. The structures are novel and provide the first complete views of LSI-DNA complexes and LSI-RDF interactions. The proposed model for directionality control is a significant conceptual advance.  
  *Scientific importance*: High for the recombination field and for genome engineering. The mechanism proposed has clear implications for understanding and engineering LSI function. However, the importance would be enhanced by demonstrating generalizability.  
  *Interdisciplinary readership*: Moderate. The work will be of great interest to structural biologists, microbiologists, and synthetic biologists. The broader genome editing community may find the engineering implications relevant, but the dense structural detail may limit accessibility.  
  *Technical soundness*: Currently not fully assessable due to missing validation data. The experimental design is sound, but the resolution of several key maps and the lack of functional validation are concerns.  
  *Readability for nonspecialists*: The manuscript is well-written but assumes significant background knowledge. The abstract is clear, but the Results section is dense and would benefit from more accessible explanations and schematics.
- **Recommendation posture** Supportive if technical concerns are resolved. The structural data are valuable and the proposed model is compelling, but the manuscript requires additional validation data and functional experiments to fully establish the mechanistic claims. The authors should also address the generalizability of their findings.

## Risk / unsupported claims
- The claim that the RDF "dictates a very different synaptic complex" is supported by the structures but not by direct functional evidence that this difference is causal for directionality.
- The claim that "these insights provide a conceptual framework for engineering efficient and versatile genome editing tools" is not supported by any engineering experiments in this manuscript.
- The statement that "the sole exception is the Helix E, which interacts differently with cleaved vs. uncleaved DNA" is based on the presented structures but is not quantitatively validated (e.g., no interaction energy calculations or mutational analysis of the specific residues involved).
- The assertion that "the most important function of the RDF is to change the pivot point of the CC rather than simply to restrain how far it can extend" is inferred from the structures and the hinge-elongation experiments, but the experiments only show that hinge length affects function, not that the pivot point change is the primary mechanism.
- The generalizability of the 4 bp shift in DBD2 positioning to other LSIs is not established; the authors note a 5 bp shift was predicted for some LSIs and seen in φC31, but the functional significance of this difference is not explored.