## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and acknowledgments. No supplementary files, figures, or tables were provided beyond those referenced in the text.
- **Assessment boundary** The review assesses the scientific claims, methodological soundness, and interpretative validity of the study as presented in the manuscript. It does not evaluate the editorial fit for a specific journal.
- **Shared manuscript claim summary** The authors claim that convolutional neural networks (CNNs) trained on proximal DNA sequence (upstream and downstream of genes) can predict cold-responsive differential gene expression in Arabidopsis thaliana with moderate accuracy, and that this approach is limited by biological complexity, trans-acting variation, and the need for additional data types. They also report de novo motif discovery in regulatory regions of differentially expressed genes and show that known transcription factor binding sites do not predict expression status well using random forests.
- **Visible evidence base** The manuscript text includes descriptions of methods, results, and statistical tests. Specific numerical results are reported for motif counts, prAUC values, p-values, and model performance metrics. No raw data, code, or supplementary tables are available for independent verification.
- **Missing materials affecting confidence** Supplementary tables (S1–S11), figures (S1–S10), the full set of 1344 model architectures, the specific hyperparameter grid, the permutation test details, and the tt8 knockout analysis results are referenced but not provided. This limits the ability to verify the robustness of the reported findings and the validity of the statistical comparisons.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question in evolutionary genomics: whether DNA sequence alone can predict gene expression responses to the environment. The authors use a reasonable combination of motif discovery and deep learning approaches, and they are appropriately cautious in interpreting their moderate results. However, the study is largely exploratory and the predictive performance is modest, with several methodological details and validation steps that are either underreported or not reported at all. The claim that CNNs can predict cold-responsive differential expression is only weakly supported by the evidence presented, and the manuscript would benefit from clearer reporting of model selection, cross-validation, and the biological interpretation of the learned features.
- **Who would be interested in the results, and why** Researchers in plant evolutionary genomics, regulatory genomics, and computational biology would be interested in this work. The study addresses the feasibility of using sequence-based deep learning to predict expression plasticity, which is relevant for understanding adaptation to environmental stress. The negative and moderate results are informative for the community developing predictive models of gene regulation, particularly in non-model systems where additional omics data are scarce.
- **Major strengths** The study uses a multi-genotype design, which is more realistic than single-genotype analyses and allows for some assessment of GxE. The authors include a positive control (spike-in experiment) to test the capacity of the CNN architectures, which is a useful diagnostic. The manuscript is honest about the limitations of the approach and does not overstate the predictive power. The use of de novo motif discovery in both up- and down-regulated genes is a reasonable exploratory step.
- **Major Concerns** The concerns below detail issues with the predictive performance, the interpretation of the spike-in experiment, the handling of trans-acting variation, the lack of cross-validation details, and the incomplete reporting of the tt8 control analysis.
- **Minor Comments** Several smaller issues relate to clarity of reporting, statistical details, and the interpretation of motif enrichment.
- **Technical failings that need to be addressed before the case is established** The core claim of moderate predictive accuracy is not well established because the reported prAUC values are close to what might be expected from class imbalance or trivial features, and the manuscript does not report a proper baseline comparison. The spike-in experiment is described as a positive control, but the results are not clearly interpreted in terms of what they imply for the real-data performance. The handling of trans-acting variation is incomplete, and the conclusion that trans-effects limit prediction is not directly tested. The tt8 analysis is mentioned but not described in sufficient detail to assess its validity.
- **Assessment against Nature-style criteria** Originality: The question is not entirely new, but the specific combination of multi-genotype sequence data and CNN-based prediction of cold-responsive expression is a reasonable contribution. Scientific importance: The topic is important, but the moderate results and the lack of a clear biological insight limit the potential impact. Interdisciplinary readership: The work is likely to appeal to a specialized audience in plant genomics and computational biology, but the presentation is not sufficiently accessible for a broader readership. Technical soundness: The methods are generally appropriate, but the reporting is incomplete in several areas, and the lack of cross-validation and baseline comparisons weakens the technical case. Readability for nonspecialists: The manuscript is written in a technical style that assumes familiarity with deep learning and genomics, and the abstract and introduction do not provide enough context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an exploratory analysis with modest results, but the core claims are not sufficiently supported by the evidence as reported. The authors should address the technical concerns, provide additional validation, and clarify the interpretation of their findings before the case is made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Predictive performance and baseline comparison
- **Claim pointer** The authors claim that CNNs predicted differential expression with moderate accuracy, with prAUC values around 0.7 for the best models.
- **Evidence pointer** Section 3.3, Section 3.5, Tables 2, S5–S7
- **Concern** The reported prAUC values of approximately 0.7 are described as moderate, but the manuscript does not provide a baseline comparison to a trivial model or a model trained on shuffled or permuted sequences. Given the class imbalance (approximately 1:11 ratio of DEGs to non-DEGs), a model that predicts the majority class would achieve a high accuracy but a low prAUC. The authors do not report the prAUC of a null model or a model trained on random sequences, which is essential to interpret whether the CNN is learning meaningful sequence features. The permutation test described in Section 3.3 is mentioned, but the results are not reported in detail, and it is unclear whether the permutation was performed on the labels or the sequences.
- **Why it matters** Without a proper baseline, the claim of moderate predictive accuracy is not interpretable. The prAUC values could be driven by trivial features such as GC content or sequence length, rather than by cis-regulatory motifs. The authors need to demonstrate that the CNN is learning sequence features that are specifically associated with cold-responsive expression, rather than general properties of DEGs or non-DEGs.
- **Resolution test** The authors should report the prAUC of a model trained on shuffled or permuted sequences, as well as the prAUC of a model that always predicts the majority class. They should also report the distribution of prAUC values from the permutation test and the p-value for the observed prAUC. If the observed prAUC is not significantly higher than the null distribution, the claim of moderate accuracy is not supported.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of the spike-in experiment
- **Claim pointer** The authors state that the spike-in experiment (inserting a 5 bp sequence in the upstream region of up-regulated DEGs) improved model performance, suggesting that the models can learn a simple, high-effect signal.
- **Evidence pointer** Section 3.5, Figure 2, Table S7
- **Concern** The spike-in experiment is described as a positive control, but the results are not clearly interpreted. The authors report that the spiked models had higher prAUC values than the non-spiked models, but they do not report the magnitude of the improvement or whether the improvement is statistically significant. More importantly, the spike-in experiment does not directly address the question of whether the models are learning biologically relevant cis-regulatory motifs in the real data. The spike is an artificial, perfectly predictive signal, and its detection does not imply that the models are capturing the complex, weak, and variable signals present in real regulatory regions. The authors also do not report whether the spike-in experiment was performed for the down-regulated DEGs or for the tt8 control.
- **Why it matters** The spike-in experiment is used to argue that the models are capable of learning sequence features, but this does not validate the biological relevance of the features learned from real data. The authors need to show that the models are learning motifs that are known to be involved in cold response, or that the learned features are enriched for known transcription factor binding sites, in order to support the claim that the approach is useful for understanding the cis-regulatory code.
- **Resolution test** The authors should report the full results of the spike-in experiment, including the distribution of prAUC values for spiked and non-spiked models, and a statistical test comparing the two distributions. They should also perform a motif analysis of the learned CNN filters to determine whether they correspond to known cold-responsive transcription factor binding sites. If the learned features are not biologically interpretable, the claim that the approach can learn the cis-regulatory code is weakened.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Handling of trans-acting variation
- **Claim pointer** The authors state that including multiple genotypes did not improve prediction accuracy and that trans-acting variation at high frequency may limit predictions.
- **Evidence pointer** Section 3.6, Section 3.8, Figures S7, S9, Tables S8, S10
- **Concern** The authors test the effect of trans-acting variation by training models on subsets of genotypes that share similar CBF alleles, but the analysis is incomplete. They report that the models trained on genotypes with similar CBF alleles did not perform better than the full model, but they do not report the results of the models trained on genotypes with different CBF alleles. The authors also do not directly test the hypothesis that trans-acting variation limits prediction by comparing models trained on genotypes with and without known trans-eQTL. The conclusion that trans-acting variation is a limiting factor is therefore not directly supported by the data presented.
- **Why it matters** The authors' interpretation of their results hinges on the idea that trans-acting variation, particularly in the CBF genes, confounds the prediction of cis-regulatory effects. Without a direct test of this hypothesis, the conclusion is speculative. The authors should either provide a more direct test of the role of trans-acting variation or temper their interpretation.
- **Resolution test** The authors should train models on genotypes with and without known trans-eQTL and compare the performance. They should also report the results of the models trained on genotypes with different CBF alleles. If the models trained on genotypes with similar CBF alleles perform better than those trained on genotypes with different CBF alleles, this would support the hypothesis. If not, the authors should revise their interpretation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reporting of the tt8 control analysis
- **Claim pointer** The authors state that the tt8 knockout line, which has a simpler transcriptional response, also showed modest prediction accuracy, but the details are not provided.
- **Evidence pointer** Section 3.8, Supplementary Materials
- **Concern** The tt8 control analysis is mentioned only briefly, and the results are not reported in the main text. The authors state that the predictions were modest, but they do not provide the prAUC values, the number of DEGs, or the model architecture used. This makes it impossible to assess whether the tt8 control is a valid comparison for the cold response. The tt8 knockout is expected to have a simpler regulatory architecture, so if the CNN also performs poorly on this simpler system, it suggests that the limitations are not specific to the complexity of the cold response.
- **Why it matters** The tt8 control is potentially informative for interpreting the limitations of the approach. If the CNN cannot predict a simpler transcriptional response, this suggests that the model architecture or the sequence features are insufficient, rather than the biological complexity of the cold response. The authors should report the full results of the tt8 analysis to allow readers to evaluate this comparison.
- **Resolution test** The authors should report the prAUC values, the number of DEGs, and the model architecture for the tt8 control analysis. They should also compare the performance of the tt8 model to the cold response model and discuss the implications for the interpretation of their results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of motif enrichment results
- **Affected element** Section 3.1, Figure 1, Tables S3, S4
- **Evidence pointer** Section 3.1
- **Issue** The authors report the number of motifs discovered in up- and down-regulated DEGs, but they do not provide the motif sequences or the enrichment statistics for each motif. The statement that "the majority of the discovered motifs were significantly enriched in high frequency" is vague, and the reader cannot assess the biological relevance of the motifs without seeing the sequences and their associated p-values.
- **Required correction** The authors should provide the motif sequences, their enrichment p-values, and the frequency of each motif in the DEG and non-DEG sets. This would allow readers to evaluate the biological significance of the discovered motifs.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting of model performance
- **Affected element** Section 3.3, Tables 2, S5–S7
- **Evidence pointer** Section 3.3
- **Issue** The authors report prAUC values for the best models, but they do not report the standard deviation or confidence intervals for these values. The performance of deep learning models can be highly variable depending on the random initialization and the train-test split, and the authors should report the variability across multiple runs.
- **Required correction** The authors should report the mean and standard deviation of the prAUC values across multiple training runs, or at least provide the range of values observed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of the random forest results
- **Affected element** Section 3.2, Figure S1
- **Evidence pointer** Section 3.2
- **Issue** The random forest analysis using known transcription factor binding sites showed low prAUC values, but the authors do not discuss the potential reasons for this. The low performance could be due to the incompleteness of the known binding site database, the use of a single genotype, or the fact that the binding sites are not informative for the specific cold response. The authors should provide a more detailed interpretation of this result.
- **Required correction** The authors should discuss the potential reasons for the low performance of the random forest model and how this relates to the CNN results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity of the spike-in experiment description
- **Affected element** Section 3.5, Figure 2
- **Evidence pointer** Section 3.5
- **Issue** The description of the spike-in experiment is unclear. The authors state that they "replaced the first 5 bp of the upstream region of up-regulated DEGs with the sequence AAGGG," but it is not clear whether this was done for all up-regulated DEGs or only a subset, and whether the spike was inserted in the same position for all genes. The authors should provide a clearer description of the spike-in procedure.
- **Required correction** The authors should describe the spike-in procedure in more detail, including the number of genes affected, the position of the spike, and whether the spike was inserted in both the upstream and downstream regions.

## Risk / unsupported claims
- The claim that CNNs predict cold-responsive differential expression with moderate accuracy is not fully supported because no baseline comparison is provided and the permutation test results are not reported in detail.
- The claim that trans-acting variation, particularly in the CBF genes, limits prediction is not directly tested and is therefore speculative.
- The claim that the tt8 control analysis supports the interpretation of the cold response results is unsupported because the tt8 results are not reported in sufficient detail.
- The claim that the discovered motifs are biologically relevant is not fully supported because the motif sequences and enrichment statistics are not provided.
- The claim that the approach could be useful for non-model systems is speculative and not directly tested in this study.