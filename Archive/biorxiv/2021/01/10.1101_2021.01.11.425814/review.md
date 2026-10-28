## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusions, methods) as provided
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. Figures and tables are referenced but not directly viewable.
- **Shared manuscript claim summary** The authors report that FOXO4 and p53 interact through two distinct binding surfaces: FOXO4 FHD binds p53 TAD (specifically TAD2), and FOXO4 CR3 binds p53 DBD. Both interactions are characterized by micromolar affinities, with FOXO4 FHD-p53 TAD having higher affinity. The authors propose that these dual interactions contribute to cooperative p21 transcription and cellular senescence.
- **Visible evidence base** NMR chemical shift perturbation data (Figures 2-6), ITC thermodynamic data (Figure 7), structural models (Figure 8), and sequence alignments referenced in text
- **Missing materials affecting confidence** Actual figures and tables are not viewable. NMR spectra, CSP plots, ITC thermograms, and structural models cannot be independently assessed. Raw data, fitting parameters, and statistical analyses are not provided in full.

## Reviewer

- **Overall assessment** This manuscript addresses a biologically important question regarding the molecular basis of the FOXO4-p53 interaction, which is relevant to cellular senescence and aging-related disease. The authors use NMR spectroscopy and ITC to identify and characterize two binding interfaces. The work is potentially of interest to the senescence and transcription factor communities. However, the manuscript has several significant weaknesses. The NMR data are presented in a manner that is difficult to evaluate without the figures, and the quantitative analysis appears incomplete. The ITC data, while providing affinity values, lack sufficient detail on fitting quality and experimental replicates. The proposed model in the Discussion, while interesting, is highly speculative and goes beyond the data presented. The claim that FOXO4 CR3 and p53 TAD compete for overlapping surfaces on FOXO4 FHD is not directly tested. Overall, the core findings are plausible but the evidence as presented is not fully convincing.

- **Who would be interested in the results, and why** Researchers studying cellular senescence, transcription factor regulation, p53 biology, FOXO family proteins, and protein-protein interactions. The work may also be of interest to those developing therapeutic strategies targeting the FOXO4-p53 interaction for senescence-associated diseases. The biophysical characterization of intrinsically disordered protein regions interacting with folded domains is of methodological interest to the structural biology community.

- **Major strengths**
  1. The study addresses a clinically and biologically relevant question with potential therapeutic implications.
  2. The use of reciprocal NMR titrations (labeling either FOXO4 or p53) is a rigorous approach to map binding interfaces.
  3. The identification of a second binding interface (FOXO4 CR3-p53 DBD) beyond the previously known FHD-TAD interaction adds new information.
  4. The combination of NMR and ITC provides both structural and thermodynamic information.
  5. The alanine mutagenesis approach to probe the contribution of specific CR3 residues is appropriate.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that FOXO4 FHD binds p53 TAD with a Kd of 2.19 ± 0.06 μM and that FOXO4 CR3 binds p53 DBD with a Kd of 10.26 ± 0.64 μM, and that the FHD-TAD interaction has higher affinity.
- **Evidence pointer** Figure 7, Table 1, Results section "Thermodynamic analysis of FOXO4-p53 dual binding surface"
- **Concern** The ITC data are presented with minimal detail. The stoichiometry for the FOXO4 CR3-p53 DBD interaction is reported as 0.781, which deviates substantially from 1.0. This deviation is not adequately explained. The authors state that "it can be assumed that the two domains interact in a 1:1 ratio," but this assumption is not justified. A stoichiometry of 0.781 could indicate protein concentration errors, aggregation, or a more complex binding model. Additionally, the error values are stated to be derived from 3 replicates, but the reported errors for Kd are very small (0.06 and 0.64 μM), which seems inconsistent with typical ITC variability. The fitting model is described as "Independent," but no information is provided about the quality of the fits, residuals, or whether alternative models were tested. Without the actual ITC thermograms and fitting curves, the reliability of these thermodynamic parameters cannot be assessed.
- **Why it matters** The affinity values and their relative magnitudes are central to the authors' argument that FHD-TAD binding takes precedence over CR3-DBD binding. If the ITC data are unreliable or misinterpreted, the entire thermodynamic framework of the paper is compromised.
- **Resolution test** Provide the raw ITC thermograms, integrated heat curves, and fitted isotherms for all replicates. Report the fitting residuals and provide a justification for the "Independent" model. Address the n = 0.781 stoichiometry explicitly, either by explaining the deviation or by providing additional experiments (e.g., varying concentrations, checking protein monodispersity) to rule out artifacts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that NMR CSP analysis identified specific residues on FOXO4 FHD (G102, S105, Y137, W101ε, Q104, Y106, L160, K163, T172, E183) and on p53 TAD (TAD2 residues D48, E51, Q52, W53, F54, T55, I50) that are involved in the interaction.
- **Evidence pointer** Figures 2, 3, Results sections "FOXO4 FHD prefers binding to p53 TAD" and "p53 helix TAD2 is responsible for the interaction with FOXO4 FHD"
- **Concern** The CSP analysis is described qualitatively. The authors state that residues were "perturbed by more than the average + 2σ" or "+1σ," but the actual CSP values, the average, and the standard deviation are not reported numerically. The threshold for significance is not clearly defined. More critically, the authors do not report the magnitude of the chemical shift changes, which is essential for assessing the strength of the interaction and for mapping the binding interface. The statement that "the average value of CSP of FOXO4 FHD caused by p53 DBD was about 0.004 ppm, which was much smaller than that caused by p53 TAD, 0.154 ppm" is useful, but the distribution of CSP values and the number of residues affected are not provided. Without the actual spectra or CSP plots, it is impossible to verify the assignment of the binding interface. Additionally, the authors do not discuss whether the observed CSPs are in the fast, intermediate, or slow exchange regime on the NMR timescale, which is important for interpreting binding affinity and kinetics.
- **Why it matters** The identification of the binding interfaces is the primary experimental result of the paper. If the CSP data are not presented in a way that allows independent evaluation, the core claims cannot be verified.
- **Resolution test** Provide a table of CSP values for all assigned residues, with the average and standard deviation clearly indicated. Show the CSP plots (bar graphs) for both titrations. Indicate the exchange regime for the affected residues. If possible, map the CSPs onto the structure of FOXO4 FHD (PDB) to visually demonstrate the binding interface.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors claim that the FOXO4 CR3-p53 DBD interaction involves overlapping surfaces with DNA binding and p53 TAD binding on p53 DBD, and that this suggests a network of potentially competitive and/or coordinated interactions.
- **Evidence pointer** Figure 5, Results section "Binding surfaces of p53 DBD to DNA, p53 TAD and FOXO4 CR3 overlap", Discussion
- **Concern** The authors show that FOXO4 CR3 binds to the DNA-binding surface of p53 DBD (α-helix H3 and β-strand S2). This is an interesting observation, but the functional implications are not explored experimentally. The claim that this creates a "network of potentially competitive and/or coordinated interactions" is speculative. The authors do not test whether FOXO4 CR3 binding to p53 DBD competes with DNA binding, nor do they test whether the dual binding of FOXO4 to p53 affects p53's transcriptional activity. The proposed model in Figure 8 is entirely hypothetical and is not supported by any functional data. The authors acknowledge this in the Discussion, but the model is presented with considerable detail and confidence, which may overstate the strength of the evidence.
- **Why it matters** The functional significance of the dual binding interface is the main conceptual advance claimed by the authors. Without experimental validation, the model remains a hypothesis, and the paper's impact is diminished.
- **Resolution test** Perform competition experiments (e.g., EMSA or fluorescence anisotropy) to test whether FOXO4 CR3 inhibits p53 DBD binding to DNA. Alternatively, perform cell-based assays to test whether mutations in the FOXO4 CR3 binding surface on p53 DBD affect p21 transcription or senescence. At minimum, temper the language in the Discussion to clearly distinguish between data and hypothesis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the FOXO4 FHD-p53 TAD interaction and the FOXO4 CR3-p53 DBD interaction are both biologically relevant, and that the FHD-TAD interaction takes precedence based on higher affinity.
- **Evidence pointer** Table 1, Figure 7, Discussion
- **Concern** The comparison of binding affinities between the two interactions is complicated by the fact that the constructs used are isolated domains, not full-length proteins. The authors do not discuss how the affinities might change in the context of full-length FOXO4 and p53, where intramolecular interactions (FOXO4 FHD-CR3, p53 TAD-DBD) could compete with the intermolecular interactions. The authors mention the intramolecular FOXO4 FHD-CR3 interaction and note that it has higher affinity than the intermolecular FHD-TAD interaction, but they do not address how this affects the biological relevance of the intermolecular interaction. The claim that "the binding of FOXO4 FHD-p53 TAD takes precedence over the FOXO4 CR3-p53 DBD binding" is based solely on the Kd values of isolated domains and may not hold in a cellular context.
- **Why it matters** The relative importance of the two binding interfaces is a key conclusion. If the affinity comparison is not meaningful in a biological context, the conclusion is weakened.
- **Resolution test** Discuss the limitations of using isolated domains and address how intramolecular interactions might modulate the intermolecular affinities. If possible, perform experiments with longer constructs or full-length proteins to verify the affinity hierarchy. Alternatively, use competition experiments to directly test which interaction is preferred when all components are present.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "the binding between FOXO4's forkhead domain (FHD) and p53's transactivation domain (TAD), and between FOXO4's C-terminal transactivation domain (CR3) and p53's DNA-binding domain (DBD), mediate the FOXO4-p53 interaction." This is clear, but the abstract does not mention the relative affinities or the proposed model, which are key findings. The abstract could be more informative.
- **Required correction** Consider adding a sentence summarizing the affinity comparison and the proposed functional model.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 2
- **Issue** The introduction states that "a previous study suggested that FHD and CR3 interact to form an intramolecular complex, and CR3 kinetically affects selective DNA recognition of FHD." This is relevant, but the reference is not provided in the text (only numbered references are used). It would be helpful to briefly explain the nature of this previous study.
- **Required correction** Add a brief explanation of the previous study's findings and how they relate to the current work.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods
- **Evidence pointer** Methods, "Nuclear magnetic resonance experiments"
- **Issue** The NMR experiments are described, but the concentrations of the proteins used in the titrations are not stated. The buffer conditions are given, but the protein concentrations are essential for interpreting the titration data and for assessing whether the observed CSPs are in the appropriate regime.
- **Required correction** Add the protein concentrations used in the NMR titration experiments.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods
- **Evidence pointer** Methods, "Isothermal titration calorimetry analysis"
- **Issue** The ITC methods state that "the first injection (10 μL) was not used in the analysis," which is standard practice. However, the concentration of the titrant and the cell contents are not explicitly stated beyond "1000 μM protein" and "100 μM protein." It is also unclear which protein was in the syringe and which was in the cell for each of the two interactions studied.
- **Required correction** Clarify the experimental setup for each ITC experiment, including which protein was in the syringe and which was in the cell.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The authors propose three models for how the dual binding interface could facilitate cooperative p21 transcription. These models are presented in detail, but they are not experimentally tested. While the authors acknowledge this, the models are described with a level of confidence that may be misleading.
- **Required correction** Clearly label the models as speculative and consider presenting them more concisely.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 4
- **Issue** The authors discuss the FOXO4-DRI peptide and suggest that it exerts its effect by binding to p53 TAD2. This is an interesting implication, but it is not tested. The authors could strengthen this point by discussing whether the FOXO4-DRI peptide sequence overlaps with the FOXO4 FHD residues identified in their CSP analysis.
- **Required correction** Add a brief comparison between the FOXO4-DRI peptide sequence and the FOXO4 FHD residues that show significant CSPs upon p53 TAD binding.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: ITC data presentation is insufficient. Raw data, fitting quality, and justification for the stoichiometry deviation are missing.
  - R1-M2: NMR CSP data are not presented quantitatively. The magnitude of CSPs, the threshold for significance, and the exchange regime are not reported.
  - R1-M3: The functional significance of the dual binding interface is not experimentally tested. The proposed model is speculative.
  - R1-M4: The affinity comparison between the two interactions is based on isolated domains and may not reflect the biological context.

- **Assessment against Nature-style criteria**
  - **Originality**: The identification of a second binding interface between FOXO4 CR3 and p53 DBD is novel. Previous work had only identified the FHD-TAD interaction. This adds new information to the field.
  - **Scientific importance**: The FOXO4-p53 interaction is relevant to cellular senescence and aging, which is a topic of high interest. Understanding the molecular basis of this interaction could have therapeutic implications. However, the functional significance of the dual binding is not demonstrated, which limits the immediate importance.
  - **Interdisciplinary readership**: The work is primarily of interest to structural biologists, biophysicists, and researchers in the senescence field. The NMR and ITC methods are standard, and the findings are unlikely to attract a broad interdisciplinary audience beyond these fields.
  - **Technical soundness**: The experimental approach is appropriate, but the presentation of the data is incomplete. The NMR CSP analysis and ITC experiments are standard, but the lack of quantitative detail prevents a full assessment of the technical quality.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible. The introduction and discussion are clear. However, the results section assumes familiarity with NMR and ITC methods, which may be a barrier for some readers.

- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are plausible and potentially interesting, but the manuscript in its current form does not provide sufficient evidence to fully support the claims. The ITC and NMR data need to be presented in greater detail, and the functional model needs to be either tested or clearly labeled as speculative. If these issues are addressed, the manuscript could make a valuable contribution to the field.

## Risk / unsupported claims
- The claim that FOXO4 FHD-p53 TAD binding "takes precedence" over FOXO4 CR3-p53 DBD binding is not fully supported, as the comparison is based on isolated domains and does not account for intramolecular competition.
- The proposed model of three possible mechanisms for cooperative p21 transcription (Figure 8B) is entirely speculative and not supported by experimental data.
- The suggestion that the FOXO4-DRI peptide exerts its effect by binding to p53 TAD2 is not tested and is inferred solely from the CSP data.
- The claim that the FOXO4 CR3-p53 DBD interaction is "mediated over a wide surface" is based on the alanine mutagenesis data, but the interpretation is somewhat subjective without quantitative binding data for the mutants.
- The statement that "the binding between FOXO4's FHD and p53's TAD, and between FOXO4's CR3 and p53's DBD, mediate the FOXO4-p53 interaction" is supported by the NMR data, but the relative contribution of each interaction to the overall FOXO4-p53 complex formation is not quantified.