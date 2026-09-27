## Review setup

- **Input scope** Abstract and metadata only. The provided material is the arXiv landing page for the manuscript, containing the title, author list, submission date, DOI, and abstract text. No full text, figures, tables, or supplementary materials were supplied.
- **Assessment boundary** This review is limited to the claims and evidence visible in the abstract and the bibliographic record. Any assessment of methodology, results, or reproducibility is constrained by the absence of the manuscript body.
- **Shared manuscript claim summary** The manuscript proposes Motif-Vocab, a tokenization method for genomic language models that uses statistically calibrated transcription-factor-identity motifs. The central claim is that this approach improves the performance of genomic language models by incorporating transcription-factor binding specificity into the token vocabulary.
- **Visible evidence base** Abstract text only. No figures, tables, methods sections, or results are available for inspection.
- **Missing materials affecting confidence** Full manuscript text, all figures and tables, methods description, code availability statement, and any supplementary information. Without these, the technical validity of the statistical calibration and the reported performance improvements cannot be assessed.

## Reviewer

- **Overall assessment** The abstract presents a conceptually interesting idea, namely the integration of transcription-factor identity into tokenization for genomic language models. However, the abstract is too brief to establish the technical soundness of the approach. Key details on the statistical calibration method, the tokenization algorithm, the model architecture, and the evaluation benchmarks are absent. The claim of improved performance is stated without quantitative support. The work may be of interest to the computational genomics community, but the current evidence base is insufficient to evaluate its validity or significance.
- **Who would be interested in the results, and why** Researchers in computational genomics, particularly those working on genomic language models, regulatory genomics, and transcription-factor binding site prediction. The approach could also interest machine learning researchers focused on domain-specific tokenization strategies for biological sequences.
- **Major strengths** The idea of using transcription-factor identity as a tokenization principle is novel and addresses a real limitation of current genomic language models, which typically rely on k-mer or byte-pair encoding without biological semantics. The statistical calibration aspect suggests a principled approach to motif selection, which is a positive signal.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract claims that Motif-Vocab provides statistically calibrated transcription-factor-identity tokenization that improves genomic language model performance.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not describe the statistical calibration method. It is unclear what statistical model or test is used to select motifs, how motif boundaries are defined, how overlapping or redundant motifs are handled, and how the token vocabulary size is determined. Without this information, the technical validity of the approach cannot be assessed.
  - **Why it matters** The core novelty of the work rests on the statistical calibration of motif tokens. If the calibration method is flawed or ad hoc, the entire approach loses its claimed advantage over existing tokenization schemes.
  - **Resolution test** The full manuscript must provide a detailed description of the calibration procedure, including the statistical model, the null hypothesis, the significance threshold, and the handling of motif redundancy. The method should be reproducible from the description alone.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The abstract implies that Motif-Vocab improves genomic language model performance, but no quantitative results are provided.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract states that the method improves performance but does not report any numerical results, benchmark datasets, or comparison baselines. It is impossible to judge the magnitude of the improvement, the statistical significance, or the generalizability of the findings.
  - **Why it matters** A performance claim without supporting data is not verifiable. The scientific value of the work depends on demonstrating that the improvement is real, consistent, and meaningful relative to existing methods.
  - **Resolution test** The full manuscript must include evaluation results on at least one standard benchmark, with clear baselines, error bars, and statistical tests. The improvement should be shown to be robust across multiple datasets or tasks.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The abstract implies that the method is a complete and usable tokenization approach for genomic language models.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** No information is provided on code availability, data availability, or implementation details. The abstract does not mention whether the software is open source, whether the training data are publicly accessible, or whether the model can be run on standard hardware.
  - **Why it matters** Reproducibility is a core requirement for computational biology research. Without code or data, other groups cannot validate the method or build on it.
  - **Resolution test** The manuscript should include a data and code availability statement, and ideally a public repository with the implementation and instructions for use.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract wording
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The term "statistically calibrated" is used without definition. It is unclear whether this refers to p-value calibration, probability calibration, or some other statistical procedure.
  - **Required correction** Define the term explicitly in the abstract or provide a reference to the statistical framework used.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Scope
  - **Affected element** Evaluation scope
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract does not specify which genomic language models were tested or which downstream tasks were used for evaluation.
  - **Required correction** State the model architectures and the specific tasks (for example, promoter prediction, splice site detection, chromatin accessibility) in the abstract.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Context
  - **Affected element** Related work
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract does not mention existing tokenization methods for genomic language models, such as k-mer based or byte-pair encoding approaches, or how Motif-Vocab compares to them conceptually.
  - **Required correction** Add a sentence in the abstract that situates the method relative to existing tokenization strategies.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The statistical calibration method must be fully described and the performance claims must be supported with quantitative evidence. R1-M3 is non-blocking but should be addressed for reproducibility.
- **Assessment against Nature-style criteria**  
  Originality: The concept of using transcription-factor identity for tokenization is original and not a trivial extension of existing methods. However, the abstract does not demonstrate that the approach is fundamentally different from motif-based feature engineering used in earlier genomic models.  
  Scientific importance: If the performance claims hold, the method could improve the utility of genomic language models for regulatory genomics. The importance is plausible but not established from the abstract alone.  
  Interdisciplinary readership: The work sits at the intersection of genomics and machine learning, which is a broad readership. The abstract is accessible to both communities, though the lack of technical detail limits its appeal.  
  Technical soundness: Not assessable from the abstract. The statistical calibration and evaluation methodology are not described.  
  Readability for nonspecialists: The abstract is concise and uses standard terminology, but the key concept of "statistically calibrated" is not explained, which may confuse readers outside the immediate field.
- **Recommendation posture** Currently not established from the provided evidence. The idea is promising, but the abstract alone does not provide sufficient technical detail or quantitative support to assess the validity of the claims. A full review of the manuscript would be required to determine whether the approach is sound and the results are significant.

## Risk / unsupported claims

- The claim that Motif-Vocab improves genomic language model performance is unsupported by any quantitative data in the provided material.
- The claim that the tokenization is "statistically calibrated" is unverifiable without a description of the calibration method.
- Any claim regarding the novelty or superiority of the approach relative to existing tokenization methods cannot be evaluated from the abstract alone.