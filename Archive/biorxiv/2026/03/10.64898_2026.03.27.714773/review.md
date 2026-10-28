## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusions, supplementary statements)
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present IDBSpred, a sequence-based machine learning method using ESM-2 protein language model embeddings and a multilayer perceptron to predict residue-level IDP-binding sites on structured partner proteins, trained on the DIBS database, achieving an ROC AUC of 0.87 and average precision of 0.61, with structural case studies showing recovery of major binding interfaces.
- **Visible evidence base** Abstract, Introduction, Model and Methods, Results (including descriptions of Figures 1-4), Conclusions, Code availability statement
- **Missing materials affecting confidence** Actual figures (Figures 1-4) not provided; no quantitative performance metrics beyond ROC AUC and average precision; no baseline comparisons; no cross-validation details; no dataset statistics (e.g., number of proteins, residue counts, class balance); no hyperparameter tuning details; no statistical significance tests; no external validation on independent datasets

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and understudied problem, namely predicting IDP-binding sites on structured partners, which complements existing disorder-centric predictors. The use of ESM-2 embeddings with a simple MLP is a reasonable and potentially scalable approach. However, the current evidence base is insufficient to establish the method's utility or superiority. Key limitations include the absence of baseline comparisons, lack of dataset characterization, no cross-validation or independent testing, and no quantitative evaluation of the structural case studies. The claims of effectiveness and practical utility are therefore not fully supported by the provided material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein-protein interaction prediction, intrinsically disordered proteins, and machine learning applications in structural biology. Researchers studying IDP-mediated signaling and therapeutic targeting of such interfaces may also find the tool relevant, provided the method is validated more rigorously.
- **Major strengths** The problem is well-motivated and addresses a genuine gap in the field. The use of protein language model embeddings is contemporary and aligns with current trends. The method is simple and potentially reproducible, with code availability stated. The amino acid composition analysis provides useful biological insight into IDP-binding site preferences.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no baseline comparisons), R1-M2 (no dataset characterization), R1-M3 (no cross-validation or independent testing), R1-M4 (no quantitative evaluation of case studies), R1-M5 (no statistical significance testing)
- **Assessment against Nature-style criteria** Originality: Moderate. The problem is relatively underexplored, but the methodological approach (ESM-2 embeddings plus MLP) is not novel in itself. Scientific importance: Potentially high if validated, as IDP-mediated interactions are biologically significant and therapeutically relevant. Interdisciplinary readership: The topic bridges computational biology, structural biology, and drug discovery, which could attract a broad audience. Technical soundness: Currently insufficient. The lack of baseline comparisons, dataset details, and rigorous evaluation protocols undermines confidence in the reported performance. Readability for nonspecialists: The manuscript is generally clear and accessible, though some methodological details are underspecified.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but substantial additional work is required to demonstrate that IDBSpred performs competitively and reliably.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "IDBSpred achieves strong overall performance in distinguishing binding from non-binding residues" and "the combination of ESM-2 embeddings and a simple MLP provides an effective framework"
- **Evidence pointer** Results section, Figure 3
- **Concern** The manuscript reports ROC AUC of 0.87 and average precision of 0.61 but provides no comparison against existing methods or simpler baselines. It is unclear whether the ESM-2 embeddings and MLP architecture offer any advantage over, for example, sequence composition features, one-hot encoding, or existing predictors such as Disobind. Without such comparisons, the claimed effectiveness cannot be contextualized.
- **Why it matters** A new predictor must demonstrate added value over existing approaches to justify its use. The absence of baselines makes it impossible to assess whether the reported performance is competitive or merely adequate.
- **Resolution test** Provide quantitative comparisons against at least one existing IDP-binding site predictor and one or more simple baseline models (e.g., logistic regression on amino acid composition, SVM on one-hot encoding) using the same train/test split. Report ROC AUC, average precision, and other relevant metrics for all methods.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "Training and evaluation data were collected from the DIBS database, which contains more than 700 non-redundant interacting complexes"
- **Evidence pointer** Model and Methods, Based Dataset construction
- **Concern** The dataset is described only as "more than 700 non-redundant complexes" with no further details. The number of proteins, total residues, number of positive and negative samples, class imbalance ratio, and sequence redundancy filtering criteria are not reported. This information is essential for understanding the problem difficulty and for reproducing the work.
- **Why it matters** Without dataset statistics, readers cannot assess the representativeness of the training data, the severity of class imbalance, or the potential for data leakage. Reproducibility is a core requirement for computational methods.
- **Resolution test** Report the exact number of complexes, proteins, residues, positive and negative samples, and the class imbalance ratio. Describe the redundancy filtering procedure used by DIBS and any additional filtering applied. Provide the train/test split in a reproducible manner (e.g., by protein or complex ID).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The training loss decreases steadily over the course of 25 epochs... the model reaches a consistent level of generalization on the held-out test data"
- **Evidence pointer** Results section, Figure 3a
- **Concern** The evaluation protocol is limited to a single random train/test split of residues. No cross-validation, no multiple random seeds, and no independent test set are described. The reported performance metrics may be highly dependent on the specific split, and the generalization claims are therefore not robustly supported.
- **Why it matters** Single-split evaluation can lead to overoptimistic or unstable performance estimates, especially with imbalanced data. Robust evaluation is necessary to establish that the method generalizes beyond the specific training sample.
- **Resolution test** Perform k-fold cross-validation (e.g., 5-fold) at the protein or complex level to avoid residue-level leakage. Report mean and standard deviation of ROC AUC and average precision across folds. If computational cost is a concern, justify the single-split approach with a clear rationale.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Structural case studies further showed that the predicted sites largely overlap with experimentally defined interfaces and can successfully recover the major binding regions in representative complexes"
- **Evidence pointer** Results section, Figure 4
- **Concern** The case studies are described qualitatively ("largely overlaps", "some local over-prediction", "somewhat more fragmented") without any quantitative metrics such as precision, recall, F1-score, or overlap coefficients (e.g., Matthews correlation coefficient, Jaccard index) between predicted and experimental binding sites. The figures themselves are not provided, so the visual claims cannot be verified.
- **Why it matters** Qualitative descriptions are insufficient to support claims of accurate interface recovery. Quantitative evaluation is needed to demonstrate that the method provides practically useful predictions at the residue level.
- **Resolution test** For each case study, compute and report precision, recall, F1-score, and a spatial overlap metric (e.g., fraction of predicted positive residues within a certain distance of experimental binding sites). Provide the figures or a link to them for verification.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "Analysis of amino acid composition showed that IDP-binding sites are enriched in aromatic residues, especially Trp, Tyr, and Phe, as well as several charged and polar residues, whereas Ala and several small or conformationally restrictive residues are depleted"
- **Evidence pointer** Results section, Figure 2
- **Concern** The amino acid composition analysis is presented without any statistical testing. It is unclear whether the observed enrichments and depletions are statistically significant or could arise from random variation. No confidence intervals or effect sizes are reported.
- **Why it matters** Without statistical support, the biological interpretation of the composition bias is speculative. The claim that these features "distinguish them from general protein surfaces" requires formal testing against an appropriate background distribution.
- **Resolution test** Perform a statistical test (e.g., chi-square test, Fisher's exact test, or a permutation test) comparing amino acid frequencies at binding sites versus non-binding sites or versus the overall protein composition. Report p-values and effect sizes, with appropriate multiple testing correction.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "predicting the corresponding binding sites on the structured partner remains challenging" but does not specify what makes it challenging or how the proposed method addresses these specific challenges.
- **Required correction** Add one sentence in the abstract briefly stating the key challenge (e.g., lack of structural information, sequence diversity of IDPs) and how the method overcomes it.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model and Methods, Neural network classifier
- **Evidence pointer** Model and Methods, Neural network classifier
- **Issue** The MLP architecture is described as having "one fully connected hidden layer with 128 neurons" but no details are given on weight initialization, activation functions beyond ReLU, or whether batch normalization or other regularization techniques were used.
- **Required correction** Provide full architectural details, including initialization scheme, any regularization (e.g., dropout is mentioned but not its placement), and the exact training procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Model and Methods, Model training
- **Evidence pointer** Model and Methods, Model training
- **Issue** The learning rate is given as 1×10^-3, but no learning rate schedule, early stopping criteria, or selection of the final model checkpoint are described.
- **Required correction** Describe the model selection procedure, including how the best epoch was chosen and whether early stopping was used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Figure 3
- **Evidence pointer** Results section, Figure 3
- **Issue** The text describes the confusion matrix and normalized confusion matrix but does not report the actual numbers or the threshold used to convert probabilities to binary predictions.
- **Required correction** Report the confusion matrix values and specify the decision threshold (e.g., 0.5) or state that metrics are threshold-independent.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Conclusions
- **Evidence pointer** Conclusions
- **Issue** The conclusion mentions "future improvements may be achieved by incorporating structural context, surface accessibility, evolutionary conservation, or partner-aware information" but does not discuss potential limitations of the current approach beyond prediction of the minority class.
- **Required correction** Add a brief discussion of other limitations, such as potential bias in the DIBS database, generalizability to non-DIBS complexes, or sensitivity to sequence length.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Editorial
- **Affected element** Footnotes
- **Evidence pointer** Footnotes
- **Issue** The footnote states "There is a typo in the last name of the first author, should be 'Jones' instead of 'Jone'." This is an editorial issue that should be corrected in the manuscript itself, not left as a footnote.
- **Required correction** Correct the author name in the manuscript and remove the footnote.

## Risk / unsupported claims
- The claim that IDBSpred "provides a practical framework for studying IDP-mediated interfaces and identifying potential therapeutic hotspots" is unsupported without external validation or demonstration of utility beyond the training data.
- The claim that "these results demonstrate that protein language model embeddings plus machine learning algorithms can effectively capture sequence features associated with IDP recognition" is overstated given the lack of baseline comparisons and the absence of statistical testing on the composition analysis.
- The claim that the model "recovers the major binding regions in representative complexes" is not quantitatively supported, as no metrics are provided for the case studies.
- The generalizability of the method to proteins outside the DIBS database is not assessed and cannot be inferred from the provided evidence.