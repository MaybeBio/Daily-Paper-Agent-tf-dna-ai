## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided by the author.
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by the presented evidence. No assessment of editorial fit or publication policy.
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics (CGMD) simulations with a 1-bead-per-amino acid protein model and a newly developed 3-bead-per-nucleotide RNA model to study ternary phase diagrams of FUS/TDP43, RNA (U40), and dipeptide repeat proteins (DPRs) associated with C9orf72 ALS/FTD. They report that arginine-containing DPRs (R-DPRs) disrupt native RBP-RNA condensates via cation-π and electrostatic interactions, leading to core-shell or marbled morphologies, and propose this as a potential toxicity mechanism.
- **Visible evidence base** Main text figures (Figures 1–7), supplementary figure references (Figures S1–S23), and methodological descriptions in the Models and Simulation Methods section.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S23) are referenced but not provided. Simulation parameter files, force field details, and convergence criteria are not fully described. No experimental validation data are included.

## Reviewer
- **Overall assessment** The manuscript presents a systematic computational study of ternary phase behavior in RBP-RNA-DPR systems, addressing a relevant hypothesis in C9orf72 ALS/FTD research. The work is technically competent in its use of CGMD and offers a plausible mechanistic framework. However, the central claims regarding toxicity mechanisms are extrapolated from simulation observations without direct experimental validation, and several methodological details are insufficiently described to fully assess robustness. The novelty is moderate, building on prior CGMD work by the same group, and the biological implications, while interesting, remain speculative.
- **Who would be interested in the results, and why** Researchers in computational biophysics, phase separation, and neurodegeneration. The study provides a molecular-level framework for how DPRs might alter RBP-RNA condensate architecture, which could inform experimental design in ALS/FTD research. The methodological extension of the 1BPA model to RNA may also interest modelers.
- **Major strengths** 1. Systematic exploration of ternary phase diagrams across multiple DPR lengths and sequences. 2. Clear identification of distinct interaction types (cation-π, electrostatic) driving different morphological outcomes. 3. Use of a consistent simulation protocol with explicit equilibration and production phases. 4. The proposed core-shell morphology as a potential toxicity mechanism is a testable hypothesis.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (force field validation), R1-M2 (convergence and sampling), R1-M3 (biological extrapolation), R1-M4 (model representation of TDP43).
- **Assessment against Nature-style criteria**  
  - *Originality*: Moderate. The application of CGMD to ternary RBP-RNA-DPR systems is a logical extension of prior work, but the core interaction mechanisms (cation-π, electrostatics) are well established. The specific morphological predictions (core-shell, marbled) add some novelty.  
  - *Scientific importance*: Moderate to high. The question of DPR toxicity in C9orf72 ALS/FTD is of significant biomedical interest, and the study offers a mechanistic hypothesis. However, the lack of experimental validation limits immediate impact.  
  - *Interdisciplinary readership*: The work bridges biophysics, computational chemistry, and neurobiology, but the technical focus may limit accessibility to a broad biological audience.  
  - *Technical soundness*: Generally sound within the CGMD framework, but concerns about force field validation, sampling convergence, and model representation reduce confidence.  
  - *Readability for nonspecialists*: The introduction and conclusions are accessible, but the methods and results sections assume familiarity with CGMD and phase separation concepts. Figures are informative but some (e.g., Figure 3) are dense.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is plausible and the simulations are a reasonable first step, but the manuscript currently overreaches in its biological conclusions without experimental support or sufficient methodological validation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that the 1BPA model and the newly developed 3BPN model are suitable for studying RBP-RNA-DPR phase behavior, and that the observed morphologies reflect native interactions.  
- **Evidence pointer** Models and Simulation Methods section, Figures 1–7, Figure S1–S2 (referenced but not provided)  
- **Concern** The 3BPN model is described as "newly developed," but no validation against experimental RNA phase behavior or known RNA-protein interactions is presented. The mapping from Kapcha-Rossky hydrophobicity to 1BPA parameters is described only briefly, and the accuracy of this mapping for RNA is not demonstrated. Additionally, the 1BPA model's performance is only shown in a supplementary figure (S1) that is not available for review.  
- **Why it matters** Without validation of the RNA model and the combined protein-RNA force field, the quantitative and even qualitative predictions of phase behavior (e.g., core-shell formation, marbled structures) may be artifacts of the model rather than physical properties. This undermines the central claims of the manuscript.  
- **Resolution test** Provide validation of the 3BPN model against experimental RNA condensation data or high-resolution simulations. Show that the 1BPA model reproduces known phase behavior of FUS and TDP43 in the absence of RNA. Include these data in the main text or accessible supplementary material.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that the simulated phase diagrams and morphologies are representative of equilibrium or near-equilibrium behavior, and that the 3 μs production runs are sufficient to capture the relevant physics.  
- **Evidence pointer** Models and Simulation Methods section (Droplet Simulation Protocol), Figures 1, 3, 5, S5  
- **Concern** The manuscript does not report on convergence of the simulations. No analysis of time evolution of order parameters (e.g., cluster sizes, density profiles) is provided to demonstrate that the observed morphologies are stable over the 3 μs production run. The use of a single initial configuration per composition (as implied) raises concerns about sampling bias, especially for complex multicomponent systems where kinetic trapping is likely.  
- **Why it matters** If the simulations are not converged, the reported phase diagrams and morphological classifications (e.g., core-shell vs. marbled) may reflect transient states rather than equilibrium behavior. This would invalidate the mechanistic conclusions drawn from the phase diagram.  
- **Resolution test** Provide convergence analysis, such as time evolution of key observables (e.g., radius of gyration, contact numbers) and replicate simulations from different initial conditions. Show that the phase boundaries and morphologies are reproducible and stable over the simulation time.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance / Claim support  
- **Claim pointer** The authors conclude that "R-DPRs can disrupt the RBP condensates through cation-π interactions and can strongly sequester RNA through electrostatic interactions," and that this "provides a potential mechanism for R-DPR toxicity" via increased interfacial area.  
- **Evidence pointer** Conclusions section, Figures 3, 5, 7  
- **Concern** The leap from simulation observations to a toxicity mechanism is not supported by the data presented. The simulations show morphological changes, but no link to cellular toxicity, aggregation kinetics, or functional outcomes is established. The claim that increased interfacial area "could provide a mechanism to increase the rate of aggregation transitions" is purely speculative and not tested.  
- **Why it matters** The manuscript's significance hinges on the biological relevance of the findings. Without experimental evidence or at least a quantitative link to known toxicity thresholds (e.g., DPR concentration, repeat length), the conclusions remain a hypothesis, not a demonstrated mechanism. This overreach weakens the paper's impact.  
- **Resolution test** Either temper the conclusions to clearly state the speculative nature of the toxicity link, or add experimental data (e.g., in vitro aggregation assays, cell-based studies) that test the predicted morphological changes and their consequences.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Technical soundness  
- **Claim pointer** The authors use the TDP43 C-terminal domain (residues 273–414) to represent full-length TDP43 and claim that "TDP43 droplets excluding U40" reflects native behavior.  
- **Evidence pointer** Models and Simulation Methods section (Protein and RNA Sequences), Figures 4–5  
- **Concern** The TDP43 construct lacks the RRM domains, which are known to be critical for RNA binding. The authors acknowledge this but do not discuss how this truncation affects the interpretation of the ternary phase behavior. The claim that TDP43-RNA interactions are "significantly curtailed" without RRM domains is presented as a finding, but it is an artifact of the model construct.  
- **Why it matters** The comparison between FUS (which includes the RGG1 RNA-binding domain) and TDP43 (which lacks RRM domains) is not apples-to-apples. This could lead to incorrect conclusions about the relative roles of RNA binding in the two systems and the generality of the proposed toxicity mechanism.  
- **Resolution test** Include simulations with a TDP43 construct that includes the RRM domains, or clearly frame the results as specific to the C-terminal domain and discuss the limitations this imposes on the conclusions.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Figure 3 and Figure S5  
- **Evidence pointer** Results and Discussion section, Figures 3, S5  
- **Issue** The ternary phase diagrams are complex and the color-coding scheme is not fully explained in the main text. The distinction between "full LLPS," "U40 in dilute phase," and "PR60 in dilute phase" regions is not immediately clear from the figure alone.  
- **Required correction** Add a clear legend and a brief description of the phase diagram regions in the figure caption or main text. Consider simplifying the presentation or using annotated schematics.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Simulation protocol  
- **Evidence pointer** Models and Simulation Methods section (Droplet Simulation Protocol)  
- **Issue** The manuscript states that the initial droplet is formed and then inserted into a larger box, but the details of the initial droplet preparation (e.g., how the droplet is equilibrated before insertion) are not described.  
- **Required correction** Provide a more detailed description of the initial droplet preparation and the equilibration steps, including the rationale for the chosen box sizes and densities.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scientific importance  
- **Affected element** Discussion of ΔR-DPRs  
- **Evidence pointer** Results and Discussion section (Aliphatic Interactions Drive Length Dependent LLVM of ΔR-DPRs), Figure S7  
- **Issue** The finding that short ΔR-DPRs (GA15) do not interact with RBP condensates is presented as consistent with experimental observations, but the specific experimental references are not cited in the text.  
- **Required correction** Add appropriate citations to experimental studies that support the lack of interaction for short ΔR-DPRs, to strengthen the connection between simulation and experiment.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Conclusions section  
- **Evidence pointer** Conclusions section  
- **Issue** The conclusion that "the second hypothesis (R-DPRs have an indirect effect through RNA interaction on RBP function) is more likely" is stated without a clear summary of the evidence for and against the first hypothesis (direct RBP interaction).  
- **Required correction** Provide a brief comparative summary of the evidence for both hypotheses before stating the preferred one, to make the reasoning transparent.

## Risk / unsupported claims
- The claim that R-DPR-induced morphological changes "could provide a potential mechanism for R-DPR toxicity" is unsupported by direct evidence and is speculative.
- The claim that the 3BPN model is "1BPA-compatible" and suitable for studying RNA-protein interactions is not validated against experimental or high-resolution reference data.
- The claim that TDP43 "excluding U40" reflects native behavior is an artifact of the truncated construct and is not representative of full-length TDP43.
- The claim that "no discernible difference" between PR and GR R-DPRs is a general conclusion is based on limited sequence sampling and may not hold for other repeat lengths or contexts.
- The quantitative phase diagram boundaries (e.g., "small additions of R-DPRs") are not defined with error bars or statistical analysis, making the thresholds unreliable.