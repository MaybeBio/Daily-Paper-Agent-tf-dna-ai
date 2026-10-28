## Review setup
- **Input scope** Full manuscript text (abstract, results, methods, data access, acknowledgments)
- **Assessment boundary** Scientific content, methodological rigor, claims vs. evidence, and technical soundness as presented in the provided text
- **Shared manuscript claim summary** The authors profile allele-specific TF binding in F1 Drosophila embryos from genetically diverse crosses, identify extensive cis-acting genetic effects on binding, expand WASP to include indels, reconstruct functional TF motifs from allelic imbalance, and train a Basenji deep learning model to prioritize causal variants and infer mechanisms of cooperative and tissue-specific TF recruitment.
- **Visible evidence base** Results sections with figures referenced (Figs. 1–5), supplemental figures and tables referenced, methods descriptions, data availability statements
- **Missing materials affecting confidence** Figures and supplemental materials not provided; exact statistical details, model hyperparameters, and validation metrics partially described; no access to raw data or code for independent verification

## Reviewer
- **Overall assessment** This manuscript presents a substantial and well-designed study that combines a genetically controlled F1 cross design, allele-specific ChIP-seq, and deep learning to dissect the impact of natural genetic variation on TF binding during embryogenesis. The work is technically ambitious and the integration of experimental and computational approaches is commendable. The expansion of WASP to handle indels is a useful methodological contribution. However, several claims, particularly regarding the mechanistic interpretation of cooperative binding and tissue-specific CTCF recruitment, are supported by limited direct evidence. The Basenji model's predictive performance and its added value over simpler motif-based approaches require clearer quantitative justification. The manuscript would benefit from more rigorous statistical reporting and a more cautious framing of causal inferences.

- **Who would be interested in the results, and why** Researchers in regulatory genomics, developmental biology, and computational biology would find this study valuable. Those working on allele-specific expression and binding, TF cooperativity, and the functional interpretation of noncoding variation would benefit from the methodological advances and the rich dataset. The work is also relevant to those interested in the application of deep learning to interpret regulatory variation in a developmental context.

- **Major strengths**
  1. The F1 cross design with a shared maternal line and diverse paternal lines is a powerful and well-controlled approach for studying cis-regulatory variation.
  2. The expansion of WASP to include indels addresses a significant technical gap and demonstrably increases the number of testable variants.
  3. The integration of experimental allele-specific binding data with a deep learning model (Basenji) to prioritize and interpret variants is a modern and potentially powerful strategy.
  4. The reconstruction of functional TF motifs from in vivo allelic imbalance data is a clever and informative analysis.
  5. The observation that genetic effects are buffered in regions with higher regulatory complexity (e.g., cobinding) is an interesting and biologically plausible finding.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Statistical rigor
- **Claim pointer** The manuscript claims that the Basenji model can "accurately predict binding from DNA sequence" and that its predictions can "prioritize causal variants" and provide "mechanistic interpretation."
- **Evidence pointer** Results section "Basenji prioritizes causal variants, contextualizes variant effects, and reveals mechanisms of corecruitment"; Methods section "Basenji model and training"
- **Concern** The performance of the Basenji model is described qualitatively (e.g., "performs very well," median Pearson's correlation of 0.74 for ReMap, 0.70 for DNase, 0.78 for this study's ChIP-seq). However, the key claim for variant prioritization is the model's ability to predict the direction and magnitude of allelic imbalance. The manuscript reports that the top-ranked variants predict the correct direction in 68% of cases (79.1% for large effect sizes), but this is only modestly above random (50%). The added value of the deep learning model over simpler approaches, such as directly using motif disruption scores (which already explain 16–33% of imbalanced peaks), is not quantitatively demonstrated. A baseline comparison (e.g., using PWM scores alone to predict direction) is missing. Furthermore, the model's performance is not stratified by TF, genomic context, or variant type, which could reveal important limitations.
- **Why it matters** The central claim of the paper is that the deep learning model provides a powerful tool for prioritizing causal variants. If its predictive performance is only marginally better than chance or simpler models, this claim is overstated. A rigorous, quantitative evaluation with appropriate baselines is essential to establish the model's utility and to support the mechanistic interpretations that follow.
- **Resolution test** Provide a baseline comparison (e.g., using PWM score changes) for predicting the direction of allelic imbalance. Report model performance stratified by TF, variant type (SNP vs. indel), and distance to motif. Include confidence intervals for all performance metrics. If performance is not significantly better than baselines, temper the claims accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The manuscript claims that the data "reveals unexpected relationships between TFs, including potential cooperative pairs, and mechanisms of tissue-specific recruitment of the ubiquitous factor CTCF."
- **Evidence pointer** Results sections "Concordant changes in allelic imbalance between TFs and stages indicate a shared regulatory mechanism" and "Genetic variation uncovers mechanisms of tissue-specific recruitment of CTCF"
- **Concern** The evidence for cooperative binding and tissue-specific recruitment of CTCF is largely based on correlative observations of concordant allelic imbalance between TFs at shared loci. While this is suggestive, it does not directly demonstrate a mechanistic relationship. For example, the claim that Twist may "prime" a site for later CTCF binding is speculative and not supported by temporal or direct molecular evidence. The number of cases (e.g., "seven have an effect on two different TFs or stages") is very small, and the statistical significance of these co-occurrences is not assessed against a null model of independent binding. The manuscript does not rule out alternative explanations, such as independent effects of linked variants in strong LD.
- **Why it matters** The mechanistic interpretations are a major part of the paper's significance and are highlighted in the title and abstract. If these are presented as strong conclusions rather than hypotheses, the paper overreaches its evidence. The field needs robust, causal evidence for cooperative interactions, not just correlative patterns.
- **Resolution test** Provide a statistical test for the enrichment of concordant allelic imbalance between TF pairs compared to a randomized null model. For the specific case of Twist and CTCF, provide additional evidence (e.g., temporal ChIP-seq data, genetic perturbation) to support the priming hypothesis. Alternatively, reframe these findings as testable hypotheses rather than established mechanisms.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Reproducibility
- **Claim pointer** The manuscript claims that the new version of WASP (WASP-indel) "applies the same algorithm to both SNPs and indels, making it equally effective in removing mapping biases caused by either."
- **Evidence pointer** Results section "Quantifying TF binding across genetically diverse embryos"; Methods section "ChIP-seq mappability and inclusion of indels: WASP-indel"
- **Concern** The description of the WASP-indel modifications is brief. The claim of "equally effective" is strong and requires validation. The manuscript reports an increase in usable reads (13–28%) but does not provide a direct assessment of whether the indel-aware mapping correction fully removes bias. For example, are there residual biases for longer indels or indels in repetitive regions? A comparison of allele-specific ratios at known true-positive and true-negative indel sites would be more convincing. The code is mentioned as available, but the manuscript does not describe any validation experiments (e.g., simulations) to demonstrate the effectiveness of the new method.
- **Why it matters** The methodological contribution of WASP-indel is a key part of the paper. If the method is not thoroughly validated, its reliability is uncertain, which could affect the validity of all downstream analyses that include indels.
- **Resolution test** Include a validation section for WASP-indel, using simulated data with known indels to demonstrate that mapping bias is removed. Report the false positive and false negative rates for detecting allelic imbalance at indel sites. Compare the performance of WASP-indel to the original WASP on the same data to quantify the improvement.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Methods section "Basenji model and training"
- **Evidence pointer** Methods section "Basenji model and training"
- **Issue** The description of the model architecture and training procedure is incomplete. Key hyperparameters (e.g., number of layers, learning rate schedule, early stopping criteria) are not fully specified. The manuscript mentions "stochastic gradient descent with a learning rate of 0.1" but does not describe how this was chosen or whether it was tuned.
- **Required correction** Provide a complete description of the model architecture, including the number of parameters, and all training hyperparameters. State how hyperparameters were selected (e.g., grid search, random search) and report the final values. This is essential for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "Effects of genetic variation on TF binding are extensive and preferably detected in genomic regions with less buffering"
- **Evidence pointer** Results section "Effects of genetic variation on TF binding are extensive and preferably detected in genomic regions with less buffering"
- **Issue** The manuscript reports that imbalanced peaks are enriched in putative enhancers and depleted in cobound regions. The statistical tests used (Fisher's exact test) are mentioned, but the exact numbers of peaks and the effect sizes (odds ratios) are only partially reported. The multiple testing correction for the enrichment analyses is not described.
- **Required correction** Report the full contingency tables for the enrichment analyses, including the number of peaks in each category. State the multiple testing correction method used (e.g., Benjamini-Hochberg) and report adjusted p-values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Allele-specific binding preferences reconstruct functional TF motifs via in vivo 'saturation mutagenesis'"
- **Evidence pointer** Results section "Allele-specific binding preferences reconstruct functional TF motifs via in vivo 'saturation mutagenesis'"
- **Issue** The term "saturation mutagenesis" is used to describe the reconstruction of TF motifs from allelic imbalance data. This is potentially confusing, as saturation mutagenesis typically refers to an experimental technique. The authors should clarify that this is an in silico analysis of naturally occurring variants, not an experimental saturation mutagenesis screen.
- **Required correction** Use a more precise term, such as "in vivo allelic series analysis" or "natural saturation mutagenesis," and define it clearly upon first use.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "Quantifying TF binding across genetically diverse embryos"
- **Evidence pointer** Results section "Quantifying TF binding across genetically diverse embryos"
- **Issue** The manuscript states that "the majority of sites occupied by CTCF do not change during embryogenesis" and cites a reference, but the data from this study that support this claim (e.g., overlap of CTCF peaks between stages) are not shown.
- **Required correction** Provide a supplementary figure or table showing the overlap of CTCF peaks between the profiled stages, or explicitly state that this is based on prior work and not directly assessed here.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Data access section
- **Evidence pointer** Data access section
- **Issue** The processed data and code are available on a lab website and a Git server. While this is commendable, the long-term stability of lab websites is not guaranteed. The manuscript should also deposit the processed data in a permanent public repository (e.g., GEO, ArrayExpress) and the code in a permanent archive (e.g., Zenodo).
- **Required correction** Deposit the processed bigWig files and the WASP-indel code in permanent public repositories and provide the accession numbers in the manuscript.

## Risk / unsupported claims
- The claim that the Basenji model provides "mechanistic interpretation" for how variants impact binding is not fully supported. The model provides predictions, but the mechanistic interpretation is inferred from the saturation mutagenesis analysis, which is a post-hoc interpretation of model behavior, not a direct mechanistic assay.
- The claim that "genetic variation has an extensive impact on TF occupancy during embryogenesis in vivo, even for essential developmental regulators" is supported by the data, but the generalizability to other TFs and developmental contexts is not established.
- The claim that "tissue-specific TFs may play a role in recruiting CTCF" is presented as a conclusion, but the evidence is correlative and based on a small number of cases. This should be framed as a hypothesis.
- The statement that "indels with strong phenotypic effects are relatively rare in the genetically controlled context of F1 hybrids" is speculative and not directly tested.
- The performance of the Basenji model for predicting allelic imbalance is not compared to simpler baseline models, making its added value unquantified.