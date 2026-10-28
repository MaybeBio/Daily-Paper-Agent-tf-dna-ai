## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, and significance of the integrative modeling approach and conclusions presented
- **Shared manuscript claim summary** The authors present an integrative molecular model of TFIIH recruitment to the transcription-coupled repair (TCR) machinery, combining existing cryo-EM structures with AlphaFold predictions and molecular dynamics simulations. They propose that TFIIH is initially recruited in an open, repair-inhibited conformation, with STK19 serving as a central scaffolding protein. The model also addresses the roles of CRL4CSA-mediated ubiquitination of Rpb1 and UVSSA in facilitating TFIIH recruitment.
- **Visible evidence base** Full text with methods, figure legends, and supplementary figure descriptions; no raw data, PDB files, or simulation trajectories provided
- **Missing materials affecting confidence** Atomic coordinates of the integrative models, simulation input files and trajectories, AlphaFold prediction confidence metrics, validation statistics for the models, and experimental validation data

## Reviewer

- **Overall assessment** This manuscript presents a technically sophisticated integrative modeling study that addresses an important gap in our understanding of TCR assembly. The authors combine available structural data with state-of-the-art computational methods to generate testable hypotheses about TFIIH recruitment. However, the study is entirely computational, and the central claims rest on models that cannot be fully validated without experimental confirmation. The manuscript would be strengthened by clearer presentation of model confidence and limitations, and by explicit acknowledgment of the speculative nature of several key conclusions.

- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, transcription, and genome stability would find this work of interest. The proposed model offers a framework for understanding how TFIIH is recruited to stalled RNA polymerase II, which is a fundamental question in TCR biology. The study also provides a methodological template for integrative modeling of large macromolecular assemblies, which may interest computational biologists. Clinically oriented researchers studying Cockayne syndrome and UV-sensitive syndrome may also find the structural hypotheses relevant to understanding disease mechanisms.

- **Major strengths** The manuscript addresses a significant unresolved question in TCR biology. The integrative approach combining multiple structural datasets with advanced computational methods is appropriate and well-executed. The authors carefully incorporate known biochemical and structural constraints into their models. The use of multiple complementary computational techniques (AlphaFold2/3, Rosetta docking, MD simulations, PNEB path calculations, and network analysis) provides cross-validation of the proposed interactions. The discussion of the model's implications for TCR mechanism is thoughtful and generates clear, testable predictions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their integrative model of the TCR-TFIIH complex is "practically complete" and that STK19 serves as a "linchpin" of the assembly, with over 80% of its surface area buried in protein-protein interfaces.
- **Evidence pointer** Results sections "Molecular architecture of the nascent TCR-TFIIH complex" and "STK19 is the linchpin of the TCR-TFIIH complex"; Figures 1-3
- **Concern** The central structural claims rest entirely on computational predictions without experimental validation. While the authors note that cryo-EM structures of TCR-STK19 complexes were published during review, they do not provide a detailed comparison between their model and these experimentally determined structures. The claim that STK19 is a "linchpin" with >80% buried surface area is a strong statement that requires experimental support. The authors should provide a systematic comparison of their model with the newly available cryo-EM structures, and temper their claims accordingly if discrepancies exist.
- **Why it matters** The central thesis of the paper is that STK19 is the organizing center of the TCR-TFIIH assembly. If the experimentally determined structures show different interfaces or positioning, the model's conclusions would be substantially weakened. The lack of detailed comparison with available experimental data undermines confidence in the model's accuracy.
- **Resolution test** Provide a detailed structural comparison between the integrative model and the published cryo-EM structures of TCR-STK19 complexes, including RMSD calculations and interface analysis. If discrepancies exist, discuss their implications and revise the claims accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their MD simulations reveal the "interplay of segmental DDB1 flexibility, continuous Cullin4A flexibility, and the key role of ELOF1 for Pol II ubiquitination that enables TCR."
- **Evidence pointer** Results section "ELOF1 arrests the Cullin4A arm rotation to promote specific Rpb1-K1268 ubiquitin transfer"; Figure 5
- **Concern** The MD simulation methodology and validation are insufficiently described. The authors state that simulations were performed for 1 microsecond, but do not provide details on system size, number of replicates, convergence criteria, or error analysis. The PNEB calculations are described only briefly, and the statistical significance of the observed conformational differences between states is not established. The claim that ELOF1 "arrests" Cullin4A rotation is based on a single simulation trajectory and requires replicate simulations to establish robustness.
- **Why it matters** The dynamic conclusions are a key part of the paper's contribution. Without proper statistical treatment and convergence analysis, the reader cannot assess whether the observed conformational preferences are meaningful or simply simulation artifacts. The mechanistic claims about ELOF1 function have implications for understanding TCR regulation.
- **Resolution test** Provide details on the number of independent simulations performed, convergence metrics (e.g., RMSD stabilization, principal component analysis), and statistical analysis of the observed conformational differences. If only single trajectories were run, acknowledge this limitation and temper the strength of the dynamic claims.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors propose a detailed mechanism for TFIIH recruitment involving "an open repair-inhibited conformation, which requires subsequent CAK module removal and conformational closure to process damaged DNA."
- **Evidence base** Results section "Molecular architecture of the nascent TCR-TFIIH complex"; Discussion; Figure 8
- **Concern** The proposed conformational transition from an open to a closed TFIIH state during TCR is presented as a central mechanistic insight, but the evidence supporting this transition is indirect. The authors compare their model to the closed TFIIH conformation from GG-NER, but do not demonstrate that such a transition is thermodynamically feasible or kinetically accessible in the context of the TCR complex. The role of CAK removal in this process is speculative and not supported by direct simulation or experimental data.
- **Why it matters** The proposed mechanism has implications for understanding how TCR is regulated and how mutations in TCR factors lead to disease. If the conformational transition is not supported by evidence, the mechanistic model loses its predictive power.
- **Resolution test** Provide additional simulations or free energy calculations that support the feasibility of the proposed conformational transition. Alternatively, clearly label this aspect of the model as a hypothesis requiring experimental testing, and discuss alternative models.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "AlphaFold2 (but not AlphaFold3) predicts STK19 binding to the back side of XPD near the interface of the Arch and Fe-S domains" and that this interaction is mutually exclusive with the VHS-STK19 interaction.
- **Evidence base** Results section "STK19 is the linchpin of the TCR-TFIIH complex"; Figure 2e
- **Concern** The discrepancy between AlphaFold2 and AlphaFold3 predictions is mentioned but not explained or resolved. The authors dismiss the AlphaFold2 prediction of STK19-XPD binding based on incompatibility with the rest of the complex, but this is a circular argument if the rest of the complex was built using AlphaFold3. The possibility that STK19 could bind XPD in a different conformational state of the complex is not explored.
- **Why it matters** The choice of which AlphaFold prediction to trust fundamentally affects the model's architecture. If the AlphaFold2 prediction is correct, the proposed role of STK19 as a stable linchpin would need revision. The authors should address this discrepancy more rigorously.
- **Resolution test** Provide a more detailed analysis of why the AlphaFold2 prediction is less reliable in this case, including confidence metrics and comparison with experimental data. Discuss the possibility of alternative STK19 binding modes in different functional states.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence base** Abstract
- **Issue** The abstract states that the model shows "how TFIIH can be first recruited in an open repair-inhibited conformation," but the word "can" is ambiguous. It is unclear whether this is a prediction of the model or a statement of possibility.
- **Required correction** Clarify whether the open conformation is the predicted dominant state or one of several possible states.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Model building"
- **Evidence base** Methods
- **Issue** The methods describe the use of AlphaFold2/3, Rosetta, and Modeller, but do not provide version numbers, specific parameters, or command-line options used. This makes it difficult for others to reproduce the exact models.
- **Required correction** Provide detailed software versions and parameters, or reference a protocol paper or repository where these are documented.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Functional roles of CRL4CSA, ELOF1, and RNAPIIo ubiquitination in TCR-TFIIH recruitment"
- **Evidence base** Figure 4
- **Issue** The authors state that ELOF1 causes a ~7 Å shift and ~35° rotation of the VHS-CSA-DDB1 module, but do not provide error estimates for these values. It is unclear whether these changes are within the noise of the simulation.
- **Required correction** Provide error estimates or confidence intervals for the reported conformational changes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence base** Discussion
- **Issue** The discussion of the newly published cryo-EM structures is brief and does not clearly state whether the experimental structures support or contradict the authors' model.
- **Required correction** Expand this section to provide a more detailed comparison and explicitly state the level of agreement between the model and experimental data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Molecular dynamics"
- **Evidence base** Methods
- **Issue** The methods state that simulations were performed with NAMD3 using the Parm14SB and OL15 force fields, but do not mention the water model parameters or the specific NAMD3 version. The choice of force field combination (Parm14SB with OL15) is unusual and should be justified.
- **Required correction** Justify the force field choice and provide complete simulation parameters.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Covariance-based community network analysis"
- **Evidence base** Methods
- **Issue** The network analysis is described briefly, and the threshold for considering residues "in contact" (4.5 Å for 75% of the trajectory) is stated, but the sensitivity of the results to these thresholds is not discussed.
- **Required correction** Discuss the robustness of the network analysis results to changes in the contact thresholds.

## Risk / unsupported claims
- The claim that STK19 is a "linchpin" of the TCR-TFIIH complex with >80% buried surface area is unsupported by experimental validation and should be tempered.
- The proposed mechanism of TFIIH conformational transition from open to closed states during TCR is speculative and not directly supported by the simulations presented.
- The claim that ELOF1 "arrests" CullinA4 rotation to enable specific ubiquitination is based on limited simulation data and requires additional replicates and experimental support.
- The functional significance of the K1268 polyubiquitin chain and CSB UBD in "strengthening" the VHS-PHD interaction is inferred from the model but not directly tested.
- The statement that the model is "practically complete" overstates the confidence level given the entirely computational nature of the study and the lack of experimental validation.
- The discrepancy between AlphaFold2 and AlphaFold3 predictions for STK19-XPD binding is not resolved, and the dismissal of the AlphaFold2 prediction is not fully justified.
- The proposed role of STK19 in "facilitating XPD unwinding by guiding dsDNA toward the Pol II cleft" is speculative and not supported by functional data.
- The claim that the model provides "a roadmap for future experiments" is appropriate, but the authors should more clearly distinguish between well-supported aspects of the model and those that are purely hypothetical.