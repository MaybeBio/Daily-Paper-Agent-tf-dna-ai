## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the supplied abstract
- **Shared manuscript claim summary** The authors propose a lifelong learning based dynamic deep network that fuses six feature extraction methods (Average Blocks, Discrete Cosine Transform, Discrete Wavelet Transform, Global encoding, Normalized Moreau-Broto Autocorrelation, Pseudo position-specific scoring matrix) for DNA binding protein prediction. They report superior performance on three datasets compared to other classification techniques, with single-sample specificity of 81.0% and 83.0%, single-sample sensitivity of 82.4% and 90.7%, and accuracy of 88.4%, 80.0%, and 76.6% on benchmark datasets.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or dataset descriptions provided
- **Missing materials affecting confidence** Full manuscript, experimental setup, dataset specifications, baseline method details, statistical significance tests, implementation code, and hyperparameter configurations

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting application of lifelong learning to DNA binding protein prediction, a well studied binary classification problem in bioinformatics. However, the supplied material is insufficient to evaluate the technical soundness of the proposed method or the validity of the reported performance claims. The abstract lacks critical details on model architecture, training procedure, comparison protocols, and statistical rigor. The reported metrics are presented without confidence intervals or significance testing, and the relationship between the lifelong learning framework and the specific prediction task is not clearly justified. The case for novelty and practical advantage over existing methods is not established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics, particularly those working on protein function prediction and DNA binding site identification, may find the application of lifelong learning to feature fusion interesting. Additionally, machine learning researchers exploring continual learning in biological sequence classification contexts could be interested in the methodological transfer. However, the current abstract does not provide enough detail to assess whether the results would be broadly useful beyond a narrow methodological niche.
- **Major strengths** The abstract addresses a relevant problem in bioinformatics with potential practical implications. The use of multiple feature extraction methods is a common and reasonable strategy for capturing diverse sequence properties. The application of lifelong learning to this domain is a relatively fresh angle that could offer a new perspective on model adaptation in biological sequence analysis.
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
  Originality: The application of lifelong learning to DNA binding protein prediction is somewhat novel, but the abstract does not demonstrate how this differs fundamentally from existing deep learning approaches in the field. The feature fusion strategy is standard practice.  
  Scientific importance: DNA binding protein prediction is an established problem with many existing solutions. The abstract does not articulate a clear biological or methodological advance that would elevate its importance beyond incremental improvement.  
  Interdisciplinary readership: The work sits at the intersection of machine learning and bioinformatics, but the abstract is written in a way that assumes familiarity with both fields without providing sufficient context for either audience.  
  Technical soundness: Not assessable from the abstract. Critical details on model design, training, and evaluation are missing.  
  Readability for nonspecialists: The abstract is dense with technical terms and lacks clear explanations of the proposed architecture and its advantages. The writing is not accessible to a broad scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract does not provide sufficient information to assess the validity of the claims or the novelty of the approach. A full manuscript with detailed methods, rigorous evaluation, and statistical analysis would be required to support the reported findings.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The proposed dynamic deep network based on lifelong learning architecture fuses six features for efficient classification of DNA binding proteins.  
- **Evidence pointer** Abstract, "A dynamic deep network based on lifelong learning architecture was then proposed in order to fuse six features"  
- **Concern** The abstract provides no description of the network architecture, the mechanism by which lifelong learning is implemented, or how the six features are fused. Without these details, the technical validity of the proposed method cannot be assessed.  
- **Why it matters** The core contribution of the work is the proposed architecture. If the architecture and its lifelong learning component are not described, reviewers and readers cannot evaluate whether the method is sound, reproducible, or genuinely novel.  
- **Resolution test** Provide a detailed description of the network architecture, the lifelong learning mechanism (e.g., regularization, replay, or parameter isolation), and the feature fusion strategy in the full manuscript.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The model is superior to other approaches in terms of single-sample specificity (81.0%, 83.0%) and single-sample sensitivity (82.4%, 90.7%), and achieves high accuracy on the benchmark dataset (88.4%, 80.0%, and 76.6%).  
- **Evidence pointer** Abstract, "The findings demonstrated that the model used in this research was superior to other approaches"  
- **Concern** The reported performance metrics are presented without any statistical context. There are no confidence intervals, standard deviations, or significance tests comparing the proposed method to baselines. The claim of superiority is therefore unsupported.  
- **Why it matters** In machine learning and bioinformatics, performance differences can be due to random variation, dataset splits, or hyperparameter tuning. Without statistical validation, the reported improvements cannot be distinguished from noise.  
- **Resolution test** Report results across multiple runs with standard deviations, perform statistical significance tests (e.g., paired t-test or Wilcoxon signed-rank test) against baseline methods, and describe the experimental protocol in detail.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim Pointer** The researchers ran trials on three datasets and contrasted them with other classification techniques.  
- **Evidence pointer** Abstract, "The researchers ran trials on three datasets and contrasted them with other classification techniques"  
- **Concern** The abstract does not identify the three datasets, their sources, sizes, or how they were split into training and test sets. The baseline methods are also not named. This makes the results impossible to reproduce or verify.  
- **Why it matters** Reproducibility is a fundamental requirement for scientific claims. Without dataset details and baseline specifications, the reported results cannot be independently validated or compared to existing literature.  
- **Resolution test** Specify the datasets used, including accession numbers or download links, describe preprocessing and splitting procedures, and list all baseline methods with their configurations.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Novelty and contribution  
- **Claim pointer** This model offers a fresh perspective on the dichotomous classification problem in bioinformatics and broadens the application field of lifelong learning.  
- **Evidence pointer** Abstract, "This model offers a fresh perspective on the dichotomous classification problem in bioinformatics"  
- **Concern** The abstract does not explain what is novel about applying lifelong learning to this problem compared to existing deep learning methods. It is unclear whether lifelong learning provides a specific advantage for DNA binding protein prediction, such as handling new data over time or reducing catastrophic forgetting.  
- **Why it matters** The claimed novelty is central to the paper's contribution. If the advantage of lifelong learning is not articulated and demonstrated, the work may be seen as an incremental application of an existing technique without clear benefit.  
- **Resolution test** Clearly state the specific problem that lifelong learning solves in this context, provide a comparison to standard deep learning approaches without lifelong learning, and demonstrate the claimed advantage empirically.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, "Average Blocks, Discrete Cosine Transform, Discrete Wavelet Transform, Global encoding, Normalized Moreau-Broto Autocorrelation and Pseudo position-specific scoring matrix"  
- **Evidence pointer** Abstract, feature extraction methods list  
- **Issue** The feature extraction methods are listed without any explanation of what they capture or why they were chosen. This makes the abstract difficult to follow for readers not familiar with these specific techniques.  
- **Required correction** Provide a brief justification for each feature type or group them by category (e.g., sequence composition, physicochemical properties, evolutionary information) to improve readability.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Abstract, "single-sample specificity" and "single-sample sensitivity"  
- **Evidence pointer** Abstract, performance metrics  
- **Issue** The terms "single-sample specificity" and "single-sample sensitivity" are not standard in the bioinformatics literature. Standard terms are typically "specificity" and "sensitivity" or "recall." The intended meaning is unclear.  
- **Required correction** Use standard terminology or define these terms explicitly in the abstract.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Writing quality  
- **Affected element** Abstract, "The aforementioned methods are indeed more efficient than those based on manual classification, but there is still room for improvement in terms of prediction accuracy and speed."  
- **Evidence pointer** Abstract, introduction sentence  
- **Issue** The sentence is vague and does not specify which methods are being compared or what the specific limitations are. The phrase "manual classification" is also unclear in this context.  
- **Required correction** Rewrite the sentence to clearly state the limitations of existing methods and the specific gap the proposed approach addresses.

## Risk / unsupported claims
- The claim that the proposed model is "superior to other approaches" is unsupported because no baseline methods, statistical tests, or error bars are provided in the abstract.
- The claim that the model "offers a fresh perspective" and "broadens the application field of lifelong learning" is not substantiated with evidence of novelty or a clear articulation of the contribution.
- The reported accuracy values (88.4%, 80.0%, 76.6%) and specificity/sensitivity values are presented without context on dataset difficulty, class balance, or comparison to state-of-the-art results, making them unverifiable.
- The relationship between lifelong learning and the DNA binding protein prediction task is not explained, so the relevance of the lifelong learning framework is not assessable from the supplied material.