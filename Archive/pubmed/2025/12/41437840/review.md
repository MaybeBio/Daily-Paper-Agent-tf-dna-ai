## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and interpretation presented in the manuscript
- **Shared manuscript claim summary** The authors present a structure-based model of the SPS amino acid sensing complex in Saccharomyces cerevisiae, integrating computational modeling (Phyre2, AlphaFold, AlphaFold 3) with previously published mutant phenotypes to propose that an inward-facing occluded conformation of Ssy1 is the signaling state, and that signal transduction involves phosphorylation-dependent displacement of Ptr3 from Ssy1 and subsequent Ssy5 activation.
- **Visible evidence base** Full text including Abstract, Introduction, Results and Discussion, and Data availability statement. Supplementary figures and tables are referenced but not provided.
- **Missing materials affecting confidence** Supplementary Figures 1-31 and Supplementary Tables 1-3 are referenced extensively but were not available for review. Experimental data supporting mutant phenotypes are cited from prior publications (Poulsen et al. 2005a, 2005b, 2006, 2008) but not shown. No experimental validation of the proposed models is presented.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive computational analysis of the SPS amino acid sensing complex, integrating structural modeling with a substantial body of previously published genetic and biochemical data. The authors propose a detailed mechanistic model for signal generation and transduction, centered on the concept that an inward-facing occluded conformation of Ssy1 is the signaling state. The work is ambitious and potentially valuable for the yeast signaling community, but it is entirely computational and the central claims rest on indirect inference from mutant phenotypes mapped onto homology models. The lack of experimental validation, combined with the absence of the supplementary materials from this review, limits the confidence with which the core conclusions can be accepted. The manuscript is well-written and logically structured, but the speculative nature of several key proposals needs to be more clearly delineated from established findings.

- **Who would be interested in the results, and why** Researchers studying nutrient sensing in yeast, particularly the SPS sensor pathway, will find this work directly relevant. The proposed model for Ssy1 conformational states and the role of the C-terminal latch offers testable hypotheses for experimentalists. The broader community interested in the evolution of transporters into receptors, and in the application of AlphaFold-based modeling to understand signaling mechanisms, may also find value. The analysis of phosphorylation motifs and PP2A interactions could interest researchers studying kinase-phosphatase signaling networks.

- **Major strengths**
  1. The manuscript integrates a large body of prior genetic and biochemical data into a coherent structural framework, which is a valuable synthesis.
  2. The use of multiple computational tools (Phyre2, AlphaFold, AlphaFold 3) and cross-validation with known transporter structures is methodologically sound.
  3. The authors are appropriately cautious in several places, explicitly labeling their model as provisional and suggesting experimental tests.
  4. The writing is clear and the logical flow from Ssy1 structure to Ptr3/Ssy5 interactions is easy to follow.
  5. The identification of specific interaction interfaces (e.g., BoxA-Ssy5, BoxD/E-Ptr3, LFA motif) provides concrete targets for future mutagenesis studies.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The central claim that an "inward-facing occluded" conformation of Ssy1 is the signaling state, and that the seven constitutively signaling mutations promote this conformation.
- **Evidence pointer** Results and discussion, sections "The signaling conformation of Ssy1", "Interpretation of hyper-responsive and constitutive SSY1 mutants"; Figures 1-3; Supplementary Figures 4-6
- **Concern** The conclusion that the signaling state is inward-facing occluded is inferred entirely from mapping seven gain-of-function mutations onto homology models. The authors argue that the positions of these mutations are consistent with promoting this specific conformation, but this is an indirect inference. Alternative explanations, such as the mutations affecting protein dynamics, stability, or interactions with Ptr3 in ways not captured by static models, are not rigorously excluded. The authors do consider an alternative occluded state but dismiss it based on the same indirect reasoning. Without experimental validation (e.g., conformational sensors, cross-linking, or cryo-EM), the central claim remains a hypothesis, not an established finding.
- **Why it matters** The entire mechanistic model presented in the paper rests on this identification of the signaling conformation. If the signaling state is different, then the subsequent proposals about latch release, Ptr3 displacement, and phosphorylation dynamics would need substantial revision.
- **Resolution test** Experimental validation is required. This could include: (1) introducing the constitutively activating mutations into a purified Ssy1 and assessing conformational changes via DEER spectroscopy or similar techniques; (2) cryo-EM structures of Ssy1 in the presence and absence of amino acid ligands; (3) in vivo FRET-based conformational reporters. Alternatively, the authors could strengthen their argument by performing molecular dynamics simulations to show that the mutations indeed stabilize the proposed inward-facing occluded state relative to other states.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The proposal that the C-terminal latch (residues 805-827) tethers the TM bundle in the outward-open state and that its release is a key step in signaling.
- **Evidence pointer** Results and discussion, section "Interaction of the intracellular loop IL2-3 with a C-terminal latch"; Figure 4; Supplementary Figures 28-30
- **Concern** The existence and functional role of the C-terminal latch is inferred primarily from the AlphaFold model of Ssy1 in the outward-open conformation. The authors note that AlphaFold 3 modeling of phosphorylated Ptr3 variants suggests a rotational displacement, but the confidence metrics for the full-length trimer model are low (ipTM = 0.46). The specific claim that the latch "offers a mechanism for signaling" is speculative. The comparison to dDAT and hSERT is interesting but those are transporters, not signaling receptors, and the functional relevance of their C-terminal latch to Ssy1 signaling is not established.
- **Why it matters** The latch mechanism is a novel and potentially important contribution of this paper. If it is not correctly identified, the proposed signaling mechanism would be incorrect. The low confidence of the full-length model undermines the reliability of this specific structural feature.
- **Resolution test** Targeted mutagenesis of the latch residues (e.g., D817, D819, R822, D826) followed by functional assays (Ssy1-dependent reporter gene expression) could test whether disrupting the latch constitutively activates signaling. Cross-linking mass spectrometry could provide experimental evidence for the latch-TM bundle interaction. Higher-confidence structural models, perhaps using cryo-EM, would be needed to confirm the latch position.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The prediction of specific interaction interfaces between Ssy1 and Ptr3 (BoxD/E) and Ssy1 and Ssy5 (BoxA) based on AlphaFold 3 models.
- **Evidence pointer** Results and discussion, sections "Interactions between blade 3 in Ptr3 and BoxD and BoxE in Ssy1", "Interaction between BoxA in Ssy1 and the catalytic domain of Ssy5"; Supplementary Figures 23-24
- **Concern** While the AlphaFold 3 models for the binary complexes have reasonable confidence scores (ipTM 0.79-0.81), these are still computational predictions. The authors do not acknowledge the known limitations of AlphaFold in predicting the effects of mutations on protein-protein interactions, nor do they discuss the possibility that the true interfaces may be different. The claim that specific residues "may form" interactions is appropriately hedged, but the subsequent mechanistic conclusions (e.g., that T435K and Q439R mutations disrupt the Ssy1-Ptr3 interface) are presented with more certainty than the evidence supports.
- **Why it matters** These predicted interfaces are used to explain the phenotypes of existing mutants and to propose a mechanism for signal transduction. If the interfaces are incorrect, the mechanistic conclusions would be invalid.
- **Resolution test** Experimental validation via co-immunoprecipitation of wild-type and mutant proteins, hydrogen-deuterium exchange mass spectrometry, or cross-linking mass spectrometry. Mutagenesis of the predicted interface residues followed by functional assays would also be informative.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The claim that the identified Yck phosphorylation motifs and PP2A binding motifs in Ptr3 and Ssy5 provide a basis for understanding the antagonistic regulation of signaling.
- **Evidence pointer** Results and discussion, sections "Phosphorylation of Ptr3 by protein kinase Yck", "Dephosphorylation of Ptr3 by protein phosphatase 2A", "Phosphorylation and dephosphorylation of Ssy5"; Supplementary Figures 13, 16-18
- **Concern** The analysis identifies potential phosphorylation sites and PP2A binding motifs based on sequence conservation and structural modeling. However, no experimental evidence is provided that these sites are actually phosphorylated in vivo, that Yck phosphorylates them, or that PP2A dephosphorylates them. The claim that these motifs "constitute a basis for predicting novel aspects of phosphorylation" is modest, but the discussion goes further to propose a specific regulatory mechanism without experimental support.
- **Why it matters** The proposed antagonism between Yck-mediated phosphorylation and PP2A-mediated dephosphorylation is a key part of the signaling model. Without experimental validation, this remains speculative.
- **Resolution test** Phosphoproteomic analysis of Ptr3 and Ssy5 in wild-type and mutant strains, in vitro kinase assays with purified Yck, and phosphatase assays with purified PP2A. Site-directed mutagenesis of the predicted phosphorylation sites followed by functional assays would directly test their role in signaling.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Results and discussion, section "The signaling conformation of Ssy1"
- **Issue** The terms "inward-facing occluded" and "occluded" are used to describe distinct states, but the distinction is not always clear. The authors use "occluded" for states C and E and "inward-facing occluded" for states D and F, but the structural difference between these is not explicitly defined.
- **Required correction** Provide a clear structural definition of each state, perhaps with a schematic figure, to avoid confusion.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion of alternative models
- **Evidence pointer** Results and discussion, section "The signaling conformation of Ssy1"
- **Issue** The authors dismiss the alternative that an occluded state (C or E) is signaling, but do not discuss other possible signaling mechanisms, such as ligand-induced dimerization of Ssy1 or conformational changes that do not involve a simple outward-to-inward transition.
- **Required correction** Briefly discuss alternative models and explain why they are less consistent with the available data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Model confidence
- **Evidence pointer** Results and discussion, section "Interactions in the SPSsensor complex"
- **Issue** The authors report confidence metrics (ipTM, pTM) for the AlphaFold 3 models but do not provide a systematic comparison of the confidence across different models or a discussion of what these metrics mean for the reliability of the specific interaction interfaces.
- **Required correction** Add a supplementary table summarizing the confidence metrics for all AlphaFold 3 models and briefly explain the interpretation of these metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure accessibility
- **Evidence pointer** Figures 1-8
- **Issue** The figures are dense and may be difficult for non-specialists to interpret. The main text refers to specific residues and interactions, but the figures do not always clearly highlight these.
- **Required correction** Consider simplifying figures or adding callout boxes to highlight key residues and interactions discussed in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The authors state that all data are present in the article and supplementary materials, but the supplementary materials were not provided for review. This makes it impossible to verify the alignments, models, and additional analyses referenced in the text.
- **Required correction** Ensure that all supplementary materials are made available to reviewers and readers.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract and Introduction
- **Issue** The term "hyper-responsive" is used to describe mutant phenotypes, but the quantitative definition (e.g., fold-change in EC50) is not provided in the main text.
- **Required correction** Define "hyper-responsive" and "constitutive" with reference to the specific assays and thresholds used in the cited prior work.

## Risk / unsupported claims
- The central claim that the signaling conformation of Ssy1 is "inward-facing occluded" is unsupported by direct experimental evidence and relies entirely on indirect inference from mutant phenotypes mapped onto homology models.
- The proposed C-terminal latch mechanism is speculative and based on a low-confidence full-length trimer model.
- The predicted interaction interfaces between Ssy1-Ptr3 and Ssy1-Ssy5 are computational predictions that have not been experimentally validated.
- The proposed phosphorylation and dephosphorylation sites in Ptr3 and Ssy5 are predicted based on sequence motifs and structural modeling, but no experimental evidence is provided for their functional relevance.
- The claim that the AlphaFold 3 model of the SPS complex is the "currently best working model" is subjective and not supported by comparison with other potential models or experimental data.
- The statement that "the results constitute a basis for predicting novel aspects of phosphorylation in the signaling mechanism" is vague and not falsifiable as stated.