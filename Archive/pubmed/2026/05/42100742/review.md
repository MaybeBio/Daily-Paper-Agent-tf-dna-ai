## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends, tables)
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to presented evidence, and suitability for the stated journal context
- **Shared manuscript claim summary** The authors present PNABPred, a multi-modal framework combining ESM-2 protein language model embeddings with Atchley factors (biophysical) and BLOSUM50 substitution matrix (evolutionary) priors, to predict protein-nucleic acid interactions at both protein-level (binding vs. non-binding) and residue-level (binding site prediction) tasks. They report state-of-the-art performance on multiple benchmark datasets, improved generalization on newly curated and cross-training datasets, and demonstrate via ablation studies that each modality contributes to performance.
- **Visible evidence base** Results section with performance tables (Tables 1 and 2), ablation study descriptions (Figure 3, Tables S7 and S8), case studies (Figure 4, Figure S5), t-SNE visualizations (Figure 3C-F, Figure S2), amino acid composition analysis (Figure S3), and methodological details in STAR Methods
- **Missing materials affecting confidence** Actual figure images (only legends provided), supplemental tables S1-S10 contents, hyperparameter details (Table S10), specific dataset statistics, baseline model reproduction details, and the newly curated BioLiP dataset composition

## Reviewer

### Overall assessment
The manuscript presents a technically competent and well-motivated framework for protein-nucleic acid interaction prediction. The multi-modal feature fusion strategy is sensible, and the reported performance improvements over existing methods are notable. However, several methodological concerns regarding dataset leakage, baseline fairness, statistical rigor, and the interpretation of ablation results need to be addressed before the core claims can be fully established. The work is likely of interest to the computational biology community, but the current evidence base does not fully support all stated conclusions.

### Who would be interested in the results, and why
Computational biologists and bioinformaticians working on protein function prediction, particularly those focused on nucleic acid binding proteins. Researchers developing protein language model applications for downstream prediction tasks would also find the multi-modal integration strategy relevant. Additionally, experimental biologists studying protein-nucleic acid interactions may find PNABPred useful as a screening tool, though they are less likely to be the primary audience given the technical focus.

### Major strengths
1. The multi-modal feature fusion approach is well-reasoned, combining complementary information sources (semantic, biophysical, evolutionary) in a principled manner.
2. The use of parameter-efficient fine-tuning (LoRA) for the large ESM-2 model is practical and addresses computational feasibility concerns.
3. The evaluation is comprehensive, covering multiple benchmark datasets, protein-level and residue-level tasks, and including generalization assessments.
4. The ablation studies and feature visualization provide useful insights into model behavior and component contributions.
5. The case studies on diverse protein systems help demonstrate practical utility beyond aggregate metrics.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data leakage and benchmark integrity
- **Claim pointer** The authors claim PNABPred "outperforms other state-of-the-art sequence-based methods" on benchmark datasets, and that the newly curated BioLiP test sets enable "rigorous generalization testing."
- **Evidence pointer** Results section, "PNABPred improves the accuracy of protein-nucleic acid binding prediction"; Methods, "Datasets"
- **Concern** The manuscript states that all test sets were filtered via CD-HIT to ensure a maximum of 30% sequence identity "against our training data." However, the training data composition is not described in sufficient detail. It is unclear whether the training set includes sequences from the same families or folds as the test sets, and whether the 30% threshold was applied symmetrically (i.e., also removing training sequences similar to test sequences). More critically, the newly curated BioLiP datasets were constructed with a January 2025 cutoff, but the manuscript does not specify whether these sequences were checked for redundancy against the training data of the baseline models being compared. If baseline models were trained on data overlapping with these new test sets, the comparison would be unfair. Additionally, the manuscript does not report the number of proteins in each dataset, the sequence length distributions, or the proportion of positive versus negative examples, making it difficult to assess potential class imbalance effects.
- **Why it matters** If test sequences share significant similarity with training sequences, reported performance may reflect memorization rather than generalization. This would undermine the central claim of superior predictive accuracy and would mislead potential users about real-world performance on novel proteins.
- **Resolution test** Provide a detailed description of training data construction, including source databases, redundancy removal procedures, and the exact relationship between training and test sets. Report sequence identity statistics between training and test sets. For the BioLiP-derived datasets, specify the clustering threshold used and confirm that baseline models were evaluated under identical conditions. Include dataset size and class balance information.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of performance comparisons
- **Claim pointer** The authors state that PNABPred's improvements over baseline methods are significant, citing p < 0.05 from Mann-Whitney U tests.
- **Evidence pointer** Results section, "PNABPred improves the accuracy of protein-nucleic acid binding prediction"; Methods, "Statistical analysis"
- **Concern** The statistical comparison methodology is inadequately described. The manuscript states that a Mann-Whitney U test was used to compare PNABPred against "the second-best performing baseline model," but it is unclear what constitutes the statistical sample. If the test was performed on per-residue predictions, the assumption of independence is violated due to spatial autocorrelation within proteins. If performed on per-protein metrics, the sample size may be very small. Furthermore, the manuscript reports only p-values without effect sizes or confidence intervals. The Benjamini-Hochberg correction is mentioned but the number of comparisons and which comparisons were included in the correction are not specified. The reported p-values in the text (e.g., "p < 0.05") are not tied to specific comparisons or datasets.
- **Why it matters** Without a clearly defined and statistically valid comparison framework, the claimed superiority of PNABPred cannot be properly evaluated. Readers cannot determine whether the observed differences are meaningful or within the range of random variation.
- **Resolution test** Clearly specify the unit of analysis (per-protein or per-residue), the number of samples in each comparison, and the exact statistical test procedure. Report effect sizes with confidence intervals. Provide the full table of adjusted p-values for all pairwise comparisons across all datasets and metrics. If per-residue analysis was used, employ appropriate methods that account for spatial dependence (e.g., cluster-robust standard errors or permutation tests at the protein level).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline fairness and reproducibility
- **Claim pointer** The authors claim PNABPred outperforms "the transformer-based method CLAPE-DB" and other baselines, with specific percentage improvements reported.
- **Evidence pointer** Results section, Tables 1 and 2; Methods, "Datasets"
- **Concern** The manuscript does not describe how baseline models were implemented or reproduced. For methods like CLAPE-DB, Seq-RBPPred, and others, it is unclear whether the authors used original implementations, retrained models, or used published performance values. If published values were used, differences in training data, preprocessing, and evaluation protocols could confound comparisons. If models were retrained, the training details (hyperparameters, data splits, early stopping criteria) are not provided. The manuscript also does not report whether baseline models were tuned on the same validation sets as PNABPred, which could introduce bias in favor of the proposed method. The percentage improvements reported (e.g., "17.44% higher MCC") are relative improvements, but the absolute differences are small in some cases (e.g., MCC 0.889 vs. 0.757), and the practical significance of these differences is not discussed.
- **Why it matters** Fair and reproducible baseline comparisons are essential for establishing that a new method genuinely advances the state of the art. Without detailed baseline reproduction information, readers cannot verify the claimed improvements or assess whether they stem from methodological advances or from implementation details.
- **Resolution test** Provide detailed descriptions of baseline implementations, including source code availability, hyperparameter settings, and training procedures. If published performance values were used, clearly state this and discuss potential differences in evaluation protocols. Consider reporting absolute performance differences alongside relative improvements. Make all code and trained models publicly available to enable independent verification.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalization claim support
- **Claim pointer** The authors claim "PNABPred showed significantly higher accuracy than other models" on the independent Test_181 dataset and newly curated BioLiP datasets, supporting "rigorous generalization assessment."
- **Evidence pointer** Results section, "PNABPred has better generalization ability"; Figure 2E-F; Table S4
- **Concern** The generalization assessment is described only briefly in the main text, with detailed results relegated to supplementary tables. The manuscript does not report the number of proteins in the Test_181 dataset, the sequence identity distribution between Test_181 and the training sets, or the composition of the newly curated BioLiP datasets. The cross-training experiments (Train_646 vs. Train_573) are mentioned but the results are not presented in the main text. It is unclear whether the performance differences on these generalization tests are statistically significant given the potentially small number of test proteins. The manuscript also does not discuss potential biases in the BioLiP dataset, such as overrepresentation of certain protein families or structural classes.
- **Why it matters** The generalization claim is central to the manuscript's stated contribution of improved real-world applicability. If the independent test sets are small, biased, or share significant similarity with training data, the generalization results may not be reliable indicators of real-world performance.
- **Resolution test** Report detailed statistics for all generalization test sets, including number of proteins, sequence identity distributions relative to training data, and class balance. Present the cross-training results in the main text with appropriate statistical analysis. Discuss potential biases in the BioLiP-derived datasets and how they might affect interpretation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Ablation study interpretation
- **Claim pointer** The authors state that ablation studies "confirm that each module substantially contributes to improving the accuracy of PNABPred."
- **Evidence pointer** Results section, "Analysis of module contribution and model feature representation"; Figure 3A-B; Tables S7 and S8
- **Concern** The ablation results are described qualitatively in the text, with detailed numbers in supplementary tables. The manuscript reports that removing the pLM module causes the largest performance drop, which is expected given the dominance of ESM-2 embeddings. However, the contribution of biophysical and evolutionary features appears modest in some cases (e.g., MCC decrease from 0.468 to 0.460 for biophysical features in DNA binding site prediction). The manuscript does not report whether these differences are statistically significant across the 10 training runs. The t-SNE visualizations are described as showing "distinct, well-separated clusters" but the actual figures are not available for inspection, and the interpretation of such visualizations is inherently subjective.
- **Why it matters** The claim that each modality contributes meaningfully to performance is a key part of the manuscript's contribution. If the contributions of biophysical and evolutionary features are not statistically significant, the multi-modal approach may not be justified over simpler alternatives.
- **Resolution test** Report statistical significance tests for all ablation comparisons, including effect sizes and confidence intervals. Provide quantitative cluster separation metrics (e.g., silhouette scores) in addition to t-SNE visualizations. Discuss the practical significance of the observed performance differences.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of contribution
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction, paragraph 3
- **Issue** The abstract states PNABPred "outperforms other state-of-the-art sequence-based methods" but does not specify the scope of comparison (e.g., which methods, which datasets). The introduction would benefit from a clearer statement of what specific gap in existing methods PNABPred addresses beyond the general observation that current methods have limitations.
- **Required correction** Specify in the abstract the key comparison methods and datasets. In the introduction, articulate the specific limitations of existing pLM-based approaches that motivate the multi-modal integration strategy.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods, "Multi-modal feature representation"
- **Evidence pointer** Methods section, "Multi-modal feature representation"
- **Issue** The description of the ESM-2 embedding extraction states that "per-residue embeddings from the final (33rd) layer" are used, but it is unclear whether these are the raw hidden states or if any pooling or projection is applied before concatenation with the other feature streams. The dimensionality of the Atchley and BLOSUM embeddings after projection is stated as 512, but the final concatenated dimension is 2304 (1280 + 512 + 512), which is consistent. However, the intra-modal refinement layer architecture is described only briefly.
- **Required correction** Clarify whether raw ESM-2 hidden states are used directly or if any transformation is applied. Provide more detail on the intra-modal refinement layer, including the number of attention heads, feedforward dimensions, and whether residual connections are used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evaluation metrics
- **Affected element** Methods, "Evaluation and statistical analysis"
- **Evidence pointer** Methods section, "Evaluation and statistical analysis"
- **Issue** The manuscript reports Precision, F1, MCC, and AUROC but does not report Recall separately, despite the formula being provided. For residue-level prediction tasks where positive samples (binding residues) are typically a small fraction of all residues, Recall and Precision-Recall AUC would be informative. The choice of AUROC over PR-AUC for imbalanced data is not discussed.
- **Required correction** Report Recall values or PR-AUC in addition to the current metrics. Discuss the class imbalance in the datasets and justify the choice of evaluation metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Case study selection
- **Affected element** Results, "Case studies illustrate PNABPred's accuracy on diverse proteins"
- **Evidence pointer** Results section, "Case studies illustrate PNABPred's accuracy on diverse proteins"; Figure 4
- **Issue** The case studies are described as "representative" but the selection criteria are not stated. It is unclear whether these were chosen to showcase successes or whether they represent typical performance. The manuscript reports that PNABPred "correctly identified all DNA-binding sites" on one protein (7KUF) but does not provide quantitative comparison with baseline methods for these specific cases.
- **Required correction** State the selection criteria for case study proteins. Provide quantitative comparison with at least one baseline method for each case study to contextualize the qualitative observations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Computational cost
- **Affected element** Methods, "Parameter-efficient fine-tuning and model training"
- **Evidence pointer** Methods section, "Parameter-efficient fine-tuning and model training"
- **Issue** The manuscript mentions training on an NVIDIA A100 GPU but does not report training time, inference time, or memory requirements. For a framework intended for scalable sequence screening, these practical considerations are relevant.
- **Required correction** Report training time, inference speed, and GPU memory usage. Discuss the computational trade-offs of the multi-modal approach compared to simpler baselines.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and code availability
- **Evidence pointer** Data and code availability section
- **Issue** The data and code are deposited at a Zenodo DOI, which is appropriate, but the manuscript does not specify the license under which the code is released or whether the trained model weights are included in the deposit.
- **Required correction** Specify the software license and confirm whether trained model weights are included in the data deposit.

### Technical failings that need to be addressed before the case is established
1. Insufficient description of training data construction and its relationship to test sets (R1-M1)
2. Inadequate statistical comparison methodology (R1-M2)
3. Lack of baseline reproduction details (R1-M3)
4. Incomplete reporting of generalization test set characteristics (R1-M4)

### Assessment against Nature-style criteria

**Originality:** The multi-modal integration of pLM embeddings with biophysical and evolutionary priors is a reasonable and somewhat novel contribution, though the individual components are well-established. The specific combination and its application to nucleic acid binding prediction appears to be new, but the conceptual advance over existing pLM fine-tuning approaches is incremental rather than transformative.

**Scientific importance:** Protein-nucleic acid interaction prediction is an important problem in functional genomics and drug discovery. The reported performance improvements, if reproducible and statistically robust, would be practically useful. However, the importance is primarily incremental, improving upon existing methods rather than enabling fundamentally new capabilities.

**Interdisciplinary readership:** The work is primarily of interest to computational biologists and bioinformaticians. The potential applications in biotechnology and therapeutic development are mentioned but not developed in sufficient detail to attract a broader readership. The manuscript is unlikely to appeal to experimental biologists or clinicians without additional validation in those contexts.

**Technical soundness:** The framework architecture is technically sound, and the use of LoRA for parameter-efficient fine-tuning is appropriate. However, the evaluation methodology has significant gaps in statistical rigor and baseline fairness that need to be addressed. The ablation study design is reasonable but the interpretation of small performance differences requires more careful statistical treatment.

**Readability for nonspecialists:** The manuscript is generally well-written and accessible to readers with a computational biology background. The introduction provides adequate context, and the methods are described with sufficient detail for reproduction. However, the results section relies heavily on technical metrics (MCC, AUROC) without sufficient interpretation of practical significance for nonspecialist readers.

### Recommendation posture
**Supportive if technical concerns are resolved.** The core idea is sound and the reported results are promising, but the manuscript currently does not provide sufficient evidence to fully establish the claims of superior performance and generalization. The authors should address the concerns regarding data leakage, statistical rigor, and baseline fairness before the case is fully made. With these issues resolved, the work would be a solid contribution to the computational biology literature.