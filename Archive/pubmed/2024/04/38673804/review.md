## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, conclusions)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and conclusions as presented in the manuscript
- **Shared manuscript claim summary** The authors report that the Entamoeba histolytica heat shock transcription factor EhHSTF5 oligomerizes into dimers and trimers in a concentration-dependent manner, and that the dimeric form binds with higher affinity to the heat shock element (HSE) in the EhPgp5 gene promoter than the monomeric form. In silico modeling and docking suggest the alpha-3 helix of the DNA-binding domain mediates specific contacts with the HSE major groove.
- **Visible evidence base** Western blot data (Figure 1), purification profiles (Figure 2), crosslinking assays (Figure 3), EMSA and supershift assays (Figure 4), structural models and validation metrics (Figures 5-6, Supplementary Figure S2), docking scores and interaction analyses (Figure 7, Supplementary Table S1), structural superposition data (Figure 8), and a schematic summary (Figure 9)
- **Missing materials affecting confidence** Original gel/blot images, raw densitometry data, statistical analysis outputs, molecular docking parameter details, model template alignment details, and negative control data for EMSA experiments were not fully described. No in vivo functional validation was provided.

## Reviewer
- **Overall assessment** This manuscript presents a straightforward biochemical and computational characterization of EhHSTF5 oligomerization and DNA binding. The experimental design is logical and the data generally support the conclusion that dimeric EhHSTF5 binds HSE_EhPgp5 with higher affinity than the monomer. However, several technical concerns regarding protein identity confirmation, quantitative rigor, and the biological relevance of the in vitro conditions limit the strength of the conclusions. The in silico component is descriptive and would benefit from more robust validation. The claim that EhHSTF5 may regulate multiple HSE-containing genes is speculative and not directly tested.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation in parasitic protozoa, particularly those interested in stress response mechanisms in Entamoeba histolytica. The work may also be of interest to investigators studying heat shock transcription factor structure-function relationships across species, given the conserved nature of the DNA-binding domain. The potential link to drug resistance mechanisms via EhPgp5 regulation could attract those working on antiparasitic drug development.
- **Major strengths** The study addresses a relevant gap in understanding EhHSTF family members beyond EhHSTF7. The combination of in vitro biochemical assays with in silico structural analysis provides complementary evidence. The crosslinking and EMSA experiments directly test the oligomerization-binding relationship. The structural conservation analysis across species is informative.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (protein identity confirmation), R1-M2 (quantitative binding affinity claims), R1-M3 (docking validation)
- **Assessment against Nature-style criteria** Originality: Moderate. The finding that a second EhHSTF can bind HSE_EhPgp5 is incremental over prior work on EhHSTF7. Scientific importance: Moderate. The study provides mechanistic insight into stress response regulation in an important pathogen, but does not establish functional consequences in the parasite. Interdisciplinary readership: Limited. The work is primarily of interest to molecular parasitologists and transcription factor biologists. Technical soundness: Adequate but with notable gaps in protein identity confirmation and quantitative rigor. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some in silico methods could be explained more clearly.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding protein identity confirmation and quantitative binding analysis.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the 38, 76, and 114 kDa proteins represent monomer, dimer, and trimer states of rEhHSTF5, and that the 47 kDa band represents a transition state.
- **Evidence pointer** Figure 1, Section 2.1
- **Concern** The identification of the oligomeric states relies solely on molecular weight estimation from SDS-PAGE and Western blot. The 47 kDa band is described as a "transition state" without any direct evidence supporting this interpretation. The predicted molecular weight of the EhHSTF5 monomer is not explicitly stated, and the discrepancy between the predicted and observed molecular weights is not discussed. The α6xHis antibody detects only the 38 and 76 kDa bands, while the αEhHSTF5 antibody detects all four bands. This differential recognition is not adequately explained. If the 114 kDa band is a trimer, it should contain three His-tags and should be recognized by the α6xHis antibody unless the tag is buried or cleaved. The authors suggest the His-tag is "hidden" in the trimer, but this is presented without experimental evidence such as tag accessibility assays or mass spectrometry.
- **Why it matters** The central claim of the paper is that oligomerization enhances DNA binding. If the oligomeric assignments are incorrect, the interpretation of the EMSA results is compromised. The "transition state" designation for the 47 kDa band is particularly problematic as it is used to support the oligomerization pathway model.
- **Resolution test** Provide mass spectrometry analysis of the purified protein bands to confirm their identities. Perform Western blot analysis with antibodies against both N-terminal and C-terminal regions of EhHSTF5. Use size exclusion chromatography or analytical ultracentrifugation to confirm the native oligomeric states. Provide a clear explanation for the differential antibody recognition pattern.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the dimeric conformation of rEhHSTF5 shows higher affinity for HSE_EhPgp5 than the monomeric state, and that increasing dimer concentration enhances complex formation.
- **Evidence pointer** Figure 4, Section 2.4
- **Concern** The EMSA experiments are described qualitatively. No binding constants (Kd values) or quantitative comparisons between monomer and dimer binding are provided. The claim of "higher affinity" is based on visual inspection of band intensities. The concentration range tested is not clearly specified, and no saturation binding analysis was performed. The competition experiments use only two competitor concentrations (150x and 350x), which is insufficient to establish specificity quantitatively. The supershift experiment with the αEhHSTF5 antibody is used to confirm the identity of the complex, but the antibody may stabilize or destabilize the complex, confounding interpretation.
- **Why it matters** The quantitative claim of differential binding affinity between oligomeric states is a key conclusion. Without quantitative binding data, the conclusion that oligomerization "enhances" binding is not rigorously supported.
- **Resolution test** Perform quantitative EMSA with a range of protein concentrations to generate binding curves. Calculate apparent Kd values for monomer and dimer. Use fluorescence anisotropy or surface plasmon resonance as orthogonal methods to confirm binding affinities. Include a full titration series for competition experiments.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that in silico docking shows the alpha-3 helix of EhHSTF5 is crucial for binding to the HSE major groove, and that the dimeric complex exhibits more favorable interactions than the monomeric complex.
- **Evidence pointer** Section 2.7, Figure 7, Supplementary Table S1
- **Concern** The docking scores are presented as absolute values without statistical validation. No re-docking or cross-validation was performed to assess the reliability of the docking protocol. The claim that the dimer has "higher affinity" based on docking scores is problematic because docking scores are not directly equivalent to binding free energies. The interaction analysis is descriptive and lacks a systematic comparison with known HSTF-HSE crystal structures. The selection of the first docking pose is stated but no justification is provided for why this pose is biologically relevant.
- **Why it matters** The in silico results are used to support the mechanistic interpretation of the experimental data. If the docking is not properly validated, the structural conclusions are unreliable.
- **Resolution test** Perform re-docking with known HSTF-HSE complexes to validate the protocol. Use molecular dynamics simulations to assess complex stability. Provide statistical analysis of docking scores across multiple runs. Compare the predicted interaction interface with experimentally determined structures.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, Figure 1
- **Evidence pointer** Figure 1
- **Issue** The induction time course is described but the figure does not clearly show the time points evaluated. The text states that the monomer "peaked at 3 h" but the figure legend does not specify which lanes correspond to which time points.
- **Required correction** Add clear time point labels to Figure 1 and ensure the figure legend explicitly states the induction times shown.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.9
- **Evidence pointer** Section 4.9
- **Issue** The template used for homology modeling is described as "the DBD of human HSTF2 in complex with HSE" with PDB ID 5D8L. However, the sequence identity between EhHSTF5 and human HSTF2 is not reported, and the quality of the sequence alignment is not discussed.
- **Required correction** Report the sequence identity and coverage of the template. Provide the alignment as supplementary material.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 4.16
- **Evidence pointer** Section 4.16
- **Issue** The statistical methods section describes normality testing and ANOVA, but no statistical analysis is presented in the results for the EMSA or Western blot quantification. It is unclear which experiments were subjected to statistical testing.
- **Required correction** Clearly indicate which experiments were statistically analyzed and report the results in the figure legends or text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.4
- **Evidence pointer** Figure 4
- **Issue** The EMSA experiments use only the HSE from the EhPgp5 promoter. No control experiments with a mutated HSE or a different promoter sequence are shown to demonstrate sequence specificity.
- **Required correction** Include EMSA experiments with a mutated HSE probe to demonstrate sequence-specific binding.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3, Discussion
- **Evidence pointer** Section 3
- **Issue** The discussion speculates that EhHSTF5 may regulate multiple genes containing HSEs in their promoters, but no experimental evidence is provided to support this claim. The authors cite their own previous work on EhHSTF7 but do not directly test whether EhHSTF5 can bind other HSEs.
- **Required correction** Either provide experimental evidence for binding to other HSEs or clearly label this as a hypothesis requiring future testing.

## Risk / unsupported claims
- The claim that the 47 kDa band represents a "transition state" toward oligomerization is unsupported by direct evidence.
- The claim that the His-tag is "hidden" in the trimeric conformation is presented without experimental verification.
- The claim that the dimeric form has "higher affinity" for HSE_EhPgp5 is not quantitatively supported.
- The claim that EhHSTF5 may regulate a wide variety of genes harboring HSEs is speculative and not tested.
- The in silico docking results are presented as evidence of binding affinity without proper validation.
- The biological relevance of the in vitro conditions (e.g., protein concentrations, buffer conditions) to the intracellular environment of E. histolytica is not established.