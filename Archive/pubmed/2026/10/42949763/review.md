## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and data availability statements. Figures and supplementary materials referenced but not provided.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided text. No assessment of code functionality or figure quality beyond what is described.
- **Shared manuscript claim summary** The authors present XChrom, a deep learning framework that integrates DNA sequence and single-cell RNA-seq-derived cell embeddings to predict chromatin accessibility across genomic regions and cells, including unseen combinations. They claim superior performance over existing methods in cross-region, cross-cell, and cross-sample tasks, cross-species generalization, and utility in identifying disease-associated regulatory changes in COVID-19.
- **Visible evidence base** Text descriptions of model architecture, training procedures, evaluation metrics, and results summaries. References to figures (Figure 1-7), supplementary figures (S1-S18), and tables (S1-S10) are made but the actual data are not available in this submission.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials. Detailed hyperparameter settings, exact dataset statistics, and code outputs. The absence of these materials prevents independent verification of the reported quantitative results and statistical claims.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in single-cell genomics: predicting chromatin accessibility for unseen regions and cells by integrating sequence and cellular context. The proposed architecture is a reasonable extension of existing sequence-based models like scBasset, with the addition of a cell embedding module. The application scenarios, including cross-cell, cross-sample, and cross-species prediction, are well motivated. However, the manuscript as presented has several critical gaps. The evaluation methodology, particularly regarding baseline comparisons and statistical rigor, is incompletely described. The claims of superiority over existing methods are not fully supported by the visible evidence, and the absence of figures and tables makes it impossible to assess the magnitude of reported effects. The cross-species and COVID-19 analyses are interesting but their validation is incomplete. The manuscript would benefit from clearer descriptions of the evaluation protocols and more robust statistical analyses.
- **Who would be interested in the results, and why** Researchers in computational genomics, particularly those working on single-cell epigenomics, chromatin accessibility modeling, and regulatory genomics. The framework's ability to predict accessibility in unseen cells and regions could be of interest to those studying cell-type-specific regulation, developmental biology, and disease mechanisms. The cross-species generalization aspect may appeal to evolutionary genomics researchers. The open-source implementation and tutorials could make it a useful resource for the community.
- **Major strengths** The problem is well defined and practically relevant. The integration of sequence and cell context in a single model is a sensible and potentially powerful approach. The authors consider multiple realistic scenarios (cross-region, cross-cell, cross-sample, cross-species) which increases the potential utility of the method. The inclusion of interpretability analyses (ISM, TF activity) is a strength, as it moves beyond prediction to biological insight. The open-source availability and documentation are commendable.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims that "XChrom consistently outperforms existing methods in cross-region and cross-cell predictions" and "uniquely enables cross-both predictions."
- **Evidence pointer** Figure 2, Tables S1-S3, location not provided
- **Concern** The quantitative evidence supporting the central performance claims is not visible in the provided materials. The text describes comparisons with scBasset, Seurat, LS_Lab, and MultiVI, but the actual performance numbers, statistical test results, and effect sizes are not available. Without these data, the claim of consistent superiority cannot be evaluated. Furthermore, the description of the evaluation protocol is incomplete. For example, it is unclear how hyperparameters were selected for baseline methods, whether the same train/test splits were used for all methods, and how variability across random seeds or dataset subsamples was handled.
- **Why it matters** The core contribution of the manuscript is the claimed performance advantage of XChrom. If this claim is not robustly supported by the evidence, the manuscript's main conclusion is not established.
- **Resolution test** Provide the actual performance metrics (e.g., auROC, auPRC) for all methods across all datasets and scenarios, with confidence intervals or standard deviations. Describe the evaluation protocol in detail, including hyperparameter tuning, cross-validation strategy, and statistical testing procedures. Show the statistical test results (e.g., p-values) for the comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "XChrom can predict new samples from the same tissue or organ as the training set" and that this requires "batch effects are properly corrected."
- **Evidence pointer** Figure 5, Figure S10-S12, location not provided
- **Concern** The cross-sample prediction scenario is a key practical application, but the analysis is not fully convincing. The authors compare several batch correction methods (Scanpy ingest, Harmony, Scanorama, scVI) and find them "broadly comparable." However, the criteria for "comparable" are not defined, and the statistical significance of differences between methods is not reported. More importantly, the manuscript does not address the potential confounding between batch effects and biological variation. In the BMMC dataset, donor and platform differences may correlate with cell-type composition, and it is unclear whether the model is learning biological signals or batch artifacts. The claim that XChrom "outperformed the raw ATAC data" in NS is interesting but the practical significance of this improvement is not discussed.
- **Why it matters** The utility of XChrom for real-world applications depends on its ability to generalize to new samples. If the model's performance is highly sensitive to batch correction or if the evaluation does not adequately separate batch from biology, the practical claims are weakened.
- **Resolution test** Provide a more detailed analysis of the cross-sample scenario, including the magnitude of batch effects, the correlation between batch and cell-type composition, and the statistical significance of differences between batch correction methods. Discuss the potential limitations of the approach when batch effects are severe or when new samples contain novel cell states.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes the model architecture and training procedure, but key details are missing.
- **Evidence pointer** Methods section, location not provided
- **Concern** The description of the model architecture is incomplete. The text mentions "seven convolutional blocks" with specific output dimensions, but does not specify kernel sizes, stride, padding, activation functions for each layer, or the exact architecture of the cell embedding module. The integration mechanism (matrix multiplication) is described, but the details of the "learnable sequencing depth correction term" are vague. The training procedure is also underspecified: the learning rate schedule, batch size, number of training steps, and early stopping criteria are not fully described. The manuscript mentions data augmentation (random reverse complementation, random shifts) but does not specify the exact parameters. These details are essential for reproducibility.
- **Why it matters** Without a complete description of the model and training procedure, other researchers cannot reproduce the results or apply the method to their own data.
- **Resolution test** Provide a complete description of the model architecture, including all hyperparameters, layer configurations, and training details. Consider providing the code as a supplementary file or pointing to a stable repository version.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports "significant" differences in TF activity between COVID-19 severity groups and between cell types, using the Wilcoxon rank-sum test.
- **Evidence pointer** Figure 7, Tables S9-S10, location not provided
- **Concern** The statistical analysis of TF activity differences is described, but the multiple testing correction is not mentioned. Given the large number of TFs tested, the false discovery rate could be high. The manuscript states that p-values were adjusted using the Benjamini-Hochberg method, but the number of tests and the threshold for significance are not reported. Additionally, the biological interpretation of the TF activity differences is somewhat speculative. The authors link the identified TFs to known COVID-19 biology, but the causal relationship between predicted TF activity and disease pathogenesis is not established.
- **Why it matters** The COVID-19 analysis is presented as a case study demonstrating the utility of XChrom. If the statistical analysis is not rigorous, the conclusions drawn from this case study may be overstated.
- **Resolution test** Report the number of TFs tested, the FDR threshold, and the number of significant TFs. Provide effect sizes and confidence intervals for the key comparisons. Discuss the limitations of the TF activity inference approach and the potential for confounding factors.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that XChrom "uniquely enables cross-both predictions" but does not clarify what this means in practical terms. The phrase "cross-both" is not defined in the abstract.
- **Required correction** Define "cross-both" in the abstract, e.g., "predicting accessibility for both unseen genomic regions and unseen cells simultaneously."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods, "XChrom Architecture" section, location not provided
- **Issue** The description of the "learnable sequencing depth correction term" is vague. It is unclear how this term is computed and how it interacts with the main prediction.
- **Required correction** Provide a more detailed description of this component, including its mathematical formulation and how it is trained.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results
- **Evidence pointer** Figure 2, location not provided
- **Issue** The text states that "XChrom's performance trend was highly consistent with that of scBasset" in cross-region prediction, but the meaning of "performance trend" is unclear. Does this refer to relative performance across datasets or across metrics?
- **Required correction** Clarify the statement, e.g., "XChrom and scBasset showed similar relative performance across datasets, with no significant differences in most metrics."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, location not provided
- **Issue** The authors state that XChrom "does not simply memorize shallow RNA-to-ATAC mappings" but this claim is not directly tested. The ablation studies show the importance of both modules, but they do not demonstrate that the model learns "underlying biological principles."
- **Required correction** Soften this claim or provide additional evidence, such as analysis of the learned embeddings or transfer learning experiments.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data Availability
- **Evidence pointer** Data Availability Statement, location not provided
- **Issue** The statement mentions that processed data are uploaded to Zenodo, but the link is not provided in the manuscript text.
- **Required correction** Include the Zenodo DOI or URL in the Data Availability Statement.

## Risk / unsupported claims
- The claim of "consistent outperformance" over existing methods is unsupported without the actual performance data.
- The claim that XChrom "captures evolutionarily conserved regulatory rules" is inferred from cross-species prediction performance but is not directly demonstrated.
- The claim that XChrom can "accurately identify" TF activities in novel cell states is based on correlation with known biology but lacks direct validation.
- The claim that XChrom "does not simply memorize shallow RNA-to-ATAC mappings" is not directly tested.
- The practical utility of XChrom for predicting chromatin accessibility in new samples is not fully established due to the incomplete cross-sample analysis.