## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not separately provided)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and reproducibility as presented in the provided text
- **Shared manuscript claim summary** The authors present an active machine learning framework to iteratively train models of cis-regulatory grammar in developing mouse photoreceptors. They claim that active learning more than doubles model performance compared to training on genomic data alone, and that the resulting models can distinguish functionally non-equivalent transcription factor binding sites in enhancers and silencers.
- **Visible evidence base** Results sections describing four rounds of active learning, two test sets (mutagenic series and genomic test set), benchmarking against random sampling, a second application in K562 cells, and multiple validation analyses
- **Missing materials affecting confidence** Figure panels referenced but not visible (Figures 1-5, Supplementary Figures S1-S10); exact numerical results for many comparisons; full model architecture details; hyperparameter search results; statistical significance testing details

## Reviewer
- **Overall assessment** This manuscript presents a compelling application of active learning to a challenging problem in regulatory genomics. The core idea is timely and well-motivated, and the authors demonstrate meaningful improvements in model performance through iterative uncertainty-based sampling. The validation analyses, particularly the discrimination of functionally non-equivalent binding sites and the identification of a novel NR1-family motif contribution, are thoughtful and address key limitations of prior approaches. However, several technical aspects require clarification and additional evidence to fully establish the claims, particularly regarding the generalizability of the approach, the statistical robustness of the reported improvements, and the biological interpretation of the learned grammar.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and machine learning applied to biology. The work is directly relevant to those studying cis-regulatory grammar, enhancer and silencer function, and the interpretation of non-coding variation. The active learning framework may also interest method developers working on experimental design for functional genomics assays.
- **Major strengths** The problem is important and the active learning approach is a novel and sensible solution. The experimental system (retinal explant MPRA) is well-suited to the question, and the inclusion of both enhancer and silencer measurements is a significant advantage. The validation strategy is multi-faceted, including known biological features (CRX motif affinity, homotypic clustering, GC content) and novel predictions (NR1-family motif). The benchmarking in a second cell type (K562) strengthens the generalizability claim. The authors also thoughtfully address the choice of uncertainty sampling metric and the importance of active versus inactive training examples.
- **Major Concerns** 
- **Minor Comments**
- **Technical failings that need to be addressed before the case is established** The lack of statistical significance testing for the key performance comparisons; the potential for circularity in the validation of the NR1-family motif; the limited description of the CNN architecture and training details; the absence of a clear comparison to state-of-the-art non-active-learning models trained on larger datasets.
- **Assessment against Nature-style criteria** Originality is high; the application of active learning to cis-regulatory grammar is novel. Scientific importance is substantial, as the problem of learning complex regulatory grammar is a major bottleneck. Interdisciplinary readership is plausible, though the technical detail may limit accessibility. Technical soundness is generally good but requires additional statistical rigor and clarity. Readability for nonspecialists is adequate but could be improved with more intuitive explanations of the active learning concept and the significance of the findings.
- **Recommendation posture** Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "After three rounds of active learning, the performance of these models more than doubled, on average" and "Active learning outperforms random sampling on a human cell culture dataset"
- **Evidence pointer** Figure 1c, Figure 4a, Figure 5b, location not provided
- **Concern** The central claim that active learning outperforms random sampling and doubles performance is not supported by any statistical significance testing. The manuscript reports point estimates (e.g., wF1 scores) but does not provide confidence intervals, error bars, or p-values for the comparisons between active learning and random sampling, or between rounds. Given the stochastic nature of model training and the variability in MPRA measurements, it is essential to demonstrate that the observed improvements are not due to chance.
- **Why it matters** The primary conclusion of the paper rests on the superiority of active learning over random sampling. Without statistical evidence, the claim is not established. This is particularly important because the differences in performance, while substantial, could be influenced by the specific test sets, the random initialization of models, or the particular sequences sampled.
- **Resolution test** Provide confidence intervals or error bars for the performance metrics, based on multiple independent model training runs (e.g., different random seeds) and/or bootstrapping of the test sets. Report p-values for the comparison between active learning and random sampling at each round, using an appropriate statistical test (e.g., paired bootstrap or permutation test).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of novel biological findings
- **Claim pointer** "The model identifies causal differences between CREs with similar TF binding motifs" and the identification of the NR1-family motif as important in the strong enhancer
- **Evidence pointer** Figure 2, Figure S6, location not provided
- **Concern** The validation of the NR1-family motif as a causal contributor to enhancer activity is potentially circular. The authors state that the NR1-family motif was "not detected as globally enriched among CRX-bound strong enhancers by traditional motif-enrichment analyses." However, the model was trained on data that includes the strong enhancer in question. The model's importance scores are derived from the training data, and the subsequent experimental validation (scrambling the NR1 motif) confirms the model's prediction. This is a valid approach, but the claim that the model "discovers" this motif is weakened if the motif is present in the training data and the model has simply learned its contribution. The authors should clarify whether the NR1-family motif was identified in a truly unbiased manner, or whether its importance was inferred from the training data and then validated.
- **Why it matters** The discovery of novel regulatory features is a key selling point of the approach. If the NR1-family motif finding is not robust to the training data composition, the claim of "discovery" is overstated. The authors need to demonstrate that the model's ability to identify this motif is not simply a reflection of its presence in the training set.
- **Resolution test** Perform a more rigorous out-of-sample validation. For example, train the model on a dataset that excludes the specific strong enhancer used in the validation, and then test whether the model still assigns high importance to the NR1-family motif in that held-out sequence. Alternatively, use a permutation test to show that the importance score assigned to the NR1-family motif is significantly higher than what would be expected by chance, given the model's training data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and comparison to existing methods
- **Claim pointer** "Active learning may be a more efficient approach because it generates training data that are enriched for positive examples of highly active sequences"
- **Evidence pointer** Figure 5, location not provided
- **Concern** The claim that active learning is more efficient than random sampling is only demonstrated in the context of a single, relatively small dataset (K562). The authors do not compare their approach to other state-of-the-art methods for modeling cis-regulatory activity, such as deep learning models trained on large-scale MPRA datasets (e.g., Enformer, Basenji) or other active learning strategies. The efficiency gain may not hold for larger datasets or for models with different architectures.
- **Why it matters** The practical utility of the proposed method depends on its ability to outperform existing approaches in realistic settings. Without a comparison to current best practices, the significance of the contribution is unclear.
- **Resolution test** Compare the performance of the active learning model to a model trained on a large, randomly sampled dataset of comparable size, and to a model trained on the full K562 dataset. Also, consider benchmarking against a published deep learning model for enhancer activity prediction. Report the computational cost of the active learning approach relative to these alternatives.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model interpretability and biological insight
- **Claim pointer** "The model learned the role of other TFs enriched in photoreceptor CREs" and the generation of hypotheses about motif order and spacing
- **Evidence pointer** Figure 3, location not provided
- **Concern** The biological insights derived from the model, such as the importance of NR1-family motifs and the predicted effects of motif positioning, are presented as hypotheses. However, the manuscript does not provide a clear framework for how these hypotheses can be tested beyond the specific examples shown. The authors should discuss the broader implications of their findings and how the model can be used to generate testable predictions for future experiments.
- **Why it matters** The value of the model extends beyond its predictive accuracy. The ability to generate novel, testable hypotheses about regulatory grammar is a major contribution. The authors should more clearly articulate the biological significance of their findings and how they advance our understanding of photoreceptor gene regulation.
- **Resolution test** Provide a more detailed discussion of the biological implications of the NR1-family motif finding and the predicted positional effects. Suggest specific experiments that could test these predictions, such as targeted mutagenesis of the NR1-family motif in the context of the full enhancer or genome editing to alter motif spacing.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Model architecture and training details
- **Evidence pointer** Methods section, location not provided
- **Issue** The description of the CNN architecture is brief. The number of layers, filter sizes, pooling strategies, and the use of regularization are mentioned, but the exact specifications are not provided. This limits the reproducibility of the work.
- **Required correction** Provide a complete description of the CNN architecture, including the number of filters, kernel sizes, stride, padding, and the use of batch normalization and dropout. Include a table or diagram of the architecture.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Processed data and code
- **Evidence pointer** Data and code availability section, location not provided
- **Issue** The authors state that processed data and code are available on GitHub, but the specific repository structure and the exact files are not described. This makes it difficult for readers to access and use the data and code.
- **Required correction** Provide a more detailed description of the GitHub repository, including the directory structure, the main scripts, and the format of the processed data files. Consider adding a README file with instructions for reproducing the main results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation of results
- **Affected element** Figure legends
- **Evidence pointer** Figures 1-5, location not provided
- **Issue** The figure legends are not provided in the manuscript text. This makes it difficult to interpret the figures without referring to the main text.
- **Required correction** Include the figure legends in the manuscript, either in the main text or as a separate section. Each legend should clearly describe the experimental design, the data shown, and the statistical tests used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Active learning" definition
- **Evidence pointer** Introduction, location not provided
- **Issue** The term "active learning" is used throughout, but the specific definition in the context of this work could be clarified. The authors should explicitly state that active learning refers to the iterative process of selecting new training examples based on model uncertainty, and distinguish it from other forms of sequential experimental design.
- **Required correction** Add a brief definition of active learning in the introduction, and clarify how it differs from passive learning or random sampling.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Correlation coefficients
- **Evidence pointer** Figure 3, location not provided
- **Issue** The manuscript reports Pearson correlation coefficients (PCC) for some comparisons but does not provide confidence intervals or p-values. This makes it difficult to assess the strength and significance of the correlations.
- **Required correction** Report confidence intervals and p-values for all correlation coefficients, or provide a measure of uncertainty such as the standard error.

## Risk / unsupported claims
- The claim that active learning "more than doubles" performance is not statistically supported.
- The claim that the model "discovers" the NR1-family motif is potentially overstated, as the motif is present in the training data.
- The claim that active learning is "more efficient" than random sampling is only demonstrated in one dataset and not compared to other methods.
- The claim that the model "learned the role of other TFs" is based on correlation and requires experimental validation.
- The claim that the model can be used to "generate hypotheses" is not fully developed, and the specific predictions are not clearly articulated.