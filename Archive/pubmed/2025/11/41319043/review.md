## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific validity, methodological rigor, claims substantiation, and presentation quality based solely on the provided text
- **Shared manuscript claim summary** The authors present ETNet, a CNN-Transformer hybrid deep learning architecture for predicting enhancer-enhancer interactions (EEIs) from DNA sequence alone. They claim superior performance over existing methods including EnContact across multiple cell lines, demonstrate cross-cell-type and cross-task transferability, recover known cell-type-specific transcription factor motifs via interpretability analysis, and provide computational evidence for super-additive cooperative mechanisms between enhancers.
- **Visible evidence base** Text descriptions of results including AUC/AUPRC values, P-values from DeLong tests, motif enrichment counts, correlation coefficients, and methodological descriptions. No actual figures, tables, or supplementary data were provided.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials referenced throughout the manuscript (Supplementary Figs 1-8, Supplementary Tables 1-8) were not available. This substantially limits verification of methodological details, data quality, and the validity of reported performance metrics.

## Reviewer

### Overall assessment
The manuscript addresses a genuinely under-explored problem in regulatory genomics: predicting enhancer-enhancer interactions from DNA sequence. The authors propose a reasonable architecture combining CNN feature extraction with a full Transformer encoder, and they report competitive performance against existing methods. The transfer learning experiments and interpretability analyses are valuable additions that go beyond simple benchmark reporting. However, the manuscript as presented has several significant weaknesses. The evaluation methodology is incompletely described, particularly regarding dataset construction, negative sampling, and the critical issue of genomic distance confounding. The claim of "super-additive cooperative mechanisms" is based on computational inference without experimental validation, and the authors appropriately acknowledge this, but the framing in the abstract overstates the strength of this evidence. The cross-task transfer to EPI prediction is presented as exploratory, which is appropriate, but the interpretation of shared chromatin interaction principles is speculative. The SNP analysis is explicitly hypothesis-generating, which is honest, but its inclusion in the abstract as a contribution is questionable given its preliminary nature. The writing is generally clear but occasionally verbose, and the manuscript would benefit from tighter organization. The statistical rigor is mixed: DeLong tests are appropriately used for AUC comparisons, but the multiple testing across six cell lines and multiple metrics is not addressed. The enhancer-level splitting strategy is a commendable effort to control information leakage, but the reported performance degradation is not discussed in sufficient depth. Overall, the work has merit and addresses a relevant gap, but the evidence as presented does not fully establish all claims, particularly regarding the biological interpretations.

### Who would be interested in the results, and why
Computational biologists and bioinformaticians working on regulatory genomics, particularly those focused on 3D genome organization, enhancer function, and deep learning applications to genomics. Researchers developing sequence-based predictors for chromatin interactions would find the architecture comparison and transfer learning results relevant. The interpretability analysis and motif recovery could interest experimental biologists studying cell-type-specific transcriptional regulation, though they would likely view the findings as hypothesis-generating. The SNP prioritization framework could appeal to researchers studying regulatory variants in disease, though the preliminary nature of the analysis limits its immediate utility.

### Major strengths
1. Addresses an under-studied problem (EEI prediction) with a reasonable deep learning architecture
2. Comprehensive benchmarking against multiple baseline methods including the current state-of-the-art
3. Rigorous attention to information leakage through enhancer-level splitting
4. Transfer learning experiments across cell types and tasks provide practical value
5. Interpretability analysis with known cell-type-specific motifs adds biological credibility
6. Honest acknowledgment of limitations and hypothesis-generating nature of biological claims
7. Open-source code availability supports reproducibility

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** "Evaluation across three cell lines (GM12878, K562, MCF-7) demonstrated superior performance compared to existing methods including EnContact, with statistical significance confirmed through DeLong tests across six cell lines."
- **Evidence pointer** Methods section "Construction and processing of enhancer-enhancer interaction datasets"; Results section "Comprehensive comparative analysis validates model superiority"
- **Concern** The dataset construction methodology is critically under-specified. The authors state that EEIs were identified by integrating ChIA-PET loops with FANTAOM5 enhancers, but do not describe: (1) the exact criteria for defining a positive EEI pair, (2) how negative pairs were generated beyond "randomly pairing enhancers from left and right anchors," (3) whether genomic distance between enhancer pairs was controlled for in the primary evaluation, (4) the number of positive and negative samples per cell line, and (5) whether the same enhancer could appear in multiple training and test pairs in the primary 8:1:1 split. The distance-matching negative sampling experiment is described only in the context of bias evaluation, not as the primary evaluation. This is a critical omission because sequence-based interaction predictors are notoriously susceptible to learning genomic distance as a proxy rather than genuine regulatory features. The reported AUC values of 0.875-0.982 are remarkably high for sequence-only prediction of chromatin interactions, which raises the suspicion that distance confounding may be inflating performance.
- **Why it matters** Without clear documentation of dataset construction and negative sampling, the reported performance metrics cannot be properly interpreted. If distance is not controlled, the model may be learning trivial distance relationships rather than regulatory grammar. This would undermine the central claim of the paper and the biological interpretations drawn from the model.
- **Resolution test** The authors must provide a detailed description of dataset construction including: exact overlap criteria, negative sampling procedure, distance distributions of positive and negative pairs, and sample sizes. They should report performance with distance-matched negatives as the primary evaluation, or clearly justify why the random negative set is appropriate. Ideally, they would also report performance stratified by genomic distance bins to demonstrate the model captures features beyond distance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "with statistical significance confirmed through DeLong tests across six cell lines"
- **Evidence pointer** Results section "Comprehensive validation using cross-validation, stringent data partitioning, and DeLong statistical testing"
- **Concern** The DeLong test is used to compare AUCs between ETNet and EnContact across six cell lines, but the manuscript does not describe: (1) whether the test was applied to the same test set predictions from both models, (2) whether the test accounts for the correlated nature of predictions from two models evaluated on the same data, (3) how multiple testing across six cell lines was handled, and (4) whether the DeLong test assumptions are met given the potentially large test set sizes. The reported P-values (e.g., P = .013157 for GM12878) are all below .05, but with six comparisons, the family-wise error rate is inflated. A Bonferroni correction or FDR control should be applied. Additionally, the DeLong test for correlated ROC curves is appropriate when comparing two models on the same data, but the manuscript does not clarify whether this was the implementation used.
- **Why it matters** The statistical significance claim is central to establishing ETNet's superiority over EnCTA. If the testing procedure is flawed or multiple testing is not addressed, the claim of "statistical significance" is weakened. This is particularly important given that the reported improvements are modest (~3-5% in AUC).
- **Resolution test** The authors should describe the exact DeLong test implementation, clarify whether predictions from both models on the same test set were used, and apply multiple testing correction across the six cell lines. They should also report confidence intervals for AUC differences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** "revealed computational evidence for super-additive cooperative mechanisms, with cooperativity negatively correlating with sequence similarity"
- **Evidence pointer** Results section "Higher-order enhancer-enhancer interaction analysis using greedy search"; Results section "Integrated feature attribution and nonlinear cooperative mechanisms"
- **Concern** The claim of "super-additive cooperative mechanisms" is based entirely on computational inference from the model's prediction scores. The authors use a greedy search algorithm with dinucleotide shuffling perturbations to identify "critical regions" and then compare summed individual importance scores with "synergistic importance scores under cooperative conditions." However, the manuscript does not provide: (1) a formal definition of "super-additivity" in this context, (2) the statistical test used to determine whether the observed super-additivity is significant beyond chance, (3) any validation that the greedy search reliably identifies true functional regions, or (4) any experimental evidence supporting the claim. The negative correlation with sequence similarity (r = -0.407, P = 1.36 x 10^-4) is presented as evidence for a "functional complementarity model," but this is a post-hoc interpretation of a correlational finding. The authors do acknowledge this is computational and requires experimental validation, which is appropriate, but the abstract states this as a finding without sufficient hedging.
- **Why it matters** The super-additivity claim is presented as a significant biological insight in the abstract and discussion. If the computational methodology is not rigorously validated, this claim could mislead readers into believing there is stronger evidence for cooperative mechanisms than actually exists. The correlation with sequence similarity is interesting but could be an artifact of the model's architecture or the specific test set.
- **Resolution test** The authors should provide a formal definition of super-additivity, describe the statistical framework for testing it, and ideally validate the greedy search approach on simulated or experimentally characterized enhancer pairs. They should also discuss alternative explanations for the observed correlation with sequence similarity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodology
- **Claim pointer** "ETNet exhibited effective cross-cell type transfer learning through selective fine-tuning and showed cross-task transferability to enhancer-promoter interaction prediction"
- **Evidence pointer** Results section "Cross-cell-type enhancer-enhancer interaction prediction through transfer learning"; Results section "Transfer learning enables cross-task enhancer-promoter interaction prediction"
- **Concern** The transfer learning experiments are described at a high level but lack critical details. For cross-cell-type transfer, the manuscript states that "selective fine-tuning" was used, adapting input, convolutional, and output layers while freezing transformer layers, but does not specify: (1) which cell type was used for initial training and which for fine-tuning in each direction, (2) the number of fine-tuning epochs and early stopping criteria, (3) the performance comparison against training from scratch on the target cell type, and (4) whether the improvement is statistically significant. For cross-task transfer to EPI, the manuscript reports AUC values but does not describe the EPI dataset construction, the number of samples, or how the model architecture was adapted. The claim of "shared chromatin interaction principles" is a strong interpretation from limited transfer experiments.
- **Why it matters** Transfer learning is presented as a key contribution, but without proper experimental details and baselines, the reader cannot assess whether the transfer is genuinely effective or whether the results are confounded by dataset similarity or other factors. The biological interpretation of "shared principles" requires more rigorous evidence.
- **Resolution test** The authors should provide complete experimental details for all transfer learning experiments, including training from scratch baselines on target datasets, and statistical comparison of transfer versus from-scratch performance. They should temper the biological interpretation or provide additional evidence for shared mechanisms.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Methodology
- **Claim pointer** "Feature attribution analysis recovered cell-type-specific regulatory motifs consistent with known transcription factors"
- **Evidence pointer** Results section "Integrated feature attribution and nonlinear cooperative mechanisms"; Methods section "Deep learning important features analysis"
- **Concern** The motif analysis methodology is under-specified. The authors state that DeepLIFT attribution scores were converted to position weight matrix format and compared against JASPAR motifs using cosine similarity with a threshold of 0.8. However, they do not describe: (1) how attribution scores were converted to PWMs, (2) how many motifs were identified per cell line, (3) the background model used for enrichment analysis, (4) whether the enrichment is statistically significant relative to a null model, or (5) how the threshold of 0.8 was chosen. The reported motif counts (e.g., GATA2: 249 in K562 vs 40 in GM12878) are presented without statistical context. The claim that motifs are "consistent with known transcription factors" is based on similarity to JASPAR motifs, but the significance of this similarity is not established.
- **Why it matters** The motif recovery is presented as evidence that the model learns biologically meaningful features. Without rigorous statistical analysis, this claim is not substantiated. The cosine similarity threshold of 0.8 may be too lenient or too strict, and the reader cannot assess the false discovery rate.
- **Resolution test** The authors should provide a detailed description of the motif identification pipeline, including the PWM conversion, the statistical significance testing for motif enrichment, and the choice of similarity threshold. They should also report the number of motifs tested and the multiple testing correction applied.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "super-additive cooperative mechanisms" as a finding without sufficient hedging. Given that this is entirely computational and the authors acknowledge it requires experimental validation, the abstract should more clearly frame this as a computational prediction or hypothesis.
- **Required correction** Revise the abstract to state "computational evidence suggesting potential super-additive cooperative mechanisms" or similar hedging language.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods section "DNA sequence encoding"
- **Evidence pointer** Methods section "DNA sequence encoding"
- **Issue** The one-hot encoding method is described, but the handling of ambiguous bases (N) as [0,0,0,0] is problematic. This representation is indistinguishable from a gap or padding token, which could introduce artifacts. The authors should clarify how N bases are distributed in the dataset and whether this encoding choice affects performance.
- **Required correction** Provide statistics on N base frequency in the dataset and discuss the potential impact of the encoding choice, or consider alternative encoding strategies.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "Comprehensive validation using cross-validation, stringent data partitioning, and DeLong statistical testing"
- **Evidence pointer** Results section "Comprehensive validation using cross-validation, stringent data partitioning, and DeLong statistical testing"
- **Issue** The manuscript reports that enhancer-level splitting reduced test set sizes but does not report the number of unique enhancers in the training and test sets. This information is important for understanding the degree of information leakage that was controlled.
- **Required correction** Report the number of unique enhancers in training and test sets for each cell line under both splitting strategies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results section "Comprehensive comparative analysis validates model superiority"
- **Evidence pointer** Results section "Comprehensive comparative analysis validates model superiority"
- **Issue** The manuscript states that "all evaluated models were executed with consistent hyperparameter configurations where applicable," but this is vague. For a fair comparison, the hyperparameter tuning procedure for each baseline should be described.
- **Required correction** Describe the hyperparameter selection process for each baseline method, including whether hyperparameters were tuned on a validation set and the search space considered.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods section "Higher-order enhancer-enhancer interaction analysis using greedy search"
- **Evidence pointer** Methods section "Higher-order enhancer-enhancer interaction analysis using greedy search"
- **Issue** The greedy search algorithm is described conceptually, but the stopping criterion and the number of regions selected per sequence are not specified. This makes it difficult to interpret the "critical regions" identified.
- **Required correction** Specify the stopping criterion for the greedy search and the typical number of regions selected per sequence.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of "shared chromatin interaction principles" based on cross-task transfer is speculative. While the authors acknowledge this, the discussion would benefit from a more measured interpretation and a clearer statement of what additional evidence would be needed.
- **Required correction** Revise the discussion to more clearly distinguish between the demonstrated transferability of the model and the inferred biological principles.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods section "Transfer learning fine-tuning strategy"
- **Evidence pointer** Methods section "Transfer learning fine-tuning strategy"
- **Issue** The selective fine-tuning strategy is described as adapting "input layer, convolutional layers, and output layer" while freezing transformer layers, but the rationale for this specific choice is not provided. Why freeze the transformer layers?
- **Required correction** Provide a rationale for the selective fine-tuning strategy, or present an ablation study comparing different fine-tuning approaches.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results section "ETNet performance in capturing super-enhancer regulatory architecture"
- **Evidence pointer** Results section "ETNet performance in capturing super-enhancer regulatory architecture"
- **Issue** The super-enhancer analysis is presented as a separate section but is not clearly motivated in the introduction. The connection between EEI prediction and super-enhancer biology should be made more explicit.
- **Required correction** Add a brief motivation for the super-enhancer analysis in the introduction or at the start of the results section.

### Technical failings that need to be addressed before the case is established
1. Dataset construction and negative sampling methodology is critically under-specified (R1-M1)
2. Statistical testing for AUC comparisons lacks multiple testing correction and procedural details (R1-M2)
3. Super-additivity analysis lacks formal definition and statistical validation (R1-M3)
4. Transfer learning experiments lack baseline comparisons and complete experimental details (R1-M4)
5. Motif analysis lacks statistical significance testing and methodological details (R1-M5)

### Assessment against Nature-style criteria
**Originality:** The problem of EEI prediction is genuinely under-studied, and the application of a full transformer encoder to this task is a reasonable contribution. However, the architectural novelty is limited, as CNN-transformer hybrids are well-established in genomics. The interpretability analysis and transfer learning experiments add some originality, but the core approach is incremental.

**Scientific importance:** EEI prediction is relevant to understanding gene regulation, and the transfer learning results could have practical utility. However, the biological claims (super-additivity, shared principles) are not experimentally validated and are presented with more confidence than warranted. The importance is moderate but not transformative.

**Interdisciplinary readership:** The manuscript is primarily of interest to computational biologists and bioinformaticians. The biological interpretations may attract some experimental biologists, but the lack of experimental validation limits broader appeal. The writing is technical and assumes familiarity with deep learning and genomics.

**Technical soundness:** The technical approach is reasonable, but the evaluation methodology has significant gaps. The dataset construction is under-specified, the statistical testing is incomplete, and the interpretability analysis lacks rigorous validation. These issues undermine confidence in the reported results.

**Readability for nonspecialists:** The manuscript is clearly written but is not accessible to nonspecialists. The methods are described at a level that requires expertise in deep learning and genomics. The abstract is reasonably accessible but overstates the biological findings.

### Recommendation posture
**Supportive if technical concerns are resolved.** The manuscript addresses a relevant problem and the proposed architecture is reasonable. However, the evaluation methodology must be substantially improved to establish the central claims. Specifically, the authors must provide complete details on dataset construction and negative sampling, address the distance confounding issue, apply appropriate multiple testing corrections, and provide rigorous statistical validation for the super-additivity and motif analysis claims. The biological interpretations should be tempered to match the computational nature of the evidence. If these concerns are addressed, the manuscript could make a useful contribution to the field.

## Risk / unsupported claims
- The claim of "super-additive cooperative mechanisms" is unsupported by experimental evidence and is based on a computational inference method that is not rigorously validated.
- The claim of "shared chromatin interaction principles" based on cross-task transfer is speculative and not directly supported by the experimental design.
- The claim that ETNet "recovers cell-type-specific regulatory motifs consistent with known transcription factors" is not supported by statistical significance testing.
- The claim of "effective cross-cell type transfer learning" is not supported by comparison against training from scratch baselines.
- The claim of "superior performance compared to existing methods" is potentially confounded by genomic distance if the negative sampling does not control for this factor.
- The SNP analysis is explicitly described as hypothesis-generating, which is appropriate, but the inclusion of this as a contribution in the abstract may overstate its significance.