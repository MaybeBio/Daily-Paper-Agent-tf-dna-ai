## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, tables referenced but not fully provided)
- **Assessment boundary** Scientific and technical soundness of the claims as presented in the supplied text; no assessment of code, data availability, or reproducibility artifacts beyond what is described
- **Shared manuscript claim summary** The authors propose a sequence-based deep learning model for DNA-binding residue prediction that combines a pre-trained protein language model (ProtBert), an attention-based encoder, and a contrastive learning module. They report state-of-the-art performance on two benchmark datasets, demonstrate generalization via cross-dataset transfer, and claim that interpretability analysis of attention scores reveals structural information capture consistent with a graph neural network model.
- **Visible evidence base** Tables 2, 3, 4 (referenced, values partially reported in text); Figures 1, 2, 3, 4, 5 (described, not visible); Supplementary Figures 1, 2, 3, 4 and Supplementary Table 1 (referenced, not visible)
- **Missing materials affecting confidence** Full tables with all metric values; all figures; supplementary materials; hyperparameter settings; training details; baseline model descriptions; statistical significance tests; code or data availability statement

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology with a reasonable methodological approach. The combination of a pre-trained protein language model with attention mechanisms and contrastive learning is sensible, and the reported performance improvements are potentially interesting. However, the evidence as presented is incomplete in several critical respects. Key performance numbers are partially reported, figures and tables are not visible, and the interpretability analysis, while novel in framing, lacks quantitative validation. The claim that the sequence-based model "learned structural information" is supported only by qualitative visual inspection of a small number of examples. The manuscript would benefit from clearer reporting of experimental details, statistical significance testing, and a more rigorous treatment of the interpretability claims.
- **Who would be interested in the results, and why** Researchers working on protein-DNA interaction prediction, computational drug design, and protein function annotation would find the methodological contributions relevant. The interpretability analysis may also interest the broader deep learning for biology community, particularly those studying what language models learn about protein structure.
- **Major strengths** The problem is well-motivated and practically important. The use of a pre-trained protein language model without fine-tuning is computationally efficient and methodologically clean. The inclusion of a contrastive learning module to address class imbalance is thoughtful. The parallel design of sequence-based and structure-based models for interpretability comparison is a creative approach.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (incomplete performance reporting), R1-M2 (lack of statistical significance testing), R1-M3 (interpretability claim not quantitatively validated), R1-M4 (baseline comparison fairness unclear)
- **Assessment against Nature-style criteria** Originality: moderate. The combination of components is novel, but each individual component is established. Scientific importance: moderate. DNA-binding residue prediction is a useful task, but the incremental improvement over existing methods needs to be clearly demonstrated. Interdisciplinary readership: limited. The manuscript is primarily of interest to computational biologists and machine learning practitioners working on protein problems. Technical soundness: currently not fully assessable due to missing details and incomplete reporting. Readability for nonspecialists: acceptable, though the methods section assumes familiarity with deep learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea has merit, but the current evidence base is insufficient to fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that the proposed method "outperformed all other sequence-based models across two prevalent benchmark datasets" and reports specific metric values in the text.
- **Evidence pointer** Tables 2 and 3, location not provided
- **Concern** The performance comparison is reported incompletely. For Dataset1, only specificity, precision, F1, MCC, and AUC are given for the proposed model, with a partial comparison to DBPred. For Dataset2, the text states the model "outperformed all sequence-based models and three structure-based models on the AUC metric" but does not provide the full set of metric values for all compared methods. The tables are referenced but not visible in the supplied material.
- **Why it matters** Without complete performance tables, the reader cannot verify the claimed state-of-the-art performance, assess the magnitude of improvement, or evaluate whether the differences are practically meaningful. The central claim of the manuscript depends on this evidence.
- **Resolution test** Provide full tables with all metrics for all compared methods on both datasets, including standard deviations if available. Report the exact values for every metric mentioned in the text.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that the proposed model "significantly outperformed" and "outperformed" existing methods on benchmark datasets.
- **Evidence pointer** Section 3.1, Tables 2 and 3, location not provided
- **Concern** No statistical significance testing is reported. The text uses the word "significantly" without any supporting statistical analysis. Given the class imbalance in the datasets and the potential for variance across training runs, it is unclear whether the reported improvements are robust or within the range of random variation.
- **Why it matters** Claims of superiority over existing methods require statistical support, particularly in deep learning applications where results can vary across random seeds. Without significance testing or confidence intervals, the reader cannot distinguish genuine improvement from noise.
- **Resolution test** Report statistical significance tests (e.g., bootstrapping, paired tests across multiple runs) or confidence intervals for the key performance metrics. State the number of independent runs and the variance observed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The manuscript claims that "the sequence-based model learned structural information" and that attention scores are consistent with graph edge weights, based on interpretability analysis.
- **Evidence pointer** Section 3.3, Figure 5, Supplementary Figures 3 and 4, location not provided
- **Concern** The interpretability analysis is qualitative. The manuscript selects a small number of proteins with high prediction accuracy and visually compares attention weights with graph edge weights. No quantitative measure of consistency is provided. The claim that the attention mechanism "captures structural information" is inferred from visual similarity in a few examples.
- **Why it matters** The interpretability claim is presented as a novel contribution and a key finding of the manuscript. Qualitative visual inspection of a handful of examples is insufficient to establish that the model systematically learns structural information. Without a quantitative metric, the claim remains anecdotal.
- **Resolution test** Provide a quantitative measure of consistency between attention weights and structural proximity or graph edge weights across a larger set of proteins. Report correlation coefficients or overlap metrics with appropriate statistical testing.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity
- **Claim pointer** The manuscript states that the proposed model was compared against existing methods on two benchmark datasets, and that Dataset1 is for sequence-based models while Dataset2 includes both sequence-based and structure-based models.
- **Evidence pointer** Section 2.1, Section 3.1, Tables 2 and 3, location not provided
- **Concern** The baseline comparison is not fully described. It is unclear which specific methods were included in the comparison, whether the same training and testing splits were used for all methods, and whether the baselines were re-implemented or results were taken from published papers. The categorization of NucBind as a structure-based model is noted but the rationale is not fully explained.
- **Why it matters** Fair comparison against baselines is essential for establishing the validity of the performance claims. Without clarity on the comparison protocol, the reader cannot assess whether the reported improvements are due to methodological advantages or differences in experimental setup.
- **Resolution test** Clearly describe the baseline methods, their sources (re-implemented or published results), the exact training and testing protocols, and any hyperparameter tuning performed for baselines. Justify the categorization of each baseline method.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, Dataset description
- **Evidence pointer** Section 2.1, location not provided
- **Issue** The description of Dataset1 is incomplete. The text states that the dataset was pre-processed with a 30 percent sequence similarity threshold but the sentence is cut off. The composition of the dataset in terms of protein families, sequence length distribution, and the source of the data is not fully described.
- **Required correction** Complete the description of the dataset preprocessing and provide a full characterization of both datasets, including the number of proteins, the distribution of binding and non-binding residues, and any filtering criteria applied.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.2, Model architecture
- **Evidence pointer** Section 2.2, location not provided
- **Issue** The model architecture is described at a high level, but several implementation details are missing. The number of attention heads, the number of layers, the hidden dimensions, the learning rate, the optimizer, the batch size, and the number of training epochs are not reported. The contrastive learning loss formulation is described but the temperature parameter and the weighting between contrastive and cross-entropy losses are not specified.
- **Required correction** Provide a complete specification of all hyperparameters and training details. Report the exact formulation of the combined loss function including all weighting terms.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.1, Performance comparison
- **Evidence pointer** Section 3.1, location not provided
- **Issue** The text reports percentage improvements over DBPred but the baseline values are not fully given. The sentence "This represents a substantial improvement over the second-best model, DBPred, with gains of 11.1" is incomplete.
- **Required correction** Complete the sentence and provide the full comparison table with all metric values for all methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 3.2, Contrastive learning analysis
- **Evidence pointer** Section 3.2, Table 4, location not provided
- **Issue** The t-SNE analysis is described as showing that the contrastive learning module produces "more distinguishable" embeddings. However, t-SNE visualizations are known to be sensitive to hyperparameters and can be misleading. The manuscript does not report the t-SNE hyperparameters used or provide any quantitative measure of cluster separability.
- **Required correction** Report t-SNE hyperparameters and consider adding a quantitative clustering metric (e.g., silhouette score) to support the visual interpretation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4, Discussion
- **Evidence pointer** Section 4, location not provided
- **Issue** The discussion mentions the potential of the contrastive learning module as a "general component" but does not discuss limitations of the study, such as the small number of proteins used in the interpretability analysis, the potential for dataset bias, or the computational cost of the approach.
- **Required correction** Add a limitations paragraph that addresses the scope of the interpretability analysis, the generalizability of the findings, and the computational requirements of the method.

## Risk / unsupported claims
- The claim that the proposed model "outperformed all other sequence-based models" on both datasets cannot be fully verified because complete comparison tables are not provided in the supplied material.
- The claim that the sequence-based model "learned structural information" is not quantitatively supported; the evidence is limited to qualitative visual inspection of a small number of examples.
- The claim that the contrastive learning module "improves the performance" of both models is supported by Table 4, but the magnitude of improvement and its statistical significance are not reported.
- The claim that the model demonstrates "robust generalization to unseen datasets" is based on a single transfer experiment, and the comparison to DBPred's transfer performance is not fully described.
- The statement that "large-scale pre-trained protein language models, together with attention mechanisms, can effectively capture structural information solely from protein sequence inputs" is a broad conclusion drawn from limited interpretability evidence and requires more rigorous validation.