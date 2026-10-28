## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, and materials and methods
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and computational modeling as presented in the manuscript
- **Shared manuscript claim summary** The authors propose that HIV-1 Tat, when associated with syndecan-1 on lymphocytes, simultaneously activates lymphocytes in cis and endothelial cells in trans, promoting lymphocyte spreading and trans-endothelial migration. They further provide computational models of Tat/heparin interactions to support their proposed mechanism.
- **Visible evidence base** Figures 1–6 (described in text), Supplementary Figures S1–S2, Supplementary Table S1 (referenced but not provided)
- **Missing materials affecting confidence** Original Western blot images, full statistical reporting (only p < 0.05 stated), Supplementary Table S1 with quantitative activation data, raw computational docking scores and trajectories, and details of homology model validation

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and timely question in HIV-1 pathogenesis, namely how extracellular Tat promotes lymphocyte extravasation through coordinated signaling on both lymphocytes and endothelial cells. The experimental design is logical, and the use of Namalwa cell models expressing different HSPGs is appropriate for dissecting the roles of syndecan-1 versus glypican-1. However, several technical concerns limit the strength of the conclusions. The distinction between adhesion and spreading is not rigorously quantified, the specificity of some inhibitors is questionable, and the computational modeling, while interesting, is presented without sufficient validation or methodological detail to assess its reliability. The claim of a "two-way" activation mechanism is plausible but not fully established from the data presented.
- **Who would be interested in the results, and why** Researchers studying HIV-1 pathogenesis, particularly viral protein interactions with the host vasculature and immune cell trafficking. The work may also interest investigators focused on HSPG biology, integrin signaling, and the molecular mechanisms of leukocyte trans-endothelial migration. The computational models of Tat dimerization and heparin binding could be of interest to structural biologists studying viral protein-glycosaminoglycan interactions.
- **Major strengths** The study addresses a clinically relevant question with a well-designed cellular model system. The comparison between syndecan-1 and glypican-1 expressing cells provides a clean approach to dissect the roles of transmembrane versus GPI-anchored HSPGs. The inclusion of both experimental and computational approaches is commendable. The proposed model of in cis and in trans interactions is conceptually novel and provides a framework for future studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantification of spreading), R1-M2 (inhibitor specificity), R1-M3 (computational model validation), R1-M4 (endothelial activation specificity)
- **Assessment against Nature-style criteria** **Originality** The concept of Tat orchestrating simultaneous in cis and in trans signaling at the lymphocyte-endothelial interface is novel and extends previous work on Tat-HSPG interactions. However, the individual components (Tat binding to HSPGs, integrin engagement, VEGFR2 activation) have been previously described. **Scientific importance** The findings have potential implications for understanding HIV-1 dissemination and could inform therapeutic strategies targeting lymphocyte extravasation. However, the clinical relevance is not directly demonstrated. **Interdisciplinary readership** The work bridges virology, cell biology, and computational structural biology, which could appeal to a broad audience. **Technical soundness** Several technical concerns (see Major Concerns) need to be addressed. The experimental approaches are generally appropriate but require additional controls and quantification. **Readability for nonspecialists** The manuscript is clearly written and the figures are well-organized. The conceptual model in Figure 6 is helpful. However, some methodological details in the computational section may be challenging for non-specialists.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the experimental system is appropriate, but the current evidence does not fully establish the proposed two-way activation mechanism.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental quantification
- **Claim pointer** The authors claim that Tat induces lymphocyte spreading, demonstrated by a 1.5-fold increase in substrate contact area (Figure 1b) and that this spreading is dependent on syndecan-1.
- **Evidence pointer** Figure 1a–d, Section 2.1.1
- **Concern** The quantification of cell spreading is based on a single metric (substrate contact area) measured at a single time point. The authors do not provide details on how many cells were measured per condition, whether the analysis was blinded, or how the threshold for "spread" versus "non-spread" cells was determined. The representative images in Figure 1a show qualitative differences, but the quantitative analysis is not described in sufficient detail. Furthermore, the spreading assay appears to be performed at a single time point (2 hours), which may not capture the full dynamics of the spreading process.
- **Why it matters** The distinction between adhesion and spreading is central to the authors' claim that Tat induces a specific cellular response beyond mere attachment. Without rigorous quantification, it is difficult to assess whether the observed differences are biologically meaningful or within the range of experimental variability.
- **Resolution test** Provide detailed methodology for the spreading quantification, including the number of cells analyzed, the criteria for defining a spread cell, and whether the analysis was performed blinded. Include a time-course experiment to demonstrate that the observed spreading is a dynamic process. Show that the effect is dose-dependent with respect to Tat concentration.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Inhibitor specificity
- **Claim pointer** The authors claim that src, ERK1/2, FAK, and integrins are required for Tat-induced lymphocyte spreading, based on the effects of pharmacological inhibitors (PP2, PD98059, U0129, RGD).
- **Evidence pointer** Figure 1d, Section 2.1.1
- **Concern** The manuscript relies heavily on pharmacological inhibitors to establish the involvement of specific signaling pathways. However, the specificity of these inhibitors is not fully addressed. For example, PP2 is described as a src inhibitor, but it can also affect other kinases at the concentrations used. The authors do not provide dose-response curves for the inhibitors or demonstrate that the inhibitors do not affect cell viability or adhesion. The statement that "none of the inhibitors affects the number of SYN-NCs that adhere to Tat" is only shown in supplementary Figure S1, which is not provided for review. Additionally, the use of a single concentration for each inhibitor is insufficient to establish a specific effect.
- **Why it matters** The conclusion that specific signaling pathways are required for spreading depends on the specificity of the inhibitors used. If the inhibitors have off-target effects, the conclusions about the involvement of particular kinases may be incorrect.
- **Resolution test** Provide dose-response data for each inhibitor, demonstrating that the effect on spreading is concentration-dependent and occurs at concentrations that do not affect cell viability. Include genetic approaches (e.g., siRNA or dominant-negative constructs) to confirm the involvement of specific kinases. Show that the inhibitors do not affect the initial adhesion step, ideally with the supplementary data provided.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational model validation
- **Claim pointer** The authors claim that their computational models provide "a characterization at an atomic level of the binding modes of the Tat/heparin interaction" and that the models support the proposed mechanism of Tat dimerization and HSPG binding.
- **Evidence pointer** Section 2.2, Figure 5
- **Concern** The computational section is presented with insufficient methodological detail and validation. The homology model of Tat is generated from a template with 93% sequence identity, but no information is provided on the quality of the model (e.g., Ramachandran plot, RMSD to template). The protein-protein docking using ClusPro is described, but the scoring function and the criteria for selecting the best model are not specified. The heparin docking uses a "sliding window method" that is not described in sufficient detail to be reproduced. Most importantly, the computational predictions are not validated against any experimental data. For example, the authors do not test whether mutations in the predicted heparin-binding residues affect Tat binding to HSPGs or the functional outcomes described in the experimental sections.
- **Why it matters** The computational models are presented as supporting evidence for the proposed mechanism. Without proper validation, the models remain speculative and do not strengthen the experimental findings. The claim of "atomic level" characterization requires rigorous validation to be credible.
- **Resolution test** Provide detailed methods for the homology modeling, including model quality assessment. Describe the docking protocols in sufficient detail for reproduction. Validate the computational predictions experimentally, for example by testing Tat mutants with altered heparin-binding residues in the adhesion and spreading assays. Provide a comparison of the computational model with any available experimental structures of Tat or Tat-like proteins.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Endothelial activation specificity
- **Claim pointer** The authors claim that Tat presented by lymphocytes activates endothelial cells, as evidenced by VEGFR2, src, ERK1/2, and FAK phosphorylation, and that this leads to VE-cadherin reorganization and increased permeability.
- **Evidence pointer** Section 2.1.3, Figure 4
- **Concern** The experiments demonstrating endothelial activation use a co-culture system where Tat-presenting lymphocytes are seeded onto endothelial monolayers. However, it is not clear whether the observed endothelial responses are specifically due to Tat presented on the lymphocyte surface or could be due to soluble Tat released from the lymphocytes during the experiment. The authors do not include a control where soluble Tat is added directly to the endothelium at concentrations comparable to what might be released. Additionally, the VE-cadherin reorganization is assessed by immunofluorescence, but the quantification method is not described, and the images are not shown in the provided text.
- **Why it matters** The distinction between membrane-bound and soluble Tat is important for the proposed mechanism of in trans activation. If soluble Tat is responsible for the observed effects, the model of a stable in trans complex at the cell-cell interface would need to be revised.
- **Resolution test** Include a control where Tat-presenting lymphocytes are separated from the endothelium by a permeable membrane to assess the contribution of soluble Tat. Quantify VE-cadherin reorganization using a defined metric (e.g., junctional continuity index) with appropriate blinding. Measure the amount of Tat released from lymphocytes during the experiment to determine if soluble concentrations are sufficient to activate endothelial cells.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** All quantitative experiments
- **Evidence pointer** Section 2.1, Figure legends
- **Issue** The manuscript states that differences were considered significant when p < 0.05, but the actual p-values are not reported in the text or figure legends. The number of independent experiments (n) is not consistently stated.
- **Required correction** Report exact p-values for all statistical comparisons and state the number of independent experiments performed. Consider using effect sizes with confidence intervals.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1a, Figure 3a, Figure 4b
- **Evidence pointer** Section 2.1
- **Issue** The representative images for spreading, FAK localization, and VE-cadherin distribution are described but not shown in the provided text. The resolution and magnification of the images are not specified.
- **Required correction** Provide representative images with scale bars and specify the magnification. Consider including higher-magnification insets to better illustrate the described phenotypes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Experimental details
- **Affected element** Tat loading on lymphocytes
- **Evidence pointer** Section 2.1.2, Materials and Methods
- **Issue** The method for loading Tat onto lymphocytes is described briefly. It is unclear how much Tat remains associated with the cell surface versus being internalized, and whether the loading efficiency is consistent between experiments.
- **Required correction** Provide a quantitative assessment of Tat loading efficiency (e.g., flow cytometry or quantitative Western blot) and state the batch-to-batch variability.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Section 3
- **Issue** The discussion would benefit from a more thorough comparison with previous studies on Tat-induced endothelial permeability and lymphocyte migration, particularly those that have used different experimental models.
- **Required correction** Expand the discussion to place the findings in the context of the broader literature on Tat and endothelial dysfunction, noting where the current results agree or disagree with previous reports.

## Risk / unsupported claims
- The claim that Tat triggers "simultaneously" in cis and in trans activation is not directly demonstrated with temporal resolution. The experiments show that both events occur, but not that they are simultaneous.
- The claim that the computational model provides "atomic level" characterization is not supported by the level of validation presented.
- The statement that VE-cadherin reorganization leads to "consequent endothelial permeabilization" is inferred from the observed redistribution but not directly measured in the same experiment.
- The claim that the Tat/syndecan-1 complex "plays a central role" in orchestrating the multimeric complexes is not fully established, as the authors do not test whether disrupting this complex abolishes all the observed effects.
- The extrapolation from heparin (used in computational studies) to heparan sulfate chains of syndecan-1 is acknowledged by the authors but remains an assumption that is not experimentally validated.