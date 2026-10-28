## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no figures, tables, methods details, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present two thermodynamic integration (TI) schemes that, combined with Direct Coexistence simulations and the Mpipi-Recharged coarse-grained model, enable accurate calculation of saturation concentrations and phase diagrams for phase-separating proteins, including intrinsically disordered and multidomain proteins, and compare these methods against a machine-learning predictor.
- **Visible evidence base** Abstract text only; no quantitative results, error bars, comparison tables, or methodological derivations are visible
- **Missing materials affecting confidence** Full methods, simulation parameters, convergence criteria, force field details, benchmark datasets, experimental reference values, machine-learning model architecture and training data, and all figures and tables

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable methodological advance for computing saturation concentrations in biomolecular phase separation, addressing a recognized limitation of Direct Coexistence simulations. The proposed combination of thermodynamic integration with existing coarse-grained models is conceptually sound and likely of interest to the simulation community. However, the abstract provides no quantitative evidence to support the central claims of accuracy, broad applicability, or superiority over existing approaches. The comparison with a machine-learning predictor is mentioned but not substantiated with any performance metrics. The case for the method's utility and reliability is therefore not established from the supplied material.
- **Who would be interested in the results, and why** Computational biophysicists and physical chemists studying biomolecular condensates, developers of coarse-grained models for intrinsically disordered proteins, and researchers seeking quantitative links between simulation and experiment for phase behavior. The work may also interest experimentalists who use simulation predictions to guide in vitro measurements of saturation concentrations.
- **Major strengths** The problem addressed is well-defined and practically important. The proposed approach of using thermodynamic integration to overcome the statistical limitations of Direct Coexistence simulations is physically motivated and conceptually appropriate. The stated scope, covering both intrinsically disordered and multidomain proteins including disease-associated systems, suggests broad potential applicability. The explicit comparison with a machine-learning predictor is a useful framing that acknowledges complementary approaches.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: The concept of using thermodynamic integration for saturation concentration calculations is not entirely new, but the specific combination with Direct Coexistence and the Mpipi-Recharged model may offer a novel practical contribution. Scientific importance: The ability to accurately compute saturation concentrations is central to quantitative understanding of phase separation, so the potential importance is high, but this is not demonstrated in the abstract. Interdisciplinary readership: The topic bridges biophysics, physical chemistry, and cell biology, and the abstract is written in a way that nonspecialists can follow the motivation. Technical soundness: Cannot be assessed from the abstract alone; no convergence criteria, error analysis, or validation details are provided. Readability for nonspecialists: The abstract is clear and well-structured, with key terms defined, though the technical content is necessarily dense.
- **Recommendation posture** Currently not established from the provided evidence. The abstract promises a methodological advance but provides no quantitative support. A supportive posture would require evidence of accuracy, robustness, and comparative performance.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that the TI methods "accurately estimate C(sat) for a broad range of intrinsically disordered and multidomain proteins."
- **Evidence pointer** Abstract only; no figures, tables, or numerical results provided
- **Concern** The central claim of accurate estimation is made without any quantitative data. No values of C(sat) are reported, no comparison with experimental measurements is shown, and no error estimates or statistical uncertainties are provided. The phrase "accurately estimate" is a strong claim that requires quantitative support.
- **Why it matters** The entire value proposition of the work rests on the accuracy of the computed saturation concentrations. Without numerical evidence, the reader cannot judge whether the method achieves its stated purpose or whether the accuracy is comparable to, better than, or worse than existing approaches.
- **Resolution test** Provide a table or figure comparing computed C(sat) values against experimental measurements for the full set of proteins studied, including error bars and a measure of agreement such as mean absolute error or correlation coefficient.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative validation
- **Claim pointer** The abstract states that the TI methods are compared against "a computationally efficient machine-learning predictor trained to estimate saturation concentrations at room temperature" and that "both approaches yield realistic predictions."
- **Evidence pointer** Abstract only; no details of the machine-learning model or comparison results provided
- **Concern** The comparison with the machine-learning predictor is mentioned but not substantiated. No performance metrics, benchmark datasets, or specific results of the comparison are given. The claim that both approaches yield "realistic predictions" is vague and unsupported.
- **Why it matters** A meaningful comparison with an alternative method is essential to position the proposed approach within the existing landscape. Without quantitative comparison, the reader cannot assess the relative merits of the TI methods versus the machine-learning approach, nor understand the trade-offs in accuracy, computational cost, and information content.
- **Resolution test** Present a direct comparison of C(sat) predictions from both methods against experimental data for the same protein set, including metrics such as root mean square error, Pearson correlation, and computational cost. Clarify the training data and architecture of the machine-learning model.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The abstract claims that "two independent thermodynamic integration (TI) schemes" are presented and that they enable "accurate calculation of saturation concentrations and phase diagrams."
- **Evidence pointer** Abstract only; no methodological details provided
- **Concern** The abstract does not describe the two TI schemes, their differences, the thermodynamic pathways used, the treatment of finite-size effects, or the criteria for convergence. Without this information, the methods cannot be evaluated for correctness, reproducibility, or generalizability.
- **Why it matters** Thermodynamic integration is a delicate technique that requires careful handling of integration paths, sampling, and error propagation. The lack of methodological detail prevents assessment of whether the schemes are theoretically sound and practically implementable by others.
- **Resolution test** Provide a full methods section describing both TI schemes, including the Hamiltonian perturbation, the number of intermediate states, the equilibration and production lengths, the treatment of electrostatic and hydrophobic interactions, and the convergence criteria. Include a validation of the TI results against an independent method for at least one test case.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Scope clarity
- **Affected element** Claim of "broad range" of proteins
- **Evidence pointer** Abstract only
- **Issue** The abstract states the methods work for "a broad range of intrinsically disordered and multidomain proteins" but does not specify how many proteins were tested, their sequence diversity, or the range of C(sat) values covered.
- **Required correction** Specify the number and types of proteins studied, and the range of C(sat) values explored, to support the claim of broad applicability.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Use of "accurate" and "realistic"
- **Evidence pointer** Abstract only
- **Issue** The terms "accurate" and "realistic" are used without operational definitions. It is unclear what level of agreement with experiment is considered acceptable or what constitutes a "realistic" prediction from the machine-learning model.
- **Required correction** Define quantitative criteria for accuracy, such as a target percentage error or a statistical measure of agreement, and state these criteria explicitly in the abstract or results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Contextual positioning
- **Affected element** Statement on limitations of Direct Coexistence
- **Evidence pointer** Abstract only
- **Issue** The abstract states that Direct Coexistence "yields poor estimates of the equilibrium concentrations of the dilute phase due to lack of statistics" but does not quantify this limitation or cite specific examples.
- **Required correction** Provide a brief quantitative illustration of the limitation, such as typical error magnitudes or a reference to a specific case, to justify the motivation for the new approach.

## Risk / unsupported claims
- The claim that the TI methods "accurately estimate C(sat)" is unsupported by any quantitative data in the abstract.
- The claim that "both approaches yield realistic predictions" in the comparison with the machine-learning predictor is unsupported by any performance metrics.
- The claim that the methods enable "accurate calculation of saturation concentrations and phase diagrams" across "a wide range of conditions" is not substantiated with any examples of conditions tested.
- The claim that the approach "offers a robust, physically grounded framework for improving and validating coarse-grained models" is an assertion of broader impact that is not evidenced in the abstract.
- The statement that the methods "facilitate direct comparison with experimental measurements" is plausible but not demonstrated with any specific comparisons.