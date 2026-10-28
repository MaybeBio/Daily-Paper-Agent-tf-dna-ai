## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and results as presented in the provided text
- **Shared manuscript claim summary** The authors introduce NA-MPNN, a message-passing neural network that unifies protein, DNA, and RNA in a single graph representation, and claim it outperforms existing methods on RNA sequence design and fixed-dock protein-DNA specificity prediction
- **Visible evidence base** Text descriptions of architecture, datasets, evaluation protocols, and reported quantitative results; no figures, tables, or supplementary materials were available for inspection
- **Missing materials affecting confidence** All figures, tables, supplementary materials, code repository contents, and detailed benchmark outputs were not provided; this limits verification of quantitative claims and methodological details

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially impactful contribution to nucleic acid inverse folding by extending the well-established ProteinMPNN framework to a unified biopolymer representation. The core idea is conceptually sound and the reported results are promising. However, the absence of figures, tables, and supplementary materials in the provided text prevents full verification of the claims. The evaluation against baselines appears limited in scope, and several methodological details require clarification. The claim of state-of-the-art performance is not fully established from the evidence presented in the text alone.

- **Who would be interested in the results, and why** Researchers in RNA design, protein-DNA interaction prediction, and computational structural biology would find this work relevant. The unified architecture offers a practical tool for inverse folding across nucleic acid contexts, which could benefit efforts in synthetic biology, RNA therapeutics, and transcription factor engineering. The extension of a widely used method (ProteinMPNN) to nucleic acids also makes the work accessible to a broad computational biology audience.

- **Major strengths**
  1. The conceptual unification of RNA design and protein-DNA specificity prediction under a single inverse-folding framework is elegant and addresses a genuine gap in the field
  2. The architectural extension of ProteinMPNN is technically sound and leverages a proven design
  3. The inclusion of experimental validation through the OpenKnot challenge adds real-world credibility
  4. The data augmentation strategies for specificity training are thoughtful and address known challenges in learning position-specific preferences
  5. The manuscript is clearly written and accessible to nonspecialists

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "NA-MPNN outperforms previous methods on RNA sequence design and fixed-dock protein-DNA specificity prediction"
  - **Evidence pointer** Results section, Figures 2 and 4 (not visible in provided text)
  - **Concern** The central claim of superior performance is based on comparisons with only two baselines (gRNAde and RhoDesign) for RNA design and one baseline (DeepPBS) for specificity prediction. The text does not describe the statistical significance of the reported differences, the variance across runs, or the specific conditions under which each baseline was evaluated. Without a more comprehensive benchmark including additional state-of-the-art methods and proper statistical testing, the claim of "outperforms" is not fully substantiated.
  - **Why it matters** The primary contribution of the manuscript rests on this comparative claim. If the performance advantage is not robust or is within noise, the practical value of NA-MPNN is diminished.
  - **Resolution test** Provide a more extensive benchmark with additional baselines, report confidence intervals or significance tests for all comparisons, and describe the exact evaluation conditions for each method.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "the model attains higher predicted OpenKnot scores from RibonanzaNet, lower C1'-RMSD to the native structure after AlphaFold 3 prediction, and higher AlphaFold 3 pLDDT than either competitor method"
  - **Evidence pointer** Results section, Figure 2e-h (not visible in provided text)
  - **Concern** The evaluation on the pseudoknot subset relies heavily on predicted metrics (RibonanzaNet, AlphaFold 3) rather than direct experimental measurements. While the OpenKnot challenge provides experimental validation, the text does not clearly separate in silico predictions from experimental results in the main claims. The use of AlphaFold 3 as an evaluator is also potentially circular if the design method and the evaluator share similar training distributions.
  - **Why it matters** Predicted structural metrics can be biased or unreliable, and the manuscript's strongest claims of structural fidelity depend on these predictions. The distinction between predicted and experimentally validated performance must be explicit.
  - **Resolution test** Clearly separate predicted and experimental metrics in the results, discuss potential biases in using AlphaFold 3 as an evaluator, and provide the experimental OpenKnot scores as the primary evidence of structural fidelity.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** "a single model would have larger and more diverse datasets available for training and a considerably greater range of applicability"
  - **Evidence pointer** Introduction, Discussion
  - **Concern** The manuscript trains two separate models for the two tasks rather than a single unified model, which weakens the stated motivation of joint training benefits. The text does not demonstrate that the unified architecture provides advantages over task-specific models beyond the convenience of a shared codebase. The claimed benefits of "larger and more diverse datasets" are not empirically tested, as the two models are trained separately on different data.
  - **Why it matters** The stated motivation for the unified approach is not directly validated by the experimental design. If the two tasks do not benefit from joint training, the scientific novelty is reduced to an architectural extension rather than a conceptual advance.
  - **Resolution test** Either train a single model on both tasks and compare against the separate models, or explicitly discuss why separate training is necessary and what the unified architecture uniquely enables.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** "the model attains higher predicted OpenKnot scores from RibonanzaNet, lower C1'-RMSD to the native structure after AlphaFold 3 prediction, and higher AlphaFold 3 pLDDT than either competitor method"
  - **Evidence pointer** Results section, Figure 2e-h (not visible in provided text)
  - **Concern** The comparison with RhoDesign on the pseudoknot subset is potentially confounded by the fact that RhoDesign was run without secondary structure conditioning, as stated in the Methods. This may disadvantage RhoDesign, as secondary structure information is a known important input for RNA design. The text does not discuss whether this choice is fair or whether RhoDesign's performance would improve with this information.
  - **Why it matters** An unfair comparison undermines the validity of the performance claims and could mislead readers about the relative merits of the methods.
  - **Resolution test** Run RhoDesign with secondary structure conditioning as well, or provide a clear justification for why the comparison without it is appropriate.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Methods section, Loss equation
  - **Evidence pointer** Methods, Loss
  - **Issue** The loss equation is presented without a clear derivation or explanation of the mask term. The notation is dense and may be difficult for readers unfamiliar with the ProteinMPNN framework to follow.
  - **Required correction** Provide a brief textual explanation of each term in the loss equation, particularly the mask and the summation indices.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Data augmentation strategy
  - **Evidence pointer** Methods, Data Augmentation Details
  - **Issue** The augmentation that drops protein chains with 50% probability and assigns uniform PPMs to all nucleic acid positions is described, but the rationale for the specific probability value and the potential impact on training dynamics are not discussed.
  - **Required correction** Briefly justify the choice of 50% and discuss any sensitivity analysis performed on this hyperparameter.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion of limitations
  - **Evidence pointer** Discussion
  - **Issue** The Discussion does not address potential limitations of the approach, such as the reliance on backbone coordinates only, the handling of modified nucleotides, or the applicability to non-canonical nucleic acid structures.
  - **Required correction** Add a paragraph discussing limitations and potential avenues for future improvement.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Evaluation protocol for specificity
  - **Evidence pointer** Methods, Model Evaluation
  - **Issue** The text states that DeepPBS predictions are generated on the same distillation complexes, but does not specify whether DeepPBS was retrained or used as a pre-trained model. This affects the fairness of the comparison.
  - **Required correction** Clarify whether DeepPBS was used as provided by its authors or retrained on the same data.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract uses the term "fixed-dock" without defining it, which may confuse readers outside the protein-DNA interaction field.
  - **Required correction** Add a brief parenthetical definition, such as "fixed-dock (given a known complex structure)".

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Insufficient benchmarking and lack of statistical testing for the central performance claim
  - R1-M2: Over-reliance on predicted structural metrics without clear separation from experimental validation
  - R1-M4: Potentially unfair comparison with RhoDesign due to omitted secondary structure conditioning

- **Assessment against Nature-style criteria**
  - **Originality** The unified treatment of RNA and DNA inverse folding in a single architecture is a novel contribution, though it builds directly on established ProteinMPNN methods. The conceptual framing is original, but the incremental nature of the architectural changes limits the degree of novelty.
  - **Scientific importance** The work addresses a real need in nucleic acid design and protein-DNA interaction prediction. The potential impact on RNA therapeutics and transcription factor engineering is significant. However, the demonstrated advantages over existing methods are not fully established from the provided evidence.
  - **Interdisciplinary readership** The work bridges computational biology, structural biology, and synthetic biology. The unified framework and clear writing make it accessible to a broad audience, though some domain-specific terminology may require careful reading.
  - **Technical soundness** The architectural design is sound and follows established principles. The training protocols and data handling are generally rigorous. However, the evaluation methodology has gaps as noted in the major concerns, and the lack of visible figures and tables prevents full verification.
  - **Readability for nonspecialists** The manuscript is generally well-written and the conceptual framing is clear. The Methods section is dense but appropriate for a technical audience. Some terms could benefit from brief definitions.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the reported results are encouraging, but the central performance claims require stronger evidence through more comprehensive benchmarking, clearer separation of predicted versus experimental metrics, and fairer comparisons with baselines. The manuscript would be suitable for publication in a high-impact venue after these issues are addressed.

## Risk / unsupported claims
- The claim that NA-MPNN "outperforms previous methods" is not fully supported by the limited benchmarking described in the text
- The claim of "superior structural fidelity" based on predicted metrics (RibonananzaNet, AlphaFold 3) is not fully established without clear separation from experimental validation
- The stated motivation of "larger and more diverse datasets available for training" is not empirically demonstrated, as the two models are trained separately
- The claim that NA-MPNN "should be broadly useful" for various applications is speculative and not directly tested in this work
- The assertion that the unified architecture enables "additional applications" is plausible but not demonstrated with any preliminary results