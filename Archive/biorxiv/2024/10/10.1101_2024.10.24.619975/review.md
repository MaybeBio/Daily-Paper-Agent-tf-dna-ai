## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability, author contributions, declarations, acknowledgments)
- **Assessment boundary** Scientific content, technical soundness, methodological rigor, and claims as presented in the provided manuscript text. No external data or supplementary materials were assessed.
- **Shared manuscript claim summary** The authors use F1 crosses of genetically diverse Drosophila lines to profile allele-specific TF binding during embryogenesis, identify 9-18% of TF peaks affected by cis genetic variation, extend WASP to include INDELs, reconstruct functional TF motifs from allelic imbalance, and train a Basenji deep learning model to prioritize causal variants and reveal cooperative TF relationships.
- **Visible evidence base** Main text figures (Fig. 1-5), supplementary tables (S1, S2, S4, S5, S6), supplementary figures (1-7), methods section, and referenced external resources (WASP-INDEL code, Basenji code, Shiny app)
- **Missing materials affecting confidence** Supplementary figures and tables were not provided in full; exact statistical methods for CHT permutation testing are only partially described; details of Basenji hyperparameter tuning and model selection are not fully specified; data accession numbers are placeholders (xx); no information on computational resource requirements or runtime for model training

## Reviewer
- **Overall assessment** This manuscript presents a substantial and well-designed dataset that will be of considerable value to the fields of regulatory genomics and developmental biology. The use of F1 crosses to profile allele-specific TF binding across multiple embryonic stages is methodologically sound, and the extension of WASP to handle INDELs addresses a genuine gap in existing tools. The reconstruction of functional TF motifs from in vivo allelic imbalance data is conceptually elegant and provides a useful proof-of-principle. The Basenji application for variant prioritization is timely and generally well-executed, though the interpretability of the model's predictions for non-expert readers could be improved. The main weaknesses lie in the relatively small number of TF-stage combinations profiled, the limited validation of predicted cooperative interactions, and some under-specified methodological details that would need clarification for full reproducibility. Overall, the work is technically competent and the conclusions are largely supported by the data presented, but the breadth of biological insight is somewhat narrower than the title and abstract suggest.

- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, particularly those interested in the genetic basis of TF binding variation, will find the dataset and the WASP-INDEL extension immediately useful. The Basenji model trained on Drosophila regulatory data will be of interest to computational biologists working on deep learning approaches to regulatory genomics. Developmental biologists studying mesoderm specification and muscle development will value the stage-specific TF binding maps. The demonstration that tissue-specific TFs can recruit CTCF to a subset of sites has implications for understanding cell-type-specific chromatin architecture, which will interest the 3D genome community. Finally, the general approach of using natural genetic variation as a perturbation tool will appeal to those working on variant effect prediction in human disease contexts.

- **Major strengths** 1) The experimental design using F1 crosses with a shared maternal line is rigorous and well-controlled, enabling clean allele-specific analysis. 2) The extension of WASP to include INDELs is a practical and needed methodological contribution. 3) The reconstruction of functional TF motifs from in vivo allelic imbalance data provides a compelling validation of the approach. 4) The Basenji model is trained on a large and diverse set of regulatory tracks, and the demonstration that it can predict the direction of strong-effect variants with >90% accuracy is impressive. 5) The observation that TF binding variation is buffered in co-bound regions is biologically interesting and consistent with recent work on regulatory robustness.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the combined haplotype test (CHT) identifies variants associated with TF binding differences, and that permutation testing confirms the relatedness of fly lines does not lead to excess false associations.
- **Evidence pointer** Results section "Effects of genetic variation on TF binding are extensive...", Figure 2C, Methods "Combined haplotype test"
- **Concern** The permutation testing procedure is described only briefly. The authors state that "permuting genotype information also revealed some deviation from the uniform p-value distribution" and that 12-255 significant variants remain per condition after permutation. However, it is unclear how the permutation was performed (e.g., permuting genotypes across individuals, permuting allele labels, or permuting phenotypes). The statement that these numbers "fall within the CHT FDR threshold" is not a valid statistical justification for accepting them as true positives. The authors should provide a more rigorous assessment of whether the observed number of significant variants after permutation is consistent with the expected false discovery rate, or whether it indicates residual confounding.
- **Why it matters** The validity of the entire set of AI peaks depends on the CHT correctly controlling false positives. If the permutation-based null is not properly calibrated, the reported 9-18% of TF peaks affected by genetic variation could be substantially overestimated.
- **Resolution test** Provide a detailed description of the permutation procedure, including what exactly is permuted and how many permutations are performed. Report the distribution of the number of significant variants across permutations and compare the observed number to this null distribution. If the observed number is within the expected range under the null, this should be stated explicitly with appropriate statistics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the Basenji model "could accurately predict experimental AI for strong effect variants" and that pAI prioritizes causal variants.
- **Evidence pointer** Results section "Basenji prioritises causal variants...", Figure 5C-E, Methods "Basenji model and training"
- **Concern** The evaluation of Basenji's predictive performance is incomplete. The authors report that the top-ranked pAI variants predict the correct direction of experimental AI in 68% of cases, increasing to 79.1% for variants with large predicted effect size. However, it is unclear what the baseline accuracy would be (e.g., random guessing would give 50% for direction prediction). More importantly, the authors do not report how many of the 3,368 significant AI peaks had any variant with a meaningful pAI prediction, nor do they provide a comparison against simpler sequence-based predictors (e.g., position weight matrix scores alone). The claim that pAI "prioritises causal variants" requires a demonstration that pAI outperforms existing methods for variant effect prediction.
- **Why it matters** The utility of the Basenji model as a variant prioritization tool depends on its performance relative to existing approaches. Without a baseline comparison, the 68-79% accuracy figures are difficult to interpret, and the claim that pAI is a "powerful tool" is not fully supported.
- **Resolution test** Provide a comparison of pAI-based prioritization against at least one simpler baseline (e.g., PWM score differences, or a logistic regression on motif presence). Report the area under the ROC curve or precision-recall curve for pAI-based prioritization of causal variants. Additionally, report the fraction of AI peaks for which the model makes a confident prediction, and discuss the characteristics of peaks where the model fails.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that their analysis "revealed unexpected relationships between TFs, including potential cooperative pairs, and mechanisms of tissue specific recruitment of the ubiquitous factor CTCF."
- **Evidence pointer** Results section "Basenji prioritises causal variants...", Figure 5G, Supplementary Figure 7F-H
- **Concern** The evidence for cooperative TF binding and tissue-specific CTCF recruitment is largely correlative and based on a small number of examples. The authors identify cases where variants in one TF's motif affect another TF's binding, but they do not provide direct experimental validation of these predicted cooperative interactions. The claim that "Twist binding is facilitated by CTCF and Mef2 acting as co-factors" is based on co-binding data from other studies, not on functional experiments in the F1 system. The number of validated examples (7 variants affecting 2 TFs) is very small, and the authors do not assess whether this is more than expected by chance.
- **Why it matters** The biological insights regarding cooperative TF binding and CTCF recruitment are among the most novel and interesting claims in the manuscript. If these are not robustly supported, the broader significance of the work is diminished.
- **Resolution test** Provide a statistical assessment of whether the number of variants affecting multiple TFs exceeds what would be expected by chance (e.g., by permutation of TF peak assignments). For the specific examples highlighted, consider validating at least one predicted cooperative interaction experimentally (e.g., by CRISPR mutagenesis of the predicted co-factor motif and measuring the effect on the primary TF's binding).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "By expanding WASP to examine INDELs, we increased detection of allele imbalanced (AI) peaks by 30-50%."
- **Evidence pointer** Abstract, Results section "Quantifying TF binding across genetically diverse embryos", Methods "ChIP-seq read mapping and mappability filter"
- **Concern** The specific contribution of the WASP-INDEL extension to the increased detection of AI peaks is not clearly quantified. The 30-50% increase could be due to the inclusion of INDELs themselves, or it could be due to other changes in the pipeline (e.g., different mapping parameters, updated reference genome, or the use of de novo genotyping). The authors do not provide a direct comparison between the original WASP and WASP-INDEL on the same data.
- **Why it matters** The WASP-INDEL extension is presented as a key methodological contribution. Without a direct comparison, it is unclear whether the improvement is specifically attributable to the INDEL handling or to other factors.
- **Resolution test** Run both the original WASP and WASP-INDEL on the same subset of data and report the number of AI peaks detected by each. Quantify the increase in detected AI peaks specifically attributable to INDEL inclusion, and discuss whether the increase is driven by INDELs overlapping TF motifs or by other mechanisms.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction assume familiarity with allele-specific analysis and deep learning approaches to regulatory genomics. Terms such as "combined haplotype test," "allelic imbalance," and "Basenji" are used without brief definitions. For a Nature-style readership that includes non-specialists, a brief explanation of these concepts would improve accessibility.
- **Required correction** Add one or two sentences in the introduction explaining the concept of allele-specific analysis and why it is powerful for dissecting cis-regulatory effects. Briefly describe what Basenji does in plain terms (e.g., "a deep neural network that learns to predict regulatory activity from DNA sequence").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "De novo genotyping of parental lines"
- **Evidence pointer** Methods section
- **Issue** The description of the genotyping procedure mentions that reads were mapped to a "joint genome of Drosophila melanogaster and Wolbachia" to quantify parasite contamination, but the details of how contamination was handled in downstream analyses are not provided. It is unclear whether reads mapping to Wolbachia were excluded from all subsequent analyses.
- **Required correction** Clarify whether Wolbachia-mapping reads were removed from the ChIP-seq and genotyping analyses, and if so, at what stage. If not, explain why contamination did not affect the results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Concern** The discussion does not address the potential limitations of using Drosophila as a model for understanding human TF binding variation. While the authors note that TF binding domains are conserved, the regulatory complexity of human genomes (e.g., larger intergenic spaces, more extensive chromatin looping) may limit the direct transferability of the findings.
- **Required correction** Add a brief paragraph in the discussion acknowledging the limitations of the Drosophila model and discussing which aspects of the findings are likely to generalize to vertebrates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Basenji model and training"
- **Evidence pointer** Methods section
- **Issue** The description of the Basenji model architecture is incomplete. The authors mention convolutional blocks, residual blocks with dilated convolutions, and a final dense layer, but do not specify the total number of parameters, the learning rate schedule, the number of training epochs, or the early stopping criteria. This level of detail is necessary for reproducibility.
- **Required correction** Provide a complete description of the model architecture, including the number of layers, filter sizes, dilation rates, and the total parameter count. Specify the training procedure, including the number of epochs, learning rate schedule, and any regularization techniques used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results section "Basenji prioritises causal variants..."
- **Evidence pointer** Figure 5
- **Issue** The description of the saturation mutagenesis analysis and the interpretation of importance scores may be difficult for readers unfamiliar with deep learning interpretability methods. The authors state that "the model predicts at least one motif within 75bp of the strong pAI variants" but do not explain how this relates to the importance scores or what a "motif" means in this context.
- **Required correction** Provide a brief explanation of saturation mutagenesis in the context of deep learning models (i.e., systematically mutating each position in the sequence and measuring the change in predicted output) and clarify how the importance scores relate to the identification of functional motifs.

- **Technical failings that need to be addressed before the case is established** 1) The permutation testing procedure for CHT needs to be described in detail and the results interpreted more rigorously (R1-M1). 2) The evaluation of Basenji's predictive performance needs a baseline comparison and more complete reporting of model performance metrics (R1-M2). 3) The specific contribution of WASP-INDEL to increased AI peak detection needs to be directly quantified (R1-M4). 4) The model architecture and training details for Basenji need to be fully specified for reproducibility (R1-m4).

- **Assessment against Nature-style criteria** Originality: The work is original in its application of F1 crosses to study TF binding during embryogenesis and in the extension of WASP to INDELs. The reconstruction of functional TF motifs from allelic imbalance data is a novel analytical approach. However, the conceptual framework (using natural variation to dissect regulatory mechanisms) is not entirely new, and the biological insights are somewhat incremental. Scientific importance: The dataset is valuable and will be a useful resource, but the breadth of biological insight is limited by the small number of TFs and stages examined. The finding that tissue-specific TFs can recruit CTCF is interesting but based on limited evidence. Interdisciplinary readership: The work bridges developmental biology, population genetics, and computational biology, and will appeal to readers across these fields. However, the technical complexity of the deep learning component may limit accessibility. Technical soundness: The experimental design is rigorous, and the computational methods are generally appropriate. However, the evaluation of the Basenji model and the statistical validation of CHT results need strengthening. Readability for nonspecialists: The manuscript is clearly written but assumes substantial background knowledge in genomics and machine learning. The abstract and introduction could be more accessible.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable dataset and a useful methodological contribution, but the statistical validation of the CHT results and the evaluation of the Basenji model need to be strengthened before the central claims are fully established. The biological insights regarding cooperative TF binding and CTCF recruitment are intriguing but would benefit from additional validation or a more cautious interpretation.

## Risk / unsupported claims
- The claim that "9-18% of TF bound regions [are] impacted by genetic variation" is dependent on the CHT permutation testing, which is not fully described and may not adequately control for relatedness among lines.
- The claim that pAI "could accurately predict experimental AI for strong effect variants" is based on a single evaluation metric (direction accuracy) without comparison to baseline methods.
- The claim that "the model could predict the direction of strong effect variants across all TFs with an accuracy >90%" appears to refer to a subset of variants (top pAI with large effect size) and may not generalize to all variants.
- The claim that "Twist binding is facilitated by CTCF and Mef2 acting as co-factors" is based on co-binding data from other studies and indirect evidence, not on direct functional experiments in this system.
- The claim that "this fine-grained 'mutagenesis' could reconstruct functionalized binding motifs of all factors" is supported by the data, but the statement that this is equivalent to saturation mutagenesis may overstate the coverage of all possible mutations.
- The data availability section contains placeholder accession numbers (xx), making the data accessibility claims unverifiable at this stage.