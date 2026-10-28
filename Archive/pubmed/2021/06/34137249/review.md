## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) with supplementary material referenced but not provided.
- **Assessment boundary** Scientific claims, methodological soundness, and interpretation of results as presented in the manuscript. No assessment of editorial fit or publication policy.
- **Shared manuscript claim summary** The authors use microsecond-scale all-atom MD simulations to characterize DNA recognition by transcription factors MarA and Rob. They propose that the N-terminal HTH motif, particularly Arg40, drives specific tight binding to the A-box of target promoters, and that an acidic C-terminal loop in Rob modulates the DNA binding mode, allowing interconversion between single- and dual-HTH binding states.
- **Visible evidence base** Main text figures (Figures 1–10), supplementary figures and tables (S1–S52), simulation methods, and MM-PBSA binding energy estimates. Supplementary movies referenced but not reviewed.
- **Missing materials affecting confidence** Supplementary tables (S1–S22) and figures (S1–S52) are referenced extensively but not provided in the submitted material. This limits verification of quantitative results, simulation convergence, and detailed interaction analyses.

## Reviewer
- **Overall assessment** The manuscript presents a substantial computational study of two homologous transcription factors, addressing a biologically relevant question about DNA recognition mechanisms. The simulation effort is extensive (307.5 μs cumulative), and the authors connect their findings to prior experimental data. However, several claims, particularly regarding the role of Arg40 and the loop-deletion effect, are not fully supported by the evidence presented in the main text. The absence of supplementary data prevents full evaluation of key quantitative analyses. The mechanistic conclusions are plausible but require stronger validation, especially given known limitations of force-field-based simulations for protein–DNA interactions.
- **Who would be interested in the results, and why** Researchers in computational biophysics, protein–DNA recognition, transcription factor biology, and antimicrobial drug design. The study provides a detailed dynamic view of how two homologous TFs achieve different DNA binding modes, which is relevant for understanding specificity in the AraC/XylS family and for structure-based design of antivirulence agents.
- **Major strengths** 1) Extensive sampling (307.5 μs) with multiple replicas per system, providing statistical power for dynamic analyses. 2) Direct connection to prior experimental mutagenesis and binding affinity data, grounding the simulations in observable biology. 3) Identification of a specific residue (Arg40) and a structural element (acidic loop) as key determinants of binding mode, offering testable hypotheses. 4) Use of multiple analysis techniques (distances, H-bonds, PCA, MM-PBSA) to cross-validate findings.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "Arg40 of the N-terminal HTH-motif allows for specific tight binding" and that this is demonstrated by their simulations.
  - **Evidence pointer** Results section "Interactions that Drive the Binding of MarA and Rob to Different DNA Sequences", Figure 6, Tables S8 and S12.
  - **Concern** The claim that Arg40 drives specific tight binding is based on H-bond occupancy analyses in simulations. However, the authors do not provide quantitative comparison of Arg40 interaction stability across different DNA sequences (e.g., wild-type vs. micFA) in the main text. The single mutation in micFA (C↔G) is stated to disrupt binding experimentally, but the simulation data showing loss of Arg40-specific contacts are not presented in sufficient detail. Furthermore, no free energy calculations (e.g., MM-PBSA per-residue decomposition) are shown to support the energetic importance of Arg40 over other residues.
  - **Why it matters** The central mechanistic claim of the paper rests on the specific role of Arg40. Without quantitative evidence that Arg40 interactions are uniquely stable or energetically dominant, the claim remains speculative. The authors themselves note poor quantitative agreement between MM-PBSA predictions and experimental KDNA values, which undermines confidence in energetic interpretations.
  - **Resolution test** Provide per-residue interaction energy decomposition or H-bond occupancy comparisons between wild-type and mutant complexes, showing that Arg40 interactions are significantly more stable or energetically favorable than other residues. Alternatively, perform alchemical mutation simulations of Arg40 to demonstrate its contribution to binding free energy.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "an acidic C-terminal loop of Rob can control the DNA binding mode, facilitating interconversion between the distinct DNA binding modes observed in MarA and Rob."
  - **Evidence pointer** Results section "The Role of the Rob C-Terminal Domain in DNA Binding", Figures 8–9, Figures S45–S47.
  - **Concern** The loop-deletion simulations show that the Rob variant can bind both A- and B-boxes, but the authors do not demonstrate that this is due to removal of the acidic loop per se, rather than to other structural changes caused by the deletion. The loop is replaced by a single alanine, which could alter local flexibility or electrostatics in ways unrelated to the specific acidic character. No control simulations (e.g., neutral loop substitution) are presented. Additionally, the claim of "interconversion" implies dynamic switching between binding modes, but the simulations do not show repeated transitions within a single trajectory; rather, the loop-deletion variant simply adopts a different stable state.
  - **Why it matters** The conclusion that the acidic loop controls binding mode is a key finding with potential regulatory implications. If the effect is due to non-specific structural perturbation rather than the acidic nature of the loop, the biological interpretation changes. The lack of dynamic evidence for interconversion weakens the claim of a regulatory switch.
  - **Resolution test** Perform simulations with a neutral loop substitution (e.g., replacing acidic residues with serines) to isolate the electrostatic effect. Show multiple binding/unbinding events of the C-terminal HTH motif within individual trajectories to demonstrate true interconversion, or use enhanced sampling methods to estimate free energy barriers between binding modes.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The authors state that "we performed 5 × 2.5 μs MD simulations of each protein in complex with all the DNA sequences considered in this work" and that cumulative simulation time is 307.5 μs.
  - **Evidence pointer** Methods section "System Setup" and "Simulation Details", Tables S3 and S4.
  - **Concern** The exact number of systems and replicas is not fully clear from the main text. The authors mention 10 complexes (5 MarA + 5 Rob) plus free proteins and free DNA, but the total simulation time of 307.5 μs implies more systems than described. The supplementary tables are not provided, so the simulation matrix cannot be verified. Additionally, convergence criteria for the simulations are not stated.
  - **Why it matters** Reproducibility is a core requirement for computational studies. Without a clear enumeration of all systems, replicas, and simulation lengths, readers cannot assess whether the sampling is sufficient for the conclusions drawn. Lack of convergence analysis raises concerns about the reliability of the dynamic and energetic results.
  - **Resolution test** Provide a complete table of all simulated systems, number of replicas, simulation lengths, and convergence metrics (e.g., RMSD stabilization, block averaging of key observables) in the main text or supplementary material.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, last sentence
  - **Issue** The abstract states that the work provides "detailed molecular insight into DNA binding and recognition by these proteins, which in turn is an important step toward the efficient design of antivirulence agents." This claim of translational relevance is not supported by any direct evidence in the manuscript, as no drug design or inhibitor studies are presented.
  - **Required correction** Soften the claim to indicate potential relevance for future drug design, or remove it from the abstract.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, MM-PBSA calculations
  - **Evidence pointer** Methods section "Predictions of the Protein–DNA Binding Energies"
  - **Issue** The authors use an internal dielectric constant of 10 for MM-PBSA calculations, citing a prior benchmark. However, they also acknowledge poor quantitative agreement with experimental KDNA values. The choice of dielectric constant is a known sensitive parameter, and the authors do not discuss how varying it would affect their conclusions.
  - **Required correction** Add a sensitivity analysis for the dielectric constant or discuss the limitations of the MM-PBSA approach more explicitly in the context of their qualitative conclusions.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Results section "Interactions that Drive the Binding of MarA and Rob to Different DNA Sequences"
  - **Evidence pointer** Figure 6 and accompanying text
  - **Issue** The description of H-bond networks and π–π stacking interactions is dense and would benefit from a schematic diagram summarizing the key contacts for both MarA and Rob with their respective DNA sequences.
  - **Required correction** Add a simplified schematic figure showing the key protein–DNA contacts (Arg40, Trp36, etc.) for both proteins, to aid reader comprehension.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, system preparation
  - **Evidence pointer** Methods section "System Setup"
  - **Issue** The authors state that MarA complexes were built by aligning MarA onto the Rob-micF complex, but details of the alignment procedure (e.g., which residues were used for superposition) are not provided. This could affect the initial placement of the C-terminal HTH motif relative to the DNA.
  - **Required correction** Provide details of the structural alignment, including the residue ranges used for superposition and any subsequent minimization or equilibration steps that might relax the initial geometry.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The central mechanistic claims regarding Arg40 and the acidic loop require stronger quantitative evidence. Additionally, the lack of convergence analysis and incomplete system enumeration (R1-M3) must be addressed to establish the reliability of the simulation results.
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The study applies established MD simulation techniques to a new system, but the conceptual framework (HTH motif dynamics, DNA bending) is not novel. The identification of the acidic loop as a binding-mode switch is the most original aspect.  
  *Scientific importance*: Moderate. The findings are relevant to understanding transcription factor specificity, but the biological implications are limited by the lack of experimental validation of the predicted loop-deletion effect.  
  *Interdisciplinary readership*: Limited. The manuscript is written for a specialized computational biophysics audience. The biological significance is not framed in a way that would attract a broader readership.  
  *Technical soundness*: The simulation methodology is standard and appropriate, but the analysis and interpretation have gaps as detailed in the major concerns. The MM-PBSA limitations are acknowledged but not fully addressed.  
  *Readability for nonspecialists*: The manuscript is dense and assumes familiarity with MD simulation techniques and protein–DNA interaction analysis. The main conclusions are stated clearly, but the supporting evidence is difficult to follow without access to the supplementary material.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an interesting question with substantial computational effort, but the key mechanistic claims require additional analysis and validation. The authors should address the blocking concerns regarding Arg40 and the acidic loop, provide convergence and system details, and consider softening translational claims. With these revisions, the manuscript could become a solid contribution to the computational biophysics literature, though its scope and impact are likely more suited to a specialized journal than a broad-interest venue.

## Risk / unsupported claims
- The claim that Arg40 "allows for specific tight binding" is not quantitatively supported in the main text.
- The claim that the acidic loop "facilitates interconversion between distinct DNA binding modes" is not supported by dynamic evidence of switching.
- The statement that the work is "an important step toward the efficient design of antivirulence agents" is unsupported by any direct evidence in the manuscript.
- The assertion that "the system reaches a conformation close to that observed in the crystal structure within the first 500 ns" is based on visual inspection of movies, not quantitative comparison.
- The claim that "B-box mutations do not prevent the HTH helices from being inserted into the major grooves" is based on simulations of mutant complexes, but the experimental binding data for these mutants are not presented in the main text.