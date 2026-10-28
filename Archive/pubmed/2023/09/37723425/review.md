## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusion. Figures and tables referenced but not fully visible. Supplementary materials not provided.
- **Assessment boundary** Assessment is limited to the provided manuscript text. Claims regarding experimental results, model architecture, and comparisons with other methods are evaluated based on the text alone. Figures, tables, and supplementary files are referenced but their contents are not fully accessible for verification.
- **Shared manuscript claim summary** The manuscript proposes DeepCAC, a deep learning architecture combining multi-head self-attention and concatenated convolutional modules, for the classification of DNA transcription factors. The authors claim that DeepCAC achieves superior performance compared to existing methods (DanQ, DeepSite, CNN-Zeng, CNN-BiGRU) in terms of accuracy, AUC, and AP, while maintaining a smaller parameter count. The method is presented as a novel contribution to the field of transcription factor classification.
- **Visible evidence base** The manuscript text includes descriptions of the model architecture, training setup, and evaluation metrics. Numerical results are reported in the text and in Table 1 (AUC per class). Figures 2 and 3 are referenced but not visible. Supplementary files are mentioned but not provided.
- **Missing materials affecting confidence** The following materials are not available for review: full figures (Fig. 1, 2, 3), supplementary files (Additional files 1-4), the complete dataset description, and any code or implementation details. The absence of these materials limits the ability to fully verify the reported results and the reproducibility of the method.

## Reviewer
- **Overall assessment** The manuscript presents a reasonable and potentially useful deep learning architecture for transcription factor classification. The combination of multi-head self-attention with convolutional layers is not entirely novel, as similar approaches have been explored in other domains, but its application to transcription factor classification may offer some value. However, the manuscript has several significant weaknesses. The experimental evaluation is limited in scope, the comparison with existing methods is not sufficiently rigorous, and the reported results are not fully verifiable from the provided text. The claims of novelty and superiority are not fully supported by the evidence presented. The manuscript would benefit from a more thorough experimental design, including statistical significance testing, ablation studies, and a more detailed analysis of the model's behavior. The writing is generally clear but could be improved in terms of precision and conciseness.
- **Who would be interested in the results, and why** Researchers working on deep learning applications in genomics, particularly those focused on transcription factor binding site prediction and classification, may find this work of interest. The proposed architecture could be a useful addition to the toolbox of methods for sequence-based classification tasks. Additionally, researchers interested in the application of attention mechanisms in bioinformatics may find the approach worth considering.
- **Major strengths** The manuscript addresses a relevant problem in bioinformatics, namely the classification of transcription factors from DNA sequences. The proposed architecture is clearly described, and the authors have made an effort to compare their method with several existing approaches. The focus on parameter efficiency is a positive aspect, as it addresses a practical concern in deep learning model deployment.
- **Major Concerns** The experimental evaluation is not sufficiently comprehensive. The comparison with existing methods is limited to a single dataset, and no statistical significance testing is reported. The manuscript lacks ablation studies to justify the specific design choices, such as the number of attention heads and the number of concatenated modules. The reported results are not fully reproducible from the text, as the figures and supplementary materials are not available. The claim of novelty is overstated, as attention-augmented convolutions have been explored in other fields. The discussion of the results is somewhat superficial and does not provide deep insights into why the proposed method works or fails in specific cases.
- **Minor Comments** The manuscript contains some typographical and grammatical errors. The notation in the equations is not always clearly defined. The description of the dataset is incomplete, and the preprocessing steps are not fully detailed. The discussion of future work is somewhat speculative and not well grounded in the current results.
- **Technical failings that need to be addressed before the case is established** The lack of statistical significance testing and the absence of ablation studies are significant technical shortcomings. The manuscript does not provide sufficient details on the hyperparameter tuning process, which makes it difficult to assess the robustness of the method. The comparison with existing methods is not entirely fair, as the baselines may not have been optimally tuned. The manuscript does not provide a clear analysis of the computational cost of the proposed method, which is an important consideration for practical applications.
- **Assessment against Nature-style criteria** 
  - **Originality:** The combination of multi-head self-attention and convolutional layers is not entirely new, but its application to transcription factor classification is a modest extension of existing work. The novelty is limited.
  - **Scientific importance:** The problem of transcription factor classification is important, but the proposed method does not represent a major conceptual advance. The potential impact is moderate.
  - **Interdisciplinary readership:** The work is primarily of interest to researchers in bioinformatics and computational biology. It is unlikely to attract a broad interdisciplinary audience.
  - **Technical soundness:** The technical approach is generally sound, but the experimental validation is insufficient. The lack of statistical testing and ablation studies weakens the technical case.
  - **Readability for nonspecialists:** The manuscript is written in a technical style that may be challenging for nonspecialists. The introduction and discussion could be improved to make the work more accessible.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the experimental evaluation and technical validation are not sufficient to support the claims made. The authors would need to provide a more rigorous and comprehensive analysis to establish the case for the proposed method.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The manuscript claims that DeepCAC achieves superior performance compared to DanQ, DeepSite, CNN-Zeng, and CNN-BiGRU in terms of accuracy, AUC, and AP.
- **Evidence pointer** Results section, Figure 2, Table 1
- **Concern** The reported results are based on a single dataset, and no statistical significance testing is provided. It is unclear whether the observed improvements are statistically significant or due to random variation. The comparison with baseline methods may not be fair, as the baselines may not have been optimally tuned.
- **Why it matters** Without statistical significance testing, the claim of superiority is not robust. A single dataset evaluation limits the generalizability of the findings. An unfair comparison could lead to misleading conclusions.
- **Resolution test** The authors should provide statistical significance testing (e.g., confidence intervals, p-values) for the reported metrics. They should also evaluate the method on multiple datasets to demonstrate generalizability. The baselines should be carefully tuned, and the tuning process should be described.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The manuscript claims that the concatenated attention-augmented convolution module is effective in capturing hidden features and improving classification performance.
- **Evidence pointer** Methods section, Figure 1, Algorithm 2
- **Concern** The manuscript does not include ablation studies to justify the design choices. It is unclear how the number of attention heads, the number of concatenated modules, and the specific combination of convolution and attention contribute to the overall performance. The contribution of each component is not isolated.
- **Why it matters** Without ablation studies, it is difficult to determine whether the proposed architecture is truly optimal or whether simpler designs could achieve similar results. The design choices appear somewhat arbitrary.
- **Resolution test** The authors should conduct ablation studies by systematically removing or varying key components (e.g., attention heads, concatenated modules) and reporting the impact on performance. This would provide a clearer understanding of the contribution of each component.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes the model architecture and training setup, but the details are insufficient for reproduction.
- **Evidence pointer** Methods section, Experiment settings
- **Concern** The manuscript does not provide sufficient details on the hyperparameter tuning process, the initialization of the model, the learning rate schedule, or the batch size. The dataset preprocessing steps are not fully described. The code and trained models are not made available.
- **Why it matters** Reproducibility is a fundamental requirement for scientific research. Without sufficient details, other researchers cannot replicate the experiments or build upon the work.
- **Resolution test** The authors should provide a detailed description of all hyperparameters, training procedures, and data preprocessing steps. They should also make the code and trained models publicly available.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with state-of-the-art
- **Claim pointer** The manuscript claims that DeepCAC achieves state-of-the-art performance compared to classical convolutional methods.
- **Evidence pointer** Results section, Discussion section
- **Concern** The comparison is limited to a small set of baseline methods. More recent and advanced methods for transcription factor classification, such as those based on transformer architectures (e.g., DNABERT), are not included in the comparison. The claim of state-of-the-art performance is therefore not fully supported.
- **Why it matters** A limited comparison may not accurately reflect the current state of the field. The claim of state-of-the-art performance requires a more comprehensive comparison with the latest methods.
- **Resolution test** The authors should include a broader set of baseline methods, particularly those that have been recently published, and compare their performance on the same dataset.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Equation 1
- **Evidence pointer** Methods section, Overview of our method
- **Issue** The equation for the loss function appears to have a formatting error. The term `(1-y_i log(1-σ(α·H_i+β)))` is missing a closing parenthesis and the structure is ambiguous.
- **Required correction** The equation should be rewritten with proper parentheses and clear notation. For example, it should be `ζ = -Σ [y_i σ(α·H_i+β) + (1-y_i) log(1-σ(α·H_i+β))]`.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Dataset description
- **Evidence pointer** Data source section
- **Issue** The description of the dataset is incomplete. The number of samples, the class distribution, and the specific preprocessing steps are not described. The list of transcription factors includes "MEF2A" twice, which may be a typo.
- **Required correction** The authors should provide a complete description of the dataset, including the number of samples, class distribution, and preprocessing steps. The duplicate "MEF2A" should be corrected.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2
- **Evidence pointer** Results section
- **Issue** The description of Figure 2 is incomplete. The figure is said to show accuracy, AUC, AP, and parameters, but the layout and the specific panels are not described in the text.
- **Required correction** The authors should provide a more detailed description of Figure 2 in the text, including the content of each panel.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout the manuscript
- **Evidence pointer** Entire text
- **Issue** The manuscript contains several grammatical errors and awkward phrasings. For example, "the design of CNN-Zeng model uses 128 convolutional kernels for feature extraction as reported in the paper" could be rephrased for clarity.
- **Required correction** The manuscript should be carefully proofread and edited for grammar and clarity.

## Risk / unsupported claims
- The claim that DeepCAC achieves "state-of-the-art performance" is not fully supported, as the comparison is limited to a small set of baselines and does not include more recent methods.
- The claim that the method "enables the simultaneous capture of local hidden features and long-distant dependent hidden features" is not directly verified by the experiments. No analysis is provided to demonstrate that the model indeed captures these features.
- The claim that the method achieves "optimal results even with a small number of parameters" is not fully supported, as the parameter counts of the baseline methods are not reported in the text.
- The claim that the method is "the first time such an approach has been used in work on DNA transcription factors" is difficult to verify and may be overstated, as similar attention-augmented convolution approaches have been used in other domains.
- The reported numerical results (e.g., accuracy, AUC, AP) are not fully verifiable from the provided text, as the figures and supplementary materials are not available.