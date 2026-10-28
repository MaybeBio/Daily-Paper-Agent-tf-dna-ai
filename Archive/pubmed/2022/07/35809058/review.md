## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract, as supplied
- **Shared manuscript claim summary** The authors propose iHMnBS, a deep learning multi-objective method to identify which of seven histone modifications a DNA sequence may bind and which parts of the sequence bind them, using a customized dataset and outperforming a baseline, with potential utility for biological experiments and disease relevance via transcription factor binding patterns.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or supplementary data provided
- **Missing materials affecting confidence** Full manuscript, methods description, dataset construction details, baseline definition, performance metrics, statistical tests, code verification, and supplementary data

## Reviewer
- **Overall assessment** The abstract presents a potentially useful computational approach for histone modification binding prediction, but the evidence provided is insufficient to evaluate technical soundness, reproducibility, or the strength of the claimed improvements. The claims are broad and lack quantitative support, and the baseline comparison is not described in enough detail to assess fairness or significance.
- **Who would be interested in the results, and why** Researchers in epigenomics and computational biology, particularly those working on histone modification prediction, deep learning applications to genomics, and integrative analysis of transcription factor interactions. The potential link to disease relevance may interest translational bioinformatics groups.
- **Major strengths** The idea of jointly learning multiple binding sites and modification types is conceptually interesting. The availability of source code is a positive step for reproducibility. The focus on a customized dataset with positional binding information could offer a richer training signal than conventional approaches.
- **Major Concerns**  
  - **Concern ID** R1-M1  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Technical soundness  
    **Claim pointer** "iHMnBS outperforms a baseline method"  
    **Evidence pointer** Abstract, Results section; location not provided  
    **Concern** The abstract states that iHMnBS outperforms a baseline method, but no details are given about the baseline, the evaluation metrics, the datasets used for comparison, or whether the improvement is statistically significant.  
    **Why it matters** Without a clear baseline and quantitative results, the claimed superiority cannot be assessed or reproduced. This is central to the paper's contribution.  
    **Resolution test** Provide a detailed description of the baseline, evaluation protocol, metrics, and statistical tests in the full manuscript, with results shown in tables or figures.  
  - **Concern ID** R1-M2  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Reproducibility  
    **Claim pointer** "iHMnBS employs a customized dataset that allows the marking of modifications contained in histones that may bind to any position in the DNA sequence"  
    **Evidence pointer** Abstract, Methods; location not provided  
    **Concern** The construction of the customized dataset is not described. It is unclear how the data were generated, labeled, or validated, and whether the dataset is publicly available.  
    **Why it matters** The novelty of the approach depends on this dataset design. Without details, the method cannot be reproduced or compared fairly with existing benchmarks.  
    **Resolution test** Describe dataset construction, labeling rules, sources, and availability in the full manuscript or supplementary materials.  
  - **Concern ID** R1-M3  
    **Severity** Major  
    **Blocking** No  
    **Axis** Claim support  
    **Claim pointer** "the probability of binding to modified histones assigned to a representative nucleotide of a DNA sequence can serve as a reference for biological experiments"  
    **Evidence pointer** Abstract, Results; location not provided  
    **Concern** This claim suggests practical utility, but no experimental validation or case study is presented in the abstract.  
    **Why it matters** The claim implies biological relevance beyond computational prediction, which requires external validation or at least a demonstration of predictive accuracy on independent data.  
    **Resolution test** Provide validation experiments, case studies, or comparisons with experimental data in the full manuscript.  
  - **Concern ID** R1-M4  
    **Severity** Major  
    **Blocking** No  
    **Axis** Interdisciplinary relevance  
    **Claim pointer** "we extracted a number of sequence patterns that may bind to transcription factors, and explored their possible impact on disease"  
    **Evidence pointer** Abstract, Results; location not provided  
    **Concern** The disease relevance is mentioned but not substantiated with any specific findings, disease types, or statistical associations.  
    **Why it matters** This claim broadens the impact but is currently unverifiable from the abstract.  
    **Resolution test** Include specific results, such as enriched disease-associated variants or pathways, with supporting statistics in the full manuscript.

- **Minor Comments**  
  - **Concern ID** R1-m1  
    **Severity** Minor  
    **Axis** Clarity  
    **Affected element** Abstract, Results  
    **Evidence pointer** Abstract; location not provided  
    **Issue** The phrase "which parts of the DNA sequence bind to them" is ambiguous regarding whether the model outputs base-level or region-level predictions.  
    **Required correction** Clarify the output granularity in the abstract.  
  - **Concern ID** R1-m2  
    **Severity** Minor  
    **Axis** Completeness  
    **Affected element** Abstract, Availability  
    **Evidence pointer** Abstract; location not provided  
    **Issue** The source code link is provided, but no version, license, or dependency information is mentioned.  
    **Required correction** Specify the software version, license, and key dependencies in the abstract or supplementary.  
  - **Concern ID** R1-m3  
    **Severity** Minor  
    **Axis** Terminology  
    **Affected element** Abstract, Motivation  
    **Evidence pointer** Abstract; location not provided  
    **Issue** The term "jointly learning technology" is vague and not standard in the field.  
    **Required correction** Replace with a more precise term such as "multi-task learning" or "joint multi-label classification."

- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The lack of baseline details and dataset description prevents any assessment of the core methodological contribution. R1-M3 and R1-M4 are non-blocking but require additional evidence to support the broader claims.

- **Assessment against Nature-style criteria**  
  - **Originality** The idea of joint learning across multiple binding sites and modification types is somewhat novel, but the abstract does not clearly differentiate it from existing multi-task or multi-label deep learning approaches in epigenomics.  
  - **Scientific importance** Histone modification prediction is an active and important area, but the abstract does not demonstrate a significant advance over current state of the art.  
  - **Interdisciplinary readership** The abstract is written for a bioinformatics audience and may not be accessible to experimental biologists or clinicians without additional context.  
  - **Technical soundness** Not assessable from the abstract due to missing methodological and evaluation details.  
  - **Readability for nonspecialists** The abstract is concise but uses jargon without sufficient explanation, limiting accessibility.

- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide enough information to support the claims of improved performance or biological utility. A full manuscript with detailed methods, results, and validation would be required for a supportive assessment.

## Risk / unsupported claims
- The claim of outperforming a baseline is unsupported without baseline details or metrics.
- The claim that predicted probabilities can serve as a reference for biological experiments is unsupported without validation.
- The claim of exploring disease impact is unsupported without specific findings.
- The novelty and effectiveness of the customized dataset are unassessable without dataset description.