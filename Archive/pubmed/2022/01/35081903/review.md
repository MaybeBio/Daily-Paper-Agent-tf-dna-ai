## Review setup
- **Input scope** Full manuscript text (abstract, background, methods, results, discussion, supplementary file descriptions)
- **Assessment boundary** Technical soundness, methodological novelty, validation rigor, and clarity of claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose DIDL, a deep learning method combining two DNN encoders with a tensor factorization predictor, to predict inter-omics interactions in multi-layer networks using only known inter-layer interactions, without relying on biochemical features. They report performance exceeding state-of-the-art methods across drug–target, TF–DNA, and miRNA–mRNA datasets, robustness to network sparsity, and successful prediction of interaction types in a complex multi-layer network.
- **Visible evidence base** Methods section (encoder, predictor, training, experimental setup), Results section (Figs. 1–6, Table 1), Discussion section, supplementary file descriptions
- **Missing materials affecting confidence** Actual performance metrics (AUC, AUPRC, precision, recall, accuracy values), figures and tables themselves, dataset preprocessing details, hyperparameter search ranges, baseline implementation details, statistical significance testing details, code availability, and full supplementary files

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach that combines deep neural network encoders with tensor factorization for inter-omics interaction prediction. The core idea of using only inter-layer interactions and avoiding reliance on biochemical features is appealing and could have practical value. However, the current text lacks sufficient quantitative detail to verify the reported performance claims. Key experimental results are referenced but not shown in the provided material, making it impossible to assess whether the method genuinely outperforms baselines or whether the reported robustness and validation claims are statistically supported. The methodological description is clear at a high level but omits important implementation details that would affect reproducibility. The novelty relative to existing deep learning-based link prediction methods is not fully articulated. The manuscript would benefit from a more rigorous and complete presentation of results, baselines, and limitations.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on network integration, link prediction, and multi-omics data analysis would be the primary audience. Researchers developing deep learning methods for biological network inference would find the encoder-predictor architecture of interest. Those working on drug repurposing, miRNA target prediction, and transcriptional regulation might also find the application demonstrations useful, provided the performance claims are substantiated.

- **Major strengths**
  1. The method addresses a relevant problem: predicting inter-omics interactions without requiring biochemical features, which broadens applicability to less-characterized molecule types.
  2. The architecture is conceptually simple and modular, combining representation learning with tensor factorization in an end-to-end trainable framework.
  3. The evaluation spans multiple interaction types and includes a complex multi-layer network (Hetionet), which is commendable.
  4. The robustness analysis with respect to network sparsity is a useful practical consideration.
  5. The T-SNE visualization showing clustering of miRNAs by family provides an interpretable sanity check.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that DIDL outperformed state-of-the-art methods across all three datasets, with AUC and AUPRC exceeding 0.85 and 0.83 respectively.
- **Evidence pointer** Results section, Fig. 2; location not provided for actual metric values
- **Concern** The actual performance values, baseline results, and statistical comparison are not presented in the provided text. The claim of outperformance is stated but cannot be verified without seeing the numerical results, error bars, or significance tests. The figure is referenced but not available in the provided material.
- **Why it matters** The central claim of the paper is that DIDL is superior to existing methods. Without the actual numbers and appropriate statistical testing, this claim is unsupported. The reader cannot assess the magnitude of improvement, whether it is consistent across datasets, or whether it is statistically meaningful.
- **Resolution test** Provide the full results table with mean and standard deviation for each metric, for each method and dataset, along with the results of appropriate statistical tests (e.g., paired t-tests or Wilcoxon signed-rank tests) comparing DIDL to each baseline.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The authors state that negative sampling was applied with a ratio equal to 1, resulting in balanced data.
- **Evidence pointer** Methods section, "Model training and optimization"; location not provided
- **Concern** The negative sampling strategy is described only briefly. It is unclear how negative samples were selected (uniform random among all unobserved pairs?), whether the sampling was performed once or repeatedly during training, and how this affects the evaluation. The statement "Since negative sampling is equal to 1, therefore the data is balanced" is ambiguous. Additionally, the potential issue of false negatives (unobserved interactions treated as negatives) is acknowledged but not addressed in terms of its impact on evaluation metrics.
- **Why it matters** Negative sampling is a critical component of the training procedure and directly affects the learned representations and the evaluation. Without a clear description, the results cannot be reproduced, and the validity of the evaluation may be compromised if the negative sampling introduces bias.
- **Resolution test** Provide a detailed description of the negative sampling procedure, including the sampling distribution, whether it is done per epoch or once, and how the test set is constructed. Discuss the potential impact of false negatives on the reported metrics and consider using evaluation protocols that account for this (e.g., ranking-based metrics).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** The authors claim that 7 out of 10 top predicted miRNA–mRNA interactions were confirmed by experimental evidence not yet in miRTarBase.
- **Evidence pointer** Results section, Table 1; location not provided for the literature search methodology
- **Concern** The literature validation is presented as a key evidence of the method's practical utility, but the methodology for this validation is not described. It is unclear how the literature search was conducted, what criteria were used to consider an interaction "confirmed," and whether the search was blinded to the prediction results. The table lists citations but the provided text does not include them.
- **Why it matters** Literature-based validation is a common but potentially biased approach. Without a clear and systematic protocol, the claim of 7 out of 10 confirmations is anecdotal and cannot be independently assessed. The selection of the top 10 predictions for validation also needs justification.
- **Resolution test** Describe the literature search protocol in detail, including databases searched, search terms, inclusion criteria, and whether the search was performed independently of the prediction results. Provide the full citations and a summary of the evidence for each confirmed interaction.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Baseline comparison fairness
- **Claim pointer** The authors state that DIDL outperformed node2vec, DeepWalk, CN, and JI, and that the difference with GCN-DTI is "subtle" despite DIDL using less information.
- **Evidence pointer** Results section, Fig. 2 and Additional file 2; location not provided for baseline implementation details
- **Concern** The baseline methods are mentioned but their implementation details are not provided. It is unclear whether the baselines were tuned fairly, whether the same train/test splits were used, and whether the evaluation protocol was identical. For GCN-DTI, the comparison is described as "subtle" but the actual numbers are not given.
- **Why it matters** Fair comparison with baselines is essential to support the claim of outperformance. If baselines are not properly tuned or evaluated under the same conditions, the comparison is not meaningful. The "subtle" difference with GCN-DTI, which uses additional information, needs to be quantified to assess the trade-off.
- **Resolution test** Provide implementation details for all baselines, including hyperparameter settings and tuning procedures. Report the full comparison table with all metrics for all methods. Clarify the evaluation protocol to ensure it is identical across methods.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Novelty positioning
- **Claim pointer** The authors describe DIDL as a "novel nonlinear deep learning method" and a "novel autoencoder architecture."
- **Evidence pointer** Abstract and Discussion; location not provided
- **Concern** The novelty of the approach is not clearly positioned relative to existing deep learning-based link prediction methods, such as graph neural networks, variational autoencoders for link prediction, or other matrix/tensor factorization with deep learning. The combination of DNN encoders with tensor factorization is not new in the recommender systems literature, and the authors do not discuss how their approach differs from or advances beyond these existing methods.
- **Why it matters** For a methods paper, clear positioning of novelty is critical. Without a thorough comparison to related work, the reader cannot assess the contribution. The claim of novelty needs to be substantiated with a discussion of prior art and a clear statement of what is genuinely new.
- **Resolution test** Add a dedicated related work section that discusses deep learning-based link prediction, tensor factorization methods, and their applications in biology. Clearly articulate the specific contributions of DIDL relative to these methods.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Model training and optimization"
- **Evidence pointer** Location not provided
- **Issue** The sentence "Since negative sampling is equal to 1, therefore the data is balanced" is grammatically awkward and conceptually unclear. It likely means the negative-to-positive ratio is 1:1, but this should be stated explicitly.
- **Required correction** Rewrite to clearly state the negative-to-positive sampling ratio and how balance is achieved.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Experimental setup"
- **Evidence pointer** Location not provided
- **Issue** The description of the neural network architecture is incomplete. The number of layers is stated (4), but the number of neurons per layer, activation functions beyond ReLU, dropout rates, and L2 regularization strength are not fully specified.
- **Required correction** Provide a complete specification of the network architecture and all hyperparameters, or reference a publicly available code repository.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, Fig. 2
- **Evidence pointer** Location not provided
- **Issue** The text mentions "T test analysis (P value < 0.05)" but does not specify what was compared, how many comparisons were made, or whether multiple testing correction was applied.
- **Required correction** Clarify the statistical testing procedure, including the number of comparisons and whether corrections for multiple testing were applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "Prediction of interaction in a complex multi-layer network"
- **Evidence pointer** Additional file 5; location not provided
- **Issue** The results for the Hetionet application are described only qualitatively ("could successfully predict interactions"). No metrics are provided in the text.
- **Required correction** Provide quantitative results for the Hetionet evaluation, either in the main text or by summarizing the key findings from Additional file 5.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** Results, "miRNA-mRNA interaction prediction"
- **Evidence pointer** Fig. 4; location not provided
- **Issue** The T-SNE visualization is described as showing clustering by miRNA family, but the figure is not available. It is unclear how the clustering was quantified or whether it is visually apparent.
- **Required correction** Provide the figure and, if possible, a quantitative measure of clustering quality (e.g., silhouette score) to support the claim.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Location not provided
- **Issue** The term "inter-omics interactions" is used throughout, but the datasets include drug–target, TF–DNA, and miRNA–mRNA, which are not all strictly "omics" in the same sense. The terminology could be clarified.
- **Required correction** Consider using a more precise term such as "cross-layer interactions" or "heterogeneous molecular interactions" and define it clearly at first use.

## Risk / unsupported claims
- The claim that DIDL outperformed state-of-the-art methods is unsupported in the provided text because actual performance values and statistical comparisons are not shown.
- The claim that 7 out of 10 top predictions were experimentally confirmed is unsupported without a described literature search methodology and the actual citations.
- The claim of robustness to network sparsity is only qualitatively described; the actual degradation curves and thresholds are not provided.
- The claim that DIDL is a "novel" architecture is not substantiated with a comparison to related work.
- The claim that the method is applicable to a "wide variety of networks" is plausible but not demonstrated beyond the three datasets and one multi-layer network mentioned.
- The performance of the interaction type prediction (Fig. 5b) is not quantified in the text.
- The comparison with GCN-DTI is described as "subtle" but no numbers are provided to assess the trade-off.