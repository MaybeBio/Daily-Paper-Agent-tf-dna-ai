## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, methodological rigor, and claims as presented in the provided text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors characterize the binding kinetics of cohesin and CTCF to chromatin in live developing zebrafish embryos using single-molecule imaging, and combine these measurements with polymer simulations to propose that increasing chromatin-bound fractions of these architectural proteins, driven by changes in association and dissociation rates, underlies the gradual emergence of chromatin architecture during embryogenesis.
- **Visible evidence base** Figures 1–4 (referenced but not shown), Supplementary Figures 1–10 (referenced but not shown), Supplementary Tables 12, 13, 15–22 (referenced but not shown), Methods section
- **Missing materials affecting confidence** All figures, supplementary figures, supplementary tables, and supplementary movies were not provided; this significantly limits the ability to assess data quality, statistical rigor, and the validity of the conclusions drawn from the experimental data

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question: how the kinetic properties of cohesin and CTCF binding to chromatin change during zebrafish embryogenesis and how these changes relate to the establishment of chromatin architecture. The use of single-molecule imaging in live embryos is technically ambitious and represents a valuable approach. However, the manuscript as presented has several significant issues. The results section is incomplete, with no actual data shown in the provided text, making it impossible to evaluate the robustness of the claims. The methods are described in detail, but key experimental validations (e.g., the extent of overexpression, the specificity of the mutants) are only briefly mentioned. The connection between the measured kinetic parameters and the polymer simulations is presented qualitatively, and the simulations themselves rely on several assumptions that are not fully justified. The claim that the observed changes in binding kinetics are "sufficient" to explain the increase in bound fractions is supported by a model, but the model's assumptions and limitations are not critically discussed. Overall, the work has potential, but the current presentation does not establish the case convincingly.

- **Who would be interested in the results, and why** Researchers in the fields of chromatin biology, developmental biology, and biophysics would be interested. Specifically, those studying the mechanisms of loop extrusion, the role of architectural proteins in genome organization, and the dynamics of transcription factor and structural protein binding in vivo would find the single-molecule data valuable. The work also speaks to the broader question of how nuclear organization is established during development, which is of interest to developmental biologists.

- **Major strengths**
  1. The use of single-molecule imaging in live zebrafish embryos is a significant technical achievement and provides data that are difficult to obtain with other methods.
  2. The combination of experimental measurements with polymer simulations is a powerful approach to connect molecular kinetics to higher-order chromatin organization.
  3. The study addresses a fundamental question about the molecular underpinnings of chromatin architecture formation during a critical developmental window.
  4. The use of multiple experimental perturbations (mutants, morpholinos, drugs) to dissect the contributions of different factors is a thoughtful experimental design.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality and completeness
  - **Claim pointer** The authors claim that the fraction of chromatin-bound cohesin and CTCF increases during development, and that this is due to changes in both association and dissociation rates.
  - **Evidence pointer** Results section, Figures 1d, 1e, 3f, 3g; location not provided
  - **Concern** The results section is presented as a narrative without any of the actual data (figures, tables, or quantitative values) being visible in the provided text. The claims about the magnitude of changes (e.g., "8.7-fold" increase for rad21, "1.5-fold" for CTCF) are stated without showing the underlying distributions, statistical tests, or error bars. It is impossible to assess the quality of the single-molecule data, the appropriateness of the fitting models, or the significance of the reported differences. The reader cannot verify that the "slow diffusion component" truly represents chromatin-bound molecules, or that the changes are not due to artifacts such as photobleaching or tracking errors.
  - **Why it matters** The central claims of the manuscript rest entirely on the quality and interpretation of the single-molecule data. Without seeing the data, the claims are unverifiable. The distinction between "short" and "long" binding events is critical, and the evidence for this distinction (e.g., the ITM data) must be shown to be robust.
  - **Resolution test** The authors must provide the actual data figures with clear statistical analysis. The fitting procedures for the diffusion models must be described in detail, including how the number of components was determined and how the "immobile" fraction was defined. The reproducibility of the measurements across embryos and cells should be demonstrated.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Model assumptions and validation
  - **Claim pointer** The authors claim that polymer simulations with experimentally derived parameters recapitulate the gradual emergence of chromatin architecture, and that the changes in binding kinetics are sufficient to explain the observed increase in bound fractions.
  - **Evidence pointer** Results section, Figure 4; Methods, Polymer simulations; location not provided
  - **Concern** The polymer simulation model is described, but the key parameters (e.g., the mapping of simulation time to real time, the processivity rate, the loading and unloading rates) are either assumed or derived from other systems (e.g., mouse embryonic stem cells). The manuscript does not provide a sensitivity analysis to show how robust the conclusions are to variations in these parameters. The claim that the simulations "recapitulate" experimental Hi-C data is only qualitative, and the specific metrics used for comparison are not defined. The model also appears to lack a detailed representation of CTCF-mediated stalling, which is a central feature of the loop extrusion model.
  - **Why it matters** The simulations are used to make a causal claim: that the measured kinetic changes are sufficient to drive the formation of chromatin architecture. If the model is not well-constrained or validated, this claim is not supported. The lack of a sensitivity analysis and quantitative comparison to experimental data weakens the conclusions.
  - **Resolution test** The authors should provide a more detailed description of the model parameters and their justification. A sensitivity analysis should be performed to show how the results change with different parameter values. The comparison to Hi-C data should be made quantitative (e.g., using metrics like insulation scores or contact probability decay). The model should explicitly incorporate CTCF stalling and test its effect.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of perturbation experiments
  - **Claim pointer** The authors claim that the long-bound fraction of cohesin is influenced by Wapl, CTCF, and RNA Polymerase II, and that these effects are compatible with their reported roles in loop extrusion.
  - **Evidence pointer** Results section, Figure 1i; location not provided
  - **Concern** The effects of Wapl, CTCF, and Nipbl perturbations are reported, but the data are not shown. The interpretation that the long-bound fraction represents loop-extruding cohesin is based on the observation that Wapl knockdown increases it and CTCF knockdown decreases it. However, the manuscript does not discuss potential off-target effects of the morpholinos, the efficiency of knockdown, or whether the observed changes are specific to the long-bound fraction or could reflect changes in the total protein levels or chromatin state. The effect of Nipbl on chromatin mobility is interpreted as evidence for loop extrusion, but alternative explanations (e.g., changes in chromatin compaction) are not considered.
  - **Why it matters** The perturbation experiments are key to linking the observed binding kinetics to the function of cohesin in loop extrusion. If the perturbations are not well-controlled or the interpretation is ambiguous, the link is weakened.
  - **Resolution test** The authors should show the data for the perturbation experiments, including controls. The efficiency and specificity of the morpholinos should be demonstrated. The discussion should address alternative interpretations of the results.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness of methods
  - **Affected element** Methods, Zebrafish husbandry
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The methods state that zebrafish were maintained following guidelines, but no details are given on the specific husbandry conditions (e.g., temperature, light cycle, feeding).
  - **Required correction** Provide standard husbandry details for reproducibility.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results, Figure 1c
  - **Evidence pointer** Results section; location not provided
  - **Issue** The manuscript refers to "mobile and immobile molecules" but does not define the threshold for immobility or how it was determined.
  - **Required correction** Define the criteria for classifying molecules as mobile or immobile.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results, Figures 1d, 1e, 3f, 3g
  - **Evidence pointer** Results section; location not provided
  - **Issue** The text reports fold-changes and values with error bars (e.g., "91 ± 47 nm") but does not state the number of embryos, cells, or molecules analyzed, nor the statistical tests used.
  - **Required correction** Report sample sizes and statistical methods for all quantitative claims.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section; location not provided
  - **Issue** The discussion does not address the potential limitations of the study, such as the overexpression of the HaloTag fusion proteins, the potential effects of the tags on protein function, or the challenges of imaging in live embryos (e.g., depth, motion).
  - **Required correction** Add a paragraph discussing the limitations of the approach and their potential impact on the conclusions.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Introduction, Discussion
  - **Evidence pointer** Introduction, Discussion; location not provided
  - **Issue** The manuscript does not discuss recent work on cohesin dynamics in other systems (e.g., mammalian cells) in sufficient detail, particularly regarding the residence times of cohesin and the role of Wapl.
  - **Required correction** Expand the discussion to place the findings in the context of existing literature on cohesin and CTCF dynamics.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The lack of visible data for the central claims is a critical failing. The manuscript cannot be evaluated without the figures and tables.
  - R1-M2: The polymer simulation model is not sufficiently validated or described to support the causal claims made.

- **Assessment against Nature-style criteria**
  - **Originality** The work is original in its application of single-molecule imaging to study cohesin and CTCF dynamics in a live developing vertebrate embryo. This is a technically challenging and relatively unexplored area.
  - **Scientific importance** The question of how chromatin architecture is established during development is of high importance. The findings could have implications for understanding gene regulation and developmental decisions. However, the importance is somewhat diminished by the lack of a clear mechanistic link between the observed kinetic changes and the functional consequences for gene expression.
  - **Interdisciplinary readership** The work is likely to appeal to a niche but significant audience at the interface of biophysics, chromatin biology, and developmental biology. The technical nature of the methods may limit its accessibility to a broader readership.
  - **Technical soundness** The technical approach is sound in principle, but the current presentation does not allow for a full assessment of the data quality and analysis. The polymer simulations are a useful addition but are not yet convincing.
  - **Readability for nonspecialists** The manuscript is written in a way that is generally accessible, but the results section is too brief and lacks the necessary detail to guide a nonspecialist through the findings. The methods are dense and would be challenging for a nonspecialist to follow.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a significant question with a promising approach, but the lack of visible data and the insufficiently validated model prevent a positive recommendation. The authors should be encouraged to resubmit a revised version that includes the full dataset, a more detailed description of the analysis, and a more rigorous validation of the simulations.

## Risk / unsupported claims
- The claim that the increase in chromatin-bound fractions of cohesin and CTCF is "sufficient" to explain the emergence of chromatin architecture is not supported by the evidence presented, as the model's assumptions are not fully validated.
- The claim that the long-bound fraction of cohesin represents loop-extruding cohesin is inferred from perturbation experiments but is not directly demonstrated.
- The claim that the changes in binding kinetics are due to changes in both association and dissociation rates is stated but not supported by visible data.
- The claim that the polymer simulations "recapitulate" experimental Hi-C data is qualitative and not quantitatively demonstrated.
- The claim that the short-bound fraction of cohesin and CTCF is not associated with their default chromatin-binding function is based on mutant studies but the data are not shown.