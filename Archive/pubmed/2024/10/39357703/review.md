## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose PDNAPred, a sequence-based method combining two pre-trained protein language models with a CNN-GRU network and focal loss, to predict protein-DNA binding sites. They claim improved accuracy over existing sequence-based methods, comparability to structure-based methods, generalizability to RNA-binding site prediction, and interpretability of model performance.
- **Visible evidence base** Abstract text only; no quantitative results, dataset descriptions, or methodological details provided
- **Missing materials affecting confidence** Full methods, experimental setup, benchmark datasets, evaluation metrics, comparison baselines, statistical significance tests, and interpretability analysis details are not available

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially useful computational approach to a well-recognized problem in protein function annotation. The combination of pre-trained protein language models with a CNN-GRU architecture and focal loss is methodologically reasonable, and the claim of generalizability to RNA-binding sites is interesting. However, the abstract lacks quantitative evidence, dataset specifications, and comparison details, making it impossible to evaluate the strength of the reported improvements or the validity of the comparability claims. The interpretability claim is stated without any indication of what analysis was performed or what insights were obtained.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those developing sequence-based methods for binding site annotation. Researchers interested in applying pre-trained language models to biological sequence analysis tasks would also find the approach relevant. The potential generalizability to RNA-binding sites broadens the appeal to researchers studying nucleic acid-protein interactions more generally.
- **Major strengths** The problem addressed is important and timely, given the gap between sequence availability and functional annotation. The use of pre-trained protein language models is current and aligns with state-of-the-art trends in the field. The explicit handling of class imbalance through focal loss shows methodological awareness. The claim of generalizability to RNA-binding sites suggests a potentially broader impact beyond DNA-binding prediction.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The combination of two pre-trained language models with a CNN-GRU architecture is incremental rather than conceptually novel, though the specific configuration may offer practical advantages. Scientific importance: The problem is significant, but the abstract does not demonstrate a substantial advance over existing methods without quantitative evidence. Interdisciplinary readership: The work is primarily of interest to computational biologists; the abstract does not articulate broader implications for experimental biology or drug discovery beyond a general statement. Technical soundness: Cannot be assessed from the abstract alone; the absence of methodological details and evaluation metrics precludes judgment. Readability for nonspecialists: The abstract is generally clear, though terms such as CNN-GRU and focal loss are used without explanation, which may limit accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially useful method, but the absence of quantitative results and methodological details prevents assessment of whether the core claims are supported.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "PDNAPred significantly improved the accuracy of DNA-binding site prediction, outperforming existing state-of-the-art sequence-based methods"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract claims significant improvement over state-of-the-art sequence-based methods but provides no quantitative metrics, such as Matthews correlation coefficient, area under the ROC curve, or F1 score, and no comparison table or statistical significance values.  
- **Why it matters** Without specific performance numbers and statistical tests, the claim of significant improvement cannot be verified. The magnitude of improvement and the specific baselines used are essential for assessing whether the advance is meaningful.  
- **Resolution test** Provide performance metrics on standard benchmark datasets with confidence intervals or statistical significance tests, and specify which existing methods were used as comparators.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "PDNAPred also achieved results comparable to advanced structure-based methods"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The claim of comparability to structure-based methods is stated without any supporting data. It is unclear which structure-based methods were compared, on which datasets, and what metric was used to establish comparability.  
- **Why it matters** Structure-based methods typically have an advantage due to additional information. A claim of comparable performance is strong and requires explicit evidence, including the specific methods, datasets, and evaluation criteria.  
- **Resolution test** Provide a direct comparison table with structure-based methods on the same benchmark datasets, including the metric used and a clear definition of what constitutes comparability.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "We conducted model interpretability analysis to elucidate the reasons behind PDNAPred's outstanding performance"  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract mentions interpretability analysis but gives no indication of what analysis was performed, what biological or methodological insights were obtained, or how the analysis supports the claim of outstanding performance.  
- **Why it matters** Interpretability is a stated contribution of the work. Without any description of the analysis or its findings, this claim is unverifiable and does not add to the scientific value of the study as presented.  
- **Resolution test** Describe the interpretability method used, present representative results, and explain how these results provide insight into the model's predictions or biological relevance.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Method description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract states that two pre-trained protein language models are combined but does not specify which models were used.  
- **Required correction** Name the specific pre-trained models to allow readers to understand the methodological choices and reproducibility.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Dataset description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No information is provided about the training and evaluation datasets, including their size, source, or how they were split.  
- **Required correction** Specify the datasets used for training and testing, including the number of proteins and binding site annotations, and describe the data splitting strategy.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Generalizability claim  
- **Affected element** RNA-binding site validation  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The claim of generalizability to RNA-binding sites is mentioned in a single sentence without any details on the datasets, performance, or comparison to RNA-specific methods.  
- **Required correction** Provide at least a brief summary of the RNA-binding site prediction results, including datasets and performance metrics, to support the generalizability claim.

## Risk / unsupported claims
- The claim of significant improvement over state-of-the-art sequence-based methods is unsupported without quantitative results.
- The claim of comparability to structure-based methods is unsupported without comparison data.
- The claim of generalizability to RNA-binding sites is unsupported without experimental details.
- The interpretability claim is unsupported without any description of the analysis performed.
- The statement that PDNAPred is applicable to large-scale prediction tasks is not substantiated with runtime or scalability data.