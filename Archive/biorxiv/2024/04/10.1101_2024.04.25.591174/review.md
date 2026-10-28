## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data accessibility, conflict of interest, acknowledgments, footnotes)
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and clarity of the manuscript as provided. No assessment of formatting or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors test whether flexible machine learning models, specifically convolutional neural networks (CNNs), can learn cis-regulatory sequence features that predict gene expression responses to cold in Arabidopsis thaliana, using natural variation across five accessions. They report moderate predictive accuracy, identify enriched sequence motifs in differentially expressed genes, and conclude that current sequence-only approaches are limited by biological complexity and the need for additional data types.
- **Visible evidence base** Abstract, introduction, methods, results, discussion, figure legends (referenced but not shown), tables (referenced but not shown), supplementary materials (referenced but not shown)
- **Missing materials affecting confidence** Figures, tables, supplementary tables (S1-S11), supplementary figures (S1-S10), and the supplemental material on the tt8 knockout analysis are referenced but not provided. These are essential for evaluating the validity of the reported results.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question: whether DNA sequence alone, through cis-regulatory regions, can predict gene expression responses to environment. The authors apply a reasonable and increasingly common approach (CNNs) to a well-characterized system (Arabidopsis cold response) with multiple accessions. However, the reported predictive performance is modest, and the manuscript does not clearly establish that the approach outperforms simpler baselines or that the identified motifs are functionally meaningful. The lack of figures, tables, and supplementary materials prevents full evaluation of the methods and results. The manuscript is honest about limitations, which is commendable, but the central claim that CNNs can learn cis-regulatory genotype-to-phenotype maps is only weakly supported by the evidence presented.
- **Who would be interested in the results, and why** Researchers in plant genomics, gene regulation, evolutionary biology, and computational biology would be interested. The work speaks to the feasibility of predicting expression responses from sequence, which is relevant for understanding adaptation, improving crop breeding strategies, and developing predictive models for non-model species. The negative or modest results are also informative for the community developing machine learning approaches for regulatory genomics.
- **Major strengths** The study addresses a fundamental and unresolved question in regulatory genomics. The use of multiple Arabidopsis accessions captures natural genetic variation, which is a strength. The authors are transparent about the limitations of their approach and do not overstate their findings. The inclusion of a spike-in positive control is a thoughtful way to assess model capability. The comparison of sequence-only models with and without additional information is a useful framework.
- **Major Concerns** The central claim of moderate predictive accuracy is difficult to evaluate without the actual performance metrics, figures, and tables. The manuscript does not provide a clear comparison to simpler baseline models, which is essential for interpreting the value of the CNN approach. The biological interpretation of the enriched motifs is speculative, as the authors do not demonstrate functional validation or link motifs to known regulatory mechanisms beyond sequence overlap. The analysis of trans-effects via CBF genotypes is interesting but the results are not clearly presented. The manuscript lacks a clear statement of the null hypothesis and what would constitute meaningful improvement over chance.
- **Technical failings that need to be addressed before the case is established** The absence of all figures, tables, and supplementary materials is a major technical failing that prevents verification of the results. The methods for CNN training, hyperparameter selection, and evaluation are described but the actual outcomes are not visible. The spike-in experiment is described but the results are not shown. The comparison between models trained on different accession sets is mentioned but not quantified in the text.
- **Assessment against Nature-style criteria** Originality: The question is not entirely novel, as similar approaches have been applied in other species, but the focus on natural variation in Arabidopsis and the explicit test of cis-regulation is a reasonable contribution. Scientific importance: The question is important, but the modest results and lack of clear improvement over existing methods limit the impact. Interdisciplinary readership: The topic bridges genomics, evolution, and machine learning, which could attract a broad audience, but the presentation is quite technical and may not be accessible to nonspecialists. Technical soundness: The methods are generally sound in principle, but the lack of visible results and the absence of baseline comparisons undermine confidence. Readability for nonspecialists: The manuscript is dense and assumes significant background knowledge; the abstract is clear but the body is not easily accessible.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the missing materials and lack of clear performance metrics prevent a supportive recommendation. The authors should provide all figures, tables, and supplementary materials, add baseline comparisons, and clarify the biological significance of their findings.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that CNNs predicted differential expression with moderate accuracy, with evidence that predictions were hindered by biological complexity and the large potential regulatory code.
- **Evidence pointer** Results section, "Predicting gene expression regulation based on regulatory regions using naive methods is possible"; Figure 2; Tables 2; S5-S11 Tables; S2-S4 Figures
- **Concern** The central result of the paper, the predictive accuracy of the CNNs, is not visible in the provided text. The authors report median and mean prAUC values for training and test sets, but the actual distributions, the selected best models, and the comparison to chance are not shown. The figures and tables that would contain this information are referenced but not provided.
- **Why it matters** Without the actual performance metrics, the reader cannot assess whether the claimed moderate accuracy is meaningful, whether the models are overfitting, or whether the approach has any practical utility. The claim that predictions were hindered by biological complexity is an interpretation that requires the data to support it.
- **Resolution test** Provide all figures and tables, including the distribution of prAUC values across the 1,344 models, the performance of the selected best models, and a comparison to a random or baseline model. Show the confusion matrices or precision-recall curves for the test sets.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline comparison
- **Claim pointer** The authors state that random forest models based on known TFBS were not able to predict DEGs with high accuracy, and that CNNs provided better prediction.
- **Evidence pointer** Results section, "Known transcription factor binding sites within Col-0 do not accurately predict the expression response to cold using random forests"; S1 Figure
- **Concern** The manuscript does not provide a direct comparison between the CNN models and the random forest models, nor does it compare the CNN performance to a simple baseline such as predicting the majority class or using sequence composition features. The claim that CNNs are better is not supported by a head-to-head comparison.
- **Why it matters** Without a baseline comparison, the reader cannot determine whether the CNN approach adds value over simpler methods. The random forest result is reported as low accuracy, but the CNN result is also modest, so the improvement may be marginal or not statistically significant.
- **Resolution test** Provide a direct comparison of prAUC or other relevant metrics between the CNN models, the random forest models, and a simple baseline (e.g., predicting all genes as non-DEGs). Include confidence intervals or statistical tests for the differences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological interpretation
- **Claim pointer** The authors claim that the discovered motifs significantly overlap with known transcription factor binding sites, including DOF family members, and that this suggests a potential role in cold response.
- **Evidence pointer** Results section, "The presence of enriched motifs in the up regulated DE gene sequences suggests their potential contribution to environmental response"; Figure 1; Table 1; S3-S4 Tables
- **Concern** The overlap with known TFBS is reported as significant, but the methods for this comparison are not described in sufficient detail. The authors do not state how the significance of the overlap was calculated, what background model was used, or whether multiple testing was accounted for. The biological interpretation that these motifs contribute to cold response is speculative without functional validation.
- **Why it matters** The identification of enriched motifs is a key part of the paper's narrative, but without rigorous statistical analysis and functional context, the motifs could be spurious or non-functional. The claim that they are related to cold response requires more evidence.
- **Resolution test** Describe the statistical method for assessing motif enrichment and overlap with known TFBS, including the background model and multiple testing correction. Provide the full list of motifs and their associated statistics. If possible, validate a subset of motifs experimentally or with independent data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Trans-effect control
- **Claim pointer** The authors state that training models on accessions with similar CBF genotypes did not improve prediction, suggesting that trans-effects are not the primary limitation.
- **Evidence pointer** Results section, "Predicting only among genotypes sharing alleles for major trans eQTL does not improve the prediction of the up-regulated DEGs"; S7-S8 Figures; S8 Table
- **Concern** The analysis of CBF genotypes is described but the results are not shown. The authors do not provide the performance metrics for the models trained on the different accession sets, nor do they compare them statistically. The conclusion that trans-effects are not the primary limitation is not supported by visible data.
- **Why it matters** The CBF analysis is intended to address a potential confounding factor, but without the results, the reader cannot evaluate whether the conclusion is justified. This is important for interpreting the overall findings.
- **Resolution test** Provide the performance metrics for models trained on the different accession sets, including the prAUC distributions and the selected best models. Include a statistical comparison between the models trained on all accessions versus those trained on subsets.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Spike-in control
- **Claim pointer** The authors state that the spike-in experiment showed that models can learn a simple artificial signal, but with limitations.
- **Evidence pointer** Results section, "CNNs imperfectly identify a simple artificial signal within the regulatory regions"; Figure 2; S6 Figure; S7 Table
- **Concern** The spike-in experiment is described but the results are not shown. The authors report that the spike improved prediction accuracy, but the actual metrics, the comparison to non-spiked models, and the interpretation of the limitations are not visible.
- **Why it matters** The spike-in is a critical control to assess whether the CNN architecture is capable of learning a perfect signal in this data setting. Without the results, the reader cannot determine whether the modest performance on real data is due to model limitations or biological complexity.
- **Resolution test** Provide the performance metrics for the spike-in models, including the prAUC distributions, the accuracy for each class, and a comparison to the non-spiked models. Show the effect of the spike on model performance across different hyperparameter settings.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, "Transcriptome and genome data"
- **Evidence pointer** Methods section, "Transcriptome and genome data"
- **Issue** The description of the data processing is brief. The authors state that they used published pseudogenomes and the differentially expressed gene dataset, but do not describe how the sequence regions were extracted, how the one-hot encoding was implemented, or how the train-test split was performed.
- **Required correction** Provide more detail on the data processing pipeline, including the exact coordinates of the extracted regions, the handling of ambiguous bases, and the random seed or stratification used for the train-test split.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, "The presence of enriched motifs in the up regulated DE gene sequences suggests their potential contribution to environmental response"
- **Evidence pointer** Results section, "The presence of enriched motifs in the up regulated DE gene sequences suggests their potential contribution to environmental response"
- **Issue** The authors report p-values for motif enrichment but do not state the statistical test used or the number of comparisons. The p-values are presented without context.
- **Required correction** Specify the statistical test used for motif enrichment, the multiple testing correction applied, and the total number of motifs tested.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the tt8 knockout analysis is very brief and is relegated to the supplemental material. Given that this is a simpler biological system, the results could provide important context for interpreting the cold response results.
- **Required correction** Provide a summary of the tt8 knockout results in the main text, including the performance metrics and a comparison to the cold response results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data Accessibility section
- **Evidence pointer** Data Accessibility section
- **Issue** The authors provide GitHub repositories for scripts, but do not specify the versions of software packages used or provide a detailed README. The reproducibility of the analysis is not fully ensured.
- **Required correction** Provide a detailed description of the software environment, including package versions, and ensure the repositories include a clear README with instructions for running the analysis.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that CNNs predicted differential expression with moderate accuracy, but does not provide a numerical value or a comparison to a baseline. This makes it difficult for readers to gauge the practical significance.
- **Required correction** Include a specific performance metric (e.g., prAUC value) and a brief comparison to a baseline model in the abstract.

## Risk / unsupported claims
- The claim that CNNs predicted differential expression with moderate accuracy is unsupported because the actual performance metrics are not provided in the visible text.
- The claim that the discovered motifs significantly overlap with known TFBS is unsupported because the statistical methods and results are not fully described.
- The claim that including multiple accessions improves motif discovery is not supported by a quantitative comparison.
- The claim that trans-effects are not the primary limitation is unsupported because the results of the CBF genotype analysis are not shown.
- The claim that the spike-in experiment demonstrates model capability is unsupported because the results are not shown.
- The claim that the tt8 knockout analysis highlights the challenge of predicting transcriptomic dynamics is unsupported because the results are not provided in the main text.