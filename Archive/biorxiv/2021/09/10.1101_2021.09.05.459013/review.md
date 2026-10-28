## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, acknowledgements) as provided.
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality based solely on the supplied text. No external data, figures, or supplementary materials were accessed.
- **Shared manuscript claim summary** The authors present ScanNet, an end-to-end, interpretable geometric deep learning model for structure-based prediction of protein-protein binding sites and B-cell epitopes. They claim state-of-the-art performance, interpretability of learned filters, robustness to conformational changes, and utility for epitope prediction on the SARS-CoV-2 spike protein.
- **Visible evidence base** Abstract, introduction, results sections A-D, discussion, materials and methods sections A-G, acknowledgements, and footnotes. References to figures (Fig. 1-5), tables (Table I), and supplementary items (Fig. S1-S22, Table S1-S6) are mentioned but not provided.
- **Missing materials affecting confidence** All figures, tables, supplementary figures and tables, and the full materials and methods details for baseline comparisons and data set construction are not available. This significantly limits the ability to verify quantitative claims, architectural details, and benchmark fairness.

## Reviewer
- **Overall assessment** This manuscript introduces a novel geometric deep learning architecture for protein binding site prediction, with a strong emphasis on interpretability. The core idea of learning spatio-chemical patterns directly from atomic coordinates is timely and relevant, especially given the recent advances in structure prediction. The authors demonstrate competitive performance against established baselines and provide insightful analyses of learned filters. However, the absence of key figures, tables, and supplementary data prevents a full evaluation of the technical soundness and the strength of the empirical claims. The manuscript is well-written and the methodological description is detailed, but several concerns regarding baseline fairness, generalizability, and the interpretability claims need to be addressed.
- **Who would be interested in the results, and why** Computational biologists, structural bioinformaticians, and researchers in protein function prediction would find this work of high interest. The model's interpretability and its ability to generalize to unseen folds are particularly appealing for understanding the physicochemical determinants of protein interactions. The application to SARS-CoV-2 epitope prediction also broadens its appeal to the immunology and virology communities.
- **Major strengths** 1. Novel architecture that learns directly from raw atomic coordinates, avoiding handcrafted features. 2. Strong emphasis on interpretability, with visualization of learned spatio-chemical patterns. 3. Comprehensive benchmarking against multiple baselines, including structural homology and feature-based ML. 4. Demonstration of robustness to conformational changes and label noise. 5. Practical utility shown through epitope prediction on a clinically relevant target.
- **Major Concerns** 1. The comparison with Masif-site is potentially unfair due to differences in training data and the lack of retraining. 2. The claim of interpretability is supported by qualitative visualizations, but a more quantitative or systematic evaluation is needed. 3. The generalizability of the model to other types of binding sites (e.g., small molecules, nucleic acids) is not demonstrated. 4. The performance on the BCE dataset is modest, and the practical utility for epitope prediction needs further validation. 5. The manuscript does not discuss potential limitations of the approach, such as sensitivity to input structure quality or computational cost for very large proteins.
- **Minor Comments** 1. The abstract could be more concise and highlight the key quantitative results. 2. The introduction could better contextualize the work within the broader landscape of deep learning for proteins. 3. The discussion of the "O-ring" filter is interesting but could be expanded with more mechanistic detail. 4. The availability statement mentions a webserver, but the code and data availability are not clearly stated. 5. Some terminology, such as "spatio-chemical arrangement," could be defined more explicitly for a general audience.
- **Technical failings that need to be addressed before the case is established** 1. The Masif-site comparison is not a fair head-to-head evaluation, as Masif-site was not retrained on the same data. This weakens the claim of "outperforming" this baseline. 2. The interpretability analysis relies on visual inspection of filters, which is subjective. A more rigorous approach, such as quantifying filter specificity or performing mutagenesis predictions, would strengthen the claim. 3. The manuscript does not provide error bars or statistical significance tests for the performance differences, making it difficult to assess the robustness of the results.
- **Assessment against Nature-style criteria** *Originality*: High. The architecture is a novel contribution to geometric deep learning for proteins. *Scientific importance*: High. Accurate and interpretable binding site prediction is a fundamental problem with broad applications. *Interdisciplinary readership*: Moderate. The work will appeal to computational and structural biologists, but the technical depth may limit accessibility to a wider audience. *Technical soundness*: Moderate. The methodology is sound in principle, but the lack of full data and the unfair baseline comparison raise concerns. *Readability for nonspecialists*: Good. The manuscript is generally well-written, but some technical sections are dense.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the results are potentially significant, but the current evidence base is insufficient to fully establish the claims. The authors must address the baseline fairness issue, provide a more rigorous interpretability analysis, and make the full data and code available for verification.

### Major Concerns
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "ScanNet outperforms baseline methods based on ML, structural homology and surface-based geometric deep learning."
- **Evidence pointer** Results section B, Table I, Sup. Fig. S17
- **Concern** The comparison with Masif-site is not a fair evaluation. Masif-site was not retrained on the same training data, and its training set was smaller. This introduces a significant confound, as the performance difference could be attributed to data quantity rather than architectural superiority. The authors acknowledge this limitation but still use the comparison to support their claim of outperformance.
- **Why it matters** A fair comparison is essential to validate the claim of state-of-the-art performance. Without retraining Masif-site on the same data, the results are not directly comparable, and the conclusion is weakened.
- **Resolution test** The authors should retrain Masif-site on the same training set (or a representative subset) and report the performance. Alternatively, they could clearly state that the comparison is indicative only and not a head-to-head benchmark.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability
- **Claim pointer** "Through appropriate parameterization and regularization, the filters learnt by ScanNet can be readily visualized and interpreted."
- **Evidence pointer** Results section C, Fig. 3, Fig. 4
- **Concern** The interpretability claim is supported primarily by qualitative visualizations of a few selected filters. While these are informative, the analysis is subjective and does not systematically demonstrate that the filters are consistently interpretable across the entire filter set or that they correspond to known physicochemical motifs in a statistically significant manner.
- **Why it matters** Interpretability is a key selling point of the model. A more rigorous evaluation is needed to substantiate this claim and to convince readers that the interpretability is not cherry-picked.
- **Resolution test** The authors should provide a quantitative analysis, such as comparing the spatial distribution of filter activations to known motif annotations, or performing a systematic clustering of filters based on their learned patterns and correlating these with functional categories.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "ScanNet is a versatile, powerful, and interpretable model suitable for functional site prediction tasks."
- **Evidence pointer** Abstract, Discussion
- **Concern** The model is only demonstrated on two related tasks (PPBS and BCE). The claim of versatility is not fully supported, as the model's performance on other types of binding sites (e.g., small molecules, nucleic acids) or on other functional annotation tasks is not explored.
- **Why it matters** The claim of versatility is broad and implies the model can be easily adapted to other problems. Without evidence, this claim is speculative.
- **Resolution test** The authors should either provide preliminary results on at least one additional task (e.g., DNA/RNA binding site prediction) or temper the claim of versatility to reflect the demonstrated scope.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** "ScanNet achieved an AUCPR of 0.694, accuracy of 87.7% and 73.5% precision at 50% recall, the best performance by a substantial margin."
- **Evidence pointer** Results section B, Table I
- **Concern** The manuscript does not report any measures of variance (e.g., standard deviation, confidence intervals) or statistical significance tests for the performance metrics. This makes it difficult to assess whether the observed differences are meaningful or within the noise.
- **Why it matters** For a claim of "best performance by a substantial margin," it is crucial to demonstrate that the difference is statistically significant and not due to random variation.
- **Resolution test** The authors should report the mean and standard deviation of performance metrics across multiple runs (e.g., different random seeds) and perform appropriate statistical tests (e.g., paired t-test or Wilcoxon signed-rank test) to compare against baselines.

### Minor Comments
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and could be more accessible to a broader audience. The term "spatio-chemical arrangement" is not defined.
- **Required correction** Briefly define "spatio-chemical arrangement" in the abstract or introduction, and consider simplifying the language to improve readability.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods, Section A
- **Evidence pointer** Materials and Methods, Section A
- **Issue** The description of the network architecture is detailed, but some hyperparameters (e.g., number of filters per layer, learning rate schedule) are not explicitly stated.
- **Required correction** Provide a complete list of hyperparameters in the main text or a supplementary table to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results, Section D
- **Evidence pointer** Results, Section D
- **Issue** The comparison with AlphaFold-multimer is interesting but is presented briefly. The criteria for selecting the six representative antibodies for the RBD epitope analysis are not fully described.
- **Required correction** Expand the description of the AlphaFold-multimer comparison, including the selection criteria for antibodies and a more detailed discussion of the results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Availability
- **Evidence pointer** Availability section
- **Issue** The availability statement mentions a webserver but does not clearly state whether the source code and training data will be made publicly available.
- **Required correction** Clearly state the availability of source code, training data, and any trained models, in line with best practices for reproducibility.

## Risk / unsupported claims
- The claim of "outperforming" Masif-site is not fully supported due to the unfair comparison setup.
- The claim of "interpretability" is not rigorously validated and relies on qualitative visualizations.
- The claim of "versatility" is not demonstrated beyond the two tasks presented.
- The claim of "robustness to conformational changes" is based on a specific dataset and may not generalize to all cases.
- The claim of "predicting a previously uncharacterized epitope" on the SARS-CoV-2 spike protein is not verifiable without the specific details and validation data.