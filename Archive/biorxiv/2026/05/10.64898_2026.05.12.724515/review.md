## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological soundness, validity of claims relative to presented evidence, and clarity of presentation. No assessment of code functionality or data availability beyond what is described.
- **Shared manuscript claim summary** The authors propose ArChIPelago, a framework that combines multiple position weight matrices (PWMs) for the same transcription factor into a joint classifier using classic machine learning methods. They claim consistent improvements over individual PWMs, diPWMs, and Slim models in predicting transcription factor binding sites from ChIP-Seq data, and demonstrate cross-species transferability.
- **Visible evidence base** Abstract, introduction, methods sections 2.1–2.7, results sections 3.1–3.3 and 4, conclusions, author contributions, funding, and supplementary figure references. Figures 1–4 and supplementary figures S1–S4 are referenced but not provided.
- **Missing materials affecting confidence** Figures 1–4 and supplementary figures S1–S4 are not included in the provided material. Supplementary tables 1–3 are referenced but not provided. Detailed hyperparameter search results, feature importance analyses, and per-TF performance breakdowns are not shown. The manuscript states a GitHub repository and Zenodo data availability, but these are not assessed.

## Reviewer
- **Overall assessment** The manuscript addresses a practical and relevant question in transcription factor binding site prediction: whether combining multiple existing PWMs via machine learning can outperform individual models. The scale of evaluation (704 ChIP-Seq datasets, 36 TF pairs) is substantial and the cross-species validation is a valuable addition. However, the absence of key figures and supplementary materials limits the ability to fully evaluate the strength of the reported improvements. The methodological description is generally clear, but several claims regarding generalizability and mechanism would benefit from additional analysis or clarification. The work is likely of interest to the computational genomics community, though the incremental nature of the improvement and the moderate absolute performance metrics warrant careful interpretation.
- **Who would be interested in the results, and why** Researchers in computational biology and genomics, particularly those working on transcription factor binding site prediction, motif discovery, and regulatory genomics. The practical message that lightweight ensemble models using publicly available PWMs can achieve competitive performance may appeal to those seeking accessible tools without deep learning expertise. The cross-species analysis may interest those studying regulatory evolution.
- **Major strengths** 1) Large-scale and diverse evaluation across 36 TF pairs and 704 datasets. 2) Cross-species validation is a meaningful addition. 3) Comparison against multiple baseline methods, including Slim models and diChIPMunk. 4) The framework is simple, interpretable, and uses readily available resources. 5) The observation that diPWMs contribute despite lower individual performance is an interesting finding.
- **Major Concerns** 1) The manuscript claims consistent improvements, but the provided text does not include the actual performance figures or statistical details needed to verify the magnitude and consistency of these gains. 2) The mechanism by which the ensemble captures motif subtypes is asserted but not directly demonstrated. 3) The cross-species results show weaker and less consistent gains, and the discussion of this limitation is brief. 4) The comparison to deep learning methods, which are the current state of the art, is absent. 5) The choice of negative set construction and its potential biases are not fully discussed.
- **Minor Comments** 1) The abstract states "improves prediction" but does not quantify the improvement. 2) The introduction could better position the work relative to recent deep learning approaches. 3) The methods section on data preparation is detailed but could benefit from a clearer statement on how the final 36 TFs were selected. 4) The discussion of why some TFs (e.g., FLI1, PRGR) do not improve is speculative and could be strengthened with additional analysis. 5) The conclusion that "lightweight, publicly available PWMs may be sufficient" is somewhat overstated given the moderate absolute performance.
- **Technical failings that need to be addressed before the case is established** 1) The absence of figures and supplementary tables prevents verification of the central claims. 2) The statistical significance of the improvements is mentioned but not fully reported. 3) The cross-species analysis lacks a clear discussion of potential confounding factors (e.g., species-specific motif usage). 4) The manuscript does not report confidence intervals or variance across datasets for the performance metrics.
- **Assessment against Nature-style criteria** Originality: The idea of combining multiple PWMs via machine learning is not entirely new, but the systematic large-scale evaluation and the specific finding regarding diPWM contributions add some novelty. Scientific importance: The work addresses a practical problem and could influence tool choice, but the incremental gains over existing methods may limit its broader impact. Interdisciplinary readership: The topic is specialized; the manuscript is likely to appeal primarily to computational biologists and bioinformaticians. Technical soundness: The methodology is generally sound, but the lack of key figures and detailed results prevents full verification. Readability for nonspecialists: The manuscript is reasonably clear but assumes familiarity with PWM concepts and machine learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the provision of the missing figures and supplementary materials, and if the authors address the limitations regarding cross-species generalizability and comparison to deep learning baselines.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims consistent improvements over individual PWMs, diPWMs, and Slim models across diverse TF families.
- **Evidence pointer** Figures 2, 3, 4 and supplementary figures S1–S4 are referenced but not provided. Supplementary tables 1–3 are also not provided.
- **Concern** The central claims of the manuscript rest on the performance comparisons shown in the figures and supplementary tables. Without these materials, it is impossible to verify the magnitude, consistency, or statistical significance of the reported improvements. The text provides some median values (e.g., 0.022 increase in auROC) but does not show the distribution of results across TFs or datasets.
- **Why it matters** The validity of the main conclusions depends entirely on the evidence presented in these figures and tables. The reader cannot assess whether the improvements are meaningful or whether they hold for the majority of TFs.
- **Resolution test** Provide the missing figures and supplementary tables, including per-TF performance values, confidence intervals, and statistical test results. The authors should also show the distribution of performance gains across TFs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity
- **Claim pointer** The manuscript states that the ensemble captures alternative motif subtypes, leading to improved predictions.
- **Evidence pointer** Section 3.3, Figure 3D (not provided).
- **Concern** The claim that the ensemble accounts for motif subtypes is plausible but not directly demonstrated. The text mentions examples (RXRA, SRF, ANDR) where improvements are attributed to multiple subtypes, but no analysis is shown to confirm that the ensemble indeed learns distinct subtype-specific features rather than simply averaging noisy predictions.
- **Why it matters** Understanding the mechanism of improvement is important for generalizing the approach to other TFs and for interpreting why the method works. Without this analysis, the claim remains speculative.
- **Resolution test** Provide an analysis showing that the ensemble assigns different weights to different PWMs in a way that correlates with known motif subtypes, or demonstrate that the ensemble outperforms a simple average of PWM scores.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Comparison to state of the art
- **Claim pointer** The manuscript positions ArChIPelago as a practical alternative to more complex models, but does not compare against deep learning methods.
- **Evidence pointer** Sections 3.2–3.4, no mention of deep learning baselines.
- **Concern** Deep learning models (e.g., DeepBind, DeepSEA, BPNet) are widely used for TF binding prediction and often achieve higher performance than PWM-based approaches. The absence of any comparison to these methods limits the assessment of the practical value of ArChIPelago.
- **Why it matters** If deep learning methods substantially outperform ArChIPelago, the practical utility of the proposed framework is diminished, even if it is simpler and more interpretable.
- **Resolution test** Add a comparison against at least one or two representative deep learning models on the same datasets, or clearly justify why such a comparison is not feasible or relevant.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Cross-species validity
- **Claim pointer** The manuscript claims reliable cross-species predictions, but notes that for 12 TFs the performance was worse than the best PWM.
- **Evidence pointer** Section 3.3, supplementary figures S2 and S3 (not provided).
- **Concern** The cross-species results are presented as a strength, but the text acknowledges that for a substantial number of TFs (12 out of 36), the ensemble underperforms. This suggests that the model may be learning species-specific features in some cases, which is a significant limitation for the claimed generalizability.
- **Why it matters** The cross-species claim is a key differentiator of this work. If the method does not consistently transfer across species, its utility for studying regulatory evolution or for application to less-studied species is limited.
- **Resolution test** Provide a detailed analysis of which TFs fail in cross-species transfer and investigate potential reasons (e.g., motif divergence, differences in ChIP-seq data quality). Discuss whether the failures are systematic or idiosyncratic.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of abstract
- **Affected element** Abstract
- **Evidence pointer** Abstract, "Results" paragraph
- **Issue** The abstract states that ArChIPelago "improves prediction" but does not provide any quantitative measure of improvement. This makes it difficult for a reader to gauge the practical significance.
- **Required correction** Include a representative quantitative improvement (e.g., median auROC increase) in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2, "Data splitting and feature generation"
- **Issue** The description of negative set construction is brief. It states that negatives were selected from peaks of other TFs from unrelated families, but does not specify how "unrelated" was defined or how the GC-matching was performed.
- **Required correction** Provide more detail on the negative set construction, including the criteria for "unrelated" and the GC-matching procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.2
- **Evidence pointer** Section 3.2, "ArChIPelago outperforms individual mono- and di-nucleotide PWMs"
- **Issue** The text mentions a Wilcoxon signed-rank test (p<0.05) but does not report the test statistic or the number of comparisons. It is also unclear whether multiple testing corrections were applied.
- **Required correction** Report the test statistic, the number of TFs included, and whether any multiple testing correction was applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Section 5, "Conclusions"
- **Evidence pointer** Section 5, "Conclusions"
- **Issue** The conclusion states that the approach is "practically viable" but does not discuss potential limitations such as the need for a sufficient number of PWMs per TF or the sensitivity to the quality of input PWMs.
- **Required correction** Add a brief discussion of the conditions under which the method is likely to be most and least effective.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.7, "Data and code availability"
- **Evidence pointer** Section 2.7
- **Issue** The manuscript states that data and code are available, but does not specify the exact versions of software dependencies or provide a detailed environment specification.
- **Required correction** Provide a list of software versions and a configuration file (e.g., conda environment or Dockerfile) to ensure reproducibility.

## Risk / unsupported claims
- The claim that ArChIPelago "consistently outperforms" individual PWMs is not fully verifiable without the figures and supplementary tables.
- The claim that the ensemble captures motif subtypes is plausible but not directly demonstrated with evidence.
- The claim of "reliable cross-species predictions" is weakened by the acknowledged underperformance for 12 TFs.
- The statement that "lightweight, publicly available PWMs may be sufficient" is an overgeneralization given the moderate absolute performance metrics and the lack of comparison to deep learning methods.
- The assertion that improvements are "meaningful" in the context of a 1:100 class imbalance is reasonable but not quantified in terms of practical impact (e.g., number of additional true binding sites recovered).