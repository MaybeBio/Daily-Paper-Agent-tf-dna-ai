## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and figure legends (figures themselves not provided)
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and general interest assessment based solely on the provided text
- **Shared manuscript claim summary** The authors present Affinity Distillation (AD), a method to extract thermodynamic binding affinities from deep learning models trained on in vivo protein-DNA binding data. They claim AD outperforms motif-based methods across multiple TF classes and can recover quantitative affinities from ChIP-based data.
- **Visible evidence base** Text descriptions of results, figure legends, methods sections, supplementary figure references
- **Missing materials affecting confidence** Actual figures and supplementary data not provided; exact numerical values for many comparisons only partially reported; detailed statistical methods for some comparisons not fully described

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting approach to bridge deep learning models of TF binding with thermodynamic affinity measurements. The core idea of using in silico marginalization to extract affinity information from models trained on in vivo data is novel and potentially impactful. However, several technical concerns need to be addressed, particularly regarding the interpretation of what exactly is being measured, the statistical rigor of some comparisons, and the generalizability claims. The manuscript would benefit from clearer articulation of the relationship between the marginalization scores and true thermodynamic parameters, and from additional validation of the method's assumptions.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and gene regulation would be interested. The method offers a way to extract quantitative biophysical information from deep learning models, which is a growing area of interest. Those studying TF binding specificity, paralog-specific regulation, and the interpretation of non-coding variants would find the approach relevant. The work also speaks to the broader question of what deep learning models learn about biology.
- **Major strengths** The conceptual advance of extracting thermodynamic information from in vivo-trained deep learning models is significant. The systematic validation across multiple TF classes and data types is thorough. The comparison against multiple motif-based methods is appropriate. The demonstration of paralog-specific affinity prediction is particularly compelling. The method's ability to capture non-additive effects is an important advantage over traditional approaches.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - **Originality** High. The concept of distilling thermodynamic affinities from deep learning models of in vivo binding is novel and not a straightforward extension of existing methods.
  - **Scientific importance** Potentially high. If validated, this approach could change how researchers interpret deep learning models of TF binding and enable new types of analyses. The ability to predict affinities for arbitrary sequences from in vivo data has broad applications.
  - **Interdisciplinary readership** Moderate to high. The work bridges machine learning, biophysics, and regulatory genomics. The clear writing and conceptual framing make it accessible to a broad audience, though some technical details may be challenging for non-specialists.
  - **Technical soundness** Generally sound but with concerns. The core methodology is well-described, but several statistical and interpretational issues need clarification. The validation approach is reasonable but some comparisons may be biased.
  - **Readability for nonspecialists** Good. The manuscript is well-structured with clear explanations of the conceptual framework. The figures (based on legends) appear well-designed to convey the main findings. Some methods details are dense but appropriate for the target audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the initial results are encouraging, but several technical issues need to be addressed before the claims are fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability of what AD measures
- **Claim pointer** The manuscript claims AD extracts "thermodynamic affinities" from deep learning models of in vivo binding. The authors state AD "predicts energetic impacts of sequence variation" and that the method "isolates the energetic impacts of a sequence of interest."
- **Evidence pointer** Results sections on Pho4/Cbf1 and GR; Figure 1E-G; Figure 5K-M
- **Concern** The manuscript equates the marginalization scores with thermodynamic affinities, but the relationship between what the deep learning model learns from in vivo ChIP data and true thermodynamic binding energies is not fully established. ChIP-based measurements reflect occupancy, which is influenced by many factors beyond intrinsic affinity, including cooperativity, competition, chromatin state, and nuclear architecture. While the authors demonstrate correlation with in vitro measurements, correlation does not establish that the extracted quantity is truly thermodynamic affinity. The manuscript would benefit from a more careful discussion of what exactly is being measured and the assumptions underlying the interpretation.
- **Why it matters** The central claim of the paper is that AD extracts thermodynamic information. If the extracted quantity is not truly thermodynamic affinity but rather some composite measure that correlates with it, the interpretation of all downstream analyses changes. This affects the validity of the paralog-specific predictions and the claims about non-additive effects.
- **Resolution test** The authors should provide additional validation that the extracted quantities behave like thermodynamic parameters. This could include testing whether the predicted affinities are concentration-independent, whether they predict binding across different experimental conditions, or whether they can be used to predict absolute Kd values without calibration. Alternatively, the authors should temper their claims and describe the extracted quantity as an "effective affinity" that captures both intrinsic and context-dependent contributions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of method comparisons
- **Claim pointer** The manuscript claims AD "outperforms" motif-based methods across multiple datasets, with specific RMSE values reported (e.g., 0.204 kcal/mol for Pho4, 0.409 kcal/mol for Cbf1, 0.414 kcal/mol for GR).
- **Evidence pointer** Figures 1H-I, 2H-I, 3G, 5L-M; Supplement Section 3
- **Concern** The comparison between AD and motif-based methods may not be entirely fair. The motif-based methods are calibrated using the same calibration set, but the calibration procedure may favor AD if the relationship between AD scores and measured affinities is more linear. Additionally, the manuscript does not report confidence intervals or statistical tests for the RMSE differences. It is unclear whether the reported improvements are statistically significant. The comparison also does not account for the fact that AD uses the full sequence context, while motif-based methods are inherently limited to the motif region.
- **Why it matters** The claim of superior performance is central to the paper's impact. If the comparison is biased or the differences are not statistically significant, the conclusions about AD's advantages are weakened.
- **Resolution test** The authors should provide confidence intervals for the RMSE values, perform statistical tests for the differences between methods, and discuss potential sources of bias in the comparison. They should also consider whether the calibration procedure is optimal for each method or whether it introduces bias.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability claims
- **Claim pointer** The manuscript claims AD "can accurately predict binding affinities" across "diverse classes of yeast and mammalian TFs" and that the method generalizes to "multiple mammalian TF classes and cell types."
- **Evidence pointer** Results sections on Pho4, Cbf1, GR, MAX, Myc, GABPA, E2F1; Figures 2, 3, 5, 6
- **Concern** The generalizability claims are based on a limited number of TF classes. The TFs tested include bHLH (Pho4, Cbf1, MAX, Myc), nuclear receptor (GR), ETS (GABPA), and E2F (E2F1) families. While this is a reasonable diversity, it is not clear how the method would perform on TFs with very different binding modes, such as those that bind as heterodimers with strong cooperative interactions, or those that bind to highly degenerate motifs. The manuscript also does not address how the method would perform on TFs with very few ChIP peaks or on TFs where the binding is strongly influenced by pioneer factors or chromatin remodeling.
- **Why it matters** The claim of generalizability is important for the method's utility. If the method only works well for certain TF classes, its impact is more limited.
- **Resolution test** The authors should either test additional TF classes with different binding characteristics or temper their generalizability claims. They should also discuss the potential limitations of the method for TFs with unusual binding properties.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of non-additive effects
- **Claim pointer** The manuscript claims AD "successfully recapitulated the non-additive effects of multiple binding site mutations" and that this is a key advantage over additive models.
- **Evidence pointer** Figure 5O
- **Concern** The evidence for non-additive effects is based on a single comparison (Figure 5O) with limited description of the experimental design. The manuscript does not provide details on how many sequences were tested, how the non-additive effects were quantified, or whether the observed non-additivity is statistically significant. The comparison between AD predictions and additive model predictions is also not fully described.
- **Why it matters** The ability to capture non-additive effects is a key claimed advantage of AD. If this is not rigorously demonstrated, the advantage over simpler models is not established.
- **Resolution test** The authors should provide more details on the experimental design for the non-additivity analysis, including the number of sequences tested, the statistical methods used, and the magnitude of the non-additive effects. They should also consider whether the observed non-additivity could be an artifact of the model architecture or training procedure.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of calibration procedure
- **Affected element** Methods section on calibration
- **Evidence pointer** Methods section "Affinity Distillation"
- **Issue** The calibration procedure is described briefly. It is unclear how many in vitro measurements are needed for calibration, how the calibration set is selected, and whether the calibration is robust to the choice of calibration points.
- **Required correction** Provide more details on the calibration procedure, including the number of points needed, the selection criteria, and the sensitivity of the results to the calibration set.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reporting of numerical results
- **Affected element** Results sections
- **Evidence pointer** Figures 1-6
- **Issue** The manuscript reports correlation coefficients and RMSE values but does not consistently report confidence intervals or the number of sequences tested in each comparison. This makes it difficult to assess the precision of the reported values.
- **Required correction** Report confidence intervals for all correlation coefficients and RMSE values, and specify the number of sequences used in each analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion does not adequately address potential limitations of the approach, such as the dependence on the quality of the deep learning model, the potential for overfitting, or the assumptions underlying the marginalization procedure.
- **Required correction** Add a paragraph discussing the limitations of the approach and potential sources of error or bias.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and Data Availability section
- **Evidence pointer** Code and Data Availability section
- **Issue** The code is available, but the manuscript does not specify the computing environment, dependencies, or expected runtime. This may hinder reproducibility.
- **Required correction** Provide a detailed description of the computing environment, software dependencies, and expected runtime for the main analyses.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures (based on legends)
- **Evidence pointer** Figure legends
- **Issue** Based on the legends, some figures appear to contain a large amount of information that may be difficult to interpret. For example, Figure 1 appears to have multiple panels with different types of information.
- **Required correction** Consider simplifying figures or providing additional explanatory text in the legends to improve readability.

## Risk / unsupported claims
- The claim that AD extracts "thermodynamic affinity" from in vivo data is not fully supported. The relationship between the marginalization scores and true thermodynamic parameters needs further validation.
- The claim that AD "outperforms" motif-based methods is based on RMSE comparisons without statistical tests or confidence intervals.
- The claim of generalizability across "diverse" TF classes is based on a limited number of TF families.
- The claim that AD captures "non-additive effects" is based on a single analysis with limited description.
- The statement that AD "can serve as an in silico biophysical oracle" is speculative and not directly supported by the data presented.
- The claim that AD "bridges the gap between modern neural network models and ground-up biophysical thermodynamic models" is an interpretation that requires more careful justification.