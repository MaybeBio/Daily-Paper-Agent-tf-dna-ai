## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present Deep DNAshape, a deep learning method that predicts DNA shape features for any length and number of DNA sequences in a high-throughput manner, accounting for the influence of extended flanking regions without requiring molecular simulations or structural biology experiments. They claim that flanking regions, including distant ones, quantitatively affect DNA shape readout of a core target, and that incorporating Deep DNAshape features into machine learning models improves prediction accuracy.
- **Visible evidence base** Abstract text only; no quantitative results, performance metrics, comparisons, or methodological details are available
- **Missing materials affecting confidence** Full manuscript, methods description, training and validation datasets, benchmark comparisons, model architecture details, evaluation metrics, and any figures or tables

## Reviewer
- **Overall assessment** The abstract describes a potentially useful tool for high-throughput DNA shape prediction, addressing a real limitation of existing k-mer based approaches. However, the claims are broad and largely unsupported by the evidence visible in the abstract. No quantitative results, validation strategies, or comparisons to existing methods are presented. The scientific case is therefore not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying protein-DNA binding mechanisms, gene regulation, and structural bioinformatics would be interested. The method could also appeal to computational biologists developing machine learning models for regulatory genomics, as improved DNA shape features may enhance predictive performance.
- **Major strengths** The proposed approach addresses a recognized limitation in current DNA shape prediction methods, namely the neglect of extended flanking region effects. The claim of high-throughput prediction without costly simulations is practically appealing. The potential integration with machine learning models for regulatory genomics is a useful direction.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is plausible, as the idea of using deep learning to account for extended flanking regions in DNA shape prediction appears novel. Scientific importance is potentially high for the gene regulation community, but the abstract does not provide evidence of impact. Interdisciplinary readership is likely, spanning structural biology, bioinformatics, and genomics. Technical soundness cannot be assessed from the abstract alone. Readability for nonspecialists is adequate, though some terms such as "k-mer based" and "DNA shape readout" may require prior knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but lacks the quantitative and methodological detail needed to support the claims. A full manuscript with validation and benchmarks would be required for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The method "accurately accounts for the influence of extended flanking regions" and can predict "refined DNA shape features for any length and number of DNA sequences."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract provides no quantitative evidence, such as accuracy metrics, correlation coefficients, or error rates, to support the claim of accurate prediction. No comparison to existing k-mer based methods or experimental structures is described.
- **Why it matters** Without validation against known DNA structures or established prediction tools, the accuracy claim is unsubstantiated. The central value of the method depends on its predictive reliability.
- **Resolution test** Provide benchmark results comparing Deep DNAshape predictions to experimental structures and existing methods, including error metrics and correlation analyses.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "DNA shape readout mechanisms of a core target are quantitatively affected by flanking regions, including extended flanking regions."
- **Evidence pointer** Abstract only; location not provided
- **Concern** This is a substantive biological claim, but the abstract presents no data demonstrating the magnitude or significance of flanking region effects. No examples, statistical tests, or effect sizes are given.
- **Why it matters** The claim is central to the novelty of the work. If unsupported, the contribution reduces to a technical tool without demonstrated biological insight.
- **Resolution test** Show specific examples with quantitative comparisons of predicted shape features for core regions with and without extended flanking regions, including statistical significance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "When incorporated in machine learning models, the features generated by Deep DNAshape improve the model prediction accuracy."
- **Evidence pointer** Abstract only; location not provided
- **Concern** No details are provided on the machine learning tasks, datasets, baseline models, or improvement metrics. The claim of improved accuracy is not quantifiable from the abstract.
- **Why it matters** This claim suggests practical utility beyond prediction, but without specifics it cannot be evaluated or reproduced.
- **Resolution test** Describe the downstream tasks, datasets, baseline comparisons, and report performance gains with appropriate metrics and statistical tests.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "k-mer based" is used without explanation, which may confuse readers outside bioinformatics.
- **Required correction** Briefly define k-mer based methods or provide context for nonspecialist readers.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity of claims
- **Affected element** Scope of prediction
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "any length and number of DNA sequences" is overly broad and may imply unlimited scalability without computational constraints.
- **Required correction** Qualify the claim with practical limits or performance characteristics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Method availability
- **Evidence pointer** Abstract; location not provided
- **Issue** No mention of code or data availability, which is important for a method paper.
- **Required correction** State where the software and training data can be accessed.

## Risk / unsupported claims
- The claim of accurate prediction of DNA shape features is unsupported by any quantitative evidence in the abstract.
- The claim that flanking regions quantitatively affect DNA shape readout is unsupported by data.
- The claim that Deep DNAshape features improve machine learning model accuracy is unsupported by specific results.
- The general statement that the method can serve as a "versatile and powerful tool" is an assertion without demonstrated scope or limitations.