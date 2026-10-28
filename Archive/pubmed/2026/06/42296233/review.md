## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results and discussion, and conclusion sections. Figures and tables are referenced but not provided in full detail.
- **Assessment boundary** Evaluation is limited to the provided text. Numerical results are reported in the text and in referenced tables (Tables 1-4) and figures (Figs. 1-4), but the actual table and figure contents are not available for verification.
- **Shared manuscript claim summary** The authors propose a language model-based self-training framework that integrates pre-trained language models (ESM-1b for proteins, doc2vec for RNA) with semi-supervised self-training to classify biological sequences (DNA-binding proteins and non-coding RNAs) using only 1% of labeled data, achieving performance competitive with fully supervised state-of-the-art methods.
- **Visible evidence base** Text descriptions of experimental results, including accuracy, sensitivity, specificity, precision, F1-score, MCC, and AUC values for multiple datasets (DBP1, DBP2, DBP3, CPP1, CPP2, CPP3). Algorithm 1 is described in text. Figures 1-4 and Tables 1-4 are referenced but not shown.
- **Missing materials affecting confidence** Actual figure and table contents, detailed hyperparameter settings, exact dataset statistics, baseline implementation details, statistical significance tests, and the full algorithm pseudocode are not available in the provided material.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely reducing labeled data requirements for biological sequence classification. The proposed framework combining PLMs with self-training is conceptually reasonable and the reported results are promising. However, several technical aspects require clarification and additional validation before the central claims can be fully supported. The claim of "99% reduction in labeled data requirements" is bold and needs more rigorous demonstration, including comparisons across a wider range of labeled data fractions and statistical significance testing.
- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics working on sequence classification, particularly those dealing with low-resource settings where experimental labels are scarce. The work may also interest machine learning researchers focused on semi-supervised learning and domain adaptation for biological data. The practical implications for large-scale genome annotation projects and novel species analysis are significant.
- **Major strengths** The problem addressed is important and timely. The integration of PLMs with self-training is a sensible approach that leverages complementary strengths. The use of multiple benchmark datasets and comparison with several baselines is commendable. The inclusion of experimentally validated novel sequences (DBP3, CPP3) for testing is a notable strength. The computational efficiency analysis adds practical value.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of statistical significance testing), R1-M2 (insufficient ablation analysis), R1-M3 (incomplete comparison with SSL baselines), R1-M4 (data leakage concerns not fully addressed), R1-M5 (threshold selection methodology unclear).
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The combination of PLMs and self-training is not entirely novel, but the specific application to biological sequence classification with a focus on extreme label efficiency has some originality.
  - Scientific importance: High. Reducing labeled data requirements is a critical bottleneck in biological sequence analysis, and the potential impact is substantial.
  - Interdisciplinary readership: Moderate. The work bridges machine learning and computational biology, but the presentation is somewhat technical and may not fully engage a broader biological audience.
  - Technical soundness: Currently not fully established. Several methodological details and validation aspects need strengthening.
  - Readability for nonspecialists: Acceptable but could be improved. The introduction provides good context, but the methods section assumes familiarity with SSL and PLM concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the results are encouraging, but the current evidence does not fully substantiate the strong claims made in the title and abstract.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that the proposed method achieves "competitive performance compared to full supervision while using far fewer labeled samples" and that it "reduces labeled data requirements by 99%."
- **Evidence pointer** Results and discussion sections, Tables 1-4 (location not provided)
- **Concern** The reported performance differences between the proposed method and baselines are presented without any statistical significance testing. Given the variability inherent in machine learning experiments, especially with small labeled sets, it is unclear whether the observed differences are meaningful or within the range of random variation. The claim of achieving performance comparable to full supervision with only 1% of labels is strong and requires confidence intervals or significance tests across multiple runs.
- **Why it matters** Without statistical validation, the central claim of the paper cannot be reliably assessed. The difference between, for example, 91.32% and 92.22% accuracy on DBP2 may not be statistically significant, which would weaken the claim of achieving near-SOTA performance.
- **Resolution test** Provide results from multiple independent runs (e.g., 5-10 runs with different random seeds) and report mean and standard deviation for each metric. Perform appropriate statistical tests (e.g., paired t-test or Wilcoxon signed-rank test) comparing the proposed method against each baseline. Report p-values or confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Ablation analysis
- **Claim pointer** The manuscript states that "the language model-based self-training method outperforms traditional semi-supervised approaches like TSVM" and that the framework integrates PLMs with SSL to achieve its results.
- **Evidence pointer** Results and discussion sections, Fig. 4 (location not provided)
- **Concern** The individual contributions of the PLM features and the self-training algorithm are not systematically isolated. While the text mentions that the supervised-only baselines (SVM0) use the same PLM features, there is no ablation showing the performance of self-training with non-PLM features or the performance of PLM features without self-training across all datasets. This makes it difficult to attribute the observed improvements to the specific components of the proposed framework.
- **Why it matters** Understanding the contribution of each component is essential for assessing the novelty and generalizability of the approach. If the self-training algorithm provides minimal benefit over PLM features alone, the contribution of the paper is substantially diminished.
- **Resolution test** Include ablation experiments with the following configurations: (1) PLM features + supervised SVM (already reported as SVM0), (2) non-PLM features (e.g., k-mer frequencies) + self-training, (3) non-PLM features + supervised SVM, and (4) PLM features + self-training (proposed method). Report all metrics for each configuration across all datasets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline comparison
- **Claim pointer** The manuscript claims that the proposed method "outperforms traditional semi-supervised approaches like TSVM" and achieves "competitive performance against state-of-the-art fully supervised methods."
- **Evidence pointer** Results and discussion sections, Fig. 4, Tables 1-4 (location not provided)
- **Concern** The comparison with SSL baselines is limited to TSVM and Seed K-means. Modern SSL methods that are more relevant to the proposed approach, such as self-training with confidence thresholds (e.g., FixMatch, FlexMatch) or consistency regularization methods adapted for biological sequences, are not included. Additionally, the fully supervised baselines may not represent the current state of the art, particularly for PLM-based methods.
- **Why it matters** The claim of outperforming "traditional" SSL methods is not particularly strong if more modern and effective SSL baselines are not considered. A more comprehensive comparison would strengthen the case for the proposed method's advantages.
- **Resolution test** Include additional SSL baselines such as self-training with different confidence thresholds, co-training, and possibly a recent consistency-based method adapted for tabular or sequence data. For fully supervised baselines, include more recent PLM-based methods beyond DBP2Vec and CPPVec.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data leakage
- **Claim pointer** The manuscript acknowledges potential data leakage concerns with ESM-1b but argues that no label leakage occurs since the model was trained with unsupervised masked language modeling.
- **Evidence pointer** Materials and methods, ESM-1b section
- **Concern** While the argument about label leakage is reasonable, the potential for feature leakage remains. If ESM-1b's pre-training corpus contains sequences highly similar to test sequences, the features may encode information that is not available in a truly low-resource setting. The manuscript does not quantify the sequence similarity between the pre-training data and the test sets, nor does it demonstrate that the results hold when using a PLM trained on data excluding any sequences homologous to the test sets.
- **Why it matters** The claim of reducing labeled data requirements by 99% is predicated on the assumption that the PLM features are generalizable. If the results are partly due to feature leakage, the practical utility of the method in genuinely novel sequence spaces would be overstated.
- **Resolution test** Provide an analysis of sequence identity between the pre-training corpus and the test sets. If feasible, include an experiment using a PLM trained on a corpus that explicitly excludes sequences with high similarity to the test sets, and show that the performance gains are maintained.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Threshold selection
- **Claim pointer** The manuscript describes a dual-threshold confidence strategy with thresholds tau1 and tau2, initially set to 0.7 and 0.3, and progressively tightened.
- **Evidence pointer** Materials and methods, Self-training with pseudo-labels section
- **Concern** The procedure for selecting and adjusting the thresholds is not described in sufficient detail. It is unclear whether the thresholds are dataset-specific, how they are tuned, and whether the reported results are sensitive to the choice of thresholds. The progressive tightening schedule is also not specified.
- **Why it matters** The performance of self-training methods is often highly sensitive to confidence thresholds. Without a clear and reproducible threshold selection procedure, the results may not be generalizable to new datasets or settings.
- **Resolution test** Provide a detailed description of the threshold selection process, including any validation-based tuning. Include a sensitivity analysis showing how performance varies with different initial threshold values and tightening schedules.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, Key points
- **Issue** The key points are presented as bullet points without clear connection to the main text. The third key point states "requiring only 1% labeled data for effective classification" but the abstract does not specify what "effective" means in quantitative terms.
- **Required correction** Clarify the key points by linking them to specific quantitative results reported in the main text. Define "effective classification" with reference to specific performance metrics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and methods, Datasets
- **Evidence pointer** Datasets section
- **Issue** The dataset descriptions are brief. For DBP1, DBP2, and DBP3, the exact number of positive and negative samples is not stated. For CPP1, CPP2, and CPP3, the species composition and the number of sequences are not provided.
- **Required correction** Provide complete dataset statistics, including the number of positive and negative samples for each dataset, and the species breakdown for the multi-species CPP datasets.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and methods, ESM-1b
- **Evidence pointer** ESM-1b section
- **Issue** The PCA dimensionality reduction step is mentioned, but the criterion for selecting the number of principal components is not described beyond preserving 95% cumulative variance. The resulting dimensionality is not reported.
- **Required correction** Specify the exact number of principal components retained for each dataset and describe any validation performed to confirm that this choice does not degrade performance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and methods, Doc2vec
- **Evidence pointer** Doc2vec section
- **Issue** The doc2vec model is described as being trained on protein sequences translated from the longest ORFs of RNA sequences. The details of ORF selection, translation, and the doc2vec hyperparameters (e.g., vector size, window size, epochs) are not provided.
- **Required correction** Provide the full details of the ORF selection and translation process, and report the doc2vec hyperparameters used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results and discussion, Computational efficiency
- **Evidence pointer** Computational efficiency and runtime analysis section
- **Issue** The runtime analysis reports ranges (e.g., 50-80 s for DBP1, 1500-6000 s for DBP2) but does not specify the hardware environment or the number of iterations corresponding to these times.
- **Required correction** Specify the hardware used for the experiments and report the number of self-training iterations for each dataset to provide context for the runtime ranges.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and discussion, Performance on experimentally annotated ncRNAs and DBPs
- **Evidence pointer** Performance on experimentally annotated ncRNAs and DBPs section
- **Issue** The results on DBP3 and CPP3 are reported as accuracy with confidence intervals, but the number of samples in these test sets is not stated. The statement "accurately identifying 64 DBPs" suggests a total of 76, but this is not explicit.
- **Required correction** Clearly state the total number of samples in DBP3 and CPP3 and report the full confusion matrix or at least the number of true positives, false positives, true negatives, and false negatives.

## Risk / unsupported claims
- The claim of "reducing labeled data requirements by 99%" is not fully supported by the evidence presented. While the method uses 1% of the labeled data, the performance comparison is only shown for a single labeled data fraction. A more comprehensive analysis across different fractions (e.g., 0.5%, 1%, 2%, 5%, 10%) would be needed to substantiate this claim.
- The statement that the method "achieves competitive performance compared to full supervision" is based on results without statistical significance testing, making it difficult to assess the reliability of this claim.
- The claim that the method "outperforms traditional semi-supervised approaches like TSVM" is based on a limited comparison with only two SSL baselines, and the results for DBP1 show the proposed method performing slightly worse than TSVM on sensitivity, which is not fully discussed.
- The assertion that ESM-1b serves "strictly as a static feature extractor" and that its potential "cannot be fully realized without our self-training framework" is not directly tested. An experiment using ESM-1b features with a supervised classifier (without self-training) is reported as the SVM0 baseline, but the comparison is not framed as a direct test of this claim.
- The generalizability of the approach to other biological sequence classification tasks beyond DBP and ncRNA detection is claimed but not demonstrated.