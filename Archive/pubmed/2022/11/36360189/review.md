## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Technical soundness, methodological validity, reproducibility, and interpretation of results as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose GHTNet, a transformer-based model integrating DNA sequence, DNA shape, histone modification patterns, chromatin accessibility, and conservation scores to predict tissue-specific TF-DNA binding. They claim superior performance over existing methods, identify tissue-specific importance of chromatin features, demonstrate cross-species transferability, and provide downstream applications including motif discovery and disease association analysis.
- **Visible evidence base** Main text including abstract, introduction, methods, results, discussion; references to supplementary figures and tables (S1–S13, Tables S2–S4) whose contents are not provided
- **Missing materials affecting confidence** Supplementary materials (figures S1–S13, tables S2–S4, texts S1–S2), detailed hyperparameter configurations, exact dataset composition per tissue/TF, code availability, and full comparison results

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational genomics: predicting tissue-specific TF-DNA binding using multiple chromatin features. The transformer-based architecture is a reasonable methodological choice given the success of attention mechanisms in capturing long-range dependencies. However, the manuscript has several significant technical weaknesses that undermine confidence in the reported results. The evaluation methodology is incompletely described, statistical rigor is inconsistent, and several claims exceed what the presented evidence can support. The cross-species and disease analyses are interesting but preliminary. The manuscript would benefit from substantial revision and additional validation before the claims can be considered established.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on TF binding prediction, regulatory genomics, and deep learning applications in genomics would be the primary audience. Researchers studying tissue-specific gene regulation and chromatin biology may also find the feature importance analyses relevant. The cross-species transferability results could interest those working on model organisms where human data are limited. The disease association analysis may appeal to researchers studying Alzheimer's disease and related neurodegenerative conditions.

- **Major strengths** 
  1. The problem is well-motivated and addresses a genuine gap: most existing methods rely primarily on DNA sequence, and systematic analysis of multiple chromatin features for tissue-specific binding is limited.
  2. The transformer-based architecture with a hybrid design (pseudo Siamese C-transformer and CNN modules) is a sensible approach for integrating heterogeneous data types.
  3. The use of word2vec for k-mer embedding is a reasonable strategy to address high-dimensionality of one-hot encoded sequences.
  4. The manuscript includes multiple analyses (feature importance, cross-species transfer, disease association) that go beyond simple prediction and attempt biological interpretation.
  5. The writing is generally clear and the logical flow from problem statement to methods to results is coherent.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "GHTNet achieves Acc of 92.79%, yielding extra 8.29%, 8.02%, 7.92%, 8.49%, and 6.38% improvements over CNN_Zeng, DanQ, DeepSEA, DLBSS, and FactorNet, respectively"
- **Evidence pointer** Section 3.1.1, Table 1
- **Concern** The reported accuracy improvements are substantial (6–8 percentage points), yet the manuscript does not describe the evaluation protocol in sufficient detail. It is unclear whether the comparison methods were retrained on the same data splits, whether hyperparameters were optimized for each method, and whether the same train/validation/test partitions were used across all methods. The claim of "fair comparison" is stated but not demonstrated. Additionally, the manuscript reports accuracy, AUROC, and AUPRC, but does not report confidence intervals or variance across cross-validation folds. Given the modest performance differences reported in ablation studies (e.g., 0.0019–0.0066 AUROC changes), the large improvements over baselines require scrutiny regarding potential data leakage or evaluation inconsistencies.
- **Why it matters** If the comparison is not conducted under strictly controlled conditions, the central claim of superior performance is not established. The magnitude of improvement is unusually large for this type of problem and could indicate methodological differences in evaluation rather than genuine model superiority.
- **Resolution test** The authors should provide a detailed description of the evaluation protocol, including data splitting, hyperparameter selection for each method, and statistical significance testing with confidence intervals. Ideally, they should release code and data splits to allow independent reproduction.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "The GHTNet decodes the relationship between tissue-specific TF-DNA binding and chromatin features via a specific input scheme of alternative inputs"
- **Evidence pointer** Section 2.2, Figure 2
- **Concern** The architecture description is insufficient for reproduction. The manuscript states that the pseudo Siamese C-transformer module consists of "a multi-head self-attention layer and a C-FFN" but does not specify key architectural details: number of attention heads, embedding dimensions, number of transformer layers (beyond stating L=2), filter sizes and counts in the CNN components, pooling strategies, or the exact fusion mechanism for the pseudo Siamese branches. The "specific input scheme of alternative inputs" is not clearly defined. The supplementary materials are referenced but not provided for review.
- **Why it matters** Without complete architectural specifications, the work cannot be reproduced or built upon by other researchers. This is a fundamental requirement for computational method papers.
- **Resolution test** Provide a complete architectural specification in the main text or supplementary materials, including all hyperparameters, layer dimensions, and the exact input encoding scheme for each feature type. Release code to enable reproduction.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "The results suggest that the importance of these TF-DNA binding features varies across tissues"
- **Evidence pointer** Section 3.2, Figures 4–5, Supplementary Table S2
- **Concern** The manuscript reports differences in feature importance across tissues and TFs, but the statistical analysis is unclear. For example, the claim that "DNA shape is more important than the sequence" for POLR2A in testis tissue is based on a single comparison without reporting variance, effect size, or significance testing. The leave-one-out strategy for assessing feature importance is mentioned but the methodology is not described in detail. It is unclear how many replicates were performed, whether the observed differences are consistent across cross-validation folds, and whether multiple testing corrections were applied given the large number of comparisons (20 TFs × 34 tissues × multiple features).
- **Why it matters** The biological conclusions about tissue-specific feature importance are a key contribution of the paper. If these are not statistically robust, the biological interpretations are not reliable.
- **Resolution test** Provide a clear statistical framework for comparing feature importance across conditions, including appropriate multiple testing corrections. Report variance across folds and effect sizes for key claims.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** "Cross-species studies address the limited data, thus providing new ideas in this case" and "The results show that human and mouse TF-DNA binding mechanisms are very similar"
- **Evidence pointer** Section 3.3, Figure 6, Supplementary Table S4
- **Concern** The cross-species transfer experiment is described at a high level but critical details are missing. The manuscript states that "all HM patterns common to humans and mice were collected" but does not specify which marks, how many tissues, or how the transfer was performed. The claim that "TFBSs in the control group were well predicted after the model transfer with AUROC decreased by less than 0.01" is presented without statistical context. It is unclear whether the transferred model was fine-tuned on human data or used directly, and whether the comparison accounts for differences in data quality between species.
- **Why it matters** The cross-species transferability claim has practical implications for using mouse models to study human gene regulation. If the methodology is not clearly described, the claim cannot be evaluated or applied by others.
- **Resolution test** Provide detailed experimental setup for cross-species transfer, including data composition, transfer protocol (direct vs. fine-tuned), and statistical comparison with appropriate controls.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability validation
- **Claim pointer** "The GHTNet has excellent interpretability, and the critical biological regions it captures allow us to understand its decision-making process"
- **Evidence pointer** Section 3.4.1, Figure 7, Supplementary Figures S6–S7, S11
- **Concern** The interpretability analysis is presented as a strength, but the validation is limited. The manuscript reports that 78 of 91 identified motifs matched JASPAR database entries, but does not provide the matching criteria, the distribution of e-values/p-values, or a comparison with motifs identified by existing methods. The attention map visualization is qualitative, and no quantitative assessment of whether attention weights correspond to known functional regions is provided. The claim that "there are still many regions that models consider important whose functions are not yet known" is presented without evidence that these regions are genuinely functional rather than artifacts.
- **Why it matters** Interpretability claims are increasingly scrutinized in deep learning for genomics. Without rigorous validation, the interpretability analysis is suggestive but not conclusive.
- **Resolution test** Provide quantitative evaluation of motif discovery (e.g., comparison with known motifs using established metrics), statistical enrichment analysis of attention-highlighted regions for known functional elements, and comparison with interpretability from baseline methods.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Clinical relevance
- **Claim pointer** "The GHTNet is applied to interpret the relationship among TFs, chromatin features, and diseases associated with AD46 tissue"
- **Evidence pointer** Section 3.4.2, Figure 8, Supplementary Figures S8–S10
- **Concern** The disease association analysis is the weakest section methodologically. The manuscript reports differences in HM importance between disease groups (normal, MCI, AD, CI, AD+CI) but the sample sizes are very small (e.g., three samples in the CI and AD+CI groups). The claim that "on average the importance of these HM patterns was lower in AD and MCI patients than in the normal group" is based on these small samples without statistical testing. The visualization of HM expression at ±1000 bp from ChIP-seq peaks is descriptive, and no formal statistical comparison between groups is reported.
- **Why it matters** The disease analysis is presented as a downstream application demonstrating the utility of the model. If the analysis is not statistically sound, it could mislead readers about the clinical relevance of the findings.
- **Resolution test** Provide appropriate statistical tests for group comparisons, account for small sample sizes, and clearly state the exploratory nature of these findings.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "achieving about a 5% absolute improvement over existing methods" but the results section reports 8.29%, 8.02%, 7.92%, 8.49%, and 6.38% improvements in accuracy. The abstract understates the reported results, creating inconsistency.
- **Required correction** Align the abstract with the results section or clarify what metric the 5% improvement refers to.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The description of negative sample selection is vague: "the regions with similar GC content to positive sequences were selected as negative sequences from the whole genome." It is unclear how many negative samples were selected per positive sample, whether they were matched for other properties, and whether the same negative set was used across all TFs and tissues.
- **Required correction** Provide a detailed description of negative sample generation, including matching criteria and the ratio of negative to positive samples.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.3.2
- **Evidence pointer** Section 2.3.2
- **Issue** The training procedure states that "five-fold cross-validation was used, and the average is taken as the final result" but does not specify whether the test set is held out within each fold or whether the same test set is used across folds. The relationship between the 80/10/10 split and the five-fold cross-validation is unclear.
- **Required correction** Clarify the relationship between the train/validation/test split and the cross-validation procedure.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.1.1
- **Evidence pointer** Section 3.1.1, Table 1
- **Issue** The manuscript reports p-values for some comparisons (e.g., p = 2.30 × 10−5) but does not describe the statistical test used or whether multiple testing corrections were applied.
- **Required correction** Describe the statistical tests used and specify whether corrections for multiple comparisons were applied.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2.1
- **Evidence pointer** Section 3.2.1, Figure 4
- **Issue** The text states "DNA shape is more important than the sequence" for POLR2A in testis tissue, but the basis for this claim is unclear. The figure is referenced but not described in sufficient detail to understand what comparison is being made.
- **Required correction** Clearly describe the comparison being made and provide the quantitative results supporting this claim.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Section 3.3
- **Evidence pointer** Section 3.3
- **Issue** The final sentence states "The above results indicate a high similarity for the TFs binding features in humans and ice." The word "ice" appears to be a typo for "mice."
- **Required correction** Correct the typo.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.4.1
- **Evidence pointer** Section 3.4.1
- **Issue** The manuscript reports "A total of 91 motifs were identified, 78 motifs were matched to the JASPAR databases, and the other 14 were undocumented." The numbers do not add up (78 + 14 = 92, not 91).
- **Required correction** Correct the numerical inconsistency.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Section 2.2.1
- **Evidence pointer** Section 2.2.1
- **Issue** The description of the encoding module states that "the encoding dimension was 5k" for one-hot encoding, but this appears to be a simplification. For k-mers with 5 possible characters, the dimension should be 5^k, not 5k.
- **Required correction** Clarify the encoding dimension calculation.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.3.1
- **Evidence pointer** Section 2.3.1
- **Issue** The word2vec training procedure is described but the corpus used for training is not specified. It is unclear whether the word2vec model was trained on the same sequences used for GHTNet training or on a separate corpus.
- **Required correction** Specify the training corpus for the word2vec model.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The comparison methods are listed but their implementations are not described. It is unclear whether the authors used published implementations, reimplemented the methods, or used available software packages.
- **Required correction** Provide details on the implementations of comparison methods.

## Risk / unsupported claims
- The claim of "about 5% absolute improvement over existing methods" in the abstract is not consistent with the results section, which reports larger improvements.
- The claim that "DNA shape is more important than the sequence" for POLR2A in testis tissue is not supported by sufficient statistical evidence.
- The claim that "human and mouse TF-DNA binding mechanisms are very similar" is based on transfer learning results that are not fully described.
- The disease association analysis claims are based on very small sample sizes (n = 3 for some groups) without appropriate statistical treatment.
- The claim that "the GHTNet has excellent interpretability" is not quantitatively validated.
- The numerical inconsistency in motif counts (91 vs. 78 + 14) undermines confidence in the reported results.
- The claim that "the GHTNet is an accurate and robust framework" is not fully supported given the incomplete evaluation methodology description.
- The cross-species transferability claim is presented as a solution to limited data, but the practical utility is not demonstrated with concrete examples.
- The relationship between TF binding, chromatin features, and disease is described as "significant" but no statistical measures of significance are provided for the disease analysis.