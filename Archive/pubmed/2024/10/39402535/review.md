## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present SigTFB, a deep learning method to detect and quantify cell-type specific DNA binding signatures in transcription factor (TF) binding sites. They apply this method to 169 TFs across up to 14 cell types using ENCODE ChIP-seq data, report that approximately two-thirds of TFs show statistically significant cell-type specific DNA binding signatures, and demonstrate that the presence of such signatures is largely uncorrelated with the degree of peak overlap between cell types. They further characterize the signatures through motif enrichment analyses.
- **Visible evidence base** Main text, Figures 1-5, Methods section, Supplementary Table 1 and 2 references, Supplementary Figure S1 reference
- **Missing materials affecting confidence** Supplementary Table 1, Supplementary Table 2, and Supplementary Figure S1 were not provided. Full methodological details for the deep learning architecture (e.g., exact layer sizes, activation functions, regularization) are partially described but some hyperparameter ranges are not specified. Statistical test details for the significance thresholds used in Figure 3a are not fully described. The ENCODE accession numbers are listed only in the supplementary material.

## Reviewer

- **Overall assessment** This manuscript addresses an important and understudied question in transcriptional regulation: whether TF DNA binding preferences are invariant across cell types. The authors propose a novel supervised learning formulation that quantifies cell-type specificity in DNA binding signatures, and apply it at a scale (169 TFs) that substantially exceeds prior work. The two-stage training approach, the careful distinction between peak overlap and DNA signature specificity, and the systematic motif enrichment analyses are commendable. However, several technical aspects require clarification and additional validation before the central claims can be fully accepted. The manuscript is well-written and the figures are informative, but the lack of access to supplementary materials limits a complete assessment.

- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational genomics, and machine learning applied to genomics would be the primary audience. The finding that many TFs exhibit cell-type specific DNA binding signatures has implications for understanding cell fate decisions, disease mechanisms, and for improving predictive models of TF binding. The methodological framework (SigTFB) could be adopted by others studying differential binding. The results also speak to the limitations of current motif databases and position weight matrix approaches that assume cell-type invariant binding preferences.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that SigTFB detects statistically significant DNA binding signatures in approximately two-thirds of TFs, and that the difference in AUC between cell-type specific and cell-type general instances is a measure of cell-type specificity.
- **Evidence pointer** Results section "Comprehensive analysis of cell-type specific DNA-signatures in 169 transcription factors", Figure 3a, 3b
- **Concern** The statistical framework for determining significance of the AUC difference is not fully described. The authors mention a one-sample t-test on AUC differences for ATF7 and CTCF, but for the genome-wide analysis in Figure 3a, the color gradient is based on negative log10 p-values across 10 folds of cross-validation. It is unclear how these p-values are computed across folds, whether they are corrected for multiple testing across 199 TF-AB combinations, and what threshold defines "statistically significant" for the two-thirds claim. Without this information, the central quantitative claim of the paper cannot be evaluated.
- **Why it matters** The primary conclusion of the paper, that two-thirds of TFs show cell-type specific DNA binding signatures, depends entirely on the statistical significance framework. If the threshold is too lenient or the multiple testing correction is inadequate, the proportion could be substantially overestimated.
- **Resolution test** Provide a detailed description of the statistical test used, including how p-values are aggregated across cross-validation folds, the multiple testing correction method applied, and the significance threshold. Re-analyze the data with a conservative multiple testing correction and report the proportion of TFs that remain significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the difference in predictive performance between cell-type specific and cell-type general instances quantifies the extent to which the learner can pick up cell-type specific DNA signatures.
- **Evidence pointer** Results section "A supervised learning formulation for detecting cell-type specific DNA-binding signatures", Figure 1a
- **Concern** The formulation uses the same unified peaks for both cell-type specific and cell-type general instances, with the only difference being the presence or absence of the cell-type identity vector. However, the cell-type general instances are trained with the same output labels (A_ij) as the cell-type specific instances. This means the model is asked to predict whether a peak is bound in a specific cell type, but without being told which cell type. The interpretation of this as a measure of "cell-type specificity" needs careful scrutiny. A model that performs well on cell-type general instances could simply be learning the overall propensity of a sequence to be bound in any cell type, and the difference in AUC might reflect the model's ability to use the cell-type information to adjust predictions. The authors should clarify what exactly the cell-type general model is predicting and why the AUC difference is a valid measure of DNA signature specificity rather than, for example, a measure of the model's capacity to use additional input features.
- **Why it matters** The validity of the entire methodological approach rests on this formulation. If the cell-type general baseline is not an appropriate control, then the AUC differences may not reflect cell-type specific DNA signatures as claimed.
- **Resolution test** Provide a formal argument or simulation demonstrating that the AUC difference between cell-type specific and cell-type general instances specifically captures cell-type specific DNA sequence features, and not other differences in the learning problem. Alternatively, provide a control experiment where the cell-type labels are randomly permuted and show that the AUC difference disappears.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the motif enrichment analysis reveals cell-type specific signatures, including differential enrichment of known TF motifs and the presence of alternative motifs in specific cell types.
- **Evidence pointer** Results section "TFs with cell-type specificity show differential enrichment for known TF-DNA binding motifs", Figure 4e, 4f, Figure 5
- **Concern** The motif enrichment analysis uses FIMO with default parameters and a library of 400 JASPAR motifs. The authors report enrichment fractions as the number of motif-containing peaks divided by total peaks per cell type. However, it is unclear how statistical significance of enrichment is determined. The text mentions "statistically significant" motif hits but does not describe the significance threshold or whether multiple testing correction was applied across the 400 motifs and multiple cell types. Additionally, the selection of "top 20 motifs with the highest enrichment ratio per cell type" for the heatmap in Figure 5 is arbitrary and may not capture statistically meaningful differences.
- **Why it matters** The motif enrichment analysis is used to provide biological interpretation of the cell-type specific signatures. Without proper statistical thresholds, the reported enrichment patterns may include false positives, and the conclusions about which motifs are differentially enriched may not be reliable.
- **Resolution test** Describe the statistical significance criteria for motif enrichment, including the FIMO p-value threshold and any multiple testing correction. Provide the full enrichment results in Supplementary Table 2 with significance indicators, and re-evaluate the conclusions based on statistically significant enrichments only.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the consistency of cell-type specificity estimates across different antibodies for the same TF provides reassurance of the generality of their results.
- **Evidence pointer** Results section "Comprehensive analysis of cell-type specific DNA-signatures in 169 transcription factors", Figure 3d
- **Concern** Figure 3d shows AUC differences for 24 TFs assayed with at least 2 antibodies. While the authors note overall consistency, they also report a striking inconsistency for ETV6, where two antibodies give essentially 0 and 0.37 AUC difference for the same two cell types. The authors attribute this to antibody differences or peak number differences, but this explanation is speculative. This single example raises concerns about the robustness of the method to data quality variations, and the authors do not systematically investigate the sources of such inconsistencies.
- **Why it matters** The reliability of the method across antibody batches and data quality levels is important for its general applicability. A single large inconsistency could indicate that the method is sensitive to technical artifacts in some cases, which would affect the interpretation of results for TFs where only one antibody was used.
- **Resolution test** Provide a more detailed analysis of the ETV6 case, including peak counts, quality metrics, and potential sources of the discrepancy. Discuss whether the method includes any quality control steps to identify and handle such cases.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that their results have implications for predicting TF binding in unassayed cell types, suggesting limitations to such approaches.
- **Evidence pointer** Conclusion section
- **Concern** The authors state that the existence of cell-type specific DNA binding signatures implies limitations for cross-cell-type prediction of TF binding. However, they do not directly test this claim. A more direct demonstration would be to train a model on some cell types and test on held-out cell types, comparing performance with and without cell-type information. The current analysis only shows that cell-type information improves prediction within the same set of cell types, which does not directly address the cross-cell-type prediction scenario.
- **Why it matters** The stated implication for cross-cell-type prediction is a potentially important contribution, but it is not directly supported by the presented analyses. Without a direct test, the claim remains speculative.
- **Resolution test** Perform a cross-cell-type prediction experiment where models are trained on a subset of cell types and tested on held-out cell types, comparing the performance of cell-type specific and cell-type general models. Report whether the cell-type specific models generalize better or worse than cell-type general models.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction and Results section "A supervised learning formulation for detecting cell-type specific DNA-binding signatures"
- **Evidence pointer** Introduction, Results section
- **Issue** The distinction between "cell-type specific DNA binding signatures" and "differential binding" (i.e., binding at different genomic locations in different cell types) could be clarified earlier. The authors note that differential binding does not necessarily imply different DNA sequence preferences, but this distinction is central to the paper and could be emphasized more prominently.
- **Required correction** Add a brief explanation early in the Introduction that clarifies the difference between differential binding (where a TF binds different locations) and differential DNA binding signatures (where the sequence preferences themselves differ), and why the latter is mechanistically distinct.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "SigTFB's two-stage training process"
- **Evidence pointer** Methods section
- **Issue** The description of the network architecture is incomplete. The text mentions a convolutional layer, maxpool layer, and fully connected layers, but does not specify the number of layers in the fully connected portion of the DNA-processing pathway, the activation functions used, or the exact output layer configuration for the multi-task SL1 formulation.
- **Required correction** Provide a complete specification of the network architecture, including the number and size of all layers, activation functions, and the output layer configuration for both SL1 and SL2.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "ATF7 binding shows cell-type specific DNA binding signatures"
- **Evidence pointer** Figure 2c
- **Concern** The authors report a p-value of p << 0.05 for the AUC difference in ATF7 using a one-sample t-test. However, it is unclear how many data points are used in this test (i.e., the number of cross-validation folds or the number of cell types). A t-test with a very small sample size may not be reliable.
- **Required correction** Report the sample size used for the t-test and consider using a non-parametric test if the sample size is small.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results section "Comprehensive analysis of cell-type specific DNA-signatures in 169 transcription factors"
- **Evidence pointer** Figure 3a
- **Concern** The scatter plot in Figure 3a plots cell-type specific AUC versus cell-type general AUC, but the interpretation of the diagonal and the distance from the diagonal could be explained more clearly for readers unfamiliar with this type of analysis.
- **Required correction** Add a sentence in the figure legend or text explaining that points on the diagonal indicate no benefit from cell-type information, while points above the diagonal indicate that cell-type information improves prediction.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Motif analysis"
- **Evidence pointer** Methods section
- **Issue** The description of the in silico mutagenesis procedure is vague. The text mentions "positions that in silico mutagenesis found to have the most influence on network output" but does not describe how the mutagenesis was performed or how many positions were selected.
- **Required correction** Provide a detailed description of the in silico mutagenesis procedure, including how mutations were introduced, how the influence on network output was quantified, and the criteria for selecting positions for the 35 bp windows.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The authors discuss the potential for using their framework to study TF binding in unassayed cell types, but they do not discuss the computational cost or scalability of their approach. Given the large number of TFs and cell types in ENCODE, this information would be useful for readers considering adopting the method.
- **Required correction** Add a brief discussion of the computational resources required for training SigFTP on a single TF-AB combination and the total computational cost of the full analysis.

## Risk / unsupported claims
- The claim that approximately two-thirds of TFs have statistically significant cell-type specific DNA binding signatures is not fully supported without a detailed description of the statistical significance framework and multiple testing correction.
- The claim that the AUC difference between cell-type specific and cell-type general models specifically measures cell-type specific DNA sequence features is not formally justified.
- The claim that the results imply limitations for cross-cell-type prediction of TF binding is not directly tested and remains speculative.
- The claim of consistency across antibodies for most TFs is based on visual inspection of Figure 3d without quantitative measures of consistency.
- The biological interpretation of the motif enrichment results (e.g., the suggestion that MAFK motif variants in JUND peaks may indicate co-binding) is presented as suggestive but the statistical support for these specific observations is not provided.
- The statement that "one-sample t-test on AUC difference" yields p << 0.05 for ATF7 is reported without the sample size or effect size, making it impossible to assess the reliability of this result.