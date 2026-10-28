## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplemental figure/table legends
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and clarity of the presented work
- **Shared manuscript claim summary** The authors present deepTFBS, a deep learning framework combining multi-task learning and transfer learning to predict transcription factor binding sites (TFBSs) within and across plant species. They report superior performance over PWM, DeepSEA, DanQ, and an adapted BPNet in Arabidopsis, improved cross-species prediction in wheat, and experimental validation of WUS target predictions via yeast one-hybrid assays.
- **Visible evidence base** Main text figures 1-6 (referenced), supplemental figures 1-9, supplemental tables S1-S8, methods section, and abstract
- **Missing materials affecting confidence** Actual figure images, supplemental data files, model architecture diagrams, hyperparameter details, and complete benchmark results are not provided in the submitted text

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in plant genomics, namely the prediction of TFBSs in species with limited experimental data. The proposed framework combining multi-task and transfer learning is conceptually sound and the reported performance improvements are notable. However, several methodological details, evaluation choices, and statistical considerations require clarification and strengthening before the claims can be fully assessed. The cross-species application and experimental validation are commendable, but the evidence presented in the text alone is insufficient to fully evaluate the robustness of the approach.
- **Who would be interested in the results, and why** Plant molecular biologists studying transcriptional regulation, computational biologists developing deep learning methods for genomics, and researchers working on non-model plant species where TF binding data are scarce. The framework's ability to transfer knowledge across species could be of broad interest to the gene regulation community.
- **Major strengths** 1) The problem addressed is important and timely, particularly the cross-species prediction aspect. 2) The multi-task and transfer learning strategy is well motivated and represents a sensible methodological contribution. 3) The inclusion of experimental validation via yeast one-hybrid assays strengthens the practical relevance. 4) The ablation study provides useful insight into architectural contributions. 5) The open-source availability and web server enhance usability and reproducibility.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The combination of multi-task and transfer learning for plant TFBS prediction is a reasonable incremental advance, though similar strategies have been explored in mammalian systems. Scientific importance: The cross-species prediction capability is valuable for plant research, but the demonstrated improvements over existing methods are modest and require more rigorous benchmarking. Interdisciplinary readership: The work bridges computational and plant biology, but the presentation assumes familiarity with deep learning terminology. Technical soundness: The core architecture is reasonable, but several evaluation and validation aspects need strengthening. Readability for nonspecialists: The abstract and introduction are accessible, but the results section becomes dense with technical details.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evaluation methodology
- **Claim pointer** The claim that deepTFBS-MT outperforms DeepSEA, DanQ, and BPNet with 49.15%, 23.32%, and other improvements in PRAUC
- **Evidence pointer** Results section, Figures 2E-2J, Supplemental Table S2
- **Concern** The comparison with baseline methods is described only in terms of aggregate improvements. It is unclear whether the reported improvements are statistically significant across the 359 TFs. No confidence intervals, significance tests, or per-TF distributions are presented. Additionally, the adaptation of BPNet from a regression to a classification task is described but the details of this adaptation are not provided, making it difficult to assess whether the comparison is fair.
- **Why it matters** Without statistical rigor, the reported performance gains could be within the range of random variation, particularly given the large number of TFs tested. A fair comparison requires that all methods are evaluated under identical conditions with appropriate statistical testing.
- **Resolution test** Provide per-TF performance distributions, paired statistical tests (e.g., Wilcoxon signed-rank test) comparing deepTFBS-MT against each baseline, and confidence intervals for the aggregate improvements. Clarify the exact adaptation of BPNet and ensure hyperparameter tuning is comparable across methods.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data leakage and evaluation protocol
- **Claim pointer** The claim that deepTFBS-MT achieves a median PRAUC of 0.629 on the Arabidopsis test set
- **Evidence pointer** Results section, Figure 2, Methods section "Sample generation and feature encoding"
- **Concern** The manuscript states that the Arabidopsis genome was divided into non-overlapping 200-bp bins and extended to 1,000 bp. It is unclear how the training, validation, and test sets were partitioned. If the partitioning was random at the bin level, adjacent bins from the same genomic region could appear in both training and test sets, leading to data leakage due to sequence similarity. The manuscript does not describe chromosome-level or region-level splitting.
- **Why it matters** Data leakage can inflate performance estimates and undermine the validity of the reported results. Genomic sequence similarity between training and test bins could allow the model to memorize rather than generalize.
- **Resolution test** Describe the exact partitioning strategy. If random bin-level splitting was used, re-evaluate with chromosome-level or at least non-overlapping region-level splitting to ensure no sequence overlap between training and test sets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Cross-species evaluation
- **Claim pointer** The claim that deepTFBS-TL yields a significant PRAUC improvement of 30.6% over baseline models in cross-species prediction of TFBS in wheat
- **Evidence pointer** Results section, Figure 5C, Supplemental Table S4
- **Concern** The cross-species evaluation is described only in terms of aggregate improvement. It is unclear how the wheat TF binding data were obtained, how the orthology between Arabidopsis and wheat TFs was established, and whether the evaluation was performed on held-out wheat data. The manuscript mentions "curated binding profiles for 110 TFs in wheat" but does not describe the curation process or the quality of these data.
- **Why it matters** Cross-species prediction is a central claim of the manuscript. Without a clear description of the data, orthology mapping, and evaluation protocol, the validity of the cross-species results cannot be assessed.
- **Resolution test** Provide details on the wheat data source, the orthology assignment method, and the evaluation protocol. Clarify whether the wheat models were fine-tuned on wheat data or used directly from Arabidopsis, and report per-TF results with statistical testing.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The claim that yeast one-hybrid assays confirmed seven out of 14 predicted wheat targets
- **Evidence pointer** Results section, Figure 6C, Supplemental Figure S7, Supplemental Table S5
- **Concern** The experimental validation is described briefly. The manuscript states that seven out of 14 predicted targets were confirmed, but the criteria for "confirmation" are not defined. Additionally, the comparison with PWM-based predictions (two out of 16) is mentioned but the details of this comparison are not provided. The number of replicates, statistical thresholds, and the specificity of the Y1H assay are not described.
- **Why it matters** Experimental validation is a key strength of the manuscript, but without clear criteria and sufficient detail, the reliability of the validation is uncertain. The comparison with PWM-based predictions is important for demonstrating the advantage of deepTFBS, but the small numbers and lack of statistical analysis limit the strength of the conclusion.
- **Resolution test** Provide detailed criteria for positive Y1H results, the number of independent experiments, and statistical analysis of the comparison between deepTFBS and PWM predictions. Consider increasing the number of tested targets for a more robust comparison.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Variant effect prediction
- **Claim pointer** The claim that deepTFBS-MT can identify putative functional regulatory variants, supported by enrichment analyses
- **Evidence pointer** Results section, Figure 4, Supplemental Figure S3
- **Concern** The variant effect analysis is based on 10.7 million SNPs from the 1001 Genomes Project. The manuscript reports enrichment of high-impact variants in promoter and intergenic regions, enrichment of rare alleles (OR = 1.87), and enrichment in conserved non-coding sequences. However, the definition of "effect score" and the threshold for "high-impact" are not clearly specified. The enrichment analyses lack confidence intervals and multiple testing corrections. The two case examples are anecdotal and not statistically validated.
- **Why it matters** The variant effect prediction is presented as a practical application of deepTFBS-MT. Without clear definitions and rigorous statistical analysis, the biological relevance of these predictions is uncertain.
- **Resolution test** Clearly define the effect score and the threshold for high-impact variants. Provide confidence intervals and multiple testing corrections for enrichment analyses. Consider validating the predictions with additional functional assays or independent datasets.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states a 244.49% improvement in PRAUC over PWM. This large percentage improvement is likely due to the very low baseline PRAUC of PWM, which could be misleading. It would be helpful to also report absolute PRAUC values.
- **Required correction** Report absolute PRAUC values alongside percentage improvements for all comparisons.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Methods section "The deepTFBS architecture and training"
- **Issue** The manuscript mentions that the model was implemented using TensorFlow v2.6 but does not provide the exact hyperparameters (e.g., learning rate, number of filters, kernel sizes, dropout rate) or the random seed used for initialization.
- **Required correction** Provide a complete list of hyperparameters and the random seed to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Results section, Figure 2
- **Issue** The manuscript reports median PRAUC and AUC values but does not report the interquartile range or other measures of variability. This makes it difficult to assess the consistency of performance across TFs.
- **Required correction** Report the interquartile range or standard deviation for the performance metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** Results section, Figure 3
- **Issue** The ablation study is described in a single sentence. It would be helpful to provide a more detailed description of the six variants and the specific contribution of each component.
- **Required correction** Expand the description of the ablation study and consider adding a table summarizing the performance of each variant.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The term "DNA language model" is used in the abstract, but the model architecture is a CNN-BiLSTM-attention hybrid, which is not typically described as a language model. This terminology may be misleading.
- **Required correction** Either clarify what is meant by "DNA language model" or use more standard terminology such as "deep learning model."

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Methods section "Model interpretation by integrated gradients and consensus motif identification"
- **Issue** The method for consensus motif identification is described briefly. The parameters for UMAP and DBSCAN are not provided, and the criteria for selecting the top k motifs are not specified.
- **Required correction** Provide the parameters used for UMAP and DBSCAN and describe the motif selection criteria in detail.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Not provided in the manuscript
- **Issue** The manuscript does not include a data availability statement describing where the raw and processed data, as well as the trained models, can be accessed.
- **Required correction** Add a data availability statement specifying the accession numbers for the raw sequencing data and the location of the trained models.

## Risk / unsupported claims
- The claim of a 244.49% improvement over PWM is not well contextualized without absolute PRAUC values and may be misleading.
- The claim that deepTFBS-MT can identify putative functional regulatory variants is based on enrichment analyses that lack statistical rigor and clear definitions.
- The cross-species prediction improvement of 30.6% is reported without statistical testing or per-TF results, making it difficult to assess significance.
- The experimental validation via Y1H assays is described without clear criteria for positive results or statistical analysis, limiting the strength of the claim.
- The claim that deepTFBS is a "DNA language model" is not supported by the described architecture and may be misleading to readers.