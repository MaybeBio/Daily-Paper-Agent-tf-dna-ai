## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose a deep learning model, ISANREG, that combines block self-attention and attention-attribution mechanisms to predict transcription factor-bound motif instances and DNA-mediated TF-TF interactions, with interpretability at single-nucleotide resolution, overcoming memory and interpretability limitations of standard self-attention networks
- **Visible evidence base** Abstract text only; no quantitative results, model architecture details, dataset descriptions, or benchmark comparisons are available
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, training and evaluation details, baseline comparisons, and code availability

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach to a relevant problem in regulatory genomics, namely improving interpretability of deep learning models for TF binding and interaction prediction. However, the abstract lacks any quantitative evidence, methodological detail, or comparison to existing methods. The core claims of improved interpretability and predictive performance cannot be evaluated from the supplied material. The work may have merit, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, transcription factor binding prediction, and interpretable deep learning for biological sequences. Researchers developing attention-based models for genomics would also be interested in the block-attention and attribution mechanisms proposed.
- **Major strengths** The problem addressed is timely and important. The proposed combination of block self-attention and attention-attribution is a plausible approach to mitigate memory constraints and improve interpretability. The stated goal of single-nucleotide resolution interpretability is valuable for the field.
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
  - Originality: The combination of block self-attention with attention attribution for regulatory interaction prediction appears novel, but without methodological detail, the degree of novelty cannot be fully assessed.
  - Scientific importance: The problem of interpretable deep learning for regulatory genomics is of high importance, and the proposed framework could be impactful if validated.
  - Interdisciplinary readership: The topic bridges machine learning and molecular biology, which could attract a broad readership, but the abstract is too technical for nonspecialists without sufficient biological context.
  - Technical soundness: Not assessable from the abstract; no results, validation, or comparison to baselines are provided.
  - Readability for nonspecialists: The abstract is concise but uses jargon without adequate explanation, limiting accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient support for the core claims. A full manuscript with quantitative results and methodological detail is required for a fair assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The model "predicts transcription factor-bound motif instances and DNA-mediated TF-TF interactions using self-attention attribution scores"
- **Evidence pointer** Abstract only; location not provided
- **Concern** No quantitative results are presented. There are no performance metrics, no comparison to existing state-of-the-art models, and no validation on independent datasets. The claim that ISANREG successfully predicts these biological outcomes is unsupported.
- **Why it matters** Predictive performance is the central claim of the work. Without any numerical evidence, the reader cannot judge whether the model works at all, let alone whether it outperforms existing approaches.
- **Resolution test** Provide performance metrics such as AUROC, AUPRC, or accuracy on benchmark datasets, with comparisons to at least one or two established baseline models.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The model "combines both block self-attention and attention-attribution mechanisms" and "overcomes the limitations of previous deep learning models"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not describe how block self-attention is implemented, how attention attribution scores are computed, or how these components are integrated. The claim of overcoming memory limitations is plausible but not demonstrated with any architectural or computational details.
- **Why it matters** Without methodological detail, the novelty and technical soundness of the approach cannot be evaluated. The reader cannot assess whether the proposed mechanisms are sound or whether they indeed address the stated limitations.
- **Resolution test** Include a detailed methods section describing the architecture, the block attention mechanism, the attribution method, and a complexity analysis showing memory savings relative to standard self-attention.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability validation
- **Claim pointer** The model provides "interpretability of self-attention scores" and "interpreting the contribution of the input with single-nucleotide resolution"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract claims interpretability at single-nucleotide resolution but provides no evidence that the attribution scores are biologically meaningful. There is no demonstration that the identified nucleotides correspond to known binding sites or regulatory elements.
- **Why it matters** Interpretability claims are only valuable if the attributions are accurate and biologically relevant. Without validation against known ground truth, the interpretability claim is speculative.
- **Resolution test** Provide case studies or systematic evaluation showing that attribution scores highlight known TF binding motifs or regulatory variants, with quantitative agreement against ChIP-seq or other experimental data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "regulatory feature interactions" is used without definition. It is unclear whether this refers to TF-TF interactions, motif co-occurrence, or something else.
- **Required correction** Define the term explicitly in the abstract or introduction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Model name
- **Evidence pointer** Abstract; location not provided
- **Issue** The model name ISANREG is introduced as an acronym for "Interpretable Self-Attention Network for REGulatory interactions," but the abstract title uses "block-attention network." This inconsistency may confuse readers.
- **Required correction** Align the terminology between the title and the abstract, or explain the relationship between the two names.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Related work
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract mentions "previous deep learning models" but does not name any. This makes it difficult to contextualize the claimed improvements.
- **Required correction** Cite and briefly describe one or two representative prior models to establish the baseline for comparison.

## Risk / unsupported claims
- The claim that ISANREG "overcomes the limitations of previous deep learning models" is unsupported without comparative results.
- The claim of "single-nucleotide resolution" interpretability is unsupported without validation against experimental data.
- The claim that the model "predicts transcription factor-bound motif instances and DNA-mediated TF-TF interactions" is unsupported without any performance metrics.
- The general statement that ISANREG "will serve as a framework for other biological models" is speculative and not substantiated.