## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose a machine learning framework using quantitative molecular surface analysis (QMSA) descriptors derived from molecular electrostatic potential to predict PFAS bioactivity against five protein targets. They report high predictive performance (accuracy 0.950 ± 0.017, AUC-ROC 0.938 ± 0.012, F1-score 0.734 ± 0.024, MCC 0.684 ± 0.111) across five targets, outperforming previously reported models. SHAP analysis identifies estimated density, molecular volume, positive surface area, and nonpolar surface area as key descriptors. Molecular docking and molecular dynamics simulations are cited as evidence that these descriptors relate to non-covalent PFAS-protein interactions. The authors claim the framework enables high-throughput screening of emerging PFAS and informs water quality management.
- **Visible evidence base** Abstract text only; no dataset descriptions, model training details, validation procedures, descriptor definitions, docking protocols, or simulation parameters are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary information, dataset composition and size, model hyperparameters, cross-validation scheme, external validation results, docking and simulation details, and statistical comparison with prior models

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable application of QMSA descriptors to PFAS bioactivity prediction, with an interpretability component that is commendable. However, the evidence base available for review is limited to the abstract, which precludes verification of the central claims regarding model performance, descriptor importance, and mechanistic interpretation. The reported performance metrics are strong, but without details on dataset composition, validation strategy, and comparison methodology, the claim of outperforming prior models cannot be assessed. The mechanistic link between QMSA descriptors and docking/simulation results is asserted but not demonstrated in the provided material. The work addresses an important environmental health problem and may interest computational toxicologists and environmental regulators, but the case is not fully established from the abstract alone.
- **Who would be interested in the results, and why** Computational toxicologists and environmental chemists studying PFAS risk assessment would be the primary audience. Researchers developing interpretable machine learning models for molecular property prediction would also find the QMSA descriptor approach relevant. Water quality regulators and agencies prioritizing contaminants for monitoring and treatment could benefit from a high-throughput screening tool, provided the model generalizes beyond the training set. The mechanistic interpretability component may appeal to molecular biologists studying PFAS-protein interactions.
- **Major strengths** The problem addressed is timely and of high environmental relevance. The use of QMSA descriptors is a novel angle compared to traditional constitutional, topological, and geometric descriptors. The inclusion of SHAP-based interpretability and the attempt to link descriptors to mechanistic evidence via docking and dynamics is a strength. The reported performance metrics are strong, and the multi-target design across five proteins adds breadth.
- **Major Concerns** 
  - R1-M1: Dataset composition and size are not described, making the performance claims unverifiable.
  - R1-M2: The validation strategy is not specified, so the reported metrics cannot be interpreted for generalizability.
  - R1-M3: The claim of outperforming previously reported models lacks comparative details.
  - R1-M4: The mechanistic link between QMSA descriptors and docking/simulation results is asserted without supporting evidence in the abstract.
  - R1-M5: The scope of the screening claim for "emerging PFAS" is not supported by evidence of external validation or applicability domain analysis.
- **Minor Comments**
  - R1-m1: The abstract does not specify the number of PFAS compounds in the dataset.
  - R1-m2: The five targets are listed but their biological relevance to PFAS toxicity is not explained.
  - R1-m3: The term "extraordinary performance" is subjective and should be replaced with quantitative comparisons.
  - R1-m4: The abstract does not state whether the models were tested on a held-out test set or only via cross-validation.
  - R1-m5: The relationship between the five targets and aquatic environmental relevance is not clarified.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** 
  - Originality: The QMSA descriptor approach is a novel contribution relative to standard QSAR descriptors, but the abstract does not demonstrate how it differs fundamentally from prior surface-based descriptors.
  - Scientific importance: The problem of PFAS toxicity prediction is important, and a reliable, interpretable model would be valuable. However, the importance of the specific five targets is not established in the abstract.
  - Interdisciplinary readership: The work bridges computational chemistry, machine learning, and environmental toxicology, which could attract a broad readership if the methods are clearly presented.
  - Technical soundness: Cannot be assessed from the abstract. The performance metrics are reported with standard deviations, suggesting cross-validation, but no details are given.
  - Readability for nonspecialists: The abstract is generally clear, but terms like QMSA, SHAP, and MCC are used without definition, which may hinder nonspecialist comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising approach, but the lack of methodological detail and validation information prevents a supportive recommendation. A full manuscript with complete methods, dataset description, and validation results would be required to assess the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data transparency
- **Claim pointer** The models achieved outstanding performance with accuracy of 0.950 ± 0.017, AUC-ROC of 0.938 ± 0.012, F1-score of 0.734 ± 0.024, and MCC of 0.684 ± 0.111 for five targets.
- **Evidence pointer** Abstract, performance metrics section; location not provided
- **Concern** The abstract does not report the number of PFAS compounds, the number of active and inactive compounds per target, or the source of the bioactivity data. Without this information, the reported metrics cannot be interpreted in context, and the risk of class imbalance or data leakage cannot be assessed.
- **Why it matters** Performance metrics are only meaningful with knowledge of dataset size, class distribution, and data provenance. If the dataset is small or imbalanced, the reported accuracy and AUC-ROC may be misleading. Data leakage from similar PFAS structures across training and test sets could inflate performance.
- **Resolution test** Provide dataset size, class balance, data source, and a description of how compounds were split into training and test sets. Report performance on a held-out external test set if available.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** Five machine learning models achieved outstanding performance with best accuracy of 0.950 ± 0.017, AUC-ROC of 0.938 ± 0.012, F1-score of 0.734 ± 0.024, and MCC of 0.684 ± 0.111.
- **Evidence pointer** Abstract, performance metrics section; location not provided
- **Concern** The abstract does not specify the validation scheme, such as k-fold cross-validation, leave-one-out, or an external test set. The standard deviations suggest repeated cross-validation, but this is not stated. The possibility of overfitting or optimistic bias cannot be evaluated.
- **Why it matters** Without a clear validation strategy, the reported performance cannot be trusted as an estimate of generalizability. Overly optimistic metrics are common in QSAR studies when validation is not rigorous.
- **Resolution test** State the exact validation protocol, including the number of folds, repeats, and whether hyperparameter tuning was performed within or outside the cross-validation loop. If an external test set was used, describe its composition and how it was selected.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evidence
- **Claim pointer** The models outperform previously reported models.
- **Evidence pointer** Abstract, performance comparison statement; location not provided
- **Concern** The abstract claims superior performance over prior models but does not identify which models were compared, what datasets were used for comparison, or whether the comparison was performed under identical conditions. Without this context, the claim is unverifiable.
- **Why it matters** A claim of outperformance requires a fair, apples-to-apples comparison. Differences in datasets, endpoints, or evaluation metrics could explain performance differences rather than the QMSA descriptors themselves.
- **Resolution test** Specify the prior models, the datasets and endpoints used for comparison, and the statistical tests applied to establish significance. Provide a table comparing performance metrics across models on the same data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic evidence
- **Claim pointer** These descriptors were deeply involved in PFAS binding to target proteins via non-covalent interactions as evidenced by molecular docking and molecular dynamics simulations.
- **Evidence pointer** Abstract, mechanistic interpretation section; location not provided
- **Concern** The abstract states that docking and dynamics simulations provide evidence for the mechanistic role of the identified descriptors, but no results from these simulations are presented. The connection between descriptor importance and binding modes is asserted, not demonstrated.
- **Why it matters** The interpretability claim is a key selling point of the work. If the docking and simulation evidence is not clearly linked to the SHAP-identified descriptors, the mechanistic interpretation remains speculative.
- **Resolution test** Present docking scores, binding poses, and simulation trajectories that directly show how the identified descriptors correlate with binding affinity or interaction energy. Show that the descriptors are not merely statistically important but mechanistically relevant.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Scope of application
- **Claim pointer** This study provides a novel machine learning framework for the high-throughput and cost-effective screening of high-risk emerging PFAS in aquatic environments.
- **Evidence pointer** Abstract, application statement; location not provided
- **Concern** The abstract claims the framework is suitable for screening emerging PFAS, but no evidence is provided that the model generalizes to PFAS structures outside the training set. The applicability domain of the model is not discussed.
- **Why it matters** Emerging PFAS include novel structures that may fall outside the chemical space of the training data. Without an applicability domain analysis or external validation on diverse PFAS, the screening claim is unsupported.
- **Resolution test** Provide an applicability domain analysis, such as a Williams plot or descriptor space coverage assessment. Validate the model on an external set of PFAS not used in training, including structurally diverse or emerging compounds.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data reporting
- **Affected element** Dataset description
- **Evidence pointer** Abstract, dataset section; location not provided
- **Issue** The number of PFAS compounds in the dataset is not stated.
- **Required correction** Report the total number of compounds and the number per target.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Biological context
- **Affected element** Target selection
- **Evidence pointer** Abstract, target list; location not provided
- **Issue** The five protein targets are listed but their relevance to PFAS toxicity is not explained.
- **Required correction** Briefly justify the selection of these targets in the context of PFAS bioactivity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Performance description
- **Evidence pointer** Abstract, performance statement; location not provided
- **Issue** The term "extraordinary performance" is subjective and not quantifiable.
- **Required correction** Replace with a neutral phrase such as "high predictive performance" and rely on the reported metrics for support.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Validation reporting
- **Affected element** Test set description
- **Evidence pointer** Abstract, validation statement; location not provided
- **Issue** It is unclear whether the reported metrics are from cross-validation or a held-out test set.
- **Required correction** State explicitly whether the metrics are from cross-validation or an external test set.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Environmental relevance
- **Affected element** Application context
- **Evidence pointer** Abstract, application statement; location not provided
- **Issue** The link between the five targets and aquatic environmental risk is not clarified.
- **Required correction** Explain how bioactivity against these targets relates to ecological or human health risk in aquatic environments.

## Risk / unsupported claims
- The claim that QMSA-based models outperform previously reported models is unsupported without comparative details.
- The claim that docking and dynamics simulations evidence the mechanistic role of the identified descriptors is unsupported without presenting simulation results.
- The claim that the framework enables high-throughput screening of emerging PFAS is unsupported without applicability domain analysis or external validation.
- The reported performance metrics are unverifiable without dataset composition and validation details.
- The interpretability claim, while plausible, is not demonstrated in the abstract.