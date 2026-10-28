## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, supporting information references)
- **Assessment boundary** Scientific claims, methodological soundness, validation adequacy, and generalizability of the peaFramework as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present a two-stage computational framework (peaBrain) using convolutional neural networks to predict transcriptomic consequences of non-coding variation and small molecules. Stage 1 predicts mean gene abundance from promoter sequences with optional epigenetic annotations; Stage 2 predicts individual-level expression differences from sequence variation. The authors claim superior performance over existing methods in multiple tasks, including disease variant prioritization, allele-specific binding prediction, and functional tissue identification.
- **Visible evidence base** Main text figures referenced (Fig 1-5), tables (Table 1-3), supplementary tables (S1-S4), supplementary text (S1-S3), methods section
- **Missing materials affecting confidence** Actual figure images, supplementary data files, code availability, hyperparameter tuning details, full model architecture diagrams, and complete benchmark comparisons

## Reviewer
- **Overall assessment** The manuscript presents an ambitious and potentially valuable framework for predicting transcriptomic consequences of non-coding variation. The two-stage architecture is conceptually interesting, and the authors demonstrate several applications. However, the manuscript suffers from significant methodological ambiguities, incomplete validation, and overclaimed generalizability. The core claims about outperforming existing methods are not fully supported by the evidence presented, and several technical details are insufficiently described for reproducibility. The computational cost of Stage 2 appears prohibitive for practical use, yet this limitation is not adequately addressed.
- **Who would be interested in the results, and why** Computational geneticists and bioinformaticians developing predictive models for regulatory genomics would be interested. Researchers studying functional interpretation of GWAS variants and eQTL prioritization would find the framework relevant. The small molecule prediction extension could interest pharmacogenomics researchers. However, the practical utility is currently limited by computational requirements and incomplete validation.
- **Major strengths** The two-stage framework is conceptually novel, combining promoter sequence modeling with individual variation. The authors demonstrate multiple applications, showing versatility. The comparison with experimental assays (MPRA, BiT-STARR-seq, HiDRA) is a valuable contribution. The embedding approach for gene representation is interesting and potentially useful.
- **Major Concerns** 
- **Minor Comments**
- **Technical failings that need to be addressed before the case is established** Stage 2 computational cost, insufficient benchmark comparisons, lack of code availability, incomplete hyperparameter reporting, potential data leakage in cross-validation
- **Assessment against Nature-style criteria** Originality is moderate; the framework combines existing ideas but the specific architecture is novel. Scientific importance is potentially high but not yet established due to validation gaps. Interdisciplinary readership is limited by technical density and lack of accessible summaries. Technical soundness is questionable due to incomplete methodological details. Readability for nonspecialists is poor; the manuscript assumes deep familiarity with both genomics and deep learning.
- **Recommendation posture** Currently not established from the provided evidence. Major revisions and additional validation are required before the claims can be supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "peaBrain accounts for the majority (>50%) of variance observed in mean transcript abundance across most tissues"
- **Evidence pointer** Figure 1, Results section "peaBrain captures >50% of the variance in mean gene abundance"
- **Concern** The claim that class-C models capture >50% variance is based on models that include tissue-specific epigenetic annotations. However, the authors do not clearly separate the contribution of DNA sequence versus epigenetic annotations. The class-A (DNA-only) models achieve only 17% variance explained, and class-B (with non-specific annotations) achieve 45%. The jump to >50% with tissue-specific annotations raises the question of whether the model is simply memorizing tissue-specific chromatin states rather than learning generalizable regulatory principles. Furthermore, the cross-validation procedure is not clearly described - it is unclear whether genes were properly partitioned to avoid leakage between training and test sets.
- **Why it matters** The central claim of the paper rests on this performance metric. If the variance explained is primarily due to epigenetic annotations rather than sequence features, the framework's utility for predicting consequences of unseen sequence variation is severely limited. The authors explicitly state that Stage 2 is "purely sequence based," but the Stage 1 results suggest sequence alone is insufficient.
- **Resolution test** The authors should provide: (1) a clear breakdown of variance explained by sequence alone versus sequence plus annotations, (2) a description of the cross-validation scheme ensuring no gene overlap between training and test sets, (3) performance metrics on held-out chromosomes or genomic regions, and (4) an analysis of whether the model generalizes to tissues not included in training.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "Our computational framework, peaBrain, models the transcriptional machinery of a tissue"
- **Evidence pointer** Methods section, S6 and S7 Tables
- **Concern** The manuscript lacks sufficient detail for reproduction. The model architecture is described at a high level, but critical hyperparameters are missing: learning rate schedules, batch sizes, number of training epochs beyond the minimum 100, early stopping criteria, weight initialization schemes, and regularization parameters beyond dropout. The S6 and S7 tables are referenced but not provided in the manuscript text. Most critically, no code or data availability statement is provided, making it impossible for other researchers to implement or verify the framework.
- **Why it matters** Reproducibility is a fundamental requirement for computational biology papers. Without code and complete methodological details, the framework cannot be independently validated or built upon. This is particularly important given the complexity of the architecture and the multiple stages involved.
- **Resolution test** The authors should: (1) provide a public code repository with documentation, (2) include all hyperparameters in the methods or supplementary materials, (3) provide trained model weights for downstream use, and (4) include a detailed data processing pipeline for reproducing the input features.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation adequacy
- **Claim pointer** "peaBrain score outperforms existing measures in predicting disease-associated variants and in predicting allele-specific transcription factor binding"
- **Evidence pointer** Table 1, Table 3, Results section "peaBrain score outperforms existing measures"
- **Concern** The comparison with existing methods (CADD, Eigen) is limited and potentially biased. The authors use logistic regression coefficients to compare methods, but do not report standard metrics such as AUC, precision-recall curves, or calibration. The comparison is also restricted to somatic mutations in COSMIC census genes, which may not be representative of all disease-associated variation. For allele-specific binding, the comparison with DeepSEA is confounded by the fact that DeepSEA was not designed for this specific task. The authors do not compare against more recent deep learning methods for variant effect prediction.
- **Why it matters** The claim of outperforming existing methods is central to the paper's significance. If the comparison is incomplete or biased, the conclusion is not supported. The field has moved rapidly, and comparisons against state-of-the-art methods are essential.
- **Resolution test** The authors should: (1) report AUC and precision-recall metrics for all comparisons, (2) include additional benchmark datasets beyond COSMIC, (3) compare against more recent methods such as Enformer, Sei, and other deep learning variant effect predictors, and (4) perform calibration analysis to ensure the scores are well-calibrated.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational feasibility
- **Claim pointer** "we extended the peaBrain model to incorporate a 1Mbps window"
- **Evidence pointer** Results section "Stage 1 peaBrain model is designed with extensibility in mind", Methods section
- **Concern** The computational cost of Stage 2 is not adequately addressed. The authors state that analyzing a single gene in a single tissue with 94 individuals required 15 days on a CPU, and the complete analysis of 816 genes took approximately one month on 600 cores. This is extremely computationally intensive. The authors do not discuss the scalability of this approach to larger sample sizes, more tissues, or genome-wide applications. The practical utility of a framework that requires this level of computational resources is questionable.
- **Why it matters** If the framework cannot be applied at scale, its utility for the broader genomics community is limited. The authors should provide a clear analysis of computational scaling and discuss potential optimizations or approximations.
- **Resolution test** The authors should: (1) provide a detailed computational cost analysis including GPU vs CPU time, (2) discuss strategies for reducing computational cost (e.g., model compression, approximation methods), (3) provide estimates for genome-wide application, and (4) discuss the trade-offs between model complexity and performance.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability
- **Claim pointer** "peaBrain is a black-box approach and we must be cautious in attempting to elucidate scientific rationales"
- **Evidence pointer** Discussion section
- **Concern** The authors acknowledge the black-box nature of their approach but do not provide any interpretability analysis. Given the framework's goal of understanding regulatory genomics, the lack of interpretability is a significant limitation. The authors do not attempt to identify which sequence features or motifs are most important for predictions, nor do they provide any analysis of the learned representations.
- **Why it matters** For the framework to be scientifically useful beyond prediction, it must provide insights into regulatory mechanisms. The authors claim the embeddings capture meaningful biological information but do not demonstrate this beyond correlation with pathway membership.
- **Resolution test** The authors should: (1) perform feature importance analysis to identify key sequence elements, (2) analyze the learned embeddings for known regulatory motifs, (3) provide case studies of specific variants with mechanistic interpretation, and (4) compare learned features with known regulatory grammar.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract claims the framework predicts "transcriptomic consequences of non-coding variation and small molecules" but the small molecule application is only briefly mentioned in the supplementary text. The main text focuses almost exclusively on genetic variation.
- **Required correction** Either move the small molecule application to the main text with adequate validation, or revise the abstract to accurately reflect the paper's scope.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The confidence intervals for logistic regression coefficients are reported, but no multiple testing correction is mentioned. Given the large number of tests performed across tissues and tasks, the false discovery rate may be inflated.
- **Required correction** Report adjusted p-values or explicitly state the multiple testing correction method used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The description of the "difference sequence" input for Stage 2 is unclear. It is not specified how insertions, deletions, or structural variants are handled in the sequence alignment and differencing process.
- **Required correction** Provide a detailed description of the sequence differencing algorithm, including handling of indels and complex variants.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Benchmarking
- **Affected element** Figure 5
- **Evidence pointer** Figure 5
- **Issue** The correlation analysis with other variant effect prediction methods is limited to a single figure with no quantitative comparison. The authors should provide a more systematic benchmark.
- **Required correction** Provide a comprehensive benchmark table with multiple methods and multiple metrics.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The authors do not specify the version of the GTEx data used for Stage 2 analyses beyond mentioning v6p for eQTLs and v7 for training. The exact data versions and processing pipelines should be clearly stated.
- **Required correction** Provide a complete data availability statement with exact versions and accession numbers.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations is brief and does not address several important concerns, including the computational cost, potential overfitting, and the limited validation of the small molecule predictions.
- **Required correction** Expand the limitations section to address these concerns and provide a balanced assessment of the framework's strengths and weaknesses.

## Risk / unsupported claims
- The claim that peaBrain "outperforms" existing methods is not fully supported due to limited benchmark comparisons and potential biases in the evaluation framework.
- The claim that the framework can predict "transcriptomic consequences of small molecules" is not adequately validated in the main text; the supplementary analysis appears preliminary.
- The claim that Stage 1 models capture ">50% of variance" is dependent on tissue-specific annotations, and the contribution of sequence alone is modest (17%).
- The claim that the framework identifies "putatively functional eQTLs that are missed by high-throughput experimental approaches" is not validated with independent experimental evidence.
- The generalizability of the framework to non-human species is claimed based on limited correlation analyses with orthologous promoters, but the predictive performance is weak (rho = 5-22%).
- The biological interpretability of the learned embeddings is claimed but not demonstrated beyond superficial correlation analyses.