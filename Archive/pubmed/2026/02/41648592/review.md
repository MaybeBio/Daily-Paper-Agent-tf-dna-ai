## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors investigate the dimerization mechanism of the S. cerevisiae Spo11 core complex (Spo11, Ski8, Rec102, Rec104). They report that the complex dimerizes transiently on DNA, forming unstable complexes with duplex and branched substrates. Using AlphaFold modeling, they identify mutations that reduce dimerization in vitro, yet find that DSB formation in vivo is resilient to these mutations. They also identify a key DNA-binding function for Rec102 and a trans interaction between Rec102 and Ski8 that contributes to dimerization. A forward genetic screen identified a Spo11-A236V mutation that abolishes DSB formation via active site occlusion across the dimer interface.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Materials and Methods (partial), figure legends referenced but figures not provided
- **Missing materials affecting confidence** Figures and supplementary figures not provided; numerical data (KD values, quantification details) not fully described; AlphaFold model details not shown; full genetic screen results not provided

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in meiosis research: how the Spo11 core complex assembles into a catalytically competent dimer. The work combines biochemical, structural modeling, and in vivo approaches to provide new insights into Spo11 dimerization and the roles of accessory subunits. The finding that the dimer interface is highly resilient to mutagenesis in vivo, despite clear in vitro effects, is interesting and suggests additional stabilizing factors. The identification of Rec102 as a critical DNA-binding component and the trans Rec102-Ski8 interaction are valuable contributions. However, the manuscript has several technical and presentational issues that need to be addressed. The evidence for transient dimerization relies heavily on gel shift assays with indirect interpretation; the in vivo resilience data are somewhat paradoxical and not fully resolved; and the mechanistic model proposed would benefit from more direct structural or biophysical validation. The manuscript is well-written and will interest the meiosis and DNA repair communities, but the current evidence does not fully establish all claims.
- **Who would be interested in the results, and why** Researchers studying meiotic recombination, Spo11 biology, topoisomerase mechanisms, and the assembly of multiprotein-DNA complexes. The work also has relevance for understanding how enzymes that require dimerization for catalysis are regulated to prevent inappropriate activity.
- **Major strengths** 1. The study addresses a fundamental and unresolved question in meiosis: how Spo11 dimerizes to form a catalytically active complex. 2. The combination of AlphaFold modeling, in vitro biochemistry, and in vivo genetics is powerful and appropriate. 3. The identification of Rec102 as a key DNA-binding subunit and the trans Rec102-Ski8 interaction are novel and mechanistically informative. 4. The forward genetic screen provides an unbiased approach to identify functionally important residues. 5. The manuscript is clearly written and the logic is generally easy to follow.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** **Originality**: The work is original in its focus on the dimerization mechanism of the Spo11 core complex, which has not been systematically dissected before. The finding that the dimer interface is resilient to mutagenesis in vivo is novel and somewhat counterintuitive. **Scientific importance**: The question of how Spo11 is activated to form DSBs is central to meiosis and genome stability. The results provide new mechanistic insights and will likely influence future studies. **Interdisciplinary readership**: The work will primarily interest meiosis and DNA repair researchers, but the general principles of enzyme dimerization control may appeal to a broader biochemistry audience. **Technical soundness**: The biochemical and genetic approaches are generally sound, but several concerns (see above) need to be addressed. The reliance on gel shift assays for dimerization assessment and the lack of direct structural validation of the AlphaFold model are notable limitations. **Readability for nonspecialists**: The manuscript is well-written and accessible, with clear figures (not provided) and logical flow. The Introduction and Discussion provide sufficient context for readers outside the immediate field.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for transient dimerization
- **Claim pointer** "We show that the Spo11 complex dimerizes transiently on DNA, forming unstable dimeric complexes with duplex and branched DNA substrates."
- **Evidence pointer** Results section, Figure 2
- **Concern** The claim of transient dimerization is based primarily on gel shift assays showing two complexes (Complex 1 and Complex 2) and the effects of competitor DNA on complex distribution. The interpretation that Complex 2 contains two core complexes and that its instability reflects transient dimerization is plausible but not directly demonstrated. The mixing experiment with heavy and light tagged proteins (Figure 2C) is clever, but the absence of the expected 1:2:1 ratio of heavy-heavy, heavy-light, light-light complexes is interpreted as subunit exchange during electrophoresis. This is an indirect inference. The authors do not provide direct biophysical evidence (e.g., sedimentation velocity, single-molecule imaging, or crosslinking) for the stoichiometry of Complex 2 or the dynamics of dimerization.
- **Why it matters** The central claim of the paper is that Spo11 dimerizes transiently on DNA. If this is not rigorously established, the subsequent interpretation of the mutagenesis data and the proposed model are weakened.
- **Resolution test** Provide direct evidence for the stoichiometry of Complex 2 (e.g., using fluorescence correlation spectroscopy, analytical ultracentrifugation, or crosslinking followed by SDS-PAGE). Alternatively, perform a more rigorous kinetic analysis of complex formation and dissociation using stopped-flow or surface plasmon resonance. If subunit exchange during electrophoresis is invoked, provide a control experiment where the exchange is prevented (e.g., by crosslinking the complex before electrophoresis).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo relevance of in vitro dimerization mutants
- **Claim pointer** "Surprisingly, DSB formation is resilient to mutagenesis of the Spo11 dimer interface, implying that additional factors promote dimerization in vivo."
- **Evidence pointer** Results section, Figures 3, 4
- **Concern** The authors show that mutations that reduce dimerization in vitro (e.g., S136A/V138A/E139A) have only modest effects on DSB formation in vivo. This is interpreted as evidence for additional stabilizing factors in vivo. However, the in vivo assays used (spore viability, Southern blotting for DSBs) are relatively insensitive and may not detect subtle changes in DSB levels or distribution. The authors do show reduced and redistributed DSBs for the SVE mutant, but the magnitude of the effect is not quantified. Moreover, the possibility that the mutations affect other aspects of Spo11 function (e.g., recruitment to chromatin, interaction with other proteins) is not excluded.
- **Why it matters** The conclusion that the dimer interface is resilient to mutagenesis in vivo is a key finding of the paper. If the in vivo assays are not sensitive enough, this conclusion may be overstated.
- **Resolution test** Provide quantitative measurements of DSB levels (e.g., by deep sequencing of Spo11 oligos or by more sensitive Southern blotting with phosphorimaging quantification) for the dimerization mutants. Also, test whether the SVE mutant affects Spo11 recruitment to chromatin or interaction with known partners (e.g., Rec114, Mre11) to rule out alternative explanations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** AlphaFold model validation
- **Claim pointer** "Guided by AlphaFold modeling of a pre-cleavage complex, we identified mutations that reduce dimerization."
- **Evidence pointer** Results section, Figure 1, Supplementary Figures 1-6
- **Concern** The AlphaFold model is used to guide the mutagenesis, but the model itself is not experimentally validated. The authors compare predicted and experimental interface residues (Supplementary Figures 3-6), but the experimental data come from the cryo-EM structure of the post-cleavage complex, not the pre-cleavage complex. The pre-cleavage model is therefore untested. The authors acknowledge that the active sites are not poised for catalysis in the model, which raises questions about its accuracy.
- **Why it matters** The mutagenesis strategy relies on the accuracy of the AlphaFold model. If the model is incorrect, the interpretation of the mutant phenotypes may be flawed.
- **Resolution test** Validate the pre-cleavage model using an orthogonal approach, such as hydrogen-deuterium exchange mass spectrometry, crosslinking mass spectrometry, or small-angle X-ray scattering. Alternatively, test the model by making mutations in residues predicted to be at the interface and showing that they specifically affect dimerization without affecting other functions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Rec102 DNA-binding function
- **Claim pointer** "Rec102 exerts a key DNA-binding function, essential for catalysis"
- **Evidence pointer** Results section, Figures 6, 7
- **Concern** The authors show that Rec102 mutations (R243E/R244E/R245E) reduce DNA binding by >100-fold and abolish DSB formation. However, the DNA-binding assays are performed with the core complex, not with Rec102 alone. It is therefore not clear whether the reduced DNA binding is due to a direct effect of the mutations on Rec102-DNA interactions or an indirect effect on complex stability or conformation. The authors do not show that Rec102 alone binds DNA, nor do they map the DNA-binding surface of Rec102 directly.
- **Why it matters** The claim that Rec102 is a key DNA-binding component is important for understanding the mechanism of Spo11 complex assembly. If the effect is indirect, the conclusion may be incorrect.
- **Resolution test** Perform DNA-binding assays with Rec102 alone (or with the Rec102-Rec104 subcomplex) to demonstrate direct DNA binding. Use a more direct method, such as fluorescence anisotropy or surface plasmon resonance, to measure the affinity of Rec102 for DNA. Also, test whether the RRR mutation affects the interaction between Rec102 and other complex components.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Results section, Figure 2
- **Issue** The gel shift assays show two complexes, but the quantification of the fraction of each complex as a function of protein concentration is not shown. The KD values are mentioned in the text but not presented in a figure or table.
- **Required correction** Provide a quantification of the gel shift data, including a binding curve and the derived KD values, either in the main figures or in a supplementary figure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Figures 3, 4, 5, 6, 7, 8
- **Evidence pointer** Results section, Figures 3-8
- **Issue** The manuscript does not report statistical tests for the in vivo phenotypes (spore viability, DSB levels). It is unclear whether the differences between wild-type and mutants are statistically significant.
- **Required correction** Add statistical analysis (e.g., t-tests or ANOVA) for the quantitative in vivo data, and report the number of biological replicates.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and Methods, "Pulldown assay"
- **Evidence pointer** Materials and Methods section
- **Issue** The pulldown assay description is brief. The quantification method (ImageJ) is mentioned, but the normalization procedure is not fully described. It is unclear how the "30-40% reduction" in interaction was calculated.
- **Required correction** Provide a more detailed description of the pulldown quantification, including the exact normalization steps and the number of replicates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, "Does the Spo11 core complex capture two duplexes?"
- **Evidence pointer** Discussion section
- **Concern** The discussion of whether the complex captures two duplexes is speculative. The authors acknowledge that the dimensions of the arms in their substrate are insufficient to accommodate a dimer, but they do not provide a clear model for how the complex binds the junction.
- **Required correction** Clarify the model for junction binding, or explicitly state that the mechanism remains unresolved.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript does not discuss the recent cryo-EM structure of the Spo11 core complex (Yu et al. 2024) in sufficient detail. The authors mention it but do not compare their findings to the structural data in a systematic way.
- **Required correction** Add a more detailed comparison between the AlphaFold model and the cryo-EM structure, highlighting similarities and differences.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Nomenclature
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The term "core complex" is used to refer to the Spo11-Ski8-Rec102-Rec104 complex, but this is not standard nomenclature. The authors should define the term clearly at first use.
- **Required correction** Define "core complex" at first use and consider using a more standard term, such as "Spo11 complex" or "Spo11 holoenzyme."

## Risk / unsupported claims
- The claim that the Spo11 core complex "dimerizes transiently on DNA" is not fully supported by the provided evidence, as the gel shift assays do not directly demonstrate the stoichiometry or dynamics of the proposed dimer.
- The claim that "DSB formation is resilient to mutagenesis of the Spo11 dimer interface" is based on in vivo assays that may lack sensitivity; the magnitude of the effects is not quantified.
- The claim that "Rec102 exerts a key DNA-binding function, essential for catalysis" is supported by the mutagenesis data, but the direct DNA-binding activity of Rec102 is not demonstrated.
- The AlphaFold model of the pre-cleavage complex is not experimentally validated, and the authors acknowledge that the active sites are not poised for catalysis, which limits the confidence in the model.
- The functional significance of the junction-binding activity is speculative and not directly tested.
- The claim that the Rec102-Ski8 interaction in trans facilitates dimer assembly is supported by pulldown and mutagenesis data, but the in vivo relevance is not fully established.