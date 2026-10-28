## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, claims, and evidence presented in the manuscript
- **Shared manuscript claim summary** The authors present NetProphet3 (NP3), a supervised machine learning framework that combines evidence scores from multiple network inference methods using XGBoost, trained on transcription factor binding data. They claim NP3 outperforms existing methods including NetProphet 2.0 across three independent evaluation metrics, and introduce a novel "integration mode" that forges consensus networks by intentionally overfitting to binding labels.
- **Visible evidence base** Full text including Methods, Results, Figures 1-5 (referenced), Supplementary Figures S1-S11 (referenced), and Supplementary Files S1-S9 (referenced)
- **Missing materials affecting confidence** Actual figure images, supplementary figures, and supplementary files were not provided. Code and data availability are stated but not independently verified. Detailed hyperparameter settings and computational runtime comparisons are not fully described.

## Reviewer
- **Overall assessment** This manuscript presents a useful and potentially impactful framework for transcription factor network inference. The core idea of using supervised learning to combine heterogeneous evidence scores is sound and addresses a real limitation of previous approaches. The integration mode concept is genuinely novel and well-motivated. However, several technical aspects require clarification and additional validation before the claims are fully established. The evaluation metrics, while creative, have limitations that are not fully acknowledged. The comparison with existing methods, particularly regarding computational cost and practical usability, is incomplete. The manuscript is generally well-written and accessible, though some methodological details are underspecified.
- **Who would be interested in the results, and why** Researchers in systems biology, gene regulatory network inference, and computational genomics would be the primary audience. The framework's ability to integrate multi-omics data and its demonstrated performance on yeast data would interest those working on less-characterized organisms where binding data are scarce. The integration mode concept could also appeal to machine learning researchers interested in novel applications of supervised learning beyond generalization.
- **Major strengths** 1) The supervised learning approach to combining evidence scores is a principled improvement over manually tuned combinations. 2) The integration mode is a genuinely novel concept that reframes overfitting as a feature for data fusion. 3) The use of three independent evaluation metrics provides a more robust assessment than single-metric comparisons. 4) The cross-dataset validation (TFKO to ZEV and vice versa) strengthens the generalizability claims. 5) The framework is designed to be extensible to other organisms and data types.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - **Originality** The integration mode concept is original and distinguishes this work from prior network inference methods. The supervised combination of evidence scores, while building on prior work, is applied in a more systematic way than previous attempts.
  - **Scientific importance** The problem of accurate TF network inference is fundamental to understanding gene regulation. The framework's potential to work with limited binding data could extend its utility to less-studied organisms, which is scientifically valuable.
  - **Interdisciplinary readership** The work bridges machine learning and molecular biology. The methods section may be challenging for purely biological readers, but the results and discussion are accessible. The potential applications in multi-omics integration could attract a broader readership.
  - **Technical soundness** The core methodology is technically sound, but several concerns (detailed below) need to be addressed. The evaluation metrics are creative but have limitations that require acknowledgment and additional validation.
  - **Readability for nonspecialists** The introduction and discussion are well-written and accessible. The methods section assumes familiarity with network inference and machine learning concepts, which is appropriate for the target audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core ideas are promising and the framework appears functional, but the current evidence does not fully establish all claims, particularly regarding the superiority of NP3 over existing methods and the robustness of the integration mode.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "By these metrics, NetProphet3 is more accurate than other commonly used packages, including NetProphet 2.0, when gene expression data from direct TF perturbations are available."
- **Evidence pointer** Section 3.1, Figure 1B-E, Supplementary Figures S1, S2, S7
- **Concern** The claim of superiority over existing methods is based on three evaluation metrics, but the manuscript does not provide statistical significance testing for the observed differences. The figures show performance curves, but without confidence intervals or statistical tests, it is unclear whether the improvements are meaningful or within noise. Additionally, the comparison with Genie3 and Inferelator3 on the GO metric shows similar performance (stated as "about the same"), which weakens the overall claim of superiority. The authors should provide statistical analysis (e.g., bootstrapping, permutation tests) to support the claim that NP3 is significantly more accurate.
- **Why it matters** The central claim of the manuscript is that NP3 outperforms existing methods. Without statistical support, this claim is not rigorously established, and readers cannot assess the reliability of the improvement.
- **Resolution test** Provide confidence intervals or statistical tests (e.g., paired bootstrap across TF folds) for the differences in performance metrics between NP3 and each comparator method. Report p-values or effect sizes for the key comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We also developed three independent, genome-scale evaluation metrics."
- **Evidence pointer** Sections 2.5-2.7, Figure 1B-E
- **Concern** The three evaluation metrics are described as "independent," but they are not truly independent. The binding metric and GO-directness metric both rely on binding data, and the GO metric and PPI metric both depend on the quality of the underlying functional annotations. More critically, the GO metric has a known limitation: it measures enrichment of functional terms but does not directly assess whether predicted edges are correct. The authors acknowledge this indirectly but do not address the potential circularity in using binding data both for training labels and for one of the evaluation metrics. The manuscript should clarify the degree of independence and discuss the limitations of each metric more explicitly.
- **Why it matters** The claim of three independent metrics is used to argue for robust evaluation. If the metrics are correlated or share biases, the evaluation may overstate NP3's performance.
- **Resolution test** Provide a correlation analysis between the three metrics across methods and thresholds. Discuss explicitly how each metric's limitations could affect the conclusions and whether any metric could be biased in favor of NP3.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The performance of NP3 continued to improve as the number of training TFs increased, up to 90, after which it did not change."
- **Evidence pointer** Section 3.3, Figure 2D
- **Concern** The analysis of performance versus number of training TFs is presented as a key result for practical recommendations, but the figure is not provided in the manuscript text. The text states performance "did not change" after 90 TFs, but it is unclear whether this is a plateau or a decline. Additionally, the recommendation to use the yeast-trained model for organisms with fewer than 40 TFs with binding data is based on this analysis, but the cross-species transferability is not directly tested. The manuscript should show the actual data and discuss the variance across random TF selections.
- **Why it matters** The practical recommendation for users in less-studied organisms depends on this analysis. If the plateau is not robust or the variance is high, the recommendation may be unreliable.
- **Resolution test** Provide the full learning curve data with error bars showing variance across random TF subsets. Discuss whether the plateau at 90 TFs is consistent across both datasets and whether the recommendation for fewer than 40 TFs is conservative enough.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Substantial improvements were achieved by overfitting models to binding data for a specific TF."
- **Evidence pointer** Section 3.7, Figure 5A-C, Supplementary Figure S11
- **Concern** The integration mode relies on intentional overfitting, which is a novel and interesting concept. However, the manuscript does not adequately address the risk of overfitting to noise in the binding data. The control experiment with randomized features (Supplementary Figure S11) is mentioned but not described in sufficient detail. It is unclear how much the improvement depends on the specific binding dataset used, and whether the overfitting would generalize to noisier or sparser binding data. The manuscript should provide a more thorough analysis of the overfitting behavior, including how performance varies with the quality and quantity of binding data.
- **Why it matters** The integration mode is presented as a major contribution. If the overfitting approach is not robust to realistic binding data quality, its practical utility is limited.
- **Resolution test** Provide a detailed description of the randomization control and its results. Test the integration mode with varying amounts of binding data (e.g., downsampled binding labels) to show how performance degrades. Discuss the potential for overfitting to systematic biases in binding data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section 2.1
- **Evidence pointer** Section 2.1, location not provided
- **Issue** The description of the XGBoost hyperparameter tuning is vague. The text states hyperparameters were tuned using 5-fold CV within the training fold, but the specific hyperparameter search space and the final chosen values are not reported.
- **Required correction** Provide the hyperparameter grid or search strategy and the final hyperparameter values used in the reported results.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4, location not provided
- **Issue** The description of the curated binding data states it was "downloaded from the regulatory edges with binding support in YEASTRACT" and then supplemented with Calling Cards and ChIP-Exo data. The exact criteria for including or replacing edges are not fully specified.
- **Required correction** Provide a more detailed description of the curation process, including the specific YEASTRACT version or download date, the criteria for selecting Calling Cards and ChIP-Exo edges, and how conflicts between datasets were resolved.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.6
- **Evidence pointer** Section 3.6, location not provided
- **Issue** The discovery section presents interesting biological findings, but the connection to the NP3 framework is not always clear. For example, the Nrg1-iron connection is supported by unpublished personal communication, which is not verifiable.
- **Required correction** Clarify which findings are directly supported by the NP3 predictions and which rely on external unpublished data. Consider whether the unpublished data should be included as a supplementary file or removed from the main text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3, location not provided
- **Issue** The description of the ZEV dataset states it contains "gene expression profiles at various time points after transient induction of 167 TFs." The specific time points and the number of replicates are not reported.
- **Required correction** Provide details on the time points, replicates, and any preprocessing steps applied to the ZEV dataset.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.7
- **Evidence pointer** Section 3.7, location not provided
- **Issue** The comparison between "constrained NP3 scores" and "original NP3 scores" in Figure 5D-F is not clearly explained in the text. The distinction between these two modes is important for understanding the results.
- **Required correction** Provide a clear definition of the constrained and unconstrained NP3 scores and explain the difference in the context of the integration mode.

## Risk / unsupported claims
- The claim that NP3 is "more accurate" than other methods is not supported by statistical testing.
- The claim of "three independent evaluation metrics" overstates the degree of independence, as the metrics share underlying data sources.
- The recommendation to use yeast-trained models for organisms with fewer than 40 TFs with binding data is based on indirect evidence and has not been tested cross-species.
- The biological findings in Section 3.6, particularly the Nrg1-iron connection, rely on unpublished personal communication and are not fully verifiable from the provided materials.
- The claim that the integration mode "forges a consensus network" is supported by the presented results, but the robustness of this approach to varying binding data quality is not established.
- The performance comparison with Genie3 and Infererator3 on the GO metric shows similar results, which is not fully reconciled with the overall claim of superiority.