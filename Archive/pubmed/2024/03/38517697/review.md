## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and data/code availability statements.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to presented evidence, and completeness of reporting. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors evaluate 14 computational models for predicting the effects of SNPs on TF-DNA binding using large-scale in vitro (SNP-SELEX) and in vivo (ASB) datasets. They report that in vitro prediction accuracy exceeds in vivo accuracy, that kmer/gkm-based methods perform best in vitro, that DNN-based multitask models perform best in vivo, that certain TF classes are more predictable than others, and that non-sequence factors influence in vivo predictive performance.
- **Visible evidence base** Abstract, full introduction, full methods section, full results section, full discussion, funding, author contributions, code availability, data availability. Figures and tables are referenced but not provided. Supplementary materials are referenced but not provided.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are referenced but not included. This includes Figure 1-5, Supplementary Figures S1-S7, Supplementary Tables S1-S21, Supplementary Data 1-6, and Supplementary Methods. Statistical outputs are reported in text but underlying data distributions and model-specific details are not fully verifiable.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question: how well do existing computational models predict the effects of SNPs on TF-DNA binding? The scale of the evaluation, covering 14 models across hundreds of TFs and thousands of SNPs, is a notable strength. The finding that in vitro performance exceeds in vivo performance, and that different model families excel in different contexts, is potentially useful for the community. However, the manuscript has several significant limitations. The absence of all figures and tables makes it impossible to verify the reported results. The evaluation methodology has potential circularity issues, particularly for models trained on data derived from the same experimental platforms used for evaluation. The statistical comparisons, while extensive, are not always clearly motivated or corrected for multiple testing. The analysis of TF properties and their relationship to prediction performance is largely correlational and may be confounded by data quantity or quality per TF. The discussion of biological mechanisms underlying performance differences is speculative and not directly tested. Overall, the work is a useful benchmark but the current presentation does not fully establish all claims made.
- **Who would be interested in the results, and why** Computational biologists developing or using variant effect prediction tools would be the primary audience. Researchers studying regulatory genomics and TF-DNA binding mechanisms would also find the comparative analysis useful. The findings on which model families perform best in which contexts could inform tool selection for practical applications such as prioritizing non-coding variants from GWAS studies. The analysis of TF properties associated with prediction accuracy may interest those studying TF biology and evolution.
- **Major strengths** 1) Large-scale evaluation covering 14 models, hundreds of TFs, and thousands of SNPs, representing a substantial benchmarking effort. 2) Use of both in vitro and in vivo datasets allows comparison across experimental contexts. 3) Analysis of TF classes and properties provides insights beyond simple model ranking. 4) Clear reporting of data sources and availability of code and benchmark datasets.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (circularity in evaluation), R1-M2 (missing figures and tables), R1-M3 (statistical methodology), R1-M4 (confounding in TF property analysis).
- **Assessment against Nature-style criteria** **Originality**: The work is largely confirmatory of existing knowledge, with the main contribution being scale rather than conceptual novelty. The finding that kmer/gkm methods excel in vitro and DNNs excel in vivo is not entirely unexpected given prior literature. **Scientific importance**: The benchmark is useful for the community and could inform tool selection, but the insights are incremental rather than transformative. **Interdisciplinary readership**: The work is primarily of interest to computational biologists and regulatory genomics researchers. The methods and findings are unlikely to attract broad interdisciplinary attention. **Technical soundness**: The evaluation design has potential circularity issues, and the absence of figures and tables prevents full verification. Statistical methods are not fully described. **Readability for nonspecialists**: The manuscript is written for a specialist audience and would be challenging for nonspecialists to follow. The methods are described at a level appropriate for a bioinformatics journal but not for a general science audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant question and the scale of the evaluation is commendable, but the missing figures and tables, potential circularity in evaluation design, and incomplete statistical reporting prevent full assessment. The authors should be encouraged to resubmit after addressing these concerns.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design / evaluation methodology
- **Claim pointer** The authors claim that "deltaSVM_HT-SELEX and QBiC-Pred, trained on in vitro datasets, exhibit the best performance" for in vitro variant impact prediction, and that "DNN-based multitask models (DeepSEA, Sei, Enformer) trained on the ChIP-seq dataset exhibit relatively superior performance" for in vivo ASB prediction.
- **Evidence pointer** Methods section "Evaluation datasets preprocessing", Results section "Evaluation of the models using the SNP-SELEX data" and "Evaluation of the models using the ASB data", Table 1 (not provided)
- **Concern** The evaluation may have circularity issues. Models trained on SNP-SELEX data (e.g., deltaSVM_HT-SELEX, QBiC-Pred) are evaluated on SNP-SELEX data, and models trained on ChIP-seq data (e.g., DeepSEA, Sei, Enformer) are evaluated on ASB data derived from ChIP-seq experiments. This is not inherently problematic if the training and evaluation datasets are independent, but the manuscript does not clearly establish this independence. For example, if the SNP-SELEX training data and evaluation data share SNPs or TFs, the reported performance could be inflated. Similarly, if the ChIP-seq data used to train DeepSEA, Sei, or Enformer overlaps with the ChIP-seq data used to derive the ASB calls, the evaluation would be circular. The authors need to explicitly address dataset independence, including whether any SNPs or TFs in the evaluation sets were also present in the training sets, and whether the ASB calls were derived from ChIP-seq experiments independent of those used for model training.
- **Why it matters** If the evaluation is circular, the reported performance rankings and conclusions about which models are best would be invalid. This is a fundamental issue that affects the core claims of the manuscript.
- **Resolution test** The authors should provide a clear statement of dataset independence, including overlap analysis between training and evaluation sets. If overlap exists, they should either exclude overlapping instances or demonstrate that results are robust to their inclusion.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness of reporting
- **Claim pointer** The manuscript reports specific numerical results, such as median AUROC values, AUPRC values, Spearman correlation coefficients, and statistical test results, across multiple figures and tables.
- **Evidence pointer** All figures (Figures 1-5) and tables (Tables 1-2) are referenced but not provided. All supplementary materials (Figures S1-S7, Tables S1-S21, Data 1-6) are referenced but not provided.
- **Concern** The manuscript cannot be properly evaluated without the figures, tables, and supplementary materials. The text describes results but the actual data visualizations, model descriptions, and detailed statistical outputs are absent. This is a critical omission that prevents verification of the reported findings. For example, the claim that "67.86% (First Batch) and 41.31% (Novel Batch) of them were deltaSVM_HT-SELEX" cannot be verified without Figure 2C. The model descriptions in Table 1 are essential for understanding what exactly was evaluated.
- **Why it matters** Without the actual data presentations, the reported results cannot be checked for accuracy, and the reader cannot assess the quality of the analysis. This is a fundamental barrier to evaluation.
- **Resolution test** The authors must provide all figures, tables, and supplementary materials in the revised submission. The review should be re-evaluated with the complete set of materials.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The authors report extensive pairwise comparisons between models using paired Wilcoxon tests, and multiple group comparisons using Kruskal-Wallis tests and Dunn's tests.
- **Evidence pointer** Results sections "Evaluation of the models using the SNP-SELEX data" and "Evaluation of the models using the ASB data", Supplementary Data 3 and 5 (not provided)
- **Concern** The manuscript does not describe how multiple testing was handled. With 14 models, pairwise comparisons between all models would involve 91 tests for each dataset. The authors report "P-values and 95% CIs obtained from pairwise paired Wilcoxon tests between all models" but do not state whether any correction for multiple comparisons was applied (e.g., Bonferroni, Benjamini-Hochberg). Without such correction, the number of false positives could be substantial. Additionally, the choice of paired Wilcoxon tests is not fully justified, particularly for the ASB data where the number of TFs per model varies considerably.
- **Why it matters** Without appropriate multiple testing correction, the reported statistical differences between models may be unreliable. This affects the validity of the performance rankings and the conclusions drawn from them.
- **Resolution test** The authors should state whether multiple testing correction was applied and, if so, which method was used. If not, they should apply an appropriate correction and re-evaluate which comparisons remain significant. They should also justify the use of paired tests given the varying numbers of TFs per model.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Confounding in TF property analysis
- **Claim pointer** The authors claim that "TFs in the 'Basic leucine zipper factors' class could be predicted more accurately" and that "TFs with extensive modifications performed worse compared to those with fewer modifications."
- **Evidence pointer** Results section "Relationship between prediction performance of TFs and their DBDs" and "Performance of TFs is influenced by in vivo properties of DNA and TFs", Figures 4-5 (not provided)
- **Concern** The analysis of TF properties and their relationship to prediction performance may be confounded by the number of SNPs or binding sites available per TF. TFs with more data points may have more reliable AUROC estimates, and this could correlate with TF class or other properties. The manuscript does not appear to control for data quantity per TF in these analyses. Additionally, the analysis of TF expression, interactions, and PTMs relies on external data sources, and the manuscript does not describe how these data were integrated or whether the analyses were adjusted for potential confounders such as TF family or DNA-binding domain.
- **Why it matters** If the observed associations between TF properties and prediction performance are confounded by data quantity or other factors, the conclusions about which TF classes are more or less predictable would be misleading.
- **Resolution test** The authors should include data quantity per TF as a covariate in their analyses, or stratify by data quantity to show that the observed associations are robust. They should also describe how external data on expression, interactions, and PTMs were integrated and whether any adjustment for confounders was performed.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Methods section "Definition of positive and negative samples in SNP-SELEX"
- **Evidence pointer** Methods section, subsection "Definition of positive and negative samples in SNP-SELEX"
- **Issue** The criteria for defining positive and negative samples in the SNP-SELEX data are described briefly. The authors state that positive samples are pbSNPs with PBS P-value <0.01 and negative samples have PBS P-value >0.5, but the rationale for these specific thresholds is not provided. Additionally, the handling of SNPs with PBS P-values between 0.01 and 0.5 is not described.
- **Required correction** The authors should justify the chosen thresholds and describe how SNPs with intermediate PBS P-values were treated (e.g., excluded, or included in a separate category).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of model descriptions
- **Affected element** Table 1 (not provided)
- **Evidence pointer** Methods section "Overview of state-of-the-art models", Table 1 (not provided)
- **Issue** The manuscript states that 14 models were selected and lists them in Table 1, but the table is not provided. The text mentions that models are based on PWM, SVM, OLS, and DNN, but does not describe the specific implementations, hyperparameters, or versions of each model. This information is essential for reproducibility.
- **Required correction** The authors should provide Table 1 with full descriptions of each model, including version, training data, and any relevant parameters. If this information is in the Supplementary Methods, it should be clearly referenced.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections reporting AUROC and AUPRC values
- **Evidence pointer** Results sections "Evaluation of the models using the SNP-SELEX data" and "Evaluation of the models using the ASB data"
- **Issue** The manuscript reports median AUROC and AUPRC values but does not consistently report confidence intervals or measures of variability for these estimates. The text mentions 95% CIs for pairwise comparisons but not for the AUROC estimates themselves.
- **Required correction** The authors should report confidence intervals or other measures of uncertainty for the AUROC and AUPRC estimates, particularly when making claims about relative model performance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of correlation between datasets
- **Affected element** Results section "Evaluation of the models using the SNP-SELEX data", Figure 1D and E
- **Evidence pointer** Results section, subsection "Evaluation of the models using the SNP-SELEX data", Figure 1D and E (not provided)
- **Issue** The authors report significant positive correlations between PBS values in the SNP-SELEX data and ΔES values in the ASB data, but the correlation coefficients are low (0.159 and 0.095). The text states that the datasets "would complement each other due to their ability to capture different aspects of TF-DNA binding," but this interpretation is not fully developed. The low correlations could also indicate substantial disagreement between in vitro and in vivo measurements.
- **Required correction** The authors should discuss the implications of the low correlations more thoroughly, including potential reasons for disagreement and how this affects the interpretation of model performance across the two datasets.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity of TF property analysis
- **Affected element** Results section "Performance of TFs is influenced by in vivo properties of DNA and TFs"
- **Evidence pointer** Results section, subsection "Performance of TFs is influenced by in vivo properties of DNA and TFs", Figure 5 (not provided)
- **Issue** The analysis of TF expression, interactions, and PTMs is described briefly. The authors state that TFs were divided into three groups based on these properties, but the specific cutoffs or methods for grouping are not described in the main text. It is unclear whether these analyses were pre-specified or exploratory.
- **Required correction** The authors should describe the grouping methodology in the main text or clearly reference the Supplementary Methods where this information should be provided.

## Risk / unsupported claims
- The claim that "our evaluation datasets reached an unprecedented scale in terms of the number of SNPs and TFs" is not directly verifiable without comparison to prior benchmarks, and the term "unprecedented" is a strong claim that should be supported with specific comparisons to previous studies.
- The claim that "TFs with more extensive modifications performed worse compared to those with fewer modifications" is presented as a general finding, but the analysis may be confounded by TF family or data quantity, as noted in R1-M4.
- The claim that "the Sei and Enformer model trained on different cell types exhibited higher variance in prediction, implying they might capture more cell-type-specific allelic TF binding" is speculative. Higher variance across cell types could also indicate noise or instability, and the manuscript does not provide a direct test of cell-type-specific capture.
- The statement that "kmer/gkm-based models could overcome the limitation of low-affinity TFBS" is presented as an explanation for their performance but is not directly tested in this study.
- The claim that "tRap employed different algorithm to measure variant impact scores" as an explanation for its superior performance among PWM methods is not fully developed, and the specific algorithmic differences are not described.