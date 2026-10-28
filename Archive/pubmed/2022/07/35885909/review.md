## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific and technical soundness of the proposed method, validity of performance claims, and adequacy of evidence presented
- **Shared manuscript claim summary** The authors propose PromoterLCNN, a two-stage light CNN architecture for predicting and classifying E. coli promoters into six sigma factor subclasses (σ70, σ24, σ32, σ38, σ28, σ54). They claim comparable or better performance than existing CNN-based methods (pcPromoter-CNN, iPromoter-BcNN) with 30–90% reduction in training, prediction, and hyperparameter optimization time.
- **Visible evidence base** Abstract, Introduction, Methods (datasets, encoding, architecture, hyperparameters, metrics), Results and Discussion (Figures 5 and 6 referenced), Conclusions
- **Missing materials affecting confidence** Figures 1–6 not provided; Table 1 (dataset sizes) and Table 2 (hyperparameter candidates) not provided; no code or reproducibility details; no statistical significance tests reported; no detailed per-class performance breakdown beyond what is described in text

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in bacterial genomics, namely promoter prediction and sigma factor classification. The proposed architecture is simpler and lighter than existing cascaded CNN approaches, which is a legitimate contribution if performance parity can be demonstrated. However, the evidence presented in the text is insufficient to fully evaluate the claims. Key figures and tables are missing, statistical significance is not addressed, and the comparison methodology has potential weaknesses. The core idea is sound but the current presentation does not establish the case convincingly.
- **Who would be interested in the results, and why** Researchers in bacterial genomics, bioinformatics, and synthetic biology who need fast and accurate promoter annotation tools. The lightweight nature of the model may appeal to those with limited computational resources or who need to process large genomic datasets. The comparative analysis against existing CNN methods is useful for practitioners choosing among available tools.
- **Major strengths** 1) The problem is well-motivated and relevant. 2) The two-stage multiclass architecture is a sensible simplification compared to cascaded binary classifiers. 3) The use of standard benchmark datasets (RegulonDB) facilitates comparison with prior work. 4) The emphasis on computational efficiency is practically valuable. 5) The manuscript follows a clear structure and the writing is generally accessible.
- **Major Concerns** 
  - R1-M1: Missing key figures and tables prevents verification of reported results.
  - R1-M2: No statistical significance testing for performance differences.
  - R1-M3: Potential data leakage or unfair comparison due to dataset construction.
  - R1-M4: The claim of 30–90% time reduction is not substantiated with concrete measurements.
  - R1-M5: Limited discussion of failure cases and generalizability beyond E. coli.
- **Minor Comments** 
  - R1-m1: Equation formatting issues.
  - R1-m2: Terminology inconsistency ("iPromoter-BcNN" vs "IPromoter-BnCNN").
  - R1-m3: The statement about "minor contamination of non-promoters" is unclear.
  - R1-m4: The conclusion overstates practical applicability.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The two-stage multiclass approach is a variation on existing CNN-based promoter classifiers, not a fundamentally new concept. The lightweight design is a practical contribution but not conceptually novel.
  - Scientific importance: Moderate. Promoter prediction is an ongoing need, and efficiency improvements are useful, but the incremental nature of the contribution limits its significance.
  - Interdisciplinary readership: Limited. The work is primarily of interest to bioinformatics and genomics specialists. The presentation assumes familiarity with CNN terminology and promoter biology.
  - Technical soundness: Currently not fully assessable due to missing figures and tables. The methodology as described is reasonable, but verification is impossible without the visual data.
  - Readability for nonspecialists: Acceptable. The writing is clear, but the technical depth and lack of background explanations for CNN concepts may limit accessibility.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim PromoterLCNN achieves "similar or better performance" than pcPromoter-CNN and iPromoter-BcNN, supported by Figures 5 and 6.
- **Evidence pointer** Figures 5 and 6 (not provided); Table 1 (not provided)
- **Concern** The central performance claims rest entirely on Figures 5 and 6, which are not included in the provided material. Without these figures, it is impossible to verify the reported accuracy, sensitivity, specificity, and MCC values, or to assess the per-class performance across the six sigma subclasses. Additionally, Table 1, which provides dataset sizes, is referenced for interpreting results but is also missing.
- **Why it matters** The entire contribution hinges on the validity of the performance comparison. Without the actual data, the claims are unverifiable and the scientific case is not established.
- **Resolution test** Provide Figures 5 and 6 and Table 1 in the manuscript. The figures should clearly show per-class metrics for all methods compared, with error bars or confidence intervals where applicable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors state PromoterLCNN performs "better than or similar to" existing methods across multiple metrics.
- **Evidence pointer** Section 3, Results and Discussion (location not provided)
- **Concern** No statistical significance testing is reported. Differences in accuracy, sensitivity, specificity, or MCC between methods could be within random variation, especially given the small sample sizes for some sigma classes (as acknowledged for σ24 and σ70 with n≥30). Without confidence intervals, p-values, or other statistical measures, the claimed superiority or parity cannot be distinguished from noise.
- **Why it matters** In machine learning benchmarks, performance differences are often not statistically meaningful. The absence of significance testing weakens the central comparative claim.
- **Resolution test** Perform and report appropriate statistical tests (e.g., McNemar's test for paired classification results, or bootstrap confidence intervals for each metric). State clearly whether observed differences are statistically significant.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology validity
- **Claim pointer** The authors state they use "the same disjointed datasets as in the literature" for training and independent testing.
- **Evidence pointer** Section 2.1, Benchmark and Test Datasets
- **Concern** The manuscript does not clarify whether the independent test set (RegulonDB v10.7) was used in any way during model development, such as for early stopping, hyperparameter selection, or threshold tuning. If the test set influenced any design decision, the reported performance would be optimistically biased. Additionally, the negative set construction (random coding sequences) may not reflect real genomic contexts where promoter-like sequences appear.
- **Why it matters** Dataset leakage or inappropriate negative sampling would invalidate the performance claims and the comparison with other methods.
- **Resolution test** Explicitly state that the independent test set was not used for any training or tuning decisions. Describe the negative set construction in detail and justify its representativeness. If possible, include a genomic negative set (e.g., intergenic non-promoter regions) as an additional validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** The authors claim "reducing time by approximately 30–90% for training, prediction, and hyperparameter optimization."
- **Evidence pointer** Section 3, Results and Discussion (location not provided)
- **Concern** No concrete timing measurements are provided. The claim of 30–90% time reduction is presented without specifying hardware, software versions, batch sizes, number of epochs, or the exact comparison protocol. The range is also very wide, which raises questions about what exactly is being compared.
- **Why it matters** Computational efficiency is a stated advantage of the proposed method. Without reproducible timing benchmarks, this claim is unverifiable and potentially misleading.
- **Resolution test** Provide a table or figure with wall-clock times for training, inference, and hyperparameter optimization for all compared methods, on the same hardware and software environment. Specify all relevant settings.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors suggest PromoterLCNN "might help researchers and users working in the field of bacterial genomics, molecular biology, and bioinformatics."
- **Evidence pointer** Section 4, Conclusions
- **Concern** The model is trained and tested exclusively on E. coli data. The authors do not discuss whether the architecture or hyperparameters would transfer to other bacterial species with different promoter architectures or GC content. The claim of broad utility is therefore speculative.
- **Why it matters** If the model is intended for general bacterial promoter prediction, evidence of cross-species performance is needed. Without it, the practical scope is limited to E. coli.
- **Resolution test** Add a discussion of potential limitations for cross-species application, or include preliminary results on at least one other bacterial species.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Presentation quality
- **Affected element** Equations (3)–(6)
- **Evidence pointer** Section 2.4, Performance Metrics
- **Issue** The equations contain formatting errors, including an apostrophe after the denominator in Equation (3) and inconsistent use of commas in Equations (4)–(6). These are likely typographical issues but detract from readability.
- **Required correction** Correct the formatting of all equations to ensure they are mathematically clear and properly typeset.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Method names
- **Evidence pointer** Section 1, Introduction; Section 3, Results and Discussion
- **Issue** The manuscript refers to "iPromoter-BcNN" in the Introduction and "iPromoter-BcNN" in the Results, but the original paper is cited as "IPromoter-BnCNN" (Ref. [18]). This inconsistency could confuse readers.
- **Required correction** Use a single consistent name for the reference method throughout the manuscript, matching the original publication.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results interpretation
- **Evidence pointer** Section 3, Results and Discussion
- **Issue** The sentence "the specificity row suggests that these corresponded to false-negative non-promoters as the dataset is balanced" is unclear. The relationship between specificity, false negatives, and dataset balance is not explained.
- **Required correction** Rewrite this sentence to clearly explain the observed pattern and its implications for model behavior.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Claim scope
- **Affected element** Conclusions
- **Evidence pointer** Section 4, Conclusions
- **Issue** The conclusion states the model "might help researchers" without acknowledging that the model has only been validated on E. coli and that real-world applicability requires further testing on diverse genomic contexts.
- **Required correction** Temper the conclusion to reflect the current scope of validation and explicitly mention the need for broader testing.

## Risk / unsupported claims
- The claim of "similar or better performance" than existing methods is unsupported without Figures 5 and 6.
- The claim of "reducing time by approximately 30–90%" is unsupported without concrete timing measurements.
- The suggestion of broad utility for "bacterial genomics, molecular biology, and bioinformatics" is unsupported given the E. coli-only validation.
- The statement that the model "might help researchers" in synthetic biology is speculative and not backed by any demonstration of practical use cases.
- The assertion that the model "is generalizing correctly" based on training data performance is not adequately justified without analysis of the train-test performance gap.