## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific claims, methodology, validation approach, and reproducibility as presented in the provided text; no supplementary figures or tables were available for inspection
- **Shared manuscript claim summary** The authors present GenomicLinks, a deep learning model combining dual CNNs with a bidirectional LSTM, trained on maize Hi-ChIP data (H3K4me3 and H3K27me3), to predict 3D chromatin interactions from DNA sequence. Using in silico mutagenesis (SNIPER), they identify bHLH and AP2/EREBP transcription factor binding motifs as predictive of loop formation. Predictions are validated using natural genetic variants from the maize 282 diversity panel and single-cell ATAC-seq co-accessibility data.
- **Visible evidence base** Main text figures referenced (Figures 1–5), Supplementary Figures S1–S3, Supplementary Table S1; none of these were provided for review
- **Missing materials affecting confidence** All figures, supplementary materials, code repository contents, and detailed model architecture parameters; the manuscript states these are available but they were not part of the submitted material

## Reviewer
- **Overall assessment** The manuscript addresses an important gap: the lack of plant-specific deep learning models for 3D chromatin interaction prediction. The authors demonstrate that a human-trained model (DeepMILO) performs at near-chance level on maize data, justifying the need for a plant-trained model. The core technical approach is reasonable, and the integration of multiple validation layers (in silico mutagenesis, natural variants, single-cell co-accessibility) is commendable. However, several critical issues undermine confidence in the central claims. The negative set construction involves a subtle but potentially problematic step (random shifting of permuted anchors), the validation with single-cell co-accessibility shows only modest statistical support, and the claim that specific TF motifs "drive" predictions is not fully established given the correlational nature of the analysis. The manuscript would benefit from clearer reporting of model interpretability analyses and more rigorous statistical controls.
- **Who would be interested in the results, and why** Plant molecular biologists studying 3D genome organization, particularly those working on maize and other large complex plant genomes; computational biologists developing deep learning approaches for regulatory genomics; researchers interested in the sequence determinants of chromatin loops and their evolutionary conservation across eukaryotes. The open-source web tool will appeal to the broader plant community seeking accessible prediction tools.
- **Major strengths** 1) Addresses a clear gap: no plant-trained deep learning models exist for chromatin interaction prediction, and the authors demonstrate cross-species transfer failure. 2) The dual-CNN + LSTM architecture is well-motivated by prior work in animal systems. 3) The multi-layered validation strategy (in silico mutagenesis, natural variants, single-cell co-accessibility) is thoughtful and provides complementary evidence. 4) The open-source implementation and web tool enhance accessibility and reproducibility. 5) The analysis of TF motif classes (bHLH enrichment, AP2/EREBP depletion) generates testable hypotheses.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1 (negative set construction), R1-M2 (validation statistics), R1-M3 (interpretability claims)
- **Assessment against Nature-style criteria** **Originality**: Moderate to high. The application of deep learning to plant 3D chromatin is novel, and the demonstration of cross-species transfer failure is an important contribution. However, the architectural approach is largely borrowed from animal systems, and the interpretability method (in silico mutagenesis) is established. **Scientific importance**: High for the plant genomics community; moderate for the broader chromatin biology field, as the findings are largely consistent with existing knowledge about TF-mediated loop formation. **Interdisciplinary readership**: The work bridges deep learning, chromatin biology, and plant genetics, which could attract readers from multiple communities, but the technical depth may limit accessibility. **Technical soundness**: The core modeling approach is sound, but concerns about negative set construction and validation statistics need resolution. The lack of provided figures and supplementary materials prevents full assessment. **Readability for nonspecialists**: The manuscript is generally well-written, but the methods section assumes familiarity with deep learning and Hi-C terminology. The abstract and introduction are accessible, but the results section would benefit from clearer explanations of key concepts (e.g., what "co-accessibility" means and why it serves as a proxy for chromatin interactions).
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important gap and presents a useful tool, but the negative set construction, validation statistics, and interpretability claims require clarification and potentially additional analyses before the central conclusions are fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The negative training set is constructed by permuting anchor positions and randomly shifting them 5–25 bp, with the claim that this ensures the model learns "sequence features that determine the potential of two genomic regions to interact rather than the 3D interaction architecture itself."
- **Evidence pointer** Material and methods, Data preprocessing; location not provided
- **Concern** The negative set construction is problematic. Permuting anchor positions from the positive set means negative pairs share the same genomic regions as positive pairs, but the random 5–25 bp shifts introduce a subtle confound. The shifted sequences may still contain the same TF binding motifs (since motifs are typically 6–20 bp), meaning the model could learn to distinguish shifted vs. unshifted sequences rather than interacting vs. non-interacting regions. The authors state that without these shifts "no learning progress" occurs, which suggests the model is highly sensitive to exact sequence positioning. This raises the question of whether the model is learning biologically meaningful features or artifacts of the negative set construction. The authors should provide a more rigorous justification for this approach, including analysis of what features the model actually learns to discriminate.
- **Why it matters** If the negative set is not truly representative of non-interacting regions, the model's reported performance (accuracy 0.848, AUC 0.925) may be inflated, and the subsequent in silico mutagenesis results could be artifacts of the training procedure rather than reflections of genuine sequence determinants of chromatin looping.
- **Resolution test** The authors should demonstrate that the model performs well on an independent negative set derived from genomic regions matched for chromatin state, GC content, and repeat content but not derived from positive anchors. Additionally, they should show that the model's predictions are robust to alternative negative set construction strategies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors claim that single-cell co-accessibility data validate their predicted interaction losses, citing a pooled genotype test with χ² = 7.89, df = 1, P = 5.0e-03.
- **Evidence pointer** Results, "Single-cell co-accessibility validates predicted interaction losses"; Figure 4E–G; location not provided
- **Concern** The statistical support for the key validation claim is weak. A single pooled test across all genotypes yields P = 0.005, which would not survive multiple testing correction if each genotype or each RAP is considered a separate test. Moreover, the authors note that B97 is an exception, but do not explain why. The Fisher's Exact Test for co-ACR counts (P = 0.0105) is similarly marginal. The authors should report per-genotype statistics, effect sizes, and confidence intervals. They should also clarify whether the analysis was pre-specified or exploratory.
- **Why it matters** The validation using independent data is the strongest evidence that the model's predictions have biological relevance. If the statistical support is marginal, the claim that natural variants in TF motifs lead to reduced chromatin interactions is not firmly established.
- **Resolution test** The authors should provide per-genotype and per-RAP statistics, with appropriate multiple testing correction. They should also report the magnitude of co-accessibility changes (not just P-values) and demonstrate consistency across genotypes, with a clear explanation for the B97 exception.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability
- **Claim pointer** The authors state that "the presence of binding motifs of specific transcription factor classes, especially bHLH, is predictive of chromatin interaction specificities" and that removal of these motifs "leads to reduced interaction probabilities."
- **Evidence pointer** Results, "In silico predictions of TF-mediated 3D chromatin contacts"; Figure 3B–C; location not provided
- **Concern** The in silico mutagenesis approach identifies motifs whose removal reduces predicted interaction probability, but this does not establish that these motifs are causal drivers of loop formation. The analysis is correlational: motifs are enriched or depleted in RAPs, but the authors do not demonstrate that the presence of these motifs is sufficient for loop formation, nor do they rule out that the motifs are merely correlated with other sequence features (e.g., chromatin state, DNA methylation) that actually drive the interactions. The claim that bHLH motifs are "predictive" is supported, but the stronger claim of a mechanistic role is not.
- **Why it matters** The manuscript's central contribution is the identification of sequence features that mediate chromatin looping. If the interpretability analysis only shows correlation, the biological conclusions are overstated, and the utility of the model for generating mechanistic hypotheses is limited.
- **Resolution test** The authors should perform additional analyses to strengthen the causal claim, such as: (1) testing whether the presence of bHLH motifs is sufficient to predict interactions in regions that do not currently form loops; (2) comparing the predictive power of bHLH motifs against other sequence features (e.g., GC content, chromatin state) in a multivariate model; (3) validating a subset of predictions experimentally, even in a small number of cases.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that "the presence of binding motifs of specific transcription factor classes, especially bHLH, is predictive of chromatin interaction specificities" but does not mention the validation with natural variants or single-cell data. This underrepresents the manuscript's scope.
- **Required correction** Consider adding a sentence summarizing the validation approach and key findings to the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Model architecture
- **Evidence pointer** Material and methods, Model architecture and training process; location not provided
- **Issue** The model architecture description is brief. Key hyperparameters (e.g., number of layers, dropout rates, learning rate schedule, batch size) are not fully specified. The manuscript refers to Supplementary Figure S1 for the model summary, but this was not available for review.
- **Required correction** Provide a complete specification of all hyperparameters in the main text or ensure the supplementary material is comprehensive and accessible.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, Comparative benchmarking
- **Evidence pointer** Results, "Comparative benchmarking of GenomicLinks"; location not provided
- **Issue** The performance metrics are reported as point estimates without confidence intervals or variability across cross-validation folds. This makes it difficult to assess the stability of the reported performance.
- **Required correction** Report mean and standard deviation (or confidence intervals) for all performance metrics across cross-validation folds.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability section
- **Evidence pointer** Data availability; location not provided
- **Issue** The data availability statement lists accession numbers but does not specify which datasets correspond to which analyses. It is unclear whether the Hi-ChIP data, scATAC data, and NAM co-ACR data are all publicly available and whether the code is versioned.
- **Required correction** Clarify the correspondence between datasets and analyses, and provide a versioned release of the code (e.g., a DOI from Zenodo or Figshare).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion; location not provided
- **Issue** The discussion of transfer learning is speculative and not grounded in any experiments presented in the manuscript. While this is a reasonable future direction, it is presented as a mitigation strategy without evidence.
- **Required correction** Either remove or clearly label this as a speculative future direction, or provide preliminary evidence (e.g., performance of GenomicLinks on another plant species) to support the claim.

## Risk / unsupported claims
- The claim that GenomicLinks "learned meaningful DNA sequence features predictive of chromatin looping in maize" is supported by the reported performance metrics, but the biological interpretability of these features is not fully established.
- The claim that "removal of these motifs from loop anchors leads to reduced interaction probabilities" is based on in silico mutagenesis, which is a computational prediction and not an experimental validation.
- The claim that "natural mutations in TFBS lead to predicted losses in 3D chromatin contacts" is supported by the single-cell co-accessibility analysis, but the statistical evidence is marginal (P = 0.005) and the B97 exception is unexplained.
- The statement that "models trained on animal data perform poorly when applied to plants, yielding prediction accuracies as low as 0.1%" is presented without details of the cross-species evaluation; this is referenced to supplementary material that was not available for review.
- The claim that "the model combines dual convolutional neural networks (CNNs) with a long short-term memory (LSTM) network, enabling the identification of spatial and sequential aspects of chromatin interactions" is an architectural description, but the specific contribution of each component is not evaluated through ablation studies.