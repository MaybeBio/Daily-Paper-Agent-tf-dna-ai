## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific and technical evaluation of the presented method, results, and claims
- **Shared manuscript claim summary** The authors introduce seqgra, a deep learning pipeline for genomics that simulates biological sequence data using rule-based grammars, trains neural network architectures on these data, and evaluates models using both conventional metrics and feature attribution methods. They demonstrate its utility through ablation analysis and comparisons of popular genomics architectures, and validate a simulation-vetted architecture on experimental ChIP-seq data.
- **Visible evidence base** Main text including Methods, Results, Discussion, and figure descriptions; references to supplementary figures and tables
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; no quantitative results (e.g., AUC values, error bars) reported in the main text; no code or reproducibility details beyond availability statements

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful software framework for benchmarking neural network architectures in genomics using simulated data. The concept of combining rule-based simulation with model evaluation and feature attribution is sound and addresses a real need in the field. However, the main text lacks quantitative results, making it difficult to assess the strength of the claims. The validation on experimental data is described but not shown in sufficient detail. The manuscript would benefit from clearer presentation of key findings and a more critical discussion of limitations.
- **Who would be interested in the results, and why** Researchers developing or applying deep learning models to genomics sequence data, particularly those interested in model interpretability, architecture selection, and benchmarking. The framework could also be of interest to method developers working on feature attribution techniques, as it provides a controlled environment for evaluation.
- **Major strengths** The idea of using simulated data with known ground truth to evaluate both predictive performance and interpretability is timely and valuable. The framework is designed to be reproducible and supports multiple deep learning libraries. The inclusion of feature attribution methods as part of the evaluation pipeline is a notable strength, as interpretability is often neglected in benchmarking studies.
- **Major Concerns** The main text provides almost no quantitative results, making it impossible to evaluate the magnitude of the reported effects. The comparison of architectures is described qualitatively, and the validation on ChIP-seq data is not presented with sufficient detail. The claim that seqgra enables "principled selection" of architectures is not fully supported by the evidence shown.
- **Minor Comments** The manuscript would benefit from a more detailed description of the grammar specification language. The discussion of limitations is somewhat brief, particularly regarding the gap between simulated and real data. Some terminology (e.g., "grammar recovery") could be defined more clearly for nonspecialist readers.
- **Technical failings that need to be addressed before the case is established** The absence of quantitative results in the main text is a major technical shortcoming. The validation on experimental data is described but not shown, and the comparison of architectures lacks statistical rigor.
- **Assessment against Nature-style criteria** Originality: The concept of using rule-based simulation for benchmarking interpretability is not entirely new but is applied here in a comprehensive framework, which adds value. Scientific importance: The work addresses a genuine problem in genomics deep learning, but the impact is limited by the lack of demonstrated results. Interdisciplinary readership: The manuscript is likely to appeal to computational biologists and machine learning researchers, but the presentation may be too technical for a broader audience. Technical soundness: The framework appears well-designed, but the lack of quantitative evidence undermines confidence. Readability for nonspecialists: The manuscript is generally well-written but assumes familiarity with deep learning and genomics terminology.
- **Recommendation posture** Currently not established from the provided evidence. The framework has potential, but the manuscript needs to present quantitative results and a more rigorous validation to support its claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that seqgra can identify neural network architectures capable of recovering the rules of a hypothesized model of genome regulation, and that the DeepSEA architecture exhibited "at times substantially higher predictive performance" than others.
- **Evidence pointer** Section 3.3, Supplementary Figures S6A–D
- **Concern** The main text provides no quantitative results, such as AUC values, confidence intervals, or statistical comparisons. The claim that DeepSEA outperforms other architectures is based on visual inspection of supplementary figures that are not provided to the reviewer. Without numerical data, the reader cannot assess the magnitude or significance of the reported differences.
- **Why it matters** The central claim of the paper is that seqgra enables principled architecture selection. This claim cannot be evaluated without quantitative evidence. The absence of numbers in the main text is a critical omission that prevents the reader from drawing any conclusions about the framework's utility.
- **Resolution test** The authors should include key quantitative results in the main text, such as mean and standard deviation of AUC values across seeds, and ideally statistical tests comparing architectures. The supplementary figures should be referenced with specific values reported in the text.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation strength
- **Claim pointer** The authors state that a simulation-vetted architecture's high predictive performance is "recapitulated with ChIP-seq data" for SOX2 and POU5F1.
- **Evidence pointer** Section 3.4, Figures 3D–G
- **Concern** The validation on experimental data is described only qualitatively. No quantitative metrics (e.g., AUC, precision, recall) are reported for the experimental dataset, and the comparison between simulated and experimental performance is not shown numerically. The figures are described but not available for review.
- **Why it matters** The claim that simulation performance predicts experimental performance is a key contribution of the paper. Without quantitative evidence, the reader cannot verify this claim or assess its generalizability. The lack of detail also prevents replication.
- **Resolution test** The authors should report quantitative performance metrics for both simulated and experimental datasets, ideally in a comparative table or figure. They should also discuss any discrepancies between simulated and experimental performance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scope of claims
- **Claim pointer** The authors suggest that seqgra can be used to "analyze a model's predictive performance as a function of training set size and the complexity of the rules behind the simulated data."
- **Evidence pointer** Section 3.2, Figure 2D–E
- **Concern** The ablation analysis is described, but the results are not presented in sufficient detail. The claim that batch normalization has a "negative effect on efficiency" is based on a single figure, and the analysis is limited to one basic architecture. The generalizability of these findings to other architectures or grammars is unclear.
- **Why it matters** The paper positions seqgra as a tool for understanding how architecture choices affect performance. The current evidence is too limited to support broad conclusions about the effects of specific components like batch normalization.
- **Resolution test** The authors should expand the ablation analysis to include more architectures and grammars, and report quantitative results with error bars. They should also discuss the limitations of the specific architecture chosen for the analysis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Section 2.3
- **Issue** The term "grammar recovery" is used to describe the degree to which a model's decisions align with the rules used to simulate data. This term may be unclear to readers unfamiliar with the concept.
- **Required correction** Define "grammar recovery" explicitly when first introduced, and consider using a more descriptive term such as "rule recovery" or "feature alignment."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The authors state that data will be shared on reasonable request, but no details are given about the format or accessibility of the simulated datasets.
- **Required correction** Provide a more detailed data availability statement, including where the simulated datasets can be accessed (e.g., a repository) and in what format.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results section
- **Evidence pointer** Section 3.3
- **Issue** The comparison of DeepSEA, Basset, and ChromDragoNN is described in a single paragraph, with no discussion of why these specific architectures were chosen or how they differ in design.
- **Required correction** Add a brief description of the architectural differences between the three models and justify their selection as representative examples.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Section 4
- **Issue** The discussion of the gap between simulated and real data is brief and does not address potential strategies for mitigating this gap.
- **Required correction** Expand the discussion to include possible approaches for improving the transferability of insights from simulated to experimental data.

## Risk / unsupported claims
- The claim that seqgra enables "principled selection" of neural network architectures is not supported by the quantitative evidence presented in the main text.
- The claim that DeepSEA outperforms other architectures is based on unreferenced supplementary figures and lacks statistical support.
- The claim that simulation performance predicts experimental performance is not substantiated with quantitative results.
- The claim that batch normalization has a negative effect on training efficiency is based on a single, limited analysis.
- The generalizability of the findings to other grammars, architectures, and experimental conditions is not established.