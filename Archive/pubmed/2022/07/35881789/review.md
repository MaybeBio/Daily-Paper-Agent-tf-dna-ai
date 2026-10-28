## Review setup
- **Input scope** Full manuscript text, including Significance statement, main text, Materials and Methods, and references to supplementary materials.
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and alignment with claims. No assessment of editorial fit or formatting.
- **Shared manuscript claim summary** The authors investigate the biophysics of transcription factor (TF) condensates of the nuclear progesterone receptor (PR) in living cells. They report that PR condensates grow via a Brownian coalescence mechanism at short times but reach a finite, nanoscale size at steady state, deviating from classical predictions. They propose a theoretical model incorporating stochastic particle unbinding to explain this arrested growth and validate it with simulations.
- **Visible evidence base** Main text figures (Figs. 1–4), supplementary figure references (SI Appendix, Figs. S1–S12), video references (Video S1), and a public repository link for data and code.
- **Missing materials affecting confidence** The full supplementary information, including all SI figures and notes, was not provided. Specific numerical values for key experimental results (e.g., fitted exponents, condensate radii distributions, statistical tests) are not fully detailed in the main text. The public repository was not accessed for verification.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and timely study on the dynamics of transcription factor condensates in living cells, combining advanced single-molecule imaging with theoretical modeling. The observation of arrested growth at the nanoscale, attributed to stochastic particle unbinding, is novel and significant. The work is generally well-structured and the conclusions are largely supported by the presented evidence. However, several technical aspects require clarification and additional analysis to fully solidify the claims, particularly regarding the quantitative rigor of the image analysis and the uniqueness of the proposed model.
- **Who would be interested in the results, and why** Researchers in the fields of biophysics, cell biology, and soft matter physics, specifically those studying phase separation, condensates, transcription regulation, and single-molecule tracking. The work provides a new mechanism for controlling condensate size, which is relevant for understanding cellular organization and gene regulation.
- **Major strengths**
    1.  The use of single-molecule tracking in living cells to study TF condensates is a significant technical achievement, providing dynamic information that is inaccessible to ensemble methods.
    2.  The identification of a sharp transition in PR mobility and diffusion behavior at a critical hormone concentration is a clear and interesting finding.
    3.  The combination of experimental observations with a theoretical model and simulations provides a strong framework for interpreting the data and generating testable predictions.
    4.  The proposed mechanism of particle unbinding controlling condensate size is a conceptually important contribution to the field.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** The claim that condensate growth follows a power law with exponent β = 0.3505 for the first 30 minutes and then reaches a steady-state plateau.
    - **Evidence pointer** Figure 3E, "Data analysis" section in Materials and Methods.
    - **Concern** The determination of the growth exponent β and the identification of the plateau rely on the analysis of 2D density maps generated from single-molecule localizations. The methodology for extracting condensate radii from these maps, the criteria for defining a "condensate" (e.g., minimum number of localizations, density threshold), and the statistical analysis (e.g., number of cells, number of condensates, error bars) are not fully described in the main text. The fit for β is stated but the uncertainty and goodness-of-fit are not provided. The identification of the plateau is based on visual inspection, and a more quantitative test (e.g., comparing a plateau model to a continued power-law growth) is needed.
    - **Why it matters** The growth exponent and the existence of a steady-state plateau are central to the paper's main claim that growth deviates from classical BMC. Without a rigorous and transparent analysis, the validity of this key observation is not fully established.
    - **Resolution test** Provide a detailed description of the image analysis pipeline, including all parameters and thresholds. Show the distribution of condensate radii at each time point with appropriate statistical measures (e.g., mean ± SEM, number of condensates). Provide the best-fit parameters for the power-law growth, including uncertainties, and perform a statistical test to confirm that the plateau model is a better fit than a continued power law for the later time points.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical Soundness
    - **Claim pointer** The claim that the theoretical model with stochastic particle unbinding (Pu > 0) can "fully recapitulate" the experimental data, including the growth dynamics, final condensate size, and diffusion coefficient distributions.
    - **Evidence pointer** Figure 4, "Theoretical model and simulations" section in Materials and Methods.
    - **Concern** The model is presented as an extension of BMC with a single additional parameter, Pu. While the simulations show that Pu > 0 leads to arrested growth, the manuscript does not demonstrate a quantitative, parameter-free comparison between the model predictions and the experimental data. For example, can the model predict the specific plateau radius (~70 nm) and the time at which it is reached, given the experimental parameters (e.g., particle number, diffusion coefficient, box size)? The comparison of diffusion coefficient histograms (Fig. 4E) is qualitative. A more rigorous fitting of the model to the experimental data, or a demonstration that the model's predictions are unique to this mechanism, would strengthen the claim.
    - **Why it matters** The theoretical model is a key part of the paper's contribution. If the model is not quantitatively validated against the experimental data, its explanatory power is limited, and alternative mechanisms for arrested growth (e.g., viscoelasticity of the environment, depletion of components) cannot be excluded.
    - **Resolution test** Perform a quantitative comparison between the model and experiment. This could involve simulating the system with parameters estimated from the experiments and comparing the predicted growth curves and size distributions to the measured ones. Alternatively, the authors could fit the model to the data to extract Pu and show that this value is consistent with the observed escape events. A discussion of alternative models and why they are less likely would also be valuable.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific Importance
    - **Claim pointer** The claim that the mechanism of particle unbinding provides "an exquisite control of condensate size in nonequilibrium systems such as living cells."
    - **Evidence pointer** Significance statement, Discussion.
    - **Concern** While the model demonstrates that Pu can control the final size, the manuscript does not provide direct experimental evidence that the cell actively regulates this parameter to control condensate size. The connection between the model parameter Pu and a specific biological or molecular process (e.g., post-translational modifications, chromatin state) is speculative. The claim of "exquisite control" is an interpretation that goes beyond the direct evidence presented.
    - **Why it matters** The broader significance of the work hinges on the idea that this mechanism is a biologically relevant control point. Without experimental evidence linking Pu to a regulatory pathway, the importance of the finding for cellular function remains a hypothesis.
    - **Resolution test** The authors should temper the claim in the Discussion or provide experimental evidence that altering a specific biological process (e.g., inhibiting PR DNA binding) changes the steady-state condensate size in a way that is consistent with a change in Pu. If this is not possible, the claim should be reframed as a testable prediction of the model.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Readability for Nonspecialists
    - **Affected element** Significance statement
    - **Evidence pointer** Significance statement
    - **Issue** The phrase "exquisite control" is somewhat informal and could be replaced with a more precise description, such as "precise regulation."
    - **Required correction** Consider revising the wording to "providing a mechanism for precise regulation of condensate size."
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** Figure 2D
    - **Evidence pointer** Figure 2D
    - **Issue** The separation of the two clusters by the SVM is stated, but the accuracy of the SVM classification is not reported.
    - **Required correction** Report the classification accuracy or cross-validation score for the SVM to support the claim of clear separation.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** "Data analysis" section
    - **Evidence pointer** "Data analysis" section in Materials and Methods.
    - **Issue** The method for detecting "escape events" is described as "challenging" but the specific criteria used to identify them are not defined.
    - **Required correction** Provide a clear definition of what constitutes an escape event in the trajectory analysis (e.g., a particle moving a certain distance away from a cluster).
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** "Theoretical model and simulations" section
    - **Evidence pointer** "Theoretical model and simulations" section in Materials and Methods.
    - **Issue** The model assumes a uniform escape probability for all particles in a condensate. The authors note this is negligible for small systems, but a brief justification or reference for this assumption would be helpful.
    - **Required correction** Add a sentence justifying the uniform escape assumption, perhaps by citing the small condensate size relative to the diffusion length.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of detailed statistical analysis for the growth exponent and plateau identification.
    - R1-M2: Lack of quantitative validation of the theoretical model against experimental data.
- **Assessment against Nature-style criteria**
    - **Originality** High. The application of single-molecule tracking to study the dynamics of TF condensates and the proposal of a new mechanism for size control are novel.
    - **Scientific importance** High. The work addresses a fundamental question in cell biology and biophysics regarding the regulation of condensate size, with implications for gene regulation.
    - **Interdisciplinary readership** High. The work bridges cell biology, biophysics, and soft matter physics, making it of interest to a broad audience.
    - **Technical soundness** Medium. The experimental techniques are state-of-the-art, but the quantitative rigor of the data analysis and model validation needs to be improved to fully support the claims.
    - **Readability for nonspecialists** Good. The manuscript is generally well-written and the concepts are explained clearly, though some sections could be more accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially significant, but the manuscript requires substantial revisions to provide a more rigorous quantitative analysis of the experimental data and a more robust validation of the theoretical model before the case is fully established.

## Risk / unsupported claims
- The claim that the model "fully recapitulates" the experimental data is not supported by the quantitative evidence presented.
- The claim of "exquisite control" of condensate size by the cell is an interpretation that is not directly supported by experimental evidence.
- The statement that the sharp transition in PR mobility is due to LLSP is an interpretation; while consistent with the data, other mechanisms (e.g., changes in chromatin structure) are not explicitly ruled out.
- The generalizability of the proposed mechanism to other TF condensates is speculative and not directly tested.