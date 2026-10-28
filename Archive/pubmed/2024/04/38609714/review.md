## Review setup
- **Input scope** Full manuscript text (abstract, main text, results, methods) as provided.
- **Assessment boundary** Scientific and technical evaluation of the claims, methodology, and validation as presented in the provided text. No assessment of supplementary figures, tables, or external data not included in the material.
- **Shared manuscript claim summary** The authors present LINGER, a neural network-based method for inferring gene regulatory networks (GRNs) from single-cell multiome data (paired gene expression and chromatin accessibility). LINGER uses lifelong learning to incorporate atlas-scale external bulk data (ENCODE) and motif prior knowledge via manifold regularization. The authors claim substantial improvements in GRN inference accuracy over existing methods, the ability to construct cell-type-specific and cell-level GRNs, and utility in downstream analyses including GWAS trait interpretation and driver regulator identification.
- **Visible evidence base** Abstract, main text, results sections (including descriptions of Figures 1-6 and Extended Data Figures 1-4), and methods sections as provided. Specific quantitative results are described in text but the actual figures, supplementary tables, and code are not available for inspection.
- **Missing materials affecting confidence** All figures, extended data figures, supplementary tables (1-8), and the associated code repository. Detailed hyperparameter settings, training procedures, and computational resource requirements. Full benchmark results and statistical details for all comparisons.

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable contribution to the field of GRN inference by addressing a key limitation: the scarcity of independent data points in single-cell datasets. The idea of using lifelong learning to leverage external bulk data is conceptually interesting and timely. However, the current manuscript, as provided, has several significant technical and presentational gaps that prevent a full evaluation of the method's validity and impact. The core claims of improved accuracy and utility are supported by descriptions of results, but the lack of access to the actual figures, detailed benchmark protocols, and a clear articulation of the method's limitations and failure modes makes it difficult to assess the robustness and generalizability of the approach. The writing is clear but the manuscript would benefit from a more critical discussion of the method's assumptions and potential biases.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing and applying GRN inference methods. Researchers studying gene regulation in specific cell types or disease contexts, particularly those using single-cell multiome data. Geneticists interested in interpreting GWAS signals by linking non-coding variants to regulatory networks and target genes. The method's ability to estimate TF activity from expression data alone could be of broad interest to the functional genomics community.
- **Major strengths**
  - The conceptual advance of using lifelong learning to integrate external bulk data is a novel and potentially powerful approach to address the data sparsity problem in single-cell GRN inference.
  - The method integrates multiple data modalities (expression, chromatin accessibility, motif information) in a principled manner.
  - The authors demonstrate a wide range of applications, from benchmarking against existing methods to downstream analyses like GWAS interpretation and TF activity estimation, which showcases the potential utility of the method.
  - The validation strategy, using ChIP-seq, eQTL, Hi-C, and perturbation data as ground truth, is comprehensive and appropriate for the claims being made.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness and validation
- **Claim pointer** The central claim that LINGER achieves a "fourfold to sevenfold relative increase in accuracy over existing methods" for GRN inference.
- **Evidence pointer** Results section "LINGER improves the cellular population GRN inference" and "Systematic benchmarking of cell-type-specific trans-regulatory potential performance"; Figures 2, 3, 4; Supplementary Tables 1, 4, 6, 7.
- **Concern** The claim of a "fourfold to sevenfold relative increase" is a headline result, but the provided text does not allow for a critical evaluation of this metric. The definition of "relative increase" is unclear. Is this an increase in the AUPR ratio? If so, an increase from 1.2 to 1.25 is a 4% increase, not a 4-fold increase. The text states "LINGER achieves 1.25 units above random prediction, indicating a fourfold to sevenfold relative increase." This is confusing. A "unit above random" is not a standard metric, and the fold-change calculation is not explained. The comparison to other methods (GENIE3, PIDC, SCORPION, etc.) is mentioned, but the specific protocols, hyperparameters, and data preprocessing for these methods are not described. Without a clear definition of the metric and a detailed description of the benchmark setup, this central claim is not verifiable. The authors must clarify the exact metric used, how the fold-change is calculated, and provide a detailed, reproducible benchmark protocol.
- **Why it matters** This is the primary quantitative claim of the paper and is used to justify the method's superiority. If the metric is not clearly defined or is misleading, the core value proposition of the manuscript is undermined.
- **Resolution test** The authors should provide a precise definition of the performance metric and the exact formula for calculating the "relative increase." They should also provide a detailed description of the benchmark protocol, including how competing methods were configured and run. Ideally, they would provide a table showing the raw AUPR and AUROC values for all methods on all datasets, allowing reviewers to independently verify the fold-change calculation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness and methodology
- **Claim pointer** The claim that LINGER's use of lifelong learning (pre-training on ENCODE bulk data) is the key factor driving its improved performance.
- **Evidence pointer** Results section "LINGER improves the cellular population GRN inference"; Extended Data Figure 2h.
- **Concern** The manuscript describes a comparison between LINGER and scNN (which does not use pre-training) and shows LINGER performs better. However, the text also states that "scNN modeled gene expression better than elastic net" and that scNN outperforms PCC and BulkNN. The specific contribution of the lifelong learning component is not isolated. The comparison to scNN is confounded by the fact that LINGER and scNN may have different architectures or training procedures beyond just the pre-training step. The authors mention that "the sigmoid activation function would not improve the gene expression prediction but would improve the GRN inference," suggesting that architectural choices have a significant impact. To support the claim that lifelong learning is the key innovation, the authors should perform an ablation study where the only difference between the models is the presence or absence of the pre-training step and the EWC loss.
- **Why it matters** The novelty of the method rests on the lifelong learning concept. If the performance gain is primarily due to other architectural choices or the inclusion of motif information, the contribution is less novel than claimed.
- **Resolution test** The authors should present an ablation study comparing: (1) LINGER (with pre-training and EWC), (2) scNN (no pre-training, no EWC), and (3) scNN with pre-training but no EWC, and (4) scNN with EWC but no pre-training. This would isolate the contribution of each component.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance and validation
- **Claim pointer** The claim that LINGER can identify "driver regulators" from case-control gene expression studies, as exemplified by FOXN1 in AML and FOXK2/NR4A1 in T cell stimulation.
- **Evidence pointer** Results section "Identify driver regulators based on transcription profiles"; Figure 6.
- **Concern** The two examples provided are interesting but are presented as anecdotal evidence. For the AML example, the authors state that FOXN1 is "significantly less active" in patients and that it is a known tumor suppressor. However, the analysis is based on a GRN inferred from PBMCs, which may not be the relevant cell type for AML. The manuscript does not discuss the potential confounding factor of cell type composition differences between AML and healthy samples. For the T cell stimulation example, the authors identify FOXK2 and NR4A1 as activated, but the link to the literature is brief. A more rigorous validation would involve demonstrating that the identified TFs are not only known but also that the predicted target gene sets are functionally enriched for relevant pathways. The authors should also compare their TF activity estimates with those from other methods, such as SCENIC, to demonstrate added value.
- **Why it matters** The ability to identify driver regulators from expression data alone is a major potential application of this work. The current evidence is not strong enough to support the claim that this is a reliable and generalizable feature of the method.
- **Resolution test** The authors should provide a more systematic validation of the driver regulator identification. This could include: (1) a broader analysis using multiple case-control datasets, (2) a comparison with other TF activity inference methods, and (3) a demonstration that the identified TFs are enriched for known regulators in a variety of contexts.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness and methodology
- **Claim pointer** The claim that LINGER can infer cell-level GRNs.
- **Evidence pointer** Results section "LINGER improves the cell type-specific GRN inference"; Figure 4g-i.
- **Concern** The manuscript describes the construction of cell-level GRNs but the methodology is not fully detailed. The text states that cell-level GRNs are constructed by combining "consistent information across all cells" with "cell-level information." The exact formula or algorithm for this combination is not provided. The example given (RUNX1 regulating SPI1 in monocytes) is a known interaction, but it is not clear how this demonstrates the advantage of cell-level GRNs over cell-type-level GRNs. The authors should provide a clear mathematical description of how cell-level GRNs are constructed and a quantitative comparison showing that cell-level GRNs provide information not available from cell-type-level GRNs.
- **Why it matters** Cell-level GRN inference is a significant claim and a major potential advantage of the method. Without a clear methodology and a demonstration of its unique value, this claim is not substantiated.
- **Resolution test** The authors should provide a detailed description of the cell-level GRN construction algorithm. They should also present a quantitative analysis, for example, showing that cell-level GRNs can distinguish between cells within the same cell type or that they provide better predictions of perturbation outcomes.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract; Results section "LINGER improves the cell type-specific GRN inference".
- **Issue** The abstract states that LINGER "achieves a fourfold to sevenfold relative increase in accuracy over existing methods." This is a strong claim that is not clearly defined in the abstract. The results section provides some context, but the metric is still ambiguous.
- **Required correction** The abstract should be revised to state the performance metric more clearly, e.g., "achieves a fourfold to sevenfold relative increase in the AUPR ratio over existing methods."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness and methodology
- **Affected element** Methods section "GRN inference by lifelong learning"
- **Evidence pointer** Methods section, equation for L_BULK.
- **Issue** The loss function for the bulk pre-training step is described as MSE with L1 regularization. The manuscript does not specify how the L1 regularization is applied (e.g., to the weights of the first layer only, or to all layers). The choice of the regularization parameter λ0 is also not discussed.
- **Required correction** The authors should specify the exact form of the L1 regularization and how the regularization parameter was chosen.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Results section "LINGER reveals the regulatory landscape of GWAS traits"
- **Evidence pointer** Figure 5a.
- **Concern** The text states that "in classical monocytes, trait regulation scores for the top-expressed TF are significantly higher than randomly selected TFs (P = 8.9 × 10−29, one-sided unpaired t-test)". The use of a t-test to compare a single value (the score for the top-expressed TF) against a distribution of scores from randomly selected TFs is statistically questionable. A t-test assumes the data are normally distributed and compares means of two groups. Here, the "top-expressed TF" is a single observation, not a group.
- **Required correction** The authors should use a more appropriate statistical test, such as a permutation test or a one-sample test, to assess whether the score for the top-expressed TF is significantly higher than the null distribution.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Methods section "TF importance score"
- **Evidence pointer** Methods section, "TF importance score" subsection.
- **Issue** The description of the "TF importance score" is somewhat convoluted. The text describes a "co-activity score" and then a "TF importance score" which is the average of the co-activity scores. The relationship between these scores and the final use in the model could be clarified.
- **Required correction** The authors should streamline the description of the TF importance score and clearly state how it is used in the model.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness and methodology
- **Affected element** Methods section "Benchmark the trans-regulatory potential"
- **Evidence pointer** Methods section, "Benchmark the trans-regulatory potential" subsection.
- **Issue** The text states that for PIDC, "we used the 5,000 most variable genes as input." This is a significant reduction in the feature space and could bias the comparison against PIDC, which may perform better with a more complete gene set. The authors should justify this choice and discuss its potential impact on the results.
- **Required correction** The authors should provide a justification for this choice and discuss its potential impact on the benchmark results.

## Risk / unsupported claims
- The claim of a "fourfold to sevenfold relative increase in accuracy" is not verifiable from the provided text due to the unclear definition of the metric and the lack of detailed benchmark data.
- The claim that lifelong learning is the key factor driving performance improvements is not fully supported, as the contribution of this component is not isolated from other architectural choices.
- The claim that LINGER can identify "driver regulators" is based on anecdotal examples and lacks systematic validation.
- The claim that LINGER can infer cell-level GRNs is not fully supported by the provided methodology and validation.
- The statistical test used to assess the significance of trait regulation scores in Figure 5a is inappropriate.
- The manuscript does not discuss the computational cost and runtime of LINGER, which is an important practical consideration for a method intended for widespread use.
- The manuscript does not discuss the sensitivity of the results to the choice of hyperparameters, such as the number of hidden units, the learning rate, and the weight of the manifold regularization term.