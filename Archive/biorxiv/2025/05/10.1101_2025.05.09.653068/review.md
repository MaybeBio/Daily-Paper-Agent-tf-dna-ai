## Review setup

- **Input scope** Full manuscript text (abstract, introduction, methodology, results, conclusions, acknowledgements, appendix) as provided by the user. No supplementary material, figures, or tables were included in the submission.
- **Assessment boundary** The assessment is limited to the scientific content, methodological validity, and presentation quality of the manuscript as described in the provided text. Claims regarding the performance of the Mpipi-Recharged model and the proposed thermodynamic integration methods are evaluated based on the evidence described in the text alone.
- **Shared manuscript claim summary** The authors propose two thermodynamic integration (TI) schemes, TI-Csat and TI-CC, to compute the saturation concentration (Csat) of phase-separating proteins. These methods are designed to overcome the limitations of direct coexistence (DC) simulations, which struggle to sample the extremely low protein concentrations in the dilute phase at sub-physiological temperatures. The methods are validated against experimental in vitro data for a range of intrinsically disordered and multi-domain proteins, including disease-associated RNA- and DNA-binding proteins and engineered mutants of hnRNPA1. The authors also benchmark their approach against a machine-learning predictor (CALVADOS2-based).
- **Visible evidence base** The manuscript text describes results from DC simulations, NVT simulations, and comparisons with experimental data. Specific figures (Fig. 1-5) and supplementary figures (Fig. S1, S3, S4) are referenced but not provided. The text includes quantitative claims about agreement with experimental data (e.g., "quantitatively match", "underestimates by ~2 orders of magnitude") but does not provide the actual numerical values or statistical measures within the provided text.
- **Missing materials affecting confidence** The figures, tables, and all supplementary material are not provided. This includes the actual phase diagrams, simulation details, error bars, and the specific numerical values of Csat for each protein. The absence of these materials prevents a full quantitative assessment of the claims. The specific equations (Eq. 1-20) are referenced but not fully displayed in the provided text, making it difficult to verify the derivations.

## Reviewer

- **Overall assessment** This manuscript addresses a significant and timely challenge in the field of biomolecular condensates: the accurate and efficient computation of saturation concentrations, a key thermodynamic quantity that is often experimentally measured but computationally difficult to obtain. The proposed thermodynamic integration schemes are conceptually sound and represent a valuable methodological contribution. The validation against a diverse set of proteins and the comparison with a machine-learning predictor are strengths. However, the manuscript's impact is currently limited by the lack of detailed quantitative data in the provided text. The claims of accuracy and agreement with experiments are stated but not fully substantiated with the necessary numerical evidence, error analysis, and methodological details. The derivation of the TI-Csat method, while plausible, is not fully transparent from the text alone. The manuscript has the potential to be a strong contribution, but the current evidence base is insufficient to fully establish the robustness and general applicability of the proposed methods.
- **Who would be interested in the results, and why** Researchers in the fields of computational biophysics, molecular dynamics simulation, and the biology of phase separation would be the primary audience. Specifically, developers and users of coarse-grained models for proteins and nucleic acids would find the TI methods useful for validating and improving their models. Experimental biologists studying condensate formation would also be interested in a computational tool that can predict Csat and complement their in vitro measurements. The work is relevant to understanding the molecular mechanisms of diseases linked to aberrant phase transitions, such as ALS and FTD.
- **Major strengths**
    1.  The manuscript tackles a well-known and important problem: the computational determination of low saturation concentrations, which is a bottleneck for comparing simulations with experiments.
    2.  The proposed TI methods are a creative and physically grounded approach, leveraging thermodynamic principles to extrapolate from easily accessible high-temperature states to challenging low-temperature states.
    3.  The validation is performed on a wide range of biologically relevant proteins, including disease-associated mutants, which demonstrates the potential utility of the method.
    4.  The comparison with a machine-learning predictor provides a useful context and highlights the complementary strengths of physics-based and data-driven approaches.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The manuscript claims that the TI-Csat and TI-CC methods "enable accurate calculation of saturation concentrations" and that the results "quantitatively match" or "reasonably estimate" experimental data for various proteins.
    - **Evidence pointer** Results section A and B, Figures 2, 3, 4, and 5. Specific numerical values are not provided in the text.
    - **Concern** The central claim of the paper is the accuracy of the proposed methods. However, the provided text lacks the quantitative evidence needed to assess this claim. The manuscript states that results "remarkably agree" or "underestimate by ~2 orders of magnitude" but does not provide the actual Csat values, the simulation parameters, the error bars on the simulation data, or the statistical measures of agreement (e.g., R^2, mean absolute error) with the experimental data. Without this information, it is impossible to evaluate the true accuracy and reliability of the methods. The statement that the model "underestimates the saturation concentration by ~2 orders of magnitude" for some mutants is a significant discrepancy that is not adequately discussed or explained.
    - **Why it matters** The primary contribution of this work is a new computational method. The validity and utility of this method are entirely dependent on its demonstrated accuracy. Without a rigorous, quantitative comparison to experimental data, the core claim of the manuscript is not established. The reader cannot judge whether the method is a genuine improvement over existing approaches or if its predictions are reliable enough for practical use.
    - **Resolution test** The authors must provide a table or figure with the numerical values of Csat (both simulated and experimental) for all proteins studied, along with the associated uncertainties (e.g., standard deviation or confidence intervals) for the simulation results. They should also provide a quantitative measure of the agreement, such as the mean absolute error or a correlation coefficient, and a discussion of the discrepancies, particularly for the highly charged mutants.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The manuscript describes the derivation of the TI-Csat method, which relies on a series of thermodynamic integrations and the assumption of ideal gas behavior for the dilute phase.
    - **Evidence pointer** Methodology section A and the Appendix.
    - **Concern** The derivation of the TI-Csat method is not fully transparent from the provided text. The key equations (Eq. 1, and the equations in the Appendix) are referenced but not fully displayed or explained. The assumption that the pressure change is negligible along the isochoric path and that Δµ2 ≈ 0 for the condensed phase is a significant approximation that requires careful justification. The text mentions that "negative pressures can be obtained unless the sampling is large," which raises concerns about the robustness of the method. The conditions under which these approximations hold are not clearly defined.
    - **Why it matters** The scientific validity of the proposed method rests on the correctness of its derivation and the validity of its underlying assumptions. If the derivation is flawed or the assumptions are not generally applicable, the method may produce inaccurate results. A reader must be able to follow the derivation and understand the limitations of the method to use it correctly.
    - **Resolution test** The authors should present the full derivation of the TI-Csat method in a clear and step-by-step manner, including all the relevant equations. They should explicitly state and justify all assumptions, particularly the ideal gas approximation and the neglect of pressure-volume work. They should also discuss the limitations of these assumptions and provide guidelines for when the method is expected to be valid.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific importance / Interdisciplinary readership
    - **Claim pointer** The manuscript claims that the proposed methods "offer a robust, physically grounded framework for improving and validating coarse-grained models of biomolecular phase behaviour."
    - **Evidence pointer** Conclusions section.
    - **Concern** While the methods are useful for computing Csat, the manuscript does not fully demonstrate how they can be used to "improve and validate" coarse-grained models. The validation is one-directional: the model is used to predict Csat and compared to experiments. The manuscript does not show an example of how the discrepancy between predicted and experimental Csat could be used to refine the model parameters or identify deficiencies in the model. The discussion of the failure for highly charged mutants (e.g., +7R, +8D) is brief and does not provide a clear path for model improvement.
    - **Why it matters** The broader impact of the work would be significantly enhanced if it could demonstrate a clear workflow for model improvement. This would make the methods not just a tool for prediction, but an integral part of a model development cycle. This would appeal to a wider audience of model developers and users.
    - **Resolution test** The authors could add a section or discussion on how the discrepancies between their predictions and experimental data can be used to identify specific interaction parameters (e.g., electrostatic scaling) that need refinement. A case study showing a model parameter being adjusted based on the TI-Csat results to improve agreement would be a powerful demonstration.

- **Minor Comments**

    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Readability for nonspecialists
    - **Affected element** Introduction and Methodology
    - **Evidence pointer** Introduction, Methodology section A and B.
    - **Issue** The manuscript uses several terms and concepts that may be unfamiliar to a broader scientific audience, such as "direct coexistence simulations," "binodal," and "thermodynamic integration." While these are standard in the field, a brief, intuitive explanation of these concepts would improve accessibility.
    - **Required correction** Add a short paragraph in the introduction or methodology that explains the concept of a phase diagram, the difficulty of sampling the dilute phase, and the basic idea behind thermodynamic integration in a way that is accessible to a non-specialist.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Methodology section B
    - **Evidence pointer** Methodology section B, Eq. 3.
    - **Issue** The manuscript states that the enthalpy difference can be approximated by the internal energy difference (H ≈ U) because the pV term is negligible. While this is a common approximation, it is not always valid, especially for condensed phases. The authors should provide a more detailed justification for this approximation in the context of their simulations.
    - **Required correction** Provide a brief justification for neglecting the pV term, perhaps by estimating the magnitude of the pressure in the simulation and comparing the pV term to the internal energy.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Results section B, Figure 3
    - **Evidence pointer** Results section B, Figure 3.
    - **Issue** The manuscript mentions that the model "underestimates the saturation concentration by ~2 orders of magnitude" for some highly charged mutants. This is a large error, and the explanation that it is due to the "implicit treatment of ions and water" is plausible but not fully explored.
    - **Required correction** The authors should expand the discussion on the limitations of the model for highly charged sequences. They could discuss the specific physical interactions that are likely misrepresented and suggest potential improvements to the model, such as a more detailed treatment of salt ions.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Readability for nonspecialists
    - **Affected element** Results section C, Figure 5
    - **Evidence pointer** Results section C, Figure 5.
    - **Issue** The comparison with the machine-learning predictor is interesting, but the text does not provide enough detail on the predictor itself. It is unclear what features the predictor uses, how it was trained, and what its limitations are.
    - **Required correction** Provide a brief description of the machine-learning predictor, including its input features, training data, and known limitations. This will help the reader understand the context of the comparison.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of quantitative data to support the central claim of accuracy.
    - R1-M2: Lack of transparency in the derivation of the TI-Csat method and justification of its key assumptions.

- **Assessment against Nature-style criteria**
    - **Originality** The work is original. While thermodynamic integration is a standard technique, its specific application to compute saturation concentrations for biomolecular condensates using coarse-grained models is a novel and valuable contribution.
    - **Scientific importance** The work is of high importance to the field of biomolecular condensates. The ability to accurately and efficiently compute Csat is crucial for validating models and understanding the thermodynamic drivers of phase separation. The method has the potential to become a standard tool.
    - **Interdisciplinary readership** The work is primarily of interest to computational biophysicists, physical chemists, and molecular biologists. The topic is specific, and the methods are technical, which may limit its appeal to a broader interdisciplinary audience. However, the implications for understanding disease mechanisms could attract interest from the biomedical community.
    - **Technical soundness** The conceptual basis of the methods is sound, but the technical soundness cannot be fully assessed due to the lack of quantitative data and the incomplete presentation of the derivation. The significant errors for some mutants also raise concerns about the general applicability of the model.
    - **Readability for nonspecialists** The manuscript is written in a technical style that is appropriate for a specialist audience. However, the abstract and introduction could be slightly more accessible to a broader scientific readership. The lack of a clear, intuitive explanation of the methods is a minor weakness.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a novel and potentially very useful methodological advance. The core idea is sound and the validation, while not fully presented, suggests the method works for a range of proteins. However, the manuscript cannot be accepted in its current form. The authors must provide the full quantitative data, a transparent derivation, and a more thorough discussion of the method's limitations. Once these concerns are addressed, the manuscript would be a strong candidate for publication.