## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, theory, methods, results, discussion, conclusions, and supplementary information.
- **Assessment boundary** Scientific validity, technical soundness, methodological rigor, clarity of presentation, and significance of findings as presented in the provided manuscript.
- **Shared manuscript claim summary** The authors extend the open-source Perses package to perform relative alchemical binding free energy (RBFE) calculations for amino acid mutations in a model protein:protein complex (barnase:barstar). They identify sampling challenges, particularly for charge-changing mutations, attribute them to slow, mutation-specific degrees of freedom (sidechain torsions, interfacial contacts, waters), and demonstrate that longer simulations (50 ns/replica) with alchemical replica exchange (AREX) or alchemical replica exchange with solute tempering (AREST) yield accurate predictions (RMSE 1.61 kcal/mol) and correct sign classification for all mutations.
- **Visible evidence base** Abstract, Introduction, Theory, Methods, Results, Discussion, Conclusions, Supplementary Information (including detailed methods, figures, and tables).
- **Missing materials affecting confidence** The manuscript text provided is incomplete in places (e.g., equations are referenced but not fully displayed, some figure references are incomplete). The full set of supplementary figures and tables is not available for direct inspection. The "Detailed Methods" section is referenced but not fully included in the provided text. These omissions limit a complete assessment of technical details.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important challenge in the application of alchemical free energy calculations to protein:protein interactions. The work is methodologically sound, well-motivated, and provides a valuable practical framework for diagnosing and addressing sampling issues. The systematic analysis of a well-characterized model system (barnase:barstar) is appropriate, and the identification of charge-changing mutations as particularly problematic is a useful insight. The comparison of AREX and AREST is relevant, and the demonstration that sufficient simulation time can resolve most sampling issues is encouraging. However, the manuscript would be strengthened by a more detailed discussion of the limitations of the approach, a clearer presentation of the statistical analysis, and a more thorough comparison with existing literature on enhanced sampling for protein:protein systems. The generalizability of the findings to other complexes, as acknowledged by the authors, remains an open question.
- **Who would be interested in the results, and why** Computational chemists and biophysicists working on free energy calculations, particularly those applying these methods to protein:protein interactions or challenging alchemical transformations. The practical guidance on diagnosing sampling problems and the comparison of enhanced sampling methods will be of direct use to practitioners. The open-source implementation in Perses is a valuable resource for the community.
- **Major strengths**
    1.  The manuscript addresses a significant and under-explored challenge: the application of RBFE calculations to protein:protein complexes, which are more complex than typical small molecule:protein systems.
    2.  The systematic approach to identifying and characterizing sampling problems, using a combination of convergence analysis, restraint experiments, and correlation analysis with ∂U/∂λ, is rigorous and provides a practical template for other researchers.
    3.  The comparison of AREX and AREST under controlled conditions is valuable, and the finding that AREST offers efficiency gains for specific problematic mutations is a useful contribution.
    4.  The use of a well-characterized model system (barnase:barstar) with a diverse set of experimental mutations allows for a meaningful assessment of accuracy.
    5.  The open-source implementation and availability of all data and scripts is commendable and promotes reproducibility.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Technical soundness
        - **Claim pointer** The authors claim that "inadequate sampling can be attributed to slow degrees of freedom that are mutation-specific" and identify specific degrees of freedom (e.g., T42 χ1 angle, R87-D39 distance, neighboring waters) as being highly correlated with ∂U/∂λ.
        - **Evidence pointer** Results section 2, Figures 4 and 5.
        - **Concern** The correlation analysis identifies degrees of freedom that are correlated with ∂U/∂λ, but correlation does not necessarily imply causation. The authors do not demonstrate that actively enhancing sampling of these specific degrees of freedom (e.g., via biased simulations) would resolve the convergence issues. The analysis is diagnostic but not conclusive. The authors should temper their claims or provide additional evidence, such as biased simulations targeting the identified degrees of freedom, to confirm their role in the sampling problem.
        - **Why it matters** The central claim of the paper is that specific, mutation-dependent slow degrees of freedom cause the sampling problems. If this is not definitively established, the proposed diagnostic framework is less useful for guiding the selection of enhanced sampling methods.
        - **Resolution test** The authors could perform additional simulations where the identified slow degrees of freedom are deliberately enhanced (e.g., via Hamiltonian replica exchange with a bias on the specific torsion or distance) and show that this resolves the convergence issue. Alternatively, they could analyze whether the identified degrees of freedom are consistently slow across multiple independent simulations.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Scientific importance
        - **Claim pointer** The authors state that "we provide a model workflow for applying protein mutation free energy calculations to protein:protein complexes, and importantly, catalog the sampling challenges associated with these types of alchemical transformations."
        - **Evidence pointer** Conclusions, Discussion.
        - **Concern** The study is limited to a single protein:protein complex (barnase:barstar). While this is a well-chosen model system, the generalizability of the specific findings (e.g., that charge-changing mutations are always the most problematic, or that the identified types of slow degrees of freedom are universal) is not established. The authors acknowledge this limitation, but the significance of the work would be greatly enhanced by demonstrating the applicability of the diagnostic framework to at least one other, structurally distinct protein:protein complex.
        - **Why it matters** The value of the proposed workflow and the catalog of sampling challenges depends on their transferability to other systems of interest. Without a demonstration of generalizability, the impact of the work is limited to the specific system studied.
        - **Resolution test** The authors could apply their diagnostic workflow to a second, structurally distinct protein:protein complex (e.g., a complex with a different fold or binding mode) and show that the framework is effective in identifying sampling problems and that the types of slow degrees of freedom are similar or can be readily identified.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Technical soundness
        - **Claim pointer** The authors report that with 50 ns/replica AREX, "86% (24/28) of predictions are close to experiment and all mutations have the correct sign" and an RMSE of 1.61 kcal/mol.
        - **Evidence pointer** Results section 3, Figure 6D.
        - **Concern** The assessment of accuracy is based on a comparison with experimental ΔΔG values. The authors do not provide a detailed discussion of the uncertainty in the experimental measurements, nor do they compare their results with other computational methods or force fields. The RMSE of 1.61 kcal/mol is reasonable, but it is not clear how this compares to the expected accuracy of the underlying force field (ff14SB) and water model (TIP3P) for this type of system. A more critical evaluation of the accuracy, including a discussion of potential systematic errors, would strengthen the paper.
        - **Why it matters** The claim of "accurate predictions" is central to the paper's conclusion that the methods are ready for use. A more nuanced discussion of accuracy, including its limitations, is necessary for a fair assessment.
        - **Resolution test** The authors could compare their results with those obtained using a different force field (e.g., CHARMM36m) or a different water model. They could also perform a more detailed error analysis, separating statistical and systematic errors, and discuss the implications of their results for the field.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Readability for nonspecialists
        - **Affected element** Introduction, Theory
        - **Evidence pointer** Sections 1-3.
        - **Issue** The introduction and theory sections are dense and assume a high level of familiarity with alchemical free energy calculations. The distinction between AREX and AREST, and the specific advantages of AREST, could be explained more clearly for a broader audience.
        - **Required correction** Consider adding a brief, high-level summary of the key concepts (e.g., alchemical transformation, replica exchange, solute tempering) in plain language, perhaps with a simple schematic figure.
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Technical soundness
        - **Affected element** Methods, Results
        - **Evidence pointer** Section A.6, Figure 6.
        - **Issue** The manuscript mentions that "all-to-all replica swaps were attempted every cycle" but does not provide details on the acceptance rates or the efficiency of the replica exchange. This information is important for assessing the quality of the sampling.
        - **Required correction** Report the average acceptance rates for replica exchange moves for both AREX and AREST simulations.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Technical soundness
        - **Affected element** Results, Discussion
        - **Evidence pointer** Section 3, Figure 7.
        - **Issue** The comparison of AREX and AREST efficiency is based on the time to convergence of the ΔΔG prediction. However, the computational cost per unit of simulation time may differ between the two methods. A fairer comparison would be based on the total computational cost (e.g., GPU hours) required to achieve a given level of accuracy.
        - **Required correction** Discuss the computational cost of the two methods and, if possible, present the efficiency comparison in terms of total computational cost.
    - **R1-m4**
        - **Severity** Minor
        - **Axis** Scientific importance
        - **Affected element** Discussion
        - **Evidence pointer** Section 4.
        - **Concern** The discussion of the implications of the work for drug discovery is brief. The authors could elaborate on how the identified sampling challenges and the proposed workflow might be applied in a practical drug discovery setting, where many mutations need to be evaluated.
        - **Required correction** Add a paragraph in the discussion section specifically addressing the practical implications for drug discovery projects.
- **Technical failings that need to be addressed before the case is established**
    - The manuscript text is incomplete in the provided version, with missing equations and incomplete figure references. A complete version is required for a full technical assessment.
    - The "Detailed Methods" section is referenced but not fully provided, limiting the ability to assess the reproducibility of the simulations.
    - The statistical analysis of the results, particularly the calculation of confidence intervals and the handling of correlated data, is not fully described.
- **Assessment against Nature-style criteria**
    - **Originality** The work is original in its systematic focus on sampling challenges specific to protein:protein RBFE calculations. While the individual methods (AREX, AREST, correlation analysis) are not new, their application and combination for this specific problem, along with the practical diagnostic workflow, represents a novel contribution.
    - **Scientific importance** The work addresses a significant bottleneck in the application of a powerful computational method to an important class of biological systems. The findings have direct implications for practitioners and could help guide the development of more robust and efficient methods. The importance is somewhat limited by the single-system focus, but the framework is likely to be broadly applicable.
    - **Interdisciplinary readership** The work is primarily of interest to computational chemists, biophysicists, and structural biologists. The technical nature of the content may limit its accessibility to a broader biological audience, but the practical implications for understanding mutation effects on binding are relevant to a wider community.
    - **Technical soundness** The methodological approach is sound, and the use of a well-characterized model system is appropriate. The analysis is thorough, but the causal link between identified slow degrees of freedom and sampling problems is not definitively established. The accuracy assessment would benefit from a more critical discussion of potential systematic errors.
    - **Readability for nonspecialists** The manuscript is well-written but technically dense. The abstract and introduction are clear, but the theory and methods sections require significant expertise to follow. The figures are informative, but some are referenced incompletely in the provided text.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable and timely contribution to the field. The main technical concerns (R1-M1, R1-M2) are addressable through additional analysis or a more nuanced discussion. The minor comments are straightforward to address. The work is suitable for publication in a high-impact journal, provided the authors can strengthen the evidence for their central claims and provide a more complete and accessible presentation.

## Risk / unsupported claims
- The claim that "inadequate sampling can be attributed to slow degrees of freedom that are mutation-specific" is supported by correlation analysis but not by direct causal evidence.
- The claim that the proposed workflow is a "model workflow" for other protein:protein complexes is not supported by evidence from other systems.
- The claim that "accurate predictions" are achieved is based on a single force field and water model, and the potential for systematic errors is not fully explored.
- The generalizability of the finding that charge-changing mutations are particularly problematic is not established beyond the barnase:barstar system.