## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors propose iEnhancer-Hybrid, a dual-branch model combining DNABERT-2 for global contextual features and a three-layer multi-scale dilated convolution network for local regulatory motifs, achieving state-of-the-art performance on the iEnhancer-2L test set (ACC 81.25%, AUC 86.84%) and demonstrating motif-level interpretability via saliency analysis and motif comparison against JASPAR 2024.
- **Visible evidence base** Abstract text only; no quantitative comparisons, statistical tests, or methodological details are provided
- **Missing materials affecting confidence** Full methods, model architecture details, hyperparameters, training/validation splits, baseline descriptions, full performance tables, saliency analysis methodology, STREME/Tomtom parameters, and JASPAR comparison details

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially useful approach to enhancer prediction by combining a pretrained language model with a multi-scale convolutional branch. The reported performance is competitive, and the interpretability analysis is a welcome addition. However, the abstract alone does not provide sufficient evidence to evaluate the robustness of the claims, the novelty relative to existing enhancer prediction methods, or the validity of the interpretability conclusions. Several technical details and statistical considerations are missing, and the current evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Researchers in computational genomics, regulatory genomics, and machine learning applied to DNA sequence analysis would be interested. The work addresses a practical problem in enhancer identification, which is relevant for understanding gene regulation and disease-associated variants. The combination of pretrained models with local motif extraction may appeal to those developing interpretable deep learning methods for genomics.
- **Major strengths** The dual-branch architecture is conceptually clear and addresses a recognized limitation of pretrained language models, namely their reduced sensitivity to position-sensitive local patterns. The use of multi-scale dilated convolutions to capture local motifs without a large parameter increase is a sensible design choice. The inclusion of interpretability analysis through saliency and motif comparison strengthens the biological relevance of the approach.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: The combination of a pretrained DNA language model with a multi-scale dilated convolution branch is a reasonable incremental contribution, but the abstract does not clearly differentiate it from existing enhancer prediction methods that also use hybrid architectures or motif-based features. Originality is moderate but not fully established.  
  - Scientific importance: Enhancer identification is an important problem, and improved accuracy with interpretable features would be valuable. However, the abstract does not demonstrate a substantial advance over the current state of the art beyond a marginal accuracy improvement.  
  - Interdisciplinary readership: The work is primarily of interest to computational biologists and machine learning researchers. The abstract is written in a way that is accessible to these groups, but the broader biological significance is not articulated.  
  - Technical soundness: The architecture is plausible, but the abstract lacks details on training, validation, and statistical rigor. The performance claims are not supported by confidence intervals or significance tests.  
  - Readability for nonspecialists: The abstract is reasonably clear, but terms such as "multi-scale dilated convolution" and "input-gradient-based saliency" may be opaque to readers outside the field. A brief explanation of these concepts would improve accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The approach is promising, but the abstract alone does not provide sufficient detail to assess the validity of the performance claims, the novelty of the method, or the robustness of the interpretability analysis. A full manuscript with detailed methods and results would be required to make a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The model achieved an ACC of 81.25% and an AUC of 86.84% on the independent iEnhancer-2L test set, attaining the highest values among the compared methods.  
- **Evidence pointer** Abstract, performance results section (location not provided)  
- **Concern** The abstract reports only two performance metrics without any indication of variance, confidence intervals, or statistical significance relative to the compared methods. It is unclear how many runs were performed, whether the results are averaged, and whether the differences from baselines are meaningful.  
- **Why it matters** Without statistical rigor, the claim of "highest values" cannot be evaluated. Small differences in ACC or AUC may not be significant, and the absence of error bars or significance tests undermines the reliability of the performance claim.  
- **Resolution test** Provide the number of independent runs, mean and standard deviation for each metric, and a statistical test (e.g., paired bootstrap or McNemar's test) comparing iEnhancer-Hybrid to each baseline.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The dual-branch architecture enables complementary representation of global semantics and local motifs, improving predictive performance without substantially increasing the number of parameters.  
- **Evidence pointer** Abstract, method description (location not provided)  
- **Concern** The abstract does not provide any quantitative information on the parameter count of iEnhancer-Hybrid relative to DNABERT-2 alone or to other baselines. The claim of "without substantially increasing the number of parameters" is unsupported.  
- **Why it matters** The efficiency claim is a key selling point of the proposed architecture. Without parameter counts or a complexity comparison, readers cannot assess whether the added convolutional branch is indeed lightweight or whether the performance gain comes at a significant computational cost.  
- **Resolution test** Report the total number of trainable parameters for iEnhancer-Hybrid and for each baseline, and discuss the trade-off between performance and model size.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The model uses a three-layer multi-scale dilated convolution network to enlarge the receptive field and capture local regulatory motifs at multiple scales.  
- **Evidence pointer** Abstract, method description (location not provided)  
- **Concern** The abstract does not specify the dilation rates, kernel sizes, number of filters, or how the multi-scale features are combined. Without these details, the architecture cannot be reproduced or compared fairly with other methods.  
- **Why it matters** Reproducibility is a core requirement for computational biology methods. The lack of architectural details prevents other researchers from implementing or validating the approach, and it also makes it difficult to assess whether the design choices are optimal.  
- **Resolution test** Provide a full description of the convolutional branch, including layer dimensions, dilation rates, activation functions, and the fusion mechanism, in the methods section.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Interpretability and biological validity  
- **Claim pointer** Input-gradient-based saliency analysis, together with STREME/Tomtom motif comparison of model-prioritized sequence fragments against JASPAR 2024 transcription factor binding profiles, indicated that the learned local patterns were consistent with known transcription factor binding motifs.  
- **Evidence pointer** Abstract, interpretability analysis (location not provided)  
- **Concern** The abstract does not describe how the saliency analysis was performed, how sequence fragments were prioritized, what thresholds were used for motif matching, or how many motifs were found to be consistent with JASPAR. The claim of consistency is vague and not quantified.  
- **Why it matters** The interpretability analysis is presented as supporting the biological relevance of the model. Without specific details on the analysis pipeline and the statistical significance of the motif matches, the claim that the model learns known motifs is not substantiated.  
- **Resolution test** Describe the saliency method, the criteria for selecting sequence fragments, the STREME parameters, the Tomtom significance threshold, and report the number and identity of matched motifs with their associated p-values or E-values.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, method description  
- **Evidence pointer** Abstract, first paragraph (location not provided)  
- **Issue** The term "multi-scale dilated convolution" is used without explaining what "multi-scale" refers to in this context, such as different dilation rates or kernel sizes.  
- **Required correction** Briefly clarify the meaning of "multi-scale" in the abstract or methods.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract, performance comparison  
- **Evidence pointer** Abstract, results section (location not provided)  
- **Issue** The abstract states that iEnhancer-Hybrid achieved the highest values among compared methods, but it does not list which methods were compared or how many.  
- **Required correction** Name the baseline methods and provide a summary of their performance in the abstract or a table.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract, interpretability section  
- **Evidence pointer** Abstract, final sentence (location not provided)  
- **Issue** The phrase "model-prioritized sequence fragments" is ambiguous and could be interpreted in multiple ways.  
- **Required correction** Define what is meant by "model-prioritized" and how the fragments were selected.

## Risk / unsupported claims
- The claim of achieving the highest ACC and AUC among compared methods is unsupported without statistical tests and a full list of baselines.
- The claim that the model improves performance without substantially increasing parameters is unsupported without parameter counts.
- The claim that learned local patterns are consistent with known transcription factor binding motifs is unsupported without details on the motif analysis and significance thresholds.
- The overall performance improvement over existing methods is not quantified beyond two metrics, and the generalizability of the model to other enhancer datasets is not addressed.