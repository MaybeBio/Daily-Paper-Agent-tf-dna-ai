## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, conclusion, methods) as provided
- **Assessment boundary** Scientific validity, technical soundness, clarity, and support of claims based solely on the supplied material
- **Shared manuscript claim summary** The authors present TECSAS, a Transformer-based deep learning model that predicts chromatin subcompartment annotations (A/B and A1/A2/B1/B2/B3) and nuclear body associations (LADs, NADs, SPADs) directly from epigenomic data (histone modifications, transcription factor binding, RNA-seq), without reliance on Hi-C input. They report high accuracy, demonstrate the importance of long-range epigenomic context, and show transferability across cell types.
- **Visible evidence base** Abstract; Introduction; Results sections 2.1, 2.2, 2.3; Conclusion; Methods sections 4.1, 4.2, 4.3; Figures referenced (1, 2, 3, 4, 5) but not provided; Supplementary information referenced but not provided
- **Missing materials affecting confidence** Figures 1-5 (including confusion matrices, attention maps, accuracy plots, structural projections) are referenced but not included; Supplementary Information (SI) is referenced but not provided; specific hyperparameter values, training details, and data preprocessing code are not fully described; no quantitative comparison with existing methods (e.g., PyMEGABASE) beyond a single accuracy value; no statistical significance tests or confidence intervals reported

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful application of Transformer architectures to predict chromatin subcompartments from epigenomic data, addressing a relevant problem in 3D genome biology. The core idea is timely and the reported accuracies are promising. However, the current manuscript, as provided, lacks critical details and visual evidence needed to fully evaluate the claims. Several key results are referenced to figures that are not available, and the comparison with existing methods is incomplete. The technical approach is sound in principle, but the evidence base is insufficient to establish the case at the level expected for a high-impact journal.
- **Who would be interested in the results, and why** Researchers in 3D genome organization, epigenomics, and computational biology would be interested. The model offers a way to infer structural compartments from widely available epigenomic data, potentially enabling studies in cell types where Hi-C is not available. The fine-tuning capability for nuclear body associations adds practical value. The work also speaks to the broader community interested in applying deep learning to genomics.
- **Major strengths** 1. The problem is well-motivated and relevant. 2. The use of a Transformer architecture to capture long-range epigenomic context is a reasonable and potentially powerful approach. 3. The model's flexibility (fine-tuning for different structural annotations) is a notable strength. 4. The reported accuracy (0.78 for subcompartments, 0.87/0.93 for A/B) is competitive with existing methods, and the comparison to experimental replicate accuracy (~0.95) is a useful benchmark. 5. The analysis of transition regions and confidence scores adds biological insight.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
  - R1-M5
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
  - R1-m6
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing figures and data), R1-M2 (incomplete comparison), R1-M3 (lack of statistical rigor), R1-M4 (insufficient methodological detail), R1-M5 (overstated claims)
- **Assessment against Nature-style criteria** 
  - Originality: The application of Transformers to predict subcompartments from epigenomic data is novel, though the underlying concept of linking epigenomics to structure is not new. The fine-tuning approach for nuclear bodies adds originality.
  - Scientific importance: The potential to predict 3D structure from epigenomic data alone is important, as it could expand the scope of structural studies. However, the demonstrated impact is limited by the lack of new biological insights or broad applicability shown.
  - Interdisciplinary readership: The work bridges deep learning and genomics, which has broad appeal. However, the presentation assumes familiarity with both fields, and the lack of clear biological implications may limit appeal to a general audience.
  - Technical soundness: The architecture is reasonable, but the evaluation is incomplete. Missing figures, lack of statistical tests, and incomplete comparisons undermine confidence in the technical claims.
  - Readability for nonspecialists: The manuscript is generally clear but includes jargon and references to methods without full explanation. The absence of figures makes it harder to follow the results.
- **Recommendation posture** Currently not established from the provided evidence. The core idea is promising, and the approach is technically plausible, but the manuscript as supplied does not provide sufficient evidence to support the claims. I would be supportive if the missing figures, detailed methods, and rigorous comparisons are provided and the claims are appropriately tempered.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims high accuracy in predicting subcompartments (0.78 overall, 0.87/0.93 for A/B) and improved performance with larger epigenomic context, but these claims are supported only by references to figures that are not provided.
- **Evidence pointer** Figures 2A-F, 3A-E, 4A-C, 5A-D; location not provided
- **Concern** The central results are presented through figures that are not included in the supplied material. Without the confusion matrices, accuracy plots, attention maps, and structural projections, the reader cannot verify the reported accuracies, the comparison with PyMEGABASE, the effect of context size, or the biological validity of the nuclear body predictions.
- **Why it matters** The claims of high accuracy and the importance of long-range context are the core of the paper. Without visual or quantitative evidence, these claims are unverifiable. The reader cannot assess whether the model performs as described or whether the conclusions are justified.
- **Resolution test** Provide all figures with clear labels, legends, and statistical details. Ensure that the data underlying each figure are accessible and that the claims in the text are directly supported by the displayed results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evaluation
- **Claim pointer** The manuscript states that TECSAS outperforms PyMEGABASE (0.78 vs 0.57 accuracy) and that this improvement is due to the Transformer architecture and larger context, but the comparison is incomplete and not rigorously quantified.
- **Evidence pointer** Section 2.2, Figure 3A-B; location not provided
- **Concern** The comparison with PyMEGABASE is limited to a single accuracy value under a specific condition. There is no discussion of the variability of these results, no statistical testing, and no comparison with other existing methods (e.g., CoRNN, Epiphany, Calder). The claim that the Transformer architecture is the reason for improvement is not directly tested, as the simplified TECSAS with fewer features still outperforms PYMB, but the contribution of architecture vs. input features is not disentangled.
- **Why it matters** A fair and thorough comparison is essential to establish the advantage of TECSAS over existing tools. Without it, the claim of superiority is not supported. The field would benefit from knowing under what conditions TECSAS is preferable and where it might fail.
- **Resolution test** Include a systematic comparison with multiple methods across several cell lines and resolutions, with appropriate statistical tests (e.g., confidence intervals, permutation tests). Discuss the limitations of each method and the conditions under which TECSAS is advantageous.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports accuracies and improvements but does not provide any measure of uncertainty, such as confidence intervals, standard deviations, or statistical significance tests.
- **Evidence pointer** Sections 2.1, 2.2, 2.3; location not provided
- **Concern** The reported accuracies (e.g., 0.78, 0.87, 0.93) are presented as point estimates without any indication of variability across different data splits, random seeds, or biological replicates. The improvement in accuracy with larger context is described qualitatively, but no statistical test is performed to confirm that the improvement is significant.
- **Why it matters** Without measures of uncertainty, the reader cannot assess the reliability of the results. The differences between models or conditions could be within the noise. Statistical rigor is essential for a deep learning paper, especially when claims of superiority are made.
- **Resolution test** Report the mean and standard deviation (or confidence intervals) of accuracy metrics across multiple runs or cross-validation folds. Perform statistical tests (e.g., paired t-test, Wilcoxon signed-rank test) for key comparisons, such as TECSAS vs. PYMB and the effect of context size.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological detail
- **Claim pointer** The manuscript describes the model architecture and training, but key details are missing, including the exact number of parameters, training time, data preprocessing steps, and the specific implementation of the fine-tuning procedure.
- **Evidence pointer** Section 4.2, 4.3; location not provided
- **Concern** The methods section is brief and lacks sufficient detail for reproducibility. For example, the learning rate is described as "initially set to 2.5," which is unusually high and likely a typo. The description of the fine-tuning process is vague, and the criteria for selecting hyperparameters are not given. The data preprocessing steps (e.g., how the 14-locus neighborhood is defined, how missing data are handled) are not fully specified.
- **Why it matters** Reproducibility is a cornerstone of scientific publishing. Without complete methodological details, other researchers cannot replicate the work or build upon it. The high learning rate raises concerns about the correctness of the training procedure.
- **Resolution test** Provide a complete description of the model architecture, training procedure, hyperparameter selection, and data preprocessing. Include a link to the code and any relevant configuration files. Clarify the learning rate and other training details.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** The manuscript claims that TECSAS can predict nuclear body associations (LADs, NADs, SPADs) with high accuracy and that these predictions are biologically meaningful, but the evidence is limited and the biological validation is weak.
- **Evidence pointer** Section 2.3, Figure 5A-D; location not provided
- **Concern** The accuracy for predicting LADs, NADs, and SPADs is reported, but the biological significance is only inferred from the expected overlap with A/B compartments. The validation using 3D structures from DNA tracing is mentioned but not shown in detail. The claim that the model reveals heterogeneity within compartments is interesting but not fully explored.
- **Why it matters** The ability to predict nuclear body associations is a key selling point of the paper. Without strong biological validation, the reader cannot be confident that the predictions are meaningful beyond statistical correlation. The claim of heterogeneity needs more evidence to be convincing.
- **Resolution test** Provide detailed results of the 3D structure validation, including quantitative measures of colocalization. Discuss the biological implications of the heterogeneity more thoroughly. Consider additional validation using independent datasets or experimental perturbations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract is clear but could be more specific about the performance metrics and the novelty of the approach. The phrase "Epigenetics is all you need" in the title is catchy but may be seen as overclaiming.
- **Required correction** Consider tempering the title and abstract to avoid overstatement. Specify the exact accuracy values and the scope of the model's applicability.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Introduction
- **Evidence pointer** Section 1, location not provided
- **Issue** The introduction provides a good background but does not clearly state the limitations of existing methods beyond PyMEGABASE. The novelty of TECSAS is not sharply contrasted with other deep learning approaches.
- **Required correction** Add a more explicit comparison with existing deep learning methods (e.g., CoRNN, Epiphany) and clarify what TECSAS offers that they do not.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Methods
- **Evidence pointer** Section 4.2, location not provided
- **Issue** The learning rate is stated as "initially set to 2.5," which is likely a typo. This is an unusually high value and would likely cause training instability.
- **Required correction** Verify and correct the learning rate value. Provide the actual learning rate schedule and optimizer settings.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Section 4.1, location not provided
- **Issue** The data preprocessing steps are described briefly. The exact definition of the "14-locus neighborhood" and how the signal intensities are aggregated are not fully clear.
- **Required correction** Provide a more detailed description of the data preprocessing, including how the neighborhood is defined and how missing data are handled.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results
- **Evidence pointer** Section 2.2, location not provided
- **Issue** The text refers to "Figures ??" and "Figure ??" without specific numbers, indicating incomplete cross-referencing.
- **Required correction** Ensure all figure references are correctly numbered and that the figures are included in the final manuscript.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results
- **Evidence pointer** Section 2.3, location not provided
- **Issue** The interpretation of the attention maps is somewhat speculative. The claim that attention maps reveal "the model's focus on specific patterns" is not rigorously supported.
- **Required correction** Provide a more cautious interpretation of the attention maps, and consider additional analyses to support the claims about feature importance.

## Risk / unsupported claims
- The claim that TECSAS achieves high accuracy in predicting subcompartments is unsupported without the actual figures and data.
- The claim that TECSAS outperforms PyMEGABASE is based on a single comparison and lacks statistical rigor.
- The claim that the Transformer architecture is the reason for improved performance is not directly tested.
- The claim that TECSAS can predict nuclear body associations with high accuracy is not fully validated biologically.
- The claim that the model reveals heterogeneity within compartments is interesting but not sufficiently explored.
- The claim that TECSAS is transferable across cell types is based on limited evidence and needs more extensive validation.