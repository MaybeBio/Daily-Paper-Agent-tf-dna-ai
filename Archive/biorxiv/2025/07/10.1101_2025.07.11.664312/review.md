## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, methods, and supplementary figure descriptions. No figures or supplementary files were provided for direct inspection.
- **Assessment boundary** Assessment is limited to the claims and evidence as presented in the text. Figures, tables, and supplementary materials are referenced but were not available for direct examination.
- **Shared manuscript claim summary** The authors present PromoterAtlas, a 1.8M parameter transformer model trained on approximately 9 million upstream regulatory sequences from 3,371 gammaproteobacterial species. They claim the model recognizes diverse regulatory elements, enables genome-wide promoter annotation across five sigma factors, encodes cross-species evolutionary relationships in its embedding space, and supports prediction of transcription and translation levels.
- **Visible evidence base** Text descriptions of results, methods, and figure captions. No actual figures, tables, or supplementary data files were provided for inspection.
- **Missing materials affecting confidence** All figures (Figures 1-5), supplementary figures (S1-S6), and the underlying datasets. Without these, quantitative claims regarding performance metrics, validation results, and visualizations cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable resource in the form of a large-scale pretrained transformer model for bacterial regulatory sequence analysis. The core idea of leveraging unsupervised pretraining on a broad taxonomic clade to overcome labeled data scarcity is sound and timely. However, the evidence presented in the text is largely qualitative, with key quantitative results relegated to figures that were not available for review. The validation strategy for the promoter annotation tool, while multi-pronged, relies on a small manually annotated training set and a single ChIP-seq dataset for validation. The claims regarding cross-species evolutionary relationships and expression prediction are intriguing but require closer scrutiny of the underlying data and baselines.
- **Who would be interested in the results, and why** Researchers in bacterial genomics, synthetic biology, and computational biology would find this work relevant. The model and annotation tool could be useful for genome annotation efforts in non-model Gammaproteobacteria, and the expression prediction capabilities may interest those engineering bacterial gene expression. The approach of clade-wide pretraining may also be of methodological interest to the broader deep learning for genomics community.
- **Major strengths** The scale of pretraining data (9M sequences, 3,371 species) is a significant advance over prior species-specific models. The focus on a comprehensive annotation framework rather than binary classification addresses a real gap in the field. The multi-sigma factor annotation capability is a clear functional advantage over existing tools. The demonstration that embeddings capture sigma factor identity across species is conceptually interesting and suggests the model has learned biologically meaningful representations.
- **Major Concerns** The major concerns are detailed below.
- **Minor Comments** The minor comments are detailed below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** **Originality** The approach of clade-wide pretraining for bacterial regulatory sequences is a novel contribution, though it builds on established transformer architectures and pretraining paradigms. **Scientific importance** The potential to enable genome-wide promoter annotation across a major bacterial class is significant, but the current evidence does not fully establish the reliability of the tool. **Interdisciplinary readership** The work bridges machine learning, genomics, and synthetic biology, and would appeal to a broad readership if the claims are substantiated. **Technical soundness** The architecture and training approach are reasonable, but the validation strategy has notable weaknesses, particularly the small training set for the segmentation head and the limited comparative analysis against existing tools. **Readability for nonspecialists** The manuscript is generally well-written and accessible, though some sections assume familiarity with bacterial promoter biology and transformer architectures.
- **Recommendation posture** Supportive if technical concerns are resolved. The core resource and approach are promising, but the current evidence, as presented in the text, is insufficient to fully establish the stated claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that PromoterAtlas-annotation achieves a 70% validation rate against ChIP-seq data, compared to 58% and 62% for SAPPHIRE and ProPr, respectively, and 56% for a naive baseline.
- **Evidence pointer** Results section "Whole genome promoter motif annotation", Figure 3B. Location not provided.
- **Concern** The comparison against existing tools and a naive baseline is presented as a single percentage point without any measure of uncertainty, statistical significance, or description of the test set composition. The naive baseline of placing promoters 30 nucleotides upstream of every coding sequence is a strong prior for E. coli, and the marginal improvement over this baseline (70% vs 56%) requires statistical validation. Furthermore, the comparison with SAPPHIRE and ProPr may be confounded by differences in output formats, score thresholds, and the definition of a "valid" prediction. The text does not describe how these tools' outputs were processed to enable a fair comparison.
- **Why it matters** The central claim of the annotation tool's utility rests on this comparative validation. Without statistical rigor and a clear description of the evaluation protocol, the superiority of PromoterAtlas-annotation over existing methods is not established.
- **Resolution test** Provide confidence intervals or statistical tests for the validation rates. Describe the exact evaluation protocol, including how predictions from each tool were converted to comparable promoter calls, what genomic regions were considered, and how the ChIP-seq peaks were processed. Report performance on a per-sigma-factor basis, as aggregating across sigma factors may mask significant differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the model's embeddings enable effective prediction of transcription and translation levels, with the best model reaching state-of-the-art performance on transcription prediction.
- **Evidence pointer** Results section "Predicting transcription and translation levels", Figure 5B, Supplementary Figure S6. Location not provided.
- **Concern** The text states that the PromoterAtlas-based model "consistently outperformed" a simple convolutional network and that the best model reached correlations "on par with or higher than" Promoter Calculator. However, no actual correlation values are reported in the text for the transcription task, and the protein expression prediction result (0.79) is compared to a single model (ANOVA, 0.82) without discussing whether this difference is meaningful. The choice of a simple convolutional network as the only baseline is weak; a comparison against a state-of-the-art promoter strength prediction tool on the same datasets would be more informative. The text also does not describe the hyperparameter tuning process for the prediction heads, raising concerns about whether the comparison is fair.
- **Why it matters** The claim of state-of-the-art performance is a key selling point of the model. Without reporting actual numbers, comparing against appropriate baselines, and describing the experimental setup in sufficient detail, this claim cannot be evaluated.
- **Resolution test** Report the actual Pearson correlation values for all models and datasets in the text or a table. Include a stronger baseline, such as Promoter Calculator, in the comparison for both transcription and translation tasks. Describe the hyperparameter search procedure and the final model configurations. Provide error bars or confidence intervals for the correlations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The claim that the segmentation head was trained on 318 manually annotated sequences, with the resulting model used for genome-wide annotation.
- **Evidence pointer** Methods section "PromoterAtlas-annotation". Location not provided.
- **Concern** A training set of 318 sequences for a 12-class segmentation task is extremely small, especially for a model that is expected to generalize across a diverse clade. The text does not describe the criteria used for manual annotation, the inter-annotator agreement, or how representative these sequences are of the broader Gammaproteobacteria. The risk of overfitting to the specific promoter architectures present in the training set is high, and the reported validation on E. coli ChIP-seq data may not reflect performance on more distantly related species.
- **Why it matters** The reliability of the genome-wide annotation tool depends on the quality and representativeness of its training data. A small, potentially biased training set undermines confidence in the tool's generalizability.
- **Resolution test** Provide a detailed description of the manual annotation protocol, including the exact definitions used for each sigma factor promoter class. Report inter-annotator agreement statistics. Describe the taxonomic distribution of the training sequences and compare it to the distribution of the full pretraining dataset. Consider augmenting the training set or using a semi-supervised approach to leverage the larger unlabeled corpus.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that the embedding space encodes cross-species evolutionary relationships, with sigma factor identity emerging as the dominant organizing principle in deeper layers.
- **Evidence pointer** Results section "PromoterAtlas encodes cross-species evolutionary relationships", Figure 4. Location not provided.
- **Concern** The UMAP visualization is presented as evidence of the model's understanding of evolutionary relationships, but this is a qualitative observation. The text does not provide any quantitative measure of clustering quality or separation. The observation that GC content organizes shallow layers and sigma factor identity organizes deeper layers is interesting but is presented without a rigorous analysis. For example, it is unclear how the authors determined that GC content is the "primary organizing principle" in shallow layers, or how they quantified the emergence of sigma factor identity in deeper layers.
- **Why it matters** This claim speaks to the model's ability to learn biologically meaningful representations, which is a key motivation for the work. However, without quantitative support, it remains an anecdotal observation.
- **Resolution test** Provide quantitative metrics for cluster quality, such as silhouette scores or adjusted Rand index, for both GC content-based and sigma factor-based groupings across layers. Consider using a more rigorous approach, such as training a classifier on the embeddings to predict sigma factor identity and reporting accuracy as a function of layer depth.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that the model recognizes various regulatory elements, including transcription factor binding sites for CRP, ntrC, luxR, and FNR.
- **Evidence pointer** Results section "Recognition of regulatory features", Supplementary Figure S2. Location not provided.
- **Concern** The recognition of transcription factor binding sites is demonstrated through logit plot visualization. This is a qualitative assessment and does not constitute a systematic evaluation. The text does not describe how these motifs were identified in the logit plots, whether the recognition is specific (i.e., the model does not produce similar patterns at non-binding sites), or how sensitive the approach is to motif variations.
- **Why it matters** The claim that the model recognizes diverse regulatory elements is a core part of the paper's contribution. A qualitative demonstration on a few examples is insufficient to establish this capability.
- **Resolution test** Perform a systematic evaluation of transcription factor binding site recognition. For example, use a set of known binding sites and matched control sequences, and measure the model's ability to distinguish them based on logit values or attention patterns. Report sensitivity and specificity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract. Location not provided.
- **Issue** The abstract states the model was trained on "9M regulatory sequences" but does not specify the sequence length or the total number of nucleotides. This information is relevant for assessing the model's capacity and training scope.
- **Required correction** Add the sequence length (200 nucleotides) to the abstract or specify the total nucleotide count.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Whole genome promoter motif annotation"
- **Evidence pointer** Results section "Whole genome promoter motif annotation". Location not provided.
- **Issue** The text mentions that the relative abundances of predicted promoters across sigma factors are "plausible from a biological perspective" and cites the 12:1 ratio of sigma70/sigma38 to sigma54 promoters. However, no comparison is made to known or expected ratios from experimental data in other species.
- **Required correction** Provide a quantitative comparison to published estimates of sigma factor usage or promoter distributions, if available, to strengthen this claim.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Prediction of transcription levels"
- **Evidence pointer** Methods section "Prediction of transcription levels". Location not provided.
- **Issue** The description of the cross-evaluation procedure is brief. It states that "separate models were trained on each dataset and evaluated against all other datasets," but it is unclear whether the model architecture and hyperparameters were kept fixed across datasets or re-tuned for each.
- **Required correction** Clarify whether the same hyperparameters were used for all datasets and whether any dataset-specific tuning was performed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Prediction of protein expression levels"
- **Evidence pointer** Methods section "Prediction of protein expression levels". Location not provided.
- **Issue** The text states that a logarithmic transformation was applied to the target values, but the base of the logarithm is not specified. This affects the interpretation of the reported correlation values.
- **Required correction** Specify the base of the logarithm used for the transformation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Recognition of regulatory features"
- **Evidence pointer** Results section "Recognition of regulatory features". Location not provided.
- **Issue** The text mentions that attention maps were helpful in revealing promoter motifs in cases where logit plots were unclear. It is not stated whether this was a systematic issue or limited to a few cases.
- **Required correction** Quantify how often attention maps were needed and whether this correlated with specific sequence features or sigma factor types.

## Risk / unsupported claims
- The claim of "state-of-the-art performance" in transcription prediction is unsupported as no actual performance numbers are reported in the text and the comparison baseline is limited.
- The claim that the model "encodes cross-species evolutionary relationships" is based solely on qualitative UMAP visualization and is not quantitatively supported.
- The claim that the model recognizes transcription factor binding sites is based on anecdotal visual inspection of logit plots and is not systematically evaluated.
- The generalizability of the segmentation model trained on 318 sequences to the entire Gammaproteobacteria class is asserted but not demonstrated with data from diverse species.
- The biological plausibility of predicted sigma factor promoter distributions is asserted but not compared to independent experimental data.