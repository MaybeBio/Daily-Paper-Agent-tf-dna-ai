## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the provided text
- **Shared manuscript claim summary** The authors combine machine learning predictions with lentiMPRA experiments in human and chimpanzee neural progenitor cells to dissect the functional effects of human-chimpanzee sequence differences in Human Accelerated Regions, concluding that most HAR variants alter enhancer activity, that cis effects dominate over trans effects, and that compensatory evolution likely drove HAR sequence evolution.
- **Visible evidence base** Summary, Introduction, Results sections (Figures 1-7 referenced), Discussion, Methods (partial), Supplementary table references
- **Missing materials affecting confidence** Full figure panels, supplementary tables (S1-S8), detailed statistical outputs, complete methods for ML model training and validation, raw data accessions, code availability

## Reviewer
- **Overall assessment** This manuscript presents a substantial and technically ambitious integration of computational prediction and experimental validation to address a long-standing question about the functional significance of human accelerated regions. The combination of deep learning predictions with lentiMPRA in both human and chimpanzee cells is a notable advance over prior work. The central finding that cis-regulatory effects dominate over trans effects, and the evidence for compensatory evolution within HARs, are potentially important contributions. However, several concerns regarding the interpretation of the ML predictions, the statistical framework for identifying opposing variants, and the generalizability of the conclusions from a subset of HARs need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Evolutionary biologists studying human-specific genomic changes, neurodevelopmental geneticists interested in enhancer function and gene regulation, computational biologists developing and applying deep learning methods to regulatory genomics, and researchers studying the genetic basis of neuropsychiatric disorders. The work bridges evolutionary genomics and functional neurobiology in a way that will appeal to a broad interdisciplinary audience.

- **Major strengths** The study design is ambitious and integrative, combining multiple complementary approaches (deep learning, lentiMPRA, Hi-C, CRISPRa) to address a fundamental question in human evolution. The inclusion of chimpanzee cells is a significant methodological advance that allows direct assessment of trans effects. The permutation-based dissection of individual variants within HARs is a powerful approach to test evolutionary hypotheses. The finding that cis effects dominate over trans effects is a clean and important result. The link to neurodevelopmental genes and psychiatric disorders adds translational relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity of opposing variant identification
- **Claim pointer** "43% of HARs have variants with large opposing effects on chromatin state and 14% on neurodevelopmental enhancer activity. This is significantly more than expected by chance (bootstrap p=0.03)."
- **Evidence pointer** Results section "Many HARs contain variants predicted to have opposing effects on enhancer activity"; Figure 4E
- **Concern** The statistical framework for identifying "opposing variants" and testing enrichment against a null expectation is not fully described. The bootstrap p-value of 0.03 is marginal, and it is unclear how the null distribution was constructed. Specifically, were the null simulations performed on matched sequences with similar GC content, CpG density, and motif structure? The threshold for "large" effects (exceeding the mean of common variants) appears arbitrary, and the sensitivity of the 43% and 14% estimates to this threshold is not reported. Furthermore, the claim that variants have "opposing effects" requires demonstrating that the predicted effects are not simply noise around zero, particularly given that Sei was trained on human data and may have systematic biases when applied to chimpanzee sequences.
- **Why it matters** The compensatory evolution hypothesis is a central conclusion of the paper. If the statistical evidence for opposing variants is weak or confounded by technical artifacts, this conclusion is not supported. The marginal p-value and unclear null model undermine confidence in the central evolutionary claim.
- **Resolution test** Provide a detailed description of the null model, including how matched control sequences were generated. Report the distribution of opposing variant frequencies in null simulations. Show that the results are robust to different thresholds for defining "large" effects. Demonstrate that the opposing variant signal is not driven by sequence composition differences between human and chimpanzee HAR alleles.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of Sei predictions for cross-species comparisons
- **Claim pointer** "Using machine learning (ML), we interrogated the function of all human-chimpanzee variants in 2,645 Human Accelerated Regions (HARs), finding 43% of HARs have variants with large opposing effects on chromatin state"
- **Evidence pointer** Results section "Deep learning predicts that most individual HAR variants alter enhancer activity"; Figure 4
- **Concern** Sei was trained exclusively on human genomic data. Applying it to chimpanzee sequences assumes that the sequence-to-function mapping learned from human data is transferable across species. This assumption is questionable given that TF binding motifs, chromatin states, and regulatory grammar may have diverged between species. The authors acknowledge this limitation in the methods ("Sei utilizes tens of thousands of human datasets which do not exist for chimpanzee") but do not address how this might bias the predicted effects. Specifically, if Sei has learned human-specific sequence features, it may systematically overestimate or underestimate the functional impact of chimpanzee-derived alleles. The manuscript does not report any validation of Sei predictions against experimental data in chimpanzee cells prior to the lentiMPRA comparisons.
- **Why it matters** The entire computational screen of 2,645 HARs relies on the validity of Sei predictions for cross-species comparisons. If these predictions are biased, the prioritization of HARs for experimental validation and the genome-wide conclusions about the fraction of HARs with functional variants could be incorrect.
- **Resolution test** Provide evidence that Sei predictions correlate with lentiMPRA measurements in both human and chimpanzee cells. Report the correlation separately for human and chimpanzee sequences. If possible, validate Sei predictions on a set of known functional variants in chimpanzee regulatory elements. Discuss the potential direction of bias and how it might affect the conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of lentiMPRA results
- **Claim pointer** "The species-specific enhancer activity of HARs was accurately predicted from the presence and absence of transcription factor footprints in each species."
- **Evidence pointer** Results section "MPRA characterization of HAR variants in primate NPCs"; Figure 5
- **Concern** The lentiMPRA was performed on a subset of 714 HARs, of which 293 were classified as active. The authors state that these 714 HARs are representative of the full set of 2,645, but the criteria for representativeness are not fully described. More importantly, the lentiMPRA measures enhancer activity in an episomal or integrated context that may not fully recapitulate endogenous chromatin environment. The authors acknowledge this limitation in the discussion, but the extent to which this affects the conclusions about cis versus trans effects is not quantified. Additionally, the lentiMPRA was performed in neural progenitor cells at two stages, but the authors do not report whether the cis-trans conclusions hold across both stages or whether there are stage-specific effects.
- **Why it matters** The conclusion that cis effects dominate over trans effects is based on a subset of HARs tested in a specific cellular context. If this conclusion is stage-specific or context-dependent, the general claim about HAR evolution would need to be qualified.
- **Resolution test** Report the cis-trans analysis separately for N2 and N3 stages. Discuss how the lentiMPRA context (integrated vs. episomal, copy number, flanking sequence) might affect the measured activity ratios. If possible, validate a subset of findings using an orthogonal assay such as CRISPR perturbation or endogenous locus manipulation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of TF footprint analysis
- **Claim pointer** "A supervised gradient boosting regressor was able to use the human and chimpanzee footprints of each HAR to predict their human:chimpanzee lentiMPRA log ratios with very low error (R2=0.8, RMSE=0.04)"
- **Evidence pointer** Results section "Species differences in HAR enhancer activity can be predicted from TF footprints"; Figure 6
- **Concern** The R2 of 0.8 for predicting lentiMPRA log ratios from TF footprints is surprisingly high, particularly given the complexity of enhancer function and the indirect relationship between TF binding and transcriptional output. The RMSE of 0.04 is also remarkably low. It is unclear whether this performance is achieved on held-out data or in-sample. The methods state that 80% of HARs were used for training and 20% for early stopping, but the reported R2 appears to be in-sample. If the model is evaluated on held-out data, the performance would likely be substantially lower. Additionally, the variable importance analysis identifies TFs that contribute to prediction, but the direction of effects and the biological plausibility of the top TFs are not discussed in detail.
- **Why it matters** The claim that TF footprints can accurately predict enhancer activity differences is a strong statement that, if true, would have broad implications for understanding regulatory evolution. However, if the reported performance is in-sample, the claim is overstated.
- **Resolution test** Report the R2 and RMSE on held-out test data. Provide cross-validated performance metrics. Discuss the biological interpretation of the top predictive TFs and whether they are known regulators of neurodevelopment.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence for compensatory evolution
- **Claim pointer** "This pattern, consistent with compensatory evolution, was confirmed using massively parallel reporter assays in chimpanzee and human neural progenitor cells."
- **Evidence pointer** Results section "Many HARs contain variants predicted to have opposing effects on enhancer activity"; Figure 7
- **Concern** The evidence for compensatory evolution rests on the observation that individual variants within the same HAR have opposing effects on enhancer activity. However, the permutation experiments were performed on only three HARs. While the authors state that all three show evidence of opposing variants, the sample size is very small. Moreover, the interpretation of opposing effects as evidence for compensatory evolution assumes that the net activity of the human HAR is similar to the ancestral state. This assumption is not directly tested. It is possible that the opposing variants simply reflect the stochastic nature of regulatory evolution rather than active compensation.
- **Why it matters** The compensatory evolution hypothesis is a major conclusion of the paper. The evidence from three HARs, while suggestive, is not sufficient to establish this as a general mechanism for HAR evolution.
- **Resolution test** Expand the permutation analysis to additional HARs. Test whether the net activity of human HARs is similar to the reconstructed ancestral sequence. Discuss alternative explanations for opposing variant effects, such as neutral drift or epistasis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** ML model training and validation
- **Evidence pointer** Methods section "Supervised and unsupervised learning analysis with in vivo epigenetic profiles"
- **Issue** The description of the L1-penalized logistic regression model for distinguishing neurodevelopmental enhancers is brief. It is unclear how the training set was constructed, what features were used, and how hyperparameters were selected.
- **Required correction** Provide additional details on the training procedure, including the number of positive and negative examples, the feature set, and the hyperparameter tuning strategy.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Differential activity analysis
- **Evidence pointer** Results section "MPRA characterization of HAR variants in primate NPCs"
- **Issue** The manuscript reports that 159 HARs show significant cis effects at FDR < 1%, but the effect sizes and confidence intervals are not reported. It is unclear how many of these effects are of meaningful magnitude.
- **Required correction** Report the distribution of effect sizes and provide confidence intervals for the cis effects. Consider reporting the proportion of HARs with effects exceeding a biologically meaningful threshold.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figures 1-7
- **Evidence pointer** All figures
- **Issue** The figure legends are not provided in the manuscript text. Without legends, it is difficult to fully interpret the figures.
- **Required correction** Ensure that figure legends are included in the final submission and that they clearly describe the experimental design, sample sizes, and statistical tests used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data accessions
- **Evidence pointer** Methods section "Data and Code Availability"
- **Issue** The data availability statement mentions GEO accession GSE110760, but it is unclear whether all processed data and analysis code are publicly available.
- **Required correction** Provide a detailed data availability statement that includes accessions for all datasets generated in this study and a link to the analysis code repository.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion acknowledges some limitations but does not address the potential impact of using human-trained ML models on chimpanzee sequences in sufficient depth.
- **Required correction** Add a paragraph discussing the limitations of cross-species application of human-trained models and how this might affect the interpretation of the results.

## Risk / unsupported claims
- The claim that 43% of HARs have variants with large opposing effects on chromatin state is based on Sei predictions that have not been validated for cross-species comparisons.
- The claim that compensatory evolution drove HAR evolution is based on evidence from only three HARs and assumes that net activity of human HARs is similar to the ancestral state, which is not directly tested.
- The R2 of 0.8 for predicting lentiMPRA activity from TF footprints appears to be in-sample and may not reflect held-out performance.
- The statement that "70% of HARs overlap open chromatin and/or active marks in the human brain" is based on a comparison with a non-random set of genomic regions and may not be a statistically rigorous enrichment analysis.
- The conclusion that cis effects dominate over trans effects is based on lentiMPRA data from a subset of HARs and may not generalize to all HARs or to endogenous chromatin contexts.