## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, footnotes) as provided
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and evidence as presented in the supplied text; no external verification of data or code
- **Shared manuscript claim summary** The authors present IDBindT5, a machine learning model using ProtT5 protein language model embeddings and disorder annotations to predict binding residues in intrinsically disordered protein regions. They claim state-of-the-art performance comparable to ANCHOR2 and DeepDISOBind, with substantially faster runtime, and demonstrate robustness when disorder annotations are replaced by predictions.
- **Visible evidence base** Abstract, Introduction, Results and Discussion sections, Methods (datasets, input embeddings, prediction methods, performance measures), Data availability statement, Author contributions, Acknowledgements, Footnotes
- **Missing materials affecting confidence** Supplementary figures and tables (SOM_F1 through SOM_F8, SOM_T1 through SOM_T8) are referenced but not provided; Figure 1, Figure 2, and Figure 3 are referenced but not visible; exact equations (Eqn. 1-8) are referenced but not shown; no code or model weights were inspected

## Reviewer

- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely the prediction of binding residues in intrinsically disordered protein regions, an area where existing tools often underperform. The use of protein language model embeddings is timely and well motivated. The authors provide a clear description of their method, datasets, and evaluation strategy. However, the core claim of state-of-the-art performance rests on comparisons that are only partially visible in the provided text, and the statistical framework for comparing methods is not fully described. The runtime advantage is clearly presented and is a genuine strength. The manuscript is generally well written and accessible, though some methodological details require clarification. The main limitations are the absence of the actual performance figures and supplementary materials, which prevents full verification of the central claims.

- **Who would be interested in the results, and why** Computational biologists working on protein function prediction, particularly those focused on intrinsically disordered proteins and their interaction partners. Researchers developing machine learning methods for protein sequence analysis will find the comparison of pLM embeddings versus traditional features useful. Experimental biologists studying disordered protein binding, especially those interested in molecular recognition features, may benefit from a fast prediction tool. The runtime analysis is relevant for developers of high-throughput proteome-scale analysis pipelines.

- **Major strengths** The problem is well defined and practically important. The use of pLM embeddings is current and well justified. The authors explicitly address the issue of data leakage through redundancy reduction against training sets of compared methods. The runtime comparison on a large human proteome subset is a practical and useful addition. The ablation study on input feature importance is informative. The authors acknowledge limitations of their data and evaluation, including the small test set sizes and the inability to distinguish binding partner types.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that IDBindT5 "reached SOTA" and performed "favorably" compared to ANCHOR2 and DeepDISOBind, with balanced accuracy of 57.2±3.6% and MCC of 0.139±0.07.
- **Evidence pointer** Results and Discussion section, "IDBindT5 reached SOTA" subsection; Figure 2; Supplementary Tables SOM_T4 and SOM_T7
- **Concern** The central performance claim is presented without the actual numerical results being visible in the provided text. The authors state that no method "stood out in a Welch test" and that differences were not significant at the 95% CI, but the specific values for ANCHOR2 and DeepDISOBind on the same test set are not given in the main text. The reader cannot assess whether the performance is genuinely comparable, marginally worse, or marginally better. The claim of "SOTA" is therefore not verifiable from the supplied material.
- **Why it matters** The primary contribution of the paper is a new prediction method. If the performance comparison is not transparently presented with all relevant numbers, the central claim cannot be evaluated. The phrase "reached SOTA" is ambiguous when statistical tests show no significant difference, and the practical significance of the result depends on the actual magnitudes.
- **Resolution test** Provide the full performance table for all methods on the Mobi195 test set, including balanced accuracy, MCC, precision, recall, and F1 with confidence intervals. Clarify what "SOTA" means in this context, and discuss whether the lack of statistical significance reflects insufficient power or genuine equivalence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The authors state that "the CNN can capture more information about the local residue environment than an FNN" and that the FNN was favored to reduce overfitting and runtime, but the comparison between CNN_disorder and IDBindT5 is not shown in the main text.
- **Evidence pointer** Results and Discussion section, "Embeddings allow for simple downstream architecture" subsection; Supplementary Figure SOM_F2 and Table SOM_T3
- **Concern** The decision to select the FNN over the CNN is described as based on "validation set" performance, but the actual performance values are not provided in the main text. The claim that the FNN was chosen to "reduce the odds of over-fitting" is plausible but not supported by any presented evidence, such as training versus validation performance curves. The reader cannot determine whether the choice was well justified or whether the CNN was actually better on the validation set.
- **Why it matters** Model selection is a critical step in machine learning research. If the choice between architectures is not transparently justified with data, the reader cannot assess whether the final model is indeed the best among those considered, or whether the selection process introduced bias.
- **Resolution test** Present the validation set performance for both CNN_disorder and IDBindT5, including all relevant metrics. Show training and validation loss curves to support the overfitting claim. Clarify the exact selection criterion used.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** External validity
- **Claim pointer** The authors state that "IDBindT5's SOTA predictions are much faster than other methods, easily enabling full-proteome analyses" and provide runtime data on a human proteome subset.
- **Evidence pointer** Results and Discussion section, "IDBindT5 good and fastest" subsection; Supplementary Table SOM_T8
- **Concern** The runtime comparison is presented as a strength, but the details of the comparison are not fully visible. The authors report that DeepDISOBind took 33 hours and 22 minutes, ANCHOR2 took 21 minutes, and IDBindT5 took 2 hours and 10 minutes on the same machine. However, it is unclear whether the runtime for the other methods includes their own preprocessing steps, such as generating multiple sequence alignments, which are known to be time-consuming. The claim of "much faster" is also not quantified in terms of speedup factors in the main text.
- **Why it matters** Runtime is a practical consideration for users. If the comparison is not apples-to-apples, the runtime advantage may be overstated. The claim of "easily enabling full-proteome analyses" depends on the actual throughput, which is not clearly stated.
- **Resolution test** Clarify whether the reported runtimes include all preprocessing steps for each method. Provide the speedup factor relative to each baseline. State the throughput in terms of proteins per hour or similar.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors claim that IDBindT5 "maintains SOTA performance with predicted disorder as input" and that the performance drop was not statistically significant.
- **Evidence pointer** Results and Discussion section, "IDBindT5 performance with predicted disorder data remains high" subsection; Supplementary Table SOM_T5
- **Concern** The evaluation with predicted disorder annotations uses SETH and AlphaFold2-disorder, but the quality of these predictions on the test set is reported as "limited" with MCC values of 0.324 and 0.432, respectively. The claim that binding prediction performance remains stable is based on a comparison of confidence intervals, but the actual performance values with predicted disorder are not shown in the main text. The practical utility of the method in a real-world scenario, where experimental disorder annotations are often unavailable, depends on this analysis.
- **Why it matters** The authors position IDBindT5 as a tool that can be used with predicted disorder annotations, which is important for applicability. If the performance drop is substantial in absolute terms, the claim of "remains high" may be misleading.
- **Resolution test** Present the full performance table for IDBindT5 with experimental disorder annotations, SETH predictions, and AlphaFold2-disorder predictions. Discuss the absolute performance levels, not just statistical significance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states "we presented a novel machine learning (ML) model" using past tense, which is unusual for a manuscript submission. The rest of the abstract uses present tense appropriately.
- **Required correction** Change "presented" to "present" for consistency.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and Discussion, "IDBindT5 reached SOTA" subsection
- **Evidence pointer** "Given the small sizes of both our test set (195 proteins) and the CAID2 binding benchmark (78 proteins), none of the SOTA methods consistently improved over the random baseline at levels that were statistically significant"
- **Issue** This statement is concerning because it suggests that even the SOTA methods do not significantly outperform random on these benchmarks. This raises questions about the difficulty of the task and the informativeness of the evaluation. The authors do not discuss the implications of this finding for the interpretation of their own results.
- **Required correction** Add a brief discussion of why the task is so challenging and what this means for the practical utility of all methods, including IDBindT5.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Precision
- **Affected element** Results and Discussion, "IDBindT5 good and fastest" subsection
- **Evidence pointer** "The slowest method, DeepDISOBind needed 33 hours and 22 minutes, the fastest, ANCHOR2 took 21 minutes."
- **Issue** The sentence structure is awkward and the missing comma after "DeepDISOBind" makes it initially read as if DeepDISOBind is both the slowest and the fastest.
- **Required correction** Rephrase for clarity, for example: "The slowest method was DeepDISOBind, which needed 33 hours and 22 minutes, while the fastest was ANCHOR2, which took 21 minutes."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Transparency
- **Affected element** Methods, "Datasets" subsection
- **Evidence pointer** "We excluded the protein titin (Q8WZ42 with 34,350 residues) to manage memory consumption (only proteins with over 10k (10,000) residues)."
- **Issue** The parenthetical phrase is confusing. It is unclear whether the exclusion criterion was titin specifically or all proteins over 10,000 residues. If the latter, the text should state how many proteins were excluded by this criterion.
- **Required correction** Clarify the exclusion criterion and state how many proteins were removed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Prediction methods" subsection
- **Evidence pointer** "The cutoff used to classify a residue as binding... was chosen individually for each model and fold, based on receiver operating characteristic (ROC) curves"
- **Issue** The exact procedure for choosing the cutoff from the ROC curves is not described. Different researchers might choose different points on the ROC curve, and the choice affects the reported precision and recall values.
- **Required correction** Describe the exact criterion for selecting the cutoff from the ROC curve, or state that the cutoff was optimized on the validation set using a specific objective function.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Methods, "Performance measures" subsection
- **Evidence pointer** "Standard boot-strapping turned these metrics into statistical estimates, applying each to batches of 100 disordered residues."
- **Issue** The description of the bootstrapping procedure is brief. It is unclear how the batches of 100 residues were sampled, whether they were sampled with replacement, and how the confidence intervals were computed from the bootstrap distribution.
- **Required correction** Provide a more detailed description of the bootstrapping procedure, including the number of bootstrap replicates and the method for computing confidence intervals.

- **Technical failings that need to be addressed before the case is established** The central performance comparison is not fully visible in the provided text, making the "SOTA" claim unverifiable. The model selection process between CNN and FNN is not transparently documented. The runtime comparison may not account for all preprocessing steps of baseline methods. The evaluation with predicted disorder annotations requires the actual performance values to be presented.

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of pLM embeddings to binding residue prediction in disordered regions is a reasonable extension of existing work, but the approach is not conceptually novel. The authors themselves note that pLM embeddings have been shown to be predictive of many protein features.
  - Scientific importance: Moderate. The problem is relevant, and a fast method for this task could be useful. However, the performance gains over existing methods are not clearly demonstrated, and the authors acknowledge that differences are not statistically significant.
  - Interdisciplinary readership: Limited. The manuscript is primarily of interest to computational biologists and bioinformaticians. The biological insights are limited, and the authors do not provide new experimental or functional data.
  - Technical soundness: The methodology is generally sound, but the incomplete presentation of performance data and the unclear model selection process are concerns. The statistical framework for comparing methods is not fully described.
  - Readability for nonspecialists: The manuscript is reasonably well written and the main ideas are accessible. However, some sections, particularly the methods, assume familiarity with machine learning terminology and protein bioinformatics concepts.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant problem and presents a reasonable approach. The runtime advantage is a genuine practical contribution. However, the central performance claims must be fully documented with visible numerical results, the model selection process must be transparent, and the statistical comparisons must be clearly described. The authors should also address the concerning finding that no method significantly outperforms random on these benchmarks.

## Risk / unsupported claims
- The claim that IDBindT5 "reached SOTA" is not verifiable from the provided text, as the actual performance values for the compared methods are not shown.
- The claim that the FNN was chosen to "reduce the odds of over-fitting" is not supported by presented evidence.
- The claim that IDBindT5 "maintains SOTA performance with predicted disorder as input" requires the actual performance values to be presented.
- The claim that the choice of pLM was "not critical" is based on a comparison of two pLMs only and may not generalize.
- The statement that "none of the SOTA methods consistently improved over the random baseline at levels that were statistically significant" raises questions about the evaluation benchmarks that are not addressed.
- The runtime comparison may not be apples-to-apples if preprocessing steps for baseline methods are not included.