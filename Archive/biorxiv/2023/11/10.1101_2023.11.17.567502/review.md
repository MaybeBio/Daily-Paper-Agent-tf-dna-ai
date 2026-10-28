## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusions, appendix) as provided
- **Assessment boundary** Scientific and technical evaluation of the DARDN method, its validation, and the biological claims made; no assessment of code functionality or data reproducibility beyond what is described
- **Shared manuscript claim summary** The authors present DARDN, a dual-CNN deep learning model with residual connections, to classify long (up to 20 kb) DNA sequences centered at cancer-specific versus constitutive CTCF binding sites, and use DeepLIFT attribution scores to identify sequence motifs for putative oncogenic transcription factors in six cancer types
- **Visible evidence base** Methods section (Sections 2.1-2.3), Results sections (3.1-3.3), Figures 1-5 referenced, Appendix Tables A1-A5 and Figures A1-A5 referenced, data and code availability links
- **Missing materials affecting confidence** Figures 1-5 and Appendix Figures A1-A5 are referenced but not provided in the submitted text; Appendix Tables A1-A5 are referenced but not provided; no hyperparameter search details; no training/validation split details; no confidence intervals or statistical significance tests for motif enrichment; no comparison to alternative deep learning architectures or motif discovery tools beyond HOMER

## Reviewer
- **Overall assessment** The manuscript addresses a genuinely important problem in cancer genomics: identifying sequence features that distinguish cancer-specific CTCF binding sites from constitutive ones, where the relevant TF binding sites may be located at variable and potentially large distances. The DARDN architecture, combining dual CNNs with residual connections, is a reasonable and potentially effective approach for this task. The simulation study provides a useful proof-of-concept that the pipeline can recover an inserted known motif. However, the manuscript as presented has several significant gaps that prevent the claims from being fully established. The most critical issues are the lack of a rigorous comparison against simpler or existing methods, the absence of statistical significance testing for the key biological findings, the lack of detail on model training and evaluation protocols, and the reliance on literature-based validation for the cancer-specific motifs without quantitative evidence that these motifs are specifically enriched in gained versus constitutive sites beyond what HOMER reports. The robustness analyses are commendable but are presented without error bars or statistical replication, and the interpretation of the distance distributions as evidence for long-range interactions is under-supported given the 10 kb window and the lack of chromatin conformation data at appropriate resolution. The writing is generally clear, but the results section would benefit from more quantitative detail. Overall, the work is promising and of potential interest to a specialized audience, but the current evidence does not fully support the strength of the claims made.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on deep learning applications in genomics, particularly those focused on regulatory genomics, transcription factor binding site prediction, and interpretability of neural network models. Cancer biologists studying CTCF-mediated chromatin architecture and oncogenic transcription factor cooperation would also be interested, as the method offers a way to nominate candidate TFs from DNA sequence alone. The approach could be of broader interest to researchers developing methods for feature discovery from long genomic sequences where the location of the relevant feature is unknown.

- **Major strengths** The problem addressed is important and timely, and the authors correctly identify the limitations of conventional motif discovery in this setting. The DARDN architecture is thoughtfully designed, with the dual-kernel approach and residual connections being biologically motivated. The simulation study is a valuable validation step that demonstrates the pipeline can recover an inserted motif with high accuracy. The robustness analyses across sequence lengths, subsequence lengths, and sampling strategies are a positive feature. The application to multiple cancer types and the identification of known and literature-supported TFs (e.g., RBPJ in T-ALL, PU.1 in AML) provides some external validation. The manuscript is generally well-written and the methods are described in sufficient detail to be reproducible in principle.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that DARDN accurately classifies cancer-specific versus constitutive CTCF binding sites and that the model outperforms plain CNN models, as shown in Table 1.
- **Evidence pointer** Section 2.3, Table 1 (referenced but not provided)
- **Concern** The claim of superior performance over plain CNN models is central to the justification for the DARDN architecture, but Table 1 is not provided in the submitted material. Without the actual performance numbers, including MCC values for DARDN versus plain CNN, and without details on the training setup (e.g., number of parameters, training epochs, regularization, early stopping criteria), it is impossible to assess whether the observed differences are meaningful or could be attributed to differences in model capacity, training procedure, or random initialization. Furthermore, no statistical significance testing is reported for the performance differences.
- **Why it matters** The entire motivation for the DARDN architecture rests on the claim that plain CNNs are ineffective for this task. If this claim is not rigorously supported, the contribution of the architectural innovations is unclear. Moreover, without a comparison to a standard baseline (e.g., a simple k-mer-based SVM or a logistic regression on motif scores), it is unclear whether the deep learning approach itself is necessary.
- **Resolution test** Provide Table 1 with MCC values (and ideally precision, recall, F1) for DARDN and at least one plain CNN baseline, with error bars or confidence intervals across multiple random seeds. Report the training details (epochs, batch size, learning rate, regularization) and perform a statistical test (e.g., paired t-test or Wilcoxon signed-rank test across seeds) to demonstrate that DARDN is significantly better.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that DeepLIFT attribution scores, followed by sliding window aggregation and HOMER analysis, identify sequence motifs for transcription factors potentially active in each cancer type, including known oncogenes such as RBPJ in T-ALL.
- **Evidence pointer** Sections 2.3, 3.2, 3.3, Figures 3-5, Appendix Tables A1-A5
- **Concern** The validation of the identified motifs relies almost entirely on literature-based confirmation for a small number of known TFs. For the other cancer types, the authors state that "the most prominent oncogenes for some of these cancers are less studied" and provide literature support for some motifs, but no quantitative assessment is provided for the specificity or significance of these motif enrichments. Specifically, it is not shown whether the identified motifs are significantly more enriched in the gained sites compared to what would be expected by chance, or compared to the constitutive sites themselves. The HOMER enrichment p-values are not reported. Furthermore, the choice of the top 1000 subsequences by DeepLIFT score is arbitrary, and no sensitivity analysis is shown for this parameter.
- **Why it matters** The biological claims of identifying oncogenic TFs are the main translational output of the work. If the motif enrichment is not statistically validated, the findings could be spurious or could reflect general properties of CTCF-flanking regions rather than cancer-specific features. The lack of quantitative validation undermines the confidence in the biological conclusions.
- **Resolution test** Report HOMER enrichment p-values (or equivalent) for all identified motifs in all cancer types. Perform a permutation test where DeepLIFT scores are randomly shuffled and the same pipeline is run, to establish a null distribution for motif enrichment ranks. Show that the identified motifs are significantly enriched compared to this null. Additionally, demonstrate that the identified motifs are not equally enriched in the constitutive sites when the same analysis is applied to them.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the distance distributions between CTCF centers and identified motif sites, which show motifs occurring at various distances up to 10 kb, suggest long-range interactions between CTCF and cooperating transcription factors through DNA looping.
- **Evidence pointer** Section 3.2, Figures 4 and 5
- **Concern** The interpretation of the distance distributions as evidence for long-range interactions is not well-supported. The input sequences are 10 kb (or 5 kb or 20 kb) centered at CTCF sites, so motifs can only be found within this window. The observation that motifs are distributed across the window does not demonstrate looping; it could simply reflect the fact that the relevant TF binding sites are located at various distances from the CTCF site in linear genomic space. The authors acknowledge that their Hi-C data has insufficient resolution (10 kb) to provide direct evidence, but this means the looping claim is speculative. No alternative explanations (e.g., cooperative binding at linear distances, or indirect effects) are discussed or ruled out.
- **Why it matters** The claim of long-range interactions is a significant biological interpretation that goes beyond the computational method. If this claim is not supported, the biological significance of the findings is reduced to the identification of motifs, which is less novel. Over-interpretation of the data could mislead readers.
- **Resolution test** Either provide direct experimental evidence for looping (e.g., Hi-C at higher resolution, or 3C-based assays) at a subset of loci, or temper the claim to state that the method identifies motifs at variable distances from CTCF sites, without speculating on the mechanism. Alternatively, perform an analysis showing that the distance distribution of identified motifs is significantly different from a null distribution of random genomic positions relative to CTCF sites.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that DARDN is robust to variations in input sequence length, subsequence length, and sampling of foreground and background sites, as shown in Figures 3 and 4.
- **Evidence pointer** Section 3.2, Figures 3 and 4
- **Concern** The robustness analyses are presented as single runs without error bars or replication. For example, in Figure 3b, the five sampling runs of background constitutive sites show a wide range of RBPJ ranks (from 69th to 97.3rd percentile), which suggests considerable variability. The authors attribute the low rank in run 1 to the reduced number of background sites, but this is not tested systematically. It is unclear whether the observed variability is acceptable or whether it indicates that the method is sensitive to the choice of background set. Similarly, the MCC values vary across runs (0.80 to 0.92), and no confidence intervals are provided.
- **Why it matters** The robustness of the method is a key selling point, especially given the small number of positive samples (72 T-ALL-specific sites). If the results are highly variable depending on sampling, the reliability of the method for new cancer types is questionable.
- **Resolution test** Repeat the sampling experiments multiple times (e.g., 10 or more) and report the mean and standard deviation of the RBPJ rank and MCC. Perform a systematic analysis of the effect of the number of background sites on performance. Report the results with appropriate error bars.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the choice of kernel sizes 4 and 8 is motivated by the RBPJ motif length and its core sequence.
- **Evidence pointer** Section 2.3
- **Concern** The kernel size selection is presented as being driven by the RBPJ motif, but this is a post-hoc justification. The method is intended to be generalizable to other cancer types where the target motif is unknown. It is not clear whether kernel sizes 4 and 8 are optimal for other motifs of different lengths. No systematic hyperparameter search is reported, and the sensitivity of the results to kernel size is not explored.
- **Why it matters** If the architecture is tuned to a known motif in the development set, the performance on other cancer types may not be representative. The generalizability of the method depends on the kernel sizes being appropriate for a range of motif lengths.
- **Resolution test** Perform a hyperparameter sweep over kernel sizes (e.g., 2, 4, 6, 8, 12, 16) and report the effect on classification accuracy and motif discovery performance. Show that the results are not highly sensitive to the specific kernel sizes chosen, or provide a principled method for selecting them.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.2, evaluation metrics
- **Evidence pointer** Section 2.2
- **Issue** The formula for MCC is described in words but the actual equation is missing from the text. The sentence "MCC is calculated by dividing the product of their standard deviations, which is represented as: where TP is..." appears to have a formatting error, as the equation itself is not shown.
- **Required correction** Include the full MCC formula in the text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.1, data augmentation
- **Evidence pointer** Section 2.1
- **Issue** The data augmentation procedure is described as shifting sequences "stochastically between 1 to 5 base pairs." It is unclear whether this is done for both the positive and negative sets, and whether the shifting is applied to the one-hot encoded matrix or to the genomic coordinates. The exact implementation details are not specified.
- **Required correction** Clarify the augmentation procedure, including whether it is applied to both classes, the exact range of shifts, and whether the shifted sequences are used for training only or also for validation/testing.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2, Figure 3a
- **Evidence pointer** Section 3.2
- **Issue** The description of Figure 3a states that the x-axis represents sequence lengths of 5kbps, 10kbps, and 20kbps, denoted as "short," "moderate," and "long." However, the text then refers to "short input sequence length," "moderate input sequence length," and "long input sequence length" without consistently using the same labels. This could be confusing to the reader.
- **Required correction** Use consistent terminology throughout the text when referring to the different sequence lengths.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.3, Appendix
- **Evidence pointer** Section 3.3, Appendix A
- **Issue** The results for the five additional cancer types are summarized in the text, but the full list of enriched motifs is only in the Appendix tables, which are not provided. The text mentions "the most significantly enriched motifs" but does not give any quantitative information, such as enrichment scores or p-values, for these motifs.
- **Required correction** Provide at least a summary table in the main text with the top motifs for each cancer type, including enrichment scores or p-values, so that the reader can assess the significance of the findings without referring to the Appendix.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Section 2.3, DeepLIFT reference
- **Evidence pointer** Section 2.3
- **Issue** The description of the DeepLIFT reference value is brief. It states that "we randomly sampled 80% of the constitutive sites and used the averaged frequency at each index as the reference value." It is unclear whether this reference is computed once and used for all sequences, or whether it is recomputed for each fold of cross-validation. The potential impact of the choice of reference on the results is not discussed.
- **Required correction** Clarify how the reference value is computed and whether it is held fixed across all experiments. Discuss the sensitivity of the results to the choice of reference.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.3, model training
- **Evidence pointer** Section 2.3
- **Concern** The manuscript does not specify the train/validation/test split ratio, whether cross-validation was used, or how the 72 T-ALL positive samples were divided. Given the small number of positive samples, this is an important detail for assessing the reliability of the reported MCC values.
- **Required correction** Provide details on the data split, including the number of samples in each set, and whether any form of cross-validation was employed.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 1, Introduction
- **Evidence pointer** Section 1
- **Issue** The introduction is somewhat dense and could benefit from a clearer statement of the specific gap the method fills. The sentence "Conventional TF motif search methods are not feasible for this problem because the relative genomic location of the target oncogenic TF binding site relative to the cancer-specific CTCF site is unknown and can be very far, and it varies across different cancer-specific CTCF sites" is a run-on sentence that could be split for clarity.
- **Required correction** Rewrite this sentence for clarity and consider adding a brief summary of the method's contributions at the end of the introduction.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and Code Availability Statement
- **Evidence pointer** Data and Code Availability Statement
- **Issue** The code repository link is provided, but it is not stated whether the code is versioned, whether it includes the trained model weights, or whether it includes the exact scripts used to generate the figures. This limits the reproducibility of the results.
- **Required correction** Clarify the contents of the code repository, including whether trained models and figure-generation scripts are included.

## Risk / unsupported claims
- The claim that DARDN identifies "oncogenic regulatory features" is not fully supported by the evidence presented. The identification of known TFs (e.g., RBPJ) in T-ALL provides some validation, but for the other cancer types, the validation is based on literature association rather than functional experiments. The term "oncogenic" implies a causal role that is not demonstrated.
- The claim that the distance distributions suggest "long-range interactions" through DNA looping is speculative and not directly supported by the data, as the authors acknowledge the Hi-C resolution is insufficient.
- The claim that DARDN is "versatile" and "broadly applicable" is not fully established, as the method is only tested on CTCF-related data. The generalizability to other types of regulatory elements or sequence classification tasks is not demonstrated.
- The performance comparison to plain CNN models is not assessable because Table 1 is not provided.
- The statistical significance of the motif enrichment results is not reported, making it impossible to assess whether the findings are robust or could be due to chance.