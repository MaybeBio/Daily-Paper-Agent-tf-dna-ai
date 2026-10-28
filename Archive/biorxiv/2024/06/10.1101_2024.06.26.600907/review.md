## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials and Methods, Results, Discussion, Author Contributions, Funding, Acknowledgments)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. Figures and supplementary materials are referenced but not directly examined.
- **Shared manuscript claim summary** The manuscript reports a functional dissection of the C. elegans LEM-3/ANKLE1 nuclease, showing that (i) LEM-3(241-704) cleaves a broad range of branched DNA substrates in vitro, (ii) the catalytic mechanism is conserved with bacterial GIY-YIG nucleases based on AlphaFold modeling, (iii) LEM-3 may form homodimers on Holliday junctions, (iv) both the LEM-like and GIY-YIG domains are required for DNA binding, nuclease activity, and in vivo function, and (v) preventing nuclear access of LEM-3 is important to avoid toxicity.
- **Visible evidence base** Results sections describing in vitro nuclease assays, EMSA binding studies, AlphaFold structural predictions, in vivo IR sensitivity assays, fluorescence microscopy localization studies, and Western blot analyses. Figures S1-S10 and Tables S1-S4 are referenced.
- **Missing materials affecting confidence** Figures and supplementary data are not provided for direct inspection. Statistical details (exact p-values, sample sizes, replicates) are not fully described in the text. The manuscript is a preprint and has not undergone peer review.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive structure-function analysis of the conserved LEM-3/ANKLE1 nuclease, combining in vitro biochemistry, structural modeling, and in vivo genetics in C. elegans. The work addresses an important question in genome stability: how persistent DNA bridges are processed at the midbody during cytokinesis. The authors provide evidence for broad substrate specificity, a conserved catalytic mechanism, and a role for the LEM-like domain in DNA binding. The finding that a GIY-YIG-only derivative is toxic when it gains nuclear access is particularly interesting and has potential implications for understanding ANKLE1 regulation in human cells. However, several concerns regarding experimental rigor, quantification, and the strength of certain conclusions need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers studying DNA repair, genome stability, chromosome segregation, and cytokinesis would find this work relevant. The evolutionary conservation of LEM-3/ANKLE1 across animals and its connection to human disease (ANKLE1 variants are associated with cancer susceptibility) make this study of interest to a broader cell biology and cancer biology audience. The structural modeling approach may also appeal to computational biologists studying nuclease mechanisms.

- **Major strengths** (1) The combination of in vitro biochemistry, structural prediction, and in vivo genetics provides a multi-pronged approach to dissecting LEM-3 function. (2) The identification of the LEM-like domain as a DNA-binding module is a novel contribution. (3) The observation that a GIY-YIG-only derivative is toxic when nuclear is an important finding with potential translational relevance. (4) The use of atomic mutants (Y530F, Y556F) is elegant and provides mechanistic insight. (5) The study addresses a biologically significant question with clear relevance to genome stability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental rigor / quantification
- **Claim pointer** The authors claim that LEM-3(241-704) cleaves a wide range of branched DNA substrates with differential activity, and that the Y530F mutation largely abolishes this activity.
- **Evidence pointer** Results section "Purification of LEM-3(241-704) and genetic characterization", Figure 1A-C, Figure 3A-B
- **Concern** The manuscript describes nuclease activity qualitatively but does not provide quantitative measurements of cleavage efficiency, kinetic parameters, or statistical comparisons between substrates and mutants. The text states that "LEM-3(241-704) displayed the highest activity against 5'-flaps, 3'-flaps, and nicked HJs" and that activity towards RFs and HJs was "~2-fold reduced," but no error bars, replicate numbers, or statistical tests are reported. Similarly, the claim that Y530F "largely" abolishes activity is not quantified.
- **Why it matters** Without quantitative data and statistical analysis, it is difficult to assess the robustness of the substrate specificity conclusions and the extent of catalytic impairment in mutants. This is central to the paper's main claims about LEM-3 function.
- **Resolution test** Provide quantification of cleavage products (e.g., percent substrate converted) with at least three independent replicates, include error bars and statistical tests (e.g., ANOVA with multiple comparison correction), and report kinetic parameters if possible.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural modeling validation
- **Claim pointer** The authors claim that AlphaFold modeling shows the catalytic mechanism of LEM-3/ANKLE1 is conserved with bacterial GIY-YIG nucleases, and that specific residues (Y530, Y556, K559, R564, H568, E620) participate in catalysis.
- **Evidence pointer** Results section "LEM-3(241-704) structural conservation and catalysis", Figure 2A-C, Figure S5
- **Concern** The structural conclusions are based entirely on AlphaFold predictions and sequence alignments, without experimental validation of the predicted contacts or mutagenesis of all proposed catalytic residues. While the Y530F and Y556F mutations are tested in vivo, the manuscript does not report in vitro activity of these mutants on defined substrates. The claim that E620 coordinates the metal ion is not experimentally tested. Additionally, the manuscript notes that ANKLE1 N565 and K519 are not conserved in the core catalytic mechanism, but does not test whether these residues affect LEM-3 activity.
- **Why it matters** Structural predictions, while valuable, are hypotheses that require experimental testing. The paper's mechanistic conclusions about catalysis would be substantially strengthened by in vitro analysis of the proposed catalytic mutants and by testing the role of the additional helix/loop regions.
- **Resolution test** Perform in vitro nuclease assays with purified Y530F, Y556F, and E620A mutants on at least one substrate (e.g., HJ or 5'-flap) to confirm loss of activity. If possible, test the K559A, R564A, and H568A mutants as well. Consider testing the role of the additional helix/loop regions in substrate binding or catalysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Dimerization evidence
- **Claim pointer** The authors conclude that "LEM-3 may form a homodimeric complex on the HJ DNA to mediate the coordinated bilateral cleavage of the junction, like other HJ-resolving enzymes such as RuvC and Gen1."
- **Evidence pointer** Results section "Cleavage of HJ substrates and evidence for LEM-3 acting as a dimer", Figure 3C-D, Figure S8
- **Concern** The evidence for dimerization is indirect. The EMSA shows two distinct protein-DNA complexes, which the authors interpret as monomeric and dimeric species, but no direct evidence (e.g., cross-linking, size-exclusion chromatography, or analytical ultracentrifugation) is provided to confirm the stoichiometry. The Hill coefficient is mentioned but not shown or statistically evaluated. The plasmid cleavage assay shows linear product formation, suggesting dual incision, but this could also result from sequential independent cleavage events.
- **Why it matters** The dimerization model has implications for understanding the mechanism of coordinated cleavage and for comparing LEM-3 to other HJ resolvases. If the dimerization claim is not well-supported, the mechanistic model needs to be revised.
- **Resolution test** Provide direct evidence for dimer formation, such as chemical cross-linking followed by SDS-PAGE, or size-exclusion chromatography with multi-angle light scattering. Alternatively, perform a Hill plot analysis with proper statistical evaluation and show the data. If possible, test whether a catalytically dead monomer can complement a wild-type monomer in trans to demonstrate functional dimerization.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** In vivo functional redundancy
- **Claim pointer** The authors state that "the N-terminal 240 amino acids of LEM-3 are not essential for its function in vivo" and that the N-terminus "carries a function redundant with the LEM-like domain."
- **Evidence pointer** Results section "Purification of LEM-3(241-704) and genetic characterization", Figure 1D, Figure 6A-B
- **Concern** The IR sensitivity data show that lem-3(241-704) rescues IR sensitivity to wild-type levels, but the manuscript does not report whether this derivative fully rescues all LEM-3 functions, such as the timing of development or fertility. The claim of redundancy between the N-terminal region and the LEM-like domain is based on the observation that full-length LEM-3 with a deleted LEM-like domain shows intermediate IR sensitivity, but the mechanism of this redundancy is not explored.
- **Why it matters** Understanding which domains are essential for LEM-3 function is important for the structure-function model. The redundancy claim has implications for how LEM-3 is regulated and how it interacts with other proteins.
- **Resolution test** Perform additional phenotypic analyses (e.g., developmental timing, brood size, chromosome segregation fidelity) for the various LEM-3 derivatives. If possible, test whether the N-terminal region and LEM-like domain bind to overlapping or distinct partners to explain the redundancy.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Toxicity mechanism
- **Claim pointer** The authors propose that "preventing LEM-3 nuclear access is important to avoid toxicity, likely caused by branched DNAs cleavage during normal DNA metabolism."
- **Evidence pointer** Results section "Role of LEM-domain for catalytic activity and toxic LEM-3 derivates", Figure 4C-D, Figure S9
- **Concern** The toxicity of the GIY-YIG-only derivative is attributed to nuclear access and cleavage of genomic DNA, but the manuscript does not directly demonstrate that the toxicity is due to DNA cleavage. The Y530F mutation in the GIY-YIG-only background suppresses toxicity, which is consistent with a cleavage-dependent mechanism, but alternative explanations (e.g., protein aggregation, sequestration of binding partners) are not excluded. The manuscript also does not address whether the toxicity is cell-autonomous or due to developmental defects.
- **Why it matters** The toxicity mechanism is a key finding with potential relevance to understanding how nucleases are regulated to prevent genomic damage. A clearer mechanistic understanding would strengthen the paper.
- **Resolution test** Perform experiments to directly test whether the toxic derivative causes DNA damage (e.g., γH2AX staining, comet assay, or pulsed-field gel electrophoresis). If possible, test whether the toxicity requires the catalytic activity by using a catalytically dead mutant in the GIY-YIG-only background.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract
- **Evidence pointer** Abstract, last sentence
- **Issue** The phrase "last chance catch-all" is informal and may not be appropriate for a scientific manuscript. The term "catch-all" is vague and could be misinterpreted.
- **Required correction** Replace with more precise language, e.g., "acts as a final safeguard mechanism that processes diverse DNA bridge substrates before cell division."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Materials and Methods, nuclease assays
- **Evidence pointer** Materials and Methods section "DNA substrate preparation and nuclease assays"
- **Issue** The manuscript does not specify the exact reaction conditions for nuclease assays (e.g., enzyme concentration range, time points, temperature, buffer composition beyond what is mentioned). This limits reproducibility.
- **Required correction** Provide a detailed description of reaction conditions, including a range of enzyme concentrations tested, time courses, and the specific buffer components used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, IR sensitivity assays
- **Evidence pointer** Results section "Purification of LEM-3(241-704) and genetic characterization", Figure 1D
- **Issue** The IR sensitivity data are described qualitatively (e.g., "protected from ionizing radiation") without reporting the number of biological replicates, the number of embryos scored, or statistical comparisons between strains.
- **Required correction** Report the number of independent experiments, the number of embryos scored per condition, and the statistical test used to compare strains.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figures S1-S10
- **Evidence pointer** Referenced throughout Results
- **Issue** The supplementary figures are referenced but not described in sufficient detail in the text. For example, Figure S1A is mentioned as showing protein purification but the purity and yield are not described.
- **Required correction** Briefly describe the key findings of each supplementary figure in the text to help readers interpret the data without needing to access the figures separately.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The manuscript does not discuss potential limitations of the study, such as the use of truncated protein fragments for in vitro studies, the reliance on AlphaFold predictions without experimental structures, or the potential differences between C. elegans and human LEM-3/ANKLE1.
- **Required correction** Add a paragraph discussing the limitations of the study and how they might affect the interpretation of the results.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 1
- **Issue** The introduction cites references for DNA bridge formation and resolution but does not provide a comprehensive overview of the field. Some statements lack specific citations (e.g., the claim that ANKLE1 localizes to the midbody).
- **Required correction** Ensure all factual claims are supported by appropriate citations and consider expanding the introduction to provide more context on the known functions of LEM-3/ANKLE1.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Materials and Methods
- **Evidence pointer** Materials and Methods section
- **Issue** The manuscript does not include a data availability statement. Given the increasing requirements for data sharing, this is a notable omission.
- **Required correction** Add a data availability statement indicating where the data and materials can be accessed.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Nomenclature consistency
- **Affected element** Throughout
- **Evidence pointer** Results, Figure legends
- **Issue** The manuscript uses both "LEM-3(241-704)" and "GFP::LEM-3(241-704)" to refer to different constructs, which is clear, but the naming of mutants (e.g., "Y530F") is not always consistent with the full construct name (e.g., "LEM-3(241-704)-Y530F" vs "GFP::LEM-3Y530F(241-704)"). This could cause confusion.
- **Required correction** Standardize the naming convention for all constructs and mutants throughout the manuscript.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1
- **Evidence pointer** Figure 1A
- **Issue** The domain structure schematic in Figure 1A is described in the text but the figure itself is not available for review. The authors should ensure that the schematic is clear and accurately represents the domain boundaries.
- **Required correction** Verify that the domain schematic is accurate and clearly labeled, and consider adding a scale bar or amino acid positions.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Discussion of alternative interpretations
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph on dimerization
- **Issue** The discussion of dimerization does not consider alternative models, such as monomeric nicking followed by dissociation and rebinding, or the possibility that the two cleavage events are not coordinated.
- **Required correction** Briefly discuss alternative models and explain why the dimerization model is preferred based on the available data.

## Risk / unsupported claims
- The claim that LEM-3 forms a homodimer on HJ DNA is not directly supported by the presented evidence; the EMSA data are consistent with but do not prove dimerization.
- The claim that the catalytic mechanism of LEM-3/ANKLE1 is conserved with bacterial GIY-YIG nucleases is based on AlphaFold predictions and sequence alignments, which are suggestive but not definitive without experimental validation.
- The statement that "preventing LEM-3 nuclear access is important to avoid toxicity, likely caused by branched DNAs cleavage during normal DNA metabolism" is presented as a conclusion but is partly speculative; the manuscript does not directly demonstrate that the toxicity is due to DNA cleavage.
- The claim that the N-terminal 240 amino acids are not essential for LEM-3 function in vivo is based on IR sensitivity data, but the manuscript does not report whether other phenotypes (e.g., developmental timing, fertility) are fully rescued.
- The manuscript states that LEM-3(485-704) has "residual activity only observable at the highest protein concentration" but does not quantify this activity or compare it statistically to the null control.
- The statement that "LEM-3 may have an additional role independent of catalysis" is supported by the observation that catalytic mutants are less sensitive than null alleles, but the nature of this non-catalytic role is not explored.