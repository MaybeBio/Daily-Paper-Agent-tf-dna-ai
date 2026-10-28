## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, methods, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present Nucleotide GPT, a transformer-based model pre-trained on multi-species genomes, and claim that after fine-tuning it predicts lamina-associated domains (LADs) and speckle-associated domains (SPADs) from DNA sequence alone with average accuracies of 73.6% and 79.4% across three cortical development cell types. They further claim that the model's internal embeddings distinguish LADs from inter-LADs, that lower confidence scores are assigned to cell type-specific LADs compared to constitutive LADs (cLADs), and that attention patterns at correctly classified regions suggest specific sequence elements govern predictions. The authors conclude that DNA sequence substantively determines nuclear subcompartment associations.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data
- **Missing materials affecting confidence** Full manuscript, all figures and tables, model architecture details, training and fine-tuning procedures, dataset descriptions, evaluation protocols, baseline comparisons, statistical significance testing, and code availability

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting application of transformer-based language models to the prediction of genome-nuclear subcompartment interactions from DNA sequence. The core idea, that sequence features may encode information about 3D genome organization, is scientifically plausible and timely. However, the abstract alone provides insufficient detail to evaluate the technical soundness of the approach, the validity of the accuracy claims, or the robustness of the interpretability analyses. Several claims appear to extend beyond what the reported metrics can support, and the lack of baseline comparisons and statistical context weakens the case. The manuscript may have merit, but the evidence as presented in the abstract does not establish the central conclusions.
- **Who would be interested in the results, and why** Researchers in 3D genome organization, epigenomics, and gene regulation would be interested in whether DNA sequence alone can predict nuclear subcompartment associations. Computational biologists working on deep learning applications to genomics would also be interested in the transformer architecture and its transfer learning capabilities. Developmental biologists studying neuronal differentiation and cell type-specific genome organization may find the cLAD versus cell type-specific LAD analysis relevant.
- **Major strengths** The application of a pre-trained transformer model to nuclear subcompartment prediction is a novel combination of existing techniques. The multi-species pre-training strategy is sensible for learning general sequence features. The distinction between cLADs and cell type-specific LADs is a biologically meaningful analysis that could provide insight into sequence determinants of genome organization. The use of attention patterns for interpretability is a reasonable approach.
- **Major Concerns** The abstract reports accuracy values without any baseline comparison, confidence intervals, or statistical significance testing. The claim that sequence features play a stronger role in maintaining cLAD associations is based on a comparison of confidence scores, but the abstract does not describe how this comparison was controlled for potential confounders. The attention pattern analysis is described only superficially, and no evidence is provided that the identified sequence elements are functionally validated or distinct from genomic background. The general claim that DNA sequence determines nuclear subcompartment associations is broader than what predictive accuracy alone can establish, since correlation between sequence and compartment status does not demonstrate causation.
- **Minor Comments** The abstract does not specify the number of parameters in the model, the training data composition, or the fine-tuning procedure. The three cortical development cell types are not named. The definition of accuracy is not provided, and it is unclear whether this is per-base, per-domain, or per-bin classification accuracy. The UMAP analysis is mentioned but no quantitative metric is given for how well the embeddings separate LADs from inter-LADs. The phrase "specific sequence elements govern model decision making" is vague and would benefit from concrete examples or motif analysis.
- **Technical failings that need to be addressed before the case is established** The absence of baseline comparisons makes the accuracy claims uninterpretable. The lack of statistical significance testing for the cLAD versus cell type-specific LAD confidence comparison weakens that claim. The attention pattern analysis is not described in sufficient detail to assess whether the identified sequence elements are meaningful or artifacts of the model.
- **Assessment against Nature-style criteria** Originality: The combination of transformer-based sequence modeling with nuclear subcompartment prediction is moderately original, though each component is established. Scientific importance: The question of whether sequence encodes 3D genome organization is important, but the abstract does not provide enough evidence to assess the magnitude of the contribution. Interdisciplinary readership: The topic bridges genomics, deep learning, and developmental biology, which could attract broad interest if the claims are well supported. Technical soundness: Cannot be assessed from the abstract alone; the reported metrics lack necessary context. Readability for nonspecialists: The abstract is generally clear, though terms like LADs, SPADs, and cLADs are used without full explanation of their biological significance.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents promising directions, but the claims as stated require substantial additional evidence, including baseline comparisons, statistical validation, and more detailed interpretability analyses, before the case can be considered.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model achieves an average accuracy of 73.6% for LADs and 79.4% for SPADs across three cortical development cell types.
- **Evidence pointer** Abstract, results section; location not provided
- **Concern** The accuracy values are reported without any baseline comparator, such as genomic feature models, sequence composition models, or simpler machine learning approaches. Without knowing the performance of a trivial classifier or an established method on the same datasets, these numbers cannot be interpreted as evidence of meaningful predictive power.
- **Why it matters** Accuracy alone is uninformative without context. If a simple GC-content model or a k-mer based classifier achieves similar accuracy, the claim that the transformer architecture contributes predictive value would be unsupported. The abstract also does not report confidence intervals or cross-validation details, so the stability of these estimates is unknown.
- **Resolution test** Provide baseline comparisons on identical train and test splits, report confidence intervals or standard deviations across cross-validation folds, and include a null model or permutation test to demonstrate that the accuracy exceeds chance and baseline performance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The model assigns lower confidence scores to cell type-specific LADs compared to cLADs, suggesting sequence features may play a stronger role in maintaining cLAD associations.
- **Evidence pointer** Abstract, results section; location not provided
- **Concern** The abstract does not describe how this comparison was performed, what statistical test was used, or whether the difference in confidence scores is significant. It also does not address potential confounders, such as differences in genomic composition, domain size, or chromatin state between cLADs and cell type-specific LADs.
- **Why it matters** The biological interpretation that sequence features are more important for cLAD maintenance is a strong claim that goes beyond descriptive observation. Without controlling for confounding variables and demonstrating statistical significance, the claim is speculative.
- **Resolution test** Describe the statistical comparison in detail, including the test used, effect size, and p-value. Control for relevant genomic features, such as GC content, repeat density, and chromatin marks, and show that the confidence difference persists. Consider a permutation or bootstrap analysis to establish robustness.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** Examination of the model's attention patterns at correctly classified regions suggests that specific sequence elements govern model decision making about nuclear subcompartment associations.
- **Evidence pointer** Abstract, results section; location not provided
- **Concern** The abstract provides no detail on how attention patterns were analyzed, whether the identified sequence elements were compared to genomic background or known motifs, or whether the analysis was performed on held-out data. Attention patterns in transformer models are known to be difficult to interpret, and without rigorous analysis, this claim is not supported.
- **Why it matters** The interpretability analysis is presented as evidence that the model uses meaningful sequence features. If the attention analysis is not validated, this claim could be an artifact of the model architecture or training procedure rather than a reflection of biological sequence determinants.
- **Resolution test** Provide a detailed description of the attention analysis methodology, including how attention heads were aggregated, how sequence elements were identified, and how they were compared to background or known regulatory motifs. Validate the findings on independent datasets and consider perturbation experiments, such as in silico mutagenesis, to confirm that the identified elements are functionally relevant.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Model description
- **Evidence pointer** Abstract, methods section; location not provided
- **Issue** The abstract does not specify the model size, number of parameters, or the composition of the pre-training dataset beyond "diverse set of multi-species genomes."
- **Required correction** Provide these details in the full manuscript, including the number of species, genome assemblies used, and model architecture specifications.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Dataset description
- **Evidence pointer** Abstract, results section; location not provided
- **Issue** The three cortical development cell types are not named, and the source of the experimental LAD and SPAD data is not described.
- **Required correction** Name the cell types and cite the experimental datasets used for fine-tuning and evaluation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Metric definition
- **Affected element** Accuracy metric
- **Evidence pointer** Abstract, results section; location not provided
- **Issue** The definition of accuracy is unclear. It is not specified whether this is per-base, per-domain, or per-bin classification accuracy, and whether it is averaged over classes or weighted by class frequency.
- **Required correction** Define the accuracy metric precisely and report additional metrics such as precision, recall, and F1 score, particularly given potential class imbalance between LAD and inter-LAD regions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** UMAP analysis
- **Evidence pointer** Abstract, results section; location not provided
- **Issue** The UMAP analysis is described qualitatively as showing that embeddings "effectively distinguish" LADs from inter-LADs, but no quantitative measure of separation is provided.
- **Required correction** Report a quantitative metric, such as silhouette score or adjusted Rand index, to support the qualitative claim of separation.

## Risk / unsupported claims
- The claim that DNA sequence "determines" nuclear subcompartment associations is not supported by predictive accuracy alone, as correlation does not establish causation.
- The claim that sequence features play a stronger role in maintaining cLAD associations is unsupported without statistical testing and confounding control.
- The claim that specific sequence elements govern model decision making is unsupported without detailed attention analysis and functional validation.
- The general claim of the model's "genomic understanding" based on evaluation on histone modifications, promoter detection, and transcription factor binding sites is not assessable from the abstract, as no results for these tasks are reported.
- The accuracy values for LAD and SPAD prediction are uninterpretable without baselines, confidence intervals, or cross-validation details.