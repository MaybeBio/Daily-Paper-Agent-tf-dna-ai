## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to figures, tables, methods, or supplementary materials
- **Shared manuscript claim summary** The authors generated whole-body single-cell transcriptomic atlases for zebrafish, Drosophila, and earthworm; integrated these with existing atlases from eight metazoan species; developed a deep-learning tool named Nvwa to predict gene expression and identify regulatory sequences at single-cell resolution; and used cross-species comparisons of cell-type-specific transcription factors to infer conserved regulatory programs.
- **Visible evidence base** Abstract text only; no methodological details, validation metrics, or data availability statements are provided
- **Missing materials affecting confidence** Full methods, all figures and tables, supplementary analyses, benchmarking of Nvwa, details of the eight-species integration, and any statistical or computational validation

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially valuable resource for cross-species single-cell genomics and regulatory genomics. The core claims, however, are stated without quantitative support or methodological transparency. The deep-learning model Nvwa is described only in passing, and no performance metrics, benchmarking against existing tools, or validation of regulatory sequence predictions are provided. The claim of conserved regulatory programs is plausible but not substantiated in the abstract. The work is likely of interest to a broad community, but the evidence base as presented is insufficient to evaluate technical soundness or the strength of the biological conclusions.
- **Who would be interested in the results, and why** Researchers in single-cell genomics, comparative genomics, regulatory genomics, and computational biology would be interested. The resource of whole-body atlases for three non-model species and the integration across eight metazoan species could serve as a reference for evolutionary studies. The deep-learning approach for predicting gene expression and regulatory sequences may appeal to those developing or applying machine learning in genomics.
- **Major strengths** The scope of generating whole-body single-cell atlases for three species and integrating them with existing data across eight metazoan species is substantial and could provide a valuable community resource. The focus on conserved regulatory programs across evolution addresses a fundamental question in biology. The development of a deep-learning strategy for single-cell-level regulatory prediction is timely and potentially impactful.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The combination of new whole-body atlases for three species, integration across eight metazoan species, and a deep-learning model for regulatory prediction is original in scope. However, the abstract does not clarify how Nvwa differs from existing deep-learning methods for gene expression prediction or regulatory sequence identification.  
  Scientific importance: The potential to identify conserved regulatory programs across evolution is scientifically important, but the abstract does not provide evidence that such programs are actually identified or validated.  
  Interdisciplinary readership: The work bridges genomics, evolution, and machine learning, which could attract a broad readership. The abstract is accessible but lacks technical detail that would allow specialists to assess the claims.  
  Technical soundness: Not assessable from the abstract. No metrics, benchmarks, or validation are provided for Nvwa or the cross-species integration.  
  Readability for nonspecialists: The abstract is clearly written and understandable, but the lack of context on the deep-learning approach and the nature of the conserved programs limits comprehension of the significance.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes an ambitious project, but the core claims regarding Nvwa's performance and the identification of conserved regulatory programs require substantial additional evidence. A supportive posture would be possible if the full manuscript provides rigorous validation and benchmarking.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that Nvwa can "predict gene expression and identify regulatory sequences at the single-cell level."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** No performance metrics, benchmarking against existing methods, or validation of predictions are presented. It is unclear how Nvwa was trained, what input features were used, how accuracy was measured, or whether predictions were experimentally or computationally validated.  
- **Why it matters** The central methodological contribution of the paper is Nvwa. Without evidence of its accuracy, robustness, or superiority over existing tools, the claim that it provides a "new strategy" is unsupported.  
- **Resolution test** Provide quantitative benchmarks of Nvwa against established methods for gene expression prediction and regulatory sequence identification, including metrics such as correlation, area under the curve, or precision-recall, and demonstrate validation on held-out or independent datasets.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence strength  
- **Claim pointer** The authors claim that they "systematically compared cell-type-specific transcription factors to reveal conserved genetic regulation in vertebrates and invertebrates."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not specify which transcription factors were compared, how conservation was defined, or what evidence supports the claim of conserved regulation. No examples of conserved programs are given, and no statistical framework for the comparison is described.  
- **Why it matters** The biological conclusion of conserved regulatory programs is a key outcome of the study. Without details on the comparison method and results, the claim is not verifiable.  
- **Resolution test** Describe the criteria for identifying cell-type-specific transcription factors, the statistical tests used to assess conservation across species, and provide specific examples of conserved regulatory programs with supporting evidence.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The authors state that they "integrated cell landscapes from eight representative metazoan species."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not describe how the integration was performed, which species were included beyond the three newly generated atlases, how batch effects or technical differences were handled, or how the quality of integration was assessed.  
- **Why it matters** Cross-species integration is technically challenging, and the validity of downstream comparisons depends on the quality of this integration. Without details, the reliability of the integrated landscapes is unknown.  
- **Resolution test** Provide a detailed description of the integration pipeline, including normalization, batch correction, and quality control metrics, and show that the integrated data preserve biological signal across species.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Resource availability  
- **Claim pointer** The authors imply that the whole-body atlases and integrated landscapes constitute a "valuable resource."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** No information is given on data availability, accession numbers, or whether the atlases and Nvwa code will be publicly released.  
- **Why it matters** For a resource paper, accessibility is critical for the community to use and validate the data and tools.  
- **Resolution test** State data availability and provide accession numbers or a repository link for the atlases and the Nvwa software.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The phrase "regulatory grammar" is vague and not defined.  
- **Required correction** Define what is meant by regulatory grammar, or replace with a more precise term such as regulatory sequence features or cis-regulatory logic.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Species selection  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not justify why these eight species were chosen as representative metazoans.  
- **Required correction** Briefly state the rationale for species selection, such as phylogenetic coverage or availability of reference genomes.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Related work  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not mention existing cross-species single-cell studies or deep-learning methods, making it difficult to assess novelty.  
- **Required correction** Add a sentence in the abstract or introduction that situates this work relative to prior efforts in cross-species single-cell integration and deep learning for regulatory genomics.

## Risk / unsupported claims
- The claim that Nvwa can predict gene expression and identify regulatory sequences at the single-cell level is unsupported without performance metrics or validation.
- The claim of conserved regulatory programs in vertebrates and invertebrates is unsupported without details on the comparison method or examples.
- The claim that the integrated landscapes constitute a valuable resource is not assessable without data availability information.
- The overall utility of the resource and the generalizability of Nvwa across species are not assessable from the abstract.