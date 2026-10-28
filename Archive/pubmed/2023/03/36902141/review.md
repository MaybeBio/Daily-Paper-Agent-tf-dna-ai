## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** The manuscript as provided, including abstract, introduction, results, discussion, methods, and conclusions
- **Shared manuscript claim summary** The authors use molecular dynamics simulations to characterize the interaction between PHD2 and HIF-1α/HIF-2α, propose that the PHD2 C-terminus may act as a molecular regulator of substrate specificity, and report that phosphorylation of Thr405 has limited structural impact but alters binding energy
- **Visible evidence base** Main text, Figures 1-8 (referenced), Tables 1-2 (referenced), Supplementary Tables S1-S4 (referenced)
- **Missing materials affecting confidence** Figures, tables, and supplementary materials are referenced but not provided; specific simulation parameters and force field validation details are incomplete; no raw trajectory data or convergence metrics are shown

## Reviewer
- **Overall assessment** This manuscript presents a computational study of PHD2 substrate specificity using MD simulations. The work addresses a relevant biological question, namely the molecular determinants of differential HIF-α isoform recognition by PHD2. The authors identify specific intermolecular interactions and propose a regulatory role for the PHD2 C-terminus. However, the study is entirely in silico and the conclusions rest on a homology model of the PHD2/HIF-2α complex, which introduces substantial uncertainty. The binding free energy calculations are based on single representative conformations per cluster, which may not adequately capture the thermodynamic ensemble. The statistical analysis is underpowered given the small number of replicas and conformations sampled. While the findings are potentially interesting, the evidence presented does not fully establish the central claims, particularly regarding the functional role of the C-terminus and the effect of Thr405 phosphorylation.

- **Who would be interested in the results, and why** Researchers studying hypoxia signaling, prolyl hydroxylase biology, and the molecular basis of HIF regulation would find this work relevant. Those interested in the structural determinants of enzyme-substrate specificity and the role of disordered regions in protein-protein interactions may also be interested. The potential implications for cancer biology, given the role of PHD2 in tumor progression, could attract a broader oncology-focused audience, though the in silico nature of the study limits immediate translational relevance.

- **Major strengths** The study addresses a biologically important question with potential therapeutic relevance. The use of multiple replicas for each system is appropriate. The authors consider post-translational modifications, adding a layer of regulatory complexity. The identification of specific residue-residue interactions provides testable hypotheses for experimental validation.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The homology model of the PHD2/HIF-2α complex is used as the basis for all subsequent simulations and interaction analyses
  - **Evidence pointer** Section 2.1, Section 4.1
  - **Concern** The homology model of the PHD2/HIF-2α complex is generated using the PHD2/HIF-1α crystal structure as a template, with the assumption that the proline position is preserved. However, the manuscript does not provide any validation of this model beyond a brief minimization and short equilibration. No assessment of model quality (e.g., Ramachandran plots, DOPE score comparison across models, or structural alignment metrics) is presented. The authors state that ten models were generated and the best one selected by DOPE score, but no details on the score distribution or the structural differences among models are given. Given that the central conclusions about C-terminus-mediated regulation and substrate discrimination depend critically on the accuracy of this model, the lack of rigorous model validation is a significant concern.
  - **Why it matters** If the homology model is inaccurate, all downstream analyses, including interaction networks, binding free energies, and conclusions about substrate specificity, could be artifacts of the model rather than genuine biological features. The scientific community requires confidence in structural models before accepting mechanistic claims derived from them.
  - **Resolution test** Provide a thorough validation of the homology model, including Ramachandran analysis, DOPE score comparison, structural superposition with the template, and ideally cross-validation against any available experimental data (e.g., mutagenesis studies). Show that the model is stable over extended simulation times and that key interactions are robust to model generation choices.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The binding free energy calculations are used to support claims about differential substrate affinity and the effect of Thr405 phosphorylation
  - **Evidence pointer** Section 2.4, Section 4.5, Table S1
  - **Concern** The MM/GBSA binding free energy calculations are performed on single representative conformations extracted from each cluster, rather than on ensembles of conformations. This approach is known to introduce significant variability and may not provide reliable estimates of binding affinity. The authors do not report standard deviations or confidence intervals for the calculated energies. Furthermore, the number of conformations used (six per system) is very small for a meaningful statistical comparison. The t-test results are therefore based on extremely limited samples, and the statistical power to detect true differences is questionable.
  - **Why it matters** The claim that PHD2 has greater affinity for HIF-1α than HIF-2α, and the claim that phosphorylation alters binding energy, rest on these calculations. If the energy estimates are unreliable, these conclusions are not supported. The manuscript does not provide sufficient evidence that the observed differences are robust to the choice of conformations or the calculation method.
  - **Resolution test** Perform binding free energy calculations on multiple conformations sampled throughout the trajectories (e.g., every 10 ns) and report mean values with standard deviations. Use multiple independent methods (e.g., MM/PBSA, umbrella sampling) to cross-validate the results. Provide a clear statistical framework that accounts for the small sample size, or increase the number of replicas and conformations analyzed.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors propose that the PHD2 C-terminus may act as a molecular regulator of enzyme activity and substrate specificity
  - **Evidence pointer** Section 2.2.1, Section 3, Figure 4
  - **Concern** The claim that the C-terminus acts as a molecular regulator is based on observations of conformational variability and occasional interactions with the substrate in MD simulations. However, the functional significance of these observations is not established. The authors do not provide any experimental validation, nor do they connect their findings to known functional data on PHD2 regulation. The observation that the C-terminus can adopt different conformations is not sufficient to support a regulatory role without evidence that these conformations affect enzymatic activity or substrate binding in a functionally meaningful way.
  - **Why it matters** The central novelty of the manuscript hinges on this proposed regulatory mechanism. Without functional evidence, the claim remains speculative. The manuscript would be strengthened by discussing how these findings align with or challenge existing experimental data on PHD2 regulation, and by proposing specific experimental tests that could validate the proposed mechanism.
  - **Resolution test** Provide a more nuanced discussion that clearly separates observations from interpretations. Suggest specific experimental approaches (e.g., mutagenesis of C-terminal residues, activity assays with truncated PHD2 variants) that could test the proposed regulatory role. Alternatively, temper the claim to reflect the speculative nature of the proposal.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that phosphorylation of Thr405 causes a variation in binding energy despite limited structural impact
  - **Evidence pointer** Section 2.2.2, Section 2.4, Figure 5, Figure 8
  - **Concern** The simulation of phosphorylated Thr405 is described, but the manuscript does not provide sufficient detail on how the phosphorylation was modeled. The authors state that the phosphate group was added using UCSF Chimera's Build Structure tool, but no information is given on the protonation state, the force field parameters for the phosphorylated residue, or the equilibration protocol. The 200 ns pre-equilibration followed by 1 µs production is described, but the convergence of the system is not demonstrated. The finding that phosphorylation has limited structural impact but alters binding energy is interesting, but the reliability of this result depends on the accuracy of the phosphorylation model.
  - **Why it matters** If the phosphorylation is not modeled accurately, the observed effects (or lack thereof) could be artifacts. The manuscript does not provide enough information for readers to assess the validity of the phosphorylation simulation.
  - **Resolution test** Provide detailed information on the phosphorylation modeling, including the force field parameters used, the protonation state, and any validation of the phosphorylated residue parameters. Show convergence of the simulations (e.g., RMSD over time, block averaging) and compare the structural and energetic properties of the phosphorylated and unphosphorylated systems over multiple independent replicas.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction
  - **Evidence pointer** Section 1
  - **Issue** The introduction assumes familiarity with the hypoxia signaling pathway and PHD biology. A brief explanation of the functional significance of PHD2 substrate specificity in the context of cancer would help nonspecialist readers understand the motivation for the study.
  - **Required correction** Add one or two sentences in the introduction that explicitly state why understanding PHD2 substrate specificity matters for cancer biology, beyond the general statement that hypoxia promotes tumor growth.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods
  - **Evidence pointer** Section 4.2
  - **Issue** The manuscript states that AKG parameters were generated with CHARMM-GUI and CGenFF and then modified by recalculating partial charges. The rationale for this modification and the validation of the final parameters are not described.
  - **Required correction** Provide a brief explanation of why the default CGenFF charges were deemed inadequate and how the recalculated charges were validated (e.g., comparison with quantum mechanical calculations or experimental data).

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Results
  - **Evidence pointer** Section 2.2.1, Table 1
  - **Issue** The interaction analysis identifies many specific residue-residue contacts, but the criteria for defining a "stable" or "relevant" interaction are not clearly stated. The reader cannot assess how the authors distinguished significant interactions from transient contacts.
  - **Required correction** Define the criteria used to classify interactions as stable or relevant (e.g., occupancy threshold, distance cutoff, persistence time) in the methods section.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Discussion
  - **Evidence pointer** Section 3
  - **Issue** The discussion of entropic effects and their contribution to binding energy differences is brief and may be difficult for nonspecialists to follow.
  - **Required correction** Expand the discussion of entropic contributions, explaining in accessible terms how conformational flexibility of the C-terminus could affect binding affinity.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods
  - **Evidence pointer** Section 4.5
  - **Issue** The manuscript does not specify the number of frames used for the MM/GBSA calculations or the dielectric constant and other parameters used in the HawkDock server.
  - **Required correction** Provide the specific parameters used for the MM/GBSA calculations, including the number of frames, the dielectric constant, and any other relevant settings.

## Risk / unsupported claims
- The claim that the PHD2 C-terminus acts as a molecular regulator of enzyme activity is not supported by functional evidence and remains speculative.
- The claim that phosphorylation of Thr405 causes a variation in binding energy is based on a single modeling approach without adequate validation of the phosphorylation parameters.
- The claim of greater affinity of PHD2 for HIF-1α compared to HIF-2α is supported by the calculations but the reliability of the MM/GBSA results is questionable given the small sample size and use of single conformations.
- The homology model of the PHD2/HIF-2α complex is not validated, and conclusions drawn from simulations of this model may not be reliable.
- The statistical significance of differences in binding energy between systems is based on very small sample sizes and may not be robust.