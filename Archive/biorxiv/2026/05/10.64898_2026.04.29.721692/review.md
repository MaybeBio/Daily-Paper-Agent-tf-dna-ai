## Review setup
- **Input scope** Full manuscript text (abstract, introduction, related works, method, experiments, conclusion, impact statement, code availability, acknowledgements)
- **Assessment boundary** Scientific claims, methodological soundness, experimental design, evidence quality, and reporting completeness as presented in the provided text. No supplementary materials, figures, or tables were available for inspection.
- **Shared manuscript claim summary** The authors introduce DPLM, a protein language model that aligns sequence embeddings with molecular dynamics trajectory embeddings via contrastive learning. They claim that this dynamics-aware pretraining improves representation quality over static sequence- and structure-based PLMs, as evidenced by stronger correlations with RMSF, better clustering on CATH and enzyme datasets, superior zero-shot mutation effect prediction, and top-tier performance on stability and disorder prediction tasks.
- **Visible evidence base** Text descriptions of results in Sections 4.1–4.3, including references to Figures 2–4 and Tables 1–4. No actual figures, tables, or numerical data were provided in the supplied material.
- **Missing materials affecting confidence** All figures and tables; dataset construction details beyond summary statistics; hyperparameters, training details, and computational resources; baseline implementation specifics; statistical significance tests; ablation studies; code repository contents.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important problem: incorporating protein dynamics into language model representations. The core idea of aligning sequence embeddings with MD trajectory embeddings via contrastive learning is conceptually appealing and methodologically distinct from prior work. However, the provided text does not contain sufficient quantitative evidence to evaluate the strength of the claims. The results sections reference figures and tables that are not included, making it impossible to verify the reported improvements. Several methodological details are also underspecified, particularly regarding the MD encoder preprocessing, the contrastive loss formulation, and the fairness of baseline comparisons. The manuscript has potential, but the case is not established from the supplied material alone.
- **Who would be interested in the results, and why** Computational protein scientists, machine learning researchers working on protein representation learning, and structural biologists interested in dynamics-aware embeddings. The approach could be relevant to anyone developing or using PLMs for mutation effect prediction, stability prediction, or disorder prediction, as these tasks are central to protein engineering and drug discovery.
- **Major strengths** 1) The problem is well-motivated: static PLMs ignore conformational dynamics, which are central to protein function. 2) The use of a pretrained video model (ViViT) to encode MD trajectories is a creative and novel transfer of ideas from computer vision. 3) The contrastive alignment approach is unsupervised, avoiding the need for hand-engineered dynamics labels. 4) The downstream task selection (mutation effects, stability, disorder) is relevant and practically important. 5) The authors acknowledge limitations and discuss future work.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative evidence), R1-M2 (loss function not defined), R1-M3 (baseline comparison fairness), R1-M4 (MD encoder preprocessing details), R1-M5 (statistical significance).
- **Assessment against Nature-style criteria** Originality: The idea of aligning sequence and MD trajectory embeddings via contrastive learning is novel and distinct from prior dynamics-aware approaches. Scientific importance: Protein dynamics are fundamental to function, and a dynamics-aware PLM could have broad impact. However, the importance is not yet demonstrated with the evidence provided. Interdisciplinary readership: The work bridges machine learning, biophysics, and protein science, which could appeal to a broad audience. Technical soundness: The approach is plausible, but key technical details are missing, and the evidence base is incomplete. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume familiarity with PLM and MD terminology.
- **Recommendation posture** Currently not established from the provided evidence. The core idea is promising, but the manuscript requires substantial additional information and verification before the claims can be assessed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that DPLM outperforms ESM2 and other baselines across multiple tasks, including zero-shot mutation effect prediction, stability prediction, and disorder identification.
- **Evidence pointer** Sections 4.1–4.3; Figures 2–4; Tables 1–4
- **Concern** The results sections reference figures and tables that are not included in the supplied material. No numerical values, error bars, or statistical comparisons are provided in the text. It is therefore impossible to assess the magnitude of the reported improvements, whether they are statistically significant, or whether they are practically meaningful.
- **Why it matters** The central claims of the manuscript rest entirely on these quantitative results. Without the actual data, the claims cannot be verified or reproduced.
- **Resolution test** Provide the figures and tables with full numerical data, including error bars, sample sizes, and statistical significance tests (e.g., p-values or confidence intervals) for all reported comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The manuscript states that a contrastive loss based on NT-Xent is used, modified for cross-view contrast as introduced in X-CLIP.
- **Evidence pointer** Section 3.4
- **Concern** The loss function is referenced but not explicitly written out. The text says "the loss is defined as:" but the equation is missing. It is unclear how the cross-view contrast is implemented, how the temperature parameter is set, and how the within-modality contrast terms are weighted relative to the cross-modal term.
- **Why it matters** The training objective is the core of the method. Without a precise definition, the method cannot be reproduced or compared to alternative formulations.
- **Resolution test** Provide the complete loss function, including all terms, weighting coefficients, and hyperparameter values.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Fairness of comparison
- **Claim pointer** The manuscript claims that DPLM outperforms ESM2-based representations in zero-shot mutation effect prediction and achieves top-tier performance on stability and disorder prediction.
- **Evidence pointer** Sections 4.2–4.3; Tables 1–4
- **Concern** The baseline comparisons are not described in sufficient detail. For mutation effect prediction, the comparison is made at the representation level using a residue-level alignment method, but it is unclear whether the same evaluation protocol was applied to all models. For stability and disorder prediction, the manuscript states that DPLM is compared to previously reported results, but it is not clear whether the training data, evaluation protocol, and model capacity are matched across methods.
- **Why it matters** Unfair or inconsistent comparisons can lead to misleading conclusions about the relative performance of DPLM.
- **Resolution test** Describe the exact evaluation protocol for each baseline, including any preprocessing, hyperparameter selection, and whether the same training and test splits were used. For previously reported results, specify the source and confirm that the comparison is apples-to-apples.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity
- **Claim pointer** The manuscript states that MD trajectories are converted into contact map images and processed by a pretrained ViViT model.
- **Evidence pointer** Section 3.2
- **Concern** The preprocessing pipeline is underspecified. It is unclear how the 100 ns trajectories are divided into 32-frame segments, how the contact maps are computed (e.g., which atoms, what distance cutoff), how the 224×224 resolution is achieved for proteins of varying length, and how the zero-padding affects the model. The choice of ViViT-b-16×2 pretrained on Kinetics-400 is also not justified.
- **Why it matters** The MD encoder is a critical component of the method. Without a clear description of the preprocessing, the results cannot be reproduced, and the suitability of the chosen architecture is unclear.
- **Resolution test** Provide a detailed description of the contact map computation, trajectory segmentation, padding strategy, and any normalization steps. Justify the choice of ViViT architecture and pretraining dataset.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports correlations and performance metrics for DPLM and baselines across multiple tasks.
- **Evidence pointer** Sections 4.1–4.3; Figures 2–4; Tables 1–4
- **Concern** No statistical significance tests are reported for any of the comparisons. It is unclear whether the observed differences between DPLM and baselines are within the range of random variation, particularly for datasets with small sample sizes (e.g., 9 DMS datasets, 669 stability mutations).
- **Why it matters** Without significance testing, the reported improvements could be due to chance, especially given the number of comparisons made.
- **Resolution test** Report confidence intervals or p-values for all key comparisons, and specify the number of independent runs or bootstrap resamples used.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2
- **Evidence pointer** "MD trajectories (saved in .xtc files) were read as md.Trajectory objects using the MDTraj Python package."
- **Issue** The text says "md.Trajectory" but the correct MDTraj class is "md.Trajectory" (lowercase "md" is the module alias). This is a minor typographical issue.
- **Required correction** Clarify the import statement or use the full class name.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.1
- **Evidence pointer** "We used data from 1,938 proteins (three replicates each)."
- **Issue** The total number of trajectories is 1,938 × 3 = 5,814, but the training set is stated as 1,472 proteins (4,416 replicates). The discrepancy between 1,938 and 1,472 is not explained.
- **Required correction** Clarify how the 1,938 proteins were split into training, validation, and test sets, and why the training set contains fewer proteins than the total.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.2
- **Evidence pointer** "We focused on nine DMS datasets that probe functional properties closely tied to protein dynamics"
- **Issue** The criteria for selecting these nine datasets are not described. It is unclear whether the selection was made before or after seeing the results, which could introduce selection bias.
- **Required correction** Describe the selection criteria and justify why these nine datasets were chosen.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.3
- **Evidence pointer** "The training and evaluation datasets were collected from (Xu et al., 2024)."
- **Issue** The reference to Xu et al. (2024) is not listed in the provided text. The reader cannot verify the dataset details.
- **Required correction** Provide the full citation and describe the dataset construction in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.3
- **Evidence pointer** "Methods that outperform DPLM either rely on explicit structural information... or employ computationally expensive ensemble strategies."
- **Issue** This statement is made without quantitative support. It is unclear which methods outperform DPLM and by what margin.
- **Required correction** Provide the specific performance numbers for the top-performing methods and DPLM to support this claim.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.4
- **Evidence pointer** "The training objective encourages embeddings from the same protein... to be closely aligned, while simultaneously pushing apart embeddings from different proteins."
- **Issue** The batch size N and temperature τ are not specified. These hyperparameters can significantly affect contrastive learning performance.
- **Required correction** Report the batch size and temperature used during training.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.1
- **Evidence pointer** "We extracted the DPLM residue embeddings for proteins in the Atlas test set, and reduced the embeddings to scalars by computing their L2 norms."
- **Issue** The use of L2 norm as a scalar summary of residue embeddings is a strong assumption. It is unclear whether this choice is justified or whether other reduction methods (e.g., PCA, mean pooling) were explored.
- **Required correction** Justify the choice of L2 norm or show that results are robust to the choice of reduction method.

## Risk / unsupported claims
- The claim that DPLM "outperforms ESM2-based representations in zero-shot mutation effect prediction" is unsupported because the actual data in Table 1 is not provided.
- The claim that DPLM "achieves top-tier performance" on stability and disorder prediction is unsupported because the comparison data in Tables 2–4 is not provided.
- The claim that DPLM embeddings "capture meaningful dynamic properties" is only weakly supported by the text description of Figure 2A; no correlation coefficients are given.
- The claim that DPLM is "approximately 10–10^4 times faster" than competing methods is unsupported because no runtime measurements are provided.
- The claim that the contrastive loss is based on a "modification of the NT-Xent loss" is unverifiable because the equation is missing.
- The claim that the MD encoder is "frozen during pretraining" is stated but not justified; the impact of this choice is not explored.
- The claim that the method "mitigates catastrophic forgetting" is not tested or compared to alternative approaches.