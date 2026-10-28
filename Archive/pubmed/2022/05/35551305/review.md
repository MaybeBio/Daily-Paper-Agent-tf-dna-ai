## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present DeepSTARR, a deep-learning model that predicts enhancer activity from DNA sequence in Drosophila S2 cells, learns relevant TF motifs and higher-order syntax rules, validates these rules experimentally and in human cells, and enables de novo design of synthetic enhancers with desired activities.
- **Visible evidence base** Abstract text only; no quantitative results, model architecture details, dataset descriptions, or validation statistics are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, model architecture and training details, dataset composition and sizes, experimental validation protocols, statistical analyses, and code availability

## Reviewer
- **Overall assessment** The abstract describes a potentially impactful application of deep learning to enhancer biology, with claims spanning predictive modeling, mechanistic insight, cross-species generalization, and de novo design. However, the abstract alone provides insufficient quantitative detail to evaluate the strength of the evidence. The core claims are plausible but not verifiable from the supplied material. The work addresses a question of broad interest, and the stated results, if fully supported, would represent a meaningful advance. The assessment is therefore conditional on the full manuscript providing adequate technical and statistical support.

- **Who would be interested in the results, and why** Researchers in gene regulation, computational biology, and synthetic biology would be interested. The model's ability to predict enhancer activity and design synthetic enhancers has direct applications in understanding cis-regulatory logic and in engineering gene expression. The claimed cross-species generalization to human enhancers would extend relevance to human genetics and disease studies.

- **Major strengths** The abstract states a clear and ambitious goal, namely quantitative prediction and de novo design of enhancers. The combination of computational modeling with experimental validation, including testing of over 40,000 wildtype and mutant enhancers, suggests a substantial empirical effort. The claim that the model learns biologically interpretable features, such as TF motifs and syntax rules, bridges predictive performance with mechanistic understanding.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The model quantitatively predicts enhancer activity from DNA sequence.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract provides no quantitative performance metrics, such as correlation coefficients, area under the curve, or mean squared error, between predicted and measured enhancer activities. Without these, the accuracy and reliability of the predictions cannot be assessed.
  - **Why it matters** The central claim of the paper rests on the model's predictive accuracy. If performance is modest or only strong on a subset of sequences, the conclusions about learned rules and design capacity would be weakened.
  - **Resolution test** Provide performance metrics on held-out test sets, including separate evaluations for developmental and housekeeping enhancers, and compare against appropriate baseline models.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The model learned relevant TF motifs and higher-order syntax rules, including functionally nonequivalent instances of the same TF motif determined by flanking sequence and intermotif distances.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that these rules were learned and validated experimentally, but no details are given on how the rules were extracted from the model, how many motifs were identified, or what specific syntax rules were tested. The experimental validation is mentioned but not described in terms of design, controls, or effect sizes.
  - **Why it matters** The claim of mechanistic insight is a key differentiator from purely predictive models. Without clear evidence that the identified rules are biologically meaningful and not artifacts of model interpretation, this claim remains unsupported.
  - **Resolution test** Describe the motif discovery and rule extraction methods, and present experimental results showing that mutations predicted to disrupt syntax rules alter enhancer activity in the expected direction and magnitude.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generalizability
  - **Claim pointer** The rules can be generalized to humans by testing more than 40,000 wildtype and mutant Drosophila and human enhancers.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract claims cross-species generalization but does not specify how human enhancer activity was measured, whether the model was retrained or fine-tuned on human data, or what the predictive performance was on human enhancers. The number 40,000 is stated without breakdown by species or condition.
  - **Why it matters** Generalization to humans is a strong claim with implications for the model's utility beyond Drosophila. If the human testing involved only a narrow set of sequences or conditions, the claim would be overstated.
  - **Resolution test** Provide a clear description of the human enhancer datasets, assay conditions, model transfer approach, and performance metrics for human enhancers separately from Drosophila.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The authors designed and functionally validated synthetic enhancers with desired activities de novo.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not describe the design strategy for synthetic enhancers, the number of designs tested, the success rate, or the range of activities achieved. Without these details, the claim of de novo design cannot be evaluated.
  - **Why it matters** De novo design is a demanding application that requires demonstration of both accuracy and generalizability. A small number of successful examples or a narrow activity range would limit the significance.
  - **Resolution test** Present the design algorithm, the number of synthetic enhancers tested, the distribution of predicted versus measured activities, and a comparison to endogenous enhancer activities.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract wording
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The phrase "higher-order syntax rules" is used without definition or examples, which may be unclear to readers outside the immediate field.
  - **Required correction** Define what constitutes a syntax rule in this context and provide a concrete example in the abstract or refer to a figure.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Dataset description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions "thousands of developmental and housekeeping enhancers" but does not specify the exact number, source, or assay used to measure activity.
  - **Required correction** Include the number of enhancers, their genomic origin, and the assay type in the abstract or main text.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Model availability
  - **Evidence pointer** Abstract; location not provided
  - **Issue** No mention is made of code or model availability, which is important for reproducibility and community use.
  - **Required correction** State where the model and code can be accessed, or note that they will be made available upon publication.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4. The abstract does not provide sufficient quantitative or methodological detail to establish any of the four main claims. Each requires additional evidence from the full manuscript.

- **Assessment against Nature-style criteria** Originality is potentially high, as the combination of predictive modeling, mechanistic interpretation, cross-species validation, and de novo design in a single study is not common. Scientific importance is potentially high given the central role of enhancers in gene regulation and the difficulty of de novo design. Interdisciplinary readership is likely, spanning genomics, machine learning, and synthetic biology. Technical soundness cannot be assessed from the abstract alone, as no performance metrics or methodological details are provided. Readability for nonspecialists is adequate, though terms such as "higher-order syntax rules" could be clarified. Overall, the work has the potential to meet Nature-style standards, but the evidence presented in the abstract is insufficient to confirm this.

- **Recommendation posture** Supportive if technical concerns are resolved. The claims are ambitious and potentially significant, but the abstract alone does not establish them. The full manuscript must provide quantitative performance metrics, detailed descriptions of rule extraction and experimental validation, clear evidence of cross-species generalization, and a thorough account of the de novo design process. If these are adequately addressed, the work would be of considerable interest.

## Risk / unsupported claims
- The claim of quantitative prediction of enhancer activity is unsupported without performance metrics.
- The claim of learning relevant TF motifs and syntax rules is unsupported without details on model interpretation and experimental validation.
- The claim of generalization to humans is unsupported without specifics on human datasets and performance.
- The claim of de novo design of synthetic enhancers is unsupported without design strategy and success rates.
- The overall significance and impact cannot be evaluated from the abstract alone.