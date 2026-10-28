## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific soundness, methodological validity, claims versus evidence, and suitability for a general interdisciplinary journal
- **Shared manuscript claim summary** The authors present a computational workflow combining docking, ligand-receptor contact fingerprints (LRCFs), and machine learning (ML) with data augmentation via multiple docked poses to identify novel STAT3 inhibitors. They report two pharmacophore models, virtual screening of the NCI database, and in vitro validation of three hits, one of which (compound 342) is claimed to be a direct STAT3 inhibitor with submicromolar cytotoxicity and downstream gene suppression.
- **Visible evidence base** Abstract, full methods, results, figures referenced in text, tables referenced in text, supplementary material descriptions
- **Missing materials affecting confidence** Supplementary figures and tables (ESI Fig. S1-S3, Tables S1-S5), raw data for docking scores, ML performance metrics beyond those summarized, full qPCR data, compound structures for hits 317-342, and details of the genetic algorithm implementation

## Reviewer

- **Overall assessment** The manuscript presents an interesting and potentially valuable computational approach for STAT3 inhibitor discovery, combining docking-based data augmentation with ML and pharmacophore modeling. The workflow is logical and the integration of multiple orthogonal methods is commendable. However, several technical concerns limit the strength of the conclusions. The validation of the key claim that compound 342 is a direct STAT3 inhibitor is incomplete, as only cytotoxicity and downstream gene expression are shown, without direct binding or functional STAT3 assays. The ML methodology, while reasonable, lacks sufficient detail on hyperparameter tuning, class imbalance handling, and the impact of data augmentation on model generalizability. The pharmacophore models are derived from a single docked pose of one compound, which raises questions about their representativeness. The comparison with crystallographic pharmacophores is brief and does not fully address why the ML-derived models are superior. Overall, the work is promising but requires additional experimental and computational validation to fully support the claims.

- **Who would be interested in the results, and why** Researchers in computational drug discovery, medicinal chemistry, and cancer biology would find this work relevant. The methodological approach of using docked poses for data augmentation in ML-QSAR modeling is of interest to those developing similar workflows. The identification of a new STAT3 inhibitor scaffold could be of interest to medicinal chemists seeking novel leads. The work also speaks to the broader community interested in the application of explainable AI (SHAP) to drug design.

- **Major strengths** The study integrates multiple computational techniques in a coherent pipeline, from docking to ML to pharmacophore generation. The use of data augmentation via multiple docked poses is a creative approach to address limited training data. The inclusion of SHAP values for feature interpretation is a modern and useful addition. The in vitro validation, including the use of a panel of cell lines and qPCR for downstream gene expression, provides some experimental support. The identification of a compound with a novel chemotype is a positive outcome.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The manuscript claims that compound 342 is a "purely direct STAT3 inhibitor" based on its lack of DHFR activity and its effect on downstream gene expression.
- **Evidence pointer** Section 3.7, Table 8, Fig. 10
- **Concern** The claim that 342 is a direct STAT3 inhibitor is not supported by direct experimental evidence. The authors show that 342 is not a DHFR inhibitor and that it reduces expression of c-Myc and Bcl-xl, but these are indirect readouts. Direct binding to the STAT3 SH2 domain, inhibition of STAT3 phosphorylation, or STAT3-dependent transcriptional activity assays are not reported. The conclusion of direct inhibition is therefore an overreach based on the presented data.
- **Why it matters** The central claim of the paper is the discovery of a new direct STAT3 inhibitor. Without direct evidence of binding or functional inhibition of STAT3, the conclusion is not established. This is a critical issue that affects the validity of the entire study's main finding.
- **Resolution test** The authors should provide direct evidence of STAT3 inhibition, such as a STAT3-dependent reporter assay, STAT3 phosphorylation inhibition in cells, or a biophysical binding assay (e.g., SPR, ITC) to the SH2 domain. Alternatively, the claim should be revised to state that 342 is a potential STAT3 inhibitor based on indirect evidence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors claim that the ML models are valid and that the data augmentation strategy improves model performance.
- **Evidence pointer** Section 2.3, Section 3.3, Fig. 4, Tables 3-4
- **Concern** The ML methodology lacks critical details. The manuscript does not describe hyperparameter tuning for the ML algorithms, the handling of class imbalance (116 actives vs 106 inactives vs 92 intermediates), or the potential for data leakage due to the augmentation of multiple poses from the same compound. The performance metrics are reported as accuracy and Cohen's kappa, but the distribution of these metrics across cross-validation folds is not shown. The comparison between models with and without data augmentation is not explicitly made, so the claimed benefit of augmentation is not directly demonstrated.
- **Why it matters** The validity of the ML models is central to the identification of the hits. Without proper methodological details and a clear demonstration of the augmentation benefit, the reliability of the screening results is questionable.
- **Resolution test** The authors should provide a detailed description of the ML pipeline, including hyperparameter optimization, cross-validation strategy, and class imbalance handling. They should also present a direct comparison of model performance with and without data augmentation to support their claim.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Pharmacophore validity
- **Claim pointer** The authors claim that the two pharmacophore models (Hypo-1 and Hypo-2) are valid and can be used for virtual screening.
- **Evidence pointer** Section 3.4, Fig. 7-8
- **Concern** The pharmacophore models are generated from a single docked pose of one compound (115). This is a very limited basis for generating a pharmacophore, as it may not capture the full range of binding interactions possible for diverse ligands. The validation of the pharmacophores is based on ROC analysis against the training set, which is not a true external validation. The comparison with crystallographic pharmacophores is brief and does not provide a clear statistical comparison of their screening performance.
- **Why it matters** The pharmacophores are used to screen the NCI database, and their validity directly impacts the quality of the identified hits. A pharmacophore based on a single pose may be biased and not generalizable.
- **Resolution test** The authors should validate the pharmacophores using an external test set of known STAT3 inhibitors and non-inhibitors. They should also consider generating pharmacophores from multiple docked poses of diverse active compounds to ensure representativeness.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data availability and reproducibility
- **Claim pointer** The authors claim that the workflow is reproducible and the results are robust.
- **Evidence pointer** Section 2, Supplementary Material
- **Concern** The manuscript relies heavily on supplementary material for critical details, including compound structures, docking parameters, and ML implementation. However, the supplementary material is not provided for review. This makes it impossible to assess the reproducibility of the work. Additionally, the in-house Fortran code for LRCF generation is not described in sufficient detail to be replicated.
- **Why it matters** Reproducibility is a cornerstone of scientific research. Without access to the detailed methods and data, the work cannot be independently verified or built upon.
- **Resolution test** The authors should provide the supplementary material for review and ensure that all methods are described in sufficient detail for replication. The LRCF generation code should be made available or described in a way that allows independent implementation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "three hits of novel chemotypes" were identified, but the text later indicates that two of these (319 and 333) are known DHFR inhibitors and are excluded from further evaluation. This is confusing and should be clarified.
- **Required correction** Revise the abstract to clearly state that three hits were identified, but only one (342) was pursued as a potential direct STAT3 inhibitor.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** ML performance metrics
- **Evidence pointer** Tables 3-4
- **Issue** The performance metrics are reported as single values without confidence intervals or standard deviations. This makes it difficult to assess the variability and robustness of the models.
- **Required correction** Report performance metrics with confidence intervals or standard deviations across cross-validation folds.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Fig. 4
- **Evidence pointer** Fig. 4
- **Issue** The figure showing Cohen's kappa values for different ML algorithms and consensus levels is difficult to interpret. The axes are not clearly labeled, and the legend is not descriptive enough.
- **Required correction** Improve the figure clarity by adding clear axis labels, a descriptive legend, and possibly error bars.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 2.2.4
- **Evidence pointer** Section 2.2.4
- **Issue** The term "Shapley additive explanations" is used, but the abbreviation "SHAP" is introduced later. For consistency, the abbreviation should be defined at first use.
- **Required correction** Define SHAP at first use in the text.

- **Technical failings that need to be addressed before the case is established** The lack of direct experimental evidence for STAT3 inhibition by compound 342 is a critical failing. The ML methodology lacks sufficient detail and validation. The pharmacophore models are based on a single pose and lack external validation. The supplementary material, which is essential for reproducibility, is not available for review.

- **Assessment against Nature-style criteria** 
  - **Originality** The combination of docking-based data augmentation with ML and pharmacophore modeling is somewhat novel, but similar approaches have been reported. The use of SHAP for feature selection in this context adds a modern element.
  - **Scientific importance** The identification of new STAT3 inhibitors is of clinical relevance, but the impact is limited by the lack of direct validation. The methodological findings are of moderate interest to the computational chemistry community.
  - **Interdisciplinary readership** The work bridges computational chemistry, ML, and cancer biology, which could appeal to a broad audience. However, the technical depth may limit accessibility.
  - **Technical soundness** The computational workflow is logical, but the ML methodology lacks rigor and the experimental validation is incomplete. The pharmacophore generation is based on a limited dataset.
  - **Readability for nonspecialists** The manuscript is generally well-written, but the methods section is dense and may be challenging for readers without a strong computational background. The figures and tables are not always self-explanatory.

- **Recommendation posture** Currently not established from the provided evidence. The work has potential, but the central claim of a direct STAT3 inhibitor is not supported by the experimental data. The ML methodology requires more rigor and validation. The authors should address the major concerns, particularly the direct evidence of STAT3 inhibition, before the case can be made.