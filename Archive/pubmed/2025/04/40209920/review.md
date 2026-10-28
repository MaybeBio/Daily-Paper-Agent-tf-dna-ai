## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors review computational methods for protein-DNA binding site prediction, categorize them into template detection, statistical machine learning, and deep learning-based approaches, benchmark 14 state-of-the-art models on 136 non-redundant proteins, report that deep learning-based methods, especially pre-trained large language model-based ones, outperform the other categories, and discuss applications of these methods.
- **Visible evidence base** Abstract text only; no methodological details, benchmark results, or application examples are provided
- **Missing materials affecting confidence** Full manuscript, benchmark dataset details, model specifications, performance metrics, statistical analyses, and application case studies are not available

## Reviewer
- **Overall assessment** The abstract presents a timely and potentially useful review of computational methods for protein-DNA binding site prediction, with a clear categorization and a comparative benchmark claim. However, the abstract alone provides insufficient detail to evaluate the rigor of the review methodology, the validity of the benchmark, or the strength of the performance conclusions. The claim that deep learning-based methods, particularly pre-trained large language model-based ones, achieve superior performance is plausible but not verifiable from the supplied material. The scope is relevant to a broad computational biology audience, but the evidence base is too limited to establish the case.
- **Who would be interested in the results, and why** Computational biologists, bioinformaticians, and researchers in protein-nucleic acid interactions would be interested in this review as a consolidated resource for method selection and benchmarking. Developers of prediction tools may also find the comparative performance insights useful for guiding future model design, particularly regarding the adoption of large language model-based approaches.
- **Major strengths** The abstract addresses a practically important problem with clear translational relevance to drug discovery. The categorization of methods into three major classes provides a structured framework for readers. The inclusion of a benchmark on 136 non-redundant proteins suggests an effort toward objective comparison, which is valuable in a field with many disparate evaluation protocols.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract claims that 14 state-of-the-art models were benchmarked on 136 non-redundant proteins and that deep learning-based, especially pre-trained large language model-based, methods achieve superior performance.
  - **Evidence pointer** Abstract only; location not provided
  - **Concern** The abstract provides no details on the benchmark protocol, including dataset construction, evaluation metrics, statistical significance testing, or model training and inference settings. Without this information, the comparative performance claim cannot be assessed for fairness or robustness.
  - **Why it matters** Benchmarking claims in method reviews are only meaningful if the evaluation is unbiased and reproducible. If the benchmark lacks proper controls, such as cross-validation or independent test sets, the reported superiority of deep learning methods may be an artifact of dataset characteristics or model tuning.
  - **Resolution test** The full manuscript must provide a detailed description of the benchmark setup, including dataset sources, redundancy reduction criteria, evaluation metrics, and statistical comparisons. The performance differences should be accompanied by confidence intervals or significance tests to support the claim of superiority.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract uses terms such as "template detection" and "pre-trained large language model-based" without brief definitions, which may reduce accessibility for readers outside the immediate computational biology field.
  - **Required correction** Add a short parenthetical explanation for each method category, for example, "template detection (methods that match query proteins to known DNA-binding structures)" and "pre-trained large language model-based (methods using models pre-trained on large protein sequence corpora)."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Applications section
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions that applications of these methods are involved, but provides no examples or context, making it unclear what specific applications are covered and how they relate to the benchmark findings.
  - **Required correction** Specify at least one or two representative application areas, such as variant effect prediction or drug target identification, and briefly indicate how the reviewed methods are used in those contexts.
- **Technical failings that need to be addressed before the case is established** R1-M1 is the primary technical failing. The benchmark claim is central to the review's value, and without detailed methodological transparency, the case for deep learning superiority is not established.
- **Assessment against Nature-style criteria** Originality: The review appears to consolidate existing methods, but the abstract does not indicate a novel conceptual framework or new insights beyond categorization, so originality is moderate. Scientific importance: The problem is important, and a rigorous benchmark could be highly valuable, but the abstract does not demonstrate that the benchmark is sufficiently comprehensive or well-controlled. Interdisciplinary readership: The topic bridges computational biology and molecular biology, but the abstract's technical density may limit appeal to experimentalists. Technical soundness: Not assessable from the abstract due to missing benchmark details. Readability for nonspecialists: The abstract is generally clear but lacks brief definitions for method categories, as noted in R1-m1.
- **Recommendation posture** Currently not established from the provided evidence. The review topic is relevant and the benchmark idea is promising, but the abstract alone does not provide enough methodological detail to support the central performance claim. A revised manuscript with full benchmark transparency and statistical rigor could change this assessment.

## Risk / unsupported claims
- The claim that deep learning-based methods, especially pre-trained large language model-based ones, achieve superior performance over template detection and statistical machine learning methods is unsupported from the abstract alone, as no benchmark details or results are provided.
- The claim that the review covers "major computational approaches" is not verifiable, as the abstract does not specify the scope of literature search or inclusion criteria.
- The claim that applications of these methods are involved is unassessable, as no specific applications are described.