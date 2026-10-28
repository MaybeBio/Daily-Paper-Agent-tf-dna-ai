## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No external data, supplementary figures, or raw datasets were available for verification.
- **Shared manuscript claim summary** The authors identify a piperine analog (PIP-2) that selectively binds to and stabilizes the G-quadruplex (G4) motif in the c-myc promoter, leading to downregulation of c-myc transcription and translation, with selective cytotoxicity toward A549 lung cancer cells.
- **Visible evidence base** Biophysical assays (fluorescence binding, ITC, CD, CD melting), gel retardation, PCR stop assay, molecular docking and MD simulation, MTT cytotoxicity, mTFP reporter assay, qRT-PCR, western blotting, ROS measurement, wound healing, and colony formation assays.
- **Missing materials affecting confidence** Supplementary figures and tables (e.g., full gel images, binding curves, statistical details), raw MD simulation data, structural validation of PIP-2, and detailed experimental replicates. These are referenced but not provided in the submitted text.

## Reviewer
- **Overall assessment** The manuscript presents a systematic screening of piperine analogs and identifies PIP-2 as a promising c-myc G4 stabilizer with selective anticancer activity. The combination of biophysical, computational, and cellular assays is commendable. However, several technical and interpretive gaps, particularly regarding binding stoichiometry, selectivity quantification, and mechanistic causality, prevent the current evidence from fully establishing the central claims.
- **Who would be interested in the results, and why** Researchers in chemical biology, nucleic acid structure and function, anticancer drug discovery, and G-quadruplex-targeting therapeutics. The work may also interest those exploring natural-product-derived scaffolds for promoter-targeted gene regulation.
- **Major strengths**  
  - Multi-technique approach integrating biophysics, computation, and cell biology.  
  - Identification of a lead compound with improved selectivity and potency over the parent piperine.  
  - Use of multiple control DNA structures (mutant G4, duplex, other G4s) to support selectivity.  
  - Cellular assays include both cancer and non-cancer cell lines, addressing therapeutic window.
- **Major Concerns**
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The manuscript claims a 1:2 binding stoichiometry for PIP-2 with c-myc G4 DNA based on fluorescence and ITC data.  
  - **Evidence pointer** Section "Steady-state fluorescence binding assay", "Isothermal titration calorimetry (ITC) assay", Figure 4, Supplementary Tables S4a and S5a.  
  - **Concern** The two-site binding model is used to fit both fluorescence and ITC data, but the manuscript does not provide adequate justification for this model, nor does it discuss alternative models (e.g., cooperative vs. independent sites). The reported Kd and Ka values are presented without confidence intervals or goodness-of-fit statistics. The stoichiometry claim is central to the proposed mechanism but is not rigorously validated.  
  - **Why it matters** If the binding model is incorrect, the derived thermodynamic parameters and the proposed 1:2 interaction mode are unreliable, undermining the mechanistic interpretation of G4 stabilization.  
  - **Resolution test** Provide global fitting with statistical comparison of one-site vs. two-site models, include residuals, confidence intervals, and independent validation (e.g., ESI-MS or analytical ultracentrifugation) to confirm stoichiometry.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Scientific importance / claim support  
  - **Claim pointer** The manuscript claims that PIP-2 selectively downregulates c-myc expression via G4 stabilization, with no significant effect on other G4-containing oncogenes (c-kit, bcl-2).  
  - **Evidence pointer** Section "Analysis of the effect of PIP-2 on the transcription of c-myc and other oncogenes", Figure 11e,f, Supplementary Figure S23.  
  - **Concern** The qRT-PCR data show c-myc downregulation, but the selectivity claim is based on a single concentration (6 µM) and lacks dose-response data for c-kit and bcl-2. The western blot only examines c-myc protein, not the other oncogenes. The manuscript does not demonstrate that the observed downregulation is directly caused by G4 stabilization rather than off-target effects or general cytotoxicity.  
  - **Why it matters** The central therapeutic premise is that PIP-2 acts through a G4-mediated, gene-specific mechanism. Without direct evidence linking G4 binding to transcriptional repression (e.g., via chromatin immunoprecipitation or reporter assays with mutated G4), the mechanism remains correlative.  
  - **Resolution test** Include dose-response qRT-PCR for c-kit and bcl-2, perform a reporter assay with a G4-disrupting mutation in the c-myc promoter, and assess whether PIP-2 affects c-myc mRNA stability independently of transcription.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Technical soundness  
  - **Claim pointer** The manuscript states that PIP-2 shows higher toxicity toward A549 cells (IC50 = 6.00 ± 0.12 µM) and lower toxicity toward HEK293 cells (IC50 = 48.62 ± 0.42 µM).  
  - **Evidence pointer** Section "Cell toxicity assay of PIP-2 in malignant and non-malignant cell lines", Figure 8a–f, Supplementary Table S8.  
  - **Concern** The IC50 values are reported with very small standard deviations, which is unusual for biological triplicates and may indicate overfitting or insufficient replication. The manuscript does not specify the number of independent experiments or the statistical test used to compare IC50 values across cell lines. Additionally, the selectivity index is not calculated or discussed.  
  - **Why it matters** The therapeutic window claim depends on the reliability and statistical robustness of the cytotoxicity data. Inflated precision or unreported variability could mislead readers about the compound's safety profile.  
  - **Resolution test** Report the number of replicates, the statistical method used, and provide a selectivity index with confidence intervals. Include raw cell viability data as supplementary material.

- **Minor Comments**
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Readability for nonspecialists  
  - **Affected element** Introduction  
  - **Evidence pointer** Section "Introduction"  
  - **Issue** The introduction is dense and assumes familiarity with G4 biology and c-myc regulation. Terms such as "Hoogsteen hydrogen bonding" and "nuclease hypersensitive element III1" are introduced without brief explanations.  
  - **Required correction** Add one or two sentences defining G4 structures and their biological relevance for a broader readership.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Technical soundness  
  - **Affected element** Methods, "Molecular dynamics simulation"  
  - **Evidence pointer** Section "Study of the atomic level interaction of c-myc-PIP-2 G4 DNA complex by molecular dynamics simulation"  
  - **Issue** The MD simulation parameters are not fully described. The force field, water model, temperature/pressure coupling, and simulation length are not stated. The convergence of the simulation is not demonstrated.  
  - **Required correction** Provide full simulation details in the Methods section, including software version, force field parameters, equilibration protocol, and analysis methods.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Scientific importance  
  - **Affected element** Discussion of selectivity  
  - **Evidence pointer** Section "Study of interaction of Piperine analog PIP-2 with c-myc G4 DNA using fluorescence emission spectroscopy"  
  - **Issue** The manuscript states that PIP-2 shows higher affinity for c-myc G4 than for other G4s, but the quantitative comparison is not presented in the main text. The Kd values for other G4s are only in supplementary tables.  
  - **Required correction** Include a summary table or figure in the main text comparing Kd values across all tested G4 and control DNA to support the selectivity claim.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Technical soundness  
  - **Affected element** Methods, "mTFP reporter assay"  
  - **Evidence pointer** Section "Construction of c-myc and c-myc mutant G4 m-TFP based plasmid and perform m-TFP based reporter assay"  
  - **Issue** The description of the mTFP reporter assay is brief. It is unclear whether the G4 sequence was inserted in the promoter or 5' UTR, and how the mutant was designed to disrupt G4 formation.  
  - **Required correction** Clarify the construct design, the position of the G4 motif relative to the reporter gene, and the nature of the mutations used to abrogate G4 formation.

- **Technical failings that need to be addressed before the case is established**  
  - R1-M1: Binding stoichiometry and model validation.  
  - R1-M2: Direct mechanistic link between G4 stabilization and transcriptional downregulation.  
  - R1-M3: Statistical robustness of cytotoxicity data and selectivity index.

## Risk / unsupported claims
- The claim that PIP-2 "arrests" the c-myc gene is not supported by direct evidence of transcriptional arrest; the data show reduced mRNA and protein levels, which could result from multiple mechanisms.
- The claim of "strong selectivity" for c-myc G4 over other G4s is not quantitatively established in the main text.
- The statement that PIP-2 "may be used as anticancer therapeutics" is speculative given the lack of in vivo efficacy or pharmacokinetic data.
- The molecular dynamics results are presented as supporting stability, but without convergence criteria or error analysis, the conclusions are not fully verifiable.