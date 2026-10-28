## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supporting information references)
- **Assessment boundary** Scientific validity, methodological soundness, interpretability claims, and reproducibility of the proposed EPE and DEPE methods as presented in the provided text
- **Shared manuscript claim summary** The authors introduce Expected Pattern Effect (EPE) and Differential Expected Pattern Effect (DEPE), two black-box interpretation methods for multi-task deep learning models of genome sequence, and demonstrate their utility in identifying cell type-specific transcription factor motifs and motif spacing from chromatin accessibility and ChIP-seq data. They also provide an executable software package for non-experts.
- **Visible evidence base** Results sections describing ChIP-seq validation (Fig 2), Oct4/Sox2 spacing analysis (Fig 3A-B), differential motif discovery across cell types (Fig 3C-E), and software availability statements; Methods sections for data processing, model training, and sequence selection
- **Missing materials affecting confidence** Actual figures and supplementary figures (S1-S4) are referenced but not provided; quantitative performance metrics for the DeepAccess models (e.g., AUC, accuracy) are not reported; details on hyperparameter selection, model architecture specifics beyond prior work, and statistical test assumptions are incomplete; code repository contents and versioning are not described in detail

## Reviewer
- **Overall assessment** The manuscript presents a conceptually useful extension of existing interpretation methods for genomic deep learning models, with a clear focus on differential analysis across conditions. The core idea of using designed sequences and ratio-based effect sizes is reasonable and addresses a genuine gap in the field. However, the evidence provided is insufficient to fully establish the validity and generalizability of the methods. Key validation experiments are described qualitatively without supporting quantitative data, and several methodological choices (e.g., sequence background selection, insertion position effects) are acknowledged but not rigorously justified. The software contribution is valuable, but the scientific claims require stronger empirical support.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on deep learning interpretation for regulatory genomics would find this relevant. Researchers studying cell type-specific transcription factor activity, particularly in development and reprogramming contexts, may use EPE/DEPE to generate hypotheses. The software package lowers the barrier for non-experts, which could broaden adoption in experimental labs.
- **Major strengths** The ratio-based formulation of EPE is a thoughtful improvement over difference-based approaches, particularly for imbalanced class settings. The application to multi-task models across many cell types is practical and addresses a real computational bottleneck. The validation using ChIP-seq data with known motifs is a sensible proof-of-concept. The software distribution via multiple channels (binary, PyPI, bioconda) is commendable for accessibility.
- **Major Concerns** (detailed below)
- **Minor Comments** (detailed below)
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative validation), R1-M2 (background sequence selection rationale), R1-M3 (statistical test appropriateness), R1-M4 (generalizability claims)
- **Assessment against Nature-style criteria** Originality: moderate, as the approach builds on existing interpretation methods but adds a differential dimension. Scientific importance: potentially high for the genomics community, but not yet demonstrated with robust evidence. Interdisciplinary readership: the software and conceptual framing could attract both computational and experimental researchers, but the current presentation is somewhat technical. Technical soundness: the core idea is plausible, but validation is incomplete and some methodological details are under-specified. Readability for nonspecialists: the abstract and introduction are accessible, but the results section assumes familiarity with deep learning interpretation and genomics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the need for quantitative validation and clearer methodological justification.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that EPE and DEPE "identify relevant transcription factor motifs and spacings that are predictive of cell type-specific chromatin accessibility" and that DEPE correctly identifies differential transcription factor activity in ChIP-seq validation.
- **Evidence pointer** Results sections "Expected pattern effect identifies differential motif activity from neural network models" and "DeepAccess trained on chromatin accessibility predicts preferred transcription factor spacing and cell type-specific transcription factors"; Figures 2 and 3 (not provided)
- **Concern** The validation results are described only qualitatively. For the ChIP-seq experiment, the text states that motifs matching the transcription factor ChIP are found to have significant DEPE, but no quantitative metrics (e.g., enrichment scores, p-values, effect sizes, ranking accuracy) are reported. Similarly, the Oct4/Sox2 spacing analysis claims agreement with ChIP-seq co-binding data, but the degree of agreement is not quantified. Without numerical evidence, the reader cannot assess the strength or reliability of the findings.
- **Why it matters** The central claim of the paper is that EPE/DEPE provide reliable and interpretable signals. Qualitative descriptions are insufficient to establish this, especially given the known variability in deep learning interpretation methods. The absence of quantitative validation undermines confidence in the method's utility.
- **Resolution test** Provide quantitative results for the ChIP-seq validation, such as the number of significant motifs, enrichment of known motifs relative to background, and comparison to alternative methods. For the spacing analysis, report the correlation or overlap between predicted preferred spacing and ChIP-seq-derived spacing distributions, with appropriate statistical tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors state that "we use randomly sampled closed DNA as our distribution sequences" for EPE/DEPE calculations, and that EPEs are "smaller when distribution-approximating sequences are selected from accessible or inaccessible parts of the genome" (S4 Fig).
- **Evidence pointer** Methods section "Selection of synthetic distribution of sequences"; Results section "DeepAccess trained on chromatin accessibility predicts preferred transcription factor spacing and cell type-specific transcription factors"; S4 Fig (not provided)
- **Concern** The choice of background sequences to approximate the data distribution D is critical for the validity of EPE/DEPE. The authors acknowledge that EPEs vary depending on whether accessible or inaccessible regions are used, but they do not provide a principled justification for selecting closed (inaccessible) regions. This choice could bias results, particularly for motifs that are enriched in open chromatin. The sensitivity analysis in S4 Fig is referenced but not described in sufficient detail to evaluate its implications.
- **Why it matters** If the background distribution is not representative of the sequences where the model is applied, the estimated effects may be misleading. The authors' choice could systematically over- or under-estimate motif effects, affecting the biological conclusions drawn.
- **Resolution test** Justify the choice of closed regions as background, or demonstrate that results are robust across different background choices (e.g., random genomic regions, accessible regions, matched GC content). Provide a more detailed description of the sensitivity analysis in S4 Fig, including quantitative comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical validity
- **Claim pointer** The authors define the significance of EPE using a signed-rank test statistic and compute DEPE significance similarly, but the text does not specify the null hypothesis or how multiple testing is handled.
- **Evidence pointer** Results section "Expected pattern effect identifies differential motif activity from neural network models"; equations for W and DEPE
- **Concern** The signed-rank test is appropriate for paired comparisons, but the manuscript does not clarify what constitutes a "pair" in this context (e.g., the same sequence with and without pattern insertion). Additionally, when testing hundreds of motifs across multiple cell type comparisons, multiple testing correction is essential to avoid false positives, but no correction is mentioned.
- **Why it matters** Without clear statistical framing and multiple testing control, the reported significant motifs may include false positives, undermining the reliability of the biological hypotheses generated.
- **Resolution test** Specify the null hypothesis and the pairing structure for the signed-rank test. Describe whether and how multiple testing correction is applied (e.g., Benjamini-Hochberg FDR) and report adjusted p-values or q-values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state that DEPE "can be used to discover condition-specific sequence features from many types of experimental genome-wide sequencing data" and that the software is "readily accessible to non-experts."
- **Evidence pointer** Discussion section; Results section "Executable allows for training and interpreting DeepAccess models for new tasks"
- **Concern** The generalizability claim is based on a single application to chromatin accessibility and a ChIP-seq validation. The manuscript does not demonstrate application to other data types (e.g., RNA-seq, methylation) or other model architectures. Additionally, the claim of accessibility to non-experts is not substantiated with usability testing or documentation examples.
- **Why it matters** Overstated generalizability could mislead potential users into applying the method in contexts where it may not perform well. The software claim is important for adoption but requires evidence of usability.
- **Resolution test** Either temper the generalizability claims to reflect the demonstrated scope, or provide additional validation on at least one other data type. For the software, include a brief usage example or tutorial in the manuscript or supplement to support the accessibility claim.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of "pattern" in EPE
- **Evidence pointer** Results section "Expected pattern effect identifies differential motif activity from neural network models"
- **Issue** The term "pattern" is used broadly to include motifs, motif combinations, and spacing, but the formal definition of αp assumes a single pattern p inserted into a sequence. It is unclear how combinations or spacing are encoded in this framework.
- **Required correction** Clarify how multi-motif patterns or spacing configurations are represented in the EPE calculation, possibly with a formal definition or example.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model training details
- **Evidence pointer** Methods section "DeepAccess model trained on ATAC-seq for 10 mouse cell types"
- **Issue** The manuscript references prior work for the DeepAccess architecture but does not specify key hyperparameters (e.g., learning rate, batch size, number of layers) or the exact training procedure used here.
- **Required correction** Provide a summary of hyperparameters and training details, or explicitly state that they are identical to the prior publication with a clear reference.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure references
- **Evidence pointer** Results sections referencing Figures 2, 3, S1-S4
- **Issue** The figures are not provided in the manuscript text, making it difficult to evaluate the claims. Some figure descriptions are vague (e.g., "Fig 2C" without describing the content).
- **Required correction** Ensure figures are included in the submission and provide more detailed captions or in-text descriptions of what each panel shows.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Software versioning
- **Evidence pointer** Results section "Executable allows for training and interpreting DeepAccess models for new tasks"
- **Issue** The software is described as available via PyPI and bioconda, but no version number or release date is provided, and the URL is given only in the abstract.
- **Required correction** Include a specific version number and mention the release date in the manuscript, and ensure the URL is also listed in the methods or data availability section.

## Risk / unsupported claims
- The claim that DEPE "identifies relevant transcription factor motifs and spacings that are predictive of cell type-specific chromatin accessibility" is not quantitatively supported by the provided text.
- The claim that EPE is "more robust" than Global Importance Analysis under class imbalance is referenced to S2 Fig but not described with sufficient detail to evaluate.
- The generalizability of DEPE to "many types of experimental genome-wide sequencing data" is asserted without demonstration.
- The accessibility of the software to "non-experts" is claimed without usability evidence.
- The biological interpretations (e.g., Hox genes in motor neurons, Fox factors in liver) are plausible but presented as confirmatory without statistical or experimental validation beyond literature citations.