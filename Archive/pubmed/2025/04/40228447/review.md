## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report an in silico analysis of BCOR fusion proteins in BCOR-rearranged sarcomas (BRS), covering domain architecture, disorder prediction, physicochemical properties, and AlphaFold3-based structural modeling with PRODIGY binding affinity calculations. They claim significant alterations in domain architecture, loss of BCL6-regulated transcriptional repression, increased C-terminal disorder, decreased isoelectric point/stability/hydrophobicity, and statistically significant deviations in binding affinities for BCOR-PCGF1 dimers and a non-canonical PRC1 variant tetramer. They further claim this is the first compilation and comparative analysis of known BCOR fusions in BRS and introduce a new in silico approach.
- **Visible evidence base** Abstract text only; no figures, tables, methods, statistical details, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, statistical analysis details, AlphaFold3 prediction parameters, PRODIGY algorithm settings, sequence accession numbers, and validation data

## Reviewer
- **Overall assessment** The abstract presents a potentially useful computational survey of BCOR fusion proteins in BRS, a rare sarcoma subtype. The topic is of interest to the sarcoma and structural biology communities. However, the abstract alone provides insufficient detail to evaluate the technical rigor of the in silico methods, the statistical claims, or the biological significance of the findings. Several claims appear plausible but are not verifiable from the supplied material. The novelty claim of "first compilation" is difficult to assess without a literature comparison. The study may represent a reasonable contribution to the field, but the evidence base provided is too limited to establish the case.
- **Who would be interested in the results, and why** Researchers in sarcoma genetics and molecular pathology, particularly those studying BCOR-rearranged tumors, would be interested in a systematic comparison of fusion variants. Structural biologists working on Polycomb Repressive Complex 1 and protein-protein interaction prediction may also find the AlphaFold3-based approach relevant. Clinicians and diagnostic pathologists might benefit from a clearer understanding of fusion protein consequences, though the translational relevance is not yet demonstrated.
- **Major strengths** The abstract addresses a clinically relevant and understudied topic. The systematic inclusion of multiple BCOR fusion partners is a useful framing. The combination of multiple in silico tools (IUPred3, ProtParam, AlphaFold3, PRODIGY) suggests a comprehensive approach. The focus on both domain architecture and binding affinity provides a multi-level analysis.
- **Major Concerns** The abstract lacks methodological detail, making the statistical claims unverifiable. The biological interpretation of the predicted changes is not sufficiently justified. The novelty claim is not substantiated.
- **Minor Comments** The abstract would benefit from clearer specification of the number of fusion variants analyzed, the statistical tests used, and the magnitude of the reported changes. The phrase "non-canonical PRC1 variant tetramer" is vague and should be specified.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: The compilation of BCOR fusions may be novel, but the abstract does not demonstrate this against existing literature. Scientific importance: The topic is relevant but the significance of the findings for understanding BRS oncogenesis is not established. Interdisciplinary readership: The abstract is accessible to computational biologists and sarcoma researchers, but the lack of biological validation limits broader appeal. Technical soundness: Cannot be assessed from the abstract alone; the statistical claims require full methods. Readability for nonspecialists: The abstract is reasonably clear but uses specialized terminology without sufficient context.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** "statistically significant deviations in binding affinities for BCOR-PCGF1 dimers and a non-canonical PRC1 variant tetramer compared to the wild-type BCOR"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract reports statistically significant deviations in binding affinities but provides no information on the statistical test used, sample sizes, effect sizes, confidence intervals, or multiple testing corrections. The number of fusion variants compared and the number of independent predictions per variant are not stated.
- **Why it matters** Without this information, the statistical claim cannot be evaluated. In silico binding affinity predictions are known to be sensitive to methodological choices, and the significance of small differences may be overstated without proper controls.
- **Resolution test** Provide the full statistical analysis in the methods, including the test used, the number of comparisons, the distribution of predicted affinities, and a clear statement of what constitutes a meaningful difference in this context.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological interpretation
- **Claim pointer** "significant alterations in the domain architecture of BCOR, which resulted in the loss of BCL6-regulated transcriptional repression"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The claim that domain alterations result in loss of BCL6-regulated transcriptional repression is a functional conclusion drawn from structural predictions. The abstract does not describe how this functional loss is inferred from domain architecture changes, nor does it provide any experimental or literature-based support for this causal link.
- **Why it matters** This is a central mechanistic claim of the study. If the inference is purely based on domain loss, it may be an oversimplification, as fusion proteins can retain partial function or acquire new interactions. The claim as stated goes beyond what structural prediction alone can establish.
- **Resolution test** Clarify the inference chain from domain architecture to functional loss, and either provide supporting literature or temper the claim to reflect that this is a predicted consequence requiring experimental validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and scope
- **Claim pointer** "we provide the first compilation and comparative analysis of the known BCOR fusions of BRS"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The novelty claim of "first compilation" is not verifiable from the abstract. No comparison with existing reviews or databases is provided, and the criteria for inclusion of fusions are not stated.
- **Why it matters** If prior compilations exist, the novelty claim would be overstated. The claim also implies a comprehensive scope that cannot be assessed without knowing the search strategy and inclusion criteria.
- **Resolution test** Provide a literature search summary and a table of all known BCOR fusions with references, and explicitly state how this compilation differs from prior work.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods description
- **Evidence pointer** Abstract only; location not provided
- **Issue** The abstract does not specify how many fusion variants were analyzed or which specific fusions beyond BCOR::CCNB3 were included in the structural predictions.
- **Required correction** State the number of fusion variants analyzed and list all fusion partners included in the computational pipeline.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "non-canonical PRC1 variant tetramer"
- **Evidence pointer** Abstract only; location not provided
- **Issue** This term is vague and could refer to multiple possible assemblies. The composition of the tetramer is not specified.
- **Required correction** Specify the exact subunit composition of the tetramer modeled and the rationale for choosing this assembly.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reporting
- **Affected element** Physicochemical properties
- **Evidence pointer** Abstract only; location not provided
- **Issue** The abstract reports decreases in isoelectric point, stability, and hydrophobicity but does not indicate the magnitude of these changes or whether they are consistent across all fusion variants.
- **Required correction** Provide quantitative values or ranges for the reported changes and note any variant-specific differences.

## Risk / unsupported claims
- The claim of "loss of BCL6-regulated transcriptional repression" is a functional conclusion not supported by the abstract's evidence.
- The claim of "statistically significant deviations in binding affinities" is unverifiable without statistical details.
- The claim of "first compilation" of BCOR fusions is unsubstantiated without a literature comparison.
- The overall suggestion that the findings "contribute to the oncogenic mechanisms underlying BRS" is an interpretive leap not supported by the abstract alone.
- The "new in silico approach" claim is not defined clearly enough to assess its novelty.