## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness based solely on the supplied text; no external data or supplementary materials were accessed
- **Shared manuscript claim summary** The authors report that the FXR N-terminal domain (NTD) engages in interdomain interactions with the LBD and binds coregulator proteins. They identify a novel SXXLF motif (SENLF) in the NTD that mediates these interactions, supported by luciferase reporter assays, mammalian two-hybrid (M2H) assays, and molecular dynamics (MD) simulations. Mutation of the motif to SENAA reduces transcriptional activity and alters conformational dynamics and allosteric coupling in silico.
- **Visible evidence base** Figures 1, 3, and 4 are referenced in the text; methods for cloning, luciferase assays, M2H assays, and MD simulations are described. No figure panels, numerical data, or statistical outputs are shown in the provided text.
- **Missing materials affecting confidence** Actual figure images, numerical fold-change values, statistical test outputs, MD simulation convergence metrics, AlphaFold3 model confidence scores, and construct validation data (e.g., western blots, sequencing) are not available. This limits quantitative verification of the claims.

## Reviewer
- **Overall assessment** The manuscript addresses an important and understudied question: the functional role of the intrinsically disordered NTD in FXR. The identification of a novel SXXLF motif is potentially significant for the nuclear receptor field. However, the evidence as presented is incomplete. Key claims regarding interdomain interactions and coregulator binding rely on M2H assays whose raw data are not shown, and the MD simulation results are described qualitatively without convergence or reproducibility metrics. The link between the in silico conformational changes and the functional transcriptional data is correlative rather than mechanistic. The manuscript is promising but does not currently establish the case from the provided evidence.
- **Who would be interested in the results, and why** Researchers studying nuclear receptor signaling, particularly those focused on FXR biology, intrinsically disordered protein domains, and coregulator recruitment mechanisms. The identification of a new interaction motif may also interest structural biologists and computational biologists studying protein-protein interactions in transcriptional regulation.
- **Major strengths** 1) The question is timely and addresses a clear gap in FXR biology. 2) The use of multiple orthogonal approaches (functional assays, M2H, MD simulations) is commendable. 3) The identification of a novel SXXLF motif, if validated, would be a meaningful contribution. 4) The discussion of potential coregulator specificity (SRC-1/SRC-2 vs. p300) adds nuance.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative data), R1-M2 (MD simulation rigor), R1-M3 (M2H assay interpretation), R1-M4 (AlphaFold3 model validation), R1-M5 (causal link between mutation and transcriptional effects).
- **Assessment against Nature-style criteria**  
  *Originality*: The work is original in identifying a novel SXXLF motif in FXR, which has not been previously reported. However, the concept of NTD-mediated interdomain and coregulator interactions is established in other nuclear receptors, so the novelty is incremental rather than paradigm-shifting.  
  *Scientific importance*: The findings could be important for understanding FXR regulation and the general principles of NTD function in nuclear receptors. However, the importance is contingent on robust validation of the motif's functional relevance, which is not fully demonstrated here.  
  *Interdisciplinary readership*: The topic will appeal to molecular endocrinologists, structural biologists, and computational biologists. The breadth of interest is moderate; it is unlikely to attract a wide audience beyond these fields.  
  *Technical soundness*: The experimental design is reasonable, but the lack of quantitative data and incomplete MD simulation reporting undermine confidence. The M2H assay interpretation requires additional controls.  
  *Readability for nonspecialists*: The manuscript is generally well-written and accessible, though some sections (e.g., MD simulation details) assume familiarity with specialized terminology. The abstract is clear.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the core claims require substantial additional data and analysis before they can be considered supported.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence completeness  
- **Claim pointer** The authors claim that the NTD interacts with the LBD and coregulators, and that the SENLF motif mediates these interactions, based on M2H assays and luciferase reporter assays.  
- **Evidence pointer** Figures 1B, 1D, 3D, 3F; location not provided for numerical values  
- **Concern** The manuscript does not provide any numerical data, error bars, or statistical test results in the text. All quantitative claims (e.g., ">50% decrease," "significant increase in fold-change") are presented without the underlying values. This makes it impossible to assess the magnitude, reproducibility, or statistical significance of the reported effects.  
- **Why it matters** Without quantitative data, the reader cannot evaluate whether the observed differences are biologically meaningful or within experimental noise. This is a fundamental requirement for establishing the claims.  
- **Resolution test** Provide the actual fold-change values, standard deviations, and p-values for all reported comparisons in the main text or supplementary materials. Include the number of independent biological replicates.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors state that MD simulations reveal "large changes in conformational and allosteric coupling" upon SENAA mutation, and that specific inter-residue distances change significantly (e.g., G27-Q313 from 18.7 Å to 37.2 Å).  
- **Evidence pointer** Figure 4; Methods section "Molecular dynamics simulations"  
- **Concern** The MD simulation methodology is described but key details are missing. No convergence metrics (e.g., RMSD over time, block averaging), force field validation, or system size information are provided. The claim of "significant" distance changes is based on a t-test, but the number of independent samples (frames) and the autocorrelation of MD data are not addressed. The use of AlphaFold3 models as starting structures without experimental validation is a concern, as the NTD is predicted to be disordered and its conformation in the model may not be representative.  
- **Why it matters** MD simulations are only meaningful if they are well-converged and the statistical analysis accounts for correlated data. Without this, the reported conformational changes may be artifacts of insufficient sampling or model bias.  
- **Resolution test** Provide RMSD and RMSF plots, convergence analysis, and details on how statistical significance was determined (e.g., block averaging, bootstrapping). Validate the AlphaFold3 model against known experimental structures of the DBD and LBD, and discuss the limitations of modeling a disordered NTD.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Experimental design  
- **Claim pointer** The authors conclude that the NTD competes with coregulators for LBD binding, based on the observation that NTD addition reduces LBD-coregulator interaction in M2H assays.  
- **Evidence pointer** Figure 3E (referenced in text); location not provided  
- **Concern** The M2H assay measures protein-protein interactions in a cellular context, but the interpretation that the NTD "interferes" with LBD-coregulator binding is not directly supported. The reduced signal could be due to steric hindrance, altered protein stability, or indirect effects on transcription. No control experiments (e.g., using a non-interacting protein as a competitor) are described.  
- **Why it matters** The conclusion that the NTD competes with coregulators is a key mechanistic claim. If the reduced M2H signal is due to nonspecific effects, the interpretation is invalid.  
- **Resolution test** Include control experiments with a non-interacting protein (e.g., GST or a scrambled peptide) to demonstrate specificity. Additionally, perform a dose-response experiment to show that increasing NTD concentration progressively reduces the LBD-coregulator interaction.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Model validation  
- **Claim pointer** The authors use AlphaFold3 models to predict the structure of full-length FXR and identify the SENLF motif docking near the AF-2 surface.  
- **Evidence pointer** Figure 3B, 3C; Methods section "Molecular dynamics simulations"  
- **Concern** AlphaFold3 predictions for disordered regions, such as the NTD, are often unreliable. The authors do not provide confidence scores (e.g., pLDDT) or discuss the uncertainty in the predicted NTD conformation. The claim that SENLF "docks" near AF-2 is based on a single model and is not experimentally validated.  
- **Why it matters** If the predicted structure is incorrect, the subsequent MD simulations and the interpretation of the SENLF motif's location are built on a flawed foundation.  
- **Resolution test** Provide pLDDT scores for the NTD region and discuss the limitations of the model. Ideally, validate the NTD-LBD interaction using experimental methods such as cross-linking mass spectrometry or NMR.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Causal inference  
- **Claim pointer** The authors state that the SENAA mutation "induces large changes in conformational and allosteric coupling" and that this explains the reduced transcriptional activity.  
- **Evidence pointer** Figures 3D, 4; location not provided  
- **Concern** The link between the in silico conformational changes and the functional transcriptional data is correlative. The authors do not demonstrate that the conformational changes directly cause the reduced activity. Other explanations, such as altered protein stability, changes in DNA binding, or effects on coregulator recruitment, are not ruled out.  
- **Why it matters** The manuscript's central claim is that the SENLF motif mediates function through specific conformational and allosteric effects. Without a direct mechanistic link, the claim is not established.  
- **Resolution test** Perform additional experiments to test the mechanism, such as measuring NTD-LBD binding affinity directly (e.g., ITC or SPR), assessing protein stability (e.g., thermal shift assays), or using FRET to monitor conformational changes in live cells.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The abstract states "A novel SXXLF motif" but the motif is later identified as SENLF. The abstract should specify the exact sequence to avoid ambiguity.  
- **Required correction** Change to "A novel SXXLF motif (SENLF)" in the abstract.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Experimental detail  
- **Affected element** Methods, Luciferase assays  
- **Evidence pointer** Methods section "Transfection and dual-luciferase assay"  
- **Issue** The ligand concentrations used (10 μM or 100 μM) are not specified for each experiment. Different ligands may have different potencies, and the choice of concentration could affect the results.  
- **Required correction** Specify the concentration used for each ligand in each experiment, and justify the choice based on published EC50 values.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical reporting  
- **Affected element** Results, Figure 1B  
- **Evidence pointer** Figure 1B; location not provided  
- **Issue** The text states "a significant decrease in response (> 50%)" but does not report the exact p-values or the statistical test used for this specific comparison.  
- **Required correction** Report the p-values and the specific statistical test for each comparison in the figure legends or text.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Results, "Peptides from nuclear receptor coregulators interact with the FXR NTD"  
- **Evidence pointer** Figure 3F; location not provided  
- **Issue** The authors state that "all three coregulators retain interactions with FXR regardless of NTD mutations," but the data are normalized to no-coregulator controls. This normalization may obscure differences in absolute activity levels.  
- **Required correction** Show both raw and normalized data to allow readers to assess the absolute effects of the mutations.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Technical detail  
- **Affected element** Methods, Molecular dynamics simulations  
- **Evidence pointer** Methods section "Molecular dynamics simulations"  
- **Issue** The simulation lengths for the heterodimer are described as "1.5 to 3.5 μs" per replica, but the total simulation time per system is not stated.  
- **Required correction** State the total simulation time per system (e.g., 4 replicas × 2.5 μs = 10 μs) and the number of replicas used for analysis.

## Risk / unsupported claims
- The claim that the SENLF motif "mediates interactions with both coregulators and the ligand binding domain" is not fully supported because the M2H data are not shown quantitatively and the AlphaFold3 model is not validated.
- The claim that the SENAA mutation "induces large changes in conformational and allosteric coupling" is based on MD simulations that lack convergence metrics and statistical rigor.
- The claim that the NTD "interferes" with LBD-coregulator interaction is not supported by control experiments.
- The claim that "SXXLF represents a novel recognition motif" is plausible but requires demonstration that the motif is functionally conserved or present in other nuclear receptors.
- The statement that "other parts of the NTD may facilitate the receptor's normal function" is speculative and not directly tested.