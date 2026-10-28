## Review setup
- **Input scope** Full manuscript text (preprint, arXiv:2410.06211v1)
- **Assessment boundary** Scientific claims, methodology, experimental validation, and theoretical results as presented in the provided text
- **Shared manuscript claim summary** The authors propose ARGMINN, a mechanistically interpretable neural network architecture for regulatory genomics, which directly encodes motifs and their syntax in weights and activations, claims full expressivity, superior motif discovery and instance calling, robustness, and interpretable sequence generation
- **Visible evidence base** Main text sections 1-6, Appendix A (proofs), Appendix B (supplementary figures/tables descriptions), Appendix C (supplementary methods)
- **Missing materials affecting confidence** Actual figures and tables (only descriptions provided), supplementary figures S1-S11, supplementary tables S1-S5, quantitative performance numbers, code implementation details, hyperparameter values, dataset accession numbers

## Reviewer
- **Overall assessment** The manuscript presents a novel and potentially impactful architecture for interpretable regulatory genomics. The core idea of designing a network where motifs and syntax are directly readable is compelling and addresses a real limitation of post hoc interpretation methods. However, the current version has significant gaps in empirical validation, particularly the absence of quantitative results in the main text, and the theoretical claims require closer scrutiny regarding their practical implications. The expressivity proof is a strength, but its connection to real-world performance needs clarification. The robustness and generation experiments are promising but underreported. Overall, the work is of interest to the computational genomics and interpretable ML communities, but the evidence as presented is insufficient to fully establish the claimed advantages.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those developing or using deep learning models for TF binding prediction and motif discovery. Researchers in interpretable machine learning, especially those interested in mechanistic interpretability applied to scientific domains. The work may also interest experimental biologists seeking to understand regulatory syntax, as the architecture promises direct readability of learned rules.

- **Major strengths**
  1. Novel architecture design that directly encodes motifs and syntax, addressing a known limitation of post hoc interpretation methods
  2. Theoretical expressivity result (Theorem 1) with a constructive proof, showing the architecture can recognize any first-order-logic-definable motif configuration
  3. Comprehensive comparison against multiple baselines (standard CNN, ExplaiNN, MoRIS) across simulated and experimental datasets
  4. Demonstration of practical utility through QTL prioritization, robustness analysis, and interpretable sequence generation
  5. The filter-overlap regularizer is a simple yet effective contribution that could be applied to other architectures

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "ARGMINN identified known, biologically relevant motifs, and compared to other methods, it generally missed the fewest relevant motifs and discovered the fewest redundant motifs"
- **Evidence pointer** Section 4.1, Figure 2, Supplementary Figures S2-S5, Supplementary Table S1
- **Concern** The main text provides no quantitative results. All performance comparisons are described qualitatively ("generally missed the fewest", "far more similar", "consistently identified less-accurate"). Without actual numbers, effect sizes, or statistical significance tests, the claimed superiority over baselines cannot be evaluated. The supplementary tables are referenced but not included in the provided material. This is a critical gap for a paper whose central claim is empirical superiority.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Theoretical claim validation
- **Claim pointer** "ARGMINN is capable of learning any possible configuration of motifs—including positional and syntactic constraints—as long as the constraints are definable in first-order logic"
- **Evidence pointer** Section 5, Appendix A.1
- **Concern** The proof constructs a specific instantiation of ARGMINN with weights set to implement a given first-order logic sentence. However, the proof assumes the architecture can be constructed with exact knowledge of the target sentence. In practice, the network must learn these weights from data via gradient descent. The proof does not address whether the training dynamics can converge to such solutions, nor does it discuss the sample complexity or optimization landscape. The claim of "full expressivity" is therefore theoretical in a narrow sense and may not translate to practical learnability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Baseline fairness
- **Claim pointer** "ARGMINN surpasses ExplaiNN in both interpretability and expressivity"
- **Evidence pointer** Section 2, Section 4.1, Section 5.1, Supplementary Table S5
- **Concern** The comparison with ExplaiNN is central to the paper's claims, but the experimental setup may not be fully fair. The authors state that "all models were given the same number and size of convolutional filters, and the overall complexity/capacity of the models were kept as similar as possible." However, ARGMINN has additional components (memory stream, attention layers) that ExplaiNN lacks. The claim of "same complexity" needs clarification on what metric was used. Furthermore, the theoretical comparison (Corollary 1.1) shows ExplaiNN cannot represent certain configurations, but this is a representational limitation, not necessarily a practical one if such configurations are rare in real data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalization of robustness claims
- **Claim pointer** "ARGMINN's performance suffered the least, with a higher and tighter distribution of performance in general"
- **Evidence pointer** Section 4.4, Supplementary Figure S8a
- **Concern** The robustness analysis is limited to simulated datasets with GC content variation. The claim that ARGMINN is "robust to background variations" is only demonstrated for one type of variation. Real regulatory data contains many other sources of variation (e.g., sequence composition biases, repeat elements, chromatin state). The adversarial attack demonstration is also limited to a single dataset (SPI1) and a single attack strategy. The generalizability of these robustness claims is unclear.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Validation of generation claims
- **Claim pointer** "enables fully interpretable generation of novel functional sequences"
- **Evidence pointer** Section 4.5, Figure 5, Supplementary Figure S9
- **Concern** The interpretable generation experiment is validated only through in silico predictions from other models (ARGMINN itself, Borzoi, and fine-tuned Enformer). No experimental validation is provided. While in silico validation is a reasonable first step, the claim of generating "functional" sequences requires experimental confirmation. The statistical comparison with natural sequences (p = 0.75 for similarity) is interesting but does not establish functional equivalence.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.1, equation for activations
- **Evidence pointer** Section 3.1, "location not provided"
- **Issue** The equation for the convolutional activations is referenced but not shown in the provided text. The description of the filter-overlap regularization is also incomplete, with the loss function not fully specified.
- **Required correction** Provide the complete equations for the activation computation and the filter-overlap regularization loss.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.1, motif extraction procedure
- **Evidence pointer** Section 4.1, Appendix C.4
- **Issue** The procedure for extracting motifs from filters is described as "averaging test-set subsequences which highly activate the filter," but the threshold for "highly activate" is not specified. The criteria for dropping filters that are "never activated" is also vague.
- **Required correction** Specify the activation threshold and the criteria for considering a filter as "activated."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 4.2, motif instance calling
- **Evidence pointer** Section 4.2, Figure 3c, Supplementary Figure S6
- **Issue** The comparison of motif instance calling uses precision and recall, but no confidence intervals or statistical tests are reported. The claim that ARGMINN's instances are "far more accurate" needs statistical support.
- **Required correction** Report confidence intervals or perform statistical tests (e.g., bootstrap, permutation test) for the precision/recall comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.3, QTL prioritization
- **Evidence pointer** Section 4.3, Figure 4
- **Issue** The QTL prioritization experiment is described, but the baseline for comparison is not clearly stated. The text says "compared to other architectures," but does not specify which ones or how the comparison was made.
- **Required correction** Clearly state the baseline architectures and the evaluation metric used for QTL prioritization.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 5.1, experimental follow-up
- **Evidence pointer** Section 5.1
- **Issue** The simulated REST dataset is described, but the specific accuracy numbers (90.9% vs 73.4%) are given without context on the difficulty of the task or chance level. The significance of this difference is not tested.
- **Required correction** Provide chance-level accuracy and statistical significance for the REST experiment.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Appendix C.2, model architectures
- **Evidence pointer** Appendix C.2
- **Issue** The description of the standard CNN architecture is incomplete. The number of layers, filter sizes, and other hyperparameters are not fully specified. The ExplaiNN implementation is referenced but not described.
- **Required correction** Provide complete architecture specifications for all models used in the comparison.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.4, adversarial attacks
- **Evidence pointer** Section 4.4, Appendix C.4
- **Issue** The adversarial attack construction is described in the methods, but the specific attack parameters (e.g., number of iterations, perturbation budget) are not provided in the main text.
- **Required correction** Include the attack parameters in the main text or refer to a specific section in the appendix where they are fully specified.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 6, Discussion
- **Evidence pointer** Section 6
- **Issue** The discussion mentions that ARGMINN "did not outperform its non-MI counterparts" on experimental datasets, but this is stated without specific numbers. The reader cannot assess the magnitude of the performance gap.
- **Required correction** Provide the actual performance numbers for the experimental datasets in the main text or a summary table.

## Risk / unsupported claims
- The claim of "superior motif discovery" (Section 4.1) is not supported by quantitative evidence in the provided text
- The claim of "fully interpretable generation of novel functional sequences" (Section 4.5) is not supported by experimental validation
- The claim that ARGMINN is "robust to background variations" (Section 4.4) is only demonstrated for GC content variation on simulated data
- The theoretical expressivity result (Theorem 1) does not address practical learnability, so the claim of "full expressivity" may be misleading without qualification
- The comparison with ExplaiNN (Section 5.1) uses a single simulated dataset and does not establish general superiority
- The QTL prioritization results (Section 4.3) lack clear baseline comparison and statistical evaluation
- The claim that ARGMINN is "the most MI (yet still fully expressive) architecture for genome regulation" (Section 6) is not substantiated by a comprehensive comparison with all existing interpretable architectures